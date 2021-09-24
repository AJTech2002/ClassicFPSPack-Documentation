# Key Manager

The Key Manager is a Scriptable Object meaning it is an item that lives inside your Project. You can create a new Key Manager for your project by doing the following in the project window: 

`Right Click > Classic FPS Pack > Key Manager`

Once you have a Key Manager you can assign that in the [Game Manager](gamemanager.md) object. 

The Key Manager just stores a list of the Keys in the game through the `KeySettings` class.

So when you want to **create a new key** just add a new element to the list within the Key Manager and modify the Key Settings to your liking.

# Key Settings

The `KeySettings` class has the following properties:

- **keyID**: The Unique ID to identify the key within the project.
- **consumable**: Meaning when the key is used to open a door does it get removed from player inventory.
- **allowMultiplePickups**: Can the player hold more than one of these keys up?
- **keySprite**: The sprite of the Key that will show up on the UI.

Most of these properties are enforced in logic through the `KeyPickup.cs` script and `Door.cs` script. You can find the documentation for these under the *Door_System* namespace.

The keys the player has at any point is tracked in the `PlayerStatistics.cs` script. 