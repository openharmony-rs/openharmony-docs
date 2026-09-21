# @ohos.arkui.advanced.SegmentButtonV2

## 导入模块

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SegmentButtonV2Item](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2item-c.md) |  |
| [SegmentButtonV2Items](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2items-c.md) | 分段按钮选项集合。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md) | 分段按钮组件用于创建页签型、单选或多选的胶囊型分段按钮，支持文本、图标、Symbol等多种选项类型及图文混合配置，可自定义字体、颜色、圆角等样式。页签型分段按钮适用于页签切换场景，单选胶囊型分段按钮适用于单选切换场景，多选胶囊型分段按钮适用于多选筛选场景。 |
| [MultiCapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-multicapsulesegmentbuttonv2-s.md) | 分段按钮组件用于创建页签型、单选或多选的胶囊型分段按钮，支持文本、图标、Symbol等多种选项类型及图文混合配置，可自定义字体、颜色、圆角等样式。页签型分段按钮适用于页签切换场景，单选胶囊型分段按钮适用于单选切换场景，多选胶囊型分段按钮适用于多选筛选场景。 |
| [TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md) | 分段按钮组件用于创建页签型、单选或多选的胶囊型分段按钮，支持文本、图标、Symbol等多种选项类型及图文混合配置，可自定义字体、颜色、圆角等样式。页签型分段按钮适用于页签切换场景，单选胶囊型分段按钮适用于单选切换场景，多选胶囊型分段按钮适用于多选筛选场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [SegmentButtonV2ItemOptions](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2itemoptions-i.md) | 配置分段按钮选项参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnSelectedIndexChange](arkts-arkui-onselectedindexchange-t.md) | 单选分段按钮选中项变更时调用的回调函数类型。 |
| [OnSelectedIndexesChange](arkts-arkui-onselectedindexeschange-t.md) | 多选分段按钮选中项变更时调用的回调函数类型。 |

## 示例

### 示例1（页签型分段按钮）

此示例说明页签型分段按钮的基本用法。



```TypeScript
import { SegmentButtonV2Items, TabSegmentButtonV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct TabSegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '手机' },
    { text: '平板' },
    { text: '2in1' },
    { text: '智能穿戴' },
  ]);
  @Local textSelectedIndex: number = 0;
  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local imageSelectedIndex: number = 0;
  @Local symbolItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { symbol: $r('sys.symbol.phone') },
    { symbol: $r('sys.symbol.pad') },
    { symbol: $r('sys.symbol.matebook') },
    { symbol: $r('sys.symbol.watch') },
  ]);
  @Local symbolSelectedIndex: number = 0;
  @Local hybridItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '手机', symbol: $r('sys.symbol.phone') },
    { text: '平板', symbol: $r('sys.symbol.pad') },
    { text: '2in1', symbol: $r('sys.symbol.matebook') },
    { text: '智能穿戴', symbol: $r('sys.symbol.watch') },
  ]);
  @Local hybridSelectedIndex: number = 0;
  @Local freeItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '年' },
    { text: '月' },
    { text: '周' },
    { text: '日' },
    { icon: $r('sys.media.ohos_ic_public_search_filled') },
  ]);
  @Local freeSelectedIndex: number = 0;

  build() {
    Scroll() {
      Column({ space: 12 }) {
        VCard({ title: '纯文本选项' }) {
          TabSegmentButtonV2({
            items: this.textItems,
            selectedIndex: this.textSelectedIndex!!,
          })
        }

        VCard({ title: '纯图标选项（Image）' }) {
          TabSegmentButtonV2({
            items: this.imageItems,
            selectedIndex: this.imageSelectedIndex!!,
          })
        }

        VCard({ title: '纯图标选项（Symbol）' }) {
          TabSegmentButtonV2({
            items: this.symbolItems,
            selectedIndex: this.symbolSelectedIndex!!,
          })
        }

        VCard({ title: '图文混合选项' }) {
          TabSegmentButtonV2({
            items: this.hybridItems,
            selectedIndex: this.hybridSelectedIndex!!,
          })
        }

        VCard({ title: '自由选项' }) {
          TabSegmentButtonV2({
            items: this.freeItems,
            selectedIndex: this.freeSelectedIndex!!,
          })
        }

        Button(`isHybrid接口用法说明，${this.textItems[0].isHybrid}`) // 纯文本选项未配置图标，显示false。
          .width('70%')

        Button(`isHybrid接口用法说明，${this.hybridItems[0].isHybrid}`) // 图文混合选项已配置文本和图标，显示true。
          .width('70%')

        Button(`hasHybrid接口用法说明，${this.textItems.hasHybrid}`) // 分段按钮无图文混合选项，显示false。
          .width('70%')

        Button(`hasHybrid接口用法说明，${this.hybridItems.hasHybrid}`) // 分段按钮有图文混合选项，显示true。
          .width('70%')
      }
      .constraintSize({ minHeight: '100%' })
      .justifyContent(FlexAlign.Start)
      .padding(16)
    }
    .backgroundColor('#f1f3f5')
    .width('100%')
    .height('100%')
  }
}

@Builder
function Noop() {
}

@Component
export struct VCard {
  @Prop
  title: ResourceStr;
  @BuilderParam
  content: () => void = Noop;

  build() {
    Column({ space: 8 }) {
      if (this.title) {
        Text(this.title)
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
          .constraintSize({ maxWidth: '80%' })
      }
      this.content()
    }
    .backgroundColor(Color.White)
    .borderRadius(8)
    .padding(8)
    .width('100%')
  }
}
```

