# Game Manager

The GameManager is an essential component of the Classic FPS Pack, it handles spawning in the Player Controller and creating the global references for all other scripts to use. It also handles the loading and saving of scenes when the Player spawns into a new scene.

Whenever you switch between scenes you should do it through the GameManager as it will do the following things:

1. Spawn Player Controller in Spawn Point
2. Make Player Controller and other references easily available (ex. `GameManager.PlayerController`)
3. Check if Level has existing saves and load in all the data
4. If the Level doesn't have an existing save, create a default one so you can load back in on the last level you left off at

## Important Information

The GameManager is not destroyed in between scenes, meaning the first GameManager that is found will be used. This means the properties of the GameManager that will be in the Menu scene will carry onto all the scenes from there.

In order for this to work, the GameManager must be in the root of scene, it must not be under any other GameObject in the scene.

### Game Flow

The Game would start at the Main Menu scene, the GameManager would exist on this scene. The configuration here would follow through the entire game.

The Main Menu should have a way to load from the last save.

The `GameState` stores the last level that was loaded. The Player enters that scene and the `SceneManager_sceneLoaded(Scene scene, LoadSceneMode sceneMode)` function in GameManager is executed.

This loads in all the level data.

If the `GameState` doesnt have a previously saved Level then the GameManger will spawn the Player in the first level.

At the start of each level a new save will be created to allow the Player to 'load' back into that game.

On Player Death the health will be reset and the Player will be pushed back to the last save; this behaviour can be modified in the `PlayerStatistics` script.

When the Player reaches the End Scene, all saves can be cleared to allow them to restart.

This flow is implemented in the `Demo Scenes` folder, from the `Menu` to the `End Screen`.

---

## Public & Static Functions

Static functions can be accessed by :

```C#
GameManager.StaticFunction()
```

Public functions can be accessed by :

```C#
GameManager.instance.PublicFunction()
```

### Static

1. **LoadStartScene()** : Loads the starting scene defined in the GameManager properties
2. **LoadScene (string sceneName, bool requiresLoading)** : Loads the scene with a name (given it is in Build Settings) and if requiresLoading is true then it handles the Player Spawning, Saving etc. in most cases it should be true unless it is a UI scene such as 'Game Over'.
3. **RespawnFromLastSave()** : Respawn from the last save the player made.

### Public

1. **LoadPlayerCurrentLevel()** : Loads the last scene the player was in before they left the game.

### Important Private Functions

1. **SceneManager_sceneLoaded(Scene scene, LoadSceneMode sceneMode)** : This function is automatically called when a new scene is loaded and `requiresLoading = true`; here you can handle all the logic of what to do when a new scene is created.

---

## Variables

### General

Here are some other General variables that need to be assigned, the demo will have these pre-defined:

1. **playerPrefab**: Reference to the FPS Controller, it's best to use the one provided with the pack.
2. **keyManager**: The Key Manager scriptable object within the Project.
3. **weaponManager**: The Weapon Manager scriptable object within the Project.
4. **startingSceneName**: The name of the starting scene, this is used when the GameManager can't find any other saves, take a look at the Menu scene to see this being used.

### Testing

When you are testing a scene you need to mark this as true in the GameManager, this will ensure the player is spawned.

`public bool isTestingScene = false;`

Usually the Player is spawned only when the GameManager.LoadScene function is called, however in a testing environment you might want to automatically call that; that's what this boolean is for.

Don't forget to uncheck it once you're done with it.

```
public bool saveSceneOnSpawn = true;
public bool loadSceneContentsOnLoad = true;
```

These should generally be 'true', however if you don't want to save the scene everytime the player spawns or you want to start afresh each time you can modify these variables; ensure they are both set to true when you're not testing.

### Static References

You can access the following variables directly from the GameManager:

```csharp
public static PlayerWeaponController PlayerWeaponController;
public static PlayerController PlayerController;
public static PlayerStatistics PlayerStatistics;
public static PlayerSFX PlayerSFX;
```

They can be accessed by:

`GameManager.PlayerWeaponController;`

This prevents you from using `GameObject.FindObjectOfType` too much.
