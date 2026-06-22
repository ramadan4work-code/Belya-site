# Belya - Marble Flicking Game

## 1. Project Overview

**Project Name:** Belya
**Project Type:** Mobile Touch Game
**Core Functionality:** A marble flicking game where players control their white cue ball to strike colored glass balls out of various chalk-drawn geometric figures. Features 15 progressive levels with different shapes and ball counts. Players must start throws from a designated throwing line below the figure.
**Target Users:** Casual gamers who enjoy skill-based touch games

## 2. Game Rules

### Starting Position
- **Throwing Line:** A dashed brown line placed approximately 6-7cm below the figure (scaled to ~220 pixels)
- **Cue Ball Start:** Player's white ball always starts on this throwing line, centered below the figure
- **Visual Indicator:** "THROW LINE" label marks the starting position

### Sound Control
- **Sound Toggle:** Located in top bar (🔊/🔇) and menu screen
- **Default State:** Sound enabled by default
- **Mute Function:** Disables all game audio (push, collide, score, win sounds)

### Scoring System
- **Base Score:** 1000 points for completing a level
- **Par:** Equal to the number of target balls in the level
- **Bonus Points:** +100 points for each shot saved (if shots ≤ par)
- **Formula:** Total Score = 1000 + (Par - Shots + 1) × 100 (if completed in par or under)
- **Star Rating:**
  - ⭐ 1 Star: Completed (any number of shots)
  - ⭐⭐ 2 Stars: Completed in par + 2 shots or fewer
  - ⭐⭐⭐ 3 Stars: Completed in par shots or fewer

### Shooting Mechanic
- Player drags from their white cue ball to aim
- Pull back direction determines shot direction (opposite)
- Power determined by drag distance
- Release to shoot

## 3. Level System

### Level Progression (15 Levels)

| Level | Shape | Balls | Difficulty |
|-------|-------|-------|------------|
| 1 | Triangle | 3 | Easy |
| 2 | Square | 4 | Easy |
| 3 | Diamond | 4 | Easy |
| 4 | Big Triangle | 6 | Medium |
| 5 | Pentagon | 5 | Medium |
| 6 | Hexagon | 6 | Medium |
| 7 | Big Square | 8 | Medium |
| 8 | Circle | 6 | Medium |
| 9 | Star | 6 | Medium |
| 10 | Big Hexagon | 9 | Hard |
| 11 | Cross | 8 | Hard |
| 12 | Octagon | 8 | Hard |
| 13 | Big Circle | 10 | Hard |
| 14 | Big Star | 10 | Hard |
| 15 | Decagon | 10 | Expert |

### Figure Types

1. **Triangle (△)** - 3-sided, triangular arrangement
2. **Square (□)** - 4-sided, classic box shape
3. **Diamond (◇)** - 4-sided rotated square, diamond orientation
4. **Pentagon (⬠)** - 5-sided, pentagonal arrangement
5. **Hexagon (⬡)** - 6-sided, honeycomb pattern
6. **Circle (○)** - 16-point circle boundary
7. **Star (☆)** - 10-pointed star with alternating radii
8. **Cross (✚)** - 12-point cross/plus shape
9. **Octagon** - 8-sided, octagonal boundary
10. **Decagon** - 10-sided, decagonal boundary

## 4. Visual & Rendering Specification

### Scene Setup
- **Camera:** 2D top-down orthographic view
- **Canvas Size:** Responsive, fills mobile viewport
- **Background:** Outdoor playground with solid ground texture (dirt/sand ground)

### Environment Design
- **Ground:** Solid flat surface with natural outdoor texture (brown dirt/sand)
- **Throwing Line:** Brown dashed line with "THROW LINE" label, ~150px below figure
- **Figure Drawing:** White chalk lines forming various geometric shapes
- **Corner Marks:** Small chalk dots at figure corners
- **Ambient Elements:** Subtle grass patches, small pebbles around edges