### 示例2（单选的胶囊型分段按钮）

该示例介绍单选胶囊型分段按钮的基本用法。



```TypeScript
import { CapsuleSegmentButtonV2, SegmentButtonV2Items } from '@kit.ArkUI';

@Entry
@ComponentV2
struct CapsuleSegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // 设置分段按钮选项文本。
    { text: '手机' },
    { text: '平板' },
    { text: '2in1' },
    { text: '智能穿戴' },
  ]);
  @Local textSelectedIndex: number = 0;
  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // 设置分段按钮选项图标。
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local imageSelectedIndex: number = 0;
  @Local symbolItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // 分段按钮选项图标，Symbol类型。
    { symbol: $r('sys.symbol.phone') },
    { symbol: $r('sys.symbol.pad') },
    { symbol: $r('sys.symbol.matebook') },
    { symbol: $r('sys.symbol.watch') },
  ]);
  @Local symbolSelectedIndex: number = 0;
  @Local hybridItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '手机', symbol: $r('sys.symbol.phone') },
    { text: '平板', symbol: $r('sys.symbol.pad') },
    { text: '2in1', symbol: $r('sys.symbol.matebook') },
    { text: '智能穿戴', symbol: $r('sys.symbol.watch') },
  ]);
  @Local hybridSelectedIndex: number = 0;
  @Local freeItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '年' },
    { text: '月' },
    { text: '周' },
    { text: '日' },
    { icon: $r('sys.media.ohos_ic_public_search_filled') },
  ]);
  @Local freeSelectedIndex: number = 0;

  build() {
    Scroll() {
      Column({ space: 12 }) {
        VCard({ title: '纯文本选项' }) {
          CapsuleSegmentButtonV2({
            items: this.textItems,
            selectedIndex: this.textSelectedIndex!!,
          })
        }

        VCard({ title: '纯图标选项（Image）' }) {
          CapsuleSegmentButtonV2({
            items: this.imageItems,
            selectedIndex: this.imageSelectedIndex!!,
          })
        }

        VCard({ title: '纯图标选项（Symbol）' }) {
          CapsuleSegmentButtonV2({
            items: this.symbolItems,
            selectedIndex: this.symbolSelectedIndex!!,
          })
        }

        VCard({ title: '图文混合选项' }) {
          CapsuleSegmentButtonV2({
            items: this.hybridItems,
            selectedIndex: this.hybridSelectedIndex!!,
          })
        }

        VCard({ title: '自由选项' }) {
          CapsuleSegmentButtonV2({
            items: this.freeItems,
            selectedIndex: this.freeSelectedIndex!!,
          })
        }
      }
      .constraintSize({ minHeight: '100%' })
      .justifyContent(FlexAlign.Start)
      .padding(16)
    }
    .backgroundColor('#f1f3f5')
    .width('100%')
    .height('100%')
  }
}

@Builder
function Noop() {
}

@Component
export struct VCard {
  @Prop
  title: ResourceStr;
  @BuilderParam
  content: () => void = Noop;

  build() {
    Column({ space: 8 }) {
      // 判断title是否存在，不存在不显示。
      if (this.title) {
        Text(this.title)
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
          .constraintSize({ maxWidth: '80%' })
      }
      this.content()
    }
    .backgroundColor(Color.White)
    .borderRadius(8)
    .padding(8)
    .width('100%')
  }
}
```

