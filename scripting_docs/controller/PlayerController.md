# Player Controller

The **PlayerController** Component is the 'brain' of the whole player, it joins together the input, physics, logic all into one script. It's very easy to setup and configure.

### Public Variables

- **Forward Direction**: Just a reference to the **_ForwardDirection_** GameObject in the Hierarchy.

- **Camera**: Just a reference to the **_Camera_** GameObject in the Hierarchy.

- **Walk Speed**: The default speed for the Player.

- **Sprint Speed**: When the key to enable sprinting is pressed, this will become the new speed.

- **Jump Speed**: The initial speed of the Jump that will be sent to the Player when the key binded to the Jump is pressed.

- **Slope Slip Speed**: The speed of the Player when it is standing on a slope that exceeds the **_slopeLimit_** defined in the **CharacterController**. The speed controls how fast the Player slips down a slope.

### Public Methods

What if you want to modify the functionality of the Player Controller yourself, or if you want to use some of the information captured by the controller?

First get a reference to the **PlayerController**, then you can access the following functions and variables using a format like this:

```C#
GameManager.PlayerController.publicFunction(arguments);
```

Here are the most important ones:

1. **isStrictlyGrounded()** : This tells you precisely if the Player is grounded, it is extremely accurate and hence will be false even on the slightest detachment from the ground.

2. **isApproximatelyGrounded()** : This tells you if the Player is standing on some type of stable grounding, this is the function that is used for the **_Jump_** functionality. This is done because we need the player to be grounded but if we wait for extreme accuracy then the Player may not be able to jump on rough surfaces.

3. **ApplyVerticalForce (float forceAmount)** : This simply applies an immediate vertical force which will eventually be brought down by gravity.

4. **ApplyForce (Vector3 force)** : If you have some object that needs to exert some force on the player then you can use this, the input of the Player will still be active so they can fight the force.

5. **ApplyImpulseForce (Vector3 force)** : Should be used if you need to exert an immediate and impulsive force that overrides the input.

6. **EnablePlayer()** and **DisablePlayer()** : If for any reason you need to disable/enable the Player then you can use this, no inputs, movement etc. will function anymore. This is useful in situations such as climbing up a vertical wall for a wall climbing system, as the Player Controller will actively prevent you from doing that.

7. **isStandingOnSlope()** : Returns whether or not the Player is currently standing on a slope that exceeds the **_slopeLimit_** assigned in the **CharacterController**.

8. **bottomOfPlayerController()** : Returns a `Vector3` telling you where the exact bottom of the Player is, this can be useful if you want to make your own ground checks.

9. **TeleportPlayer(Vector3 newPosition)**: Moves the Player to a new position immediately.

### Public State Variables

These variables are public however they are intended to be used to understand the state of the Player Controller.

1. **groundHit** : This is a `RaycastHit` variable that returns information about the current ground of the Player.

2. **characterSpeed** : The current speed of the character, it fluctuates between the **_walkSpeed_** and **_sprintSpeed_**.

3. **hasJumped** : Whether or not the Player is performing a Jump.

4. **lastVelocity**: Last known velocity of the Player (last frame).

5. **airTime**: How long the Player has been in the air, it's used to determine when to play the landing sound.

There are a lot more exposed variables that you can use to determine the state of the Player Controller, take a look through the code.

### Saving & Loading

After a state has been loaded on a Player Controller it calls the following function:

`if (GetComponent<PlayerController>()) GetComponent<PlayerController>().AccumulateSaveState();`

The `AccumulateSaveState()` on the `PlayerController` will tell the Player Controller that the loading process has been completed; when both the Transform State and Player Statistics state complete loading the Player Controller will fade out the loading screen.

This will ensure there is no jittering when the Player Controller is teleporting when loading in.

The two states that are on the Player Controller are:

1. **Transform State**: Tracks player position & camera rotation
2. **Player Statistics**: Keys, Health, Weapons etc.

Both of these have to complete loading before the loading screen is released (or no saves to load).

Take a look at the UIManager to change loading screen behaviour.

---

The script within the Player Controller is very complex and it split into the different logical components, if you need any advice on how to modify the script please contact me:

ajays.workemail@gmail.com
