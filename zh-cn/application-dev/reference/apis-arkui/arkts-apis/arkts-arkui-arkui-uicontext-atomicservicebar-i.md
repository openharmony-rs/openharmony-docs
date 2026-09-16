# AtomicServiceBar

interface AtomicServiceBar

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## getBarRect

```TypeScript
getBarRect(): Frame
```

获取原子化服务menuBar相对窗口的布局信息。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Frame](arkts-arkui-graphics-frame-i.md) | 原子化服务menuBar的大小和位置。 |

## onBarRectChange

```TypeScript
onBarRectChange(callback: Callback<Frame>): void
```

当原子化服务menuBar（即AtomicServiceMenuBar，右上角菜单功能胶囊）的大小或位置发生变化时，触发注册的回调，返回menuBar最新的布局信息。该布局信息包含了menuBar的大小和位置，其中位置已考虑左右margin的影响。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Frame](arkts-arkui-graphics-frame-i.md)&gt; | 是 | AtomicServiceMenuBar布局变化时的回调，返回变化后的布局信息。 |

## setBackgroundColor

```TypeScript
setBackgroundColor(color: Nullable< Color | number | string>): void
```

通过该方法设置原子化服务menuBar的背景颜色。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Nullable](arkts-arkui-nullable-t.md)&lt;[Color](arkts-arkui-color-e.md) &#124; number &#124; string&gt; | 是 | 原子化服务menuBar的背景颜色，undefined代表使用默认颜色。number为HEX格式颜色，支持rgb或者argb，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。从API version 12开始，在原子化服务中该参数将被忽略。 |

## setIconColor

```TypeScript
setIconColor(color: Nullable< Color | number | string>): void
```

通过该方法设置原子化服务menuBar图标的颜色。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Nullable](arkts-arkui-nullable-t.md)&lt;[Color](arkts-arkui-color-e.md) &#124; number &#124; string&gt; | 是 | 原子化服务menuBar图标的颜色，undefined代表使用默认颜色。number为HEX格式颜色，支持rgb或者argb，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。从API version 12开始，在原子化服务中该参数将被忽略。 |

## setTitleContent

```TypeScript
setTitleContent(content: string): void
```

通过该方法设置原子化服务menuBar的标题内容。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string | 是 | 原子化服务menuBar中的标题内容。从API version 12开始，在原子化服务中该参数将被忽略。 |

## setTitleFontStyle

```TypeScript
setTitleFontStyle(font: FontStyle): void
```

通过该方法设置原子化服务menuBar标题的字体样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | [FontStyle](arkts-arkui-fontstyle-e.md) | 是 | 原子化服务menuBar标题中的字体样式。从API version 12开始，在原子化服务中该参数将被忽略。 |

## setVisible

```TypeScript
setVisible(visible: boolean): void
```

通过该方法设置原子化服务menuBar是否可见。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| visible | boolean | 是 | 原子化服务menuBar是否可见。true表示设置menuBar可见，false表示设置menuBar不可见。从API version 12开始，在原子化服务中该参数将被忽略。 |
