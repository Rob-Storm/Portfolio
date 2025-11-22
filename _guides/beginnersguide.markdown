---
layout: guide
title: Beginner's Guide To Game Development
description: Design not included!
---

I've been making games for over half my life and I am entirely self-taught so I think I am somewhat qualified to try and explain my methods to others. Any tools or technologies I mention will be free unless stated otherwise, wherein a free alternative will also be mentioned.

Hopefully this article will help you get started making your first game.

## Engine

Doesn't matter. Pretty much every engine can do everything so just pick one and stick with it. If you become experienced with one, its fairly straightforward to move to another (ask me how I know...).

## Programming

Unless you are opting to use no engine or write your own, (YOU SHOULD NOT BE DOING THIS AS A BEGINNER!) you are locked into whatever language the engine you picked uses. For Unity, its C#. Unreal uses a visual scripting system called Blueprints but you can use C++ if you want. Godot uses its own GDScript language which is similar to Python but it also supports C# via its Mono build and C++ through the GDExtension C++ bindings. GameMaker Studio uses a visual "drag-and-drop" programming as well as a custom programming language called GML (GameMaker Langauge).

I personally learned programming with C# by using a book called the *C# Player's Guide* by RB Whitaker. It set me back about $35 but I also got free shipping (was not so lucky with *Game Engine Architecture*...). If you put in the work and do all of the challenges, you will learn programming without a doubt. In fact, it wasn't until a few weeks ago I actually finished the book because I got to the end of the object oriented part and stopped since I had learned enough to be self-sufficient. I personally recommend reading until the **Lambda Expressions** chapter since those C# features you learn about are pretty much universal across all languages and they will save you a lot of headaches (events/delegates especially).

### IDEs

The bare minimum for writing code is really just a text editor and a terminal. You *could* use notepad and command prompt but I can say from experience that you'd be better of with Sublime Text + Cmder.

I wouldn't actually suggest a beginner use this but it's important to know that the bar for entry to writing source code is basically zero. I mean they used 0s and 1s on punch cards way back in the day so really we are spoiled for choice. Speaking of which:

**Visual Studio**
It doesn't get any easier than Visual Studio. I wouldn't recommend using the newest Visual Studio (2026) since Microsoft is cramming AI into everything and this release is no different. Just use Visual Studio 2022 and forgo the already-implemented AI garbage.

If you are going to write separate Windows applications (like tools), then I can strongly recommend Visual Studio 2022 since it has workflows well-suited for that purpose.

**Visual Studio Code**
The similarly-named, but completely different program, Visual Studio Code (VSCode) is kind of like a lite version of Visual Studio. It's main advantage is that it runs a lot faster and is cross platform + open source.

**Sublime Text + Cmder**
I really only use this for Unreal Engine C++ programming since Visual Studio is slow and bloat your machine with intermediate files related to intellisense. Not a bad choice but like I said earlier, I don't suggest a beginner should use this. That being said, it's improved my skills with Unreal since I've been able to easily navigate the UE source code and I better understand how to write C++ code.

## Assets

I wouldn't stress about assets too much when starting out. I used the stock assets that came with GameMaker 8.1 when I first used it and gradually made my own (crude) 2D sprites. Source them from wherever but if you use something without permission, don't expect to be able to publish your game, which you also shouldn't worry about as a beginner.

### Textures

**Gimp** is my go to for texturing and image processing but I do use **Aseprite** for low-res pixel art. It's not free unless you are willing to put in the legwork to building it yourself but **Pain.NET** is a good alternative, and Gimp could honestly work too since it supports palettes just like Aseprite.

If you are looking for something you can do drawing or painting in, then I hear **Krita** is pretty solid as well. I'd say definitely use these software in combination with each other since while they do all have some overlap, they also have their unique strengths.

### Audio

For general audio processing, **Audacity** is about as good as they come. I'd be remiss not to mention that Audacity is undergoing major changes so it could change for the worse or better.

For music we have **Linux Multi-Media Studio** or **LMMS**. Now in spite of the name, it is on Windows but as you would expect from the name, it's open source, as is most of the software mentioned here.

### Video

You probably won't be making videos too often, but I've done it enough I thought I'd mention it anyways.

I've used variety of video editing programs but **DaVinci Resolve** is my preferred because it's free, powerful, and doesn't destroy my computer's performance like some programs (*cough cough* Premiere Pro and After Effects).

### 3D Modeling

**Blender**. 'Nuff said. It's free + open source and avaiable on its own site as well as Steam!

## Version Control

Use **Git** + **GitHub Deskop**. Starting out, this will be more than sufficient. It's not too hard to use, just getting used to some terminology and workflows, like what is a commit, branch or repo? 

## Collaboration

Little disclaimer, I've not found a lot of success collaborating with other people. It's likely just a me problem, but I struggle to find people who I feel I can reliably work with. Culture fit is important to me and I just can't seem to find "my crowd" if that makes sense.

Anyways the two main places I look are on Reddit and Discord. The subreddit I use is r/INAT or "I need a team". Most of the posts are usually nonsense and I roll my eyes frequently browsing it. I was able to get my first contracting gig through it so it does have its uses. Diamond in the rough for sure.

For Discord servers, I would say joining any related to the engine, language, or genre of game you are working on/with. There are Discord servers for subreddits like r/INAT but its mostly the same people serial posting on both.

## Your First Game

Find a simple game and clone it. The reason you want to clone an existing simple game is that you won't need to concern yourself with making it unique so you can get the technical fundamentals down. There will be time for design later.