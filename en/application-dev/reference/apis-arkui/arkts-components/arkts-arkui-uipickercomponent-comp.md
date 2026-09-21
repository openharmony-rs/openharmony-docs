# UIPickerComponent

The **UIPickerComponent** container is used to implement user selection operations. It supports single selection from a limited set of options and can be applied to various scenarios such as time selection, date selection, region selection, and status selection. Its display effect is a three-dimensional wheel style, supporting customizable options including text type, image type, and text-image combination type.

NOTE

- The height of the **UIPickerComponent** container options is fixed at 40 vp, and a maximum of seven options can
be displayed. Due to the three-dimensional wheel display effect, options other than the selected one will be rotated at different angles, so the actual visible height will be less than 40 vp.

- It is recommended that the [height](arkts-arkui-common-comp-commonmethod-c.md#height) of the **UIPickerComponent**
container be set to 200 vp. When the set height is greater than or equal to this recommended value, all 7 options can be fully displayed. Otherwise, the display area will be cropped from the top and bottom edges towards the center, and the number of displayed options will be reduced accordingly, always keeping the selected item vertically centered.

- When the **UIPickerComponent** container's [width](arkts-arkui-common-comp-commonmethod-c.md#width) is not set, the
maximum width of the visible child components in the current view is taken as the container width. You are advised to set the width of the **UIPickerComponent** container or set the same width for each child component to avoid dynamic changes in container width during sliding, which affects the display effect.

- The alignment mode of child components in the **UIPickerComponent** container is fixed to center alignment, and
cannot be changed via the [align](arkts-arkui-common-comp-commonmethod-c.md#align) attribute.

- Currently, the **UIPickerComponent** container does not support wearables.

- This component supports WithTheme since API version 26.0.0.

Child Components

- Multiple child components are supported.
- Supported child component types: Text, Image, Row, and
SymbolGlyph
- Supported rendering control types: [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) and
[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)

NOTE

- When the Row **container** is used as a child component, the **Row** container can contain only the **Text**,
**Image**, and **SymbolGlyph** basic components. Including other container components may affect the display effect or cause sliding functionality abnormalities.

- When counting the number of child components, the **Row** container and its child components are counted as one
child component.

- When the child component is **Text**, **Image**, or **SymbolGlyph**, the
[height](arkts-arkui-common-comp-commonmethod-c.md#height) attribute does not take effect and is fixed at 40 vp.

- When the child component is a **Row** container, its [height](arkts-arkui-common-comp-commonmethod-c.md#height) attribute
does not take effect and is fixed at 40 vp. The [height](arkts-arkui-common-comp-commonmethod-c.md#height) attribute of the child components in the **Row** container takes effect. The final display effect is determined by the **Row** container.

- The text-image combination option requires that the **Row** container contain the **Text** and **Image**
components. When using the text-image combination option, you are advised to set the image's [height](arkts-arkui-common-comp-commonmethod-c.md#height) to 40 vp or below to avoid cropping when images are large.

- The **fontSize** attribute of all text components (including the **Text** components in the **Row** container) in
the **UIPickerComponent** container is 20 fp by default. User settings will override the default value, and abnormal values will be processed according to the result of handling the text component's [fontSize](arkts-arkui-text-comp-attribute.md#fontsize). You are advised to set the **fontSize** attribute to a unified value or not to set it to ensure a good display effect.

## UIPickerComponent

```TypeScript
UIPickerComponent(options?: UIPickerComponentOptions)
```

Creates a **UIPickerComponent** container, whose selected item is determined by the **selectedIndex** attribute in the **options** parameter.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [UIPickerComponentOptions](arkts-arkui-uipickercomponent-comp-uipickercomponentoptions-i.md) | No | Parameters of the **UIPickerComponent** container. If the parameter is left empty, the component is a placeholder but the content is empty. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PickerIndicatorStyle](arkts-arkui-uipickercomponent-comp-pickerindicatorstyle-i.md) | Sets parameters of the selected item indicator style. |
| [UIPickerComponentOptions](arkts-arkui-uipickercomponent-comp-uipickercomponentoptions-i.md) | Describes the parameters of the **UIPickerComponent** container. |

### Types

| Name | Description |
| --- | --- |
| [OnUIPickerComponentCallback](arkts-arkui-uipickercomponent-comp-onuipickercomponentcallback-t.md) | Defines the callback types for the [onChange](arkts-arkui-uipickercomponent-comp-attribute.md#onchange) and [onScrollStop](arkts-arkui-uipickercomponent-comp-attribute.md#onscrollstop) events. |

### Enums

| Name | Description |
| --- | --- |
| [PickerIndicatorType](arkts-arkui-uipickercomponent-comp-pickerindicatortype-e.md) | Enumerates the types of the selected item indicator. |

## Examples

### Example 1: Switching Loop Scrolling and Enabling/Disabling Haptic Feedback

Since API version 22, this example demonstrates how to switch the loop scrolling of the UIPickerComponent container and how to enable or disable haptic feedback via button clicks.



```TypeScript
// xxx.ets
@Entry
@Component
struct UIPickerComponentAttrsExample {
  private dataArray: string[] = [];
  @State loop: boolean = true;
  @State hapticFeedback: boolean = true;

  aboutToAppear(): void {
    // Construct the option data.
    for (let i = 1; i <= 10; i++) {
      this.dataArray.push(i.toString())
    }
  }

  build() {
    Column() {
      Row() {
        UIPickerComponent() {
          ForEach(this.dataArray, (item: string) => {
            Text(item)
          })
        }
        // Configure the option list to loop.
        .canLoop(this.loop)
        // Configure haptic feedback.
        .enableHapticFeedback(this.hapticFeedback)
        .width('70%')
      }

      Column() {
        Row() {
          Toggle({ type: ToggleType.Switch, isOn: true })
            .onChange((isOn: boolean) => {
              this.loop = isOn;
            })
          Text('canLoop').fontSize(20)
        }
        .width('70%')

        Row() {
          Toggle({ type: ToggleType.Switch, isOn: true })
            .onChange((isOn: boolean) => {
              this.hapticFeedback = isOn;
            })
          Text('enableHapticFeedback').fontSize(20)
        }
        .width('70%')
      }

    }
    .width('100%')
  }
}
```

### Example 2: Setting Event Callbacks

Since API version 22, this example implements the onChange and onScrollStop event callbacks of the UIPickerComponent container based on status selection.

```TypeScript
// xxx.ets
@Entry
@Component
struct UIPickerComponentEventsExample {
  // Construct the status option data.
  private dataArray: string[] = ['To do', 'In progress', 'Completed'];
  @State onChangeDesc: string = '';
  @State onScrollStopDesc: string = '';
  @State index: number = 0;

  build() {
    Column() {
      Row() {
        UIPickerComponent({
          selectedIndex: this.index
        }) {
          ForEach(this.dataArray, (item: string) => {
            Text(item)
          })
        }
        // Configure the onChange event callback.
        .onChange((selectedIndex: number) => {
          this.index = selectedIndex;
          this.onChangeDesc = 'on change: ' + selectedIndex;
        })
        // Configure the onScrollStop event callback.
        .onScrollStop((selectedIndex: number) => {
          this.onScrollStopDesc = 'on scroll stop: ' + selectedIndex;
        })
        .width('70%')
      }

      Column() {
        Text(this.onChangeDesc)
        Text(this.onScrollStopDesc)
      }

    }
    .width('100%')
  }
}
```

### Example 3: Setting the Selected Item Index

Since API version 22, this example implements setting the selected item index of the UIPickerComponent container.



```TypeScript
// xxx.ets
@Entry
@Component
struct UIPickerComponentSelectedIndexExample {
  private dataArray: string[] = [];
  @State selectedIndex: number = 0;

  aboutToAppear(): void {
    // Construct the option data.
    for (let i = 1; i <= 10; i++) {
      this.dataArray.push(i.toString())
    }
  }

  build() {
    Column() {
      Row() {
        UIPickerComponent({
          // Configure the selected index value.
          selectedIndex: this.selectedIndex
        }) {
          ForEach(this.dataArray, (item: string) => {
            Text(item)
          })
        }
        .onChange((selectedIndex: number) => {
          this.selectedIndex = selectedIndex;
        })
        .onScrollStop((selectedIndex: number) => {
          this.selectedIndex = selectedIndex;
        })
        .width('70%')
      }

      Column() {
        Text('selectedIndex: ' + this.selectedIndex)
      }

    }
    .width('100%')
  }
}
```

### Example 4: Setting the Selected Item Indicator

Since API version 22, this example implements setting the selected item indicator of the UIPickerComponent container. Specifically, when a background indicator is used, set backgroundColor and borderRadius of [PickerIndicatorStyle](arkts-arkui-uipickercomponent-comp-pickerindicatorstyle-i.md); when a divider indicator is used, set strokeWidth, dividerColor, startMargin, and endMargin of [PickerIndicatorStyle](arkts-arkui-uipickercomponent-comp-pickerindicatorstyle-i.md).



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct UIPickerComponentIndicatorExample {
  private dataArray: string[] = [];
  @State indicatorType: Optional<PickerIndicatorType> = undefined;
  @State bgColor: Color | undefined = undefined;
  @State dividerColor: Color | undefined = undefined;
  @State strokeWidth: LengthMetrics = LengthMetrics.px(2);
  @State startMargin: LengthMetrics = LengthMetrics.px(2);
  @State endMargin: LengthMetrics = LengthMetrics.px(2);
  @State selectIndicator: PickerIndicatorStyle | undefined = undefined;
  @State bgBorderRadius: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses | undefined = undefined
  bgBorderRadiuses1: LengthMetrics = LengthMetrics.vp(10)
  bgBorderRadiuses2: BorderRadiuses = {
    topLeft: 10,
    bottomLeft: 0,
    topRight: 10,
    bottomRight: 0,
  }
  bgBorderRadiuses3: LocalizedBorderRadiuses = {
    topStart: LengthMetrics.vp(0),
    bottomStart: LengthMetrics.vp(10),
    topEnd: LengthMetrics.vp(0),
    bottomEnd: LengthMetrics.vp(10)
  }
  private controller: TabsController = new TabsController();
  @State curTabIndex: number = 0;

  @Builder
  dividerBuilder() {
    Column() {
      Row() {
        Text('Divider Stroke Width')
      }.margin(2)

      Row() {
        Button('0')
          .onClick(() => {
            this.strokeWidth = LengthMetrics.px(0)
          })
          .fontSize(12)
          .height(30)
          .width(100)
          .margin(2)
        Button('10px')
          .onClick(() => {
            this.strokeWidth = LengthMetrics.px(10)
          })
          .fontSize(12)
          .height(30)
          .width(100)
          .margin(2)
        Button('10vp')
          .onClick(() => {
            this.strokeWidth = LengthMetrics.vp(10)
          })
          .fontSize(12)
          .height(30)
          .width(100)
          .margin(2)
      }

      Row() {
        Text('Start margin')
      }.margin(2)

      Row() {
        Button('0')
          .onClick(() => {
            this.startMargin = LengthMetrics.px(0)
          })
          .fontSize(12)
          .height(30)
          .width(100)
          .margin(2)
        Button('10px')
          .onClick(() => {
            this.startMargin = LengthMetrics.px(10)
          })
          .fontSize(12)
          .height(30)
          .width(100)
          .margin(2)
        Button('10vp')
          .onClick(() => {
            this.startMargin = LengthMetrics.vp(10)
          })
          .fontSize(12)
          .height(30)
          .width(100)
          .margin(2)
      }

      Row() {
        Text('End Margin')
      }.margin(2)

      Row() {
        Button('0')
          .onClick(() => {
            this.endMargin = LengthMetrics.px(0)
          })
          .fontSize(12)
          .height(30)
          .width(100)
          .margin(2)
        Button('10px')
          .onClick(() => {
            this.endMargin = LengthMetrics.px(10)
          })
          .fontSize(12)
          .height(30)
          .width(100)
          .margin(2)
        Button('10vp')
          .onClick(() => {
            this.endMargin = LengthMetrics.vp(10)
          })
          .fontSize(12)
          .height(30)
          .width(100)
          .margin(2)
      }

      Row() {
        Text('Divider Color')
      }

      Row() {
        Button('Blue')
          .onClick(() => {
            this.dividerColor = Color.Blue
          })
          .fontSize(12)
          .height(30)
          .width(73)
          .margin(2)
        Button('Black')
          .onClick(() => {
            this.dividerColor = Color.Black
          })
          .fontSize(12)
          .height(30)
          .width(73)
          .margin(2)
      }

      Row() {
        Button('Ignore Custom Settings')
          .onClick(() => {
            this.dividerColor = undefined
          })
          .fontSize(12)
          .height(30)
          .width(150)
          .margin(2)
      }
    }
  }

  @Builder
  backgroundBuilder() {
    Column() {
      Row() {
        Text('Corner Radius Settings')
      }.margin(2)

      Column() {
        Button('Use LengthMetrics to Implement Unified Corner Radius')
          .onClick(() => {
            this.bgBorderRadius = this.bgBorderRadiuses1
          })
          .fontSize(12)
          .height(30)
          .width(300)
          .margin(2)
        Button('Use BorderRadiuses to Achieve Top Rounded, Bottom Square')
          .onClick(() => {
            this.bgBorderRadius = this.bgBorderRadiuses2
          })
          .fontSize(12)
          .height(30)
          .width(300)
          .margin(2)
        Button('Use LocalizedBorderRadiuses to Achieve Top Square, Bottom Rounded')
          .onClick(() => {
            this.bgBorderRadius = this.bgBorderRadiuses3
          })
          .fontSize(12)
          .height(30)
          .width(300)
          .margin(2)
      }.margin(2)

      Row() {
        Text('Background Color Settings')
      }.margin(2)

      Row() {
        Button('Blue')
          .onClick(() => {
            this.bgColor = Color.Blue
          })
          .fontSize(12)
          .height(30)
          .width(73)
          .margin(2)
        Button('Green')
          .onClick(() => {
            this.bgColor = Color.Green
          })
          .fontSize(12)
          .height(30)
          .width(73)
          .margin(2)
      }

      Row() {
        Button('Ignore Custom Settings')
          .onClick(() => {
            this.bgColor = undefined
          })
          .fontSize(12)
          .height(30)
          .width(150)
          .margin(2)
      }
    }
  }

  aboutToAppear(): void {
    // Construct the option data.
    for (let i = 1; i <= 10; i++) {
      this.dataArray.push(i.toString())
    }
  }

  build() {
    Column() {
      Row() {
        UIPickerComponent() {
          ForEach(this.dataArray, (item: string) => {
            Text(item)
          })
        }
        // Configure the selection indicator.
        .selectionIndicator({
          type: this.indicatorType,
          strokeWidth: this.strokeWidth,
          dividerColor: this.dividerColor,
          startMargin: this.startMargin,
          endMargin: this.endMargin,
          backgroundColor: this.bgColor,
          borderRadius: this.bgBorderRadius
        })
        .width('70%')
      }
      Tabs({ barPosition: BarPosition.Start, index: this.curTabIndex, controller: this.controller }) {
        TabContent() {
          this.backgroundBuilder()
        }.tabBar('Background Indicator')

        TabContent() {
          this.dividerBuilder()
        }.tabBar('Divider Indicator')
      }
      .vertical(false)
      .barMode(BarMode.Fixed)
      .barWidth(360)
      .barHeight(56)
      .animationDuration(400)
      .onChange((index: number) => {
        this.curTabIndex = index
        if (this.curTabIndex == 1) {
          this.indicatorType = PickerIndicatorType.DIVIDER
        } else {
          this.indicatorType = PickerIndicatorType.BACKGROUND
        }
      })
      .height(LayoutPolicy.wrapContent)
      .divider({ strokeWidth: 2 })
      .margin({ top: 20 })
      .backgroundColor('#F1F3F5')
    }
    .width('100%')
  }
}
```

### Example 5: Customizing the Month Picker

Since API version 22, this example uses the UIPickerComponent container with nested text child components to implement a month picker.



```TypeScript
// xxx.ets
@Entry
@Component
struct MonthUIPickerComponentExample {
  private fontSize: number | string | Resource = '20vp';
  private monthArray: string[] = [];

  aboutToAppear(): void {
    // Construct the option data.
    for (let i = 1; i <= 12; i++) {
      this.monthArray.push(i + 'month')
    }
  }

  build() {
    Column() {
      UIPickerComponent() {
        ForEach(this.monthArray, (item: string) => {
          Text(item)
            .fontSize(this.fontSize)
            .textAlign(TextAlign.Center)
            .fontColor(Color.Black)
        })
      }
      .width('70%')
      // Configure the option list to loop.
      .canLoop(true)
      // Disable haptic feedback.
      .enableHapticFeedback(false)
      // Set the selection indicator to a divider.
      .selectionIndicator({ type: PickerIndicatorType.DIVIDER })
      // Subscribe to the selection change event.
      .onChange((idx: number) => {
        console.info('UIPickerComponent item changed: ' + this.monthArray[idx]);
      })
      // Subscribe to the scroll stop event.
      .onScrollStop((idx: number) => {
        console.info('UIPickerComponent scroll stopped: ' + this.monthArray[idx]);
      })
    }
    .width('100%')
  }
}
```

### Example 6: Customizing the Area Picker

Since API version 22, this example uses a multi-column UIPickerComponent container combination to implement an area selector.



```TypeScript
// xxx.ets

type RegionDict = Record<string, Record<string, Array<string>>>;
// Define the region dictionary.
let regionData: RegionDict = {
  'Liaoning': {
    'Shenyang': ['Shenhe District', 'Heping District', 'Hunnan District'],
    'Dalian': ['Zhongshan District', 'Jinzhou District', 'Changhai County']
  },
  'Jilin': {
    'Changchun': ['Nanguan District', 'Kuancheng District', 'Chaoyang District'],
    'Siping': ['Tiexi District', 'Tiedong District', 'Lishu County']
  },
  'Heilongjiang': {
    'Harbin': ['Daoli District', 'Daowai District', 'Nangang District'],
    'Daqing': ['Honggang District', Longfeng District', Datong District']
  },
};

@Entry
@Component
struct RegionUIPickerComponentExample {
  @State provinceIndex: number = 0;
  @State cityIndex: number = 0;
  @State countyIndex: number = 0;
  @State provinces: Array<string> = [];
  @State cities: Array<string> = [];
  @State counties: Array<string> = [];

  aboutToAppear(): void {
    this.provinces = Object.keys(regionData);
    this.flushCityColumn()
  }

  flushCityColumn() {
    let currentProvince = this.provinces[this.provinceIndex]
    this.cities = Object.keys(regionData[currentProvince]);
    this.cityIndex = 0;
    this.flushCountyColumn()
  }

  flushCountyColumn() {
    let currentProvince = this.provinces[this.provinceIndex]
    let currentCity = this.cities[this.cityIndex]
    this.counties = regionData[currentProvince][currentCity];
    this.countyIndex = 0;
  }

  build() {
    Column() {
      Row() {
        // Provincial level
        UIPickerComponent({
          selectedIndex: this.provinceIndex
        }) {
          ForEach(this.provinces, (province: string) => {
            Text(province)
          })
        }
        .onChange((selectedIndex: number) => {
          this.provinceIndex = selectedIndex;
          this.flushCityColumn()

        })
        .onScrollStop((selectedIndex: number) => {
          this.provinceIndex = selectedIndex;
        })
        .selectionIndicator({ type: PickerIndicatorType.DIVIDER })
        .width('25%')

        // City
        UIPickerComponent({
          selectedIndex: this.cityIndex
        }) {
          ForEach(this.cities, (city: string) => {
            Text(city)
          })
        }
        .onChange((selectedIndex: number) => {
          this.cityIndex = selectedIndex;
          this.flushCountyColumn()
        })
        .onScrollStop((selectedIndex: number) => {
          this.cityIndex = selectedIndex;
        })
        .selectionIndicator({ type: PickerIndicatorType.DIVIDER })
        .width('25%')

        // County
        UIPickerComponent({
          selectedIndex: this.countyIndex
        }) {
          ForEach(this.counties, (county: string) => {
            Text(county)
          })
        }
        .onChange((selectedIndex: number) => {
          this.countyIndex = selectedIndex;
        })
        .onScrollStop((selectedIndex: number) => {
          this.countyIndex = selectedIndex;
        })
        .selectionIndicator({ type: PickerIndicatorType.DIVIDER })
        .width('25%')
      }
    }
    .width('100%')
  }
}
```

### Example 7: Customizing Option Types

Since API version 22, this example uses the UIPickerComponent container to implement pickers with different option types, including a text picker, an image picker, and a combined image-text picker.



```TypeScript
// xxx.ets
@Entry
@Component
struct UIPickerComponentExample {
  @State textList: string[] =
    ['text1', 'text2', 'text3', 'text4', 'text5', 'text6', 'text7', 'text8'];
  // The following $r('sys.media.*') resource files need to be replaced with the image resource files required by developers.
  @State imageList: Resource[] =
    [$r('sys.media.ohos_ic_normal_white_grid_audio'), $r('sys.media.ohos_ic_normal_white_grid_calendar'),
      $r('sys.media.ohos_ic_normal_white_grid_compress'), $r('sys.media.ohos_ic_normal_white_grid_doc'),
      $r('sys.media.ohos_ic_normal_white_grid_flac'), $r('sys.media.ohos_ic_normal_white_grid_folder'),
      $r('sys.media.ohos_ic_normal_white_grid_html'), $r('sys.media.ohos_ic_normal_white_grid_image')];
  // The following $r('sys.symbol.*') resource files need to be replaced with the image resource files required by developers.
  @State symbolList: Resource[] =
    [$r('sys.symbol.calendar_01'), $r('sys.symbol.calendar_02'), $r('sys.symbol.calendar_03'),
      $r('sys.symbol.calendar_04'), $r('sys.symbol.calendar_05'), $r('sys.symbol.calendar_06'),
      $r('sys.symbol.calendar_07'), $r('sys.symbol.calendar_08')];
  private controller: TabsController = new TabsController();
  @State curTabIndex: number = 0;

  @Builder
  ImagePicker() {
    Column() {
      UIPickerComponent() {
        ForEach(this.imageList, (item: Resource) => {
          Image(item)
        })
      }
      .margin(20)
      .width(200)
    }
  }

  @Builder
  TextPicker() {
    Column() {
      UIPickerComponent() {
        ForEach(this.textList, (item: string) => {
          Text(item)
        })
      }
      .margin(20)
      .width(200)
    }
  }

  @Builder
  HybridPicker() {
    Column() {
      UIPickerComponent() {
        ForEach(this.symbolList, (item: Resource, index: number) => {
          Row() {
            SymbolGlyph(item)
              .height('20vp')
            Text(this.textList[index])
          }
        })
      }
      .margin(20)
      .width(200)
    }
  }

  build() {
    Column() {
      Tabs({ barPosition: BarPosition.Start, index: this.curTabIndex, controller: this.controller }) {
        TabContent() {
          this.TextPicker()
        }.tabBar('Text Picker')

        TabContent() {
          this.ImagePicker()
        }.tabBar('Image Picker')

        TabContent() {
          this.HybridPicker()
        }.tabBar('Text-Image Picker')
      }
      .vertical(true)
      .divider({ strokeWidth: 1 })
      .barMode(BarMode.Fixed)
      .barWidth(140)
      .barHeight(230)
      .height(230)
      .animationDuration(400)
    }
  }
}
```

### Example 8: Customizing the Time Picker

Since API version 22, this example implements a time picker with the following features: setting whether to loop scrolling, whether to display seconds, whether to use the 24-hour format, and whether to display leading zeros. It can also display content in the language corresponding to the current system language and adjust the display order of each column based on language habits.

> NOTE
> 
> In this example, the content of each column of the time picker is displayed in the language corresponding to the system language. For example, an English system displays AM/PM, while a Chinese system displays morning/afternoon.
> 
> In this example, the display order of each column of the time picker is adjusted according to the system language. For example, an English system displays hour/minute/second/AMPM, while a Chinese system displays morning/afternoon/hour/minute/second.

To make "morning/afternoon" switch with the system language, you need to add the corresponding language translations in the resource directory of the project. For example:

Chinese (default): Create a base directory under the resource directory, create an element directory under the base directory, and add a string.json file under the element directory (if the file already exists, append the following "name"-"value" key-value pairs to the file instead of overwriting the original file). The file content is as follows:

```TypeScript
{
  "string": [
    {
      "name": "app_name",
      "value": "timePicker"
    },
    {
      "name": "am",
      "value": "AM"
    },
    {
      "name": "pm",
      "value": "PM"
    }
  ]
}
```

English: Create the en directory under the resource directory, create the element directory under the en directory, and add the string.json file under the element directory (if the file already exists, append the following "name"-"value" key-value pairs to the file instead of overwriting the original file). The file content is as follows:

```TypeScript
{
  "string": [
    {
      "name": "app_name",
      "value": "timePicker"
    },
    {
      "name": "am",
      "value": "AM"
    },
    {
      "name": "pm",
      "value": "PM"
    }
  ]
}
```

Arabic: Create the ar directory under the resource directory, create the element directory under the ar directory, and add the string.json file under the element directory (if the file already exists, append the following "name"-"value" key-value pairs to the file instead of overwriting the original file). The file content is as follows:

```TypeScript
{
  "string": [
    {
      "name": "app_name",
      "value": "timePicker"
    },
    {
      "name": "am",
      "value": "ص"
    },
    {
      "name": "pm",
      "value": "م"
    }
  ]
}
```

The same applies to other languages.

The sample code is as follows:



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';
import { i18n, intl } from '@kit.LocalizationKit';
import { commonEventManager } from '@kit.BasicServicesKit';

@Entry
@Component
struct TimeUIPickerComponentExample {
  @State showSecond: boolean = false;
  @State useMilitary: boolean = false;
  @State zeroPrefix: boolean = true;
  @State loop: boolean = true;
  @State amPmAtLast: boolean = false
  @State isRtl: boolean = false;

  startBorderStyle: LocalizedBorderRadiuses = {
    topStart: LengthMetrics.px(40),
    bottomStart: LengthMetrics.px(40),
    topEnd: LengthMetrics.px(0),
    bottomEnd: LengthMetrics.px(0)
  }
  centerBorderStyle: LengthMetrics = LengthMetrics.px(0)
  endBorderStyle: LocalizedBorderRadiuses = {
    topStart: LengthMetrics.px(0),
    bottomStart: LengthMetrics.px(0),
    topEnd: LengthMetrics.px(40),
    bottomEnd: LengthMetrics.px(40)
  }
  @State amPmBorder: LengthMetrics | LocalizedBorderRadiuses = this.startBorderStyle;
  @State hourBorder: LengthMetrics | LocalizedBorderRadiuses = this.startBorderStyle;
  @State minBorder: LengthMetrics | LocalizedBorderRadiuses = this.endBorderStyle;
  @State secBorder: LengthMetrics | LocalizedBorderRadiuses = this.endBorderStyle;

  @State amPmIndex: number = 0;
  @State hourIndex: number = 0;
  @State minIndex: number = 0;
  @State secIndex: number = 0;

  @State amPmArr: Array<string| undefined> = []
  @State hourArr: Array<string> = []
  @State minSecArr: Array<string> = []

  @State currentTime: string = '';

  sysLanguageChanged: boolean = false
  zero: string = '0'
  systemLanguage: string = i18n.System.getSystemLanguage();
  // Create a NumberFormat object using the current system locale ID.
  formatter: intl.NumberFormat = new intl.NumberFormat();
  private subscriber: commonEventManager.CommonEventSubscriber | undefined = undefined;

  aboutToAppear(): void {
    this.zero = this.formatter.format(0)
    this.flushAmPmColumn()
    this.flushHourColumn()
    this.flushMinSecColumn()
    this.flushCurrentTime()
    this.flushBorderStyle()
    let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
      events: [commonEventManager.Support.COMMON_EVENT_LOCALE_CHANGED]
    };
    // Create a subscriber to listen for system language changes.
    commonEventManager.createSubscriber(subscribeInfo)
      .then((commonEventSubscriber: commonEventManager.CommonEventSubscriber) => {
        console.info("CreateSubscriber");
        this.subscriber = commonEventSubscriber;
        commonEventManager.subscribe(this.subscriber, (err, data) => {
          if (err) {
            console.error(`Failed to subscribe common event. error code: ${err.code}, message: ${err.message}.`);
            return;
          }
          this.formatter = new intl.NumberFormat();
          this.zero = this.formatter.format(0);
          this.sysLanguageChanged = true;
          this.systemLanguage = i18n.System.getSystemLanguage();
          this.flushAmPmColumn()
          this.flushHourColumn()
          this.flushMinSecColumn()
          this.flushCurrentTime()
          this.flushBorderStyle()
        })
      })
      .catch((err: BusinessError) => {
        console.error(`CreateSubscriber failed, code is ${err.code}, message is ${err.message}`);
      });
  }

  // Refresh the UI state after the system language changes.
  aboutToDisappear(): void {
    if (this.subscriber) {
      commonEventManager.unsubscribe(this.subscriber, (err) => {
        if (err) {
          console.error(`Failed to unsubscribe common event. error code: ${err.code}, message: ${err.message}.`);
        }
      });
    }
  }

  onPageShow(): void {
    if (this.sysLanguageChanged) {
      this.flushAmPmColumn()
      this.flushCurrentTime()
      this.flushBorderStyle()
      this.sysLanguageChanged = false
    }
  }

  buildColumnOptions(start: number, end: number, isHour: boolean = false) : string[] {
    let newOptions: string[] = []
    for (let i = start; i <= end; i++) {
      if (isHour && i == 0 && !this.useMilitary) {
        newOptions.push(this.formatter.format(12))
        continue
      }
      if (this.zeroPrefix) {
        newOptions.push(this.formatTime(i))
      } else {
        newOptions.push(this.formatter.format(i))
      }
    }
    return newOptions
  }

  flushAmPmColumn() {
    // Set whether the amPm column is placed last based on language conventions.
    if (this.systemLanguage.startsWith('en') || this.systemLanguage == 'ug') {
      this.amPmAtLast = true
    } else {
      this.amPmAtLast = false
    }
    this.amPmArr = [];
    this.amPmArr[0] = this.getUIContext().getHostContext()?.resourceManager.getStringSync($r('app.string.am').id)
    this.amPmArr[1] = this.getUIContext().getHostContext()?.resourceManager.getStringSync($r('app.string.pm').id)
  }

  flushHourColumn() {
    if (this.useMilitary) {
      this.hourArr = this.buildColumnOptions(0, 23)
    } else {
      this.hourArr = this.buildColumnOptions(0, 11, true)
    }
  }

  flushMinSecColumn() {
    this.minSecArr = this.buildColumnOptions(0, 59)
  }

  flushBorderStyle() {
    let realStartBorder = this.startBorderStyle
    let realEndBorder = this.endBorderStyle
    // Set the time order of mirror languages based on language conventions.
    if (this.systemLanguage == 'ar' || this.systemLanguage == 'ug') {
      this.isRtl = true
      realStartBorder = this.endBorderStyle
      realEndBorder = this.startBorderStyle
    } else {
      this.isRtl = false
    }
    if (!this.useMilitary) {
      if (this.amPmAtLast) {
        this.amPmBorder = realEndBorder
        this.hourBorder = realStartBorder
        this.minBorder = this.centerBorderStyle
        this.secBorder = this.centerBorderStyle
      } else {
        this.amPmBorder = realStartBorder
        this.hourBorder = this.centerBorderStyle
        if (this.showSecond) {
          this.minBorder = this.centerBorderStyle
        } else {
          this.minBorder = realEndBorder
        }
        this.secBorder = realEndBorder
      }
    } else {
      this.hourBorder = realStartBorder
      if (this.showSecond) {
        this.minBorder = this.centerBorderStyle
      } else {
        this.minBorder = realEndBorder
      }
      this.secBorder = realEndBorder
    }
  }

  formatTime(time: number): string {
    if (time < 10) {
      return this.zero + this.formatter.format(time)
    }
    return this.formatter.format(time)
  }

  @Builder
  buildAmPmColumn() {
    UIPickerComponent({ selectedIndex: this.amPmIndex }) {
      ForEach(this.amPmArr, (amPm: string | undefined) => {
        Text(amPm ?? '')
      })
    }
    .width('200px')
    .canLoop(this.loop)
    .selectionIndicator({
      type: PickerIndicatorType.BACKGROUND,
      borderRadius: this.amPmBorder
    })
    .onChange((selectedIndex: number) => {
      this.amPmIndex = selectedIndex
      this.flushCurrentTime()
    })
    .onScrollStop((selectedIndex: number) => {
      this.amPmIndex = selectedIndex
      this.flushCurrentTime()
    })
  }

  @Builder
  buildHourColumn() {
    UIPickerComponent({ selectedIndex: this.hourIndex }) {
      ForEach(this.hourArr, (hour: string) => {
        Text(hour)
      })
    }
    .width('200px')
    .canLoop(this.loop)
    .selectionIndicator({
      type: PickerIndicatorType.BACKGROUND,
      borderRadius: this.hourBorder
    })
    .onChange((selectedIndex: number) => {
      this.hourIndex = selectedIndex
      this.flushCurrentTime()
    })
    .onScrollStop((selectedIndex: number) => {
      this.hourIndex = selectedIndex
      this.flushCurrentTime()
    })
  }

  @Builder
  buildMinColumn() {
    UIPickerComponent({ selectedIndex: this.minIndex }) {
      ForEach(this.minSecArr, (min: string) => {
        Text(min)
      })
    }
    .width('200px')
    .canLoop(this.loop)
    .selectionIndicator({
      type: PickerIndicatorType.BACKGROUND,
      borderRadius: this.minBorder
    })
    .onChange((selectedIndex: number) => {
      this.minIndex = selectedIndex
      this.flushCurrentTime()
    })
    .onScrollStop((selectedIndex: number) => {
      this.minIndex = selectedIndex
      this.flushCurrentTime()
    })
  }

  @Builder
  buildSecColumn() {
    UIPickerComponent({ selectedIndex: this.secIndex }) {
      ForEach(this.minSecArr, (sec: string) => {
        Text(sec)
      })
    }
    .width('200px')
    .canLoop(this.loop)
    .selectionIndicator({
      type: PickerIndicatorType.BACKGROUND,
      borderRadius: this.secBorder
    })
    .onChange((selectedIndex: number) => {
      this.secIndex = selectedIndex
      this.flushCurrentTime()
    })
    .onScrollStop((selectedIndex: number) => {
      this.secIndex = selectedIndex
      this.flushCurrentTime()
    })
  }

  flushCurrentTime() {
    this.currentTime = ''
    if (!this.useMilitary) {
      this.currentTime += this.amPmArr[this.amPmIndex] + ' ';
    }
    this.currentTime += this.hourArr[this.hourIndex] + ':' + this.minSecArr[this.minIndex];
    if (this.showSecond) {
      this.currentTime += ':' + this.minSecArr[this.secIndex];
    }
  }

  build() {
    Column() {
      Row() {
        // Create columns in the display order based on the mirrored language.
        if (!this.isRtl) {
          if (!this.useMilitary && !this.amPmAtLast) {
            this.buildAmPmColumn()
            this.buildHourColumn()
          } else {
            this.buildHourColumn()
          }
          this.buildMinColumn()
          if (this.showSecond) {
            this.buildSecColumn()
          }
          if (!this.useMilitary && this.amPmAtLast) {
            this.buildAmPmColumn()
          }
        } else {
          if (!this.useMilitary && this.amPmAtLast) {
            this.buildAmPmColumn()
          }
          if (this.showSecond) {
            this.buildSecColumn()
          }
          this.buildMinColumn()
          if (!this.useMilitary && !this.amPmAtLast) {
            this.buildHourColumn()
            this.buildAmPmColumn()
          } else {
            this.buildHourColumn()
          }
        }
      }

      Row() {
        Text('selected time: ' + this.currentTime)
          .margin(5)
          .width("80%")
          .textAlign(TextAlign.Center)
      }
      .border({ width: 1 })
      .margin(5)

      Column() {
        Row() {
          Toggle({ type: ToggleType.Switch, isOn: true })
            .onChange((isOn: boolean) => {
              this.loop = isOn;
            })
          Text('loop').fontSize(20)
        }.width(200).margin(5)
        Row() {
          Toggle({ type: ToggleType.Switch, isOn: false })
            .onChange((isOn: boolean) => {
              this.showSecond = isOn
              this.flushCurrentTime()
              this.flushBorderStyle()
            })
          Text('show second').fontSize(20)
        }.width(200).margin(5)
        Row() {
          Toggle({ type: ToggleType.Switch, isOn: false })
            .onChange((isOn: boolean) => {
              this.useMilitary = isOn
              if (this.useMilitary) {
                if (this.amPmIndex) {
                  this.hourIndex += 12;
                }
              } else {
                if (this.hourIndex >= 12) {
                  this.amPmIndex = 1;
                  this.hourIndex -= 12;
                } else {
                  this.amPmIndex = 0;
                }
              }
              this.flushBorderStyle()
              this.flushHourColumn()
              this.flushCurrentTime()
            })
          Text('use military').fontSize(20)
        }.width(200).margin(5)
        Row() {
          Toggle({ type: ToggleType.Switch, isOn: true })
            .onChange((isOn: boolean) => {
              this.zeroPrefix = isOn
              this.flushHourColumn()
              this.flushMinSecColumn()
              this.flushCurrentTime()
            })
          Text('2-digits').fontSize(20)
        }.width(200).margin(5)
      }
    }
    .width('100%')
  }
}
```

### Example 9: Setting the Item Height

This example uses [itemHeight](#itemheight) to set the item height of the UIPickerComponent container.

Since API version 26.0.0, the [itemHeight](#itemheight) attribute is added.

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct UIPickerComponentItemHeightExample {
  private dataArray: string[] = [];
  @State pickerItemHeight: LengthMetrics | undefined = undefined;
  @State selectedIndex: number = 0;

  aboutToAppear(): void {
    for (let i = 1; i <= 10; i++) {
      this.dataArray.push('Item' + i)
    }
  }

  build() {
    Column({ space: 12 }) {
      Text('Current itemHeight: ' + (this.pickerItemHeight ? this.pickerItemHeight.value + 'vp' : 'Default value (40vp)'))
        .fontSize(16)

      UIPickerComponent({
        selectedIndex: this.selectedIndex
      }) {
        ForEach(this.dataArray, (item: string) => {
          Text(item)
        })
      }
      .width('70%')
      .itemHeight(this.pickerItemHeight)
      .onChange((selectedIndex: number) => {
        this.selectedIndex = selectedIndex
      })

      Row({ space: 12 }) {
        Button('40vp')
          .onClick(() => {
            this.pickerItemHeight = LengthMetrics.vp(40)
          })
        Button('50vp')
          .onClick(() => {
            this.pickerItemHeight = LengthMetrics.vp(50)
          })
        Button('64vp')
          .onClick(() => {
            this.pickerItemHeight = LengthMetrics.vp(64)
          })
      }
    }
    .width('100%')
    .padding(16)
  }
}
```

### Example 10: Setting the Number of Visible Items

This example uses [displayedItemCount](arkts-arkui-uipickercomponent-comp-attribute.md#displayeditemcount) to set the number of visible items in the UIPickerComponent container.

Since API version 26.0.0, the [displayedItemCount](arkts-arkui-uipickercomponent-comp-attribute.md#displayeditemcount) attribute is added.

```TypeScript
// xxx.ets
@Entry
@Component
struct UIPickerComponentDisplayedCountExample {
  private dataArray: string[] = [];
  @State visibleCount: number = 7;
  @State selectedIndex: number = 0;

  aboutToAppear(): void {
    for (let i = 1; i <= 12; i++) {
      this.dataArray.push('Item' + i)
    }
  }

  build() {
    Column({ space: 12 }) {
      Text('displayedItemCount: ' + this.visibleCount)
        .fontSize(16)

      UIPickerComponent({
        selectedIndex: this.selectedIndex
      }) {
        ForEach(this.dataArray, (item: string) => {
          Text(item)
        })
      }
      .onChange((selectedIndex: number) => {
        this.selectedIndex = selectedIndex
      })
      .width('70%')
      .displayedItemCount(this.visibleCount)

      Row({ space: 12 }) {
        Button('Item 3')
          .width(120)
          .height(40)
          .onClick(() => {
            this.visibleCount = 3
          })
        Button('Item 5')
          .width(120)
          .height(40)
          .onClick(() => {
            this.visibleCount = 5
          })
        Button('Item 8 (auto changes to 9)')
          .width(120)
          .height(40)
          .onClick(() => {
            this.visibleCount = 8
          })
      }
    }
    .width('100%')
    .padding(16)
  }
}
```
