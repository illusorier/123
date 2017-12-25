缓存相关的HTTP header

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

The no-cache directive means that 

Cache-Control: No-Store

The no-store directive means browsers are not allowed to cache a response and must pull it from the server each time it's requested.

The private response 

#### Last-Modified

The `Last-Modified` response HTTP 

Less accurate than an `ETag` header, it is a fallback mechanism.

#### X-DNS-Prefetch-Control