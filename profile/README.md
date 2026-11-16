<p align="center">
  <img src="https://raw.githubusercontent.com/eskiu-lang/eskiu/main/assets/logo.png" alt="Eskiu" width="120">
</p>

<h3 align="center">Eskiu packages</h3>

<p align="center">
  The packages the Eskiu project maintains.
  <br>
  <a href="https://github.com/eskiu-lang/eskiu">The language</a> ·
  <a href="https://eskiu-lang.org/packages.html">Package catalog</a> ·
  <a href="https://eskiu-lang.org">Website</a>
</p>

---

These are packages like any other: they live apart from the language
([eskiu-lang/eskiu](https://github.com/eskiu-lang/eskiu)), and a package from anyone's
repository is added the same way, by its git URL and a tag. Each one needs Eskiu 0.15.1 or
newer unless its README says otherwise.

## Libraries

Each one is added with `eskiuc add NAME --git https://github.com/eskiu-packages/REPO --rev TAG`, at the
tag its README gives. Every package documents its whole API in `docs/api.md`.

| Package | What it does |
|---|---|
| [gpu](https://github.com/eskiu-packages/gpu) | GPU compute and rendering over WebGPU (Metal, Vulkan, DirectX 12, and the browser, with a WebGL2 fallback), glTF and OBJ models with PBR, morph targets, image-based lighting and shadows, render targets, cube maps and compressed textures, camera and video frames from YUV, windows, gamepads and touch over SDL3, and machine learning: Llama inference from GGUF and safetensors (Llama 2 7B at 45 tokens per second on an M4 Pro) and training |
| [scene](https://github.com/eskiu-packages/scene) | A scene graph and material renderer on gpu: Constant, Lambert, Phong, Blinn and PBR materials, ambient, directional, point and spot lights, HDR with tone mapping and bloom, skyboxes and shadows, input, physics, animation, particles, and rendering for Meta Quest and Apple Vision Pro |
| [onnx](https://github.com/eskiu-packages/onnx) | ONNX Runtime inference on the CPU, Core ML, NNAPI and WebGPU, with image resizing that matches Pillow and OpenCV byte for byte and SSD detection helpers |
| [tflite](https://github.com/eskiu-packages/tflite) | TensorFlow Lite inference with the XNNPACK, GPU and Core ML delegates |
| [compress](https://github.com/eskiu-packages/compress) | Deflate, zlib, gzip and zip, written in Eskiu |
| [yaml](https://github.com/eskiu-packages/yaml) | YAML configuration files read into the standard library's JSON tree, written in Eskiu |
| [audio](https://github.com/eskiu-packages/audio) | WAV files, Ogg Vorbis on every platform, a mixer with buses, loop points, fades and gapless playlists, and sound output: SDL3 on the desktop, RemoteIO and AAudio on iOS and Android, where MP3, AAC and FLAC decode through the system |
| [font](https://github.com/eskiu-packages/font) | TrueType fonts: glyph rendering, text layout and atlases |
| [jni](https://github.com/eskiu-packages/jni) | Native methods for Android and the JVM, written in Eskiu with no C glue |
| [nds](https://github.com/eskiu-packages/nds) | Nintendo DS file formats: ROMs, NARC archives, SDAT sound, 2D graphics, 3D textures, and models, animations and SPL particles exported to glTF |
| [quickjs](https://github.com/eskiu-packages/quickjs) | JavaScript in Eskiu programs through QuickJS, with prebuilt libraries for each platform |
| vision (private for now) | Corners, optical flow, multi-view geometry and planes in pure Eskiu, from ReactVision's tinyvio; it opens together with tinyvio |

## The ui framework

[ui](https://github.com/eskiu-packages/ui) makes native apps for iOS, Android, macOS, Linux, Windows
and the web from one Eskiu codebase: components drawn by each platform's own views, signals,
navigation, a kit of themed components, and the `ui` tool that builds, reloads and ships them
to the stores. `<ui/webapp>` also runs a web front end in the desktop's webview with the
Eskiu program as its backend, as Tauri does for Rust. Packages bring device services and drawing to a ui app:

| Package | What it does |
|---|---|
| [ui-location](https://github.com/eskiu-packages/ui-location) | Where the device is |
| [ui-notifications](https://github.com/eskiu-packages/ui-notifications) | Local notifications, shown also with the app closed |
| [ui-camera](https://github.com/eskiu-packages/ui-camera) | Photos from the library and the camera, a live camera view, and its frames handed to Eskiu |
| [video](https://github.com/eskiu-packages/video) | Video playback with the platform's player, and the decoded frames handed to Eskiu |
| [ar](https://github.com/eskiu-packages/ar) | ARKit, ARCore and WebXR sessions: camera pose, planes, anchors, hit tests, image targets, light and depth, meshes, faces and bodies, cloud and Earth anchors, with the camera image for gpu to draw |
| [arscene](https://github.com/eskiu-packages/arscene) | An ar session drawn with scene, as ViroReact's AR navigator: the camera behind the scene, depth occlusion, tap to place, image markers and the world mesh |
| [ui-barcode](https://github.com/eskiu-packages/ui-barcode) | QR codes and barcodes read live from the camera |
| [ui-pedometer](https://github.com/eskiu-packages/ui-pedometer) | Steps walked, live and between two times |
| [ui-securestore](https://github.com/eskiu-packages/ui-securestore) | Small secrets in the Keychain and the Android Keystore |
| [ui-svg](https://github.com/eskiu-packages/ui-svg) | SVG drawings, tinted by the style's color |
| [ui-canvas](https://github.com/eskiu-packages/ui-canvas) | A 2D canvas drawn every frame, for sprites and pixel art |

[ui-starter](https://github.com/eskiu-packages/ui-starter) is an app to start from, and
[ui-package-template](https://github.com/eskiu-packages/ui-package-template) a package to start from.

## Publishing your own

A package is a git repository with an `eskiu.toml` (`eskiuc new NAME` makes one, and
[ui-package-template](https://github.com/eskiu-packages/ui-package-template) starts a package
for ui apps). Tag a release and others add it with
`eskiuc add NAME --git https://github.com/YOU/NAME --rev v0.1.0`. To list it next to these,
open a pull request on the [package index](https://github.com/eskiu-lang/index) that adds
`packages/NAME.toml`.
