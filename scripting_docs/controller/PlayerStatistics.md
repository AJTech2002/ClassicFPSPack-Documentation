# Player Statistics

Player Statistics is based off the `State` class, this means it is tracked by the Save Manager and hence saved/loaded when a scene is loaded.

More information about how saving/loading works can be found in the [Save Manager](../managers/SaveManager) reference.

The **UID** of the PlayerStatistics class is simply _"PlayerStats"_, since it does not have the scene name in the UID it is not dependent on the current scene. This means any information tracked in this state will remain throughout different scenes.

## Public Variables

These variables can be changed to modify the initial state of the Player:

1. **maxHealth**: The maximum health the Player can have, the Player will start with this amount of health & health pickups won't increase health past this amount.

2. **playerOptions**: This is the default state of the Player, you can change these variables however if there is a save file then this will be changed to those values.

### Health Resetting

The Health is reset back to the Max Health in the following scenarios:

1. Player Dies & Respawns (Handled in PlayerStatistics Death function) - all information goes back to last save.

2. The Player switches Level through the LevelSwitcher component (there is an option to disable resetting health on moving to another level)

## Public Functions

These functions can be used to find out information & change the state of the player. They can be accessed through the following:

```C#
GameManager.PlayerStatistics.PublicFunction();
```

1. **CollectKey(string keyID)**: Allows Player to pickup a key.

2. **HasKey(string keyID)**: Checks if Player has a given key.

3. **UpdateUI()**: Updates the UI relating to the health & coin variables stored in the player.

4. **TakeDamage(float damage)**: Allows player to take a certain amount of damage and handles the death condition & SFX as well.

5. **Death()**: Kills the player. If there is an existing save it goes back to that save as 'respawn' behaviour; if there isn't nothing happens; you will have to implement this logic.

   It is highly recommended that the death function is changed to suit the needs of your game.

## Tracked Information

The Player Statistics script tracks the following information:

- The health of the Player
- The number of coins the Player has
- The guns the Player has picked up
- The keys the Player has collected

These are stored in the `Stats` struct.

### On Save

When the state is saved the following is executed:

- Save all the collected weapons
- Save all the information such as health, coins & keys

### On Load

When the state is loaded the following is executed:

1. Find all saved weapons and equip them onto the Player
2. Find all saved keys and collect them
3. Update the UI
4. Play spawn noise
5. Tell the Player Controller that the Player Statistics is loaded
