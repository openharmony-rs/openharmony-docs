# ImeChangeCallback

```TypeScript
export type ImeChangeCallback = (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void
```

The callback of 'imeChange' event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputMethod-export type ImeChangeCallback = (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void--><!--Device-inputMethod-export type ImeChangeCallback = (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputMethodProperty | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 是 | the property of current inputmethod. |
| inputMethodSubtype | [InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md) | 是 | the subtype of current inputmethod. |

