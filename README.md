# Abhimaniu - BGMI Profile Manager

A React Native Expo mobile application for managing BGMI (Battlegrounds Mobile India) profiles with advanced graphics settings and a floating overlay.

## Features

### 🔐 Login System
- Secure access key authentication (Default: `ABHI2026`)
- Configurable login duration options:
  - 1 Hour
  - 1 Day
  - 7 Days (Default)
  - 30 Days
  - Never Expire
- Session tracking with remaining time display
- Local storage for offline functionality

### 📁 Profile Management
- Import ZIP files (MOD1.zip - MOD5.zip)
- Enable/Disable imported profiles
- Visual profile status indicators
- Profile-specific BGMI launch

### 🎮 Graphics Settings
- Smooth Graphics toggle
- HDR Mode toggle
- Extreme FPS toggle
- Anti-Lag toggle
- Settings persist across sessions

### 🚀 BGMI Integration
- One-tap BGMI launch
- Profile-aware game launching
- Automatic BGMI detection
- Error handling for missing installation

### 📱 Floating Overlay
- Draggable overlay panel
- Stays on top during gameplay
- Minimize to bubble mode
- Quick access to graphics settings
- Hide/Close/Run Game controls

### 💾 Local Storage
- All data stored locally using AsyncStorage
- Secure credential storage with expo-secure-store
- No internet connection required
- Offline-first architecture

### 🎨 Goku GFX UI Theme
- Black background
- White cards with pink borders
- Pink buttons and switches
- Circular logo design
- RAM and Storage progress indicators
- Rounded corners with shadows

## Installation

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- Expo CLI
- Android device or emulator

### Setup

1. Install dependencies:
```bash
cd abhimaniu-app
npm install
```

2. Start the development server:
```bash
npm start
```

3. Run on Android:
```bash
npm run android
```

## Project Structure

```
abhimaniu-app/
├── App.js                          # Main app entry with navigation
├── app.json                        # Expo configuration
├── src/
│   ├── screens/
│   │   ├── LoginScreen.js         # Login with access key
│   │   ├── MainScreen.js          # Main app interface
│   │   ├── SettingsScreen.js      # Settings & logout
│   │   └── FloatingOverlay.js     # Draggable overlay panel
│   ├── components/
│   │   ├── Card.js                # Styled card component
│   │   ├── Button.js              # Custom button
│   │   └── ToggleSwitch.js        # Toggle switch component
│   ├── utils/
│   │   ├── storage.js             # AsyncStorage utilities
│   │   └── constants.js           # App constants & colors
│   └── services/
│       └── bgmiLauncher.js        # BGMI launch service
└── assets/                         # App icons & images
```

## Usage

### First Time Setup

1. Launch the app
2. Enter the access key: `ABHI2026`
3. Tap "Login"

### Importing Profiles

1. From the main screen, tap "Import File (.zip)"
2. Select a supported ZIP file (MOD1-5.zip)
3. The profile will be saved and displayed

### Enabling Profiles

1. After importing, locate the "Imported Profile" section
2. Toggle "Enable Imported Profile" to ON
3. Profile status shows "✓ Profile Ready"
4. Run button changes to "Run BGMI with Profile"

### Changing Login Duration

1. Open Settings (gear icon)
2. Select desired duration option
3. Remaining time updates automatically

### Using Floating Overlay

1. Launch overlay from main screen
2. Drag to reposition
3. Toggle graphics settings
4. Use "Hide" to minimize to bubble
5. Use "Close" to stop overlay service
6. Use "Run Game" to launch BGMI

## Configuration

### Default Access Key
Located in: `src/utils/constants.js`
```javascript
export const DEFAULT_ACCESS_KEY = 'ABHI2026';
```

### BGMI Package Name
Located in: `src/utils/constants.js`
```javascript
export const BGMI_PACKAGE_NAME = 'com.pubg.imobile';
```

### Colors (Goku GFX Theme)
Located in: `src/utils/constants.js`
```javascript
export const COLORS = {
  background: '#000000',
  cardBackground: '#FFFFFF',
  cardBorder: '#FF1493',
  primary: '#FF1493',
  // ... more colors
};
```

## Permissions

The app requests the following Android permissions:
- `READ_EXTERNAL_STORAGE` - For importing ZIP files
- `WRITE_EXTERNAL_STORAGE` - For file management
- `SYSTEM_ALERT_WINDOW` - For floating overlay

## Important Notes

### Profile Management
- ZIP files are not injected into BGMI
- No BGMI files are modified
- Profiles are stored locally for reference only
- Launching with profile enabled shows visual indicator

### Floating Overlay
- True system overlay requires native Android code
- Current implementation shows draggable in-app overlay
- For system-wide overlay, app needs to be ejected from Expo

### Storage
- All data stored locally on device
- No cloud sync or backup
- Uninstalling app removes all data

## Building for Production

### Create APK

1. Configure app signing in `app.json`
2. Build APK:
```bash
expo build:android -t apk
```

### Create AAB (for Play Store)

```bash
expo build:android -t app-bundle
```

## Troubleshooting

### BGMI Won't Launch
- Ensure BGMI is installed
- Check package name is correct
- Verify app has necessary permissions

### Import File Not Working
- Check file format (.zip only)
- Ensure file name matches MOD1-5.zip pattern
- Verify storage permissions granted

### Login Expired
- Check Settings for remaining time
- Adjust login duration in Settings
- Re-login with access key

## Version

Current Version: **1.0.0**

## Support

For issues or questions, please check the app settings or contact support.

---

**App Name**: Abhimaniu  
**Package**: com.abhimaniu.app  
**Platform**: Android (React Native Expo)
