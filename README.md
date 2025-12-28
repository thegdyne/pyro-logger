# Pyro Logger App

Progressive Web App (PWA) and native iOS/Android app for logging pyrotechnic work experience.

## Features

- 📱 **Progressive Web App** - Install directly from browser, works offline
- 🍎 **Native iOS** - Full App Store distribution via Capacitor
- 🤖 **Native Android** - Full Play Store distribution via Capacitor
- 📄 **PDF Generation** - Creates official Joint Industry SFX grading forms
- 💾 **Local Storage** - All entries saved on device
- 🔒 **Offline First** - Works without internet after first load

## Quick Start (PWA - Recommended)

### Option 1: Serve Locally

```bash
# Install dependencies
npm install

# Serve the app
npm run serve

# Open http://localhost:3000 in browser
```

### Option 2: Deploy to Web

Upload the `www/` folder to any static hosting:
- GitHub Pages
- Netlify
- Vercel
- Any web server

### Installing the PWA

1. Open the app in Chrome, Safari, or Edge
2. Look for "Add to Home Screen" or "Install" prompt
3. The app will work offline after installation

## Native App Development

### Requirements

- **iOS**: macOS with Xcode 15+
- **Android**: Android Studio with SDK 33+
- Node.js 18+

### Building Native Apps

```bash
# Install dependencies
npm install

# Add platforms
npx cap add ios      # Requires macOS + Xcode
npx cap add android  # Requires Android Studio

# Sync web files to native projects
npx cap sync

# Open in IDE
npx cap open ios     # Opens Xcode
npx cap open android # Opens Android Studio
```

### iOS Distribution

1. `npx cap open ios`
2. In Xcode: Select your team in Signing & Capabilities
3. Select a device/simulator
4. Press Play (⌘R)

To distribute:
- Product → Archive → Distribute App

### Android Distribution

1. `npx cap open android`
2. Build → Generate Signed Bundle/APK
3. Follow wizard to create keystore and build

## Project Structure

```
pyro-logger-app/
├── www/
│   ├── index.html          # Main app (single-file)
│   ├── manifest.json       # PWA manifest
│   ├── service-worker.js   # Offline caching
│   └── icons/              # App icons (all sizes)
├── capacitor.config.json   # Native app config
├── package.json
└── README.md
```

## PWA Features

The PWA includes:

- **Manifest** - Proper app metadata for installation
- **Service Worker** - Caches app and jsPDF for offline use
- **Icons** - All sizes for iOS, Android, Windows
- **Standalone Mode** - Runs like a native app

### Testing PWA

Use Chrome DevTools:
1. Open DevTools (F12)
2. Go to Application tab
3. Check Manifest and Service Worker sections
4. Use Lighthouse to audit PWA compliance

## Updating the App

1. Edit `www/index.html`
2. Update version in `service-worker.js` cache name
3. For native: run `npx cap sync` and rebuild

## App Store Submission Notes

**iOS App Store:**
- Bundle ID: `com.pyrologger.app`
- Requires screenshots (6.5" and 5.5" iPhone)
- Requires privacy policy URL

**Google Play:**
- Package: `com.pyrologger.app`
- Requires feature graphic (1024x500)
- Content rating questionnaire

## Offline Support

The PWA service worker automatically caches:
- The main HTML app
- All app icons
- jsPDF library from CDN

After first load, everything works offline.
