# Magic UI Components

#project #magicui #component

## Installed Components

### 1. BlurFade
- **File**: `components/magicui/blur-fade.tsx` (60 lines)
- **Registry**: `blur-fade`
- **What it does**: Fade-in animation with optional blur effect, triggered on scroll via `useInView`
- **Props**: `children`, `variant`, `duration` (default 0.5), `delay`, `yOffset` (default 6), `inView`, `inViewMargin`, `blur` (default "6px")
- **Used on**: [[Page-Landing]] (all sections), [[Page-Pricing]], [[Page-About]], [[Page-Trust]], [[Page-Compare]], [[Page-Preview]]
- **Customizations**: Various delay values for staggered section reveals

### 2. AnimatedShinyText
- **File**: `components/magicui/animated-shiny-text.tsx` (42 lines)
- **Registry**: `animated-shiny-text`
- **What it does**: Text with a shimmer/shine animation sweeping across
- **Props**: `children`, `className`, `shimmerWidth` (default 100)
- **Used on**: [[Page-Landing]] (badge text)
- **Customizations**: None significant

### 3. NumberTicker
- **File**: `components/magicui/number-ticker.tsx` (68 lines)
- **Registry**: `number-ticker`
- **What it does**: Animated counting number with spring physics
- **Props**: `value`, `direction` ("up"/"down"), `delay`, `className`, `decimalPlaces`, `prefix`, `suffix`
- **Used on**: [[Page-Landing]] (stats section: 60+, 11, 20+, 38, <2 min), [[Page-Preview]]
- **Customizations**: Custom prefix/suffix for each stat

### 4. Marquee
- **File**: `components/magicui/marquee.tsx` (54 lines)
- **Registry**: `marquee`
- **What it does**: Continuous scrolling content (horizontal or vertical)
- **Props**: `className`, `reverse`, `pauseOnHover`, `children`, `vertical`, `repeat` (default 4)
- **Used on**: [[Page-Landing]] (trust strip with firm type badges)
- **Customizations**: `pauseOnHover` enabled, 4x repeat

### 5. ShimmerButton
- **File**: `components/magicui/shimmer-button.tsx` (93 lines)
- **Registry**: `shimmer-button`
- **What it does**: Button with animated shimmer spark effect using conic-gradient
- **Props**: `shimmerColor`, `shimmerSize`, `shimmerDuration`, `borderRadius`, `background`, `className`
- **Used on**: [[Page-Landing]] (primary CTA)
- **Customizations**: Custom shimmer colors to match brand blue

### 6. BorderBeam
- **File**: `components/magicui/border-beam.tsx` (75 lines)
- **Registry**: `border-beam`
- **What it does**: Animated gradient beam traveling along element border
- **Props**: `size`, `duration`, `delay`, `colorFrom`, `colorTo`, `transition`, `style`, `reverse`, `initialOffset`, `borderWidth`
- **Used on**: Previously on Action Plans and pricing cards — **removed in commit 75239a5** (caused visual noise)
- **Customizations**: N/A (removed)

## CSS Keyframes (globals.css)
```css
@keyframes marquee { from { transform: translateX(0) } to { transform: translateX(calc(-100% - var(--gap))) } }
@keyframes shimmer-slide { to { transform: translate(calc(100cqw - 100%), 0) } }
@keyframes spin-around { 0% { transform: translateZ(0) rotate(0) } 15%, 35% { transform: translateZ(0) rotate(90deg) } 65%, 85% { transform: translateZ(0) rotate(270deg) } 100% { transform: translateZ(0) rotate(360deg) } }
@keyframes fade-up { from { opacity: 0; transform: translateY(20px) } to { opacity: 1; transform: translateY(0) } }
```

## Related Notes
- [[Design-System]] — Overall visual language
- [[Tech-Stack]] — Framer Motion dependency
- [[Page-Landing]] — Primary showcase of all Magic UI components
