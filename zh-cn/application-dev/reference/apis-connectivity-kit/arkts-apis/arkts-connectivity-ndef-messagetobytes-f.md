# messageToBytes

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## messageToBytes

```TypeScript
function messageToBytes(ndefMessage: NdefMessage): number[]
```

把输入的NDEF消息数据对象，转换为字节格式的数据。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ndefMessage | NdefMessage | 是 | NDEF消息数据对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | NDEF消息数据对象，所转换成的字节格式的数据。每个number十六进制表示，范围是0x00~0xFF。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
