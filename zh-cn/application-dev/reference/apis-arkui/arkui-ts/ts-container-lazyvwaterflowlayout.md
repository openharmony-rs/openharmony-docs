# LazyVWaterFlowLayout

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yangcan18-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

该组件用于实现支持懒加载的瀑布流布局，其父组件仅限于[List](ts-container-list.md)、[Scroll](ts-container-scroll.md)、[WaterFlow](ts-container-waterflow.md)或[FlowItem](ts-container-flowitem.md)，并支持使用自定义组件或[NodeContainer](ts-basic-components-nodecontainer.md)组件封装后应用在上述组件中。

该组件仅在[List](ts-container-list.md)组件、[Scroll](ts-container-scroll.md)组件、[WaterFlow](ts-container-waterflow.md)组件的单列模式或分段布局中的单列分段并且布局方向为FlexDirection.Column的情况下支持懒加载。在[WaterFlow](ts-container-waterflow.md)的多列模式或布局方向为FlexDirection.Row或FlexDirection.RowReverse的情况下使用该组件，则不支持懒加载。此外，在布局方向为FlexDirection.ColumnReverse的[WaterFlow](ts-container-waterflow.md)组件下使用该组件会导致显示异常。当懒加载功能生效时，该组件仅加载显示区域内的子组件，并在帧间空闲间隙预加载显示区域上方和下方各半屏的内容。

