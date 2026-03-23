# Yacht Master: Docking Challenge
## 3 Progressive Prompts for Google AI Studio (Gemini Canvas)

---

## 📋 Overview

These three prompts are designed to be used sequentially in **Google AI Studio (Gemini Canvas)** to build a complete 3D yacht docking simulator. Each prompt builds upon the previous one, adding layers of complexity and interactivity.

**Stack:** JavaScript, Three.js, Cannon.js (physics), QR Code generation

**Key Features:**
- Luxury 3D yacht docking simulation with Monaco marina setting
- Autonomic computing (self-healing, self-configuration)
- Real-time physics and collision detection
- Dynamic UI with HUD panels and docking assistance
- QR code generation for prize system
- Leaderboard with localStorage persistence

---

## 🎯 Prompt 1: Scene Setup & 3D Environment

### Purpose
Establish the 3D scene foundation with Three.js, load yacht and dock assets, implement Golden Hour lighting, and create the water environment.

### JSON for Gemini Canvas

```json
{
  "system_prompt": "You are an expert 3D web developer specializing in Three.js and interactive web experiences. Your task is to generate a complete, production-ready HTML file that can be executed directly in a browser or Google AI Studio Canvas. The code must be self-contained, use CDN libraries, and include detailed comments.",
  "user_prompt": "Create a self-contained HTML file for the first phase of a luxury yacht docking simulator. Requirements:\n\n1. **Scene Setup:**\n   - Initialize Three.js scene with WebGL renderer\n   - Set canvas to full window size with proper aspect ratio handling\n   - Implement responsive resizing on window change\n\n2. **Lighting - Golden Hour Effect:**\n   - Add directional light (sun) at 50, 40, 30 position with warm orange color (#ffa500)\n   - Enable shadow mapping for realistic shadows\n   - Add ambient light (#ffd700) for overall illumination\n   - Create a sky gradient (orange to purple) using a sphere geometry\n\n3. **Water Environment:**\n   - Create a large plane geometry (200x200 units) for water\n   - Apply a procedural water texture using canvas (blue with wave patterns)\n   - Use MeshStandardMaterial for realistic water reflections\n   - Position at y=0 (sea level)\n\n4. **Dock Structure:**\n   - Main platform: 30x1x15 units, brown color (#8b7355)\n   - Add 5 wooden pilings (cylinders) at regular intervals\n   - Create a glowing docking zone marker (25x0.1x10) with green color and emissive material\n   - Position dock at z=15\n\n5. **Yacht Model (Simplified):**\n   - Hull: white box (4x2x12 units)\n   - Cabin: gray box (3x2x4 units) positioned on hull\n   - Mast: tall cylinder (0.1 radius, 15 height)\n   - Rudder: small box at stern for visual reference\n   - All meshes must cast and receive shadows\n   - Initial position: x=0, y=0, z=-30\n\n6. **Camera Setup:**\n   - Perspective camera at position (0, 15, 25)\n   - Looking at origin (0, 0, 0)\n   - FOV: 75 degrees\n   - Aspect ratio must update on resize\n\n7. **Code Structure:**\n   - Use ES6 modules and modern JavaScript\n   - Include all Three.js CDN links in <head>\n   - Add basic CSS for full-screen canvas\n   - Export functions for scene, camera, renderer for use in next phases\n\nOutput: A complete, working HTML file that displays a beautiful 3D marina scene with golden hour lighting. The scene should be visually stunning and ready for adding physics and interactivity in the next phase.",
  "output_format": "Complete HTML file with embedded JavaScript and CSS"
}
```

### Expected Output
A working 3D scene showing:
- Golden hour lighting with realistic shadows
- Blue water plane with wave texture
- Wooden dock structure with pilings
- White yacht positioned away from dock
- Responsive camera that updates on window resize

---

## 🎮 Prompt 2: Physics & Navigation System

### Purpose
Implement Cannon.js physics engine, yacht navigation mechanics (throttle, rudder, inertia), wind simulation, and collision detection with the dock.

### JSON for Gemini Canvas

