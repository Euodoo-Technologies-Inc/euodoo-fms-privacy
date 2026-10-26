---
layout: default
title: euodoó FMS Privacy Policy
---

# euodoó FMS — Privacy Policy

**Effective date:** 26 October 2026
**Applies to:** the euodoó FMS Android application (`com.euodoo.fms`) and, once push
notifications are available, the notification service operated alongside it.

Euodoo Technologies, Inc. ("Euodoo", "we") provides euodoó FMS, a fleet management client
for organisations that use a GPS fleet-tracking platform (the "tracking platform"). This
policy explains what the app handles, where it goes, and how long it stays there.

Push notifications are not yet available in the app. The parts of this policy that
describe them are marked *(once notifications are available)* and apply from the release
that introduces them; until then, no notification registration exists and nothing reaches
our notification service.

## 1. Who uses this app

euodoó FMS is a business tool. There is no public sign-up: accounts are issued by a fleet
operator's own administrator, and you sign in with credentials that already exist in that
operator's tracking-platform account. You are either the operator or a person that operator has
authorised.

The vehicle data in this app belongs to the operator, not to us and not to the individual
signing in.

## 2. What the app handles

### Sign-in credentials

Your tracking-platform **username and password** are stored on your device so the app can
silently re-authenticate when your session expires (access tokens last roughly 30 minutes,
and re-prompting every half hour would make the app unusable).

- On Android they are held in the **operating system's hardware-backed keystore** via
  `expo-secure-store` — not in app preferences, not in a plain file.
- They are transmitted **only** to the tracking platform's API to obtain an access token,
  over HTTPS.
- **We never receive them.** They do not reach Euodoo servers, and they are not included in
  any diagnostic or analytics transmission — the app contains no analytics or crash-reporting
  SDK of any kind.
- Signing out deletes them from the keystore.

### Access tokens

The short-lived access token is kept for the life of your session and used to
authorise API calls. *(once notifications are available)* When you enable notifications,
the token is sent once to our notification service **solely so the service can ask
the tracking platform which vehicles you are allowed to see**. The token itself is used for that check
and then discarded — it is never written to disk by that service.

### Notification registration *(once notifications are available)*

If you turn on push notifications, our notification service stores:

- your **Expo push token** — an opaque identifier for delivering messages to your device
  installation; it is not tied to your name, email or phone number,
- your **notification preferences** (alarms, idling, geozone),
- the **set of vehicle IDs your account was authorised to see** at the moment you registered.

That authorised set is derived server-side from the tracking platform, never from anything the app claims.
It exists so that a device can only ever be sent an alert about a vehicle its account is
permitted to view.

Turning notifications off, or signing out, removes this record.

### Fleet and vehicle data

The app displays vehicle positions, status, trip history, events and reports retrieved from
your operator's tracking-platform account. This is **operator-owned fleet telemetry**, not personal
location data about the person holding the phone.

To keep the app usable on poor connections, recently viewed fleet data is cached on the
device. The cache is cleared when you sign out and when the app's storage is cleared.

### Reports you export

Report exports (PDF and spreadsheet) are generated **on your device** and handed to
Android's share sheet. Where they go from there is your choice — we do not receive a copy
and we do not upload them anywhere.

## 3. What the app does *not* do

- **It does not collect your device's location.** The app requests no location permission
  and contains no location provider. Every coordinate shown comes from vehicle trackers via
  the tracking platform.
- **No analytics, telemetry, behavioural tracking or advertising.** There is no advertising
  ID, no ad SDK, no attribution SDK, no third-party analytics.
- **No access to contacts, photos, camera, microphone, call logs, SMS or installed apps.**
- **No sale or sharing of data** with anyone for advertising or any other purpose.
- **No profiling** and no automated decision-making about you.

## 4. Who else receives data

| Recipient | What reaches them | Why |
| --- | --- | --- |
| **Your organisation's fleet-tracking platform** | Sign-in credentials, API requests, your IP | It is the fleet platform of record; the app is a client for it. Governed by your operator's agreement with that platform's provider. |
| **Expo push service** and, in turn, **Google Firebase Cloud Messaging** *(once notifications are available)* | Push token and notification content (a short alert like a vehicle name and event type) | Required to deliver an Android push notification at all. |
| **Map tile providers** — OpenStreetMap, CARTO, Esri/ArcGIS Online, OpenTopoMap | Your IP address and the map tiles requested, when a map is on screen | To render the base map. No account data is sent; which one is contacted depends on the map style you select. |
| **Euodoo notification service** *(once notifications are available)* | The items listed under *Notification registration* | To decide which devices should receive which alerts. |

We use no other processors. We do not transfer data to any party for advertising.

## 5. Retention

| Data | Retained |
| --- | --- |
| Credentials in the device keystore | Until you sign out or uninstall |
| Cached fleet data on the device | Until you sign out or clear app storage |
| Push token, preferences and authorised vehicle scope *(once notifications are available)* | Until you disable notifications, sign out, or the push token is reported as no longer valid — our service prunes those automatically |
| Tracking-platform access tokens | Not retained by us |

Fleet data held inside the tracking platform is retained under your operator's own
configuration and agreement, which this policy does not govern.

## 6. Security

Credentials are stored in Android's hardware-backed keystore. All network communication
uses HTTPS/TLS. *(once notifications are available)* Notification scope is authorised
server-side against the tracking platform on every registration, so a device cannot request alerts for
vehicles it is not entitled to see, and the registration endpoint is rate-limited.

No system is perfectly secure, but we do not hold the data that would be most sensitive if
breached: we never receive your password, and we never store your access token.

## 7. Your choices and your rights

- **Stop notification processing:** *(once notifications are available)* disable
  notifications in the app's settings, or in Android's app settings. The stored
  registration is removed.
- **Remove local data:** sign out, or uninstall the app. Both clear the stored credentials
  and the cached fleet data from the device.
- **Access, correction or deletion of fleet data:** that data lives in your operator's
  tracking-platform account. Contact your fleet administrator, who controls it.
- **Deletion of a Euodoo-held record:** *(once notifications are available)* contact us
  at the address in §10 and we will delete any notification registration associated with
  your device.

Because accounts are created by your operator and not in the app, account deletion is
handled by your operator's administrator rather than in-app.

## 8. Children

euodoó FMS is a workplace tool intended for people aged 18 and over. It is not directed at
children and we do not knowingly collect data from them.

## 9. Changes

If this policy changes materially we will update the effective date above and, where the
change affects how notifications or credentials are handled, note it in the app's release
notes.

## 10. Contact

Euodoo Technologies, Inc.
Level 10-1 One Global Place, 5th Ave, BGC, Taguig City, Philippines
marketing@euodoo.com.ph

For fleet data held in the tracking platform, contact your own fleet administrator first — they are the
controller of that data.
