# getPrimaryDisplaySync

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="getprimarydisplaysync"></a>
## getPrimaryDisplaySync

```TypeScript
function getPrimaryDisplaySync(): Display
```

获取主屏信息。除2in1之外的设备获取的是设备自带屏幕的Display对象；2in1设备外接屏幕时获取的是当前主屏幕的Display对象；2in1设备没有外接屏幕时获取的是自带屏幕的Display对象。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-display-function getPrimaryDisplaySync(): Display--><!--Device-display-function getPrimaryDisplaySync(): Display-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Display](arkts-arkui-display-display-i.md) | 当前设备主屏幕的Display对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. Possible cause: Invalid display id. |

**示例：**

```TypeScript
let displayClass: display.Display | null = null;

displayClass = display.getPrimaryDisplaySync();

```

