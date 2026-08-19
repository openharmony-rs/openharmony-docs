# isFloatingBallEnabled

## 导入模块

```TypeScript
import { floatingBall } from '@kit.ArkUI';
```

## isFloatingBallEnabled

```TypeScript
function isFloatingBallEnabled(): boolean
```

判断当前设备是否支持闪控球功能。

**起始版本：** 23

<!--Device-floatingBall-function isFloatingBallEnabled(): boolean--><!--Device-floatingBall-function isFloatingBallEnabled(): boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备是否支持闪控球功能。true表示支持，false则表示不支持。 |

**示例**

```TypeScript
// xxx.ets

let enable: boolean = floatingBall.isFloatingBallEnabled();
console.info('Floating ball enabled is: ' + enable);
```

