# GridObjectSortComponent

网格对象排序组件，用于网格对象的编辑、拖动排序、新增和删除。

> **说明：**
> 
> - 该组件仅可在Stage模型下使用。
> 
> - 如果GridObjectSortComponent设置通用属性和
> 通用事件，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到
> GridObjectSortComponent本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议GridObjectSortComponent设置通用属性和通用事件。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { GridObjectSortComponentType, GridObjectSortComponentItem, GridObjectSortComponentOptions, GridObjectSortComponent } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

Build function of GridObjectSortComponent.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel: () => void
```

取消保存数据的回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSave

```TypeScript
onSave: (select: Array<GridObjectSortComponentItem>, unselect: Array<GridObjectSortComponentItem>) => void
```

保存编辑排序的回调函数，select为编辑后的选中数据，unselect为编辑后的未选中数据。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| select | Array&lt;[GridObjectSortComponentItem](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentitem-i.md)&gt; | 是 |  |
| unselect | Array&lt;[GridObjectSortComponentItem](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentitem-i.md)&gt; | 是 |  |

## dataList

```TypeScript
dataList: Array<GridObjectSortComponentItem>
```

传入的数据，最大长度为50，数据长度超过50，只会取前50条数据。

**类型：** Array&lt;[GridObjectSortComponentItem](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentitem-i.md)&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: GridObjectSortComponentOptions
```

组件配置信息。

**类型：** [GridObjectSortComponentOptions](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentoptions-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
