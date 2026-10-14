# Roll-A-Ball 2

Roll-A-Ball 2 takes [my first game's](https://github.com/connor-gt/roll-a-ball-scripts) ball-rolling concept and expands it into 12 handcrafted levels with moving obstacles and a camera the player can control.

**Details:** Unity/C#, scripts-only repository  
**Development Timeline:** August 2024 - October 2024

<p align="center">
  <img src="Screenshots/RollABall2_menu.jpg" alt="Roll-A-Ball 2 main menu" width="720">
  <br>
  <em>Main menu</em>
</p>

## Gameplay

The goal is to reach the end of each level without falling or getting hit off the track by an obstacle. Each level has its own layout, with new obstacles and more difficult movement patterns introduced as the player progresses. Completing a level unlocks the next one.

The levels are split into three themes: clouds for levels 1-4, fire for levels 5-8, and void for levels 9-12. The player can use the mouse to look around, and movement follows the camera's direction. Moving sections of the track and rotating obstacles also mean the player has to pay attention to timing before moving forward.

| Cloud-theme level | Fire-theme level | Void-theme level |
| :---: | :---: | :---: |
| <img src="Gifs/clouds.gif" alt="Moving obstacles in a cloud-themed level" width="360"> | <img src="Gifs/fire.gif" alt="Moving obstacles in a fire-themed level" width="360"> | <img src="Gifs/void.gif" alt="Moving obstacles in a void-themed level" width="360"> |

## Code Tour

These scripts are good starting points for looking through the project:

| Script | What it handles |
| --- | --- |
| [PlayerController.cs](Scripts/Player/PlayerController.cs) | Handles camera-relative movement, ground checks, and interactions with objects that implement ITriggerable. |
| [CustomCinemachineInputProvider.cs](Scripts/Camera/CustomCinemachineInputProvider.cs) | Controls when the Cinemachine camera receives look input. |
| [MoveSideToSide.cs](Scripts/Obstacles%26TrackPieces/MoveSideToSide.cs) | Moves obstacles or track pieces between two positions, with configurable timing and delays. |
| [GameController.cs](Scripts/GameState/GameController.cs) | Handles winning, losing, and pausing, and records level progress. |
| [Bootstrapper.cs](Scripts/Systems/Bootstrapper.cs) | Creates the shared persistent objects before a scene loads. |

---
<p align="center">
  <img src="Gifs/void_level.gif" width="720">
  <br>
  <em>Admiring the view</em>
</p>

---

## Looking Back

After finishing Crazy Runner, I wanted to come back to the Roll-A-Ball idea and make it more interactive. Adding a camera the player could control meant the movement also needed to follow the camera's direction. Creating individual levels gave me more control over the challenges, and I could build layouts around specific moving obstacles. I also created some of my own assets for this project, which gave me more experience with modeling, texturing, and bringing those assets into Unity.

One issue I wanted to fix from my time with Crazy Runner was having to start from the main menu whenever I wanted to test the game scene, because other scripts depended on objects initialized there. For this project, I added a bootstrapper to create shared objects before scenes load which made testing in Unity so much easier because I load straight into a level without first having to go through the main menu (like I did with Crazy Runner). I also started using interfaces and events to reduce some of the direct dependencies between scripts. For example, the player controller can activate an object through ITriggerable without needing to know which specific type of trigger it is.
