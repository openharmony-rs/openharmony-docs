# HttpProtocol

HTTP协议版本。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## HTTP1_1

```TypeScript
HTTP1_1 = 0
```

协议HTTP1.1。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## HTTP2

```TypeScript
HTTP2 = 1
```

协议HTTP2。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## HTTP3

```TypeScript
HTTP3 = 2
```

协议HTTP3，若系统或服务器不支持，则使用低版本的HTTP协议请求。  
**注意：** 仅对HTTPS的URL生效，HTTP则会请求失败。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack
