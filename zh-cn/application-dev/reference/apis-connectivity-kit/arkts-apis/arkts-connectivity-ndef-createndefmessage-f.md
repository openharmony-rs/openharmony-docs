# createNdefMessage

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## createNdefMessage

```TypeScript
function createNdefMessage(data: number[]): NdefMessage
```

使用原始字节数据创建NDEF标签的Message。该数据必须符合NDEF Record数据格式，如果不符合格式，则返回的NdefMessage数据对象，所包含的NDEF Record列表会为空。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | number[] | 是 | 原始字节，每个number十六进制表示，范围是0x00~0xFF。要求必须满足NDEF Record的格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NdefMessage | NDEF标签的Message，详见NDEF技术规范《NFCForum-TS-NDEF_1.0》。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |


## createNdefMessage

```TypeScript
function createNdefMessage(ndefRecords: NdefRecord[]): NdefMessage
```

使用NDEF Records列表，创建NDEF Message。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ndefRecords | [NdefRecord](arkts-connectivity-tag-ndefrecord-i.md)[] | 是 | NDEF标签的Record列表，详见NDEF技术规范《NFCForum-TS-NDEF_1.0》。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NdefMessage | NDEF标签的Message，详见NDEF技术规范《NFCForum-TS-NDEF_1.0》。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
