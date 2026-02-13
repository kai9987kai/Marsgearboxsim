# Mars Gearbox Sim — MarsGearboxSim

Educational **lumped-parameter** simulator for a **single spur-gear stage** operating in a **Mars-like environment** (low-pressure CO₂, weak convection, cold ambient, dust). The goal is a *plausible* “systems feel” (losses → heating, lubrication regime shifts, wear/backlash growth, mesh whine), **not** design-grade validation.

> This project is intentionally simplified. Use it for intuition, teaching, and parameter sweeps—not for certifying hardware.

---

## What it simulates

### Core physics blocks
- **Gear ratio** (pinion/gear tooth count)
- **Torsional compliance** (mesh stiffness + damping)
- **Backlash** (base backlash + growth with wear; temperature affects clearance)
- **Losses**
  - Load-dependent **bearing friction**
  - Pressure/density-dependent **windage**
  - **Churning** losses (oil fill factor dependent)
- **Tribology**
  - Lubricant **viscosity vs temperature**
  - **Stribeck-style** friction behavior (boundary → mixed → hydrodynamic transitions)
  - Dust-driven abrasion impact on friction/wear
- **Wear growth** (Archard-like behavior → backlash growth)
- **Thermal balance**
  - Heat in from losses
  - Heat out via **convection + radiation** (radiation can dominate at Mars pressures)
- **Audio (“mesh whine”)**
  - Gear whine behavior driven by torque ripple + stiffness modulation

### Not simulated (by design)
- Tooth micro-geometry & contact patch resolution
- Full EHL film thickness solver
- Elastodynamics / FEM tooth deflection fields
- Scuffing/pitting fatigue
- Housing conduction gradients / 3D temperature field
- 3D lubrication flow / CFD

---

## Run it

This repo	cb is intentionally minimal: it’s a **single file** app.

### Option A — open directly
1. Download/clone the repo
2. Open `Index.html` in your browser

### Option B — serve locally (recommended)
Some browsers apply stricter rules for local files. Serving avoids most issues:

```bash
git clone https://github.com/kai9987kai/Marsgearboxsim.git
cd Marsgearboxsim
python -m http.server 8000
