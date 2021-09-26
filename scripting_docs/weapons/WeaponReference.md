# Weapon Reference

The Weapon Reference is used in the Weapon Manager as a way to represent Weapons before they have been spawned into the game.

## Core Propreties

1. **WeaponUniqueID**: The UID of the Weapon that is used everywhere to represent the Weapon.
2. **WeaponPrefab**: The Weapon Prefab that is linked to the UID, the prefab should contain [`Weapon`](Weapon.md) component in it's root.
3. **keyBindNumber**: Number to link to the weapon (0-9), if it is -1 it won't be included in keyBind.

   It will still work with Scroll Wheel without key bind. You can also attach a custom way to equip this weapon through looking at the [`PlayerWeaponController`](../controller/PlayerWeaponController.md) documentation.
