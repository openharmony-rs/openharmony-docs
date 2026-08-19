# ResponseCode

发起请求返回的响应码。

**起始版本：** 23

<!--Device-http-export enum ResponseCode--><!--Device-http-export enum ResponseCode-End-->

**系统能力：** SystemCapability.Communication.NetStack

## OK

```TypeScript
OK = 200
```

请求成功。用于GET与POST请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-OK = 200--><!--Device-ResponseCode-OK = 200-End-->

**系统能力：** SystemCapability.Communication.NetStack

## CREATED

```TypeScript
CREATED = 201
```

已创建。请求成功并已创建新资源。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-CREATED = 201--><!--Device-ResponseCode-CREATED = 201-End-->

**系统能力：** SystemCapability.Communication.NetStack

## ACCEPTED

```TypeScript
ACCEPTED = 202
```

已接受。请求已被接受，但未处理完成。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-ACCEPTED = 202--><!--Device-ResponseCode-ACCEPTED = 202-End-->

**系统能力：** SystemCapability.Communication.NetStack

## NOT_AUTHORITATIVE

```TypeScript
NOT_AUTHORITATIVE = 203
```

非授权信息。请求成功。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-NOT_AUTHORITATIVE = 203--><!--Device-ResponseCode-NOT_AUTHORITATIVE = 203-End-->

**系统能力：** SystemCapability.Communication.NetStack

## NO_CONTENT

```TypeScript
NO_CONTENT = 204
```

无内容。服务器成功处理，但未返回内容。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-NO_CONTENT = 204--><!--Device-ResponseCode-NO_CONTENT = 204-End-->

**系统能力：** SystemCapability.Communication.NetStack

## RESET

```TypeScript
RESET = 205
```

重置内容。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-RESET = 205--><!--Device-ResponseCode-RESET = 205-End-->

**系统能力：** SystemCapability.Communication.NetStack

## PARTIAL

```TypeScript
PARTIAL = 206
```

部分内容。服务器成功处理了部分GET请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-PARTIAL = 206--><!--Device-ResponseCode-PARTIAL = 206-End-->

**系统能力：** SystemCapability.Communication.NetStack

## MULT_CHOICE

```TypeScript
MULT_CHOICE = 300
```

多种选择。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-MULT_CHOICE = 300--><!--Device-ResponseCode-MULT_CHOICE = 300-End-->

**系统能力：** SystemCapability.Communication.NetStack

## MOVED_PERM

```TypeScript
MOVED_PERM = 301
```

永久移动。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-MOVED_PERM = 301--><!--Device-ResponseCode-MOVED_PERM = 301-End-->

**系统能力：** SystemCapability.Communication.NetStack

## MOVED_TEMP

```TypeScript
MOVED_TEMP = 302
```

临时移动。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-MOVED_TEMP = 302--><!--Device-ResponseCode-MOVED_TEMP = 302-End-->

**系统能力：** SystemCapability.Communication.NetStack

## SEE_OTHER

```TypeScript
SEE_OTHER = 303
```

查看其它地址。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-SEE_OTHER = 303--><!--Device-ResponseCode-SEE_OTHER = 303-End-->

**系统能力：** SystemCapability.Communication.NetStack

## NOT_MODIFIED

```TypeScript
NOT_MODIFIED = 304
```

未修改。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-NOT_MODIFIED = 304--><!--Device-ResponseCode-NOT_MODIFIED = 304-End-->

**系统能力：** SystemCapability.Communication.NetStack

## USE_PROXY

```TypeScript
USE_PROXY = 305
```

使用代理。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-USE_PROXY = 305--><!--Device-ResponseCode-USE_PROXY = 305-End-->

**系统能力：** SystemCapability.Communication.NetStack

## BAD_REQUEST

```TypeScript
BAD_REQUEST = 400
```

客户端请求的语法错误，服务器无法理解。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-BAD_REQUEST = 400--><!--Device-ResponseCode-BAD_REQUEST = 400-End-->

**系统能力：** SystemCapability.Communication.NetStack

## UNAUTHORIZED

```TypeScript
UNAUTHORIZED = 401
```

请求需要用户的身份认证。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-UNAUTHORIZED = 401--><!--Device-ResponseCode-UNAUTHORIZED = 401-End-->

**系统能力：** SystemCapability.Communication.NetStack

## PAYMENT_REQUIRED

```TypeScript
PAYMENT_REQUIRED = 402
```

保留字段，将来使用。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-PAYMENT_REQUIRED = 402--><!--Device-ResponseCode-PAYMENT_REQUIRED = 402-End-->

**系统能力：** SystemCapability.Communication.NetStack

## FORBIDDEN

```TypeScript
FORBIDDEN = 403
```

服务器理解请求客户端的请求，但是拒绝执行此请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-FORBIDDEN = 403--><!--Device-ResponseCode-FORBIDDEN = 403-End-->

**系统能力：** SystemCapability.Communication.NetStack

## NOT_FOUND

```TypeScript
NOT_FOUND = 404
```

服务器无法根据客户端的请求找到资源(网页)。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-NOT_FOUND = 404--><!--Device-ResponseCode-NOT_FOUND = 404-End-->

**系统能力：** SystemCapability.Communication.NetStack

## BAD_METHOD

```TypeScript
BAD_METHOD = 405
```

客户端请求中的方法被禁止。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-BAD_METHOD = 405--><!--Device-ResponseCode-BAD_METHOD = 405-End-->

**系统能力：** SystemCapability.Communication.NetStack

