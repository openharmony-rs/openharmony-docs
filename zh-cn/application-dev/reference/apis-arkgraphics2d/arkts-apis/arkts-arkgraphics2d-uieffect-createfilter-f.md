# createFilter

## createFilter

```TypeScript
function createFilter(): Filter
```

创建Filter实例用于给组件添加多种Filter效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-uiEffect-function createFilter(): Filter--><!--Device-uiEffect-function createFilter(): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回Filter实例，支持添加多种Filter效果。 |

## 示例

```TypeScript
let filter : uiEffect.Filter = uiEffect.createFilter()
```

