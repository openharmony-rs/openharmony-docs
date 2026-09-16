# DialogPresenter

提供统一的Dialog API，可创建并显示固定样式弹出框、自定义样式弹出框，并支持更新与关闭弹出框。适用于应用中需要弹出提示、确认、选择等弹出框交互的场景。

> **说明：** 
> 
> 以下API需先使用UIContext中的[getDialogPresenter()](arkts-arkui-arkui-uicontext-uicontext-c.md#getdialogpresenter)方法获取到DialogPresenter对象，再通过该对象调用对应方法。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## dismiss

```TypeScript
dismiss(target: number | ComponentContent<Object>): Promise<void>
```

关闭弹出框，无返回结果。使用Promise异步回调。适用于在用户完成交互后关闭弹出框的场景。

接受弹出框ID（由[present](#present)返回的DialogResult中的dialogId）或ComponentContent引用作为target，关闭对应的弹出框。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | number &#124; [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;Object&gt; | 是 | 要关闭的弹出框ID或组件内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103301](../errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | Dialog content not found. The ComponentContent cannot be found. |

## present

```TypeScript
present(options?: dialog.DialogStyleOptions): Promise<DialogResult>
```

提供一个固定样式的弹出框，返回对话结果。使用Promise异步回调。适用于使用系统统一样式展示提示或确认信息的场景。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [dialog.DialogStyleOptions](arkts-arkui-dialog-dialogstyleoptions-i.md) | 否 | 固定样式弹出框的配置选项，用于配置弹出框的标题、副标题、消息、按钮及工作表项等内容。弹出框样式（背景、对齐、蒙层、避让等）继承自[dialog.DialogBaseOptions](arkts-arkui-dialog-dialogbaseoptions-i.md)。<br>**说明：** dialog.DialogBaseOptions中的isModal与showInSubWindow不能同时设置为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DialogResult](arkts-arkui-arkui-dialog-dialogresult-i.md)&gt; | Promise对象，返回对话结果，包含弹出框ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103306](../errorcode-promptAction.md#103306-节点挂载失败导致无法打开弹出框) | The dialog cannot be opened due to node mount failure. |
| [103308](../errorcode-promptAction.md#103308-子窗口创建失败导致无法打开弹出框) | The dialog cannot be opened due to subwindow create failure. |

## present

```TypeScript
present(content: CustomBuilder | CustomBuilderWithId | ComponentContent<Object>, options?: dialog.DialogCustomOptions): Promise<DialogResult>
```

提供一个自定义样式的弹出框，其中包含所提供的内容，返回对话结果，使用Promise异步回调。适用于需要自定义弹出框内容、布局和样式的场景。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) &#124; [CustomBuilderWithId](arkts-arkui-custombuilderwithid-t.md) &#124; [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;Object&gt; | 是 | 自定义弹出框内容，支持三种类型：CustomBuilder（自定义内容的生成器函数）、CustomBuilderWithId（支持传入ID的生成器函数）、ComponentContent（支持状态驱动更新的组件内容）。 |
| options | [dialog.DialogCustomOptions](arkts-arkui-dialog-dialogcustomoptions-i.md) | 否 | 自定义弹出框的配置选项，用于配置弹出框的背景、对齐、蒙层、避让等样式，继承自dialog.DialogBaseOptions。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DialogResult](arkts-arkui-arkui-dialog-dialogresult-i.md)&gt; | Promise对象，返回对话结果，包含弹出框ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103301](../errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | Dialog content error. The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-内容节点对应自定义弹窗已存在) | Dialog content already exist. The ComponentContent has already been opened. |
| [103306](../errorcode-promptAction.md#103306-节点挂载失败导致无法打开弹出框) | The dialog cannot be opened due to node mount failure. |
| [103308](../errorcode-promptAction.md#103308-子窗口创建失败导致无法打开弹出框) | The dialog cannot be opened due to subwindow create failure. |

## update

```TypeScript
update(content: ComponentContent<Object>, options?: dialog.DialogBaseOptions): Promise<void>
```

更新已弹出的自定义弹出框，无返回结果。使用Promise异步回调。适用于弹出框已弹出后需要动态更新其样式或位置的交互场景。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;Object&gt; | 是 | 用于标识弹出框的组件内容。 |
| options | [dialog.DialogBaseOptions](arkts-arkui-dialog-dialogbaseoptions-i.md) | 否 | 要更新的弹出框选项。目前仅支持更新alignment、offset、autoCancel、maskColor。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103301](../errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | Dialog content not found. The ComponentContent cannot be found. |
