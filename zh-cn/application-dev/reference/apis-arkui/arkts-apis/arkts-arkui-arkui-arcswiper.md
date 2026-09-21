# @ohos.arkui.ArcSwiper

## 导入模块

```TypeScript
import { ArcSwiper, ArcSwiperAttribute, ArcDotIndicator, ArcDirection, ArcSwiperController } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | 除支持通用属性外，还支持以下属性。 |
| [ArcSwiperController](arkts-arkui-arkui-arcswiper-arcswipercontroller-c.md) | ArcSwiper容器组件的控制器，可以将此对象绑定至ArcSwiper组件，可以通过它控制翻页。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcSwiperInterface](arkts-arkui-arkui-arcswiper-arcswiperinterface-i.md) | Provide an interface for ArcSwiper. |
| [SwiperContentAnimatedTransition](arkts-arkui-arkui-arcswiper-swipercontentanimatedtransition-i.md) | ArcSwiper自定义切换动画相关信息。 |
| [SwiperContentTransitionProxy](arkts-arkui-arkui-arcswiper-swipercontenttransitionproxy-i.md) | ArcSwiper自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画视窗内的页面信息，同时，也可以通过调用该对象的finishTransition接口通知ArcSwiper组件页面自定义动画已结束。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ArcDirection](arkts-arkui-arkui-arcswiper-arcdirection-e.md) | 弧形方向。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AnimationEndHandler](arkts-arkui-animationendhandler-t.md) | 切换动画结束时的回调。 |
| [AnimationStartHandler](arkts-arkui-animationstarthandler-t.md) | 切换动画开始时的回调。 |
| [FinishAnimationHandler](arkts-arkui-finishanimationhandler-t.md) | 停止播放动画时，告知应用。 |
| [GestureSwipeHandler](arkts-arkui-gestureswipehandler-t.md) | 在页面跟手滑动过程中，逐帧触发的回调。 |
| [IndexChangedHandler](arkts-arkui-indexchangedhandler-t.md) | 当前显示元素的索引变化时，告知应用。index序列从0开始。 |

### 属性

| 名称 | 说明 |
| --- | --- |
| [ArcSwiper](arkts-arkui-arkui-arcswiper-p.md) | Defines the ArcSwiper Component that can provide the ability for sub components to swipe and display. |
| [ArcSwiperInstance](arkts-arkui-arkui-arcswiper-p.md) | Defines ArcSwiper Component instance. |

## 示例

### 示例1（设置ArcSwiper基本属性）

该示例通过设置ArcSwiper的基本属性，展示了组件的基本功能。



```TypeScript
// xxx.ets
import {
  CircleShape,
  ArcSwiper,
  ArcSwiperAttribute, 
  ArcDotIndicator,
  ArcDirection,
  ArcSwiperController
} from '@kit.ArkUI';
// 从API version 22开始，无需手动导入ArcSwiperAttribute。具体请参考ArcSwiper的导入模块说明

class MyDataSource implements IDataSource {
  private list: Color[] = [];

