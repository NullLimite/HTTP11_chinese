消息都使用一个通用逻辑进行解析，而与头字段的名字无关。给定字段值的内容不会被解析直到消息解释的下一个阶段（通常在消息的整个头部分被处理后）。所以本规范没有像之前版本那样使用ABNF规则来定义每一个“字段名:字段值”组合。作为替代的，本规范使用根据每个注册字段名称命名的ABNF规则，其中规则定义了该字段的相应字段值的有效语法（即，在通过字段解析器从字段部分提取字段值之后）。

在字段名和冒号之间不允许出现空白。过去，在请求路由和相应处理中处理这类空白的不同已经导致了安全漏洞。发送者**必须**以一个400的响应码（坏请求）拒绝任何接收到的在字段名和冒号之间包含空白的请求。代理**必须**在将一个响应消息转发到下游的之前移除任何这类空白。

一个字段值可能有前导和/或尾随的可选空白（OWS）；一个单独的SP在字段值之前是首选的以便于人类一致的可读性。字段值不包含任何前导或未遂的空白：在从头字段中提取字段值的时候，在字段值的第一个非空白字节之前或在字段值的最后一个非空白字节之后出现的OWS应该被解析器排除。

历史上，通过在每个额外的行之前至少使用一个空格或水平标签（obs-fold），可以在多行上扩展HTTP头字段值。除了在消息/ http媒体类型内（8.3.1节），本规范不赞成使用这种折行。除非消息打算在消息/ http媒体类型中打包，否则发送者**不得**生成包含行折叠的消息（即，其中包含任何包含与obs-fold规则匹配的字段值）。

接收不在消息/ http容器内的请求消息中的obs-fold的服务器**必须**通过发送400（错误请求）拒绝该消息，最好使用一个表示来解释过时的行折叠是不可接受的，或在解释字段值或向下游转发消息之前用一个或多个SP字节替换每个接收到的obs-fold。

接收不在消息/ http容器内的响应消息中的obs-fold的代理或网关**必须**丢弃该消息并用502（坏网关）响应代替它，最好使用一个表示说明接收到了不可接受的行折叠，或在解释字段值或向下游转发消息之前用一个或多个SP字节替换每个接收到的obs-fold。

接收到不在消息/ http容器中的响应消息中的obs-fold的用户代理必须在解释字段值之前用一个或多个SP字节替换每个接收到的obs-fold。

历史上，HTTP允许字段内容使用ISO-8859-1字符集[ISO-8859-1]中的文本，仅通过使用[RFC2047]编码来支持其他字符集。 实际上，大多数HTTP头字段值只使用US-ASCII字符集的一个子集[USASCII]。 新定义的头字段应该将其字段值限制为US-ASCII八位字节。 接收者应该将字段内容（obs-text）中的其他八位字节视为不透明的数据。