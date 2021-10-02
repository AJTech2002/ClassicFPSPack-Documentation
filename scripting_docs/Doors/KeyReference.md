# Key Reference

The Key Reference is just a class with a string inside it, it is serializable and the only purpose is to allow a custom editor to be generated.

The Custom Editor will check if there is a Key Manager in the project and develop a drop down that you can select the key from, this makes adding Key Selection variables easier in the code.

However, if you have multiple Key Managers it will revert to a text field.
