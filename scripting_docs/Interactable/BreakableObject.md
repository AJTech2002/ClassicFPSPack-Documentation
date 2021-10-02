# Breakable Object

A Breakable Object is derived from `DamageableEntity` meaning its health is tracked and it is able to take damage and eventually die.

Breakable Objects are items such as Crates that can be attacked by weapons or be destroyed by throwing them.

Damageable Entities including this one are able to drop objects on their death, and play death and damage SFX.

## Public Variables

Most of the public variables are drawn from the `DamageableEntity` script; however there are a few variables:

1. **damageVelocityMultiplier**: The amount to multiply the velocity of the object on impact to take damage with.

2. **minimumVelocityForImpact**: Minimum amount of velocity needed to take damage.