> **说明：**
>
> - LazyVWaterFlowLayout组件高度默认自适应内容，不建议设置会固定或约束组件垂直方向尺寸的属性，设置后会导致显示异常或无法正常滚动。涉及的属性包括[height](ts-universal-attributes-size.md#height)、[size](ts-universal-attributes-size.md#size)中的height、[constraintSize](ts-universal-attributes-size.md#constraintsize)中的minHeight/maxHeight、[aspectRatio](ts-universal-attributes-layout-constraints.md#aspectratio)、[layoutWeight](ts-universal-attributes-size.md#layoutweight)，以及[height](ts-universal-attributes-size.md#height15)取[LayoutPolicy](ts-universal-attributes-size.md#layoutpolicy15)值的场景。
> - 当父组件设置主轴方向尺寸时，LazyVWaterFlowLayout按照父组件可视区域进行懒加载；当父组件未设置主轴方向尺寸时，LazyVWaterFlowLayout会被内容撑开，导致所有子组件都会被加载布局。
> - 该组件在不同父组件下的懒加载支持条件如下：
>   1. 在List组件下，要求List组件布局方向必须是竖直方向（即[listDirection](ts-container-list.md#listdirection)属性设置为Axis.Vertical），在非竖直方向的List中使用该组件会导致应用崩溃。当List设置了[lanes](ts-container-list.md#lanes9)、[chainAnimation](ts-container-list.md#chainanimation)、[scrollSnapAlign](ts-container-list.md#scrollsnapalign10)属性中的任意一个或多个时，该组件的懒加载功能会失效。
>   2. 在Scroll组件下，要求Scroll组件布局方向必须是竖直方向（即[scrollable](ts-container-scroll.md#scrollable)属性设置为ScrollDirection.Vertical），在非竖直方向的Scroll中使用该组件会导致应用崩溃。
>   3. 在WaterFlow组件下，仅在WaterFlow组件的单列模式或分段布局中的单列分段，并且布局方向为FlexDirection.Column时支持懒加载。当WaterFlow为多列模式或布局方向为FlexDirection.Row、FlexDirection.RowReverse时，该组件的懒加载功能会失效。此外，在布局方向为FlexDirection.ColumnReverse的WaterFlow组件下使用该组件会导致显示异常。
> - 当懒加载功能生效时，该组件仅加载父组件可视区域内的子组件，并在帧间空闲时隙预加载可视区域上方和下方各半屏的内容。
> - 此处的父组件指最靠近当前组件的上层滚动组件，其他文档下的具体含义请参考对应内容。

**起始版本：** 26.0.0

## 导入模块

```ts
import { LazyVWaterFlowLayout } from '@kit.ArkUI';
```

## 接口

LazyVWaterFlowLayout()

创建垂直方向懒加载瀑布流布局容器。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### columnsTemplate

columnsTemplate(value: string | ItemFillPolicy | undefined)

设置当前瀑布流组件布局列的数量，不设置时默认1列。

当value设置为string类型时，可以使用columnsTemplate('1fr 1fr 2fr')将LazyVWaterFlowLayout分为3列，LazyVWaterFlowLayout宽分为4等份，第1列占1份，第2列占1份，第3列占2份。

可使用columnsTemplate('repeat(auto-fill, track-size)')根据给定的列宽track-size自动计算列数，其中repeat、auto-fill为关键字，track-size为可设置的宽度，支持的单位包括px、vp、%，默认单位为vp。也可以设置没有单位的有效数字。

当value设置为ItemFillPolicy类型时，将根据LazyVWaterFlowLayout组件宽度对应[断点类型](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)确定列数。

例如，ItemFillPolicy.BREAKPOINT_DEFAULT在组件宽度相当于sm及更小的设备上显示2列，相当于md设备时显示3列，相当于lg及更大的设备时显示5列，且每列均为1fr。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                               |
| ------ | ------ | ---- | ---------------------------------- |
| value  | string \| [ItemFillPolicy](./ts-types.md#itemfillpolicy22) \| undefined | 是   | 当前瀑布流布局列的数量或最小列宽值。<br/>方法入参为undefined时，恢复为默认值（1列）。 |

### columnsGap

columnsGap(value: LengthMetrics | undefined): T

设置列与列的间距。默认值为0vp，设置为小于0的值时，按默认值显示。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                         | 必填 | 说明                         |
| ------ | ---------------------------- | ---- | ---------------------------- |
| value  |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| undefined | 是   | 列与列的间距。<br/>方法入参为undefined时，恢复为默认值（0vp）。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前组件。 |

### rowsGap

rowsGap(value: LengthMetrics | undefined): T

设置行与行的间距。默认值为0vp，设置为小于0的值时，按默认值显示。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                         | 必填 | 说明                         |
| ------ | ---------------------------- | ---- | ---------------------------- |
| value  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| undefined | 是   | 行与行的间距。<br/>方法入参为undefined时，恢复为默认值（0vp）。|

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前组件。 |

## 事件

除支持[通用事件](ts-component-general-events.md)外，还支持以下事件：

### onVisibleIndexesChange

onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T

当前瀑布流显示的起始位置或终止位置的子组件发生变化时触发。瀑布流初始化时会触发一次。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                                  |
| ------ | ------ | ---- | ------------------------------------- |
| callback  | [OnVisibleIndexesChangeCallback](./ts-container-scrollable-common.md#onvisibleindexeschangecallback) \| undefined | 是   | 回调函数，当可见区域内的子组件索引发生变化时触发。<br/>方法入参为undefined时，取消监听。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前组件。 |

## 示例

通过[Scroll](ts-container-scroll.md)和LazyVWaterFlowLayout组件实现懒加载瀑布流布局。

MyDataSource实现了LazyForEach数据源接口[IDataSource](ts-rendering-control-lazyforeach.md#idatasource)，用于通过LazyForEach给LazyVWaterFlowLayout提供子组件。 

从API版本26.0.0开始，新增支持LazyVWaterFlowLayout组件。

<!--code_no_check-->
```ts
import { LengthMetrics, LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute } from '@kit.ArkUI';
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVWaterFlowLayoutSample1 {
  private arr : MyDataSource<number> = new MyDataSource<number>();

  // 返回随机高度
  private itemHeight(index: number): number {
    return 80 + (index * 37 % 121)
  }

  private itemColor(index: number): string {
    const colors: string[] = ['#FFE0B2', '#C8E6C9', '#BBDEFB', '#F8BBD0', '#D1C4E9', '#FFF9C4']
    return colors[index % colors.length]
  }

  build() {
    Column() {
      Scroll() {
        LazyVWaterFlowLayout() {
          LazyForEach(this.arr, (item: number) => {
            Column() {
              Text('item ' + item.toString())
                .fontSize(16)
                .fontColor(Color.Black)
            }
            .height(this.itemHeight(item))
            .width('100%')
            .borderRadius(8)
            .backgroundColor(this.itemColor(item))
            .justifyContent(FlexAlign.Center)
          })
        }
        .columnsTemplate('1fr 1fr')
        .rowsGap(LengthMetrics.vp(10))
        .columnsGap(LengthMetrics.vp(10))
        .onVisibleIndexesChange((start: number, end: number) => {
          // 滚动监听：即将触底时提前加载更多数据
          if (end + 20 >= this.arr.totalCount()) {
            // 添加100个新数据到数据源
            let currentCount = this.arr.totalCount();
            for (let i = currentCount; i < currentCount + 100; i++) {
              this.arr.pushData(i);
            }
          }
        })
      }
      .padding(10)
      .layoutWeight(1)
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#DCDCDC')
  }

  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.arr.pushData(i);
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
![scroll_lazyvwaterflowlayout.png](figures/scroll_lazyvwaterflowlayout.png)