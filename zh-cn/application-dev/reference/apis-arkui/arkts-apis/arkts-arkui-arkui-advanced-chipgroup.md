# @ohos.arkui.advanced.ChipGroup

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ChipGroup](arkts-arkui-arkui-advanced-chipgroup-chipgroup-s.md) | ChipGroup组件提供操作块群组能力，支持单选或多选模式，可自定义样式、图标和间距，支持选中状态管理和事件回调。适用于文件分类、资源筛选、标签选择、内容分组等多种场景，帮助开发者快速实现选择功能，提供统一的视觉和交互体验。 |
| [IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md) | ChipGroup组件提供操作块群组能力，支持单选或多选模式，可自定义样式、图标和间距，支持选中状态管理和事件回调。适用于文件分类、资源筛选、标签选择、内容分组等多种场景，帮助开发者快速实现选择功能，提供统一的视觉和交互体验。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChipGroupItemOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupitemoptions-i.md) | ChipGroupItemOptions定义每个Chip的非通用属性。 |
| [ChipGroupPaddingOptions](arkts-arkui-arkui-advanced-chipgroup-chipgrouppaddingoptions-i.md) | ChipGroupPaddingOptions定义了ChipGroup的上下内边距，用于控制其整体高度。 |
| [ChipGroupSpaceOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupspaceoptions-i.md) | ChipGroupSpaceOptions 定义了ChipGroup左右内边距，以及Chip与Chip之间的间距。 |
| [ChipItemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md) | ChipItemStyle定义了Chip的通用属性。 |
| [IconItemOptions](arkts-arkui-arkui-advanced-chipgroup-iconitemoptions-i.md) | 定义了尾部builder接口，用于配置尾部图标及其背景区域的显示属性。 |
| [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md) | IconOptions定义图标的通用属性。 |
| [LabelOptions](arkts-arkui-arkui-advanced-chipgroup-labeloptions-i.md) | LabelOptions定义文本属性。 |
| [SuffixImageIconOptions](arkts-arkui-arkui-advanced-chipgroup-suffiximageiconoptions-i.md) | 后缀图标选项的类型。 |
| [SymbolItemOptions](arkts-arkui-arkui-advanced-chipgroup-symbolitemoptions-i.md) | ChipGroup的后缀图标选项类型。 |

## 示例

### 示例1（无最右侧的builder）

该示例实现了在没有最右侧builder时的效果。



