# TextPicker

A component that allows users to select text, images, or hybrid content through scrolling. Users can create a single- column data picker, a multi-column non-linked data picker, and a multi-column linkage data picker as needed. It is applicable to needs where users select data from preset options, such as date selection, region selection, and configuration item settings. The component supports features such as cyclic scrolling, custom text styles, divider style, fade effect, selection item height adjustment, haptic feedback, and crown sensitivity setting, providing a smooth scrolling interaction experience and flexible data display.

> **NOTE:** 
> 
> - This component is supported since API version 8. New APIs added in later versions are marked with a superscript to indicate their
> 
> - It is not recommended for developers to modify attribute data during animation.
> 
> - The maximum display rows differ between landscape and portrait modes. In portrait mode, the default is 5 rows. In landscape mode, it depends on the system configuration, and the default is 3 rows when not configured. You can view the specific configuration value through the following parameter: $r('sys.float.ohos_id_picker_show_count_landscape ').
> 
> - The multi-column non-linked data picker and the multi-column linkage data picker are collectively referred to as the multi-column data picker in the following sections.

## Child Components

This is a basic component, and it is not recommended to include child components.

## TextPicker

```TypeScript
TextPicker(options?: TextPickerOptions)
```

Creates a text picker based on the specified data list.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerInterface-(options?: TextPickerOptions): TextPickerAttribute--><!--Device-TextPickerInterface-(options?: TextPickerOptions): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md) | No | Parameters for configuring the text picker. Pass this parameter when you need to customize the data source, selected item, column width, and other configurations of the picker. If this parameter is not set, the component cannot be displayed. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md) | Define the divider configuration options. |
| [PickerBackgroundStyle](arkts-arkui-textpicker-comp-pickerbackgroundstyle-i.md) | Defines the background style configuration for selected picker items. |
| [TextCascadePickerRangeContent](arkts-arkui-textpicker-comp-textcascadepickerrangecontent-i.md) | Defines the content for multi-column picker options. |
| [TextPickerDialogOptions](arkts-arkui-textpicker-comp-textpickerdialogoptions-i.md) | Inherits from [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md). |
| [TextPickerDialogOptionsExt](arkts-arkui-textpicker-comp-textpickerdialogoptionsext-i.md) | Inherits from [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md). |
| [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md) | Defines the configuration options of the text picker. |
| [TextPickerRangeContent](arkts-arkui-textpicker-comp-textpickerrangecontent-i.md) | Defines the content for single-column picker options. |
| [TextPickerResult](arkts-arkui-textpicker-comp-textpickerresult-i.md) | Represents the selection result of a **TextPicker** component. |
| [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md) | Defines the text style options for the text picker. Inherits from [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md). |

### Types

| Name | Description |
| --- | --- |
| [OnTextPickerChangeCallback](arkts-arkui-textpicker-comp-ontextpickerchangecallback-t.md) | Defines the **onChange** event callback signature. |
| [TextPickerEnterSelectedAreaCallback](arkts-arkui-textpicker-comp-textpickerenterselectedareacallback-t.md) | Defines the **onEnterSelectedArea** event callback signature. |
| [TextPickerScrollStopCallback](arkts-arkui-textpicker-comp-textpickerscrollstopcallback-t.md) | Defines the **onScrollStop** event callback signature. |

## Examples

### Example 1: Setting the Number of Columns in the Picker

This example demonstrates how to configure single-column and multi-column text pickers by setting range and customizing the width of each column using columnWidths.

