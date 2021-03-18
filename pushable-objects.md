## Pushable Objects

By default Players cannot move Rigidbodies, this is because the Player object does not have a Rigidbody itself as the character is completely controlled without Unity's Physics.

So how do we allow a Player to push a Sphere or Cube across the ground? The **Player Physics** Component has a feature that detects any Colliders that it has intersected with using the ```OnControllerColliderHit(ControllerColliderHit hit)``` method. 

Once the Collision detection has been found we do the following checks:

1. Does the Collision object have a Rigidbody
2. Does the Collision object have a **PushableObject** Component

If these conditions are met then we push the collided Rigidbody in the movement direction of the Player.

Now take a look at the **Player Physics** Component on the Player, this also affects how Pushable objects are affected.

![Replaced Force.png]({{site.baseurl}}/Replaced Force.png)

There are a few things that contribute to how much the Pushable objects are affected by a collision:

1. The **Push Power** variable, this determines how much force to apply to the Object that you are pushing up against. This can determine how quickly the Object reaches the **Pushable Object Velocity Max**.

2. The **Pushable Object Velocity Max**, this determines the max velocity that the Player can impart on another Object. If this is not limited then the Player can add infinite force to an Object.

3. The **Speed** of the Player

4. The properties of the **Rigidbody** attached to the Pushable object

  - The Mass of the Rigidbody that the Player is trying to push
  - The Angular Drag of the Rigidbody that the Player is trying to push
  - The Drag of the Rigidbody that the Player is trying to push

## Creating a Pushable Object

![23_Final_Inspector_Iteration.png]({{site.baseurl}}/23_Final_Inspector_Iteration.png)

For example, you want a simple cube that you can push on the ground. Simply create a **Cube** GameObject, then follow these steps:

1. Assign the **PushableObject** Component to the object

	- You can modify the ***Velocity Drag*** to individually affect the different axis' Drag __after__ the Player loses contact with the object (can prevent sliding effect).

        
2. Ensure there is a Collider on the object

	- A **primitive** Collider is recommended here (Cube, Sphere, Capsule) as the forces can behave unrealistically on more complex geometry. 
    
3. Ensure there is a Rigidbody on the object

	- If you want the Cube to just move along the surface of the ground then you can ***Freeze Rotation*** on the ***X*** and ***Z*** axis. 
    
    - If you don't want the Cube to rotate too much then you can bump up the ***Angular Drag***.
    
The GameObject would behave something like this:

![pushable_drag.gif]({{site.baseurl}}/pushable_drag.gif)

## Drag Forces

Drag determines how much the velocity drops per frame if the object is left in motion. There are two drag forces available to change:

1. Angular Drag - This affects the speed of rotation after the Player loses contact
2. Drag - This affects the speed of movement after the Player loses contact

**Angular Drag** can be changed directly through the **Rigidbody** Component, increasing it will slow down rotation after Player loses contact.

**Drag** can also be changed directly through the **Rigidbody** Component, however it will affect all the axis of movement. So, even when the Cube drops from a height it will appear to 'float' downward. This won't look great. 

To fix this, the **Pushable Object** Component has a slider of grag for each axis of movement. In the case of the Cube, we only want Drag to affect the **X** and **Y** axis. We can now do this!

Let's modify a couple of settings and see how it looks.

![grounded_move_2.gif]({{site.baseurl}}/grounded_move_2.gif)

Now I have modified the Cube to contain the following properties:

1. ***Angular Drag*** on **Rigidbody** has a value of **10** instead of **4** which means it will rotate slower after the Player loses contact.

2. **Pushable Object** Component has been modified to have the following properties:

![INDIVIDUALAXIS.png]({{site.baseurl}}/INDIVIDUALAXIS.png)

Note that even a small Drag of **5** on the **X** and **Z** Axis is sufficient to prevent the slipping.

## Premade Prefabs

If you want a good starting point for your Pushable objects, you can use the following:

1. Cube that can slide across the ground
2. Wall that can be knocked over
3. Sphere that can be rolled

You can look in ***Assets/Prefabs/Pushable Prefabs*** to find these prefabs.

## Optimisations

The **Pushable Object** script is heavily optimised, it does __not__ have an ``Update()`` function, it only runs when the Player is pushing the object, so a scene can contain many Pushable objects.
