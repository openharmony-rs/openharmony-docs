# DialogPresenter

```TypeScript
export class DialogPresenter
```

Provides unified dialog APIs. It provides APIs for creating and displaying fixed-style and custom-style dialog boxes, updating and closing dialog boxes. It applies to scenarios where pop-up interactions such as prompts, confirmations, and selections are required within an application.

**Since:** 26.0.1

<!--Device-unnamed-export class DialogPresenter--><!--Device-unnamed-export class DialogPresenter-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler, GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback, SwiperContentInfo, SwiperItemInfo, BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## dismiss

```TypeScript
dismiss(target: number | ComponentContent<Object>): Promise<void>
```

Dismisses a dialog box. Accepts either the dialog ID (returned by present) or the ComponentContent reference. This API uses a promise to return the result. It is applicable to scenarios where the dialog box needs to be closed after a user completes the interaction.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogPresenter-dismiss(target: int | ComponentContent<Object>): Promise<void>--><!--Device-DialogPresenter-dismiss(target: int | ComponentContent<Object>): Promise<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | number &#124; [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;Object&gt; | Yes | The dialog ID or ComponentContent to dismiss. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | Dialog content not found. The ComponentContent cannot be found. |

## present

```TypeScript
present(options?: dialog.DialogStyleOptions): Promise<DialogResult>
```

Presents a fixed-style dialog box and returns the dialog result. This API uses a promise to return the result. It is applicable to scenarios where the system's unified style is used to display prompts or confirmation information.

> **NOTE:** 
> 
> Configuration options are used to configure the title, subtitle, message, buttons, and sheet items of the
> dialog box. The dialog box style (background, alignment, mask, avoidance, etc.) inherits from
> **dialog.DialogBaseOptions**. In **dialog.DialogBaseOptions**, **isModal** and **showInSubWindow** cannot be set
> to **true** at the same time.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogPresenter-present(options?: dialog.DialogStyleOptions): Promise<DialogResult>--><!--Device-DialogPresenter-present(options?: dialog.DialogStyleOptions): Promise<DialogResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [dialog.DialogStyleOptions](arkts-arkui-dialog-dialogstyleoptions-i.md) | No | Dialog options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DialogResult](arkts-arkui-arkui-dialog-dialogresult-i.md)&gt; | Promise used to return the dialog result. The dialog ID is returned via **dialogId** in **DialogResult**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [103306](../errorcode-promptAction.md#103306-node-mount-failure-causes-dialog-box-to-fail-to-open) | The dialog cannot be opened due to node mount failure. |
| [103308](../errorcode-promptAction.md#103308-dialog-box-cannot-be-opened-due-to-subwindow-creation-failure) | The dialog cannot be opened due to subwindow create failure. |

## present

```TypeScript
present(content: CustomBuilder | CustomBuilderWithId | ComponentContent<Object>, options?: dialog.DialogCustomOptions): Promise<DialogResult>
```

Presents a custom-style dialog box with the provided content.

It returns the dialog result via a promise. It is applicable to scenarios where the content, layout, and style of the dialog box need to be customized.

The content parameter accepts three types via union type:  
- CustomBuilder: Builder function for custom dialog content.  
- CustomBuilderWithId: Builder function that supports passing an ID.  
- ComponentContent: Component content supporting state-driven updates.

isModal = true and showInSubWindow = true cannot be used at the same time.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogPresenter-present(content: CustomBuilder | CustomBuilderWithId | ComponentContent<Object>, options?: dialog.DialogCustomOptions): Promise<DialogResult>--><!--Device-DialogPresenter-present(content: CustomBuilder | CustomBuilderWithId | ComponentContent<Object>, options?: dialog.DialogCustomOptions): Promise<DialogResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md) &#124; [CustomBuilderWithId](arkts-arkui-custombuilderwithid-t.md) &#124; [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;Object&gt; | Yes | Custom dialog content. |
| options | [dialog.DialogCustomOptions](arkts-arkui-dialog-dialogcustomoptions-i.md) | No | Custom dialog options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DialogResult](arkts-arkui-arkui-dialog-dialogresult-i.md)&gt; | Promise used to return the dialog result. The dialog ID is returned via **dialogId** in **DialogResult**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-custom-dialog-box-already-exists) | Dialog content already exist. The ComponentContent has already been opened. |
| [103306](../errorcode-promptAction.md#103306-node-mount-failure-causes-dialog-box-to-fail-to-open) | The dialog cannot be opened due to node mount failure. |
| [103308](../errorcode-promptAction.md#103308-dialog-box-cannot-be-opened-due-to-subwindow-creation-failure) | The dialog cannot be opened due to subwindow create failure. |

## update

```TypeScript
update(content: ComponentContent<Object>, options?: dialog.DialogBaseOptions): Promise<void>
```

Updates a displayed custom dialog box. This API uses a promise to return the result. It applies to interaction scenarios where the style or position of a dialog box needs to be dynamically updated after it is displayed.

> **NOTE:** 
> 
> Currently, only **alignment**, **offset**, **autoCancel**, and **maskColor** can be updated.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogPresenter-update(content: ComponentContent<Object>, options?: dialog.DialogBaseOptions): Promise<void>--><!--Device-DialogPresenter-update(content: ComponentContent<Object>, options?: dialog.DialogBaseOptions): Promise<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;Object&gt; | Yes | The content used to identify the dialog. |
| options | [dialog.DialogBaseOptions](arkts-arkui-dialog-dialogbaseoptions-i.md) | No | Options to update. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | Dialog content not found. The ComponentContent cannot be found. |
