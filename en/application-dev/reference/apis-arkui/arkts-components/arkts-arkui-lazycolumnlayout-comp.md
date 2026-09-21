# LazyColumnLayout

Defines the lazy column layout component.

## LazyColumnLayout

```TypeScript
LazyColumnLayout()
```

Construct the lazy column layout attribute.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

## Examples

### Example 1: Implementing Lazy-Loading Linear Layout

This example demonstrates how to use the [Scroll](ts-container-scroll.md) and LazyColumnLayout components to implement lazy-loading linear layout, and how to use [onVisibleIndexesChange](#onvisibleindexeschange) to return the start and end indexes when the viewport changes.

Since API version 26.0.0, the LazyColumnLayout component and the onVisibleIndexesChange event are supported.



```TypeScript
import { LengthMetrics, LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';

// Data structure of the following list.
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

// Data structure of the recommended list.
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
    new Follow('Alice', $r('app.media.icon'), 'Sharing is happiness!'), // $r('app.media.icon') needs to be replaced with the required image resource file.
    new Follow('Bob', $r('app.media.icon'), 'Photography enthusiast'),
    new Follow('Carol', $r('app.media.icon'), 'Sports make me happy'),
    new Follow('Dave', $r('app.media.icon'), 'Exploring unknown tech...'),
    // ...
  ]
  // Convert followList into an array of two elements each.
  private followPairs: Follow[][] = []
  private recommend: Recommend[] = [
    new Recommend('Emma', $r('sys.symbol.person_crop_circle_fill'), 'Feeling pretty good today...'),
    new Recommend('Frank', $r('sys.symbol.person_crop_circle_fill'), 'Reading at a cafe...'),
    new Recommend('Grace', $r('sys.symbol.person_crop_circle_fill'), 'Let's go hiking this weekend!'),
    new Recommend('Henry', $r('sys.symbol.person_crop_circle_fill'), 'Just finish a 5K run'),
    new Recommend('Ivy', $r('sys.symbol.person_crop_circle_fill'), 'Learned a new recipe'),
    new Recommend('John', $r('sys.symbol.person_crop_circle_fill'), 'Finally launched the project'),
    new Recommend('Kate', $r('sys.symbol.person_crop_circle_fill'), 'Listening to an old song...'),
    new Recommend('Leo', $r('sys.symbol.person_crop_circle_fill'), 'Ready to go on a trip'),
    new Recommend('Mike', $r('sys.symbol.person_crop_circle_fill'), 'What a beautiful day!'),
    new Recommend('Nina', $r('sys.symbol.person_crop_circle_fill'), 'Working overtime. Please do not disturb.'),
    new Recommend('Oscar', $r('sys.symbol.person_crop_circle_fill'), 'Got a little kitten'),
    new Recommend('Paul', $r('sys.symbol.person_crop_circle_fill'), 'Playing basketball.'),
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
          Text('Following:')

          // Nest LazyColumnLayout to display a two-column following list.
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

          Text ('Recommended:')

          // Use an independent LazyColumnLayout to display the recommended list.
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

### Example 2: Setting Header or Footer Components and Sticky Styles

This example nests LazyColumnLayout in [Scroll](ts-container-scroll.md) and implements top and bottom sticky styles through [header](#header), [footer](#footer), and [sticky](#sticky). During scrolling, the header sticks to the top of the viewport and the footer sticks to the bottom of the viewport.

Since API version 26.0.0, the header, footer, and sticky attributes are supported.

```TypeScript
import { LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';
// MyDataSource is a custom data source class that implements the IDataSource API required by LazyForEach.
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

  // Build the header component.
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
      // Set both header and footer to sticky.
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
