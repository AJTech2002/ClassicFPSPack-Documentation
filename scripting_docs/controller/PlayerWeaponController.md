# Player Weapon Controller

The Player Weapon Controller handles the interaction between the input of the player and the weapons system, it also handles any requests & queries related to Weapons.

The Player Weapon Controller is found on the Player Controller object alongside the Player Controller.

## Public Variables

These variables will control the behaviour of the Weapons system:

### References

1. **weaponSoundSource**: The AudioSource of the Weapons, this is held on the _Gun Mount_ GameObject on the Player Controller.

2. **defaultWeapons**: List of Default Weapons that should be added to the Player, these are UID's of the Weapons on the WeaponManager.

3. **weaponMount**: The GameObject on which the Weapon's will be spawned.

4. **defaultCrosshair**: The default crosshair icon that will be used when a weapon is _not_ equipped.

### Input

These have been pre-created to work with the number mappings & scroll values; however you can modify these:

5. **numberKeys**: The input maps for all the number keys (premade).

6. **scrollTolerance**: The 'amount' of scroll required to switch to the next weapon.

7. **scrollWheel**: The scroll wheel input.

## Public Functions

Public functions can be accessed by :

```C#
GameManager.PlayerWeaponController.PublicFunction();
```

Here are some of the core public functions:

1. **ChangeWeapon (int selected)**: Changes the currently holding weapon to the weapon at the 'selected' index on the _collectedWeapons_ list.

2. **UpdateUI()**: Updates the Weapon related UI (Weapon Image, Ammo Count).

3. **CollectWeapon (string ID)**: Collect a weapon given an ID; this method ensures the weapon has not already been collected and does other cleanup logic.

4. **CurrentHoldingID()**: Get the ID of the gun that the Player is currently holding.

5. **GetCurrentWeapon()**: This gets the WeaponReference of the currently spawned weapon.

6. **HasActiveWeapon()**: Returns true/false depending on whether the Player has an active weapon.

7. **GetWeapon (string UID)**: Returns the actual Weapon Component on the spawned weapon given the UID.

8. **GetActiveWeapon ()**: Get the actual Weapon Component on the currently spawned weapon.

9. **UnequipWeapon()**: Unequip the weapon the Player is currently holding.

10. **DirectEquip()**: Equip the weapon that the _currentlyHoldingIndex_ is on.

11. **EquipWeapon (float delay)**: Equip the current weapon with a delay.

12. **ChangeCrosshair (Sprite crosshair)**: Change the crosshair of the player.

13. **RevertCrosshair ()**: Revert back to default crosshair.

14. **nextAvailableIndex(int from)** and **previousAvailableIndex(int from)**: Given an index, give the next/previous available weapon index.
