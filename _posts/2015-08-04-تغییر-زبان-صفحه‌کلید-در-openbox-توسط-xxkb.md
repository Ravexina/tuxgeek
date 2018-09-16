---
layout: post
title: تغییر زبان صفحه‌کلید در OpenBox توسط xxkb
permalink: /گنو-لینوکس/معرفی-نرم-افزار/تغییر-زبان-صفحه‌کلید-در-openbox-توسط-xxkb
post_id: 573
author: milad
categories: 
- openbox
- xxkb
- xxkb openbox
- تغییر زبان openbox
- تنظیم زبان openbox
- تنظیمات xxkb
- راهنما نکات و ترفندها
- معرفی نرم افزار
---

پیش‌تر در مطلبی به نحوه به 
[افزودن زبان فارسی به OpenBox ](http://tuxgeek.ir/%da%af%d9%86%d9%88-%d9%84%db%8c%d9%86%d9%88%da%a9%d8%b3/%d8%a7%d9%81%d8%b2%d9%88%d8%af%d9%86-%d8%b2%d8%a8%d8%a7%d9%86-%d9%81%d8%a7%d8%b1%d8%b3%db%8c-%d8%a8%d9%87-openbox)و 
[نحوه تعیین کلید میانبر برای تغییر صفحه‌کلید](http://tuxgeek.ir/%da%af%d9%86%d9%88-%d9%84%db%8c%d9%86%d9%88%da%a9%d8%b3/%d8%a7%d9%81%d8%b2%d9%88%d8%af%d9%86-%d8%b2%d8%a8%d8%a7%d9%86-%d9%81%d8%a7%d8%b1%d8%b3%db%8c-%d8%a8%d9%87-openbox) پرداختیم، اما داشتن یک icon که وضعیت کنونی زبان انتخاب شده را در Notification Area نواروظیفه، پنل یا ... به نمایش می‌گذارد بسیار مفید خواهد بود، برای این منظور از xxkb استفاده می کنیم.

xxkb وضعیت زبان انتخاب شده کنونی را به نمایش می‌گذارد، همینطور به شما اجازه می دهند با موس و کلیک از بین زبان‌های موجود گزینه دیگری را انتخاب نمایید. از دیگر قابلیت‌های xxkb به‌ خاطر نگاه داشتن وضعیت زبان برای هر پنجره به صورت مجزا می‌باشد و بعد از جابه‌جا شدن بین پنجره‌ها و قرارگرفتن فکوس روی آنها به صورت خودکار زبان را به حالت قبل از ترک پنجره تغییر خواهد داد.

ابتدا xkkb را نصب نمایید: (برایم مثال در Debian یا Ubuntu)

sudo apt-get install xxkb

یا در آرچ:

sudo pcaman -S xxkb

حال باید یک Directory برای نگه‌داری تصاویر مورد استفاده در Notification Area برای نمایش زبان‌ها بسازید، این دایرکتوری را در شاخه زیر با نام xxkb بسازید:

- می‌توانید در صورت تمایل در محل دیگری هم این دایرکتوری را بسازید.

cd ~/.config

mkdir xxkb

اکنون می‌توانید تصاویر مورد نیاز (برای مثال پرچم کشورها) را از یک سایت که به صورت رایگان ارائه می‌کند دانلود نمایید، پس از دانلود با توجه به فضای موجود در Task bar خود آنها را تغییر اندازه دهید و با فرمت xpm در دایرکتوری که در مرحله قبل ساختیم ذخیره نمایید:

~/.config/xxkb

- برای تصاویر نام‌های مناسب در نظر بگیرید، برای مثال ir.xpm و us.xpm.

فایل تنظیمات xxkb را در دایرکتوری خانگی خود ایجاد نمایید:

nano ~/.xxkbrc

تنظیمات زیر را در فایل باز شده ذخیره نمایید:

- نام کاربری خود را در اولین خط جایگزین نمایید.
- اگر تصاویر را در دایرکتوری مورد نظر خورد ذخیره کردید تغییرات لازم را در خط اول اعمال نمایید.
- خط XXkb.mainwindow.geometry را مطابق اندازه تصاویر خودتان تغییر دهید. اندازه پیش‌فرض در تنظیمات 10x10 است.
- در صورتی که تصاویرتان را با نام‌های متفاوتی ایجاد و ذخیره کرده اید خطوط XXkb.mainwindow.image.X را مطابق نام فایل ها تغییر دهید.

XXkb.image.path: /home/your-user-name/.config/xxkb

XXkb.group.base: 1

XXkb.group.alt: 2

XXkb.mainwindow.type: tray

XXkb.mainwindow.enable: yes

XXkb.mainwindow.appicon: yes

XXkb.mainwindow.border.width: 1

XXkb.mainwindow.label.enable: no

XXkb.mainwindow.border.color: white

XXkb.mainwindow.geometry: 
10x10+0+0

XXkb.mainwindow.image.1: 
us.xpm

XXkb.mainwindow.image.2: 
ir.xpm

XXkb.mainwindow.image.3:

XXkb.mainwindow.image.4:

XXkb.mainwindow._delete: no

XXkb.button.enable: no

XXkb.controls.focusout: no

XXkb.controls.two_state: no

XXkb.controls.add_when_start: yes

XXkb.controls.add_when_create: yes

XXkb.controls.add_when_change: no

نهایتا xxkb را در فایل autostart قرار دهید، برای این منظور:

sudo nano ~/.config/openbox/autostart
و xxkb را در آن قرار داده و ذخیره نمایید:

(sleep 3s && xxkb &)

دستور فوق ۳ ثانیه پس از بالا آمدن محیط OpenBox اجرا خواهد شد.

و برای اینکه xxkb را بدون نیاز به راه اندازی مجدد سیستم به‌کار بگیرید دستور زیر را اجرا نمایید:

xxkb &

منابع: 
ویکی Manjarooو man xxkb