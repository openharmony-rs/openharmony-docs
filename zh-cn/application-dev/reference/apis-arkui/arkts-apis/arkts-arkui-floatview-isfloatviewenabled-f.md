# isFloatViewEnabled

## 导入模块

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## isFloatViewEnabled

```TypeScript
function isFloatViewEnabled(): boolean
```

判断当前设备是否支持标准悬浮窗功能。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-floatView-function isFloatViewEnabled(): boolean--><!--Device-floatView-function isFloatViewEnabled(): boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备是否支持标准悬浮窗功能。true表示支持，false则表示不支持。 |

**示例：**

```TypeScript
// 判断当前设备是否支持闪控窗功能
let enable: boolean = floatView.isFloatViewEnabled();
console.info('Float view enabled is: ' + enable);

```

