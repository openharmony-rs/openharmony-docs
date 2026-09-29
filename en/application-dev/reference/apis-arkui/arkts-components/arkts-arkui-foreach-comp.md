# ForEach

The **ForEach** API performs loop rendering based on array-type data. It can quickly generate child components with the same structure but different content based on array data. It is applicable to scenarios such as dynamic lists and batch data display, and must be used together with a container component.

For details about the development, see [ForEach: Rendering Repeated Content](../../../ui/rendering-control/arkts-rendering-control-foreach.md).

## ForEach

```TypeScript
ForEach(
    arr: Array<any>,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string,
  )
```

This API must be used together with a container component, and the components returned by the API must be child components that are allowed to be contained in the **ForEach** parent container component. For example, the [ListItem](arkts-arkui-listitem-comp.md) component requires that the parent container component of **ForEach** must be a [List](arkts-arkui-list-comp.md) component or a [ListItemGroup](arkts-arkui-listitemgroup-comp.md) component.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ForEachInterface-(    arr: Array<any>,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,  ): ForEachAttribute--><!--Device-ForEachInterface-(    arr: Array<any>,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,  ): ForEachAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arr | Array&lt;any&gt; | Yes | Data source, of the `Array` type. <br>If it is set to `undefined`, the **ForEach** API does not take effect. <br>**Note:** <br>- It can be set to an empty array, in which case no child component is created. <br>- It can be set to a function that returns an array, for example, `arr.slice(1, 3)`. However, the function set must not change any state variable, including the array itself. For example, functions that change the original array, such as `Array.splice()`, `Array.sort()`, or `Array.reverse()`, must not be used. |
| itemGenerator | (item: any, index: number) =&gt; void | Yes | Component generation function. <br>- Creates a component for each data item in the array. <br>- `item` parameter (optional): data item in the `arr` array. <br>- `index` parameter (optional): index of the data item in the `arr` array. <br>- It is recommended that the data type of `item` be consistent with that of `arr`. Otherwise, if the `itemGenerator` contains operations strongly related to the data type, the child component may fail to render properly or even crash at runtime. <br>**Note:** <br>- The component type must be allowed by the parent container of `ForEach`. For example, the `ListItem` component requires the parent container component of `ForEach` to be a `List` component or a `ListItemGroup` component. <br>- The component generation function must not change any component state. |
| keyGenerator | (item: any, index: number) =&gt; string | No | Key generation function. <br>- Generates a unique and stable key value for each data item in the data source `arr`. Developers can customize the key generation rule through this function. For example, when a data item contains a unique identifier, the identifier can be used as the key value to improve rendering performance. When data items may be added, deleted, or reordered, a custom stable key value ensures correct component reuse. If the key value is not unique or persistent, component reuse errors or rendering exceptions may occur. <br>- `item` parameter (optional): data item in the `arr` array. It is recommended that the data type of `item` be consistent with that of `arr`. Otherwise, if the `keyGenerator` contains operations strongly related to the data type, the child component may fail to render properly or even crash at runtime. <br>- `index` parameter (optional): index of the data item in the `arr` array. <br>**Note:** <br>- If this function is omitted, the default key generation function of the framework is `(item: any, index: number) =&gt; { return index + '__' + JSON.stringify(item); }` <br>- The key generation function must not change any component state. |

## Summary
