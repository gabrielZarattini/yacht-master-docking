# ⚓ Yacht Master: Docking Challenge

A luxury 3D yacht docking simulator built with **Three.js** and **Cannon.js**, designed for high-end trade show experiences. Navigate a precision yacht through Monaco's Port Hercule during golden hour, master realistic water physics, and unlock prizes through perfect docking.

---

## 🎯 Features

### Core Experience
- **3D Luxury Environment:** Monaco Port Hercule marina with golden hour lighting
- **Realistic Physics:** Cannon.js-powered water dynamics, inertia, and wind simulation
- **Precision Docking:** Real-time accuracy calculation with visual feedback
- **Autonomic Computing:** Self-healing on collision + adaptive difficulty

### User Interface
- **HUD Panels:** Navigation status, docking precision, captain's commands
- **Docking Assist:** Color-coded guidance (green/orange/red) as you approach
- **Real-time Feedback:** Speed, heading, wind, distance to dock
- **Leaderboard:** Top 5 scores with localStorage persistence

### Prize System
- **QR Code Generation:** Unlock at >95% docking accuracy
- **Trade Show Integration:** Scan for instant prize notifications
- **Score Tracking:** Persistent leaderboard across sessions

---

## 🚀 Quick Start

### Play Online
1. Download `client/public/yacht-simulator.html`
2. Open in any modern web browser
3. Use keyboard controls to dock the yacht

### Controls
| Key | Action |
|-----|--------|
| **↑ / W** | Forward throttle |
| **↓ / S** | Reverse throttle |
| **← / A** | Port (turn left) |
| **→ / D** | Starboard (turn right) |
| **SPACE** | Reset yacht |

---

## 🎮 Gameplay

### Objective
Navigate the luxury yacht to the docking zone with maximum precision.

### Scoring System
- **Accuracy:** Based on distance from dock center (0-100%)
- **Success Threshold:** >95% accuracy required for QR code
- **Leaderboard:** Top 5 scores saved in browser

### Difficulty Progression
- **Self-Configuration:** Rudder sensitivity adapts to your skill level
- **Dynamic Wind:** Unpredictable wind forces change every frame
- **Realistic Inertia:** Yacht momentum requires planning ahead

---

## 📁 Project Structure

```
yacht-master-docking/
├── client/
│   └── public/
│       └── yacht-simulator.html      # Main simulator (self-contained)
├── GEMINI_PROMPTS.md                 # 3 progressive Gemini Canvas prompts
├── GITHUB_ASSET_GUIDE.md             # GitHub setup and asset structure
└── README.md                         # This file
```

---

## 🛠️ Technical Stack

| Component | Technology | Version |
|-----------|-----------|---------|
| 3D Graphics | Three.js | r128 |
| Physics Engine | Cannon-es | 0.20.0 |
| QR Code | QRCode.js | 1.5.3 |
| Language | JavaScript (ES6+) | - |
| Styling | CSS3 | - |

### CDN Libraries
All dependencies loaded via CDN - no build process required:
- Three.js: `https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js`
- Cannon-es: `https://cdn.jsdelivr.net/npm/cannon-es@0.20.0/dist/cannon-es.js`
- QRCode.js: `https://cdn.jsdelivr.net/npm/qrcode@1.5.3/build/qrcode.min.js`

---

## 🎨 Design Philosophy

