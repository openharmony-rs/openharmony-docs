# PlaceholderRegister

```TypeScript
export class PlaceholderRegister
```

Provides the methods for registering, unregistering, and querying scroll placeholder builders. Each UI instance holds its own registry: builders registered in one instance are not visible to another. Do not create instances of this class; use [getPlaceholderRegister()](arkts-arkui-arkui-uicontext-uicontext-c.md#getplaceholderregister) to obtain the registry of the current UI instance.

**Since:** 26.1.0

<!--Device-unnamed-export class PlaceholderRegister--><!--Device-unnamed-export class PlaceholderRegister-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { PlaceholderOptions, PlaceholderProvider, PlaceholderRegister } from '@kit.ArkUI';
```

## isRegistered

```TypeScript
isRegistered(id: string): boolean
```

Checks whether a placeholder builder has been registered under the given ID for this UI instance.

This is a read-only query: it does not change the registration state and does not affect subsequent placeholder behavior. A template remains registered regardless of whether the framework currently retains prebuilt placeholder instances for it.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PlaceholderRegister-isRegistered(id: string): boolean--><!--Device-PlaceholderRegister-isRegistered(id: string): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the placeholder template to query. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the ID has been registered in this UI instance; **false** otherwise. |

## register

```TypeScript
register(id: string, builder: WrappedBuilder<[]>): void
```

Registers a placeholder builder under the given ID for scrollable components.

The builder must be a global, parameterless **@Builder({ isPlaceholder: true })** function that performs read-only static rendering: it must not access reactive state, register gestures, or register business callbacks. To pass the builder, wrap it with **wrapBuilder**.

Registering the same ID again atomically publishes a new template version; placeholder tasks already dispatched are validated against the template generation before being mounted.

The framework validates the restricted-builder mark carried in the compile product at registration. A builder that is not marked with **@Builder({ isPlaceholder: true })** at compile time (including builders passed in through dynamic means that bypass compile-time type checks) is rejected: the ID is not registered, and a **scrollPlaceholder** provider hit on it uses the system default placeholder.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PlaceholderRegister-register(id: string, builder: WrappedBuilder<[]>): void--><!--Device-PlaceholderRegister-register(id: string, builder: WrappedBuilder<[]>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the placeholder template. A **scrollPlaceholder** provider refers to the template by this ID. |
| builder | [WrappedBuilder](../arkts-components/arkts-arkui-common-comp-wrappedbuilder-c.md)&lt;[]&gt; | Yes | Global parameterless placeholder builder wrapped through **wrapBuilder**; a bare builder function is not accepted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 100031 | Registration rejected: the builder is not marked with **@Builder({ isPlaceholder: true })**. The ID is not registered. |

## unregister

```TypeScript
unregister(id: string): void
```

Unregisters the placeholder builder registered under the given ID for this UI instance.

Once a template is unregistered, its ID can no longer be matched: a **scrollPlaceholder** provider hit on this ID uses the system default placeholder, and placeholder tasks already dispatched for the template are not mounted. Unregistering an ID that is not registered is a silent no-op.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PlaceholderRegister-unregister(id: string): void--><!--Device-PlaceholderRegister-unregister(id: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the placeholder template to unregister. |
