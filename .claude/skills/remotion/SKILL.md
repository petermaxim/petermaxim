---
name: remotion
description: "Create videos programmatically with React using Remotion. Reels, ads, carousels, animated explainers — all code-driven. Use when: creating Instagram reels, building video intros, making animated explainers, generating ads, creating animated carousels, producing social media videos."
user-invocable: true
allowed-tools:
  - Read
  - Bash
  - WebFetch
---

# Remotion: Programmatic Video with React

Create videos as React components. Everything is code — no timeline editors, no manual rendering.

## Core Concepts

### Composition

Every video is a `<Composition>` — defines width, height, fps, and duration:

```tsx
import { Composition } from "remotion";

export const RemotionRoot = () => (
  <Composition
    id="MyVideo"
    component={MyVideo}
    durationInFrames={150}
    fps={30}
    width={1920}
    height={1080}
  />
);
```

### useCurrentFrame

The fundamental hook — gives you the current frame number:

```tsx
import { useCurrentFrame } from "remotion";

export const MyVideo = () => {
  const frame = useCurrentFrame();
  return <div style={{ opacity: frame / 30 }}>Hello</div>;
};
```

### spring() — Physics-Based Motion

The primary animation primitive. Never use CSS transitions for video — use `spring()`:

```tsx
import { spring, useCurrentFrame, useVideoConfig } from "remotion";

export const Animated = () => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();

  const scale = spring({
    frame,
    fps,
    config: {
      damping: 200,
      stiffness: 80,
      mass: 1,
    },
  });

  return <div style={{ transform: `scale(${scale})` }}>Content</div>;
};
```

### interpolate()

Map frame ranges to value ranges:

```tsx
import { interpolate, useCurrentFrame } from "remotion";

const opacity = interpolate(frame, [0, 30], [0, 1], {
  extrapolateLeft: "clamp",
  extrapolateRight: "clamp",
});
```

## Sequences and Timing

### `<Sequence>` — Offset Content in Time

```tsx
import { Sequence } from "remotion";

export const MyVideo = () => (
  <>
    <Sequence from={0} durationInFrames={60}>
      <Title />
    </Sequence>
    <Sequence from={30} durationInFrames={90}>
      <Content />
    </Sequence>
  </>
);
```

### `<Series>` — Stack Sequences Back-to-Back

```tsx
import { Series } from "remotion";

export const MyVideo = () => (
  <Series>
    <Series.Sequence durationInFrames={60}><Intro /></Series.Sequence>
    <Series.Sequence durationInFrames={90}><Main /></Series.Sequence>
    <Series.Sequence durationInFrames={30}><Outro /></Series.Sequence>
  </Series>
);
```

## Staggered Reveals

Stagger children by offsetting their `from` prop:

```tsx
const items = ["First", "Second", "Third"];

export const List = () => (
  <>
    {items.map((item, i) => (
      <Sequence key={item} from={i * 10}>
        <FadeIn>{item}</FadeIn>
      </Sequence>
    ))}
  </>
);
```

## Media

### Images
```tsx
import { Img, staticFile } from "remotion";

<Img src={staticFile("photo.jpg")} />
// Or from URL:
<Img src="https://example.com/image.jpg" />
```

### Audio
```tsx
import { Audio, staticFile } from "remotion";

<Audio src={staticFile("background.mp3")} volume={0.5} />
```

### Video
```tsx
import { Video, staticFile } from "remotion";

<Video src={staticFile("clip.mp4")} />
```

### Fonts (Google Fonts)
```tsx
import { loadFont } from "@remotion/google-fonts/Inter";

const { fontFamily } = loadFont();
// Use fontFamily in styles
```

## Captions

```tsx
import { useCurrentFrame } from "remotion";

const captions = [
  { startFrame: 0, endFrame: 60, text: "Welcome to my video" },
  { startFrame: 60, endFrame: 120, text: "Let's get started" },
];

export const Captions = () => {
  const frame = useCurrentFrame();
  const caption = captions.find(c => frame >= c.startFrame && frame < c.endFrame);
  return caption ? <div className="caption">{caption.text}</div> : null;
};
```

## Common Animation Patterns

### Fade In
```tsx
const opacity = spring({ frame, fps, config: { damping: 200 } });
```

### Slide In from Left
```tsx
const x = interpolate(
  spring({ frame, fps }),
  [0, 1],
  [-100, 0]
);
```

### Scale Pop
```tsx
const scale = spring({
  frame,
  fps,
  config: { damping: 12, stiffness: 200 },
});
```

### Typewriter Effect
```tsx
const chars = Math.floor(interpolate(frame, [0, 60], [0, text.length], {
  extrapolateRight: "clamp",
}));
const displayText = text.slice(0, chars);
```

## Export Formats

| Format | Command |
|--------|---------|
| MP4 | `npx remotion render MyVideo out.mp4` |
| GIF | `npx remotion gif MyVideo out.gif` |
| PNG sequence | `npx remotion still MyVideo --frame=0` |
| ProRes | `npx remotion render MyVideo out.mov --codec=prores` |

## Common Video Sizes

| Format | Width | Height | FPS |
|--------|-------|--------|-----|
| Instagram Reel / TikTok | 1080 | 1920 | 30 |
| YouTube | 1920 | 1080 | 30 |
| Twitter/X | 1280 | 720 | 30 |
| Instagram Square | 1080 | 1080 | 30 |
| Story | 1080 | 1920 | 30 |

## Key Rules

1. **Never use CSS `transition` or `animation`** — use `spring()` or `interpolate()` with `useCurrentFrame()`
2. **Every value must be deterministic** given a frame number — no `Math.random()` without a seed
3. **Use `staticFile()`** for local assets, never relative paths
4. **FPS matters** — always get fps from `useVideoConfig()`, never hardcode it
5. **Clamp interpolations** — always set `extrapolateLeft: "clamp"` and `extrapolateRight: "clamp"` unless intentional
6. **Use `<AbsoluteFill>`** for full-frame backgrounds and overlays

```tsx
import { AbsoluteFill } from "remotion";

export const Background = () => (
  <AbsoluteFill style={{ backgroundColor: "#000" }} />
);
```

## Project Setup

```bash
npx create-video@latest
cd my-video
npm run dev   # Opens the Remotion Studio at localhost:3000
```
