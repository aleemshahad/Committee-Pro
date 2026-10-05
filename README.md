# 📱 CommitteePro — Android & Web Committee (ROSCA) Manager
[![CI](https://github.com/aleemshahad/CommitteePro/actions/workflows/main.yml/badge.svg)](https://github.com/aleemshahad/CommitteePro/actions/workflows/main.yml)
<p align="center">
  <strong>کمیٹی پرو — ڈیجیٹل بچت کمیٹی اور بی سی مینجمنٹ سسٹم</strong><br>
  A modern, cloud-backed financial management system and Android mobile application designed to manage community savings groups (Committees, Kameti, BC, Chit Funds) with complete transparency, bilingual support (English & Urdu), digital lucky draws, and AI-assisted reminders.
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%20%7C%20Web-brightgreen?style=flat-square" alt="Platform">
  <img src="https://img.shields.io/badge/React-19-blue?style=flat-square" alt="React">
  <img src="https://img.shields.io/badge/TypeScript-5.8-blue?style=flat-square" alt="TypeScript">
  <img src="https://img.shields.io/badge/TailwindCSS-3.4-38bdf8?style=flat-square" alt="Tailwind">
  <img src="https://img.shields.io/badge/Capacitor-6.0-1192e8?style=flat-square" alt="Capacitor">
  <img src="https://img.shields.io/badge/AI-Gemini%202.5%20Flash-orange?style=flat-square" alt="Gemini">
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License">
</p>


---

## 🌟 Key Features

### 1. 👥 Multi-Tier Administrative Governance (RBAC)
- **Super Head Admin (سپر ہیڈ ایڈمن):**
  - Full system oversight: approve or reject newly submitted committee proposals.
  - User and admin control directory: block fraudulent users, activate Pro, and grant the `admin` role.
  - Delete or archive stale committee records.
- **Group Head Admin (گروپ ہیڈ ایڈمن):**
  - Submit committee proposals with monthly contributions (PKR) and member counts.
  - Track monthly payments, record cash/online transaction methods, and execute lucky draws.
- **Member (عام ممبر):**
  - Transparent view of payment status across all months, draw winners list, and payout schedules.

### 2. 📅 Month-by-Month Calendar Matrix
- Interactive visual grid showing all members along the Y-axis and all committee **Months (ماہ)** along the X-axis.
- Instant color-coded badges for **Paid** (Green) vs. **Pending/Unpaid** (Slate).
- Direct payment logging modal with payment method selection (`CASH`, `BANK_TRANSFER`, `ONLINE_WALLET` JazzCash/EasyPaisa), notes, and receipt verification.

### 3. 🎡 Digital Lucky Draw Wheel (قرعہ اندازی)
- 60 FPS Canvas-rendered interactive spinning wheel.
- Automatic exclusion algorithm for members who won in previous months to ensure fair, zero-bias selection.
- Audit history logging winning member, draw date, month index, and disbursement notes.

### 4. 🤖 AI-Powered Polite Reminder Generator (Google Gemini 2.5 Flash)
- Generates polite, culturally respectful WhatsApp payment reminders.
- Bilingual output in **Urdu (اردو اسکرپٹ)** and **English**.
- Ready-made reminder templates that work without a network connection.

### 5. 🌐 Bilingual & Culturally Localized
- 1-click toggle between **English** and **Urdu (اردو)**.
- Authentic South Asian financial terms: *کمیٹی (Committee), قسط (Installment), قرعہ اندازی (Draw), بچت (Savings)*.

---

## 🏗️ Architecture Overview

```
                      ┌─────────────────────────────────────────┐
                      │    CommitteePro Android / Web Client   │
                      └────────────────────┬────────────────────┘
                                           │
         ┌─────────────────────────────────┼─────────────────────────────────┐
         │                                 │                                 │
┌────────▼────────┐              ┌─────────▼─────────┐             ┌─────────▼────────┐
│  Presentation   │              │  State & Storage  │             │ Hybrid Bridge    │
│  - React 19     │              │  - StorageService │             │ - Capacitor 6    │
│  - Tailwind CSS │              │  - LocalStorage   │             │ - Android Gradle │
│  - Lucide Icons │              │  - Local Cache    │             │ - Native Haptics │
└─────────────────┘              └───────────────────┘             └──────────────────┘
```

---

## 🚀 Getting Started & Local Web Development

### Prerequisites
- [Node.js](https://nodejs.org/) (version 18.0 or higher)
- [npm](https://www.npmjs.com/) or [bun](https://bun.sh/)

### Installation & Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/aleemshahad/CommitteePro.git
   cd CommitteePro
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the local development server:**
   ```bash
   npm run dev
   ```
   Open [http://localhost:3000](http://localhost:3000) in your browser.

4. **Build the production web bundle:**
   ```bash
   npm run build
   ```

---

## 📱 Building the Android App (APK / AAB)

CommitteePro is fully configured for packaging into a high-performance native Android application using **Capacitor 6** and **Android Studio**.

### Step 1: Install Capacitor CLI & Android Platform
```bash
npm install @capacitor/core @capacitor/cli @capacitor/android
npx cap init "CommitteePro" "com.committeepro.app" --web-dir "dist"
```

### Step 2: Build Web Assets & Add Android
```bash
# 1. Compile the production bundle
npm run build

# 2. Add Android platform
npx cap add android

# 3. Sync web assets into Android project
npx cap sync android
```

### Step 3: Open in Android Studio & Generate APK
```bash
npx cap open android
```

In **Android Studio**:
1. Wait for Gradle sync to complete.
2. Select **Build** $\rightarrow$ **Build Bundle(s) / APK(s)** $\rightarrow$ **Build APK(s)**.
3. Your installable Debug APK will be generated at:
   `android/app/build/outputs/apk/debug/app-debug.apk`

### ⚙️ Automatic APK via GitHub Actions (recommended)

A GitHub Action (`.github/workflows/build-apk.yml`) builds the APK for you on any push and on every release **tag** (e.g. `v1.0.0`):

```bash
git tag v1.0.0
git push origin v1.0.0
```

- The **debug APK** is attached to the auto-created GitHub Release.
- The APK for any run is also available under **Actions → Build Android APK → Artifacts**.
- A `CI` workflow (`.github/workflows/main.yml`) verifies the web build on every push.

### 🔐 Preparing a signed production release (Play Store)

Side-loaded debug APKs are fine for testing, but a store-ready build needs a signed keystore.

1. Generate a keystore (keep it safe — you cannot recover it):
   ```bash
   keytool -genkey -v -keystore committeepro-release.jks \
     -alias committeepro -keyalg RSA -keysize 2048 -validity 10000
   ```
2. Add these **repository secrets** (Settings → Secrets and variables → Actions):
   `KEYSTORE_BASE64` (base64 of your `.jks`), `KEYSTORE_PASSWORD`, `KEY_ALIAS`, `KEY_PASSWORD`.
3. Update the `Build debug APK` step in `.github/workflows/build-apk.yml` to use
   `assembleRelease` and inject your `signingConfigs` — then tags will ship signed builds.

---

## 📂 Project Structure

```
├── components/                 # UI components
│   ├── DrawWheel.tsx           # Canvas 60 FPS Lucky Draw spinning wheel
│   ├── Layout.tsx              # Sidebar, navigation bar, language switcher
│   └── RecordPaymentModal.tsx  # Payment entry & verification modal
├── context/
│   └── LanguageContext.tsx     # Bilingual English & Urdu translation context
├── pages/
│   ├── Profile.tsx             # the signed-in account: role, status, plan, cloud session
│   ├── AdminPanel.tsx          # Super Head Admin user and committee manager
│   ├── Dashboard.tsx           # Financial stats, pending approvals, quick actions
│   ├── GroupDetail.tsx         # Month-by-Month matrix ledger & draw controls
│   ├── Groups.tsx              # List of active committees & creation dialog
│   ├── Login.tsx               # Role switcher (Super Admin, Group Admin, Member)
│   └── Reports.tsx             # Aggregate financial analytics & progress charts
├── services/
│   ├── geminiService.ts        # Google Gemini 2.5 Flash reminder generator
│   └── storageService.ts       # Local cache + sync bridge (never an auth gate)
├── types.ts                    # TypeScript types & interface definitions
├── constants.ts                # English & Urdu translation dictionaries
├── PRD.md                      # Comprehensive Product Requirements Document
├── package.json                # Project dependencies and build scripts
└── vite.config.ts              # Vite configuration
```

---

## 🔐 Accounts and Roles

There are **no pre-seeded accounts**. A fresh install starts completely empty and people
appear only by signing up with a real Firebase Email/Password account.

| Role | Who gets it | Capabilities |
| :--- | :--- | :--- |
| `regular` | Everyone on sign-up | Own profile, own committees, own payment/draw history. No admin surface at all. |
| `admin` | Granted by the Super Admin | Read every member profile for moderation, block/unblock, activate Pro, approve committees. **Cannot** read anyone's private dataset and **cannot** change roles. |
| `super_admin` | Only `MASTER_ADMIN_EMAIL` in `constants.ts` (`aleemssg@gmail.com`) | Full control. Exactly one, always. |

`super_admin` is **not a writable field**. `firestore.rules` recomputes it from the verified
email in the ID token on every request, so nobody can promote themselves, nobody can create a
second Super Admin, and deleting the role from a document does not remove the privilege.
To move Super Admin to a different person, change `MASTER_ADMIN_EMAIL` in `constants.ts`
*and* the matching literal in `firestore.rules`, then redeploy the rules — a deliberate,
reviewable code change.

---

## 💰 Monetization (Freemium)

CommitteePro runs on a **free core, ad-supported** model with an optional one-time **PRO** upgrade.

### Free plan (ad-supported)
- All core committee tools: create/manage up to **2 committees**, month-by-month ledger,
  digital lucky draw, member management, language switcher, and manual WhatsApp reminder drafts.
- **AdMob banner slots** (`components/AdBanner.tsx`) render only once real Ad Unit ids are
  filled into `ADMOB` in `constants.ts`; the Ads feature toggle is off by default, so a fresh
  install shows no ad slot at all.

### PRO plan (manual Raast / EasyPaisa / JazzCash verification)
Unlocked by a **manual payment flow** with Super-Admin-only verification — no payment gateway:

**1. Account details & payment submission**
- Member taps **Upgrade to Pro** → `PaywallModal` shows the admin's local wallets
  (**Raast / EasyPaisa / JazzCash**) and the PKR amount to send. Only wallets that are
  actually filled in are rendered — `configuredPaymentChannels()` drops empty ones, so a blank
  row can never read as a real account number, and while nothing is configured the screen
  says so and the **Confirm Payment** button stays disabled.
- The member enters the **Transaction ID (TID)** from their receipt and attaches a **payment
  screenshot**, then taps **"Confirm Payment"**.
- The screenshot is re-encoded in the browser (`services/proRequest.ts` → `prepareProofImage`)
  to a ≤900px JPEG under `PRO_REQUEST.maxProofBytes`. This is not cosmetic: the receipt is stored
  inside a Firestore document, and a document may not exceed ~1 MiB, so a raw 4 MB phone
  screenshot would otherwise fail the write with an opaque error.

**2. Strict Super Admin-only access**
The platform has two administrative tiers plus one owner, and verification belongs **exclusively
to the owner**:

| Tier | Committee management | Block/unblock | PRO requests & promotion |
| --- | --- | --- | --- |
| `regular` | own committees | — | may *submit* a request |
| `admin` | own + assigned committees | yes | **no access at all** |
| `super_admin` | everything | yes | **the only tier that may verify** |

This is enforced at four independent layers, so no single mistake exposes it:
- **`firestore.rules` → `match /proRequests/{uid}`** has no `isAdmin()` branch anywhere. A group
  admin's request is denied by the database, not just hidden by the UI.
- **`cloudWatchProRequests`** refuses to subscribe for a non-master and reports an error rather
  than an empty queue, and **`cloudSettleProRequest`** re-checks the live Firebase session email
  before writing.
- **`isMaster()`** derives the privilege from the *verified email in the ID token*, so a stored
  role field cannot grant it.
- **`watchAllUsers`** strips `proPending` from the user list for a non-master, so an admin cannot
  even learn that someone has applied.

**3. Super Admin action panel**
`AdminPanel.tsx → PRO payment verification queue` lists every pending request with the submitted
**screenshot** (clickable full size) and the **Transaction ID**, and offers:
- **"Accept & Promote to PRO"** → writes `proActive` on `users/{uid}` and marks the request
  `ACCEPTED`, in one step.
- **"Reject"** → the account is not promoted and the request is retained as evidence
  (`allow delete: if false`).

The section renders only for the master (`canVerifyPayments`). A group admin gets a plain
notice instead of a dimmed panel, because a disabled-but-present queue would still leak who
applied into their DOM.

The applicant's own screen watches their request document, so an accept or a reject shows up for
them without a reload, and a rejection offers a resubmit path.

Benefits once activated:
- **Automated reminders** — one-tap "Remind All Unpaid" WhatsApp blast + direct SMS compose
  for each unpaid member (`pages/GroupDetail.tsx`).
- **Payment alerts & auto-reminder toggles** — PRO-only advanced settings (`pages/Settings.tsx`).
- **PDF / Excel exports** — real client-side reports with zero new dependencies
  (`pages/Reports.tsx` + `services/exportService.ts`; Excel = UTF‑8 CSV, PDF = print dialog).
- **Unlimited multi-circle management** (free plan capped at `FREE_PLAN_MAX_COMMITTEES`).
- **Ad-free experience.**

### Super Admin feature switches
`AdminPanel → Pro & Feature Management → Feature Controls` lets the Super Head Admin toggle
individual paid features app-wide (`AppState.featureFlags`): Ads, reminders, exports,
multi-circle and advanced settings. A disabled feature is blocked for everyone, including Pro users.

### Where user data lives
**Firestore is the source of truth.** It is split into two collections so that moderators can
read a profile without ever seeing the person's private numbers:

| Document | Contents | Readable by |
| :--- | :--- | :--- |
| `users/{uid}` | name, contact, role, status, Pro state | the owner, any `admin`, the `super_admin` |
| `datasets/{uid}` | committees, payments, draws | the owner and the `super_admin` only |

`localStorage` (`committee_pro_db_v1` and friends) is a **cache only**. It is never used to
decide who is signed in — the gate is the Firebase Auth session, and a local row is only
accepted when its id matches the signed-in UID. Removing the cache cannot grant access to
anyone, because every read is re-checked against `firestore.rules`.

### ☁️ Cloud backend (required, free Firebase tier)
Authentication and data always go through the real backend: a Super Admin sees **every**
account over the internet and can block/unblock, grant `admin` and activate Pro remotely — the
change reaches the member's phone instantly. If Firebase is not configured the app cannot sign
anyone in at all; there is no offline fallback identity.

**Part 1 — create the project (≈3 min, no card needed)**

1. [console.firebase.google.com](https://console.firebase.google.com) → **Add project**.
2. **Build → Authentication → Sign-in method** → enable **Email/Password**.
3. **Firestore Database** → **Create database** in **production mode** (free Spark tier).
4. **Project settings → General → Your apps → Add app → Web** → register the app, then copy the
   whole `firebaseConfig` object. You need exactly these keys:

   | key | example |
   | --- | --- |
   | `apiKey` | `AIzaSy...` |
   | `authDomain` | `your-project.firebaseapp.com` |
   | `projectId` | `your-project` |
   | `appId` | `1:1234567890:web:abc123` |
   | `storageBucket` | `your-project.appspot.com` *(optional)* |
   | `messagingSenderId` | `1234567890` *(optional)* |

**Part 2 — wire it into the app (one command)**

```bash
npm run firebase:setup     # paste the firebaseConfig object; it patches constants.ts for you
npm run firebase:check     # confirms it is set up
```

The script turns on `configured: true` automatically. Nothing else is edited by hand.

**Part 3 — publish the security rules**

The repo ships `firestore.rules` (members write their own data and can *request* Pro; only a
Super Admin can grant Pro, block, or change a role; nobody can delete a document).

```bash
npm run firebase:login           # one-time, opens a browser
npm run firebase:deploy:rules    # publishes firestore.rules
```

This repo already targets one project, so `.firebaserc` is committed and a fresh clone can
deploy straight away. If you are pointing the app at a *different* project, run
`npm run firebase:use` first to switch it.

Prefer the console? **Firestore → Rules**, paste the contents of `firestore.rules`, **Publish**.
Without any rules a production-mode database rejects every read and write.

**Part 4 — the Super Admin account**

There is no promotion step to perform. The Super Admin is the single account whose Firebase Auth
email equals `MASTER_ADMIN_EMAIL` in `constants.ts` (`aleemssg@gmail.com`), and `firestore.rules`
recomputes that from the verified token on every request:

1. Make sure that exact address is the one you sign in with on the app, and that Firebase has
   verified it (**Authentication → Users →** the row → `Email verified`).
2. Sign in. The app writes its own `users/{uid}` document, and the `create` rule stamps
   `role: "super_admin"` on it because the token proves the address.
3. Everyone else who signs up is created as `regular` and can only be moved to `admin` from the
   Admin Panel, never to `super_admin`.

Setting `role` to `super_admin` on some *other* document in the console does nothing — the rules
never read that field to decide authority, which is exactly what makes a second Super Admin
impossible.

**Part 5 — rebuild**

```bash
npm run build                   # web
npm run firebase:deploy:hosting # optional: also publish the web app
```

The Android build picks the config up automatically (see `.github/workflows/build-apk.yml`).

**Testing it end to end**

```bash
npm run firebase:rules:check    # validates the rules with the local emulator (needs Java)
```

The shipped rules already enforce the tiering: `role`, `status`, `blocked` and the Pro fields are
writable only by an admin or the Super Admin, a member may *request* Pro but never grant it, a
member can never write their own role, and an admin can never write anyone's role at all. The
`tests/test-rules.mjs` suite parses `firestore.rules` and fails if the client push or the admin
operations ever grow a field that the rules do not allow — so the two cannot drift apart silently.

> **Next hardening step for a public launch:** move the admin writes (Pro activation, block, role
> grant) into a **Cloud Function / Admin SDK** so those fields are not writable from *any* client,
> then turn on App Check. The data model and rules are already shaped so this is an additive change.

`services/cloudService.ts` (Auth + Firestore), `services/syncAdapter.ts` (pure mapping), and
`services/storageService.ts` (local cache + sync bridge) implement the backend.

### Wiring real ads & payments later
1. **AdMob**: set `ADMOB.bannerAdUnitId*` in `constants.ts`, then add the Capacitor
   `@capacitor-community/admob` plugin and render the native banner in `AdBanner.tsx`.
2. **Real IAP/subscription**: replace the manual EasyPaisa/JazzCash flow with the Google Play
   Billing Capacitor plugin; keep the per-user `User.proActive` flag as the cached entitlement.

---

## 📄 Documentation
For detailed architectural specifications, user flows, and technical schema, see [PRD.md](./PRD.md).

---

## 
