# Test Series

A ThreeUI-powered Test Series library with access-code volumes and a Firebase-backed catalogue/admin studio.

## Run it

```sh
npm install
npm run dev
```

## Firebase setup

1. Create a Firebase web app and copy the `.env.example` file to `.env.local`.
2. Paste the Firebase web configuration values into `.env.local`.
3. In Firebase Authentication, enable **Email/Password** and create the administrator account for `visheshjog863@gmail.com` using the password you provided. The password is deliberately not stored in source control or bundled into the browser.
4. Create a Firestore database, then deploy the included rules with `firebase deploy --only firestore:rules` (or paste [firestore.rules](./firestore.rules) into the Firestore Rules editor).

## Firebase Hosting deployment

The Firebase “Site Not Found” screen is resolved by deploying the production build, not the source directory. The project now includes the required Hosting configuration in [firebase.json](./firebase.json): it publishes `dist` and rewrites every route to `index.html`.

1. Replace `YOUR_FIREBASE_PROJECT_ID` in [.firebaserc.example](./.firebaserc.example), then save it as `.firebaserc`.
2. Run `npx firebase login` if this computer is not already authenticated.
3. Run `npm run deploy`.

For a Hosting-only release, use `npm run deploy:hosting`. Once complete, Firebase prints the live `https://<project-id>.web.app` URL.

Books are stored in the `books` collection. Visitors can read the catalogue; only the configured Firebase account can create, edit, or remove books. Before Firebase is configured, the catalogue uses browser-local seed data so the public browsing and code flow still work.

## Admin access

Select **Admin**, or click the `TS TEST SERIES` logo five times. Sign in through Firebase, then use the Admin Studio at the bottom of the page to add, change, or remove books and their access codes.

## Registered ThreeUI source

The supplied canonical files are kept in the project without modification:

- `src/shaders/ashen-press/sources/ashen-press.html` — SHA-256 `5fe2554e578acac5d55cb466a9564440e7767e38797981f8e829dfd2de0bc90f`
- `src/shaders/ashen-press/AshenPress.tsx` — SHA-256 `36b365f7a69223f1c3347bfcb3f2d1aa1ab20d30f2c31e5efb248e62ab4ddc90`
- `public/landing-pages/complete-shelf-v2.html` — SHA-256 `606f200fed8602c243f40a11c8c364f0e625c57f80e7c97dc76419da207f198e`

The local component wrapper serves the canonical Working Volumes HTML inside an iframe, preserving its authored Three.js r165 presentation. AshenPress uses the exact registered wrapper and canonical source document.
