# getNdefFormatable

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getNdefFormatable

```TypeScript
function getNdefFormatable(tagInfo: TagInfo): NdefFormatableTag
```

获取NDEF Formatable类型Tag对象，通过该对象可访问支持NDEF Formatable技术类型的Tag。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tagInfo | [TagInfo](arkts-connectivity-tag-taginfo-i.md) | 是 | Indicates the dispatched tag information. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NdefFormatableTag | NDEF Formatable类型Tag对象，通过该对象访问NDEF Formatable类型的相关接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