```json
{
  "system_prompt": "You are an expert in 3D physics simulation and interactive game mechanics. Your task is to enhance an existing Three.js scene with Cannon.js physics, realistic naval mechanics, and collision detection. Maintain all visual assets from the previous phase while adding interactive gameplay.",
  "user_prompt": "Enhance the yacht docking simulator with physics and navigation. Build upon the existing Three.js scene (yacht, dock, water, lighting). Requirements:\n\n1. **Cannon.js Physics Setup:**\n   - Initialize Cannon.World with gravity set to (0, 0, 0) - no gravity in water\n   - Create rigid body for yacht (mass: 1000 kg, shape: box 2x1x6)\n   - Create static rigid body for dock (mass: 0, shape: box 15x0.5x7.5)\n   - Set default contact material friction to 0.3\n\n2. **Yacht Navigation Mechanics:**\n   - Implement throttle control (keyboard: arrow up/down or W/S)\n   - Throttle range: -0.5 (reverse) to 1.0 (full forward)\n   - Apply thrust force based on throttle and yacht heading\n   - Implement rudder control (keyboard: arrow left/right or A/D)\n   - Rudder angle range: -1.0 to 1.0 (port to starboard)\n   - Apply angular velocity based on rudder angle\n   - Add friction to throttle and rudder (natural deceleration)\n\n3. **Water Physics Simulation:**\n   - Simulate water resistance (velocity damping: 0.95 per frame)\n   - Implement dynamic wind force that changes over time\n   - Wind force: sin/cos based on timestamp, magnitude 5 units\n   - Wind affects yacht velocity in x and z directions\n   - Display wind direction and speed in UI\n\n4. **Collision Detection:**\n   - Listen for collision events between yacht and dock\n   - Trigger collision callback when yacht touches dock\n   - Prevent yacht from passing through dock\n   - Reset yacht position after collision (back to starting position)\n\n5. **Docking Accuracy Calculation:**\n   - Calculate distance from yacht to dock center (0, 0, 15)\n   - Accuracy formula: max(0, 100 - (distX + distZ) * 2)\n   - Check if docked: distZ < 2 AND distX < 3 AND speed < 2 knots\n   - Update accuracy in real-time as yacht approaches\n\n6. **Input Handling:**\n   - Keyboard event listeners for arrow keys and WASD\n   - Space bar to reset yacht position\n   - Store input state in keys object for smooth control\n\n7. **Game State Management:**\n   - Track yacht position, rotation, velocity\n   - Track throttle and rudder angles\n   - Calculate speed in knots (velocity magnitude * 1.944)\n   - Store docking accuracy percentage\n   - Track collision count and attempts\n\n8. **Animation Loop Integration:**\n   - Update physics world at 60 FPS (deltaTime: 1/60)\n   - Sync Three.js mesh positions with Cannon.js bodies\n   - Update camera to follow yacht smoothly\n   - Maintain all visual elements from Phase 1\n\nOutput: A fully playable yacht navigation system where users can control the yacht with keyboard, experience realistic water physics, and attempt to dock with precision. The yacht should respond naturally to controls with inertia and wind effects.",
  "output_format": "Complete HTML file with Three.js + Cannon.js integration"
}
```

### Expected Output
A playable simulator with:
- Smooth yacht control with throttle and rudder
- Realistic inertia and water resistance
- Dynamic wind affecting yacht movement
- Collision detection with dock
- Real-time accuracy calculation
- Camera following yacht smoothly

---

## 🎨 Prompt 3: UI, Self-Healing, QR Code & Leaderboard

### Purpose
Add the complete user interface with HUD panels, autonomic computing (self-healing visual effects), QR code generation for prizes, and localStorage-based leaderboard.

### JSON for Gemini Canvas

