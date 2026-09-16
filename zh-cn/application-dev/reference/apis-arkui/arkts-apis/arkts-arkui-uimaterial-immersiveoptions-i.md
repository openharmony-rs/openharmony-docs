# ImmersiveOptions

沉浸式材质参数。

**起始版本：** 26.0.0

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

当该参数为true时，材质中的阴影效果固定生效，优先于shadow通用属性。当该参数为false时，shadow通用属性生效，材质的阴影效果不生效。

**说明：** 该参数对支持沉浸式材质的所有档位的算力设备的显示效果生效。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorInvert

```TypeScript
colorInvert?: boolean
```

设置了材质对象的节点的子树是否自动将颜色适配为材质背景色的反色。

若为false，则不会自动反色。

若为true，则当材质样式满足系统定义的反色条件(需要材质参数足够薄)时才会自动反色。具体能反色的材质由系统定义，材质样式为THIN或ULTRA_THIN，且与设置应用的沉浸光感的强弱配置相关。材质越薄、沉浸光感越强，越容易符合反色材质的要求。

自动反色能力仅对部分属性接口设置特殊资源（见下表1）值时生效，生效的属性接口包括：

Text组件的fontColor，

Button组件的fontColor，

SymbolGlyph组件的fontColor，

Image组件的fillColor，

Search组件的placeholderColor、fontColor，searchIcon中的图标颜色、cancelButton中的图标颜色、caretStyle中的光标颜色，searchButton 中的按钮颜色，

TabContent组件的[tabBar](../arkts-components/arkts-arkui-tabcontent-comp-attribute.md#tabbar)属性使用[BottomTabBarStyle](../arkts-components/arkts-arkui-bottomtabbarstyle-c.md)，

Chip组件的[prefixIcon](arkts-arkui-arkui-advanced-chip-prefixiconoptions-i.md)、suffixIcon属性的[fillColor](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md)，[label](arkts-arkui-arkui-advanced-chip-labeloptions-i.md)属性的[fontColor](arkts-arkui-arkui-advanced-chip-labeloptions-i.md)，

ChipGroup组件的[itemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md)的[fontColor](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md)，

TextArea组件的fontColor、placeholderColor，

TextInput组件的fontColor、placeholderColor，

SegmentButton组件的[fontColor](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md#fontcolor)，

Swiper组件的fontColor，

使用以上接口时，其中的文本和图标颜色会自动反色。

**说明：** 该参数仅对支持沉浸式材质的高算力和中算力设备的显示效果生效。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## interactive

```TypeScript
interactive?: boolean
```

是否启用交互形变效果。交互形变效果是指组件在用户交互时产生形变的视觉反馈效果。

当该参数为true时，启用交互形变效果。当该参数为false时，不启用交互形变效果。

**说明：** 该参数对支持沉浸式材质的所有档位的算力设备的显示效果生效。

默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lightEffect

```TypeScript
lightEffect?: LightEffectOptions | null
```

光感交互反馈效果参数。传入LightEffectOptions对象时启用光感交互反馈；传入null时显式禁用光感交互反馈效果；不传入时默认为undefined，取决于组件是否默认有交互光感效果。

**说明：** 该参数仅对支持沉浸式材质的高算力和中算力设备的显示效果生效。

默认值：undefined，不设置光感交互反馈效果。

**类型：** [LightEffectOptions](arkts-arkui-uimaterial-lighteffectoptions-i.md) &#124; null

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## materialColor

```TypeScript
materialColor?: ResourceColor
```

材质层赋色。对于支持沉浸式材质的高算力和中算力设备，若不设置该参数或该参数为undefined，不额外混合纯色效果；若设置该参数为有效颜色值，该参数会为材质层滤镜再混合一层纯色效果，若该颜色为纯不透明的颜色，会遮挡材质层滤镜效果。对于支持沉浸式材质的低算力设备，若不设置该参数或该参数为undefined，生效低算力设备材质自带的背景色效果；若设置该参数为有效颜色值，该参数作为背景色backgroundColor属性值。

**说明：** 该参数对支持沉浸式材质的所有档位的算力设备的显示效果生效。

默认值：undefined

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**默认值：** Color.Transparent

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ImmersiveStyle
```

材质样式。不同样式对应不同的材质参数，影响材质的厚度。

**说明：** 该参数仅对支持沉浸式材质的高算力和中算力设备的显示效果生效。

默认值：uiMaterial.ImmersiveStyle.REGULAR

**类型：** [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md)

**默认值：** uiMaterial.ImmersiveStyle.REGULAR

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
