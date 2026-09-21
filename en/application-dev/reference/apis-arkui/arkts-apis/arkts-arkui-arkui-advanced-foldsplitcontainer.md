# @ohos.arkui.advanced.FoldSplitContainer(Defines FoldSplitContainer component.)

## Modules to Import

```TypeScript
import { ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions, PresetSplitRatio, FoldSplitContainer, HoverModeStatus, OnHoverStatusChangeHandler, } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [FoldSplitContainer](arkts-arkui-arkui-advanced-foldsplitcontainer-foldsplitcontainer-s.md) | The **FoldSplitContainer** component implements split-screen layout, providing region control for two-panel and three -panel layouts on foldable screens in the expanded state (device fully unfolded), hover state (device half-folded), and folded state (device fully folded). It is suitable for responsive layout adaptation scenarios in foldable screen apps, helping developers implement intelligent split-panel layouts across multiple screen states and improving user experience. For details about fold status, see [display.FoldStatus](arkts-arkui-display-foldstatus-e.md). |

### Interfaces

| Name | Description |
| --- | --- |
| [ExpandedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-expandedregionlayoutoptions-i.md) | Defines layout information for the expanded state. |
| [FoldedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-foldedregionlayoutoptions-i.md) | Defines the layout information for the folded state. |
| [HoverModeRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermoderegionlayoutoptions-i.md) | Defines layout information for the hover state. |
| [HoverModeStatus](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermodestatus-i.md) | Provides device or application information covering fold status, hover mode, application rotation, and window status type. |

### Enums

| Name | Description |
| --- | --- |
| [ExtraRegionPosition](arkts-arkui-arkui-advanced-foldsplitcontainer-extraregionposition-e.md) | Provides the position information of the extra region. |
| [PresetSplitRatio](arkts-arkui-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md) | Enumerates the split ratios. |

### Types

| Name | Description |
| --- | --- |
| [OnHoverStatusChangeHandler](arkts-arkui-onhoverstatuschangehandler-t.md) | Defines an event handler for hover state changes. |

## Examples

### Example 1: Setting Up a Two-Panel Layout

This example demonstrates how to control the region for a two-panel layout on a foldable screen across different states: folded, expanded, and hover.

```TypeScript
import { FoldSplitContainer } from '@kit.ArkUI';

@Entry
@Component
struct TwoColumns {
  @Builder
  privateRegion() {
    Text("Primary")
      .backgroundColor('rgba(255, 0, 0, 0.1)')
      .fontSize(28)
      .textAlign(TextAlign.Center)
      .height('100%')
      .width('100%')
  }

  @Builder
  secondaryRegion() {
    Text("Secondary")
      .backgroundColor('rgba(0, 255, 0, 0.1)')
      .fontSize(28)
      .textAlign(TextAlign.Center)
      .height('100%')
      .width('100%')
  }

