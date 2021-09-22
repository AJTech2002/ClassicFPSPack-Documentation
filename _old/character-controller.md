## Character Controller

The **CharacterController** is a component provided by Unity that provides some collision and movement logic that is executed in the background, however it is important to know the values that have been exposed to the Inspector so that we can modify how the Player reacts to its environment.

Find the Component in the Inspector.

![5.png]({{site.baseurl}}/5.png)

Let's break down the properties given to us:

- **Slope Limit**: This is a very important property, basically it tells the controller; if the Player is standing on a slope that exceeds the angle in this property then restrict movement and begin sliding down the slope.

![6.png]({{site.baseurl}}/6.png)

- **Step Offset**: This property determines the maximum height of an object for which the Player can simply 'step' over, or continue on its current motion uninterrupted.

The remaining properties aren't that important and won't need to be configured, the **Radius** should be set to **0.5** and the **Height** is usually set to **2**.
