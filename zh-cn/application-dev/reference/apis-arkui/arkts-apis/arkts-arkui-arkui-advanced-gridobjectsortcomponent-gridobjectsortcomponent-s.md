# GridObjectSortComponent

网格对象排序组件，用于网格对象的编辑、拖动排序、新增和删除。

> **说明：**  
>  
> - 该组件仅可在Stage模型下使用。  
>  
> - 如果GridObjectSortComponent设置[通用属性](./@internal/component/ets/common)和  
> [通用事件](./@internal/component/ets/common)，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到  
> GridObjectSortComponent本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议GridObjectSortComponent设置通用属性和通用事件。

**起始版本：** 11

<!--Device-unnamed-export declare struct GridObjectSortComponent--><!--Device-unnamed-export declare struct GridObjectSortComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { GridObjectSortComponentType, GridObjectSortComponentOptions, GridObjectSortComponent, GridObjectSortComponentItem } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

Build function of GridObjectSortComponent.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponent-build(): void--><!--Device-GridObjectSortComponent-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dataList

```TypeScript
dataList: Array<GridObjectSortComponentItem>
```

传入的数据，最大长度为50，数据长度超过50，只会取前50的数据。

**类型：** Array<GridObjectSortComponentItem>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponent-dataList: Array<GridObjectSortComponentItem>--><!--Device-GridObjectSortComponent-dataList: Array<GridObjectSortComponentItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel: () => void
```

取消保存数据的回调。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponent-onCancel: () => void--><!--Device-GridObjectSortComponent-onCancel: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSave

```TypeScript
onSave: (select: Array<GridObjectSortComponentItem>, unselect: Array<GridObjectSortComponentItem>) => void
```

保存编辑排序的回调函数，返回编辑后的数据。

**类型：** (select: Array<GridObjectSortComponentItem>, unselect: Array<GridObjectSortComponentItem>) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponent-onSave: (select: Array<GridObjectSortComponentItem>, unselect: Array<GridObjectSortComponentItem>) => void--><!--Device-GridObjectSortComponent-onSave: (select: Array<GridObjectSortComponentItem>, unselect: Array<GridObjectSortComponentItem>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: GridObjectSortComponentOptions
```

组件配置信息。

**类型：** GridObjectSortComponentOptions

**起始版本：** 11

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponent-options: GridObjectSortComponentOptions--><!--Device-GridObjectSortComponent-options: GridObjectSortComponentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

