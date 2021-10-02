# Scripting Documentation

The Classic FPS Pack contains multiple namespaces under which the different scripts are held, the content will be split based on the namespaces.

## Provided Namespaces

### Managers

Contains manager scripts that control the behaviour of different systems in the game, include by adding the following:

```C#
using ClassicFPS.Managers;
```

**Scripts in Namespace**:

- [GameManager](managers/gamemanager.md)
- [SaveManager](managers/savemanager.md)
- [KeyManager](managers/keymanager.md)
- [WeaponManager](managers/weaponmanager.md)
- [UIManager](managers/uimanager.md)
- [SFXManager](managers/sfxmanager.md)

---

### Controller

Contains core controller scripts, these dictate movement & interaction of the Player Controller in the game.

```C#
using ClassicFPS.Controller;
```

**Scripts in Namespace**:

- [PlayerController](controller/PlayerController.md)
- [PlayerCameraController](controller/PlayerCameraController.md)
- [PlayerWeaponController](controller/PlayerWeaponController.md)
- [PlayerInputManager](controller/PlayerInputManager.md)
- [PlayerPhysics](controller/PlayerPhysics.md)
- [PlayerObjectInteractionHandler](controller/PlayerObjectInteractionHandler.md)
- [PlayerStatistics](controller/PlayerStatistics.md)
- [DefaultPlayerWalkAnimator](controller/DefaultPlayerWalkAnimator.md)

---

### Weapons

Contains all the scripts that dictate the actions of the weapons before/during/after equipped.

```C#
using ClassicFPS.Weapons;
```

**Abstract/General**

- [Weapon](weapons/Weapon.md)
- [BaseWeapon](weapons/BaseWeapon.md)
- [WeaponAttribute](weapons/WeaponAttribute.md)
- [WeaponReference](weapons/WeaponReference.md)

**Demo Scripts**

- [Projectile](weapons/Projectile.md)
- [DemoGravityGun](weapons/DemoGravityGun.md)
- [DefaultClassicFPSWeapon](weapons/DefaultClassicFPSWeapon.md)

---

### Audio

Classes responsible for handling audio within all the other components of the pack, scripts also responsible for footstep ground detection on terrains.

```C#
using ClassicFPS.Audio;
```

**Scripts in Namespace**:

- [Sound](audio/Sound.md)
- [GroundSound](audio/GroundSound.md)
- [PlayerSFX](audio/PlayerSFX.md)
- [PlayerSFXReference](audio/PlayerSFXReference.md)
- [TerrainSurface](audio/TerrainSurface.md)

---

### Saving and Loading

Classes responsible for saving and loading the states of the game, also contains some general states that can be applied to objects.

```C#
using ClassicFPS.Saving_and_Loading;
```

**Abstract/General**

- [ISaver](saving/ISaver.md)
- [State](saving/State.md)
- [SaveUtils](saving/SaveUtils.md)

**Demo Scripts**

- [GameState](saving/GameState.md)
- [SavePoint](saving/SavePoint.md)
- [TransformState](saving/TransformState.md)

---

### Interactable Objects

Classes responsible for handling interactable objects for example things that can be pushed, thrown or broken.

```C#
using ClassicFPS.Interactable_Objects;
```

- [BreakableObject](Interactable/BreakableObject.md)
- [PushableObject](Interactable/PushableObject.md)

---

### Enemy

Classes that contains all the scripts that manage Enemy movement, interaction and saving.

```C#
using ClassicFPS.Enemy;
```

**Scripts in Namespace**:

- [DamageableEntity](Enemy/DamageableEntity.md)
- [Enemy](Enemy/Enemy.md)
- [ClassicEnemy](Enemy/ClassicEnemy.md)
- [DroneEnemy](Enemy/DroneEnemy.md)

---

### Door System

Classes that control opening Doors w/ key pickups and also dialogue interactions to get keys from NPCs.

```C#
using ClassicFPS.Door_System;
```

**Scripts in Namespace**:

- [Door](Doors/Door.md)
- [KeyPickup](Doors/KeyPickup.md)
- [KeyReference](Doors/KeyReference.md)
- [KeyDialogue](Doors/KeyDialogue.md)

---

### Dialogue System

Scripts used for the Dialogue System, all the way from parsing serialized dialogue to interacting with it and showing it on UI.

```C#
using ClassicFPS.Dialogue_System;
```

**Scripts in Namespace**:

- [Dialogue](Dialogue/Dialogue.md)
- [DialogueInteraction](Dialogue/DialogueInteraction.md)
- [DialogueProcessor](Dialogue/DialogueProcessor.md)
- [DialogueRunner](Dialogue/DialogueRunner.md)
- [DialogueUtils](Dialogue/DialogueUtils.md)

---

### Pickups

General Pickup items that are used to modify the state of the Player.

```C#
using ClassicFPS.Pickups;
```

**Scripts in Namespace**:

- [Pickup](Pickups/Pickup.md)
- [CoinPickup](Pickups/CoinPickup.md)
- [HealthPickup](Pickups/HealthPickup.md)
- [WeaponPickup](Pickups/WeaponPickup.md)
- [AmmoBox](Pickups/AmmoBox.md)

---

### UI

General UI Scripts to interact with different systems in the pack.

```C#
using ClassicFPS.UI;
```

**Scripts in Namespace**:

- [KeyUI](UI/KeyUI.md)
- [EndUI](UI/EndUI.md)
- [SaveUI](UI/SaveUI.md)

---

### Utils

Only contains one script, this is used by both Gravity Gun and PlayerObjectInteractionHandler to handle pickup up objects.

```C#
using ClassicFPS.Utils;
```

**Scripts in Namespace**:

- [PickupUtils](utils/PickupUtils.md)
