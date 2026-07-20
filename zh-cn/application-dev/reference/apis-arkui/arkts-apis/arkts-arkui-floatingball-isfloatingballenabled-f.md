# isFloatingBallEnabled

## 导入模块

```TypeScript
import { floatingBall } from '@kit.ArkUI';
```

<a id="isfloatingballenabled"></a>
## isFloatingBallEnabled

```TypeScript
function isFloatingBallEnabled(): boolean
```

判断当前设备是否支持闪控球功能。

**起始版本：** 20

<!--Device-floatingBall-function isFloatingBallEnabled(): boolean--><!--Device-floatingBall-function isFloatingBallEnabled(): boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备是否支持闪控球功能。true表示支持，false则表示不支持。 |

**示例：**

```TypeScript
// 判断当前设备是否支持闪控球功能
let enable: boolean = floatingBall.isFloatingBallEnabled();
console.info('Floating ball enabled is: ' + enable);

```

