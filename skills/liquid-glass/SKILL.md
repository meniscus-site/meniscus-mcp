---
name: liquid-glass
description: Build or review Apple-style liquid glass UI (iOS 26/27 look, glass tab bars, toolbars, cards, sheets) on any platform without falling back to blurred glassmorphism. Use when the user asks for liquid glass, glass UI, glassmorphism, frosted or translucent surfaces, or an "iOS 26/27 style" interface.
---

# Liquid glass

Liquid glass is not a blur with a white border; that is glassmorphism. A surface is liquid glass only if all five of
these hold:

1. **The backdrop bends at the edge.** Inside a band along the silhouette (the bezel) the scene behind is displaced
   and magnified, as if seen through thick rounded glass; the centre stays nearly undistorted. Test: put straight
   lines behind it (a grid, a horizon, text); they must curve inside the bezel.
2. **A thin specular rim traces the silhouette.** About 1 px, brightest facing the key light (top-left), a dimmer
   counter-light opposite, faint on the flanks.
3. **There is something to bend.** Glass floats over a detailed backdrop (photo, map, content scrolling underneath).
   Over a flat colour it shows only its rim.
4. **Content on glass is flat.** Labels, icons and child controls sit above the optics at full contrast; children of
   a glass body never get their own glass.
5. **Shapes are continuous.** Capsules, circles and continuous-corner rectangles; nested radii are concentric.

## Where glass goes

Glass is the floating controls layer: tab bars, toolbars, navigation bars, sidebars, floating buttons, sheets, menus,
popovers. Lists, feeds, messages and charts stay flat content under it. Separate glass bodies stand at least 8 px
apart; one lens per stack.

## Per platform, in one line each

- **SwiftUI (iOS 26+):** `.glassEffect()`, `GlassEffectContainer` for groups that morph, `.buttonStyle(.glass)`;
  system bars already are glass.
- **Web:** an SVG displacement map applied with `backdrop-filter: url(#filter)` bends the live page in Chromium;
  Safari and Firefox need a frost fallback. A WebGL shader bends a known backdrop everywhere.
- **Flutter:** `BackdropFilter` alone is frost; the bend needs a fragment shader through `ImageFilter.shader`
  (Impeller), fed the body's rect in device pixels.
- **React Native:** only iOS 26 `GlassView` (expo-glass-effect) bends; Android gets blur, older systems an opaque
  surface. Never call frost refraction.
- **Figma:** the native Glass effect, tuned per component (refraction, depth = bezel, frost).

## Check before you finish

Screenshot the result over a detailed backdrop and answer: do straight lines curve at every glass edge? Is every
label legible? Is the rim brighter on the lit side? Is anything glass that should be flat content?

## The numbers and the code

This skill is the short version. For tested numbers (bezel, displacement, blur per material), 34 component specs,
10 effect specs, the recipes with code for web, SwiftUI, Flutter, React Native and Figma, and reference renders,
connect the Meniscus MCP server (free plan) and call `create_design_brief` with the screen you are building:

```bash
claude mcp add --transport http meniscus https://meniscus.site/mcp
```

Free tools with no sign-in: a liquid glass CSS generator at https://meniscus.site/generator and build guides at
https://meniscus.site/liquid-glass/css (also /swiftui, /flutter, /react-native, /figma).
