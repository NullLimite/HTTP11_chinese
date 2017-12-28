"Referer"头字段允许用户代理为目标资源指定一个URI引用，目标URI是从这个URI中获得（即，“被引用”，虽然这段名被拼写错误）。当生成Referer字段值的时候，用户代理**不得**包括URI引用中的片段和用户信息组件RFC3986。

> ```
>    Referer = absolute-URI / partial-URI
> ```

Referer头字段允许服务器给其他资源生成反向连接用于简单的分析，日志记录，缓存优化等。它还允许找到过时或错误的链接来进行维护。一些服务器使用Referer头字段作为拒绝从其他站点链接的一种手段或跨站请求伪造的限制，但不是所有的请求都包含它。

例如：

> ```
>   Referer: http://www.example.org/hypertext/Overview.html
> ```

如果目标URI是从一个没有自己的URI的资源（例如，来自用户键盘的输入，或者用户书签/收藏的要给条目）获得的。用户代理**必须**排除Referer字段或者发送一个“`about:blank`”值。 

Referer字段有潜力揭示请求上下文信息或用户浏览历史，如果引用资源的标识符透露个人信息（如帐户名）或机密资源（如防火墙后或安全服务内部），这可能是一个隐私担忧。大多数通用用户代理在引用的资源是本地“文件”或“数据”URI时不发送Referer头字段。如果引用页面是通过安全协议被接收的，用户代理**不得**在不受保护的HTTP请求中发送Referer头字段。查看9，4节了解额外安全注意事项。

一些中介已经被知道会无条件的从传出的请求中移除Referer头字段。这有干扰防止CSRF攻击的不良副作用，这可能对他们的用户更有害。希望限制用户信息在Referer中泄露的中介或用户代理扩展应该限制他们的改变为特定的编辑，例如使用假名或截断查询和/或路径组件以替换内部域名。当字段值与作为请求目标的host共享相同的方案时，一个中介**不应该**修改或删除Referer头字段。