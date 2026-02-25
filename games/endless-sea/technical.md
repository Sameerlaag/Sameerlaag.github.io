The game run on Unity 6 URP, with most of the shaders and assets were made by the dev and 3D team.
We begun with a sea simulation system, built through C# scripts and shaders.
Then we applied gradually it's forces on the player character boat's character controller.
The PC reads inputs and switches states between free movement, interaction mode, drive mode and mini games, with a couple of helper methods to disable all movements while in animation.

The boat has it's own character controller built to mimic real life boats' tank controls.

The key interfaces of the project are the IDrivable interface, which stream their own control listeners to the pc in order to have different sets of drivable objects and easily implement them through out the life cycle of the game.

One of them is the radio, which listens to event actions to activate or deactivate one of the key minigames, the "oil rig minigame", where depending on the direction the boat is facing, the radio produces more static, serving as the game's compass.

Audio was implemented through an audio manager, but eventually we introduced Fmod when an audio engineer joined the project.

The game's lifecycle is handled by the game manager, which serves as an observer for the event actions launched through out the run, then delegates to a subscript which is meant to react and trigger other events.