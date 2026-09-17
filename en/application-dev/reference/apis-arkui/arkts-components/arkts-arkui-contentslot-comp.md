# ContentSlot

The **ContentSlot** component is a component designed to render and manage components created on the native layer using C APIs.

With support for hybrid development, the **ContentSlot** component is recommended when the container is an ArkTS component and the child component is created on the native side.

## ContentSlot

```TypeScript
ContentSlot(content: Content)
```

Called when content is added to a placeholder component

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [Content](arkts-arkui-content-t.md) | Yes | Manager of the **ContentSlot** component. Through the APIs provided by the native side, it can register and trigger the attach and detach event callbacks for **ContentSlot**, as well as manage the child components of **ContentSlot**. |

## Summary

### Types

| Name | Description |
| --- | --- |
| [Content](arkts-arkui-content-t.md) | Defines a base class for **ComponentContent** and **NodeContent**. |

## Examples

```TypeScript
The following example shows the basic usage of ContentSlot.
```
