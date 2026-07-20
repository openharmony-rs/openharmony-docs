# getCurrentInputMethod

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

<a id="getcurrentinputmethod"></a>
## getCurrentInputMethod

```TypeScript
function getCurrentInputMethod(): InputMethodProperty
```

使用同步方法获取当前输入法。

**含义/功能**：获取当前正在使用的输入法属性信息。

**使用场景：**当应用需要知道当前活跃的输入法是哪个（如判断输入法名称、获取输入法id用于后续切换操作）时使用。

**使用后效果**：返回当前输入法的InputMethodProperty对象。

**起始版本：** 9

<!--Device-inputMethod-function getCurrentInputMethod(): InputMethodProperty--><!--Device-inputMethod-function getCurrentInputMethod(): InputMethodProperty-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 返回当前输入法属性对象。 |

**示例：**

```TypeScript
let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();

```

