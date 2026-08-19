# HoverEventParam

当前设备与悬停状态相关的参数，包括设备的折叠状态、悬停状态、应用方向以及窗口模式枚举。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface HoverEventParam--><!--Device-unnamed-export declare interface HoverEventParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## appRotation

```TypeScript
appRotation: AppRotation
```

当前应用方向。

**类型：** [AppRotation](arkts-arkui-approtation-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HoverEventParam-appRotation: AppRotation--><!--Device-HoverEventParam-appRotation: AppRotation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## foldStatus

```TypeScript
foldStatus: FoldStatus
```

当前设备的折叠状态。

**类型：** [FoldStatus](arkts-arkui-foldstatus-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HoverEventParam-foldStatus: FoldStatus--><!--Device-HoverEventParam-foldStatus: FoldStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isHoverMode

```TypeScript
isHoverMode: boolean
```

当前是否为悬停态。 设置为true时表示当前为悬停态，设置为false时表示当前为非悬停态。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HoverEventParam-isHoverMode: boolean--><!--Device-HoverEventParam-isHoverMode: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowStatusType

```TypeScript
windowStatusType: WindowStatusType
```

窗口模式枚举。

**类型：** [WindowStatusType](arkts-arkui-windowstatustype-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HoverEventParam-windowStatusType: WindowStatusType--><!--Device-HoverEventParam-windowStatusType: WindowStatusType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

