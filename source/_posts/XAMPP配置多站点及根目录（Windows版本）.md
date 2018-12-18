---
title: XAMPP配置多站点及根目录（Windows版本）
tags:
  - Web服务器
  - XAMPP
  - 多站点设置
url: 51.html
id: 51
categories:
  - WEB
date: 2018-09-13 08:49:07
---

1、首先修改C:\\WINDOWS\\System32\\drivers\\etc目录下的 hosts 文件，用记事本打开，加入： （是在文件的未尾加入） 127.0.0.1 a.jenkin.fun 127.0.0.1 b.jenkin.fun 2、打开xampp\\apache\\conf\\httpd.conf文件，搜索 “Include conf/extra/httpd-vhosts.conf”，确保前面没有 # 注释符，也就是确保引入了 vhosts 虚拟主机配置文件。 开启了httpd-vhosts.conf，默认的httpd.conf默认配置失效（确保 httpd-vhosts.conf 文件里也开启了虚拟主机配置，见第3条），访问此IP的域名将全部指向 vhosts.conf 中的第一个虚拟主机。（注意是第一个，详见第4） 3、在虚拟主机设置文件xampp\\apache\\conf\\extra\\httpd-vhosts.conf里设置： 取消 NameVirtualHost *:80 前面的 ##，这样就启用了 vhosts.conf ，默认的httpd.conf默认配置失效。虚拟主机配置将只设置在 httpd-vhosts.conf 里。 <VirtualHost *:80> DocumentRoot "a.jenkin.fun 的网站目录" ServerName a.jenkin.fun </VirtualHost> <VirtualHost *:80> DocumentRoot " b.jenkin.fun 的网站目录" ServerName a.jenkin.fun </VirtualHost> 4、 设置完了第3条之后，你会发现访问 localhost直接指向到设置的 a 那个路径去了，这个问题在第2条有讲。也就是开启了 vhosts后，默认的 httpd 的配置就会失效了，默认的访问就指向到 vhosts 里的第一条设置去了。这时候你要把 localhost的目录配置给设置回来。 <VirtualHost *:80> DocumentRoot "C:/xampp/htdocs" ServerName localhost </VirtualHost> 至此，XAMPP 的虚拟主机设置完毕。 重启XAMPP中的Apache，现在访问 localhost 还是原来的 XAMPP 的帮助指南，访问 a.jenkin.fun 将指向到绑定的 a 目录，访问 b.jenkin.fun将指向到绑定的 b 目录。