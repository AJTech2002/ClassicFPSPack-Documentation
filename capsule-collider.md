## Capsule Collider

The primary purpose of the Capsule Collider is to ensure that the Player does not get stuck in walls, hence its size and width will vary to the rest of the controller.

For reference, lets compare the default configuration of the **Capsule Collider** with the **Character Controller** (which is also shaped like a Capsule).

![4.png]({{site.baseurl}}/4.png)

Note that there are ***2*** capsules overlapping, the top most capsule is the Capsule Collider, note that it is around half the height of the Character Controller and the radius is slightly larger than the Character Controller. 

You can think of the Character Controller as the 'true' size of the Player while the Capsule Collider is simply a protective bubble around the Player preventing it from getting stuck in things. For this reason the Collider has to have a slightly larger radius than the Character Controller. 

But why is it only half the height? This is because when we are trying to step over things we don't want our Capsule Collider pushing us away from them. For example if we need the Player to climb some small pebbles, the Capsule Collider might intersect with those rocks and cause some slight jittering. The only time we want to use the Capsule Collider is if we are stuck in a wall, and for that case it can be floating well above the ground.
