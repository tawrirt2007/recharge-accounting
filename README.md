# 📱 برنامج محاسبة بطاقات التعبئة - المغرب

برنامج متكامل لإدارة مبيعات ومخزون بطاقات التعبئة (Maroc Telecom, INWI, Orange, Meditel) في المغرب.

## ✨ الميزات

- **تسجيل المبيعات**: اختيار المشغل، القيمة، الكمية، أسعار الشراء/البيع
- **حسابات تلقائية**: إجمالي البيع، إجمالي الشراء، الربح المتوقع
- **إدارة المخزون**: إضافة رصيد، تتبع المخزون الحالي مع تنبيهات النقص
- **تقارير مفلترة**: حسب المشغل والفترة (يوم، أسبوع، شهر)
- **حفظ محلي**: البيانات محفوظة في المتصفح (localStorage) - لا تضيع عند الإغلاق
- **يعمل أوفلاين**: بفضل Service Worker
- **قابل للتثبيت**: PWA جاهز للتحويل لتطبيق جوال (APK)

## 👨‍💻 المطور

**محمد القادري**
📞 للتواصل: **06 80 89 83 84** | [+212 6 80 89 83 84](tel:+212680898384)

---

## 🚀 التشغيل السريع

### 1. التشغيل المباشر
افتح ملف `morocco-recharge-accounting.html` في أي متصفح حديث.

### 2. التشغيل كخادم محلي (موصى للميزات الكاملة)

```bash
# باستخدام Python
python -m http.server 8000

# أو باستخدام Node.js
npx serve .

# أو باستخدام PHP
php -S localhost:8000
```

ثم افتح `http://localhost:8000/morocco-recharge-accounting.html`

---

## 📦 ملفات المشروع

```
├── morocco-recharge-accounting.html   # التطبيق الرئيسي
├── manifest.json                       # إعدادات PWA
├── sw.js                              # Service Worker (للعمل أوفلاين)
├── icon.svg                           # أيقونة التطبيق (متجهة)
├── generate-icons.html                # أداة توليد أيقونات PNG بجميع الأحجام
└── README.md                          # هذا الملف
```

---

## 🔧 تحويل التطبيق إلى APK (تطبيق أندرويد)

### الطريقة الأسهل: **PWA Builder** (لا تحتاج تثبيت برامج)

1. **ارفع المشروع على استضافة تدعم HTTPS:**
   - **GitHub Pages** (مجاني): ارفع الملفات على مستودع GitHub، فعّل Pages من Settings
   - **Netlify** (مجاني): اسحب مجلد المشروع على netlify.com/drop
   - **Vercel** (مجاني): اربط مستودع GitHub أو ارفع عبر CLI

2. **ابنِ الـ APK:**
   - اذهب إلى [PWABuilder.com](https://www.pwabuilder.com/)
   - أدخل رابط موقعك (مثلاً: `https://username.github.io/repo/`)
   - اضغط **Start** → انتظر التحليل
   - اختر **Android** → **Generate**
   - حمل ملف **APK** أو **AAB** (للمتجر)

### طريقة Bubblewrap (تتطلب Node.js)

```bash
# تثبيت الأداة
npm i -g @bubblewrap/cli

# تهيئة المشروع (استبدل بالرابط الفعلي)
bubblewrap init --manifest=https://your-domain.com/manifest.json

# بناء الـ APK
bubblewrap build
```

ستجد ملف APK في مجلد `app/release/`

### طريقة Capacitor (للمطورين)

```bash
# إنشاء مشروع Capacitor
npm init @capacitor/app my-recharge-app
cd my-recharge-app

# نسخ ملفات المشروع إلى مجلد www
# (انسخ morocco-recharge-accounting.html كـ index.html، وباقي الملفات)

# إضافة منصة أندرويد
npm install @capacitor/core @capacitor/android
npx cap add android

# المزامنة والبناء
npx cap sync
npx cap open android
```

في **Android Studio**: `Build` → `Build Bundle(s) / APK(s)` → `Build APK(s)`

---

## 🎨 توليد الأيقونات

افتح `generate-icons.html` في المتصفح:
1. اضغط **"رسم جميع الأيقونات"**
2. اضغط **"تحميل جميع الأيقونات"**
3. ستحصل على ملفات: `icon-72.png` إلى `icon-512.png`

أو استخدم أدوات أونلاين:
- [PWA Asset Generator](https://www.pwabuilder.com/imageGenerator)
- [Maskable App](https://maskable.app/editor)

---

## 📋 متطلبات PWA للعمل الكامل

| الميزة | المطلوب |
|----------|---------|
| التثبيت على الجوال | HTTPS + manifest.json + أيقونات |
| العمل أوفلاين | HTTPS + Service Worker (sw.js) |
| تحديث تلقائي | HTTPS + Service Worker |
| إشعارات | HTTPS + VAPID keys (إضافي) |

**ملاحظة:** `localhost` يعمل للاختبار، لكن للتثبيت الحقيقي على أجهزة المستخدمين **يجب HTTPS**.

---

## 💾 آلية حفظ البيانات

- **المبيعات**: `localStorage` تحت مفتاح `sales`
- **المخزون**: `localStorage` تحت مفتاح `stock`
- البيانات تبقى محفوظة حتى عند إغلاق المتصفح أو إعادة تشغيل الهاتف
- لا يوجد خادم خارجي - خصوصية تامة

---

## 🔄 تحديث التطبيق

1. عدل الملفات محلياً
2. ارفع التحديثات للاستضافة (GitHub/Netlify/Vercel)
3. المستخدمون سيحصلون على التحديث تلقائياً عند الفتح القادم
4. Service Worker سيتعامل مع التخزين المؤقت بذكاء

---

## 📱 اختبار على الجوال

### Chrome DevTools:
1. افتح DevTools (`F12`)
2. اضغط أيقونة **Device Toolbar** (`Ctrl+Shift+M`)
3. اختر جهاز جوال
4. اختبر التثبيت من قائمة Chrome → "تثبيت التطبيق"

### على جهاز حقيقي:
1. افتح رابط الموقع على Chrome/Android
2. سيظهر بانر "تثبيت التطبيق" تلقائياً
3. أو من قائمة المتصفح → "إضافة للشاشة الرئيسية"

---

## ⚠️ استكشاف الأخطاء

| المشكلة | الحل |
|----------|-------|
| لا يظهر خيار التثبيت | تأكد من HTTPS، manifest.json صحيح، أيقونات موجودة |
| لا يعمل أوفلاين | تحقق من تسجيل Service Worker في Console |
| البيانات لا تحفظ | تأكد من تفعيل localStorage في إعدادات المتصفح |
| خطأ في البناء | تحقق من صحة JSON في manifest.json |

---

## 📄 الترخيص

جميع الحقوق محفوظة © 2025 - **محمد القادري**

هذا البرنامج مُصمم للاستخدام الشخصي والتجاري في المغرب.
يمنع إعادة توزيع الكود المصدري بدون إذن.

---

## 📞 الدعم الفني

للاستفسارات، طلب ميزات، أو الإبلاغ عن أخطاء:
- **الهاتف/واتساب**: 06 80 89 83 84
- **المطور**: محمد القادري

---
*تم التطوير بـ ❤️ للمغرب*