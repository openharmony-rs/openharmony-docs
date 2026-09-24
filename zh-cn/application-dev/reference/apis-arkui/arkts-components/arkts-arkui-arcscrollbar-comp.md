# ArcScrollBar

弧形滚动条组件ArcScrollBar，适用于圆形屏幕等需要弧形滚动条的场景，用于配合可滚动组件使用，如[ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist)、[List](arkts-arkui-list-comp.md#list)、[Grid](arkts-arkui-grid-comp.md#grid)、[Scroll](arkts-arkui-scroll-comp.md#scroll)、[WaterFlow](arkts-arkui-waterflow-comp.md#water_flow)。

> **说明：** 
> 
> - 未设置宽高时，ArcScrollBar采用父组件[LayoutConstraint](../arkts-apis/arkts-arkui-framenode-layoutconstraint-i.md)中的maxSize作为尺寸。若父组件存在可滚动组件，如[ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist)、[List](arkts-arkui-list-comp.md#list)、[Grid](arkts-arkui-grid-comp.md#grid)、[Scroll](arkts-arkui-scroll-comp.md#scroll)、[WaterFlow](arkts-arkui-waterflow-comp.md#water_flow)，建议设置ArcScrollBar宽高，否则尺寸可能为无穷大。
> 
> - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

## 子组件

不包含子组件。

## ArcScrollBar

```TypeScript
ArcScrollBar(options: ArcScrollBarOptions)
```

ArcScrollBar的构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArcScrollBarOptions](arkts-arkui-arcscrollbar-comp-arcscrollbaroptions-i.md) | 是 | ArcScrollBar的配置参数，用于指定绑定的可滚动组件控制器和滚动条状态。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcScrollBarOptions](arkts-arkui-arcscrollbar-comp-arcscrollbaroptions-i.md) | ArcScrollBar的构造函数参数。 |

## 示例

该示例通过ArcScrollBar与[Scroll](ts-container-scroll.md)组件联动，设置了弧形外置滚动条。

```TypeScript
import { ArcScrollBar } from '@kit.ArkUI';

@Entry
@Component
struct ArcScrollBarExample {
  private scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  build() {
    Stack({ alignContent: Alignment.Center }) {
      Scroll(this.scroller) {
        Flex({ direction: FlexDirection.Column }) {
          ForEach(this.arr, (item: number) => {
            Row() {
              Text(item.toString())
                .width('80%')
                .height(60)
                .backgroundColor('#3366CC')
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 5 })
            }
          }, (item: number) => item.toString())
        }.margin({ right: 15 })
      }
      .width('90%')
      .scrollBar(BarState.Off)

      ArcScrollBar({ scroller: this.scroller, state: BarState.Auto })
    }
    .width('100%')
    .height('100%')
  }
}
```
