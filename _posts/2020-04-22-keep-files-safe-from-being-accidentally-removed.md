---
layout: post
title: چطور اشتباهی فایلی رو پاک نکنیم؟
permalink: /linux/protect-files-from-accidentally-being-removed
author: milad
date: 2020-04-22 16:16:00 +0430
categories: 
- Linux
---

## مشکل چیست؟


اگر مدت زیادی رو تو خط‌فرمان سپری کرده باشید ناخودآگاه به کلید‌های میان‌بر تسلط پیدا می‌کنید. سرعت عملکرد شما بالا میره و وقتی با خط‌فرمان کار می‌کنید، 
از دید یک فرد ناآشنا انگار دارید جادو می‌کنید. یا ممکن فکر کنند هر روز دوره تایپ می‌گذرونید که اینقدر سریع جابه‌جا می‌شید و دستورات رو ویرایش و اجرا می‌کنید.

حالت‌های مختلفی برای اشتباه حذف کردن یک یا چندین فایل توسط کاربر ممکنه رخ بده. فرضا ممکنه اشتباهی دستور زیر رو اجرا کنید:
{% highlight bash %}
sudo rm -rf /bin
{% endhighlight %}


تا حالا همچین اشتباهی نکردم، ولی راه حل [بازگردانی bin](https://askubuntu.com/a/906675/264781) رو اینجا نوشتم می‌تونید بخونید.

اینجا قرار نیست درباره اینکه چه طور خرابکاری رو درست کنیم صحبت کنیم. قصد داریم با ابزارهایی آشنا بشیم که جلو رخ دادن این اشتباهات رو می‌تونند تا حدی بگیرند.

اشتباه دیگه زمانی ممکنه رخ بده که بخواید از تاریخچه خط‌فرمان استفاده کنید و دستورات قبل رو اشتباها روی فایل و شاخه‌های  دیگه اجرا کنید.

فرض کنید:

{% highlight bash %}
cd ~/.config
echo 'enforce=no' >> se.conf
rm se.conf.bk
{% endhighlight %}

و بعد اگر مثل من عادت داشته باشید Ctrl+L تا خط‌فرمان رو از دستورات قبلی خالی کنید.

حالا میرید پی یک سری کار دیگه، بر می‌گردید به خط فرمان قصد دارید دستور echo رو روی فایل جدید اجرا کنید. Ctrl+P میزنید اسم فایل رو تغییر میدید
به فایل جدید و Enter میزنید. همه در کسری از ثانیه. بله به جای echo دستور rm رو اجرا کردیم.

{% highlight bash %}
rm xxkb.conf
{% endhighlight %}


اینجا من ctrl+p استفاده کردم ولی این نمونه‌ها رو فرض کنید:

{% highlight bash %}
!-7:0
!string
{% endhighlight %}

همه پتانسیل رخ دادن اشتباه مشابه رو دارند. البته کافیه Ctrl+Alt+E بزنید تا ببنید کدوم دستور رو دارید اجرا می‌کنید.



## راهکار چیست؟

### Alias
ساده ترین کاری که میشه کرد اینکه دستور rm رو alias کنیم به چیزی شبیه rm -i **که این کار پیشنهاد نمی‌شه**.


{% highlight bash %}
alias rm='rm -i'
{% endhighlight %}

دلیلش این هست که وقتی رو سیستم شخصی این alias رو داشته باشید و بهش عادت کنیم اون موقع پیش‌فرض ذهنی شما بر این اصل بنا خواهد شد که بقیه سیستم
ها هم به همین شکل کار می‌کنند و ممکنه روی یک سرور و فایل‌هایی مهم rm رو اجرا کنید و منتظر باشید تا ازتون بپرسه فایل رو حذف کنم یا نه ولی دیگه برای فکر کردن دیر شده.


### safe-rm
گزینه بعدی استفاده از ابزاری مثل safe-rm هست. این بسته با یک لیست قابل تنظیم جلوی حذف شدن فایل‌های مهم سیستمی رو می‌گیره. پیشنهاد سازنده‌ها این هست که
به safe-rm یک symbolic link بزنید به عنوان rm و در usr/local/bin/ قرار بدید که اولویت اجرای بیشتری داره:

{% highlight bash %}
sudo apt install safe-rm
ln -s /usr/local/bin/safe-rm /usr/local/bin/rm
{% endhighlight %}

حالا اگر دستور زیر رو اجرا کنید:



{% highlight bash %}
sudo rm -rf /usr/bin
{% endhighlight %}

درواقع دستور safe-rm اجرا می‌شه و جلوی جذف شدن این شاخه مهم رو می‌گیره.


### [trash-cli](https://github.com/andreafrancia/trash-cli) و gvfs-bin

این دو بسته دستوراتی رو در اختیار ما قرار می‌دند که بتونیم فایل‌ها رو از خط‌فرمان به trash انتقال بدیم. مثل همیشه تو Debian بیس‌ها می‌تونیم با apt اونها رو نصب کنیم.

{% highlight bash %}
sudo apt install trash-cli
sudo apt install gvfs-bin
{% endhighlight %}

حالا کافیه به جای rm از دستورات معادل استفاده کنیم:


{% highlight bash %}
# gvfs-bin
gio trash file

# trash-cli
trash-put file
{% endhighlight %}

و پیشنهاد میشه rm رو غیرفعال کنیم. نه اینکه alias کنیم به دستورات فوق:

{% highlight bash %}
alias rm='echo you should use \"gio trash\" or \"trash-put\" instead!'
{% endhighlight %}

و قطعا می‌دونید اگر بخواید rm رو اجرا کنید می‌تونید alias رو نادیده بگیرید:

{% highlight bash %}
''rm file
""rm file
\rm file 
{% endhighlight %}


فراموشن نکنید:

{% highlight bash %}
man gio
man trash-put trash-list trash-empty trash-rm
{% endhighlight %}