The columnWidths attribute of [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md) is added since API version 18.



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct TextPickerExample {
  private select: number = 1;
  private apfruits: string[] = ['apple1', 'apple2', 'apple3', 'apple4'];
  private orfruits: string[] = ['orange1', 'orange2', 'orange3', 'orange4'];
  private pefruits: string[] = ['peach1', 'peach2', 'peach3', 'peach4'];
  private multi: string[][] = [this.apfruits, this.orfruits, this.pefruits];
  private cascade: TextCascadePickerRangeContent[] = [
    {
      text: 'Liaoning Province',
      children: [{ text: 'Shenyang', children: [{ text: 'Shenhe District' }, { text: 'Heping District' }, { text: 'Hunnan District' }] },
        { text: 'Dalian', children: [{ text: 'Zhongshan District' }, { text: 'Jinzhou District' }, { text: 'Changhai County' }] }]
    },
    {
      text: 'Jilin Province',
      children: [{ text: 'Changchun', children: [{ text: 'Nanguan District' }, { text: 'Kuancheng District' }, { text: 'Chaoyang District' }] },
        { text: 'Siping', children: [{ text: 'Tiexi District' }, { text: 'Tiedong District' }, { text: 'Lishu County' }] }]
    },
    {
      text: 'Heilongjiang Province',
      children: [{ text: 'Harbin', children: [{ text: 'Daoli District' }, { text: 'Daowai District' }, { text: 'Nangang District' }] },
        { text: 'Mudanjiang', children: [{ text: `Dong'an District` }, { text: `Xi'an District` }, { text: 'Aimin District' }] }]
    }
  ];
  private singleColumnWidths: LengthMetrics[] = [
    LengthMetrics.percent(50)
  ];

  private multipleColumnWidths: LengthMetrics[] = [
    LengthMetrics.vp(100),
    LengthMetrics.vp(200),
    LengthMetrics.vp(100)
  ];

  private cascadeColumnWidths: LengthMetrics[] = [
    LengthMetrics.percent(20),
    LengthMetrics.percent(30),
    LengthMetrics.percent(50)
  ];
  build() {
    Column() {

      TextPicker({ range: this.apfruits, selected: this.select, columnWidths: this.singleColumnWidths })
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('Picker item changed, value: ' + value + ', index: ' + index);
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('Picker scroll stopped, value: ' + value + ', index: ' + index);
        }).margin({ bottom: 50 })
        .onEnterSelectedArea((value: string | string[], index: number | number[]) => {
          console.info('Picker item enter selected area, value: ' + value + ', index: ' + index);
        })

      TextPicker({ range: this.multi, columnWidths: this.multipleColumnWidths })
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('TextPicker multi-column: onChange ' + JSON.stringify(value) + ', ' + 'index: ' + JSON.stringify(index));
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('TextPicker multi-column: onScrollStop ' + JSON.stringify(value) + ', ' + 'index: ' + JSON.stringify(index));
        }).margin({ bottom: 50 })
        .onEnterSelectedArea((value: string | string[], index: number | number[]) => {
          console.info('TextPicker multi-column: onEnterSelectedArea ' + JSON.stringify(value) + ', ' + 'index: ' + JSON.stringify(index));
        })

      TextPicker({ range: this.cascade, columnWidths: this.cascadeColumnWidths })
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('TextPicker multi-column cascading: onChange ' + JSON.stringify(value) + ', ' + 'index: ' + JSON.stringify(index));
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('TextPicker multi-column cascading: onScrollStop ' + JSON.stringify(value) + ', ' + 'index: ' + JSON.stringify(index));
        })
        .onEnterSelectedArea((value: string | string[], index: number | number[]) => {
          console.info('TextPicker multi-column cascading: onEnterSelectedArea ' + JSON.stringify(value) + ', ' + 'index: ' + JSON.stringify(index));
        })
    }
  }
}
```

### Example 2: Setting the Text Style

This example demonstrates how to configure [disappearTextStyle](#disappeartextstyle10), [textStyle](#textstyle10), and [selectedTextStyle](#selectedtextstyle10) to customize the text style in the text picker.



```TypeScript
// xxx.ets
@Entry
@Component
struct TextPickerExample {
  private select: number = 0;
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4'];

  build() {
    Column() {
      TextPicker({
        range: this.fruits,
        selected: this.select,
        value: this.fruits[this.select]
      })
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('Picker item changed, value: ' + value + ', index: ' + index);
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('Picker scroll stopped, value: ' + value + ', index: ' + index);
        })
        .disappearTextStyle({ color: Color.Red, font: { size: 15, weight: FontWeight.Lighter } })
        .textStyle({ color: Color.Black, font: { size: 20, weight: FontWeight.Normal } })
        .selectedTextStyle({ color: Color.Blue, font: { size: 30, weight: FontWeight.Bolder } })
        .defaultPickerItemHeight(50)
        .canLoop(false)
        .selectedIndex(2)
    }.width('100%').height('100%')
  }
}
```

### Example 3: Using the No-Divider Style

This example demonstrates how to configure a text picker with no divider by setting [divider](#divider12) to null.



```TypeScript
// xxx.ets
@Entry
@Component
struct TextPickerExample {
  private select: number = 0;
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4'];