### Color Palette
- **Ground:** Sandy brown (#C4A574) with darker patches
- **Throwing Line:** Saddle brown (#8B4513) with dashed style
- **Chalk Lines:** Off-white (#F5F5F5)
- **Cue Ball:** White (#FFFFFF) with gray outline and soft glow
- **Target Marbles:** 8 vibrant glass-like colors:
  - Ruby Red (#E63946)
  - Sapphire Blue (#1D3557)
  - Emerald Green (#2D6A4F)
  - Amber Yellow (#F4A261)
  - Amethyst Purple (#7B2CBF)
  - Sunflower Yellow (#E9C46A)
  - Teal (#2A9D8F)
  - Orange (#F77F00)

### Visual Effects
- **Cue Ball:** White with soft white glow, pulsing border when ready
- **Target Marbles:** Radial gradients with glass-like highlights
- **Shadows:** Soft elliptical shadows under all balls
- **Aiming Line:** Dashed arrow with power indicator
- **Score Popup:** Floating "+1" text when marble exits figure

## 5. Game Mechanics Specification

### Ball Types
- **Cue Ball (Player's Ball):**
  - White color with subtle gray outline
  - Size: 22px diameter
  - Starts on throwing line below figure
  - Controlled by touch drag
  - Has glow effect when ready to shoot

- **Target Marbles:**
  - Colored glass marbles
  - Size: 20px diameter
  - Distributed within figure boundary
  - Must be knocked out by cue ball

### Flicking Mechanics
- **Input:** Touch/click on cue ball, drag to aim
- **Direction:** Opposite to drag (pull back to shoot forward)
- **Power:** Drag distance * 0.12, capped at 20
- **Visual Feedback:** Arrow with power dot

### Physics
- **Friction:** 0.988 per frame
- **Bounce:** 0.65 off boundaries
- **Ball Collision:** Momentum-based with sound

### Scoring
- 1 point per target marble knocked outside figure
- Progress tracked as "X / Total" in UI
- Level complete when all balls cleared

## 6. UI Elements

### Top Bar
- **Level Display:** Shows current level number
- **Score Display:** "X / Y" balls cleared vs total
- **Reset Button:** Restarts current level

### Menu Screen
- Game mode selection (Solo / VS Player)
- Level selector with figure icons
- Level preview showing shape and ball count
- Play button to start

### Win Overlay
- "Level Complete!" or "All Levels Complete!" text
- Score display (balls cleared / total)
- "Next Level" and "Menu" buttons

### Hint Text
- Bottom center, guides player on controls
- "Drag from your white ball to aim"
- Changes to "Wait for balls to stop..." during motion

## 7. Audio Feedback

- **Push:** Whoosh when cue ball is shot
- **Collision:** Clack when balls hit each other
- **Score:** Chime when marble exits figure
- **Win:** Victory melody
- **Level Up:** Ascending notes

## 8. Technical Implementation

- HTML5 Canvas for rendering
- Vanilla JavaScript game logic
- Touch + mouse input support
- Web Audio API for sounds
- Responsive design

## 9. Acceptance Criteria

- [x] White cue ball with subtle gray outline
- [x] Colored target marbles
- [x] Throwing line positioned ~6-7cm below figure
- [x] Cue ball starts on throwing line
- [x] 15 unique levels with different shapes and ball counts
- [x] Ground renders as solid outdoor surface
- [x] All figure shapes render correctly
- [x] Touch aiming from cue ball works
- [x] Physics simulation (friction, bouncing, collisions)
- [x] Shot-based scoring system (fewer shots = higher score)
- [x] Star rating system (1-3 stars based on efficiency)
- [x] Shot counter displayed during gameplay
- [x] Solo and VS modes
- [x] Sound toggle button (top bar and menu)
- [x] Audio feedback (respects mute setting)
- [x] Reset and menu navigation
- [x] Level preview in menu
- [x] Win screen with score, stars, and shot count