---
layout: default
title: "Odeya Nidström's Desperate: Dig"
---

# Desperate: Dig

"Desperate: Dig" is a 3D game where player has to dig underground from a small room to a portal to escape from a level.

It is a blocky game visually, inspired by Wolfenstein 3D, but with 10cm blocks instead of 2m.

Funny: I have discovered [Veloren](https://veloren.net/) very recently. And found its visuals are very similar to those I imagined. And more funny: it's written in Rust! Less funny: it runs at 4 FPS on my MBP.

## Game mechanics

Levels are generated on the fly.
In a first attempt, I will stick to a 100m x 100m x 100m matrix, with 10cm per block side, so a level should be roughly 1GB heavy. Simple RLE compression may efficiently reduce this size.

It seems a small playground, but can be improved later, for example with a more dynamic level structure where only digged blocked are tracked, allowing for greatest playground for same amount of data. Level can also be zoned to help rendering to drop unseen blocks.

To introduce some interest to such game, we can imagine a switch will have to be discovered somewhere to activate the portal. Some zone may be not diggable to introduce some challenge ; some lava/water may stream accross the level and submerge player if dug too harshly. I think some detectors may help player to find what it's looking for. A radiation detector for portal and switch, heat for lava, etc.

Rooms too large may also collapse.

I'm not really sure it can be a fun game. But visually, I find it interesting to work on.