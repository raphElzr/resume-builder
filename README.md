# Resume Builder

This is a static site and is ready to deploy with Firebase Hosting.

Use the **Edit JSON** tab to edit the current resume data directly. The preview updates as soon as the JSON becomes valid; incomplete or invalid edits leave the last valid preview in place and show the parsing issue.

## Deploy

1. Install the project dependencies (once): `yarn install`
2. Sign in: `yarn firebase login`
3. Create or select a Firebase project in the [Firebase console](https://console.firebase.google.com/).
4. From this directory, deploy with your Firebase project ID:

   ```sh
   yarn deploy --project YOUR_PROJECT_ID
   ```

The Hosting configuration publishes `index.html` from the repository root. It deliberately does not include a `.firebaserc` file, so a project ID is never accidentally committed; add one locally with `yarn firebase use --add` if you prefer a default project. Once selected, deployment is simply `yarn deploy`.
