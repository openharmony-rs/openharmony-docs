# UIContext

Implements a **UIContext** instance.

> **NOTE:** 
> 
> - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.
> 
> - The following APIs must be called through a corresponding UIContext instance. There are three ways to obtain a
> **UIContext** instance: (1) using the
> [getUIContext()](../../../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10) method from
> ohos.window; (2) using the built-in method
> [getUIContext()](../../../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext) of a custom
> component; (3) using static methods of the UIContext class such as
> [getCallingScopeUIContext](#getcallingscopeuicontext). In this document, the **UIContext** instance
> is represented by **uiContext**.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## addLocalInputEventMonitor

```TypeScript
addLocalInputEventMonitor(eventMask: number, listener: InputEventListener): InputEventMonitor
```

Registers a local input event monitor.

The "Local" in the interface name indicates that the monitor is only valid within the current UIContext, and does not affect other UIContext instances. Each UIContext maintains its own independent list of monitors.

Performance Warning: Do not perform time-consuming operations in the callback!

Monitor Object Notes:

- The returned Monitor object is a unique identifier created by the system.  
- Developers cannot actively construct or forge this object.  
- Must save the returned monitor object reference for subsequent cancellation.  
- It is recommended to use a variable to save it to avoid losing the reference.

Usage Examples:

```typescript
// Monitor a single event type
const monitor1 = uiContext.addLocalInputEventMonitor(
InputEventSubTypeMask.LEFT_MOUSE_DOWN,
(wrapper: RawInputEventWrapper) =&gt; {
if (wrapper.isMouseEvent()) {
const mouseEvent = wrapper.asMouseEvent();
console.log(`Mouse: (&#36;{mouseEvent.windowX}, &#36;{mouseEvent.windowY})`);
return { action: InputEventInterceptAction.CONTINUE }; // Allow event to continue
}
return { action: InputEventInterceptAction.BLOCK }; // Block event
}
);
// Monitor multiple event types (using bitwise operations)
const monitor2 = uiContext.addLocalInputEventMonitor(
InputEventSubTypeMask.LEFT_MOUSE_DOWN | InputEventSubTypeMask.RIGHT_MOUSE_DOWN,
(wrapper: RawInputEventWrapper) =&gt; {
if (wrapper.isMouseEvent()) {
const mouseEvent = wrapper.asMouseEvent()!;
console.log(`Mouse button: &#36;{mouseEvent.button}`);
return { action: InputEventInterceptAction.BLOCK };
}
return { action: InputEventInterceptAction.CONTINUE };
}
);
// When unregistering the monitor, use the returned Monitor object
uiContext.removeLocalInputEventMonitor(monitor1);
uiContext.removeLocalInputEventMonitor(monitor2);
```

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventMask | number | Yes | Event type mask, specifying the types of events to monitor through bitwise operations. |
| listener | [InputEventListener](../arkts-components/arkts-arkui-inputeventlistener-t.md) | Yes | Event listener callback function. |

**Return value:**

| Type | Description |
| --- | --- |
| [InputEventMonitor](../arkts-components/arkts-arkui-inputeventmonitor-i.md) | Unique identifier object for the monitor, used for subsequent cancellation of registration. |

## animateTo

```TypeScript
animateTo(value: AnimateParam, event: () => void): void
```

Adds transition animations for state changes in closure code.

> **NOTE:** 
> 
> - Avoid using **animateTo** in **aboutToAppear** or **aboutToDisappear**.
> 
> - When **animateTo** is called in [aboutToAppear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear), the component's build method is not executed yet, and internal components are not created. This means the animation has no initial values to work with and will not function as expected.
> 
> - During execution of [aboutToDisappear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttodisappear),the component is being destroyed, so animations should not be used.
> 
> - When a component appears or disappears, animation effects can be added through [component transition](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md).
> 
> - For properties that component transitions do not support, refer to [Example 2: Enabling Component Disappearance After Animation Completion](../../../reference/apis-arkui/arkui-ts/ts-explicit-animation.md#example-2-enabling-component-disappearance-after-animation-completion),which uses **animateTo** to achieve the effect of the component disappearing after the animation finishes.
> 
> - In certain scenarios, using animateTo with [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2) may produce unexpected results. For details, see [Using animateTo Failed in State Management V2](../../../ui/state-management/arkts-new-local.md#using-animateto-failed-in-state-management-v2).
> 
> 
> - When a UIAbility switches from the foreground to the background, any limited iteration animations that are currently running will end immediately, thereby triggering the [onFinish animation completion callback](../arkts-components/arkts-arkui-animateparam-i.md).
> 
> - If transition animations are turned off in Developer options, animations end on the current frame, and the
> **onFinish** callback is executed immediately. Avoid placing timing-dependent functional logic inside this
> callback.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AnimateParam](../arkts-components/arkts-arkui-animateparam-i.md) | Yes | Animation settings. |
| event | () =&gt; void | Yes | Closure function that displays the animation. The system automatically inserts the transition animation if the state changes in the closure function. |

## animateToImmediately

```TypeScript
animateToImmediately(param: AnimateParam, processor: Callback<void>): void
```

Specifies a clear animation host instance context via the UIContext object and triggers the explicit animation to be dispatched immediately. This avoids issues where animations are not executed or animation end callbacks are not triggered due to inability to locate the instance or using an incorrect instance. This API uses an asynchronous callback to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [AnimateParam](../arkts-components/arkts-arkui-animateparam-i.md) | Yes | Animation settings. |
| processor | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback function. It specifies the closure function that displays the animation. The system automatically inserts the transition animation if the state changes in the closure function. |

## bindTabsToNestedScrollable

```TypeScript
bindTabsToNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void
```

Bind tabs to nested scrollable container components to automatically hide tab bar.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md) | Yes | The controller of the tabs. |
| parentScroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | Yes | The controller of the parent scrollable container component. |
| childScroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | Yes | The controller of the child scrollable container component. |

## bindTabsToScrollable

```TypeScript
bindTabsToScrollable(tabsController: TabsController, scroller: Scroller): void
```

Bind tabs to scrollable container component to automatically hide tab bar.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md) | Yes | The controller of the tabs. |
| scroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | Yes | The controller of the scrollable container component. |

## closeBindSheet

```TypeScript
closeBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>): Promise<void>
```

Closes the sheet corresponding to **bindSheetContent**. This API uses a promise to return the result.

> **NOTE:** 
> 
> Closing a sheet using this API will not invoke the **shouldDismiss** callback.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bindSheetContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content to display on the sheet. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [120001](../errorcode-bindSheet.md#120001-incorrect-bindsheetcontent) | The bindSheetContent is incorrect. |
| [120003](../errorcode-bindSheet.md#120003-no-matching-modal-found) | The bindSheetContent cannot be found. |

## constructor

```TypeScript
constructor()
```

Construct a **UIContext** object.

> **NOTE:** 
> 
> A **UIContext** object created using the constructor points to an ambiguous UI context, meaning it is not bound
> to any specific UI instance. The unique ID of such a UIContext instance is -1.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## createAnimator

```TypeScript
createAnimator(options: AnimatorOptions): AnimatorResult
```

Creates an **Animator** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | Yes | Animator options. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## createAnimator

```TypeScript
createAnimator(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult
```

Creates an **AnimatorResult** object for animations. Compared to the previous [createAnimator](#createanimator) API, this API adds support for the [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) &#124; [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Yes | Animator options. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## createUIContextWithoutWindow

```TypeScript
static createUIContextWithoutWindow(context: common.UIAbilityContext | common.ExtensionContext) : UIContext | undefined
```

Creates a UI instance that does not depend on a window and returns its UI context. The created UI instance is a singleton.

> **NOTE:** 
> 
> The returned UI context can only be used to create [custom nodes](../../../ui/arkts-user-defined-node.md). It
> cannot be used for other UI operations.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) &#124; [common.ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-extensioncontext-t.md) | Yes | Context corresponding to [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md) or [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) &#124; undefined | Context of the created UI instance, or **undefined** if creation fails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. The number of parameters is incorrect. <br> 2. Invalid parameter type of context. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## destroyUIContextWithoutWindow

```TypeScript
static destroyUIContextWithoutWindow(): void
```

Destroys the UI instance created using [createUIContextWithoutWindow](#createuicontextwithoutwindow).

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dispatchKeyEvent

```TypeScript
dispatchKeyEvent(node: number | string, event: KeyEvent): boolean
```

Dispach keyboard event to the frameNode with inspector key.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | number &#124; string | Yes | The uniqueId or inspector key of the target FrameNode. |
| event | [KeyEvent](../arkts-components/arkts-arkui-keyevent-i.md) | Yes | The key event to be sent. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether the key event is consumed. |

## enableEventPassthrough

```TypeScript
enableEventPassthrough(enabled: boolean, eventType: RawInputEventType): void
```

Whether to enable or disable event passthrough.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | enable or disable event passthrough. The default value is false. |
| eventType | [RawInputEventType](arkts-arkui-rawinputeventtype-e.md) | Yes | the type of raw input event. |

## enableSwipeBack

```TypeScript
enableSwipeBack(enabled: Optional<boolean>): void
```

whether to enable or disable swipe to back event.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | Yes | enable or disable swipe to back event. |

## fp2px

```TypeScript
fp2px(value: number): number
```

Converts a value in fp units to a value in px.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

## getAllUIContexts

```TypeScript
static getAllUIContexts(): UIContext[]
```

Obtains all currently valid UIContext instances.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)[] | Array of all currently valid UIContext instances. Returns an empty array if no valid UIContext instance exists. |

## getAtomicServiceBar

```TypeScript
getAtomicServiceBar(): Nullable<AtomicServiceBar>
```

Get AtomicServiceBar.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Nullable](arkts-arkui-nullable-t.md)&lt;[AtomicServiceBar](arkts-arkui-arkui-uicontext-atomicservicebar-i.md)&gt; | The atomic service bar. |

## getAttachedFrameNodeById

```TypeScript
getAttachedFrameNodeById(id: string): FrameNode | null
```

Get the FrameNode attached to current window by id.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The id of FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | The instance of FrameNode. |

## getCallingScopeUIContext

```TypeScript
static getCallingScopeUIContext(): UIContext | undefined
```

Obtains the UIContext of this [calling scope](../../../ui/arkts-global-interface.md#basic-concepts). This API returns **undefined** if the calling scope is ambiguous.

> **NOTE:** 
> 
> The returned UIContext object may point to a destroyed UI instance, which usually occurs when an asynchronous
> task is dispatched from an instance that has already been destroyed. As such, you are advised to verify its
> validity via the [isAvailable](#isavailable) API.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) &#124; undefined | UIContext of the current [calling scope](../../../ui/arkts-global-interface.md#basic-concepts). Returns **undefined** if the calling scope is ambiguous. |

## getComponentSnapshot

```TypeScript
getComponentSnapshot(): ComponentSnapshot
```

Get ComponentSnapshot.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md) | the ComponentSnapshot |

## getComponentUtils

```TypeScript
getComponentUtils(): ComponentUtils
```

get object ComponentUtils.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ComponentUtils](arkts-arkui-arkui-uicontext-componentutils-c.md) | object ComponentUtils. |

## getContextMenuController

```TypeScript
getContextMenuController(): ContextMenuController
```

Get object context menu controller.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ContextMenuController](arkts-arkui-arkui-uicontext-contextmenucontroller-c.md) | object context menu controller. |

## getCursorController

```TypeScript
getCursorController(): CursorController
```

Get object cursor controller.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [CursorController](arkts-arkui-arkui-uicontext-cursorcontroller-c.md) | object cursor controller. |

## getDialogPresenter

```TypeScript
getDialogPresenter(): DialogPresenter
```

Get the Dialog object.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DialogPresenter](arkts-arkui-arkui-uicontext-dialogpresenter-c.md) | Dialog object. |

## getDragController

```TypeScript
getDragController(): DragController
```

Get DragController.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) | the DragController |

## getFilteredInspectorTree

```TypeScript
getFilteredInspectorTree(filters?: Array<string>): string
```

Obtains the component tree and component attributes. This API has a long processing time and is intended for <br>testing scenarios only.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filters | Array&lt;string&gt; | No | List of component attributes used for filtering. Currently, only the following filter fields are supported:<br>**"id"**: unique ID of the component. <br>**"src"**: source of the resource. <br>**"content"**: information or data contained in the element, component, or object. <br>**"editable"**: whether the component is editable. <br>**"scrollable"**: whether the component is scrollable. <br>**"selectable"**: whether the component is selectable. <br>**"focusable"**: whether the component is focusable. <br>**"focused"**: whether the component is currently focused. <br>If **filters** includes one or more fields, unspecified fields will be filtered out from the results. <br>If **filters** is not provided or is an empty array, none of the aforementioned fields <br>will be filtered out. <br>The following filter field is supported since API version 20: <br>**"isLayoutInspector"**: whether the component tree contains custom components. <br>If **filters** is omitted or <br>does not contain **"isLayoutInspector"**, the returned component tree <br>will not include custom component details. <br>Other filter fields are used only in testing scenarios. |

**Return value:**

| Type | Description |
| --- | --- |
| string | JSON string of the component tree and component attributes. For details about each field in the component, see the return value description of [getInspectorInfo](arkts-arkui-framenode-c.md#getinspectorinfo). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## getFilteredInspectorTreeById

```TypeScript
getFilteredInspectorTreeById(id: string, depth: number, filters?: Array<string>): string
```

Obtains the attributes of the specified component and its child components. This API has a long processing time <br>and is intended for testing scenarios only.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the target component. |
| depth | number | Yes | Number of layers of child components. If the value is **0**, the attributes of the specified component and all its child components are obtained. If the value is **1**, only the attributes of<br>the specified component are obtained. If the value is **2**, the attributes of <br>the specified component and its <br>level-1 child components are obtained. The rest can be deduced by analogy. |
| filters | Array&lt;string&gt; | No | List of component attributes used for filtering. Currently, only the following filter fields are supported:<br>**"id"**: unique ID of the component. <br>**"src"**: source of the resource. <br>**"content"**: information or data contained in the element, component, or object. <br>**"editable"**: whether the component is editable. <br>**"scrollable"**: whether the component is scrollable. <br>**"selectable"**: whether the component is selectable. <br>**"focusable"**: whether the component is focusable. <br>**"focused"**: whether the component is currently focused. <br>If **filters** includes one or more fields, unspecified fields will be filtered out from the results. <br>If **filters** is not provided or is an empty array, none of the aforementioned fields <br>will be filtered out. <br>Other filter fields are used only in testing scenarios. |

**Return value:**

| Type | Description |
| --- | --- |
| string | JSON string of the attributes of the specified component and its child components. For details about each field in the component, see the return value <br>description of [getInspectorInfo](arkts-arkui-framenode-c.md#getinspectorinfo). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## getFocusController

```TypeScript
getFocusController(): FocusController
```

Get FocusController.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [FocusController](arkts-arkui-arkui-uicontext-focuscontroller-c.md) | the FocusController |

## getFont

```TypeScript
getFont(): Font
```

Obtains a **Font** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Font](arkts-arkui-arkui-uicontext-font-c.md) | **Font** object. |

## getFrameNodeById

```TypeScript
getFrameNodeById(id: string): FrameNode | null
```

Get FrameNode by id.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The id of FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | The instance of FrameNode. |

## getFrameNodeByUniqueId

```TypeScript
getFrameNodeByUniqueId(id: number): FrameNode | null
```

Get FrameNode by uniqueId. Obtains the entity node, FrameNode, of a component on the component tree using its uniqueId. The return value depends on the type of component associated with the uniqueId.

1. If the uniqueId corresponds to a built-in component, the associated FrameNode is returned.
2. If the uniqueId corresponds to a custom component: If the component has rendered content, its root node is
returned, with the type __Common__; if the component has no rendered content, the FrameNode of its first child component is returned.
3. If the uniqueId does not correspond to any component, null is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | The uniqueId of the FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | The FrameNode with the target uniqueId, or null if the frameNode is not existed. |

## getHostContext

```TypeScript
getHostContext(): Context | undefined
```

Obtains the context of this ability.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Context](arkts-arkui-context-t.md) &#124; undefined | Context of the ability. The context type depends on the ability type. For example, if this API is called in a page within a UIAbility window, the returned context type is [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md). If this API is called in a page within an ExtensionAbility window, the returned context type is [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md). If the ability context does not exist, **undefined** is returned. |

## getId

```TypeScript
getId(): number
```

Obtains the unique ID of a UI instance object. In multi-instance scenarios, you can use this unique ID to distinguish between different UI instance objects for easier management.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Unique ID of the backend instance. The value range is [-1, +∞). |

## getKeyboardAvoidMode

```TypeScript
getKeyboardAvoidMode(): KeyboardAvoidMode
```

Obtains the avoidance mode of the virtual keyboard.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [KeyboardAvoidMode](arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md) | Avoidance mode of the virtual keyboard. |

## getLastFocusedUIContext

```TypeScript
static getLastFocusedUIContext(): UIContext | undefined
```

Obtains the UIContext of the UI instance that most recently switched to the focused state.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) &#124; undefined | UIContext of the UI instance that most recently switched to the focused state. Returns **undefined** if the most recently focused instance has been destroyed or if no instance has ever been focused. |

## getLastForegroundUIContext

```TypeScript
static getLastForegroundUIContext(): UIContext | undefined
```

Obtains the UIContext of the UI instance that most recently switched to the foreground state.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) &#124; undefined | UIContext of the UI instance that most recently switched to the foreground state. Returns **undefined** if the most recently foreground UI instance has been destroyed or if no UI instance has ever been in the foreground. |

## getMagnifier

```TypeScript
getMagnifier(): Magnifier
```

Obtains a [Magnifier](arkts-arkui-arkui-uicontext-magnifier-c.md) object, which can be used to control the display and hiding of a magnifier.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Magnifier](arkts-arkui-arkui-uicontext-magnifier-c.md) | **Magnifier** object, which can be used to control the display and hiding of a magnifier. |

## getMaxFontScale

```TypeScript
getMaxFontScale(): number
```

Get the max font scale.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | The max font scale. |

## getMeasureUtils

```TypeScript
getMeasureUtils(): MeasureUtils
```

Obtains a **MeasureUtils** object for text calculation.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [MeasureUtils](arkts-arkui-arkui-uicontext-measureutils-c.md) | Text metrics, such as text height and width. |

## getMediaQuery

```TypeScript
getMediaQuery(): MediaQuery
```

get object mediaQuery.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [MediaQuery](arkts-arkui-arkui-uicontext-mediaquery-c.md) | object MediaQuery. |

## getNavigationInfoByUniqueId

```TypeScript
getNavigationInfoByUniqueId(id: number): observer.NavigationInfo | undefined
```

Get navigation information of the frameNode with uniqueId.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | The uniqueId of the target FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [observer.NavigationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md) &#124; undefined | The navigation information of the frameNode with the target uniqueId, or undefined if the frameNode is not existed or does not have navigation information. |

## getOverlayManager

```TypeScript
getOverlayManager(): OverlayManager
```

Obtains the OverlayManager object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [OverlayManager](arkts-arkui-arkui-uicontext-overlaymanager-c.md) | OverlayManager instance obtained. |

## getOverlayManagerOptions

```TypeScript
getOverlayManagerOptions(): OverlayManagerOptions
```

Get object OverlayManagerOptions.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [OverlayManagerOptions](arkts-arkui-arkui-uicontext-overlaymanageroptions-i.md) | object OverlayManagerOptions. |

## getPageInfoByUniqueId

```TypeScript
getPageInfoByUniqueId(id: number): PageInfo
```

Get page information of the frameNode with uniqueId.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | The uniqueId of the target FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [PageInfo](arkts-arkui-arkui-uicontext-pageinfo-i.md) | The page information of the frameNode with the target uniqueId, includes navDestination and router page information. If the frame node does not have navDestination and router page information, it will return an empty object. |

## getPageRootNode

```TypeScript
getPageRootNode(): FrameNode | null
```

Obtains the root node of the page corresponding to the UIContext.

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | FrameNode of the root node of the page or **null**.<br>If no valid FrameNode is available, **null** is returned. <br>If no page is loaded in the window, **null** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [120007](../errorcode-uicontext.md#120007-instance-not-exist) | The UIContext is not available. |

## getPixelRoundMode

```TypeScript
getPixelRoundMode(): PixelRoundMode
```

Obtains the pixel rounding mode for this page.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PixelRoundMode](arkts-arkui-pixelroundmode-e.md) | Pixel rounding mode of the current page. |

## getPromptAction

```TypeScript
getPromptAction(): PromptAction
```

Obtains a PromptAction object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md) | PromptAction object. |

## getRouter

```TypeScript
getRouter(): Router
```

Obtains a Router object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Router](arkts-arkui-arkui-uicontext-router-c.md) | Router object. |

## getSharedLocalStorage

```TypeScript
getSharedLocalStorage(): LocalStorage | undefined
```

Obtains the **LocalStorage** instance shared by this stage.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LocalStorage](arkts-arkui-localstorage-c.md) &#124; undefined | **LocalStorage** instance if it exists; **undefined** if it does not exist. |

## getSmartGestureController

```TypeScript
getSmartGestureController(): SmartGestureController
```

Get object smart gesture controller.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [SmartGestureController](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md) | object smart gesture controller. |

## getTextMenuController

```TypeScript
getTextMenuController(): TextMenuController
```

Obtains a [TextMenuController](arkts-arkui-arkui-uicontext-textmenucontroller-c.md) object, which can be used to control the context menu on selection.

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 16.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TextMenuController](arkts-arkui-arkui-uicontext-textmenucontroller-c.md) | Obtained **TextMenuController** object. |

## getUIInspector

```TypeScript
getUIInspector(): UIInspector
```

Obtains the **UIInspector** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIInspector](arkts-arkui-arkui-uicontext-uiinspector-c.md) | **UIInspector** object. |

## getUIObserver

```TypeScript
getUIObserver(): UIObserver
```

Obtains the **UIObserver** object.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIObserver](arkts-arkui-arkui-uicontext-uiobserver-c.md) | **UIObserver** object. |

## getWindowHeightBreakpoint

```TypeScript
getWindowHeightBreakpoint(): HeightBreakpoint
```

Obtains the height breakpoint value of the window where this instance is located. The specific value is determined based on the window aspect ratio. For details, see [HeightBreakpoint](arkts-arkui-heightbreakpoint-e.md).

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [HeightBreakpoint](arkts-arkui-heightbreakpoint-e.md) | Height breakpoint value of the window where the current instance is located. If the window aspect ratio is 0, **HEIGHT_SM** is returned. |

## getWindowId

```TypeScript
getWindowId(): number | undefined
```

Obtains the ID of the window to which the current application instance belongs.

> **NOTE:** 
> 
> If the UIContext resides inside a
> [UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) that runs in the main
> application process, the top-level window ID of the main application is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number &#124; undefined | ID of the window to which the current application instance belongs. If the window does not exist, **undefined** is returned. |

## getWindowName

```TypeScript
getWindowName(): string | undefined
```

Obtains the name of the window where this instance is located.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; undefined | Name of the window where the current instance is located. If the window does not exist, **undefined** is returned. |

## getWindowWidthBreakpoint

```TypeScript
getWindowWidthBreakpoint(): WidthBreakpoint
```

Obtains the width breakpoint value of the window where this instance is located. The specific value is determined by the vp value of the window width. For details, see [WidthBreakpoint](arkts-arkui-widthbreakpoint-e.md).

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [WidthBreakpoint](arkts-arkui-widthbreakpoint-e.md) | Width breakpoint value of the window where the current instance is located. If the window width is 0 vp, **WIDTH_XS** is returned. |

## isAvailable

```TypeScript
isAvailable(): boolean
```

Checks whether the UI instance corresponding to this **UIContext** object is valid. The **UIContext** object can be obtained using the [getUIContext](../../../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10) API. A UI instance is considered valid when the backend UI instance exists. UIContext objects created using **new UIContext()** have no corresponding UI instance. After multiple [loadContent](../../../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9) operations, old UI instances become invalid. In multi-window scenarios, when a window is closed, its UI instance becomes invalid. In summary, a UIContext object is invalid when it has no corresponding backend UI instance.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the UI instance corresponding to the current **UIContext** object is valid. The value **true** indicates yes, and the value **false** indicates no. |

## isEasySplit

```TypeScript
isEasySplit(): boolean
```

Checks whether the current UI instance is in easy split mode.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the current UI instance is in easy split mode; returns false otherwise. |

## isFollowingSystemFontScale

```TypeScript
isFollowingSystemFontScale(): boolean
```

Checks whether current font scale follows the system.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if current font scale follows the system; returns false otherwise. |

## keyframeAnimateTo

```TypeScript
keyframeAnimateTo(param: KeyframeAnimateParam, keyframes: Array<KeyframeState>): void
```

Generates a key frame animation. For details about how to use this API, see [keyframeAnimateTo](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [KeyframeAnimateParam](../arkts-components/arkts-arkui-keyframeanimateparam-i.md) | Yes | Overall animation parameter of the keyframe animation. |
| keyframes | Array&lt;[KeyframeState](../arkts-components/arkts-arkui-keyframestate-i.md)&gt; | Yes | List of all keyframe states. |

## lpx2px

```TypeScript
lpx2px(value: number): number
```

Converts a value in lpx units to a value in px.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

## openBindSheet

```TypeScript
openBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>, sheetOptions?: SheetOptions, targetId?: number): Promise<void>
```

Creates a sheet whose content is as defined in **bindSheetContent** and displays the sheet. This API uses a promise to return the result.

> **NOTE:** 
> 
> 1. When calling this API, if no valid value is provided for **targetId**, you won't be able to set
> **SheetOptions.preferType** to **POPUP** or **SheetOptions.mode** to **EMBEDDED**.
> 
> 2. Since [updateBindSheet](#updatebindsheet) and [closeBindSheet](#closebindsheet)depend on **bindSheetContent**, you need to maintain the passed **bindSheetContent** yourself.
> 
> 3. Setting **SheetOptions.UIContext** is not supported.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bindSheetContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content to display on the sheet. |
| sheetOptions | [SheetOptions](../arkts-components/arkts-arkui-sheetoptions-i.md) | No | Style of the sheet.<br>**NOTE:** <br>1. **SheetOptions.uiContext** cannot be set. Its value is fixed to the **UIContext** object of the current instance.<br>2. If **targetId** is not passed in, **SheetOptions.preferType** cannot be set to **POPUP**; if **POPUP** is set, it will be replaced with **CENTER**.<br>3. If **targetId** is not passed in, **SheetOptions.mode** cannot be set to **EMBEDDED**; the default mode is **OVERLAY**.<br>4. For the default values of other attributes, see [SheetOptions](../arkts-components/arkts-arkui-sheetoptions-i.md). |
| targetId | number | No | ID of the component to be bound. If this parameter is not set, no component is bound. If the ID does not exist, the error code 120004 is returned. Returns error code 401 if **undefined** is passed in. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [120001](../errorcode-bindSheet.md#120001-incorrect-bindsheetcontent) | The bindSheetContent is incorrect. |
| [120002](../errorcode-bindSheet.md#120002-modal-for-bindsheetcontent-already-exists) | The bindSheetContent already exists. |
| [120004](../errorcode-bindSheet.md#120004-specified-targetid-does-not-exist) | The targetId does not exist. |
| [120005](../errorcode-bindSheet.md#120005-node-specified-by-targetid-is-not-mounted-on-the-component-tree) | The node of targetId is not in the component tree. |
| [120006](../errorcode-bindSheet.md#120006-node-specified-by-targetid-is-not-a-child-of-a-page-node-or-navdestination-node) | The node of targetId is not a child of the page node or NavDestination node. |

## postDelayedFrameCallback

```TypeScript
postDelayedFrameCallback(frameCallback: FrameCallback, delayTime: number): void
```

Post a frame callback to run on the next frame after the specified delay.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| frameCallback | [FrameCallback](arkts-arkui-arkui-uicontext-framecallback-c.md) | Yes | The frame callback to run on the next frame. |
| delayTime | number | Yes | The delay time in milliseconds, |

## postFrameCallback

```TypeScript
postFrameCallback(frameCallback: FrameCallback): void
```

Post a frame callback to run on the next frame.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| frameCallback | [FrameCallback](arkts-arkui-arkui-uicontext-framecallback-c.md) | Yes | The frame callback to run on the next frame. |

## px2fp

```TypeScript
px2fp(value: number): number
```

Converts a value in px units to a value in fp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

## px2lpx

```TypeScript
px2lpx(value: number): number
```

Converts a value in px units to a value in lpx.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

## px2vp

```TypeScript
px2vp(value: number): number
```

Converts a value in px units to a value in vp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

## removeLocalInputEventMonitor

```TypeScript
removeLocalInputEventMonitor(monitor: InputEventMonitor): void
```

Removes a local input event monitor.

**Important Notes**:

- Only Monitor objects returned by addLocalInputEventMonitor can be removed.  
- Cannot unregister a monitor by manually constructing an object.  
- If an invalid object is passed, the system silently ignores it.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monitor | [InputEventMonitor](../arkts-components/arkts-arkui-inputeventmonitor-i.md) | Yes | Monitor identifier object (returned by addLocalInputEventMonitor). |

## requireDynamicSyncScene

```TypeScript
requireDynamicSyncScene(id: string): Array<DynamicSyncScene>
```

Require DynamicSyncScene by id.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The id of DynamicSyncScene. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md)&gt; | The instance of SwiperDynamicSyncScene. |

## resolveUIContext

```TypeScript
static resolveUIContext(): ResolvedUIContext
```

Obtains a UIContext instance along with its resolution strategy using a predefined priority order.

> **NOTE:** 
> 
> This API resolves and returns a UIContext instance together with the strategy used to determine it,
> 
> based on the following priority rules (in order):
> 
> 1. UIContext in the current calling scope.
> 
> 2. If only one UI instance exists, its UIContext is returned.
> 
> 3. If a UI instance has switched to the focused state, and the most recently focused UI instance has not been destroyed, the UIContext of that most recently focused instance is returned.
> 
> 4. If a UI instance has switched to the foreground state, and the most recently foreground UI instance has not been destroyed, the UIContext of that most recently foreground instance is returned.
> 
> 5. If multiple UI instances exist, the UIContext with the largest unique instance ID is returned.
> 
> 6. If none of the above conditions are met, an invalid UIContext instance is returned.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ResolvedUIContext](arkts-arkui-arkui-uicontext-resolveduicontext-c.md) | UIContext instance along with its resolution strategy. |

## runScopedTask

```TypeScript
runScopedTask(callback: () => void): void
```

Run custom functions inside the UIContext scope.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | () =&gt; void | Yes | The function called through UIContext. |

## setCustomKeyboardContinueFeature

```TypeScript
setCustomKeyboardContinueFeature(feature: CustomKeyboardContinueFeature): void
```

Set custom keyboard continue feature.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| feature | [CustomKeyboardContinueFeature](arkts-arkui-arkui-uicontext-customkeyboardcontinuefeature-e.md) | Yes | The custom keyboard continue feature. |

## setImageCacheCount

```TypeScript
setImageCacheCount(value: number): void
```

Set image cache capacity of decoded image count. if not set, the application will not cache any decoded image.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | capacity of decoded image count. |

## setImageRawDataCacheSize

```TypeScript
setImageRawDataCacheSize(value: number): void
```

Set image cache capacity of raw image data size in bytes before decode. if not set, the application will not cache any raw image data.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | capacity of raw image data size in bytes. |

## setKeyboardAvoidMode

```TypeScript
setKeyboardAvoidMode(value: KeyboardAvoidMode): void
```

Sets the avoidance mode for the virtual keyboard.

> **NOTE:** 
> 
> With **KeyboardAvoidMode.RESIZE**, the page is resized to prevent the virtual keyboard from obstructing the
> view. Regarding components on the page, those whose width and height are set in percentage are resized with the
> page, and those whose width and height are set to specific values are laid out according to their settings.
> With **KeyboardAvoidMode.RESIZE**, **expandSafeArea([SafeAreaType.KEYBOARD],[SafeAreaEdge.BOTTOM])** does not
> take effect.
> 
> With **KeyboardAvoidMode.NONE**, keyboard avoidance is disabled, and the page will be covered by the displayed
> keyboard.
> 
> **setKeyboardAvoidMode** only affects page layouts. It does not apply to popup components, including the
> following: **Dialog**, **Popup**, **Menu**, **BindSheet**, **BindContentCover**, **Toast**, **OverlayManager**.
> For details about the avoidance mode of popup components, see
> [CustomDialogControllerOptions](../../../reference/arkui-ts/ts-methods-custom-dialog-box.md).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [KeyboardAvoidMode](arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md) | Yes | Avoidance mode of the virtual keyboard.<br>Default value: **KeyboardAvoidMode.OFFSET**, which means that the page moves up when the keyboard is displayed.<br>When **setKeyboardAvoidMode** is set to an invalid value, this attribute does not take effect. |

## setOverlayManagerOptions

```TypeScript
setOverlayManagerOptions(options: OverlayManagerOptions): boolean
```

Init OverlayManager.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [OverlayManagerOptions](arkts-arkui-arkui-uicontext-overlaymanageroptions-i.md) | Yes | Options. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if it is called first and before getting an OverlayManager instance; returns false otherwise. |

## setPixelRoundMode

```TypeScript
setPixelRoundMode(mode: PixelRoundMode): void
```

Sets the pixel rounding mode for this page.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [PixelRoundMode](arkts-arkui-pixelroundmode-e.md) | Yes | Pixel rounding mode. Default value:**PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH**.<br>If this parameter is set to an invalid value, the default value will be used. |

## setResourceManagerCacheMaxCountForHSP

```TypeScript
static setResourceManagerCacheMaxCountForHSP(count: number): void
```

Set the upper limit for the cache count of HSP resource management objects.

If the upper limit of the cache is set too high, there is a risk of excessive memory overhead. It is recommended to configure it according to actual needs.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | The cache limit of resource manager for HSP, must be non negative integers. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100101](../errorcode-uicontext.md#100101-invalid-negative-parameter-value) | The parameter is less than 0. |
| [100102](../errorcode-uicontext.md#100102-incorrect-parameter-type) | The parameter value cannot be a floating point number. |
| [100103](../errorcode-uicontext.md#100103-invalid-thread-context) | The function cannot be called from a non main thread. |

## setTextSelectionClearPolicy

```TypeScript
setTextSelectionClearPolicy(policy: TextSelectionClearPolicy): void
```

Sets the text selection clear policy for text component. Default policy: **TextSelectionClearPolicy.KEEP_SELECTED_TEXT_ON_EXTERNAL_TOUCH**

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [TextSelectionClearPolicy](arkts-arkui-arkui-uicontext-textselectionclearpolicy-e.md) | Yes | The text selection clear policy. |

## showActionSheet

```TypeScript
showActionSheet(value: ActionSheetOptions): void
```

Shows an action sheet in the given settings.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) | Yes | Parameters of the action sheet. |

## showAlertDialog

```TypeScript
showAlertDialog(options: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions): void
```

Shows an alert dialog box.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AlertDialogParamWithConfirm](arkts-arkui-alertdialogparamwithconfirm-i.md) &#124; [AlertDialogParamWithButtons](arkts-arkui-alertdialogparamwithbuttons-i.md) &#124; [AlertDialogParamWithOptions](arkts-arkui-alertdialogparamwithoptions-i.md) | Yes | Shows an AlertDialog component in the given settings. |

## showDatePickerDialog

```TypeScript
showDatePickerDialog(options: DatePickerDialogOptions): void
```

datePickerDialog display.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DatePickerDialogOptions](../arkts-components/arkts-arkui-datepickerdialogoptions-i.md) | Yes | Options. |

## showTextPickerDialog

```TypeScript
showTextPickerDialog(options: TextPickerDialogOptions): void
```

textPickerDialog display.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextPickerDialogOptions](../arkts-components/arkts-arkui-textpickerdialogoptions-i.md) | Yes | Options. |

## showTextPickerDialog

```TypeScript
showTextPickerDialog(style: TextPickerDialogOptions | TextPickerDialogOptionsExt): void
```

textPickerDialog display.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [TextPickerDialogOptions](../arkts-components/arkts-arkui-textpickerdialogoptions-i.md) &#124; [TextPickerDialogOptionsExt](../arkts-components/arkts-arkui-textpickerdialogoptionsext-i.md) | Yes | Dialog style. |

## showTimePickerDialog

```TypeScript
showTimePickerDialog(options: TimePickerDialogOptions): void
```

timePickerDialog display.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TimePickerDialogOptions](../arkts-components/arkts-arkui-timepickerdialogoptions-i.md) | Yes | Options. |

## unbindTabsFromNestedScrollable

```TypeScript
unbindTabsFromNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void
```

Unbind tabs from nested scrollable container components.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md) | Yes | The controller of the tabs. |
| parentScroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | Yes | The controller of the parent scrollable container component. |
| childScroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | Yes | The controller of the child scrollable container component. |

## unbindTabsFromScrollable

```TypeScript
unbindTabsFromScrollable(tabsController: TabsController, scroller: Scroller): void
```

Unbind tabs from scrollable container component.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md) | Yes | The controller of the tabs. |
| scroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | Yes | The controller of the scrollable container component. |

## updateBindSheet

```TypeScript
updateBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>, sheetOptions: SheetOptions, partialUpdate?: boolean): Promise<void>
```

Updates the style of the sheet corresponding to the provided **bindSheetContent**. This API uses a promise to return the result.

> **NOTE:** 
> 
> **SheetOptions.UIContext**, **SheetOptions.mode**, and callback functions cannot be updated.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bindSheetContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content to display on the sheet. |
| sheetOptions | [SheetOptions](../arkts-components/arkts-arkui-sheetoptions-i.md) | Yes | Style of the sheet.<br>**NOTE:** <br>**SheetOptions.UIContext** and **SheetOptions.mode** cannot be updated. |
| partialUpdate | boolean | No | Whether to update the sheet in incremental mode.<br>Default value: **false**<br> **NOTE:** <br>1. **true**: incremental update, where the specified properties in **SheetOptions** are updated, and other properties stay at their current value.<br>2. **false**: full update, where all properties except those specified in **SheetOptions** are restored to default values. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [120001](../errorcode-bindSheet.md#120001-incorrect-bindsheetcontent) | The bindSheetContent is incorrect. |
| [120003](../errorcode-bindSheet.md#120003-no-matching-modal-found) | The bindSheetContent cannot be found. |

## vp2px

```TypeScript
vp2px(value: number): number
```

Converts a value in vp units to a value in px.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |
