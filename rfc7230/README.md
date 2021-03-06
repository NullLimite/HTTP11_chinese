RFC: https://tools.ietf.org/html/rfc7230

- [1. 介绍](Introduction/README.md)
    - [1.1 要求表示法](Introduction/Requirements_Notation.md)
    - [1.2 语法表示法](Introduction/Syntax_Notation.md)
- [2. 结构](Architecture/README.md)
    - [2.1 客户端/服务器消息](Architecture/Client_Server_Messaging.md)
    - [2.2 实施多样性](Architecture/Implementation_Diversity.md)
    - [2.3 中介](Architecture/Intermediaries.md)
    - [2.4 缓存](Architecture/Caches.md)
    - [2.5 一致性和错误处理](Architecture/Conformance_and_Error_Handling.md)
    - [2.6 协议版本](Architecture/Protocol_Versioning.md)
    - [2.7 统一资源标识符](Architecture/Uniform_Resource_Identifiers/README.md)
        - [2.7.1 http URI格式](Architecture/Uniform_Resource_Identifiers/http_URI_Scheme.md)
        - [2.7.2 https URI格式](Architecture/Uniform_Resource_Identifiers/https_URI_Scheme.md)
        - [2.7.3 http和https URI规范化和比较](Architecture/Uniform_Resource_Identifiers/http_and_https_URI_Normalization_and_Comparison.md)
- [3. 消息格式](Message_Format/README.md)
    - [3.1 开始行](Message_Format/Start_Line/README.md)
        - [3.1.1 请求行](Message_Format/Start_Line/Request_Line.md)
        - [3.1.2 状态行](Message_Format/Start_Line/Status_Line.md)
    - [3.2 头字段](Message_Format/Header_Fields/README.md)
        - [3.2.1 字段扩展性](Message_Format/Header_Fields/Field_Extensibility.md)
        - [3.2.2 字段顺序](Message_Format/Header_Fields/Field_Order.md)
        - [3.2.3 空白](Message_Format/Header_Fields/Whitespace.md)
        - [3.2.4 字段解析](Message_Format/Header_Fields/Field_Parsing.md)
        - [3.2.5 字段限制](Message_Format/Header_Fields/Field_Limits.md)
        - [3.2.6 字段值组件](Message_Format/Header_Fields/Field_Value_Components.md)
    - [3.3 消息体](Message_Format/Message_Body/README.md)
        - [3.3.1 传输编码](Message_Format/Message_Body/Transfer-Encoding.md)
        - [3.3.2 内容长度](Message_Format/Message_Body/Content-Length.md)
        - [3.3.3 消息体长度](Message_Format/Message_Body/Message_Body_Length.md)
    - [3.4 处理不完整消息](Message_Format/Handling_Incomplete_Messages.md)
    - [3.5 消息解析健壮性](Message_Format/Message_Parsing_Robustness.md)
- [4. 传输编码](Transfer_Codings/README.md)
	- [4.1 分块传输编码](Transfer_Codings/Chunked_Transfer_Coding/README.md)
		- [4.1.1 分块扩展](Transfer_Codings/Chunked_Transfer_Coding/Chunk_Extensions.md)
		- [4.1.2 分块报尾部分](Transfer_Codings/Chunked_Transfer_Coding/Chunked_Trailer_Part.md)
		- [4.1.3 解码分块](Transfer_Codings/Chunked_Transfer_Coding/Decoding_Chunked.md)
	- [4.2 压缩编码](Transfer_Codings/Compression_Codings/README.md)
		- [4.2.1 Compress编码](Transfer_Codings/Compression_Codings/Compress_Coding.md)
		- [4.2.2 Deflate编码](Transfer_Codings/Compression_Codings/Deflate_Coding.md)
		- [4.2.3 Gzip编码](Transfer_Codings/Compression_Codings/Gzip_Coding.md)
	- [4.3 TE](Transfer_Codings/TE.md)
	- [4.4 Trailer](Transfer_Codings/Trailer.md)
