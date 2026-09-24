# @ohos.arkui.advanced.FoldSplitContainer

## 导入模块

```TypeScript
import { ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions, PresetSplitRatio, FoldSplitContainer, HoverModeStatus, OnHoverStatusChangeHandler, } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [FoldSplitContainer](arkts-arkui-arkui-advanced-foldsplitcontainer-foldsplitcontainer-s.md) | FoldSplitContainer分栏布局，实现折叠屏二分栏、三分栏在展开态（设备完全展开状态）、悬停态（设备半折叠状态）以及折叠态（设备完全折叠状态）的区域控制。适用于折叠屏应用的响应式布局适配场景，可帮助开发者实现多屏状态下的智能分栏布局，提升用户体验。折叠状态详情可参考[display.FoldStatus](arkts-arkui-display-foldstatus-e.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ExpandedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-expandedregionlayoutoptions-i.md) | 展开态布局信息。 |
| [FoldedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-foldedregionlayoutoptions-i.md) | 折叠态布局信息。 |
| [HoverModeRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermoderegionlayoutoptions-i.md) | 悬停态布局信息。 |
| [HoverModeStatus](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermodestatus-i.md) | 设备或应用的折叠、悬停、旋转、窗口状态信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnHoverStatusChangeHandler](arkts-arkui-onhoverstatuschangehandler-t.md) | 悬停状态变化事件处理器。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ExtraRegionPosition](arkts-arkui-arkui-advanced-foldsplitcontainer-extraregionposition-e.md) | 扩展区域位置信息。 |
| [PresetSplitRatio](arkts-arkui-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md) | 区域比例。 |

## 示例

### 示例1（设置二分栏）

该示例实现了折叠屏二分栏在展开态、悬停态以及折叠态的区域控制。

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
        // 主要区域回调函数
        primary: () => {
          this.privateRegion()
        },
        // 次要区域回调函数
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

### 示例2（设置三分栏）

该示例实现了折叠屏三分栏在展开态、悬停态以及折叠态的区域控制。

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
        // 主要区域回调函数
        primary: () => {
          this.privateRegion()
        },
        // 次要区域回调函数
        secondary: () => {
          this.secondaryRegion()
        },
        // 扩展区域回调函数
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

### 示例3（展示FoldSplitContainer折叠态、悬停态、展开态下的配置行为）

该示例通过[ExpandedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-expandedregionlayoutoptions-i.md)、[HoverModeRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermoderegionlayoutoptions-i.md)和[FoldedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-foldedregionlayoutoptions-i.md)分别配置折叠屏的展开态、悬停态和折叠态布局信息。示例提供交互式配置界面，用户可在各区域实时调整布局参数：主要区域（MajorRegion）用于配置折叠态参数，次要区域（MinorRegion）用于配置悬停态参数，扩展区域（ExtraRegion）用于配置展开态参数。这些区域使用封装的区域组件Region实现，其中RadioOptions为封装的切换单选框组件，SwitchOption为封装的切换开关组件。示意图展示了不同参数配置下的多种布局效果。

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
  // 展开态布局配置
  @State expandedRegionLayoutOptions: ExpandedRegionLayoutOptions = {
    horizontalSplitRatio: PresetSplitRatio.LAYOUT_3V2,
    verticalSplitRatio: PresetSplitRatio.LAYOUT_1V1,
    isExtraRegionPerpendicular: true,
    extraRegionPosition: ExtraRegionPosition.TOP
  };
  // 悬停态布局配置
  @State hoverModeRegionLayoutOptions: HoverModeRegionLayoutOptions = {
    horizontalSplitRatio: PresetSplitRatio.LAYOUT_3V2,
    showExtraRegion: false,
    extraRegionPosition: ExtraRegionPosition.TOP
  };
  // 折叠态布局配置
  @State foldedRegionLayoutOptions: FoldedRegionLayoutOptions = {
    verticalSplitRatio: PresetSplitRatio.LAYOUT_1V1
  };

  @Builder
  // 主要区域自定义组件
  MajorRegion() {
    Region({
      title: "折叠态配置",
      compBackgroundColor: "rgba(255, 0, 0, 0.1)",
    }) {
      Column({ space: 4 }) {
        RadioOption({
          label: "折叠态垂直高度比",
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
              label: "未定义",
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
  // 次要区域自定义组件
  MinorRegion() {
    Region({
      title: "悬停态配置",
      compBackgroundColor: "rgba(0, 255, 0, 0.1)"
    }) {
      Column({ space: 4 }) {
        RadioOption({
          label: "悬停态水平宽度比",
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
              label: "未定义",
              value: undefined,
              onChecked: () => {
                this.hoverModeRegionLayoutOptions.horizontalSplitRatio = undefined
              }
            },
          ]
        })

        SwitchOption({
          label: "悬停态是否显示扩展区",
          value: this.hoverModeRegionLayoutOptions.showExtraRegion,
          onChange: (checked) => {
            this.hoverModeRegionLayoutOptions.showExtraRegion = checked;
          }
        })

        if (this.hoverModeRegionLayoutOptions.showExtraRegion) {
          RadioOption({
            label: "悬停态扩展区位置",
            value: this.hoverModeRegionLayoutOptions.extraRegionPosition,
            options: [
              {
                label: "顶部",
                value: ExtraRegionPosition.TOP,
                onChecked: () => {
                  this.hoverModeRegionLayoutOptions.extraRegionPosition = ExtraRegionPosition.TOP
                }
              },
              {
                label: "底部",
                value: ExtraRegionPosition.BOTTOM,
                onChecked: () => {
                  this.hoverModeRegionLayoutOptions.extraRegionPosition = ExtraRegionPosition.BOTTOM
                }
              },
              {
                label: "未定义",
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
  // 扩展区域自定义组件
  ExtraRegion() {
    Region({
      title: "展开态配置",
      compBackgroundColor: "rgba(0, 0, 255, 0.1)"
    }) {
      Column({ space: 4 }) {
        RadioOption({
          label: "展开态水平宽度比",
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
              label: "未定义",
              value: undefined,
              onChecked: () => {
                this.expandedRegionLayoutOptions.horizontalSplitRatio = undefined
              }
            },
          ]
        })

        RadioOption({
          label: "展开态垂直高度比",
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
              label: "未定义",
              value: undefined,
              onChecked: () => {
                this.expandedRegionLayoutOptions.verticalSplitRatio = undefined
              }
            }
          ]
        })

        SwitchOption({
          label: "展开态扩展区是否上下贯穿",
          value: this.expandedRegionLayoutOptions.isExtraRegionPerpendicular,
          onChange: (checked) => {
            this.expandedRegionLayoutOptions.isExtraRegionPerpendicular = checked;
          }
        })

        if (!this.expandedRegionLayoutOptions.isExtraRegionPerpendicular) {
          RadioOption({
            label: "展开态扩展区位置",
            value: this.expandedRegionLayoutOptions.extraRegionPosition,
            options: [
              {
                label: "顶部",
                value: ExtraRegionPosition.TOP,
                onChecked: () => {
                  this.expandedRegionLayoutOptions.extraRegionPosition = ExtraRegionPosition.TOP
                }
              },
              {
                label: "底部",
                value: ExtraRegionPosition.BOTTOM,
                onChecked: () => {
                  this.expandedRegionLayoutOptions.extraRegionPosition = ExtraRegionPosition.BOTTOM
                }
              },
              {
                label: "未定义",
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
        // 主要区域回调函数
        primary: () => {
          this.MajorRegion()
        },
        // 次要区域回调函数
        secondary: () => {
          this.MinorRegion()
        },
        // 扩展区域回调函数
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
