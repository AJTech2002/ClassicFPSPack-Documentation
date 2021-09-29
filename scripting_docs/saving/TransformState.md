# Transform State

The Transform State is based off the [`State`](State.md) class and it tracks the following information.

Normal Objects:

1. Position
2. Rotation
3. Scale
4. Rigidbody Velocity
5. Rigidbody Angular Velocity

If it is a Player Controller, it tracks also:

1. Camera Direction
2. Player Position (handles teleportation on load)

## Additional State Information

The `TransformState` utilises `ShouldSave()` override, it only saves when the position/rotation has changed to save space.

When the Player Controller's transform is loaded this specific code is executed:

```C#
GetComponent<PlayerController>().TeleportPlayer(SaveUtils.XYZToVector3(savedState.positionState));
GetComponent<PlayerCameraController>().SetRotation(SaveUtils.XYZToVector3(savedState.rotationState));
```

The `TeleportPlayer` and `SetRotation` function on the respective scripts interrupt the flow of the Player Controller to inject this behaviour.
