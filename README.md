# 🚨 فاجعه امنیتی در ربات‌های ناشناس تلگرام:

سلام به همه رفقا! 👋

تا حالا شده تو ربات‌های چت ناشناس به یکی پیام بدین و فکر کنین هویت‌تون کاملاً مخفیه؟ 🤔 خب، یه خبر بد براتون دارم: به احتمال ۹۹٪، طرف مقابل می‌تونه با چندتا کلیک ساده بفهمه شما کی هستین! 

اینجا می‌خوام پرده از یه گاف امنیتی خیلی بزرگ بردارم که برنامه‌نویس‌های این ربات‌ها دادن و باعث شده یه بازار سیاه راه بیفته که توش هویت شما رو به پول می‌فروشن. 💸

---

## اول بفهمیم داستان چیه: دکمه‌های شیشه‌ای و `Callback` 🤓

وقتی تو یه ربات ناشناس پیام می‌گیری، زیرش چندتا دکمه خوشگل می‌بینی مثل "پاسخ دادن" یا "بلاک کردن". به اینا میگن **دکمه‌های شیشه‌ای** (Inline Buttons).

![ایناها، از همین دکمه‌ها حرف می‌زنم](https://private-user-images.githubusercontent.com/118823267/479613717-c82cdbf6-d9fd-44f3-a3b3-4e621cef8f75.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTU2MjE4MzIsIm5iZiI6MTc1NTYyMTUzMiwicGF0aCI6Ii8xMTg4MjMyNjcvNDc5NjEzNzE3LWM4MmNkYmY2LWQ5ZmQtNDRmMy1hM2IzLTRlNjIxY2VmOGY3NS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwODE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDgxOVQxNjM4NTJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0xNjc5Nzg0NjRmYTIzMDRkMTgzMWFhY2IzZDEwYjkyN2E5MDFkMjhmMzY3NTE1NGYwYjM2ZjJjZjk5NTQyMWZhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.SpP7EyMUwoDV8SMxYII3Y-lTpAsEgpjwJ7hLiBpIuds)

حالا وقتی روی یکی از این دکمه‌ها می‌زنی، یه چیزی به اسم **کال‌بک کوئری (Callback Query)** برای ربات فرستاده می‌شه. فکر کن یه نامه محرمانه می‌فرستی به ربات و توش می‌گی: «آهای ربات! من روی دکمه "پاسخ" برای این پیام کلیک کردم». 💌

مهم‌ترین قسمت این نامه، یه تیکه کد به اسم `callback_data` هست که برنامه‌نویس توش یه سری اطلاعات می‌ذاره تا ربات بفهمه باید چیکار کنه.

---

## 💣 گاف بزرگ کجاست؟ پخش کردن آیدی شما!

مشکل دقیقاً همین‌جاست. برنامه‌نویس‌های عزیز (که انگار یکم عجله داشتن 🏃‍♂️)، برای اینکه ربات بفهمه جواب شما رو باید برای کی بفرسته، خیلی راحت میان **چت آیدی (Chat ID)** طرف مقابل رو مستقیم می‌ذارن توی همون `callback_data`.

یعنی دکمه "پاسخ" شما، مثل یه بسته پست عمل می‌کنه که روش آدرس خونه فرستنده نوشته شده! 🏡

```json
// اینجوری گند می‌زنن به امنیت:
{
  "text": "پاسخ بده 📩",
  "callback_data": "reply_123456789" // این عدده همون آیدی طرفه! لو رفتی !
}
```

### چجوری مچ‌شونو می‌گیرن؟ خیلی ساده! 🕵️‍♂️

کافیه با تلگرام دسکتاپ از چت با ربات یه خروجی (Export) بگیری. بعد فایل HTML رو که باز کنی، مثل روز روشنه که چت آیدی طرفِ مقابل چنده. به همین راحتی!

![بفرما! آیدی طرف مثل هلو افتاده بیرون!](https://private-user-images.githubusercontent.com/118823267/479616585-1244fde8-1c66-490d-ab30-4ea62b8e84cd.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTU2MjE4MzIsIm5iZiI6MTc1NTYyMTUzMiwicGF0aCI6Ii8xMTg4MjMyNjcvNDc5NjE2NTg1LTEyNDRmZGU4LTFjNjYtNDkwZC1hYjMwLTRlYTYyYjhlODRjZC5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwODE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDgxOVQxNjM4NTJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hODZiMzcxNWNhNTcwMGNjOWJiYjI5N2VkYmE4ZTZjMWNiYTQzNWUwNGI4OThiN2U2NmJlZWE3MmQyNjhjYjVhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.cXuBX58OeBYg5siM6hV6WCnvYLXfsPrbpbSKjO8R9-Q)

بعدش هم با اون چت آیدی، پیدات می‌کنن(چون هر اکانت تلگرامی یه چت ایدی داره که مثل یوزر نیم قابل تغییر نیست و همیشه یه عدد میمونه). یه عده هم از همین راه دارن پول درمیارن و هویت شما رو می‌فروشن. 

---

## اونایی که فکر می‌کنن زرنگن: کدگذاری با `Base64` 🤡

یه عده از برنامه‌نویس‌ها گفتن خب بیایم آیدی رو یه جوری بپوشونیم که کسی نبینه! چیکار کردن؟ اومدن با `Base64` کدگذاریش کردن.

```json
// مثلاً خیلی امنش کردن الان:
{
  "text": "پاسخ بده 📩",
  "callback_data": "reply_MTIzNDU2Nzg5" // این رشته عجیب غریب همون آیدی قبلیه!
}
```

این کار مثل اینه که روی یه بسته پستی مهم، آدرس رو به(یه زبان دیگه)زبان مرُغی بنویسی! 🐔 هر بچه‌ای هم می‌تونه با یه ابزار آنلاین ساده دیکُدش کنه و به آیدی اصلی برسه. پس اینم امنیت نداره!

![دو ثانیه هم طول نکشید تا آیدی اصلی در بیاد!](https://private-user-images.githubusercontent.com/118823267/479617379-c82f8b00-2d10-44a1-bcf0-42251338138f.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTU2MjE4MzIsIm5iZiI6MTc1NTYyMTUzMiwicGF0aCI6Ii8xMTg4MjMyNjcvNDc5NjE3Mzc5LWM4MmY4YjAwLTJkMTAtNDRhMS1iY2YwLTQyMjUxMzM4MTM4Zi5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwODE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDgxOVQxNjM4NTJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02NjBiYjZlY2VhMjhmN2NhYjc3MWJjNjgzNDNkMTIxYWQ1MDU0Njg0ZDhmYThjYTEzZGEyN2JiMWE0YmQ2NjI5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.9fx91aB-wKOhaHfdUwRqx9EFmjQP_0fQbxzdXHdUsaA)

---

## ✅ راه‌حل‌های درست و حسابی چیه پس؟

**قانون اول امنیت: اطلاعات حساس کاربر رو هیچوقت نفرست برای خودش!**

برای اینکه یه ربات ناشناس واقعی داشته باشیم، دو تا راه اصلی وجود داره:

### ۱. استفاده از دیتابیس 🛡️

این روش حرفه‌ای و استاندارده. ربات باید همه‌ی اطلاعات رو پیش خودش نگه داره.

- **ساخت یه کد رندوم:** وقتی دو نفر می‌خوان چت کنن، ربات باید یه کد کاملاً تصادفی و یکتا (مثلاً `a7b2-c8d3-e4f5`) بسازه.
- **ذخیره اطلاعات:** بعد این کد رو با آیدی دو طرف توی دیتابیس خودش ذخیره می‌کنه.
- **استفاده از کد امن:** حالا توی دکمه "پاسخ"، به جای آیدی طرف، همون کد امن رو می‌ذاره.

```json
// اینجوری کار درسته:
{
  "text": "پاسخ بده 📩",
  "callback_data": "reply_a7b2-c8d3-e4f5" // این کد هیچ اطلاعاتی از کاربر لو نمی‌ده!
}
```
اینجوری وقتی کاربر روی دکمه کلیک می‌کنه، ربات کد رو می‌گیره، میره تو دیتابیس خودش نگاه می‌کنه و می‌فهمه باید پیام رو به کی بفرسته. تمام! هویت شما امن باقی می‌مونه.

![این دیاگرام نشون می‌ده کار درست چجوریه](https://private-user-images.githubusercontent.com/118823267/479618548-5fa9817d-405c-4716-ac78-8bc2dfd378d8.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTU2MjE4MzIsIm5iZiI6MTc1NTYyMTUzMiwicGF0aCI6Ii8xMTg4MjMyNjcvNDc5NjE4NTQ4LTVmYTk4MTdkLTQwNWMtNDcxNi1hYzc4LThiYzJkZmQzNzhkOC5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwODE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDgxOVQxNjM4NTJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01Y2I2ZGQzYmFmNjM4NjNlZjdhMjRjZDdiYzFiMWYyMWMxNjRhZTZhNWMzNDUyYTVlMGU3MTI1NzIwOWNhMWE5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.XKOSSD6WQXcJU5CjoEKLpOicWyMIfKLwUJTLsxaEplU)

### ۲. استفاده از رمزنگاری پیشرفته و چندمرحله‌ای 🔐

اگه به هر دلیلی نمی‌خوایم از دیتابیس استفاده کنیم، یه راه دیگه هم هست که خیلی بهتر از `Base64` عمل می‌کنه. در این روش، ما آیدی کاربر رو با یک **کلید مخفی** که فقط روی سرور ربات وجود داره، **رمزنگاری (Encrypt)** می‌کنیم.

- **رمزنگاری:** آیدی کاربر (`123456789`) با استفاده از یک الگوریتم قوی (مثل AES) و یک کلید مخفی، به یک رشته چرت‌وپرت و بی‌معنی (مثلاً `xYz123...`) تبدیل می‌شه.
- **رمزگشایی:** وقتی کاربر روی دکمه کلیک می‌کنه، ربات همون رشته بی‌معنی رو می‌گیره و با استفاده از همون کلید مخفی، **رمزگشایی (Decrypt)** می‌کنه تا به آیدی اصلی برسه.

چون کاربر به کلید مخفی دسترسی نداره، عملاً نمی‌تونه رشته رمزنگاری شده رو باز کنه و به آیدی برسه. می‌شه این روش رو با تکنیک‌های جایگذاری و تغییر کاراکترها پیچیده‌تر هم کرد تا امنیتش بالاتر بره. البته یادتون باشه این روش هنوز به اندازه استفاده از دیتابیس امن نیست، ولی صد شرف داره به لو دادن مستقیم آیدی مثل هیدن چت مزخرف!

---

اینجوری وقتی شما روی دکمه کلیک می‌کنی، ربات کد الکی رو می‌گیره، میره تو دیتابیس خودش نگاه می‌کنه و می‌فهمه باید پیام رو به کی بفرسته. تمام! هویت شما امن باقی می‌مونه. 🛡️

---

## 📢 لیست ربات‌های ناامن

این ربات‌ها امنیت شما رو جدی نگرفتن. اگه حریم خصوصی‌تون براتون مهمه، دور اینا رو تا زماین که برنامه نویسشون این مورد رو برطرف نکرده یه خط قرمز بکشین! ❌

**🚨
- `@NashenasBot` 
- `@BiChatBot` 
- `@BChatBot` 
- `@paym_nashenasBot` 
- `@BChatsBot` 
- `@BitChatsBot` 
- `@BoldChat_Bot`
- `@ChatOGeramBot`
- `@harfinobot`
- `@HidenChat_bot`
- `@pinkChats_bot`
- `@RazGapBot`
- `@TeIeCommentBot`
- `@XBCHATBOT`


## 📢 چند تا ربات امن
تا زمان حل این نقص امنیتی در ربات های بالا میتونید از ربات های زیر استفاده کنید:

- `@YourAnonChatBot`
- `@the404bot`

---

## حرف آخر 👋

**کاربر عزیز:** حواست باشه! "ناشناس" بودن تو این ربات‌ها بیشتر شبیه یه شوخیه. با احتیاط ازشون استفاده کن.

**برنامه‌نویس عزیز:** امنیت کاربرات شوخی‌بردار نیست! لطفاً کدهاتو چک کن و این مشکل رو حل کن تا جلوی این سوءاستفاده‌ها گرفته بشه. و دلیل نوشتن این ریپو به پیشنهاد یکی از صاحب‌های همین ربات‌ها بود و الان که این رو می‌خونید باید از ایشون تشکر کنید. خلاصه تنها دلیل نوشته شدن این ریپو این بود که امروز دیدم توی بعضی گروه‌ها و چنل‌های تلگرامی داره بنرهای خوشگلی پخش می‌شه با عنوان: «با مبلغ توافقی می‌تونی بفهمی توی ربات ناشناس کی بهت پیام داده».
زیاد این بازار برام مهم نبود، بیشتر اون دختر و بچه‌ای که زیر سن قانونی توی این ربات‌ها فیلم، ویس و یا عکسی از خودشون انتشار دادن باعث شد اینو بنویسم چون الان اون دخترها و بچه‌ها امن نیستن و همینجوری داره تعدادشون بیشتر می‌شه. امیدوارم این مشکل هرچه زودتر درست بشه و این بازار سیاه تموم بشه. و اگر چیزی از خودتون نشر دادین و براتون مهمه که کسی بهش دسترسی نداشته باشه، بهترین کار دیلیت اکانت کردنه، چون بعد از نوشتن این ریپو، افرادی هم که از این موضوع آگاه نبودن، آگاه شدن.

مراقب خودتون و اطلاعات‌تون باشید! ❤️
