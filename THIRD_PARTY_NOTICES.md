# Third-party software

SignBridge is built on open-source work. These pieces are copied into the site by `npm run build`
and served from the site's own address.

| Project | What it is used for | License |
|---|---|---|
| [MediaPipe Tasks Vision](https://github.com/google-ai-edge/mediapipe) (`@mediapipe/tasks-vision` 0.10.14) | Finds the hand and its 21 points in the camera picture | Apache License 2.0 |
| MediaPipe Hand Landmarker model (`hand_landmarker.task`) | The trained hand model, downloaded once during the build | Apache License 2.0 |
| [Atkinson Hyperlegible](https://brailleinstitute.org/freefont) via [Fontsource](https://fontsource.org) | A typeface designed by the Braille Institute for easy reading | SIL Open Font License 1.1 |

Used only for development and tests: [jsdom](https://github.com/jsdom/jsdom) (MIT) and [esbuild](https://github.com/evanw/esbuild) (MIT).

Please check each project's own license text for the full terms.
