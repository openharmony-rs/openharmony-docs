# Select

The **Select** component provides a drop-down menu that allows users to select among multiple options.

> **NOTE**

## Child Components

Not supported

## Select

```TypeScript
Select(options: Array<SelectOption>)
```

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | Array&lt;[SelectOption](arkts-arkui-select-comp-selectoption-i.md)&gt; | Yes | Options of the drop-down menu. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [MenuItemConfiguration](arkts-arkui-select-comp-menuitemconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md). |
| [MenuOutlineOptions](arkts-arkui-select-comp-menuoutlineoptions-i.md) | Defines the outline of the drop-down menu. |
| [SelectOption](arkts-arkui-select-comp-selectoption-i.md) | Provides information about the drop-down menu options. |

### Types

| Name | Description |
| --- | --- |
| [OnSelectCallback](arkts-arkui-select-comp-onselectcallback-t.md) | Defines the callback invoked when a drop-down menu option is selected. |

### Enums

| Name | Description |
| --- | --- |
| [ArrowPosition](arkts-arkui-select-comp-arrowposition-e.md) | Enumerates arrow positions. |
| [AvoidanceMode](arkts-arkui-select-comp-avoidancemode-e.md) | Enumerates the drop-down menu avoidance modes. |
| [MenuAlignType](arkts-arkui-select-comp-menualigntype-e.md) | Enumerates drop-down menu alignment modes. |

## Examples

### Example 1: Creating a Drop-down Menu

