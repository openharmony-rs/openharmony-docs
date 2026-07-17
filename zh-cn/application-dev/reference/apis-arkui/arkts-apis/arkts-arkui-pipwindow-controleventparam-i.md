# ControlEventParam

画中画控制面板控件动作回调的参数。

**起始版本：** 12

<!--Device-PiPWindow-interface ControlEventParam--><!--Device-PiPWindow-interface ControlEventParam-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## controlType

```TypeScript
controlType: PiPControlType
```

回调画中画控制面板控件动作事件类型。应用依据控件类型做相应处理，如视频模板中暂停/播放控件被点击时，需要开始或停止视频。

**类型：** PiPControlType

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ControlEventParam-controlType: PiPControlType--><!--Device-ControlEventParam-controlType: PiPControlType-End-->

**系统能力：** SystemCapability.Window.SessionManager

## status

```TypeScript
status?: PiPControlStatus
```

表示可切换状态的控件当前的状态，如具备打开和关闭两种状态的麦克风控件组、摄像头控件组和静音控件组，打开为PiPControlStatus.PLAY，关闭为PiPControlStatus.PAUSE。如不具备开/关和播放/暂停状态的挂断控件默认返回值为-1。

**类型：** PiPControlStatus

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ControlEventParam-status?: PiPControlStatus--><!--Device-ControlEventParam-status?: PiPControlStatus-End-->

**系统能力：** SystemCapability.Window.SessionManager

