# ForEach

## ForEach

```TypeScript
ForEach(
    arr: Array<any>,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string,
  )
```

ForEach接口基于数组类型数据来进行循环渲染，需要与容器组件配合使用，且接口返回的组件应当是允许包含在ForEach父容器组件中的子组件。例如，[ListItem]{@link list_item}组件要求ForEach的父容
器组件必须为[List]{@link list}组件或[ListItemGroup]{@link list_item_group}组件。

**起始版本：** 7

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为7.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arr | Array<any> | 是 |  |
| itemGenerator | (item: any, index: number) => void | 是 |  |
| keyGenerator | (item: any, index: number) => string | 否 |  |

## 汇总

