# DockCornerMode

```TypeScript
export enum DockCornerMode
```

定义浮动工具栏拖拽到角落时的吸附模式。

**Since:** 26.1.0

<!--Device-unnamed-export enum DockCornerMode--><!--Device-unnamed-export enum DockCornerMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EXPAND

```TypeScript
EXPAND = 1
```

保持拖拽方向，不进行最小化。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-DockCornerMode-EXPAND = 1--><!--Device-DockCornerMode-EXPAND = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MINIMIZE

```TypeScript
MINIMIZE = 0
```

吸附到角落并最小化；点击角落后跟随所在边缘。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-DockCornerMode-MINIMIZE = 0--><!--Device-DockCornerMode-MINIMIZE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