### 示例3（多选的胶囊型分段按钮）

该示例介绍多选胶囊型分段按钮的基本用法。



```TypeScript
import { MultiCapsuleSegmentButtonV2, SegmentButtonV2Items } from '@kit.ArkUI';

@Entry
@ComponentV2
struct MultiCapsuleSegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // 设置分段按钮选项文本。
    { text: '手机' },
    { text: '平板' },
    { text: '2in1' },
    { text: '智能穿戴' },
  ]);
  @Local textSelectedIndexes: number[] = [0];
  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // 设置分段按钮选项图标。
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local imageSelectedIndexes: number[] = [0];
  @Local symbolItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // 分段按钮选项图标，Symbol类型。
    { symbol: $r('sys.symbol.phone') },
    { symbol: $r('sys.symbol.pad') },
    { symbol: $r('sys.symbol.matebook') },
    { symbol: $r('sys.symbol.watch') },
  ]);
  @Local symbolSelectedIndexes: number[] = [0];
  @Local hybridItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '手机', symbol: $r('sys.symbol.phone') },
    { text: '平板', symbol: $r('sys.symbol.pad') },
    { text: '2in1', symbol: $r('sys.symbol.matebook') },
    { text: '智能穿戴', symbol: $r('sys.symbol.watch') },
  ]);
  @Local hybridSelectedIndexes: number[] = [0];
  @Local freeItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '年' },
    { text: '月' },
    { text: '周' },
    { text: '日' },
    { icon: $r('sys.media.ohos_ic_public_search_filled') },
  ]);
  @Local freeSelectedIndexes: number[] = [0];

  build() {
    Scroll() {
      Column({ space: 12 }) {
        VCard({ title: '纯文本选项' }) {
          MultiCapsuleSegmentButtonV2({
            items: this.textItems,
            selectedIndexes: this.textSelectedIndexes!!,
          })
        }

        VCard({ title: '纯图标选项（Image）' }) {
          MultiCapsuleSegmentButtonV2({
            items: this.imageItems,
            selectedIndexes: this.imageSelectedIndexes!!,
          })
        }

        VCard({ title: '纯图标选项（Symbol）' }) {
          MultiCapsuleSegmentButtonV2({
            items: this.symbolItems,
            selectedIndexes: this.symbolSelectedIndexes!!,
          })
        }

        VCard({ title: '图文混合选项' }) {
          MultiCapsuleSegmentButtonV2({
            items: this.hybridItems,
            selectedIndexes: this.hybridSelectedIndexes!!,
          })
        }

        VCard({ title: '自由选项' }) {
          MultiCapsuleSegmentButtonV2({
            items: this.freeItems,
            selectedIndexes: this.freeSelectedIndexes!!,
          })
        }
      }
      .constraintSize({ minHeight: '100%' })
      .justifyContent(FlexAlign.Start)
      .padding(16)
    }
    .backgroundColor('#f1f3f5')
    .width('100%')
    .height('100%')
  }
}

@Builder
function Noop() {
}

@Component
export struct VCard {
  @Prop
  title: ResourceStr;
  @BuilderParam
  content: () => void = Noop;

  build() {
    Column({ space: 8 }) {
      // 判断title是否存在，不存在不显示。
      if (this.title) {
        Text(this.title)
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
          .constraintSize({ maxWidth: '80%' })
      }
      this.content()
    }
    .backgroundColor(Color.White)
    .borderRadius(8)
    .padding(8)
    .width('100%')
  }
}
```

### 示例4（分段按钮Modifier的基本用法）

该示例介绍页签型分段按钮、单选的胶囊型分段按钮、多选的胶囊型分段按钮的Modifier基本用法。



```TypeScript
import {
  SegmentButtonV2Items,
  TabSegmentButtonV2,
  CapsuleSegmentButtonV2,
  MultiCapsuleSegmentButtonV2,
  TextModifier,
  ImageModifier,
  SymbolGlyphModifier
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct SegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '手机', textModifier: new TextModifier().fontSize(20) }, // textModifier: 分段按钮选项文本属性样式修改器。
    { text: '平板' },
    // iconModifier: 修改分段按钮选项图片类型的图标属性样式。
    { icon: $r('sys.media.ohos_ic_public_device_phone'), iconModifier: new ImageModifier().height(17).width(17) },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    // symbolModifier: 分段按钮选项Symbol类型图标属性样式修改器。
    { symbol: $r('sys.symbol.phone'), symbolModifier: new SymbolGlyphModifier().fontColor([Color.Pink]) },
    { symbolModifier: new SymbolGlyphModifier($r('sys.symbol.pad')).fontColor([Color.Orange]) },
    { symbol: $r('sys.symbol.matebook') },
  ]);
  @Local textSelectedIndex: number = 0;
  @Local freeSelectedIndexes: number[] = [0];

  build() {
    Column() {
      VCard({ title: 'TabSegmentButtonV2' }) {
        TabSegmentButtonV2({
          items: this.textItems,
          selectedIndex: this.textSelectedIndex!!,
        })
      }

      VCard({ title: 'CapsuleSegmentButtonV2' }) {
        CapsuleSegmentButtonV2({
          items: this.textItems,
          selectedIndex: this.textSelectedIndex!!,
        })
      }

      VCard({ title: 'MultiCapsuleSegmentButtonV2' }) {
        MultiCapsuleSegmentButtonV2({
          items: this.textItems,
          selectedIndexes: this.freeSelectedIndexes!!,
        })
      }

    }
    .constraintSize({ minHeight: '100%' })
    .justifyContent(FlexAlign.Start)
    .padding(16)

  }
}

@Builder
function Noop() {
}

@Component
export struct VCard {
  @Prop
  title: ResourceStr;
  @BuilderParam
  content: () => void = Noop;

  build() {
    Column({ space: 8 }) {
      // 判断title是否存在，不存在不显示。
      if (this.title) {
        Text(this.title)
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
          .constraintSize({ maxWidth: '80%' })
      }
      this.content()
    }
    .backgroundColor(Color.White)
    .borderRadius(8)
    .padding(8)
    .width('100%')
  }
}
```

### 示例5（开启SegmentButtonV2的属性动画）

此示例展示了SegmentButtonV2开启enableStateAnimation后，在通过状态变量修改selectedIndex的值时，按钮切换也具有动画效果。

从API version 24开始，[TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md)和[CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md)新增enableStateAnimation属性。



