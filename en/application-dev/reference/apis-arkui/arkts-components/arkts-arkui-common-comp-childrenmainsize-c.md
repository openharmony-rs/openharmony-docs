# ChildrenMainSize

```TypeScript
declare class ChildrenMainSize
```

Provides the size information of the child components of the **List** or **ListItemGroup** component along the main axis. This object only supports one-to-one binding to the **List** or **ListItemGroup** component.

> **NOTE:** 
> 
> - The main axis size information must match the actual main axis size of the child components. When child components' main axis sizes change or components are added or removed, the **ChildrenMainSize** object methods must be invoked to notify the **List** or **ListItemGroup** component.

**Since:** 12

<!--Device-unnamed-declare class ChildrenMainSize--><!--Device-unnamed-declare class ChildrenMainSize-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(childDefaultSize: number)
```

A constructor used to create a **ChildrenMainSize** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ChildrenMainSize-constructor(childDefaultSize: number)--><!--Device-ChildrenMainSize-constructor(childDefaultSize: number)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| childDefaultSize | number | Yes | Default size of the child component along the main axis.<br>Unit: vp <br>**NOTE:** <br>The value must be a finite non-negative number; otherwise, an exception will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## splice

```TypeScript
splice(start: number, deleteCount?: number, childrenSize?: Array<number>): void
```

Performs batch operations to add, delete, or modify the size information of child components along the main axis.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ChildrenMainSize-splice(start: number, deleteCount?: number, childrenSize?: Array<number>): void--><!--Device-ChildrenMainSize-splice(start: number, deleteCount?: number, childrenSize?: Array<number>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Index starting from 0, which indicates the position at which to begin modifying the size information of child components along the main axis.<br>**NOTE:** <br>1. The value must be a finite non-negative number; otherwise, an exception will be thrown. <br>2. Non-integer values are truncated to the nearest integer. <br>3. Values exceeding the maximum index do not take effect. <br>Value range: [0, +∞) |
| deleteCount | number | No | Number of size information entries to be deleted starting from the **start** position.<br>**NOTE:** <br>1. The value must be a finite non-negative number; otherwise, it will be treated as **0**. <br>2. Non-integer values are truncated to the nearest integer. <br>3. The result of (start + deleteCount - 1) can exceed the maximum index, which will delete all size information of child components starting from the **start** position. <br>Default value: **+∞** <br>Value range: [0, +∞) |
| childrenSize | Array&lt;number&gt; | No | Size information of all child components to be inserted, starting from the **start** position.<br>Unit for each value in the array: vp <br>**NOTE:** <br>1. If the values in the array are finite non-negative number, they are considered specified sizes and will not change with the default size. <br>2. If the values in the array are not finite non-negative number, they will be treated as the default size and will change with the default size. <br>The default value is an empty array. <br>Value range: [0, +∞) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## update

```TypeScript
update(index: number, childSize: number): void
```

Updates main size for specified child.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ChildrenMainSize-update(index: number, childSize: number): void--><!--Device-ChildrenMainSize-update(index: number, childSize: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | index of child to be updated. |
| childSize | number | Yes | new section options. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## childDefaultSize

```TypeScript
set childDefaultSize(value: number)
```

Sets the default size of the child component along the main axis.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ChildrenMainSize-set childDefaultSize(value: number)--><!--Device-ChildrenMainSize-set childDefaultSize(value: number)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

```TypeScript
get childDefaultSize(): number
```

Get default size

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ChildrenMainSize-get childDefaultSize(): number--><!--Device-ChildrenMainSize-get childDefaultSize(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