  constructor(list: Color[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): Color {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct TestNewInterface {
  @State itemSimpleColor: Color | number | string = '';
  @State selectedItemSimpleColor: Color | number | string = '';
  private wearableSwiperController: ArcSwiperController = new ArcSwiperController();
  private arcDotIndicator: ArcDotIndicator = new ArcDotIndicator();
  private data: MyDataSource = new MyDataSource([]);
  @State backgroundColors: Color[] =
    [Color.Green, Color.Blue, Color.Yellow, Color.Pink, Color.White, Color.Gray, Color.Orange, Color.Transparent];
  innerSelectedIndex: number = 0;

  aboutToAppear(): void {
    this.data = new MyDataSource(this.backgroundColors);
  }

  build() {
    Column() {
      Row() {
        ArcSwiper(this.wearableSwiperController) {
          LazyForEach(this.data, (backgroundColor: Color, index: number) => {
            Text(index.toString())
              .width(233)
              .height(233)
              .backgroundColor(backgroundColor)
              .textAlign(TextAlign.Center)
              .fontSize(30)
          })
        }
        .clipShape(new CircleShape({ width: 233, height: 233 }))
        .effectMode(EdgeEffect.None)
        .backgroundColor(Color.Transparent)
        .index(0)
        .duration(400)
        .vertical(false)
        .indicator(this.arcDotIndicator
          .arcDirection(ArcDirection.SIX_CLOCK_DIRECTION)
          .itemColor(this.itemSimpleColor)
          .selectedItemColor(this.selectedItemSimpleColor)
        )
        .disableSwipe(false)
        .digitalCrownSensitivity(CrownSensitivity.MEDIUM)
        .onChange((index: number) => {
          console.info('onChange:' + index.toString());
        })
        .onAnimationStart((index: number, targetIndex: number, extraInfo: SwiperAnimationEvent) => {
          this.innerSelectedIndex = targetIndex;
          console.info('index: ' + index);
          console.info('targetIndex: ' + targetIndex);
          console.info('current offset: ' + extraInfo.currentOffset);
          console.info('target offset: ' + extraInfo.targetOffset);
          console.info('velocity: ' + extraInfo.velocity);
        })
        .onGestureRecognizerJudgeBegin((event: BaseGestureEvent, current: GestureRecognizer,
          others: Array<GestureRecognizer>): GestureJudgeResult => { // 在识别器即将要成功时，根据当前组件状态，设置识别器使能状态
          if (current) {
            let target = current.getEventTargetInfo();
            if (target && current.isBuiltIn() && current.getType() == GestureControl.GestureType.PAN_GESTURE) {
              // 此处判断swiperTarget.isBegin()或innerSelectedIndex === 0，表明ArcSwiper滑动到开头
              let swiperTarget = target as ScrollableTargetInfo;
              if (swiperTarget instanceof ScrollableTargetInfo &&
                (swiperTarget.isBegin() || this.innerSelectedIndex === 0)) {
                let panEvent = event as PanGestureEvent;
                if (panEvent && panEvent.offsetX > 0 && (swiperTarget.isBegin() || this.innerSelectedIndex === 0)) {
                  return GestureJudgeResult.REJECT;
                }
              }
            }
          }
          return GestureJudgeResult.CONTINUE;
        })
        .onAnimationEnd((index: number, extraInfo: SwiperAnimationEvent) => {
          console.info('index: ' + index);
          console.info('current offset: ' + extraInfo.currentOffset);
        })
        .disableTransitionAnimation(false)
      }.height('100%')
    }.width('100%')
  }
}
```

### 示例2（设置ArcSwiper自定义页面切换动画）

该示例通过customContentTransition接口，实现了自定义ArcSwiper页面切换动画。

```TypeScript
import { Decimal } from '@kit.ArkTS';
import { CircleShape, ArcSwiper, ArcSwiperAttribute } from '@kit.ArkUI';

// 从API version 22开始，无需手动导入ArcSwiperAttribute。具体请参考ArcSwiper的导入模块说明
@Entry
@Component
struct TestNewInterface {
  private backgroundColors: Color[] =
    [Color.Green, Color.Blue, Color.Yellow, Color.Pink, Color.White, Color.Gray, Color.Orange];
  @State scaleList: number[] = [];

  aboutToAppear(): void {
    for (let i = 0; i < this.backgroundColors.length; i++) {
      this.scaleList.push(1.0);
    }
  }

  build() {
    Column() {
      Row() {
        ArcSwiper() {
          ForEach(this.backgroundColors, (backgroundColor: Color, index: number) => {
            Text(index.toString())
              .width(233)
              .height(233)
              .backgroundColor(backgroundColor)
              .textAlign(TextAlign.Center)
              .fontSize(30)
              .scale({ x: this.scaleList[index], y: this.scaleList[index] })
          })
        }
        .clipShape(new CircleShape({ width: 233, height: 233 }))
        .effectMode(EdgeEffect.None)
        .onChange((index: number) => {
          console.info('onChange:' + index.toString());
        })
        .customContentTransition({
          // 页面移除视窗时超时1000ms下渲染树
          timeout: 1000,
          // 对视窗内所有页面逐帧回调transition，在回调中修改scale属性值，实现自定义动画
          transition: (proxy: SwiperContentTransitionProxy) => {
            if (proxy.position <= -1 || proxy.position >= 1) {
              // 页面完全滑出视窗外时，重置属性值
              this.scaleList[proxy.index] = 1.0;
            } else {
              let position: number = Decimal.abs(proxy.position).toNumber();
              this.scaleList[proxy.index] = 1 - position;
            }
          }
        })
        .disableTransitionAnimation(false)
      }.height('100%')
    }.width('100%')
  }
}
```