```TypeScript
import { TabSegmentButtonV2, CapsuleSegmentButtonV2, SegmentButtonV2Items } from '@kit.ArkUI';

@Entry
@ComponentV2
struct SegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '手机' },
    { text: '平板' },
    { text: '2in1' },
    { text: '智能穿戴' },
  ]);
  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local textSelectedIndex: number = 0;
  @Local imageSelectedIndex: number = 0;
  @Local currentSelectedIndex: number = 0; // 切换选中项的索引计数器

  build() {
    Scroll() {
      Column({ space: 12 }) {
        VCard({ title: 'TabSegmentButtonV2' }) {
          TabSegmentButtonV2({
            items: this.textItems,
            selectedIndex: this.textSelectedIndex!!,
            enableStateAnimation: true // 开启TabSegmentButtonV2的属性动画
          })
        }

        VCard({ title: 'CapsuleSegmentButtonV2' }) {
          CapsuleSegmentButtonV2({
            items: this.imageItems,
            selectedIndex: this.imageSelectedIndex!!,
            enableStateAnimation: true // 开启CapsuleSegmentButtonV2的属性动画
          })
        }

        Button('ChangeSelectedIndex').onClick((event: ClickEvent) => {
          // 通过状态变量自增修改选中项的索引值，若超出最大索引则重置为0
          this.currentSelectedIndex = this.currentSelectedIndex < 3 ? this.currentSelectedIndex + 1 : 0;
          this.textSelectedIndex = this.currentSelectedIndex;
          this.imageSelectedIndex = this.currentSelectedIndex;
        })
      }
      .constraintSize({ minHeight: '100%' })
      .justifyContent(FlexAlign.Start)
      .padding(16)
    }
    .backgroundColor('#f1f3f5')
    .width('100%')
    .height('100%')
  }
}

@Builder
function Noop() {
}

@Component
export struct VCard {
  @Prop
  title: ResourceStr;
  @BuilderParam
  content: () => void = Noop;

  build() {
    Column({ space: 8 }) {
      if (this.title) {
        Text(this.title)
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
          .constraintSize({ maxWidth: '80%' })
      }
      this.content()
    }
    .backgroundColor(Color.White)
    .borderRadius(8)
    .padding(8)
    .width('100%')
  }
}
```

### 示例6（设置背景板材质）

以下示例通过backgroundSystemMaterial属性，为分段按钮设置了透明的背景板材质、开启自动反色和交互形变效果，并自定义反馈光感的颜色。

从API版本26.0.0开始，[TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md)和[CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md)中新增backgroundSystemMaterial属性。

该示例配图为高算力设备强档效果。



```TypeScript
import { SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, uiMaterial, ColorMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct SegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '手机' },
    { text: '平板' },
    { text: 'PC/2in1' },
    { text: '智能穿戴' },
  ]);
  @Local textSelectedIndex: number = 0;
  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local imageSelectedIndex: number = 0;

  @Builder
  NavigationTitle() {
    Column({ space: 12 }) {
      VCard({ title: '纯文本选项' }) {
        TabSegmentButtonV2({
          items: this.textItems,
          selectedIndex: this.textSelectedIndex!!,
          // 将itemFontColor设置为特殊系统资源值，启用自动反色能力。
          itemFontColor: ColorMetrics.resourceColor($r('sys.color.font_primary')),
          itemSelectedFontColor: ColorMetrics.resourceColor(Color.Black),
          // 设置为系统材质样式为ULTRA_THIN，并开启自动反色和交互形变效果、自定义反馈光感的颜色。
          backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
            colorInvert: true,
            interactive: true,
            lightEffect: { color: $r('sys.color.interactive_click') }
          })
        })
      }

      VCard({ title: '纯图标选项' }) {
        CapsuleSegmentButtonV2({
          items: this.imageItems,
          selectedIndex: this.imageSelectedIndex!!,
          // 将itemFontColor设置为特殊系统资源值，启用自动反色能力。
          itemFontColor: ColorMetrics.resourceColor($r('sys.color.font_primary')),
          itemSelectedFontColor: ColorMetrics.resourceColor(Color.Black),
          // 设置为系统材质样式为ULTRA_THIN，开启自动反色和交互形变效果、自定义反馈光感的颜色。
          backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
            colorInvert: true,
            interactive: true,
            lightEffect: { color: undefined }
          })
        })
      }
    }
    .linearGradient({
      angle: 180, // 渐变角度，180度是从上到下。
      colors: [
        ['#FF9A9E', 0.0], // 起始颜色及位置（0.0表示起点）。
        ['#FECFEF', 0.5], // 中间颜色及位置。
        ['#3B324C', 1.0] // 结束颜色及位置（1.0表示终点）。
      ]
    })
    .height(225)
    .justifyContent(FlexAlign.Start)
    .padding(16)
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

@Builder
function Noop() {
}

@Component
export struct VCard {
  @Prop
  title: ResourceStr;
  @BuilderParam
  content: () => void = Noop;

  build() {
    Column({ space: 8 }) {
      if (this.title) {
        Text(this.title)
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
          .constraintSize({ maxWidth: '80%' })
      }
      this.content()
    }
    .backgroundColor(Color.Transparent)
    .borderRadius(8)
    .padding(8)
    .width('100%')
  }
}
```

