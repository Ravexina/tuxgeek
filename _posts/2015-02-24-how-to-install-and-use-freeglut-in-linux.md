---
layout: post
title: نصب و استفاده از FreeGLUT در GNU/Linux
permalink: /دسته‌بندی-نشده/how-to-install-and-use-freeglut-in-linux
post_id: 506
author: milad
categories: 
- FreeGLUT
- اجرای GLTU در Ubuntu
- اوبونتو FreeGLUT
- توسعه و برنامه نویسی
- دسته‌بندی نشده
- راهنما نکات و ترفندها
- لینوکس FreeGLUT
- نصب FreeGLUT
---

[FreeGLUT](http://freeglut.sourceforge.net) یک جایگزین متن‌باز برای 
[GLUT](https://en.wikipedia.org/wiki/OpenGL_Utility_Toolkit) است که ساخت و مدیریت پنجره‌هایی شامل محتوای 
[OpenGL](https://www.opengl.org/) را در محدوده‌ای وسیع از سیستم‌عامل‌های متفاوت امکان‌پذیر می‌سازد.

پروژه FreeGLUT در سال 1999 توسط Pawel W. Olszta ایجاد شده و  تحت مجوز X-Consortium منتشر می‌شود. این ابزار تقریبا یک جایگزین صد در صدی برای GLUT می‌باشد.

OpenGL Utility Toolkit که اختصارا GLUT‌ خوانده می‌شود، یک کتابخانه از ابزارهای مفید برای برنامه‌های OpenGL است.

نمایی از یک بازی شطرنج ساخته شده توسط FreeGLUT:

[![chess-freeGLUT](/assets/images/wp/2015/02/chessdemo.png)](/assets/images/wp/2015/02/chessdemo.png)در این پست به نحوه نصب و استفاده از FreeGLUT (جایگزین متن باز GLUT) در توزیع Ubuntu خواهیم پرداخت، به طبع نصب در سایر توزیع‌ها به صورت مشابه امکان‌پذیر خواهد بود.

more


## نصب FreeGLUT توسط مدیربسته (پیشنهادی):


مراحل نصب و بکارگیری بسیار ساده است، تمام بسته‌های مورد نیاز در مخازن به صورت باینری موجود و توسط مدیربسته قابل نصب می‌باشند.

بسته‌های build-essential و freeglut3-dev را توسط apt-get نصب نمایید:

sudo apt-get install freeglut3-dev build-essential

کار تمام است، فایل منبع برنامه خود را با پارامترهای زیر کامپایل کرده و نهایتا اجرا نمایید:

g++ -o exam1 exam1.cpp -lglut -lGL


## نصب FreeGLUT به صورت Manual:

ابتدا FreGLUT را از آدرس زیر دریافت نمایید:

http://freeglut.sourceforge.net/index.php#download
سپس نسخه دانلود شده را از حالت فشرده خارج کنید.

zcat freeglut-2.2.0.tar.bz2 | tar -vxf

توجه نمایید که ممکن است فایل دانلود شده توسط شما با توجه به نسخه‌ای که دانلود کرده‌اید دارای شماره نسخه متفاوتی باشد.
به پوشه استخراج شده وارد شوید و دستورات زیر را اجرا نمایید:

./configure
make all
make install

پروسه کامپایل و نصب طی خواهد شد، حال همانند سابق میتوانید فایل‌های منبع خود را کامپایل و استفاده نمایید، توجه کنید که برای الحاق کتابخانه FreeGLUT به صورت زیر اقدام کنید:

# include <GL/glut.h>
منابع:

http://ubuntuforums.org/showthread.php?t=345177

http://freeglut.sourceforge.net/docs/install.php

https://www.opengl.org/discussion_boards/showthread.php/172614-undefined-reference-to-glutInt