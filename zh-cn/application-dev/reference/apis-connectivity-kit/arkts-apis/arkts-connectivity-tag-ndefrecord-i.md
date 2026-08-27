# NdefRecord

NDEF标签Record属性的定义，参考NDEF标签技术规范《NFCForum-TS-NDEF_1.0》的定义细节。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NFC.Tag

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## id

```TypeScript
id: number[]
```

NDEF Record的ID，每个number十六进制表示，范围是0x00~0xFF。

**类型：** number[]

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

## payload

```TypeScript
payload: number[]
```

NDEF Record的PAYLOAD，每个number十六进制表示，范围是0x00~0xFF。

**类型：** number[]

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

## rtdType

```TypeScript
rtdType: number[]
```

NDEF Record的RTD(Record Type Definition)类型值，每个number十六进制表示，范围是0x00~0xFF。

**类型：** number[]

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

## tnf

```TypeScript
tnf: number
```

NDEF Record的TNF(Type Name Field)。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag
