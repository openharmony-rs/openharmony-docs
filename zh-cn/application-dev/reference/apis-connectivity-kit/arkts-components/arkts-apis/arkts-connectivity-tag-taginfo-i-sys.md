# TagInfo

在对相关Tag类型卡片进行读写之前，必须先获取[TagInfo](arkts-connectivity-tag-taginfo-i.md)相关属性值，以确认设备读取到的Tag卡片支持哪些技术类型。这样Tag应用程序才能调用正确的接口和所读取到的Tag卡片进行通信。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NFC.Tag

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## extrasData

```TypeScript
extrasData: PacMap[]
```

标签所支持技术的扩展属性值。

**系统接口：** 此接口为系统接口。

**类型：** [PacMap](../../apis-ability-kit/arkts-apis/arkts-ability-dataabilityhelper-pacmap-i.md)[]

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**系统接口：** 此接口为系统接口。

## remoteTagService

```TypeScript
remoteTagService: rpc.RemoteObject
```

NFC服务进程的远端对象，用于客户端和服务之间的接口通信。

**系统接口：** 此接口为系统接口。

**类型：** [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**系统接口：** 此接口为系统接口。

## tagRfDiscId

```TypeScript
tagRfDiscId: number
```

标签发现时分配的ID值。

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**系统接口：** 此接口为系统接口。
