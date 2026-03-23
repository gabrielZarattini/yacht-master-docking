# Yacht Master: Docking Challenge
## GitHub Asset Structure & Setup Guide

---

## 📦 Project Overview

The **Yacht Master: Docking Challenge** is a luxury 3D yacht docking simulator designed for trade show stands. The complete application is self-contained in a single HTML file that can be deployed anywhere, but 3D models and textures can be hosted on GitHub for easy version control and updates.

---

## 🗂️ Recommended GitHub Repository Structure

```
yacht-master-docking/
│
├── README.md                          # Main project documentation
├── GEMINI_PROMPTS.md                  # 3 progressive prompts for Gemini Canvas
├── GITHUB_ASSET_GUIDE.md              # This file
│
├── index.html                         # Main simulator (complete, self-contained)
│
├── models/                            # 3D Models (GLB format)
│   ├── yacht-luxury.glb              # OKEAN 80 or luxury yacht model
│   ├── dock-monaco.glb               # Monaco Port Hercule dock structure
│   ├── water-plane.glb               # Optional: high-poly water
│   └── README.md                     # Model credits and licenses
│
├── textures/                          # Texture maps (PNG/JPG)
│   ├── water-normal.png              # Water normal map for waves
│   ├── water-roughness.png           # Water roughness map
│   ├── wood-dock.png                 # Dock wood texture
│   ├── metal-mast.png                # Mast metal texture
│   ├── sky-gradient.png              # Sky background
│   └── README.md                     # Texture sources and licenses
│
├── sounds/                            # Optional: Audio assets
│   ├── engine-start.mp3              # Yacht engine sound
│   ├── collision.mp3                 # Collision sound effect
│   ├── success.mp3                   # Docking success sound
│   └── README.md                     # Audio credits
│
├── docs/                              # Documentation
│   ├── ARCHITECTURE.md               # Technical architecture
│   ├── CUSTOMIZATION.md              # How to customize the simulator
│   ├── DEPLOYMENT.md                 # Deployment instructions
│   └── TROUBLESHOOTING.md            # Common issues and solutions
│
├── examples/                          # Example configurations
│   ├── easy-mode.html                # Easier difficulty version
│   ├── hard-mode.html                # Harder difficulty version
│   └── branded-version.html          # Custom branded version
│
└── .gitignore                         # Git ignore rules
```

---

## 🚀 Step-by-Step GitHub Setup

### 1. Create Repository

```bash
# Create new repository on GitHub
# Name: yacht-master-docking
# Description: Luxury 3D yacht docking simulator for trade shows
# Visibility: Public (for easy sharing)
# Initialize with README.md

# Clone locally
git clone https://github.com/[your-username]/yacht-master-docking.git
cd yacht-master-docking
```

### 2. Add Main Files

```bash
# Copy the simulator HTML
cp /path/to/yacht-simulator.html index.html

# Copy documentation
cp /path/to/GEMINI_PROMPTS.md .
cp /path/to/GITHUB_ASSET_GUIDE.md .

# Create directory structure
mkdir -p models textures sounds docs examples
```

### 3. Add 3D Models

#### Option A: Use Free Models from Sketchfab

1. Visit [Sketchfab.com](https://sketchfab.com)
2. Search: "luxury yacht glb"
3. Filter: "Downloadable" + "GLB Format"
4. Download and place in `models/` directory

**Recommended Models:**
- **Yacht:** Search "luxury yacht" or "sailboat" (look for models with good lighting)
- **Dock:** Search "marina dock" or "port structure"
- **Water:** Search "ocean water" (for advanced water shader)

#### Option B: Create Simple Procedural Models

If you prefer not to use external models, the current simulator generates yacht and dock procedurally in Three.js. This is perfectly functional for trade shows.

#### Option C: Commission Custom Models

For a branded experience, commission a 3D artist to create:
- OKEAN 80 yacht model (specific luxury brand)
- Monaco Port Hercules accurate dock
- Custom marina environment

**Budget Estimate:** $500-2000 for professional models

### 4. Add Textures

Create or download textures:

```bash
# Water textures (from free sources)
# - Textures Haven: https://texturehaven.com/textures/?c=water
# - Poly Haven: https://polyhaven.com/textures?search=water

# Wood textures (for dock)
# - Poly Haven: https://polyhaven.com/textures?search=wood

# Save as PNG in textures/ directory
```

### 5. Create .gitignore

```bash
# Create .gitignore file
cat > .gitignore << 'EOF'
# OS files
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
*.swp
*.swo

# Build artifacts
dist/
build/
*.log

# Dependencies (if using npm)
node_modules/
package-lock.json

# Large files (if using Git LFS)
*.blend
*.max
*.fbx
*.obj
EOF

git add .gitignore
git commit -m "Add gitignore"
```

### 6. Create README.md

```markdown
# Yacht Master: Docking Challenge

A luxury 3D yacht docking simulator for trade shows and events.

## Features

- **3D Environment:** Monaco Port Hercule with golden hour lighting
- **Physics Simulation:** Realistic water physics and yacht navigation
- **Autonomic Computing:** Self-healing on collision, adaptive difficulty
- **Prize System:** QR code generation for trade show prizes
- **Leaderboard:** Real-time scoring with localStorage persistence

## Quick Start

1. Download `index.html`
2. Open in any modern web browser
3. Use arrow keys to control yacht
4. Dock with >95% accuracy to unlock QR code prize

## Controls

- **↑/W:** Forward throttle
- **↓/S:** Reverse throttle
- **←/A:** Port (turn left)
- **→/D:** Starboard (turn right)
- **SPACE:** Reset yacht

## Customization

See [CUSTOMIZATION.md](docs/CUSTOMIZATION.md) for:
- Difficulty adjustment
- Branding and colors
- Physics tuning
- Sound effects

## Deployment

See [DEPLOYMENT.md](docs/DEPLOYMENT.md) for:
- Web hosting options
- Stand setup
- QR code integration

## Technical Stack

- **Three.js:** 3D graphics
- **Cannon-es:** Physics engine
- **QRCode.js:** QR code generation

## License

MIT License - See LICENSE file

## Credits

- 3D Models: [Model sources]
- Textures: [Texture sources]
- Concept: Luxury yacht docking experience
```

### 7. Create Documentation Files

#### docs/ARCHITECTURE.md

```markdown
# Technical Architecture

## Core Components

### 1. Scene Management
- Three.js scene initialization
- Camera setup with follow behavior
- Lighting system (golden hour)
- Water plane with procedural texture

### 2. Physics Engine
- Cannon.js world setup
- Yacht rigid body (mass: 1000 kg)
- Dock static body (mass: 0)
- Collision detection and response

### 3. Input System
- Keyboard event listeners
- Throttle and rudder control
- Smooth input handling with decay

### 4. Game Logic
- Docking accuracy calculation
- Self-healing on collision
- Self-configuration of rudder sensitivity
- Success detection and QR code generation

### 5. UI System
- HUD panels with real-time data
- Docking assist visualization
- Leaderboard management
- QR code modal

## Data Flow

```
Input Events
    ↓
Game State Update
    ↓
Physics Simulation
    ↓
Accuracy Calculation
    ↓
UI Rendering
    ↓
Three.js Render
```

## Performance Optimization

- 60 FPS target
- Efficient mesh updates
- Shadow map optimization
- Texture compression
```

#### docs/CUSTOMIZATION.md

```markdown
# Customization Guide

## Difficulty Levels

### Easy Mode
```javascript
// In calculateDockingAccuracy()
const maxDist = 30;  // Larger zone
const accuracyThreshold = 90;  // Lower threshold
```

### Hard Mode
```javascript
// In calculateDockingAccuracy()
const maxDist = 15;  // Smaller zone
const accuracyThreshold = 98;  // Higher threshold
```

## Branding

### Colors
Edit CSS variables in `<style>` section:
```css
--primary-color: #ffd700;  /* Gold */
--accent-color: #00ff00;   /* Green */
--background-color: #0a1929;  /* Dark blue */
```

### Textures
Replace texture URLs in `createWater()` and `createDock()`:
```javascript
const texture = new THREE.TextureLoader().load('path/to/custom-texture.png');
```

### Models
Load external GLB models:
```javascript
const loader = new THREE.GLTFLoader();
loader.load('models/yacht.glb', (gltf) => {
    yachtMesh = gltf.scene;
    scene.add(yachtMesh);
});
```

## Physics Tuning

### Yacht Speed
```javascript
const moveForce = 50;  // Increase for faster yacht
```

### Rudder Sensitivity
```javascript
const rotationForce = 0.1;  // Increase for more responsive steering
```

### Wind Strength
```javascript
gameState.windForce.x = Math.sin(Date.now() * 0.001) * 5;  // Increase multiplier
```

## Sound Effects

Add audio playback:
```javascript
const engineSound = new Audio('sounds/engine-start.mp3');
engineSound.play();
```

## UI Customization

### Captain Commands
Edit array in gameState:
```javascript
gameState.captainCommands = [
    "Ready for docking maneuver...",
    "Steady as she goes, sir",
    // Add more phrases
];
```

### Leaderboard Display
Modify `displayLeaderboard()` function to show more entries or different format.
```

#### docs/DEPLOYMENT.md

```markdown
# Deployment Guide

## Web Hosting Options

### Option 1: GitHub Pages (Free)
1. Push to GitHub repository
2. Go to Settings → Pages
3. Select "Deploy from branch"
4. Choose main branch
5. Access at: `https://[username].github.io/yacht-master-docking/`

### Option 2: Netlify (Free)
1. Connect GitHub repository
2. Set build command: (none needed)
3. Set publish directory: `/`
4. Deploy

### Option 3: Vercel (Free)
1. Import GitHub repository
2. Deploy
3. Access at auto-generated URL

### Option 4: Custom Server
1. Upload `index.html` to web server
2. Configure CORS if needed
3. Access via your domain

## Trade Show Stand Setup

### Hardware
- Large touchscreen (55"+ recommended)
- Laptop/PC with Chrome browser
- QR scanner (mobile phone or dedicated scanner)

### Software
1. Open `index.html` in Chrome (fullscreen)
2. Set display to 1920x1080 or higher
3. Disable screensaver
4. Optional: Use kiosk mode

### QR Code Integration
1. When player achieves >95% accuracy
2. QR code appears on screen
3. Attendee scans with phone
4. Redirect to: `https://your-domain.com/prize?code=[QR_DATA]`

### Leaderboard Display
Option 1: Display on second monitor
```javascript
// Modify displayLeaderboard() to show on separate canvas
```

Option 2: Use external dashboard
```javascript
// Send scores to backend API
fetch('/api/scores', {
    method: 'POST',
    body: JSON.stringify(gameState)
});
```

## Performance Optimization

### For Older Hardware
- Reduce shadow map resolution
- Disable fog
- Simplify water texture
- Lower particle count

### For High-End Hardware
- Increase shadow map resolution
- Add more lighting effects
- Use advanced water shader
- Add post-processing effects
```

### 8. Commit and Push

```bash
# Add all files
git add .

# Commit
git commit -m "Initial commit: Yacht Master simulator with documentation"

# Push to GitHub
git push origin main
```

---

## 📥 Using External 3D Models

### Loading GLB Models from GitHub

```javascript
// In your HTML file
const loader = new THREE.GLTFLoader();

// Load yacht model
loader.load('https://raw.githubusercontent.com/[user]/yacht-master-docking/main/models/yacht.glb', 
    (gltf) => {
        const yacht = gltf.scene;
        yacht.scale.set(0.5, 0.5, 0.5);
        scene.add(yacht);
    }
);

// Load dock model
loader.load('https://raw.githubusercontent.com/[user]/yacht-master-docking/main/models/dock.glb',
    (gltf) => {
        const dock = gltf.scene;
        dock.position.z = 15;
        scene.add(dock);
    }
);
```

### Using jsDelivr CDN for GitHub Files

```javascript
// jsDelivr provides fast CDN delivery of GitHub files
const modelUrl = 'https://cdn.jsdelivr.net/gh/[user]/yacht-master-docking@main/models/yacht.glb';
```

---

## 🎨 Free Asset Resources

### 3D Models
- **Sketchfab:** https://sketchfab.com (free models with GLB export)
- **TurboSquid Free:** https://www.turbosquid.com/Search/3D-Models/free
- **CGTrader Free:** https://www.cgtrader.com/free-3d-models
- **Poly Haven:** https://polyhaven.com/models

### Textures
- **Poly Haven:** https://polyhaven.com/textures
- **Textures Haven:** https://texturehaven.com
- **Ambient CG:** https://ambientcg.com

### Sounds
- **Freesound:** https://freesound.org
- **Zapsplat:** https://www.zapsplat.com
- **BBC Sound Effects:** https://sound-effects.bbcrewind.co.uk

---

## 🔄 Version Control Best Practices

### Commit Messages

```bash
# Feature additions
git commit -m "feat: add wind simulation to physics engine"

# Bug fixes
git commit -m "fix: correct docking accuracy calculation"

# Documentation
git commit -m "docs: update customization guide"

# Asset updates
git commit -m "assets: add high-res yacht model"
```

### Branching Strategy

```bash
# Create feature branch
git checkout -b feature/new-feature

# Make changes and commit
git add .
git commit -m "feat: description"

# Push to GitHub
git push origin feature/new-feature

# Create Pull Request on GitHub
# After review, merge to main
```

---

## 📊 File Size Optimization

### Model Compression

```bash
# Using gltf-pipeline (npm install -g gltf-pipeline)
gltf-pipeline -i yacht.glb -o yacht-compressed.glb -d

# Using Draco compression
gltf-pipeline -i yacht.glb -o yacht-draco.glb --draco.compressionLevel=7
```

### Texture Optimization

```bash
# Using ImageMagick
convert texture.png -quality 85 -resize 2048x2048 texture-optimized.png

# Using TinyPNG API for batch compression
# https://tinypng.com/developers
```

---

## 🚀 Continuous Deployment

### GitHub Actions Workflow

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

---

## 📝 Troubleshooting

### Models Not Loading
- Check file paths are correct
- Verify GitHub URLs are accessible
- Check browser console for CORS errors
- Use jsDelivr CDN for faster loading

### Performance Issues
- Reduce model polygon count
- Compress textures
- Disable shadow maps on older hardware
- Use LOD (Level of Detail) models

### QR Code Not Generating
- Verify QRCode.js CDN is accessible
- Check QR data format is valid
- Ensure modal element exists in HTML

---

## 📞 Support & Resources

- **Three.js Documentation:** https://threejs.org/docs
- **Cannon.js Documentation:** https://cannon-es.github.io
- **GitHub Help:** https://docs.github.com
- **Sketchfab Support:** https://support.sketchfab.com

---

**Last Updated:** March 23, 2026  
**Version:** 1.0  
**Maintained by:** Manus AI
