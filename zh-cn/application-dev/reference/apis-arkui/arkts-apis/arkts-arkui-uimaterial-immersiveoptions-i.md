# ImmersiveOptions

沉浸式材质参数。

**起始版本：** 26.0.0

<!--Device-uiMaterial-interface ImmersiveOptions--><!--Device-uiMaterial-interface ImmersiveOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## applyShadow

```TypeScript
applyShadow?: boolean
```

是否添加材质的阴影效果。

当该参数为true时，材质中的阴影效果固定生效，优先于[shadow](../arkts-components/arkts-arkui-common-commonmethod-c.md#shadow-1)通用属性。当该参数为false时，shadow通用属性生效，材质的阴影效果不生效。

**说明**：该参数仅对所有档位的算力设备的显示效果生效。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ImmersiveOptions-applyShadow?: boolean--><!--Device-ImmersiveOptions-applyShadow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorInvert

```TypeScript
colorInvert?: boolean
```

设置了材质对象的节点的子树是否自动适配材质到背景色的反色。

若为false，则不会自动反色。

若为true，则只有材质参数足够薄时才会自动反色。具体能反色的材质由系统定义，材质样式至少为THIN或ULTRA_THIN，且与设置应用的沉浸光感的强弱配置相关。材质越薄、沉浸光感越强，越容易符合反色材质的要求。

自动反色能力仅对部分属性接口设置特殊资源值时生效，生效的属性接口包括：Text组件的[fontColor](TextAttribute#fontColor)，Button组件的[fontColor](ButtonAttribute#fontColor)，SymbolGlyph组件的[fontColor](SymbolGlyphAttribute#fontColor(value: Array<ResourceColor>))，Image组件的[fillColor](ImageAttribute#fillColor(value: ResourceColor))，Search组件的[placeholderColor](SearchAttribute#placeholderColor)、[fontColor](SearchAttribute#fontColor)、[searchIcon](SearchAttribute#searchIcon)中的图标颜色、[cancelButton](SearchAttribute#cancelButton)中的图标颜色、[caretStyle](SearchAttribute#caretStyle)中的光标颜色，TabContent组件的[tabBar](TabContentAttribute#tabBar(options: string | Resource | CustomBuilder | TabBarOptions))属性使用[BottomTabBarStyle](../arkts-components/arkts-arkui-tab-content-bottomtabbarstyle-c.md)样式时其中的文本和图标颜色。

**说明**：该参数仅对高档和中档算力设备的显示效果生效。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ImmersiveOptions-colorInvert?: boolean--><!--Device-ImmersiveOptions-colorInvert?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## interactive

```TypeScript
interactive?: boolean
```

是否为设置材质的组件设置交互形变效果。

**说明**：该参数对所有档位的算力设备的显示效果生效。

默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ImmersiveOptions-interactive?: boolean--><!--Device-ImmersiveOptions-interactive?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lightEffect

```TypeScript
lightEffect?: LightEffectOptions | null
```

是否为设置材质的组件设置光感交互反馈效果。当该参数为null时，禁用光感交互反馈效果。

**说明**：该参数对所有档位的算力设备的显示效果生效。

默认值：undefined，不设置光感交互反馈效果。

**类型：** LightEffectOptions | null

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ImmersiveOptions-lightEffect?: LightEffectOptions | null--><!--Device-ImmersiveOptions-lightEffect?: LightEffectOptions | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## materialColor

```TypeScript
materialColor?: ResourceColor
```

材质层赋色，该参数会为材质滤镜再混合一层纯色效果。该颜色需要带一定的透明度值，不能为纯不透明的颜色，否则会将材质滤镜效果完全遮挡。

**说明**：该参数仅对高档和中档算力设备的显示效果生效。

默认值：Color.Transparent

**类型：** ResourceColor

**默认值：** Color.Transparent

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ImmersiveOptions-materialColor?: ResourceColor--><!--Device-ImmersiveOptions-materialColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ImmersiveStyle
```

材质样式。不同样式对应不同的材质参数，影响材质的厚度。

**说明**：该参数仅对高档和中档算力设备的显示效果生效。

默认值：ImmersiveStyle.REGULAR

**类型：** ImmersiveStyle

**默认值：** uiMaterial.ImmersiveStyle.REGULAR

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ImmersiveOptions-style?: ImmersiveStyle--><!--Device-ImmersiveOptions-style?: ImmersiveStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

