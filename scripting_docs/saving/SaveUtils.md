# Save Utils

Save Utils contains a few functions that aid in the Saving & Loading of states. In older versions of Unity Vector3 was not able to be converted to JSON, in those cases you can use this:

```C#
SaveUtils.Vector3ToXYZ (vectorValue); //Saving Vector
SaveUtils.XYZToVector3 (value); //Loading Vector
```
