---
name: Boids Flocking Algorithm
tools: [C#, Unity, Compute Shader]
description: A tech demo to showcase how compute shaders can be used for parallel processing.
source_code: https://github.com/App24/Boids-Flocking
image: ../assets/projects/boids.png
weight: -1
pinned: true
year_from: 2024
build_url: https://github.com/App24/Boids-Flocking/releases
---

# 🐟Boids🐟

---

For a module, we have to create something that would use the GPU in some way, such as shaders or compute shaders. I ended up settling for simulate schools of fish with the Boids Flocking Algorithm.

As the previous knowledge I had with compute shaders was [Raymarching](/projects/raymarching), I knew some of the basics of compute shaders, but was not very comfortable or confident with how to pass data from the CPU to the GPU and vice-versa, so this was my first step in figuring out how to pass boid information the GPU and return a position to be rendered to the screen. I started of with creating a compute shader that would calculate an oscillating position for a cube and pass it to the CPU and assign it to a position of a cube in the scene. Next was writing the boids flocking algorithm in C# on the CPU so that I could easily debug it, and then after fixing any issues, I put it in a compute shader.

To represents the boids, I was using game objects that were present on the scene, this ended up meaning that the bottleneck for performance was these game objects. I switched to having all the rendering be on the GPU alone and not have any game object representation on the CPU side, this improved performance by a large amount.

Another improvement that allowed to simulate much more boids, was reducing the amount of data being sent from the CPU to the GPU and vice-versa, this was done through many ways. A primary one was that any data shared between boids, such as their minimum and maximum speed, avoidance radius, view range, etc., was stored in a separate buffer that then each boid reference the index of which their settings were stored at. This ended turning 40 bytes of data that is shared between boids into a singular 4 byte unsigned integer. Another piece of data that I was able to shorten was putting the boid group variable and the flags variable into a singular variable, by using bit operators to separate these in two during the calculation. I also did this for the colour of the boids, turning 3 floats for each colour channel into a singular 4 byte unsigned integer variable that uses 1 byte per colour, which does reduce the available colour range, but that was not a problem for my tech demo. From all my optimisations I was able to reduce the size of a boid in memory from 92 bytes, down to 76 bytes.