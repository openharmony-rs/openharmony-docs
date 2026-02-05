# Repeat
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liubihao-->
<!--Designer: @keerecles-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

**Repeat** performs iterative rendering based on array data and is typically used together with scrollable components.

This document provides API parameter descriptions. For details about the component descriptions and usage guidelines, see [Repeat: Reusing Components for Repeated Content Rendering](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

## APIs

### Repeat: \<T\>(arr: Array\<T\>)

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type      | Mandatory| Description     |
| ------ | ---------- | -------- | -------- |
| arr    | Array\<T\> | Yes| Data source, which is an array of the **Array\<T>** type. You can determine the data types.|

**Example**
```ts
// arr is an array of the Array<string> type, which is used as the data source for Repeat.
Repeat<string>(this.arr)
```

### Repeat: \<T\>(arr: RepeatArray\<T\>)<sup>18+</sup>

> **NOTE**
>
> Data sources of the RepeatArray type are supported since API version 18.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type      | Mandatory| Description     |
| ------ | ---------- | -------- | -------- |
| arr    | [RepeatArray\<T\>](#repeatarrayt18) | Yes| Data source, which is an array of the **RepeatArray\<T>** type. You can determine the data types.|

## Properties

In addition to the [drag-and-drop sorting](./ts-universal-attributes-drag-sorting.md) attribute, the following attributes are supported.

### each

each(itemGenerator: (repeatItem: RepeatItem\<T\>) => void)

Component generator. When the return value of [.templateId()](#templateid) does not match any [.template()](#template) type (that is, the current item does not match any defined template style), the data item is processed using **.each()**.

> **NOTE**
>
> - The **each** property is mandatory. If it is omitted, runtime errors will occur.
> - The **itemGenerator** parameter is of the **RepeatItem** type, which combines **item** and **index**. Do not destructure **RepeatItem**.
>
> - This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description|
| ------ | ---------- | -------- | -------- |
| itemGenerator  | (repeatItem: [RepeatItem\<T\>](#repeatitemt)) => void | Yes| Component generator.|

**Example**
```ts
// Create a Text component for each item in the arr array of the Array<string> type.
Repeat<string>(this.arr)
  .each((obj: RepeatItem<string>) => { Text(obj.item) })
```

### key

key(keyGenerator: (item: T, index: number) => string)

Key generator.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description |
| ------ | ---------- | -------- | -------- |
| keyGenerator  | (item: T, index: number) => string | Yes| Key generator.<br>**item**: data item in the **arr** array. It is optional.<br>**index**: index of a data item in the **arr** array. It is optional.|

**Example**
```ts
// Create a Text component for each item in the arr array of the Array<string> type.
// Use the string value as its key.
Repeat<string>(this.arr)
  .each((obj: RepeatItem<string>) => { Text(obj.item) })
  .key((obj: string) => obj)
```

### virtualScroll

virtualScroll(virtualScrollOptions?: VirtualScrollOptions)

Enables virtual scrolling for **Repeat**.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description |
| ------ | ---------- | -------- | -------- |
| virtualScrollOptions  | [VirtualScrollOptions](#virtualscrolloptions)  | No| Virtual scrolling configuration.|

**Example**
```ts
// Create a Text component for each item in the arr array of the Array<string> type.
// Use Repeat in a List container component with virtual scrolling enabled.
List() {
  Repeat<string>(this.arr)
    .each((obj: RepeatItem<string>) => { ListItem() { Text(obj.item) }})
    .virtualScroll()
}
```

### template

template(type: string, itemBuilder: RepeatItemBuilder\<T\>, templateOptions?: TemplateOptions)

Renders the corresponding template child component based on the template type.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description |
| ------ | ---------- | -------- | -------- |
| type | string | Yes| Current template type.|
| itemBuilder  | [RepeatItemBuilder](#repeatitembuildert)\<T\> | Yes| Component generator.|
| templateOptions | [TemplateOptions](#templateoptions) | No| Current template configuration.|

**Example**
```ts
// arr is an array of the Array<string> type.
// Use Repeat in a List container component with virtual scrolling enabled.
// Define a reusable template temp for generating Text components.
List() {
  Repeat<string>(this.arr)
    .each((obj: RepeatItem<string>) => {})
    .virtualScroll()
    .template('temp', (obj: RepeatItem<string>) => { ListItem() { Text(obj.item) }})
}
```

### templateId

templateId(typedFunc: TemplateTypedFunc\<T\>)

Assigns a template type for this data item.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description |
| ------ | ---------- | -------- | -------- |
| typedFunc | [TemplateTypedFunc](#templatetypedfunct)\<T\> | Yes| Function that generates a template type for each data item.|

**Example**
```ts
// arr is an array of the Array<string> type.
// Use Repeat in a List container component with virtual scrolling enabled.
// Define a reusable template temp for generating Text components.
// Use the temp template for all data items.
List() {
  Repeat<string>(this.arr)
    .each((obj: RepeatItem<string>) => {})
    .virtualScroll()
    .template('temp', (obj: RepeatItem<string>) => { ListItem() { Text(obj.item) }})
    .templateId((item: string, index: number) => { return 'temp' })
}
```

## RepeatArray\<T\><sup>18+</sup>

type RepeatArray\<T\> = Array\<T\> | ReadonlyArray\<T\> | Readonly\<Array\<T\>\>

Defines a union type for **Repeat** data source parameters.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|  Type      | Description     |
| -------- | -------- |
| Array\<T\> | Regular array type.|
| ReadonlyArray\<T\> | Read-only array type, where the array object cannot be modified.|
| Readonly\<Array\<T\>> | Read-only array type, where the array object cannot be modified.|

## RepeatItem\<T\>

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type  | Read-Only| Optional| Description                                        |
| ------ | ------ | ---- | ---- | -------------------------------------------- |
| item   | T      | No| No | Each data item in the **arr** array. **T** indicates the data type passed in.|
| index  | number | No| No | Index corresponding to the current data item.                      |

## VirtualScrollOptions

Configures the expected total number of data items to be loaded in lazy loading mode, the reuse capability, and the precise data lazy loading capability.

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type  | Read-Only| Optional| Description                                                        |
| ---------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| totalCount | number | No| Yes | Expected total number of data items to be loaded, which may not be equal to the data source length (length of the array passed to **Repeat**).<br>Value range: natural numbers<br>If **totalCount** is not specified or exceeds the value range, **totalCount** takes the value of the data source length, and the list scrolls normally.<br>If **totalCount** is set to **0**, no data is loaded.<br>If the value of **totalCount** is in the range (0, Data source length], only data in the range [0, **totalCount** – 1] is rendered on the GUI.<br>If the value of **totalCount** is greater than the data source length, the **Repeat** component renders data in the range [0, **totalCount** – 1], and the scrollbar style of the container component changes according to the value of **totalCount**. During the scrolling of the container component, the application must ensure that subsequent data is requested before the list is about to reach the end of the data source. You need to handle error scenarios (such as network delays) for data requests until all data sources are loaded; otherwise, scrolling exceptions may occur during list scrolling. You are advised to use [onLazyLoading](#onlazyloading19) to implement lazy loading.<br>In addition to the **totalCount** attribute, you can also use the [onTotalCount](#ontotalcount19) method to set a custom method to calculate the expected total number of data items to be loaded.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| reusable<sup>18+</sup> | boolean | No| Yes | Whether to enable the reuse feature.<br>**true**: Enable the reuse feature.<br>**false**: Disable the reuse feature.<br>Default value: **true**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

**Example**

```ts
// arr is an array of the Array<string> type. Use Repeat in a List container component with virtual scrolling enabled.
// Set the total number of data items to the length of the data source and enable component reuse.
List() {
  Repeat<string>(this.arr)
    .each((obj: RepeatItem<string>) => { ListItem() { Text(obj.item) }})
    .virtualScroll( { totalCount: this.arr.length, reusable: true } )
}
```

### onTotalCount<sup>19+</sup>

onTotalCount?(): number

(Optional) Calculates the expected total number of data items to be loaded. You need to provide a calculation method, and its return value may not be equal to the data source length (length of the array passed to **Repeat**).

Both the return values of [totalCount](#virtualscrolloptions) and **onTotalCount()** indicate the expected total number of data items to be loaded. You can directly set the **totalCount** attribute to specify the expected total number of data items to be loaded, or use **onTotalCount()** to set a custom method to calculate the expected total number of data items to be loaded. Use either **totalCount** or **onTotalCount**. If neither is set, the default value is used. If both are set, **totalCount** is ignored.

The data loading rules for different return values of **onTotalCount()** are the same as those for **totalCount**. The details are as follows:

- If the return value of **onTotalCount()** is **0**, no data is loaded.
- If the return value of **onTotalCount()** is in the range (0, Data source length], only data in the index range [0, Return value – 1] is loaded.
- If the return value of **onTotalCount()** is greater than the data source length, the **Repeat** component expects to load data in the index range [0, Return value – 1]. The scrollbar style of the container component changes according to the value of **totalCount**. During the scrolling of the container component, the application must ensure that subsequent data is requested before the list is about to reach the end of the data source. You need to handle error scenarios (such as network delays) for data requests until all data sources are loaded; otherwise, scrolling exceptions may occur during list scrolling. You are advised to use [onLazyLoading](#onlazyloading19) to implement lazy loading.
- If the return value of **onTotalCount()** is not a natural number, the data source length will be used as the return value.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

|    Type  | Description|
| ------ | ---------- |
|  number |  Expected total number of data items to be loaded.<br>Value range: natural numbers|

### onLazyLoading<sup>19+</sup>

onLazyLoading?(index: number): void

(Optional) Lazily loads data at a specified index. You need to provide a data loading method.

The **onLazyLoading** method must be used in lazy loading scenarios. You can implement a custom method to write data to a specified index in the data source. The processing rules for **onLazyLoading** are as follows:

- Before reading the data corresponding to an index in the data source, the **Repeat** component checks whether data exists at the index.
- If no data exists but the **onLazyLoading** method is implemented, **Repeat** calls this method.
- In the **onLazyLoading** method, you need to write data to the index specified by **Repeat** in the following format: arr[index] =..., where **arr** indicates the array passed to **Repeat**. Array operations except **[]** are not allowed, and elements except the specified index cannot be written. Otherwise, the system throws an exception.
- After the **onLazyLoading** method is executed, if no data exists in the specified index, the components corresponding to the current index and subsequent indexes cannot be loaded.
- The precise lazy loading capability is optional. If **onLazyLoading** is not specified and the return value of **totalCount** or **onTotalCount** is greater than the data source length, **Repeat** does not render the list scrolling to the bottom.
- Avoid using the **onLazyLoading** method to execute time-consuming operations. If data loading takes a long time, you are advised to create a placeholder for the data in the **onLazyLoading** method and then create an asynchronous task to load the data.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description|
| ------ | ---------- | -------- | -------- |
| index  | number | Yes| Index of the data item to be loaded.<br>Value range: natural numbers|

**Example**

```ts
// Assume that the total number of items is 100, and 3 items are needed for the initial screen rendering.
// The initial array provides the first 3 items (arr = ['No.0', 'No.1', 'No.2']), and lazy loading is enabled.
List() {
  Repeat<string>(this.arr)
    .each((obj: RepeatItem<string>) => { ListItem() { Text(obj.item) }})
    .virtualScroll({ 
      onTotalCount: () => { return 100; },
      onLazyLoading: (index: number) => { this.arr[index] = `No.${index}`; }
    })
}
```

## RepeatItemBuilder\<T\>

type RepeatItemBuilder\<T\> = (repeatItem: RepeatItem\<T\>) => void

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type         | Mandatory     | Description                                   |
| ---------- | ------------- | --------------------------------------- | --------------------------------------- |
| repeatItem | [RepeatItem](#repeatitemt)\<T\> | No| State variable that combines **item** and **index**.|

## TemplateOptions

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type  | Read-Only| Optional| Description                                                        |
| ----------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| cachedCount | number | No| Yes | Maximum number of child component nodes that can be cached in the cache pool of the current template. The value range is [0, +∞). The default value is the sum of the number of nodes in the display area of the container component and the number of nodes in the preloading area. When this sum increases (during the scrolling, when only part of the height of child components is within the display area), the value of **cachedCount** also increases accordingly. Note that the value of **cachedCount** does not decrease.|

When **cachedCount** is set to the maximum number of nodes in the display area of the container component for the current template, **Repeat** achieves maximum reuse efficiency. If there are no nodes of the current template in the container component's display area, the cache list is not released, which increases application memory usage. You are advised to set **cachedCount** to the number of nodes within the container component's display area and adjust the value according to the actual situation. Yet, setting **cachedCount** to less than 2 is not recommended, as this may lead to the frequent node ceation during rapid scrolling and result in performance degradation.

> **NOTE**
> 
> The **.cachedCount()** attribute of the scrollable container component and the **cachedCount** parameter of the **.template()** method of **Repeat** are used to balance performance and memory, but their meanings are different.
> - **.cachedCount()** of the scrollable container component: size of the preloading area outside the display area of the container component. The child component nodes in this area are located in the component tree. The scrollable container component renders nodes in these preloading areas, improving the list scrolling performance.
> - cachedCount in .template(): size of the cache pool for each template in the **Repeat** component. When rendering a new child component, **Repeat** checks whether there are available nodes in the cache pool for the corresponding template. If yes, the nodes are reused. If no, new nodes are created.

**Example**
```ts
// arr is an array of the Array<string> type. Use Repeat in a List container component with virtual scrolling enabled.
// Define a reusable template temp for generating Text components. Use the temp template for all data items.
// Set the maximum cache count for the temp template to 2.
List() {
  Repeat<string>(this.arr)
    .each((obj: RepeatItem<string>) => {})
    .virtualScroll()
    .template('temp', (obj: RepeatItem<string>) => { ListItem() { Text(obj.item) }}, { cachedCount: 2 })
    .templateId((item: string, index: number) => { return 'temp' })
}
```

## TemplateTypedFunc\<T\>

type TemplateTypedFunc\<T\> = (item: T, index: number) => string

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                        |
| ------ | ------ | ---- | -------------------------------------------- |
| item   | T      | No  | Each data item in the **arr** array. **T** indicates the data type passed in.|
| index  | number | No  | Index corresponding to the current data item.                      |
