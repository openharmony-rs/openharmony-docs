# createKeyboardDelegate

## createKeyboardDelegate

```TypeScript
function createKeyboardDelegate(): KeyboardDelegate
```

获取客户端编辑事件监听代理实例[KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md#KeyboardDelegate)。输入法应用获取该实例后，可订阅物理键盘按键事件、选中文本变化事件等。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [getKeyboardDelegate](arkts-ime-inputmethodengine-getkeyboarddelegate-f.md#getKeyboardDelegate)()

<!--Device-inputMethodEngine-function createKeyboardDelegate(): KeyboardDelegate--><!--Device-inputMethodEngine-function createKeyboardDelegate(): KeyboardDelegate-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md) | 客户端编辑事件监听代理。 |

## 示例

```TypeScript
let keyboardDelegate: inputMethodEngine.KeyboardDelegate = inputMethodEngine.createKeyboardDelegate();
```

