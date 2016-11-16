---
layout: post
title:  "Session and Cookie"
date:   2014-12-26 11:49:45 +0200
categories: jekyll update
---
首先我们要明白为什么要使用Session和Cookie ,在非常多时候，我们需要跟踪浏览者在整个网站的活动，对他们身份进行自动或半自动的识别（也就是平时常说的网站登陆之类的功能），这时候，我们常采用Cookie与 Session来跟踪和判断。

Session和Cookie之间也存在着非常大的区别，Session信息是存放在server端，但session id是存放在client cookie的，当然php的session存放方法是多样化的，这样就算禁用cookie一样可以跟踪
Cookie是完全保持在客户端的如：IE firefox 当客户端禁止cookie时将不能再使用

首先我们来看一下Cookie 。
PHP对Cookie的接收和处理的支持非常好，是完全自动的，跟FORM变量的原则一样，特别简单。
比如设置一个名为 MyCookier的Cookie，PHP会自动从WEB服务器接收的HTTP头里把它分析出来，并形成一个与普通变量一样的变量，名为$ myCookie，这个变量的值就是Cookie的值。数组同样适用。另外一个办法是引用PHP的全局变量$HTTP_COOKIE_VARS数组。
分别举例如下：（假设这些都在以前的页面里设置过了，并且仍然有效）


{% highlight ruby %}
echo $MyCookie;
echo $CookieArray[0];
echo $_COOKIE["MyCookie"]; 
echo $HTTP_COOKIE_VARS["MyCookie"]; 
{% endhighlight %}
要删除一个已经存在的Cookie，有两个办法：
{% highlight ruby %}
   
    SetCookie("Cookie", "");
    SetCookie("Cookie", "value" , time()-1 / time() );
 
{% endhighlight %}
使用Cookie的限制
1、必须在HTML文件的内容输出之前设置；
2、不同的浏览器对Cookie的处理不一致，且有时会出现错误的结果。
3、限制是在客户端的。一个浏览器能创建的Cookie数量最多为30个，并且每个不能超过4KB，每个WEB站点能设置的Cookie总数不能超过20个。

接下来我们看看session 。
我们首先需要进行开启session，然后进行配置和使用。
{% highlight ruby %}
   
    session_start();                    //初始化session.需在文件头部
	$_SESSION[name]=value;  //配置Seeeion
	echo $_SESSION[name];    //使用session
	isset($_SESSION[name]);   // 判断
	unset($_SESSION[name]);   //删除
	session_destroy()；             //消耗所有session
 
{% endhighlight %}

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
