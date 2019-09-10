# markdown使用
1. 创建标题(#)
2. 代码块(```)
3. 引用内容(>)
4. 超链接([链接文本](链接地址))
5. 水平线(---)
6. 列表(+或者-)

---

# Node.js
## Node.js是什么
>  Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 
>  Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 

## 为什么要学Node.js
1. 了解前后端交互流程
2. 能够写api接口
3. 了解后端开发的工作，方便交流
4. 全栈工程师
## 如何安装
> [node.js官网](http://nodejs.cn/)下载程序包安装
## 如何运行(REPL)
```
node -v
node hello.js
```
## 模块化
+ 内置模块（node.js中提供的可以直接调用）
+ 第三方模块
+ 自定义模块
    - 创建一个模块 （一个js文件是一个模块）
    - 导出一个模块  (module.exports=name)
    - 引用一个模块并且调用
## 内置fs模块使用
### 文件夹操作
+ fs.readdir(),fs.readdirSync()
+ fs.mkdir()
+ fs.rmdir()
+ fs.rename()
### 文件操作
+ fs.writeFile()
+ fs.appendFile()
+ fs.readFile()
+ fs.unlink()
+ fs.stat()
## 内置url模块使用
+ url.parse()
+ url.format()
## 内置querystring模块的使用
+ querystring.parse()
+ querystring.escape()
## 爬虫案例
1. 获取目标网站内容
    + http.get(url,(res)=>{})
    + req.on('data',(chunk)=>{})
    + req.end(()=>{})
2. 分析网站内容
3. 获取到有效信息并进一步操作
    + cheerio
        - 安装
        - $ = cheerio.load(内容字符串)
        - $('css 选择器')
## 邮箱验证码案例
1. 安装nodemailer模块
```
npm install nodemailer -save
```
2. 创建发送邮件的对象
```
let transporter = nodemailer.createTransport({})
```
3. 发送邮件
```
transporter.sendMail({})
```

