# Speedizer — اسپیدایزر 🚀

<div align="center">

<img src="docs/icon.png" width="128" alt="Speedizer Icon"/>

**شارپ، سبک و سریع — شتاب‌دهنده و پاک‌ساز رم اندروید**

[![Platform](https://img.shields.io/badge/platform-Android-green.svg)](https://www.android.com)
[![API](https://img.shields.io/badge/API-23%2B-brightgreen.svg)](https://android-arsenal.com/api?level=23)
[![Language](https://img.shields.io/badge/language-Java-orange.svg)](https://www.java.com)
[![Dependencies](https://img.shields.io/badge/dependencies-0-blue.svg)](#)
[![License: MIT](https://img.shields.io/badge/license-MIT-lightgrey.svg)](LICENSE)

</div>

---

## 🇮🇷 معرفی

**اسپیدایزر (Speedizer)** یک برنامه اندرویدی متن‌باز برای پاک‌سازی و شتاب‌دهی گوشی است. این برنامه مصرف رم را به‌صورت لحظه‌ای رصد می‌کند، با یک لمس پردازش‌های پس‌زمینه را پاک می‌سازد و با **سرویس دائمی + زمان‌بند خودکار** مانع هنگ‌کردن گوشی شما می‌شود.

## ✨ امکانات

- ⚡ **بوست رم با یک لمس** — پاک‌سازی پردازش‌های پس‌زمینه و آزادسازی حافظه با نمایش میزان رم آزادشده
- 🔄 **حلقه پیشرفت دایره‌ای زنده** — نمایش درصد مصرف رم با انیمیشن روان
- 📊 **کارت‌های آماری** — رم در حال استفاده، پردازش‌های فعال، آزادسازی امروز و آخرین پاک‌سازی
- 🛡️ **سرویس دائمی پس‌زمینه** — مانیتورینگ لحظه‌ای رم با اعلان دائمی و دکمه «همین حالا پاک‌سازی کن»
- ⏰ **پاک‌سازی خودکار زمان‌بندی‌شده** — هر ۱۵ / ۳۰ / ۶۰ دقیقه + پاک‌سازی اضطراری هنگام پر شدن رم (بالای ۸۵٪)
- 🌙 **سوییچ تم** — جابه‌جایی بین حالت **آبی و سفید** و **آبی و سیاه** با یک لمس
- 🔔 **اجرای خودکار با روشن شدن گوشی** (قابل خاموش‌کردن)
- 🇮🇷 **رابط کاربری کامل فارسی** (راست‌چین) با فونت وزیرمتن + پشتیبانی از اعداد فارسی
- 📦 **صفر وابستگی خارجی** — فقط APIهای خالص اندروید؛ APK نهایی فقط حدود ۲۰۰ کیلوبایت!

## 📱 نصب

آخرین نسخه APK را از بخش [Releases](../../releases) دانلود کنید (یا فایل `Speedizer-v1.0.0.apk` تحویل‌شده)، سپس:

1. فایل را باز کنید و در صورت پرسش، «نصب از منابع ناشناس» را فعال کنید
2. پس از نصب، اجازه **اعلان‌ها** را تأیید کنید تا مانیتورینگ فعال شود
3. دکمه **شتاب‌دهی گوشی** را بزنید و لذت ببرید ✨

> پیش‌نیاز: اندروید ۶ (Marshmallow) به بالا

## 🛠 ساخت از سورس

### با Android Studio
پروژه را Clone کنید و مستقیماً در Android Studio (نسخه Hedgehog یا جدیدتر) باز کنید:

```bash
git clone https://github.com/USERNAME/Speedizer.git
```

### با خط فرمان (Gradle Wrapper)

```bash
./gradlew assembleRelease
```

خروجی در `app/build/outputs/apk/release/` ساخته می‌شود (برای نصب نیاز به امضا دارد — یا از `assembleDebug` استفاده کنید).

### بدون Gradle (aapt2 خالص)
اسکریپت ساخت مستقیم بدون Gradle نیز موجود است (نیازمند Android SDK با build-tools و platform android-34):

```bash
./scripts-local/build_apk.sh   # در صورت وجود SDK
```

## 📁 ساختار پروژه

```
Speedizer/
├── app/src/main/
│   ├── java/com/speedizer/app/
│   │   ├── MainActivity.java        # داشبورد اصلی (حلقه رم + دکمه بوست + کارت‌ها)
│   │   ├── SettingsActivity.java    # تنظیمات (تم، پاک‌سازی خودکار، بوت)
│   │   ├── BoostService.java        # سرویس Foreground مانیتورینگ رم
│   │   ├── BoostEngine.java         # موتور پاک‌سازی و اندازه‌گیری رم
│   │   ├── RamRingView.java         # ویو سفارشی حلقه پیشرفت
│   │   ├── CleanAlarmReceiver.java  # زمان‌بند پشتیبان (AlarmManager)
│   │   ├── BootReceiver.java        # اجرای خودکار بعد از بوت
│   │   ├── ThemePrefs.java          # ذخیره تم و تنظیمات
│   │   ├── Fonts.java               # اعمال فونت وزیرمتن
│   │   └── Fa.java                  # تبدیل اعداد فارسی و قالب‌بندی
│   ├── res/
│   │   ├── layout/                  # چیدمان‌های راست‌چین
│   │   ├── values/                  # رنگ‌ها، تم‌ها و متون فارسی
│   │   ├── font/                    # وزیرمتن Regular / Bold
│   │   └── mipmap-*/                # آیکون لانچر (adaptive + legacy)
│   └── AndroidManifest.xml
├── keystore/speedizer.jks           # کلید امضای نسخه‌های فعلی
├── docs/icon.png                    # لوگو برای README
└── build.gradle / settings.gradle
```

## 🔧 نحوه کار فنی

| بخش | مکانیزم |
|---|---|
| اندازه‌گیری رم | `ActivityManager.MemoryInfo` |
| آزادسازی حافظه | `ActivityManager.killBackgroundProcesses()` با مجوز `RESTART_PACKAGES` |
| مانیتورینگ دائمی | سرویس Foreground با اعلان LOW-importance و تیک هر ۳۰ ثانیه |
| زمان‌بندی خودکار | حلقه داخلی سرویس + `AlarmManager.setAndAllowWhileIdle` به‌عنوان پشتیبان |
| اجرای پس از بوت | `BOOT_COMPLETED` receiver |
| سوییچ تم | دو تم سفارشی (Light/Dark) با attributeهای سفارشی + `setTheme()` |

## 📝 نکات

- در اندروید ۱۲ به بالا، محدودیت‌های سیستمی روی kill کردن پردازش‌های سایر برنامه‌ها سخت‌گیرانه‌تر است؛ اسپیدایزر بهترین اثر را روی اندروید ۶ تا ۱۱ دارد و در نسخه‌های جدیدتر علاوه بر آزادسازی رم، کش‌های سیستمی را نیز فشرده می‌کند.
- فایل `keystore/speedizer.jks` (رمز: `speedizer2024`) صرفاً برای امضای نسخه‌های توسعه قرار گرفته است؛ برای انتشار عمومی کلید شخصی خودتان را بسازید.

## 🤝 مشارکت

Pull Requestها خوش‌آمدند! برای تغییرات بزرگ لطفاً ابتدا یک Issue باز کنید.

## 📄 مجوز

این پروژه تحت مجوز [MIT](LICENSE) منتشر شده است.

---

<div align="center">

**Speedizer** — Built with ❤️ for faster phones

</div>
