# getNfcFTag

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getNfcFTag

```TypeScript
function getNfcFTag(tagInfo: TagInfo): NfcFTag
```

获取NFC F类型Tag对象，通过该对象可访问NfcF技术类型的Tag。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getNfcF](arkts-connectivity-tag-getnfcf-f.md)

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tagInfo | [TagInfo](arkts-connectivity-tag-taginfo-i.md) | 是 | 包含Tag技术类型和相关参数，从[tag.getTagInfo(want: Want)](arkts-connectivity-tag-gettaginfo-f.md)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NfcFTag | NFC F类型Tag对象。 |
