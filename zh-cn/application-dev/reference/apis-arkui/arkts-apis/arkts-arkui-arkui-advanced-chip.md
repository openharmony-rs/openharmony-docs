# @ohos.arkui.advanced.Chip

## 导入模块

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [Chip](arkts-arkui-arkui-advanced-chip-chip-f.md) | Chip组件用于标签展示和交互场景，支持自定义样式、图标、激活态等功能，适用于搜索框历史记录、邮件发送列表等场景，可快速实现标签的创建、删除和交互能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityOptions](arkts-arkui-arkui-advanced-chip-accessibilityoptions-i.md) | 后缀图标的无障碍朗读功能属性。 |
| [ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md) | ChipOptions定义Chip的样式及具体样式参数。 |
| [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md) | symbol类型后缀图标的无障碍朗读功能属性及点击事件回调。 |
| [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md) | ChipSymbolGlyphOptions定义前缀图标和后缀图标的属性。 |
| [CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md) | CloseOptions用于定义Chip组件默认的关闭图标功能属性，包括无障碍功能属性，其中accessibilityText默认为"删除"。 |
| [IconCommonOptions](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md) | IconCommonOptions定义图标的共通属性。 |
| [LabelMarginOptions](arkts-arkui-arkui-advanced-chip-labelmarginoptions-i.md) | LabelMarginOptions用于定义文本与左右侧图标之间间距。 |
| [LabelOptions](arkts-arkui-arkui-advanced-chip-labeloptions-i.md) | LabelOptions定义文本属性。 |
| [LocalizedLabelMarginOptions](arkts-arkui-arkui-advanced-chip-localizedlabelmarginoptions-i.md) | LocalizedLabelMarginOptions用于定义本地化文本与左右侧图标之间间距。 |
| [PrefixIconOptions](arkts-arkui-arkui-advanced-chip-prefixiconoptions-i.md) | PrefixIconOptions定义前缀图标的属性。 |
| [SuffixIconOptions](arkts-arkui-arkui-advanced-chip-suffixiconoptions-i.md) | SuffixIconOptions定义后缀图标的属性。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessibilitySelectedType](arkts-arkui-arkui-advanced-chip-accessibilityselectedtype-e.md) | AccessibilitySelectedType定义Chip可指定的选中态类型，用于控制无障碍服务如何向用户传达组件的选中状态。不同的选中态类型提供了不同的语义和用户体验。 |
| [ChipSize](arkts-arkui-arkui-advanced-chip-chipsize-e.md) | ChipSize定义Chip组件可指定的尺寸类型，如普通类型和小尺寸型。 |

## 示例

### 示例1（自定义后缀图标）

通过配置suffixIcon实现自定义操作块的后缀图标。



