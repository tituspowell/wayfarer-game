# Wayfarer: A C# Unity Passion Project

## Introduction

**Wayfarer** is a single-player turn-based dungeon crawler game that runs in Windows. I wrote it in C# using Unity. It is the very definition of a passion project - I spent two years developing it, with no intention of a public release. It was always just for myself and family and friends to play. During that time it has evolved in scope and complexity far beyond what I imagined when starting it.

## Game Overview

The core gameplay is that you start with a character, and have to win eight games to reach the title of Champion, at which point the character retires and you start with a new one. Each game is a snackable 15-30 minutes to play, and any items or gold you win a game with can be brought into the next one. So your character grows stronger with equipment and abilities as he or she progresses, but the challenges increase as you progress through the eight levels.

What makes Wayfarer unique is the sheer variety of things that can happen. Every game is completely unique and memorable and makes you want to tell someone about the crazy adventure you just had. This is achieved through multiple interacting complex systems combined with a high degree of randomness. This leads to emergent, entertaining and frequent laugh-out-loud or gasp-out-loud experiences.

To give you an idea of the staggering depth and variety, there are:

- 14 different procedurally generated **landscape** types to explore (Catacombs, Forest, Citadel, Swamp, Desert, etc.) with a unique layout every time.
- 17 different **landscape variations** (the catacombs or forest could be Frozen, Intense, Toxic, Sacred, etc.)
- 44 different **character classes** you can be, and 16 different fantasy **races**, each with unique advantages and disadvantages.
- 56 different **abilities** you can gain on winning a game to better equip you in subsequent ones.
- 255 unique **magic items** you can potentially find, use and keep.
- 48 **magic spells** you can potentially learn and cast.
- 56 classes of **NPCs** with different behaviours, skills and unpredictable personalities, along with a random name generator. Some will offer to join as a companion. Others will trade or attack. Sometimes they fight each other.
- 57 unique **monster** types with a range of possible behaviours.
- 23 different **trap** types.
- 23 different **diseases** you can catch that temporarily debuff you until they are cured.
- 13 **Houses** you can align yourself with giving you optional extra challenges and rewards if you succeed.
- 96 **Chaos effects** - dramatic and fun gameplay variants that you can trigger or try to avoid.
- **Laws** that you have the option of breaking, with stiff penalties if you are then caught by a Sentinel.
- **Pacts** you can make with demons that give you one of 21 possible boons with one of 16 possible costs.
- **Religion** points you can accumulate to ask God to help you out in a fix, which he may or may not do.
- Magic portals, quests, rumours, limb damages, curio locations, ranged weapons, arcane events, legendary items, a luck system and more!

## Technical Highlights - TO DO

1. Procedural Generation System
   - Description of how diverse game elements are generated
   - Code snippet showcasing a key algorithm
2. AI and NPC Behavior
   - Overview of NPC decision-making processes
   - Example of a complex interaction system
3. Item and Spell Systems
   - Explanation of how magic items and spells are implemented
   - Code snippet of an interesting item or spell effect
4. World Building and Environment
   - Description of how different landscapes are created and managed
   - Visual demonstration of world variety

## Development Journey and Current State

The initial motivation for creating Wayfarer was to refresh my programming skills by recreating a family board game. I was completely new to Unity so it was an ambitious challenge to take on, having not done any coding for several years. I had no idea how much it would evolve beyond the original board game, or how deep and complex the game mechanics would become over the next two years.

One thing it suffers from is a lack of a wider player base. My family have been playing it avidly over the past two years and giving me fantastic feedback as well as obscure issues to fix. But because nobody new was playing it, there's a distinct lack of onboarding. Apart from a nominal 'tutorial mode' where it is slightly gentler with its random events, there really is nothing to help ease a new player into the game, or introduce the mechanics. A seasoned gamer would figure a lot of it out after a couple of games but my lack of focus on the user experience for new players is immediately evident if you try it. I added a 'Help' button recently to at least give players a summary of where they are up to in a game. For a proper public release it would need a full interactive tutorial. I've considered this a few times but it would be so much work that I haven't taken that on.

The graphics are decidedly janky, my lack of Unity experience showing, with poor lighting, generic assets (a single animated monster token to represent all of the various monster types, for example) and almost no awareness of shaders and particle effects. There is no audio at all.

The clever things it does, and the wonderfully varied gameplay that is its core appeal, only really emerges once you get past the amateurish graphics and the lack of tutorial. Making it a finished, polished game would take an immense amount more work, and as I'm not looking to become a game designer, much of that would feel irrelevant and time-consuming - creating prettier animated assets, for example. I did learn Blender at one point to create a custom scythe model that appears so small on the screen you can't appreciate any of the detail.

## Platforms

Unity lets you build for different platforms and, as a lifelong Windows user, I naturally developed it for Windows. This is obviously a limitation, as Mac users can't play it; nor can it be played on devices. Unity supports all these other platforms but porting it to another one would be non trivial. There is a lot of information provided when you mouse-over elements in the game, for example, and if porting to an iPad that would need to be reworked completely.

I did briefly manage a web port and have it working in a browser early on. The challenge there is that the game saves to a save file to keep track of your characters and progress, which is too large for localStorage (and too precious if you've sunk thousands of hours into playing it). Saving it to the cloud using my brother's AWS key did work but it would need a more scalable solution if shared publicly.

## Reflections on Technical Decisions

The game successfully provides countless hours of entertainment but several initial design decisions would come back to haunt me. With the glorious benefit of hindsight, much could be improved or should have been implemented differently. The experience has taught me a lot about what not to do as well as what worked.

Here are my reflections on some of those technical decisions and what I learned from them.

- Single player vs multiplayer. As a Unity noob starting an ambitious project, I knew that multiplayer would be too difficult. I also knew that if I didn't weave it into the game right from the beginning, it would be impossible to add later. Perhaps I should have started with a simple multiplayer game first - Tic Tac Toe or Battleships. But I was eager to start and so it is forever a single player game.

- If starting over I would do a much better job of separating UI, core functionality and also AI. I tried to keep them separate, using events rather than direct function calls, but didn't go far enough, not anticipating that the project would grow so large. It would be really nice if the UI was entirely separate with a clear API such that someone else could in theory come along and completely overhaul the graphics and UI. As it is that would be no easy task, because the lines of separation got blurred.

- One thing I really wish I'd anticipated and set up early is a state management system. The game often saves the characters to disk, but there is no way to save a game itself mid-way through, or to undo a move. The game's state at any given point consists of hundreds of variables spread across dozens of objects and static classes. It would have been relatively easy to create a system early on that packaged up the state as a snapshot of that turn and kept track of a game through an array of snapshots, allowing a game to be saved and resumed, and moves to be undone.

These flaws and the early design decisions what would have prevented them are obvious in hindsight. I take it as an encouraging measure of progress that I can see where I made mistakes and that I can chart how I've grown as a developer by when each file was written.

## Conclusion

The goal was to sharpen my C# and broader programming instincts while also making a fun game, and I feel I very much succeeded. The mistakes taught me much more than if I'd approached it perfectly right from the start. I'm only scratching the surface of what Unity can do, but it was never about learning Unity or becoming a games developer, so I'm not interested in going further down that path, at least at the moment.

Making a game was a great decision, I think, because it's so much fun. Had I instead written a database report management system or something else more 'business applicable', I never would have worked on it for two years and reaped all the lessons along the way. My core skill - C# - and instincts about programming in general were helped enormously by this passion project, and those sharpened skills translate to any broader software development role, not just in games.

## Additional Resources - TODO

- Link to downloadable game (for those interested in trying it)
- GitHub repository with README and selected code samples
