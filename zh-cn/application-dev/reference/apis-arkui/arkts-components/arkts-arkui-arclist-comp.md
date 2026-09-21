# ArcList

弧形列表由沿弧形排列的一系列列表项组成，适用于圆形屏幕设备。适合连续、多行呈现同类数据，例如图片和文本。

> **说明：** > > - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

## 子组件

仅支持[ArcListItem](#ohosarkuiarclist)子组件。

> **说明：** 
> 
> ArcList的子组件索引值计算规则：
> 
> - 按子组件的顺序依次递增。
> 
> - [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)语句中，只有条件成立的分支内的子组件会参与索引值计算，条件不成立的分支内子组件不计算索引值。
> 
> - [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)/[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)语句中，会计算展开所有子组件索引值。
> 
> - [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)发生变化以后，会更新子组件索引值。
> 
> - ArcList子组件[visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility)属性设置为Hidden或None依然会计算索引值。

## ArcList

```TypeScript
ArcList(options?: ArkListOptions)
```

创建弧形列表实例，传入弧形列表配置项参数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArkListOptions](arkts-arkui-arclist-comp-arklistoptions-i.md) | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcListItemInterface](arkts-arkui-arclist-comp-arclistiteminterface-i.md) | 用于展示弧形列表的子组件，必须配合[ArcList](#ohosarkuiarclist)使用。 |
| [ArkListOptions](arkts-arkui-arclist-comp-arklistoptions-i.md) | 包含创建ArcList组件的基础参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ArcScrollIndexHandler](arkts-arkui-arclist-comp-arcscrollindexhandler-t.md) | 有子组件划入或划出ArcList显示区域时触发的回调。 |

## 示例

该示例增加了ArcList支持标题栏设置的效果，子项自动缩放显示。

```TypeScript
// xxx.ets
import { ComponentContent, LengthMetrics, UIContext, CircleShape } from '@kit.ArkUI';
// 从API version 22开始，无需手动导入ArcListAttribute和ArcListItemAttribute。具体请参考ArcList、ArcListItem的导入模块说明。
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';

@Builder
function buildText() {
  Column() {
    Text('header')
      .fontSize('60px')
      .fontWeight(FontWeight.Bold)
      .fontColor(Color.Black)
  }.margin(0)
}

@Entry
@Component
struct Index {
  @State private numItems: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  private watchSize: string = '466px'; // Wearable默认宽高：466*466
  private listSize: string = '414px'; // item宽度

  context: UIContext = this.getUIContext();
  headerContent: ComponentContent<Object> = new ComponentContent(this.context, wrapBuilder(buildText));

  @Builder
  buildList() {
    Stack() {
      Column() {
      }
      .justifyContent(FlexAlign.Center)
      .width(this.watchSize)
      .height(this.watchSize)
      .clipShape(new CircleShape({ width: '100%', height: '100%' }))
      .backgroundColor(Color.White)

      ArcList({ initialIndex: 0, header: this.headerContent }) {
        ForEach(this.numItems, (item: number, index: number) => {
          ArcListItem() {
            Button('' + item, { type: ButtonType.Capsule })
              .width(this.listSize)
              .height('100px')
              .fontSize('40px')
              .focusable(true)
              .focusOnTouch(true)
              .backgroundColor(0x17A98D)
          }.align(Alignment.Center)
        }, (item: number, index: number) => (item + index).toString())
      }
      .space(LengthMetrics.px(10))
      .borderRadius(this.watchSize)
      .focusable(true)
      .focusOnTouch(true)
      .defaultFocus(true)
    }
    .align(Alignment.Center)
    .width(this.watchSize)
    .height(this.watchSize)
    .border({color: Color.Black, width: 1})
    .borderRadius(this.watchSize)
  }

  build() {
    Column() {
      this.buildList()
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
    .justifyContent(FlexAlign.Center)
  }
}
```
