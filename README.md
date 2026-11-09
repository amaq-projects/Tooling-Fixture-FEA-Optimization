# Tooling-Fixture-FEA-Optimization
# Tooling Housing | Structural FEA & Design Optimization

**Software:** Abaqus/CAE, MATLAB  
**Focus:** Mechanical Design, Finite Element Analysis (FEA), Structural Optimization

## Project Overview

This project involved analyzing and optimizing a PETG housing used in a semi-automatic electromechanical tooling fixture. The housing supports the tooling and linear actuators, which generate reaction forces during operation.

The main objective was to reduce the housing's weight while keeping stress and displacement within acceptable limits and maintaining enough clearance for the surrounding components.

### Tooling Housing Overview

The housing includes mounting interfaces for the tooling and linear actuators.

![Tooling Housing Overview](Housing-Overview.png)

---

## Engineering Approach

### 1. Structural Analysis — Abaqus/CAE

I used Abaqus/CAE to evaluate the housing's structural behavior under the expected reaction loads.

- Created a 3D finite element model using 10-node quadratic tetrahedral elements (C3D10).
- Applied boundary conditions at the mounting interfaces and distributed loads at the actuator connection points.
- Analyzed von Mises stress and displacement to evaluate the housing's response to loading.

**Applied Reaction Loads**

The reaction loads were applied at the actuator mounting interfaces to represent the forces acting on the housing during operation.

![Reaction Loads](Reaction-Loads.png)

**Finite Element Mesh**

The housing was meshed using quadratic tetrahedral elements (C3D10) with a global seed size of 5.5 mm.

![Finite Element Mesh](FEA-Mesh.png)

---

### 2. Design Evaluation — Abaqus/CAE

I compared three housing configurations to evaluate how changes in geometry affected mass, stress, and displacement.

The two main dimensions investigated were:

- **Base thickness:** Reduced to lower material usage and overall weight.
- **Hole depth:** Increased from 37 mm to 42.5 mm to provide the required clearance for surrounding components.

#### Case 1 — Baseline Design

The original housing had a base thickness of 20 mm and a hole depth of 37 mm.

**Von Mises Stress — Baseline**

![Baseline Von Mises Stress](Von-Mises-Stress.png)

**Displacement — Baseline**

![Baseline Displacement](Displacement.png)

#### Case 2 — Reduced Base Thickness

The base thickness was reduced from 20 mm to 17 mm while maintaining the original 37 mm hole depth.

This configuration reduced component mass by approximately **8.3%**, with increased displacement compared to the baseline.

**Von Mises Stress — Case 2**

![Case 2 Von Mises Stress](Case-2-Von-Mises-Stress.png)

**Displacement — Case 2**

![Case 2 Displacement](Case-2-Displacement.png)

#### Case 3 — Increased Hole Depth

The hole depth was increased from 37 mm to 42.5 mm while maintaining the original 20 mm base thickness.

This modification addressed the required component clearance and provided a reference configuration for the final optimization.

**Von Mises Stress — Case 3**

![Case 3 Von Mises Stress](Case-3-Von-Mises-Stress.png)

**Displacement — Case 3**

![Case 3 Displacement](Case-3-Displacement.png)

### FEA Design Comparison

| Configuration | Max. Stress (MPa) | Max. Displacement (mm) | Mass (g) |
|---|---:|---:|---:|
| Case 1 — Baseline | 1.997 | 0.05079 | 1,050.76 |
| Case 2 — Reduced Base | 2.002 | 0.05973 | 963.60 |
| Case 3 — Increased Hole Depth | 1.819 | 0.05505 | 1,037.00 |

The comparisons showed that reducing the base thickness had the greatest effect on material usage. I therefore selected base thickness as the main optimization variable while keeping the revised hole depth fixed at 42.5 mm.

---

### 3. Design Optimization — MATLAB

Using the Abaqus simulation results, I developed linear approximations relating base thickness to component mass, stress, and displacement.

I then used MATLAB to minimize housing mass while satisfying the following constraints:

- **Maximum displacement:** 0.060 mm
- **Maximum von Mises stress:** 2.10 MPa
- **Allowable base thickness:** 17–20 mm
- **Required hole depth:** 42.5 mm

The optimization produced a predicted base thickness of approximately **18.34 mm**.

---

## Final Optimization Results

| Parameter | Result |
|---|---:|
| Original Housing Mass | 1,050.76 g |
| Optimized Housing Mass | 988.9 g |
| **Final Predicted Mass Reduction** | **5.9%** |
| Optimized Base Thickness | 18.34 mm |
| Required Hole Depth | 42.5 mm |
| Maximum Predicted von Mises Stress | 1.82 MPa |
| Maximum Predicted Displacement | 0.060 mm |

The initial design study achieved an **8.3% mass reduction** by reducing the base thickness to 17 mm. However, that configuration did not include the increased hole depth needed for clearance.

The final MATLAB optimization accounted for this requirement and predicted a **5.9% reduction in mass** while satisfying the specified stress, displacement, and geometric constraints.

These final values were obtained using linear approximations developed from the Abaqus simulation results.

---

## Key Takeaways

The biggest challenge was reducing the housing's weight without exceeding the displacement limit or creating clearance issues.

Comparing different geometries in Abaqus helped identify which dimensions had the greatest effect on structural performance. MATLAB then provided a way to estimate an optimized design based on those results.

This project gave me practical experience using FEA to support mechanical design decisions and evaluating tradeoffs between weight, stiffness, and component geometry.

---

## Full Project Presentation

The complete PowerPoint presentation includes:

- Housing geometry and design requirements
- Applied loads and boundary conditions
- Abaqus finite element mesh
- Von Mises stress and displacement contour plots
- Design comparisons and optimization formulation
- MATLAB optimization results

**[View or Download the Full PowerPoint Presentation](Tooling%20Fixture%20FEA%20%26%20Design%20Optimization.pptx)**
