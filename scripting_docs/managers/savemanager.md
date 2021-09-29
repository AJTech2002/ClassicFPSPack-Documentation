# Save Manager

The Save Manager lies in the same object as the Game Manager, therefore it also doesn't get destroyed while moving between scenes.

The Save Manager doesn't have any functionality in itself, it holds a bunch of static functions that can be called to trigger saving/loading functionality.

## Important

When using the Saving system, ensure that GameObjects with states attached adhere the following properties:

1. They do not have a duplicate name to any other GameObject in the scene
2. The UID of the State starts with the scene name followed by an '\_'

   This should be the default behaviour if the State's GetUID() function is not overriden.

## How it works

The topic of how saving works is very important for this pack because all components are tied back to Saving somehow.

**Watch these two videos**:

1. [Classic FPS Pack Saving Tutorial](https://youtu.be/mdo683qLLuY)
2. [Saving System Coding Tutorial](https://www.youtube.com/watch?v=LqrdAKjftOM&t=0s)

**The Save Manager works by the following principles**:

1. Every object that you want to save in the scene contains a class derived from the provided State.cs class
2. The State class contains functions that tell the SaveManager how to serialize and deserialize this asset
3. On Save the Save Manager goes through all the States in the scene and saves them to a file
4. On Load the Save Manager goes through all the States in the scene and finds the corresponding file in the disk and loads them back in

   The process of finding which file corresponds to a given state is determined by the UID of that state.

   That is defined within the State class as well.

The Save Manager doesn't worry about what information is saved, it just handles the process of saving and loading.

The Save Manager can save to two different formats by default, **Plain Text** and **Binary Encrypted**. Plain Text is for testing and you can see what has been saved, Binary Encrypted is for production, it ensures no one tampers with the data.

## Settings

These settings can be changed on the script within the GameManager GameObject.

By default the saves are located in the [Application.persistentDataPath](https://docs.unity3d.com/ScriptReference/Application-persistentDataPath.html)

### General

Here are some other General variables that need to be assigned, the demo will have these pre-defined:

1. **binary**: Whether or not it is a binary saving system.

2. **overrideSavePath**: String of where you should save if you don't want to use persistent data path.

3. **usePersistentDataPath**: If this is true then the overrideSavepath will be ignored.

4. **testing**: If testing is true, then you can use two selected keys to load and save on demand without the need for an interaction.

   The default buttons for saving and loading are C and V. You can change these on the Save Manager script as well.

5. **ensureUniqueIds**: This will throw an error instead of a warning about any duplicate IDs in the scene.

## Static Functions

Static functions can be accessed by :

```C#
SaveManager.StaticFunction()
```

You can use these anywhere where the SaveManager is present to save/load as you need.

### Loading

1. **LoadLevelContents()**: Load all the states in the current scene with a small delay.

2. **LoadStateFromFile(State state, bool force)**: Load the state of only one file from the disk, if force is false then it will follow the rules of `state.ShouldLoad()`

### Saving

1. **SaveAllAsync()**: Save all states in the current scene asynchronously, this saves in the background but spreads it out over multiple frames as to prevent the game from lagging/stopping.

2. **SaveAllSynchronous()**: Saves all states immediately before continuing the game.

3. **SaveStateToFile(State state, bool force)**: Save a single state to file.

4. **EnsureSafeSaving ()**: If you called SaveAllAsync() but the player is about to die or the scene is about to switch, ensure that the saving is completed before continuing the game.

### Clearing

1. **ClearAllSaves()**: Clear all the saves.

2. **ClearLevelSaves(string sceneName)**: Clear all the saves for the current level, note that this only works when you follow the naming convention for the States' UID.

   `(gameObject.scene.name+"_"+gameObject.name+"_"+(this.GetType().Name));`

   The most important part is that the states' UID starts with the scene name followed by an underscore. Everything else is optional.

   If a State is global, this does not need to be followed; global meaning the state should be loaded across multiple scenes, such as a player's health.

### Querying Information

1. **GetSavingDataPath()**: Where are the saves being held.

2. **ProcessedUID(State state)**: Returns the UID of the state after it has been processed, if `binary` is true then the output will be an encrypted state UID.

3. **HasSaveFiles()**: Returns if has any save files at all.

4. **HasSaveFilesForScene(string scene)**: Returns if there are any save files for this current scene.

5. **HasSaveFilesForState(State state)**: Returns if there are any save files for the state.

6. **FindAllStates()**: Find all the states in the scene, it is important you use this function as `GameObject.FindObjectsOfType<State>()` will not find disabled objects.

7. **DebugWarningsUniqueStateIDs()**: This will scan the scene for any duplicate IDs and throw an error or warning about this depending on `ensureUniqueIds`.
