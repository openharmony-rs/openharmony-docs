# SubHeaderV2

子标题，用于列表项或内容项顶部，将该列表或内容划分为一个区块，子标题名称用来概括该区块内容。 该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制子标题的数据和状态，实现更高效的用户界面刷新。 > **说明：** > > - 该组件仅可在Stage模型下使用。 > > - 如果SubHeaderV2设置通用属性和通用事件，编译工具 > 链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到SubHeaderV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议SubHeaderV2设 > 置通用属性和通用事件。

**起始版本：** 18

<!--Device-unnamed-export declare struct SubHeaderV2--><!--Device-unnamed-export declare struct SubHeaderV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SubHeaderV2IconType, SubHeaderV2Title, SubHeaderV2Select, SubHeaderV2, SubHeaderV2OperationType, SubHeaderV2OperationItem, SubHeaderV2OperationItemType } from '@kit.ArkUI';
```

## icon

```TypeScript
@Param
  readonly icon?: SubHeaderV2IconType
```

图标设置项，用于为子标题添加图标标识。 默认值：undefined 当title使用secondaryTitle属性时，设置icon属性才会生效。

**类型：** [SubHeaderV2IconType](arkts-arkui-subheaderv2icontype-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2-@Param  readonly icon?: SubHeaderV2IconType--><!--Device-SubHeaderV2-@Param  readonly icon?: SubHeaderV2IconType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operationItems

```TypeScript
@Param
  readonly operationItems?: SubHeaderV2OperationItem[]
```

操作区的设置项，用于配置子标题右侧的操作按钮。 默认值：undefined 当operationType为ICON_GROUP时，数组最多包含三个元素。

**类型：** [SubHeaderV2OperationItem](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationitem-c.md)[]

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2-@Param  readonly operationItems?: SubHeaderV2OperationItem[]--><!--Device-SubHeaderV2-@Param  readonly operationItems?: SubHeaderV2OperationItem[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operationType

```TypeScript
@Param
  readonly operationType?: SubHeaderV2OperationType
```

操作区元素样式，用于定义子标题右侧操作按钮的显示形式。 默认值：SubHeaderV2OperationType.BUTTON

**类型：** [SubHeaderV2OperationType](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationtype-e.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2-@Param  readonly operationType?: SubHeaderV2OperationType--><!--Device-SubHeaderV2-@Param  readonly operationType?: SubHeaderV2OperationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## select

```TypeScript
@Param
  readonly select?: SubHeaderV2Select
```

下拉选择器的配置项，包含下拉选项内容、选中状态及回调事件。 默认值：undefined

**类型：** [SubHeaderV2Select](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2select-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2-@Param  readonly select?: SubHeaderV2Select--><!--Device-SubHeaderV2-@Param  readonly select?: SubHeaderV2Select-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
@Param
  readonly title?: SubHeaderV2Title
```

标题设置项。 默认值：undefined

**类型：** [SubHeaderV2Title](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2title-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2-@Param  readonly title?: SubHeaderV2Title--><!--Device-SubHeaderV2-@Param  readonly title?: SubHeaderV2Title-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleBuilder

```TypeScript
@BuilderParam
  titleBuilder?: SubHeaderV2TitleBuilder
```

自定义标题区内容。当设置此参数时，title参数将不生效。 默认值：() => void

**类型：** [SubHeaderV2TitleBuilder](arkts-arkui-subheaderv2titlebuilder-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2-@BuilderParam  titleBuilder?: SubHeaderV2TitleBuilder--><!--Device-SubHeaderV2-@BuilderParam  titleBuilder?: SubHeaderV2TitleBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

