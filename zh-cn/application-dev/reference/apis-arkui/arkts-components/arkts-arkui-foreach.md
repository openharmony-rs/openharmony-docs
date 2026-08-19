# ForEach

ForEach接口基于数组类型数据进行循环渲染，可基于数组数据快速生成结构相同、内容不同的子组件，适用于动态列表、批量数据展示等场景，需与容器组件配合使用。 开发者指南见：[ForEach开发者指南](../../../ui/rendering-control/arkts-rendering-control-foreach.md)。

## ForEach

```TypeScript
ForEach(
    arr: Array<any>,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string,
  )
```

该接口需要与容器组件配合使用，且接口返回的组件应当是允许包含在ForEach父容器组件中的子组件。例如，ListItem组件要求ForEach的父容器组件必须为 List组件或ListItemGroup组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ForEachInterface-(    arr: Array<any>,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,  ): ForEachAttribute--><!--Device-ForEachInterface-(    arr: Array<any>,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,  ): ForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arr | Array&lt;any&gt; | 是 | 数据源，为`Array`类型。 <br>设置为`undefined`时ForEach接口不生效。 <br>**说明：** <br>- 可以设置为空数组，此时不会创建子组件。 <br>- 可以设置返回值为数组类型的函数，例如`arr.slice(1, 3)`，但设置的函数不应改变包括数组本身在内的任何状态变量，例如不应使用`Array.splice()`、`Array.sort()`或 `Array.reverse()`这些会改变原数组的函数。 |
| itemGenerator | (item: any, index: number) =&gt; void | 是 | 组件生成函数。 <br>- 为数组中的每个数据项创建对应的组件。 <br>- `item`参数（可选）：`arr`数组中的数据项。 <br>- `index`参数（可选）：`arr`数组中的数据项索引。 <br>- 建议`item`的数据类型与`arr`的数据类型保持一致，否则，当`itemGenerator`中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运行时崩溃。 <br>**说明：** <br>- 组件的类型必须是`ForEach`的父容器所允许的。例如，`ListItem`组件要求`ForEach`的父容器组件必须为`List`组件或`ListItemGroup`组件。 <br>- 组件生成函数不应改变任何组件状态。 |
| keyGenerator | (item: any, index: number) =&gt; string | 否 | 键值生成函数。 <br>- 为数据源`arr`的每个数据项生成唯一且稳定的键值。开发者可以通过该函数自定义键值生成规则，例如当数据项包含唯一标识符时，可使用该标识符作为键值以提升渲染性能；当数据项可能被增删或重排序时，自定义稳定键值可保证 组件正确复用。若键值不唯一或不持久，可能导致组件复用错误或渲染异常。 <br>- `item`参数（可选）：`arr`数组中的数据项。建议`item`的数据类型与`arr`的数据类型保持一致，否则，当`keyGenerator`中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运 行时崩溃。 <br>- `index`参数（可选）：`arr`数组中的数据项索引。 <br>**说明：** <br>- 如果函数缺省，框架默认的键值生成函数为`(item: any, index: number) => { return index + '__' + JSON.stringify(item); }` <br>- 键值生成函数不应改变任何组件状态。 |

## 汇总

