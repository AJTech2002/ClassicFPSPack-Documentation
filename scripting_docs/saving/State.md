# State

This is a fundemental class used all throughout the Classic FPS Pack. Whenever anything needs to be saved/loaded you will create a class that is derived from this class. 

It is a MonoBehaviour script so it will only work with component based scripts.

By extending a class from this class you will tell the `SaveManager` that this is a candidate for saving/loading.

To extend a class by state do something like the following:

```C#
using ClassicFPS.Saving_and_Loading;
public class TestClass : State {

}
```

Take a look at some common states in the pack to understand some common use cases:

- TransformState
- PlayerStatistics
- GameState
- SavePoint
- WeaponState

Take a look at this video to understand how this system works from the ground-up and how to develop further states:

https://youtu.be/LqrdAKjftOM

## How Are States Used

States are just data holders and describe how information should be converted to a string and recieved from a string. The Saving & Loading to files is done in the [`SaveManager`](../managers/SaveManager).

When you 'Save All States' all it does is find all the states in the current scene and calls the SaveState() method and stores the returned string into a file. 

Then when you load it, we read that file and pass it back into the state. In this way all the logic is self contained in the state itself. 

## Override Functions

In order to develop the logic to utilise these states you will need to override some of the following functions.

You can override a function like so (ex. SaveSate):

```C#

public override string SaveState()
{
    return "";
}
```

1. **string GetUID()**: In this function you can return a string that identifies this state uniquely. This is **extremely** important. This string will be used to identify which file to read back into this state. 

    This means your UID should strive to exist only once in a given scene. The default UID is constructed in the following format:

    `(gameObject.scene.name+"_"+gameObject.name+"_"+(this.GetType().Name));`

    This will result in something like this: `TestScene_Cube_TransformState`, the benefit of this is that this state will only be tracked for the 'TestScene' as this UID is scene dependent. 

    If you want a scene independent state such as Player health (in PlayerStatistics); you must remove the `gameObject.scene.name` section; leaving just `Cube_TransformState`. This will be loaded in no matter the scene.

    Since we are using `gameObject.name` as the default, it is possible to have multiple GameObjects with the same name in the same scene; this should be avoided. Or a custom UID can be defined for objects by overriding this method.

2. **string SaveState()**: This function when called should return the serialized string state of this class. This same string when given back to the State should be able to retrieve the needed information from it. 

    A common data format used to do this is the JSON format.

    Most of the States in Classic FPS Pack use [Unity's JSON Utility](https://docs.unity3d.com/ScriptReference/JsonUtility.html)

3. **void LoadState (string loadedJSON)**: This function takes back in some string (doesn't have to be JSON); and decides what to do with that information.

    The general course of action would be to convert the JSON back into the object it was created from; then set that information into the game.

4. **void EmptyLoadState ()**: This function is called whenever this state is loaded but there was no save found for it; this can be some initialization behaviour.

5. **bool ShouldSave ()**: Here you can write logic telling the Save Manager when it should or shouldn't save this current state. By default this always returns `true`. 

    For example in the transform state, we set this to `false` if the object has not moved, this saves space and time as we don't need to save something that hasn't changed.

6. **bool ShouldLoad()**: Similar to `ShouldSave()`, you can decide when this state should allow to be loaded in or when it shouldn't.



## Creating a new State

In order to create a new state you will need some data to track; this will have to be created by you. This data must be 'serializable', so it cannot be things such as Meshes, GameObjects etc. 

It has to be pure data that can somehow be converted to a string, this is doable for most primitives and arrays of primitives.

Checkout this very simple state that tracks the damage on a player or object:


```C# 

//1
public class DamageState : State {
    
    [System.Serializable] //2
    struct DamageStateData {
        //3
        public float health;
        public string currentState;
    }
    
    DamageStateData storedData; //4
    
    //5
    public void TakeDamage ()
    {
        storedData.health -= 10;
        
        if (storedData.health < 50) storedData.currentState = "Damaged";
        
        if (storedData.health < 20) storedData.currentState = "Heavily Damaged";
        
        if (storedData.health <= 0) {
            storedData.currentState = "Dead";
            GameObject.Destroy(this.gameObject);
        }
        
    }

    //6
    public override string SaveState()
    {
        return SaveUtils.ReturnJSONFromObject<DamageStateData>(savedState);
    }

    //7
    public override void LoadState (string loadedJSON)
    {
        storedData = SaveUtils.ReturnStateFromJSON<DamageStateData>(loadedJSON);
        
        //8
        if (storedData.health <= 0) {
            GameObject.Destroy(this.gameObject);
        }
    }

}
```

Lets break it down based on section:

1. Create a state extending from `State`

2. Create a `struct` type with any name and mark it as `[System.Serializable]` to allow to serialize the data within this struct.

3. Have some properties within this struct that are serializable 

4. Create a variable that utilises the struct such as `storedData`

5. This is an example function that makes the Object take some damage and then changes the `health` and `currentState` properties; it also has some logic so when health is < 0 it destroys the GameObject.

6. When `SaveState()` is called, I use `SaveUtils` to convert the struct to JSON data; you can use JsonUtility directly.

    In the background this is really just calling:
    
    ```C#
    public static string ReturnJSONFromObject<T>(T state)
    {
        string json = JsonUtility.ToJson(state);
        return json;
    }
    ```

7. When `LoadState()` is called, I load the `storedData` from the input JSON. 

8. As soon as I have the needed information loaded in, I can perform the logic I need. For example here, if something was killed then it should remain dead; so if health is < 0 after it is loaded then we should destroy it.

That's how simple it is to create your own states! 

