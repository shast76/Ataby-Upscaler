# ataby Upscaler

Upscale videos to 1080p, 1440p or 4K right in your browser. No uploads, no installs, no account.

**Use it here: [upscaler.ataby.info](https://upscaler.ataby.info)**

ataby Upscaler is available only as a hosted web app at the address above. This repository contains documentation only; the source file is not distributed.

## What it does

ataby Upscaler takes a video file, enlarges every frame on your GPU, sharpens it, and re-encodes the result into a new video file you can save.

- Output at **1080p, 1440p or 4K (2160p)**, keeping the original aspect ratio (landscape and portrait both work)
- **Adjustable sharpening**, from soft to strong
- **Three quality presets**: Balanced (16 Mbps), High (35 Mbps), Maximum (60 Mbps)
- **Before/after comparison slider** to see the difference against a normal browser upscale
- **Audio is kept** in the output
- Exports **MP4 (H.264)** where the browser supports it, otherwise **WebM**
- Estimated output size is shown before you start

## How it works

Each video frame is uploaded to a WebGL texture and drawn at the target resolution with a fragment shader that does two things:

1. **Catmull-Rom bicubic resampling** over a 4×4 pixel neighbourhood, which gives a much cleaner enlargement than the browser's default bilinear scaling.
2. **Edge-preserving sharpening** (unsharp mask), clamped to the local minimum and maximum of the neighbouring pixels so it doesn't produce bright halos around edges.

The canvas is then recorded with the browser's `MediaRecorder` API together with the original audio track, and the result is offered as a download.

### What it is not

This is **not AI upscaling**. It does not invent detail that isn't in the source video. It produces a noticeably crisper image than plain browser scaling, but it won't match neural upscalers such as Real-ESRGAN or Topaz Video AI on heavily compressed or very low-resolution footage.

## Usage

1. Open the site and drop a video onto the stage, or click **Select video**.
2. Choose the output resolution, sharpening amount and quality.
3. Optionally turn on **Compare** and drag the divider to preview the result.
4. Click **Start upscaling** and keep the tab open and visible until it finishes.
5. Preview the result and click **Save**.

## Limits and good to know

- **It runs in real time.** A 10-minute video takes about 10 minutes to process, because frames are captured as the video plays.
- **Keep the tab visible.** If the tab goes to the background, the browser can throttle rendering and frames may be dropped.
- **Memory.** The output is held in memory until it is saved. Rough sizes per minute of video: about 120 MB (Balanced), 260 MB (High), 450 MB (Maximum). Very long videos at 4K may exhaust memory on some machines.
- **Hardware.** Scaling and sharpening run on the GPU. Video decoding and encoding use hardware acceleration when your browser and device support it; otherwise they fall back to the CPU, which can be slow at 4K. The page shows the processing frame rate while it works. If it drops below the video's frame rate, try a lower resolution or quality.
- **Codecs.** The browser must be able to play your input file. Some formats, such as HEVC (H.265), don't open in every browser. H.264 MP4 and WebM are the safest.
- **WebM output** may have limited seeking in some players.
- **Mobile devices** can struggle with 4K. Use 1080p or 1440p and short clips there.

### Browser support

Best in recent **Chrome** and **Edge**. It needs WebGL, `MediaRecorder` and `canvas.captureStream()`. Other browsers may work but are not tested.

## Privacy

Your video never leaves your device. All processing happens locally in your browser tab, and nothing is uploaded to a server. The page loads one web font from Google Fonts, which is the only external request.

## Responsible use

Only process videos you own or have permission to modify. Upscaling a video does not change who holds the rights to it.

## License

Copyright (c) ataby. All rights reserved.
