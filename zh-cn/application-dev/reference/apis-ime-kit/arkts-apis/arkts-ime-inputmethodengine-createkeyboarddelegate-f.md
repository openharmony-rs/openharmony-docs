# createKeyboardDelegate

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## createKeyboardDelegate

```TypeScript
function createKeyboardDelegate(): KeyboardDelegate
```

获取客户端编辑事件监听代理实例[KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md)。输入法应用获取该实例后，可订阅物理键盘按键事件、选中文本变化事件等。   
> **说明：**
   
> 
   
> 从 API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getKeyboardDelegate](arkts-ime-inputmethodengine-getkeyboarddelegate-f.md)()

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md) | 客户端编辑事件监听代理。 |

**示例**

```TypeScript
let keyboardDelegate: inputMethodEngine.KeyboardDelegate = inputMethodEngine.createKeyboardDelegate();
```