  build() {
    RelativeContainer() {
      FoldSplitContainer({
        // Callback function for the primary region.
        primary: () => {
          this.privateRegion()
        },
        // Callback function for the secondary region.
        secondary: () => {
          this.secondaryRegion()
        }
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 2: Setting Up a Three-Panel Layout

This example demonstrates how to control the region for a three-panel layout on a foldable screen across different states: folded, expanded, and hover.

```TypeScript
import { FoldSplitContainer } from '@kit.ArkUI';

@Entry
@Component
struct ThreeColumns {
  @Builder
  privateRegion() {
    Text("Primary")
      .backgroundColor('rgba(255, 0, 0, 0.1)')
      .fontSize(28)
      .textAlign(TextAlign.Center)
      .height('100%')
      .width('100%')
  }

  @Builder
  secondaryRegion() {
    Text("Secondary")
      .backgroundColor('rgba(0, 255, 0, 0.1)')
      .fontSize(28)
      .textAlign(TextAlign.Center)
      .height('100%')
      .width('100%')
  }

  @Builder
  extraRegion() {
    Text("Extra")
      .backgroundColor('rgba(0, 0, 255, 0.1)')
      .fontSize(28)
      .textAlign(TextAlign.Center)
      .height('100%')
      .width('100%')
  }

  build() {
    RelativeContainer() {
      FoldSplitContainer({
        // Callback function for the primary region.
        primary: () => {
          this.privateRegion()
        },
        // Callback function for the secondary region.
        secondary: () => {
          this.secondaryRegion()
        },
        // Callback function for the extra region.
        extra: () => {
          this.extraRegion()
        }
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 3: Configuring the Folded, Hover, and Expanded States of FoldSplitContainer

This example configures the folded, hover, and expanded state layout information of the foldable screen through [ExpandedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-expandedregionlayoutoptions-i.md), [HoverModeRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermoderegionlayoutoptions-i.md), and [FoldedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-foldedregionlayoutoptions-i.md), respectively. The example provides an interactive configuration page, allowing users to adjust layout parameters in real time in each region: the primary area (MajorRegion) is used to configure folded state parameters, the secondary area (MinorRegion) is used to configure hover state parameters, and the expanded area (ExtraRegion) is used to configure expanded state parameters. These regions are implemented using the encapsulated region component Region, where RadioOptions is an encapsulated radio button switch component and SwitchOption is an encapsulated toggle switch component. The schematic diagram shows various layout effects under different parameter configurations.

```TypeScript
import { FoldSplitContainer, PresetSplitRatio, ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions } from '@kit.ArkUI';

@Component
struct Region {
  @Prop title: string;
  @BuilderParam content: () => void;
  @Prop compBackgroundColor: string;

  build() {
    Column({ space: 8 }) {
      Text(this.title)
        .fontSize("24fp")
        .fontWeight(600)

      Scroll() {
        this.content()
      }
      .layoutWeight(1)
      .width("100%")
    }
    .backgroundColor(this.compBackgroundColor)
    .width("100%")
    .height("100%")
    .padding(12)
  }
}

const noop = () => {
};

@Component
struct SwitchOption {
  @Prop label: string = ""
  @Prop value: boolean = false
  public onChange: (checked: boolean) => void = noop;

  build() {
    Row() {
      Text(this.label)
      Blank()
      Toggle({ type: ToggleType.Switch, isOn: this.value })
        .onChange((isOn) => {
          this.onChange(isOn);
        })
    }
    .backgroundColor(Color.White)
    .borderRadius(8)
    .padding(8)
    .width("100%")
  }
}

interface RadioOptions {
  label: string;
  value: Object | undefined | null;
  onChecked: () => void;
}

@Component
struct RadioOption {
  @Prop label: string;
  @Prop value: Object | undefined | null;
  @Prop options: Array<RadioOptions>;

  build() {
    Row() {
      Text(this.label)
      Blank()
      Column({ space: 4 }) {
        ForEach(this.options, (option: RadioOptions) => {
          Row() {
            Radio({
              group: this.label,
              value: JSON.stringify(option.value),
            })
              .checked(this.value === option.value)
              .onChange((checked) => {
                if (checked) {
                  option.onChecked();
                }
              })
            Text(option.label)
          }
        })
      }
      .alignItems(HorizontalAlign.Start)
    }
    .alignItems(VerticalAlign.Top)
    .backgroundColor(Color.White)
    .borderRadius(8)
    .padding(8)
    .width("100%")
  }
}

@Entry
@Component
struct Index {
  // Layout configuration in the expanded state.
  @State expandedRegionLayoutOptions: ExpandedRegionLayoutOptions = {
    horizontalSplitRatio: PresetSplitRatio.LAYOUT_3V2,
    verticalSplitRatio: PresetSplitRatio.LAYOUT_1V1,
    isExtraRegionPerpendicular: true,
    extraRegionPosition: ExtraRegionPosition.TOP
  };
  // Layout configuration in the hover state.
  @State hoverModeRegionLayoutOptions: HoverModeRegionLayoutOptions = {
    horizontalSplitRatio: PresetSplitRatio.LAYOUT_3V2,
    showExtraRegion: false,
    extraRegionPosition: ExtraRegionPosition.TOP
  };
  // Layout configuration in the folded state.
  @State foldedRegionLayoutOptions: FoldedRegionLayoutOptions = {
    verticalSplitRatio: PresetSplitRatio.LAYOUT_1V1
  };

  @Builder
  // Custom component in the primary region.
  MajorRegion() {
    Region({
      title: "Folded state settings",
      compBackgroundColor: "rgba(255, 0, 0, 0.1)",
    }) {
      Column({ space: 4 }) {
        RadioOption({
          label: "Height ratio",
          value: this.foldedRegionLayoutOptions.verticalSplitRatio,
          options: [
            {
              label: "1:1",
              value: PresetSplitRatio.LAYOUT_1V1,
              onChecked: () => {
                this.foldedRegionLayoutOptions.verticalSplitRatio = PresetSplitRatio.LAYOUT_1V1
              }
            },
            {
              label: "2:3",
              value: PresetSplitRatio.LAYOUT_2V3,
              onChecked: () => {
                this.foldedRegionLayoutOptions.verticalSplitRatio = PresetSplitRatio.LAYOUT_2V3
              }
            },
            {
              label: "3:2",
              value: PresetSplitRatio.LAYOUT_3V2,
              onChecked: () => {
                this.foldedRegionLayoutOptions.verticalSplitRatio = PresetSplitRatio.LAYOUT_3V2
              }
            },
            {
              label: "Not set",
              value: undefined,
              onChecked: () => {
                this.foldedRegionLayoutOptions.verticalSplitRatio = undefined
              }
            }
          ]
        })
      }
      .constraintSize({ minHeight: "100%" })
    }
  }

  @Builder
  // Custom component in the secondary region.
  MinorRegion() {
    Region({
      title: "Hover state settings",
      compBackgroundColor: "rgba(0, 255, 0, 0.1)"
    }) {
      Column({ space: 4 }) {
        RadioOption({
          label: "Width ratio",
          value: this.hoverModeRegionLayoutOptions.horizontalSplitRatio,
          options: [
            {
              label: "1:1",
              value: PresetSplitRatio.LAYOUT_1V1,
              onChecked: () => {
                this.hoverModeRegionLayoutOptions.horizontalSplitRatio = PresetSplitRatio.LAYOUT_1V1
              }
            },
            {
              label: "2:3",
              value: PresetSplitRatio.LAYOUT_2V3,
              onChecked: () => {
                this.hoverModeRegionLayoutOptions.horizontalSplitRatio = PresetSplitRatio.LAYOUT_2V3
              }
            },
            {
              label: "3:2",
              value: PresetSplitRatio.LAYOUT_3V2,
              onChecked: () => {
                this.hoverModeRegionLayoutOptions.horizontalSplitRatio = PresetSplitRatio.LAYOUT_3V2
              }
            },
            {
              label: "Not set",
              value: undefined,
              onChecked: () => {
                this.hoverModeRegionLayoutOptions.horizontalSplitRatio = undefined
              }
            },
          ]
        })

        SwitchOption({
          label: "Show extra region",
          value: this.hoverModeRegionLayoutOptions.showExtraRegion,
          onChange: (checked) => {
            this.hoverModeRegionLayoutOptions.showExtraRegion = checked;
          }
        })

        if (this.hoverModeRegionLayoutOptions.showExtraRegion) {
          RadioOption({
            label: "Extra region location",
            value: this.hoverModeRegionLayoutOptions.extraRegionPosition,
            options: [
              {
                label: "Top",
                value: ExtraRegionPosition.TOP,
                onChecked: () => {
                  this.hoverModeRegionLayoutOptions.extraRegionPosition = ExtraRegionPosition.TOP
                }
              },
              {
                label: "Bottom",
                value: ExtraRegionPosition.BOTTOM,
                onChecked: () => {
                  this.hoverModeRegionLayoutOptions.extraRegionPosition = ExtraRegionPosition.BOTTOM
                }
              },
              {
                label: "Not set",
                value: undefined,
                onChecked: () => {
                  this.hoverModeRegionLayoutOptions.extraRegionPosition = undefined
                }
              },
            ]
          })
        }
      }
      .constraintSize({ minHeight: "100%" })
    }
  }

  @Builder
  // Custom component in the expanded region.
  ExtraRegion() {
    Region({
      title: "Expanded state settings",
      compBackgroundColor: "rgba(0, 0, 255, 0.1)"
    }) {
      Column({ space: 4 }) {
        RadioOption({
          label: "Width ratio",
          value: this.expandedRegionLayoutOptions.horizontalSplitRatio,
          options: [
            {
              label: "1:1",
              value: PresetSplitRatio.LAYOUT_1V1,
              onChecked: () => {
                this.expandedRegionLayoutOptions.horizontalSplitRatio = PresetSplitRatio.LAYOUT_1V1
              }
            },
            {
              label: "2:3",
              value: PresetSplitRatio.LAYOUT_2V3,
              onChecked: () => {
                this.expandedRegionLayoutOptions.horizontalSplitRatio = PresetSplitRatio.LAYOUT_2V3
              }
            },
            {
              label: "3:2",
              value: PresetSplitRatio.LAYOUT_3V2,
              onChecked: () => {
                this.expandedRegionLayoutOptions.horizontalSplitRatio = PresetSplitRatio.LAYOUT_3V2
              }
            },
            {
              label: "Not set",
              value: undefined,
              onChecked: () => {
                this.expandedRegionLayoutOptions.horizontalSplitRatio = undefined
              }
            },
          ]
        })

        RadioOption({
          label: "Height ratio",
          value: this.expandedRegionLayoutOptions.verticalSplitRatio,
          options: [
            {
              label: "1:1",
              value: PresetSplitRatio.LAYOUT_1V1,
              onChecked: () => {
                this.expandedRegionLayoutOptions.verticalSplitRatio = PresetSplitRatio.LAYOUT_1V1
              }
            },
            {
              label: "2:3",
              value: PresetSplitRatio.LAYOUT_2V3,
              onChecked: () => {
                this.expandedRegionLayoutOptions.verticalSplitRatio = PresetSplitRatio.LAYOUT_2V3
              }
            },
            {
              label: "3:2",
              value: PresetSplitRatio.LAYOUT_3V2,
              onChecked: () => {
                this.expandedRegionLayoutOptions.verticalSplitRatio = PresetSplitRatio.LAYOUT_3V2
              }
            },
            {
              label: "Not set",
              value: undefined,
              onChecked: () => {
                this.expandedRegionLayoutOptions.verticalSplitRatio = undefined
              }
            }
          ]
        })

        SwitchOption({
          label: "Show extra region perpendicularly",
          value: this.expandedRegionLayoutOptions.isExtraRegionPerpendicular,
          onChange: (checked) => {
            this.expandedRegionLayoutOptions.isExtraRegionPerpendicular = checked;
          }
        })

        if (!this.expandedRegionLayoutOptions.isExtraRegionPerpendicular) {
          RadioOption({
            label: "Extra region location",
            value: this.expandedRegionLayoutOptions.extraRegionPosition,
            options: [
              {
                label: "Top",
                value: ExtraRegionPosition.TOP,
                onChecked: () => {
                  this.expandedRegionLayoutOptions.extraRegionPosition = ExtraRegionPosition.TOP
                }
              },
              {
                label: "Bottom",
                value: ExtraRegionPosition.BOTTOM,
                onChecked: () => {
                  this.expandedRegionLayoutOptions.extraRegionPosition = ExtraRegionPosition.BOTTOM
                }
              },
              {
                label: "Not set",
                value: undefined,
                onChecked: () => {
                  this.expandedRegionLayoutOptions.extraRegionPosition = undefined
                }
              },
            ]
          })
        }
      }
      .constraintSize({ minHeight: "100%" })
    }
  }

  build() {
    Column() {
      FoldSplitContainer({
        // Callback function for the primary region.
        primary: () => {
          this.MajorRegion()
        },
        // Callback function for the secondary region.
        secondary: () => {
          this.MinorRegion()
        },
        // Callback function for the extra region.
        extra: () => {
          this.ExtraRegion()
        },
        expandedLayoutOptions: this.expandedRegionLayoutOptions,
        hoverModeLayoutOptions: this.hoverModeRegionLayoutOptions,
        foldedLayoutOptions: this.foldedRegionLayoutOptions,
      })
    }
    .width("100%")
    .height("100%")
  }
}
```
