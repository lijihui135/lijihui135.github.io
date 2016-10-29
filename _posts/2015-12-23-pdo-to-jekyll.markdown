---
layout: post
title:  "PDO连接数据库"
date:   2015-12-23 11:49:45 +0200
categories: jekyll update
---

首先我们先来介绍一下PDO常用的一些方法 。
PDO::query()主要用于有记录结果返回的操作（PDOStatement），特别是select操作。

PDO::exec()主要是针对没有结果集合返回的操作。如insert,update等操作。返回影响行数。

PDO::lastInsertId()返回上次插入操作最后一条ID。

PDOStatement::fetch()是用来获取一条记录。配合while来遍历。

PDOStatement::fetchAll()是获取所有记录集到一个中。

下来我们边来连接我们的mysql数据库 下面便是一个简单的链接。 
{% highlight ruby %}
  $dbh = new PDO('mysql:host=localhost;dbname=数据库名', 'root', ''); 
  $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);  
  $dbh->exec('set names utf8'); 
{% endhighlight %}
下面这个链接方式跟上面一样 ，只不过这是一个持久性的连接持久性链接PDO::ATTR_PERSISTENT=>true。
{% highlight ruby %}
   
    $dbh=newPDO('mysql:host=localhost;port=3306; dbname=test',$user,$pass,array(
        PDO::ATTR_PERSISTENT=>true
    ));
 
{% endhighlight %}



[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
