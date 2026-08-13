# ConnectionInfo

Web原生消息连接的信息对象。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

<!--Device-unnamed-export interface ConnectionInfo--><!--Device-unnamed-export interface ConnectionInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## bundleName

```TypeScript
bundleName: string
```

调用方的应用包名，用于身份识别和权限校验，可据此判断是否允许该应用建立连接或进行消息交互。

**类型：** string

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

<!--Device-ConnectionInfo-bundleName: string--><!--Device-ConnectionInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## connectionId

```TypeScript
connectionId: number
```

连接的唯一标识符，用于区分和管理不同的Web原生消息连接，可用于在日志、状态跟踪或资源清理时定位特定连接。

**类型：** number

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

<!--Device-ConnectionInfo-connectionId: number--><!--Device-ConnectionInfo-connectionId: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## extensionOrigin

```TypeScript
extensionOrigin: string
```

调用方扩展的原始URL，用于安全控制和来源识别，可据此判断扩展的合法性或实施基于域名的访问策略。

**类型：** string

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

<!--Device-ConnectionInfo-extensionOrigin: string--><!--Device-ConnectionInfo-extensionOrigin: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## fdRead

```TypeScript
fdRead: number
```

用于读取数据的管道文件描述符，可通过此文件描述符从Web端读取消息数据。

**类型：** number

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

<!--Device-ConnectionInfo-fdRead: number--><!--Device-ConnectionInfo-fdRead: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## fdWrite

```TypeScript
fdWrite: number
```

用于写入数据的管道文件描述符，可通过此文件描述符向Web端发送消息数据。

**类型：** number

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

<!--Device-ConnectionInfo-fdWrite: number--><!--Device-ConnectionInfo-fdWrite: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