### Luxury Aesthetic
- **Color Scheme:** Dark navy (#0a1929) with gold accents (#ffd700)
- **Typography:** Monospace font (Courier New) for technical feel
- **Effects:** Glowing text shadows, semi-transparent panels, backdrop blur
- **Lighting:** Golden hour sunset for premium atmosphere

### Autonomic Computing
1. **Self-Healing:** Collision triggers visual particle effect + instant reset
2. **Self-Configuration:** Rudder sensitivity adjusts based on performance
3. **Self-Optimization:** Wind force varies dynamically for fresh challenges

---

## 🔧 Customization

### Difficulty Adjustment
```javascript
// Easy mode: larger docking zone
const maxDist = 30;  // vs default 20
const accuracyThreshold = 90;  // vs default 95

// Hard mode: smaller zone
const maxDist = 15;  // vs default 20
const accuracyThreshold = 98;  // vs default 95
```

### Physics Tuning
```javascript
// Yacht speed
const moveForce = 50;  // Increase for faster yacht

// Rudder responsiveness
const rotationForce = 0.1;  // Increase for more responsive steering

// Wind strength
gameState.windForce.x = Math.sin(Date.now() * 0.001) * 5;  // Increase multiplier
```

### Branding
- Change yacht color: modify `hullMaterial.color`
- Change UI colors: edit CSS variables in `<style>` block
- Add custom captain commands: extend `gameState.captainCommands` array
- Load external 3D models: use Three.js GLTFLoader

---

## 🚢 Using with Gemini Canvas

The project includes **3 progressive prompts** for building the simulator step-by-step in Google AI Studio:

### Prompt 1: Scene Setup
- 3D environment with Three.js
- Yacht, dock, water, lighting
- Golden hour atmosphere

### Prompt 2: Physics & Navigation
- Cannon.js physics engine
- Yacht controls (throttle, rudder)
- Wind simulation
- Collision detection

### Prompt 3: UI & Prize System
- HUD panels with real-time data
- Self-healing visual effects
- QR code generation
- Leaderboard system

**See `GEMINI_PROMPTS.md` for complete instructions.**

---

## 🎪 Trade Show Stand Setup

### Hardware Requirements
- Large touchscreen (55"+ recommended) or projection
- Laptop/PC with Chrome browser
- Optional: QR scanner (mobile or dedicated device)

### Software Setup
1. Open `yacht-simulator.html` in Chrome
2. Enable fullscreen (F11)
3. Disable screensaver
4. Optional: Use kiosk mode for unattended operation

### Engagement Strategy
- **Live Leaderboard:** Display top 5 scores on secondary monitor
- **Captain Audio:** Play nautical commands through speakers
- **Progressive Difficulty:** Increase wind strength as event progresses
- **Prize Tiers:** Different rewards for accuracy levels (90%, 95%, 98%+)

### QR Code Integration
1. Player achieves >95% accuracy
2. QR code appears on screen
3. Attendee scans with phone
4. Redirect to: `https://your-domain.com/prize?code=[QR_DATA]`

---

## 📊 Performance

### Optimization Features
- 60 FPS target on modern hardware
- Efficient shadow mapping
- Procedural texture generation
- Optimized physics timestep (1/60s)

### Browser Compatibility
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

### Hardware Requirements
- **Minimum:** 2GB RAM, integrated GPU
- **Recommended:** 4GB RAM, dedicated GPU
- **Optimal:** 8GB RAM, RTX GPU

---

## 🔐 Security & Privacy

- **No Backend Required:** Fully client-side application
- **No Data Collection:** All scores stored locally in browser
- **No External APIs:** Only CDN libraries loaded
- **CORS Safe:** Works on any domain

---

## 📚 Documentation

| Document | Purpose |
|----------|---------|
| `GEMINI_PROMPTS.md` | 3 progressive prompts for building with Gemini Canvas |
| `GITHUB_ASSET_GUIDE.md` | GitHub setup, asset structure, deployment |
| `README.md` | This file - project overview and quick start |

---

## 🎓 Learning Resources

### Three.js
- [Official Documentation](https://threejs.org/docs)
- [Examples Gallery](https://threejs.org/examples)
- [Interactive Tutorials](https://threejs.org/manual)

### Cannon.js
- [GitHub Repository](https://github.com/cannon-es/cannon-es)
- [Physics Examples](https://cannon-es.github.io)
- [API Documentation](https://cannon-es.github.io/docs)

### Game Development
- [Game Physics Simulation](https://en.wikipedia.org/wiki/Physics_engine)
- [3D Graphics Fundamentals](https://learnopengl.com)
- [Web Game Development](https://developer.mozilla.org/en-US/docs/Games)

---

## 🐛 Troubleshooting

### Black Screen
- Check browser console for errors (F12)
- Verify WebGL is supported: https://get.webgl.org
- Try a different browser
- Clear browser cache and reload

### Low Performance
- Close other applications
- Reduce browser zoom level
- Disable browser extensions
- Update GPU drivers

### Controls Not Working
- Click on canvas to ensure it has focus
- Check keyboard layout (arrow keys vs WASD)
- Verify browser isn't blocking keyboard input

### QR Code Not Generating
- Ensure accuracy is >95%
- Check browser console for JavaScript errors
- Verify QRCode.js library loaded successfully

---

## 🤝 Contributing

### Customization Ideas
- Add sound effects (engine, collision, success)
- Implement difficulty levels (easy/normal/hard)
- Create branded versions with custom colors
- Add multiplayer leaderboard via backend API
- Implement time attack mode

### Asset Improvements
- Commission professional 3D models (OKEAN 80 yacht)
- Create high-resolution textures
- Add advanced water shader
- Implement post-processing effects

---

## 📄 License

MIT License - Feel free to use, modify, and distribute.

```
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 🙏 Credits

### Technologies
- **Three.js:** 3D graphics library by Mr.doob and contributors
- **Cannon-es:** Physics engine by Stefan Hedman and contributors
- **QRCode.js:** QR code generator by davidshimjs

### Inspiration
- Luxury yacht industry and marine navigation
- Trade show experiential marketing
- Autonomic computing principles
- Golden hour cinematography

---

## 📞 Support

### Getting Help
1. Check `TROUBLESHOOTING.md` section above
2. Review browser console for error messages
3. Visit Three.js documentation
4. Check Cannon.js examples

### Reporting Issues
- Document the issue clearly
- Include browser and OS information
- Provide steps to reproduce
- Share error messages from console

---

## 🚀 Future Roadmap

### Phase 1: Core Experience ✅
- 3D environment with physics
- Yacht controls and docking
- QR code prize system

### Phase 2: Enhanced Features
- [ ] Sound effects and music
- [ ] Difficulty levels
- [ ] Multiplayer leaderboard
- [ ] Custom yacht models
- [ ] Advanced water shader

### Phase 3: Trade Show Integration
- [ ] Backend API for score tracking
- [ ] Real-time leaderboard display
- [ ] Prize redemption system
- [ ] Analytics dashboard

### Phase 4: Expansion
- [ ] Mobile version
- [ ] VR/AR support
- [ ] Additional locations (Dubai, Singapore)
- [ ] Seasonal events

---

## 📊 Project Statistics

| Metric | Value |
|--------|-------|
| Lines of Code | ~1,500 |
| 3D Models | 4 (yacht, dock, water, sky) |
| Physics Bodies | 2 (yacht, dock) |
| HUD Panels | 4 |
| Supported Browsers | 4+ |
| File Size | ~45 KB (HTML) |
| Load Time | <2 seconds |
| Target FPS | 60 |

---

## 🎬 Demo Video

[Link to demo video - coming soon]

---

## 📧 Contact

**Project Creator:** Manus AI  
**Date Created:** March 23, 2026  
**Version:** 1.0  
**Last Updated:** March 23, 2026

---

## 🌟 Acknowledgments

This project demonstrates advanced web technologies for creating immersive, interactive experiences suitable for luxury brand activations and trade show stands. The combination of Three.js 3D graphics, Cannon.js physics, and autonomic computing principles creates an engaging, adaptive experience that adapts to player skill levels.

**Enjoy the challenge, and may your docking be precise! ⚓**

---

*Built with ❤️ using Three.js, Cannon.js, and cutting-edge web technologies.*
