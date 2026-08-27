# ConnectionNativeInfo

表示Web原生消息连接的连接信息。

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
```

## bundleName

```TypeScript
bundleName: string
```

Web原生消息扩展应用的包名。

**类型：** string

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## connectionId

```TypeScript
connectionId: number
```

Web原生消息扩展连接的唯一标识，由connectNative方法返回，用于标识和管理连接。

**类型：** number

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## extensionOrigin

```TypeScript
extensionOrigin: string
```

浏览器扩展的源URL。

**类型：** string

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## extensionPid

```TypeScript
extensionPid: number
```

Web原生消息扩展的进程ID。

**类型：** number

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core
