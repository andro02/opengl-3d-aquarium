<h1 align="center">
  3D Aquarium — OpenGL Graphics Project
</h1>

<p align="center">
  An interactive 3D aquarium scene built from scratch in C++ and OpenGL, featuring two independently controllable fish, dynamic lighting, textured models, particle effects, and an animated treasure chest.
</p>

<div align="center">

![C++](https://img.shields.io/badge/C%2B%2B-OpenGL-00599C)
![OpenGL](https://img.shields.io/badge/OpenGL-3.3-5586A4)
![GLFW](https://img.shields.io/badge/GLFW-window%2Finput-brightgreen)
![status](https://img.shields.io/badge/Status-University%20Project-yellow)

</div>

## About the Project

This project renders an interactive 3D aquarium using raw OpenGL (via GLFW and GLEW), built entirely with a custom mesh/model/shader pipeline rather than a game engine. Two fish — a goldfish and a clownfish, loaded from OBJ models — can be moved independently around the tank, colliding with the tank walls and a floating treasure chest. The scene includes textured sand, glass tank walls, a Phong-lit environment, food particles the fish can eat, air bubble effects, and a toggleable treasure chest.

## Features

- Two independently controllable 3D fish models (goldfish and clownfish), each loaded from `.obj`/`.mtl` files with their own textures
- Real-time keyboard controls for movement, collision with the tank bounds and objects
- Air bubble particle emission triggered per fish
- A food-spawning system: food particles fall through the water and are eaten on contact with a fish
- An animated, toggleable treasure chest with open/close behavior
- Phong lighting model (ambient, diffuse, specular) applied across fish, tank, and props via custom GLSL shaders
- Multiple shader programs for different material types — basic (untextured), textured, fish, and screen-space overlay
- Runtime toggles for depth testing and back-face culling (for debugging/inspection)
- A frame-rate-capped render loop (75 FPS) with delta-time-based movement
- A 2D screen-space overlay shader used to render a signature/watermark image over the 3D scene

## Controls

| Key | Action |
|---|---|
| `W` `A` `S` `D` | Move the goldfish (forward/left/back/right) |
| `Q` / `E` | Move the goldfish up / down |
| `Z` | Emit bubbles from the goldfish |
| `Arrow keys` | Move the clownfish (forward/left/back/right) |
| `K` / `L` | Move the clownfish up / down |
| `X` | Emit bubbles from the clownfish |
| `F` | Spawn food in the aquarium |
| `C` | Open/close the treasure chest |
| `1` / `2` | Enable / disable depth testing |
| `3` / `4` | Enable / disable back-face culling |
| `Esc` | Exit the application |

## Architecture

- **Main.cpp** — window/context setup, the render loop, input handling, and scene composition.
- **Shader** — a wrapper for compiling and using GLSL vertex/fragment shader programs (`basic`, `texture`, `fish`, `overlay`).
- **Mesh** — generic vertex/index buffer wrapper used to build primitive geometry (cubes, spheres) and rendered models.
- **Model** — loads external `.obj`/`.mtl` fish models and their textures.
- **Util** — shared helper functions (e.g. texture loading via `stb_image`).
- Custom classes for the **Aquarium** (tank bounds and sand floor), **Fish** (movement, collision, bubble particles), **FoodSystem** (spawning and eating logic), **Chest** (animated open/close prop), and **Overlay** (2D screen-space image rendering).

## Technologies

**Language:** C++

**Graphics API:** OpenGL 3.3 (core profile)

**Libraries:** GLFW (window/input), GLEW (OpenGL function loading), GLM (math), stb_image (texture loading)

**Shading:** Custom GLSL vertex/fragment shaders (Phong lighting)

## Project Structure

```
📦 root
 ┣ Main.cpp              — entry point, render loop, input, scene setup
 ┣ Shader.h              — GLSL shader program wrapper
 ┣ Mesh.h                — vertex/index buffer wrapper, primitive mesh generation
 ┣ Model.h               — OBJ model loading
 ┣ Util.h / Util.cpp     — texture loading and helper utilities
 ┣ stb_image.h           — third-party image loading library
 ┣ *.vert / *.frag       — GLSL shaders (basic, texture, fish, overlay)
 ┗ 📂 res                — 3D models, materials, and textures (fish, chest, sand, coin, etc.)
```

## Running the Project

### Prerequisites

- Windows with Visual Studio (project uses `.vcxproj` / `.sln`)
- GLFW, GLEW, and GLM available via NuGet (see `packages.config`) or vcpkg

### Steps

```bash
# Open the solution
3D_Projekat.sln
```

Open `3D_Projekat.sln` in Visual Studio, restore the NuGet packages if prompted, then build and run the `3D_Projekat` project.

## Author

Andrija Slović, SV12/2021 — university project, Computer Graphics course.
