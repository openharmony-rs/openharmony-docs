# ComposeListItemV2

```TypeScript
export declare struct ComposeListItemV2
```

列表项组件，可自定义列表左侧、中间元素以及右侧显示内容。

**起始版本：** 26.0.0

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct ComposeListItemV2--><!--Device-unnamed-export declare struct ComposeListItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## contentItemV2

```TypeScript
contentItemV2?: ContentItemV2
```

定义列表项左侧以及中间元素。

默认不设置或设置为undefined时，不显示左侧和中间元素。

**类型：** [ContentItemV2](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ComposeListItemV2-contentItemV2?: ContentItemV2--><!--Device-ComposeListItemV2-contentItemV2?: ContentItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operateItemV2

```TypeScript
operateItemV2?: OperateItemV2
```

定义列表项右侧元素。

默认不设置或设置为undefined时，不显示右侧元素。

**类型：** [OperateItemV2](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ComposeListItemV2-operateItemV2?: OperateItemV2--><!--Device-ComposeListItemV2-operateItemV2?: OperateItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
