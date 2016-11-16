---
layout: post
title:  "javescript详解"
date:   2014-12-30 11:49:45 +0200
categories: jekyll update
---
   首先我们来简单了解一下javescript是什么有哪些特性。

    JS是一种解释型的网页脚本语言。其作用是控制浏览器的行为和内容。

	    js代码是嵌入到Html中的。

     它有这么几大特点

    在客户端运行，这就意味着可以减轻服务器的压力。提高代码的执行效率。

    JavaScript 是一种解释性语言（就是说，代码执行不进行预编译） 

        对应的编译型语言，执行的时候需要提前编译成中间代码或者机器语言，比如Java编译成.class文             件。

    javaScript和java没有任何关系。Javascript不是其他语言的精简版（例如，它只是与 Java 有点模糊而间接的关系），也不是任何事物的简化。不过，它有其局限性。例如，您不能使用该语言来编写独立运行的应用程序，并且没有对读写文件的内置支持。此外，Javascript脚本只能在某个解释器或“宿主”上运行，如 Active Server Pages（ASP）、Internet 浏览器或者 Windows 脚本宿主。

    然后我们再来看看javescript能实现什么呢 

    JavaScript能实现浏览器的脚本开发。它有很多经典的功能。我们需要掌握。

    JavaSript实现网页特效

	Js能实现很多网页特效，如图片文字的滚动，图片的动态变换等。在网上搜索，能找到很多现成的        代码。

	javescript还能够操控html元素，能操作网页元素，如对输入框，下拉框，表格等元素的操作。操作html元素的基础就是对DOM对象的操作。任何一个html元素是一个dom对象。我们可以利用js，来操作它。比如改变它的属性，动态增加元素。获取它的值等。

Html中的每一个元素都对应dom中的一个节点。html表单对应着一棵dom树，每个节点都有nodeName nodeValue nodeType属性。js就是通过操作这些属性来操作html的。

    JavaScript还能实现表单验证比如

{% highlight ruby %}
      var temp = document.getElementById("text1");  
          //对电子邮件的验证  
           var myreg =/^([a-zA-Z0-9]+[_|\_|\.]?)*[a-zA-Z0-9]+@([a-zA-Z0-9]+[_|\_|\.]?)*[a-zA-Z0-9]+\.[a-zA-Z]{2,3}$/;  
           if(!myreg.test(temp.value))  
          {  
                 alert('提示\n\n请输入有效的E_mail！');  
                myreg.focus();  
               return false;  
          }  
{% endhighlight %}

		js的是web开发中必不可少的一个技术，作为一个web开发人员，必须对它熟悉掌握。

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