```TypeScript
import { ChipSize, ChipGroup } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State selectedIndex: Array<number> = [0, 1, 2, 3, 4, 5, 6];

  build() {
    Column() {
      ChipGroup({
        // items内每个对象设置的都是每个Chip的特定属性。
        items: [
          {
            // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: '操作块1' },
            suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') },
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: '操作块2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true
          },
        ],
        // 设置Chip的style属性。
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

### 示例2（有最右侧的builder）

通过配置suffix实现最右侧的自定义组件效果。



```TypeScript
import { ChipSize, ChipGroup, IconGroupSuffix } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State selectedIndex: Array<number> = [0, 1, 2, 3, 4, 5, 6];
  @State selectedState: boolean = true;

  @LocalBuilder
  ChipGroupSuffix(): void {
    // 开发者通过引用IconGroupSuffix，实现组件最右侧的自定义组件效果。
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
        // items内每个对象设置的都是每个Chip的特定属性。
        items: [
          {
            // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: '操作块1' },
            suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') },
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: '操作块2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true
          },
        ],
        // 设置Chip的style属性。
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
        // 自定义builder，在组件最右侧显示自定义的内容。
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

### 示例3（设置Symbol类型图标）

该示例实现了IconGroupSuffix和ChipGroup传入SymbolGlyph资源。



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
    // 开发者通过引用IconGroupSuffix，实现组件最右侧的自定义组件效果。
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
        // items内每个对象设置的都是每个Chip的特定属性。
        items: [
          {
            prefixSymbol: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
            label: { text: '操作块1' },
            suffixSymbol: { normal: this.suffixModifierNormal, activated: this.suffixModifierActivated },
            allowClose: false,
          },
          {
            prefixSymbol: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
            label: { text: '操作块2' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true,
          },
        ],
        // 设置Chip的style属性。
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
        // 自定义builder，在组件最右侧显示自定义的内容。
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

### 示例4（单选时无障碍朗读）

该示例实现ChipGroup在单选模式下，有后缀区域和无后缀区域的屏幕朗读功能，具体播报内容为accessibilityText属性中的内容。



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
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          symbol: new SymbolGlyphModifier($r('sys.symbol.more')),
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多', // accessibilityLevel属性设置为“no”时，accessibilityText属性和accessibilityDescription属性无效
          accessibilityDescription: '新手提醒',
          accessibilityLevel: 'no',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
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
          SectionGroup({ title: '可用的' }) {
            SectionItem({ title: '单选 无后缀区域' }) {
              ChipGroup({
                items: [
                  {
                    prefixIcon: {
                      src: $r('app.media.startIcon')
                    },
                    label: { text: '选项1' },
                    suffixImageIcon: {
                      src: $r('sys.media.save_button_picture'),
                      accessibilityText: '保存', // 播报“保存，按钮”
                      action: () => {
                        this.getUIContext().getPromptAction().showToast({
                          message: '后缀图标被点击！'
                        });
                      },
                    }
                  },
                  {
                    label: { text: '选项2' },
                    suffixSymbol: {
                      normal: new SymbolGlyphModifier($r('sys.symbol.save')),
                      activated: new SymbolGlyphModifier($r('sys.symbol.save'))
                    },
                    suffixSymbolOptions: {
                      normalAccessibility: {
                        accessibilityText: '保存' // 播报“保存，按钮”
                      },
                      action: () => {
                        this.getUIContext().getPromptAction().showToast({
                          message: '后缀图标被点击！'
                        });
                      }
                    }
                  },
                  {
                    label: { text: '选项3' },
                    suffixIcon: { src: $r('sys.media.save_button_picture'), }
                  },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ]
              })
            }

            SectionItem({ title: '单选 有后缀区域' }) {
              ChipGroup({
                items: [
                  { label: { text: '选项1' } },
                  { label: { text: '选项2' } },
                  { label: { text: '选项3' } },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
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
    .title('基础用法')
    .backgroundColor('#F1F3F5')
  }
}
```

### 示例5（多选时无障碍朗读）

该示例实现了ChipGroup在多选模式下，有后缀区域和无后缀区域的屏幕朗读功能，具体播报内容为accessibilityText属性中的内容。



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
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          symbol: new SymbolGlyphModifier($r('sys.symbol.more')),
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多', // accessibilityLevel属性设置为“no”时，accessibilityText属性和accessibilityDescription属性无效
          accessibilityDescription: '新手提醒',
          accessibilityLevel: 'no',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
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
          SectionGroup({ title: '可用的' }) {
            SectionItem({ title: '多选 无后缀区域' }) {
              ChipGroup({
                items: [
                  { label: { text: '选项1' } },
                  { label: { text: '选项2' } },
                  { label: { text: '选项3' } },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ],
                multiple: true
              })
            }

            SectionItem({ title: '多选 有后缀区域' }) {
              ChipGroup({
                items: [
                  { label: { text: '选项1' } },
                  { label: { text: '选项2' } },
                  { label: { text: '选项3' } },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
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
    .title('基础用法')
    .backgroundColor('#F1F3F5')
  }
}
```

### 示例6（设置系统材质样式）

该示例通过配置backgroundSystemMaterial和iconBackgroundSystemMaterial实现系统材质样式，开启自动反色功能使文本颜色适配背景色。

从API版本26.0.0开始，[ChipGroup](#chipgroup-1)新增backgroundSystemMaterial属性，[IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md)新增iconBackgroundSystemMaterial属性。

该示例配图为高算力设备强档效果。



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
      // 将fontColor设置为特殊系统资源值，启用自动反色能力。
        .fontColor([$r('sys.color.font_primary')])],
      // 设置后缀图标的系统材质样式为ULTRA_THIN，并开启自动反色。
      iconBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
        style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
        colorInvert: true
      })
    })
  }

  @Builder
  NavigationTitle() {
    Column({ space: 10 }) {
      ChipGroup({
        items: [
          { label: { text: '选项1' } },
          { label: { text: '选项2' } },
          { label: { text: '选项3' } },
          { label: { text: '选项4' } },
          { label: { text: '选项5' } },
          { label: { text: '选项6' } },
        ],
        selectedIndexes: this.selectedIndexes,
        itemStyle: {
          // 设置透明的背景颜色，否则会和系统材质冲突。
          backgroundColor: Color.Transparent,
          // 将fontColor设置为特殊系统资源值，启用自动反色能力。
          fontColor: $r('sys.color.font_primary'),
          selectedFontColor: $r('sys.color.font_primary')
        },
        // 设置ChipGroup的系统材质样式为ULTRA_THIN，并开启自动反色。
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
      angle: 90, // 渐变角度，90度是从左到右。
      colors: [
        ['#FF9A9E', 0.0], // 起始颜色及位置（0.0表示起点）。
        ['#FECFEF', 0.5], // 中间颜色及位置。
        ['#3B324C', 1.0] // 结束颜色及位置（1.0表示终点）。
      ]
    })
    .padding(12)
    .width('100%')
  }

  build() {
    Column() {
      Navigation() {
        // 页面内容
      }
      .title({ builder: this.NavigationTitle, height: '100%' })
    }.width('100%').height('100%')
  }
}
```

### 示例7（设置组件选中状态的系统材质样式）

该示例通过配置selectedBackgroundSystemMaterial实现组件选中状态的系统材质样式，开启自动反色功能使文本颜色适配背景色。

从API版本26.0.0开始，[ChipGroup](#chipgroup-1)新增selectedBackgroundSystemMaterial属性。

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
      // 将fontColor设置为特殊系统资源值，启用自动反色能力。
        .fontColor([$r('sys.color.font_primary')])],
      // 设置后缀图标的系统材质样式为ULTRA_THIN，并开启自动反色。
      iconBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
        style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
        colorInvert: true
      })
    })
  }

  @Builder
  NavigationTitle() {
    Column({ space: 10 }) {
      ChipGroup({
        items: [
          { label: { text: '选项1' } },
          { label: { text: '选项2' } },
          { label: { text: '选项3' } },
          { label: { text: '选项4' } },
          { label: { text: '选项5' } },
          { label: { text: '选项6' } },
        ],
        selectedIndexes: this.selectedIndexes,
        itemStyle: {
          // 设置透明的背景颜色，否则会和系统材质冲突。
          backgroundColor: Color.Transparent,
          // 将fontColor设置为特殊系统资源值，启用自动反色能力。
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary')
        },
        // 设置ChipGroup的选中项系统材质样式为ULTRA_THIN，并开启自动反色。
        selectedBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          materialColor: $r('sys.color.ohos_id_color_emphasize'),
          colorInvert: true
        }),
        // 设置ChipGroup的系统材质样式为ULTRA_THIN，并开启自动反色。
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
      angle: 90, // 渐变角度，90度是从左到右。
      colors: [
        ['#FF9A9E', 0.0], // 起始颜色及位置（0.0表示起点）。
        ['#FECFEF', 0.5], // 中间颜色及位置。
        ['#3B324C', 1.0] // 结束颜色及位置（1.0表示终点）。
      ]
    })
    .padding(12)
    .width('100%')
  }

  build() {
    Column() {
      Navigation() {
        // 页面内容
      }
      .title({ builder: this.NavigationTitle, height: '100%' })
    }.width('100%').height('100%')
  }
}
```
