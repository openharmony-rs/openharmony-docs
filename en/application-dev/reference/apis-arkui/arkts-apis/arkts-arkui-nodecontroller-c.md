# NodeController

```TypeScript
export abstract class NodeController
```

The **NodeController** module provides APIs for managing custom nodes, such as creating, showing, and updating custom nodes, and APIs for mounting custom nodes to a [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component.

> **NOTE:** 
> 
> - NodeController objects do not support JSON serialization.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

Called after the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component bound to this **NodeController** instance is attached and about to appear.

> **NOTE:** 
> 
> For details about the callback timing, see [onAppear](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onappear).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component bound to this **NodeController** instance is destroyed.

> **NOTE:** 
> 
> For details about the callback timing, see [onDisAppear](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ondisappear).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToResize

```TypeScript
aboutToResize?(size: Size): void
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component bound to this **NodeController** instance is resized.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | Size | Yes | Width and height of the component, in vp. |

## makeNode

```TypeScript
abstract makeNode(uiContext: UIContext): FrameNode | null
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component bound to this **NodeController** instance is created. This callback returns a node, which will be mounted to the **NodeContainer**.

This callback can also be invoked through the **rebuild()** method of **NodeController**.

> **NOTE:** 
> 
> [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) does not support cross-instance reuse. If
> [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) is reused across instances and
> [NodeController](arkts-arkui-nodecontroller-c.md) of [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute)
> triggers the [makeNode](#makenode) callback method, the
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) object in the input parameter may be undefined. In this case, you need
> to check whether the [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) object in the input parameter is undefined, which
> prevents the [invalid UIContext](../../../ui/arkts-wrong-uicontext-debug.md#identifying-uicontext-errors) when
> the input parameter is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | UI context of the bound [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | **FrameNode** object, which will be mounted to the placeholder node of the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component. If a null object is returned, the child nodes of the corresponding [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component are removed. |

## onAttach

```TypeScript
onAttach?(): void
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component bound to this **NodeController** instance is attached to the main node tree.

> **NOTE:** 
> 
> For details about the callback timing, see [onAttach](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onattach).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onBind

```TypeScript
onBind?(containerId: number): void
```

Called after this **NodeController** instance is bound to a [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| containerId | number | Yes | ID of the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component to which the **NodeController** instance is bound. |

## onDetach

```TypeScript
onDetach?(): void
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component bound to this **NodeController** instance is detached from the main node tree.

> **NOTE:** 
> 
> For details about the callback timing, see [onDetach](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ondetach).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTouchEvent

```TypeScript
onTouchEvent?(event: TouchEvent): void
```

Called when the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component bound to this **NodeController** instance receives a touch event.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [TouchEvent](../arkts-components/arkts-arkui-common-comp-touchevent-i.md) | Yes | Touch event. |

## onUnbind

```TypeScript
onUnbind?(containerId: number): void
```

Called after this **NodeController** instance is unbound from a [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| containerId | number | Yes | ID of the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component from which the **NodeController** instance is unbound. |

## onWillBind

```TypeScript
onWillBind?(containerId: number): void
```

Called when this **NodeController** instance is about to be bound to a [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| containerId | number | Yes | ID of the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component to which the **NodeController** instance is about to be bound. |

## onWillUnbind

```TypeScript
onWillUnbind?(containerId: number): void
```

Called when this **NodeController** instance is about to be unbound from a [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| containerId | number | Yes | ID of the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component from which the **NodeController** instance is about to be unbound. |

## rebuild

```TypeScript
rebuild(): void
```

Instructs the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component bound to this **NodeController** instance to call the [makeNode](#makenode) API again to change child nodes.

> **NOTE:** 
> 
> Since the **rebuild** API is actively called by the application and is tied to the UI, you need to ensure that
> the UI context is valid at the time of the call, that is, it must be consistent with the UI context of the bound
> NodeContainer.
> 
> In cases where the [UI context is unclear](../../../ui/arkts-global-interface.md#ambiguous-ui-context), for
> example, during event callbacks, you can use the
> [runScopedTask](arkts-arkui-arkui-uicontext-uicontext-c.md#runscopedtask) method of
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to explicitly define the UI context at the time of the call.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
