# Tooling Housing | Structural FEA & Design Optimization

**Software:** Abaqus/CAE, MATLAB  
**Focus:** Mechanical Design, Finite Element Analysis (FEA), Design Optimization

## Project Overview

This project involved analyzing and improving a PETG housing used in a semi-automatic electromechanical tooling fixture. The housing supports the tooling and linear actuators while withstanding reaction forces during operation.

The goal was to reduce the housing's weight while maintaining structural strength, limiting deformation, and providing enough clearance for surrounding components.

![Tooling Housing Overview](Housing-Overview.png)

## Engineering Approach

### 1. Structural Analysis — Abaqus/CAE

I used Abaqus/CAE to simulate how the housing responds to forces applied during operation.

- Applied reaction loads and mounting constraints to represent operating conditions.
- Created a finite element mesh to evaluate the housing's structural behavior.
- Analyzed von Mises stress and displacement to identify how the housing responded to loading.

**Applied Reaction Loads**

![Reaction Loads](Reaction-Loads.png)

**Finite Element Mesh**

![FEA Mesh](FEA-Mesh.png)

### 2. Design Evaluation

I compared three housing configurations to understand how changes in geometry affected weight and structural performance.

| Design | Modification | Mass |
|---|---|---:|
| Baseline | 20 mm base, 37 mm hole depth | 1,050.76 g |
| Reduced Base | 17 mm base, 37 mm hole depth | 963.60 g |
| Increased Hole Depth | 20 mm base, 42.5 mm hole depth | 1,037.00 g |

Reducing the base thickness produced the largest weight reduction, approximately **8.3%**, but the housing also needed a deeper hole to avoid interference with surrounding components.

Based on these results, I selected base thickness as the main optimization variable and fixed the required hole depth at 42.5 mm.

### 3. Design Optimization — MATLAB

Using results from the Abaqus simulations, I developed linear approximations to estimate how changes in base thickness affected mass, stress, and displacement.

I used MATLAB to optimize the housing within the **17–20 mm thickness range** evaluated in the design study, while meeting the specified structural and clearance requirements.

The optimization predicted a base thickness of approximately **18.34 mm**.

## Final Results

| Parameter | Result |
|---|---:|
| Original Housing Mass | 1,050.76 g |
| Optimized Housing Mass | 988.9 g |
| **Predicted Mass Reduction** | **5.9% (61.99 g)** |
| Optimized Base Thickness | 18.34 mm |
| Maximum Predicted von Mises Stress | 1.82 MPa |
| Maximum Predicted Displacement | 0.060 mm |

The final MATLAB optimization accounted for the increased hole depth and predicted a **5.9% mass reduction** while satisfying the specified design constraints.

## Key Takeaways

The main challenge was reducing the housing's weight without allowing too much deformation or creating clearance issues.

By comparing different designs in Abaqus and using MATLAB for optimization, I was able to identify a lighter configuration that met the design requirements.

This project gave me hands-on experience using FEA and optimization to support mechanical design decisions.

## Full Project Presentation

The complete presentation includes the CAD geometry, boundary conditions, Abaqus stress and displacement contour plots, design comparisons, and MATLAB optimization calculations.

**[View or Download the Full PowerPoint](Tooling%20Fixture%20FEA%20%26%20Design%20Optimization.pptx)**
