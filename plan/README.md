# Planvia

اپلیکیشن Planvia — برنامه‌ریز روزانه، پومودورو، یادداشت، اهداف و یادگیری.
این پروژه با React + Vite ساخته شده و با Capacitor به اندروید (APK) تبدیل می‌شه.

## ساختار پروژه

```
├── src/App.jsx          کد اصلی اپلیکیشن
├── src/main.jsx         نقطه‌ی ورود React
├── index.html
├── resources/icon.png   آیکون اپلیکیشن (۱۰۲۴×۱۰۲۴)
├── resources/splash.png اسپلش‌اسکرین
├── capacitor.config.json
└── .github/workflows/build-apk.yml   ورک‌فلوی ساخت خودکار APK
```

## گرفتن APK (بدون نیاز به نصب چیزی روی سیستم خودتون)

1. یک ریپازیتوری جدید توی گیت‌هاب بسازید.
2. محتوای این zip رو داخلش push کنید (یا آپلود کنید).
3. برید به تب **Actions** توی گیت‌هاب — ورک‌فلوی «Build Android APK» خودش اجرا می‌شه
   (روی هر پوش به شاخه‌ی `main`/`master`، یا با زدن دکمه‌ی Run workflow).
4. بعد از اتمام (چند دقیقه طول می‌کشه)، وارد اجرای همون ورک‌فلو بشید،
   پایین صفحه بخش **Artifacts** یه فایل به اسم `planvia-debug-apk` می‌ذاره — دانلودش کنید،
   داخلش `app-debug.apk` هست که مستقیم روی گوشی اندروید قابل نصبه.

## توسعه‌ی محلی (اختیاری)

```bash
npm install
npm run dev          # پیش‌نمایش وب
npm run build         # ساخت خروجی وب در dist/
npx cap add android    # فقط بار اول
npx @capacitor/assets generate --android
npx cap sync android
npx cap open android   # باز کردن در Android Studio برای اجرا/دیباگ
```

## نکته درباره‌ی آیکون

آیکون از `resources/icon.png` توسط ابزار `@capacitor/assets` به‌صورت خودکار
برای همه‌ی رزولوشن‌های اندروید (mipmap) تولید می‌شه؛ نیازی به ساخت دستی نیست.

## نکته درباره‌ی امضای APK

خروجی این ورک‌فلو یک **debug APK** هست که مستقیم قابل نصبه ولی برای انتشار در
Google Play باید بیلد **release** امضا‌شده بسازید (نیاز به keystore داره).
اگه لازم شد بگید تا ورک‌فلو رو برای بیلد release هم آماده کنم.