```json
{
  "system_prompt": "You are an expert in UI/UX design for interactive web applications and autonomic computing systems. Your task is to add a sophisticated, luxury-themed interface to an existing 3D simulator, including self-healing visual effects, real-time data visualization, QR code generation, and persistent leaderboard functionality.",
  "user_prompt": "Complete the yacht docking simulator with luxury UI, autonomic computing features, and prize system. Build upon the existing Three.js + Cannon.js simulator. Requirements:\n\n1. **HUD Panels (Heads-Up Display):**\n   - Top-left panel: Navigation Status\n     * Speed (in knots)\n     * Heading (in degrees)\n     * Water depth (constant 8.5m)\n     * Wind speed and direction\n   - Top-right panel: Docking Precision\n     * Accuracy percentage with progress bar\n     * Distance to dock (in meters)\n   - Bottom-center panel: Captain's Commands\n     * Random nautical phrases that update occasionally\n     * Examples: 'Steady as she goes', 'Watch the port side!', 'Reduce throttle'\n   - All panels: Dark background (rgba 10,25,41,0.85), gold borders, green text, glowing effect\n\n2. **Docking Assist System:**\n   - Show when yacht is within 10 meters of dock\n   - Three states with visual feedback:\n     * SUCCESS (>80% accuracy): Green border, 'OPTIMAL APPROACH'\n     * WARNING (50-80% accuracy): Orange border, 'ADJUST COURSE'\n     * DANGER (<50% accuracy): Red border, 'DANGER ZONE'\n   - Smooth transitions between states\n   - Glow effect with box-shadow\n\n3. **Self-Healing Visual Effect (Autonomic Computing):**\n   - When collision detected:\n     * Show '⚠️ COLLISION!' warning at screen center\n     * Generate 10 healing particles (✦ symbols) with animation\n     * Particles fade and scale up over 0.6 seconds\n     * Particles appear at random screen positions\n     * Yacht resets to starting position after 1 second\n   - No 'Game Over' - immediate recovery with visual feedback\n\n4. **Autonomic Self-Configuration:**\n   - Adjust rudder sensitivity based on player performance\n   - If accuracy > 80%: decrease sensitivity (min 0.5)\n   - If accuracy < 30%: increase sensitivity (max 1.5)\n   - Smooth adjustment: ±0.01 per frame\n   - Store sensitivity in gameState.autoSensitivity\n\n5. **Success Trigger & QR Code:**\n   - Trigger success when: docked (distZ < 2, distX < 3, speed < 2) AND accuracy > 95%\n   - Show '✓ DOCKED!' message at screen center with pulse animation\n   - Generate QR code using QRCode.js library\n   - QR code data: 'YACHT_MASTER_PRIZE_{score}_{timestamp}'\n   - Display in modal with:\n     * Title: '🎁 BRINDE DESBLOQUEADO!'\n     * QR code (200x200)\n     * Score and accuracy percentage\n     * Close button\n\n6. **Leaderboard System:**\n   - Store top 5 scores in localStorage key 'yachtLeaderboard'\n   - Each entry: {score, accuracy, timestamp}\n   - Sort by score descending\n   - Display in bottom-left panel:\n     * Title: '🏆 LEADERBOARD'\n     * Format: '1. 850 pts', '2. 720 pts', etc.\n     * Highlight top entry in gold color\n   - Update leaderboard after successful docking\n   - Persist across browser sessions\n\n7. **Controls Information Panel:**\n   - Bottom-right corner\n   - Display keyboard controls:\n     * ↑ Forward\n     * ↓ Reverse\n     * ← Port (Left)\n     * → Starboard (Right)\n     * SPACE: Reset\n\n8. **Styling & Aesthetics:**\n   - Luxury theme: dark navy background, gold accents, green text (hacker aesthetic)\n   - Font: Courier New for monospace (technical feel)\n   - All panels: semi-transparent with backdrop blur\n   - Text shadows for glow effect\n   - Smooth transitions and animations\n   - Responsive design for all screen sizes\n\n9. **Real-time UI Updates:**\n   - Update all HUD values every frame\n   - Smooth progress bar animation\n   - Dynamic captain commands (random every ~60 frames)\n   - Docking assist state changes based on accuracy\n\n10. **QR Code Integration:**\n    - Use CDN: https://cdn.jsdelivr.net/npm/qrcode@1.5.3/build/qrcode.min.js\n    - Generate QR code on successful docking\n    - Modal overlay with semi-transparent background\n    - Close button to dismiss modal\n\nOutput: A complete, polished yacht docking simulator with luxury UI, self-healing mechanics, and prize system. The experience should feel premium and engaging for a trade show stand.",
  "output_format": "Complete HTML file with all features integrated"
}
```

### Expected Output
A complete, production-ready simulator featuring:
- Luxury HUD panels with real-time data
- Docking assist with color-coded feedback
- Self-healing visual effects on collision
- QR code generation on successful docking
- Persistent leaderboard
- Smooth animations and transitions
- Professional, engaging user experience

---

## 🚀 Usage Instructions

### Step 1: Prepare Gemini Canvas
1. Go to [Google AI Studio](https://aistudio.google.com)
2. Create a new **Canvas** project
3. Select **Code** mode

### Step 2: Use Prompt 1
1. Copy the JSON from **Prompt 1**
2. Paste the `user_prompt` into Gemini Canvas
3. Wait for the complete HTML file
4. Test in browser - you should see the 3D marina scene

### Step 3: Use Prompt 2
1. Copy the output HTML from Prompt 1
2. In Gemini Canvas, paste: "Here is the current HTML from Phase 1: [paste HTML]. Now enhance it with physics and navigation following this specification: [paste Prompt 2 user_prompt]"
3. Gemini will enhance the code with Cannon.js physics
4. Test - you should be able to control the yacht

### Step 4: Use Prompt 3
1. Copy the output HTML from Prompt 2
2. In Gemini Canvas, paste: "Here is the current HTML from Phase 2: [paste HTML]. Now add the UI, self-healing effects, and QR code system following this specification: [paste Prompt 3 user_prompt]"
3. Gemini will add all UI and prize system features
4. Test - complete simulator ready for the stand!

---

## 🎯 Customization Tips

### Adjust Difficulty
- **Easier:** Increase docking zone size (change distZ < 2 to distZ < 5)
- **Harder:** Decrease accuracy threshold (change > 95 to > 98)
- **More Wind:** Increase wind magnitude in physics update

### Customize Branding
- Change yacht color: modify hullMaterial color
- Change dock color: modify platformMaterial color
- Change UI colors: modify CSS variables in style block
- Change captain commands: add phrases to gameState.captainCommands array

### Adjust Physics
- **Faster Yacht:** Increase moveForce (currently 50)
- **More Responsive Rudder:** Increase rotationForce (currently 0.1)
- **Stronger Wind:** Increase wind magnitude (currently 5)

### QR Code Customization
- Change QR data format in triggerSuccess()
- Modify QR code size: change width/height in QRCode constructor
- Add custom text before/after QR code

---

## 📊 Asset Structure for GitHub

If hosting 3D models on GitHub, use this structure:

```
yacht-master-docking/
├── models/
│   ├── yacht.glb          # Luxury yacht 3D model
│   ├── dock.glb           # Marina dock structure
│   └── README.md          # Model credits and licenses
├── textures/
│   ├── water.png          # Water texture
│   ├── wood.png           # Dock wood texture
│   └── sky.png            # Sky gradient
├── index.html             # Main simulator file
├── GEMINI_PROMPTS.md      # This file
└── README.md              # Project documentation
```

**CDN URLs for External Assets:**
```javascript
// Example: Loading GLB models from GitHub
const yachtUrl = 'https://raw.githubusercontent.com/[user]/yacht-master-docking/main/models/yacht.glb';
const dockUrl = 'https://raw.githubusercontent.com/[user]/yacht-master-docking/main/models/dock.glb';
```

---

## 🔧 Technical Stack

| Component | Library | Version | CDN |
|-----------|---------|---------|-----|
| 3D Graphics | Three.js | r128 | `https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js` |
| Physics | Cannon-es | 0.20.0 | `https://cdn.jsdelivr.net/npm/cannon-es@0.20.0/dist/cannon-es.js` |
| QR Code | QRCode.js | 1.5.3 | `https://cdn.jsdelivr.net/npm/qrcode@1.5.3/build/qrcode.min.js` |

---

## 💡 Autonomic Computing Features

### Self-Healing
- **Mechanism:** On collision, yacht resets to starting position with visual particle effects
- **Benefit:** No frustration - players can immediately retry
- **Implementation:** Healing particles animate for 0.6s, then yacht resets

### Self-Configuration
- **Mechanism:** Rudder sensitivity adjusts based on player accuracy
- **Benefit:** Game difficulty adapts to player skill
- **Implementation:** Sensitivity range 0.5-1.5, adjusts ±0.01 per frame based on accuracy

### Self-Optimization
- **Mechanism:** Wind force updates dynamically based on time
- **Benefit:** Unpredictable challenges keep experience fresh
- **Implementation:** Wind uses sin/cos of timestamp for smooth variation

---

## 🎪 Trade Show Stand Integration

### Display Setup
1. Run simulator on large touchscreen or projection
2. Place QR scanner at stand entrance
3. When player achieves >95% accuracy, QR code appears
4. Attendee scans with phone to receive prize notification

### Engagement Strategy
- **Leaderboard:** Display top 5 scores on big screen (refresh every 5 minutes)
- **Live Commentary:** Play captain commands audio through speakers
- **Difficulty Progression:** Increase wind strength as day progresses
- **Prize Tiers:** Different prizes for different accuracy levels

---

## 📝 Notes for Gemini

When using these prompts in Gemini Canvas:
- **Always request complete HTML files**, not code snippets
- **Specify CDN libraries** - no npm installations
- **Ask for comments** in the code for clarity
- **Request responsive design** - works on all screen sizes
- **Verify physics** - test collision detection and accuracy calculation
- **Test QR code** - ensure it generates valid codes

---

**Created by:** Manus AI  
**Date:** March 23, 2026  
**Version:** 1.0
