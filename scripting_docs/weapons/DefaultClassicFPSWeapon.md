# Default Classic FPS Weapon

The Default Classic FPS Weapon is used in all the demo weapons except the Gravity Gun. It is also derived from the [`BaseWeapon`](BaseWeapon.md) class.

## General Public Variables

- **shooting**: `DefaultClassicFPSWeapon_Shooting` is a class that stores all the logic/variables related to the shooting of these weapons. It was used to seperate the shooting logic from the input logic.

- **shootAction**: Input to begin the shooting

- **shootingThroughAnimation**: If this is 'true' then using the **shootAction** will only begin the Animation. The Animation should trigger an event to call the **AnimatorShoot()** function in this script.

  This is useful for things such as an Axe where the attack should be performed only when the axe lands on the enemy.

- **shootDelay**: Delay between attacks

- **holdShoot**: Can you shoot multiple times when the **shootAction** remains pressed.

## Shooting Public Variables

The Shooting Public variables are under the **shooting** variable.

- **hasLimitedRange**: Does this gun have a limited shooting range, meaning after a certain distance no more damage will be dealt.

- **maxShootDistance**: How far can this gun shoot, if it has unlimited range then the maxShootDistance will control the amount of damage the enemy recieves. If you always want it to be the max amount of damage, se this to `1`.

- **useSphereCast**: Use a Sphere Cast instead of a Raycast.

- **sphereCastRadius**: Radius of Sphere Cast.

- **hitMask**: All layers that can be hit from this weapon.

- **shootsProjectiles**: Does this weapon shoot projectiles? Only used in the Rocket Launcher.

- **projectilePrefab**: Prefab of the Projectile.

- **projectileStartPosition**: Start position of the projectile, this is actually a reference to an empty Transform inside your Weapon prefab that indicates the starting position/rotation of the the projectile.

- **projectileSpeed**: Initial speed of the projectile, this assumes the projectile has a Rigidbody.

- **forwardForce**: Forward force imparted on any rigidbody the Raycast shot from this gun produces.

- **maximumDamage**: Maximum damage that this weapon can impart on a `DamageableEntity`.

- **minimumDamage**: The minimum damage that this weapon can impart on a `DamageableEntity`.

- **scatter**: Should this weapon scatter its bullets (shotgun).

- **scatterBulletsInEachDirection**: Amount of bullets to scatter.

- **scatterRadius**: Radius of scatter.

- **onHitObjectSFX**: What SFX to play when this object hits any surface (ground, wall etc.). If there exists a Pushable Object script with a custom SFX that will be played instead.

## Shooting Public Functions

1. **TakeSingleShot (Camera camera, Vector2 crosshairPosition)**: Take a single shot from a given crosshair position.

2. **CreateRaycast(ref Ray ray):** Creates raycast given gun properties.

3. **ShotRay(Ray ray, RaycastHit hit)**: Shot that ray, and all the different object types are handled in this function:

   - Handle shooting Rigidbody
   - Handle shooting Pushable Object
   - Handle shooting Damageable Entity (Breakable Object, Enemies)
   - Handle shooting Projectile

   You can change this function to create different behaviour given the information in the rayast hit.

4. **AnimatorShoot()**: This function is used when the animator calls the **AnimatorShoot()** function.

## Other Public Functions

1. **Attack(Camera camera, Vector2 crosshairPosition)**: This is the general attack function, this is called directly from the inputs. This triggers the animation as well as changes the ammo count.

   This also ensures that no shooting is conducted if the weapon has run out of ammo.

## Functionality

On `Update()` the weapon shoots automatically if the Player is holding down the shoot button; it also handles Player animation such as walking.

`OnGunEquipped()` and `OnGunUnequipped()` handle the registering/deregistering of Inputs and their link to start attacks.

Note that this script is derived from `BaseWeapon` so all equipping logic, animation logic and unequipping logic is handled there.