```TypeScript
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        // 设置前缀图标属性。
        prefixIcon: {
          // 'app.media.chips'仅作示例，请替换为实际使用图片。
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red
        },
        // 设置文本属性。
        label: {
          text: '操作块',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        // 设置后缀图标属性。
        suffixIcon: {
          // 'app.media.close'仅作示例，请替换为实际使用图片。
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

### 示例2（设置默认后缀图标）

配置allowClose为true，显示关闭图标。



```TypeScript
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        // 设置前缀图标属性。
        prefixIcon: {
          // 'app.media.chips'仅作示例，请替换为实际使用图片。
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue
        },
        // 设置文本属性。
        label: {
          text: '操作块',
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

### 示例3（不显示后缀图标）

配置allowClose为false，隐藏关闭图标。



```TypeScript
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        // 设置前缀图标属性。
        prefixIcon: {
          // 'app.media.chips'仅作示例，请替换为实际使用图片。
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue
        },
        // 设置文本属性。
        label: {
          text: '操作块',
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

### 示例4（激活态操作块）

该示例通过配置activated实现激活态操作块。



```TypeScript
import { Chip, ChipSize } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State isActivated: boolean = false;

  build() {
    Column({ space: 10 }) {
      Chip({
        // 设置前缀图标属性。
        prefixIcon: {
          // 'app.media.chips'仅作示例，请替换为实际使用图片。
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue,
          activatedFillColor: $r('sys.color.ohos_id_color_text_primary_contrary')
        },
        // 设置文本属性。
        label: {
          text: '操作块',
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
      // 点击“改变激活状态”，用于控制操作块的激活与关闭。
      Button('改变激活状态')
        .onClick(() => {
          this.isActivated = !this.isActivated;
        })
    }
  }
}
```

### 示例5（设置symbol类型图标）

Chip组件的前缀图标使用symbol类型资源展示。



```TypeScript
import { Chip, ChipSize, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State isActivated: boolean = false;

  build() {
    Column({ space: 10 }) {
      Chip({
        // 设置前缀图标属性，symbol类型。
        prefixSymbol: {
          normal: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontSize(16).fontColor([Color.Green]),
          activated: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontSize(16).fontColor([Color.Red]),
        },
        // 设置文本属性。
        label: {
          text: '操作块',
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

      Button('改变激活状态')
        .onClick(() => {
          this.isActivated = !this.isActivated;
        })
    }
  }
}
```

### 示例6（设置镜像效果）

配置direction实现Chip布局镜像化展示。



```TypeScript
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ChipPage {
  build() {
    Column() {
      Chip({
        direction: Direction.Rtl,
        // 设置前缀图标属性。
        prefixIcon: {
          // 'app.media.chips'仅作示例，请替换为实际使用图片。
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red,
        },
        // 设置文本属性。
        label: {
          text: '操作块',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          localizedLabelMargin: { start: LengthMetrics.vp(20), end: LengthMetrics.vp(20) },
        },
        // 设置后缀图标属性。
        suffixIcon: {
          // 'app.media.close'仅作示例，请替换为实际使用图片。
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

### 示例7（Image类型无障碍朗读）

该示例代码实现Chip组件Image类型后缀图标的无障碍朗读功能，点击后缀图标播报“图标，按钮，新手提醒”。



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
        SectionGroup({ title: '后缀图标播报' }) {
          SectionItem({ title: '自定义播报' }) {
            Chip({
              label: { text: '操作块' },
              suffixIcon: {
                src: $r('sys.media.ohos_ic_public_cut'),
                accessibilityText: '图标', // 播报“图标，按钮，新手提醒”
                accessibilityDescription: '新手提醒',
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: '后缀图标被点击！'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: '操作块被点击！'
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

### 示例8（symbol类型无障碍朗读）

该示例代码实现Chip组件symbol类型后缀图标的无障碍朗读功能，点击后缀图标播报“音乐，按钮，新手提醒”。



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
        SectionGroup({ title: '后缀Symbol播报' }) {
          SectionItem({ title: 'activatedAccessibility' }) {
            Chip({
              label: { text: '操作块' },
              activated: true,
              suffixSymbol: {
                activated: new SymbolGlyphModifier($r('sys.symbol.media_sound'))
                  .fontSize(72),
              },
              suffixSymbolOptions: {
                activatedAccessibility: {
                  accessibilityText: '音乐', // 播报“音乐，按钮，新手提醒”
                  accessibilityDescription: '新手提醒'
                },
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: '后缀Symbol被点击！'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: '操作块被点击！'
                });
              }
            })
          }

          SectionItem({ title: 'normalAccessibility' }) {
            Chip({
              label: { text: '操作块' },
              suffixSymbol: {
                normal: new SymbolGlyphModifier($r('sys.symbol.media_sound'))
                  .fontSize(72),
              },
              suffixSymbolOptions: {
                normalAccessibility: {
                  accessibilityText: '音乐', // 播报“音乐，按钮，新手提醒”
                  accessibilityDescription: '新手提醒'
                },
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: '后缀Symbol被点击！'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: '操作块被点击！'
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

### 示例9（Chip组件无障碍朗读）

示例展示Chip组件的无障碍属性设置，包括不同的accessibilitySelectedType类型和各种无障碍属性。



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
      Text('Chip组件无障碍属性示例').fontSize(20).fontWeight(FontWeight.Bold)

      // 点击型Chip - CLICKED类型
      Chip({
        label: { text: '点击型Chip' },
        prefixIcon: {
          src: $r('sys.media.ohos_app_icon'),
          fillColor: Color.Blue
        },
        size: ChipSize.NORMAL,
        accessibilitySelectedType: AccessibilitySelectedType.CLICKED, // 点击型
        accessibilityDescription: '这是一个点击型Chip', // 整体无障碍描述
        accessibilityLevel: 'yes', // 确保可被无障碍服务识别
        closeOptions: {
          accessibilityDescription: '删除此Chip，此操作无法撤销' // 为删除按钮提供详细说明
        },
        activated: this.clickedChipActivated,
        onClicked: () => {
          this.clickedChipActivated = !this.clickedChipActivated;
          this.getUIContext().getPromptAction().showToast({ message: '点击型Chip被点击' });
        },
        onClose: () => {
          this.getUIContext().getPromptAction().showToast({ message: '点击型Chip的关闭按钮被点击' });
        }
      })

      // 复选型Chip - CHECKED类型
      Chip({
        label: { text: '复选型Chip' },
        prefixIcon: {
          src: $r('sys.media.ohos_app_icon'),
          fillColor: Color.Green
        },
        size: ChipSize.NORMAL,
        accessibilitySelectedType: AccessibilitySelectedType.CHECKED, // 复选型
        accessibilityDescription: '这是一个复选型Chip', // 整体无障碍描述
        activated: this.checkedChipActivated,
        onClicked: () => {
          this.checkedChipActivated = !this.checkedChipActivated;
          this.getUIContext().getPromptAction().showToast({
            message: this.checkedChipActivated ? '复选型Chip被选中' : '复选型Chip被取消选中'
          });
        }
      })

      // 单选型Chip - SELECTED类型
      Chip({
        label: { text: '单选型Chip' },
        prefixIcon: {
          src: $r('sys.media.ohos_app_icon'),
          fillColor: Color.Red
        },
        size: ChipSize.NORMAL,
        accessibilitySelectedType: AccessibilitySelectedType.SELECTED, // 单选型
        accessibilityDescription: '这是一个单选型Chip', // 整体无障碍描述
        activated: this.selectedChipActivated,
        onClicked: () => {
          this.selectedChipActivated = !this.selectedChipActivated;
          this.getUIContext().getPromptAction().showToast({
            message: this.selectedChipActivated ? '单选型Chip被选中' : '单选型Chip被取消选中'
          });
        }
      })

      // 无障碍级别设置示例
      Chip({
        label: { text: '无障碍级别为no' },
        size: ChipSize.NORMAL,
        accessibilityLevel: 'no', // 此Chip不能被无障碍服务识别
        closeOptions: {
          accessibilityLevel: 'no'
        },
        backgroundColor: '#CCCCCC',
        onClicked: () => {
          this.getUIContext().getPromptAction().showToast({ message: '此Chip无法被无障碍服务识别' });
        }
      })
    }
    .width('100%')
    .padding(16)
  }
}
```

### 示例10（设置系统材质样式）

该示例通过配置backgroundSystemMaterial和activatedBackgroundSystemMaterial实现系统材质样式，启用自动反色功能适配标签文本颜色。

从API版本26.0.0开始，[ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md)新增backgroundSystemMaterial和activatedBackgroundSystemMaterial属性。

```TypeScript
import { Chip, ChipOptions, uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct ChipMaterialExample {
  private chipOptions: ChipOptions = {
    label: {
      text: '操作块',
      // 将fontColor设置为特殊系统资源值，启用自动反色能力。
      fontColor: $r('sys.color.font_primary'),
      activatedFontColor: $r('sys.color.font_primary')
    },
    allowClose: false,
    // 设置普通状态下的背景颜色为透明，否则会和系统材质冲突。
    backgroundColor: Color.Transparent,
    // 设置普通状态下的系统材质样式为ULTRA_THIN，并开启自动反色。
    backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      colorInvert: true
    }),
    // 设置激活状态下的背景颜色为透明，否则会和系统材质冲突。
    activatedBackgroundColor: Color.Transparent,
    // 设置激活状态下的系统材质样式。
    activatedBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN
    })
  }

  @Builder
  NavigationTitle() {
    Column({ space: 50 }) {
      Chip(this.chipOptions)
      Chip(this.chipOptions)
    }
    .linearGradient({
      angle: 0, // 渐变角度，0度是从左到右。
      colors: [
        ['#FF9A9E', 0.0], // 起始颜色及位置（0.0表示起点）。
        ['#FECFEF', 0.5], // 中间颜色及位置。
        ['#3B324C', 1.0] // 结束颜色及位置（1.0表示终点）。
      ]
    })
    .padding(12)
    .width('100%')
    .height(150)
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
