# Browser model mirrors

Byte-identical copies of published model files. They exist only because the SkillSafe
browser-model vetting intake accepts Hugging Face, npm and GitHub URLs (pinned to a commit) and
not the publisher's own storage host, and vets single ONNX / WebAssembly / TFLite files rather
than zip bundles. Verify any file by hashing it: the sha256 must match this table and the
original.

| File | Extracted from | sha256 | Bytes |
|---|---|---|---|
| `mediapipe/face_landmarker/float16/1/face_detector.tflite` | https://storage.googleapis.com/mediapipe-models/face_landmarker/face_landmarker/float16/1/face_landmarker.task, zip entry `face_detector.tflite` | `b4578f35940bf5a1a655214a1cce5cab13eba73c1297cd78e1a04c2380b0152f` | 229,746 |
| `mediapipe/face_landmarker/float16/1/face_landmarks_detector.tflite` | same bundle, zip entry `face_landmarks_detector.tflite` | `c7d54204ce0448474c7f3fa9af494787c0965cbdd6f20fc72867e43046bd43d5` | 2,553,590 |

The bundle itself is sha256 `64184e229b263107bc2b804c6625db1341ff2bb731874b0bcc2fe6544e0bc9ff`
(3,758,596 bytes); `unzip` it and hash the two entries to reproduce the table.

Licence: Apache-2.0 (Google MediaPipe, https://github.com/google-ai-edge/mediapipe/blob/master/LICENSE).
Model cards: BlazeFace short-range and Face Mesh V2, at storage.googleapis.com/mediapipe-assets.
Used by https://id-photo-maker.skillsafe.ai/ for its on-device head-height and eye-line check,
which packs the two files back into a stored zip in the browser and runs them with the
MediaPipe Tasks Vision runtime (`@mediapipe/tasks-vision` 1.0.1).
