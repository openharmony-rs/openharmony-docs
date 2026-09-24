# @ohos.arkui.advanced.Chip

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [Chip](arkts-arkui-arkui-advanced-chip-chip-f.md) | Creates a **Chip** component. |

### Interfaces

| Name | Description |
| --- | --- |
| [AccessibilityOptions](arkts-arkui-arkui-advanced-chip-accessibilityoptions-i.md) | Defines the accessibility options of the suffix icon. |
| [ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md) | Defines the style and specific style parameters of the **Chip** component. |
| [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md) | Defines the accessibility reading functional attributes and tap event callback of the symbol-type suffix icon. |
| [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md) | Defines the prefix and suffix icon options. |
| [CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md) | Defines the default close icon behavior attributes for the chip, including accessibility attributes. The default value of **accessibilityText** is **"Delete"**. |
| [IconCommonOptions](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md) | Defines the common icon options of the chip. |
| [LabelMarginOptions](arkts-arkui-arkui-advanced-chip-labelmarginoptions-i.md) | Defines the spacing between the text and the left and right icons. |
| [LabelOptions](arkts-arkui-arkui-advanced-chip-labeloptions-i.md) | Defines text configuration options. |
| [LocalizedLabelMarginOptions](arkts-arkui-arkui-advanced-chip-localizedlabelmarginoptions-i.md) | Defines the spacing between the localized text and the left and right icons. |
| [PrefixIconOptions](arkts-arkui-arkui-advanced-chip-prefixiconoptions-i.md) | Defines the prefix icon options. |
| [SuffixIconOptions](arkts-arkui-arkui-advanced-chip-suffixiconoptions-i.md) | Defines the suffix icon options. |

### Enums

| Name | Description |
| --- | --- |
| [AccessibilitySelectedType](arkts-arkui-arkui-advanced-chip-accessibilityselectedtype-e.md) | Defines the selected state types that can be specified for **Chip**. This API is used to control how the accessibility service conveys the component's selected state to users. Different selected state types provide different semantics and user experiences. |
| [ChipSize](arkts-arkui-arkui-advanced-chip-chipsize-e.md) | Enumerates the size types that can be specified for the **Chip** component, such as normal and small. |

## Examples

### Example 1: Setting a Custom Suffix Icon

This example sets a custom suffix icon by configuring suffixIcon.



```TypeScript
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        // Set the suffix icon.
        suffixIcon: {
          // Replace 'app.media.close' with your actual icon resource.
          src: $r('app.media.close'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red
        },
        size: ChipSize.NORMAL,
        allowClose: false,
        enabled: true,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        minFontScale: 0.2,
        maxFontScale: 2,
        padding: {
          start: LengthMetrics.vp(20),
          end: LengthMetrics.vp(20)
        },
        fontSize: 12
      })
    }
  }
}
```

### Example 2: Using the Default Suffix Icon

Set allowClose to true to display the close icon.



```TypeScript
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        size: ChipSize.NORMAL,
        allowClose: true,
        closeOptions: {fontSize: 12},
        enabled: true,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        minFontScale: 0.2,
        maxFontScale: 2,
        padding: {
          start: LengthMetrics.vp(20),
          end: LengthMetrics.vp(20)
        },
        fontSize: 12
      })
    }
  }
}
```

### Example 3: Displaying No Suffix Icon

Set allowClose to false to hide the close icon.



```TypeScript
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        size: ChipSize.SMALL,
        allowClose: false,
        enabled: true,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        minFontScale: 0.2,
        maxFontScale: 2,
        padding: {
          start: LengthMetrics.vp(20),
          end: LengthMetrics.vp(20)
        },
        fontSize: 12
      })
    }
  }
}
```

### Example 4: Implementing the Activated State

This example shows how to implement the activated state for a chip by configuring activated.



```TypeScript
import { Chip, ChipSize } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State isActivated: boolean = false;

  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue,
          activatedFillColor: $r('sys.color.ohos_id_color_text_primary_contrary')
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          activatedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        size: ChipSize.NORMAL,
        allowClose: true,
        enabled: true,
        activated: this.isActivated,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        activatedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        onClose: () => {
          console.info('chip on close');
        },
        onClicked: () => {
          console.info('chip on clicked');
        }
      })
      // Tap "Change Activation Status" to control the activation and deactivation of the operation block.
      Button('Activate/Deactivate')
        .onClick(() => {
          this.isActivated = !this.isActivated;
        })
    }
  }
}
```

### Example 5: Setting the Symbol Icon

This example demonstrates how to set the symbol-type prefix icon of the chip.



```TypeScript
import { Chip, ChipSize, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State isActivated: boolean = false;

  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the symbol-type prefix icon.
        prefixSymbol: {
          normal: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontSize(16).fontColor([Color.Green]),
          activated: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontSize(16).fontColor([Color.Red]),
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          activatedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 },
        },
        size: ChipSize.NORMAL,
        allowClose: true,
        enabled: true,
        activated: this.isActivated,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        activatedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        onClose: () => {
          console.info('chip on close');
        },
        onClicked: () => {
          console.info('chip on clicked');
        }
      })

      Button('Activate/Deactivate')
        .onClick(() => {
          this.isActivated = !this.isActivated;
        })
    }
  }
}
```

