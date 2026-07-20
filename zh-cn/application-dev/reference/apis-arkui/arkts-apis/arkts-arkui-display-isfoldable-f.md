# isFoldable

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="isfoldable"></a>
## isFoldable

```TypeScript
function isFoldable(): boolean
```

判断设备是否可折叠。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function isFoldable(): boolean--><!--Device-display-function isFoldable(): boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean对象，返回当前设备是否可折叠的结果。false表示不可折叠，true表示可折叠。对于外屏只有简单辅助显示作用的小折叠设备，应用无法自定义外屏界面，故其返回值为false。其他可折叠设备的返回值均为true。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
let ret: boolean = false;
ret = display.isFoldable();

```

