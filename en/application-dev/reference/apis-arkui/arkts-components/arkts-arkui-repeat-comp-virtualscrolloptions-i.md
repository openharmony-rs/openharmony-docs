# VirtualScrollOptions

```TypeScript
interface VirtualScrollOptions
```

Configures the expected total number of data items to be loaded in lazy loading mode, the reuse capability, and the precise data lazy loading capability. Since API version 26.0.0, the memory optimization strategy can be configured.

**Since:** 12

<!--Device-unnamed-interface VirtualScrollOptions--><!--Device-unnamed-interface VirtualScrollOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onLazyLoading

```TypeScript
onLazyLoading?(index: number): void
```

(Optional) Lazily loads data at a specified index. You need to provide a data loading method.

The **onLazyLoading** method must be used in lazy loading scenarios. You can implement a custom method to write data to a specified index in the data source. The processing rules for **onLazyLoading** are as follows:

- Before reading the data corresponding to an index in the data source, the **Repeat** component checks whether  
data exists at the index.  
- If no data exists but the **onLazyLoading** method is implemented, **Repeat** calls this method.  
- In the **onLazyLoading** method, you need to write data to the index specified by **Repeat** in the following  
format: arr[index] =..., where **arr** indicates the array passed to **Repeat**. Array operations except **[]** are not allowed, and elements except the specified index cannot be written. Otherwise, the system throws an exception.  
- After the **onLazyLoading** method is executed, if no data exists in the specified index, the components  
corresponding to the current index and subsequent indexes cannot be loaded.  
- The precise lazy loading capability is an optional configuration item. If **onLazyLoading** is not specified and  
the return value of **totalCount** or **onTotalCount** is greater than the data source length, **Repeat** does not render the missing subsequent data when the list scrolls to the end of the data source.  
- Avoid blocking time-consuming operations (such as synchronous network requests and complex computations) in the  
**onLazyLoading** method. If data loading may take a long time and affect scrolling smoothness, you are advised to first create a placeholder for the data in the **onLazyLoading** method, and then create an asynchronous task to load the data.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-VirtualScrollOptions-onLazyLoading?(index: number): void--><!--Device-VirtualScrollOptions-onLazyLoading?(index: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the data item to be loaded.<br>Value range: natural numbers |

**Examples**

```TypeScript
// Assume that the total number of items is 100, and 3 items are needed for the initial screen rendering.
// The initial array provides the first 3 items (arr = ['No.0', 'No.1', 'No.2']), and lazy loading is enabled.
List() {
  Repeat<string>(this.arr)
    .each((repeatItem: RepeatItem<string>) => { ListItem() { Text(repeatItem.item) }})
    .virtualScroll({ 
      onTotalCount: () => { return 100; },
      onLazyLoading: (index: number) => { this.arr[index] = `No.${index}`; }
    })
}
```

## onTotalCount

```TypeScript
onTotalCount?(): number
```

(Optional) Calculates the expected total number of data items to be loaded. You need to provide a calculation method, and its return value may not be equal to the data source length (length of the array passed to **Repeat**).

Both the return values of [totalCount](arkts-arkui-repeat-comp-virtualscrolloptions-i.md) and **onTotalCount()** indicate the expected total number of data items to be loaded. You can directly set the **totalCount** attribute to specify the expected total number of data items to be loaded, or use **onTotalCount()** to define a custom method for calculating the expected total number of data items to be loaded. At most one of **totalCount** and **onTotalCount()** can be set. If neither is set, the default value is used: the data source length. If both are set, **totalCount** is ignored.

The data loading rules for different return values of **onTotalCount()** are the same as those for **totalCount**. The details are as follows:

- If the return value of **onTotalCount()** is **0**, no data is loaded.  
- If the return value of **onTotalCount()** is in the range (0, Data source length], only data in the index range [0, Return value – 1] is loaded.  
- If the return value of **onTotalCount()** is greater than the data source length, the **Repeat** component  
expects to load data in the index range [0, Return value of onTotalCount() – 1]. The scrollbar style of the container component changes based on the return value of **onTotalCount()**. During the scrolling process of the container component, the application must ensure that subsequent data is requested when the list is about to scroll to the end of the data source. The developer needs to protect against error scenarios of data requests (such as network latency) until the data source is fully loaded. Otherwise, abnormal scrolling effects may occur during list scrolling. It is recommended to use [onLazyLoading](#onlazyloading) to implement data lazy loading.  
- If the return value of **onTotalCount()** is not a natural number, the data source length will be used as the  
return value.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-VirtualScrollOptions-onTotalCount?(): number--><!--Device-VirtualScrollOptions-onTotalCount?(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Expected total number of data items to be loaded.<br>Value range: natural numbers |

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: RepeatMemOptStrategy
```

Memory optimization strategy of **Repeat**. This parameter is set when **Repeat** is created and does not support dynamic modification.

Default value: [DEFAULT](arkts-arkui-repeat-comp-repeatmemoptstrategy-e.md)

**Atomic service API:** Since API version 26.0.0, this API is supported in atomic services.

**Type:** [RepeatMemOptStrategy](arkts-arkui-repeat-comp-repeatmemoptstrategy-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-VirtualScrollOptions-memoryOptimizationStrategy?: RepeatMemOptStrategy--><!--Device-VirtualScrollOptions-memoryOptimizationStrategy?: RepeatMemOptStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reusable

```TypeScript
reusable?: boolean
```

Whether to enable the reuse capability. When the child component of **Repeat** is a custom component decorated by [@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md), the reuse capability of **Repeat** itself takes precedence over that of @ReusableV2. If the developer wants to use the reuse capability of @ReusableV2, it is recommended to disable the reuse capability of **Repeat** itself.

**true**: enables reuse.

**false**: disables reuse.

Default value: **true**

**Atomic service API:** Since API version 18, this API is supported in atomic services.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-VirtualScrollOptions-reusable?: boolean--><!--Device-VirtualScrollOptions-reusable?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## totalCount

```TypeScript
totalCount?: number
```

Total number of expected data items to load, which can be different from the data source length (the length of the array actually passed to Repeat).

Value range: natural number.

At most one of totalCount and onTotalCount() can be set. If neither is set, the default value is used: the data source length. If both are set, totalCount is ignored.

If totalCount is omitted or out of the value range, totalCount takes the value of the data source length, and the list scrolls normally.

If totalCount = 0, no data is loaded.

If 0 &lt; totalCount &lt;= data source length, only the data in the range [0, totalCount - 1] is rendered in the UI.

If totalCount &gt; data source length, **Repeat** renders the data in the range [0, totalCount - 1], and the scrollbar style of the container component changes based on the totalCount value. During scrolling of the container component, the application must ensure that subsequent data is requested when the list is about to scroll to the end of the data source. The developer needs to protect against error scenarios of data requests (such as network latency) until the data source is fully loaded; otherwise, abnormal scrolling effects may occur during list scrolling. It is recommended to use [onLazyLoading](#onlazyloading) to implement data lazy loading.

In addition to the totalCount attribute, the developer can also set a custom method through [onTotalCount](#ontotalcount) to calculate the expected total number of data items to load.

**Atomic service API:** Since API version 12, this API is supported in atomic services.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-VirtualScrollOptions-totalCount?: number--><!--Device-VirtualScrollOptions-totalCount?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