### Example 6: Implementing a Mirrored Layout

This example shows how to implement a chip mirrored layout by configuring direction.



```TypeScript
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ChipPage {
  build() {
    Column() {
      Chip({
        direction: Direction.Rtl,
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red,
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          localizedLabelMargin: { start: LengthMetrics.vp(20), end: LengthMetrics.vp(20) },
        },
        // Set the suffix icon.
        suffixIcon: {
          // Replace 'app.media.close' with your actual icon resource.
          src: $r('app.media.close'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red,
        },
        size: ChipSize.NORMAL,
        allowClose: false,
        enabled: true,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button')
      })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

### Example 7: Implementing Accessibility for an Image-Type Suffix Icon

This example demonstrates how to implement the accessibility feature for a chip with an image-type suffix icon. Clicking the suffix icon triggers the announcement of "icon, button, usage hints."

```TypeScript
import { Chip } from '@kit.ArkUI';

@Builder
function defaultFunction(): void {
}

@Component
struct SectionGroup {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = defaultFunction;

  build() {
    Column({ space: 4 }) {
      Text(this.title)
        .fontColor('#FF666666')
        .fontSize(12)
      Column({ space: 8 }) {
        this.content()
      }
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
  }
}

@Component
struct SectionItem {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = defaultFunction;

  build() {
    Column({ space: 12 }) {
      Text(this.title)
      this.content()
    }
    .backgroundColor('#FFFFFFFF')
    .borderRadius(12)
    .padding(12)
    .width('100%')
  }
}

@Entry
@Component
struct ChipExample2 {

  build() {
    NavDestination() {
      Scroll() {
        SectionGroup({ title: 'Suffix icon announcement' }) {
          SectionItem({ title: 'Custom announcement' }) {
            Chip({
              label: { text: 'Chip' },
              suffixIcon: {
                src: $r('sys.media.ohos_ic_public_cut'),
                accessibilityText: 'Icon', // Read "Icon, button, usage hints."
                accessibilityDescription: 'Usage hints',
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'Suffix icon clicked.'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: 'Chip clicked.'
                });
              }
            })
          }
        }
      }
    }
  }
}
```

### Example 8: Implementing Accessibility for a Symbol-Type Suffix Icon

This example demonstrates how to implement the accessibility feature for a chip with a symbol-type suffix icon. Clicking the suffix icon triggers the announcement of "music, button, usage hints."

```TypeScript
import { Chip, SymbolGlyphModifier } from '@kit.ArkUI';

@Builder
function defaultFunction(): void {
}

@Component
struct SectionGroup {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = defaultFunction;

  build() {
    Column({ space: 4 }) {
      Text(this.title)
        .fontColor('#FF666666')
        .fontSize(12)
      Column({ space: 8 }) {
        this.content()
      }
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
  }
}

@Component
struct SectionItem {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = defaultFunction;

  build() {
    Column({ space: 12 }) {
      Text(this.title)
      this.content()
    }
    .backgroundColor('#FFFFFFFF')
    .borderRadius(12)
    .padding(12)
    .width('100%')
  }
}

@Entry
@Component
struct ChipExample2 {

  build() {
    NavDestination() {
      Scroll() {
        SectionGroup({ title: 'Suffix symbol announcement' }) {
          SectionItem({ title: 'activatedAccessibility' }) {
            Chip({
              label: { text: 'Chip' },
              activated: true,
              suffixSymbol: {
                activated: new SymbolGlyphModifier($r('sys.symbol.media_sound'))
                  .fontSize(72),
              },
              suffixSymbolOptions: {
                activatedAccessibility: {
                  accessibilityText: 'Music', // Read "Music, button, usage hints."
                  accessibilityDescription: 'Usage hints'
                },
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'Suffix symbol clicked.'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: 'Chip clicked.'
                });
              }
            })
          }

          SectionItem({ title: 'normalAccessibility' }) {
            Chip({
              label: { text: 'Chip' },
              suffixSymbol: {
                normal: new SymbolGlyphModifier($r('sys.symbol.media_sound'))
                  .fontSize(72),
              },
              suffixSymbolOptions: {
                normalAccessibility: {
                  accessibilityText: 'Music', // Read "Music, button, usage hints."
                  accessibilityDescription: 'Usage hints'
                },
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'Suffix symbol clicked.'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: 'Chip clicked.'
                });
              }
            })
          }
        }
      }
    }
    .padding({
      top: 8,
      bottom: 8,
      left: 16,
      right: 16,
    })
  }
}
```

### Example 9: Implementing Chip Accessibility

This example shows the accessibility property settings of the Chip component, including different accessibilitySelectedType types and various accessibility properties.

```TypeScript
import { AccessibilitySelectedType, Chip, ChipSize } from '@kit.ArkUI';

@Entry
@Component
struct ChipAccessibilityExample {
  @State clickedChipActivated: boolean = false;
  @State checkedChipActivated: boolean = false;
  @State selectedChipActivated: boolean = false;

