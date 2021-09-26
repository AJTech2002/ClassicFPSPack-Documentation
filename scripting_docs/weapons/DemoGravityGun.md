# Demo Gravity Gun

This weapon is included directly in the pack in the form of a Gravity Gun. It is derived from the [`BaseWeapon`](BaseWeapon.md) class.

The Gravity Gun can pickup items that have the `PushableObject` script with the **canPickup** variable set to true.

## Public Variables

1. **gravityGun**: This is variable is based of a class called `PickupUtils`, this script manages all the pickup behaviour; and the variables within this class modify the pickup behaviour.

2. **pickupAction**: The key/mouse button to press to pickup the object with Gravity Gun. This is an 'InputAction' asset which is a part of the new Input System, it allows you to find actions directly in the inspector.

3. **throwAction**: Action used to throw the object with force. To drop the object down you can use the same action as the **pickupAction**.

4. **releaseSound**: Sound when item is released.

5. **cantPickupOrThrowSound**: Sound when you try to pickup and object that is not throwable.

The `PickupUtils` class is also used in the `PlayerObjectInteractionHandler` to manage picking up items without a Gravity Gun.

Go to [PickupUtils Scripting Reference](../utils/PickupUtils.md) to learn how to change all the pickup properties such as pickup distance, crosshair color etc.

Most of the pickup/throwing logic is done in the `PickupUtils` script, the only thing handled in this script is the Input logic.

Note that this script is derived from `BaseWeapon` so all equipping logic, animation logic and unequipping logic is handled there.
