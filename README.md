# present.bells

A serene, browser-based game. Drift through the clouds, bounce between bells, and chase golden birds in this peaceful endless jumper.

![Game Type: HTML5 Canvas](https://img.shields.io/badge/type-HTML5%20Canvas-blue)
![No Dependencies](https://img.shields.io/badge/dependencies-none-green)
![Mobile Friendly](https://img.shields.io/badge/mobile-friendly-brightgreen)

## Overview

**present.bells** is a minimalist arcade game where you control a bunny bouncing upward through an infinite sky. The game features physics-based "cloud-like" movement, creating a floaty, dreamy experience.

## How to Play

### Controls
- **Mouse/Touch Movement**: Move horizontally (active after first jump)
- **Click/Tap**: Jump from the ground to begin

### Objective
- Bounce between white bells to gain height and score points
- Hit golden birds to multiply your score
- Don't fall below the camera view or it's game over
- Land safely on the ground to restart if you're still in the safety zone

### Scoring
- Each bell: **10 points × current multiplier**
- Each bird: **100 points × current multiplier** (and doubles your multiplier)
- Your high score is automatically saved to local storage

## Technical Details

### Architecture
- **Single-file implementation**: All game logic, rendering, and styles in one HTML file
- **Pure JavaScript**: No external libraries or frameworks
- **Canvas API**: Custom rendering for all game objects
- **Responsive**: Automatically scales to any screen size with device pixel ratio support

### Key Features
- Smooth camera following with lerp-based movement
- Physics-based bunny control with heavy damping for "cloud-like" feel
- Dynamic difficulty scaling (bells get smaller as score increases)
- Particle system for collision effects
- Parallax star field background
- Touch and mouse input support
- Local storage high score persistence
- Custom bell and bird rendering with glowing effects

### Configuration

Core gameplay values can be adjusted in the `CONFIG` object (index.html:203):

```javascript
const CONFIG = {
    gravity: 0.32,           // Vertical acceleration
    bunnyRadius: 16,         // Collision radius
    gameMaxWidth: 800,       // Max playfield width
    starCount: 100,          // Background stars
    bellSpawnGap: 110,       // Vertical spacing between bells
    birdSpawnChance: 0.003   // Probability of bird spawn
};
```

### Physics System

The game uses a custom physics engine optimized for floaty, responsive movement:
- **Gravity**: 0.32 units/frame² (very light)
- **Horizontal Control**: Smoothed mouse tracking with 0.05 lerp factor
- **Air Resistance**: 0.93 velocity multiplier per frame
- **Collision Detection**: Circle-to-circle distance checks
- **Camera**: Smooth following with 0.08 catchup rate

### World Coordinates
- Y=0 is the ground level
- Y increases upward
- X=0 is centered, with bounds based on screen/max width
- Camera follows the bunny with a vertical offset

## Installation

No installation required! Just open `index.html` in any modern web browser.

### Requirements
- Modern web browser with HTML5 Canvas support
- JavaScript enabled
- Recommended: Chrome, Firefox, Safari, or Edge (latest versions)

### Mobile Support
Fully optimized for mobile devices with:
- Touch event handling
- Viewport meta tags for proper scaling
- Touch-action CSS to prevent unwanted gestures
- Responsive font sizing

## Development

### File Structure
```
present.bells/
└── index.html    # Complete game (HTML, CSS, JS)
```

### Customization

**Change Colors:**
- Background gradient: index.html:626-627
- Bunny/bells: index.html:745 and index.html:690
- Birds: index.html:713
- Ground: index.html:647

**Modify Physics:**
- Adjust values in `CONFIG` object
- Tweak input smoothing: index.html:459
- Change acceleration: index.html:472
- Modify drag coefficient: index.html:477

**Alter Difficulty:**
- Bell size scaling: index.html:332-333
- Spawn rate: index.html:208
- Bird frequency: index.html:209

## Browser Compatibility

Tested and working on:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile Safari (iOS 13+)
- Chrome Mobile (Android 8+)

## Credits

Uses the Quicksand font family from Google Fonts.

## License

This project is provided as-is for educational and entertainment purposes.
