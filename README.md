[Uploading index.html…]()
node_modules/
dist-installer/
.DS_Store

<!doctype html>
<html lang="fa" dir="rtl">
<head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1.0"><title>MarketDesk</title></head>
<body><div id="root"></div><script type="module" src="/src/main.jsx"></script></body>
</html>
{
  "name": "marketdesk",
  "version": "0.1.0",
  "description": "Private Windows market dashboard with paper trading",
  "main": "electron/main.js",
  "scripts": {
    "start": "electron .",
    "build": "electron-builder --win",
    "dev": "vite --host 127.0.0.1"
  },
  "devDependencies": {
    "electron": "^33.2.0",
    "electron-builder": "^25.1.8",
    "vite": "^6.0.5"
  },
  "build": {
    "appId": "local.marketdesk.app",
    "productName": "MarketDesk",
    "directories": { "output": "dist-installer" },
    "files": ["electron/**/*", "src/**/*", "index.html", "package.json"],
    "win": { "target": "nsis" }
  }
}
# MarketDesk — نسخه اولیه ویندوز

این پروژه یک نمونه دسکتاپ خصوصی برای داشبورد بازارها و معاملات آزمایشی است.

## وضعیت فعلی
- رابط فارسی و راست‌چین
- بازارهای نمونه: طلا، ارز، سکه، نفت، شاخص، رمزارز و نقره
- نمودار نمایشی (ساختگی)
- ثبت‌نام/ورود محلی با ایمیل و رمز عبور (صرفاً نمونه؛ رمزها در این نسخه هش نمی‌شوند)
- کیف پول مجازی و معاملات Paper Trading
- ذخیره محلی داده‌ها
- محل تنظیم آدرس منبع قیمت

## مهم
**قیمت‌های فعلی زنده نیستند.** تغییرات خودکار صرفاً شبیه‌سازی هستند. این نسخه به TGJU وصل نشده است، چون برای اتصال قابل‌اتکا باید API/روش دسترسی مجاز، ساختار پاسخ و شرایط استفاده مشخص باشد. آدرس صفحه اصلی سایت به‌تنهایی API نیست.

این نمونه برای حساب واقعی، داده حساس یا انتشار عمومی آماده نیست. برای نسخه امن باید:
- احراز هویت سمت سرور با رمزهای هش‌شده (Argon2id/bcrypt)، نشست امن و بازیابی حساب
- سرور خصوصی و پایگاه داده
- API رسمی/مجاز داده بازار و مدیریت کلیدها در سمت سرور
- اعتبارسنجی سفارش‌ها، ثبت رویدادها، پشتیبان‌گیری و کنترل دسترسی
اضافه شود.

## اجرا در ویندوز
1. Node.js نسخه LTS را نصب کنید.
2. پوشه پروژه را استخراج کنید.
3. در پوشه پروژه، ترمینال باز کنید و اجرا کنید:

```bash
npm install
npm start
```

## ساخت فایل نصب
```bash
npm install
npm run build
```
فایل نصب در پوشه `dist-installer` ساخته می‌شود.

## اتصال TGJU
در نسخه بعد، پس از مشخص شدن API رسمی یا مجاز، یک adapter در سمت سرور اضافه می‌کنیم. از scraping غیرمجاز یا دور زدن محدودیت‌های سایت استفاده نکنید.
