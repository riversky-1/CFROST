---
title: Linux_1
tags: Linux_start
categories: Linux
abbrlink: 7dc07f2a
date: 2021-11-26 15:58:46
---

# **Linux基础语法**

mkdir: 创建文件夹    						`mkdir test`

touch: 创建文件  							  `touch test.cpp`

pwd: 显示当前路径   						直接使用`pwd`即可

ctril c: 取消命令, 并且换行

ctrl u: 清空本行命令

tab键: 补全当前命令或文件名（如果存在），补全不了可以快速按两下tab，可以显示备选选项

ls: 列出当前目录下的所有文件			`-a`显示隐藏文件 `-l`显示权限

cd XXX: 进入XXX目录下					

`cd /home/`使用全路径					`cd -` 返回上一次所在的目录

`cd ..`返回上一级目录					`cd ~`返回用户目录

cp XXX YYY:  将XXX文件复制成YYY，XXX和YYY可以是一个路径，比如../dir/a.txt，表示上层目录下的dir文件夹中的a.txt文件

`cp ../dir/a.txt ../dir/b.txt`

rm XXX: 删除普通文件； rm XXX -r: 删除文件夹  (XXX 支持正则表达式)

mv XXX YYY: 将XXX文件移动到YYY，XXX和YYY可以是一个路径；重命名也能用该命令

cat XXX: 展示文件XXX中的内容

windows下：复制命令行里的命令可以使用ctrl + shift + c    粘贴可用ctrl + shift + v