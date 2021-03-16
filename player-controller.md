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

