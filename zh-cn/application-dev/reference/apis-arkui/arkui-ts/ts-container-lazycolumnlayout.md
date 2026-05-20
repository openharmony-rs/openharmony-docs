# LazyColumnLayout

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong; @rongShao-Z; @yangcan18-->
<!--Designer: @yylong-->
<!--Tester: @huchuyun-->
<!--Adviser: @Brilliantry_Rui-->

该组件用于实现支持懒加载的垂直线性布局，其父组件仅限于[List](ts-container-list.md)、[Scroll](ts-container-scroll.md)、[WaterFlow](ts-container-waterflow.md)或[FlowItem](ts-container-flowitem.md)，并支持使用自定义组件或[NodeContainer](ts-basic-components-nodecontainer.md)组件封装后应用在上述组件中。

该组件支持嵌套懒加载容器[LazyVGridLayout](ts-container-lazyvgridlayout.md)、[LazyVWaterFlowLayout](ts-container-lazyvwaterflowlayout.md)、及其自身LazyColumnLayout。

> **说明：**
>
> - LazyColumnLayout组件高度默认自适应内容，不建议设置高度、高度约束或宽高比，设置后会导致显示异常。
> - 该组件在不同父组件下的懒加载支持条件如下：
>   1. 在List组件下，要求List组件布局方向必须是竖直方向（即[listDirection](ts-container-list.md#listdirection)属性设置为Axis.Vertical），在非竖直方向的List中使用该组件会导致应用崩溃。当List设置了[lanes](ts-container-list.md#lanes9)、[chainAnimation](ts-container-list.md#chainanimation)、[scrollSnapAlign](ts-container-list.md#scrollsnapalign10)属性中的任意一个时，该组件的懒加载功能会失效。
>   2. 在Scroll组件下，要求Scroll组件布局方向必须是竖直方向（即[scrollable](ts-container-scroll.md#scrollable)属性设置为ScrollDirection.Vertical），在非竖直方向的Scroll中使用该组件会导致应用崩溃。
>   3. 在WaterFlow组件下，要求WaterFlow组件布局方向必须是竖直方向（即[layoutDirection](ts-container-waterflow.md#layoutdirection)属性设置为FlexDirection.Column），在非竖直方向的WaterFlow中使用该组件会导致应用崩溃。当WaterFlow为多列模式或布局方向为FlexDirection.Row、FlexDirection.RowReverse时，该组件的懒加载功能会失效。此外，在布局方向为FlexDirection.ColumnReverse的WaterFlow组件下使用该组件会导致显示异常。
> - 当懒加载功能生效时，该组件仅加载父组件显示区域内的子组件，并在帧间空闲时隙预加载显示区域上方和下方各半屏的内容。

**起始版本：** 26.0.0

## 导入模块

```ts
import { LazyColumnLayout } from '@kit.ArkUI';
```

## 接口

LazyColumnLayout()

创建垂直方向懒加载线性布局容器。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### space

space(space: LengthMetrics | undefined)

设置子组件在垂直方向上的间距。未通过该接口设置时，间距默认值为0vp。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                         | 必填 | 说明                         |
| ------ | ---------------------------- | ---- | ---------------------------- |
| space  |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| undefined | 是   | 子组件在垂直方向上的间距。<br/>设置为小于0的值时，按0vp显示。<br/>方法入参为undefined时，恢复为0vp。 |

### alignItems

alignItems(value: HorizontalAlign | undefined)

设置子组件在水平方向上的对齐格式。未通过该接口设置时，对齐格式默认值为HorizontalAlign.Center。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                                    | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [HorizontalAlign](ts-appendix-enums.md#horizontalalign) \| undefined | 是   | 子组件在水平方向上的对齐格式。<br/>方法入参为undefined时，恢复为HorizontalAlign.Center。 |

## 事件

除支持[通用事件](ts-component-general-events.md)外，还支持以下事件：

### onVisibleIndexesChange

onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined)

设置onVisibleIndexesChange回调函数。在LazyColumnLayout初始化时、可视区域内子组件的索引值发生变化时触发回调，返回可视区域内子组件的起始索引值和终止索引值。使用callback异步回调。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                  |
| ------ | ------ | ---- | ------------------------------------- |
| callback  | [OnVisibleIndexesChangeCallback](ts-container-scrollable-common.md#onvisibleindexeschangecallback) \| undefined | 是   | 回调函数。<br/>方法入参为undefined时，取消监听。 |

## 示例

### 示例1（实现懒加载线性布局）

通过[Scroll](ts-container-scroll.md)和LazyColumnLayout组件实现懒加载线性布局，并通过[onVisibleIndexesChange](#onvisibleindexeschange)在可视区域发生变化时回调索引。

从API版本26.0.0开始，新增支持LazyColumnLayout组件和onVisibleIndexesChange事件。

```ts
import { LengthMetrics, LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';

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
![scroll_lazycolumnlayout.png](figures/scroll_lazycolumnlayout.png)
