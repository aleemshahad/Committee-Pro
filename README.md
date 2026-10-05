# 📱 CommitteePro — Modern Committee & Savings Group Manager

[![Release](https://img.shields.io/badge/Latest%20Release-v2.5.1-brightgreen?style=flat-square)](https://github.com/aleemshahad/CommitteePro/releases/tag/v2.5.1)
[![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20Web-blue?style=flat-square)](https://github.com/aleemshahad/CommitteePro)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![Built with](https://img.shields.io/badge/Built%20with-React%2019%20%7C%20TypeScript%20%7C%20Capacitor-orange?style=flat-square)](package.json)

---

## 🚀 Quick Download

### 📲 **Download Android App (APK)**
| Version | Size | Download |
|---------|------|----------|
| **v2.5.1** (Latest) | ~45 MB | [📥 Download APK](https://github.com/aleemshahad/CommitteePro/releases/download/v2.5.1/app-debug.apk) |
| v2.5.0 | ~45 MB | [📥 Download APK](https://github.com/aleemshahad/CommitteePro/releases/download/v2.5.0/app-debug.apk) |
| v2.4.2 | ~44 MB | [📥 Download APK](https://github.com/aleemshahad/CommitteePro/releases/download/v2.4.2/app-debug.apk) |

**👉 [View All Releases →](https://github.com/aleemshahad/CommitteePro/releases)**

### 🌐 **Use Online (No Installation)**
Open in your browser: [CommitteePro Web App](https://github.com/aleemshahad/CommitteePro)

---

## ✨ Key Features

### 1. 👥 **Multi-Tier Role-Based Access Control (RBAC)**
Manage committees with complete administrative control:

| Role | Responsibilities |
|------|------------------|
| **Super Head Admin** | Approve committees, manage all users, block/unblock, activate Pro plans |
| **Group Head Admin** | Create committees, track payments, execute lucky draws, generate reports |
| **Member** | View payment status, track draw history, receive reminders |

### 2. 📊 **Month-by-Month Financial Matrix**
- **Interactive grid** showing all members vs. all committee months
- **Color-coded badges**: 🟢 Paid | 🔴 Pending
- **Quick payment logging** with multiple methods: Cash, Bank Transfer, JazzCash, EasyPaisa
- **Receipt verification** and transaction tracking

### 3. 🎡 **Digital Lucky Draw System**
- **60 FPS Canvas-based spinning wheel** for fair, transparent draws
- **Smart algorithm** prevents repeat winners
- **Complete audit trail** of all draws and payouts
- **One-click draw execution** during monthly settlements

### 4. 🤖 **AI-Powered Reminders**
- **Google Gemini 2.5 Flash** integration
- **Bilingual reminders**: English & Urdu
- **WhatsApp-ready templates** for payment follow-ups
- **Offline mode** with pre-built reminder templates

### 5. 🌐 **Bilingual Interface**
- **One-click language toggle** between English & Urdu
- **Authentic financial terminology**: قسط (Installment), قرعہ اندازی (Draw), کمیٹی (Committee)
- **Culturally localized** for South Asian communities

### 6. 💰 **Freemium Business Model**
- **Free Tier**: Manage up to 2 committees, basic features, ad-supported
- **Pro Plan**: Unlimited committees, no ads, automated reminders, PDF/Excel exports

### 7. 📈 **Advanced Reports & Analytics**
- Monthly payment summaries with trends
- PDF & Excel export functionality
- Draw history and payout tracking
- Member contribution analysis

---

## 📋 Installation & Setup

### **For Android Users (Easiest)**

1. **Download the APK**
   - Click the download button above for the latest version
   - Or visit [Releases Page](https://github.com/aleemshahad/CommitteePro/releases)

2. **Install on Your Phone**
   - Open the downloaded `.apk` file on your Android device
   - Tap **"Install"** when prompted
   - Grant permissions when requested
   - Launch the app

3. **First Time Setup**
   - Create your account with email & password
   - Set your role (Admin or Member)
   - Create or join a committee
   - Start managing payments!

**⚠️ Note:** You may see "Unknown source" warning. This is normal for side-loaded apps. Tap **"Install Anyway"**.

---

### **For Web Users (No Installation)**

1. **Clone or Fork the Repository**
   ```bash
   git clone https://github.com/aleemshahad/CommitteePro.git
   cd CommitteePro
   ```

2. **Install Dependencies**
   ```bash
   npm install
   # or
   bun install
   ```

3. **Start Development Server**
   ```bash
   npm run dev
   ```
   - Opens at `http://localhost:3000`
   - Auto-reloads on file changes

4. **Build for Production**
   ```bash
   npm run build
   npm run preview
   ```

---

## 🛠️ Developer Guide

### **Prerequisites**
- Node.js 18+ ([Download](https://nodejs.org/))
- npm or bun package manager
- (Optional) Android Studio for APK building

### **Project Structure**
```
CommitteePro/
├── components/              # Reusable UI components
│   ├── DrawWheel.tsx        # 60 FPS lucky draw wheel
│   ├── PaymentModal.tsx     # Payment entry & verification
│   └── Layout.tsx           # App shell & navigation
├── pages/                   # Main app screens
│   ├── Login.tsx            # Authentication
│   ├── Dashboard.tsx        # Financial overview
│   ├── GroupDetail.tsx      # Committee management
│   ├── AdminPanel.tsx       # Admin controls
│   └── Reports.tsx          # Analytics & exports
├── services/                # Backend integration
│   ├── cloudService.ts      # Firebase auth & database
│   ├── geminiService.ts     # AI reminder generation
│   └── storageService.ts    # Local cache & sync
├── context/                 # Global state
│   └── LanguageContext.tsx  # Bilingual support
├── constants.ts             # App configuration & translations
├── types.ts                 # TypeScript interfaces
├── package.json             # Dependencies & scripts
└── firestore.rules          # Firebase security rules
```

### **Building the Android APK**

**Automated (GitHub Actions — Recommended)**
1. Push a tag: `git tag v1.0.0 && git push origin v1.0.0`
2. View workflow: [Actions → Build Android APK](https://github.com/aleemshahad/CommitteePro/actions)
3. Download APK from release artifacts

**Manual Build (Local)**
```bash
# Step 1: Install Capacitor
npm install @capacitor/core @capacitor/cli @capacitor/android

# Step 2: Build web assets
npm run build

# Step 3: Add Android platform
npx cap add android

# Step 4: Open in Android Studio
npx cap open android
```

In Android Studio:
- Wait for Gradle sync
- Build → Build Bundle(s) / APK(s) → Build APK(s)
- Output: `android/app/build/outputs/apk/debug/app-debug.apk`

---

## 🔐 Authentication & Security

### **How Accounts Work**
- **No pre-seeded accounts** — everyone creates their own
- **Firebase Email/Password** authentication
- **Role assignment** by Super Admin only
- **Secure Firestore rules** enforce access control

### **Super Admin Setup**
1. Change `MASTER_ADMIN_EMAIL` in `constants.ts`
2. Deploy Firestore rules: `npm run firebase:deploy:rules`
3. Sign in with that email address
4. The app automatically grants Super Admin privileges

### **Role Hierarchy**
| Privilege | Regular | Admin | Super Admin |
|-----------|---------|-------|------------|
| Create committees | ✅ (own) | ✅ (own + assigned) | ✅ (all) |
| Block/Unblock users | ❌ | ✅ | ✅ |
| Approve Pro upgrades | ❌ | ❌ | ✅ |
| Access audit logs | ❌ | ❌ | ✅ |

---

## ☁️ Firebase Setup (Required for Authentication)

### **Step 1: Create Firebase Project** (~3 min, free tier)
1. Go to [Firebase Console](https://console.firebase.google.com)
2. Click **"Add project"**
3. Choose region and create

### **Step 2: Enable Authentication**
1. **Build** → **Authentication** → **Sign-in method**
2. Enable **Email/Password**

### **Step 3: Create Firestore Database**
1. **Firestore Database** → **Create database**
2. Select **Production mode**
3. Choose your region

### **Step 4: Register Web App**
1. **Project settings** → **Your apps** → **Add app (Web)**
2. Copy the `firebaseConfig` object

### **Step 5: Configure CommitteePro**
```bash
npm run firebase:setup
# Paste your firebaseConfig when prompted
npm run firebase:check   # Verify setup
```

### **Step 6: Deploy Security Rules**
```bash
npm run firebase:login
npm run firebase:deploy:rules
```

---

## 💳 Pro Plan Activation

### **For Members: Upgrade to Pro**
1. Tap **"Upgrade to Pro"** button
2. View admin's payment methods (Raast, EasyPaisa, JazzCash)
3. Transfer the amount
4. Enter **Transaction ID** from receipt
5. Attach **payment screenshot**
6. Submit for admin approval

### **For Super Admin: Verify Payments**
1. Go to **Admin Panel**
2. View **Pro Requests** queue
3. Review screenshots and transaction IDs
4. Click **"Accept & Promote to PRO"** or **"Reject"**

### **Pro Features**
✅ Unlimited committees (vs. 2 on free)  
✅ No ads  
✅ Automated WhatsApp reminders  
✅ PDF & Excel report exports  
✅ Advanced payment analytics  

---

## 🚀 Deployment

### **Web Hosting (Firebase Hosting)**
```bash
npm run firebase:deploy:hosting
```
Your app will be live at: `https://your-project.web.app`

### **Android App Store (Google Play)**
1. Build signed release APK:
   ```bash
   keytool -genkey -v -keystore committeepro-release.jks \
     -alias committeepro -keyalg RSA -keysize 2048 -validity 10000
   ```
2. Add secrets to GitHub (repository settings):
   - `KEYSTORE_BASE64`
   - `KEYSTORE_PASSWORD`
   - `KEY_ALIAS`
   - `KEY_PASSWORD`
3. Update `.github/workflows/build-apk.yml` to use `assembleRelease`
4. Create release tag: `git tag v1.0.0 && git push origin v1.0.0`
5. Signed APK generated automatically

---

## 📞 Support & Troubleshooting

### **Common Issues**

**❌ "Cannot download APK"**
- Make sure you have [enabled downloads](https://support.google.com/android/answer/9079646)
- Use a file manager to locate the downloaded APK
- Try a different browser (Chrome, Firefox, etc.)

**❌ "Installation failed"**
- Ensure you have enough storage (need ~100 MB free)
- Allow "Install from Unknown Sources" in Android settings
- Try clearing app cache: **Settings → Apps → CommitteePro → Storage → Clear Cache**

**❌ "Firebase not configured"**
- Run `npm run firebase:check`
- Verify all 5 keys are present in `constants.ts`
- Ensure Firestore database is in **Production mode**

**❌ "Can't sign in"**
- Create account on web first at `http://localhost:3000`
- Check Firebase console for authentication errors
- Verify Super Admin email is correct in `constants.ts`

### **Need Help?**
- 📖 [Full Documentation](./PRD.md)
- 🐛 [Report Bugs](https://github.com/aleemshahad/CommitteePro/issues)
- 💬 [Start Discussion](https://github.com/aleemshahad/CommitteePro/discussions)

---

## 📜 License

This project is licensed under the **MIT License** — free to use, modify, and distribute.

```
MIT License
Copyright (c) 2026 Aleem Shahad

Permission is hereby granted, free of charge...
```

---

## 🙏 Contributing

We welcome contributions! Here's how:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to your fork (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

---

## 🌟 Roadmap

- [ ] **WhatsApp integration** for direct payment reminders
- [ ] **Dark mode** for low-light environments
- [ ] **Multi-currency** support (USD, EUR, etc.)
- [ ] **SMS reminders** for offline areas
- [ ] **iOS app** via Capacitor
- [ ] **Cloud sync** across multiple devices
- [ ] **Committee groups** for managing multiple circles

---

## 🙋 Frequently Asked Questions

**Q: Is my data stored online?**  
A: Yes, securely in Firebase Firestore. Only your account email and payment records are stored; financial data stays private.

**Q: Can I use offline?**  
A: The web and mobile apps work offline, but sync requires internet for the first login.

**Q: Is it free?**  
A: Yes! Free plan supports 2 committees with ads. Pro plan (one-time manual payment) removes ads and unlocks unlimited committees.

**Q: Can I export my data?**  
A: Yes! Pro members can export to PDF or Excel. Free plan members can screenshot or request data export from admin.

**Q: How often are updates released?**  
A: New versions are released monthly with bug fixes and new features.

---

**Made with ❤️ by [Aleem Shahad](https://github.com/aleemshahad)**

Last updated: October 5, 2026 | Latest version: **v2.5.1**
