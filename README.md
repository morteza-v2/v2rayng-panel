

پنل فروش **V2Ray** یکی از روش‌های مرسوم برای ارائه سرویس‌های وی‌پی‌ان به کاربران است. این آموزش مراحل پایه‌ای برای راه‌اندازی پنل V2Ray را توضیح می‌دهد.

---

### ۱. پیش‌نیازها
قبل از شروع، مطمئن شوید موارد زیر را دارید:
- **سرور مجازی (VPS):** با سیستم‌عامل **Ubuntu 22.04** یا مشابه.
- **دسترسی روت** یا کاربری با دسترسی sudo.
- **دامنه یا زیردامنه:** برای دسترسی راحت کاربران.
- **مهارت‌های پایه مدیریت سرور لینوکس.**

---

### ۲. نصب و تنظیم V2Ray
#### مرحله اول: به‌روزرسانی سرور
```bash
sudo apt update && sudo apt upgrade -y
```

#### مرحله دوم: نصب V2Ray
برای نصب V2Ray، می‌توانید از اسکریپت رسمی استفاده کنید:
```bash
bash <(curl -L https://github.com/v2fly/fhs-install-v2ray/raw/master/install-release.sh)
```

#### مرحله سوم: تنظیم فایل کانفیگ
فایل کانفیگ V2Ray در مسیر زیر قرار دارد:
```bash
/etc/v2ray/config.json
```
نمونه کانفیگ:
```json
{
  "inbounds": [{
    "port": 443,
    "protocol": "vmess",
    "settings": {
      "clients": [{
        "id": "UUID-اینجا-قرار-بگیرد",
        "alterId": 64
      }]
    },
    "streamSettings": {
      "network": "ws",
      "wsSettings": {
        "path": "/v2ray"
      }
    }
  }],
  "outbounds": [{
    "protocol": "freedom",
    "settings": {}
  }]
}
```
UUID را با مقدار تولید شده جایگزین کنید:
```bash
uuidgen
```

---

### ۳. نصب پنل مدیریت (مانند X-UI یا V2board)
#### نصب X-UI
1. اسکریپت نصب را اجرا کنید:
   ```bash
   bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
   ```
2. پس از نصب، پنل را با دستور زیر راه‌اندازی کنید:
   ```bash
   x-ui
   ```
3. آدرس ورود به پنل:
   ```
   http://YOUR_SERVER_IP:54321
   ```
   - نام کاربری: `admin`
   - رمز عبور: `admin`

#### نصب V2board (پنل پیشرفته)
1. نصب وب‌سرور Nginx و PHP:
   ```bash
   sudo apt install nginx php php-fpm php-mysql mariadb-server -y
   ```
2. دانلود V2board از مخزن رسمی:
   ```bash
   git clone https://github.com/v2board/v2board.git
   ```
3. تنظیمات مربوط به دامنه و دیتابیس را انجام دهید.

---

### ۴. تنظیم دامنه با SSL
برای ایجاد ارتباط امن:
1. نصب **Certbot**:
   ```bash
   sudo apt install certbot python3-certbot-nginx -y
   ```
2. دریافت گواهینامه SSL:
   ```bash
   sudo certbot --nginx -d yourdomain.com
   ```

---

### ۵. مدیریت کاربران و فروش
با استفاده از پنل نصب‌شده (مانند X-UI یا V2board)، می‌توانید:
- حساب‌های کاربری تعریف کنید.
- پلن‌های فروش تنظیم کنید.
- وضعیت مصرف کاربران را نظارت کنید.

---

### ۶. تبلیغات و پشتیبانی
- از **کانال تلگرام** برای معرفی خدمات استفاده کنید.
- برای پشتیبانی، ربات تلگرامی راه‌اندازی کنید یا از ID پشتیبانی استفاده کنید.

---

### تماس با ما : با رعایت این مراحل، پنل V2Ray شما آماده استفاده است. اگر به کمک بیشتری نیاز داشتید، می‌توانید با ایدی تلگرام @v2makers_admin در ارتباط باشید.
