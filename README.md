# [Mathemagics: Building Assets for Realtime Effects](https://conference.blender.org/2026/presentations/4223/)

> How does a technical artist approach realtime effects? Using examples from an immersive XR headset experience, industry veteran John Einselen (motion design and technical director at Launch) will walk through some of his approaches; from prototyping within Blender to building final assets and integrating them in realtime game engines.



## Presentation Content

This repository contains the project files used to render content for this Blender Conference presentation, including the Geometry Nodes and Material node trees for all of the illustrated effects. It's going to be a little messy (everything was built in about a week!), but hopefully it's helpful for dissection and exploration.



## Required Blender Extensions

Due to the unique animation and rendering setup (dynamically generated curves and automatic segmentation of timelines based on markers), the project will not be usable without required extensions. These are all part of the free [**Launch Blender Extensions**](https://github.com/jeinselen/Launch-Blender-Extensions), and can be managed via Blender Extensions using the [**repository source**](https://jeinselen.github.io/Launch-Blender-Extensions/index.json).

- **Production Kit**
  - Custom drivers are used throughout the project, using timeline markers to enable/disable assets based on collection naming conventions and animate content with easing algorithms
- **Render Kit**
  - Custom output variables are used to segment timelines into animated segments and images, while Autosave Videos compiles rendered content and delivers to the Presentation folder

Additionally, **Mesh Kit** was used to generate the static UV map meshes for the example illustrations and generate the base mesh data for the QR code. Not required to open and use the project, but was essential for creating the content!



## Project File Structure

This is based on our general project structure, where multiple production segments share a common project root (thus the Blender-specific naming conventions on most folders!).

- `/BCON26`
  - `/B Images` — textures used throughout the project
  - `/B Nodes` — textures rendered from nodes (exclusive to part 05 of the presentation)
  - `/B Renders` — raw output (not committed to Git), used by Render Kit to compile final videos
  - `/B Screenshots` — textures rendered from Blender node trees
  - `/Blender` — main project location
    - `/_Archive` — project variations (not committed to Git)
  - `/Fonts` — font files modified for use in Blender (outlines flattened to prevent corrupted meshing)
  - `/Presentation` — final presentation media

The Blender project itself is organised into several scenes.

- `Main` — primary timeline with all of the animated titles sequences
- `Part1-UV` — UV mapping section with demo and process illustrations
- `Part2-Lines` — static mesh based line animation examples and illustrations
- `Part3-Radial` — repeating radial 
- `Part4-Volume` — volumetric development illustrations
- `Part5-VolumeDemo` — volumetric cloud use case demonstration (separated from the illustrations due to timeline length)

Each scene is segmented using timeline markers. Content is turned on/off and animated based on the name of the parent collection and the current frame position (**Presentation Kit**). When rendered, the output files are named and processed based on the markers as well (**Render Kit**), ensuring the final presentation media is ready to use without manual management.



## Presenting

Rendered media is presented using [**Vuo Presentation Tools**](https://github.com/jeinselen/Vuo-PresentationTools).