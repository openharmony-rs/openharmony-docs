# getDefaultDisplaySync

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="getdefaultdisplaysync"></a>
## getDefaultDisplaySync

```TypeScript
function getDefaultDisplaySync(): Display
```

返回应用所在屏幕的Display对象。若应用内多个Ability在不同屏幕，返回主屏的Display对象，若应用内多个Ability在同一屏幕，返回所在屏幕的Display对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-display-function getDefaultDisplaySync(): Display--><!--Device-display-function getDefaultDisplaySync(): Display-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Display](arkts-arkui-display-display-i.md) | 返回默认的Display对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. Possible cause: Display is not created or destroyed. |

**示例：**

```TypeScript
let displayClass: display.Display | null = null;
try {
  displayClass = display.getDefaultDisplaySync();
} catch (exception) {
  console.error(`Failed to get default display. Code: ${exception.code}, message: ${exception.message}`);
}

```

