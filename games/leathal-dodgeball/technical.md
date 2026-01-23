From a technical standpoint, the project was built as a deliberately lightweight and hands-on Unity setup. The game was developed in Unity 6, using the Animator and PurrNet for networking. All gameplay systems were implemented in pure C#, without relying on additional plugins or external frameworks, which is likely noticeable in the feel of the demo.

The core scene architecture is organized around a few key systems:

* A Game Manager acting as a referee: it registers hits, validates interactions, triggers game events, and manages scoring and match timing.

* The map is assembled from a modular prefab-based environment, intentionally simplified to create a woozy, fever-dream-like atmosphere. Performance was a key consideration, with strong use of culling and light baking, and the scene also includes an animated low-poly crowd to add life without excessive overhead.

* The player interaction loop revolves around selecting and summoning different ball prefabs, aiming, and throwing them using alternative mechanics (rolling, licking, flicking), in line with the game jam’s theme. Each ball has its own behavior scripts, handling physics variations, contact registration, and special interactions.

* On the player side, a character controller works in tandem with a Ball Manager system. This manager relies on a ball registry that loads prefabs with parameterized properties (weight, damage modifiers, animation tweaks). It handles ball spawning, switching, ownership, and hit events, which are then verified by the referee.

* In multiplayer, the referee runs server-side, listening to player inputs, validating collisions using its own collider instances, and authoritatively updating scores and game state.

* PurrNet is used to synchronize networked objects such as players, AI-controlled dummy bots, and balls. It helps prevent basic cheating and implements a pseudo-delay–based netcode to keep gameplay consistent across clients.