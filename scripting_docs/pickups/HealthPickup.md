# Health Pickup

Health Pickup derives from `Pickup`, so it tracks the state of whether or not this item has been picked up.

**Note: This item needs a trigger.**

This affects the player's health in the `PlayerStatistics` script, then updates the UI.

## Public Variables

1. **healthPickupAmount**: Amount of health to pickup when the player moves over it, note that this will **not** be picked up when the Player already has max health.
