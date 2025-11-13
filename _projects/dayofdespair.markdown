---
layout: project
title: Day Of Despair
description: A zombie survival game made with Unreal Engine 5
full-width: true
---

## Overview

This is a zombie survival and simulation game inspired by the likes of "Project Zomboid" and "The Almost Heaven Crisis". Made with Unreal Engine 5 using a combination of blueprints for high level gameplay and C++ for any performance-necessary features such as precaching audio and pre-compiling materials/shaders upon startup.

Source Code: Available upon email request

Sorry, I can't easily share the code because a lot of the game is written in blueprints and I plan to release this game commercially. You can easily build the game just from what is on GitHub (that is how we collaborate after all) and that would undermine any of my efforts to make any income on this game. After all, why would you buy it for 10 bucks when you could just clone the Git repo and have the finished game right there?

![Inventory Screen]({{ site.baseurl }}/assets/dod/inventory.png)

## Mechanics

- **Inventory** - Uses an actor component that handles all inventory related functionality that can be placed on any actor that requires storing items. The inventory UI is much like Arma 3, allowing you to drag and drop items from your inventory to the appropriate equip slots as well as right-click functionality to immediately equip an item into slot during intense moments. You can also see items near you on the ground to further help get items during chases.

- **Action Menu** - In Project Zomboid, you can right-click on objects in the world which brings up a context menu for additional ways to interact/use the object. Day of Despair boasts a similar feature where holding right-click and releasing on certain objects, you will be prompted with a list of all of the available actions for that object which I have called the "Action Menu", just pressing right-click will use its default action. For example, you may have a door where you can open/close it, and lock/unlock it. The default action is opening/closing it, but bringing up the Action Menu will have the open/close option as well as the lock/unlock option. This works by using an interface with methods for returning a list of strings for each action as well as an interact function. Actors may implement this interface and use a switch statement for each of the actions.

- **Stats** - Variables like health, stamina, hunger/thirst, are kept in separate components and can be modified easily to make the game harder or stronger. The UI also uses progress bars and text to show the current value of each stat. Your infection level however, uses an overlay that becomes more opaque as the infection progresses and if it's high enough, sounds will play to further reflect the players dwindling sanity and adds greatly to the atmosphere of the game. Thanks to the nature of the components, classes must opt in to certain features such as zombies not using the hunger and thirst mechanics for obvious reasons

- **Day/Night Cycle** - Using a timeline component to control the sun rotation & a timer to 'tick' the seconds, I was able to achieve a smooth Day/Night cycle and because the core of the system uses a DateTime struct, the complete date of the game is also achieved for further immersion. The function used for getting the day of the week was also written in C++ and is an implementation of [Zellers Congruence](https://en.wikipedia.org/wiki/Zeller%27s_congruence).

```cpp
FString ADodGameMode::GetDayOfTheWeek(FDateTime Date)
{
	int32 Year = Date.GetYear();
	int32 Month = Date.GetMonth();
	const int32 Day = Date.GetDay();

	const TMap<int, FString> DayMap
	{
		{0, TEXT("Saturday")},
		{1, TEXT("Sunday")},
		{2, TEXT("Monday")},
		{3, TEXT("Tuesday")},
		{4, TEXT("Wednesday")},
		{5, TEXT("Thursday")},
		{6, TEXT("Friday")},
	};

    // January and February are counted as months 13 and 14 of the previous year
	if (Month == 1)
	{
		Month = 13;
		Year--;
	}
	if (Month == 2)
	{
		Month = 14;
		Year--;
	}

    const int32 DayOfMonth = Day;
    const int32 MonthIndex = Month;
    const int32 YearOfCentury = Year % 100;
    const int32 Century = Year / 100;
    const int32 ZellerCalc = DayOfMonth + 13 * (MonthIndex + 1) / 5 + YearOfCentury + YearOfCentury / 4 + Century / 4 + 5 * Century;
    int32 DayOfWeekIndex = ZellerCalc % 7;


	DayOfWeekIndex = DayOfWeekIndex % 7;

	return *DayMap.FindChecked(DayOfWeekIndex);
}
```

- **AI** - The zombies use a fairly simple AI behaviour model where they wander, investigate noises, and chase the player, if spotted. They are also capable of breaking down doors that stand between them and their victim.

## Technical Callenges

- **Performance** - Nearing the end of the 30 day MVP, I discovered that packaged builds of the game had severely worse performance than in editor. I did my best to alleviate this by adjusting the render distance on foliage, and the character/item models. It helped but not as much as I was hoping. After a long session debugging the game and using the Unreal Insights Profiler, I found out that the game was defaulting to Ultra graphics settings which was extremely wasteful due to the fog present in main level that occluded most of the geometry so it was turned down to High which looked identical but had performance gains of 200% going from ~50 to ~120fps on my personal computer.

- **Inventory** - The right-click functionality to pick up items off the ground had a strange bug where getting a ground item from the inventory, dropping it, and picking it up from the world would give an invalid item or duplicate it. I spent a long time debugging this, setting breakpoints, and printing every last value to the screen and tracked the bug to the function that drops the item and found out I forgot to set the variable corresponding to the owning inventory to none. If it was not for other people testing, I never would have found this bug since I always used the inventory menu to pickup nearby items.

- **Action Menu** - As clever as the action menu system is, it is necessarily a hack to get around the fact Unreal Engine does not allow multicast dynamic delegates to be used as input parameters for both events and functions so this was a workaround to get something up and running.

- **Day/Night Cycle** - In previous games, I had written day/night cycles but they relied exclusively on ticks and mathematics to set the correct sun position in the sky. I wanted something smoother in Day of Despair, so I spent many hours researching how to use timeline components for this but it was very tricky to keep the sun position and time shown on screen in sync.