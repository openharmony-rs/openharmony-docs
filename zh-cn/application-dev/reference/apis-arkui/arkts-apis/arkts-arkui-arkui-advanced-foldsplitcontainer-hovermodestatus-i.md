# HoverModeStatus

设备或应用的折叠、悬停、旋转、窗口状态信息。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export interface HoverModeStatus--><!--Device-unnamed-export interface HoverModeStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## appRotation

```TypeScript
appRotation: number
```

应用旋转角度，单位为度（degree）。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HoverModeStatus-appRotation: number--><!--Device-HoverModeStatus-appRotation: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## foldStatus

```TypeScript
foldStatus: display.FoldStatus
```

设备的折叠状态，包括展开、半折叠、完全折叠等状态。

**类型：** display.FoldStatus

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HoverModeStatus-foldStatus: display.FoldStatus--><!--Device-HoverModeStatus-foldStatus: display.FoldStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isHoverMode

```TypeScript
isHoverMode: boolean
```

应用当前是否处于悬停态。值为true时表示当前为悬停态，值为false时表示当前为非悬停态。

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HoverModeStatus-isHoverMode: boolean--><!--Device-HoverModeStatus-isHoverMode: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowStatusType

```TypeScript
windowStatusType: window.WindowStatusType
```

窗口模式，包括全屏、分屏、自由窗口等模式。

**类型：** window.WindowStatusType

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HoverModeStatus-windowStatusType: window.WindowStatusType--><!--Device-HoverModeStatus-windowStatusType: window.WindowStatusType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

