# createWantData

## createWantData

```TypeScript
function createWantData(want: Want): PasteData
```

构建一个Want剪贴板内容对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [createData](arkts-basicservices-pasteboard-createdata-f.md#createData)(mimeType: string, value: ValueType)

<!--Device-pasteboard-function createWantData(want: Want): PasteData--><!--Device-pasteboard-function createWantData(want: Want): PasteData-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 剪贴板内容对象。 |

## 示例

```TypeScript
import { Want } from '@kit.AbilityKit';

let object: Want = {
    bundleName: "com.example.aafwk.test",
    abilityName: "com.example.aafwk.test.TwoAbility"
};
let pasteData: pasteboard.PasteData = pasteboard.createWantData(object);
```

