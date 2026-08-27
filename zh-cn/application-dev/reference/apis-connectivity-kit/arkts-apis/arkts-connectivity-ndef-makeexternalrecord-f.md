# makeExternalRecord

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## makeExternalRecord

```TypeScript
function makeExternalRecord(domainName: string, type: string, externalData: number[]): NdefRecord
```

根据应用程序特定的外部数据，构建NDEF标签的Record。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainName | string | 是 | 外部数据发布组织的域名，一般是应用程序的包名。 |
| type | string | 是 | 外部数据的指定类型。 |
| externalData | number[] | 是 | 外部数据内容，每个number十六进制表示，范围是0x00~0xFF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NdefRecord](arkts-connectivity-tag-ndefrecord-i.md) | NDEF标签的Record，详见NDEF技术规范《NFCForum-TS-NDEF_1.0》。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
