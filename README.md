参考地址
* https://github.com/qiu-deqing/FE-interview 
* https://blog.csdn.net/come0across/article/details/104895118

# 浏览器
---

## 浏览器从输入 URL 到页面加载显示完成，这个过程中发生了什么？
* 浏览器查找当前URL是否存在缓存，并比较缓存是否过期
* DNS解析URL对应的IP。DNS 具体的查找ip地址过程，包括：浏览器缓存->系统缓存->路由器缓存
* 根据IP建立TCP连接（三次握手）
* 发送HTTP请求
* 服务器处理HTTP请求，浏览器接受HTTP响应。服务器返回给浏览器的信息，主要由HTML，css，js，图片文件组成
* 浏览器解析并渲染页面
* 关闭TCP连接（四次握手）

## HTTP和HTTPS的区别
| 内容 | 传输信息安全性 | 连接方式 | 端口 | 证书申请方式 |
| --- | --- | --- | --- | --- |
| http |超文本传输协议，信息是明文传输 | 无状态连接 | 80 | 免费申请 |
| https | 具有安全性的ssl加密传输协议，为浏览器和服务器之间的通信加密 | 由SSL＋HTTP协议构建的可进行加密传输、身份认证的网络协议 | 443 | 需要到ca申请证书，一般免费证书很少，需要交费 |  

## 什么是跨域？跨域请求资源的方法有哪些？
`浏览器同源策略`，凡是发送请求url的`协议`、`域名`、`端口`三者之间任意一个与当前页面地址不同即为跨域。存在跨域的情况：
* 网络协议不同，如http协议访问https协议。
* 端口不同，如80端口访问8080端口。
* 域名不同，如qianduanblog.com访问baidu.com。
* 子域名不同，如abc.qianduanblog.com访问def.qianduanblog.com。
* 域名和域名对应ip,如www.a.com访问20.205.28.90.

##### 解决方法：
(1) porxy代理

定义和用法：proxy代理用于将请求发送给后台服务器，通过服务器来发送请求，然后将请求的结果传递给前端。

实现方法：通过nginx代理；

注意点：1、如果你代理的是https协议的请求，那么你的proxy首先需要信任该证书（尤其是自定义证书）或者忽略证书检查，否则你的请求无法成功。 

(2)、CORS 【Cross-Origin Resource Sharing】
定义和用法：是现代浏览器支持跨域资源请求的一种最常用的方式。
使用方法：一般需要后端人员在处理请求数据的时候，添加允许跨域的相关操作。如下：
``` javascript
res.writeHead(200, {
    "Content-Type": "text/html; charset=UTF-8",
    "Access-Control-Allow-Origin":'http://localhost',
    'Access-Control-Allow-Methods': 'GET, POST, OPTIONS',
    'Access-Control-Allow-Headers': 'X-Requested-With, Content-Type'
});
```
（3）jsonp
定义和用法：通过动态插入一个script标签。浏览器对script的资源引用没有同源限制，同时资源加载到页面后会立即执行（没有阻塞的情况下）。

特点：通过情况下，通过动态创建script来读取他域的动态资源，获取的数据一般为json格式。

### 说一下图片的懒加载和预加载
https://www.jianshu.com/p/4876a4fe7731

### 常用的浏览器内核
IE 、火狐（Firefox）,谷歌（Chrome）,Safari和Opera

### 块级元素和行内元素的区别
1.行内元素与块级元素直观上的区别二、行内元素与块级元素的三个区别

    行内元素会在一条直线上排列（默认宽度只与内容有关），都是同一行的，水平方向排列。

    块级元素各占据一行（默认宽度是它本身父容器的100%（和父元素的宽度一致），与内容无关），垂直方向排列。块级元素从新行开始，结束接着一个断行。

2.块级元素可以包含行内元素和块级元素。行内元素不能包含块级元素，只能包含文本或者其它行内元素。

3.行内元素与块级元素属性的不同，主要是盒模型属性上：行内元素设置width无效，height无效(可以设置line-height)，margin上下无效，padding上下无效

### 清除浮动有哪些方法
### js中数组去重的方法有哪些 
https://www.cnblogs.com/zsp-1064239893/p/11196501.html

### 你所了解到的Web攻击技术，如何防止XSS攻击

### web前端开发，如何提高页面性能优化？

