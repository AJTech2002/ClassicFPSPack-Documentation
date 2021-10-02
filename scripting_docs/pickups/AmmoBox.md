# Ammo Box

Ammo Box derives from `Pickup`, so it tracks the state of whether or not this item has been picked up.

**Note: This item needs a trigger.**

The ammo affects the weapon given the public variables and appends ammo to it, there is no set max limit to weapon ammo.

It is a prerequisite that the Player has picked up the weapon.

Once it picks up the ammo, the SFX is played, ammo is adjusted in the state of the weapon and the UI is updated.

## Public Variables

1. **ID**: The ID of the weapon, in the Inspector this should show as a drop down; if it doesn't then enter the ID of the weapon in the WeaponManager.

2. **isUniversalAmmo**: This ammo will be appended to whatever weapon is being currently held by the Player, this will disregard the `ID`.

3. **pickupAmount**: The amount of ammo to pickup.
