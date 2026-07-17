# OnHoverStatusChangeCallback

```TypeScript
declare type OnHoverStatusChangeCallback = (param: HoverEventParam) => void
```

当前设备的悬停状态改变时触发的回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnHoverStatusChangeCallback = (param: HoverEventParam) => void--><!--Device-unnamed-declare type OnHoverStatusChangeCallback = (param: HoverEventParam) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | HoverEventParam | 是 | 当前设备与悬停状态相关的参数，包括设备的折叠状态、悬停状态、应用方向以及窗口模式枚举。 |

