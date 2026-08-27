# NfcFTag

NfcFTag 提供对NFC-F(JIS 6319-4)技术的属性和I/O操作的访问，继承自TagSession。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NfcFTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NfcFTag的独有接口。

**继承/实现关系：** NfcFTag extends TagSession

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NFC.Tag

## getPmm

```TypeScript
getPmm(): number[]
```

从标签实例获取PMm（由IC代码和制造商参数组成）。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | NfcF 标签的PMm信息，每个number十六进制表示，范围是0x00~0xFF。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 nfcF
let pmm : number[] = nfcF.getPmm();
console.info("nfcF pmm: " + pmm);
```

## getSystemCode

```TypeScript
getSystemCode(): number[]
```

从标签实例获取系统代码。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | NfcF 标签的系统代码，每个number十六进制表示，范围是0x00~0xFF。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 nfcF
let systemCode : number[] = nfcF.getSystemCode();
console.info("nfcF systemCode: " + systemCode);
```
