# Enemy

The Enemy is a base class that is used for the two types of default enemies in this pack; the script itself is derived from `DamageableEntity` meaning it can take damage and die.

## Public Variables

1. **trigger**: The trigger that the player enters in order to grasp the attention of the Enemy.

2. **damageByThroughObjectsMultiplier**: The damage provided to the Enemy is based on the velocity of an object thrown at it; this value multiplies that by a certain amount.

3. **agent**: The NavMesh agent that the is going to traverse over.

4. **animator**: The Enemy animator that will play its Walking & Attacking animations.

5. **graphics**: The Graphics object on the Enemy (ex. Capsule).

## Override Methods

These are the methods that can be used by classes that inherit from Enemy:

1. **Follow ()**: The behaviour when the Enemy is in the follow state; when the Player has entered the trigger.

2. **Attack (bool longRange)**: The behaviour of the attack when the player is close to the Enemy and far away.

## Functionality

It is important that the Enemy is standing on a NavMesh and the NavMesh is baked.