  build() {
    Column() {
      TextPicker({ range: this.fruits, selected: this.select })
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('Picker item changed, value: ' + value + ', index: ' + index);
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('Picker scroll stopped, value: ' + value + ', index: ' + index);
        })
        .disappearTextStyle({ color: Color.Red, font: { size: 15, weight: FontWeight.Lighter } })
        .textStyle({ color: Color.Black, font: { size: 20, weight: FontWeight.Normal } })
        .selectedTextStyle({ color: Color.Blue, font: { size: 30, weight: FontWeight.Bolder } })
        .divider(null)
    }.width('100%').height('100%')
  }
}
```

### Example 4: Using the Divider Style

This example demonstrates how to set the divider style for the text picker by configuring DividerOptions for divider.



```TypeScript
// xxx.ets
@Entry
@Component
struct TextPickerExample {
  private select: number = 1;
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4'];

  build() {
    Column() {
      TextPicker({ range: this.fruits, selected: this.select })
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('Picker item changed, value: ' + value + ', index: ' + index);
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('Picker scroll stopped, value: ' + value + ', index: ' + index);
        })
        .disappearTextStyle({ color: Color.Red, font: { size: 15, weight: FontWeight.Lighter } })
        .textStyle({ color: Color.Black, font: { size: 20, weight: FontWeight.Normal } })
        .selectedTextStyle({ color: Color.Blue, font: { size: 30, weight: FontWeight.Bolder } })
        .divider({
          strokeWidth: 10,
          color: Color.Red,
          startMargin: 10,
          endMargin: 20
        } as DividerOptions)
    }.width('100%').height('100%')
  }
}
```

### Example 5: Setting the Fade Effect

This example shows how to set the gradient effect height for the text picker by configuring [gradientHeight](#gradientheight12).



```TypeScript
// xxx.ets
@Entry
@Component
struct TextPickerExample {
  private select: number = 1;
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4'];

  build() {
    Column() {
      TextPicker({ range: this.fruits, selected: this.select })
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('Picker item changed, value: ' + value + ', index: ' + index);
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('Picker scroll stopped, value: ' + value + ', index: ' + index);
        })
        .disappearTextStyle({ color: Color.Red, font: { size: 15, weight: FontWeight.Lighter } })
        .textStyle({ color: Color.Black, font: { size: 20, weight: FontWeight.Normal } })
        .selectedTextStyle({ color: Color.Blue, font: { size: 30, weight: FontWeight.Bolder } })
        .gradientHeight(100)
    }.width('100%').height('100%')
  }
}
```

### Example 6: Setting the Item Height

This example demonstrates how to set the height of the picker items by configuring [defaultPickerItemHeight](#defaultpickeritemheight).



```TypeScript
// xxx.ets
@Entry
@Component
struct TextPickerExample {
  private select: number = 1;
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4'];

  build() {
    Column() {
      TextPicker({ range: this.fruits, selected: this.select })
        .defaultPickerItemHeight(60)
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('Picker item changed, value: ' + value + ', index: ' + index);
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('Picker scroll stopped, value: ' + value + ', index: ' + index);
        })
    }.width('100%').height('100%')
  }
}
```

### Example 7: Setting Loop Scrolling

This example demonstrates how to set whether to enable loop scrolling using [canLoop](#canloop10).



```TypeScript
// xxx.ets
@Entry
@Component
struct TextPickerExample {
  @State isLoop: boolean = false;
  private select: number = 1;
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4'];

  build() {
    Column() {
      TextPicker({ range: this.fruits, selected: this.select })
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('Picker item changed, value: ' + value + ', index: ' + index);
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('Picker scroll stopped, value: ' + value + ', index: ' + index);
        })
        .canLoop(this.isLoop)

      Row() {
        Text('Loopable scrolling').fontSize(20)

        Toggle({ type: ToggleType.Switch, isOn: false })
          .onChange((isOn: boolean) => {
            this.isLoop = isOn;
          })
      }.position({ x: '60%', y: '40%' })

    }.width('100%')
  }
}
```

### Example 8: Setting the Selected Item Index

This example demonstrates how to set the index of the default selected item by configuring [selectedIndex](#selectedindex10).



```TypeScript
// xxx.ets
@Entry
@Component
struct TextPickerExample {
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4'];

