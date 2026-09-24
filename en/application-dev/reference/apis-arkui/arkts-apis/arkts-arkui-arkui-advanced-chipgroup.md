# @ohos.arkui.advanced.ChipGroup

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [ChipGroup](arkts-arkui-arkui-advanced-chipgroup-chipgroup-s.md) | The **ChipGroup** component provides chip group capabilities, supporting single-selection or multi-selection modes, customizable styles, icons, and spacing, as well as selected state management and event callbacks. It is suitable for various scenarios such as file categorization, resource filtering, tag selection, and content grouping, helping developers quickly implement selection functionality while delivering a consistent visual and interactive experience. |
| [IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md) | The **ChipGroup** component provides chip group capabilities, supporting single-selection or multi-selection modes, customizable styles, icons, and spacing, as well as selected state management and event callbacks. It is suitable for various scenarios such as file categorization, resource filtering, tag selection, and content grouping, helping developers quickly implement selection functionality while delivering a consistent visual and interactive experience. |

### Interfaces

| Name | Description |
| --- | --- |
| [ChipGroupItemOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupitemoptions-i.md) | Defines the specific attributes of individual chips. |
| [ChipGroupPaddingOptions](arkts-arkui-arkui-advanced-chipgroup-chipgrouppaddingoptions-i.md) | Defines the top and bottom padding of a **ChipGroup** component, which is used to control the overall height of the **ChipGroup**. |
| [ChipGroupSpaceOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupspaceoptions-i.md) | Defines the left and right padding of the chip group, and the spacing between chips. |
| [ChipItemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md) | Defines the common attributes of chips. |
| [IconItemOptions](arkts-arkui-arkui-advanced-chipgroup-iconitemoptions-i.md) | Defines the trailing builder API, which is used to configure the display properties of the trailing icon and its background area. |
| [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md) | Defines the common attributes of icons. |
| [LabelOptions](arkts-arkui-arkui-advanced-chipgroup-labeloptions-i.md) | Defines the text attributes. |
| [SuffixImageIconOptions](arkts-arkui-arkui-advanced-chipgroup-suffiximageiconoptions-i.md) | Defines the configuration options for suffix icons. |
| [SymbolItemOptions](arkts-arkui-arkui-advanced-chipgroup-symbolitemoptions-i.md) | Defines the suffix icon option type for **ChipGroup**. |

## Examples

### Example 1: Implementing a Chip Group Without a Builder-defined Suffix

This example shows how to implement a chip group without a builder-defined suffix.



```TypeScript
import { ChipSize, ChipGroup } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State selectedIndex: Array<number> = [0, 1, 2, 3, 4, 5, 6];

  build() {
    Column() {
      ChipGroup({
        // Set the properties for each chip in the items.
        items: [
          {
            // Replace $r('app.media.icon') with the image resource file you use.
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: 'Chip 1' },
            suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') },
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: 'Chip 2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: 'Chip 3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: 'Chip 4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: 'Chip 5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: 'Chip 6' },
            allowClose: true
          },
        ],
        // Set the style of the chip.
        itemStyle: {
          size: ChipSize.SMALL,
          backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
        },
        selectedIndexes: this.selectedIndex,
        multiple: false,
        chipGroupSpace: { itemSpace: 8, endSpace: 0 },
        chipGroupPadding: { top: 10, bottom: 10 },
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
      })
    }
  }
}
```

### Example 2: Implementing a Chip Group with a Builder-defined Suffix

This example shows how to implement a chip group with a builder-defined suffix.



