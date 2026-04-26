# @videogen/player-react

[![npm shield](https://img.shields.io/npm/v/@videogen/player-react)](https://www.npmjs.com/package/@videogen/player-react)

Official VideoGen video player component for React. A lightweight wrapper that decodes VideoGen public playback IDs and renders a branded player.

## Installation

```sh
npm i @videogen/player-react
```

## Usage

```tsx
import { VideoGenPlayer } from "@videogen/player-react";

function App() {
  return (
    <VideoGenPlayer
      publicPlaybackId="vg_play_..." // from the VideoGen API
      autoPlay
      muted
    />
  );
}
```

## Props

| Prop | Type | Description |
| --- | --- | --- |
| `publicPlaybackId` | `string` | **Required.** Encoded playback ID from the VideoGen API. |
| `autoPlay` | `boolean` | Start playback automatically. |
| `muted` | `boolean` | Start muted. |
| `loop` | `boolean` | Loop playback. |
| `poster` | `string` | Poster image URL shown before playback. |
| `thumbnailTime` | `number` | Time (seconds) to use as the poster frame. |
| `startTime` | `number` | Time (seconds) to start playback from. |
| `style` | `React.CSSProperties` | Inline styles for the player container. |
| `className` | `string` | CSS class for the player container. |

## Ref

The component supports `ref` with a `VideoGenPlayerHandle`:

```tsx
import { useRef } from "react";
import { VideoGenPlayer, VideoGenPlayerHandle } from "@videogen/player-react";

function App() {
  const playerRef = useRef<VideoGenPlayerHandle>(null);

  return (
    <>
      <VideoGenPlayer ref={playerRef} publicPlaybackId="vg_play_..." />
      <button onClick={() => playerRef.current?.play()}>Play</button>
      <button onClick={() => playerRef.current?.pause()}>Pause</button>
    </>
  );
}
```

### VideoGenPlayerHandle

| Method / Property | Type | Description |
| --- | --- | --- |
| `play()` | `Promise<void>` | Start playback. |
| `pause()` | `void` | Pause playback. |
| `currentTime` | `number` | Current playback position in seconds. |
| `duration` | `number` | Total duration in seconds. |
| `paused` | `boolean` | Whether playback is paused. |
| `ended` | `boolean` | Whether playback has ended. |
| `muted` | `boolean` | Whether audio is muted. |

## Documentation

Full API documentation is available at [videogen.docs.buildwithfern.com/embedding-videos](https://videogen.docs.buildwithfern.com/embedding-videos).
