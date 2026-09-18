# LazyDynamicLayoutAttribute

Defines the LazyDynamicLayout attribute functions.

@extends CommonMethod&lt;LazyDynamicLayoutAttribute&gt;

**Inheritance/Implementation:** LazyDynamicLayoutAttribute extends CommonMethod<LazyDynamicLayoutAttribute>

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { LazyDynamicLayout, LazyDynamicLayoutAttribute } from '@kit.ArkUI';
```

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: Callback<number[]> | undefined): LazyDynamicLayoutAttribute
```

Called when visible indexes change.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;number[]&gt; &#124; undefined | Yes | Callback used to return the list of index numbers of visible subcomponents.<br>Passing undefined will unregister the callback. |

**Return value:**

| Type | Description |
| --- | --- |
| [LazyDynamicLayoutAttribute](arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayoutattribute-c.md) |  |
