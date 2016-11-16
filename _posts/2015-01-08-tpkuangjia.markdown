---
layout: post
title:  "tp框架3.2简单叙述"
date:   2015-01-08 11:49:45 +0200
categories: jekyll update
---
   
tp版本下载地址：http://thinkphp.cn/down/framework.html

1.ThinkPHP无需任何安装，直接拷贝到你的电脑或者服务器的WEB运行目录下面即可。
2.版本要求

PHP5.3以上版本（注意：PHP5.3dev版本和PHP6均不支持）
支持Windows/Unix服务器环境
可运行于包括Apache、IIS和nginx在内的多种WEB服务器和模式
支持Mysql、MsSQL、PgSQL、Sqlite、Oracle、Ibase、Mongo以及PDO等多种数据库和连接

3.下载tp3.2核心版本之后解压得到自己的web目录下，index.php是入口文件、README.md是README文件、Application是应用目录、public是资源文件目录、ThinkPHP是框架目录。

4.入口文件：

作用：1.定义框架路径、项目路径（可选）2.定义调试模式和应用模式（可选）3.定义系统相关常量（可选）4.载入框架入口文件（必须）

入口文件初始内容：

{% highlight ruby %}
// 应用入口文件
// 检测PHP环境
if(version_compare(PHP_VERSION,'5.3.0','<'))  die('require PHP > 5.3.0 !');
// 开启调试模式 建议开发阶段开启 部署阶段注释或者设为false
define('APP_DEBUG',True);
// 定义应用目录
define('APP_PATH','./Application/');
// 引入ThinkPHP入口文件
require './ThinkPHP/ThinkPHP.php';
{% endhighlight %}

如果你改变了项目目录（例如把Application更改为Apps），只需要在入口文件更改APP_PATH常量定义即可

注意：APP_PATH的定义支持相对路径和绝对路径，但必须以“/”结束。定义绝对路径会提高系统的加载效率

自动生成：

在第一次访问应用入口文件的时候，会显示如图所示的默认的欢迎页面，并自动在Application中生成了一个默认的应用模块Home：

在自动生成目录结构的同时，为了避免某些服务器开启了目录浏览权限后可以直接在浏览器输入URL地址查看目录，系统默认开启了目录安全文件机制，会在自动生成目录的时候生成空白的index.html文件，可以自己定义，在入口文件中定义，也可以关闭不生成

tp3.2采用模块化的设计架构，每个模块可以方便的卸载和部署，并且支持公共模块。

控制器类的命名方式是：控制器名（驼峰法，首字母大写）+Controller

控制器文件的命名方式是：类名+class.php（类文件后缀）

首次访问php欢迎页面的内容更改为：

{% highlight ruby %}

namespace Home\Controller;  // 表示当前类是Home模块下的控制器类，命名空间和实际的控制器文件所在的路径是一致的
use Think\Controller;
class IndexController extends Controller {
    public function index(){
        echo 'hello,world!';
    }
}

{% endhighlight %}

其实就是访问的Home模块下面的Index控制器类的index操作方法

注意：命名空间定义必须写在所有的PHP代码之前声明

开发规范：

1.类文件都是以.class.php为后缀（这里是指的ThinkPHP内部使用的类库文件，不代表外部加载的类库文件），使用驼峰法命名，并且首字母大写，例如 DbMysql.class.php；
2.类的命名空间地址和所在的路径地址一致，例如 Home\Controller\UserController类所在的路径应该是Application/Home/Controller/UserController.class.php；
3.确保文件的命名和调用大小写一致，是由于在类Unix系统上面，对大小写是敏感的（而ThinkPHP在调试模式下面，即使在Windows平台也会严格检查大小写）；
4.类名和文件名一致（包括上面说的大小写一致），例如 UserController类的文件命名是UserController.class.php， InfoModel类的文件名是InfoModel.class.php， 并且不同的类库的类命名有一定的规范；
5.函数、配置文件等其他类库文件之外的一般是以.php为后缀（第三方引入的不做要求）；
6.函数的命名使用小写字母和下划线的方式，例如 get_client_ip；
7.方法的命名使用驼峰法，并且首字母小写或者使用下划线“_”，例如 getUserName，_parseType，通常下划线开头的方法属于私有方法；
8.属性的命名使用驼峰法，并且首字母小写或者使用下划线“_”，例如 tableName、_instance，通常下划线开头的属性属于私有属性；
9.以双下划线“__”打头的函数或方法作为魔法方法，例如 __call 和 __autoload；
10.常量以大写字母和下划线命名，例如 HAS_ONE和 MANY_TO_MANY；
11.配置参数以大写字母和下划线命名，例如HTML_CACHE_ON；
12.语言变量以大写字母和下划线命名，例如MY_LANG，以下划线打头的语言变量通常用于系统语言变量，例如_CLASS_NOT_EXIST_；
13.对变量的命名没有强制的规范，可以根据团队规范来进行；
14.ThinkPHP的模板文件默认是以.html 为后缀（可以通过配置修改）；
15.数据表和字段采用小写加下划线方式命名，并注意字段名不要以下划线开头，例如 think_user 表和 user_name字段是正确写法，类似 _username 这样的数据表字段可能会被过滤。


特例：在ThinkPHP里面，有一个函数命名的特例，就是单字母大写函数，这类函数通常是某些操作的快捷定义，或者有特殊的作用。例如：A、D、S、L 方法等等，他们有着特殊的含义

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
