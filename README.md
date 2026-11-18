# HLS ASSESSMENT — Android app

Holistic Learning System's assessment app for Android phones and tablets (Android 7.0 and newer).

## What the app does

| Area | What's in it |
|---|---|
| **Today panel** | When a teacher opens the app, it shows what needs attention: scripts waiting to sync, an unfinished script, questions needing a flowchart decision, and learners due for reassessment. Each has a one-tap button. |
| **Sign-in & roles** | Teacher, Assessor, Principal/Head, Administrator, Director, Parent and Learner. The server checks every role. Learners never see answer keys. |
| **Assessment Studio & Question Bank** | Build assessments from approved questions. Import questions from Word, Excel, CSV or text. |
| **Take Assessment** | Learners sit open tests. Drafts are encrypted and saved on the phone. Leaving mid-test asks first. |
| **Marking Desk** | Mark digital scripts against the private marking guide. Question-level marks feed Remediation Reports. |
| **Script Scanner** | **📷 In-app camera** with a big shutter button, torch and **auto-snap** (captures each page once the picture is steady, then waits for the next page turn). **🖼 Photos** from the gallery. **🎥 Video**: record inside the app or choose a clip, and the app finds every page. It warns about **dark, blurry or repeated pages**. Tap the page to stamp ✓ / ½ / ✗. Saved marking schemes, "All full marks", name suggestions for learners already marked, a **"Did you mean…?"** check for spelling slips, and a warning before re-marking the same learner. **Everything is auto-saved after every tap**: if the phone dies or Android closes the app, the script is restored. Marked-script PDF to share with parents. |
| **Works offline** | Marks are kept on the phone and sync automatically when the connection returns. If the server refuses a record, it stays on the phone with the reason shown and is never silently lost. Results and lists already loaded stay viewable offline. |
| **Approve & Release** | Leadership approves marked scripts before learners and parents see them. |
| **Results & Reports** | Released results. Export to Excel, Word or PDF. |
| **Remediation Reports** | Built on the **HLS Test Response Flowchart**: *Was the question suitable?* then *Were most wrong answers similar?*, leading to **Rewrite the question**, **Reteach the misunderstanding** or **Reteach with practice**. Its built-in analysis helps with each decision: the **misunderstanding engine** recognises common slips from learners' wrong answers (for example "Pupils find one part (8 ÷ 4) but do not multiply by 3"); a **discrimination index** shows when strong learners did worse than weak ones (a sign of a bad question); and **suggested answers** can be applied with one tap. **Progress tracking** compares each topic across assessments and lists learners still struggling after reteaching. You also get re-teaching groups, learner plans, reassessment dates, class Word reports, Excel logs and parent messages. |
| **Help & Backup** | Step-by-step guides, **backup and restore** (for moving to a new phone), and a one-tap problem report for HLS support (no learner data included). |

**Reliability features:** the app restarts itself cleanly if Android runs low on memory; the sign-in survives an Android restart while the app is in use and locks after **60 minutes without use** (unfinished work is kept); errors are shown in plain language; the screen stays on while marking; large files are saved in chunks so low-memory phones don't crash; old temporary files are cleaned up automatically; and phones with an outdated WebView get a clear "please update" message instead of a blank screen.

---|---|
| **Sign-in & roles** | Teacher, Assessor, Principal/Head, Administrator, Director, Parent, Learner. The server checks each role. Learners never see answer keys. |
| **Assessment Studio & Question Bank** | Build assessments from approved questions. Import questions from Word, Excel, CSV or text. |
| **Take Assessment** | Learners sit open tests. Drafts are encrypted and auto-saved on the phone. |
| **Marking Desk** | Mark submitted digital scripts against the private marking guide. |
| **Script Scanner (new)** | Mark paper scripts three ways: **📷 Photos** (any number of pages), **🎥 Video** (film the script while turning pages; pages are found automatically), or **◉ Live scan** (auto-snap while you turn pages). Tap the page to stamp ✓ (+1), ½ (+0.5) or ✗ (0) against the active question, and the marks add up automatically. You can save and reuse marking schemes, use "Save & next script" for whole-class marking, and export a **marked-script PDF** to share with parents. If there is no network, marks are saved on the phone and sync automatically later. |
| **Approve & Release** | Leadership approves marked scripts before learners and parents can see them. |
| **Results & Reports** | Released results. Export to Excel, Word or PDF (print). |
| **Remediation Reports (new)** | Built on the **HLS Test Response Flowchart**. For each question that lost marks: **1. Was the question suitable?** If not, the action is *rewrite the question or choose one relevant to the LO*, and the question can be left out of learners' scores. If it was suitable: **2. Were most wrong answers similar?** If yes, it's the *same misunderstanding*: record what it is, and the action is to *reteach to correct it*. If no, it's *different mistakes*: *reteach and give relevant practice*. The app shows evidence for each decision (who lost marks, the most common wrong answers, warnings when even strong learners got it wrong) and builds re-teaching groups. Individual learner plans, class Word reports, Excel decision logs and parent messages are all generated from your decisions. |
| **Learning Diagnostics** | Insights from the ILDIE diagnostic engine. |

Native Android features: camera and video capture, live camera scanning with torch, saving files to **Downloads › HLS Assessment**, the Android share sheet (WhatsApp, email, Drive), printing or Save-as-PDF, the back button, full screen, and a splash screen with the HLS icon.

---

## Get the APK — easiest way (no software to install)

1. Create a free account at **github.com** and make a **new private repository** (for example `hls-assessment`).
2. On the repository page, click **"uploading an existing file"**. Drag in **everything inside this folder**, including the hidden `.github` folder. Then click **Commit changes**.
   *Tip: if your browser skips the `.github` folder, use **GitHub Desktop** instead, or create the file `.github/workflows/build-apk.yml` by hand with **Add file › Create new file** and paste in its contents.*
3. Open the **Actions** tab. The build **"Build HLS ASSESSMENT APK"** starts automatically and takes about 5 minutes.
4. When it shows a green tick, open the build and download **HLS-ASSESSMENT-APK** under *Artifacts*. Unzip it to get `HLS-ASSESSMENT-v3.0-release.apk`.
5. Copy the APK to the phone, tap it, and allow **"Install unknown apps"** when Android asks.

To publish a downloadable release page, push a tag such as `v3.0`. The APK is then attached to a GitHub Release.

## Or build with Android Studio

Open this folder in Android Studio (Hedgehog or newer). Wait for Gradle sync, then choose **Build › Build App Bundle(s) / APK(s) › Build APK(s)**.
From a terminal: `./gradlew assembleRelease` → `app/build/outputs/apk/release/`.

## Signing key — important

The project includes a signing key, `keystore/hls-assessment.jks` (password `HlsAssess2026`, alias `hlsassessment`). Every build is signed with this same key, so new versions install **over** old ones without losing data.

* **Keep the repository private.** Anyone with this key could sign an app that impersonates yours.
* **Back up the `keystore` folder.** If you lose it, phones must uninstall the app before they can install a new version.
* For Google Play or stronger security, add these repository secrets: `HLS_KEYSTORE_BASE64` (the .jks file as base64), `HLS_KEYSTORE_PASSWORD`, `HLS_KEY_ALIAS` and `HLS_KEY_PASSWORD`. Then delete the bundled key from the repository. The workflow uses the secrets automatically.

## Updating the app

* App content: `app/src/main/assets/www/index.html`
* Version: raise `versionCode` and `versionName` in `app/build.gradle` before each new release.
* Icon for the Play Store listing: `play_store_icon_512.png`

## Privacy notes

* Script photos and videos stay on the phone. Only the teacher-verified marks are sent to HLS.
* Question-level marks, flowchart decisions, notes and saved schemes are kept on the phone, separately for each signed-in user, and shown only to staff. Export a backup from **Help & Backup**.\n* The sign-in is cleared on sign-out, or after 60 minutes without use.
* The app only loads its own bundled pages. External links open in the phone's browser.
