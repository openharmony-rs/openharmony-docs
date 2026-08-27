# NfcVTag

NfcVTag 提供对NFC-V(ISO 15693)技术的属性和I/O操作的访问，继承自TagSession。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NfcVTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NfcVTag的独有接口。

**继承/实现关系：** NfcVTag extends TagSession

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NFC.Tag

## getDsfId

```TypeScript
getDsfId(): number
```

从标签实例获取数据存储格式标识符（DSFID）。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | NfcV 标签的数据存储格式标识符，十六进制表示，范围是0x00~0xFF。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 nfcV
let dsfId : number = nfcV.getDsfId();
console.info("nfcV dsfId: " + dsfId);
```

## getResponseFlags

```TypeScript
getResponseFlags(): number
```

从标签实例获取响应标志。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | NfcV 标签的响应标志，十六进制表示，范围是0x00~0xFF。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 nfcV
let responseFlags : number = nfcV.getResponseFlags();
console.info("nfcV responseFlags: " + responseFlags);
```
