# getKeyboardDelegate

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## getKeyboardDelegate

```TypeScript
function getKeyboardDelegate(): KeyboardDelegate
```

获取客户端编辑事件监听代理实例[KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md)（键盘代理对象）。 输入法应用获取该实例后，可订阅物理键盘按键事件、选中文本变化事件等。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md) | 客户端编辑事件监听代理。 |

**示例**

```TypeScript
// 获取客户端编辑事件监听代理实例
let keyboardDelegate: inputMethodEngine.KeyboardDelegate = inputMethodEngine.getKeyboardDelegate();
```
