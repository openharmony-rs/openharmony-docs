# CursorController

提供鼠标光标样式设置的能力，支持恢复默认鼠标光标样式、设置系统鼠标光标样式以及设置自定义鼠标光标样式，适用于需要根据界面交互状态动态调整鼠标光标显示效果的场景，有助于提升界面交互提示的清晰度。

> **说明：** 
> 
> - 本Class首批接口从API version 12开始支持。
> 
> - 以下API需先使用UIContext中的[getCursorController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcursorcontroller)方法获取CursorController实例，再通过此实例调用对应方法。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## restoreDefault

```TypeScript
restoreDefault(): void
```

恢复默认的光标样式。

> **说明：** 
> 
> 该接口调用后不会立即生效，而是在下一帧改变鼠标光标样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setCursor

```TypeScript
setCursor(value: PointerStyle): void
```

更改当前的鼠标光标样式。

> **说明：** 
> 
> 该接口调用后不会立即生效，而是在下一帧改变鼠标光标样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PointerStyle](arkts-arkui-pointerstyle-t.md) | 是 | 光标样式。 |

## setCustomCursor

```TypeScript
setCustomCursor(value: image.PixelMap, focusX?: number, focusY?: number): void
```

设置自定义鼠标光标样式。

> **说明：** 
> 
> - 该接口调用后不会立即生效，而是在下一帧改变鼠标光标样式。
> - 仅支持设置静态图片，不支持设置动态图片。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | 是 | 自定义鼠标光标样式的像素图。最大尺寸为256*256px，超过该尺寸时设置自定义鼠标光标样式不生效。 |
| focusX | number | 否 | 自定义光标焦点的X坐标。以光标图片左上角为原点，向右为正方向。该焦点将在显示时与系统鼠标指针的屏幕坐标对齐，鼠标的点击、拖拽等操作均以此点为准。<br>默认值：0<br>单位：px<br>取值范围：[0, 图片宽度]，超出取值范围时按默认值处理。 |
| focusY | number | 否 | 自定义光标焦点的Y坐标。以光标图片左上角为原点，向下为正方向。结合focusX共同确定图像内代表实际交互位置的点。<br>默认值：0<br>单位：px<br>取值范围：[0, 图片高度]，超出取值范围时按默认值处理。 |
