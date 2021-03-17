## Pushable Objects

By default Players cannot move Rigidbodies, this is because the Player object does not have a Rigidbody itself as the character is completely controlled without Unity's Physics.

So how do we allow a Player to push a Sphere or Cube across the ground? The **Player Physics** Component has a feature that detects any Colliders that it has intersected with using the ```OnControllerColliderHit(ControllerColliderHit hit)``` method. 

Once the Collision detection has been found we do the following checks:

1. Does the Collision object have a Rigidbody
2. Does the Collision object have a **Pushable** tag

If these conditions are met then we push the collided Rigidbody in the movement direction of the Player.

Now take a look at the **Player Physics** Component.

![Player Physics Updated.png]({{site.baseurl}}/Player Physics Updated.png)

There are a few things that contribute to how much the Pushable objects are affected by a collision:

1. The **Push Power** variable, this determines how much force to apply to the Object that you are pushing up against.
2. The **Pushable Object Velocity Max**, this determines the max velocity that the Player can impart on another Object. If this is not limited then the Player can add infinite force to an Object.
2. The current speed of the Player, the full **Push Power** will be used when the Player is sprinting.
3. The mass of the Rigidbody that the Player is trying to push

## Creating a Pushable Object

![PushableObject.png]({{site.baseurl}}/PushableObject.png)

For example, you want a simple cube that you can push on the ground. Simply create a **Cube** GameObject, then follow these steps:

1. Assign the **Pushable** tag to the object
2. Ensure there is a Collider on the object
3. Ensure there is a Rigidbody on the object
	- If you want the Cube to just move along the surface of the ground then you can ***Freeze Rotation*** on the ***X*** and ***Z*** axis. 
    - If you want to ensure there is no 'sliding' effect, you should increase the ***Drag*** of the Rigidbody. 
    
The GameObject would behave something like this:

![pushable_drag.gif]({{site.baseurl}}/pushable_drag.gif)


Notice how the Rigidbody is sliding at the start, if you want to remove that then increase the ***Drag*** of the Rigidbody and you will get behaviour more like this:


