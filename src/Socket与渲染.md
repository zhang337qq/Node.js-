# Socket
## 什么是Socket
> 网络上的两个程序通过一个双向的通信连接实现数据的交换，这个连接的一端称为一个socket（套字接）,HTTP是轿车，提供了封装或者显示数据的具体形式; Socket(tcp/ip协议的封装)是发动机，提供了网络通信的能力。

## Socket连接与HTTP连接的区别
+ HTTP是短连接，Socket(基于TCP协议的)是长连接。尽管HTTP1.1开始支持持久连接，但仍无法保证始终连接。而Socket连接一旦建立TCP三次握手，除非一方主动断开，否则连接状态一直保持。

+ HTTP连接服务端无法主动发消息，Socket连接双方请求的发送先后限制。这点就比较重要了，因为它将决定二者分别适合应用在什么场景下。HTTP采用“请求-响应”机制，在客户端还没发送消息给服务端前，服务端无法推送消息给客户端。必须满足客户端发送消息在前，服务端回复在后。Socket连接双方类似peer2peer的关系，一方随时可以向另一方喊话。

## Socket基于tcp协议的通信流程
![socket通信流程](./mkimg/基于tcp协议的socket通信流程.webp)
// net 模块(node.js自带的模块可以实现聊天室)
// websocket方式(需要现代浏览器才支持的协议,可以实现聊天室)
## 通过socket.io来实现socket编程
### socket.io简介
> node.js提供了高效的服务端运行环境，但是由于浏览器端对HTML5的支持不一，为了兼容所有浏览器，提供卓越的实时的用户体验，并且为程序员提供客户端与服务端一致的编程体验，于是socket.io诞生。Socket.io将Websocket和轮询 （Polling）机制以及其它的实时通信方式封装成了通用的接口，并且在服务端实现了这些实时机制的相应代码。
### 安装socket.io
> npm install socket.io --save
### 使用socket.io实现聊天室
1. 实现服务端socket功能
2. 实现客户端socket功能
3. 运行两个端，开始聊天
4. 知识点总结
> socket.on('自定义事件',(msg)=>{}) 监听某事件,并且接收数据
> socket.emit('自定义事件',数据) 触发当前socket端的事件并传递数据
> socket.broadcast.emit('自定义事件',数据) 广播给所有socket端除了当前socket端以外
> 内置事件名有connection,disconnect,error(服务端socket、客户端都有)
> 服务端通过引入socket.io模块，将socket.io模块注入到当前web服务器中,再通过socket.io对象的on来监听connection事件
> 客户端socket通过引入socketlio客户端js文件，再通过io.connect('ip加端口')来连接服务端

# SSR渲染与BSR渲染的区别
> 任何的WEB项目基本的需要就是将后端的数据库中的数据渲染到页面上
## BSR客户端渲染
+ 优点：灵活，真正的前后端分离，方便于前后台各自更新维护
+ 缺点： 对SEO不友好，增加了http请求次数，减缓了页面加载速度
## SSR服务端渲染
+ 优点: 对SEO友好，减少了http请求次数，加速了页面初次渲染速度
+ 缺点： 不灵活，前后端耦合度太高

# 使用token方式验证用户登录
## 安装jsonwebtoken
## 利用jsonwebtoken封装创建token，验证token的方法
## 在服务端登录成功时产生token并将token发给客户端
## 客户端发送请求时带上token(可以放置在headers中)
## 在服务端取得token验证，token正确放行，否则报错