  build() {
    Column() {
      TextPicker({ range: this.fruits, selected: 1 })
        .selectedIndex(2)
        .onChange((value: string | string[], index: number | number[]) => {
          console.info('Picker item changed, value: ' + value + ', index: ' + index);
        })
        .onScrollStop((value: string | string[], index: number | number[]) => {
          console.info('Picker scroll stopped, value: ' + value + ', index: ' + index);
        })
    }.width('100%').height('100%')
  }
}
```

### Example 9: Disabling the Text Style Animation and Setting the Corresponding Text Style

This example demonstrates how to disable the text style change animation for the text picker and set the text style by configuring [disableTextStyleAnimation](#disabletextstyleanimation15) and [defaultTextStyle](#defaulttextstyle15).

The disableTextStyleAnimation and defaultTextStyle APIs are supported since API version 15.



```TypeScript
// xxx.ets
@Entry
@Component
struct TextPickerExample {
  private select: number = 1;
  private fruits: string[] = ['AAAAA', 'BBBBBBBBBBBBB', 'CCCC', 'DDDDDDDD', 'EEE'];

  build() {
    Column() {
      TextPicker({
        range: this.fruits,
        selected: this.select,
        value: this.fruits[this.select]
      })
        .disableTextStyleAnimation(true)
        .margin({ bottom: 30 })
      TextPicker({
        range: this.fruits,
        selected: this.select,
        value: this.fruits[this.select]
      })
        .disableTextStyleAnimation(true)
        .defaultTextStyle({ minFontSize: 18, maxFontSize: 28, overflow: TextOverflow.Ellipsis })
    }.width('100%').height('100%')
  }
}
```

### Example 10: Setting the Background Style of the Selected Item

This example shows how to set the background style of the selected item by configuring [selectedBackgroundStyle](#selectedbackgroundstyle20).



```TypeScript
import { LengthUnit } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct TextPickerExample {
  private showText1: string [] =
    ['Text1', 'Text1', 'Text1', 'Text1']
  private showText2: string[] [] =
    [
      ['Text2', 'Text2', 'Text2', 'Text2'],
      ['Text3', 'Text3', 'Text3', 'Text3']
  ]

  build() {
    Column() {
      Row() {
        TextPicker({ range: this.showText1 })
          .selectedBackgroundStyle({
            color: '#FFD5D5D5',
            borderRadius: { value: 0, unit: LengthUnit.VP }
          })
        Column()
          .width('10%')
        TextPicker({ range: this.showText1 })
          .selectedBackgroundStyle({
            color: '#FFE3F8F9',
            borderRadius: {
              topStart: { value: 5, unit: LengthUnit.VP },
              topEnd: { value: 10, unit: LengthUnit.VP },
              bottomStart: { value: 15, unit: LengthUnit.VP },
              bottomEnd: { value: 20, unit: LengthUnit.VP }
            }
          })
      }

      Row()
        .height('10%')
      Row() {
        TextPicker({ range: this.showText2 })
          .selectedBackgroundStyle({
            borderRadius: {
              topLeft: 8,
              topRight: 8,
              bottomLeft: 8,
              bottomRight: 8
            },
            color: '#FFFFEEF6'
          })
      }
    }.height('100%')
  }
}
```

### Example 11: Setting the Font Size Range and Text Overflow Mode

This example shows how to set the text color, maximum font size, minimum font size, and text overflow mode by configuring [disappearTextStyle](#disappeartextstyle20), [textStyle](#textstyle20), and [selectedTextStyle](#selectedtextstyle20).

The disappearTextStyle, textStyle, and selectedTextStyle APIs are supported since API version 20.

```TypeScript
// xxx.ets
@Entry
@Component
struct TextPickerExample {
  private rangeValue: string[] = ['AAAAA', 'BBBBBBBBBBBBB', 'CCCC', 'DDDDDDDD', 'EEEEEEEEEEEEEEE'];

  build() {
    RelativeContainer() {
      TextPicker({
        range: this.rangeValue
      })
        .disappearTextStyle({
          color: '#fff52769',
          // If minFontSize and maxFontSize are set, the size property in font is ignored.
          font: { size: 50 },
          minFontSize: 12,
          maxFontSize: 18,
          overflow: TextOverflow.Ellipsis
        })
        .textStyle({
          color: Color.Orange,
          minFontSize: 12,
          maxFontSize: 18,
          overflow: TextOverflow.MARQUEE
        })
        .selectedTextStyle({
          color: '#ff9eea48',
          minFontSize: 12,
          maxFontSize: 18,
          overflow: TextOverflow.Clip
        })
        .width('100%')
    }
    .height('100%')
    .width('100%')
  }
}
```
