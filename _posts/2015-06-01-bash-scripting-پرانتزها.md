---
layout: post
title: Bash Scripting - توضیح پرانتزها
permalink: /گنو-لینوکس/ترمینال/bash-scripting-پرانتزها
post_id: 548
author: milad
categories: 
- bash
- bash scripting
- Parenthesis in bash scripting
- ترمینال - Bash
---

اگر تاکنون کد اسکریپت‌های Bash را مطالعه نموده و یا تلاش کرده‌اید که یک اسکریپت کوچک بنویسید و نحوه به کارگیری پرانتز، کروشه و آکولاد در اسکریپت‌های Bash برایتان گیج‌کننده بوده این پست تا حدودی برایتان مفید واقع خواهد شد.

در ادمه با ذکر مثال‌هایی به توضیح مفاهیم فوق خواهیم پرداخت.


آشنایی با اصطلاحات:

- Parenthesis: () (Plural parentheses - پرانتز)
- Brackets: [] (Square brackets - کروشه)
- Curly brackets: {} (Curly braces - آکولاد)

**دو پرانتز - Parenthesis در Bash Scripting**

از دو پرانتز برای انجام عملیات‌های محاسباتی استفاده می‌شود:
{% highlight shell %}
((variable++))

((variable = 3))

for ((i = 0; i < VALUE; i++))

echo $((variable + 2))

{% endhighlight %}
نکته: در عملیات‌های محاسباتی، متغیرهایی که درون دوپرانتز قرار میگیرند نیازی ندارند که با علامت $ شروع شوند.

نکته: درصورتی که نیاز دارید مقدار درون دو پرانتز را چاپ کنید یا از مقدار آن استفاده نمایید قبل از دوپرانتز $ قرار دهید.

**کروشه - Brackets در Bash Scripting**

کروشه برای ساخت شرط به کار میرود:
{% highlight shell %}
$ VAR=2

$ if [ $VAR -eq 2 ]

> then

> echo 'yes'

> fi

yes
{% endhighlight%}
با توجه به نحوه استفاده از دو پرانتز میتوان مثال قبل را به شکل زیر تغییر داد:

{% highlight shell %}
$ ((VAR=2))

$ if [ $((VAR)) -eq 2 ]

> then

> echo 'yes'

> fi

yes
{% endhighlight %}
**دو کروشه - Double Brackets**

استفاده از دو کروشه قابلیت‌های کروشه را افزایش میدهد، برای مثال میتوانید از عبارات با قاعده (Regular Expression) استفاده کنید:

{% highlight shell %}
if [ $VAR =~ [a-z] ]; then echo 'is'; fi --> اشتباه

if [[ $VAR =~ [a-z] ]]; then echo 'is'; fi --> صحیح
{% endhighlight%}

**آکولاد - Curly Braces در Bash Scripting**

از آکولاد یا curly braces برای محدود کردن یک متغیر استفاده میشود، برای مثال:

{% highlight shell %}
$ foo='stage'

$ echo $fooone --> خروجی خالی چون متغیری به این نام نداریم

$ echo ${foo}one --> نام متغیر رو از رشته ای که بهش اضافه شده جدا کرده

stageone
{% endhighlight%}
از curly braces میتوان برای parameter expansion (بسط و گسترش پارامتر) هم استفاده نمود، چند مثال:

ابتدا یک متغیر تعریف می‌کنیم:
{% highlight shell %}
var='abcdefg'
{% endhighlight %}
از کارکتر سوم دو کارکتر را برش می‌دهد:

{% highlight shell %}
echo ${var:3:2}

de
{% endhighlight %}
از ابتدای رشته تا حرف g چاپ می‌شود:

{% highlight shell %}
echo {$var%g}

abcdef
{% endhighlight %}

از ابتدای رشته تا جایی که d شروع و با هر چیزی ادامه پیدا میکند را چاپ می‌نماید:

{% highlight shell %}
echo {$var%d*}

abc
{% endhighlight %}
تنها به خاطر بسپارید که کروشه برای شروط، دوکروشه برای عبارات باقاعده و دو پرانتز برای محاسبات و حلقه های شبه C کاربر دارند.

بر اساس linuxconfig