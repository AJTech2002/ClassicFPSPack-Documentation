# Drone Enemy

The Drone Enemy script is only used on one demo enemy, the Drone Enemy; the Drone Enemy is able to fly above in the air and shoot homing missiles at the Player.

This class derives from the `Enemy` script so the properties and methods from that script can be used here.

## Public Variables

1. **aimSpeed**: Speed at which drone can lock onto the Player.

2. **followSpeed**: Speed at which the drone can follow the Player.

3. **stoppingRadius**: Radius at which the drone stops from the Player.

4. **injuryDelay**: Delay of each projectile shot.

5. **hitCollider**: This is the collider of the drone, the center of the collider needs to be relaigned with the geometry each frame to ensure the collisions remain working.

6. **geometry**: The visual geometry of the Drone.

7. **projectilePrefab**: Prefab that will be spawned as the Projectile.

8. **projectileSpawnPoint**: The spawn point of the Projectile.

## Functionality

The `Follow()` method is called when the Player is in the trigger on Update and the agent's location is set to the Player; all animations are triggered and shooting is triggered from this method as well.

The `Update` loop is in the `Enemy` script from which this script is inherited from.
