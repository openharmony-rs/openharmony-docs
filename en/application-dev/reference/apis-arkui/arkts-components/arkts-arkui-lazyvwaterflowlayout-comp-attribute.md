# LazyVWaterFlowLayout properties/events

```TypeScript
export declare class LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>
```

Defines the lazy vertical waterflow layout attribute.

@extends LazyWaterFlowLayoutAttribute&lt;LazyVWaterFlowLayoutAttribute&gt;

**Inheritance/Implementation:** LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute, LazyWaterFlowLayoutAttribute } from '@kit.ArkUI';
```

## columnsTemplate

```TypeScript
columnsTemplate(value: string | ItemFillPolicy | undefined)
```

This parameter specifies the number of columns in the current waterflow layout.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) &#124; undefined | Yes | Number of columns in the layout.<br>Default value: '1fr'<br>When the value is a string, it sets the number of columns or the minimum column width of the current &lt;em&gt;LazyVWaterFlowLayout&lt;/em&gt;. For example, &lt;em&gt;columnsTemplate('1fr 1fr 2fr')&lt;/em&gt; divides the &lt;em&gt;LazyVWaterFlowLayout&lt;/em&gt; into 3 columns, splitting the width into 4 equal parts: column 1 takes 1 part, column 2 takes 1 part, and column 3 takes 2 parts. |
