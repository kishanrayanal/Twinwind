## Prerequisites

- **macOS 14+**  
- **Xcode 16.4+**  
- An **Apple Developer** account (free account is fine for development on a device)  
- A physical iOS device running **iOS 18+** (Simulator audio recording is unreliable)  
- **Git** installed on your machine

---

## 1. Clone the Repository

```bash
git clone https://github.com/your-username/TwinWindAudioRecorder.git
cd TwinWindAudioRecorder

2. Open in Xcode
Double-click TwinWindAudioRecorder.xcodeproj

In Xcode’s Targets → Signing & Capabilities, make sure:

Automatically manage signing is enabled

A valid Team is selected

Your Bundle Identifier (e.g. com.yourcompany.TwinWindAudioRecorder) is unique

3. Insert Your OpenAI API Key
The app reads your Whisper key from the Keychain under the account name OpenAIAPIKey.

Manually (recommended for development):

Open Keychain Access on your Mac

Choose login in the sidebar → File → New Password Item…

Account Name: OpenAIAPIKey

Password: your sk-… secret key

Click Add

Programmatically (optional):
Paste your key into KeychainHelper.save(_:forKey:) in TwinWindAudioRecorderApp.swift or an early onAppear.

4. Select Your Device
In Xcode’s toolbar device menu, choose Any iOS Device (arm64) or plug in your iPhone via USB/Wi-Fi.

Your device should appear in the list—select it.

5. Build & Run
Press ⌘R (Run).

On first launch, tap Allow when prompted for microphone access.

You’ll land on the Recorder screen—tap the big mic icon to start/stop recording.
Switch to Sessions to browse by date; tap a session to view its 30 s segments and live transcription status.

Troubleshooting
Build errors about SwiftData macros?

Ensure your Deployment Target (Targets → General) is iOS 18.0+.

“Select a provisioning profile” when archiving?

Use Automatically manage signing, click Resolve Issues, then re-archive.

No microphone input?

On your device, go to Settings → Privacy & Security → Microphone → enable the app.

Transcriptions stuck at “Processing…”?

Verify that KeychainHelper.shared.get("OpenAIAPIKey") prints a non-nil value in the console.
