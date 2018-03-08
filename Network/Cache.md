HTTP最初是一个匿名、无状态的请求/响应协议。

cookie是当前识别用户，实现持久会话的最好方式。

缓存相关的HTTP header

通过特殊的HTTP Cache-Control首部和Expires首部，HTTP允许原始服务器向每个文档附加了一个"过期日期"。

在缓存文档过期之前，缓存可以以任意频率使用这些副本，而无需与服务器联系。

仅仅是已缓存文档过期了并不意味着它和原始服务器上目前处于活跃状态的文档有实际的区别：这只是意味着到了要进行核对的时间了。

这种情况被称为"服务器再验证"，  

HTTP定义了5个条件请求首部，所有条件首部都以前缀"If-"开头。

对缓存再验证来说最有用的2个首部是If-Modified-Since和If-None-Match。

#### ETag

Response header 响应首部

The `ETAG` HTTP response header is an identifier for a specific version of a resource.

It allows caches to be more efficient, 

On the other side, 

If the resource at a given URL changes, a new `ETag` value must be generated.

#### Cache-Control

The `Cache-Control` general-header field 

通用首部

通过`Cache-Control`，我们可以控制服务器端资源在客户端的缓存策略，

Cache-Control: No-Cache

The no-cache directive means that a browser may cache a response, but must first submit a validation request to an origin server.

Cache-Control: No-Store

The no-store directive means browsers are not allowed to cache a response and must pull it from the server each time it's requested.

Caching static assets:

    Cache-Control: public, max-age=31533600

The private response 

#### Last-Modified

The `Last-Modified` response HTTP header contains the date and time at which the origin server believes the resource was last modified.

It is used 

Less accurate than an `ETag` header, it is a fallback mechanism.

    Last-Modified: Wed, 21 Oct 2015 07:28:00 GMT

#### X-DNS-Prefetch-Control