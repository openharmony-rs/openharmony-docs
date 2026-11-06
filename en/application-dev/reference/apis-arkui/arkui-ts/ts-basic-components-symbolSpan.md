# SymbolSpan
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8aa8522c1582655206875d9c89c21656113a2dda translatedAt=2026-09-03T12:16:55.577Z pushedAt=2026-09-16T06:23:26.137Z -->

As a child of the **Text** component, the **SymbolSpan** component displays a preset icon symbol in a span. It supports setting attributes such as the color, size, font weight, rendering strategy, and effect strategy, and is suitable for scenarios where icon symbols need to be embedded in text, such as status indication and feature identification. **SymbolSpan** supports only system preset symbol resources and can inherit the attribute settings of the parent component **Text**.

>  **NOTE**
>
> - This component is supported since API version 11. New APIs of later versions are marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This component can inherit attribute settings from its parent component **Text**. This means that, if an attribute is not set in this component, it takes the value of the attribute (if set) from its parent component.
>
> - The **SymbolSpan** component is not dimmed when dragged.

## Child Components

Not supported

## APIs

SymbolSpan(value: Resource)

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | [Resource](ts-types.md#resource) | Yes | Resource reference of the **SymbolSpan** component, for example, **$r('sys.symbol.ohos_wifi')**. Only system preset symbol resources are supported. Referencing a non-symbol resource will cause display exceptions. |

>  **NOTE**
>
>  The resources referenced in **$r('sys.symbol.ohos_wifi')** are preset in the system. The **SymbolSpan** component supports only the preset symbol resources. Referencing a non-symbol resource will cause display exceptions.

## Attributes

The [universal attributes](ts-component-general-attributes.md) are not supported. Only the following attributes are supported.

### fontColor

fontColor(value: Array&lt;ResourceColor&gt;)

Sets the font color of the **SymbolSpan** component. If this API is not used, the default color varies with [renderingStrategy](#renderingstrategy). Under the single-color rendering strategy (**SINGLE**), the default value is a single color. Under the multi-color rendering strategy (**MULTIPLE_COLOR**) and the layered rendering strategy (**MULTIPLE_OPACITY**), the default value is the preset multi-color configuration of the icon resource. For details, see [SymbolRenderingStrategy](ts-basic-components-symbolGlyph.md#symbolrenderingstrategy11).

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | Array\<[ResourceColor](ts-types.md#resourcecolor)\> | Yes   | Font color of the **SymbolSpan** component. For details about the specific color rendering modes and their descriptions, see [SymbolRenderingStrategy](ts-basic-components-symbolGlyph.md#symbolrenderingstrategy11). |

### fontSize

fontSize(value: number | string | Resource)

Sets the font size of the **SymbolSpan** component. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported. If this API is not used, the default font size is 16 fp.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                         |
| ------ | ------------------------------------------------------------ | ---- | --------------------------------------------- |
| value  | number&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes   | Font size of the **SymbolSpan** component.<br>Value range: [0,&nbsp;+∞)<br>Unit: [fp](ts-pixel-units.md#basic-pixel-units) |

### fontWeight

fontWeight(value: number | FontWeight | string)

Sets the font weight of the **SymbolSpan** component. If this API is not used, the default font weight is **FontWeight.Normal** (normal weight, corresponding to the value **400**).

The **sys.symbol.ohos_lungs** icon does not support font weight setting.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                              |
| ------ | ------------------------------------------------------------ | ---- | -------------------------------------------------- |
| value  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;string | Yes   | Font weight of the **SymbolSpan** component.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. The default value is **400**. A larger value indicates a larger font weight. For the string type, only strings of the number type are supported, for example, **"400"**, and **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**. If the value is too large, truncation may occur in different fonts. If the input value exceeds the value range or does not meet the interval requirements, the default value is used.|

### fontWeight

fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)

Sets the font weight of the **SymbolSpan** component. This API supports setting, through **FontWeightConfigs**, whether to enable variable font weight adjustment and whether to automatically update the font weight based on the device font weight level. If this API is not used, the default font weight is **FontWeight.Normal** (normal weight, corresponding to the value **400**).

The **sys.symbol.ohos_lungs** icon does not support setting **fontWeight**.

**Since**: 26.0.0

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| value | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes | Font weight of the **SymbolSpan** component.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. The default value is **400**. A larger value indicates a larger font weight. For the string type, only strings of the number type are supported, for example, **"400"**, and **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**. If the value is too large, truncation may occur in different fonts.<br>If the input value exceeds the value range, the default value is used. If the input value does not meet the interval requirements, the input value is used when **enableVariableFontWeight** of **fontWeightConfigs** is set to **true**; otherwise, the default value is used. |
| fontWeightConfigs | [FontWeightConfigs](ts-text-common.md#fontweightconfigs24) | No | Font weight configurations. Pass this parameter when variable font weight adjustment needs to be enabled (setting a fine-grained font weight value that is not an integer multiple of 100, such as 220 or 660) or when the font weight needs to be automatically updated based on the device font weight level.<br>Default value: **{ enableVariableFontWeight: false, enableDeviceFontWeightCategory: true }** |

### renderingStrategy

renderingStrategy(value: SymbolRenderingStrategy)

Sets the rendering strategy of the **SymbolSpan** component. If this API is not used, the default rendering strategy is **SymbolRenderingStrategy.SINGLE**.

**SINGLE** indicates single-color rendering, which is suitable for scenarios where icon symbols with a unified color are required. **MULTIPLE_COLOR** indicates multi-color rendering, which is suitable for scenarios where multiple layers of an icon symbol need to be displayed in different colors. **MULTIPLE_OPACITY** indicates layered rendering, which is suitable for scenarios where the layered effect of an icon symbol needs to be displayed.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [SymbolRenderingStrategy](ts-basic-components-symbolGlyph.md#symbolrenderingstrategy11) | Yes   | Rendering strategy of the **SymbolSpan** component.|

The figure below shows the effects of different rendering strategies.

![renderingStrategy](figures/renderingStrategy.png)

### effectStrategy

effectStrategy(value: SymbolEffectStrategy)

Sets the effect strategy of the **SymbolSpan** component. If this API is not used, the default effect strategy is **SymbolEffectStrategy.NONE**.

**NONE** indicates no effect, which is suitable for static display scenarios. **SCALE** indicates an overall scaling effect, which is suitable for scenarios that need to attract user attention, such as button click feedback. **HIERARCHICAL** indicates a hierarchical effect, which is suitable for scenarios where the layered sense of an icon symbol needs to be highlighted.

For the effects of different strategies, see [Example 1: Setting Rendering and Animation Strategies](#example-1-setting-rendering-and-animation-strategies).

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                      |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| value  | [SymbolEffectStrategy](ts-basic-components-symbolGlyph.md#symboleffectstrategy11) | Yes   | Effect strategy of the **SymbolSpan** component. |

### attributeModifier<sup>12+</sup>

attributeModifier(modifier: AttributeModifier\<SymbolSpanAttribute>)

Creates an attribute modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| modifier  | [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<SymbolSpanAttribute> | Yes  | Modifier for dynamically setting attributes on the current component.|

## Events

The [universal events](ts-component-general-events.md) are not supported.

## Example

### Example 1: Setting Rendering and Animation Strategies
This example demonstrates different rendering and effect strategies using [renderingStrategy](#renderingstrategy) and [effectStrategy](#effectstrategy), available since API version 11.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        Column() {
          Text('Light')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Lighter)
              .fontSize(96)
          }
        }

        Column() {
          Text('Normal')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Normal)
              .fontSize(96)
          }
        }

        Column() {
          Text('Bold')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Bold)
              .fontSize(96)
          }
        }
      }

      Row() {
        Column() {
          Text('Monochrome')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_folder_badge_plus'))
              .fontSize(96)
              .renderingStrategy(SymbolRenderingStrategy.SINGLE)
              .fontColor([Color.Black, Color.Green, Color.White])
          }
        }

        Column() {
          Text('Multicolor')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_folder_badge_plus'))
              .fontSize(96)
              .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR)
              .fontColor([Color.Black, Color.Green, Color.White])
          }
        }

        Column() {
          Text('Multilayer')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_folder_badge_plus'))
              .fontSize(96)
              .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_OPACITY)
              .fontColor([Color.Black, Color.Green, Color.White])
          }
        }
      }

      Row() {
        Column() {
          Text('No effect')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_wifi'))
              .fontSize(96)
              .effectStrategy(SymbolEffectStrategy.NONE)
          }
        }

        Column() {
          Text('Overall scale effect')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_wifi'))
              .fontSize(96)
              .effectStrategy(SymbolEffectStrategy.SCALE)
          }
        }

        Column() {
          Text('Hierarchical effect')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_wifi'))
              .fontSize(96)
              .effectStrategy(SymbolEffectStrategy.HIERARCHICAL)
          }
        }
      }
    }
  }
}
```
![SymbolSpan](figures/symbolSpan.gif)

### Example 2: Configuring Dynamic Attributes
This example demonstrates how to create icons of a specified style using the [attributeModifier](#attributemodifier12) attribute, available since API version 12.

```ts
import { SymbolSpanModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State modifier: SymbolSpanModifier =
    new SymbolSpanModifier($r('sys.symbol.ohos_wifi')).fontColor([Color.Blue]).fontSize(100);

  build() {
    Row() {
      Column() {
        Text() {
          SymbolSpan(undefined).attributeModifier(this.modifier)
        }

        Button('Change SymbolSpanModifier')
          .onClick(() => {
            this.modifier = new SymbolSpanModifier($r("sys.symbol.ohos_trash")).fontColor([Color.Red]).fontSize(100);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
![SymbolSpanModifier](figures/symbolSpanModifier.gif)

### Example 3: Setting the Font Weight

This example shows how to use the [fontWeight](#fontweight-1) attribute to display the effects of SymbolSpan with different font weights. The icon symbol in the first line displays the effect of setting the font weight to 220 and 660 after the variable font weight adjustment is enabled. The icon symbol in the second line displays the effect of automatically updating or not updating the font weight after the system font weight is set to bold.

The [fontWeight](#fontweight-1) attribute is added since API version 26.0.0.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        Column() {
          Text('font weight: 220')
          Text() {
            // ohos_trash is the trash can symbol preset by the system.
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(220, { enableVariableFontWeight: true })
              .fontSize(96)
          }
        }
        Column() {
          Text('            ')
        }
        Column() {
          Text('font weight: 660')
          Text() {
            // ohos_trash is the trash can symbol preset by the system.
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(660, { enableVariableFontWeight: true })
              .fontSize(96)
          }
        }
      }
      Row() {
        Text('    ')
      }
      Row() {
        Text('After set system text weight: Bold')
      }
      Row() {
        Column() {
          Text('device category: true')
          Text() {
            // ohos_trash is the trash can symbol preset by the system.
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Normal, { enableDeviceFontWeightCategory: true })
              .fontSize(96)
          }
        }
        Column() {
          Text('    ')
        }
        Column() {
          Text('device category: false')
          Text() {
            // ohos_trash is the trash can symbol preset by the system.
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Normal, { enableDeviceFontWeightCategory: false })
              .fontSize(96)
          }
        }
      }
    }
  }
}
```

![symbolSpanFontWeightConfigs](figures/symbolSpanFontWeightConfigs.png)