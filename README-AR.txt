# MedGuard-JO

Bilingual Arabic/English medication safety PWA starter for Jordan.

## Included
- Responsive app interface and navigation
- Email/password authentication via Firebase Authentication
- Firestore collections for medications, symptoms, and daily checks
- PWA manifest, service worker, and app icons
- Emergency call link to 911

## 1. Configure Firebase
1. Create a Firebase project at https://console.firebase.google.com/
2. Add a Web app to the Firebase project.
3. Copy the Firebase web configuration.
4. Open `app.js` and replace the placeholder values in `firebaseConfig`.
5. In Firebase Authentication, enable Email/Password sign-in.
6. Create a Firestore database.
7. Publish the following starter rules (review and strengthen before production):

```text
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## 2. Publish
Upload the contents of this folder to a GitHub repository, enable GitHub Pages from the `main` branch and `/ (root)`, then open the published HTTPS URL.

## Important limitations before real-world use
- This is a working starter, not a clinically validated medical device.
- Medication reminders are not yet scheduled as reliable background notifications. Reliable push reminders require Firebase Cloud Messaging setup and platform-specific testing; browser support varies.
- Caregiver mode currently explains safe account use; delegated caregiver permissions and sharing need a separate secure implementation.
- Do not store highly sensitive medical data until privacy, consent, security rules, and applicable Jordanian legal requirements have been reviewed.
- The emergency link opens the phone dialer; it does not automatically contact emergency services.
- The app does not provide diagnosis or treatment advice. Emergency guidance must be clinically reviewed before release.
