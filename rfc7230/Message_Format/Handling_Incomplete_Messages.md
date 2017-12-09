服务器接收到一个不完整的请求消息通常是因为取消请求或者触发了超时错误，这时**可以**在关闭连接前发送一个错误响应。

客户端接收到一个不完整的响应消息可能发生在连接被过早的关闭或者按分块传输编码解码失败，这时**必须**将消息记录为不完整的。对不完整响应的缓存要求定义在RFC7234第3节。

如果响应在头部分的中间位置（在空行被接收到之前）终止并且状态码可能依赖头字段来传达完整的响应含义，那么客户端不能假设含义被传达；客户端可能需要再次发起请求以决定接下来的行为。

如果使用分块传输编码的消息体没有收到指示结束编码的0字节分块，那么这个消息是不完整的。如果使用有效的Content-Length值的消息已接收的消息体的尺寸比由Content-Length给定的值小，那么这个消息是不完整的。既没有分块传输编码也没有内容长度的响应通过关闭连接而终止被认为是完整的，而不管接收到的消息正文八位字节的数目如何，只要标题部分被完整地地接收。