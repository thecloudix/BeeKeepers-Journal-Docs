# Privacy Policy — Beekeeper's Journal

**Effective date:** May 15, 2026
**App:** Beekeeper's Journal (Android)
**Developer:** Christopher Wood (plainsightlogic@gmail.com)
**Published version:** This document is the source of truth. The publicly hosted copy lives at <https://thecloudix.github.io/BeeKeepers-Journal-Privacy/> and is synced from this file.

This policy describes how Beekeeper's Journal (the "app") handles your information.

## Short version

Beekeeper's Journal stores your hive records on your device. The app makes no analytics, advertising, or third-party tracking calls. There are no user accounts.

The app **does** make a small number of well-defined network requests: downloading OpenStreetMap map tiles when you choose to drop a pin on a map, and calling the device's built-in geocoder when you ask it to look up an address or use your current location. Those are the only network calls the app makes. Records, photos, and hive locations stay on your device.

## What the app stores on your device

The following information is stored in the app's private storage area on your Android device. Other apps cannot read it.

- **Hive records** — names, notes, and (optionally) location coordinates and an address label for each hive
- **Inspection records** — dates, observations, weather, brood and queen status, free-text notes, and any photos you attach
- **Harvest records** — dates, amounts, types, and notes
- **Hive location** — for any hive where you've explicitly chosen to drop a pin: latitude, longitude, and a human-readable address label
- **Photos** — copied into the app's private file directory when you attach them to an inspection
- **Theme preference** — your chosen Light / Dark / System / Honey / Material You setting

## What the app does NOT collect or transmit

- No name, email, phone number, or account information
- No analytics, crash reporting, advertising IDs, or behavioral tracking
- Your hive records, inspection notes, harvest records, photos, and locations are **never transmitted off your device**
- No third-party SDKs that touch user data

## Network requests the app makes

The app is offline-first. The only network requests it makes are:

1. **OpenStreetMap tile downloads.** When you tap "Pick on a map" on a hive's settings screen, the app downloads map tile images from `tile.openstreetmap.org`. Each request is a standard HTTP request that includes the app's package name as the User-Agent. No personal data, hive data, or location data is sent — these are anonymous tile fetches.
2. **Android device geocoder.** When you tap "Use my current location" or "Look up address" on a hive's settings screen, the app calls Android's built-in `Geocoder` API. On most devices this is handled by Google Play Services or a vendor-specific service. The app does not control where that traffic is sent — it is governed by your device-level privacy settings and the OEM's policies.

The app does not make any other network requests. There are no analytics, no crash reporting, no remote sync, no advertising calls, and no proactive contact with any backend.

## Permissions

| Permission | When requested | Why |
|---|---|---|
| **Photo library access** (system photo picker) | When you tap "Add photo" on an inspection | Lets you choose a photo to attach. The app receives only the photo you explicitly select. No background access to your library. |
| **Camera** | Requested at runtime, only when you tap "Scan hive QR" on the home screen | Lets you scan a hive's printed QR label to jump straight to its detail page. Images from the camera are processed on the device by the bundled ZXing decoder to read a single QR code — no frames, photos, or video are saved or transmitted. You can deny the permission and the rest of the app works unchanged. |
| **INTERNET** | Granted automatically at install | Needed to download OpenStreetMap tiles when you open a map picker. |
| **ACCESS_NETWORK_STATE** | Granted automatically at install | Needed by the map library to detect connectivity for tile loading. |
| **ACCESS_FINE_LOCATION** / **ACCESS_COARSE_LOCATION** | Requested at runtime, only when you tap "Use my current location" on a hive's settings page | Reads the device's last-known location to drop a pin for that hive. The location is stored locally with the hive record and is never transmitted. |
| **POST_NOTIFICATIONS** | Requested at runtime on Android 13+ | Lets the app deliver local reminder notifications for the treatment doses and next-inspection dates you've scheduled. The notification content is generated entirely on your device from your own records; no network call is involved and nothing is sent anywhere. You can deny or revoke this permission at any time in Android Settings → Apps → Beekeeper's Journal → Notifications. |

