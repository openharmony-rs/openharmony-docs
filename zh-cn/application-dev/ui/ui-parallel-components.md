# UI并行化创建组件树
从API version 20开始，UI可以并行创建组件树，从而降低组件创建时延并提升应用的流畅度。
## 概述
随着用户对应用响应速度和流畅度提出的更高要求，传统单线程UI渲染方式已无法满足日益复杂UI和数据处理需求，UI卡顿、响应迟缓等问题严重影响用户体验。基于上述问题，ArkUI提出声明式下部分UI并行化创建方案。开发者可指定并行内容，减少组件创建时延，提升用户体验。

适用场景：需要对现有复杂页面进行拆分。执行并行构建的部分不会在当前帧立即渲染，因此执行并行的内容一般为屏幕外的内容、可以延迟显示的内容或者可以先用占位替代需要显示的内容。如该页面可以将当前帧显示的内容串行创建，屏幕外的内容并行创建。

![ui_parallel003](figures/page.png)

## 约束与限制
  * 不能在[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeui)中使用外部定义的状态变量，例如：[@Link](state-management/arkts-link.md)、[@Prop](state-management/arkts-prop.md)、[@Consumer](state-management/arkts-provide-and-consume.md)、类StorageLink、类StorageProp等。需要依赖外部的状态变量更新UI，请使用[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeuit)。
  * 当前[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeui)仅支持[Column](../reference/apis-arkui/arkui-ts/ts-container-column.md)、[Image](../reference/apis-arkui/arkui-ts/ts-basic-components-image.md)、[RelativeContainer](../reference/apis-arkui/arkui-ts/ts-container-relativecontainer.md)、[Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)、[Row](../reference/apis-arkui/arkui-ts/ts-container-row.md)、[Stack](../reference/apis-arkui/arkui-ts/ts-container-stack.md)、[List](../reference/apis-arkui/arkui-ts/ts-container-list.md)、[ListItem](../reference/apis-arkui/arkui-ts/ts-container-listitem.md)、[Grid](../reference/apis-arkui/arkui-ts/ts-container-grid.md)、[GridItem](../reference/apis-arkui/arkui-ts/ts-container-griditem.md)、[Button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)、[Toggle](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md)组件。[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeui)内部只能使用上述组件，其他组件将触发运行时错误，导致应用崩溃。
  * 普通变量可以在多线程中使用，但开发者需要确保变量在多线程中的读写安全。可以使用并发容器或者锁来保证多线程中的读写安全。
  * 当前[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeui)仅支持并行化创建，创建完成后的更新操作仍在主线程完成。


## 数据传递

为了保证UI在多线程中运行的安全性与正确性，在[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeui)中禁止使用外部定义的状态变量。在debug模式下，系统会进行运行时检测并抛出异常。

如下示例演示了在[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeui)中使用外部定义的状态变量，从系统日志中可以观察到报错异常。

```ts
import { ParallelizeUI } from '@ohos.arkui.Parallelize';

@Entry
@Component
struct Index {
  @State str: string = 'Hello';
  build() {
    Column() {
      ParallelizeUI() {
        Text(this.str) // ParallelizeUI内部不能使用外部定义的状态变量
        .fontSize(50)
      }
      Text('World')
        .fontSize(50)
    }.height('100%')
      .width('100%')
  }
}
```
![ui_parallel002](figures/ui_parallel002.png)

开发者可以使用[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeuit)。

如下示例演示了如何使用[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeuit)进行数据传递。

```ts
import { ParallelizeUI } from '@ohos.arkui.Parallelize';
import { ParallelizeUI } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Index {
  @State str: string = 'Hello';
  build() {
    Column() {
      const str = ParallelizeUI<string>(() => {return this.str})
      ParallelizeUI() {
        Text(str.value) // 使用ParallelizeUI进行数据传递
        .fontSize(50)
      }
      Text('World')
        .fontSize(50)
      Button('UpperCase')
        .onClick((event: ClickEvent) => {
          this.str = this.str.toUpperCase()
        })
    }.height('100%')
      .width('100%')
  }
}
```
![ui_parallel003](figures/ui_parallel003.png)


