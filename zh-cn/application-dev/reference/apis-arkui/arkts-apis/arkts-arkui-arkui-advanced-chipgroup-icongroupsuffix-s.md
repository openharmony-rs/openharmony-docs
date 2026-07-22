# IconGroupSuffix

> **说明：**  
>  
> 传参SymbolGlyphModifier时，不支持使用symbolEffect修改动效类型和[effectStrategy](SymbolGlyphAttribute#effectStrategy)设置动效。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct IconGroupSuffix--><!--Device-unnamed-export declare struct IconGroupSuffix-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipItemLabelOptions, ChipGroupSpaceOptions, SymbolItemOptions, SuffixImageIconOptions, IconGroupSuffix, IconItemOptions, ChipItemStyle, ChipGroupItemOptions, ChipGroup, IconOptions } from '@kit.ArkUI';
```

## iconBackgroundSystemMaterial

```TypeScript
iconBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor)、[border](../arkts-components/arkts-arkui-commonmethod-c.md#border)、[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow)等视觉属性。

默认值：undefined

值为undefined时，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>
```

尾部区域显示的自定义项数组，支持IconItemOptions（Image图标）、SymbolGlyphModifier（Symbol图标）或SymbolItemOptions（Symbol图标配置）类型。

**类型：** Array&lt;IconItemOptions \| SymbolGlyphModifier \| SymbolItemOptions&gt;

**起始版本：** 12

**装饰器类型：** @Require、@Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IconGroupSuffix-items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>--><!--Device-IconGroupSuffix-items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

