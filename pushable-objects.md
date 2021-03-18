## Pushable Objects

By default Players cannot move Rigidbodies, this is because the Player object does not have a Rigidbody itself as the character is completely controlled without Unity's Physics.

So how do we allow a Player to push a Sphere or Cube across the ground? The **Player Physics** Component has a feature that detects any Colliders that it has intersected with using the ```OnControllerColliderHit(ControllerColliderHit hit)``` method. 

Once the Collision detection has been found we do the following checks:

1. Does the Collision object have a Rigidbody
2. Does the Collision object have a **PushableObject** Component

If these conditions are met then we push the collided Rigidbody in the movement direction of the Player.

Now take a look at the **Player Physics** Component.

![Replaced Force.png]({{site.baseurl}}/Replaced Force.png)

There are a few things that contribute to how much the Pushable objects are affected by a collision:

1. The **Push Power** variable, this determines how much force to apply to the Object that you are pushing up against. This can determine how quickly the Object reaches the **Pushable Object Velocity Max**.
2. The **Pushable Object Velocity Max**, this determines the max velocity that the Player can impart on another Object. If this is not limited then the Player can add infinite force to an Object.
2. The current speed of the Player, the full **Push Power** will be used when the Player is sprinting.
3. The mass of the Rigidbody that the Player is trying to push
4. The drag of the Rigidbody that the Player is trying to push

## Creating a Pushable Object

![22.png]({{site.baseurl}}/22.png)

For example, you want a simple cube that you can push on the ground. Simply create a **Cube** GameObject, then follow these steps:

1. Assign the **PushableObject** Component to the object
2. Ensure there is a Collider on the object
3. Ensure there is a Rigidbody on the object
	- If you want the Cube to just move along the surface of the ground then you can ***Freeze Rotation*** on the ***X*** and ***Z*** axis. 
    
The GameObject would behave something like this:

![pushable_drag.gif]({{site.baseurl}}/pushable_drag.gif)

Notice how the Rigidbody is sliding at the start, if you want to remove that then increase the ***Velocity Drag*** on the **PushableObject** Component. What does that do you ask?

The **Pushable Object** Component is to ensure (most of the time) that the object behaves naturally after a collision, so the ***Velocity Drag*** variable controls how much Drag Force the Object recieves __after__ the Player loses contact with the object.

For example if the ***X*** of the ***Velocity Drag*** is set to ```0.99``` then every frame after the Player loses contact the object will lose 1% of it's current speed on the ***X*** axis. If you set it to ```0.0``` then the instant the Player loses contact with the object the velocity on the ***X*** axis will become 0.

This is useful because you can prevent sliding on 2 axis while allowing the object to drop naturally without drag affecting the ***Y*** axis.

![grounded_move_2.gif]({{site.baseurl}}/grounded_move_2.gif)

Now that I have some ***Angular Drag*** and ***Velocity Drag**, you'll notice that the Cube is a lot more grounded and doesn't slide. 

## Existing Prefabs

If you need demos on how to make the following :

1. Cube that can slide across the ground
2. Wall that can be knocked over
3. Sphere that can be rolled

You can look in ***Assets/Prefabs/Pushable Prefabs***.


