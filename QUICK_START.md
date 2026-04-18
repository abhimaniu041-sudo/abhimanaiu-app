# Abhimaniu App - Quick Start Guide

## Running the App

### Development Mode

1. **Start Expo Dev Server:**
   ```bash
   cd /app/abhimaniu-app
   npm start
   ```

2. **Run on Android Device/Emulator:**
   ```bash
   npm run android
   ```

3. **Scan QR Code:**
   - Install Expo Go app on your Android device
   - Scan the QR code from terminal
   - App will load on your device

### Testing the App

#### Login Flow
1. Open app
2. Enter access key: `ABHI2026`
3. Tap "Login"
4. Should navigate to main screen

#### Import Profile
1. Tap "Import File (.zip)"
2. Select any ZIP file (preferably named MOD1-5.zip)
3. File name should appear below button
4. "Imported Profile" section should appear

#### Enable Profile
1. In "Imported Profile" section
2. Toggle "Enable Imported Profile" to ON
3. Border should turn pink
4. Status should show "✓ Profile Ready" in green
5. Run button should change to "Run BGMI with Profile"

#### Graphics Settings
1. Toggle any graphics setting (Smooth, HDR, Extreme FPS, Anti-Lag)
2. Settings should persist after app restart

#### Settings & Login Duration
1. Tap settings icon (⚙️) in top right
2. Select different login duration
3. Check "Key expires in" shows correct time
4. Tap "Logout" to return to login screen

#### BGMI Launch
1. Tap "Run BGMI with Profile" or "Run Game"
2. If BGMI installed: Game should launch
3. If BGMI not installed: Should show error message

## Default Credentials

**Access Key:** `ABHI2026`

## Features Checklist

- ✅ Login with access key
- ✅ Login duration options (1hr, 1day, 7days, 30days, never)
- ✅ Session expiry tracking
- ✅ Import ZIP files
- ✅ Enable/Disable imported profile
- ✅ Profile status indicators
- ✅ Graphics settings toggles
- ✅ RAM & Storage progress bars
- ✅ BGMI launch integration
- ✅ Settings screen
- ✅ Logout functionality
- ✅ Goku GFX UI theme
- ✅ Local storage (AsyncStorage)
- ✅ Floating overlay UI (in-app draggable)

## Known Limitations

### Floating Overlay
The current implementation provides a **draggable in-app overlay** rather than a true system-level overlay that stays on top of BGMI. 

**Why?** True system overlays require:
- Native Android code (Java/Kotlin)
- `SYSTEM_ALERT_WINDOW` permission handling
- Service implementation
- Ejecting from Expo managed workflow

**Current Implementation:**
- Draggable overlay within the app
- Can be minimized to bubble
- Works perfectly for demonstration
- Full graphics controls

**To Implement True System Overlay:**
1. Eject from Expo: `expo eject`
2. Write native Android module for overlay service
3. Implement WindowManager with TYPE_APPLICATION_OVERLAY
4. Handle lifecycle and permissions

### Profile Injection
The app **does not inject or modify BGMI files**. The "Enable Profile" toggle is a visual indicator only. True profile injection would require:
- Root access or BGMI modification
- File system access to BGMI directory
- Understanding of BGMI's file structure
- Risk of ban from game

Current implementation focuses on **safe, non-intrusive profile management** for reference purposes.

## Building Production APK

### Using Expo Build Service

1. **Configure app.json** (already done)

2. **Build APK:**
   ```bash
   expo build:android -t apk
   ```

3. **Download APK** when ready

### Using EAS Build (Recommended)

1. **Install EAS CLI:**
   ```bash
   npm install -g eas-cli
   ```

2. **Configure EAS:**
   ```bash
   eas build:configure
   ```

3. **Build APK:**
   ```bash
   eas build --platform android --profile preview
   ```

## File Structure

```
abhimaniu-app/
├── App.js                    # Main navigation setup
├── app.json                  # Expo & Android config
├── package.json             # Dependencies
├── babel.config.js          # Babel configuration
│
├── src/
│   ├── screens/
│   │   ├── LoginScreen.js        # Access key login
│   │   ├── MainScreen.js         # Main interface
│   │   ├── SettingsScreen.js     # Settings & logout
│   │   └── FloatingOverlay.js    # Draggable overlay
│   │
│   ├── components/
│   │   ├── Card.js              # Styled card
│   │   ├── Button.js            # Custom button
│   │   └── ToggleSwitch.js      # Toggle component
│   │
│   ├── utils/
│   │   ├── storage.js           # AsyncStorage helpers
│   │   └── constants.js         # Colors & constants
│   │
│   └── services/
│       └── bgmiLauncher.js      # BGMI launch logic
│
└── assets/                   # Icons & images
```

## Customization

### Change Access Key
Edit: `src/utils/constants.js`
```javascript
export const DEFAULT_ACCESS_KEY = 'YOUR_KEY_HERE';
```

### Change Theme Colors
Edit: `src/utils/constants.js`
```javascript
export const COLORS = {
  background: '#000000',      // Black
  cardBackground: '#FFFFFF',  // White
  cardBorder: '#FF1493',      // Deep Pink
  primary: '#FF1493',         // Deep Pink
  // ... customize as needed
};
```

### Change App Name
Edit: `app.json`
```json
{
  "expo": {
    "name": "Your App Name",
    "slug": "your-app-name"
  }
}
```

## Troubleshooting

### Metro Bundler Issues
```bash
cd /app/abhimaniu-app
rm -rf node_modules
npm install
npm start -- --reset-cache
```

### Android Build Errors
```bash
cd android
./gradlew clean
cd ..
npm run android
```

### Navigation Errors
- Ensure `react-native-gesture-handler` is imported in App.js
- Check babel config includes reanimated plugin

### Storage Not Persisting
- Check AsyncStorage is properly imported
- Verify async/await is used correctly
- Check device storage permissions

## Next Steps

1. Test all features thoroughly
2. Add custom icon and splash screen images
3. Build production APK
4. Test on multiple Android versions
5. Consider ejecting for native features if needed

## Support

For questions or issues:
- Check README.md for detailed documentation
- Review code comments in source files
- Test on physical Android device for best results

---

**Ready to launch Abhimaniu! 🚀**
