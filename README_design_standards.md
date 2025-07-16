# CHUMBAKA Sibu Landing Page - Design System Documentation

## Color Scheme

### Primary Colors
- **CHUMBAKA Red**: `#DC143C` - Main brand color used for CTAs, accents, and emphasis
- **Dark Red**: `#B91C3C` - Hover states and darker accents
- **Light Red**: `#FF3860` - Gradients and lighter accents

### Neutral Colors
- **Black**: `#1a1a1a` - Primary text (not pure black for softer appearance)
- **Text Primary**: `#1a202c` - Main body text
- **Text Secondary**: `#4a5568` - Descriptions and secondary content
- **Grey**: `#6B7280` - Borders and muted elements
- **Light Grey**: `#F3F4F6` - Subtle backgrounds
- **Dark Grey**: `#374151` - Dark UI elements

### Background
- **White**: `#FFFFFF` - Clean background to complement white video
- **Transparent overlays**: Using `rgba()` for glassmorphism effects

## Design Principles

### 1. **Clean Minimalism**
- White video background with no dark overlays
- Generous whitespace for breathing room
- Focus on content hierarchy

### 2. **Modern Glassmorphism**
- Header: `background: rgba(255, 255, 255, 0.9)` with `backdrop-filter: blur(10px)`
- Contact Modal: `background: rgba(255, 255, 255, 0.95)` with `backdrop-filter: blur(20px)`
- Creates depth without heavy shadows

### 3. **Subtle Depth**
- Layered shadows instead of hard borders:
  ```css
  --shadow-sm: 0 2px 4px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.07);
  --shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1);
  --shadow-xl: 0 20px 25px rgba(0, 0, 0, 0.1);
  ```

### 4. **Professional Typography**
- **Headers**: 'Space Grotesk' - Modern, geometric sans-serif
- **Body**: 'Inter' - Highly readable, versatile sans-serif
- **Large logo**: 500px width for strong brand presence
- **Responsive sizing**: Using `clamp()` for fluid typography

## Animation System

### Sequential Loading Animation

1. **Logo** (0.5s delay)
   - `fadeInScale`: Scales from 0.8 to 1 with opacity fade
   - Duration: 1.5s with ease-out

2. **Tagline Words** (Staggered)
   - "Coding." - 1.0s delay
   - "Technology." - 1.3s delay  
   - "Soft Skills." - 1.6s delay
   - `fadeInWord`: Translates up 20px while fading in
   - Duration: 0.6s each with ease-out

3. **Description** (2.0s delay)
   - Simple opacity fade-in
   - Duration: 1.5s

4. **Buttons** (Staggered)
   - Button 1: 1.2s delay
   - Button 2: 1.4s delay
   - Button 3: 1.6s delay
   - Button 4: 1.8s delay
   - `fadeInButton`: Translates up 30px while fading in
   - Duration: 0.6s each with ease-out

5. **Header Bar** (2.5s delay)
   - Slides down with opacity fade
   - Duration: 0.8s

### Interactive Animations

- **Logo Float**: Continuous 6s animation, -20px vertical movement
- **Button Hover**: -3px translateY with enhanced shadow
- **Particle Effect**: 20 subtle red particles with 25s float duration
- **Mouse Parallax**: Particles respond to cursor movement

## Key Design Patterns

### Button Styles
- **Primary (Students)**: Gradient background with red tones
- **Secondary (Parents)**: White with red border, fills on hover
- **Tertiary (Staff)**: Dark gradient background
- **Quaternary (Contact)**: White with dark border

### Hover Effects
- All interactive elements have smooth transitions (0.3s cubic-bezier)
- Buttons lift on hover with shadow enhancement
- Contact info cards slide right with background color change

### Responsive Breakpoints
- **Desktop**: Full layout with 4-column button grid
  - Logo: 500px
  - Tagline: 4rem
  - 4-column grid: `repeat(auto-fit, minmax(240px, 1fr))`
- **Tablet (<768px)**: 
  - Logo: 300px
  - Tagline: 2.5rem  
  - 2-column grid with 500px max-width
  - Header navigation hidden
- **Mobile (<480px)**: 
  - Logo: 220px
  - Tagline: 1.5rem
  - Single column with 320px max-width
  - Reduced padding throughout

## Implementation Notes

### Layout System
1. **Container Widths**:
   - Content container: `max-width: 1400px`
   - Button grid: `max-width: 1100px`
   - Description text: `max-width: 800px`
   - Modal: `max-width: 600px`

2. **Z-Index Layers**:
   - Video background: `-1`
   - Particles: `0`
   - Main content: `1`
   - Header: `100`
   - Contact modal: `1000`
   - Loading screen: `9999`

3. **Spacing System**:
   - Logo margin bottom: `40px`
   - Tagline margin bottom: `30px`
   - Description margin bottom: `40px`
   - Button container margin top: `30px`
   - Button gap: `25px`

### Typography Details
- **Font Weights**: 300, 400, 500, 600, 700, 800, 900
- **Letter Spacing**: 
  - Tagline: `-1px` (tighter)
  - Buttons: `0.3px` (slightly loose)
- **Line Heights**:
  - Tagline: `1.1`
  - Description: `1.8`

### Interactive Features

1. **Button Ripple Effect**:
   ```css
   - Creates expanding circle on click
   - Color: rgba(255, 255, 255, 0.5)
   - Duration: 0.6s
   - Scales from 0 to 4x
   ```

2. **Modal Interactions**:
   - Click outside to close
   - ESC key to close
   - X button with 90° rotation on hover

3. **Video Handling**:
   - Autoplay with muted and loop
   - playsinline for mobile
   - Fallback loading timeout: 2s

4. **Special Effects**:
   - Logo hover: Scale 1.02 with glow shadow
   - Contact info cards: 10px translateX on hover
   - Particle parallax: Responds to mouse movement

### Mobile Optimizations
- `overflow-x: hidden` to prevent horizontal scroll
- `-webkit-fill-available` for proper viewport height
- Touch-optimized button sizes
- Simplified particle count on mobile

### Technical Details
1. **Video Background**: No overlay mask to maintain white appearance
2. **Loading Screen**: White background with red spinner
3. **Floating Particles**: 20 particles with subtle red tint
4. **Border Radius**: 
   - Buttons: `12px`
   - Modal: `24px`
   - Contact info cards: `16px`
5. **Animation Timing**: `cubic-bezier(0.4, 0, 0.2, 1)` for smooth ease-out
6. **Scroll Behavior**: Body overflow hidden during modal display

## Accessibility Considerations
- High contrast between text and background
- Large touch targets (min 65-70px height)
- Keyboard navigation support for modal
- Focus states for interactive elements
- Semantic HTML structure
