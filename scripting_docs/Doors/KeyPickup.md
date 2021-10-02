# Key Pickup

This is a class derived from the [`Pickup`](../pickups/Pickup.md) class so it tracks the state of whether or not this item has been picked up.

**Note: This item needs a trigger.**

This will pickup a new key and add it to the collected keys, then these keys can be used to open doors.

The keys are appended through the `PlayerStatistics` script using the `CollectKey(string keyID)` function.

## Public Variables

1. **keyReference**: ID of the Key that this pickup should give to the player, the ID has to be something in the Key Manager; there should be a drop down to select.
