---
layout: post
title:  "命令行创建数据库和表"
date:   2014-12-29 11:49:45 +0200
categories: jekyll update
---
   在sql中使用命令行创建数据库，
   1.建立数据库

{% highlight ruby %}
   create database ttt
	on
	(
	NAME=yyy_DAT,
	FILENAME='F:\mmm\ttt.mdf',
	SIZE=3MB,
	MAXSIZE=30MB,
	FILEGROWTH=10%
	)
	LOG on
	(
	NAME=ttt_LOG,
	FILENAME='F:\mmm\ttt.LOG',
	SIZE=3MB,
	MAXSIZE=30MB,
	FILEGROWTH=10%
	)
{% endhighlight %}
2. 建立数据表
{% highlight ruby %}
   
 use ttt
go
create table tyy
(
id int primary key identity(1,1),  ---关键字，自动编号
tname char(10) not null,--不能空
tage char(5),
tsex char(2) check(tsex in('男','女'))default('女'),--有条件填空
tbirth date check(tbirth between '1990-01-01' and '2015-12-29' )
)
 
{% endhighlight %}

SQL语句：DML—数据操纵语言SQL命令，分为：select查询、insert into插入、delete from删除、update set修改.

 Select 查询命令
最复杂、存在非常多的使用方法
1、查询表中所有的数据
Select  *  from  table_name；
 
2、普通条件（where、and、or）查询
Select *或者字段1,字段2,… from　table_name where 字段1＝值1或字段2＝值2…;
如查询一个范围的薪资
SELECT store_name FROM Store_Information WHERE salary > 1000 OR (salary < 500 AND salary > 275);
 
3、模糊条件（like）查询
Select *或者字段1,字段2,… from table_name where字段1 like %A%;包含A的字符.

 insert into…插入
1、普通常用插入
Insert into table_name (字段1, 字段2, 字段3,…)values (数值1, 数值2, 数值3,…);
2、插入子查询结果
Insert into table_name [(字段1, 字段2, 字段3,…)] SELECT 语句;
--后面的select语句中，还可加相应的限制条件(如：where)

delete from…删除
1、删除表中的符合某个条件的所有数据信息：
Delete from table_name where 字段1=数值1，或字段2=数值2,…;
 
2、删除表中所有内容，表结构不删除，以下两种效果一样：
Delete table_name;
truncate table table_name;
 
3、完全删除表:
Drop table table_name;

update …set修改
update table_name set 字段1=数值1 where 字段1=数值1, 字段2=数值2,…;
例如：
UPDATE Store_Information SET Sales = 500
WHERE store_name = "Los Angeles"
AND Date = "Jan-08-1999";


[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
