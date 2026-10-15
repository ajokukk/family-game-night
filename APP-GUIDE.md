# Turning Naija Game Night into an installable app

Everything here lives in one GitHub repository: the game page, the install files, and an automatic Android build.

## 1. Put it online (free)
1. Create a GitHub repository (for example `family-game-night`).
2. Upload **all** the files in this folder, keeping the `icons` and `.github` folders.
3. Settings > Pages > Deploy from a branch > `main` / root > Save.
4. Your game is live at `https://<username>.github.io/family-game-night/`.

## 2. Install it on phones (no store needed)
- **Android:** open the link in Chrome > menu > *Install app* (or *Add to Home screen*).
- **iPhone:** open the link in **Safari** > Share > *Add to Home Screen*.
It then opens full screen with the dice icon. Players still need internet.

## 3. Get an Android APK (no Android Studio needed)
1. In the repository open the **Actions** tab > *Build Android APK* > *Run workflow*.
2. After a few minutes open the finished run and download **family-game-night-apk**. Unzip it to get `app-debug.apk`.
3. Send the APK to family on WhatsApp. They tap it and allow "install from this source".
   This is a debug build for sharing among people you trust. A Google Play release needs a signed build and a $25 one-time developer account.

## 4. iPhone App Store (only if you want it there)
Needs a Mac with Xcode and an Apple Developer account ($99/year). On the Mac: `npm install`, `mkdir www && cp -r index.html manifest.webmanifest sw.js icons www/`, `npm i @capacitor/ios`, `npx cap add ios`, `npx cap open ios`. Installing from the home screen (step 2) gives iPhone users nearly the same thing for free.

## Playing with people anywhere
Players connect through free public MQTT brokers over secure WebSockets, so it works from any country. If rooms ever fail to open, a broker is down; try again. For something more dependable later, point the app at your own broker (for example HiveMQ Cloud's free plan).
