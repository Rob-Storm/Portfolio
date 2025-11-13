---
layout: guide
title: Unreal Engine 5 BSP
description: How to use BSP brushes in UE5
---

Recently, I saw someone on Reddit asking about how to work with BSP brushes inside of Unreal to which they got an erroneous reply saying they could not, so this one is for you, Dan. I doubt BSP editing will go away in Unreal Engine 5 and it still shows up in 5.5.4. Given how its a little more obscure now than in UE4, they may remove it or further obscure it in UE6 whenever that comes out in the next decade, but for now we still have it.

It's pretty easy to get BSP editing up and running, you just need to add a brush actor, which will be under geometry (Unreal provides a few primitives as well as both spiral and curved stairs), and go into BSP editing mode.

![UE5 Geometry Actors]({{ site.baseurl }}/assets/unrealbsp/geometryactors.png)
![UE5 Brush Editing Mode]({{ site.baseurl }}/assets/unrealbsp/brushediting.png)

Compared to the Hammer Editor, Unreal's BSP editing does have some niceties like selecting faces and edges on top of individual vertices. Speaking of editing, you'll primarily be manipulating brushes by moving around their faces/edges/vertices. When you click on a face, the details panel with allow to edit properties for that face. It's basically the Face Edit Sheet/Toggle Texture Application Tool. 

![UE5 Brush Materials Details]({{ site.baseurl }}/assets/unrealbsp/bspmaterials.png)

If you want to make your editor resemble the classic Hammer Editor, you do that pretty easily too. All you have to do is click this little button and you'll get 4 viewports that you can change their view and render mode.

![Unreal Editor Viewports]({{ site.baseurl }}/assets/unrealbsp/hammerviewports.png)
![Unreal Editor Render Modes]({{ site.baseurl }}/assets/unrealbsp/rendermodes.png)
![Final Result]({{ site.baseurl }}/assets/unrealbsp/final.png)

If you want the 2D viewports to move independently of each other you can turn of the "Linked Orthographic Viewport Movement" in the editor preferences. Have fun!