# Pickup Utils

The Pickup Utils are used by both the Player Object Interaction Handler and the Gravity Gun to handle the picking up of external objects in the scene.

This script is executed in conjuction with some logic in the respective scripts that execute it.

## Public Variables

1. **pickupSpeed**: Speed at which the picked up object goes to the position infront of the Player.

2. **throwSpeed**: Speed of the throw when the player releases the object.

3. **coverViewportPercentage**: This is the amount of the viewport to fill up with the object; this value is used to pickup objects of various sizes while keeping it near to constant on the screen.

4. **maximumDamage**: Maximum damage that can be delivered from throwing this object.

5. **defaultCrosshairColor**: Normal crosshair color is white.

6. **selectedCrosshairColor**: Color of crosshair when you hover over an object that can be picked up.

7. **clippingObjectThreshold**: Amount of the object that can be clipped into the ground before it is retracted away from it.

8. **dropFromExpectedPositionLerp**: If the object is greater than this distance away from the expected position when the player attempts a throw, this will execute a drop instead.

9. **discludePlayer**: A layermask discluding the player to pickup & throw.

## Public Functions

1. **Setup(Camera playerCamera)**: The script executing this should call the Setup to setup the initial parameters.

2. **OnPickup (Transform transform, MonoBehaviour from)**: When an object is picked up pass in the transform and the script that is executing this logic.

3. **ResetObject()**: Resets the picked up object including its Rigidbody parameters, colliders etc.

4. **ModifyCrosshair ()**: Based on the raycast from the crosshair position, the object highlighted will modify the crosshair and scaling of the crosshair.

5. **UpdateLoop ()**: This update loop function should be called on Update from the script executing this utility script.