## NOT_ACCEPTABLE

```TypeScript
NOT_ACCEPTABLE = 406
```

服务器无法根据客户端请求的内容特性完成请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-NOT_ACCEPTABLE = 406--><!--Device-ResponseCode-NOT_ACCEPTABLE = 406-End-->

**系统能力：** SystemCapability.Communication.NetStack

## PROXY_AUTH

```TypeScript
PROXY_AUTH = 407
```

请求需要代理的身份认证。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-PROXY_AUTH = 407--><!--Device-ResponseCode-PROXY_AUTH = 407-End-->

**系统能力：** SystemCapability.Communication.NetStack

## CLIENT_TIMEOUT

```TypeScript
CLIENT_TIMEOUT = 408
```

请求超时。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-CLIENT_TIMEOUT = 408--><!--Device-ResponseCode-CLIENT_TIMEOUT = 408-End-->

**系统能力：** SystemCapability.Communication.NetStack

## CONFLICT

```TypeScript
CONFLICT = 409
```

服务器完成客户端的PUT请求时可能返回此代码，服务器处理请求时发生了冲突。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-CONFLICT = 409--><!--Device-ResponseCode-CONFLICT = 409-End-->

**系统能力：** SystemCapability.Communication.NetStack

## GONE

```TypeScript
GONE = 410
```

客户端请求的资源已经不存在。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-GONE = 410--><!--Device-ResponseCode-GONE = 410-End-->

**系统能力：** SystemCapability.Communication.NetStack

## LENGTH_REQUIRED

```TypeScript
LENGTH_REQUIRED = 411
```

服务器无法处理客户端发送的不带Content-Length的请求信息。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-LENGTH_REQUIRED = 411--><!--Device-ResponseCode-LENGTH_REQUIRED = 411-End-->

**系统能力：** SystemCapability.Communication.NetStack

## PRECON_FAILED

```TypeScript
PRECON_FAILED = 412
```

客户端请求信息的先决条件错误。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-PRECON_FAILED = 412--><!--Device-ResponseCode-PRECON_FAILED = 412-End-->

**系统能力：** SystemCapability.Communication.NetStack

## ENTITY_TOO_LARGE

```TypeScript
ENTITY_TOO_LARGE = 413
```

由于请求的实体过大，服务器无法处理，因此拒绝请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-ENTITY_TOO_LARGE = 413--><!--Device-ResponseCode-ENTITY_TOO_LARGE = 413-End-->

**系统能力：** SystemCapability.Communication.NetStack

## REQ_TOO_LONG

```TypeScript
REQ_TOO_LONG = 414
```

请求的URI过长(URI通常为网址)，服务器无法处理。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-REQ_TOO_LONG = 414--><!--Device-ResponseCode-REQ_TOO_LONG = 414-End-->

**系统能力：** SystemCapability.Communication.NetStack

## UNSUPPORTED_TYPE

```TypeScript
UNSUPPORTED_TYPE = 415
```

服务器无法处理请求的格式。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-UNSUPPORTED_TYPE = 415--><!--Device-ResponseCode-UNSUPPORTED_TYPE = 415-End-->

**系统能力：** SystemCapability.Communication.NetStack

## RANGE_NOT_SATISFIABLE

```TypeScript
RANGE_NOT_SATISFIABLE = 416
```

请求范围不符合要求。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-RANGE_NOT_SATISFIABLE = 416--><!--Device-ResponseCode-RANGE_NOT_SATISFIABLE = 416-End-->

**系统能力：** SystemCapability.Communication.NetStack

## INTERNAL_ERROR

```TypeScript
INTERNAL_ERROR = 500
```

服务器内部错误，无法完成请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-INTERNAL_ERROR = 500--><!--Device-ResponseCode-INTERNAL_ERROR = 500-End-->

**系统能力：** SystemCapability.Communication.NetStack

## NOT_IMPLEMENTED

```TypeScript
NOT_IMPLEMENTED = 501
```

服务器不支持请求的功能，无法完成请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-NOT_IMPLEMENTED = 501--><!--Device-ResponseCode-NOT_IMPLEMENTED = 501-End-->

**系统能力：** SystemCapability.Communication.NetStack

## BAD_GATEWAY

```TypeScript
BAD_GATEWAY = 502
```

充当网关或代理的服务器，从远端服务器接收到了一个无效的请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-BAD_GATEWAY = 502--><!--Device-ResponseCode-BAD_GATEWAY = 502-End-->

**系统能力：** SystemCapability.Communication.NetStack

## UNAVAILABLE

```TypeScript
UNAVAILABLE = 503
```

由于超载或系统维护，服务器暂时无法处理客户端的请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-UNAVAILABLE = 503--><!--Device-ResponseCode-UNAVAILABLE = 503-End-->

**系统能力：** SystemCapability.Communication.NetStack

## GATEWAY_TIMEOUT

```TypeScript
GATEWAY_TIMEOUT = 504
```

充当网关或代理的服务器，未及时从远端服务器获取请求。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-GATEWAY_TIMEOUT = 504--><!--Device-ResponseCode-GATEWAY_TIMEOUT = 504-End-->

**系统能力：** SystemCapability.Communication.NetStack

## VERSION

```TypeScript
VERSION = 505
```

服务器不支持客户端请求中使用的HTTP协议版本。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ResponseCode-VERSION = 505--><!--Device-ResponseCode-VERSION = 505-End-->

**系统能力：** SystemCapability.Communication.NetStack

