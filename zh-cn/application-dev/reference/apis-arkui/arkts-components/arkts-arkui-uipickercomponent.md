# UIPickerComponent

UIPickerComponent容器是用于实现用户选择操作的组件。它支持从一组有限的选项中让用户进行单选，采用立体滚轮样式提供直观的视觉反馈和流畅的滑动 体验。该组件支持选项按需定制，包括文本类型、图片类型和图文组合类型，可根据业务需求提供更丰富的信息展示，可广泛应用于时间选择、日期选择、地区选 择、状态选择等多种场景。
> **说明：** > > - UIPickerComponent容器默认选项行高为40vp，默认显示7个选项。可通过[itemHeight](arkts-arkui-uipickercomponent-attribute.md#itemheight) > 和[displayedItemCount](arkts-arkui-uipickercomponent-attribute.md#displayeditemcount)属性进行配置。由于显示效果为立体滚轮样式，因此除 > 选中项外的其他选项会进行不同角度的旋转，实际的可视高度会小于选项行高。 > > - UIPickerComponent容器的height建议设置为200vp。当设置的高度大于等于该建议值时， > 可完整显示默认的7个选项；若通过[displayedItemCount](arkts-arkui-uipickercomponent-attribute.md#displayeditemcount)或 > [itemHeight](arkts-arkui-uipickercomponent-attribute.md#itemheight)配置了更多可见项或更大选项高度，建议相应增大组件高度。设置高度小于建议 > 值时，显示范围会从上下边缘向中间裁剪，可显示的选项数量也会相应减少，始终保持选中项垂直居中。 > > - 当UIPickerComponent容器未设置width时，取当前视图中可见子组件的最大宽度作为容器宽 > 度。建议为UIPickerComponent容器设置宽度，或为每个子组件设置相同宽度，以避免滑动过程中容器宽度动态发生变化，影响显示效果。 > > - UIPickerComponent容器的子组件的对齐方式固定为居中对齐，不支持通过align属性改 > 变子组件的对齐方式。 > > - UIPickerComponent容器当前不支持智能手表设备。开发者可通过deviceInfo.deviceType获取设备类型，判断是否为智能手表设备。 > > - 该组件从API版本26.0.0开始支持WithTheme。
>

## 子组件 > > - 支持多个子组件。 > - 支持子组件类型：Text、Image、Row和SymbolGlyph。 > - 支持渲染控制类型：[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)和 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)。


> **说明：**
> 
> - 开发者在使用Row容器作为子组件时，Row容器中仅支持包含Text、Image、SymbolGlyph基础组件，
> 包含其他容器组件可能会影响显示效果或滑动功能异常。
> 
> - 统计子组件的个数时，不包含Row容器内的子组件，Row容器及其子组件共同视为1个子组件。
> 
> - 子组件为Text、Image、SymbolGlyph时，height属性不生效，实际高度由
> [itemHeight](arkts-arkui-uipickercomponent-attribute.md#itemheight)属性决定（默认40vp）。子组件内容会在选项区域内显示。
> 
> - 子组件为Row容器时，Row容器的height属性不生效，实际高度由
> [itemHeight](arkts-arkui-uipickercomponent-attribute.md#itemheight)属性决定（默认40vp）。Row容器内的子组件
> height属性能正常生效，最终显示效果由Row容器决定。
> 
> - 图文组合类型选项需要使用Row容器包含图片和文本组件。使用图文组合类型选项时，
> 建议将图片的height设置为40vp及以下，避免图片较大时被裁剪。
> 
> - UIPickerComponent容器内所有文本组件（包括Row容器内的文本组件）的fontSize属性默认为20fp。用户设置将覆盖默认值，
> 设置异常值时以文本组件fontSize处理的结果为准。建议统一设置或不设置fontSize以保证良好的显示效果。

## UIPickerComponent

```TypeScript
UIPickerComponent(options?: UIPickerComponentOptions)
```

创建UIPickerComponent容器，其选中项由options参数中的selectedIndex属性值决定。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [UIPickerComponentOptions](arkts-arkui-uipickercomponentoptions-i.md) | 否 | 配置UIPickerComponent容器的参数，用于自定义初始选中项等配置。参数缺省时组件占 位，但内容显示为空。当需要设置初始选中项时传入此参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [PickerIndicatorStyle](arkts-arkui-pickerindicatorstyle-i.md) | 选中项指示器样式的参数说明。 |
| [UIPickerComponentOptions](arkts-arkui-uipickercomponentoptions-i.md) | UIPickerComponent容器的参数说明。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnUIPickerComponentCallback](arkts-arkui-onuipickercomponentcallback-t.md) | 定义[onChange](arkts-arkui-uipickercomponent-attribute.md#onchange)和 [onScrollStop](arkts-arkui-uipickercomponent-attribute.md#onscrollstop)事件的回调类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PickerIndicatorType](arkts-arkui-pickerindicatortype-e.md) | 设置选中项指示器的类型。 |

## 示例

从API version 22开始，该示例通过点击按钮的方式实现切换UIPickerComponent容器的循环滚动和开启/关闭触控反馈功能。

```TypeScript
// xxx.ets
@Entry
@Component
struct UIPickerComponentAttrsExample {
  private dataArray: string[] = [];
  @State loop: boolean = true;
  @State hapticFeedback: boolean = true;

  aboutToAppear(): void {
    // 构造选项数据
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
        // 配置选项列表循环
        .canLoop(this.loop)
        // 配置触控反馈
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

从API version 22开始，该示例基于状态选择实现UIPickerComponent容器的onChange和onScrollStop事件回调。

```TypeScript
// xxx.ets
@Entry
@Component
struct UIPickerComponentEventsExample {
  // 构造状态选项数据
  private dataArray: string[] = ['待办', '进行中', '已完成'];
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
        // 配置onChange事件回调
        .onChange((selectedIndex: number) => {
          this.index = selectedIndex;
          this.onChangeDesc = 'on change: ' + selectedIndex;
        })
        // 配置onScrollStop事件回调
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

从API version 22开始，该示例实现了设置UIPickerComponent容器的选中项索引值。

```TypeScript
// xxx.ets
@Entry
@Component
struct UIPickerComponentSelectedIndexExample {
  private dataArray: string[] = [];
  @State selectedIndex: number = 0;

  aboutToAppear(): void {
    // 构造选项数据
    for (let i = 1; i <= 10; i++) {
      this.dataArray.push(i.toString())
    }
  }

  build() {
    Column() {
      Row() {
        UIPickerComponent({
          // 配置选中项索引值
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

从API version 22开始，该示例实现了设置UIPickerComponent容器的选中项指示器。具体包括：在使用背景指示器时，设置[PickerIndicatorStyle](#pickerindicatorstyle对象说明)的backgroundColor、borderRadius；在使用分割线指示器时，设置[PickerIndicatorStyle](#pickerindicatorstyle对象说明)的strokeWidth、dividerColor、startMargin、endMargin。

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
        Text('分割线线宽')
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
        Text('起始侧边距')
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
        Text('结束侧边距')
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
        Text('分割线颜色')
      }

      Row() {
        Button('蓝色')
          .onClick(() => {
            this.dividerColor = Color.Blue
          })
          .fontSize(12)
          .height(30)
          .width(73)
          .margin(2)
        Button('黑色')
          .onClick(() => {
            this.dividerColor = Color.Black
          })
          .fontSize(12)
          .height(30)
          .width(73)
          .margin(2)
      }

      Row() {
        Button('不使用自定义设置')
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
        Text('圆角设置')
      }.margin(2)

      Column() {
        Button('使用LengthMetrics，实现统一圆角')
          .onClick(() => {
            this.bgBorderRadius = this.bgBorderRadiuses1
          })
          .fontSize(12)
          .height(30)
          .width(300)
          .margin(2)
        Button('使用BorderRadiuses，实现上圆下方')
          .onClick(() => {
            this.bgBorderRadius = this.bgBorderRadiuses2
          })
          .fontSize(12)
          .height(30)
          .width(300)
          .margin(2)
        Button('使用LocalizedBorderRadiuses，实现上方下圆')
          .onClick(() => {
            this.bgBorderRadius = this.bgBorderRadiuses3
          })
          .fontSize(12)
          .height(30)
          .width(300)
          .margin(2)
      }.margin(2)

      Row() {
        Text('背景色设置')
      }.margin(2)

      Row() {
        Button('蓝色')
          .onClick(() => {
            this.bgColor = Color.Blue
          })
          .fontSize(12)
          .height(30)
          .width(73)
          .margin(2)
        Button('绿色')
          .onClick(() => {
            this.bgColor = Color.Green
          })
          .fontSize(12)
          .height(30)
          .width(73)
          .margin(2)
      }

      Row() {
        Button('不使用自定义设置')
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
    // 构造选项数据
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
        // 配置选中项指示器
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
        }.tabBar('背景指示器')

        TabContent() {
          this.dividerBuilder()
        }.tabBar('分割线指示器')
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

从API version 22开始，该示例使用UIPickerComponent容器嵌套文本子组件的方式实现月份选择器。

```TypeScript
// xxx.ets
@Entry
@Component
struct MonthUIPickerComponentExample {
  private fontSize: number | string | Resource = '20vp';
  private monthArray: string[] = [];

  aboutToAppear(): void {
    // 构造选项数据
    for (let i = 1; i <= 12; i++) {
      this.monthArray.push(i + '月')
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
      // 配置选项列表循环
      .canLoop(true)
      // 配置触控反馈为关闭
      .enableHapticFeedback(false)
      // 配置选中项的指示器标识为分割线
      .selectionIndicator({ type: PickerIndicatorType.DIVIDER })
      // 订阅选中项改变事件
      .onChange((idx: number) => {
        console.info('UIPickerComponent item changed: ' + this.monthArray[idx]);
      })
      // 订阅滑动停止事件
      .onScrollStop((idx: number) => {
        console.info('UIPickerComponent scroll stopped: ' + this.monthArray[idx]);
      })
    }
    .width('100%')
  }
}
```

从API version 22开始，该示例使用多列UIPickerComponent容器组合实现地区选择器。

```TypeScript
// xxx.ets

type RegionDict = Record<string, Record<string, Array<string>>>;
// 定义地区字典
let regionData: RegionDict = {
  '辽宁省': {
    '沈阳市': ['沈河区', '和平区', '浑南区'],
    '大连市': ['中山区', '金州区', '长海县']
  },
  '吉林省': {
    '长春市': ['南关区', '宽城区', '朝阳区'],
    '四平市': ['铁西区', '铁东区', '梨树县']
  },
  '黑龙江省': {
    '哈尔滨市': ['道里区', '道外区', '南岗区'],
    '牡丹江市': ['东安区', '西安区', '爱民区']
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
        // 省级
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

        // 地级
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

        // 县级
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

从API version 22开始，该示例使用UIPickerComponent容器实现不同选项类型的选择器，包含文本选择器、图片选择器、图文组合选择器。

```TypeScript
// xxx.ets
@Entry
@Component
struct UIPickerComponentExample {
  @State textList: string[] =
    ['text1', 'text2', 'text3', 'text4', 'text5', 'text6', 'text7', 'text8'];
  // 以下$r('sys.media.*')资源文件需要替换为开发者所需的图像资源文件。
  @State imageList: Resource[] =
    [$r('sys.media.ohos_ic_normal_white_grid_audio'), $r('sys.media.ohos_ic_normal_white_grid_calendar'),
      $r('sys.media.ohos_ic_normal_white_grid_compress'), $r('sys.media.ohos_ic_normal_white_grid_doc'),
      $r('sys.media.ohos_ic_normal_white_grid_flac'), $r('sys.media.ohos_ic_normal_white_grid_folder'),
      $r('sys.media.ohos_ic_normal_white_grid_html'), $r('sys.media.ohos_ic_normal_white_grid_image')];
  // 以下$r('sys.symbol.*')资源文件需要替换为开发者所需的图像资源文件。
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
        }.tabBar('文本选择器')

        TabContent() {
          this.ImagePicker()
        }.tabBar('图片选择器')

        TabContent() {
          this.HybridPicker()
        }.tabBar('图文组合选择器')
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

中文（默认）：在resource目录下创建base目录，在base目录下创建element目录，在element目录添加string.json文件（若文件已存在，请在文件中追加以下"name"-"value"键值对，请勿直接覆盖原文件）。文件内容如下：

```TypeScript
{
  "string": [
    {
      "name": "app_name",
      "value": "timePicker"
    },
    {
      "name": "am",
      "value": "上午"
    },
    {
      "name": "pm",
      "value": "下午"
    }
  ]
}
```

英文：在resource目录下创建en目录，在en目录下创建element目录，在element目录添加string.json文件（若文件已存在，请在文件中追加以下"name"-"value"键值对，请勿直接覆盖原文件）。文件内容如下：

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

阿拉伯语：在resource目录下创建ar目录，在ar目录下创建element目录，在element目录下添加string.json文件（若文件已存在，请在文件中追加以下"name"-"value"键值对，请勿直接覆盖原文件）。文件内容如下：

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

示例代码如下：

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
  // 使用系统当前区域ID创建NumberFormat对象
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
    // 创建订阅者，监听系统语言变化
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

  // 系统语言变化后刷新UI状态
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
    // 根据语言习惯设置amPm列是否放在最后
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
    // 根据语言习惯设置镜像语言的时间顺序
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
        // 根据镜像语言显示顺序创建column
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

从API版本26.0.0开始，新增[itemHeight](#itemheight)属性。

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
      this.dataArray.push('选项' + i)
    }
  }

  build() {
    Column({ space: 12 }) {
      Text('当前itemHeight：' + (this.pickerItemHeight ? this.pickerItemHeight.value + 'vp' : '默认值(40vp)'))
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

从API版本26.0.0开始，新增[displayedItemCount](arkts-arkui-uipickercomponent-attribute.md#displayeditemcount)属性。

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
      this.dataArray.push('第' + i + '项')
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
        Button('3项')
          .width(120)
          .height(40)
          .onClick(() => {
            this.visibleCount = 3
          })
        Button('5项')
          .width(120)
          .height(40)
          .onClick(() => {
            this.visibleCount = 5
          })
        Button('8项(自动变9)')
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
