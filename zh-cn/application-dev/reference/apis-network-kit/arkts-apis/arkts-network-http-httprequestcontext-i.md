# HttpRequestContext

HTTP请求上下文数据。该对象实例在拦截器的[interceptorHandle](arkts-network-http-httpinterceptor-i.md#interceptorhandle)方法中作为参数传入，开发者可以通过该对象获取和修改 HTTP请求的相关信息。

**起始版本：** 22

<!--Device-http-export interface HttpRequestContext--><!--Device-http-export interface HttpRequestContext-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## body

```TypeScript
body: Object
```

The header of an HTTP request interceptor. It can be modified in an interceptor.

**类型：** Object

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestContext-body: Object--><!--Device-HttpRequestContext-body: Object-End-->

**系统能力：** SystemCapability.Communication.NetStack

## header

```TypeScript
header: Object
```

The header of an HTTP request interceptor. It can be modified in an interceptor.

**类型：** Object

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestContext-header: Object--><!--Device-HttpRequestContext-header: Object-End-->

**系统能力：** SystemCapability.Communication.NetStack

## url

```TypeScript
url: string
```

The URL of an HTTP request interceptor. It can be modified in an interceptor.

**类型：** string

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestContext-url: string--><!--Device-HttpRequestContext-url: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

