# Rice Broker Khata — Android app

A phone app for a rice broker: log loads from rice mills to shops, earn commission
per quintal from both sides, see who owes you how much, record irregular payments
"up to a date", follow rice prices, and download everything as Excel-ready files.

Everything is stored **on the phone**. No internet is needed.

---

## Get the APK — easiest way (GitHub builds it for you, no Android Studio)

1. Go to github.com and create a **new repository** (for example `rice-khata`). Private is fine.
2. Upload **all files in this folder** to it (keep the folders as they are, including
   the hidden `.github` folder). The simplest way on a computer:
   ```
   cd RiceBrokerKhata
   git init
   git add .
   git commit -m "Rice Khata app"
   git branch -M main
   git remote add origin https://github.com/<your-username>/rice-khata.git
   git push -u origin main
   ```
3. Open the repository on GitHub → **Actions** tab. A job called **Build APK** starts by
   itself (or press **Run workflow**). It takes about 3–5 minutes.
4. When it shows a green tick, open it and scroll to **Artifacts** → download
   **RiceKhata-apk**. It is a zip with `RiceKhata.apk` inside.
5. Send `RiceKhata.apk` to the phone (WhatsApp to yourself, Google Drive, or USB cable),
   tap it, and allow **Install unknown apps** when Android asks. Done.

## Or build it with Android Studio

1. Install Android Studio (free) → **Open** → choose this `RiceBrokerKhata` folder.
2. Wait for "Gradle sync" to finish (first time downloads tools; needs internet).
3. Menu **Build → Build App Bundle(s) / APK(s) → Build APK(s)**.
4. Click **locate** in the popup. The file is
   `app/build/outputs/apk/debug/app-debug.apk`. Copy it to the phone and install.

To run it directly on a phone: turn on **Developer options → USB debugging**, connect the
phone with a cable, and press the green ▶ Run button.

---

## Using the app

- **Home**: the red card shows how much everyone owes you; tap it to see each mill and shop.
- **＋ New entry**: one entry is recorded for both the mill and the shop.
- **₹ Money received**: choose who paid and the date the payment covers entries up to.
  From the next day, that party starts a new period.
- **Entries → Day by day**: pick a date, see that day's loads and payments, download it.
- **Rates**: latest rice price per quintal for each rice type, with ▲ / ▼ trend.
- **Downloads** go to **Downloads › Rice Khata** on the phone, or can be sent to WhatsApp / Drive.
- The phone's **Back** button closes popups and goes back a screen.

## Keep your records safe — please read

The records live only inside the app on that phone.

- Open **Home → Backup & restore** once a week and tap **Send backup** to Google Drive
  or to yourself on WhatsApp.
- If the phone is lost or changed: install the APK on the new phone → **Backup & restore**
  → **Choose backup file**.
- **Uninstalling the app deletes the records.** To update the app, just install the new
  APK over the old one — the records stay.
- Records already in the online Claude khata can be moved here: download a backup there
  and restore it in the app.

## Updating the app later

Every build is signed with the same key (`app/khata-release.jks`), so a newer APK installs
over the old one without losing data. **Keep `khata-release.jks` safe and do not change it.**
If you raise the version, change `versionCode` (1 → 2 → 3 …) in `app/build.gradle`.

The key password is in `app/build.gradle`. That is fine for a private, personal app;
do not publish this repository publicly with the key inside.

## What's inside

```
app/src/main/assets/www/index.html   the whole app screen (HTML/CSS/JS)
app/src/main/assets/www/fonts/       Young Serif + Hanken Grotesk (SIL Open Font License)
app/src/main/java/.../MainActivity.java   Android shell: WebView, save/share files, back button
app/khata-release.jks                signing key (keep safe)
.github/workflows/build-apk.yml      GitHub builds the APK automatically
```

Minimum Android version: 8.0 (Oreo).
