# Flutter Face Detector Pro 🚀

**Flutter Face Detector Pro** is a high-performance mobile application that leverages on-device Machine Learning to detect faces in real-time. By utilizing Google ML Kit and Flutter's camera stream capabilities, this project achieves lightning-fast detection with zero latency, ensuring maximum user privacy.

## ✨ Key Features

* **Real-Time Detection:** Processes camera frames at 30+ FPS for smooth, real-time bounding box updates.
* **Advanced Landmarks & Contours:** Identifies specific facial features, including eyes, nose, mouth, and face contours.
* **Face Classification:** Detects smile probability and eye-opening state for liveness verification.
* **On-Device AI:** Powered by Google ML Kit for offline processing—no biometric data is ever sent to external servers.
* **Responsive UI Overlay:** Implements a `CustomPainter` to draw precise overlays that map correctly across different screen resolutions and aspect ratios.

## 🛠️ Tech Stack & Dependencies

This project is built using **Flutter 3.0.0+** and is optimized with the following specific package versions to ensure stability:

```yaml
dependencies:
  flutter:
    sdk: flutter
  camera: ^0.10.6              # Optimized for orientation and mirroring stability
  google_mlkit_face_detection: ^0.13.1
  provider: ^6.1.2             # Scalable state management
  permission_handler: ^12.0.0+1
  path_provider: ^2.1.1

```

## 🚀 Getting Started

### Prerequisites

* Flutter SDK: `^3.0.0`
* Dart: `^2.17.0`
* A physical Android or iOS device (Emulators do not support real-time camera streams effectively).

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/KamalSaiVoodika/Flutter-Face-Detector-Pro.git

```


2. **Navigate to the directory:**
```bash
cd Flutter-Face-Detector-Pro

```


3. **Install dependencies:**
```bash
flutter pub get

```


4. **Run the app:**
```bash
flutter run

```



## ⚙️ Platform Setup

### Android

* Set `minSdkVersion 21` in `android/app/build.gradle`.
* Add camera permission to `android/app/src/main/AndroidManifest.xml`:

```xml
    <uses-permission android:name="android.permission.CAMERA" />
    ```

### iOS
*   Add the camera usage description to `ios/Runner/Info.plist`:
    
```xml
    <key>NSCameraUsageDescription</key>
    <string>This app requires camera access to detect faces in real-time.</string>
    ```

## 🏗️ Core Implementation
The face detector is configured for maximum detail, enabling landmarks and classifications for high-precision tracking:

```dart
final faceDetector = GoogleMlKit.vision.faceDetector(
  FaceDetectorOptions(
    enableClassification: true,
    enableLandmarks: true,
    enableContours: true,
    enableTracking: true,
  ),
);

// High-performance image processing logic
Future<List<Face>> processImage(InputImage inputImage) async {
  return await faceDetector.processImage(inputImage);
}

```

## 🛠️ Troubleshooting

* **Orientation Issues:** We use `camera: ^0.10.6` specifically because newer versions (0.11.0+) are known to have orientation and mirroring bugs on certain hardware.
* **Permissions:** If the app crashes, ensure you have manually granted camera permissions in the device settings.
* **Lighting:** For the best ML performance, ensure the subject's face is well-lit.

## 🗺️ Roadmap

* [ ] **Capture & Save:** Implement functionality to save detected faces to local storage.
* [ ] **Custom Toggles:** Add UI toggles to enable/disable landmarks and contours dynamically.
* [ ] **Liveness Tracking:** Integrate "Blink" or "Smile" triggers to verify the user is a real person.
* [ ] **Performance:** Implement Flutter Isolates for heavy ML computations to maintain UI fluidity.

## 📄 License

This project is licensed under the MIT License.

## 🤝 Acknowledgements

* [Flutter Camera Plugin](https://pub.dev/packages/camera)
* [Google ML Kit](https://developers.google.com/ml-kit)

```</List<Face>

```
