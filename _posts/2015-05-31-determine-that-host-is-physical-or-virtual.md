---
layout: post
title: از کجا بفهمیم یک میزبان Virtual هست یا Physical
permalink: /گنو-لینوکس/معرفی-نرم-افزار/determine-that-host-is-physical-or-virtual
post_id: 544
author: milad
categories: 
- facter
- virtual or dedicaded server
- vps or dedicaded server
- راهنما نکات و ترفندها
- سرور مجازی یا اختصاصی
- فیزیکی یا مجازی
- معرفی نرم افزار
---

راحت ترین راه برای متوجه شدن این موضوع که یک سیستم مجازی است یا فیزیکی استفاده از بسته facter می‌باشد. facter یک ابزار کوچک است که به منظور جمع‌آوری و نمایش اطلاعات پیرامون سیستم کاربرد دارد.

** نصب Facter با مدیر بسته:**

ابتدا باید facter را نصب نماییم، برای این منظور میتوان از مدیربسته سیستم‌عامل استفاده کرد. برای مثال در Debian یا Ubuntu:

sudo apt-get install facter

** نصب Facter به صورت Manual:**

برای نصب facter در سیستم‌هایی که این بسته را در مخازن خود ندارند ابتدا آخرین نسخه این ابزار را از آدرس زیر دانلود نمایید:

https://downloads.puppetlabs.com/facter/?C=N;O=D
سپس بعد از extract کردن آرشیو دانلود شده دستور زیر را اجرا کنید:

ruby facter*/install.rb

** استفاده از Facter**


حال برای استفاده از facter میتوان از دستور زیر استفاده کرد:

facter

دستور فوق اطلاعات مفیدی از سیستم را به نمایش می‌گذارد، برای یافتن اینکه سیستم Virtual بوده یا Physical دستور را به این صورت اجرا کنید:

facter | grep is_virtual

نتیجه به صورت زیر true یا false خواهد بود:

is_virtual 
=> false