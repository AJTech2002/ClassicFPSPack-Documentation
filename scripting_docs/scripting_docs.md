# Scripting Documentation

The Classic FPS Pack contains multiple namespaces under which the different scripts are held, the content will be split based on the namespaces.

## Provided Namespaces

### Managers

Contains manager scripts that control the behaviour of different systems in the game, include by adding the following:

```C#
using ClassicFPS.Managers;
```

**Scripts in Namespace**:

- [GameManager](gamemanager.md)
- [SaveManager](savemanager.md)
- [KeyManager](keymanager.md)
- [WeaponManager](weaponmanager.md)
- [UIManager](uimanager.md)
- [SFXManager](SFXManager.md)

---

### Controller

Contains core controller scripts, these dictate movement & interaction of the Player Controller in the game.

```C#
using ClassicFPS.Controller;
```

**Scripts in Namespace**:

- [PlayerController](PlayerController.md)
- [PlayerCameraController](PlayerCameraController.md)
- [PlayerWeaponController](PlayerWeaponController.md)
- [PlayerInputManager](PlayerInputManager.md)
- [PlayerPhysics](PlayerPhysics.md)
- [PlayerObjectInteractionHandler](PlayerObjectInteractionHandler.md)
- [PlayerStatistics](PlayerStatistics.md)
- [DefaultPlayerWalkAnimator](DefaultPlayerWalkAnimator.md)

---

### Weapons

Contains all the scripts that dictate the actions of the weapons before/during/after equipped.

```C#
using ClassicFPS.Weapons;
```

**Abstract/General**

- [BaseWeapon](BaseWeapon.md)
- [Weapon](Weapon.md)
- [WeaponAttribute](WeaponAttribute.md)
- [WeaponReference](WeaponReference.md)

**Demo Scripts**

- [Projectile](Projectile.md)
- [DemoGravityGun](DemoGravityGun.md)
- [DefaultClassicFPSWeapon](DefaultClassicFPSWeapon.md)
- [DefaultClassicFPSWeapon_Shooting](DefaultClassicFPSWeapon_Shooting.md)

---

### Audio

Classes responsible for handling audio within all the other components of the pack, scripts also responsible for footstep ground detection on terrains.

```C#
using ClassicFPS.Audio;
```

**Scripts in Namespace**:

- [GroundSound](GroundSound.md)
- [PlayerSFX](PlayerSFX.md)
- [PlayerSFXReference](PlayerSFXReference.md)
- [Sound](Sound.md)
- [TerrainSurface](TerrainSurface.md)

---

### Saving and Loading

Classes responsible for saving and loading the states of the game, also contains some general states that can be applied to objects.

```C#
using ClassicFPS.Saving_and_Loading;
```

**Abstract/General**

- [ISaver](ISaver.md)
- [State](State.md)
- [SaveUtils](SaveUtils.md)

**Demo Scripts**

- [GameState](GameState.md)
- [SavePoint](SavePoint.md)
- [TransformState](TransformState.md)

---

### Interactable Objects

Classes responsible for handling interactable objects for example things that can be pushed, thrown or broken.

```C#
using ClassicFPS.Interactable_Objects;
```

- [BreakableObject](BreakableObject.md)
- [PushableObject](PushableObject.md)

---

### Enemy

Classes that contains all the scripts that manage Enemy movement, interaction and saving.

```C#
using ClassicFPS.Enemy;
```

**Scripts in Namespace**:

- [DamageableEntity](DamageableEntity.md)
- [Enemy](Enemy.md)
- [DroneEnemy](DroneEnemy.md)
- [ClassicEnemy](ClassicEnemy.md)

---

### Door System

Classes that control opening Doors w/ key pickups and also dialogue interactions to get keys from NPCs.

```C#
using ClassicFPS.Door_System;
```

**Scripts in Namespace**:

- [Door](DamageableEntity.md)
- [KeyPickup](Enemy.md)
- [KeyReference](Enemy.md)
- [KeyDialogue](Enemy.md)

---

### Dialogue System

Scripts used for the Dialogue System, all the way from parsing serialized dialogue to interacting with it and showing it on UI.

```C#
using ClassicFPS.Dialogue_System;
```

**Scripts in Namespace**:

- [Dialogue](Dialogue.md)
- [DialogueInteraction](DialogueInteraction.md)
- [DialogueProcessor](DialogueProcessor.md)
- [DialogueRunner](DialogueRunner.md)
- [DialogueUtils](DialogueUtils.md)

---

### Pickups

General Pickup items that are used to modify the state of the Player.

```C#
using ClassicFPS.Pickups;
```

**Scripts in Namespace**:

- [Pickup](Pickup.md)
- [CoinPickup](CoinPickup.md)
- [HealthPickup](HealthPickup.md)
- [WeaponPickup](WeaponPickup.md)
- [AmmoBox](AmmoBox.md)

---

### UI

General UI Scripts to interact with different systems in the pack.

```C#
using ClassicFPS.UI;
```

**Scripts in Namespace**:

- [KeyUI](KeyUI.md)
- [EndUI](EndUI.md)
- [SaveUI](SaveUI.md)

---

### Utils

Only contains one script, this is used by both Gravity Gun and PlayerObjectInteractionHandler to handle pickup up objects.

```C#
using ClassicFPS.Utils;
```

**Scripts in Namespace**:

- [PickupUtils](PickupUtils.md)
