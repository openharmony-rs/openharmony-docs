# ControlPanelActionEventCallback

```TypeScript
type ControlPanelActionEventCallback = (event: PiPActionEventType, status?: int) => void
```

描述画中画控制面板控件动作事件回调。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为26.0.0。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PiPWindow-type ControlPanelActionEventCallback = (event: PiPActionEventType, status?: int) => void--><!--Device-PiPWindow-type ControlPanelActionEventCallback = (event: PiPActionEventType, status?: int) => void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调画中画控制面板控件动作事件类型。\_\_\_HTML\_TAG\_USD\_0\_\_\_应用依据控件动作事件做相应处理，如触发'playbackStateChanged'事件时，需要开始或停止视频 。  |
| status | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 否 | 表示可切换状态的控件当前的状态，如具备打开和关闭两种状态的麦克风控件组、摄像头控件组和静音控件组，打开为1，关闭为0。其余控件该参数返回默认值-1。 取值限定为整数  |

