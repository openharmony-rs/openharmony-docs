# Layoutable

```TypeScript
declare interface Layoutable
```

Provides layout information of a child component. The **Layoutable** object is created and passed in by the ArkUI framework when **onPlaceChildren** is called. It contains the measurement result and unique identifier of the child component. Developers set the position of the child component through the **layout** method of **Layoutable**, and obtain the margin information of the child component through the **getMargin**, **getPadding**, and **getBorderWidth** methods for precise layout calculation.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getBorderWidth

```TypeScript
getBorderWidth() : DirectionalEdgesT<number>
```

Obtains the **borderWidth** information of the child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | Border width object of the child component, containing the border width values in four directions. Unit: vp. |

## getMargin

```TypeScript
getMargin() : DirectionalEdgesT<number>
```

Obtains the margin information of the child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | Margin object of the child component, containing the margin values in four directions. Unit: vp. |

## getPadding

```TypeScript
getPadding() : DirectionalEdgesT<number>
```

Obtains the padding information of the child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | Padding object of the child component, containing the padding values in four directions. Unit: vp. |

## layout

```TypeScript
layout(position: Position): void
```

Call this method to set the position information of the child component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | Position | Yes | Absolute position, containing the x and y coordinates (with the origin at the upper left corner of the parent component, the x-axis pointing right as positive and the y-axis pointing down as positive). Unit: vp. |

## measureResult

```TypeScript
measureResult: MeasureResult
```

Size information of the child component after measurement. Unit: vp.

**Type:** [MeasureResult](arkts-arkui-common-comp-measureresult-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId?: number
```

Unique ID assigned by the system to the child component. It is used to uniquely identify the child component for subsequent operations (for example, obtaining the **FrameNode** through **getFrameNodeByUniqueId**). The value range is [0, +∞).

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
