---
layout: post
title: TASM در گنو/لینوکس (Turbo Assembler)
permalink: /گنو-لینوکس/اجرای-tasm-در-گنولینوکس-turbo-assembler
post_id: 487
author: milad
categories: 
- dosbox و tasm
- tasm linux
- TASM لینوکس
- اجرای tasm در ubuntu
- اجرای tasm در لینوکس
- اسمبلی در لینوکس
- راهنما نکات و ترفندها
- گنو/لینوکس
- لینوکس اسمبلی
- معرفی نرم افزار
---

TASM یا 
[Turbo Assembler](https://en.wikipedia.org/wiki/Turbo_Assembler) یک بسته اسمبلر است که توسط Borland توسعه داده شده، این اسمبلر برای سیستم‌عامل های داس و ویندوز عرضه شده و امکان تولید کد‌های ۱۶ و ۳۲ بیتی را فراهم می سازد.

در توزیع های گنو/لینوکس گزینه‌های بسیار مناسبی همچون 
[NASM](http://manpages.ubuntu.com/manpages/precise/man1/nasm.1.html) برای انتخاب در دسترس می‌باشند، با این‌حال ممکن است به دلایلی مجبور به استفاده از TASM باشید، در این پست به نحوه اجرای TASM‌ در توزیع‌های گنو/لینوکس همچون Ubuntu، ArchLinux، Fedora و... می‌پردازیم.


## نحوه اجرای Tasm


پروسه بسیار ساده است، ما از 
[DosBox](http://www.dosbox.com) برای شبیه‌سازی محیط داس و اجرای TASM و فایل‌های تولید شده توسط آن بهره خواهیم گرفت.

ابتدا یک فولدر برای قراردادن فایل های TASM و پروژه‌های خود بسازید، برای مثال در دایرکتوری خانه خودتان فولدری به اسم tasm بسازد و فایل‌های Turbo Assembler را به این محل انتقال دهید:

{% highlight shell %}
mkdir ~/tasm
{% endhighlight %}

حال باید DosBox را نصب نماییم، برای اینکار میتوانید از Software Center یا مدیربسته توزیع مورد استفاده خود بهره بگیرید. برای مثال در توزیع های خانواده Debian که از apt-get استفاده می‌کنند، دستور زیر بسته DosBox را نصب خواهد کرد:
{% highlight shell %}
sudo apt-get install dosboxdos
{% endhighlight %}

![dosbox](/assets/images/wp/2015/02/12.png)

پس از تکمیل مراحل نصب، داس باکس را اجرا نمایید. برای این منظور می‌توانید در ترمینال وارد کنید dosbox.

در DosBox‌ باید شاخه‌ی tasm که در مرحله اول ساخته‌ایم را سوار نماییم (mount کنیم)، به این منظور در dosbox وارد کنید:
{% highlight shell %}
mount    r:    ~/tasm
{% endhighlight %}
پیغام زیر نمایش داده خواهد شد:

{% highlight code %}
Drive r is mounted as local directory /home/username/tasm
{% endhighlight %}

حال تایپ کنید :r و enter کنید تا به شاخه مجازی که ساختید منتقل شوید.

اکنون به فایل‌های Assembler و پروژه‌های خود که به فولدر tasm انتقال داد بودید دسترسی دارید و میتوانید فایل‌های خود را تولید و اجرا نمایید.

برای این منظور فایل‌های شامل کدهای Assembly‌ خود را با پسوند asm در فولدر tasm ذخیره کنید، برای مثال first.asm، سپس دستور های زیر را اجرا نمایید تا برنامه تولید و اجرا شود:
{% highlight shell %}
tasm frist.asm
tlink frist.objfrist.exe
{% endhighlight %}