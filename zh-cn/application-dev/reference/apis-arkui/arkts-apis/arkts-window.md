# @ohos.window

提供管理窗口的一些基础能力，包括对当前窗口的创建、销毁、各属性设置，以及对各窗口间的管理调度。
 该模块提供以下窗口相关的常用功能：
 - [Window](arkts-arkui-window-n.md)：当前窗口实例，窗口管理器管理的基本单元。
 - [WindowStage](arkts-arkui-window-n.md)：窗口管理器。管理各个基本窗口单元。
 > **说明：**
 >
 > - 针对系统能力SystemCapability.Window.SessionManager，请先使用
 > [canIUse()](../../../reference/common/js-apis-syscap.md#caniuse)接口判断当前设备是否支持此syscap及对应接口。


## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [window](arkts-arkui-window-n.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Callback](arkts-arkui-window-callback-i.md) | Defines the window callback. |

### 类型

| 名称 | 说明 |
| --- | --- |
| [WindowAnimationCurveParam](arkts-arkui-windowanimationcurveparam-t.md) | 动画曲线参数。 |
| [WindowEventListener](arkts-arkui-windoweventlistener-t.md) | 窗口生命周期事件通知的回调函数。 |
