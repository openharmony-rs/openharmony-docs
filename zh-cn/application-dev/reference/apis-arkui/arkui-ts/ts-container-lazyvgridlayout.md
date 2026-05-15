# LazyVGridLayout

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong; @rongShao-Z; @guozejun-->
<!--Designer: @yylong-->
<!--Tester: @huchuyun-->
<!--Adviser: @Brilliantry_Rui-->

该组件用于实现支持懒加载的网格布局。

API版本26.0.0之前，其父组件支持[WaterFlow](ts-container-waterflow.md)和[FlowItem](ts-container-flowitem.md)组件，并支持使用自定义组件或[NodeContainer](ts-basic-components-nodecontainer.md)组件封装后应用在WaterFlow或FlowItem中。

从API版本26.0.0开始，其父组件新增支持[List](ts-container-list.md)、[Scroll](ts-container-scroll.md)和[LazyColumnLayout](ts-container-lazycolumnlayout.md)，同时新增支持使用自定义组件或[NodeContainer](ts-basic-components-nodecontainer.md)组件封装后应用在List、Scroll或LazyColumnLayout中。

> **说明：**
>
> - 该组件从API version 19开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
> - LazyVGridLayout组件高度默认自适应内容，不建议设置高度、高度约束或宽高比，设置后会导致显示异常。
> - 该组件在不同父组件下的懒加载支持条件如下：
>   1. 在WaterFlow组件下，仅在WaterFlow组件的单列模式或分段布局中的单列分段，并且布局方向[FlexDirection](ts-appendix-enums.md#flexdirection)设置为FlexDirection.Column的情况下支持懒加载。在WaterFlow的多列模式或布局方向为FlexDirection.Row或FlexDirection.RowReverse的情况下使用该组件，则不支持懒加载。此外，在布局方向为FlexDirection.ColumnReverse的WaterFlow组件下使用该组件会导致显示异常。
>   2. 在List组件下，要求List组件布局方向必须是竖直方向（即[listDirection](ts-container-list.md#listdirection)属性设置为Axis.Vertical）。在非竖直方向的List中使用该组件会导致应用崩溃。当List设置了lanes、chainAnimation、scrollSnapAlign属性中的任意一个时，该组件的懒加载功能会失效。
>   3. 在Scroll组件下，要求Scroll组件布局方向必须是竖直方向（即[scrollable](ts-container-scroll.md#scrollable)属性设置为ScrollDirection.Vertical）。在非竖直方向的Scroll中使用该组件会导致应用崩溃。
> - 当懒加载功能生效时，该组件仅加载父组件显示区域内的子组件，并在帧间空闲时隙预加载显示区域上方和下方各半屏的内容。

## 接口

LazyVGridLayout()

创建垂直方向懒加载网格布局容器。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### columnsTemplate

columnsTemplate(value: string)

设置当前网格布局列的数量、固定列宽或最小列宽值，不设置时默认1列。

例如，'1fr&nbsp;1fr&nbsp;2fr'&nbsp;是将父组件分3列，将父组件允许的宽分为4等份，第一列占1份，第二列占1份，第三列占2份。

columnsTemplate('repeat(auto-fit, track-size)')是设置最小列宽值为track-size，自动计算列数和实际列宽。

columnsTemplate('repeat(auto-fill, track-size)')是设置固定列宽值为track-size，自动计算列数。

columnsTemplate('repeat(auto-stretch, track-size)')是设置固定列宽值为track-size，使用columnsGap为最小列间距，自动计算列数和实际列间距。

其中repeat、auto-fit、auto-fill、auto-stretch为关键字。track-size为列宽，支持的单位包括px、vp、%或有效数字，默认单位为vp，track-size至少包含一个有效列宽。<br/>
auto-fit模式和auto-stretch模式只支持track-size为一个有效列宽值，并且auto-stretch模式中的track-size只支持px、vp和有效数字，不支持%。auto-fill模式支持一个或多个有效列宽，如columnsTemplate('repeat(auto-fill, 20)')、columnsTemplate('repeat(auto-fill, 20 80px)')。

设置为'0fr'时，该列的列宽为0，不显示子组件。设置为其他非法值时，子组件显示为固定1列。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                               |
| ------ | ------ | ---- | ---------------------------------- |
| value  | string | 是   | 当前网格布局列的数量或最小列宽值。 |

### columnsGap

columnsGap(value: LengthMetrics): T

设置列与列的间距。设置为小于0的值时，按默认值显示。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                         | 必填 | 说明                         |
| ------ | ---------------------------- | ---- | ---------------------------- |
| value  |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 是   | 列与列的间距。<br/>默认值：0vp |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前LazyVGridLayout组件。 |

### rowsGap

rowsGap(value: LengthMetrics): T

设置行与行的间距。设置为小于0的值时，按默认值显示。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                         | 必填 | 说明                         |
| ------ | ---------------------------- | ---- | ---------------------------- |
| value  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 是   | 行与行的间距。<br/>默认值：0vp |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前LazyVGridLayout组件。 |

## 事件

除支持[通用事件](ts-component-general-events.md)外，还支持以下事件：

### onVisibleIndexesChange

onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined)

设置onVisibleIndexesChange回调函数。当LazyVGridLayout可视区域内子组件的索引值发生变化时触发回调，返回可视区域内子组件的起始索引值和结束索引值。使用callback异步回调。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| callback  | [OnVisibleIndexesChangeCallback](#onvisibleindexeschangecallback)&nbsp;\|&nbsp;undefined | 是  | onVisibleIndexesChange事件的回调函数。方法入参为undefined时，取消监听。 |

## OnVisibleIndexesChangeCallback

OnVisibleIndexesChangeCallback = (start: number, end: number) => void

LazyVGridLayout可视区域内子组件的索引值发生变化时触发的回调类型。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                  |
| ------ | ------ | ---- | ------------------------------------- |
| start  | number | 是  | 当前可视区域内子组件的起始索引。可视区域内无子组件或者LazyVGridLayout内无子组件时返回-1。 |
| end  | number | 是  | 当前可视区域内子组件的结束索引。可视区域内无子组件或者LazyVGridLayout内无子组件时返回-1。 |

## 示例

该示例通过[WaterFlow](ts-container-waterflow.md)和[LazyVGridLayout](ts-container-lazyvgridlayout.md)实现懒加载网格布局，并通过[onVisibleIndexesChange](#onvisibleindexeschange)在显示区域发生变化时回调索引。

MyDataSource实现了[LazyForEach](ts-rendering-control-lazyforeach.md)数据源接口[IDataSource](ts-rendering-control-lazyforeach.md#idatasource)，用于通过LazyForEach给LazyVGridLayout提供子组件。

从API版本26.0.0开始，新增onVisibleIndexesChange事件。

<!--code_no_check-->
```ts
import { LengthMetrics } from '@kit.ArkUI'
import { MyDataSource } from './MyDataSource'

@Entry
@Component
struct LazyVGridLayoutSample1 {
  private arr1:MyDataSource<number> = new MyDataSource<number>();
  private arr2:MyDataSource<number> = new MyDataSource<number>();
  build() {
    Column() {
      WaterFlow() {
        LazyVGridLayout() {
          LazyForEach(this.arr1, (item:number)=>{
            Text('item' + item.toString())
              .height(64)
              .width('100%')
              .borderRadius(5)
              .backgroundColor(Color.White)
              .textAlign(TextAlign.Center)
          })
        }
        .columnsTemplate('1fr')
        .rowsGap(LengthMetrics.vp(10))
        // 从API版本26.0.0开始，新增onVisibleIndexesChange事件。
        .onVisibleIndexesChange((start: number, end: number) => {
          console.info('visible indexes: start= ' + 'start,' + 'end= ' + 'end');
      })

        LazyVGridLayout() {
          LazyForEach(this.arr2, (item:number)=>{
            Text('item' + item.toString())
              .height(128)
              .width('100%')
              .borderRadius(5)
              .backgroundColor(Color.White)
              .textAlign(TextAlign.Center)
          })
        }
        .columnsTemplate('1fr 1fr')
        .rowsGap(LengthMetrics.vp(10))
        .columnsGap(LengthMetrics.vp(10))
      }.padding(10)
      .rowsGap(10)
    }
    .width('100%').height('100%')
    .backgroundColor('#DCDCDC')
  }

  aboutToAppear(): void {
    for (let i = 0; i < 6; i++) {
      this.arr1.pushData(i);
    }
    for (let i = 0; i < 100; i++) {
      this.arr2.pushData(i);
    }
  }
}
```

<!--code_no_check-->
```ts
// MyDataSource.ets
export class BasicDataSource<T> implements IDataSource {
  private listeners: DataChangeListener[] = [];
  protected dataArray: T[] = [];

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number): T {
    return this.dataArray[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      console.info('add listener');
      this.listeners.push(listener);
    }
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
    const pos = this.listeners.indexOf(listener);
    if (pos >= 0) {
      console.info('remove listener');
      this.listeners.splice(pos, 1);
    }
  }

  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    })
  }

  notifyDataAdd(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    })
  }

  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    })
  }

  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    })
  }

  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    })
  }

  notifyDatasetChange(operations: DataOperation[]): void {
    this.listeners.forEach(listener => {
      listener.onDatasetChange(operations);
    })
  }
}

export class MyDataSource<T> extends BasicDataSource<T> {
  public shiftData(): void {
    this.dataArray.shift();
    this.notifyDataDelete(0);
  }
  public unshiftData(data: T): void {
    this.dataArray.unshift(data);
    this.notifyDataAdd(0);
  }
  public pushData(data: T): void {
    this.dataArray.push(data);
    this.notifyDataAdd(this.dataArray.length - 1);
  }
  public popData(): void {
    this.dataArray.pop();
    this.notifyDataDelete(this.dataArray.length);
  }
  public clearData(): void {
    this.dataArray = [];
    this.notifyDataReload();
  }
}
```

![](figures/zh-cn_image_lazyvgridlayout1.gif)