# ControlPanelActionEventCallback

```TypeScript
type ControlPanelActionEventCallback = (event: PiPActionEventType, status?: number) => void
```

描述画中画控制面板控件动作事件回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | PiPActionEventType | 是 | 回调画中画控制面板控件动作事件类型。<br/>应用依据控件动作事件做相应处理，如触发'playbackStateChanged'事件时，需要开始或停止视频。 |
| status | int | 否 | 表示可切换状态的控件当前的状态，如具备打开和关闭两种状态的麦克风控件组、摄像头控件组和静音控件组，打开为1，关闭为0。其余控件该参数返回默认值-1。取值限定为整数 |

