# ComposeListItem

```TypeScript
export declare struct ComposeListItem
```

列表组件，可自定义列表左侧、中间元素以及右侧显示内容。

**起始版本：** 10

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct ComposeListItem--><!--Device-unnamed-export declare struct ComposeListItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ComposeListItem, ContentItem, IconType, OperateButton, OperateCheck, OperateIcon, OperateItem } from '@kit.ArkUI';
```

## contentItem

```TypeScript
contentItem?: ContentItem
```

定义左侧以及中间元素。

默认不设置或设置为undefined时，左侧和中间元素不显示。

**类型：** [ContentItem](arkts-arkui-arkui-advanced-composelistitem-contentitem-c.md)

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-ComposeListItem-contentItem?: ContentItem--><!--Device-ComposeListItem-contentItem?: ContentItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operateItem

```TypeScript
operateItem?: OperateItem
```

定义右侧元素。

默认不设置或设置为undefined时，右侧元素不显示。

**类型：** [OperateItem](arkts-arkui-arkui-advanced-composelistitem-operateitem-c.md)

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-ComposeListItem-operateItem?: OperateItem--><!--Device-ComposeListItem-operateItem?: OperateItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
