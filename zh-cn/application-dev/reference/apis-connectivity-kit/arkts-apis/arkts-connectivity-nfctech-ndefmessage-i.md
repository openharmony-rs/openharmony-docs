# NdefMessage

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NFC.Tag

## getNdefRecords

```TypeScript
getNdefRecords(): tag.NdefRecord[]
```

获取NDEF消息中的所有记录。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| tag.NdefRecord[] | NDEF标签的Record列表，详见NDEF技术规范《NFCForum-TS-NDEF_1.0》。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 从 tag.ndef.createNdefMessage 或 ndefTag.getNdefMessage 获取 ndefMessage。
// let ndefMessage : tag.NdefMessage = tag.ndef.createNdefMessage(...);
// let ndefMessage : tag.NdefMessage = ndefTag.getNdefMessage();

let ndefRecords : tag.NdefRecord[] = ndefMessage.getNdefRecords();
console.info("ndef ndefRecords number: " + ndefRecords.length);
```
