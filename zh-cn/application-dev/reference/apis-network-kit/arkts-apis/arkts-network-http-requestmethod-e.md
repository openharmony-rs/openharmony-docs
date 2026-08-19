# RequestMethod

HTTP 请求方法。

**起始版本：** 23

<!--Device-http-export enum RequestMethod--><!--Device-http-export enum RequestMethod-End-->

**系统能力：** SystemCapability.Communication.NetStack

## OPTIONS

```TypeScript
OPTIONS = "OPTIONS"
```

OPTIONS方法描述了目标资源的通信选项。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RequestMethod-OPTIONS = "OPTIONS"--><!--Device-RequestMethod-OPTIONS = "OPTIONS"-End-->

**系统能力：** SystemCapability.Communication.NetStack

## GET

```TypeScript
GET = "GET"
```

GET方法请求指定资源的表示。使用GET的请求应该只检索数据，不应该包含请求内容。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RequestMethod-GET = "GET"--><!--Device-RequestMethod-GET = "GET"-End-->

**系统能力：** SystemCapability.Communication.NetStack

## HEAD

```TypeScript
HEAD = "HEAD"
```

HEAD方法请求与GET请求相同的响应，但没有响应主体。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RequestMethod-HEAD = "HEAD"--><!--Device-RequestMethod-HEAD = "HEAD"-End-->

**系统能力：** SystemCapability.Communication.NetStack

## POST

```TypeScript
POST = "POST"
```

POST方法将实体提交给指定的资源，通常会导致服务器上的状态更改。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RequestMethod-POST = "POST"--><!--Device-RequestMethod-POST = "POST"-End-->

**系统能力：** SystemCapability.Communication.NetStack

## PUT

```TypeScript
PUT = "PUT"
```

PUT方法将目标资源的所有当前表示替换为请求内容。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RequestMethod-PUT = "PUT"--><!--Device-RequestMethod-PUT = "PUT"-End-->

**系统能力：** SystemCapability.Communication.NetStack

## DELETE

```TypeScript
DELETE = "DELETE"
```

DELETE方法用于删除指定的资源。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RequestMethod-DELETE = "DELETE"--><!--Device-RequestMethod-DELETE = "DELETE"-End-->

**系统能力：** SystemCapability.Communication.NetStack

## TRACE

```TypeScript
TRACE = "TRACE"
```

TRACE方法沿到达目标资源的路径执行消息环回测试。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RequestMethod-TRACE = "TRACE"--><!--Device-RequestMethod-TRACE = "TRACE"-End-->

**系统能力：** SystemCapability.Communication.NetStack

## CONNECT

```TypeScript
CONNECT = "CONNECT"
```

CONNECT方法建立到由目标资源标识的服务器的隧道。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RequestMethod-CONNECT = "CONNECT"--><!--Device-RequestMethod-CONNECT = "CONNECT"-End-->

**系统能力：** SystemCapability.Communication.NetStack

## PATCH

```TypeScript
PATCH = "PATCH"
```

PATCH方法对资源进行部分修改。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestMethod-PATCH = "PATCH"--><!--Device-RequestMethod-PATCH = "PATCH"-End-->

**系统能力：** SystemCapability.Communication.NetStack

