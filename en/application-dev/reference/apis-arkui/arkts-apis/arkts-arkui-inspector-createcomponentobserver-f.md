# createComponentObserver

## Modules to Import

```TypeScript
import { inspector } from '@kit.ArkUI';
```

## createComponentObserver

```TypeScript
function createComponentObserver(id: string): ComponentObserver
```

Binds to the specified component and returns the corresponding observation handle.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** [createComponentObserver](arkts-arkui-arkui-uicontext-uiinspector-c.md#createcomponentobserver)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-inspector-function createComponentObserver(id: string): ComponentObserver--><!--Device-inspector-function createComponentObserver(id: string): ComponentObserver-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the target component, set using the universal attributes [id](../arkui-ts/ts-universal-attributes-component-id.md#id) or [key](../arkui-ts/ts-universal-attributes-component-id.md#key12). |

**Return value:**

| Type | Description |
| --- | --- |
| [ComponentObserver](arkts-arkui-inspector-componentobserver-i.md) | Component observer handle, which is used to register and unregister callbacks. |

**Examples**

```TypeScript
let listener: inspector.ComponentObserver = inspector.createComponentObserver('COMPONENT_ID'); // Listen for callback events for the component whose ID is COMPONENT_ID.
```
