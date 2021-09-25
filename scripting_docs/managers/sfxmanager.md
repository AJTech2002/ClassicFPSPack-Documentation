# SFX Manager

The SFX Manager is located on the same object as the Game Manager. It's purpose is to handle the Ground Sounds.

Inside the SFX Manager you map all the ground sounds and in runtime you can get the footstep sound depending on the surface the player is currently standing on.

The Logic for finding what surface the player is standing on is done in the `PlayerSFX` script. The SFXManager just holds references and maps them to a dictionary for easy access.

To learn how to add new Ground Sounds for terrains & normal surfaces watch this tutorial:

[SFX Tutorial](https://www.youtube.com/watch?v=uOYOUjkHLlM&list=PL9FeLoYIHiTyYr5zPLr2RtjX8T41PIArx&index=7&ab_channel=AJTech)
