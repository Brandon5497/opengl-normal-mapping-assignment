# Project Assignment 03: Normal Mapping  
*Python • moderngl • PyGLM • OpenGL • Pygame*

This project renders a lit 3D scene with **normal mapping** using Python and OpenGL (via `moderngl`).  
It was completed as part of a computer graphics course and extends starter code provided by the instructor.

The scene shows a **golden teapot** resting on a **grass floor**.  
Both objects use normal maps to create detailed surface bumps, and the lighting can be toggled between a **directional** and a **point light**.


---

## Features

### Normal Mapping
- Uses a **normal map** for the floor (`floorNormal.png`) to create circular engraved patterns.
- Uses a **brick normal map** on the teapot (`brick.png`) to give it a bumpy, brick-like surface.
- Normal maps are sampled in the fragment shader and used to perturb the surface normal for lighting.

### Texturing & Materials
- Floor uses a **diffuse grass texture** (`grass.jpg`).
- Teapot uses a **gold texture** (`gold.jpg`) with a metallic look.
- Separate samplers for:
  - `map` – base color texture
  - `normalMap` – normal map texture
- Configurable **metal** flag in the shader to switch material behavior.

### Lighting
- Orbiting light source computed with `getLightVector(angle)`:
  - **Directional light** mode (uses light direction, `w = 0`)
  - **Point light** mode (uses light position, `w = 1`)
- Small **icosahedron mesh** (`20_icosahedron.obj`) visualizes the current light position using a separate shader.
- Basic Blinn–Phong style lighting with a `shininess` constant.

### Camera & Scene
- Camera uses **PyGLM** (`glm.lookAt`, `glm.perspective`) for:
  - View matrix
  - Perspective projection
- Floor is a scaled cube (`cube.obj`) transformed into a flat ground plane.
- Teapot (`teapot_with_texCoords.obj`) is scaled & translated to sit on the floor.

---

## Controls

- `ESC` – Quit  
- `P` – Pause / resume light animation  
- `L` – Toggle between **directional** and **point** light source  

---

## Technologies Used

- **Python 3**
- **moderngl** – modern OpenGL wrapper
- **PyGLM (`glm`)** – math library for matrices & vectors
- **Pygame** – window & event handling
- **NumPy**
- Custom OBJ loading via `LoadObject.getObjectData`

---

## Project Structure

```text
.
├── ProjectAssignment03.ipynb
├── LoadObject.py
├── teapot_with_texCoords.obj
├── cube.obj
├── 20_icosahedron.obj
├── gold.jpg
├── grass.jpg
├── floorNormal.png
├── brick.png
└── ProjectAssignment03Screenshot.png
