# Third-party licenses

ataby Upscaler includes the third-party programs listed below. They are bundled unchanged and run as separate executables. Each one is covered by its own license, and the original license files are kept in this folder.

These licenses apply to the programs named here, not to ataby Upscaler itself.

## FFmpeg

- **Used for:** reading videos, resizing and sharpening frames, encoding the output, and handling audio.
- **Included files:** `ffmpeg.exe` and `ffprobe.exe` in the `tools` folder.
- **License:** LGPL or GPL, depending on how the included build was compiled. The license files in the `FFmpeg` folder here are the ones that apply to the included build.
- **Build source:** _write here where you downloaded this build and its version, for example the website and version number_
- **Source code:** available from the official FFmpeg project at https://ffmpeg.org/download.html and from the page where the build above was obtained.
- **Project website:** https://ffmpeg.org

FFmpeg is a trademark of Fabrice Bellard, originator of the FFmpeg project.

## Real-ESRGAN

- **Used for:** the AI upscaling models and the research behind them.
- **Included files:** the model files in `tools\realesrgan\models` (`.param` and `.bin`).
- **License:** see the files in the `Real-ESRGAN` folder here.
- **Project website:** https://github.com/xinntao/Real-ESRGAN

## Real-ESRGAN-ncnn-vulkan

- **Used for:** running the Real-ESRGAN models on any Vulkan-capable GPU (NVIDIA, AMD, Intel).
- **Included files:** `realesrgan-ncnn-vulkan.exe` and its supporting files in `tools\realesrgan`.
- **License:** see the files in the `Real-ESRGAN-ncnn-vulkan` folder here. The executable may contain other open-source components, whose licenses are listed in those files.
- **Project website:** https://github.com/xinntao/Real-ESRGAN-ncnn-vulkan

## No warranty

These programs are provided "as is", without warranty of any kind, as described in their licenses. Their authors and copyright holders are not responsible for ataby Upscaler.

## Questions

If you think a license file is missing or something here is wrong, please open an issue in the project repository.
