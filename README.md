Name
====
Magick Image (魔图)

Table of Contents
=================

* [Name](#name)
* [Synopsis](#synopsis)
* [Installation](#installation)
* [Demo](#demo)
* [Authors](#authors)

Synopsis
========
	Use GraphicsMagick,Nginx,Luajit to convert image

Installation
============
You need install GraphicsMagick lib

    yum install -y GraphicsMagick-devel.x86_64

You need to compile [ngx_lua](https://github.com/chaoslawful/lua-nginx-module/tags) with your Nginx.

You need to configure
the [lua_package_path](https://github.com/chaoslawful/lua-nginx-module#lua_package_path) directive to
add the path of your `lua-resty-cookie` source tree to ngx_lua's Lua module search path, as in

    # nginx.conf
    http {
		resolver 8.8.8.8;

        lua_package_path "/path/to/lua-resty-cookie/lib/?.lua;;";
        ...
    }

and then load the library in Lua:

    server {
		location / {
        	index  index.html index.htm;
            default_type text/html;
       		rewrite_by_lua_file '/path/to/magick-image/rewrite.lua';
    	}
    }


[Back to TOC](#table-of-contents)


RestfulAPI
=======

	http://mi.henji.org/index.html


[Back to TOC](#table-of-contents)

Demo
=====================

### 图片信息
	http://mi.henji.org/demo1.jpg?imageInfo

### 图片基本缩略图
	http://mi.henji.org/demo1.jpg?imageView/1/w/180
	http://mi.henji.org/demo1.jpg?imageView/1/w/140/h/90
	http://mi.henji.org/demo1.jpg?imageView/2/w/180
	http://mi.henji.org/demo1.jpg?imageView/2/h/120
	http://mi.henji.org/demo1.jpg?imageView/3/w/180
	http://mi.henji.org/demo1.jpg?imageView/3/w/140/h/90

### 高级图片处理
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/!30p
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/!30px
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/!x30p
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/200x
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/x300
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/200x300
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/!200x300r
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/200x300!
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/200x300>
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/800x800<
	http://mi.henji.org/demo2.jpg?imageMogr/v1/thumbnail/300000@

	http://mi.henji.org/demo2.jpg?imageMogr/v1/crop/300x
	http://mi.henji.org/demo2.jpg?imageMogr/v1/crop/x300
	http://mi.henji.org/demo2.jpg?imageMogr/v1/crop/320x480
	http://mi.henji.org/demo2.jpg?imageMogr/v1/crop/!320x480a10a20
	http://mi.henji.org/demo2.jpg?imageMogr/v1/crop/!320x480-10a20
	http://mi.henji.org/demo2.jpg?imageMogr/v1/crop/!320x480a10-20
	http://mi.henji.org/demo2.jpg?imageMogr/v1/crop/!320x480-10-20
	http://mi.henji.org/demo2.jpg?imageMogr/v1/gravity/Center/crop/!320x480-10-20

### 水印
	http://mi.henji.org/demo3.jpg?watermark/2/text/MTcxNzPprZTlm74=/fontsize/1000/font/6buR5L2T/fill/I2ZmMDAwMA==/gravity/Center/dx/30/dy/20/angle/10
	http://mi.henji.org/demo3.jpg?watermark/1/gravity/SouthEast/dx/10/dy/10/image/aHR0cDovL3VlMS4xNzE3My5pdGMuY24vaW1hZ2VzL2xvZ28vMjAxMy8xNzE3My1sb2dvLTgweDMwLnBuZw==

[Back to TOC](#table-of-contents)


Authors
=======

MingQing Lee <limingqing@cyou-inc.com>, 17173 Inc.

[Back to TOC](#table-of-contents)