This example demonstrates how to create a drop-down menu by configuring [SelectOption](arkts-arkui-select-comp-selectoption-i.md) and how to implement menu avoidance using the [avoidance](arkts-arkui-select-comp-attribute.md#avoidance) attribute, available since API version 19.



```TypeScript
// xxx.ets
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = 2;
  @State space: number = 8;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;

  build() {
    Column() {
      // Replace $r('app.media.selection') with the image resource file you use.
      Select([{ value: 'aaa', icon: $r("app.media.selection") },
        { value: 'bbb', icon: $r("app.media.selection") },
        { value: 'ccc', icon: $r("app.media.selection") },
        { value: 'ddd', icon: $r("app.media.selection") }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .space(this.space)
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        .optionWidth(200)
        .optionHeight(300)
        /**
         * Callback triggered when a drop-down menu option is selected.
         * index: subscript of the selected option.
         * text: text of the selected option (optional).
         */
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          // Update the state for the selected index.
          this.index = index;
          // Update the text displayed in the selection box if the text value exists.
          if (text) {
            this.text = text;
          }
        })
        // Overlay the target component when there is no sufficient space below the component.
        .avoidance(AvoidanceMode.COVER_TARGET);
    }.width('100%')
  }
}
```

### Example 2: Setting the Symbol Icon

This example demonstrates how to create a drop-down menu with symbol icons in the Select component and implement menu avoidance using the [avoidance](arkts-arkui-select-comp-attribute.md#avoidance) attribute, available since API version 19.



```TypeScript
// xxx.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = 2;
  @State space: number = 8;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;
  @State symbolModifier1: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')).fontColor([Color.Green]);
  @State symbolModifier2: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]);
  @State symbolModifier3: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_trash')).fontColor([Color.Gray]);
  @State symbolModifier4: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.exposure')).fontColor([Color.Gray]);

  build() {
    Column() {
      Select([{ value: 'aaa', symbolIcon: this.symbolModifier1 },
        { value: 'bbb', symbolIcon: this.symbolModifier2 },
        { value: 'ccc', symbolIcon: this.symbolModifier3 },
        { value: 'ddd', symbolIcon: this.symbolModifier4 }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .space(this.space)
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        /**
         * Callback triggered when a drop-down menu option is selected.
         * index: subscript of the selected option.
         * text: text of the selected option (optional).
         */
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          // Update the state for the selected index.
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        // Overlay the target component when there is no sufficient space below the component.
        .avoidance(AvoidanceMode.COVER_TARGET);
    }.width('100%')
  }
}
```

### Example 3: Implementing a Custom Drop-down Menu

This example implements a custom drop-down menu, each option of which consists of text + symbol + blank area + text + drawn triangle. After a menu option is clicked, the text content of the menu option is displayed.



```TypeScript
import { SymbolGlyphModifier } from '@kit.ArkUI';

/**
 * Custom content modifier for drop-down menu options
 * Implement the standard ContentModifier to replace the default item layout of the drop-down panel.
 * Allow custom text to be appended at the end of each menu item.
 */
class MyMenuItemContentModifier implements ContentModifier<MenuItemConfiguration> {
  modifierText: string = "";

  constructor(text: string) {
    this.modifierText = text;
  }

  applyContent(): WrappedBuilder<[MenuItemConfiguration]> {
    return wrapBuilder(MenuItemBuilder);
  }
}

/**
 * UI builder for custom drop-down menu items
 * Fully override the menu item layout: text on the left side, icon, custom text, and outlined triangular shape.
 * @param configuration Configuration object for menu items, containing value, index, icon, custom content modifier and other related data.
 */
@Builder
function MenuItemBuilder(configuration: MenuItemConfiguration) {
  Row() {
    Text(configuration.value)
    Blank()
    // Render the system vector symbol icon first.
    if (configuration.symbolIcon) {
      SymbolGlyph().attributeModifier(configuration.symbolIcon).fontSize(24)
    } else if (configuration.icon) {
      Image(configuration.icon).size({ width: 24, height: 24 })
    }
    Blank(30)
    // Retrieve and display the suffix text passed by the custom content modifier.
    Text((configuration.contentModifier as MyMenuItemContentModifier).modifierText)
    Blank(30)
    // Draw a custom triangular path shape with only a stroke and no fill color.
    Path()
      .width('100px')
      .height('150px')
      .commands('M40 0 L80 100 L0 100 Z')
      .fillOpacity(0)
      .stroke(Color.Black)
      .strokeWidth(3)
  }
  .padding({left: 8, top: 8})
  .onClick(() => {
    configuration.triggerSelect(configuration.index, configuration.value.valueOf().toString());
  })
}

@Entry
@Component
struct SelectExample {
  @State text: string = "Content Modifier Select";
  @State symbolModifier1: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_trash')).fontColor([Color.Gray]);
  @State symbolModifier2: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.exposure')).fontColor([Color.Gray]);

  build() {
    Column() {
      Row() {
        // Replace $r('app.media.icon') with the image resource file you use.
        Select([{ value: 'item1', icon: $r('app.media.icon'), symbolIcon: this.symbolModifier1 },
          { value: 'item1', icon: $r('app.media.icon'), symbolIcon: this.symbolModifier2 }])
          .value(this.text)
          .onSelect((index: number, text?: string) => {
            console.info('Select index:' + index);
            console.info('Select text:' + text);
          })
          // Bind the custom menu item modifier to replace the default layout of the drop-down panel.
          .menuItemContentModifier(new MyMenuItemContentModifier("Content Modifier"))

      }.alignItems(VerticalAlign.Center).height('50%')
    }
  }
}
```

### Example 4: Using the Divider Style

This example uses DividerOptions to create a divider-style drop-down menu and implements menu avoidance using the [avoidance](arkts-arkui-select-comp-attribute.md#avoidance) attribute, available since API version 19.



```TypeScript
// xxx.ets
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = -1;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;

  build() {
    Column() {
      // Replace $r('app.media.icon') with the image resource file you use.
      Select([{ value: 'aaa', icon: $r("app.media.icon") },
        { value: 'bbb', icon: $r("app.media.icon") },
        { value: 'ccc', icon: $r("app.media.icon") },
        { value: 'ddd', icon: $r("app.media.icon") }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        .optionWidth(200)
        .optionHeight(300)
        /**
         * Custom configuration for dividers between drop-down options
         * strokeWidth: width of the divider.
         * color: color of the divider.
         * startMargin/endMargin: left and right margins of the divider.
         */
        .divider({
          strokeWidth: 5,
          color: Color.Blue,
          startMargin: 10,
          endMargin: 10
        })
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        .avoidance(AvoidanceMode.COVER_TARGET);
    }.width('100%')
  }
}
```

### Example 5: Using the No-Divider Style

This example sets the divider attribute to null to remove dividers, and implements menu avoidance using the [avoidance](arkts-arkui-select-comp-attribute.md#avoidance) attribute, available since API version 19.



```TypeScript
// xxx.ets
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = -1;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;

  build() {
    Column() {
      // Replace $r('app.media.icon') with the image resource file you use.
      Select([{ value: 'aaa', icon: $r("app.media.icon") },
        { value: 'bbb', icon: $r("app.media.icon") },
        { value: 'ccc', icon: $r("app.media.icon") },
        { value: 'ddd', icon: $r("app.media.icon") }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        .optionWidth(200)
        .optionHeight(300)
        // Pass null to divider to hide dividers between options.
        .divider(null)
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        .avoidance(AvoidanceMode.COVER_TARGET);
    }.width('100%')
  }
}
```

### Example 6: Setting the Text and Arrow Styles of the Select Component

This example illustrates how to configure the text and arrow styles of the Select component using the [textModifier](#textmodifier20) and [arrowModifier](arkts-arkui-select-comp-attribute.md#arrowmodifier) attributes, available since API version 20.



```TypeScript
import { TextModifier, SymbolGlyphModifier } from "@kit.ArkUI";

/**
 * Use TextModifier to control the text display style of the selection box.
 * Use SymbolGlyphModifier to customize the size and color of the drop-down arrow icon on the right.
 */
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTTTTTTT".repeat(3);
  @State index: number = 2;
  textModifier: TextModifier = new TextModifier();
  symbolGlyphModifier: SymbolGlyphModifier = new SymbolGlyphModifier();

  aboutToAppear(): void {
    // Initialize the global style of the main text.
    this.textModifier
      .maxLines(2)
      .fontSize(18)
      .textAlign(TextAlign.Center)
      .fontColor('#333333')
      .fontWeight(FontWeight.Medium)
      .textOverflow({overflow:TextOverflow.Clip})

    // Initialize the style of the drop-down arrow icon.
    this.symbolGlyphModifier
      .fontSize(25)
      .fontColor(['#999999'])
  }

  build() {
    Column() {
      Select([
        // Replace $r('app.media.startIcon') with the image resource file you use.
        { value: 'A very long option text that should be truncated nicely'.repeat(3), icon: $r("app.media.startIcon") },
        { value: 'Option B', icon: $r("app.media.startIcon") },
        { value: 'Option C', icon: $r("app.media.startIcon") },
        { value: 'Option D', icon: $r("app.media.startIcon") }
      ])
        .selected(this.index)
        .value(this.text)
        // Bind a custom text modifier to control the text style.
        .textModifier(this.textModifier)
        // Bind a modifier to customize the drop-down arrow.
        .arrowModifier(this.symbolGlyphModifier)
        .onSelect((index: number, text?: string) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        .margin({ top: 20,left:30 })
        .borderRadius(12)
        .width(200)
        .padding(9)
        .backgroundColor(Color.White)
        .shadow({ radius: 10, color: '#888888', offsetX: 0, offsetY: 10 })
    }
    .alignItems(HorizontalAlign.Start)
    .padding(10)
    .backgroundColor('#F0F2F5')
    .width('100%')
    .height('100%')
  }
}
```

### Example 7: Setting the Text Styles of Selected and Unselected Drop-Down Menu Options

This example demonstrates how to use the [optionTextModifier](arkts-arkui-select-comp-attribute.md#optiontextmodifier) and [selectedOptionTextModifier](arkts-arkui-select-comp-attribute.md#selectedoptiontextmodifier) attributes to set text styles for unselected and selected drop-down menu options, available since API version 20.



```TypeScript
import { TextModifier } from "@kit.ArkUI";

/**
 * Use two separate TextModifier instances to individually control the text styles of regular options and selected options in the drop-down panel.
 */
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTTTTTTT".repeat(3);
  @State index: number = 2;
  optionTextModifier: TextModifier = new TextModifier();
  selectedOptionTextModifier: TextModifier = new TextModifier();
  aboutToAppear(): void {
    // Initialize the text style for regular drop-down options.
    this.optionTextModifier
      .maxLines(1)
      .fontSize(16)
      .textAlign(TextAlign.Start)
      .fontColor('#666666')
      .fontWeight(FontWeight.Normal)
      .width(200)

    // Initialize the text style for selected drop-down options (highlighted).
    this.selectedOptionTextModifier
      .maxLines(1)
      .fontSize(18)
      .textAlign(TextAlign.Start)
      .fontColor('#007BFF')
      .fontWeight(FontWeight.Bold)
      .width(200)
  }

  build() {
    Column() {
      Select([
        // Replace $r('app.media.startIcon') with the image resource file you use.
        { value: 'A very long option text that should be truncated nicely'.repeat(3), icon: $r("app.media.startIcon") },
        { value: 'Option B', icon: $r("app.media.startIcon") },
        { value: 'Option C', icon: $r("app.media.startIcon") },
        { value: 'Option D', icon: $r("app.media.startIcon") }
      ])
        .selected(this.index)
        .value(this.text)
        .onSelect((index: number, text?: string) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        // Bind the text modifier for regular option text.
        .optionTextModifier(this.optionTextModifier)
        // Bind the text modifier for selected option text to implement highlighted styles for selected items.
        .selectedOptionTextModifier(this.selectedOptionTextModifier)
        .margin({ top: 20,left:30 })
        .borderRadius(12)
        .width(200)
        .padding(9)
        .backgroundColor(Color.White)
        .shadow({ radius: 10, color: '#888888', offsetX: 0, offsetY: 10 })
    }
    .alignItems(HorizontalAlign.Start)
    .padding(10)
    .backgroundColor('#F0F2F5')
    .width('100%')
    .height('100%')
  }
}
```

### Example 8: Setting the Divider Mode

This example shows how to set the divider mode by configuring the mode property of [DividerStyleOptions](ts-types.md#dividerstyleoptions12), supported since API version 19.



```TypeScript
import { LengthMetrics } from '@kit.ArkUI'

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Select([{ value: "SelectItem" }, { value: "SelectItem" }, { value: "SelectItem" },])
        .value("Select")
        /**
         * Complete style customization for dividers between drop-down options
         * strokeWidth: width of the divider. The unit is vp, which is used for consistent adaptation across different screens.
         * color: light gray.
         * mode: EMBEDDED_IN_MENU embedded mode.
         */
        .dividerStyle({
          strokeWidth: LengthMetrics.vp(5),
          color: '#d5d5d5',
          mode: DividerMode.EMBEDDED_IN_MENU
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 9: Setting the Outline Style of the Drop-Down Menu

This example shows how to set the outline style of the drop-down menu using the width and color properties of menuOutline, supported since API version 20.



```TypeScript
// xxx.ets
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = -1;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;

  build() {
    Column() {
      Select([{ value: 'aaa' },
        { value: 'bbb' },
        { value: 'ccc' },
        { value: 'ddd' }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        .optionWidth(200)
        .optionHeight(300)
        /**
         * Outline style configuration for the drop-down menu
         * width: outline width set to 5 vp.
         * color: outline color set to blue.
         */
        .menuOutline({
          width: '5vp',
          color: Color.Blue
        })
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F0F2F5')
  }
}
```

### Example 10: Setting the Pop-Up Menu of Select to Avoid the Soft Keyboard

This example demonstrates how to configure the drop-down menu to avoid the soft keyboard and customize the minimum distance for avoiding the soft keyboard by calling the [keyboardAvoidMode](#keyboardavoidmode23) and [minKeyboardAvoidDistance](#minkeyboardavoiddistance23) APIs.

The keyboardAvoidMode and minKeyboardAvoidDistance APIs are added since API version 23.



```TypeScript
import { inputMethod } from '@kit.IMEKit';
import { LengthMetrics } from '@kit.ArkUI';

/**
 * Sample demonstrating the Select drop-down component with automatic input method attachment
 * Configure the keyboard avoidance policy for the pop-up menu, triggering input method attachment with a 2-second delay upon the click of the drop-down box.
 */
@Entry
@Component
struct Index {
  private inputController: inputMethod.InputMethodController | null = null;
  onPageShow(): void {
    try {
      this.inputController = inputMethod.getController();
    } catch (err) {
      console.error("get input method controller fail: ", JSON.stringify(err));
    }
  }

  build() {
    RelativeContainer() {
      Select([{ value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' }])
        .value('Click Show Options')
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center },
        })
        // Set the soft keyboard avoidance mode to translate and resize the popup menu to prevent occlusion by the keyboard.
        .keyboardAvoidMode(MenuKeyboardAvoidMode.TRANSLATE_AND_RESIZE)
        // Set the minimum reserved distance of 20 vp between the popup menu and the soft keyboard.
        .minKeyboardAvoidDistance(LengthMetrics.vp(20))
        .onClick(() => {
          setTimeout(() => {
            this.attachAndListener()
          }, 2000)
        })
    }
    .height('100%')
    .width('100%')
  }

  /**
   * This is an asynchronous method to attach and listen to the input method.
   * 1. Proactively request focus for the page with Index.
   * 2. Verify the validity of the input method controller instance.
   * 3. Attach the input method by configuring the text input type and search enter key.
   */
  async attachAndListener() {
    focusControl.requestFocus('Index')
    if (!this.inputController) {
      console.error('inputController instance is null!');
      return;
    }
    try {
      await this.inputController.attach(true, {
        inputAttribute: {
          textInputType: inputMethod.TextInputType.TEXT, // Regular text input type.
          enterKeyType: inputMethod.EnterKeyType.SEARCH // Search enter key.
        }
      })
    } catch (err) {
      console.error('Fail to attach')
    }
  }
}
```
