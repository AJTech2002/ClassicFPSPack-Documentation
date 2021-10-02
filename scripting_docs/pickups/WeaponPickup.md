# Weapon Pickup

Weapon Pickup derives from `Pickup`, so it tracks the state of whether or not this item has been picked up.

**Note: This item needs a trigger.**

This appends the weapon of this pickup to the collected weapons in `PlayerWeaponController`, this is done with the function `playerWeaponController.CollectWeapon(GunID);`.

This item will only be collected when the weapon has not already been picked up; you cannot have multiple of the same Gun.

When a player picks up a weapon with an ID, all Weapon Pickups harbouring that ID will dissapear, you can change this in the CollectWeapon function on PlayerWeaponController.

## Public Variables

1. **GunID**: The ID of the weapon, in the Inspector this should show as a drop down; if it doesn't then enter the ID of the weapon in the WeaponManager.
