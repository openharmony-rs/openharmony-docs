# VirtualScrollOptions

Configures the expected total number of data items to be loaded in lazy loading mode, the reuse capability, and the precise data lazy loading capability.

**Since:** 12

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
- The precise lazy loading capability is optional. If **onLazyLoading** is not specified and the return value of  
**totalCount** or **onTotalCount** is greater than the data source length, **Repeat** does not render the list scrolling to the bottom.  
- Avoid using the **onLazyLoading** method to execute time-consuming operations. If data loading takes a long time,  
you are advised to create a placeholder for the data in the **onLazyLoading** method and then create an asynchronous task to load the data.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

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

Both the return values of [totalCount](arkts-arkui-virtualscrolloptions-i.md) and **onTotalCount()** indicate the expected total number of data items to be loaded. You can directly set the **totalCount** attribute to specify the expected total number of data items to be loaded, or use **onTotalCount()** to set a custom method to calculate the expected total number of data items to be loaded. Use either **totalCount** or **onTotalCount**. If neither is set, the default value is used. If both are set, **totalCount** is ignored.

The data loading rules for different return values of **onTotalCount()** are the same as those for **totalCount**. The details are as follows:

- If the return value of **onTotalCount()** is **0**, no data is loaded.  
- If the return value of **onTotalCount()** is in the range (0, Data source length], only data in the index range [0, Return value – 1] is loaded.  
- If the return value of **onTotalCount()** is greater than the data source length, the **Repeat** component  
expects to load data in the index range [0, Return value – 1]. The scrollbar style of the container component changes according to the value of **totalCount**. During the scrolling of the container component, the application must ensure that subsequent data is requested before the list is about to reach the end of the data source. You need to handle error scenarios (such as network delays) for data requests until all data sources are loaded; otherwise, scrolling exceptions may occur during list scrolling. You are advised to use [onLazyLoading](#onlazyloading) to implement lazy loading.  
- If the return value of **onTotalCount()** is not a natural number, the data source length will be used as the  
return value.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Expected total number of data items to be loaded.<br>Value range: natural numbers |

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: RepeatMemOptStrategy
```

Memory optimization strategy for Repeat VirtualScroll.

**Type:** [RepeatMemOptStrategy](arkts-arkui-repeatmemoptstrategy-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reusable

```TypeScript
reusable?: boolean
```

Whether to enable the reuse feature.

**true**: Enable the reuse feature.

**false**: Disable the reuse feature.

Default value: **true**.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## totalCount

```TypeScript
totalCount?: number
```

Expected total number of data items to be loaded, which may not be equal to the data source length (length of the array passed to **Repeat**).

Value range: natural numbers

If **totalCount** is not specified or exceeds the value range, **totalCount** takes the value of the data source length, and the list scrolls normally.

If **totalCount** is set to **0**, no data is loaded.

If the value of **totalCount** is in the range (0, Data source length], only data in the range [0, **totalCount** – 1] is rendered on the GUI.

If the value of **totalCount** is greater than the data source length, the **Repeat** component renders data in the range [0, **totalCount** – 1], and the scrollbar style of the container component changes according to the value of **totalCount**. During the scrolling of the container component, the application must ensure that subsequent data is requested before the list is about to reach the end of the data source. You need to handle error scenarios (such as network delays) for data requests until all data sources are loaded; otherwise, scrolling exceptions may occur during list scrolling. You are advised to use [onLazyLoading](#onlazyloading) to implement lazy loading.

In addition to the **totalCount** attribute, you can also use the [onTotalCount](#ontotalcount) method to set a custom method to calculate the expected total number of data items to be loaded.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
