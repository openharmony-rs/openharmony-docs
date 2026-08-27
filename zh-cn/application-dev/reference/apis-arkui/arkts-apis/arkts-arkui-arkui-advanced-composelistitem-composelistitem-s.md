# ComposeListItem

该组件用于展示一系列宽度相同的列表项，适用于展示连续、多行的同类数据组合（如图片与文本）。

> **说明：**
> 
> - 该组件仅可在Stage模型下使用。
> 
> - 如果ComposeListItem设置通用属性和通用事件，
> 编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到ComposeListItem本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议
> ComposeListItem设置通用属性和通用事件。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ComposeListItem, ContentItem, IconType, OperateButton, OperateCheck, OperateIcon, OperateItem } from '@kit.ArkUI';
```

## contentItem

```TypeScript
contentItem?: ContentItem
```

定义左侧以及中间元素。默认不设置或设置为undefined时，左侧和中间元素不显示。

**类型：** [ContentItem](arkts-arkui-arkui-advanced-composelistitem-contentitem-c.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operateItem

```TypeScript
operateItem?: OperateItem
```

定义右侧元素。默认不设置或设置为undefined时，右侧元素不显示。

**类型：** [OperateItem](arkts-arkui-arkui-advanced-composelistitem-operateitem-c.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
