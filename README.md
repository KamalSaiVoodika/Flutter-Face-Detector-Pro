# Flutter-Face-Detector-Pro 👤🚀

[![Pub](https://img.shields.io/badge/pub-v1.0.0-blue)](https://pub.dev/)
[![Flutter](https://img.shields.io/badge/Flutter-%E2%9C%93-brightgreen)](https://flutter.dev)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Flutter-Face-Detector-Pro** is a high-performance, real-time face detection package for Flutter apps. Powered by advanced machine learning models (like Google ML Kit), it enables developers to seamlessly track faces, identify facial landmarks (eyes, ears, nose, mouth), and detect expressions like smiling or blinking with minimal configuration.

Perfect for building AI filters, biometric check-ins, KYC identity verification, or smart camera applications.

---

## 🔥 Key Features

* **Real-Time Performance:** Ultra-low latency face detection suitable for live camera streams.
* **Landmark Detection:** Identify exact coordinates for eyes, nose, mouth, cheeks, and ears.
* **Contour Tracking:** Map the precise structural outline of eyes, eyebrows, lips, and face shape.
* **Classification Models:** Detect facial expressions such as "smiling probability" and "left/right eye open probability".
* **Cross-Platform:** Out-of-the-box support for both **iOS** and **Android**.

---

## 📦 Installation

Add this to your package's `pubspec.yaml` file:

```yaml
dependencies:
  flutter_face_detector_pro:
    git:
      url: [https://github.com/KamalSaiVoodika/Flutter-Face-Detector-Pro.git](https://github.com/KamalSaiVoodika/Flutter-Face-Detector-Pro.git)

```

*Don't forget to run `flutter pub get` in your terminal.*

---

## ⚙️ Platform Setup

### Android

Ensure your `minSdkVersion` is set to **21** or higher in `android/app/build.gradle`:

```groovy
defaultConfig {
    minSdkVersion 21
}

```

### iOS

Add camera permissions to your `ios/Runner/Info.plist`:

```xml
<key>NSCameraUsageDescription</key>
<string>This app requires camera access to detect faces in real-time.</string>

```

---

## 🛠️ Usage Example

Here is how easily you can initialize the face detector and process an image:

```dart
import 'package:flutter/material.dart';
import 'package:flutter_face_detector_pro/flutter_face_detector_pro.dart';

void main() async {
  // 1. Initialize the Face Detector with custom options
  final FaceDetector faceDetector = FaceDetector(
    options: FaceDetectorOptions(
      enableLandmarks: true,
      enableClassification: true,
      performanceMode: FaceDetectorMode.accurate,
    ),
  );

  // 2. Pass an InputImage (from file or camera stream)
  final InputImage inputImage = InputImage.fromFilePath('path_to_image.jpg');
  final List<Face> faces = await faceDetector.processImage(inputImage);

  // 3. Extract details
  for (Face face in faces) {
    final Rect boundingBox = face.boundingBox;
    
    // Check facial features
    if (face.smilingProbability != null) {
      double smileProb = face.smilingProbability!;
      print("Smiling Probability: ${(smileProb * 100).toStringAsFixed(1)}%");
    }
  }

  // 4. Always close the detector when done
  faceDetector.close();
}

```

---

## 🤝 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any improvements, bug fixes, or feature additions are welcome!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more details.

---

## 📞 Contact

**Kamal Sai Voodika** Project Link: [https://github.com/KamalSaiVoodika/Flutter-Face-Detector-Pro](https://github.com/KamalSaiVoodika/Flutter-Face-Detector-Pro)

---

*If you find this repository helpful, please drop a ⭐ to show your support!*

```

### Why this is the best structure:
1. **Badges:** Gives it an official, package-ready aesthetic right at the top.
2. **Clear Pitch:** Explains *why* someone should use this package instead of doing it from scratch (KYC, filters, smart camera).
3. **Configuration Requirements:** Saves developers hours of debugging by laying out the `minSdkVersion` and `Info.plist` requirements immediately.
4. **Clean Code Snippet:** Uses clean, generic syntax representing typical ML Kit wrappers so developers can adapt it to their codebase instantly.

```
