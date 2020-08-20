---
layout: default
title: "Odeya Nidström's Projects"
---
# Odeya Nidström's Projects

This is home of personal projects.

## "Desperate" project
Currently, I'm willing to write a game, just for fun of learning how to do. I never managed to overcome the no-architecture-crappy small prototype phase, having at best produced a Wolf-like 3D maze with Monogame, with a hard-coded level, 3 textures and a simple shader. 

I have several ideas I'd love to test, but a choice must be done, so I'll just try to describe 2 of them and prototype them.

But this is not about creating the next big thing: I hardly believe anybody other than me will ever consider playing with it, even if I manage to have something *really* working. No, it is mainly about learning about something entertaining, that can drive easily motivation with immediate results.

"Desperate" is the name of this project, and maybe of the lib containing base code to share between both prototypes.

### Goals
This is what I intend to achieve with "Desperate":
* learn about game creation
* learn about new language
* toying with GPU coding
* buildable with free softwares
* _think different_

### Target environment
It's easy: it has to be cross-platform and running on low-end hardware. I run 3 computers: 
* a 2009 MacBookPro (Core2Duo w/ GeForce 9400m & 9600m, OpenGL 3.2)
* a 2013 laptop w/ ArchLinux & Windows (Core i5 w/ integrated Intel HD3000 gpu, OpenGL 3.2 or 4.1 ?)
* a custom workstation w/ ArchLinux & Windows (Core i5 w/ GeForce GTX600, OpenGL 4.?, Vulkan)

Right now, I want to target all of them, all 3 OSes, so OpenGL is the way to go. Anyway, what I've seen of Vulkan coding doesn't fit my tastes right now.

### Technology involved

#### Foreword: the Monogame experiment
As said before, I already have toyed with [Monogame](https://www.monogame.net), a complete .NET game framework based on defunct XNA. As an experienced C# coder, it's a pleasure to use, but some issues have been really irritating.

First, for anything 3D-related, shaders are written with HLSL. If you target DesktopGL (their name for OpenGL platforms), Monogame content pipeline will translate HLSL into GLSL automatically, but it will use some Direct3D technology to do so. Which is not compatible out-of-the-box with Linux & MacOS. Wine can now be used on those systems with needed D3D dependencies, but I can't make it work again on my current MacOS. **Anyway, it breaks the rule "build with free softwares".**

Second, I ran into issues with Mono & MSBuild updates regularly. Build impossible, many install/uninstall, I'm tired of this. Last version of Monogame seems to support .NET Core, maybe it has improved.

#### Rust
I have discovered Rust recently and found it very appealing. It has also lot of hype today, it is native, and it is somewhat different from my beloved C#.

**With Rust, I have to think different**.

I'll try to use Rust and its ecosystem for at least one prototype. If it doesn't fit, maybe try Monogame 3.8 with .NET core ?

#### Dependencies: GFX, game engines, ...
Rust gaming ecosystem isn't really mature yet, even if serious work is already possible.

For bare OpenGL, Glium + Glutin crates (Rust dependencies) are good choices. Glium is a thin OpenGL wrapper, intended to be "safe" in a rusty way. It manages all issues that could lead to segfault when dealing with OpenGL API. Sadly, even if very complete, [Glium seems to be at best on hiatus](https://users.rust-lang.org/t/glium-post-mortem/7063). GFX-RS is an interesting alternative as an abstraction over many API, in the way Monogame can be, but it is currently rewritten from scratch as GFX-HAL, a vulkanic abstraction currently not compatible anymore with OpenGL.

For [Entity-Component-System](https://en.wikipedia.org/wiki/Entity_component_system), legion and specs are both interesting and widly used in Rust. I don't know about such architecture, so I will use it at least for one of my prototypes.

For game engine ... I'll write my own. Not I don't want to use [Amethyst](https://amethyst.rs/) or [Bevy](https://bevyengine.org/), 2 promising engines written in Rust, but they both rely on GFX-HAL, so they aren't capable of any OpenGL right now. [If this change in the future](https://github.com/gfx-rs/wgpu/issues/450), I'll be glad to look at it.

### Blogging
With "Desperate" project, I want to document how I think, drive, code it. Don't know if it will be of any use to anybody, but I find it useful to structure my thoughts.

### Ideas
I'll try to expand around two very different ideas:
- [Desperate: Dig](./desperate_dig/): a 3D digging "kinda-puzzle" game
- [Desperate: Kill!](./desperate_kill/): a John McClane Simulator in 2D, pixel art, where player has to shoot everybody to save the world