# PrivacyPenguin – setting reference

Every setting PrivacyPenguin can change, with the exact registry values and services it writes and what Undo puts
back. Generated from the app's own catalog (version 0.25.8), so it always matches what the app does.

**196 settings:** 108 in Recommended, 143 in Enhanced (which includes all of Recommended), and 53 that you can only pick yourself on the Advanced settings page.

**How to read it**

- **Rating:** Recommended (little effect on everyday use), Trade-off (you may notice it), Not recommended (weakens
  security or a core feature; never in a preset, and the app warns before applying it).
- **Applies to:** *each account* settings live in the account's own registry (HKCU) and can be applied to one
  account or to all accounts; *whole PC* settings (HKLM) apply to everyone.
- **Undo:** before its first change, PrivacyPenguin saves the value that was there. Undo all puts exactly that
  back (or removes the value if there was none), and a Windows switch that had the feature off then is put back
  off; it never turns on a switch that PrivacyPenguin didn't turn on, and leaves other values alone. Unticking
  one setting turns the feature back on: it puts back the saved value, and where that value had the feature off too,
  it writes the **Windows default** column instead; "removed" there means the value is deleted, which returns
  Windows to its own default behavior.
- A restore point comes before every batch of changes (Windows makes at most one every 24 hours, so it may be one made in the last 24 hours).

## Contents

