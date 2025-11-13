---
layout: article
title: Why is Visual Studio so slow with Unreal?
description: Some theories and speculation for VS2022 performance.
---

It's no secret that Visual Studio 2022 is slow when working in Unreal C++ projects, so much so that the often stated response on social media and forums is to "Just use Rider." I don't think this is the panacea everyone erroneously believes it to be but I can understand the sentiment. Some of Visual Studio's problems include:


- **Poor IntelliSense** - In fact, it's sometimes recommended to just turn it off for giving false errors

- **Types being corrupted when building** - More of a hot-reload/live coding problem

- **Live coding making types go missing** - Again, not necessarily Visual Studio's fault

- **Slow iteration times compared to Blueprints**

Aside from the type corruption, I have experienced all of these to some extent, and usually, I can remedy the IntelliSense by just waiting for the project to be scanned then it greatly improves, so much so that the Unreal Engine Integration Tool will show type references in Blueprints!

The missing type issue usually shows up when I close the editor and open it back up, and this has been remedied by enabling the "Force Compilation at Startup" option in the Editor Preferences.

![Unreal Settings]({{ site.baseurl }}/assets/ue5vs/settings.png)

So why is this the case? I mean, Visual Studio works well with Unity, so why not with Unreal? Well, I have some theories as to why. I am by no means a game engine or tools programming expert but I know enough to get by. Only Epic Games and Microsoft can really give definitive answers but here goes anyways. 

I think there are two main points here that hurt Visual Studio's performance:

### Quick disclaimer!

I am not an engine programmer by trade. I've made low level engines using Raylib and MonoGame but I have never built something from the ground up in C++ using something like SDL (though I have used OpenTK and C# :P). This is primarily speculation based off of my own experience and knowledge with Unreal, C++, Visual Studio and educational content I have consumed about game engine development. 

## C++ is complicated...

I am sure you already know how code gets compiled, either directly to machine code like with C++ or to an intermediate language like that gets run on a virtual machine and the code is compiled "Just In Time" as with C# and Java. I think this difference not only explains why we have poorer iteration times in Unreal but also why IntelliSense is much weaker (and slower) compared to a C# project, it is probably easier for IntelliSense to parse through managed code than unmanaged code. Additionally, the Unreal Engine codebase (on top of being massive) makes liberal use of macros, generated code, and 

With C# I find that the autocomplete feels like it is reading my mind sometimes, but with C++ we don't even get niceties like automatically including the header file a type is declared in if you reference a type somewhere (e.g. if you type UCapsuleComponent it should add #include "Components/CapsuleComponent.h" at the top of the file). 

Furthermore, I don't think Microsoft have given much thought for Unreal Engine C++ development because a majority of Visual Studio C++ developers are not making Unreal Engine games. Clearly enough of the userbase is because Microsoft felt it prudent to include a Workload just for C++ games development which includes the integration plugin but its not big enough to warrant making a specialized version of IntelliSense just for Unreal Engine's ecosystem.

## Too much of the build process happens outside of Visual Studio

Unreal Engine necessarily uses a custom offline build system to allow interoperability between C++ and Blueprints and more importantly enables a cross-platform build solution. C++ code that has to be exposed to Blueprints will use macros like UCLASS, UPROPERTY, or UFUNCTION which enables the Unreal Build Tool to expose those types, properties or functions. This all happens outside of Visual Studio and as such, the development workflow suffers.

## Why Epic/Microsoft should do better

Visual Studio 2022 is both the default IDE for Unreal and the recommended IDE by Epic Games themselves for Unreal Engine. With that in mind, it's frankly embarrassing that Visual Studio performs as bad as it does and I (perhaps naively) believe that they both have a moral obligation to improve the experience, Epic for endorsing Visual Studio and Microsoft for developing the laughably terrible "Unreal Engine Integration" plugin for Visual Studio. I don't expect it to be perfect but something faster, and with some quality of life improvements, namely auto-including header files, would be acceptable.

## No, Rider is not the solution

Remember how I said people will typically just proclaim, "Use Rider!" as a cure-all solution? Well unsurprisingly enough, it isn't the cure-all that everyone thinks. I would agree that it does offer better productivity features for Unreal Engine developers but it does have its problems. For one, it isn't free for commercial projects so I already don't want it but also, you have to pay a subscription to use it if you do decide to fork over the cash. For a lot of developers, I know this will be a deal-breaker so it may seem like there are no good options for writing C++ code in Unreal, but I assure you, things are not that drab.

## Conclusion

I've talked a fair bit about IDEs, C++, and Unreal. While yes, the Visual Studio performance is not that great at times, it does improve with time. I've found the more time I spend working on a project with C++ code, the better the performance, IntelliSense and stability all get. If you are willing to be patient with Visual Studio, then it can work for you. 

If you don't want to use Visual Studio, that is a perfectly valid approach to programming. If you look at the "Programming" section of the plugins tab, you will see all the IDEs that can integrate with Unreal Engine such as VSCode if you want a lightweight text editor. XCode, if you're working on Mac. KDevelop, for those who want a free and open source IDE, and if none of those sound good, Unreal wizard, Alex Forsythe has a [good video](https://youtu.be/94FvzO1HVzY) about using Sublime and how the Unreal build system works.

Side note, I actually use the Sublime + Cmder approach to Unreal C++ programming and I have found it to be my favorite way to program in UE5. I've also been glad that I have been made to read the engine source code to figure out things because I now understand Unreal Engine's architecture better and I believe not having my hand held by Visual Studio has been a major benefit. Also the lack of the 20 gigabyte intermediate folder is nice too!

Point is, you are not forced into using an IDE and we shouldn't be getting emotional about the software we use. They are just tools after all, and certain tools are better for certain tasks.