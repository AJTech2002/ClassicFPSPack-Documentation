# Classic Enemy

The Classic Enemy is used on two enemy types:

- **The Shooter Enemy**: Chases the Player and shoots projectiles at them, when it gets closes enough performs attacks.

- **The Walker Enemy**: Simply chases the Player until close enough then attacks.

This class derives from the `Enemy` script so the properties and methods from that script can be used here.

## Public Variables

1. **injuryRadius**: The radius at which the Enemy can attack the player at a close distance, this is an attack form such a punching.

2. **injuryDelay**: The delay between each attack the Enemy makes.

3. **damageByProximity**: The amount of damage the Player will take when the Enemy is attacking at close range.

4. **aimSpeed**: The speed at which the Enemy can aim their weapon.

5. **shootProjectiles**: Does this Enemy shoot any projectiles.

6. **projectilePrefab**: The projectile prefab to shoot.

7. **gunModel**: This gun model reference will point towards the player with the speed of `aimSpeed`.

8. **projectileSpawnPoint**: Spawn point of the projectile which is a child of the **gunModel** so its facing in the right direction.

9. **projectileSpeed**: Initial speed of the projectile.

## Functionality

The `Follow()` method is called when the Player is in the trigger on Update and the agent's location is set to the Player; all animations are triggered and shooting is triggered from this method as well.

The `Update` loop is in the `Enemy` script from which this script is inherited from.
