# Node.js

## Node.js简介

Node.js是一个基于chrome v8 引擎的javascript 的运行环境  可以做后端  一些JsEs6 的语法也可以使用

Node.js 也是一个使用了事件驱动，非阻塞式（也就是遇到问题无法执行命令的时候，并不会被这个命令阻止后面代码的执行，会跳过这个问题，继续执行代码，同一个时间可以做多件事） I/O（输入输出）的模型

## Node.js 命令

node -v 

node 后面文件夹名称

## Node.js 模块化

### 内置模块

要用fs 模块化  就要每次都要引入这个fs 模块化

方法: const fs = require('fs')//也就是内置fs 

### 第三方模块

### 自定义模块

​	创建一个模块(一个js文件是一个单独的模块)

​	到处一个模块(module.exports = name(也就是函数名))

​	引用一个模块并调用

## fs 内置fs 模块使用

### 文件夹操作

####     异步创建文件夹

这个创建后如果出错，报错 ，并不会影响后面代码的运行

异步创建方法 

fs.mkdir

#### 	同步创建文件夹

同步创建也就是按个执行，如果遇到错误，那么后面的代码就不会执行

解决方法  用 try 和each 把可能会出错的代码放进去

####    删除文件夹

fs.rmdir 

这个删除的话只能删除空的目录

####    重命名文件夹

fs.rename("00"，"./11", (err) =>{进行if 判断}){两个餐数，第一个也就是要被修改的文件夹名称，第二个也就是重命名什么名称}

#### 读取文件夹

fs.readdir(path,(err,data)=>{})

#### 创建文件

##### fs.writeFile

 这个文件如果没有就会创建，并且内容会强制覆盖上一次的文件内容

fs.writeFile ('路径', "content", (err回调函数) =>{})

##### fs.appendFile

这个如果没有文件就会创建，内容并不会强制覆盖，如果原来文件有内容这个也就将现在的内容添加进去

#### 删除文件

fs.unlink

会将文件强制进行删除

有两个参数  （path ， 回调函数）

#### 读取文件内容

fs.readFile  读取的时候需要带入参数 也就是data 但是要将data 进行转换成字符转  toString()才能获取到  文件里的内容

#### 读取文件各种参数

fs.stat

里面有一些语法  

1.stat.isFile()

2.stat.isDirectory()

## 爬虫

将某网站的内容复制过来存到本地的服务器

定义变量  http = require('http')

url  = "要爬虫的网址直接复制进来"  //如果目标网址是加密过的https  那么

定义变量哪里就要将结尾的http  改成https 

http.get(url,(req, res)=>{	

res.setEncoding('binary')//如果下载的是图片

​	//rep  请求对象

​	//res  响应对象

//进行监听  绑定到请求对象中

//监听数据下载的事件  data

var data ='';

rep.on('data', (chunk) =>{

​	data += chunk

console.log("数据正在下载")

​	})



//监听数据下载成功的事件 end

req.on('end', ()=>{//在保存图标的时候

