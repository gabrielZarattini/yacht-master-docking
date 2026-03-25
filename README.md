# ⚓ Yacht Master: OKEAN Enterprise

A professional luxury yacht docking simulator built with **Three.js** and **Cannon.js**, featuring the **GCRUX Naval Physics Engine v14.0**. Master the art of precision navigation with real-world hydrodynamics, wave response, and elite AI assistance.

---

## 🌊 GCRUX Naval Physics v14.0 (Global Enterprise)

The simulator has been upgraded from a basic arcade model to a **Real-World Hydrodynamics Engine**:

### 🚢 Real Naval Parameters (~50ft Motor Yacht)
- **Displacement:** 18,000 kg (Real mass inertia)
- **Hull Speed:** ~9.5 knots (Calculated via 1.34 × √LWL formula)
- **Max Speed:** 22 knots (Propulsion limited by drag curve)
- **Turning Circle:** 3.5x Vessel length (High-fidelity radius)
- **Fluid Density:** 1025 kg/m³ (Salt water physics)

### ⚙️ Hydrodynamic Features
- **Frictional Resistance:** Calculated via Cd curves and wetted area.
- **Wave-Making Resistance:** Exponential drag wall at Hull Speed (Froude Number).
- **Heave, Pitch & Roll:** Dynamic hull response to ocean waves using Gerstner wave superposition.
- **Centrifugal Healing:** Realistic vessel tilt during high-speed maneuvers.

### 🧩 Class-Based Architecture
- **YachtApp:** Main orchestration and rendering.
- **PhysicsEngine:** Standalone Cannon.js wrapper.
- **YachtController:** Decoupled input and boat logic.

---

## 🎯 Features

### Core Experience
- **3D Luxury Environment:** Monaco Port Hercule marina with premium golden hour lighting.
- **Unreal Bloom Post-Processing:** High-end light bleeding and glow effects for a visual "WOW" factor.
- **Glassmorphism UI:** Sophisticated HUD with backdrop blur and modern typography.
- **Synthetic Engine Sound:** Dynamic audio feedback using Web Audio API (oscillators).

### User Interface
- **Calibration HUD (Mapeamento 3D):** Integrated Gizmo (TransformControls) for real-time model positioning.
- **Elite AI Assistant:** GCRUX AI providing tactical feedback via Gemini.
- **Multi-Camera System:** 
    - **Chase:** Dynamic 3rd person following.
    - **Top-Down:** Orthogonal view for docking precision.
    - **Free:** OrbitControls for exploration.

---

## 🚀 Quick Start

### Local Preview
1. Download `client/public/simulator-gemini.html`
2. Open in any modern web browser.
3. Use keyboard controls to master the OKEAN yacht.

### Controls
| Key | Action |
|-----|--------|
| **W** | Diesel Throttle (Gradual acceleration) |
| **S** | Reverse Throttle (Limited power) |
| **A / D** | Hydraulic Rudder (High precision) |
| **SPACE** | Reset position |
| **🛠️ Mapeamento 3D** | Open Dev/Calibration tools |

---

## 🛠️ Technical Stack

| Component | Technology | Version |
|-----------|-----------|---------|
| 3D Graphics | Three.js | r128 |
| Physics | Cannon.js | 0.6.2 |
| Intelligence | Google Gemini | v2.5-flash |
| Sound | Web Audio API | Internal |
| UI | HTML5/CSS3 | Glassmorphism |

---

## 📂 Project Structure

```
yacht-master-docking/
├── client/
│   └── public/
│       └── simulator-gemini.html    # Elite Simulator v14.0 (Modular)
├── README.md                        # This file
└── *.glb                            # Raw 3D Assets (Yacht, Marina, Ocean)
```

---

## 📄 License
MIT License - Developed by **Antigravity (AI Architect)** for **Gabriel Zarattini**.

---

## 🌟 Acknowledgments
This project elevates the simulator to a professional grade tool, combining elite aesthetics with real-world naval engineering principles.

**Enjoy the challenge, Captain! ⚓**
