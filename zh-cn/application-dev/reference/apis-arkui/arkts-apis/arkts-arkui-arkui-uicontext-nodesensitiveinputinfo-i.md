# NodeSensitiveInputInfo

```TypeScript
export interface NodeSensitiveInputInfo
```

定义输入事件分发到**nodeIdentity**指定节点时上报的信息。

**起始版本：** 26.1.0

<!--Device-unnamed-export interface NodeSensitiveInputInfo--><!--Device-unnamed-export interface NodeSensitiveInputInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## isAgent

```TypeScript
isAgent: boolean
```

事件是否为Agent生成的事件。**true**表示该事件由系统Agent生成，或由具有ohos.permission.CONTROL_COMPONENT权限的应用注入；**false**表示用户生成的输入事件或其他注入事件。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-NodeSensitiveInputInfo-isAgent: boolean--><!--Device-NodeSensitiveInputInfo-isAgent: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyEvent

```TypeScript
keyEvent?: KeyEvent
```

按键事件，仅当**type**为[NodeSensitiveInputEventType.KEY](arkts-arkui-arkui-uicontext-nodesensitiveinputeventtype-e.md#key)时有效。

**类型：** [KeyEvent](../arkts-components/arkts-arkui-common-comp-keyevent-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-NodeSensitiveInputInfo-keyEvent?: KeyEvent--><!--Device-NodeSensitiveInputInfo-keyEvent?: KeyEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mouseEvent

```TypeScript
mouseEvent?: MouseEvent
```

鼠标事件，仅当**type**为[NodeSensitiveInputEventType.MOUSE](arkts-arkui-arkui-uicontext-nodesensitiveinputeventtype-e.md#mouse)时有效。

**类型：** [MouseEvent](../arkts-components/arkts-arkui-common-comp-mouseevent-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-NodeSensitiveInputInfo-mouseEvent?: MouseEvent--><!--Device-NodeSensitiveInputInfo-mouseEvent?: MouseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## touchEvent

```TypeScript
touchEvent?: TouchEvent
```

触摸事件，仅当**type**为[NodeSensitiveInputEventType.TOUCH](arkts-arkui-arkui-uicontext-nodesensitiveinputeventtype-e.md#touch)时有效。

**类型：** [TouchEvent](../arkts-components/arkts-arkui-common-comp-touchevent-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-NodeSensitiveInputInfo-touchEvent?: TouchEvent--><!--Device-NodeSensitiveInputInfo-touchEvent?: TouchEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: NodeSensitiveInputEventType
```

上报的输入事件类型。

**类型：** [NodeSensitiveInputEventType](arkts-arkui-arkui-uicontext-nodesensitiveinputeventtype-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-NodeSensitiveInputInfo-type: NodeSensitiveInputEventType--><!--Device-NodeSensitiveInputInfo-type: NodeSensitiveInputEventType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
