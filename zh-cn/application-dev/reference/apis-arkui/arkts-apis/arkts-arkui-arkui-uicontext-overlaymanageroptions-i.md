# OverlayManagerOptions

the property of OverlayManager.

**起始版本：** 15

<!--Device-unnamed-export interface OverlayManagerOptions--><!--Device-unnamed-export interface OverlayManagerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## enableBackPressedEvent

```TypeScript
enableBackPressedEvent?: boolean
```

Set whether support backPressed event or not.

**类型：** boolean

**默认值：** false

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManagerOptions-enableBackPressedEvent?: boolean--><!--Device-OverlayManagerOptions-enableBackPressedEvent?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## renderRootOverlay

```TypeScript
renderRootOverlay?: boolean
```

the render property of overlay node.

**类型：** boolean

**默认值：** true

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-OverlayManagerOptions-renderRootOverlay?: boolean--><!--Device-OverlayManagerOptions-renderRootOverlay?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

