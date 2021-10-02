# Pickup

The Pickup class is a base class that is extended to create other pickups such as:

- Health Pickup
- Weapon Pickup
- Coin Pickup
- Key Pickup
- Ammo Pickup

The Pickup is also derived from [`State`](../saving/State.md) therefore it is tracked by the SavingManager.

The Pickups will usually need a Trigger Collider in order to work.

## Public Variables

1. **requiresSaving**: Whether or not to save the State of the pickup.

2. **allowRespawn**: Should allow respawn of object even after it has been picked up (on next scene load).

3. **collectSFX**: SFX to play when the item is collected.

## Public Functions

These functions are designed to be called from the scripts derived from `Pickup`.

1. **EnableObject (bool render)**: This sets the Enabled state of the object, if `render` is false then it won't show the object and if it is true then it will.

2. **RunSFX()**: Runs the collection SFX.

3. **WeaponPickupAnimation**: If the weapon you have has a pickup animation, this will trigger that.

## Tracked State

The only tracked state in the Pickup is `enabled`, in other words whether or not the object has been picked up. This ensures a health pack does not keep respawning everytime the player opens/closes the game to get infinite health.
