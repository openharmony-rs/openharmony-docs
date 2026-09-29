# NodeController

```TypeScript
export abstract class NodeController
```

The **NodeController** module provides APIs for managing custom nodes, such as creating, showing, and updating custom nodes, and APIs for mounting custom nodes to a [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute). It is suitable for scenarios where custom nodes need to be dynamically created, updated, and reused on a page.

> **NOTE:** 
> 
> - NodeController objects do not support JSON serialization.

**Since:** 11

<!--Device-unnamed-export abstract class NodeController--><!--Device-unnamed-export abstract class NodeController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) bound to this **NodeController** instance is attached to the main node tree. This callback is asynchronous, and its actual execution time is later than the attachment.

> **NOTE:** 
> 
> For details about the callback timing, see [onAppear](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onappear).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeController-aboutToAppear?(): void--><!--Device-NodeController-aboutToAppear?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) bound to this **NodeController** instance is detached from the main node tree. This callback is synchronous.

> **NOTE:** 
> 
> For details about the callback timing, see [onDisAppear](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ondisappear).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeController-aboutToDisappear?(): void--><!--Device-NodeController-aboutToDisappear?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToResize

```TypeScript
aboutToResize?(size: Size): void
```

Called when [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) bound to **NodeController** is laid out.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeController-aboutToResize?(size: Size): void--><!--Device-NodeController-aboutToResize?(size: Size): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | Size | Yes | Width and height of the component layout size, in vp. |

## makeNode

```TypeScript
abstract makeNode(uiContext: UIContext): FrameNode | null
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component bound to this **NodeController** is created. This callback returns a node, which will be mounted to the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute).

Alternatively, the callback can be triggered through the **rebuild()** API of **NodeController**.

> **NOTE:** 
> 
> [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) does not support cross-instance reuse. If
> [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) is reused across instances and
> [NodeController](arkts-arkui-nodecontroller-c.md) passed to [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute)
> triggers the [makeNode](#makenode) callback, the [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)
> object in the input parameter may be **undefined**. In this case, you need to check whether the object is
> **undefined** to prevent
> [invalid UIContext](../../../ui/arkts-wrong-uicontext-debug.md#identifying-uicontext-errors) when the input
> parameter is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null--><!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | UI context bound to [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) when this API is called back. When [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) is reused across instances, this parameter may be undefined, and you need to determine this yourselves. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | **FrameNode** object. The returned node will be mounted to the placeholder node of [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute). If **null** is returned, the child nodes of the corresponding [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) will be cleared. |

## onAttach

```TypeScript
onAttach?(): void
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) bound to this **NodeController** instance is attached to the main node tree. It is triggered at the same time as [aboutToAppear](#abouttoappear) (both when the **NodeContainer** is attached to the main node tree). The difference is that **onAttach** is a synchronous callback while **aboutToAppear** is an asynchronous callback, so **onAttach** is executed before **aboutToAppear**.

> **NOTE:** 
> 
> For details about the callback timing, see [onAttach](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onattach).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-NodeController-onAttach?(): void--><!--Device-NodeController-onAttach?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onBind

```TypeScript
onBind?(containerId: number): void
```

Called after **NodeController** is bound to [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute). This callback is triggered after [onWillBind](#onwillbind). Both are optional callbacks, and the corresponding logic can be executed before or after binding as needed.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-NodeController-onBind?(containerId: number): void--><!--Device-NodeController-onBind?(containerId: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| containerId | number | Yes | Identifier of [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) that has been bound to **NodeController** when this API is called back. |

## onDetach

```TypeScript
onDetach?(): void
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) bound to this **NodeController** instance is detached from the main node tree. It is triggered at the same time as [aboutToDisappear](#abouttodisappear) (both when the **NodeContainer** is detached from the main node tree). Both are synchronous callbacks. During the detachment process, the framework triggers **onDetach** first and then **aboutToDisappear**, so **onDetach** is executed before **aboutToDisappear**.

> **NOTE:** 
> 
> For details about the callback timing, see [onDetach](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ondetach).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-NodeController-onDetach?(): void--><!--Device-NodeController-onDetach?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTouchEvent

```TypeScript
onTouchEvent?(event: TouchEvent): void
```

Called when [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) bound to **NodeController** receives a touch event.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeController-onTouchEvent?(event: TouchEvent): void--><!--Device-NodeController-onTouchEvent?(event: TouchEvent): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [TouchEvent](../arkts-components/arkts-arkui-common-comp-touchevent-i.md) | Yes | Touch event, which contains information such as the coordinates of the touch point and the touch action type. For details, see **TouchEvent**. |

## onUnbind

```TypeScript
onUnbind?(containerId: number): void
```

Called after **NodeController** is unbound from [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute). This callback is triggered after [onWillUnbind](#onwillunbind). Both are optional callbacks, and the corresponding logic can be executed before or after unbinding as needed.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-NodeController-onUnbind?(containerId: number): void--><!--Device-NodeController-onUnbind?(containerId: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| containerId | number | Yes | Identifier of [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) that has been unbound from **NodeController** when this API is called back. |

## onWillBind

```TypeScript
onWillBind?(containerId: number): void
```

Called when **NodeController** is about to be bound to [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute). This callback is triggered before [onBind](#onbind). Both are optional callbacks, and the corresponding logic can be executed before or after binding as needed.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-NodeController-onWillBind?(containerId: number): void--><!--Device-NodeController-onWillBind?(containerId: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| containerId | number | Yes | Identifier of [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) that is about to be bound with **NodeController** when this API is called back. |

## onWillUnbind

```TypeScript
onWillUnbind?(containerId: number): void
```

Called when **NodeController** is about to be unbound from [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute). This callback is triggered before [onUnbind](#onunbind). Both are optional callbacks, and the corresponding logic can be executed before or after unbinding as needed.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-NodeController-onWillUnbind?(containerId: number): void--><!--Device-NodeController-onWillUnbind?(containerId: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| containerId | number | Yes | Identifier of [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) that is about to be unbound from **NodeController** when this API is called back. |

## rebuild

```TypeScript
rebuild(): void
```

Notifies the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component to call the [makeNode](#makenode) API again to change the child node. For example, when the content data displayed by **NodeContainer** changes and the displayed child node needs to be updated, this API can be called to trigger a rebuild.

> **NOTE:** 
> 
> Since the **rebuild** API is proactively called by the application and the operation is UI-related, you must
> ensure that the UI context is valid when calling this API, that is, the UI context must be consistent with that
> of the bound **NodeContainer**.
> 
> In cases where the [UI context is unclear](../../../ui/arkts-global-interface.md#ambiguous-ui-context), for
> example, during event callbacks, you can use the
> [runScopedTask](arkts-arkui-arkui-uicontext-uicontext-c.md#runscopedtask) API of
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to explicitly define the UI context at the time of the call.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeController-rebuild(): void--><!--Device-NodeController-rebuild(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
