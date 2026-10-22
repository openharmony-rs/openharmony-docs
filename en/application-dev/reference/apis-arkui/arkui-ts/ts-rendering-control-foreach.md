# ForEach
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @maorh-->
<!--Designer: @keerecles-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=3cd7a88aa48788902d0133e2f69247ba0fd6a00d translatedAt=2026-09-01T11:38:08.594Z pushedAt=2026-09-02T11:24:50.053Z -->

The **ForEach** API performs loop rendering based on array-type data. It can quickly generate child components with the same structure but different content based on array data. It is applicable to scenarios such as dynamic lists and batch data display, and must be used together with a container component.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

For details about the development, see [ForEach: Rendering Repeated Content](../../../ui/rendering-control/arkts-rendering-control-foreach.md).

## APIs

ForEach(arr: Array\<any\>, itemGenerator: (item: any, index: number) => void, keyGenerator?: (item: any, index: number) => string)

This API must be used together with a container component, and the components returned by the API must be child components that are allowed to be contained in the **ForEach** parent container component. For example, the [ListItem](../../../reference/apis-arkui/arkui-ts/ts-container-listitem.md) component requires that the parent container component of **ForEach** must be a [List](../../../reference/apis-arkui/arkui-ts/ts-container-list.md) component or a [ListItemGroup](../../../reference/apis-arkui/arkui-ts/ts-container-listitemgroup.md) component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type                                   | Mandatory| Description                                                        |
| ------------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| arr           | Array\<any\>                         | required   | Data source, of the `Array` type.<br>If it is set to `undefined`, the **ForEach** API does not take effect.<br>**Note:**<br>- It can be set to an empty array, in which case no child component is created.<br>- It can be set to a function that returns an array, for example, `arr.slice(1, 3)`. However, the function set must not change any state variable, including the array itself. For example, functions that change the original array, such as `Array.splice()`, `Array.sort()`, or `Array.reverse()`, must not be used. |
| itemGenerator | (item: any, index: number) => void   | required   | Component generation function.<br>- Creates a component for each data item in the array.<br>- `item` parameter (optional): data item in the `arr` array.<br>- `index` parameter (optional): index of the data item in the `arr` array.<br>- It is recommended that the data type of `item` be consistent with that of `arr`. Otherwise, if the `itemGenerator` contains operations strongly related to the data type, the child component may fail to render properly or even crash at runtime.<br>**Note:**<br>- The component type must be allowed by the parent container of `ForEach`. For example, the `ListItem` component requires the parent container component of `ForEach` to be a `List` component or a `ListItemGroup` component.<br>- The component generation function must not change any component state. |
| keyGenerator  | (item: any, index: number) => string | optional   | Key generation function.<br>- Generates a unique and stable key value for each data item in the data source `arr`. Developers can customize the key generation rule through this function. For example, when a data item contains a unique identifier, the identifier can be used as the key value to improve rendering performance. When data items may be added, deleted, or reordered, a custom stable key value ensures correct component reuse. If the key value is not unique or persistent, component reuse errors or rendering exceptions may occur.<br>- `item` parameter (optional): data item in the `arr` array. It is recommended that the data type of `item` be consistent with that of `arr`. Otherwise, if the `keyGenerator` contains operations strongly related to the data type, the child component may fail to render properly or even crash at runtime.<br>- `index` parameter (optional): index of the data item in the `arr` array.<br>**Note:**<br>- If this function is omitted, the default key generation function of the framework is `(item: any, index: number) => { return index + '__' + JSON.stringify(item); }`<br>- The key generation function must not change any component state. |

> **NOTE**
>
> - The `itemGenerator` function of `ForEach` can contain [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) conditional rendering logic. In addition, the `ForEach` component can also be used in `if/else` conditional rendering statements.
> - During initial rendering, `ForEach` loads all data in the data source, creates a corresponding component for each data item, and then mounts it to the rendering tree. When the number of data items in the data source is large (for example, hundreds or more) or performance issues such as lag during the first loading of a list occur, you are advised to use the [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) component. For best practices, see [Optimizing Performance Using LazyForEach](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-lazyforeach-optimization).

The data source item type is **any**, and no type consistency check is performed. It is recommended that you maintain consistent type declarations when using **ForEach** (see the following code snippet). Incorrect usage shown in the following code snippet may cause child component rendering failures.

```ts
// Incorrect usage.
arr: Array<Type1 | Type2> = [];

ForEach(this.arr, (item: Type1) => {...}, (item: Type2) => item.toString()); // The item type is inconsistent with the data item type.

// Correct usage.
arr: Array<Type1 | Type2> = [];

ForEach(this.arr, (item: Type1 | Type2) => {...}, (item: Type1 | Type2) => item.toString()); // The item type is consistent with the data item type.
```

## Attributes

The [drag-and-drop sorting](./ts-universal-attributes-drag-sorting.md) attribute is supported.