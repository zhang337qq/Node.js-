# promise
> 大量的异步操作 如果需要顺序执行 通过回调函数执行 回调地狱
## 封装promise 函数
```
function test(){
    return new Promise((reslove,reject)=>{

    })
}
```
## 链式调用
```
xxx().then(data=>{}).then(data=>).catch()
```

# node操作mongodb数据库
## mongoose的安装
> npm install mongoose --save
## mongoose的使用
1. 连接数据库
```
const mongoose = require('mongoose')
mongoose.connect('mongodb://localhost/test',{useNewUrlParser:true})
const db = mongoose.connection
db.on('error',(err)=>{
    console.log('数据库服务器连接失败')
})
db.on('open',()=>{
    console.log('数据库服务器连接成功')
})
```
2. 创建文档结构对象
```
const userSchema = new mongoose.Schema({
    username:{type:String,required:true},
    password:{type:String,required:true},
    age:Number,
    sex:{type:Number,default:1}
})
```
3. 创建数据模型对象
```
const userModel = mongoose.model('member',userSchema)
```
4. 文档的curd
```
userModel.insertMany([{},{}]).then().catch() //添加文档
userModel.find(条件).then().catch() //查找文档
userModel.updateOne(条件,{$set:{}}).then().catch()  //修改一个文档
userModel.updateMany(条件,{$set:{}}).then().catch() //修改多个文档
userModel.deleteOne(条件}).then().catch() //删除文档
userModel.deleteMany(条件}).then().catch() //删除文档
```
## 登录、注册、发送验证码接口实现
1. api接口实现
2. 登录页面搭建
3. 前端对接api接口，实现登录

# apidoc生成api接口文档 
1. 安装
```
npm install apidoc -g
```
2. 生成api文档
> 在api接口文档中写注释
> 生成apidoc文档(apidoc -i ./routers/ -o ./doc/)