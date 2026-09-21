# LazyColumnLayout

定义懒式列布局组件。

## LazyColumnLayout

```TypeScript
LazyColumnLayout()
```

构造懒加载列布局属性。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

## 示例

### 示例1（实现懒加载线性布局）

通过[Scroll](ts-container-scroll.md)和LazyColumnLayout组件实现懒加载线性布局，并通过[onVisibleIndexesChange](#onvisibleindexeschange)在可视区域发生变化时回调起始和结束索引值。

从API版本26.0.0开始，新增支持LazyColumnLayout组件和onVisibleIndexesChange事件。



```TypeScript
import { LengthMetrics, LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';

// 关注列表数据结构
class Follow {
  name: string;
  image: Resource;
  description: string;

  constructor(name: string, image: Resource, description: string) {
    this.name = name;
    this.image = image;
    this.description = description;
  }
}

// 推荐列表数据结构
class Recommend {
  name: string;
  icon: Resource;
  description: string;

  constructor(name: string, icon: Resource, description: string) {
    this.name = name;
    this.icon = icon;
    this.description = description;
  }
}

@Entry
@Component
struct LazyColumnLayoutSample1 {
  private followList: Follow[] = [
    new Follow('甲', $r('app.media.icon'), '分享是一种快乐!'), // $r('app.media.icon')需要替换为开发者所需的图像资源文件
    new Follow('乙', $r('app.media.icon'), '摄影爱好者'),
    new Follow('丙', $r('app.media.icon'), '运动使我快乐'),
    new Follow('丁', $r('app.media.icon'), '探索未知的科技...'),
    // ...
  ]
  // 将 followList 转成每两个一组的数组
  private followPairs: Follow[][] = []
  private recommend: Recommend[] = [
    new Recommend('艾', $r('sys.symbol.person_crop_circle_fill'), '今天心情挺不错...'),
    new Recommend('陈', $r('sys.symbol.person_crop_circle_fill'), '在咖啡馆看书...'),
    new Recommend('林', $r('sys.symbol.person_crop_circle_fill'), '周末去爬山吧！'),
    new Recommend('王', $r('sys.symbol.person_crop_circle_fill'), '刚跑完五公里'),
    new Recommend('赵', $r('sys.symbol.person_crop_circle_fill'), '新学了一道菜'),
    new Recommend('张', $r('sys.symbol.person_crop_circle_fill'), '项目终于上线了'),
    new Recommend('刘', $r('sys.symbol.person_crop_circle_fill'), '在听一首老歌...'),
    new Recommend('孙', $r('sys.symbol.person_crop_circle_fill'), '准备出发去旅行'),
    new Recommend('周', $r('sys.symbol.person_crop_circle_fill'), '今天天气真好！'),
    new Recommend('吴', $r('sys.symbol.person_crop_circle_fill'), '加班中，勿扰...'),
    new Recommend('郑', $r('sys.symbol.person_crop_circle_fill'), '养了一只小猫'),
    new Recommend('杨', $r('sys.symbol.person_crop_circle_fill'), '正在打篮球'),
    // ...
  ]

  private itemColor(index: number): string {
    const colors: string[] = ['#FFE0B2', '#C8E6C9', '#BBDEFB', '#F8BBD0']
    return colors[index % colors.length]
  }

  aboutToAppear() {
    for (let i = 0; i < this.followList.length; i += 2) {
      this.followPairs.push(this.followList.slice(i, i + 2))
    }
  }

  build() {
    Column() {
      Scroll() {
        LazyColumnLayout() {
          Text('关注列表：')

          // 嵌套LazyColumnLayout展示双列关注列表
          LazyColumnLayout() {
            ForEach(this.followPairs, (pair: Follow[], rowIndex: number) => {
              Row({ space: 12 }) {
                ForEach(pair, (item: Follow, colIndex: number) => {
                  Column() {
                    Image(item.image).height(96).width('100%').backgroundColor(this.itemColor(rowIndex * 2 + colIndex))
                    Text(item.name).fontSize(20).margin({ top: 8 })
                    Text(item.description).fontSize(16).fontColor(Color.Gray).margin({ top: 2 })
                  }
                  .alignItems(HorizontalAlign.Start)
                  .layoutWeight(1)
                }, (item: Follow) => JSON.stringify(item))
              }
              .width('100%')
            })
          }
          .space(LengthMetrics.vp(12))

          Divider().height(2)

          Text('推荐的人：')

          // 使用独立LazyColumnLayout展示推荐列表
          LazyColumnLayout() {
            ForEach(this.recommend, (item: Recommend, index: number) => {
              Row() {
                SymbolGlyph(item.icon).fontSize(36).fontColor([Color.Gray])
                Column() {
                  Text(item.name).fontSize(20)
                  Text(item.description).fontSize(16).fontColor(Color.Gray).margin({ top: 2 })
                }
                .margin({ left: 12 })
                .alignItems(HorizontalAlign.Start)

                Blank()
                SymbolGlyph($r('sys.symbol.chevron_forward')).fontSize(20).fontColor([Color.Gray])
              }
              .width('100%')
            }, (item: Recommend) => JSON.stringify(item))
          }
          .space(LengthMetrics.vp(12))
          .onVisibleIndexesChange((start: number, end: number) => {
            console.info('LazyColumnLayout visible indexes: start: ' + start + ', end: ' + end);
          })
        }
        .padding({ left: 24, right: 24 })
        .space(LengthMetrics.vp(12))
        .alignItems(HorizontalAlign.Start)
      }
      .layoutWeight(1)
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例2（设置头部组件或尾部组件及吸附效果）

该示例通过[Scroll](ts-container-scroll.md)嵌套LazyColumnLayout，并通过[header](#header)、[footer](#footer)、[sticky](#sticky)实现顶部和底部吸附效果。滚动过程中header吸附在可视区域顶部，footer吸附在可视区域底部。

从API版本26.0.0开始，新增支持header、footer和sticky属性。

```TypeScript
import { LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';
// MyDataSource是自定义数据源类，实现了LazyForEach所需的IDataSource接口
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyColumnLayoutStickyDemo {
  private items: MyDataSource<number> = new MyDataSource<number>();

  aboutToAppear(): void {
    for (let i = 0; i < 30; i++) {
      this.items.pushData(i);
    }
  }

  // 构建头部组件
  @Builder
  HeaderBuilder() {
    Row() {
      Text('Header')
        .fontSize(18)
        .fontColor(Color.White)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .height(50)
    .justifyContent(FlexAlign.Center)
    .alignItems(VerticalAlign.Center)
    .backgroundColor('#4A90E2')
  }

  @Builder
  FooterBuilder() {
    Row() {
      Text('Footer')
        .fontSize(16)
        .fontColor(Color.White)
    }
    .width('100%')
    .height(40)
    .justifyContent(FlexAlign.Center)
    .alignItems(VerticalAlign.Center)
    .backgroundColor('#999999')
  }

  build() {
    Scroll() {
      LazyColumnLayout() {
        LazyForEach(this.items, (item: number) => {
          Text('item ' + item)
            .fontSize(16)
            .height(60)
            .width('100%')
            .padding({ left: 16 })
            .backgroundColor(item % 2 === 0 ? '#FFFFFF' : '#F5F5F5')
            .textAlign(TextAlign.Start)
        })
      }
      .header(this.HeaderBuilder)
      .footer(this.FooterBuilder)
      // 设置头部和尾部同时吸附
      .sticky(StickyStyle.BOTH)
    }
    .width('100%')
    .height('100%')
    .edgeEffect(EdgeEffect.Spring)
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
