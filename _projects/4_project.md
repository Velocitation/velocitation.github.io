---
layout: page
title: Falling Sand Simulation
description: An interactive particle simulation showcasing physics and user interaction
img: assets/img/fullsand.jpg
importance: 4
category: fun
giscus_comments: false
---

## Overview

This project implements an engaging sand particle simulation using Java and Swing for the graphical user interface. It demonstrates fundamental concepts in physics simulation, user interaction, and visual programming.

<div class="row align-items-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fallingsand.jpg" title="Sand simulation in action" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/sandsim.jpg" title="Particle stacking behavior" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: The simulation in action, showing particles falling. Right: Dynamic color variation of particles as they're added.
</div>

## Features

1. **Interactive Particle Creation**: Users can add sand particles to the simulation by clicking or dragging the mouse across the panel, providing an intuitive and engaging experience.

2. **Gravity Simulation**: The project implements a basic physics engine, simulating gravity to animate the sand particles. This results in realistic falling and stacking behaviors.

3. **Dynamic Color Variation**: As new particles are added to the simulation, their colors shift along the hue spectrum, creating a visually appealing and dynamic environment.

4. **Optimized Performance**: The simulation uses efficient data structures and algorithms to handle a large number of particles smoothly.

## Technical Details

The simulation is built on a grid system, where each cell can potentially contain a sand particle. The core of the simulation logic includes:

- **Particle Movement**: Particles attempt to move downwards due to simulated gravity. If the space below is occupied, they try to move diagonally down.
- **Velocity and Gravity**: Each particle has an associated velocity influenced by gravity, affecting its movement pattern.
- **Collision Detection**: The system checks for occupied cells to determine valid particle movements.

Here's a snippet of the core update logic with detailed comments:

```java
private void update() {
    // Initialize new grids for the next state
    int[][] nextGrid = new int[cols][rows];
    float[][] nextVelocityGrid = new float[cols][rows];

    // Iterate through each cell in the grid
    for (int i = 0; i < cols; i++) {
        for (int j = 0; j < rows; j++) {
            int state = grid[i][j];
            if (state > 0) {  // If the cell contains a particle
                float velocity = velocityGrid[i][j];
                boolean moved = false;

                // Check if the cell below is empty
                if (j < rows - 1 && grid[i][j + 1] == 0) {
                    // Move particle down
                    nextGrid[i][j + 1] = state;
                    nextVelocityGrid[i][j + 1] = velocity + gravity;
                    moved = true;
                } else {
                    // If can't move straight down, try diagonal movements
                    List<Integer> directions = Arrays.asList(1, -1);
                    Collections.shuffle(directions);  // Randomize direction
                    for (int dir : directions) {
                        int nextCol = i + dir;
                        // Check if diagonal move is possible
                        if (withinCols(nextCol) && j < rows - 1 && grid[nextCol][j + 1] == 0) {
                            // Move particle diagonally
                            nextGrid[nextCol][j + 1] = state;
                            nextVelocityGrid[nextCol][j + 1] = velocity + gravity;
                            moved = true;
                            break;
                        }
                    }
                }

                // If particle couldn't move, keep it in place
                if (!moved) {
                    nextGrid[i][j] = state;
                    nextVelocityGrid[i][j] = 0;  // Reset velocity for stationary particles
                }
            }
        }
    }

    // Update the main grids with the new state
    grid = nextGrid;
    velocityGrid = nextVelocityGrid;
}
```

This method is called repeatedly to update the state of each particle in the simulation, handling movement, velocity changes, and collisions. The use of separate grids for the next state ensures that all particles are updated based on the same initial conditions, preventing cascading updates within a single frame.

## Reflections and Future Improvements

Developing this sand simulation was an exciting journey into particle physics and interactive graphics programming. Some key learnings and potential future enhancements include:

1. **Performance Optimization**: While the current implementation performs well, there's room for optimization using spatial partitioning techniques like quadtrees to handle even more particles.

2. **Enhanced Physics**: Introducing more complex physics such as fluid dynamics could make the simulation more realistic and versatile.

3. **User Controls**: Adding UI elements to allow users to adjust gravity, particle size, or introduce obstacles could greatly enhance interactivity.

4. **Multi-threading**: Implementing multi-threaded updates could significantly boost performance on multi-core systems.

This project not only served as a fun coding exercise but also deepened my understanding of simulation techniques, real-time graphics, and user interaction in Java. It showcases my ability to combine theoretical concepts with practical implementation, resulting in an engaging and educational tool.

Feel free to check out the [full source code on GitHub](https://github.com/velocitation/SandSim) and try the simulation yourself!
