# ImmersiveOptions

```TypeScript
interface ImmersiveOptions
```

Immersive material parameters.

**Since:** 26.0.0

<!--Device-uiMaterial-interface ImmersiveOptions--><!--Device-uiMaterial-interface ImmersiveOptions-End-->

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

Note: This parameter takes effect on the display effect of all computing power devices that support immersive materials.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveOptions-applyShadow?: boolean--><!--Device-ImmersiveOptions-applyShadow?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorInvert

```TypeScript
colorInvert?: boolean
```

Whether the subtree of the node of the material object automatically adapts the material to the complementary color of the background color.

**false** indicates the material is not automatically adapted to the complementary color of the background color.

**true** indicates that the material is automatically adapted to the complementary color of the background color only when the material layer is thin enough. The materials that can be adapted to the complementary color are defined by the system. Such materials must have at least the **THIN** or **ULTRA_THIN** style, and are related to the strength configuration of the immersive light effect of the application. The thinner the material and the stronger the immersive light effect, the more likely the material meets the requirements for adapting to the complementary color.

The automatic complementary color adaptation capability takes effect only when special resource values (listed in Table 1) are set for some attribute APIs. Such attribute APIs include:

[fontColor](../arkts-components/arkts-arkui-text-comp-attribute.md#fontcolor) of the **Text** component;

[fontColor](../arkts-components/arkts-arkui-button-comp-attribute.md#fontcolor) of the **Button** component;

[fontColor](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#fontcolor) of the **SymbolGlyph** component;

[fillColor](../arkts-components/arkts-arkui-image-comp-attribute.md#fillcolor) of the **Image** component;

[placeholderColor](../arkts-components/arkts-arkui-search-comp-attribute.md#placeholdercolor), [fontColor](../arkts-components/arkts-arkui-search-comp-attribute.md#fontcolor), icon color in [searchIcon](../arkts-components/arkts-arkui-search-comp-attribute.md#searchicon), icon color in [cancelButton](../arkts-components/arkts-arkui-search-comp-attribute.md#cancelbutton), caret color in [caretStyle](../arkts-components/arkts-arkui-search-comp-attribute.md#caretstyle), and button color in [searchButton](../arkts-components/arkts-arkui-search-comp-attribute.md#searchbutton) under the **Search** component;

[BottomTabBarStyle](../arkts-components/arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) used by [tabBar](../arkts-components/arkts-arkui-tabcontent-comp-attribute.md#tabbar) of the **TabContent** component;

[prefixIcon](arkts-arkui-arkui-advanced-chip-prefixiconoptions-i.md), [fillColor](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md) of the **suffixIcon** attribute, and [fontColor](arkts-arkui-arkui-advanced-chip-labeloptions-i.md) of the [label](arkts-arkui-arkui-advanced-chip-labeloptions-i.md) attribute under the **Chip** component;

[fontColor](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md) of [itemStyle](arkts-arkui-arkui-advanced-chipgroup-chipgroup-s.md) of the **ChipGroup** component;

[fontColor](../arkts-components/arkts-arkui-textarea-comp-attribute.md#fontcolor) and [placeholderColor](../arkts-components/arkts-arkui-textarea-comp-attribute.md#placeholdercolor) of the **TextArea** component;

[fontColor](../arkts-components/arkts-arkui-textinput-comp-attribute.md#fontcolor) and [placeholderColor](../arkts-components/arkts-arkui-textinput-comp-attribute.md#placeholdercolor) of the **TextInput** component;

[fontColor](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md#fontcolor) of the **SegmentButton** component;

[fontColor](../arkts-components/arkts-arkui-swiper-comp-digitindicator-c.md#fontcolor) of the **Swiper** component.

When the preceding APIs are used, the text and icon colors are automatically inverted.

Note: This parameter takes effect only for high- and medium-computing devices that support immersive materials.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveOptions-colorInvert?: boolean--><!--Device-ImmersiveOptions-colorInvert?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## interactive

```TypeScript
interactive?: boolean
```

Whether to enable the interactive deformation effect.

The value **true** indicates to enable the interactive deformation effect, and **false** indicates the opposite.

Note: This parameter takes effect on the display effect of all computing power devices that support immersive materials.

Default value: **false**

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveOptions-interactive?: boolean--><!--Device-ImmersiveOptions-interactive?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lightEffect

```TypeScript
lightEffect?: LightEffectOptions | null
```

Parameter for the light sensory interaction feedback effect. When a LightEffectOptions object is passed in, light sensory interaction feedback is enabled; when null is passed in, the light sensory interaction feedback effect is explicitly disabled; when not passed in, the default value is **undefined**, depending on whether the component has a default interactive light effect.

**Note:** This parameter takes effect only on the display effect of high- and medium- computing power devices that support immersive material.

Default value: undefined, meaning the light sensory interaction feedback effect is not set.

**Type:** [LightEffectOptions](arkts-arkui-uimaterial-lighteffectoptions-i.md) &#124; null

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveOptions-lightEffect?: LightEffectOptions | null--><!--Device-ImmersiveOptions-lightEffect?: LightEffectOptions | null-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## materialColor

```TypeScript
materialColor?: ResourceColor
```

Coloring of the material layer. For high- and medium-computing devices that support immersive materials, if this parameter is not specified or is set to **undefined**, no additional pure color effect is mixed. If this parameter is set to a valid color value, this parameter will mix a pure color effect for the material filter. If the color is completely opaque, the material filter effect will be blocked. For low-computing devices that support immersive materials, if this parameter is not specified or is set to **undefined**, the background color effect of the material on the devices takes effect. If this parameter is set to a valid color value, this parameter value is used as the value of the [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor) attribute.

Note: This parameter takes effect on the display effect of all computing power devices that support immersive materials.

Default value: **undefined**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveOptions-materialColor?: ResourceColor--><!--Device-ImmersiveOptions-materialColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ImmersiveStyle
```

Material style. Different styles correspond to different material parameters, which affect the material thickness.

Note: This parameter takes effect only for high- and medium-computing devices that support immersive materials.

Default value: **uiMaterial.ImmersiveStyle.REGULAR**

**Type:** [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md)

**Default:** uiMaterial.ImmersiveStyle.REGULAR

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveOptions-style?: ImmersiveStyle--><!--Device-ImmersiveOptions-style?: ImmersiveStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
