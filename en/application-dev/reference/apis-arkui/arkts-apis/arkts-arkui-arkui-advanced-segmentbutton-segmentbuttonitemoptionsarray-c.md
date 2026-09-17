# SegmentButtonItemOptionsArray

Represents an array for storing button information.

> **NOTE:** 
> 
> The SegmentButtonItemOptionsArray can save only two to five button information elements.

**Inheritance/Implementation:** SegmentButtonItemOptionsArray extends Array<SegmentButtonItemOptions>

**Since:** 11

**Decorator:** @Observed

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(elements: SegmentButtonItemTuple)
```

Constructor.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elements | [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | Yes | Button information. |

## create

```TypeScript
static create(elements: SegmentButtonItemTuple): SegmentButtonItemOptionsArray
```

Creates a **SegmentButtonItemOptionsArray** object.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elements | [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | Yes | Button information. |

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md) | Created SegmentButtonItemOptionsArray object. |

## pop

```TypeScript
pop(): SegmentButtonItemOptions | undefined
```

Removes the last element from this array and returns that element.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md) &#124; undefined | Element removed from the array. |

## push

```TypeScript
push(...items: SegmentButtonItemArray): number
```

Adds the specified elements to the end of this array and returns the new length of the array.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | Yes | Elements to add to the end of the array.<br>Default value: array with 0 new button information items |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the array after the elements are added. |

## shift

```TypeScript
shift(): SegmentButtonItemOptions | undefined
```

Removes the first element from this array and returns that element.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md) &#124; undefined | Element removed from the array. |

## splice

```TypeScript
splice(start: number, deleteCount: number, ...items: SegmentButtonItemOptions[]): SegmentButtonItemOptions[]
```

Changes the contents of this array by removing the specified number of elements from the specified position and adding new elements in place. This API returns an array containing the removed elements.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Index of the position starting from which elements are to be removed. |
| deleteCount | number | Yes | Number of elements to remove. |
| items | [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md)[] | Yes | Element to be added to the array from start.<br>Default value: If no element is specified, the element is deleted from the array. |

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md)[] | An array containing the removed elements. |

## unshift

```TypeScript
unshift(...items: SegmentButtonItemArray): number
```

Adds an element to the beginning of this array and returns the new length of the array.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | Yes | Elements to add to the beginning of the array.<br>Default value: array with 0 new button information items |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the array after the elements are added. |
