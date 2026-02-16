# Particle Filter Robotics Simulator  
*A Java-based interactive simulator for probabilistic robot localization*

---

## Overview

This project is an interactive **Particle Filter Robotics Simulator** implemented in Java. It visualizes Monte Carlo Localization (MCL) — one of the most important probabilistic algorithms used in robotics for state estimation under uncertainty.

The simulator allows you to:

- Control a robot inside a 2D environment  
- Visualize particle propagation in real time  
- Observe noisy sensor measurements  
- Watch particle weighting and resampling  
- Understand how localization converges  

This project is designed for students, robotics enthusiasts, and anyone interested in probabilistic robotics and Bayesian filtering.

---

# What This Simulator Demonstrates

The application implements a full probabilistic localization pipeline:

##  Motion Model
Robot controls are noisy. Each particle samples from a probabilistic motion distribution.

## Sensor Model
Simulated sensors (e.g., IR sensors) generate noisy distance readings to walls.

## Importance Weighting
Each particle is weighted based on how well its predicted measurements match the robot’s actual sensor readings.

## Resampling
Particles are resampled proportionally to their likelihood. Low-probability particles disappear, and high-probability particles are duplicated.

## Convergence
Over time, the particle cloud collapses around the robot’s true pose.

---

# Running the Application

## Option 1 — Run the Prebuilt `.jar`

### Step 1: Download

Download one of the following:

- `ParticleFilterJava14.jar` (recommended if using Java 14+)  
- `ParticleFilterJava8.jar` (fallback version)

 You **must** download the `resources` folder and place it in the **same directory** as the `.jar` file.

Your folder structure should look like:

```
ParticleFilterJava14.jar
resources/
```

---

## Mac Users

macOS blocks unsigned applications by default.

If the app is blocked:

1. Go to **System Settings → Privacy & Security**
2. Scroll to the bottom
3. Click **“Open Anyway”**

This warning is normal for `.jar` files from independent developers.

---

## Windows Users

If Windows asks how to open the file:

You may need to install Java.

Download the JDK **only from Oracle’s official website**:

https://www.oracle.com/java/technologies/javase-downloads.html

Be careful — many fake Java downloads exist online.

---

## Option 2 — Clone and Run from Source

If you want the latest version or want to modify the code:

```bash
git clone <repository_url>
```

Open the project in your preferred Java IDE:

- IntelliJ IDEA  
- Eclipse  
- VS Code (with Java extensions)

Run `Simulation.java` as the main entry point.

---

# Project Architecture

The simulator is modular and structured for clarity and extensibility.

## Core Simulation

- `Simulation.java` — Main simulation loop  
- `Robot.java` — Robot state and motion model  
- `Chassis.java` — Physical robot body  
- `Wheel.java` — Wheel motion modeling  
- `Map.java` — Environment representation  
- `ImageReader.java` — Map image loading  

## Sensors

- `Sensor.java` — Abstract sensor base class  
- `IRSensor.java` — Infrared distance sensor model  

## Probability & Filtering

- `Distribution.java` — Abstract probability distribution  
- `Gaussian.java` — Gaussian noise modeling  
- `Vector.java` — Linear algebra utilities  
- `ArrayIter.java` — Iteration helper class  
- `Util.java` — Math utilities  
- `GBC.java` — GUI layout helper  

These components implement:

- Gaussian noise sampling  
- Likelihood computation  
- Particle propagation  
- Weight normalization  
- Resampling  

---

# How to Use the Simulator

When the app launches:

- Use keyboard controls to move the robot  
- Observe particles spread and reweight  
- Adjust parameters via GUI controls  
- Watch convergence behavior  

You can experiment with:

- Number of particles  
- Sensor noise  
- Motion noise  
- Different map layouts  

---

# Educational Value

This simulator is ideal for understanding:

- Why EKF struggles with multimodal distributions  
- How Particle Filters handle global uncertainty  
- The kidnapped robot problem  
- Particle degeneracy  
- The impact of sensor noise  

It visually demonstrates:

- Bayesian filtering  
- Sequential Monte Carlo methods  
- State space estimation  
- Robotics localization theory  

---

# Known Issues

- Robots near tight corners may "teleport" due to wall collision handling.  
- Windows rendering may look slightly distorted (Swing limitation).  
- Changing textbox values may steal keyboard focus.  
  - Workaround: Toggle a checkbox to regain control.  

---

# Experiment Ideas

Try:

- Increasing motion noise dramatically — watch divergence  
- Reducing the number of particles — observe filter collapse  
- Starting with global uncertainty  
- Simulating a kidnapped robot scenario  
- Comparing behavior with and without resampling  

---

# Future Improvements

Potential extensions:

- Add SLAM capability  
- Implement systematic or low-variance resampling  
- Add lidar simulation  
- Add log-likelihood weighting  
- Add multi-robot localization  

---

# Theoretical Background

Particle Filters approximate the posterior:

```
p(x_t | z_1:t, u_1:t)
```

using weighted samples:

```
{ x_t[i], w_t[i] }
```

Algorithm:

1. Sample from motion model  
2. Compute measurement likelihood  
3. Normalize weights  
4. Resample  

This simulator visualizes each of these steps in real time.

---

# Reporting Bugs

If you encounter issues:

- Problems launching the `.jar`  
- Simulation bugs  
- GUI rendering issues  

Please report them! Contributions and suggestions are welcome.

---

# Author

Matej Popovski  
Robotics | Machine Learning | Probabilistic Systems