## Local notifications

The app schedules two kinds of local reminders on your device using Android's WorkManager:

1. **Treatment-dose reminders** — when you start a multi-dose disease treatment, each upcoming dose's scheduled date is queued; the device shows a notification on that day reminding you to confirm or cancel the dose.
2. **Next-inspection reminders** — when you set a "Next inspection" date on a hive's settings screen, the device shows a notification on that day reminding you to inspect the hive.

In both cases the reminder text is generated locally from your own hive and protocol records — no data leaves your device, no remote service is contacted, and no notification is delivered through any push service (Firebase Cloud Messaging or otherwise). If you deny the POST_NOTIFICATIONS permission on Android 13+, the schedules are still kept locally but no banner is shown; pending treatment doses remain visible in the "Upcoming treatments" screen, and the next-inspection date remains visible in the hive's settings.

## Children

The app is not directed at children under 13. Because the app does not collect personally identifying information from anyone, no information is collected from children.

## Data retention and deletion

You control retention completely:

- **Delete a hive's location** with the "Clear location" button on that hive's settings page
- **Delete an individual inspection or harvest** via the overflow menu on its card or the delete icon on its detail screen
- **Clear all app data** via Android **Settings → Apps → Beekeeper's Journal → Storage → Clear data**
- **Uninstall the app** to permanently remove all hives, inspections, harvests, photos, locations, and preferences

When you uninstall the app or clear its data, everything stored locally is gone — there is no remote copy because no data is ever transmitted.

## Backups

Android's standard auto-backup feature may include this app's data in your Google account backup if you have that turned on at the system level. This is controlled by Android, not by the app, and is governed by Google's privacy policy. You can disable Android backup for this app in **Settings → System → Backup**.

## Third-party components

The app uses [osmdroid](https://github.com/osmdroid/osmdroid), an open-source Android library, to display OpenStreetMap maps. osmdroid downloads tiles from OpenStreetMap servers as described above. It does not collect or transmit personal information.

The app uses [Coil](https://coil-kt.github.io/coil/), an open-source image loading library, to render photos. Coil reads photos from local storage only — it does not make network requests in this app's configuration.

The app uses [ZXing Android Embedded](https://github.com/journeyapps/zxing-android-embedded), an open-source barcode decoding library, to scan hive QR labels. ZXing reads camera frames locally on your device to decode a single QR code — it does not save frames, photos, or video, and it does not transmit anything off the device.

The app does not use any other third-party SDK that processes or transmits user data.

## Future changes

If a future version of the app adds features that collect or transmit additional data — for example, cloud sync, community-contributed content with photo uploads, accounts, analytics, or crash reporting — this policy will be updated and the change will be noted in the change log below with a new effective date. Material changes will also be highlighted in the app's release notes on the Google Play Store.

## Contact

Questions or concerns about this policy or the app's privacy practices: **plainsightlogic@gmail.com**

## Changes to this policy

| Date       | Change                                                                                       |
|------------|----------------------------------------------------------------------------------------------|
| 2026-05-09 | Initial policy. Covers v0.1.0 release, including the optional per-hive location pin feature. |
| 2026-05-12 | Added the disease-treatment log feature, the POST_NOTIFICATIONS permission, and a new "Local notifications" section describing the on-device treatment-reminder behavior. No network or third-party push service is involved. |
| 2026-05-13 | Added per-hive next-inspection reminders. Same POST_NOTIFICATIONS permission and same on-device WorkManager mechanism — extended the "Local notifications" section to describe both kinds of reminders. No new data is collected or transmitted. |
| 2026-05-14 | Added the hive QR scanner. CAMERA permission is now requested at runtime when you tap "Scan hive QR" so the app can decode a printed hive label with the bundled ZXing library; no frames or photos are stored or transmitted. Added ZXing Android Embedded to the third-party components list. |
| 2026-05-15 | Updated the developer contact email from `thecloudix@gmail.com` to `plainsightlogic@gmail.com`. No change to data handling. |
