# NfcATag

NfcATag 提供 NFC-A(ISO 14443-3A)技术的属性和I/O操作的访问，继承自[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NfcATag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NfcATag的独有接口。

**继承/实现关系：** NfcATag extends TagSession

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NFC.Tag

## getAtqa

```TypeScript
getAtqa(): number[]
```

获取NFC-A标签的Atqa值。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | NfcA 标签的Atqa值，每个number十六进制表示，范围是0x00~0xFF。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 nfcA
let atqa : number[] = nfcA.getAtqa();
console.info("nfcA atqa: " + atqa);
```

## getSak

```TypeScript
getSak(): number
```

获取NFC-A标签的SAK值。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | NfcA 标签的SAK值，十六进制表示，范围是0x00~0xFF。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 nfcA
let sak : number = nfcA.getSak();
console.info("nfcA sak: " + sak);
```
