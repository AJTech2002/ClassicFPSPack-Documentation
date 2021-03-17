## Configuring the Camera

The Camera is primarily controlled in the **Player Camera Controller** Component on the Player, it handles the following logic:

- Capturing Mouse events through the new Input System
- Orienting the **Pivot** GameObject based on the movement of the Mouse
- Locking and Toggling Visibility of the Cursor
- Tilting the Player based on Horizontal Movement
- Increasing Field of View on Sprinting

## Cinemachine Properties

However, if we just move the **Pivot** then how is the rotation of the Camera determined? This is handled in the **CinemachineVirtualCamera** Component in the **CM VCam 1** GameObject. Let's take a look at that first. It's important to note that the **CinemachineVirtualCamera** directly controls the Camera and its properties so you won't have to work direclty with the Camera in this project.

![CINEMACHINE.png]({{site.baseurl}}/CINEMACHINE.png)

There are a lot of setting to play with here, but for a **FPS** based Camera, take a look at the options highlighted. These are the most important ones.

1. **Follow** : By attaching the **Pivot** GameObject, the Camera will follow the Pivot object. A benefit of this is that you can modify the pivot position, it is not restricted to the direct center of the Player. 

2. **Field Of View** : Controls the Field of View property on the Camera directly.

3. **Body** : This is the most important one, you will notice that the **3rd Person Follow** is selected, all this does is it rotates the Camera to look at the **Follow** object and in the direction of the **Follow** object. Hence, by modifying the rotation of the **Pivot** GameObject we also modify the Camera rotation. 

4. **Damping** : By selectin ghte **3rd Person Follow** we get many advantages such as the ability to add damping to the movement of the Camera, this can remove any minor jittering in the Camera and give a smooth feel, however if you want you can set it to ```(0,0,0)``` to remove it.

5. **Shoulder Offset** and **Vertical Arm Length** : These properties can help you position your Camera relative to the **Pivot** GameObject, so you can make your FPS Controller appear taller than it really is without modifying the height.

Other options include the **Camera Distance**, by simply increasing this you now have a 3rd Person Controller, the **Player Controller** will function exactly the same. This is why Cinemachine is used, it is extremely simple to extend upon and change to fit what you like.

## Player Camera Controller

It's also important to know how the Camera is being modified in the **Player Camera Controller**. 

![CAM_CONTROLLER_2.png]({{site.baseurl}}/CAM_CONTROLLER_2.png)

Let's run through the different properties:

1. **Pivot Transform** : A reference to an empty GameObject in the center of the Player.

2. **Virtual Camera** : A reference to the **Cinemachine Virtual Camera** we covered in the last section.

3. **Lock Rotation** : If this is enabled it will just prevent the rotation from changing, this can be useful if we need to override the rotation of the Camera.

4. **Locked** : This is referring to the Cursor Lock State, there are 3 modes that can be selected. Locked is preferred so that the Cursor does not get in the way of testing the game.
	1. Locked : The Cursor cannot move when in the Game Window
    2. Confined : The Cursor cannot leave the Game Window
    3. None : The Cursor is left without change
   
5. **Visible** : Whether or not the Cursor is visible on the screen.

6. **Pitch Min Max** : The minimum and maximum rotation on the ***up** and ***down** axis for looking.

7. **Mouse Sensitivity** : How much a movement in the mouse affects the rotation of the Camera.

8. **Rotation Smooth Time** : How quickly the rotation of the Camera reaches its desired value.

9. **Camera Influenced By Player Input** : Whether or not the Player Camera Controller should listen to inputs from the controller to change its behaviour. Also this can be set to ```false``` if this Player is to be repurposed for a Third Person Controller.

10. **FOV Zoom Amount** : How much to increase the FOV when the Player starts sprinting.

11. **Tilt Amount** : How much to tilt the character when a horizontal movement is detected (inspired by Dusk).

12. **Tilt Speed** and **FOV Zoom Speed** : How quickly the two respective parameters above are influenced.

### What exactly does the Tilt and FOV Increase do?

By increasing the FOV when sprinting it gives a feel of speed increasing by slightly increasing the amount that you can see in the corners. By tilting the Camera while moving horizontally it provides a natural feel to the Camera and a sense of motion.

![fov_tilt_displace_2.gif]({{site.baseurl}}/fov_tilt_displace_2.gif)

