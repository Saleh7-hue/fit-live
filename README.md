# 🧠 FitMind.ai — منصة الصحة الذكية

> Smart Health & Nutrition Platform · منصة الصحة واللياقة بالذكاء الاصطناعي

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-brightgreen?style=for-the-badge&logo=github)](https://Saleh7-hue.github.io/fitmind-ai)
[![Firebase](https://img.shields.io/badge/Database-Firebase-orange?style=for-the-badge&logo=firebase)](https://firebase.google.com)

---

## ✨ المميزات / Features

| الميزة | الوصف |
|--------|-------|
| 🔐 تسجيل دخول حقيقي | Firebase Authentication (Email/Password) |
| 🧠 تحليل الطعام بالذكاء الاصطناعي | AI Food Analysis مع قاعدة بيانات غذائية |
| 💾 حفظ الوجبات | Firestore — بيانات تُحفظ للأبد |
| 📊 لوحة تحكم ديناميكية | Dashboard يتحدث من بيانات المستخدم الحقيقية |
| ⚖️ تتبع القياسات | BMI، الوزن، الطول مع سجل تاريخي |
| 🏋️ خطة التمارين | Weekly Plan + Exercise Categories |
| 🩹 متابعة الإصابات | Injury & Recovery Tracking |
| 📱 Responsive | يعمل على موبايل وتابلت وكمبيوتر |
| 🌙 Dark Login | واجهة تسجيل دخول داكنة احترافية |

---

## 🚀 إعداد Firebase / Firebase Setup

### الخطوة 1 — إنشاء مشروع Firebase

1. افتح [console.firebase.google.com](https://console.firebase.google.com)
2. اضغط **Add project** → أدخل اسم المشروع `fitmind-ai`
3. اضغط **Continue** حتى يتم إنشاء المشروع

### الخطوة 2 — تفعيل Authentication

1. من القائمة الجانبية: **Build → Authentication**
2. اضغط **Get started**
3. اختر **Email/Password** → فعّله (Enable) → **Save**
4. اختياري: فعّل **Anonymous** للـ Face ID demo

### الخطوة 3 — إنشاء Firestore Database

1. من القائمة الجانبية: **Build → Firestore Database**
2. اضغط **Create database**
3. اختر **Start in test mode** (مؤقتاً للتطوير)
4. اختر أقرب منطقة → **Enable**

### الخطوة 4 — الحصول على إعدادات المشروع

1. اضغط على أيقونة ⚙️ **Project Settings**
2. انزل لقسم **Your apps** → اضغط `</>` (Web)
3. أدخل اسم التطبيق `FitMind Web` → **Register app**
4. **انسخ** `firebaseConfig` الذي يظهر

### الخطوة 5 — تحديث الكود

افتح ملف `index.html` وابحث عن هذا القسم:

```javascript
const firebaseConfig = {
  apiKey:            "YOUR_API_KEY",
  authDomain:        "YOUR_PROJECT_ID.firebaseapp.com",
  projectId:         "YOUR_PROJECT_ID",
  storageBucket:     "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId:             "YOUR_APP_ID"
};
```

**استبدله** بالـ config الذي نسخته من Firebase Console.

### الخطوة 6 — Firestore Security Rules

في **Firestore → Rules** ضع هذه القواعد:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

ثم اضغط **Publish**.

---

## 📤 رفع على GitHub / Deploy to GitHub

### الطريقة 1 — عبر GitHub Desktop (الأسهل)

1. حمّل [GitHub Desktop](https://desktop.github.com)
2. افتح التطبيق → **File → New Repository**
3. اسم المستودع: `fitmind-ai`
4. اضغط **Create Repository**
5. انسخ ملف `index.html` داخل مجلد المستودع
6. اضغط **Commit to main** → **Publish repository**

### الطريقة 2 — عبر Terminal / Command Line

```bash
# 1. أنشئ مجلد جديد
mkdir fitmind-ai && cd fitmind-ai

# 2. ضع ملف index.html داخله

# 3. ابدأ git
git init
git add .
git commit -m "🚀 Initial commit — FitMind.ai"

# 4. ربط بـ GitHub (غيّر USERNAME)
git remote add origin https://github.com/Saleh7-hue/fitmind-ai.git
git branch -M main
git push -u origin main
```

### تفعيل GitHub Pages

1. افتح المستودع على GitHub
2. اضغط **Settings** → **Pages**
3. من **Source** اختر: **Deploy from a branch**
4. Branch: **main** → Folder: **/ (root)** → **Save**
5. بعد دقيقتين يكون موقعك جاهز على:
   ```
   https://Saleh7-hue.github.io/fitmind-ai
   ```

---

## 🗂️ هيكل المشروع / Project Structure

```
fitmind-ai/
│
├── index.html          ← التطبيق الكامل (HTML + CSS + JS)
└── README.md           ← هذا الملف
```

> المشروع ملف واحد فقط — لا يحتاج build tools أو npm

---

## 🛡️ ملاحظة أمان / Security Note

مفاتيح Firebase Web API آمنة للنشر العام على GitHub. الأمان الحقيقي يأتي من **Firestore Security Rules** التي تضمن أن كل مستخدم يصل لبياناته فقط.

---

## 🔧 خارطة التطوير / Roadmap

- [ ] تحليل صور الطعام بـ Vision AI حقيقي
- [ ] إشعارات يومية (Firebase Cloud Messaging)
- [ ] مزامنة مع Apple Health / Google Fit
- [ ] تقارير PDF قابلة للتحميل
- [ ] نسخة موبايل (PWA)

---

## 👨‍💻 المطور / Developer

**Saleh7-hue** · Built with ❤️ using Firebase + Vanilla JS

---

*FitMind.ai — Smart Health Platform · منصة الصحة الذكية*