## 并行化创建组件示例

并行创建的UI在创建完成后的下一帧才能合并显示，页面需要多帧才能显示全部内容。

该场景示例介绍了如何使用[ParallelizeUI](../reference/apis-arkui/js-apis-arkui-Parallelize.md#parallelizeui)并行创建多个组件。

```ts
import { Entry, Text, Column, Component, Button, ClickEvent, FontWeight, Stack, Position,
  TextAlign, Alignment, Margin, Row, GridItem, Image ,ImageFit, $r, Grid } from '@ohos.arkui.component';
import { State, ParallelizeUI } from '@ohos.arkui.stateManagement';
import { ParallelOption, ParallelizeUI } from '@ohos.arkui.Parallelize';

class WeatherInfo {
  city:string = ''
  temperature:number = 0
  weather:int = 0
  constructor(city:string, temperature:number, weather:int) {
    this.city = city
    this.temperature = temperature
    this.weather = weather
  }
  getImg():string {
    switch (this.weather) {
      case 0:
        return 'app.media.cloudy'
      case 1:
        return 'app.media.snow'
      case 2:
        return 'app.media.sunny'
      case 3:
        return 'app.media.rain'
      default:
        break;
    }
    return 'app.media.sunny'
  }
}

let array : Array<WeatherInfo> = new Array<WeatherInfo>();

array!.push(new WeatherInfo('杭州', 40, 3));
array!.push(new WeatherInfo('上海', 39, 2));
array!.push(new WeatherInfo('南京', 37, 1));
array!.push(new WeatherInfo('苏州', 36, 0));
array!.push(new WeatherInfo('湖州', 35, 3));
array!.push(new WeatherInfo('无锡', 34, 2));
array!.push(new WeatherInfo('常州', 32, 1));
array!.push(new WeatherInfo('嘉兴', 31, 1));


@Entry
@Component
struct Page {
  @State infos :Array<WeatherInfo> = new Array<WeatherInfo>();

  aboutToAppear() {
    this.infos.push(array[0])
    this.infos.push(array[1])
    this.infos.push(array[2])
    this.infos.push(array[3])
  }

  build() {
    Column() {
      Button('Update')
        .onClick((e: ClickEvent) => {
          this.infos[0] = new WeatherInfo('北京', 30, 2); // 外层状态变量刷新
        })
        .width(200)
        .height(50)
      let prop1 = ParallelizeUI<WeatherInfo>(() => {
        return new WeatherInfo(this.infos[0].city, this.infos[0].temperature, this.infos[0].weather);
      })
      Grid() {
        // 并行创建多个组件
        ParallelizeUI() {
          GridItem() {
            Row() {
              Column() {
                Text(prop1.value.city).fontSize('25') // 使用ParallelizeUI进行数据传递
                Text(prop1.value.temperature.toString()).fontSize('25')
              }
              Image($r(prop1.value.getImg()))
                .objectFit(ImageFit.Contain)
            }
            .width('100%')
            .height('100%')
          }
          .width('100%')
          .height(100)
          .borderWidth(2).borderColor(0xAFEEEE)
        }
        // 其余组件串行创建
        for (let i = 1; i < this.infos.length; i++) {
          GridItem() {
            Row() {
              Column() {
                Text(this.infos[i].city).fontSize('25')
                Text(this.infos[i].temperature.toString()).fontSize('25')
              }
              Image($r(this.infos[i].getImg()))
                .objectFit(ImageFit.Contain)
            }
            .width('100%')
            .height('100%')
          }
          .width('100%')
          .height(100)
          .borderWidth(2).borderColor(0xAFEEEE)
        }
      }
      .columnsTemplate('1fr 1fr')
      .columnsGap(20)
      .rowsGap(20)
      .width('100%')
      .height('100%')
      .margin({ top: 100 } as Margin)
    }
  }
}

```
![ui_parallel003](figures/ui_parallel004.gif)

## 相关实例

[使用声明式的并行化方法创建UI组件](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_20250702/code/ArkTS1.2/ParallelizeUI/README.md)

