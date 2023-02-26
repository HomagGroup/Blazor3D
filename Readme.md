# Blazor3D
![Blazor3D](../main/Assets/Blazor3D.jpg)

## Making opensource

Because of the war in Ukraine and often power outages in my city, I don't have much time to develop Blazor3D.

So, I decided to open its source code to the community.
I hope it will be valuable for you.

You can find the source code in my other [Blazor3D-Core repository](https://github.com/simutaroman/Blazor3D-Core).

It still requires documentation to do, but for those who never read the docs it's OK :)

Glory to Ukraine! Glory to the Heroes!

## Overview
This repository contains examples of using the Blazor3D Viewercomponent in the [ASP.NET Core Blazor](https://docs.microsoft.com/en-us/aspnet/core/blazor/) applications.

If you want to find more tutorials, API Reference Guide etc., please, visit project webpage at [https://blazor3d.com](https://blazor3d.com) (for now it's on pause)

Live preview of these examples WebAsm versionj you can see at  [https://simutaroman.github.io/Blazor3D/](https://simutaroman.github.io/Blazor3D/) 

## Installing

With .NET CLI
```
dotnet add package Blazor3D
```
With Package Manager
```
Install-Package Blazor3D
```
Or just download it from <https://www.nuget.org/packages/Blazor3D> and add it as project reference.

## Using

### With default scene
See example [here](../main/Examples/Blazor3D.Examples.WebAsm/Pages/Index.razor)

1. Add usings to the _Imports.razor or to your page
 ```
@using Blazor3D.Viewers
```
2. Put Blazor3D Viewer component to your page
 ```
<Viewer UseDefaultScene=@true></Viewer>
```

### With custom scene
See example [here](../main/Examples/Blazor3D.Examples.WebAsm/Pages/Example01.razor)

1. Add usings to the _Imports.razor or to your page
 ```
@using Blazor3D.Settings
@using Blazor3D.Scenes
@using Blazor3D.Lights
@using Blazor3D.Maths
@using Blazor3D.Materials
@using Blazor3D.Objects
@using Blazor3D.Geometires
@using Blazor3D.Enums
```
2. Put the View3D component to you blazor application page and add some code
```
<div class="row justify-content-center">
    <div class="col-6 v3d">
        <Viewer @ref="View3D1" ViewerSettings=@settings Scene=scene />
    </div>
</div>

@code {
    private Viewer View3D1 = null!;
    private Guid objGuid;
    private ViewerSettings settings = new ViewerSettings()
        {
            ContainerId = "example1",
        };

    private Scene scene = new Scene();
    protected override Task OnInitializedAsync()
    {
        scene.Add(new AmbientLight());
        scene.Add(new PointLight()
            {
                Position = new Vector3
                {
                    X = 1,
                    Y = 3,
                    Z = 0
                }
            });
        scene.Add(new Mesh());
        scene.Add(new Mesh
            {
                Geometry = new BoxGeometry
                {
                    Width = 2,
                    Height = 0.5f
                },
                Position = new Vector3
                {
                    X = -1,
                    Y = 1,
                    Z = -1
                }
                        ,
                Rotation = new Euler
                {
                    X = (float)(Math.PI / 4)
                }
            });

        scene.Add(new Mesh
            {
                Geometry = new CircleGeometry(),
                Position = new Vector3
                {
                    X = 1,
                    Y = 1,
                    Z = -1
                },
                Scale = new Vector3(0.5f, 1f, 1f)
            });

        return base.OnInitializedAsync();
    }
```

## Examples

### Example01

This example shows how to:
    <ul>
        <li>Control the Blazor3D Viewer component's dimensions with CSS</li>
        <li>Add custom ViewerSettings</li>
        <li>Add user-defined scene</li>
        <li>Add user-defined lights and meshes with different geometries</li>
        <li>Turn on/off objects selecting mode </li>
        <li>Subscribe ObjectSelected event</li>
    </ul>

### Example02

This example shows how to:
    <ul>
        <li>Control the Blazor3D Viewer component's dimensions with CSS and HTML element style</li>
        <li>Add user-defined scene and lights</li>
        <li>Import obj, Collada, Fbx, Gltf or Stl model on button click asyncronously</li>
        <li>Control loaded object by its uuid with ObjectLoaded event</li>
        <li>Import file when all required JS modules already loaded (inital load)</li>
    </ul>

### Example03

This example shows how to:
    <ul>
        <li>Control the Blazor3D Viewer component's dimensions with CSS</li>
        <li>Use animated orthographic camera</li>
        <li>Use helpers</li>
        <li>Camera toggling</li>
        <li>Stop camera animation on start using orbit control</li>
    </ul>

### Example04

This example shows how to:
    <ul>
        <li>Add new cubes (or it can be any mech) with specified positions</li>
        <li>Update selected cube (or any mech) position (in fact the complete scene is updated)</li>
        <li>Delete selected cube (or any mech) from the scene</li>
    </ul>

### Example05

This example shows how to:
    <ul>
        <li>Load a bitmap texture to the mesh using URL</li>
        <li>Use different wrapping types</li>
        <li>Use texture repeating, offset and rotation</li>
    </ul>
