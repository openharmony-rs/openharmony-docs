# DialogPresenter

提供统一的Dialog API。

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

关闭对话框。 接受对话ID（由当前返回）或ComponentContent引用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | number \| [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;Object&gt; | 是 | 要取消的对话ID或组件内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103301](../errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | Dialog content not found. The ComponentContent cannot be found. |

## present

```TypeScript
present(options?: dialog.DialogStyleOptions): Promise<DialogResult>
```

提供一个固定样式的对话框。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | dialog.DialogStyleOptions | 否 | 对话框选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DialogResult](arkts-arkui-arkui-dialog-dialogresult-i.md)&gt; | 用于返回对话结果的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103306](../errorcode-promptAction.md#103306-节点挂载失败导致无法打开弹出框) | The dialog cannot be opened due to node mount failure. |
| [103308](../errorcode-promptAction.md#103308-子窗口创建失败导致无法打开弹出框) | The dialog cannot be opened due to subwindow create failure. |

## present

```TypeScript
present(content: CustomBuilder | CustomBuilderWithId | ComponentContent<Object>, options?: dialog.DialogCustomOptions): Promise<DialogResult>
```

提供一个自定义样式的对话框，其中包含所提供的内容。content参数通过联合类型接受CustomBuilder或ComponentContent： -CustomBuilder：自定义对话框内容的生成器函数。  
- ComponentContent：支持状态驱动更新的ComponentContent。

> **说明：**
> isModal = true和showInSubWindow = true不能同时使用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| [CustomBuilderWithId](arkts-arkui-custombuilderwithid-t.md) \| [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;Object&gt; | 是 | 自定义对话框内容。 |
| options | dialog.DialogCustomOptions | 否 | 自定义对话框选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DialogResult](arkts-arkui-arkui-dialog-dialogresult-i.md)&gt; | 用于返回对话结果的Promise。 |

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

更新已呈现的自定义对话框。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;Object&gt; | 是 | 用于标识对话框的内容。 |
| options | dialog.DialogBaseOptions | 否 | 要更新的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103301](../errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | Dialog content not found. The ComponentContent cannot be found. |