```TypeScript
import { ChipSize, ChipGroup, IconGroupSuffix } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State selectedIndex: Array<number> = [0, 1, 2, 3, 4, 5, 6];
  @State selectedState: boolean = true;

  @LocalBuilder
  ChipGroupSuffix(): void {
    // Reference IconGroupSuffix to implement the custom effect on the rightmost side of the component.
    IconGroupSuffix({
      items: [{
        icon: { src: $r('sys.media.ohos_ic_public_search_filled'), size: { width: 36, height: 36 } },
        action: () => {
          if (this.selectedState == false) {
            this.selectedIndex = [0, 1, 2, 3, 4, 5, 6];
            this.selectedState = true;
          } else {
            this.selectedIndex = [];
            this.selectedState = false;
          }
        }
      }
      ]
    })
  }

  build() {
    Column() {
      ChipGroup({
        // Set the properties for each chip in the items.
        items: [
          {
            // Replace $r('app.media.icon') with the image resource file you use.
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: 'Chip 1' },
            suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') },
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: 'Chip 2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: 'Chip 3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: 'Chip 4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: 'Chip 5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: 'Chip 6' },
            allowClose: true
          },
        ],
        // Set the style of the chip.
        itemStyle: {
          size: ChipSize.NORMAL,
          backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
        },
        selectedIndexes: this.selectedIndex,
        multiple: true,
        chipGroupSpace: { itemSpace: 8, endSpace: 0 },
        chipGroupPadding: { top: 10, bottom: 10 },
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
        // Customize the builder to display custom content on the rightmost side of the component.
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

### Example 3: Setting the Symbol Icon

This example implements IconGroupSuffix and ChipGroup with SymbolGlyph resources.



```TypeScript
import { ChipSize, ChipGroup, IconGroupSuffix, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State selectedIndex: Array<number> = [0, 1, 2, 3, 4, 5, 6];
  @State selectedState: boolean = true;
  @State prefixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_star'));
  @State prefixModifierActivated: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]);
  @State suffixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_wifi'));
  @State suffixModifierActivated: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')).fontColor([Color.Red]);

  @LocalBuilder
  ChipGroupSuffix(): void {
    // Reference IconGroupSuffix to implement the custom effect on the rightmost side of the component.
    IconGroupSuffix({
      items: [
        new SymbolGlyphModifier($r('sys.symbol.magnifyingglass'))
          .onClick(() => {
            if (this.selectedState == false) {
              this.selectedIndex = [0, 1, 2, 3, 4, 5, 6];
              this.selectedState = true;
            } else {
              this.selectedIndex = [];
              this.selectedState = false;
            }
          })
      ]
    })
  }

  build() {
    Column() {
      ChipGroup({
        // Set the properties for each chip in the items.
        items: [
          {
            prefixSymbol: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
            label: { text: 'Chip 1' },
            suffixSymbol: { normal: this.suffixModifierNormal, activated: this.suffixModifierActivated },
            allowClose: false,
          },
          {
            prefixSymbol: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
            label: { text: 'Chip 2' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: 'Chip 3' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: 'Chip 4' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: 'Chip 5' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: 'Chip 6' },
            allowClose: true,
          },
        ],
        // Set the style of the chip.
        itemStyle: {
          size: ChipSize.NORMAL,
          backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
        },
        selectedIndexes: this.selectedIndex,
        multiple: true,
        chipGroupSpace: { itemSpace: 8, endSpace: 0 },
        chipGroupPadding: { top: 10, bottom: 10 },
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
        // Customize the builder to display custom content on the rightmost side of the component.
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

### Example 4: Implementing the Screen Reader Feature for the Single-Selection Scenario

This example demonstrates how to implement the screen reader feature for a chip group with and without a suffix area in single-selection mode. The content to be read is the value of the accessibilityText attribute.

```TypeScript
import { ChipGroup, IconGroupSuffix, SymbolGlyphModifier } from '@kit.ArkUI';

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
export struct ChipGroupExample2 {
  @LocalBuilder
  suffixBuilder() {
    IconGroupSuffix({
      items: [
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: 'More', // Read "More, button, usage hints."
          accessibilityDescription: 'Usage hints',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: 'More icon touched.'
            });
          }
        },
        {
          symbol: new SymbolGlyphModifier($r('sys.symbol.more')),
          accessibilityText: 'More', // Read "More, button, usage hints."
          accessibilityDescription: 'Usage hints',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: 'More icon touched.'
            });
          }
        },
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: 'More', // If accessibilityLevel is set to no, accessibilityText and accessibilityDescription do not take effect.
          accessibilityDescription: 'Usage hints',
          accessibilityLevel: 'no',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: 'More icon touched.'
            });
          }
        }
      ]
    })
  }

  build() {
    NavDestination() {
      Scroll() {
        Column({ space: 12 }) {
          SectionGroup({ title: 'Available' }) {
            SectionItem({ title: 'Single selection without suffix area' }) {
              ChipGroup({
                items: [
                  {
                    prefixIcon: {
                      src: $r('app.media.startIcon')
                    },
                    label: { text: 'Option 1' },
                    suffixImageIcon: {
                      src: $r('sys.media.save_button_picture'),
                      accessibilityText: 'Save', // Read "Save, button."
                      action: () => {
                        this.getUIContext().getPromptAction().showToast({
                          message: 'Suffix icon touched.'
                        });
                      },
                    }
                  },
                  {
                    label: { text: 'Option 2' },
                    suffixSymbol: {
                      normal: new SymbolGlyphModifier($r('sys.symbol.save')),
                      activated: new SymbolGlyphModifier($r('sys.symbol.save'))
                    },
                    suffixSymbolOptions: {
                      normalAccessibility: {
                        accessibilityText: 'Save' // Read "Save, button."
                      },
                      action: () => {
                        this.getUIContext().getPromptAction().showToast({
                          message: 'Suffix icon touched.'
                        });
                      }
                    }
                  },
                  {
                    label: { text: 'Option 3' },
                    suffixIcon: { src: $r('sys.media.save_button_picture'), }
                  },
                  { label: { text: 'Option 4' } },
                  { label: { text: 'Option 5' } },
                  { label: { text: 'Option 6' } },
                  { label: { text: 'Option 7' } },
                  { label: { text: 'Option 8' } },
                  { label: { text: 'Option 9' } },
                ]
              })
            }

            SectionItem({ title: 'Single selection with suffix area' }) {
              ChipGroup({
                items: [
                  { label: { text: 'Option 1' } },
                  { label: { text: 'Option 2' } },
                  { label: { text: 'Option 3' } },
                  { label: { text: 'Option 4' } },
                  { label: { text: 'Option 5' } },
                  { label: { text: 'Option 6' } },
                  { label: { text: 'Option 7' } },
                  { label: { text: 'Option 8' } },
                  { label: { text: 'Option 9' } },
                ],
                suffix: this.suffixBuilder,
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
    .title('Basic usage')
    .backgroundColor('#F1F3F5')
  }
}
```

### Example 5: Implementing the Screen Reader Feature for the Multi-selection Scenario

This example demonstrates how to implement the screen reader feature for a chip group with and without a suffix area in multi-selection mode. The content to be read is the value of the accessibilityText attribute.

```TypeScript
import { ChipGroup, IconGroupSuffix, SymbolGlyphModifier } from '@kit.ArkUI';

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
export struct ChipGroupExample2 {
  @LocalBuilder
  suffixBuilder() {
    IconGroupSuffix({
      items: [
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: 'More', // Read "More, button, usage hints."
          accessibilityDescription: 'Usage hints',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: 'More icon touched.'
            });
          }
        },
        {
          symbol: new SymbolGlyphModifier($r('sys.symbol.more')),
          accessibilityText: 'More', // Read "More, button, usage hints."
          accessibilityDescription: 'Usage hints',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: 'More icon touched.'
            });
          }
        },
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: 'More', // If accessibilityLevel is set to no, accessibilityText and accessibilityDescription do not take effect.
          accessibilityDescription: 'Usage hints',
          accessibilityLevel: 'no',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: 'More icon touched.'
            });
          }
        }
      ]
    })
  }

  build() {
    NavDestination() {
      Scroll() {
        Column({ space: 12 }) {
          SectionGroup({ title: 'Available' }) {
            SectionItem({ title: 'Multi-selection without suffix area' }) {
              ChipGroup({
                items: [
                  { label: { text: 'Option 1' } },
                  { label: { text: 'Option 2' } },
                  { label: { text: 'Option 3' } },
                  { label: { text: 'Option 4' } },
                  { label: { text: 'Option 5' } },
                  { label: { text: 'Option 6' } },
                  { label: { text: 'Option 7' } },
                  { label: { text: 'Option 8' } },
                  { label: { text: 'Option 9' } },
                ],
                multiple: true
              })
            }

            SectionItem({ title: 'Multi-selection with suffix area' }) {
              ChipGroup({
                items: [
                  { label: { text: 'Option 1' } },
                  { label: { text: 'Option 2' } },
                  { label: { text: 'Option 3' } },
                  { label: { text: 'Option 4' } },
                  { label: { text: 'Option 5' } },
                  { label: { text: 'Option 6' } },
                  { label: { text: 'Option 7' } },
                  { label: { text: 'Option 8' } },
                  { label: { text: 'Option 9' } },
                ],
                suffix: this.suffixBuilder,
                multiple: true,
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
    .title('Basic usage')
    .backgroundColor('#F1F3F5')
  }
}
```

### Example 6: Setting System Material Style

This example implements the system material style by configuring backgroundSystemMaterial and iconBackgroundSystemMaterial, and enables the auto-invert feature so that the text color adapts to the background color.

Starting from API version 26.0.0, the backgroundSystemMaterial attribute is added to [ChipGroup](#chipgroup-1), and the iconBackgroundSystemMaterial attribute is added to [IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md).



```TypeScript
import { ChipGroup, IconGroupSuffix, SymbolGlyphModifier, uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct ChipGroupMaterialExample {
  @State selectedIndexes: Array<number> = [0];

  @LocalBuilder
  suffixBuilder() {
    IconGroupSuffix({
      items: [new SymbolGlyphModifier($r('sys.symbol.magnifyingglass'))
      // Set fontColor to a special system resource value and enable auto-invert.
        .fontColor([$r('sys.color.font_primary')])],
      // Set the system material style of the suffix icon to ULTRA_THIN and enable auto-invert.
      iconBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
        style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
        colorInvert: true
      })
    })
  }

  build() {
    Column({ space: 10 }) {
      ChipGroup({
        items: [
          { label: { text: 'Option 1' } },
          { label: { text: 'Option 2' } },
          { label: { text: 'Option 3' } },
          { label: { text: 'Option 4' } },
          { label: { text: 'Option 5' } },
          { label: { text: 'Option 6' } },
        ],
        selectedIndexes: this.selectedIndexes,
        itemStyle: {
          // Set a transparent background color; otherwise, it will conflict with the system material.
          backgroundColor: Color.Transparent,
          // Set fontColor to a special system resource value to enable auto-invert.
          fontColor: $r('sys.color.font_primary'),
          selectedFontColor: $r('sys.color.font_primary')
        },
        // Set the system material style of ChipGroup to ULTRA_THIN and enable auto-invert.
        backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          colorInvert: true
        }),
        onChange: (activatedChipsIndex: Array<number>) => {
          this.selectedIndexes = activatedChipsIndex;
        },
        suffix: () => {
          this.suffixBuilder()
        }
      })
    }
    .linearGradient({
      angle: 90, // Gradient angle. 90 degrees means from left to right.
      colors: [
        ['#FF9A9E', 0.0], // Start color and position (0.0 indicates the start).
        ['#FECFEF', 0.5], // Middle color and position.
        ['#3B324C', 1.0] // End color and position (1.0 indicates the end).
      ]
    })
    .padding(12)
    .width('100%')
    .height('100%')
  }
}
```

### Example 7: Setting the System Material Style for the Selected State of a Component

This example configures selectedBackgroundSystemMaterial to implement the system material style for the selected state of the component, and enables auto invert color so that the text color adapts to the background color.

Since API version 26.0.0, [ChipGroup](#chipgroup-1) adds the selectedBackgroundSystemMaterial attribute.

```TypeScript
import { ChipGroup, IconGroupSuffix, SymbolGlyphModifier, uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct ChipGroupMaterialExample {
  @State selectedIndexes: Array<number> = [0];

  @LocalBuilder
  suffixBuilder() {
    IconGroupSuffix({
      items: [new SymbolGlyphModifier($r('sys.symbol.magnifyingglass'))
      // Set the fontColor to a special system resource value to enable auto invert color.
        .fontColor([$r('sys.color.font_primary')])],
      // Set the system material style of the suffix icon to ULTRA_THIN and enable auto invert color.
      iconBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
        style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
        colorInvert: true
      })
    })
  }

  build() {
    Column({ space: 10 }) {
      ChipGroup({
        items: [
          { label: { text: 'Option 1' } },
          { label: { text: 'Option 2' } },
          { label: { text: 'Option 3' } },
          { label: { text: 'Option 4' } },
          { label: { text: 'Option 5' } },
          { label: { text: 'Option 6' } },
        ],
        selectedIndexes: this.selectedIndexes,
        itemStyle: {
          // Set a transparent background color; otherwise, it conflicts with the system material.
          backgroundColor: Color.Transparent,
          // Set the fontColor to a special system resource value to enable auto invert color.
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary')
        },
        // Set the system material style of the selected item in ChipGroup to ULTRA_THIN and enable auto invert color.
        selectedBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          materialColor: $r('sys.color.ohos_id_color_emphasize'),
          colorInvert: true
        }),
        // Set the system material style of ChipGroup to ULTRA_THIN and enable auto invert color.
        backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          colorInvert: true
        }),
        onChange: (activatedChipsIndex: Array<number>) => {
          this.selectedIndexes = activatedChipsIndex;
        },
        suffix: () => {
          this.suffixBuilder()
        }
      })
    }
    .linearGradient({
      angle: 90, // Gradient angle. 90 degrees means from left to right.
      colors: [
        ['#FF9A9E', 0.0], // Start color and position (0.0 indicates the start point).
        ['#FECFEF', 0.5], // Middle color and position.
        ['#3B324C', 1.0] // End color and position (1.0 indicates the end point).
      ]
    })
    .padding(12)
    .width('100%')
    .height('100%')
  }
}
```
