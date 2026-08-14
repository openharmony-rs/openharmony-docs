# getInputMethodSetting

## getInputMethodSetting

```TypeScript
function getInputMethodSetting(): InputMethodSetting
```

获取客户端设置实例[InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md#InputMethodSetting)。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [getSetting](arkts-ime-inputmethod-getsetting-f.md#getSetting)

<!--Device-inputMethod-function getInputMethodSetting(): InputMethodSetting--><!--Device-inputMethod-function getInputMethodSetting(): InputMethodSetting-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) | 返回当前客户端设置实例。 |

## 示例

```TypeScript
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getInputMethodSetting();
```

