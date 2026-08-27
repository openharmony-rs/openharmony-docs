# getNfcATag

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getNfcATag

```TypeScript
function getNfcATag(tagInfo: TagInfo): NfcATag
```

获取NFC A类型Tag对象，通过该对象可访问NfcA技术类型的Tag。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getNfcA](arkts-connectivity-tag-getnfca-f.md)

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tagInfo | [TagInfo](arkts-connectivity-tag-taginfo-i.md) | 是 | 包含Tag技术类型和相关参数，从[tag.getTagInfo(want: Want)](arkts-connectivity-tag-gettaginfo-f.md)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NfcATag | NFC A类型Tag对象。 |
