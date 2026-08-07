## Summary
This Jupyter notebook models long-distance jump dynamics using coupled 2D differential equations with coordinate-dependent drag coefficients. It simulates air resistance adjustments made through posture changes to find the minimum initial forward velocity required to clear a jump distance over 8 metres.

---

## README.md

### Overview
This project simulates human long-distance jumping mechanics using a system of coupled second-order ordinary differential equations (ODEs). The model incorporates position-dependent drag coefficients k_x(x) and k_z(z) defined via logistic functions to capture the physical effect of a jumper altering their posture mid-flight.

### Physics Model
The 2D trajectory is governed by the following coupled equations of motion:

$$\frac{d^{2}x}{dt^{2}} = -k_{x}(x)\,\frac{dx}{dt}\,\sqrt{\left(\frac{dx}{dt}\right)^{2}+\left(\frac{dz}{dt}\right)^{2}}$$

$$\frac{d^{2}z}{dt^{2}} = -g-k_{z}(z)\,\frac{dz}{dt}\,\sqrt{\left(\frac{dx}{dt}\right)^{2}+\left(\frac{dz}{dt}\right)^{2}}$$

where drag coefficients scale according to:

$$k_{c}(c)=\frac{A_{c}}{1+e^{-\mu_{c}\,(c-m_{c})}}+b_{c} \quad \text{for } c \in \{x, z\}$$

### Objectives
* Solve the IVP (Initial Value Problem) using `scipy.integrate.solve_ivp`.
* Determine the ground impact point using event-driven terminal conditions (z(t) = 0 while moving downwards).
* Perform a grid search over key initial parameters (v_x, v_z, m_z) to determine the minimum takeoff horizontal velocity (v_x) required to exceed an 8.0 m jump distance.
* Visualise both the spatial drag variation functions and the resulting optimal jump trajectory.

### Key Findings & Output
* **Minimum Takeoff Velocities**: v_x = 11.3 m/s, v_z = 6.0 m/s (m_z = 3.0 m)
* **Airborne Flight Duration**: 1.113 s
<img width="1200" height="500" alt="TrajectSpeed" src="https://github.com/user-attachments/assets/25c159cb-708e-4646-a5c5-bd581f8c170f" />


### Dependencies
* `python 3.x`
* `numpy`
* `scipy`
* `matplotlib`
* `IPython`

