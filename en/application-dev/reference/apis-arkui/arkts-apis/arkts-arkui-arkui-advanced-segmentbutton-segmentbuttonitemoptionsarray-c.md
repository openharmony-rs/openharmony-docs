# SegmentButtonItemOptionsArray

```TypeScript
declare class SegmentButtonItemOptionsArray extends Array<SegmentButtonItemOptions>
```

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
| elements | [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | Yes | Button information tuple used to initialize the array, containing 2 to 5 button option elements, each defining attributes such as the icon and text of a button. |

## create

```TypeScript
static create(elements: SegmentButtonItemTuple): SegmentButtonItemOptionsArray
```

Creates a **SegmentButtonItemOptionsArray** object. It accepts the same parameters as the constructor and has the same functionality. You can choose either as required.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elements | [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | Yes | Button information tuple used to initialize the array. It contains 2 to 5 button option elements, each defining attributes such as the icon and text of a button. |

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md) | **SegmentButtonItemOptionsArray** object created, which is an array for storing button information. |

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
| items | [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | Yes | Array of button information to be added.<br>Default value: no button information elements are passed in. |

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
| start | number | Yes | Start position of the element to delete, counting from 0. |
| deleteCount | number | Yes | Number of elements to delete. The value range is greater than or equal to 0. If **deleteCount** exceeds the remaining length of the array, all remaining elements starting from the start position are deleted. |
| items | [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md)[] | Yes | Element to be added to the array from start.<br>Default value: If no element is specified, the element is deleted from the array. |

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md)[] | An array containing the removed elements. |

## unshift

```TypeScript
unshift(...items: SegmentButtonItemArray): number
```

Adds new elements to the beginning of the array and returns the length of the array after the addition.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | Yes | Array of button information to add.<br>Default value: no button information elements are passed in. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Length of the array after the elements are added. |
