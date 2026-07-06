# ArkUI瀑布流渲染场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkUI瀑布流页面通常需要在滑动过程中持续加载图片、商品或资讯卡片。如果数据查询、解析或预处理直接运行在UI线程，数据量较大时会阻塞页面渲染，造成滑动卡顿。ArkTS-Sta可以使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)在后台线程生成或查询数据，UI线程接收结果后追加到WaterFlow的数据源，并通过LazyForEach按需渲染。

动态ArkTS示例中常使用@Concurrent、taskpool.Task.sendData()和onReceiveData()向UI线程回传数据。ArkTS-Sta中普通函数可以直接作为TaskPool任务函数，示例使用taskpool.execute返回查询结果；UI线程在await之后更新瀑布流数据源。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 定义瀑布流数据模型

瀑布流子项需要稳定的id作为LazyForEach键值，同时可以包含标题、图片标识、高度和背景色等渲染字段。

```ts
// ArkTS-Sta示例
// WaterFlowItem.ets
export class WaterFlowItem {
  id: int = 0;
  title: string = "";
  imageName: string = "";
  height: int = 120;
  color: int = 0xF2F3F5;

  constructor(id: int, title: string, imageName: string, height: int, color: int) {
    this.id = id;
    this.title = title;
    this.imageName = imageName;
    this.height = height;
    this.color = color;
  }
}
```

## 在TaskPool任务中查询数据

以下示例使用TaskPool模拟数据库分页查询，并返回一组瀑布流数据。实际业务中，可以在任务函数中执行数据库查询、文件解析或数据预处理，但不要在TaskPool任务中访问ArkUI组件或直接修改UI状态。

```ts
// ArkTS-Sta示例
// WaterFlowTask.ets
import { WaterFlowItem } from './WaterFlowItem'

const COLORS: Array<int> = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];

export function queryWaterFlowItems(start: int, count: int): Array<WaterFlowItem> {
  let result: Array<WaterFlowItem> = [];

  for (let index: int = 0; index < count; index++) {
    let id: int = start + index;
    let height: int = 120 + (id % 5) * 28;
    let color: int = COLORS[id % COLORS.length];
    result.push(new WaterFlowItem(
      id,
      "Item " + id,
      "Image" + id,
      height,
      color
    ));
  }

  return result;
}
```

## 封装LazyForEach数据源

WaterFlow结合LazyForEach使用时，需要通过实现IDataSource的数据源管理列表数据，并使用DataChangeListener通知组件数据变更。追加新数据时，只通知新增项，避免全量刷新导致瀑布流重新计算所有子项布局。

```ts
// ArkTS-Sta示例
// WaterFlowDataSource.ets
import { IDataSource, DataChangeListener } from '@ohos.arkui.component'
import { WaterFlowItem } from './WaterFlowItem'

export class WaterFlowDataSource implements IDataSource<WaterFlowItem> {
  private dataArray: Array<WaterFlowItem> = [];
  private listeners: Array<DataChangeListener> = [];

  public totalCount(): int {
    return this.dataArray.length;
  }

  public getData(index: int): WaterFlowItem {
    return this.dataArray[index];
  }

  public registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      this.listeners.push(listener);
    }
  }

  public unregisterDataChangeListener(listener: DataChangeListener): void {
    let position: int = this.listeners.indexOf(listener);
    if (position >= 0) {
      this.listeners.splice(position, 1);
    }
  }

  public addItems(items: Array<WaterFlowItem>): void {
    let startIndex: int = this.dataArray.length;
    for (let index: int = 0; index < items.length; index++) {
      this.dataArray.push(items[index]);
      this.notifyDataAdd(startIndex + index);
    }
  }

  private notifyDataAdd(index: int): void {
    for (let listener of this.listeners) {
      listener.onDataAdd(index);
    }
  }
}
```

## 在页面中渲染瀑布流

页面在aboutToAppear中加载首屏数据，并在WaterFlow触底时继续分页加载。taskpool.execute返回后，代码回到宿主线程继续执行，此时再将结果追加到数据源并通知LazyForEach更新。

```ts
// ArkTS-Sta示例
// Index.ets
import {
  Entry,
  Text,
  Column,
  Component,
  Button,
  ClickEvent,
  WaterFlow,
  FlowItem,
  LazyForEach
} from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { WaterFlowDataSource } from './WaterFlowDataSource'
import { WaterFlowItem } from './WaterFlowItem'
import { queryWaterFlowItems } from './WaterFlowTask'

@Entry
@Component
struct Index {
  @State message: string = "ready";

  private dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  private loading: boolean = false;
  private pageSize: int = 30;

  aboutToAppear(): void {
    this.loadMore();
  }

  private async loadMore(): Promise<void> {
    if (this.loading) {
      return;
    }

    this.loading = true;
    this.message = "loading";

    try {
      let start: int = this.dataSource.totalCount();
      let result: Array<WaterFlowItem> =
        (await taskpool.execute(queryWaterFlowItems, start, this.pageSize)) as Array<WaterFlowItem>;
      this.dataSource.addItems(result);
      this.message = "loaded: " + this.dataSource.totalCount();
    } catch (error) {
      this.message = "load failed";
      console.info("load waterflow data failed"); // load waterflow data failed
    } finally {
      this.loading = false;
    }
  }

  build() {
    Column(undefined) {
      Text(this.message).fontSize(18)

      Button("load more")
        .onClick((e: ClickEvent) => {
          this.loadMore();
        })

      WaterFlow() {
        LazyForEach(this.dataSource, (item: WaterFlowItem, index: int) => {
          FlowItem() {
            Column(undefined) {
              Text(item.title)
                .fontSize(16)
                .height(28)
              Text(item.imageName)
                .fontSize(14)
                .layoutWeight(1)
            }
            .width('100%')
            .height('100%')
          }
          .width('100%')
          .height(item.height)
          .backgroundColor(item.color)
        }, (item: WaterFlowItem, index: int): string => {
          return item.id.toString();
        })
      }
      .columnsTemplate("1fr 1fr")
      .columnsGap(8)
      .rowsGap(8)
      .cachedCount(6)
      .width('100%')
      .layoutWeight(1)
      .onReachEnd(() => {
        this.loadMore();
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

上述示例中，TaskPool只负责生成数据，WaterFlowDataSource.addItems()只在UI线程调用。LazyForEach根据WaterFlowItem.id生成稳定键值，新增数据时通过onDataAdd通知增量更新，减少瀑布流重新布局成本。

## 使用建议

- TaskPool任务函数中不要访问ArkUI组件、@State状态变量或DataChangeListener。后台任务只返回普通数据，UI线程负责更新数据源。
- LazyForEach需要稳定键值。瀑布流数据增删时，建议使用业务ID作为键值，不建议使用会随位置变化的索引作为键值。
- 分页追加数据时应使用增量通知，例如onDataAdd或批量新增通知，避免每次加载都触发全量onDataReloaded。
- cachedCount可以提升滑动时的预加载体验，但会增加预加载组件数量和内存占用，应结合子项复杂度、图片加载成本和设备性能调整。
- 瀑布流子项高度变化会影响布局计算。图片真实高度需要异步获取时，建议在数据预处理阶段计算或缓存比例，减少滑动过程中的布局抖动。
- ArkTS-Sta对象默认按共享引用传递。如果TaskPool返回的数据还会被后台线程继续修改，UI线程追加数据前应复制或通过锁保护共享状态。
