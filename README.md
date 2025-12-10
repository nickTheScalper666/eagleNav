EagleNav EfficientDet
EagleNav is an iOS prototype that uses an EfficientDet-based object detector together with ARKit and device sensors to help users understand their surroundings. The app performs real-time object detection on the iPhone camera feed and can be extended to provide audio or on-screen guidance for navigation.

📱 This README is written for running the app locally on a real iPhone via Xcode (not for App Store distribution).


Table of Contents

Features
Project Structure
Requirements
Getting Started

1. Clone the repository
2. Install dependencies (if applicable)
3. Open the project in Xcode
4. Configure signing & bundle identifier
5. Connect your iPhone
6. First build & run


App Usage
Troubleshooting
Extending the Project
Academic / Project Notes
License
Acknowledgements


Features

📷 Real-time camera input using AVFoundation/ARKit.
🧠 EfficientDet-based object detection via a machine-learning model (Core ML or TFLite).
🧭 (Optional) AR-based spatial context – objects anchored in 3D space.
🗣️ (Optional) Audio accessibility feedback.
🔧 Modular design for swapping different EfficientDet variants.


Project Structure
Your repository will look roughly like:

EagleNav-EfficientDet.xcodeproj or .xcworkspace
Sources/ or EagleNav-EfficientDet/ – Swift logic, view controllers, AR managers
Models/ – ML model files (.mlmodel or .tflite)
Assets.xcassets – icons, colors, images
Info.plist – camera/mic permissions


Requirements
Hardware

Mac with Apple Silicon or Intel
iPhone (e.g., iPhone 15 Pro Max) running iOS 16+

Software

macOS Monterey or newer
Xcode 15+
Apple ID (free) for device signing

Permissions

Camera (required)
Microphone / speech (optional)


Getting Started
1. Clone the repository
If already on GitHub:
bashgit clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
If created from ZIP:
bashcd ~/Developer/eagleNav-efficientDet
git init
git add .
git commit -m "Initial commit: EagleNav EfficientDet"
git remote add origin https://github.com/<your-username>/<your-repo-name>.git
git push -u origin main
2. Install dependencies (if applicable)
Check if a Podfile exists:
If using CocoaPods:
bashsudo gem install cocoapods
pod install
➡️ Open the .xcworkspace afterward, not .xcodeproj
If no Podfile:
Just open the .xcodeproj and SPM will auto-resolve.
3. Open the project in Xcode
Open EagleNav-EfficientDet.xcworkspace (Pods) or EagleNav-EfficientDet.xcodeproj (SPM only)
In Xcode:

Click the project name in the left sidebar
Select the app target

4. Configure signing & bundle identifier
Go to Signing & Capabilities:

Team → choose your Apple ID
Bundle ID → make unique: com.<yourname>.eaglenav
Enable Automatically manage signing
Xcode will generate a provisioning profile.

5. Connect your iPhone

Plug in device via USB-C/Lightning
Tap Trust This Computer
In Finder → enable Developer Mode:

iPhone: Settings → Privacy & Security → Developer Mode → Enable


Select your iPhone as the run target in Xcode.

6. First build & run
Press ⌘R or click Run ▶.
Xcode will:

Build the app
Install on your iPhone
Launch automatically

On first launch, allow permissions:

Camera → Allow
Microphone (if applicable) → Allow

If successful, you'll see the live camera view with detection overlays.

App Usage
Typical usage flow:

Launch the app
Point the camera at surroundings
EfficientDet runs real-time inference
Bounding boxes and labels appear (doors, signs, etc.)
If enabled, audio cues describe detected objects

Use UI toggles to:

Switch models
Adjust detection threshold
Enable/disable AR overlays


Troubleshooting
App doesn't install / build fails
Check:

Device selected as run destination
Signing team set
Bundle ID is unique
Xcode supports your iOS version

Model loading errors
Ensure the ML model is:

Added to Xcode project
Included in Target Membership
Named correctly in the code

CocoaPods issues
If you see "No such module":
bashpod install
Then reopen the .xcworkspace.

Download coreML models from here
https://github.com/gouthamvgk/coreml_conversion_hub
