# Resume Builder

This is a static site and is ready to deploy with Firebase Hosting.

Use the **Edit JSON** tab to edit the current resume data directly. The preview updates as soon as the JSON becomes valid; incomplete or invalid edits leave the last valid preview in place and show the parsing issue.

## Google sign-in and Drive saving

The app can save one `resume-builder.json` file per signed-in Google account and load it after Google sign-in. It requests only the Google Drive [`drive.file`](https://developers.google.com/drive/api/guides/api-specific-auth) scope, so it can access files the app creates rather than the user's whole Drive.

1. In Firebase Console, create a Web app and enable **Authentication > Sign-in method > Google**.
2. In the Google Cloud project linked to Firebase, enable the **Google Drive API**.
3. Copy the Web app configuration from Firebase Console > Project settings > Your apps into `firebaseConfig` in [public/index.html](public/index.html).
4. Add your deployed site URL to Firebase Authentication's Authorized domains.

Firebase keeps the user's sign-in session locally. The app also retains the short-lived Google Drive access token in the current browser session, so refreshing the page automatically reloads the saved resume while that token remains valid. If the token expires, is rejected, or the browser session ends, the app returns to **Sign in with Google**. Until a Drive file exists, the app leaves the current sample JSON in place.

## Deploy

1. Install the project dependencies (once): `yarn install`
2. Sign in: `yarn firebase login`
3. Create or select a Firebase project in the [Firebase console](https://console.firebase.google.com/).
4. From this directory, deploy with your Firebase project ID:

   ```sh
   yarn deploy --project YOUR_PROJECT_ID
   ```

The Hosting configuration publishes `index.html` from the repository root. It deliberately does not include a `.firebaserc` file, so a project ID is never accidentally committed; add one locally with `yarn firebase use --add` if you prefer a default project. Once selected, deployment is simply `yarn deploy`.
