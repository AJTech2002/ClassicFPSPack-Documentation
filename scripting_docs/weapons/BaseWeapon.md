# Base Weapon

The Base Weapon is derived from the [`Weapon`](Weapon.md) class. The Base Weapon is less abstract than the Weapon class and manages some default functionality such as managing the animator, handling unequipping/equipping logic and opening up some other general functionality.

## Responsibilities

The responsibilities of this script are to provide some common functionality that can be used in child classes, and to handle the equipping/unequipping logic especially in terms of animations.

## Public Variables

The Base Weapon is what the default weapons provided in the pack are based off. In addition to the settings described in the `Weapon` class, there are a few additional settings in the `BaseWeapon`.

Here are the public variables you can tweak to modify the weapon behaviour, these should be done on the prefab.

1. **shootSounds**: A list of sounds that will be emitted at random from the gun on shoot.

2. **emptyAmmoSound**: Sound to play when Player shoots without any ammo.

3. **disableDelay**: The delay before weapon is disabled (allows disable animation to play)

4. **enableDelay**: Delay before weapon is fully enabled and allowed to shoot (allows enable animation to play)

5. **disableBeforeEnableAnimation**: The time to wait before playing enable animation, allows previous weapon to disable before starting this weapon's animation.

## Override Methods

Note that `BaseWeapon` itself is a base class and should be overriden by other classes.

Some methods to override are:

1. **OnGunEquipped()**: What to do after the weapon has been equipped fully (animation played & completed).
2. **OnGunUnequipped()**: What to do after the weapon is completely unequipped.

## Protected Methods

Methods to call from derived classes of `BaseWeapon`.

1. **ToggleVisibility (bool value)**: Visibility of all mesh renderers beneath the Weapon.

2. **SetState (WeaponState newState)**: Allows you to change the state of the current weapon.

3. **RunShootAnimation()**: Runs the shoot animation and the sound associated with shooting.

4. **RunNoAmmoAnimation()**: Runs no ammo animation and SFX.

5. **HandlePlayerAnimate()**: This function should be called from the `Update()` function of any class deriving from `BaseWeapon`, it will determine when to play the walk animation & the speed of the walking animation.

6. **HandlePlayerPickup()**: What do do when the player picks up an item.

7. **ResetAnimator()**: Disable the animator for the current weapon/reset it.