- [General Privacy](#general-privacy) (14)
- [Activity & Clipboard](#activity--clipboard) (4)
- [App Permissions](#app-permissions) (38)
- [Windows AI](#windows-ai) (8)
- [Search](#search) (4)
- [Start & Explorer](#start--explorer) (8)
- [Lock Screen](#lock-screen) (7)
- [Settings Sync](#settings-sync) (6)
- [Telemetry & Diagnostics](#telemetry--diagnostics) (7)
- [Location](#location) (4)
- [Windows Update](#windows-update) (12)
- [Microsoft Edge](#microsoft-edge) (23)
- [Microsoft Office](#microsoft-office) (12)
- [Google Chrome](#google-chrome) (10)
- [Brave Browser](#brave-browser) (8)
- [Network & Remote Access](#network--remote-access) (5)
- [Gaming](#gaming) (1)
- [Legacy (Windows 10)](#legacy-windows-10) (5)
- [Mobile Devices](#mobile-devices) (1)
- [OneDrive](#onedrive) (2)
- [Hardware & Connectivity](#hardware--connectivity) (6)
- [Security](#security) (2)
- [Usability](#usability) (4)
- [Performance](#performance) (5)
- [Tools](#tools) (one-time jobs, never part of a preset)

## General Privacy

### Disable advertising ID

`privacy.advertising-id` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC

Stops apps from using a per-user advertising ID to track you across apps.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\AdvertisingInfo` → `Enabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\AdvertisingInfo` → `DisabledByGroupPolicy` (DWORD) | `1` | removed |

### Disable sending typing data

`privacy.typing-data` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Stops Windows from sending typing and inking samples to Microsoft to improve recognition.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Input\TIPC` → `Enabled` (DWORD) | `0` | removed |

### Disable inking & typing personalization

`privacy.input-personalization` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Stops Windows building a personal dictionary from your typing, handwriting and contacts.

**What you may notice:** Handwriting and typing suggestions become slightly less personalized.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\InputPersonalization` → `RestrictImplicitInkCollection` (DWORD) | `1` | removed |
| `HKCU\Software\Microsoft\InputPersonalization` → `RestrictImplicitTextCollection` (DWORD) | `1` | removed |
| `HKCU\Software\Microsoft\InputPersonalization\TrainedDataStore` → `HarvestContacts` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Personalization\Settings` → `AcceptedPrivacyPolicy` (DWORD) | `0` | removed |

### Disable tailored experiences

`privacy.tailored-experiences` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Stops Microsoft using your diagnostic data to personalize tips, ads and recommendations.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Privacy` → `TailoredExperiencesWithDiagnosticDataEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Policies\Microsoft\Windows\CloudContent` → `DisableTailoredExperiencesWithDiagnosticData` (DWORD) | `1` | removed |

### Disable tips, suggestions and suggested content

`privacy.suggestions` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Removes suggestions in Start, Settings and while using Windows, plus 'finish setting up your device' prompts.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SubscribedContent-338388Enabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SubscribedContent-338389Enabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SubscribedContent-338393Enabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SubscribedContent-353694Enabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SubscribedContent-353696Enabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SubscribedContent-310093Enabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SystemPaneSuggestionsEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SoftLandingEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\UserProfileEngagement` → `ScoobeSystemSettingEnabled` (DWORD) | `0` | removed |

### Disable automatic installation of promoted apps

`privacy.auto-installed-apps` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC

Stops Windows silently installing sponsored Store apps and games.

**What you may notice:** None. (Its policy value only works on Enterprise and Education.)

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SilentInstalledAppsEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `OemPreInstalledAppsEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `PreInstalledAppsEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\CloudContent` → `DisableWindowsConsumerFeatures` (DWORD) | `1` | removed |

### Disable feedback requests

`privacy.feedback-prompts` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC

Stops Windows asking you to rate it or give feedback.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Siuf\Rules` → `NumberOfSIUFInPeriod` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection` → `DoNotShowFeedbackNotifications` (DWORD) | `1` | removed |

### Hide your language list from websites

`privacy.browser-language` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Websites can no longer read your installed Windows languages, which reduces fingerprinting.

**What you may notice:** A site may occasionally pick the wrong display language.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Control Panel\International\User Profile` → `HttpAcceptLanguageOptOut` (DWORD) | `1` | removed |

### Disable online speech recognition

`privacy.online-speech` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC

Stops your voice being sent to Microsoft's cloud speech service.

**What you may notice:** Voice typing (Win+H) and some voice features stop working or become less accurate.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Speech_OneCore\Settings\OnlineSpeechPrivacy` → `HasAccepted` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\InputPersonalization` → `AllowInputPersonalization` (DWORD) | `0` | removed |

### Disable cloud backup of text messages

`privacy.message-backup` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops text messages synced from your phone being backed up to Microsoft's cloud.

**What you may notice:** None.

- Only offered when Microsoft Messaging is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Messaging` → `AllowMessageSync` (DWORD) | `0` | removed |

### Hide Microsoft account promotions

`privacy.account-state-content` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops Windows showing account-status content such as backup and subscription promotions.

**What you may notice:** None.

- Not offered on Windows Home or Pro, which don't follow it. If you already have it, it stays, marked as kept.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\CloudContent` → `DisableConsumerAccountStateContent` (DWORD) | `1` | removed |

### Disable Bluetooth advertising

`privacy.bluetooth-advertising` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Your PC stops broadcasting Bluetooth advertisements that nearby devices can detect.

**What you may notice:** Others can't find this PC for Nearby Sharing, and some phone-started pairing may not work. Paired devices and Swift Pair pop-ups for new accessories keep working.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\Bluetooth` → `AllowAdvertising` (DWORD) | `0` | removed |

### Disable Windows Media Player usage tracking

`misc.media-player` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Media Player stops sending usage data.

**What you may notice:** None. Playback works as before.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\MediaPlayer\Preferences` → `UsageTracking` (DWORD) | `0` | removed |

### Disable touch keyboard text suggestions

`input.touch-keyboard-predictions` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

The on-screen (touch) keyboard stops suggesting words as you type.

**What you may notice:** Only affects the touch keyboard: no word suggestions.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\TabletTip\1.7` → `EnableTextPrediction` (DWORD) | `0` | removed |

## Activity & Clipboard

### Disable activity history

`activity.history` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops Windows recording and uploading which apps, files and sites you use.

**What you may notice:** Cross-device 'pick up where you left off' stops working.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\System` → `EnableActivityFeed` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\System` → `PublishUserActivities` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\System` → `UploadUserActivities` (DWORD) | `0` | removed |

### Disable clipboard sync across devices

`activity.cloud-clipboard` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops copied text and images being uploaded to sync with your other devices.

**What you may notice:** Copy on one PC / paste on another no longer works.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\System` → `AllowCrossDeviceClipboard` (DWORD) | `0` | removed |

### Disable clipboard history

`activity.clipboard-history` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Windows stops keeping a list of everything you copy, so passwords, card numbers and confidential text you copied earlier can't be retrieved with Win+V by anyone using your unlocked PC.

**What you may notice:** Clipboard history is off by default in Windows; only people who turned on Win+V history notice. Normal copy and paste is unaffected.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Clipboard` → `EnableClipboardHistory` (DWORD) | `0` | removed |

### Turn off clipboard history for all users (locked)

`activity.clipboard-history-policy` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Disables Win+V clipboard history for every account on this PC and prevents turning it back on in Settings.

**What you may notice:** Nobody on this PC can use Win+V clipboard history.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\System` → `AllowClipboardHistory` (DWORD) | `0` | removed |

## App Permissions

### Block apps from reading account info

`apps.account-info` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Store apps can't read your name, picture and account details.

**What you may notice:** Some apps won't show your profile picture or name automatically.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\userAccountInformation` → `Value` (string) | `Deny` | `Allow` |

### Block apps from reading diagnostic info

`apps.diagnostics` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Store apps can't see diagnostic information about your other apps.

**What you may notice:** None.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\appDiagnostics` → `Value` (string) | `Deny` | `Allow` |

### Block apps from reading your notifications

`apps.notifications` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Apps can't read the notifications you receive from other apps (message previews, codes, emails).

**What you may notice:** Phone Link and smartwatch notification mirroring stop working. Apps can still show their own notifications.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\userNotificationListener` → `Value` (string) | `Deny` | `Allow` |

### Block apps from using Windows' built-in AI models

`apps.generative-ai` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account · AI feature

Apps can't use Windows' on-device generative AI features.

**What you may notice:** None, unless you use apps built on Windows' local AI. Cloud AI tools (Claude, ChatGPT) are unaffected.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\systemAIModels` → `Value` (string) | `Deny` | `Allow` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\generativeAI` → `Value` (string) | `Deny` | `Allow` |

### Block apps from eye tracking

`apps.eye-tracking` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Apps can't use eye-tracking hardware.

**What you may notice:** None on PCs without an eye tracker.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\gazeInput` → `Value` (string) | `Deny` | `Allow` |

### Block apps from your location

`apps.location` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Store apps can't request your location. (Turning location off for the whole PC is a separate setting.)

**What you may notice:** Weather, Maps and 'near me' features need a manually entered location. Store apps can no longer see Wi-Fi network names (Windows 11 24H2).

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\location` → `Value` (string) | `Deny` | `Allow` |

### Block apps from contacts

`apps.contacts` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Store apps can't read your contacts.

**What you may notice:** Mail, People and Phone Link can't show your contacts.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\contacts` → `Value` (string) | `Deny` | `Allow` |

### Block apps from calendar

`apps.calendar` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Store apps can't read your calendar.

**What you may notice:** Windows Calendar/Mail apps can't show appointments.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\appointments` → `Value` (string) | `Deny` | `Allow` |

### Block apps from email

`apps.email` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Store apps can't read or send your email.

**What you may notice:** Windows Mail app stops working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\email` → `Value` (string) | `Deny` | `Allow` |

### Block apps from phone calls, call history and messages

`apps.phone` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Store apps can't make calls or read your call history and text messages.

**What you may notice:** None beyond Phone Link, which Recommended turns off anyway.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\phoneCall` → `Value` (string) | `Deny` | `Allow` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\phoneCallHistory` → `Value` (string) | `Deny` | `Allow` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\chat` → `Value` (string) | `Deny` | `Allow` |

### Block apps from tasks

`apps.tasks` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Store apps can't read your task lists.

**What you may notice:** Microsoft To Do integration stops working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\userDataTasks` → `Value` (string) | `Deny` | `Allow` |

### Block Store apps from the camera

`apps.camera` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't use your camera.

**What you may notice:** Video calls in Teams, WhatsApp and the Camera app stop working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\webcam` → `Value` (string) | `Deny` | `Allow` |

### Block Store apps from the microphone

`apps.microphone` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't use your microphone.

**What you may notice:** Voice and video calls, voice recorder and dictation in Store apps stop working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\microphone` → `Value` (string) | `Deny` | `Allow` |

### Turn off the camera for the whole PC

`apps.camera-all` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

No program can use the camera: Store apps, desktop programs (Zoom, Discord, browsers) and Windows itself.

**What you may notice:** Video calls, the Camera app and webcam features stop working everywhere; Windows Hello face sign-in may stop working too.

- The app asks you to confirm before applying it.
- Also shown as applied when `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\webcam` → `Value` (string) is `Deny`.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Camera` → `AllowCamera` (DWORD) | `0` | removed |

### Turn off microphone access for the whole PC

`apps.microphone-all` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

No program can use the microphone: Store apps and desktop programs alike (Windows' 'Microphone access' switch).

**What you may notice:** Voice and video calls, voice messages, dictation and voice recording stop working everywhere.

- The app asks you to confirm before applying it.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\microphone` → `Value` (string) | `Deny` | `Allow` |

### Always show a border when apps capture your screen

`apps.capture-border` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Apps can't record your screen or windows without Windows showing a visible border.

**What you may notice:** None. You simply see when something is capturing.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\graphicsCaptureWithoutBorder` → `Value` (string) | `Deny` | `Allow` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\graphicsCaptureWithoutBorder\NonPackaged` → `Value` (string) | `Deny` | `Allow` |

### Block apps from unpaired devices

`apps.unpaired-devices` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Apps can't communicate with Bluetooth devices that aren't paired with your PC ('loosely coupled devices').

**What you may notice:** Rarely noticeable; some fitness or beacon apps may not find devices.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\bluetoothSync` → `Value` (string) | `Deny` | `Allow` |

### Block apps from reading your Downloads folder

`apps.downloads` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Store apps can't read your Downloads folder on their own.

**What you may notice:** Apps can still open downloads you pick in a file dialog.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\downloadsFolder` → `Value` (string) | `Deny` | `Allow` |

### Block apps from the entire file system

`apps.file-system` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't get broad access to all your files.

**What you may notice:** Store-based file managers and some backup apps stop working. Windows may switch this back on by itself.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\broadFileSystemAccess` → `Value` (string) | `Deny` | `Allow` |

### Block apps from Documents, Pictures, Videos and Music

`apps.libraries` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Store apps can't read your personal libraries on their own.

**What you may notice:** The Photos and Media Player apps can't show your pictures, videos or music library.

- The app asks you to confirm before applying it.
- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\documentsLibrary` → `Value` (string) | `Deny` | `Allow` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\picturesLibrary` → `Value` (string) | `Deny` | `Allow` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\videosLibrary` → `Value` (string) | `Deny` | `Allow` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\musicLibrary` → `Value` (string) | `Deny` | `Allow` |

### Block apps from presence sensing

`apps.presence` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Apps can't use sensors that detect whether you're in front of the PC.

**What you may notice:** None. Windows' own lock-on-leave and wake-on-approach keep working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\humanPresence` → `Value` (string) | `Deny` | `Allow` |

### Block apps from motion sensors

`apps.movement` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Apps can't read movement and activity sensors (accelerometer-based activity tracking).

**What you may notice:** None on most PCs.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\activity` → `Value` (string) | `Deny` | `Allow` |

### Block apps from listening for wake words

`apps.voice-activation` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Voice assistants can't listen for their activation keyword, including while the PC is locked.

**What you may notice:** None, unless you start an assistant by voice.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Speech_OneCore\Settings\VoiceActivation\UserPreferenceForAllApps` → `AgentActivationEnabled` (DWORD) | `0` | `1` |
| `HKCU\Software\Microsoft\Speech_OneCore\Settings\VoiceActivation\UserPreferenceForAllApps` → `AgentActivationOnLockScreenEnabled` (DWORD) | `0` | removed |

### Disable location override

`apps.location-override` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Apps can't use a location you entered manually as a substitute for your real location.

**What you may notice:** None for most people.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CPSS\Store\UserLocationOverridePrivacySetting` → `Value` (DWORD) | `0` | `1` |

### Block apps from controlling radios

`apps.radios` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Apps can't turn Wi-Fi, Bluetooth or mobile radios on and off.

**What you may notice:** Apps that manage Bluetooth or flight mode (e.g. device companion apps) can't switch radios.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\radios` → `Value` (string) | `Deny` | `Allow` |

### Block apps from capturing your screen

`apps.screen-capture` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

Apps (including desktop apps) can't capture your screen or windows on their own. Sharing a window you pick yourself still works.

**What you may notice:** Screen recorders, OBS window capture, remote-support tools and AI assistants that look at your screen may stop working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\graphicsCaptureProgrammatic` → `Value` (string) | `Deny` | `Allow` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\graphicsCaptureProgrammatic\NonPackaged` → `Value` (string) | `Deny` | `Allow` |

### Block apps from Bluetooth devices

`apps.bluetooth` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't communicate with paired Bluetooth devices.

**What you may notice:** Companion apps for headphones, fitness trackers, controllers and other Bluetooth devices stop working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\bluetooth` → `Value` (string) | `Deny` | `Allow` |

### Block apps from USB devices

`apps.usb` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't communicate directly with USB devices.

**What you may notice:** Store apps for USB hardware (e.g. device configurators, lab equipment) stop working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\usb` → `Value` (string) | `Deny` | `Allow` |

### Block apps from human interface devices

`apps.hid` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't access HID devices directly (special keyboards, game controllers, drawing tablets).

**What you may notice:** Store apps that configure or read special input devices stop working. Normal typing and mouse use are unaffected.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\humanInterfaceDevice` → `Value` (string) | `Deny` | `Allow` |

### Block apps from serial ports

`apps.serial` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't use serial (COM) ports.

**What you may notice:** Store apps for serial devices (e.g. microcontrollers, industrial equipment) stop working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\serialCommunication` → `Value` (string) | `Deny` | `Allow` |

### Block apps from custom sensors

`apps.custom-sensors` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't read custom hardware sensors.

**What you may notice:** Apps that rely on special sensors stop working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\sensors.custom` → `Value` (string) | `Deny` | `Allow` |

### Block apps from Wi-Fi information

`apps.wifi-info` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't read Wi-Fi network details.

**What you may notice:** Wi-Fi analyzers, some network or smart-home setup apps, and VPN apps' Wi-Fi-based features (e.g. auto-connect on untrusted Wi-Fi) stop working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\wifiData` → `Value` (string) | `Deny` | `Allow` |

### Block apps from Wi-Fi Direct

`apps.wifi-direct` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't create direct Wi-Fi connections to other devices.

**What you may notice:** Apps that connect directly to printers, cameras or phones over Wi-Fi Direct stop working.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\wiFiDirect` → `Value` (string) | `Deny` | `Allow` |

### Block apps from passkeys

`apps.passkeys` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Apps can't use or list the passkeys stored on this PC.

**What you may notice:** Signing in with passkeys in apps fails; you fall back to passwords.

- Also shown as applied when Windows has this off for the whole PC; unticking turns that back on.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\passkeys` → `Value` (string) | `Deny` | `Allow` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\passkeysEnumeration` → `Value` (string) | `Deny` | `Allow` |

### Stop all Store apps running in the background

`apps.background` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Store apps can't run, sync or receive updates while they're closed.

**What you may notice:** WhatsApp, Mail, Phone Link and similar apps stop receiving messages and notifications until opened.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\BackgroundAccessApplications` → `GlobalUserDisabled` (DWORD) | `1` | `0` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Search` → `BackgroundAppGlobalToggle` (DWORD) | `0` | removed |

### Turn off all app notifications

`apps.all-notifications` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

No app can show notifications (banners and notification center).

**What you may notice:** You won't see message alerts, reminders or warnings from any app.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\PushNotifications` → `ToastEnabled` (DWORD) | `0` | `1` |

### Disable SmartScreen for Store apps

`apps.store-smartscreen` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Stops checking web addresses used by Store apps against Microsoft's list of malicious sites (listed in some tools as 'sending URLs from apps to the Store').

**What you may notice:** SECURITY RISK: Store apps get no warning when loading known malicious web content.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\AppHost` → `EnableWebContentEvaluation` (DWORD) | `0` | `1` |

### Disable the default app for the headset button

`apps.headset-button` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Pressing the button on some headsets no longer launches the last-used voice app.

**What you may notice:** The headset button won't start a voice assistant.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Speech_OneCore\Settings\VoiceActivation\UserPreferenceForAllApps` → `AgentActivationLastUsed` (DWORD) | `0` | removed |

## Windows AI

### Disable Recall snapshots

`ai.recall` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC · AI feature

Stops Recall from saving screenshots of your activity (Copilot+ PCs).

**What you may notice:** Recall snapshots already saved on this PC are deleted. Undo can't bring them back.

- Only offered when Recall is installed.
- The app asks you to confirm before applying it.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Windows\WindowsAI` → `DisableAIDataAnalysis` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsAI` → `DisableAIDataAnalysis` (DWORD) | `1` | removed |

### Disable Click to Do

`ai.click-to-do` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Turns off the AI screen-analysis overlay on Copilot+ PCs.

**What you may notice:** None, unless you use Click to Do.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsAI` → `DisableClickToDo` (DWORD) | `1` | removed |

### Turn off the older Copilot pane and its taskbar button

`ai.copilot` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC · AI feature

Turns off the older Copilot built into Windows and hides its taskbar button. It doesn't stop the newer Copilot app; remove that on the Security & AI page.

**What you may notice:** The older Copilot is unavailable from the taskbar. Claude and ChatGPT are unaffected.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Windows\WindowsCopilot` → `TurnOffWindowsCopilot` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsCopilot` → `TurnOffWindowsCopilot` (DWORD) | `1` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `ShowCopilotButton` (DWORD) | `0` | removed |

### Don't offer Recall to any user

`ai.recall-availability` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Prevents Recall from being made available or turned on for any account on this PC (Copilot+ PCs).

**What you may notice:** Recall is removed from this PC after a restart, and snapshots already saved are deleted. Undo can't bring the snapshots back.

- Only offered when Recall is installed.
- The app asks you to confirm before applying it.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsAI` → `AllowRecallEnablement` (DWORD) | `0` | removed |

### Disable AI features in Paint

`ai.paint` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Turns off Image Creator, Cocreator and generative fill in Microsoft Paint.

**What you may notice:** Those AI tools disappear from Paint. Drawing and editing work as before.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Paint` → `DisableImageCreator` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Paint` → `DisableCocreator` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Paint` → `DisableGenerativeFill` (DWORD) | `1` | removed |

### Disable AI features in Notepad

`ai.notepad` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Turns off Notepad's AI rewrite, summarize and write features.

**What you may notice:** Those AI options disappear from Notepad.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\WindowsNotepad` → `DisableAIFeatures` (DWORD) | `1` | removed |

### Hide AI actions in File Explorer

`ai.explorer-actions` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Removes the 'AI actions' entries from the File Explorer right-click menu.

**What you may notice:** Those AI menu entries disappear.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Explorer` → `HideAIActionsMenu` (DWORD) | `1` | removed |

### Disable the AI agent in Settings

`ai.settings-agent` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Turns off the AI agent that changes settings from natural-language requests (Copilot+ PCs).

**What you may notice:** Settings search works as a normal search.

- Not offered on Windows Home or Pro, which don't follow it. If you already have it, it stays, marked as kept.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsAI` → `DisableSettingsAgent` (DWORD) | `1` | removed |

## Search

### Disable Bing web results in Start search

`search.web-results` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC · AI feature

Start menu searches stay on your PC instead of being sent to Bing.

**What you may notice:** No web results in Start search (usually faster).

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Windows\Explorer` → `DisableSearchBoxSuggestions` (DWORD) | `1` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Search` → `BingSearchEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Search` → `ConnectedSearchUseWeb` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Search` → `DisableWebSearch` (DWORD) | `1` | removed |

### Disable cloud content search and search history

`search.cloud-and-history` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC

Windows Search stops searching your OneDrive/Outlook cloud content and stops keeping search history.

**What you may notice:** Cloud files/emails no longer appear in Start search results.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SearchSettings` → `IsMSACloudSearchEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SearchSettings` → `IsAADCloudSearchEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SearchSettings` → `IsDeviceSearchHistoryEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Search` → `AllowCloudSearch` (DWORD) | `0` | removed |

### Disable Cortana

`search.cortana` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Turns off Cortana (discontinued) and its search integration.

**What you may notice:** None.

- Only offered when Cortana is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Windows Search` → `CortanaConsent` (DWORD) | `0` | removed |

### Disable search highlights

`search.highlights` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC · AI feature

Removes the trending content, illustrations and AI suggestions shown in the search box and search panel.

**What you may notice:** The search box no longer shows daily illustrations.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SearchSettings` → `IsDynamicSearchBoxEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Search` → `EnableDynamicContentInWSB` (DWORD) | `0` | removed |

## Start & Explorer

### Remove promotions from Start and File Explorer

`start.recommendations` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Removes tips/app promotions in Start, account nag notifications in Start, and OneDrive/Microsoft 365 ads in File Explorer.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `Start_IrisRecommendations` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `Start_AccountNotifications` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `ShowSyncProviderNotifications` (DWORD) | `0` | removed |

### Stop tracking app launches

`start.track-app-launches` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Windows stops recording which apps you open most.

**What you may notice:** Start no longer shows a 'Most used' list.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `Start_TrackProgs` (DWORD) | `0` | removed |

### Hide recently opened files

`start.recent-files` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Stops showing recent files in Start, Jump Lists and File Explorer.

**What you may notice:** Right-click taskbar recent-file lists and Start 'Recommended' files disappear.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `Start_TrackDocs` (DWORD) | `0` | removed |

### Hide Widgets on the taskbar

`start.widgets` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Removes the Widgets button and taskbar weather. Widgets itself stays on the PC: the panel can still open with Win+W, and lock screen widgets are a separate setting. To remove it, use Tools > Remove apps > Uninstall Widgets.

**What you may notice:** No Widgets button or taskbar weather. Recent Windows versions don't let apps change this; then turn Widgets off in Settings > Personalization > Taskbar.

- Windows protects this setting from apps on current versions; if it refuses, change it in Windows Settings (`ms-settings:taskbar`).
- Also shown as applied when `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `TaskbarDa` (DWORD) is `0`.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Dsh` → `AllowNewsAndInterests` (DWORD) | `0` | removed |

### Hide account notifications in Settings and the Spotlight desktop icon

`misc.account-notifications` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Removes Microsoft account nags in the Settings app and the 'Learn about this picture' desktop icon.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SystemSettings\AccountNotifications` → `EnableAccountNotifications` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\HideDesktopIcons\NewStartPanel` → `{2cc5ca98-6485-489a-920e-b3e88a6ccce3}` (DWORD) | `1` | removed |

### Hide the search box on the taskbar

`start.taskbar-search` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

Removes the search box/icon from the taskbar. Press Start and type to search.

**What you may notice:** No search box on the taskbar.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Search` → `SearchboxTaskbarMode` (DWORD) | `0` | `2` |

### Hide the Settings home page

`start.settings-home` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Settings opens on System instead of the home page, which mostly promotes OneDrive, Game Pass and Microsoft account features.

**What you may notice:** No Settings home page; all settings are still there.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer` → `SettingsPageVisibility` (string) | `hide:home` | removed |

### Show hidden files and folders

`explorer.hidden-files` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

File Explorer also shows files and folders marked as hidden (such as AppData), so nothing on your PC is out of sight. Protected Windows system files stay hidden.

**What you may notice:** Hidden files and folders appear, slightly faded, in File Explorer and on the desktop. File Explorer restarts to show them.

- Restarts File Explorer.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `Hidden` (DWORD) | `1` | `2` |

## Lock Screen

### Disable lock screen tips and fun facts

`lock.tips` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Removes promotional overlays on the lock screen.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `RotatingLockScreenOverlayEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `SubscribedContent-338387Enabled` (DWORD) | `0` | removed |

### Hide widgets on the lock screen

`lock.widgets` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

Removes weather and other widgets from the lock screen, for this account.

**What you may notice:** No widgets on the lock screen. You can also turn them on or off in Settings > Personalization > Lock screen.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Lock Screen` → `LockScreenWidgetsEnabled` (DWORD) | `0` | `1` |

### Hide notifications on the lock screen

`lock.notifications` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

People near your locked PC can't read your message previews.

**What you may notice:** You can't glance at notifications while locked.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Notifications\Settings` → `NOC_GLOBAL_SETTING_ALLOW_TOASTS_ABOVE_LOCK` (DWORD) | `0` | removed |

### Disable camera on the lock screen

`lock.camera` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

The camera can't be opened from the lock screen.

**What you may notice:** None for most users. Windows Hello face sign-in is unaffected.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Personalization` → `NoLockScreenCamera` (DWORD) | `1` | removed |

### Hide the password reveal button

`security.password-reveal` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Removes the 'eye' button that shows your typed password, protecting against shoulder-surfing.

**What you may notice:** You can't peek at the password you're typing.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\CredUI` → `DisablePasswordReveal` (DWORD) | `1` | removed |

### Disable biometrics

`security.biometrics` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Turns off all biometric features, including fingerprint and face recognition.

**What you may notice:** Windows Hello face and fingerprint sign-in stop working; you sign in with PIN or password.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Biometrics` → `Enabled` (DWORD) | `0` | removed |

### Disable Windows Spotlight on the lock screen

`lock.spotlight` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Turns off Spotlight's rotating Bing images and the content that comes with them on the lock screen. Spotlight as a desktop background is set separately in Settings > Personalization > Background.

**What you may notice:** Your lock screen shows a fixed picture instead of daily photos.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager` → `RotatingLockScreenEnabled` (DWORD) | `0` | `1` |

## Settings Sync

### Disable settings sync to your Microsoft account

`sync.all-settings` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Stops uploading themes, passwords, language and other settings to your Microsoft account.

**What you may notice:** Settings won't carry over to your other PCs or after a reinstall.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\SettingSync` → `DisableSettingSync` (DWORD) | `2` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\SettingSync` → `DisableSettingSyncUserOverride` (DWORD) | `1` | removed |

### Don't sync browser settings and passwords

`sync.browser-passwords` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Stops syncing browser settings and saved credentials to your Microsoft account; theme, language and other settings still sync.

**What you may notice:** Browser settings and Windows credentials won't carry over to your other PCs.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SettingSync\Groups\BrowserSettings` → `Enabled` (DWORD) | `0` | `1` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SettingSync\Groups\Credentials` → `Enabled` (DWORD) | `0` | `1` |

### Don't sync theme and design settings

`sync.design` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Wallpaper, colors and theme are no longer synced to your Microsoft account.

**What you may notice:** Your look won't carry over to other PCs.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SettingSync\Groups\Personalization` → `Enabled` (DWORD) | `0` | `1` |

### Don't sync language settings

`sync.language` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Language, keyboard and dictionary settings are no longer synced.

**What you may notice:** Language preferences won't carry over to other PCs.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SettingSync\Groups\Language` → `Enabled` (DWORD) | `0` | `1` |

### Don't sync accessibility settings

`sync.accessibility` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Accessibility settings are no longer synced.

**What you may notice:** Accessibility preferences won't carry over to other PCs.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SettingSync\Groups\Accessibility` → `Enabled` (DWORD) | `0` | `1` |

### Don't sync other Windows settings

`sync.windows-other` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Other Windows settings (such as File Explorer and mouse preferences) are no longer synced.

**What you may notice:** Those preferences won't carry over to other PCs.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\SettingSync\Groups\Windows` → `Enabled` (DWORD) | `0` | `1` |

## Telemetry & Diagnostics

### Reduce Windows diagnostic data to the minimum

`telemetry.policy` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Sets diagnostic data to the lowest level your edition allows, stops downloading telemetry configuration, limits diagnostic log collection and excludes your device name.

**What you may notice:** None. (Windows Home/Pro treat 'off' as 'Required'.)

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection` → `AllowTelemetry` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection` → `DisableOneSettingsDownloads` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection` → `LimitDiagnosticLogCollection` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection` → `AllowDeviceNameInTelemetry` (DWORD) | `0` | removed |

### Disable the telemetry service

`telemetry.service` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Disables 'Connected User Experiences and Telemetry' (DiagTrack), the service that uploads diagnostic data.

**What you may notice:** None for home users.

| Changes | Set to | Windows default |
|---|---|---|
| Service `DiagTrack` start type | Disabled (4) | Automatic (2) |

### Disable CEIP, app inventory and Steps Recorder

`telemetry.ceip-inventory` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Turns off the Customer Experience Improvement Program, the app inventory collector and the Steps Recorder.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\SQMClient\Windows` → `CEIPEnable` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\AppCompat` → `DisableInventory` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\AppCompat` → `AITEnable` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\AppCompat` → `DisableUAR` (DWORD) | `1` | removed |

### Disable handwriting data sharing

`telemetry.handwriting` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops sending handwriting samples and handwriting error reports to Microsoft.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\TabletPC` → `PreventHandwritingDataSharing` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\HandwritingErrorReports` → `PreventHandwritingErrorReports` (DWORD) | `1` | removed |

### Don't send error reports to Microsoft

`telemetry.error-reporting` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Crash reports (which can contain the app name, version and memory contents) are no longer created or sent to Microsoft. Crashes are still recorded on the PC (Event Viewer, Reliability Monitor) and no crash pop-ups appear.

**What you may notice:** Microsoft can't suggest fixes for crashes you experience.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Error Reporting` → `Disabled` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Error Reporting` → `DontShowUI` (DWORD) | `1` | removed |

### Don't report Malicious Software Removal Tool results

`telemetry.mrt-reporting` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

MRT still scans and removes malware, but stops reporting results to Microsoft.

**What you may notice:** None. Malware removal still works.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\MRT` → `DontReportInfectionInformation` (DWORD) | `1` | removed |

### Limit crash dump collection

`telemetry.crash-dumps` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Limits the memory dumps collected when apps crash; dumps can contain fragments of your data.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection` → `LimitDumpCollection` (DWORD) | `1` | removed |

## Location

### Disable location for the whole PC

`location.system` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Turns off Windows location services entirely.

**What you may notice:** Find My Device, automatic time zone and all location-based features stop working. Apps can no longer see Wi-Fi network names either (Windows 11 24H2), so VPN apps' auto-connect on untrusted Wi-Fi stops working.

- The app asks you to confirm before applying it.
- Also shown as applied when `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\location` → `Value` (string) is `Deny`.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\LocationAndSensors` → `DisableLocation` (DWORD) | `1` | removed |

### Disable automatic offline map updates

`location.maps` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops background downloads of offline map data.

**What you may notice:** Offline maps are not updated automatically.

- Only offered when Windows Maps is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Maps` → `AutoDownloadAndUpdateMapData` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Maps` → `AllowUntriggeredNetworkTrafficOnSettingsPage` (DWORD) | `0` | removed |

### Disable location sensors, scripting and the geolocation service

`location.sensors-service` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Turns off location/orientation sensors, script-based location lookups, the Windows location provider and the geolocation service.

**What you may notice:** Screen auto-rotation on tablets and all location features stop working.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\LocationAndSensors` → `DisableSensors` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\LocationAndSensors` → `DisableLocationScripting` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\LocationAndSensors` → `DisableWindowsLocationProvider` (DWORD) | `1` | removed |
| Service `lfsvc` start type | Disabled (4) | Manual (3) |
| `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Sensor\Overrides\{BFA794E4-F964-4FDB-90F6-51056BFE4B44}` → `SensorPermissionState` (DWORD) | `0` | `1` |

### Disable Find My Device

`location.find-my-device` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Stops the PC reporting its location to your Microsoft account for Find My Device.

**What you may notice:** You can't locate or lock this PC remotely if it's lost or stolen.

- The app asks you to confirm before applying it.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\FindMyDevice` → `AllowFindMyDevice` (DWORD) | `0` | removed |

## Windows Update

### Disable peer-to-peer update sharing

`update.p2p` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Updates download only from Microsoft, never uploaded to or from other PCs. Security updates keep working.

**What you may notice:** Multiple PCs at home each download updates separately.

- Also shown as applied when `HKU\S-1-5-20\Software\Microsoft\Windows\CurrentVersion\DeliveryOptimization\Settings` → `DownloadMode` (DWORD) is `0` and the policy below isn't set (Windows follows the policy when it is).

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\DeliveryOptimization` → `DODownloadMode` (DWORD) | `0` | removed |

### Don't auto-download manufacturer apps for devices

`update.device-metadata` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops Windows installing vendor apps and icons when you connect devices. Drivers still install.

**What you may notice:** Vendor companion apps must be installed manually if wanted.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Device Metadata` → `PreventDeviceMetadataFromNetwork` (DWORD) | `1` | removed |

### Disable speech model updates

`update.speech-models` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops background downloads of speech recognition/synthesis models.

**What you may notice:** Voice typing and Narrator voices won't receive improvements.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Speech` → `AllowSpeechModelUpdate` (DWORD) | `0` | removed |

### Don't get new updates as soon as they're available

`update.optional-updates` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Turns off 'Get the latest updates as soon as they're available', so non-security updates and new features arrive later. Security updates keep arriving as normal.

**What you may notice:** New features reach this PC later. Windows Home may ignore this policy.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate` → `AllowOptionalContent` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate` → `SetAllowOptionalContent` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings` → `IsContinuousInnovationOptedIn` (DWORD) | `0` | removed |

### Turn off automatic Windows Updates

`update.auto-updates-off` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Windows stops downloading and installing updates automatically; updates must be installed manually or by an IT-managed tool. For environments with managed update schedules.

**What you may notice:** SECURITY RISK: security fixes are not installed unless someone installs them. Windows Home may ignore this policy.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU` → `NoAutoUpdate` (DWORD) | `1` | removed |

### Ask before downloading Windows Updates

`update.notify-before-download` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Windows notifies you when updates are available and waits for you to download and install them.

**What you may notice:** Updates are delayed until you install them. Windows Home may ignore this policy.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU` → `AUOptions` (DWORD) | `2` | removed |

### Don't install drivers through Windows Update

`update.drivers-off` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Windows Update no longer installs or updates hardware drivers. For PCs whose drivers are managed by IT or the manufacturer.

**What you may notice:** New devices may lack drivers and driver fixes aren't installed automatically. Windows Home may ignore this policy.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate` → `ExcludeWUDriversInQualityUpdate` (DWORD) | `1` | removed |

### Turn off automatic Store app updates

`update.store-apps-off` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Microsoft Store apps are no longer updated automatically.

**What you may notice:** SECURITY RISK: app security fixes arrive only when updated manually in the Store.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\WindowsStore` → `AutoDownload` (DWORD) | `2` | removed |

### Don't update other Microsoft products through Windows Update

`update.other-products-off` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Turns off 'Receive updates for other Microsoft products' in Windows Update.

**What you may notice:** SECURITY RISK: Office and other Microsoft products need to be updated some other way.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings` → `AllowMUUpdateService` (DWORD) | `0` | removed |

### Delay feature updates by 6 months

`update.defer-feature` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Big yearly Windows feature updates arrive 180 days after release. Monthly security updates are not delayed.

**What you may notice:** New Windows features arrive later. Requires Windows Pro or higher.

- Not offered on Windows Home, which doesn't follow it. If you already have it, it stays, marked as kept.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate` → `DeferFeatureUpdates` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate` → `DeferFeatureUpdatesPeriodInDays` (DWORD) | `180` | removed |

### Disable dynamic configuration and feature experiments

`update.dynamic-config` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Limits Microsoft's feature experiments on this PC.

**What you may notice:** Some new features may arrive later or not at all.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\System` → `AllowExperimentation` (DWORD) | `0` | removed |

### Block device vendor auto-installers

`update.coinstallers` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Stops devices from installing their maker's extra software when plugged in (for example Razer Synapse). Drivers still install normally.

**What you may notice:** Extra device software (lighting, macros, control panels) has to be installed manually from the maker's website, for every device.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Device Installer` → `DisableCoInstallers` (DWORD) | `1` | `0` |

## Microsoft Edge

### Edge: reduce tracking and ad personalization

`edge.tracking` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Sends Do Not Track, stops sites checking for saved payment methods, and disables browsing-based ad personalization. Edge ignores part of this in a profile signed in with a personal Microsoft account.

**What you may notice:** None.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `ConfigureDoNotTrack` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `PaymentMethodQueryEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `PersonalizationReportingEnabled` (DWORD) | `0` | removed |

### Edge: disable diagnostic data and feedback

`edge.diagnostics-feedback` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops optional Edge diagnostic data and removes the feedback button.

**What you may notice:** None.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `DiagnosticData` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `UserFeedbackAllowed` (DWORD) | `0` | removed |

### Edge: remove shopping, rewards and promotions

`edge.promotions` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Disables the shopping assistant, Microsoft Rewards, first-run screens and in-browser recommendations. Edge ignores part of this in a profile signed in with a personal Microsoft account.

**What you may notice:** None. Edge looks and browses the same.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `EdgeShoppingAssistantEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `ShowMicrosoftRewards` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `HideFirstRunExperience` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `ShowRecommendationsEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `SpotlightExperiencesAndRecommendationsEnabled` (DWORD) | `0` | removed |

### Edge: remove sidebar and new-tab news feed

`edge.sidebar-newtab` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Removes the sidebar, the MSN news feed and sponsored tiles on new tabs. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** Edge looks different: plain new tab page, no sidebar.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `HubsSidebarEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `NewTabPageContentEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `NewTabPageHideDefaultTopSites` (DWORD) | `1` | removed |

### Edge: stop sending typos and page info to Microsoft

`edge.web-services` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Disables web services for navigation errors, similar-site suggestions, local-provider suggestions and visual search. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** None noticeable. SmartScreen protection stays on.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `ResolveNavigationErrorsUseWebService` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `AlternateErrorPagesEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `LocalProvidersEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `VisualSearchEnabled` (DWORD) | `0` | removed |

### Edge: don't store credit cards

`edge.card-autofill` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Edge stops saving and autofilling payment cards. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** You type card details manually.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `AutofillCreditCardEnabled` (DWORD) | `0` | removed |

### Edge: disable search suggestions

`edge.search-suggestions` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

What you type in the address bar is no longer sent to the search engine for suggestions. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** No search-engine suggestions while you type in the address bar; suggestions from your history and favorites remain.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `SearchSuggestEnabled` (DWORD) | `0` | removed |

### Edge: disable page preloading and startup boost

`edge.preload` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Edge no longer contacts sites you haven't visited and no longer runs in the background at startup. Edge ignores part of this in a profile signed in with a personal Microsoft account.

**What you may notice:** Pages and Edge itself may open slightly slower.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `NetworkPredictionOptions` (DWORD) | `2` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `StartupBoostEnabled` (DWORD) | `0` | removed |

### Edge: disable address/form autofill

`edge.form-autofill` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Edge stops saving and autofilling names, addresses and form entries. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** You fill forms manually. Saved passwords unaffected.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `AutofillAddressEnabled` (DWORD) | `0` | removed |

### Edge: disable AI themes and AI history search

`edge.ai-features` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Turns off AI-generated themes and AI-powered history search. In work or school profiles it also turns off Compose (AI writing) and the Microsoft 365 Copilot chat icon. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** Those AI features disappear from Edge.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `ComposeInlineEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `AIGenThemesEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `EdgeHistoryAISearchEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `Microsoft365CopilotChatIconEnabled` (DWORD) | `0` | removed |

### Edge: disable text prediction

`edge.text-prediction` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Edge stops suggesting word completions while you type in web forms. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** No inline word suggestions while typing.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `TextPredictionEnabled` (DWORD) | `0` | removed |

### Edge: disable enhanced (cloud) spell check

`edge.enhanced-spellcheck` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

What you type is no longer sent to Microsoft Editor for grammar and spelling suggestions. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** Basic spell check keeps working; grammar suggestions disappear.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `MicrosoftEditorProofingEnabled` (DWORD) | `0` | removed |

### Edge: disable SmartScreen

`edge.smartscreen` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Edge stops checking websites and downloads against Microsoft's list of phishing and malware sites.

**What you may notice:** SECURITY RISK: no warnings for phishing sites or malicious downloads in Edge.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `SmartScreenEnabled` (DWORD) | `0` | removed |

### Edge: disable the typosquatting checker

`edge.typosquatting` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Edge stops warning you when you visit a look-alike domain (e.g. 'gooogle.com').

**What you may notice:** SECURITY RISK: no warning for fake look-alike websites.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `TyposquattingCheckerEnabled` (DWORD) | `0` | removed |

### Edge: disable AI APIs, the on-device AI model and Bing Chat on new tabs

`edge.ai-integration` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Copilot can't read the page you're viewing (work or school profiles only), websites can't use Edge's built-in AI, Edge doesn't download its on-device AI model, and Bing Chat is removed from new tabs. Edge ignores part of this in a profile signed in with a personal Microsoft account.

**What you may notice:** None, unless you use Copilot inside Edge.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `CopilotPageContext` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `BuiltInAIAPIsEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `NewTabPageBingChatEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `GenAILocalFoundationalModelSettings` (DWORD) | `1` | removed |

### Edge: stop default-browser prompts and promotions

`edge.nags` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Removes 'make Edge your default' prompts and campaigns and the Adobe Acrobat subscription button. Edge ignores part of this in a profile signed in with a personal Microsoft account.

**What you may notice:** None.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `DefaultBrowserSettingsCampaignEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `DefaultBrowserSettingEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `ShowAcrobatSubscriptionButton` (DWORD) | `0` | removed |

### Edge: don't sign in from Microsoft websites

`edge.implicit-signin` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Signing in to a Microsoft website no longer signs Edge itself in automatically.

**What you may notice:** None; you can still sign in to Edge manually.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `WebToBrowserSignInEnabled` (DWORD) | `0` | removed |

### Edge: disable cloud-based tab services

`edge.tab-services` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops sending tab information to Microsoft for cloud tab features such as tab organization suggestions. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** Cloud tab suggestions disappear.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `TabServicesEnabled` (DWORD) | `0` | removed |

### Edge: don't save passwords

`edge.passwords` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Edge stops offering to save and fill passwords. Recommended if you use a separate password manager. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** Passwords saved in Edge are no longer filled in automatically.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `PasswordManagerEnabled` (DWORD) | `0` | removed |

### Edge: disable signing in to the browser

`edge.browser-signin` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Removes the Microsoft account sign-in button; Edge can't be signed in to a Microsoft account.

**What you may notice:** Edge sync (favorites, passwords, history across devices) stops working.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `BrowserSignin` (DWORD) | `0` | removed |

### Edge: block ads, trackers and cookie banners (uBlock Origin Lite)

`edge.ublock` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Installs uBlock Origin Lite from the Edge Add-ons store: a free, open-source blocker that stops ads, trackers and known malware sites on web pages. Its cookie-notice list is switched on too, which hides cookie banners without clicking Accept, so nothing is agreed to. It runs inside Edge and sends nothing anywhere. Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** Ads disappear on most sites; a few sites ask you to turn off ad blocking. You can switch the extension off on the Extensions page; undo removes it.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `ExtensionSettings` (string) | adds `{"cimighlppcgcoapaliogpjjdehbnofhn":{"installation_mode":"normal_installed","update_url":"https://edge.microsoft.com/extensionwebstorebase/v1/crx"}}` | only these entries removed |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge\3rdparty\extensions\cimighlppcgcoapaliogpjjdehbnofhn\policy` → `rulesets` (string) | `["+annoyances-cookies"]` | removed; key removed if empty |
| `HKLM\SOFTWARE\Policies\Microsoft\Edge\3rdparty\extensions\cimighlppcgcoapaliogpjjdehbnofhn\policy` → `disableFirstRunPage` (DWORD) | `1` | removed; key removed if empty |

### Edge: strict tracking prevention

`edge.tracking-strict` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Sets Edge's built-in tracking prevention to Strict, which blocks most trackers across sites (the default is Balanced). Edge ignores this in a profile signed in with a personal Microsoft account.

**What you may notice:** Some sites may not work fully: embedded videos, social sign-in buttons or comment sections can be blocked.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `TrackingPrevention` (DWORD) | `3` | removed |

### Edge: block third-party cookies

`edge.third-party-cookies` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Websites can't set cookies for other companies (ad networks, trackers) that follow you from site to site.

**What you may notice:** Rarely, a sign-in that uses another company's site (some shops, embedded payment or chat) may need an exception.

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `BlockThirdPartyCookies` (DWORD) | `1` | removed |

## Microsoft Office

### Office: minimize telemetry

`office.telemetry` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Sets Office diagnostic data to 'Neither' and turns off the older telemetry and customer-experience options. Required service data is still sent.

**What you may notice:** None. Only matters if Microsoft Office is installed.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Office\Common\ClientTelemetry` → `SendTelemetry` (DWORD) | `3` | removed |
| `HKCU\Software\Policies\Microsoft\Office\Common\ClientTelemetry` → `DisableTelemetry` (DWORD) | `1` | removed |
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common` → `QMEnable` (DWORD) | `0` | removed |
| `HKCU\Software\Policies\Microsoft\Office\16.0\OSM` → `EnableLogging` (DWORD) | `0` | removed |
| `HKCU\Software\Policies\Microsoft\Office\16.0\OSM` → `EnableUpload` (DWORD) | `0` | removed |
| `HKCU\Software\Policies\Microsoft\Office\16.0\OSM` → `EnableFileObfuscation` (DWORD) | `1` | removed |

### Office: disable surveys and feedback

`office.feedback` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Removes Office survey pop-ups and in-app feedback.

**What you may notice:** You can't send feedback from inside Office.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common\Feedback` → `SurveyEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common\Feedback` → `Enabled` (DWORD) | `0` | removed |

### Office: hide LinkedIn features

`office.linkedin` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Removes LinkedIn profile cards and Resume Assistant.

**What you may notice:** No LinkedIn info in Outlook/Word.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common` → `LinkedIn` (DWORD) | `0` | removed |

### Office: disable optional connected experiences

`office.optional-connected` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Turns off optional cloud extras. Core cloud features (AutoSave, co-authoring, Designer) keep working.

**What you may notice:** Minor extras like LinkedIn-powered features disappear.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common\Privacy` → `ControllerConnectedServicesEnabled` (DWORD) | `2` | removed |

### Office: skip first-run screens

`office.first-run` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Hides the Office welcome movie and the privacy opt-in screen shown on first start.

**What you may notice:** None.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Office\16.0\FirstRun` → `DisableMovie` (DWORD) | `1` | removed |
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common\Privacy` → `ShownFirstRunOptin` (DWORD) | `1` | removed |
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common\General` → `ShownFirstRunOptin` (DWORD) | `1` | removed |

### Office: disable experiences that analyze your content

`office.content-analytics` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Stops Office sending document content to Microsoft for cloud analysis.

**What you may notice:** Designer, Editor suggestions, Translator and Dictation stop working in Office.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common\Privacy` → `UserContentDisabled` (DWORD) | `2` | removed |

### Outlook: disable text predictions

`office.outlook-prediction` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Outlook stops suggesting how to finish your sentences while you write emails.

**What you may notice:** No grey word suggestions while typing emails.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Office\16.0\Common\MailSettings` → `InlineTextPrediction` (DWORD) | `0` | removed |

### Office: turn off automatic updates

`office.updates-off` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Microsoft 365 / Office stops updating itself. For environments where IT deploys Office updates.

**What you may notice:** SECURITY RISK: Office security fixes are not installed automatically.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Office\16.0\Common\OfficeUpdate` → `EnableAutomaticUpdates` (DWORD) | `0` | removed |

### Office: turn off all connected (cloud) experiences

`office.all-connected` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

Disables every Office feature that uses Microsoft's cloud services.

**What you may notice:** AutoSave, co-authoring, OneDrive in Office, Designer, Translator, Dictation and online help stop working.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common\Privacy` → `DisconnectedState` (DWORD) | `2` | removed |

### Office: don't download online content

`office.online-content` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Office stops downloading online templates, pictures, icons and other content.

**What you may notice:** No online templates, stock images or icons in Office.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common\Privacy` → `DownloadContentDisabled` (DWORD) | `2` | removed |

### Office: block signing in

`office.signin-off` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: each account

Office can't be signed in to a Microsoft or work account.

**What you may notice:** Microsoft 365 subscriptions can't activate; OneDrive and SharePoint aren't available in Office. Suitable only for volume-licensed Office.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Policies\Microsoft\Office\16.0\Common\SignIn` → `SignInOptions` (DWORD) | `3` | removed |

### Outlook: stay on classic Outlook

`office.classic-outlook` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account

Hides the 'Try the new Outlook' switch and stops Outlook moving you to the new version automatically. The new Outlook copies the login details of your other email accounts (Gmail, IMAP) to Microsoft's cloud.

**What you may notice:** None. You can still install the new Outlook yourself.

- Only offered when Microsoft Office is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Office\16.0\Outlook\Options\General` → `HideNewOutlookToggle` (DWORD) | `1` | removed |
| `HKCU\Software\Policies\Microsoft\Office\16.0\Outlook\Options\General` → `DoNewOutlookAutoMigration` (DWORD) | `0` | removed |
| `HKCU\Software\Policies\Microsoft\Office\16.0\Outlook\Preferences` → `NewOutlookMigrationUserSetting` (DWORD) | `0` | removed |

## Google Chrome

### Chrome: disable browsing data collection and feedback

`chrome.telemetry` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops 'make searches and browsing better' URL collection and in-browser feedback. (Chrome only lets companies turn off usage statistics by policy; home users can switch it off in Chrome's settings.)

**What you may notice:** None.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `UrlKeyedAnonymizedDataCollectionEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `UserFeedbackAllowed` (DWORD) | `0` | removed |

### Chrome: turn off in-browser ad tracking (Privacy Sandbox)

`chrome.ad-privacy` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Disables ad topics, site-suggested ads and ad measurement that Chrome shares with advertisers, and hides the prompt about them.

**What you may notice:** None. Ads you see are less personalized.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `PrivacySandboxAdTopicsEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `PrivacySandboxSiteEnabledAdsEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `PrivacySandboxAdMeasurementEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `PrivacySandboxPromptEnabled` (DWORD) | `0` | removed |

### Chrome: stop sending typos, typing and payment checks to Google

`chrome.web-services` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Disables Google's web service for navigation errors, cloud-based enhanced spell check, and sites checking for saved payment methods.

**What you may notice:** None noticeable. Basic spell check and Safe Browsing keep working.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `AlternateErrorPagesEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `SpellCheckServiceEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `PaymentMethodQueryEnabled` (DWORD) | `0` | removed |

### Chrome: block third-party cookies

`chrome.third-party-cookies` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops cross-site tracking cookies.

**What you may notice:** Some embedded content or 'sign in with' buttons on other sites may not work.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `BlockThirdPartyCookies` (DWORD) | `1` | removed |

### Chrome: disable search suggestions

`chrome.search-suggestions` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

What you type in the address bar is no longer sent to the search engine for suggestions.

**What you may notice:** No search-engine suggestions while you type in the address bar; suggestions from your history and favorites remain.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `SearchSuggestEnabled` (DWORD) | `0` | removed |

### Chrome: disable page preloading and background running

`chrome.preload-background` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Chrome no longer contacts sites you haven't visited and fully closes when you close it.

**What you may notice:** Pages may load slightly slower; Chrome apps/notifications stop when Chrome is closed.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `NetworkPredictionOptions` (DWORD) | `2` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `BackgroundModeEnabled` (DWORD) | `0` | removed |

### Chrome: disable built-in AI features

`chrome.ai-features` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Turns off Chrome's AI features: Help me write, AI history search, AI themes and Tab compare.

**What you may notice:** Those AI features disappear. Claude/ChatGPT websites are unaffected.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `HelpMeWriteSettings` (DWORD) | `2` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `HistorySearchSettings` (DWORD) | `2` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `CreateThemesSettings` (DWORD) | `2` | removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `TabCompareSettings` (DWORD) | `2` | removed |

### Chrome: don't store credit cards

`chrome.card-autofill` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Chrome stops saving and autofilling payment cards.

**What you may notice:** You type card details manually.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `AutofillCreditCardEnabled` (DWORD) | `0` | removed |

### Chrome: disable address/form autofill

`chrome.form-autofill` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Chrome stops saving and autofilling names, addresses and form entries.

**What you may notice:** You fill forms manually. Saved passwords unaffected.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `AutofillAddressEnabled` (DWORD) | `0` | removed |

### Chrome: block ads, trackers and cookie banners (uBlock Origin Lite)

`chrome.ublock` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Installs uBlock Origin Lite from the Chrome Web Store: a free, open-source blocker that stops ads, trackers and known malware sites on web pages. Its cookie-notice list is switched on too, which hides cookie banners without clicking Accept, so nothing is agreed to. It runs inside Chrome and sends nothing anywhere.

**What you may notice:** Ads disappear on most sites; a few sites ask you to turn off ad blocking. You can switch the extension off on the Extensions page; undo removes it.

- Only offered when Google Chrome is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Google\Chrome` → `ExtensionSettings` (string) | adds `{"ddkjiahejlhfcafbddmgiahcphecmpfh":{"installation_mode":"normal_installed","update_url":"https://clients2.google.com/service/update2/crx"}}` | only these entries removed |
| `HKLM\SOFTWARE\Policies\Google\Chrome\3rdparty\extensions\ddkjiahejlhfcafbddmgiahcphecmpfh\policy` → `rulesets` (string) | `["+annoyances-cookies"]` | removed; key removed if empty |
| `HKLM\SOFTWARE\Policies\Google\Chrome\3rdparty\extensions\ddkjiahejlhfcafbddmgiahcphecmpfh\policy` → `disableFirstRunPage` (DWORD) | `1` | removed; key removed if empty |

## Brave Browser

### Brave: disable usage analytics and pings

`brave.telemetry` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Turns off Brave's privacy-preserving analytics (P3A), daily usage ping, Web Discovery Project and crash/usage reporting.

**What you may notice:** None.

- Only offered when Brave is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `BraveP3AEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `BraveStatsPingEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `BraveWebDiscoveryEnabled` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `MetricsReportingEnabled` (DWORD) | `0` | removed |

### Brave: stop sites checking for saved payment methods

`brave.web-services` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Websites can no longer ask Brave whether you have payment cards saved.

**What you may notice:** None.

- Only offered when Brave is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `PaymentMethodQueryEnabled` (DWORD) | `0` | removed |

### Brave: remove Rewards, Wallet and VPN

`brave.crypto-vpn` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Removes Brave Rewards (BAT ads), the crypto Wallet and the paid Brave VPN.

**What you may notice:** Those features and their toolbar buttons disappear; earned BAT stays in your account.

- Only offered when Brave is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `BraveRewardsDisabled` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `BraveWalletDisabled` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `BraveVPNDisabled` (DWORD) | `1` | removed |

### Brave: disable Leo AI assistant

`brave.leo-ai` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC · AI feature

Removes the Leo AI chat assistant.

**What you may notice:** Leo is no longer available in Brave.

- Only offered when Brave is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `BraveAIChatEnabled` (DWORD) | `0` | removed |

### Brave: remove Brave News and Brave Talk

`brave.news-talk` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Removes the news feed on new tabs and the Brave Talk video-call feature.

**What you may notice:** Plain new tab page; Brave Talk unavailable.

- Only offered when Brave is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `BraveNewsDisabled` (DWORD) | `1` | removed |
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `BraveTalkDisabled` (DWORD) | `1` | removed |

### Brave: disable search suggestions

`brave.search-suggestions` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

What you type in the address bar is no longer sent to the search engine for suggestions.

**What you may notice:** No search-engine suggestions while you type in the address bar; suggestions from your history and favorites remain.

- Only offered when Brave is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `SearchSuggestEnabled` (DWORD) | `0` | removed |

### Brave: don't store credit cards

`brave.card-autofill` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Brave stops saving and autofilling payment cards.

**What you may notice:** You type card details manually.

- Only offered when Brave is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `AutofillCreditCardEnabled` (DWORD) | `0` | removed |

### Brave: disable address/form autofill

`brave.form-autofill` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Brave stops saving and autofilling names, addresses and form entries.

**What you may notice:** You fill forms manually. Saved passwords unaffected.

- Only offered when Brave is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\BraveSoftware\Brave` → `AutofillAddressEnabled` (DWORD) | `0` | removed |

## Network & Remote Access

### Disable Remote Assistance

`remote.assistance` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Turns off the legacy Remote Assistance feature so no one can be invited to control this PC through it.

**What you may notice:** None for most people. Quick Assist keeps working.

- Also shown as applied when `HKLM\SYSTEM\CurrentControlSet\Control\Remote Assistance` → `fAllowToGetHelp` (DWORD) is `0`.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Terminal Services` → `fAllowToGetHelp` (DWORD) | `0` | removed |

### Block Remote Desktop connections to this PC

`remote.desktop` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Prevents anyone connecting to this PC with Remote Desktop (Windows Pro and higher).

**What you may notice:** You can't remote into this PC with Remote Desktop. Connecting from it to others still works.

- Not offered on Windows Home, which doesn't follow it. If you already have it, it stays, marked as kept.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server` → `fDenyTSConnections` (DWORD) | `1` | `1` |

### Disable the internet connection check (NCSI)

`network.ncsi` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Windows stops contacting Microsoft servers to test whether you're online.

**What you may notice:** Windows may show 'No internet' while online; Store, Office, Wi-Fi login pages and some apps may act as if offline.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\NetworkConnectivityStatusIndicator` → `NoActiveProbe` (DWORD) | `1` | removed |

### Disable online activation ticket (KMS)

`network.kms-online` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Stops Windows sending activation data online for KMS client activation.

**What you may notice:** Can cause activation problems on work/school PCs or after hardware changes.

- Not offered on Windows Home, which doesn't follow it. If you already have it, it stays, marked as kept.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows NT\CurrentVersion\Software Protection Platform` → `NoGenTicket` (DWORD) | `1` | removed |

### Lock Teredo off by policy

`network.teredo` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Windows already keeps Teredo off by default; this also blocks turning it back on. Teredo is an IPv6 tunnel through IPv4 that can get around firewalls and network protections.

**What you may notice:** Some online games (e.g. Xbox party chat and multiplayer) may report 'Teredo unable to qualify' and have connection problems.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\TCPIP\v6Transition` → `Teredo_State` (string) | `Disabled` | removed |

## Gaming

### Disable Xbox Game Bar recording (Game DVR)

`gaming.game-dvr` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account and whole PC

Turns off background game recording and captures.

**What you may notice:** Win+G recording and 'record what happened' stop working.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\GameDVR` → `AllowGameDVR` (DWORD) | `0` | removed |
| `HKCU\System\GameConfigStore` → `GameDVR_Enabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\GameDVR` → `AppCaptureEnabled` (DWORD) | `0` | removed |

## Legacy (Windows 10)

### Old Edge: don't preload in the background

`legacy.edge-background` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Stops the pre-Chromium Edge from launching and preloading tabs in the background.

**What you may notice:** Only affects the old Edge on Windows 10; no effect on Windows 11.

- Only offered when the old Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\MicrosoftEdge\Main` → `AllowPrelaunch` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Policies\Microsoft\MicrosoftEdge\TabPreloader` → `AllowTabPreloading` (DWORD) | `0` | removed |

### Old Edge: disable address bar suggestions

`legacy.edge-address-bar` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Turns off the address bar drop-down in the pre-Chromium Edge.

**What you may notice:** Only affects the old Edge on Windows 10; no effect on Windows 11.

- Only offered when the old Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\Browser` → `AllowAddressBarDropdown` (DWORD) | `0` | removed |

### Disable the Edge bar

`legacy.edge-bar` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Turns off the floating Edge search bar on the desktop.

**What you may notice:** The Edge bar is no longer available (it was retired by Microsoft).

- Only offered when Microsoft Edge is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Edge` → `WebWidgetAllowed` (DWORD) | `0` | removed |

### Hide People and 'Meet Now' on the taskbar

`legacy.people-meet-now` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Removes the People icon and the Skype 'Meet Now' button from the Windows 10 taskbar.

**What you may notice:** Only affects Windows 10; no effect on Windows 11.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced\People` → `PeopleBand` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer` → `HideSCAMeetNow` (DWORD) | `1` | removed |

### Disable Cortana above the lock screen

`legacy.cortana-lock` · Rating: Trade-off · Preset: Enhanced · Applies to: whole PC

Prevents Cortana from being used while the PC is locked.

**What you may notice:** Only affects Windows 10 with Cortana; no effect on Windows 11.

- Only offered when Cortana is installed.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Search` → `AllowCortanaAboveLock` (DWORD) | `0` | removed |

## Mobile Devices

### Disable Phone Link and phone-to-PC linking

`mobile.phone-link` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: each account and whole PC

Prevents linking your phone to this PC through Phone Link and related suggestions.

**What you may notice:** Phone Link (texts, calls, photos from your phone) stops working.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\System` → `EnableMmx` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Mobility` → `CrossDeviceEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Mobility` → `PhoneLinkEnabled` (DWORD) | `0` | removed |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Mobility` → `OptedIn` (DWORD) | `0` | removed |

## OneDrive

### OneDrive: no network traffic before sign-in

`onedrive.pre-login` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

OneDrive doesn't connect to the internet until a user has signed in.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\OneDrive` → `PreventNetworkTrafficPreUserSignIn` (DWORD) | `1` | removed |

### Disable OneDrive

`onedrive.disable` · Rating: Not recommended · Preset: none (Advanced settings only) · Applies to: whole PC

Prevents OneDrive from syncing files on this PC.

**What you may notice:** OneDrive sync stops. Files that are only in the cloud stay there; check your Desktop/Documents aren't cloud-only first.

- The app asks you to confirm before applying it.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\OneDrive` → `DisableFileSyncNGSC` (DWORD) | `1` | removed |

## Hardware & Connectivity

### Disable NFC and the payments service

`hw.nfc` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Turns off the Payments and NFC/SE Manager service, so the PC's NFC chip can't be used.

**What you may notice:** Tap-to-pair, tap-to-pay and other NFC features stop working.

| Changes | Set to | Windows default |
|---|---|---|
| Service `SEMgrSvc` start type | Disabled (4) | Manual (3) |

### Disable wireless display (Miracast)

`hw.wireless-display` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Blocks projecting this PC's screen to TVs and wireless displays, and projecting other devices to this PC.

**What you may notice:** Screen casting to TVs/projectors over Miracast and 'Project to this PC' stop working.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\Windows\Connect` → `AllowProjectionToPC` (DWORD) | `0` | removed |
| `HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\WirelessDisplay` → `AllowProjectionFromPC` (DWORD) | `0` | removed |

### Disable mobile broadband (cellular)

`hw.mobile-broadband` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Turns off the WWAN AutoConfig service used by built-in LTE/5G modems and USB mobile-broadband sticks.

**What you may notice:** Cellular data connections stop working.

| Changes | Set to | Windows default |
|---|---|---|
| Service `WwanSvc` start type | Disabled (4) | Manual (3) |

### Disable Wi-Fi Direct

`hw.wifi-direct` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Turns off the Wi-Fi Direct Services Connection Manager, used for direct device-to-device Wi-Fi connections.

**What you may notice:** Wi-Fi Direct printers, some casting and nearby-sharing features stop working.

| Changes | Set to | Windows default |
|---|---|---|
| Service `WFDSConMgrSvc` start type | Disabled (4) | Manual (3) |

### Restrict Bluetooth pairing (not discoverable)

`hw.bluetooth-discoverable` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Other devices can no longer discover this PC over Bluetooth. You can still pair devices from this PC.

**What you may notice:** Devices that need to find the PC themselves (e.g. some phones) can't start pairing.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\Bluetooth` → `AllowDiscoverableMode` (DWORD) | `0` | removed |

### Block internet access for Windows Media DRM

`hw.drm-online` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Windows Media Digital Rights Management can no longer go online to acquire or update licenses.

**What you may notice:** Protected media in the legacy Windows Media Player can't get licenses. Streaming services are unaffected.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SOFTWARE\Policies\Microsoft\WMDRM` → `DisableOnline` (DWORD) | `1` | removed |

## Security

### Block software installed from the PC's firmware (WPBT)

`security.wpbt` · Rating: Recommended · Preset: Recommended and Enhanced · Applies to: whole PC

Stops Windows from running programs that the PC maker placed in the firmware (Windows Platform Binary Table). Some makers use it to install their own apps, often with telemetry, even on a fresh Windows install.

**What you may notice:** None for most PCs. PC-maker tools that install themselves this way (e.g. some 'Armoury Crate' or anti-theft agents) are no longer installed automatically.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SYSTEM\CurrentControlSet\Control\Session Manager` → `DisableWpbtExecution` (DWORD) | `1` | removed |

### Show file extensions

`security.file-extensions` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Shows the end of file names (.pdf, .exe, .docx) in File Explorer, so fake files like 'invoice.pdf.exe' are easy to spot.

**What you may notice:** File names show their extension. File Explorer restarts to show it.

- Restarts File Explorer.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `HideFileExt` (DWORD) | `0` | `1` |

## Usability

### Classic right-click menu

`usability.classic-context-menu` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

Brings back the full right-click menu from Windows 10 instead of the shortened Windows 11 menu with 'Show more options'.

**What you may notice:** Right-click menus look like Windows 10. File Explorer restarts to show it.

- Restarts File Explorer.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32` → `(Default)` (string) | empty text | removed; key removed if empty |

### Open File Explorer to 'This PC'

`usability.explorer-this-pc` · Rating: Trade-off · Preset: Enhanced · Applies to: each account

File Explorer opens on your drives instead of Home, which lists your recently opened files and cloud files for anyone who glances at the screen.

**What you may notice:** File Explorer opens on This PC. Home is still in the left pane.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `LaunchTo` (DWORD) | `1` | removed |

### End Task on taskbar right-click

`usability.end-task` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

Adds 'End task' to the right-click menu of taskbar apps, to close a frozen app without Task Manager.

**What you may notice:** None.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced\TaskbarDeveloperSettings` → `TaskbarEndTask` (DWORD) | `1` | removed |

### Hide Gallery in File Explorer

`usability.hide-gallery` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

Removes Gallery (a photo timeline of your Pictures folders) from the File Explorer navigation pane.

**What you may notice:** No Gallery in File Explorer; your photos stay in Pictures. File Explorer restarts to show it.

- Restarts File Explorer.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Classes\CLSID\{e88865ea-0e1c-4e20-9aa6-edcd0212c87c}` → `System.IsPinnedToNameSpaceTree` (DWORD) | `0` | removed; key removed if empty |

## Performance

### Turn off hibernation

`performance.hibernation` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Turns off hibernation and removes it from the power menu, freeing the disk space of the hibernation file (often several GB).

**What you may notice:** No hibernation, and Fast Startup is turned off with it (start-up may take a few seconds longer). Laptops lose the option to save work when the battery runs out. Takes effect after a restart.

| Changes | Set to | Windows default |
|---|---|---|
| `HKLM\SYSTEM\CurrentControlSet\Control\Power` → `HibernateEnabled` (DWORD) | `0` | `1` |
| `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FlyoutMenuSettings` → `ShowHibernateOption` (DWORD) | `0` | removed |

### Visual effects: best performance

`performance.visual-effects` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

Turns off animations, shadows, window contents while dragging and other effects, like 'Adjust for best performance' in System Properties.

**What you may notice:** Windows looks plainer: no animations, fades or shadows. Takes effect after signing out.

- Also shown as applied when `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffects` → `VisualFXSetting` (DWORD) is `2`.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffects` → `VisualFXSetting` (DWORD) | `3` | removed |
| `HKCU\Control Panel\Desktop` → `UserPreferencesMask` (binary) | `144 18 3 128 16 0 0 0` | `158 30 7 128 18 0 0 0` |
| `HKCU\Control Panel\Desktop` → `DragFullWindows` (string) | `0` | `1` |
| `HKCU\Control Panel\Desktop` → `MenuShowDelay` (string) | `200` | `400` |
| `HKCU\Control Panel\Desktop\WindowMetrics` → `MinAnimate` (string) | `0` | `1` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `ListviewAlphaSelect` (DWORD) | `0` | `1` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `ListviewShadow` (DWORD) | `0` | `1` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` → `TaskbarAnimations` (DWORD) | `0` | `1` |
| `HKCU\Software\Microsoft\Windows\DWM` → `EnableAeroPeek` (DWORD) | `0` | `1` |

### Turn off Storage Sense

`performance.storage-sense-off` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

Stops Windows from automatically deleting temporary files, old Recycle Bin items and unused cloud files in the background.

**What you may notice:** Temporary files are no longer cleaned up automatically; use the clean-up tools on the Tools page instead.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Microsoft\Windows\CurrentVersion\StorageSense\Parameters\StoragePolicy` → `01` (DWORD) | `0` | removed |

### Turn off automatic folder type detection

`performance.folder-discovery` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: each account

File Explorer stops guessing each folder's type (pictures, music, documents), which can make large folders slow to open.

**What you may notice:** New folders open in the general view. Folder views you already customized stay as they are. Takes effect after signing out.

| Changes | Set to | Windows default |
|---|---|---|
| `HKCU\Software\Classes\Local Settings\Software\Microsoft\Windows\Shell\Bags\AllFolders\Shell` → `FolderType` (string) | `NotSpecified` | removed; key removed if empty |

### Start Maps and Storage services only when needed

`performance.background-services` · Rating: Trade-off · Preset: none (Advanced settings only) · Applies to: whole PC

Sets the Downloaded Maps Manager and Storage Service to start only when an app needs them, instead of at every start-up.

**What you may notice:** None noticeable; the services still start when used.

| Changes | Set to | Windows default |
|---|---|---|
| Service `MapsBroker` start type | Manual (3) | Automatic (2) |
| Service `StorSvc` start type | Manual (3) | Automatic (2) |

## Tools

One-time jobs on the Tools page. They aren't settings: no preset runs them and they aren't reapplied after
Windows updates. Each run is recorded in History.

### Uninstall OneDrive

`remove.onedrive` · Remove apps · can be undone (Reinstall)

Removes the OneDrive app with its own uninstaller. Your files in the OneDrive folder stay on this PC.

**Before you run it:** Files that are only in the cloud (cloud icon in File Explorer) won't be on this PC afterwards: right-click the OneDrive folder and choose 'Always keep on this device' first. Syncing stops.

### Uninstall Microsoft Edge

`remove.edge` · Remove apps · can be undone (Reinstall)

Removes the Edge browser with its own uninstaller. Your Edge profile (favourites, passwords) is kept, and apps that show web pages inside them keep working (WebView2 stays).

**Before you run it:** Set another browser as default first. Windows Update may reinstall Edge later. Outside the EU, Microsoft doesn't officially support uninstalling Edge.

### Delete Edge browsing data

`remove.edge-data` · Remove apps · can't be undone

Deletes your Edge profile on this PC: favourites, saved passwords, history, cookies and autofill data. Use it after uninstalling Edge, or to start Edge fresh.

**Before you run it:** This can't be undone. If you're switching browsers, import your favourites and passwords into the new browser first. Data synced to your Microsoft account stays in the cloud.

### Uninstall Widgets

`remove.widgets` · Remove apps · can be undone (Reinstall)

Removes the Widgets board (news, weather, stocks) for all accounts, instead of only turning it off.

**Before you run it:** The Widgets button and board disappear. Reinstall from the Microsoft Store if you want them back.

### Delete temporary files

`cleanup.temp` · Clean up · can't be undone

Deletes files in your Temp folder and Windows' Temp folder. Files that are in use are skipped.

**Before you run it:** Close open apps first; an app's unsaved recovery files may be stored in Temp.

### Run Disk Cleanup

`cleanup.disk` · Clean up · can't be undone

Runs Windows Disk Cleanup for drive C: (temporary files, update caches, thumbnails, error reports, old Windows installations).

**Before you run it:** Your Downloads folder and Recycle Bin are left alone. Removing an old Windows installation means you can't go back to it.

### Remove replaced Windows update files

`cleanup.update-files` · Clean up · can't be undone

Removes old versions of Windows components that updates have replaced, which can free several GB.

**Before you run it:** Installed updates can no longer be uninstalled afterwards. Takes 5–30 minutes.

### Turn off reserved storage

`cleanup.reserved-storage` · Clean up · can be undone (Turn on)

Frees the space (about 7 GB) Windows keeps aside for updates, temporary files and caches.

**Before you run it:** If the disk is nearly full, big Windows updates may fail until you free space yourself.

### Ultimate Performance power plan

`performance.ultimate-plan` · Performance · can be undone (Turn off)

Adds and switches to Windows' Ultimate Performance power plan, which keeps the processor ready at all times.

**Before you run it:** Uses more power and makes the PC warmer; not for laptops on battery.

