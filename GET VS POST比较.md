# GET VS POST

GET和POST都是请求方法。

* GET用于获取资源，而POST用于传输实体主体。GET使用比POST要更广泛。
* GET传递的参数出现在URL中，而POST的位于实体主体中。
  * GET参数只支持ASCII码（因为URL只支持ASCII），POST支持Unicode码。
* GET方法是安全的，因为不会改变服务器状态；而POST不安全，因为会上传数据到服务器。
  * 安全的还有HEAD，OPTIONS等；不安全的有PUT，DELETE等。
* GET，HEAD，PUT和DELETE等方法都是幂等的，即执行一次的效果和执行多次的效果是一样的；POST不是。
  * POST方法执行多次可能会将多组（重复）数据上传到服务器的数据库，效果和执行一次不一样。
* 并不是所有响应都可以缓存，需要满足几个条件：
  * 请求方法可缓存，包括GET和HEAD。PUT，DELETE和POST都不可缓存。其实很好理解，后三个方法我们并不太需要它们的响应，只是为了发送指令/数据。
  * 响应报文状态码可缓存。
  * 响应报文首部字段Cache-Control没有禁用。
* GET在JavaScript的XMLHttpRequest中使用时会将header和data一起发送；POST则先发送header，再发送data。
  * 这里header应该包括请求首部 + 实体首部；data应该就是实体主体。
* GET方法最多传输1KB的数据；而POST为2MB。

