# SplitLayout

上下结构布局介绍了常用的页面布局样式。主要分为上下文本和上下图文两种类型。
> **说明：**
> - 该组件从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。  
>  
> - 该组件仅可在Stage模型下使用。  
>  
> - 如果SplitLayout设置[通用属性](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)和[通用事件](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到SplitLayout本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议SplitLayout设置通用属性和通用事件。

## 子组件

无

**起始版本：** 22

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct SplitLayout--><!--Device-unnamed-export declare struct SplitLayout-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SplitLayout } from '@kit.ArkUI';
```

## container

```TypeScript
@BuilderParam container: () => void
```

容器内组件。

**类型：** () =&gt; void

**起始版本：** 22

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SplitLayout-@BuilderParam container: () => void--><!--Device-SplitLayout-@BuilderParam container: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mainImage

```TypeScript
@State mainImage: ResourceStr
```

传入图片。

**类型：** ResourceStr

**起始版本：** 22

**装饰器类型：** @State

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SplitLayout-@State mainImage: ResourceStr--><!--Device-SplitLayout-@State mainImage: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
@Prop primaryText: ResourceStr
```

标题内容。

**类型：** ResourceStr

**起始版本：** 22

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SplitLayout-@Prop primaryText: ResourceStr--><!--Device-SplitLayout-@Prop primaryText: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
@Prop secondaryText?: ResourceStr
```

副标题内容。当需要在标题下方显示副标题时传入，不传入时取默认值，不显示副标题。

**类型：** ResourceStr

**起始版本：** 22

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SplitLayout-@Prop secondaryText?: ResourceStr--><!--Device-SplitLayout-@Prop secondaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tertiaryText

```TypeScript
@Prop tertiaryText?: ResourceStr
```

辅助文本。当需要显示辅助文本时传入，不传入时取默认值，不显示辅助文本。

**类型：** ResourceStr

**起始版本：** 22

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SplitLayout-@Prop tertiaryText?: ResourceStr--><!--Device-SplitLayout-@Prop tertiaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

