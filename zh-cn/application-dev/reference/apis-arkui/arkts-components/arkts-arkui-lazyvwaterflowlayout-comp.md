# LazyVWaterFlowLayout

定义LazyVWaterFlowLayout组件。

## LazyVWaterFlowLayout

```TypeScript
LazyVWaterFlowLayout()
```

构造懒加载垂直瀑布流属性。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

## 示例

### 示例1（实现懒加载瀑布流布局）

通过[Scroll](ts-container-scroll.md)和LazyVWaterFlowLayout组件实现懒加载瀑布流布局。

MyDataSource实现了LazyForEach数据源接口[IDataSource](ts-rendering-control-lazyforeach.md#idatasource)，用于通过LazyForEach给LazyVWaterFlowLayout提供子组件。

从API版本26.0.0开始，新增支持LazyVWaterFlowLayout组件。

```TypeScript
import { LengthMetrics, LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute } from '@kit.ArkUI';
// MyDataSource是自定义数据源类，实现了LazyForEach所需的IDataSource接口
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVWaterFlowLayoutSample1 {
  private arr : MyDataSource<number> = new MyDataSource<number>();

  // 返回随机高度
  private itemHeight(index: number): number {
    return 80 + (index * 37 % 121);
  }

  private itemColor(index: number): string {
    const colors: string[] = ['#FFE0B2', '#C8E6C9', '#BBDEFB', '#F8BBD0', '#D1C4E9', '#FFF9C4'];
    return colors[index % colors.length];
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
          console.info('LazyVWaterFlowLayout visible indexes: start: ' + start + ', end: ' + end);
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



```TypeScript
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
    });
  }

  notifyDataAdd(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    });
  }

  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    });
  }

  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    });
  }

  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    });
  }

  notifyDatasetChange(operations: DataOperation[]): void {
    this.listeners.forEach(listener => {
      listener.onDatasetChange(operations);
    });
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
    const deleteIndex = this.dataArray.length - 1;
    this.dataArray.pop();
    this.notifyDataDelete(deleteIndex);
  }

  public clearData(): void {
    this.dataArray = [];
    this.notifyDataReload();
  }
}
```

### 示例2（设置头部组件或尾部组件及吸附效果）

该示例通过[Scroll](ts-container-scroll.md)嵌套LazyVWaterFlowLayout，并通过[header](#header)、[footer](#footer)、[sticky](#sticky)实现瀑布流顶部和底部吸附效果。滚动过程中header吸附在可视区域顶部，footer吸附在可视区域底部。

从API版本26.0.0开始，新增支持header、footer和sticky属性。



```TypeScript
import { LengthMetrics, LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute } from '@kit.ArkUI';
// MyDataSource是自定义数据源类，实现了LazyForEach所需的IDataSource接口
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVWaterFlowLayoutStickyDemo {
  private arr : MyDataSource<number> = new MyDataSource<number>();

  // 返回随机高度
  private itemHeight(index: number): number {
    return 80 + (index * 37 % 121);
  }

  private itemColor(index: number): string {
    const colors: string[] = ['#FFE0B2', '#C8E6C9', '#BBDEFB', '#F8BBD0', '#D1C4E9', '#FFF9C4'];
    return colors[index % colors.length];
  }

  // 构建头部组件
  @Builder
  HeaderBuilder() {
    Column() {
      Text('Header')
        .fontSize(16)
        .fontColor(Color.Black)
    }
    .height(50)
    .width('100%')
    .borderRadius(8)
    .backgroundColor('#BBDEFB')
    .justifyContent(FlexAlign.Center)
  }

  @Builder
  FooterBuilder() {
    Column() {
      Text('Footer')
        .fontSize(16)
        .fontColor(Color.Black)
    }
    .height(40)
    .width('100%')
    .borderRadius(8)
    .backgroundColor('#D1C4E9')
    .justifyContent(FlexAlign.Center)
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
        .header(this.HeaderBuilder)
        .footer(this.FooterBuilder)
        // 设置头部和尾部同时吸附
        .sticky(StickyStyle.BOTH)
        .onVisibleIndexesChange((start: number, end: number) => {
          console.info('LazyVWaterFlowLayout visible indexes: start: ' + start + ', end: ' + end);
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

### 示例3（设置自适应列数）

该示例通过[columnsTemplate](#columnstemplate)设置repeat(auto-fill, track-size)和ItemFillPolicy，实现LazyVWaterFlowLayout列数自适应。

从API版本26.0.0开始，新增[columnsTemplate](#columnstemplate)接口。

```TypeScript
import {
  LengthMetrics,
  LazyColumnLayout,
  LazyColumnLayoutAttribute,
  LazyVWaterFlowLayout,
  LazyVWaterFlowLayoutAttribute,
} from '@kit.ArkUI';
// MyDataSource是自定义数据源类，实现了LazyForEach所需的IDataSource接口
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVWaterFlowLayoutColumnsTemplateDemo {
  private autoFillData: MyDataSource<number> = new MyDataSource<number>();
  private breakpointData: MyDataSource<number> = new MyDataSource<number>();
  private breakpointPolicy: ItemFillPolicy = { fillType: PresetFillType.BREAKPOINT_DEFAULT };

  aboutToAppear(): void {
    // 初始化固定数量的数据，不进行滚动触底加载
    for (let i = 0; i < 18; i++) {
      this.autoFillData.pushData(i);
      this.breakpointData.pushData(i);
    }
  }

  private itemHeight(index: number): number {
    return 80 + (index * 37 % 121)
  }

  private itemColor(index: number): string {
    const colors: string[] = ['#CDE7FF', '#D8F5D0', '#FFE6A8', '#F8D7DA', '#E4D7FF', '#D2F4EA']
    return colors[index % colors.length]
  }

  @Builder
  ModeTitle(title: string, description: string) {
    Column() {
      Text(title)
        .fontSize(16)
        .fontWeight(FontWeight.Medium)
        .fontColor('#182230')
      Text(description)
        .fontSize(12)
        .fontColor('#667085')
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
    .padding({ bottom: 8 })
  }

  @Builder
  AutoFillHeader() {
    this.ModeTitle('repeat(auto-fill, 96vp)',
      '固定列宽为96vp，LazyVWaterFlowLayout根据可用宽度自动计算瀑布流列数。')
  }

  @Builder
  BreakpointHeader() {
    this.ModeTitle('ItemFillPolicy: BREAKPOINT_DEFAULT',
      '根据组件宽度对应的断点类型确定列数，sm及以下为2列，md为3列，lg及以上为5列。')
  }

  @Builder
  WaterFlowItemBuilder(item: number) {
    Text('item ' + item)
      .height(this.itemHeight(item))
      .width('100%')
      .borderRadius(8)
      .backgroundColor(this.itemColor(item))
      .fontColor('#182230')
      .textAlign(TextAlign.Center)
  }

  build() {
    Column() {
      Scroll() {
        LazyColumnLayout() {
          // repeat(auto-fill, 96vp)：固定列宽为96vp，根据可用宽度自动计算瀑布流列数
          LazyVWaterFlowLayout() {
            LazyForEach(this.autoFillData, (item: number) => {
              this.WaterFlowItemBuilder(item)
            })
          }
          .columnsTemplate('repeat(auto-fill, 96)')
          .rowsGap(LengthMetrics.vp(8))
          .columnsGap(LengthMetrics.vp(8))
          .header(this.AutoFillHeader)
          .padding(8)
          .backgroundColor('#F7F9FC')
          .border({ width: 1, color: '#D0D5DD' })
          .borderRadius(8)

          // ItemFillPolicy：根据组件宽度对应的断点类型确定列数
          LazyVWaterFlowLayout() {
            LazyForEach(this.breakpointData, (item: number) => {
              this.WaterFlowItemBuilder(item)
            })
          }
          .columnsTemplate(this.breakpointPolicy)
          .rowsGap(LengthMetrics.vp(8))
          .columnsGap(LengthMetrics.vp(8))
          .header(this.BreakpointHeader)
          .padding(8)
          .backgroundColor('#F7F9FC')
          .border({ width: 1, color: '#D0D5DD' })
          .borderRadius(8)
        }
        .space(LengthMetrics.vp(16))
        .width('100%')
      }
      .width('100%')
      .scrollable(ScrollDirection.Vertical)
      .layoutWeight(1)
    }
    .width('100%')
    .height('100%')
    .padding({ top: 48, left: 12, right: 12, bottom: 12 })
  }
}
```
