# InterceptorType

HTTP拦截器的类型枚举。  
| 名称 | 值 |说明 | | ------ | --|-------------------------------------- | | INITIAL_REQUEST |'INITIAL_REQUEST' |在初始HTTP请求组装完成后拦截。| | REDIRECTION | 'REDIRECTION' |当收到重定向响应时拦截。| | CACHE_CHECKED | 'READ_CACHE' |在检查并且命中HTTP缓存时拦截。| | NETWORK_CONNECT | 'CONNECT_NETWORK' |在网络请求将要发出前拦截。| | FINAL_RESPONSE | 'FINAL_RESPONSE' |在获取最终HTTP响应时拦截。|

**起始版本：** 22

**系统能力：** SystemCapability.Communication.NetStack

## INITIAL_REQUEST

```TypeScript
INITIAL_REQUEST = 'INITIAL_REQUEST'
```

在初始HTTP请求组装完成后进行拦截。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## REDIRECTION

```TypeScript
REDIRECTION = 'REDIRECTION'
```

在初始HTTP请求组装完成后进行拦截。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## CACHE_CHECKED

```TypeScript
CACHE_CHECKED = 'READ_CACHE'
```

Intercept after we checked the HTTP cache.

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## NETWORK_CONNECT

```TypeScript
NETWORK_CONNECT = 'CONNECT_NETWORK'
```

Intercept when we perform network connection, such as TLS and TCP.

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## FINAL_RESPONSE

```TypeScript
FINAL_RESPONSE = 'FINAL_RESPONSE'
```

Intercept when we get the final HTTP response.

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack
