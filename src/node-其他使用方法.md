# 上传图片
## 安装multer
> npm install multer --save
## 使用multer
### 创建上传文件的接口
```
const router = require('express').Router()
const multer = require('multer)
const storage = multer.diskStorage({
    destination(req,file,cb){
        cb(null,'./uploads')
    }
    filename(req,file,cb){
        cb(null,'保存文件的名称')
    }
})
// 用于筛选哪些文件不用上传
function fileFilterFun(req,file,cb){
    if(file.size > 82332){
        cb(new Error('文件大小过大'))
    }
    cb(null,true)
}
const upload = multer({storage:storage,fileFilter:fileFilterFun}).singer('file')

router.post('/upload/',(req,res)=>{
    upload(req,res,err=>{
         if(err){
            res.send({error:1,msg:err.message})
        }else{
            let filePath = req.file.path.replace(/\\/g,'/')
            let fileInfo = {
                url:filePath
            }
            res.send({error:0,msg:'上成功',data:fileInfo})
        }
    })
})
```
### 对接上传文件的接口
> 将file对象封装到formData对象上
> 通过$.ajax请求上传文件接口，注意配置参数如下
```
$.ajax({
    url: 'action',
    type: 'POST',
    data: formData,
    //文件上传时必须配置的参数contentType和processData
    contentType: false,
    processData: false,
    dataType: "json",//返回的数据格式
})
```
# 解决跨域问题
## cors
1. 安装cors
```
npm install cors --save
```
2. 使用cors
```
const cors = require('cors)
app.use(cors()) // 全局允许跨域
```
## 使用代理
> 通过请求api接口文件所在的web服务作代理，后端不存在跨域的问题
1. 安装request模块
```
npm install request --save
```
2. 代理实现
```
app.use('^/proxy',(req,res)=>{
    // 凡是请求的接口以proxy开头的则转发到目标服务器
    request({
        url:'',
        method:req.method,
        body:req.body,
        json:true,
    },(err,response,body)=>{
        // body是目标服务器返回的内容
        res.send(body)
    })
})
```
## 使用jsonp
> 原理是将客户端的js函数传递给后端，后端获取到此函数，传入前端需要的数据作为函数的参数调用，返回给客户端
> 注意： jsonp只支持get方式请求

# session(会话)实现登录
1. 安装express-session
> npm install express-session --save
2. express-session的基本使用
```
const session = require('expess-session')
app.use(session({
    secret:'',//签名的密钥
    cookie:{
        path:'/',
        maxAge:60*60*1000
    },
    resave:true,// 即使 session 没有被修改，也保存 session 值，默认为 true
    saveUninitialized:true //无论有没有session cookie，每次请求都设置个session cookie ，默认给个标示为 connect.sid
}))

// 配置后用req.session可以读写session数据
// req.session.destroy() 销毁当前会话数据
```