### 示例7（监听对象类型属性内部属性的变化）

[SegmentButtonV2Item](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2item-c.md)使用了@ObservedV2装饰器，SegmentButtonV2组件通过@Param接收各个属性参数。对于@Trace装饰的基本类型属性，@Param已能观测到属性变化并触发UI刷新。但对于对象类型属性（如itemIconSize、itemPadding等）的内部属性（如itemIconSize的width、height，itemPadding的top、bottom、start、end），这些对象类型本身未被@ObservedV2装饰，其内部属性变化无法被@Param感知。因此，修改内部属性时UI不会自动刷新。使用[makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved)接口对对象类型属性（如itemIconSize）进行包裹，可以为该对象的内部属性补充深度观察能力，使得修改内部属性（如width、height）时，框架能够监听到变化并触发UI刷新。makeObserved接口的详细说明请参考[makeObserved接口：将非观察数据变为可观察数据](../../../ui/state-management/arkts-new-makeObserved.md)。

以下示例使用UIUtils.makeObserved包裹itemIconSize，并通过Button修改itemIconSize的width和height属性，验证对象类型属性内部属性变化能够触发SegmentButtonV2的UI刷新。

```TypeScript
import { CapsuleSegmentButtonV2, SegmentButtonV2Items, LengthMetrics, UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local items: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: '手机', icon: $r('sys.media.ohos_ic_public_device_phone') },
    { text: '平板', icon: $r('sys.media.ohos_ic_public_device_pad') },
    { text: 'PC/2in1', icon: $r('sys.media.ohos_ic_public_device_matebook') },
  ]);
  @Local selectedIndex: number = 0;
  // 使用UIUtils.makeObserved包裹itemIconSize，使内部属性width和height可被观测。
  @Local itemIconSize: SizeT<LengthMetrics> = UIUtils.makeObserved({ width: LengthMetrics.vp(30), height: LengthMetrics.vp(30) });
  @Local currentIconSize: number = 30;

  build() {
    Column({ space: 20 }) {
      CapsuleSegmentButtonV2({
        items: this.items,
        selectedIndex: this.selectedIndex!!,
        // 将makeObserved包裹的itemIconSize传入组件。
        itemIconSize: this.itemIconSize,
      })
      Button('修改图标大小')
        .onClick(() => {
          this.currentIconSize = this.currentIconSize === 30 ? 10 : 30;
          // 修改itemIconSize的内部属性，由于makeObserved包裹，UI会自动刷新。
          this.itemIconSize.width = LengthMetrics.vp(this.currentIconSize);
          this.itemIconSize.height = LengthMetrics.vp(this.currentIconSize);
        })
    }
    .width('100%')
    .height('30%')
    .padding(10)
  }
}
```
