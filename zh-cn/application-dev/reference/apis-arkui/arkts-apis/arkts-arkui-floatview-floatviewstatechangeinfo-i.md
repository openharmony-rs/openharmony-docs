# FloatViewStateChangeInfo

标准悬浮窗状态变化信息。

**起始版本：** 26.0.0

<!--Device-floatView-interface FloatViewStateChangeInfo--><!--Device-floatView-interface FloatViewStateChangeInfo-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## state

```TypeScript
state: FloatViewState
```

标准悬浮窗的状态。

**类型：** FloatViewState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewStateChangeInfo-state: FloatViewState--><!--Device-FloatViewStateChangeInfo-state: FloatViewState-End-->

**系统能力：** SystemCapability.Window.SessionManager

## stopReason

```TypeScript
stopReason: string
```

标准悬浮窗停止的原因。该参数仅在状态为FloatViewState.STOPPED时有效，在其他状态下默认为空字符串。停止原因和对应含义如下：

"APP_STOP"：应用主动停止

"STOP_IN_SIDEBAR"：在侧边栏被关闭

"TITLE_BAR_STOP_CLICK"：标题栏点击关闭按钮

"DUMPSTER_STOP"：拖入垃圾桶停止

"REPLACE_STOP"：被其他标准悬浮窗挤占

"FLOATING_BALL_STOP"：绑定状态下跟随闪控球停止

"MAIN_WINDOW_DESTROY_STOP"：context关联的主窗被销毁后停止

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewStateChangeInfo-stopReason: string--><!--Device-FloatViewStateChangeInfo-stopReason: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

