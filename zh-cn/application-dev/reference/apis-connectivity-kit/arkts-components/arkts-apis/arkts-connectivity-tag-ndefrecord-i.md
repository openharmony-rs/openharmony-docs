# NdefRecord

```TypeScript
export interface NdefRecord
```

NDEF标签Record属性的定义，参考NDEF标签技术规范《NFCForum-TS-NDEF_1.0》的定义细节。

**起始版本：** 9

<!--Device-tag-export interface NdefRecord--><!--Device-tag-export interface NdefRecord-End-->

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

**原子化服务API（仅ArkTS-Dyn）：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-NdefRecord-id: int[]--><!--Device-NdefRecord-id: int[]-End-->

**系统能力：** SystemCapability.Communication.NFC.Tag

## payload

```TypeScript
payload: number[]
```

NDEF Record的PAYLOAD，每个number十六进制表示，范围是0x00~0xFF。

**类型：** number[]

**起始版本：** 9

**原子化服务API（仅ArkTS-Dyn）：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-NdefRecord-payload: int[]--><!--Device-NdefRecord-payload: int[]-End-->

**系统能力：** SystemCapability.Communication.NFC.Tag

## rtdType

```TypeScript
rtdType: number[]
```

NDEF Record的RTD(Record Type Definition)类型值，每个number十六进制表示，范围是0x00~0xFF。

**类型：** number[]

**起始版本：** 9

**原子化服务API（仅ArkTS-Dyn）：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-NdefRecord-rtdType: int[]--><!--Device-NdefRecord-rtdType: int[]-End-->

**系统能力：** SystemCapability.Communication.NFC.Tag

## tnf

```TypeScript
tnf: number
```

NDEF Record的TNF(Type Name Field)。

**类型：** number

**起始版本：** 9

**原子化服务API（仅ArkTS-Dyn）：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-NdefRecord-tnf: int--><!--Device-NdefRecord-tnf: int-End-->

**系统能力：** SystemCapability.Communication.NFC.Tag