- [5. 消息路由](Message_Routing/README.md)
	- [5.1 识别目标资源](Message_Routing/Identifying_a_Target_Resource.md)
	- [5.2 连接入站](Message_Routing/Connecting_Inbound.md)
	- [5.3 请求目标](Message_Routing/Request_Target/README.md)
        - [5.3.1 原始形式](Message_Routing/Request_Target/origin-form.md)
		- [5.3.2 完整形式](Message_Routing/Request_Target/absolute-form.md)
		- [5.3.3 授权形式](Message_Routing/Request_Target/authority-form.md)
		- [5.3.4 星号形式](Message_Routing/Request_Target/asterisk-form.md)
	- [5.4 Host](Message_Routing/Host.md)
	- [5.5 有效的请求URI](Message_Routing/Effective_Request_URI.md)
	- [5.6 将响应与请求关联](Message_Routing/Associating_a_Response_to_a_Request.md)
	- [5.7 消息转发](Message_Routing/Message_Forwarding/README.md)
		- [5.7.1 Via](Message_Routing/Message_Forwarding/Via.md)
		- [5.7.2 转换](Message_Routing/Message_Forwarding/Transformations.md)
- [6. 连接管理](Connection_Management/README.md)
	- [6.1 Connection](Connection_Management/Connection.md)
	- [6.2 建立](Connection_Management/Establishment.md)
    - [6.3 保持](Connection_Management/Persistence/README.md)
        - [6.3.1 重试请求](Connection_Management/Persistence/Retrying_Requests.md)
        - [6.3.2 管道化](Connection_Management/Persistence/Pipelining.md)
    - [6.4 并发](Connection_Management/Concurrency.md)
    - [6.5 失败和超时](Connection_Management/Failures_and_Timeouts.md)
    - [6.6 销毁](Connection_Management/Tear-Down.md)
    - [6.7 Upgrade](Connection_Management/Upgrade.md)
- [7. ABNF列表扩展：#规则](ABNF_List_Extension/README.md)
- [8. IANA注意事项](IANA_Considerations/README.md)
    - [8.1 头字段注册](IANA_Considerations/Header_Field_Registration.md)
    - [8.2 URI方案注册](IANA_Considerations/URI_Scheme_Registration.md)
    - [8.3 互联网媒体类型注册](IANA_Considerations/Internet_Media_Type_Registration/README.md)
        - [8.3.1 互联网媒体类型message/http](IANA_Considerations/Internet_Media_Type_Registration/message_http.md)
        - [8.3.2 互联网媒体类型application/http](IANA_Considerations/Internet_Media_Type_Registration/application_http.md)
    - [8.4 传输编码注册](IANA_Considerations/Transfer_Coding_Registry/README.md)
        - [8.4.1 程序](IANA_Considerations/Transfer_Coding_Registry/Procedure.md)
        - [8.4.2 注册](IANA_Considerations/Transfer_Coding_Registry/Registration.md)
    - [8.5 内容编码注册](IANA_Considerations/Content_Coding_Registration.md)
    - [8.6 Upgrade令牌注册](IANA_Considerations/Upgrade_Token_Registration/README.md)
        - [8.6.1 程序](IANA_Considerations/Upgrade_Token_Registration/Procedure.md)
        - [8.6.2 注册](IANA_Considerations/Upgrade_Token_Registration/Upgrade_Token_Registration.md)
- [9. 安全注意事项](Security_Considerations/README.md)
    - [9.1 建立权威](Security_Considerations/Establishing_Authority.md)
    - [9.2 中介的风险](Security_Considerations/Risks_of_Intermediaries.md)
    - [9.3 通过协议元素长度的攻击](Security_Considerations/Attacks_via_Protocol_Element_Length.md)
    - [9.4 响应分裂](Security_Considerations/Response_Splitting.md)
    - [9.5 请求走私](Security_Considerations/Request_Smuggling.md)
    - [9.6 信息完整性](Security_Considerations/Message_Integrity.md)
    - [9.7 消息机密性](Security_Considerations/Message_Confidentiality.md)
    - [9.8 服务器日志信息的隐私](Security_Considerations/Privacy_of_Server_Log_Information.md)
- [10. 致谢](Acknowledgments/README.md)
- [11. 引用](References/README.md)
    - [11.1 规范性参考](References/Normative_References.md)
    - [11.2 信息参考](References/Informative_References.md)
- [附录A. HTTP版本历史](Appendix_A/README.md)
    - [A.1 从HTTP/1.0的改变](Appendix_A/Changes_from_http10/README.md)
        - [A.1.1 多宿主Web服务器](Appendix_A/Changes_from_http10/Multihomed_Web_Servers.md)
        - [A.1.2 Keep-Alive连接](Appendix_A/Changes_from_http10/Keep-Alive_Connections.md)
        - [A.1.3 Transfer-Encoding介绍](Appendix_A/Changes_from_http10/Introduction_of_Transfer-Encoding.md)
    - [A.2 从RFC2612的改变](Appendix_A/Changes_from_RFC_2612.md)
- [附录B. 收集的ABNF](Appendix_B/README.md)