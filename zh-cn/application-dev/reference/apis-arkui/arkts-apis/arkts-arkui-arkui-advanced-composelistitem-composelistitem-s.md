# ComposeListItem

该组件用于展示一系列宽度相同的列表项，适用于展示连续、多行的同类数据组合（如图片与文本）。

> **说明：**  
>  
> - 该组件仅可在Stage模型下使用。  
>  
> - 如果ComposeListItem设置[通用属性](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)和[通用事件](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)，  
> 编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到ComposeListItem本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议  
> ComposeListItem设置通用属性和通用事件。

**起始版本：** 10

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct ComposeListItem--><!--Device-unnamed-export declare struct ComposeListItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OperateCheck, OperateIcon, ComposeListItem, OperateItem, IconType, ContentItem, OperateButton } from '@kit.ArkUI';
```

## contentItem

```TypeScript
contentItem?: ContentItem
```

定义左侧以及中间元素。

**类型：** ContentItem

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeListItem-contentItem?: ContentItem--><!--Device-ComposeListItem-contentItem?: ContentItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operateItem

```TypeScript
operateItem?: OperateItem
```

定义右侧元素。

**类型：** OperateItem

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeListItem-operateItem?: OperateItem--><!--Device-ComposeListItem-operateItem?: OperateItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

