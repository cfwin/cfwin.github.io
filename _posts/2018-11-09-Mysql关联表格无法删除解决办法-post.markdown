---
layout: post
title: Mysql关联表格无法删除解决办法
date: 2018-11-09 18:32:24.000000000 +09:00
catalog: 	 true
categories: Mysql
tags:
    - Mysql
---



Mysql关联表格无法删除

显示的错误为 ERROR 1451 (23000): Cannot delete or update a parent row: a foreign key constraint fails

解决办法
~~~
SET FOREIGN_KEY_CHECKS=0; -- to disable them

drop table tablename;

SET FOREIGN_KEY_CHECKS=1; -- to re-enable them
~~~

