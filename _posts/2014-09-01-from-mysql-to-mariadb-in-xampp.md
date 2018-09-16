---
layout: post
title: تغییر MySQL به MariaDB در XAMPP
permalink: /توسعه-و-برنامه-نویسی/from-mysql-to-mariadb-in-xampp
post_id: 384
author: milad
categories: 
- Database
- MariaDB
- MySQL
- Web Server
- XAMPP
- توسعه و برنامه نویسی
- توسعه وب
---

شاید شما هم جزو کسانی باشید که علاقمند هستید در XAMPP به جای MySQL از 
[MariaDB](https://mariadb.org/)استفاده نمایید، در ادامه به ذکر مراحل مورد نیاز جهت مهاجرت به MariaDB در XAMPP  خواهیم پرداخت.

[![mariadb-fd-logo](/assets/images/wp/2014/09/ice_logo-5dcea9e47b780ff52f75c3c3304d54827f56211e-150x150.png)](/assets/images/wp/2014/09/ice_logo-5dcea9e47b780ff52f75c3c3304d54827f56211e.png)این مراحل تنها شامل جابه جایی برخی فولدر ها و یک ویرایش ناچیز است، پس از طی کردن این مراحل قادر خواهید بود  MariaDB را همانند MySQL به کار بگیرید، حتی ممکن است متوجه مقداری بهبود عملکرد شوید که تنها یکی از مزایای MariaDB است، در پست های آتی بیشتر به MariaDB خواهیم پرداخت.

more

1. در ابتدا اگر MySQL فعال است، آن را غیر فعال کنید.
2. یک نسخه قابل حمل (Portable) و متناسب با نسخه MySQL خود از 
[MariaDB](https://downloads.mariadb.org/)را دانلود نمایید.
3. فولدر mysql در شاخه XAMPP را به mysql.old تغییر نام دهید.
4. فایل دانلود شده MariaDB را Extract و در فولدر XAMPP قرار دهید.
5.نام فولدر را از MariaDB به mysql تغییر دهید.
6. در فولدر mysql، پوشه data را به data.old تغییر نام دهید.
7. فولدر های data، backup، script  را از mysql.old به mysql انتقال دهید.
8. فایل my.ini واقع در پوشه bin از mysql.old را به mysql و پوشه bin انتقال دهید، سپس در یک ویرایشگر باز کرده و پس از یافتن مقدار skip-federated آن را Comment کنید.

حال XAMPP را راه اندازی کنید.


[منبع](https://articlebin.michaelmilette.com/how-to-upgrade-mysql-to-mariadb-in-xampp-in-5-minutes-on-windows/)