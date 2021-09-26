# Weapon

The weapon class is a template for which all Weapons in the Classic FPS Pack should be based on. It provides base settings and empty methods to override when creating new weapons.

It is a MonoBehaviour script and any class derived from Weapon should lie on the root GameObject of the Weapon prefab.

The Weapon also is derived from `State`, this means that every weapon will be tracked by the `SaveManager`.

The UID of the Weapon State is the same as the UID of the Weapon.

## General

On Awake, the Player Weapon Controller will call the Weapon Manager which will spawn all the Weapons and call the `Setup()` method.

The default `Setup()` method sets the UID of the Weapon & Loads any states of the weapon manually.

## Public Variables

The UID of a Weapon is set in the [`WeaponManager`](../managers/weaponmanager.md).

To access a Weapon's public variable you should access it through the Player Weapon Controller:

```C#
//Getting pistol weapon
GameManager.PlayerWeaponController.GetWeapon ("Pistol").publicVariable;
```

There is only one key public variable inside the Weapon Class:

1. **settings**: This is a `WeaponSettings` class and it contains the core settings that every weapon needs to include for the UI & Logic to be functional.

### Settings

These are the settings inside the `settings` variable:

1. **overridePicking**: Whether or not to disable default object pickup while using this weapon, this will be set to false unless it is a weapon like Gravity Gun.

2. **requiresAmmo**: Does this weapon require tracking of ammo?

3. **defaultAmmo**: Default ammo amount.

4. **thumbnail**: The icon for the weapon that will show up in the bottom right corner of the UI.

5. **crosshair**: The icon for the crosshair when this weapon is equipped.

6. **crosshairSize**: The size of the crosshair when it is created.

7. **crosshairScaleOnTarget**: How much to scale the crosshair when it is hovering over an object to pickup.

## Tracked State

The Weapon is also constantly tracking its own state so when it is time to save and load it has the data needed.

The state is tracked in the **weaponState** variable, there are only two things tracked for the default weapon; more can be added in derived classes by overriding `SaveState() and LoadState()`.

The Weapon State tracks:

- UID of the Weapon
- ammoRemaining

Whenever the shooting action is triggered ensure to modify the state so that it is tracked.

## Override Functions

These functions should be overriden by classes that are derived from the `Weapon` class, for example the `BaseWeapon`.

1. **Equip (string UID)**: This function is called when the weapon is equipped, any equipping logic should be done here.

2. **Unequip ()**: This function is called when the weapon is unequipped.
