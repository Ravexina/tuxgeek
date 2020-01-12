---
layout: post
title: نصب پلاگین در neovim
permalink: /development/how-to-use-vim-plug-in-neovim
author: milad
date: 2020-01-13 01:49:00 +0330
categories: 
- development
---


مدتی پیش پس از سال‌ها کار کردن با Vundle، مجبور شدم به خاطر بررسی یک پلاگین خاص به vim-plug مدیرپلاگین VIMام رو تغییر بدم،
نهایتا این سوال پیش می‌یاد که چرا اصلا مهاجرت نکنیم به neovim؟
تو این پست خیلی سریع نحوه نصب و پیکربندی vim-plug روی neovim رو توضیح می‌دم.

نکته اول اینکه محل قرارگیری تنظیمات neovim برخلاف VIM که در `HOME$` قرار داشت در این شاخه قرار گرفته:

{% highlight bash %}
~/.config/nvim/init.vim
{% endhighlight %}


ابتدا این دایرکتوری رو بررسی کنید که وجود داشته باشه اگر نداره بسازید:

{% highlight bash %}
mkdir -p ~/.local/share/nvim/site/autoload
{% endhighlight %}

سپس `vim-plug` رو در دایرکتوری `autoload` قرار بدید:
{% highlight bash %}
wget \
    'https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim' \
    -O '.local/share/nvim/site/autoload/plug.vim'
{% endhighlight %}

اینطور به نظر می‌رسه که عموم مردم علاقه دارند پلاگین‌های نصب شده رو در `config/neovim./~` قرار بدند، اما من ترجیح می‌دهم در کنار خود `vim-plug` باشه،
پس دایرکتوری زیر رو ایجاد می‌کنیم:

{% highlight bash %}
mkdir ~/.local/share/nvim/site/plugged
{% endhighlight %}

و یک فایل برای نگه داشتن لیست پلاگین‌ها در این شاخه ایجاد می‌کنیم:
{% highlight bash %}
touch ~/.config/nvim/plugins.vim
{% endhighlight %}


حالا می‌تونیم تنظیمات `vim-plug` رو در فایل بالا قرار بدیم، به همراه پلاگین‌های مورد نظرمون برای نصب:

{% highlight bash %}
call plug#begin('~/.local/share/nvim/site/plugged')
Plug 'user/repo' # plugin repo in github
call plug#end()
{% endhighlight %}

به آدرسی که در ` plug#begin` آمده توجه کنید، همون دایرکتوی که در دو مرحله‌ی قبل برای نگه‌داری از پلاگین ها ساختیم.

نهایتا فایل تنظیمات neovim رو ویرایش و خط زیر رو توش قرار می‌دیم تا هر بار که اجرا می‌شه فایل حاوی لیست پلاگین‌هامون هم source بشه.

{% highlight bash %}
so ~/.config/nvim/plugins.vim
{% endhighlight %}

حالا کافیه بزنیم `PlugInstall` تا پلاگین‌ها نصب بشند.