  build() {
    Column({ space: 20 }) {
      Text('Chip accessibility example').fontSize(20).fontWeight(FontWeight.Bold)

      // Clickable chip - CLICKED type
      Chip({
        label: { text: 'Clickable chip' },
        prefixIcon: {
          src: $r('sys.media.ohos_app_icon'),
          fillColor: Color.Blue
        },
        size: ChipSize.NORMAL,
        accessibilitySelectedType: AccessibilitySelectedType.CLICKED, // Clickable type
        accessibilityDescription: 'This is a clickable chip.', // Overall accessibility description.
        accessibilityLevel: 'yes', // Make sure it can be recognized by accessibility services.
        closeOptions: {
          accessibilityDescription: 'Delete this chip. This operation cannot be undone.' // Provide detailed description for the delete button.
        },
        activated: this.clickedChipActivated,
        onClicked: () => {
          this.clickedChipActivated = !this.clickedChipActivated;
          this.getUIContext().getPromptAction().showToast({ message: 'Clickable chip is clicked.' });
        },
        onClose: () => {
          this.getUIContext().getPromptAction().showToast({ message: 'The close icon of the clickable chip is clicked.' });
        }
      })

      // Checkbox chip - CHECKED type
      Chip({
        label: { text: 'Checkbox chip' },
        prefixIcon: {
          src: $r('sys.media.ohos_app_icon'),
          fillColor: Color.Green
        },
        size: ChipSize.NORMAL,
        accessibilitySelectedType: AccessibilitySelectedType.CHECKED, // Checkbox chip
        accessibilityDescription: 'This is a checkbox chip.', // Overall accessibility description.
        activated: this.checkedChipActivated,
        onClicked: () => {
          this.checkedChipActivated = !this.checkedChipActivated;
          this.getUIContext().getPromptAction().showToast({
            message: this.checkedChipActivated ? 'Checkbox chip is selected.' : 'Checkbox chip is deselected.'
          });
        }
      })

      // Radio chip - SELECTED type
      Chip({
        label: { text: 'Radio chip' },
        prefixIcon: {
          src: $r('sys.media.ohos_app_icon'),
          fillColor: Color.Red
        },
        size: ChipSize.NORMAL,
        accessibilitySelectedType: AccessibilitySelectedType.SELECTED, // Radio type
        accessibilityDescription: 'This is a radio chip.', // Overall accessibility description.
        activated: this.selectedChipActivated,
        onClicked: () => {
          this.selectedChipActivated = !this.selectedChipActivated;
          this.getUIContext().getPromptAction().showToast({
            message: this.selectedChipActivated ? 'Radio chip is selected.' : 'Radio chip is deselected.'
          });
        }
      })

      // Example of setting the accessibility level
      Chip({
        label: { text: 'Accessibility level is set to no.' },
        size: ChipSize.NORMAL,
        accessibilityLevel: 'no', // This chip cannot be recognized by accessibility services.
        closeOptions: {
          accessibilityLevel: 'no'
        },
        backgroundColor: '#CCCCCC',
        onClicked: () => {
          this.getUIContext().getPromptAction().showToast({ message: 'This chip cannot be recognized by accessibility services.' });
        }
      })
    }
    .width('100%')
    .padding(16)
  }
}
```

### Example 10: Setting the System Material Style

This example implements the system material style by configuring backgroundSystemMaterial and activatedBackgroundSystemMaterial, and enables the auto-invert feature to adapt the label text color.

Starting from API version 26.0.0, the backgroundSystemMaterial and activatedBackgroundSystemMaterial attributes are added to [ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md).

```TypeScript
import { Chip, ChipOptions, uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct ChipMaterialExample {
  private chipOptions: ChipOptions = {
    label: {
      text: 'Chip',
      // Set fontColor to a special system resource value to enable automatic color inversion.
      fontColor: $r('sys.color.font_primary'),
      activatedFontColor: $r('sys.color.font_primary')
    },
    allowClose: false,
    // Set the background color in the normal state to transparent. Otherwise, it will conflict with the system material.
    backgroundColor: Color.Transparent,
    // Set the system material style in the normal state to ULTRA_THIN and enable automatic color inversion.
    backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      colorInvert: true
    }),
    // Set the background color in the activated state to transparent. Otherwise, it will conflict with the system material.
    activatedBackgroundColor: Color.Transparent,
    // Set the system material style in the activated state.
    activatedBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN
    })
  }

  build() {
    Column({ space: 50 }) {
      Chip(this.chipOptions)
      Chip(this.chipOptions)
    }
    .linearGradient({
      angle: 0, // Gradient angle. 0 degrees means from left to right.
      colors: [
        ['#FF9A9E', 0.0], // Start color and position (0.0 indicates the start point).
        ['#FECFEF', 0.5], // Middle color and position.
        ['#3B324C', 1.0] // End color and position (1.0 indicates the end point).
      ]
    })
    .padding(12)
    .width('100%')
    .height(150)
  }
}
```
