# @ohos.arkui.advanced.SegmentButtonV2(api/@ohos.arkui.advanced.SegmentedButton.d.ts)

## Modules to Import

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [SegmentButtonV2Item](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2item-c.md) |  |
| [SegmentButtonV2Items](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2items-c.md) | Represents items of the **SegmentButtonV2** component. |

### Structs

| Name | Description |
| --- | --- |
| [CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md) | The segmented button component is used to create tab-type, single-selection, or multi-selection capsule segmented buttons. It supports multiple option types such as text, icons, and symbols, as well as graphic-text hybrid configurations, and allows customization of fonts, colors, corner radii, and other styles. The tab segmented button is suitable for tab switching scenarios, the single-selection capsule segmented button is suitable for single- selection switching scenarios, and the multi-selection capsule segmented button is suitable for multi-selection filtering scenarios. |
| [MultiCapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-multicapsulesegmentbuttonv2-s.md) | The segmented button component is used to create tab-type, single-selection, or multi-selection capsule segmented buttons. It supports multiple option types such as text, icons, and symbols, as well as graphic-text hybrid configurations, and allows customization of fonts, colors, corner radii, and other styles. The tab segmented button is suitable for tab switching scenarios, the single-selection capsule segmented button is suitable for single- selection switching scenarios, and the multi-selection capsule segmented button is suitable for multi-selection filtering scenarios. |
| [TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md) | The segmented button component is used to create tab-type, single-selection, or multi-selection capsule segmented buttons. It supports multiple option types such as text, icons, and symbols, as well as graphic-text hybrid configurations, and allows customization of fonts, colors, corner radii, and other styles. The tab segmented button is suitable for tab switching scenarios, the single-selection capsule segmented button is suitable for single- selection switching scenarios, and the multi-selection capsule segmented button is suitable for multi-selection filtering scenarios. |

### Interfaces

| Name | Description |
| --- | --- |
| [SegmentButtonV2ItemOptions](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2itemoptions-i.md) | Defines segmented button item options. |

### Types

| Name | Description |
| --- | --- |
| [OnSelectedIndexChange](arkts-arkui-onselectedindexchange-t.md) | Defines a callback invoked when the selected segmented button item changes. |
| [OnSelectedIndexesChange](arkts-arkui-onselectedindexeschange-t.md) | Defines a callback invoked when the selected segmented button items change. |

## Examples

### Example 1: Using the TabSegmentButtonV2

This example describes how to use the TabSegmentButtonV2 component.



