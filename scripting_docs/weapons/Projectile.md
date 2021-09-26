# Projectile

The Projectile script is attached to all projectiles within the Classic FPS Pack, mainly in the following instances:

1. Player Rocket Launcher Projectile
2. Enemy Bullet Projectile
3. Enemy Homing Missile Projectile

## Layers

When you use the Classic FPS Setup Editor the following layers and properties are imported:

1. "Projectile" layer
   - Cannot collide with other Projectiles
2. "Enemy Projectile" layer
   - Cannot collide with other Enemy Projectiles
   - Cannot collide with Enemies

## Public Variables

These variables can be modified to change the behaviour of the projectile.

1. **damage**: The damage that the Projectile does on impact.

2. **canHarmPlayer**: Can cause damage to the Player.

3. **canHarmEnemies**: Can cause damage to Enemies.

4. **doesExplode**: Does it affect nearby objects on impact/destory.

5. **explosionForce**: Force of explosion onto Rigidbodies.

6. **upwardsForce**: How much upwards force does the explosion cause.

7. **explosionRadius**: Radius at which Rigidbodies are affected by the projectile.

8. **minimumImpactVelocity**: Minimum velocity to impart onto Rigidbodies on contact.

9. **minimumVelocityBeforeDestruction**: Minimum velocity before the projectile destroys itself because it is coming to a stop.

10. **stickToImpact**: Stick to the first surface the Rigidbody impacts; if this is a sticking projectile, then the collider should be a trigger.

11. **timeToImpact**: Time to destroy after sticking to surface.

12. **isHomingMissile**: Is this projectile a homing missile (will follow the player).

13. **destroyAfter**: Time after to destroy the projectile by default.

14. **moveSpeed**: Speed at which to chase the player.

15. **explosionSound**: SFX of explosion.

## Functionality

On Collision Enter the Projectile will explode and call the `Impact` function which will handle all the different cases of explosions:

1. Players nearby - Destroy/Damage them
2. Enemies nearby - Destroy/Damage them
3. Pushable Objects nearby - Move them away
4. Breakable Objects nearby - Destroy/Damage them
5. Rigidbodies - Move them away

On the `Update` method the projectile follows the player if it is a homing missile. It also checks if the Projectile drops velocity below **minimumVelocityBeforeDestruction**. if so it will detonate.
