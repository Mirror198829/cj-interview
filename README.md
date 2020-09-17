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
