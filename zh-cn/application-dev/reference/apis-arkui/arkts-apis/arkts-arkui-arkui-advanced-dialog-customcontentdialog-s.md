# CustomContentDialog

自定义内容区弹出框，同时支持定义操作区按钮样式。
> **说明：**  
>  
> 当弹框高度不足时，触发全局滚动的规格为contentBuilder被压缩，压缩至小于100vp时启动全局滚动。  
>  
> CustomContentDialog内容区的滚动需由开发者自定义，内容区自定义滚动必须配合属性nestedScroll，nestedScroll({ scrollForward:  
> NestedScrollMode.PARALLEL, scrollBackward: NestedScrollMode.PARALLEL })

**起始版本：** 12

<!--Device-unnamed-export declare struct CustomContentDialog--><!--Device-unnamed-export declare struct CustomContentDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialog, SelectDialog, ButtonOptions, PopoverOptions, TipsDialog, PopoverDialog, LoadingDialog, CustomContentDialog, ConfirmDialog } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons?: ButtonOptions[]
```

弹出框操作区按钮，最多支持4个按钮。

**类型：** ButtonOptions[]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialog-buttons?: ButtonOptions[]--><!--Device-CustomContentDialog-buttons?: ButtonOptions[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentAreaPadding

```TypeScript
contentAreaPadding?: Padding
```

弹出框内容区内边距。设置了localizedContentAreaPadding属性时该属性不生效。

**类型：** Padding

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialog-contentAreaPadding?: Padding--><!--Device-CustomContentDialog-contentAreaPadding?: Padding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentBuilder

```TypeScript
@BuilderParam contentBuilder: () => void
```

弹出框内容。

**类型：** () =&gt; void

**起始版本：** 12

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialog-@BuilderParam contentBuilder: () => void--><!--Device-CustomContentDialog-@BuilderParam contentBuilder: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: CustomDialogController
```

弹出框控制器。

**说明：** 未使用@Require装饰，构造时不强制校验参数。

**类型：** CustomDialogController

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialog-controller: CustomDialogController--><!--Device-CustomContentDialog-controller: CustomDialogController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedContentAreaPadding

```TypeScript
localizedContentAreaPadding?: LocalizedPadding
```

弹出框内容区内边距。

**类型：** LocalizedPadding

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialog-localizedContentAreaPadding?: LocalizedPadding--><!--Device-CustomContentDialog-localizedContentAreaPadding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

弹出框标题。

默认不设置或设置为undefined，弹出框标题不显示。

**说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialog-primaryTitle?: ResourceStr--><!--Device-CustomContentDialog-primaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

弹出框辅助文本。

默认不设置或设置为undefined，弹出框辅助文本不显示。

**说明：** 辅助文本超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialog-secondaryTitle?: ResourceStr--><!--Device-CustomContentDialog-secondaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## theme

```TypeScript
theme?: Theme | CustomTheme
```

主题信息，可以是CustomTheme或从onWillApplyTheme中获取的Theme实例。

**类型：** Theme \| CustomTheme

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialog-theme?: Theme | CustomTheme--><!--Device-CustomContentDialog-theme?: Theme | CustomTheme-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## themeColorMode

```TypeScript
themeColorMode?: ThemeColorMode
```

自定义弹出框深浅色模式。

默认值：ThemeColorMode.SYSTEM

**类型：** ThemeColorMode

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialog-themeColorMode?: ThemeColorMode--><!--Device-CustomContentDialog-themeColorMode?: ThemeColorMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

