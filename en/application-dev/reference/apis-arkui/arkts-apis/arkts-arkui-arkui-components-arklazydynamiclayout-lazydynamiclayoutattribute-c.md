# LazyDynamicLayoutAttribute

```TypeScript
export declare class LazyDynamicLayoutAttribute extends CommonMethod<LazyDynamicLayoutAttribute>
```

Defines the LazyDynamicLayout attribute functions.

**Inheritance/Implementation:** LazyDynamicLayoutAttribute extends CommonMethod&lt;LazyDynamicLayoutAttribute&gt;

**Since:** 26.0.0

<!--Device-unnamed-export declare class LazyDynamicLayoutAttribute extends CommonMethod<LazyDynamicLayoutAttribute>--><!--Device-unnamed-export declare class LazyDynamicLayoutAttribute extends CommonMethod<LazyDynamicLayoutAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { LazyDynamicLayout, LazyDynamicLayoutAttribute } from '@kit.ArkUI';
```

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: Callback<number[]> | undefined): LazyDynamicLayoutAttribute
```

Sets the **onVisibleIndexesChange** callback. This callback is triggered when the list of child component indexes in the visible area of **LazyDynamicLayout** changes, and returns the list of child component indexes in the visible area.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyDynamicLayoutAttribute-onVisibleIndexesChange(callback: Callback<int[]> | undefined): LazyDynamicLayoutAttribute--><!--Device-LazyDynamicLayoutAttribute-onVisibleIndexesChange(callback: Callback<int[]> | undefined): LazyDynamicLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;number[]&gt; &#124; undefined | Yes | Callback used to return the list of child component indexes in the visible area. When the input parameter is **undefined**, the listener is canceled. |

**Return value:**

| Type | Description |
| --- | --- |
| [LazyDynamicLayoutAttribute](arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayoutattribute-c.md) |  |
