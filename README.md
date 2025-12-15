# Interactive Bézier Curve with Physics

## Overview
This project takes a cubic Bézier curve and makes it behave like a springy rope you can play with. When you move your mouse, the curve wiggles and snaps back with a bit of bounce, almost like it’s alive. Everything runs right in your browser using HTML5 Canvas and plain JavaScript—no shortcuts, just custom math for the Bézier curve, some vector magic, and a physics model that mimics springs and dampers.

---

## Mathematics (Bézier Curve)
This curve uses four control points: P₀ and P₃ are the fixed endpoints, while P₁ and P₂ move around as dynamic controls. The shape follows the usual cubic Bézier equation.  

B(t) = (1 − t)³P₀ + 3(1 − t)²tP₁ + 3(1 − t)t²P₂ + t³P₃,  where 0 ≤ t ≤ 1

To show the curve’s direction and how sharply it bends, you take the derivative of the Bézier equation to get the tangent vector. Then you normalize it before drawing.

---

## Physics Model
The middle control points move like they're attached to invisible springs and dampers. The spring yanks each point back toward its target spot, while the damper keeps things from wobbling too much. Every frame, the system figures out acceleration, then updates velocity and position using basic time integration. 

Acceleration is computed as:

a = −k(x − x_target) − d·v

Where:
- **k** = spring constant (stiffness)
- **d** = damping factor
- **v** = velocity


---

## Interaction Design
- The control points' target positions are altered by mouse movement.

- For greater deformation, click and drag increases the applied force.

- Sliders enable real-time adjustment of:

  - Stiffness of spring (k)

  - Damping coefficient (d)

This design clearly illustrates physical behaviour while offering intuitive control.

---

## Design Choices
- Clean math operations with a custom Vector2D class

- Fixed ends to mimic a rope that is anchored

- Canvas rendering for fluid animation and excellent performance

- Visual aids to enhance debugging and clarity (control polygon, tangents, FPS counter)

---

## Purpose
This project demonstrates:

-A mathematical comprehension of Bézier curves

-Simulation of physics in real time

-Math, physics, input handling, and rendering are all neatly separated.

It works well as an interactive user interface demo, simulation, or graphics.
