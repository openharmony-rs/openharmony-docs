# SplitLayout

```TypeScript
export declare struct SplitLayout
```

SplitLayout是分栏布局组件，支持自适应布局能力，在不同宽度下显示不同的布局样式。

**起始版本：** 10

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct SplitLayout--><!--Device-unnamed-export declare struct SplitLayout-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SplitLayout } from '@kit.ArkUI';
```

## container

```TypeScript
container: () => void
```

容器内组件，用于在布局下方区域承载自定义组件内容，无返回值。

**起始版本：** 10

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SplitLayout-container: () => void--><!--Device-SplitLayout-container: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mainImage

```TypeScript
mainImage: ResourceStr
```

主图片资源，显示在布局上方区域，支持png、jpg、svg等常见图片格式。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**装饰器类型：** @State

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SplitLayout-mainImage: ResourceStr--><!--Device-SplitLayout-mainImage: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
primaryText: ResourceStr
```

主标题内容，无长度限制。显示在布局的标题区域。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SplitLayout-primaryText: ResourceStr--><!--Device-SplitLayout-primaryText: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
secondaryText?: ResourceStr
```

副标题内容，无长度限制。当需要在标题下方显示副标题时传入，不传入时不显示副标题。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SplitLayout-secondaryText?: ResourceStr--><!--Device-SplitLayout-secondaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tertiaryText

```TypeScript
tertiaryText?: ResourceStr
```

辅助文本，无长度限制。显示在副标题下方区域，当需要显示辅助文本时传入，不传入时不显示辅助文本。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SplitLayout-tertiaryText?: ResourceStr--><!--Device-SplitLayout-tertiaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