```TypeScript
import { SegmentButtonV2Items, TabSegmentButtonV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct TabSegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Phone' },
    { text: 'Tablet' },
    { text: '2-in-1' },
    { text: 'Wearable' },
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
    { text: 'Phone', symbol: $r('sys.symbol.phone') },
    { text: 'Tablet', symbol: $r('sys.symbol.pad') },
    { text: '2-in-1', symbol: $r('sys.symbol.matebook') },
    { text: 'Wearable', symbol: $r('sys.symbol.watch') },
  ]);
  @Local hybridSelectedIndex: number = 0;
  @Local freeItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Year' },
    { text: 'Month' },
    { text: 'Week' },
    { text: 'Day' },
    { icon: $r('sys.media.ohos_ic_public_search_filled') },
  ]);
  @Local freeSelectedIndex: number = 0;

  build() {
    Scroll() {
      Column({ space: 12 }) {
        VCard({ title: 'Text Button' }) {
          TabSegmentButtonV2({
            items: this.textItems,
            selectedIndex: this.textSelectedIndex!!,
          })
        }

        VCard({ title: 'Image Button' }) {
          TabSegmentButtonV2({
            items: this.imageItems,
            selectedIndex: this.imageSelectedIndex!!,
          })
        }

        VCard({ title: 'Symbol Button' }) {
          TabSegmentButtonV2({
            items: this.symbolItems,
            selectedIndex: this.symbolSelectedIndex!!,
          })
        }

        VCard({ title: 'Text and Icon Button' }) {
          TabSegmentButtonV2({
            items: this.hybridItems,
            selectedIndex: this.hybridSelectedIndex!!,
          })
        }

        VCard({ title: 'Custom Button' }) {
          TabSegmentButtonV2({
            items: this.freeItems,
            selectedIndex: this.freeSelectedIndex!!,
          })
        }

        Button(`Usage instructions for the isHybrid API, ${this.textItems[0].isHybrid}`) // false is displayed for text-only items.
          .width('70%')

        Button(`Usage instructions for the isHybrid API, ${this.hybridItems[0].isHybrid}`) // true is displayed for items with both text and an icon.
          .width('70%')

        Button('Usage instructions for the hasHybrid API, ${this.textItems.hasHybrid}`) // false is displayed when a segmented button does not support items with both text and an icon.
          .width('70%')

        Button('Usage instructions for the hasHybrid API, ${this.hybridItems.hasHybrid}`) // true is displayed when a segmented button supports items with both text and an icon.
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

### Example 2: Using the CapsuleSegmentButtonV2

This example describes how to use the CapsuleSegmentButtonV2 component.



```TypeScript
import { CapsuleSegmentButtonV2, SegmentButtonV2Items } from '@kit.ArkUI';

@Entry
@ComponentV2
struct CapsuleSegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // Sets the item text for the segmented button.
    { text: 'Phone' },
    { text: 'Tablet' },
    { text: '2-in-1' }, 
    { text: 'Wearable' },
  ]);
  @Local textSelectedIndex: number = 0;
  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // Set the item icon for the segmented button.
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local imageSelectedIndex: number = 0;
  @Local symbolItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // Segmented button item icon of the symbol type.
    { symbol: $r('sys.symbol.phone') },
    { symbol: $r('sys.symbol.pad') },
    { symbol: $r('sys.symbol.matebook') },
    { symbol: $r('sys.symbol.watch') },
  ]);
  @Local symbolSelectedIndex: number = 0;
  @Local hybridItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Phone', symbol: $r('sys.symbol.phone') },
    { text: 'Tablet', symbol: $r('sys.symbol.pad') },
    { text: '2-in-1', symbol: $r('sys.symbol.matebook') },
    { text: 'Wearable', symbol: $r('sys.symbol.watch') },
  ]);
  @Local hybridSelectedIndex: number = 0;
  @Local freeItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Year' },
    { text: 'Month' },
    { text: 'Week' },
    { text: 'Day' },
    { icon: $r('sys.media.ohos_ic_public_search_filled') },
  ]);
  @Local freeSelectedIndex: number = 0;

  build() {
    Scroll() {
      Column({ space: 12 }) {
        VCard({ title: 'Text Button' }) {
          CapsuleSegmentButtonV2({
            items: this.textItems,
            selectedIndex: this.textSelectedIndex!!,
          })
        }

        VCard({ title: 'Image Button' }) {
          CapsuleSegmentButtonV2({
            items: this.imageItems,
            selectedIndex: this.imageSelectedIndex!!,
          })
        }

        VCard({ title: 'Symbol Button' }) {
          CapsuleSegmentButtonV2({
            items: this.symbolItems,
            selectedIndex: this.symbolSelectedIndex!!,
          })
        }

        VCard({ title: 'Text and Icon Button' }) {
          CapsuleSegmentButtonV2({
            items: this.hybridItems,
            selectedIndex: this.hybridSelectedIndex!!,
          })
        }

        VCard({ title: 'Custom Button' }) {
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
      // Check whether the title exists. If not, the title is not displayed.
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

### Example 3: Using the MultiCapsuleSegmentButtonV2

This example describes how to use the MultiCapsuleSegmentButtonV2 component.



```TypeScript
import { MultiCapsuleSegmentButtonV2, SegmentButtonV2Items } from '@kit.ArkUI';

@Entry
@ComponentV2
struct MultiCapsuleSegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // Sets the item text for the segmented button.
    { text: 'Phone' },
    { text: 'Tablet' },
    { text: '2-in-1' }, 
    { text: 'Wearable' },
  ]);
  @Local textSelectedIndexes: number[] = [0];
  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // Set the item icon for the segmented button.
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local imageSelectedIndexes: number[] = [0];
  @Local symbolItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    // Segmented button item icon of the symbol type.
    { symbol: $r('sys.symbol.phone') },
    { symbol: $r('sys.symbol.pad') },
    { symbol: $r('sys.symbol.matebook') },
    { symbol: $r('sys.symbol.watch') },
  ]);
  @Local symbolSelectedIndexes: number[] = [0];
  @Local hybridItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Phone', symbol: $r('sys.symbol.phone') },
    { text: 'Tablet', symbol: $r('sys.symbol.pad') },
    { text: '2-in-1', symbol: $r('sys.symbol.matebook') },
    { text: 'Wearable', symbol: $r('sys.symbol.watch') },
  ]);
  @Local hybridSelectedIndexes: number[] = [0];
  @Local freeItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Year' },
    { text: 'Month' },
    { text: 'Week' },
    { text: 'Day' },
    { icon: $r('sys.media.ohos_ic_public_search_filled') },
  ]);
  @Local freeSelectedIndexes: number[] = [0];

  build() {
    Scroll() {
      Column({ space: 12 }) {
        VCard({ title: 'Text Button' }) {
          MultiCapsuleSegmentButtonV2({
            items: this.textItems,
            selectedIndexes: this.textSelectedIndexes!!,
          })
        }

        VCard({ title: 'Image Button' }) {
          MultiCapsuleSegmentButtonV2({
            items: this.imageItems,
            selectedIndexes: this.imageSelectedIndexes!!,
          })
        }

        VCard({ title: 'Symbol Button' }) {
          MultiCapsuleSegmentButtonV2({
            items: this.symbolItems,
            selectedIndexes: this.symbolSelectedIndexes!!,
          })
        }

        VCard({ title: 'Text and Icon Button' }) {
          MultiCapsuleSegmentButtonV2({
            items: this.hybridItems,
            selectedIndexes: this.hybridSelectedIndexes!!,
          })
        }

        VCard({ title: 'Custom Button' }) {
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
      // Check whether the title exists. If not, the title is not displayed.
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

### Example 4: Implementing Basic Usage of the Segmented Button Modifier

This example describes the basic usage of the Modifier for the tab segmented button, single-selection capsule segmented button, and multi-selection capsule segmented button.



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
    { text: 'Phone', textModifier: new TextModifier().fontSize(20) }, // textModifier: Text modifier for the segmented button item.
    { text: 'Tablet' },
    // iconModifier: Icon modifier for the segmented button item.
    { icon: $r('sys.media.ohos_ic_public_device_phone'), iconModifier: new ImageModifier().height(17).width(17) },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    // symbolModifier: Symbol modifier for the segmented button item.
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
      // Check whether the title exists. If not, the title is not displayed.
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

### Example 5: Enabling Property Animation for SegmentButtonV2

This example shows that after enableStateAnimation is enabled for SegmentButtonV2, the button switching also has an animation effect when the value of selectedIndex is modified through a state variable.

Since API version 24, the enableStateAnimation attribute is added to [TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md) and [CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md).

```TypeScript
import { TabSegmentButtonV2, CapsuleSegmentButtonV2, SegmentButtonV2Items } from '@kit.ArkUI';

@Entry
@ComponentV2
struct SegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Phone' },
    { text: 'Tablet' },
    { text: '2-in-1' },
    { text: 'Wearable' },
  ]);
  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local textSelectedIndex: number = 0;
  @Local imageSelectedIndex: number = 0;
  @Local currentSelectedIndex: number = 0; // Index counter for switching selected items.

  build() {
    Scroll() {
      Column({ space: 12 }) {
        VCard({ title: 'TabSegmentButtonV2' }) {
          TabSegmentButtonV2({
            items: this.textItems,
            selectedIndex: this.textSelectedIndex!!,
            enableStateAnimation: true // Enable property animation for TabSegmentButtonV2
          })
        }

        VCard({ title: 'CapsuleSegmentButtonV2' }) {
          CapsuleSegmentButtonV2({
            items: this.imageItems,
            selectedIndex: this.imageSelectedIndex!!,
            enableStateAnimation: true // Enable property animation for CapsuleSegmentButtonV2.
          })
        }

        Button('ChangeSelectedIndex').onClick((event: ClickEvent) => {
          // Increment the selected index via a state variable. Reset the index to 0 if it exceeds the maximum value.
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

### Example 6: Setting the Background Material

The following example uses the backgroundSystemMaterial attribute to set a transparent background material for the segment button, enable automatic color inversion and interactive deformation effects, and customize the color of the feedback light effect.

Since API version 26.0.0, the backgroundSystemMaterial attribute is added to [TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md) and [CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md).

```TypeScript
import { SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, uiMaterial, ColorMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct SegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Phone' },
    { text: 'Tablet' },
    { text: 'PC/2-in-1' },
    { text: 'Wearable' },
  ]);
  @Local textSelectedIndex: number = 0;
  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local imageSelectedIndex: number = 0;

  build() {
    Column({ space: 12 }) {
      VCard({ title: 'Text Button' }) {
        TabSegmentButtonV2({
          items: this.textItems,
          selectedIndex: this.textSelectedIndex!!,
          // Set itemFontColor to a special system resource value to enable automatic color inversion.
          itemFontColor: ColorMetrics.resourceColor($r('sys.color.font_primary')),
          itemSelectedFontColor: ColorMetrics.resourceColor(Color.Black),
          // Set the system material style to ULTRA_THIN, enable automatic color inversion and interactive deformation, and customize the feedback light effect color.
          backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
            colorInvert: true,
            interactive: true,
            lightEffect: { color: $r('sys.color.interactive_click') }
          })
        })
      }

      VCard({ title: 'Image Button' }) {
        CapsuleSegmentButtonV2({
          items: this.imageItems,
          selectedIndex: this.imageSelectedIndex!!,
          // Set itemFontColor to a special system resource value to enable automatic color inversion.
          itemFontColor: ColorMetrics.resourceColor($r('sys.color.font_primary')),
          itemSelectedFontColor: ColorMetrics.resourceColor(Color.Black),
          // Set the system material style to ULTRA_THIN, enable automatic color inversion and interactive deformation, and customize the feedback light effect color.
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
      angle: 180, // Gradient angle. 180 degrees means from top to bottom.
      colors: [
        ['#FF9A9E', 0.0], // Start color and position (0.0 indicates the start point).
        ['#FECFEF', 0.5], // Middle color and position.
        ['#3B324C', 1.0] // End color and position (1.0 indicates the end point).
      ]
    })
    .height(225)
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

### Example 7: Listening to Changes in Inner Properties of Object-Type Properties

[SegmentButtonV2Item](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2item-c.md) uses the @ObservedV2 decorator, and the SegmentButtonV2 component receives each attribute parameter through @Param. For basic type properties decorated by @Trace, @Param can already observe property changes and trigger UI refresh. However, for internal properties of object type properties (such as itemIconSize and itemPadding) — for example, width and height of itemIconSize, or top, bottom, start, and end of itemPadding — these object types themselves are not decorated by @ObservedV2, so their internal property changes cannot be detected by @Param. Therefore, the UI does not automatically refresh when internal properties are modified. Using the [makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved) API to wrap object type properties (such as itemIconSize) can add deep observation capability to the internal properties of the object, so that when internal properties (such as width and height) are modified, the framework can detect the changes and trigger UI refresh. For details about the makeObserved API, see [makeObserved API: Changing Unobservable Data to Observable Data](../../../ui/state-management/arkts-new-makeObserved.md).

The following example uses UIUtils.makeObserved to wrap itemIconSize, and modifies the width and height properties of itemIconSize through a Button, to verify that changes to internal properties of object type properties can trigger UI refresh of SegmentButtonV2.

```TypeScript
import { CapsuleSegmentButtonV2, SegmentButtonV2Items, LengthMetrics, UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local items: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Phone', icon: $r('sys.media.ohos_ic_public_device_phone') },
    { text: 'Tablet', icon: $r('sys.media.ohos_ic_public_device_pad') },
    { text: 'PC/2-in-1', icon: $r('sys.media.ohos_ic_public_device_matebook') },
  ]);
  @Local selectedIndex: number = 0;
  // Wrap itemIconSize with UIUtils.makeObserved to make the internal width and height properties observable.
  @Local itemIconSize: SizeT<LengthMetrics> = UIUtils.makeObserved({ width: LengthMetrics.vp(30), height: LengthMetrics.vp(30) });
  @Local currentIconSize: number = 30;

  build() {
    Column({ space: 20 }) {
      CapsuleSegmentButtonV2({
        items: this.items,
        selectedIndex: this.selectedIndex!!,
        // Pass the itemIconSize wrapped by makeObserved to the component.
        itemIconSize: this.itemIconSize,
      })
      Button('Change icon size')
        .onClick(() => {
          this.currentIconSize = this.currentIconSize === 30 ? 10 : 30;
          // Modify the internal properties of itemIconSize. The UI is automatically refreshed because of the makeObserved wrapping.
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
