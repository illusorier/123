Web缓存是可以自动保存常见文档副本的HTTP设备。

当Web请求抵达缓存时，如果本地有"已缓存的"副本，就可以从本地存储设备而不是原始服务器中提取这个文档。

缓存无法保存世界上每份文档的副本。

可以用已有的副本为某些到达缓存的请求提供服务，这被称为缓存命中(cache hit)。

其他一些到达缓存的请求可能会由于没有副本可用，而被转发给原始服务器，这被称为缓存未命中(cache miss)。

原始服务器的内容可能会发生变化，缓存要不时对其进行检测，看看它们保存的副本是否仍是服务器上最新的副本。

这些"新鲜度检测"被称为HTTP再验证(revalidation)。

为了有效地进行再验证，HTTP定义了一些特殊的请求，不用从服务器上获取整个对象

HTTP最初是一个匿名、无状态的请求/响应协议。

cookie是当前识别用户，实现持久会话的最好方式。

缓存相关的HTTP header

通过特殊的HTTP *Cache-Control* 首部和 *Expires* 首部，HTTP允许原始服务器向每个文档附加了一个"过期日期"。

服务器用HTTP/1.0的 *Expires* 首部或HTTP/1.1的 *Cache-Control:max-age* 

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