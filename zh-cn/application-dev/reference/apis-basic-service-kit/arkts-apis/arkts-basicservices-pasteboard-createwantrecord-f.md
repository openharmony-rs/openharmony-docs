# createWantRecord

## createWantRecord

```TypeScript
function createWantRecord(want: Want): PasteDataRecord
```

创建一条Want内容条目。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [createRecord](arkts-basicservices-pasteboard-createrecord-f.md#createRecord)(mimeType: string, value: ValueType)

<!--Device-pasteboard-function createWantRecord(want: Want): PasteDataRecord--><!--Device-pasteboard-function createWantRecord(want: Want): PasteDataRecord-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | 一条新建的Want内容条目。 |

## 示例

```TypeScript
import { Want } from '@kit.AbilityKit';

let object: Want = {
    bundleName: "com.example.aafwk.test",
    abilityName: "com.example.aafwk.test.TwoAbility"
};
let record: pasteboard.PasteDataRecord = pasteboard.createWantRecord(object);
```

