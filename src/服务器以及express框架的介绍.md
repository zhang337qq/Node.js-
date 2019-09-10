# express框架
## express基本介绍
> 基于 Node.js 平台，快速、开放、极简的 Web 开发框架(koa)
## express基本使用
### express安装
npm install express --save
### express搭建web服务器
1. 什么是web服务器
> Web服务器一般指网站服务器，是指驻留于因特网上某种类型计算机的程序，可以向浏览器等Web客户端提供文档，也可以放置网站文件，让全世界浏览；可以放置数据文件，让全世界下载。目前最主流的三个Web服务器是Apache、 Nginx 、IIS
2. 代码实现
```
const express = require('express)
const app = express()
app.get('/',(req,res)=>{
    res.send('首页')
})
app.listen(8080,()=>{
    console.log('web server start')
})
// 在浏览器中输入: localhost:8080 
```
### api接口
#### api接口理解
>  前端 ： 1.写界面  2.请求数据  3.数据处理
>  后端 ： 写 api接口
#### 创建api接口
```
app.get('/api/user/list',(req,res)=>{
    
})
app.post('/api/user/login',(req,res)=>{
    
})
```
#### postman工具测试接口
> 下载postman软件并安装
### 中间件
#### 第三方中间件(body-parser)
1. 安装
> npm install body-parser --save
2. 使用
```
const bodyParser = require('bodyParser')
app.use(bodyParser.urlencoded({extended:false}))
app.use(bodyParser.json())
```
#### 自定义中间件(全局，局部)
```
// 全局中间件,请求任何路径将执行当前函数
app.use((req,res,next)=>{
    
})

// 局部中间件
app.get('/food',(req,res,next)=>{

},(req,res)=>{

})
```
### 静态资源目录设置
```
app.use('/public',express.static(path.join(__dirname,'./public')))
```
### 路由(express.Router)

> **当一个路径有多个匹配规则时，使用app.use(path,callback)**，否则使用相应的app.method(get、post)

```
// user.js
const router = require('express).Router()
router.get('/findAll',(req,res)=>{})
router.post('/login',(req,res)=>{})
module.exports = router

// server.js
const userRouter = require('./routers/user')
app.use('/user',userRouter)

```
# mongodb
## mongodb的介绍
> MongoDB 是由C++语言编写的，是一个基于分布式文件存储的开源数据库系统
## mongodb的安装
1. 下载 (百度mongodb)
> https://www.mongodb.com/download-center/community
2. 安装  
    + 最后一个对号不选 
    + 缺少数据库文件  c/data/db
    + 不是内部的命令  需要设置环境变量 mongod 的bin 目录路径
3. 命令行下运行 MongoDB 服务器(mongod --dbpath 路径)
4. 连接MongoDB(mongo)
5. 配置 MongoDB 服务
## mongodb常用命令
```
// 查看当前数据库
db
// 查看当前数据库操作命令的帮助
db.help()
// 查看所有数据库
show dbs
// 选择当前数据库(没有则自动创建)
use dbName
// 删除当前数据库
db.dropDatabase()
// 在当前数据库中创建集合
db.createCollection('集合名称')
// 删除当前集合名称
db.集合名称.drop()
// 查看所有集合
show collections
// 向集合中添加一个文档
db.集合名称.insert(对象)
// 查询集合中所有文档
db.集合名称.find()
// 查询集合中所有文档并格式化
db.集合名称.find().pretty()
// 更新满足条件的文档
db.集合名称.update({条件},{$set:{要修改的数据},{multi:true}})
// 用新文档替换已有的文档
db.集合名称.save({数据})
// 删除满足条件的文档
db.remove({条件})
db.集合名称.find().skip(number).limit(number).sort({域名:-1|1})
```

