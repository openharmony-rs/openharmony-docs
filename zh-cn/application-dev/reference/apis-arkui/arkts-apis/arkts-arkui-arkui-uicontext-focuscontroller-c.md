# FocusController

提供控制焦点的能力，如清除、移动和激活焦点等功能。

> **说明：**  
>  
> 以下API需先使用UIContext中的[getFocusController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getfocuscontroller-1)方法获取FocusController实例，再通过该实例调用对应方法。

**起始版本：** 12

<!--Device-unnamed-export class FocusController--><!--Device-unnamed-export class FocusController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

<a id="activate"></a>
## activate

```TypeScript
activate(isActive: boolean, autoInactive?: boolean): void
```

设置当前界面的[焦点激活态](docroot://ui/arkts-common-events-focus-event.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-activate(isActive: boolean, autoInactive?: boolean): void--><!--Device-FocusController-activate(isActive: boolean, autoInactive?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isActive | boolean | 是 | 设置是否进入/退出焦点激活态。<br/>true表示设置进入焦点激活态，false表示设置退出焦点激活态。 |
| autoInactive | boolean | 否 | 设置焦点激活态退出逻辑。<br/>为true时，会自动在触摸事件、鼠标事件触发时退出，为false时，仅受开发者API控制。<br/>默认值：true |

<a id="clearfocus"></a>
## clearFocus

```TypeScript
clearFocus(): void
```

清除焦点，将焦点强制转移到页面根容器节点，焦点链路上其他节点失焦。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-clearFocus(): void--><!--Device-FocusController-clearFocus(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="isactive"></a>
## isActive

```TypeScript
isActive(): boolean
```

返回UI实例的焦点激活态。

焦点激活态可参考[基础概念：焦点激活态](docroot://ui/arkts-common-events-focus-event.md#基础概念)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-isActive(): boolean--><!--Device-FocusController-isActive(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回UI实例的焦点激活态。true表示当前进入焦点激活态，false表示当前已退出焦点激活态。 |

<a id="requestfocus"></a>
## requestFocus

```TypeScript
requestFocus(key: string): void
```

通过组件的id将焦点转移到组件树对应的实体节点，当前帧生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-requestFocus(key: string): void--><!--Device-FocusController-requestFocus(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 节点对应的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [150001](../errorcode-focus.md#150001-节点无法获得焦点) | the component cannot be focused. |
| [150002](../errorcode-focus.md#150002-祖先节点无法获得焦点) | This component has an unfocusable ancestor. |
| [150003](../errorcode-focus.md#150003-节点不存在) | the component is not on tree or does not exist. |

<a id="setautofocustransfer"></a>
## setAutoFocusTransfer

```TypeScript
setAutoFocusTransfer(isAutoFocusTransfer: boolean): void
```

设置页面切换时，新的页面是否需要主动获取焦点。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-setAutoFocusTransfer(isAutoFocusTransfer: boolean): void--><!--Device-FocusController-setAutoFocusTransfer(isAutoFocusTransfer: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAutoFocusTransfer | boolean | 是 | 设置页面切换时，新的页面是否需要主动获取焦点，例如[Router](arkts-router.md)、[Navigation](../arkts-components/arkts-arkui-navigation.md)、[Menu](../arkts-components/arkts-arkui-menu.md)、[Dialog](@ohos.arkui.advanced.Dialog)、[Popup](arkts-arkui-advanced-popup.md)等。true表示需要主动获取焦点，false表示不需要主动获取焦点。默认值为true。 |

<a id="setkeyprocessingmode"></a>
## setKeyProcessingMode

```TypeScript
setKeyProcessingMode(mode: KeyProcessingMode): void
```

设置按键事件处理的优先级。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-setKeyProcessingMode(mode: KeyProcessingMode): void--><!--Device-FocusController-setKeyProcessingMode(mode: KeyProcessingMode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [KeyProcessingMode](arkts-arkui-keyprocessingmode-e.md) | 是 | 按键处理模式。 |

