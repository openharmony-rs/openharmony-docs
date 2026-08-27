# TagInfo

在对相关Tag类型卡片进行读写之前，必须先获取[TagInfo](#taginfo)相关属性值，以确认设备读取到的Tag卡片支持哪些技术类型。这样Tag应用程序才能调用正确的接口和所读取到的Tag卡片进行通信。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NFC.Tag

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## supportedProfiles

```TypeScript
supportedProfiles: number[]
```

支持的技术类型。  
**说明：** 从API version 7开始支持，从API version 9开始废弃，使用[tag.TagInfo#technology](#taginfo)替代。

**类型：** number[]

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [technology](#technology)

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

## technology

```TypeScript
technology: number[]
```

支持的技术类型，每个number值表示所支持技术类型的常量值。

**类型：** number[]

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

## uid

```TypeScript
uid: number[]
```

标签的uid，每个number值是十六进制表示，范围是0x00~0xFF。

**类型：** number[]

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag
