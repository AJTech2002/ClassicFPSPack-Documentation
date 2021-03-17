## Player Input

Knowing how to configure the **PlayerInput** is very important, the **PlayerInputManager** simply listens to any events triggered by the **PlayerInput** Component. However, the keys that trigger these events can be defined by you.

Currently these are the controls:

1. **WASD** : Movement along two axis (forward/backward and left/right)
2. **Shift** : Increases the Player speed to sprinting
3. **Space** : Performs the Jump movement

However, what if you need to support this Player on a different system?

To solve this problem the Player utilises the new **Unity Input System**, you can learn in a lot more detail about it [here](https://www.raywenderlich.com/9671886-new-unity-input-system-getting-started).

Place your attention on the Inspector window and find the **PlayerInput** Component.

![9.png]({{site.baseurl}}/9.png)
