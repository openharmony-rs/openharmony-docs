# CursorController

提供光标样式设置的能力。

> **说明：**  
>  
> - 本Class首批接口从API version 12开始支持。  
>  
> - 以下API需先使用UIContext中的[getCursorController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcursorcontroller-1)方法获取CursorController实例，再通过此实例调用对应方法。

**起始版本：** 12

<!--Device-unnamed-export class CursorController--><!--Device-unnamed-export class CursorController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

<a id="restoredefault"></a>
## restoreDefault

```TypeScript
restoreDefault(): void
```

恢复默认的光标样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CursorController-restoreDefault(): void--><!--Device-CursorController-restoreDefault(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="setcursor"></a>
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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CursorController-setCursor(value: PointerStyle): void--><!--Device-CursorController-setCursor(value: PointerStyle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PointerStyle](arkts-arkui-pointerstyle-t.md) | 是 | 光标样式。 |

<a id="setcustomcursor"></a>
## setCustomCursor

```TypeScript
setCustomCursor(value: image.PixelMap, focusX?: number, focusY?: number): void
```

设置自定义鼠标光标样式。

> **说明：**  
>  
> 该接口调用后不会立即生效，而是在下一帧改变鼠标光标样式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CursorController-setCustomCursor(value: image.PixelMap, focusX?: int, focusY?: int): void--><!--Device-CursorController-setCustomCursor(value: image.PixelMap, focusX?: int, focusY?: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | image.PixelMap | 是 | 自定义鼠标光标样式的像素图。最大尺寸为256*256px，超过该尺寸时设置自定义鼠标光标样式不生效。 |
| focusX | number | 否 | 自定义光标的焦点X坐标。焦点指的是鼠标实际点击的位置，焦点设置为(0, 0)时表示图片左上角为实际点击位置。<br/>默认值：0<br/>单位：px<br/>取值范围：[0, +∞) |
| focusY | number | 否 | 自定义光标的焦点Y坐标。<br/>默认值：0<br/>单位：px<br/>取值范围：[0, +∞) |

