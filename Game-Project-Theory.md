- [Game Dev: A Practical Map](#game-dev-a-practical-map)
  - [1. Space \& Coordinates (2D vs 3D)](#1-space--coordinates-2d-vs-3d)
  - [2. Time \& the Game Loop](#2-time--the-game-loop)
  - [3. Motion \& Physics (Kinematics first)](#3-motion--physics-kinematics-first)
    - [🔑 General Rule of Thumb](#-general-rule-of-thumb)
      - [✅ Mnemonic](#-mnemonic)
  - [4. Collision Detection (What hits what?)](#4-collision-detection-what-hits-what)
  - [5. Collision Response (What happens after a hit?)](#5-collision-response-what-happens-after-a-hit)
  - [6. Cameras (2D \& 3D)](#6-cameras-2d--3d)
  - [7. Entities \& Game Architecture](#7-entities--game-architecture)
  - [8. World Building \& Navigation](#8-world-building--navigation)
  - [9. Rendering Basics](#9-rendering-basics)
  - [10. Input Handling](#10-input-handling)
  - [11. Audio](#11-audio)
  - [12. Networking (if applicable)](#12-networking-if-applicable)
  - [13. Tooling \& Pipeline](#13-tooling--pipeline)
  - [14. Performance Patterns](#14-performance-patterns)
  - [15. Design Lenses](#15-design-lenses)
    - [Worked Example: Your Platformer Jump “Double-Fire”](#worked-example-your-platformer-jump-double-fire)
    - [Quick Classification Checklist (use this to scope a game)](#quick-classification-checklist-use-this-to-scope-a-game)

# Game Dev: A Practical Map

## 1. Space & Coordinates (2D vs 3D)

Screen/UI convention (2D): most 2D APIs (HTML5 Canvas, many 2D engines) place the origin at the top-left; x grows right, y grows down. This comes from image raster memory layout and windowing systems.
[HTML Living Standard](https://html.spec.whatwg.org/multipage/canvas.html?utm_source=chatgpt.com)

Math/3D convention: in math/3D graphics you’ll often see right-handed or left-handed systems where y (or z) grows up. Engines differ (Unity: y-up, OpenGL clip space vs world space, etc.). The key is: know your engine’s convention and stay consistent.

Rule of thumb

- Pixel/UI work → y usually down.
- Physics/3D/maths → y usually up (but check your engine).

Useful terms

- World space: the “true” game world coordinates.
- Screen/view space: what’s visible after camera transforms.
- Camera: defines how world is mapped to the screen (position, zoom, rotation, projection).

## 2. Time & the Game Loop

Every real-time game runs a loop that reads input → updates simulation → renders a frame.

- Variable timestep: update once per frame using dt measured between frames. Simple but physics can jitter on slow/fast frames.
- Fixed timestep: run physics at a constant rate (e.g., 60 Hz) and render as often as you can; interpolate for smoothness. This keeps simulation stable and deterministic.
  [Gaffer On Games](https://gafferongames.com/post/?utm_source=chatgpt.com)
  [isaacsukin.com](https://isaacsukin.com/news/2015/01/detailed-explanation-javascript-game-loops-and-timing?utm_source=chatgpt.com)
  `js
    accumulator += frame_dt
    while (accumulator >= fixed_dt):
        simulate(fixed_dt)
        accumulator -= fixed_dt
    render(interpolate(state))
    `

## 3. Motion & Physics (Kinematics first)

State per object usually includes position, velocity, sometimes acceleration.
Discretized update (semi-implicit Euler is common for games):

```js
velocity += acceleration * dt;
position += velocity * dt;
```

Platformers often add:

- Gravity (constant acceleration)
- Jump impulse (set upward velocity once)
- Friction / damping (scale velocity)
- “Coyote time” & “jump buffer” (input quality-of-life so jumps feel great)

Predict-then-resolve: You typically predict next position (using velocity), check collisions against that predicted pose, then resolve (snap back / slide / zero velocity). This avoids tunneling and keeps responses stable.

### 🔑 General Rule of Thumb

1. Solid objects (walls, floor, platforms, ceilings)
   - Always use predictive (next) position.
   - Because if you miss even 1 frame, the player can clip through and break the world.
   - Example: running into a wall, landing on a floor, bonking your head on a ceiling.
2. Hazards (spikes, lava, bullets, traps)

   - Depends on the game feel you want.
   - | Hazard type                             | Use present position if…                                    | Use predictive if…                                                     |
     | --------------------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------------- |
     | **Spikes / fire / instant-death traps** | You want “if it looks like a hit, it counts” (arcade feel). | You want perfect detection even if the player moves very fast.         |
     | **Bullets / projectiles**               | They move slow enough that overlap won’t be skipped.        | They move so fast they could “tunnel” through the player in one frame. |
     | **Lava / poison areas**                 | Present position is enough (since it’s big area-based).     | Only if lava moves or is thin like a line.                             |

3. Power-ups / coins / collectibles

   - Present position is usually enough.
   - Because clipping through them isn’t game-breaking — worst case the player “misses a coin,” which feels fair.

4. Visual effects / weather
   - Always present.
   - Example: rain, wind, background animations. These aren’t solid, they just influence.

⚖️ Why this distinction matters

Predictive checks are heavier (math + logic). If you predict everything:

- CPU usage goes up
- Collisions get harder to manage

So game devs choose carefully:

- Solid → always predict (non-negotiable)
- Hazards/collectibles → depends on importance
- Visual → don’t bother

#### ✅ Mnemonic

    “If clipping breaks the game, predict. If clipping just feels minor, present is enough.”

## 4. Collision Detection (What hits what?)

Two common layers:

- Broad phase: quickly find potential colliding pairs (grids, quadtrees, sweep-and-prune).
- Narrow phase: accurate test for those pairs (AABB overlap, circle vs circle, SAT for convex polygons).
  [Reddit](https://www.reddit.com/r/gamedev/comments/18od4yw/what_are_your_thoughts_on_entity_component/?utm_source=chatgpt.com)

AABB overlap test (axis-aligned rectangles, very common in 2D):
Two boxes overlap if they overlap on both x and y axes:

```js
A.maxX > B.minX && A.minX < B.maxX;
A.maxY > B.minY && A.minY < B.maxY;
```

(AABBs are popular because the math is fast and cache-friendly.)
[Gaffer On Games](https://gafferongames.com/post/fix_your_timestep/?utm_source=chatgpt.com)

SAT (Separating Axis Theorem): used for oriented boxes / polygons. Project shapes onto candidate axes; if a gap exists on any axis, they don’t collide.
[GitHub](https://github.com/GameMakerDiscord/fix-your-timestep?utm_source=chatgpt.com)

Continuous (swept) tests: when things move fast, test the sweep from pos -> nextPos so you don’t pass through thin objects.

## 5. Collision Response (What happens after a hit?)

- Discrete platforms (platformer):
  - Move horizontally first; if you hit a wall, clamp X and zero X velocity.
  - Then move vertically; if moving down and you hit the top of a platform, snap Y to platform top, zero Y velocity, mark grounded.
  - This axis-separation keeps resolution stable and avoids corner “sticking.”
- Sliding: when colliding at an angle, keep the component along the surface, cancel the normal component.
- Bouncy: reflect velocity with a restitution factor.
- Friction: reduce tangential velocity on contact.

## 6. Cameras (2D & 3D)

- Follow: camera centers the player.
- Dead zone: only move camera when player leaves a central window to reduce jitter.
- Lerp/smoothing: exponentially approach target to avoid sharp cuts.
- Zoom & parallax: scale world, layer backgrounds at different scroll speeds for depth.

## 7. Entities & Game Architecture

- OOP (Actor/Component): game objects are classes with update/draw; add behavior via components (physics, sprite, input).
- ECS (Entity–Component–System): data in components, logic in systems; entities are just IDs. Scales well, cache-friendly, used in many modern engines. (See “Entity–Component–System”.)
- Scenes/States: menu, gameplay, pause as separate states with their own update/draw.
- Scripting: glue gameplay with Lua/C#/GDScript/JS, keep engine core in C/C++/Rust.

## 8. World Building & Navigation

- Tile maps: grid-based levels; collision often per tile; easy broad-phase.
  [Wikipedia](https://en.wikipedia.org/wiki/Category%3AVideo_games_about_time_loops?utm_source=chatgpt.com)
- Navmeshes & pathfinding: A\* on grids or navigation meshes (more in 3D).
- Triggers/Volumes: enter/exit regions to fire events (checkpoints, pickups).

## 9. Rendering Basics

2D: draw order (painters algorithm), sprite sheets/atlases, batching to reduce draw calls, animations via frame indices or skeletal systems.
3D: meshes, materials, lights, shadows, shaders; cameras (perspective/orthographic).

## 10. Input Handling

- Polling vs events: games typically poll input each frame and build a “current input state.”
- Edge detection: detect pressed this frame vs held to prevent repeat actions (e.g., single jump on key-down only).
- Quality: add coyote time and jump buffers to make platformers feel responsive.

## 11. Audio

SFX (short, many), music (long, streamed), mixing, volume ducking, positional audio (panning, attenuation), audio middleware (FMOD, Wwise).

## 12. Networking (if applicable)

- Client-server (authoritative server): server owns truth; clients send inputs; prevents cheating but needs prediction/lag compensation.
- Deterministic lockstep (RTS): all clients simulate the same fixed-step world from shared inputs; requires determinism.
- Snapshot interpolation / client prediction: send states at intervals, interpolate/extrapolate to hide latency; correct with reconciliation.
  [Reddit](https://www.reddit.com/r/gamedesign/comments/1ktd844/what_are_tile_based_games_where_units_can_take_up/?utm_source=chatgpt.com)
  [Gaffer On Games](https://gafferongames.com/post/spring_physics/?utm_source=chatgpt.com)

## 13. Tooling & Pipeline

- Engines: Unity, Unreal, Godot, Phaser, custom.
- Editors: level editors (Tiled), sprite tools (Aseprite), 3D DCC (Blender).
- Builds: asset import, compression, platform targets.
- Profiling: frame time, physics step time, draw calls, allocations.

## 14. Performance Patterns

- Spatial partitioning (uniform grids, quadtrees, BVHs).
- Reduce allocations (object pools).
- Batch draws (texture atlases).
- Keep fixed physics step reasonable (e.g., 60 or 120 Hz) and consider CCD for fast movers.

## 15. Design Lenses

- MDA framework: Mechanics (rules & systems) → Dynamics (behavior over time) → Aesthetics (player experience). Great for aligning design with implementation.
  Northwestern Computer Science
- Core loop: the repeatable action cycle (explore→fight→loot→upgrade).
- Onboarding & difficulty curves: teach, test, twist.

### Worked Example: Your Platformer Jump “Double-Fire”

When you saw a “second jump” after landing with one key press, typical causes are:

1. No edge detection: you’re checking “key is down” every frame; the initial press triggers a jump, and if you land while the key is still down, it triggers again that same press.

   - Fix: track keyPressedThisFrame vs keyHeld. Only allow jump on the transition from up→down (or use a jumpConsumed flag that resets when the key is released).

2. Grounding timing: you set grounded = true the instant you touch the platform in the vertical pass. If the key is still down that same frame and you allow grounded + keyDown to jump, you effectively chain into another jump.

   - Fix: require edge-pressed and grounded (or add a tiny “re-arm” delay after landing).

3. Weather randomness overwriting jump: ensure your weather code adds small noise to the jump, not replacing the impulse.

### Quick Classification Checklist (use this to scope a game)

- Foundations: coordinates, camera, game loop (fixed/variable), dt, interpolation.
  [isaacsukin.com](https://isaacsukin.com/news/2015/01/detailed-explanation-javascript-game-loops-and-timing?utm_source=chatgpt.com)
- Physics: kinematics, gravity, friction, impulses, axis-separated collision & response.
- Collision: broad-phase (grid/quadtree), narrow-phase (AABB/SAT), CCD.
  [Reddit](https://www.reddit.com/r/gamedev/comments/18od4yw/what_are_your_thoughts_on_entity_component/?utm_source=chatgpt.com)
  [Gaffer On Games](https://gafferongames.com/post/fix_your_timestep/?utm_source=chatgpt.com)
  [GitHub](https://github.com/GameMakerDiscord/fix-your-timestep?utm_source=chatgpt.com)
- Gameplay Feel: input edge detection, coyote time, buffers.
- World: tiles/nav, triggers, spawns.
  [Wikipedia](https://en.wikipedia.org/wiki/Category%3AVideo_games_about_time_loops?utm_source=chatgpt.com)
- Rendering/Audio: sprites/atlases/draw order; SFX/music basics.
- Architecture: OOP vs ECS, scenes/states, scripting.
- Networking (optional): client-server, prediction/interp, reconciliation.
  [Reddit](https://www.reddit.com/r/gamedesign/comments/1ktd844/what_are_tile_based_games_where_units_can_take_up/?utm_source=chatgpt.com)
- Tooling & Perf: profiling, batching, spatial partitioning.
