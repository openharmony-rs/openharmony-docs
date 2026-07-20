# GestureHandlingResolution

智慧手势处理结果声明类。

**起始版本：** 26.0.0

<!--Device-unnamed-export class GestureHandlingResolution--><!--Device-unnamed-export class GestureHandlingResolution-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(isConsumed: boolean)
```

智慧手势处理结果的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GestureHandlingResolution-constructor(isConsumed: boolean)--><!--Device-GestureHandlingResolution-constructor(isConsumed: boolean)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isConsumed | boolean | 是 | 是否消费当前智慧手势。<br/>true表示消费当前智慧手势，此时如果未设置[selectedProposal](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md#selectedproposal)沿用系统默认动作处理，设置了selectedProposal以自定义动作处理。<br/>false表示不消费，系统将本次智慧手势视为未处理。 |

## isConsumed

```TypeScript
isConsumed: boolean
```

是否消费当前智慧手势。

true表示消费当前智慧手势，此时如果未设置selectedProposal沿用系统默认动作处理，设置了selectedProposal以自定义动作处理。

false表示不消费，系统将本次智慧手势视为未处理。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GestureHandlingResolution-isConsumed: boolean--><!--Device-GestureHandlingResolution-isConsumed: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedProposal

```TypeScript
selectedProposal?: BaseGestureHandlingProposal
```

用户指定的智慧手势处理行为。

当isConsumed为true时，如果未设置selectedProposal沿用系统默认动作处理，设置了selectedProposal以自定义动作处理。

当isConsumed为false时，selectedProposal设置不生效。

**类型：** BaseGestureHandlingProposal

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GestureHandlingResolution-selectedProposal?: BaseGestureHandlingProposal--><!--Device-GestureHandlingResolution-selectedProposal?: BaseGestureHandlingProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

