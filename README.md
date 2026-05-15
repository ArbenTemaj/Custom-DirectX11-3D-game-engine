# Custom DirectX11 Game Engine

Built a closed-source real-time 3D engine featuring a PBR rendering pipeline, 
NVIDIA PhysX integration, skeletal animation blending, and a full post-processing 
stack including bloom, fog, and color grading. Demo available on request. Also, 
Feel free to check out my website for socials and contact information click [here](https://arbentemaj.github.io/)

Here below you can find all information regarding this game engine's features!
---

## Table of Contents

| Feature | Status | Notes |
|:--------|:------:|------:|
| [User Interface](#user-interface) | ✅ Available | Dear ImGui integration for game engine UI configuration |
| [Camera Controls](#camera-controls) | ✅ Available | Free camera, third-person camera, and camera settings |
| [Global Materials Controls](#global-materials-controls) | ✅ Available | Various toggle controls for PBR materials |
| [Lighting Controls](#lighting-controls) | ✅ Available | Directional, Point, and Spot lights with several optional controls |
| [Shadow Controls](#shadow-controls) | ✅ Available | Shadow map visualization, resolution options, and on/off toggle |
| [Entity Creation](#entity-creation) | ✅ Available | Creation of entities with material properties and physics settings |
| [Material Override Settings](#material-override-settings) | ✅ Available | Real-time material override, fully customizable for each entity |
| [Physics Engine](#physics-engine) | ✅ Available | NVIDIA PhysX engine integration for game engine physics |
| [Scene Hierarchy](#scene-hierarchy) | ✅ Available | List of active entities, selection of entities, and entity removal |
| [Save/Load Scene](#saveload-scene) | ✅ Available | Save and load active scenes |
| [Animations](#animations) | ✅ Available | Full locomotion animation and non-locomotion animation support |
| [Color Grading Settings](#color-grading-settings) | ✅ Available | Color grading presets and manual custom adjustments |
| [Fog Settings](#fog-settings) | ✅ Available | Fog post-processing effects with color, intensity, and distance options |
| [Blur and Bloom Settings](#blur-and-bloom-settings) | ✅ Available | Bloom intensity, separation by level, and type of bloom; fixed blur option |

> All features marked ✅ **Available** are fully supported by the engine.
> Features are constantly being updated check [Updates](#updates) for the latest information.

---

## Updates

### New Features

- Animation locomotion for third-person playable character
- Third-person character blended animations from walk-to-sprint and vice versa
- Each entity now owns its own material overrides, eliminating material race conditions
- Fixed third-person character camera to follow directly behind the playable character

### Future Updates

1. Transition from free Mixamo animations to custom paid animations
2. Add character state machine
3. Update all textures to 2K PBR materials with displacement textures
4. Extend Save/Load scenes to include all lighting and post-processing data

---

## User Interface

The engine features a fully integrated **Dear ImGui** interface, giving you real-time access to every engine system from a single, dockable panel layout. Each feature of the engine from lighting to post-processing is exposed through organized, collapsible windows so you can quickly navigate, tweak, and iterate without ever leaving the viewport. The UI is designed to be non-intrusive, snapping to the edges of the screen so your scene always remains the focus.

▶️ [Watch the UI walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=52s)

![UI Overview](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/UI1.png)

---

## Camera Controls

The engine supports multiple camera modes to suit both development and gameplay needs. **Free Camera** mode lets you fly through your scene with full six-degrees-of-freedom navigation, ideal for level inspection and debugging. **Third-Person Camera** mode locks the camera behind a target entity and tracks it dynamically with smoothed follow behavior. Camera settings such as field of view, movement speed, and sensitivity are all adjustable at runtime through the UI.

▶️ [Watch the Camera Controls walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=82s)

![Camera Controls](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/Camera1.png)

![Camera Controls](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/Camera4.PNG)

![Camera Controls](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/Camera2.png)

![Camera Controls](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/Camera3.png)
---

## Global Materials Controls

The Global Materials panel provides high-level toggle controls over the engine's **Physically Based Rendering (PBR)** pipeline. You can enable or disable individual PBR channels such as albedo, normals, roughness, metalness, and ambient occlusion across all scene materials at once. This makes it easy to visually debug shading issues, verify texture maps are loaded correctly, or quickly compare the visual impact of each channel on your scene.

▶️ [Watch the Global Materials walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=115s)

![Global Materials Controls](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/PBR.png)

---

## Lighting Controls

The lighting system supports three industry-standard light types: **Directional**, **Point**, and **Spot** lights. Each light exposes a full suite of controls including color, intensity, range, and attenuation falloff. The directional light serves as the primary sun source, driving the shadow system, while point and spot lights can be freely placed and tuned to bring depth and atmosphere to your scene. All lighting updates are reflected in the viewport in real time.

▶️ [Watch the Lighting Controls walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=260s)

![Lighting Controls](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/Lights.png)

---

## Shadow Controls

The engine features a **shadow mapping** system driven by the directional light. The Shadow Controls panel allows you to toggle shadows on or off, select from multiple shadow map resolutions for a quality-versus-performance trade-off, and visualize the raw shadow depth map directly in the viewport for debugging purposes. Tunable bias controls help eliminate shadow acne and peter-panning artifacts across different scene scales.

▶️ [Watch the Shadow Controls walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=210s)

![Shadow Controls](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/Shadows.PNG)

---

## Entity Creation

The Entity Creation panel allows you to spawn new scene objects at runtime and configure them immediately. When creating an entity you can define its initial **material properties** selecting textures and PBR parameter values as well as its **physics settings**, such as collision shape, mass, and whether it is static or dynamic. Entities are instantly added to the scene hierarchy and can be further refined through the Material Override and Physics panels.

▶️ [Watch the Entity Creation walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=460s)

![Entity Creation](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/EntityCreate.PNG)

---

## Material Override Settings

Every entity in the scene owns its own independent set of **material overrides**, allowing you to customize the look of any object without affecting others. The override panel exposes full PBR parameter control albedo color, roughness, metalness, normal map intensity, and more all adjustable in real time as you watch the changes update live in the viewport. This system was designed to eliminate material race conditions that previously caused unpredictable visual results when multiple entities shared material state.

▶️ [Watch the Material Override walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=359s)

![Material Override Settings](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/MaterialsOverride.PNG)

---

## Physics Engine

The engine integrates **NVIDIA PhysX** as its physics backend, providing robust, high-performance simulation for both static and dynamic objects. Entities can be assigned rigid body properties including collision shapes (box, sphere, capsule, mesh), mass, restitution, and friction. The physics simulation runs in lockstep with the engine's update loop, ensuring consistent behavior across frame rates. Debug visualization overlays can be toggled to inspect collision geometry directly in the viewport.

▶️ [Watch the Physics Engine walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=327s)

![Physics Engine](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/physics.PNG)

---

## Scene Hierarchy

The Scene Hierarchy panel provides a live list of every entity currently active in the scene. You can select any entity with a single click to bring its properties up in the inspector panels, or remove it from the scene entirely. The hierarchy updates dynamically as entities are created or destroyed, keeping your overview accurate at all times. Selection state is shared across all editor panels, so selecting an entity in the hierarchy immediately highlights it in the viewport and populates the material and physics editors with its current values.

▶️ [Watch the Scene Hierarchy walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=406s)

![Scene Hierarchy](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/SceneH.PNG)

---

## Save/Load Scene

The Save/Load system lets you persist your entire scene to disk and restore it in a later session. Entity transforms, material override values, physics properties, and hierarchy structure are all serialized and written to a scene file. Loading a scene restores the full state so you can continue exactly where you left off. Future updates will extend this system to also capture lighting configuration and post-processing settings.

▶️ [Watch the Save/Load Scene walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=587s)

![Save/Load Scene](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/s_load.PNG)

---

## Animations

The engine supports a full **skeletal animation** system with both **locomotion** and **non-locomotion** animation types. Locomotion animations drive the character's world-space movement in sync with their motion, producing natural, grounded movement for traversal. Non-locomotion animations handle actions like idles, attacks, or gestures that play in-place. The system also supports **blended transitions** for example, smoothly blending between a walk and a sprint cycle based on the character's current speed giving movement a polished, responsive feel.

▶️ [Watch the Animations walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=543s)

![Animations](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/anims.PNG)

---

## Color Grading Settings

The Color Grading panel gives you full control over the final look of the rendered image through a **post-processing color pipeline**. You can choose from a set of built-in presets such as cinematic warm, cool desaturated, or high contrast for instant stylistic results, or take full manual control and dial in your own values for exposure, contrast, saturation, highlights, midtones, and shadows. Changes apply in real time so you can tune the mood of your scene with immediate visual feedback.

▶️ [Watch the Color Grading walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=144s)

![Color Grading Settings](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/colorgrading.PNG)

---

## Fog Settings

The Fog system is a **post-processing effect** that adds atmospheric depth and distance haze to your scene. You can control the fog color to match your scene's lighting mood, adjust the intensity for subtle haze or heavy mist, and tune the start and end distances to define exactly where the fog begins to appear and where it reaches full opacity. Fog is a powerful, low-cost tool for masking far-clip distances and reinforcing the sense of scale and atmosphere.

▶️ [Watch the Fog Settings walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=189s)

![Fog Settings](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/fog.PNG)

---

## Blur and Bloom Settings

The Blur and Bloom panel controls two complementary post-processing effects. **Bloom** simulates the way bright light sources bleed and glow in a physical camera lens you can set the overall bloom intensity, isolate which luminance levels contribute to the bloom by adjusting the separation threshold per level, and choose between bloom algorithms for different visual styles. **Blur** provides a fixed screen-space blur pass that can be used for stylistic soft-focus effects or as a building block for depth-of-field in future updates.

▶️ [Watch the Blur and Bloom walkthrough](https://www.youtube.com/watch?v=mLddE1BvB4w&t=225s)

![Blur and Bloom Settings](https://github.com/ArbenTemaj/Custom-DirectX11-3D-game-engine/blob/main/uploads/bloom.PNG)

---
