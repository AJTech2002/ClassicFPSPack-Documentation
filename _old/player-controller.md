## Player Controller

The **PlayerController** Component is the 'brain' of the whole system, it joins together the input, physics, logic all into one script. It's very easy to setup and configure.

![7.png]({{site.baseurl}}/7.png)

Let's run through the different properties:

- **Forward Direction**: Just a reference to the ***ForwardDirection*** GameObject in the Hierarchy. 

- **Camera**: Just a reference to the ***Camera*** GameObject in the Hierarchy.

- **Walk Speed**: The default speed for the Player.

- **Sprint Speed**: When the key to enable sprinting is pressed, this will become the new speed.

- **Jump Speed**: The initial speed of the Jump that will be sent to the Player when the key binded to the Jump is pressed.

- **Slope Slip Speed**: The speed of the Player when it is standing on a slope that exceeds the ***slopeLimit*** defined in the **CharacterController**. The speed controls how fast the Player slips down a slope.

## Exposed Functionality

What if you want to modify the functionality of the Player Controller yourself, or if you want to use some of the information captured by the controller?

First get a reference to the **PlayerController**, then you can access the following functions and variables using a format like this:

```C#

void CustomPlayerFunction () {
 
  PlayerController playerControllerReference = GetComponent<PlayerController>();
  
  //For example
  playerControllerReference.publicFunction(arguments);
  
}


```

### Exposed Functions

1. ```isStrictlyGrounded()``` : This tells you precisely if the Player is grounded, it is extremely accurate and hence will be false even on the slightest detachment from the ground.

2. ```isApproximatelyGrounded()``` : This tells you if the Player is standing on some type of stable grounding, this is the function that is used for the ***Jump*** functionality. This is done because we need the player to be grounded but if we wait for extreme accuracy then the Player may not be able to jump on rough surfaces.

3. ```ApplyVerticalForce (float forceAmount)``` : This simply applies an immediate vertical force which will eventually be brought down by gravity.

4. ```ApplyForce (Vector3 force)``` : If you have some object that needs to exert some force on the player then you can use this, the input of the Player will still be active so they can fight the force.

5. ```ApplyImpulseForce (Vector3 force)``` : Should be used if you need to exert an immediate and impulsive force that overrides the input.

6. ```EnablePlayer()``` and ```DisablePlayer()``` : If for any reason you need to disable/enable the Player then you can use this, no inputs, movement etc. will function anymore. This is useful in situations such as climbing up a vertical wall for a wall climbing system, as the Player Controller will actively prevent you from doing that. 

7. ```isStandingOnSlope()``` : Returns whether or not the Player is currently standing on a slope that exceeds the ***slopeLimit*** assigned in the **CharacterController**.

8. ```bottomOfPlayerController()``` : Returns a ```Vector3``` telling you where the exact bottom of the Player is, this can be useful if you want to make your own ground checks.

### Exposed Variables

1. ```groundHit``` : This is a ```RaycastHit``` variable that returns information about the current ground of the Player.

2. ```characterSpeed``` : The current speed of the character, it fluctuates between the ***walkSpeed*** and ***sprintSpeed***.

3. ```hasJumped``` : Whether or not the Player is performing a Jump.




