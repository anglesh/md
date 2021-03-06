## HTTP文档

### HTTP方法

方法 | 说明| 支持的HTTP协议版本 |
-- | -- | --|
GET | 获取资源 | 1.0、1.1
POST | 传输实体主体 | 1.0、1.1
PUT | 传输文件 | 1.0、1.1
HEAD | 获得报文首部 | 1.0、1.1
DELETE | 删除文件 | 1.0、1.1
OPTIONS | 询问支持的方法 | 1.1
TRACE | 追踪路径 | 1.1
CONNECT | 要求用隧道协议连接代理 | 1.1
LINK | 建立和资源之间的联系 | 1.0
UNLINK | 断开连接关系 | 1.0

### HTTP报文

请求端(客户端)的HTTP报文叫做请求报文，响应端(服务器端)的叫做响应报文。HTTP报文本身是由多行(用CR + LF做换行符)数据构成的字符串文本。

HTTP报文一般由三部分组成，报文首部、空行(CR + LF)和报文主体组成。

首部字段包含：通用首部、请求首部、响应首部和实体首部。

### HTTP状态码

状态码 | 类别 | 原因短语
-- | -- | -- |
1xx | 信息状态码 | 接受的请求正在处理
2xx | 成功状态码 | 请求正常处理完毕
3xx | 重定向状态码 | 需要进行附加操作以完成请求
4xx | 客户端错误状态码 | 服务器无法处理请求
5xx | 服务器错误状态码 | 服务器请求出错

#### 2xx

##### 200 **OK**

表示从客户端发来的请求在服务端被正常处理了。

响应报文返回的信息会因为请求方法的不同而发生改变。使用GET方法时，请求的资源会作为响应实体返回；而使用HEAD方法时，请求的资源不会随报文一起返回。

##### 204 No Content

该状态码表示服务器对请求已经成功处理，但是在返回的响应报文中不包含实体的主体部分，也不允许返回任何实体的主体。

##### 206 Partial Content

改状态码表示客户端进行了范围请求，而服务器成功执行了这部分的GET请求。响应报文中包含由Content-Range指定范围的实体内容。

#### 3xx 重定向

##### 301 Moved Permanently

永久重定向。该状态码表示请求的资源已经被分配了新的URI，以后应该使用资源现在所指的URI。

##### 302 Found

临时重定向。该状态码表示请求的资源已被分配了新的URI，希望本次能使用新的URI访问。

##### 303 See Other

该状态码表示由于请求对应的资源存在着另一个URI，应该使用GET方法定向获取请求的资源。

303和302有个相同的功能，但是303状态码明确表示客户端应当采用GET方法获取资源。

##### 304 Not Modified

该状态码表示请求的资源没有改变。304状态码返回时，不包含任何响应的实体部分。

##### 307 Temporary Redirect

临时重定向，与302含义相同。

尽管302标准禁止将POST改成GET，但实际使用时并没有准守。307会遵照浏览器标准，不会从POST变成GET。

