# Tooling Housing | Structural FEA & Design Optimization

**Software:** Abaqus/CAE, MATLAB  
**Focus:** Mechanical Design, Finite Element Analysis (FEA), Design Optimization

## Project Overview

This project focused on analyzing and improving a PETG housing used in a semi-automatic electromechanical tooling fixture. The housing supports the tooling and linear actuators while withstanding reaction forces during operation.

The goal was to reduce the housing's weight while maintaining structural strength, limiting deformation, and providing sufficient clearance for surrounding components.

![Tooling Housing Overview](Housing-Overview.png)

---

## Engineering Approach

### 1. Structural Analysis — Abaqus/CAE

I used Abaqus/CAE to simulate how the housing responds to forces during operation.

- Applied reaction loads and mounting constraints to represent operating conditions.
- Created a finite element mesh using 10-node quadratic tetrahedral elements (C3D10).
- Evaluated von Mises stress and displacement to assess structural performance.

**Applied Reaction Loads**

![Reaction Loads](Reaction-Loads.png)

**Finite Element Mesh**

![FEA Mesh](FEA-Mesh.png)

### 2. Design Evaluation

I compared three housing configurations to evaluate how changes in base thickness and hole depth affected weight, stress, and displacement.

#### Case 1 — Baseline Design

Original housing with a 20 mm base thickness and 37 mm hole depth.

| Von Mises Stress | Displacement |
|---|---|
| ![Baseline Stress](Von-Mises-Stress.png) | ![Baseline Displacement](Displacement.png) |

#### Case 2 — Reduced Base Thickness

Reduced the base thickness from 20 mm to 17 mm while maintaining the original hole depth.

This reduced the housing's mass by approximately **8.3%**, although maximum displacement increased.

| Von Mises Stress | Displacement |
|---|---|
| ![Case 2 Stress](Case-2-Von-Mises-Stress.png) | ![Case 2 Displacement](Case-2-Displacement.png) |

#### Case 3 — Increased Hole Depth

Increased the hole depth from 37 mm to 42.5 mm while maintaining the original 20 mm base thickness.

This provided the required clearance for surrounding components and served as the reference for the final optimization.

| Von Mises Stress | Displacement |
|---|---|
| ![Case 3 Stress](Case-3-Von-Mises-Stress.png) | ![Case 3 Displacement](Case-3-Displacement.png) |

### FEA Design Comparison

| Configuration | Max. Stress (MPa) | Max. Displacement (mm) | Mass (g) |
|---|---:|---:|---:|
| Case 1 — Baseline | 1.997 | 0.05079 | 1,050.76 |
| Case 2 — Reduced Base | 2.002 | 0.05973 | 963.60 |
| Case 3 — Increased Hole Depth | 1.819 | 0.05505 | 1,037.00 |

The results showed that reducing base thickness had the greatest effect on weight, while increasing hole depth was necessary for clearance.

Based on these findings, I selected base thickness as the main optimization variable and fixed the required hole depth at 42.5 mm.

### 3. Design Optimization — MATLAB

Using the Abaqus simulation results, I developed linear approximations to estimate how changes in base thickness affected mass, stress, and displacement.

I used MATLAB to minimize the housing's mass within the **17–20 mm thickness range** investigated in the design study. This range was selected to keep the optimization within the evaluated design space.

The optimization also considered the following requirements:

- **Maximum displacement:** 0.060 mm
- **Maximum von Mises stress:** 2.10 MPa
- **Required hole depth:** 42.5 mm

MATLAB predicted an optimized base thickness of approximately **18.34 mm**.

---

## Final Optimization Results

| Parameter | Result |
|---|---:|
| Original Housing Mass | 1,050.76 g |
| Optimized Housing Mass | 988.9 g |
| **Predicted Mass Reduction** | **5.9%** |
| Optimized Base Thickness | 18.34 mm |
| Maximum Predicted von Mises Stress | 1.82 MPa |
| Maximum Predicted Displacement | 0.060 mm |

The initial design study achieved an 8.3% mass reduction by reducing base thickness alone. The final MATLAB optimization incorporated the increased hole-depth requirement and predicted a **5.9% mass reduction** while satisfying the specified design constraints.

## Key Takeaways

This project involved balancing weight reduction with structural performance and component clearance.

By comparing different designs in Abaqus and using MATLAB for optimization, I identified a lighter housing configuration while accounting for the design constraints.

It provided practical experience using FEA results to guide mechanical design decisions.

---

## Full Project Presentation

The complete PowerPoint includes additional CAD views, boundary conditions, FEA results, design comparisons, and MATLAB optimization calculations.

**[View or Download the Full PowerPoint](Tooling%20Fixture%20FEA%20%26%20Design%20Optimization.pptx)**
