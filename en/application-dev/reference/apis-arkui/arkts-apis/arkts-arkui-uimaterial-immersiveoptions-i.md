# ImmersiveOptions

```TypeScript
interface ImmersiveOptions
```

Immersive material parameters.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## applyShadow

```TypeScript
applyShadow?: boolean
```

Whether to add a shadow effect for a material.

If this parameter is set to **true**, the added shadow effect in the material always takes effect, which takes precedence over the general [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) attribute. If this parameter is set to **false**, only the general shadow attribute takes effect.

Note: This parameter takes effect only for the display effect of devices with all levels of computing power.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorInvert

```TypeScript
colorInvert?: boolean
```

Whether the subtree of the node of the material object automatically adapts the material to the complementary color of the background color.

**false** indicates the material is not automatically adapted to the complementary color of the background color.

**true** indicates that the material is automatically adapted to the complementary color of the background color only when the material layer is thin enough. The materials that can be adapted to the complementary color are defined by the system. Such materials must have at least the **THIN** or **ULTRA_THIN** style, and are related to the strength configuration of the immersive light effect of the application. The thinner the material and the stronger the immersive light effect, the more likely the material meets the requirements for adapting to the complementary color.

The capability of automatically adapting the material to the complementary color takes effect only when special resource values are set for some attribute APIs. The attribute APIs include [fontColor](../arkts-components/arkts-arkui-text-comp-attribute.md#fontcolor) of the **Text** component, [fontColor](../arkts-components/arkts-arkui-button-comp-attribute.md#fontcolor) of the **Button** component, [fontColor](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#fontcolor) of the **SymbolGlyph** component, [fillColor](../arkts-components/arkts-arkui-image-comp-attribute.md#fillcolor) of the **Image** component, icon colors in [placeholderColor](../arkts-components/arkts-arkui-search-comp-attribute.md#placeholdercolor), [fontColor](../arkts-components/arkts-arkui-search-comp-attribute.md#fontcolor), and [searchIcon](../arkts-components/arkts-arkui-search-comp-attribute.md#searchicon) of the **Search** component, icon colors in [cancelButton](../arkts-components/arkts-arkui-search-comp-attribute.md#cancelbutton), caret colors in [caretStyle](../arkts-components/arkts-arkui-search-comp-attribute.md#caretstyle), and text and icon colors in [tabBar](../arkts-components/arkts-arkui-tabcontent-comp-attribute.md#tabbar) of the **TabContent** component when the [BottomTabBarStyle](../arkts-components/arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) style is used.

Note: This parameter takes effect only for the display effect of devices with high- and mid-level computing power.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## interactive

```TypeScript
interactive?: boolean
```

Whether to set an interactive deformation effect for the component with a material set.

Note: This parameter takes effect for the display effect of devices with all levels of computing power.

Default value: **false**

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lightEffect

```TypeScript
lightEffect?: LightEffectOptions | null
```

Whether to set a light sensing interaction feedback effect for the component with a material set. If this parameter is set to null, the light sensing interaction feedback effect is disabled.

Note: This parameter takes effect for the display effect of devices with all levels of computing power.

Default value: **undefined**, indicating that the light sensing interaction feedback effect is not set.

**Type:** [LightEffectOptions](arkts-arkui-uimaterial-lighteffectoptions-i.md) &#124; null

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## materialColor

```TypeScript
materialColor?: ResourceColor
```

Coloring of the material layer. For high- and mid-level computing power devices that support immersive materials, if this parameter is not set or is set to undefined, no additional pure color effect is blended. If this parameter is set to a valid color value, it blends an additional pure color effect into the material layer filter. If the color is completely opaque, the material layer filter effect will be blocked. For low-level computing power devices that support immersive materials, if this parameter is not set or is set to undefined, the built-in background color effect of the material for low-level computing power devices takes effect. If this parameter is set to a valid color value, it is used as the value of the [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor) attribute.

Note: This parameter takes effect for the display effect of devices at all computing power levels that support immersive materials.

Default value: **undefined**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Default:** undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ImmersiveStyle
```

Material style. Different styles correspond to different material parameters, which affect the material thickness.

Note: This parameter takes effect only for the display effect of devices with high- and mid-level computing power.

Default value: **ImmersiveStyle.REGULAR**

**Type:** [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md)

**Default:** uiMaterial.ImmersiveStyle.REGULAR

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
