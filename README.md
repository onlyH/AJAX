# AJAX
ajax的相关知识

``` bash
var request = new XMLHttpRequest();
```

### http
http是计算机通过网络进行通信的规则
无状态协议--不建立持久的链接，服务端不保留持久链接，没有记忆
#### 7个步骤：
- 建立TCP链接。
- web浏览器向服务器发送请求命令。
- web浏览器发送请求头信息。
- web服务器应答。
- web服务器发送应答头信息。
- web服务器向浏览器发送数据。
- web服务器关闭TCP链接。

#### 一个http请求一般有四个部分组成：
1. http请求的方法或动作（get，post）
2. 正在请求的URL（地址）
3. 请求头（客户端环境信息，身份验证信息）
4. 请求体（正文，客户提交的查询字符串信息，表单信息）

##### get：信息获取，使用URL传递参数，对发送信息的数量有限制，2000个字符
##### post：修改服务器上的资源，对所发信息的数量无限制

#### http请求
1. 数组或文字组成的状态码（显示请求成功还是失败）
2. 响应头（服务器类型，日期时间，内容类型和长度）
3. 响应体（响应正文）

#### XMLHttpRequest发送请求
```
open(method,url,async)
send(string)
```

```
request.open("GET","get.php",true);  //异步
request.send();

request.open("POST","post.php",true);
request.send();

request.open("POST","create.php",true);
request.setRequestHeader("Content-type","appliction/x-www-form-urlencoded");
request.send("name=李华&sex=男");
```


#### XMLHttpRequest取得相应
- responseText：获得字符串形式的响应数据
- responseXML：获得XML影视的响应数据
- status和statusText：以数字和文本形式返回http状态码
- getAllResponseHeader()：获取所有的响应报头
- getResponseHeader()：查询响应中的某个字段的值
##### readyState属性：
- 0:请求位初始化，open还没有调用
- 1:服务器链接已建立，open已经调用
- 2:请求已接受，接收到头信息了
- 3:请求处理中，收到响应主体
- 4:请求已完成，且响应已就绪，响应完成了

```
var request = new XMLHttpRequest;
request.open("GET","get.php",true);
request.send();
request.onreadystatechange = function(){
  if(request.readyState === 4 && request.status === 200) {
    //做一些事情 request.responseText
  }
}
```
