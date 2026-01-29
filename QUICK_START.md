# 🚀 البدء السريع - تطبيق نديم

دليل سريع لتشغيل التطبيق في 5 دقائق!

## ✅ المتطلبات

قبل البدء، تأكد من توفر:
- ✅ Android Studio Hedgehog أو أحدث
- ✅ JDK 17
- ✅ حساب Gmail (لـ Firebase)
- ✅ اتصال بالإنترنت

## 📥 الخطوة 1: استنساخ المشروع

```bash
git clone https://github.com/YourUsername/Nadeem.git
cd Nadeem
```

## 🔥 الخطوة 2: إعداد Firebase (5 دقائق)

### 2.1 إنشاء المشروع
1. اذهب إلى: https://console.firebase.google.com/
2. انقر: **Add project** → أدخل اسم "Nadeem" → **Create project**

### 2.2 إضافة Android App
1. انقر على أيقونة **Android**
2. اكتب اسم الحزمة: `awab.quran.ar` ⚠️ **يجب أن يكون مطابقاً**
3. **Download google-services.json**
4. ضعه في: `Nadeem/app/google-services.json`

### 2.3 تفعيل الخدمات (3 نقرات فقط!)

**Authentication:**
```
Firebase Console → Authentication → Get started → Email/Password → Enable → Save
```

**Firestore:**
```
Firebase Console → Firestore Database → Create database → Test mode → Enable
```

**Storage:**
```
Firebase Console → Storage → Get started → Test mode → Done
```

### 2.4 تطبيق القواعد الأمنية

**Firestore Rules** (انسخ والصق):

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
    match /recitations/{recitationId} {
      allow read, write: if request.auth != null;
    }
  }
}
```

**Storage Rules** (انسخ والصق):

```javascript
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /recitations/{userId}/{allPaths=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## 💻 الخطوة 3: تشغيل التطبيق

1. **افتح Android Studio**
   ```
   File → Open → اختر مجلد Nadeem
   ```

2. **انتظر Gradle Sync** (تلقائياً)

3. **شغّل التطبيق**
   - وصّل جهاز Android أو شغّل المحاكي
   - اضغط على زر **Run** (▶️) أو `Shift + F10`

## 🎉 الخطوة 4: اختبار التطبيق

### إنشاء حساب تجريبي:
1. انقر: **إنشاء حساب جديد**
2. الاسم: `اختبار`
3. البريد: `test@example.com`
4. كلمة المرور: `123456`
5. انقر: **إنشاء الحساب**

### تجربة الميزات:
- ✅ تسجيل الدخول
- ✅ الصفحة الرئيسية
- ✅ بدء التسميع
- ✅ الملف الشخصي

## ❓ مشاكل شائعة

### المشكلة: "google-services.json not found"
**الحل**: 
```bash
# تأكد من المسار الصحيح
Nadeem/app/google-services.json  ✅
Nadeem/google-services.json      ❌ خطأ!
```

### المشكلة: "Gradle Sync Failed"
**الحل**:
```bash
./gradlew clean
./gradlew build --refresh-dependencies
```

### المشكلة: "FirebaseApp not initialized"
**الحل**:
1. ✅ تحقق من وجود google-services.json
2. ✅ تحقق من اسم الحزمة: `awab.quran.ar`
3. ✅ Build → Clean Project → Rebuild Project

## 📚 موارد إضافية

- 📖 [README الكامل](README.md)
- 🔥 [دليل Firebase المفصل](FIREBASE_SETUP.md)
- 🤝 [دليل المساهمة](CONTRIBUTING.md)

## 🆘 تحتاج مساعدة؟

- 💬 افتح [Issue](https://github.com/YourUsername/Nadeem/issues)
- 📧 راسلنا: your.email@example.com

---

**🎊 تهانينا! أنت الآن جاهز للبدء!**

بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ
