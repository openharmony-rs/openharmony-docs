# getRectangleById

## Modules to Import

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## getRectangleById

```TypeScript
function getRectangleById(id: string): ComponentInfo
```

Obtains a **ComponentInfo** object based on the component ID and synchronously returns the geometric properties of the component.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getComponentUtils](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentutils) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [ComponentUtils](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context. This API provides access to component coordinates and size information after the target component completes layout. It is recommended that you invoke this API within [layout completion callbacks](arkts-arkui-arkui-inspector.md). Note that dynamically created components must be mounted to the component tree before this API can obtain their information, as unmounted components are not measured or laid out by the UI framework. Always ensure that component mounting precedes information retrieval attempts.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** getRectangleById

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Component ID. |

**Return value:**

| Type | Description |
| --- | --- |
| [ComponentInfo](arkts-arkui-componentutils-componentinfo-i.md) | **ComponentInfo** object, which provides the size, position, translation, scaling, rotation, and affine matrix information of the component. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100001](../errorcode-internal.md#100001-internal-error) | UI execution context not found. |

**Examples**

```TypeScript
import { componentUtils } from '@kit.ArkUI';
let modePosition:componentUtils.ComponentInfo = componentUtils.getRectangleById('onClick');
```
