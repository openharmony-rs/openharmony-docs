# GestureControl

```TypeScript
declare namespace GestureControl
```

定义手势竞争结果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GestureType](arkts-arkui-tapgesture-comp-gesturetype-e.md) | 定义手势类型。 |

## 示例

该示例通过LongPressGesture实现了长按手势的识别。从API version 22开始，支持通过[LongPressGestureHandlerOptions](./ts-gesturehandler.md#longpressgesturehandleroptions)的allowableMovement属性设置识别手势的最大移动距离。

```TypeScript
// xxx.ets
@Entry
@Component
struct LongPressGestureExample {
  @State count: number = 0;

  build() {
    Column() {
      Text('LongPress onAction:' + this.count).fontSize(28)
        // 单指长按文本触发该手势事件。
        .gesture(
        // 设置长按手势识别器识别的手势的最大移动距离为200px。
        LongPressGesture({ repeat: true, allowableMovement: 200 })
          // 由于repeat设置为true，长按动作存在时会连续触发，触发间隔为duration（默认值500ms）。
          .onAction((event: GestureEvent) => {
            if (event && event.repeat) {
              this.count++;
            }
          })
            // 长按动作一结束触发。
          .onActionEnd(() => {
            this.count = 0;
          })
        )
    }
    .height(200)
    .width(300)
    .padding(20)
    .border({ width: 3 })
    .margin(30)
  }
}
```

### 示例1（双击手势识别）

该示例通过TapGesture实现了双击手势的识别。



```TypeScript
// xxx.ets
@Entry
@Component
struct TapGestureExample {
  @State value: string = '';

  build() {
    Column() {
      // 单指双击文本触发手势事件
      Text('Click twice').fontSize(28)
        .gesture(
        TapGesture({ count: 2 })
          .onAction((event: GestureEvent) => {
            if (event) {
              this.value = JSON.stringify(event.fingerList[0]);
            }
          })
        );
      Text(this.value);
    }
    .height(300)
    .width(300)
    .padding(20)
    .border({ width: 3 })
    .margin(30);
  }
}
```

### 示例2（获取单击手势坐标）

该示例通过TapGesture获取单击手势点击位置的坐标。



```TypeScript
// xxx.ets
@Entry
@Component
struct TapGestureExample {

  build() {
    Column() {
      Text('Click Once').fontSize(28)
        .gesture(
          TapGesture({ count: 1, fingers: 1 })
            .onAction((event: GestureEvent | undefined) => {
              if (event) {
                console.info(`x = ${JSON.stringify(event.tapLocation?.x)}`);
                console.info(`y = ${JSON.stringify(event.tapLocation?.y)}`);
                console.info(`windowX = ${JSON.stringify(event.tapLocation?.windowX)}`);
                console.info(`windowY = ${JSON.stringify(event.tapLocation?.windowY)}`);
                console.info(`displayX = ${JSON.stringify(event.tapLocation?.displayX)}`);
                console.info(`displayY = ${JSON.stringify(event.tapLocation?.displayY)}`);
                // 从API version 23开始，新增globalDisplayX和globalDisplayY属性。
                console.info(`globalDisplayX = ${JSON.stringify(event.tapLocation?.globalDisplayX)}`);
                console.info(`globalDisplayY = ${JSON.stringify(event.tapLocation?.globalDisplayY)}`);
              }
            })
        );
    }
    .height(200)
    .width(300)
    .padding(20)
    .border({ width: 3 })
    .margin(30)
  }
}
```

### 示例3（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取点击位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct GetCurrentLocalPositionExample {
  @State positionText: string = '';
  @State textOffsetY: number = 0;

  build() {
    Column() {
      Button('点击获取点击位置相对于当前组件实时位置左上角的坐标').translate({ y: this.textOffsetY })
        .gesture(
          TapGesture({ count: 1 })
            .onAction((event: GestureEvent) => {
              if (event) {
                // 移动组件后延迟获取点击位置相对于组件实时位置左上角的坐标。
                this.textOffsetY = -200;
                setTimeout(() => {
                  let localPos: Coordinate2D | undefined = event?.tapLocation?.getCurrentLocalPosition?.();
                  this.positionText = `相对于当前组件实时位置左上角的坐标:\n  x: ${localPos?.x ?? 0}\n  y: ${localPos?.y ?? 0}`;
                }, 2000);
              }
            })
        );

      Text(this.positionText);
    }.width('100%');
  }
}
```

该示例通过PanGesture实现了单指/双指滑动手势的识别。

```TypeScript
// xxx.ets
@Entry
@Component
struct PanGestureExample {
  @State offsetX: number = 0;
  @State offsetY: number = 0;
  @State positionX: number = 0;
  @State positionY: number = 0;
  private panOption: PanGestureOptions = new PanGestureOptions({ direction: PanDirection.Left | PanDirection.Right });

  build() {
    Column() {
      Column() {
        Text('PanGesture offset:\nX: ' + this.offsetX + '\n' + 'Y: ' + this.offsetY)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .translate({ x: this.offsetX, y: this.offsetY, z: 0 }) // 以组件左上角为坐标原点进行移动
      // 左右滑动触发该手势事件
      .gesture(
      PanGesture(this.panOption)
        .onActionStart((event: GestureEvent) => {
          console.info('Pan start');
          console.info(`Pan start timeStamp is: ${event.timestamp}`);
        })
        .onActionUpdate((event: GestureEvent) => {
          if (event) {
            // 根据滑动偏移量更新组件当前位置
            this.offsetX = this.positionX + event.offsetX;
            this.offsetY = this.positionY + event.offsetY;
          }
        })
        .onActionEnd((event: GestureEvent) => {
          // 滑动结束后保存当前位置，作为下一次滑动的起始位置
          this.positionX = this.offsetX;
          this.positionY = this.offsetY;
          console.info('Pan end');
          console.info(`Pan end timeStamp is: ${event.timestamp}`);
        })
      )

      Button('修改PanGesture触发条件')
        .onClick(() => {
          // 将PanGesture手势事件触发条件改为双指以任意方向滑动
          this.panOption.setDirection(PanDirection.All);
          this.panOption.setFingers(2);
        })
    }
  }
}
```

该示例展示了如何实现快滑手势的识别。

```TypeScript
// xxx.ets
@Entry
@Component
struct SwipeGestureExample {
  @State rotateAngle: number = 0;
  @State speed: number = 1;

  build() {
    Column() {
      Column() {
        Text('SwipeGesture speed\n' + this.speed)
        Text('SwipeGesture angle\n' + this.rotateAngle)
      }
      .border({ width: 3 })
      .width(300)
      .height(200)
      .margin(100)
      .rotate({ angle: this.rotateAngle })
      // 单指竖直方向快滑时触发该事件
      .gesture(
      SwipeGesture({ direction: SwipeDirection.Vertical })
        .onAction((event: GestureEvent) => {
          if (event) {
            this.speed = event.speed;
            this.rotateAngle = event.angle;
          }
        })
      )
    }.width('100%');
  }
}
```

该示例通过配置RotationGesture实现了双指旋转手势的识别。

```TypeScript
// xxx.ets
@Entry
@Component
struct RotationGestureExample {
  @State angle: number = 0;
  @State rotateValue: number = 0;

  build() {
    Column() {
      Column() {
        Text('RotationGesture angle:' + this.angle)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(80)
      .rotate({ angle: this.angle })
      // 双指旋转触发该手势事件
      .gesture(
      RotationGesture()
        .onActionStart(() => {
          console.info('Rotation start');
        })
        .onActionUpdate((event: GestureEvent) => {
          if (event) {
            // 根据本次手势变化角度和已保存旋转角度，更新组件当前旋转角度。
            this.angle = this.rotateValue + event.angle;
          }
        })
        .onActionEnd(() => {
          // 手势结束时保存当前旋转角度，作为下一次旋转计算的初始值。
          this.rotateValue = this.angle;
          console.info('Rotation end');
        })
      )
    }.width('100%')
  }
}
```

### 示例1（实现简单缩放）

该示例通过配置PinchGesture实现了三指捏合手势的识别功能。



```TypeScript
// xxx.ets
@Entry
@Component
struct PinchGestureExample {
  @State scaleValue: number = 1;
  @State pinchValue: number = 1;
  @State pinchX: number = 0;
  @State pinchY: number = 0;

  build() {
    Column() {
      Column() {
        Text('PinchGesture scale:\n' + this.scaleValue)
        Text('PinchGesture center:\n(' + this.pinchX + ',' + this.pinchY + ')')
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin({ top: 100 })
      .scale({ x: this.scaleValue, y: this.scaleValue, z: 1 })
      // 三指捏合触发该手势事件
      .gesture(
      PinchGesture({ fingers: 3 }) // 三指捏合手势，用于缩放操作
        .onActionStart(() => {
          console.info('Pinch start');
        })
        // 捏合手势更新时，根据缩放比例和中心点坐标更新展示状态
        .onActionUpdate((event: GestureEvent) => {
          if (event) {
            this.scaleValue = this.pinchValue * event.scale;
            this.pinchX = event.pinchCenterX;
            this.pinchY = event.pinchCenterY;
          }
        })
        // 手势结束时保存当前缩放比例，作为下一次缩放的基准值
        .onActionEnd(() => {
          this.pinchValue = this.scaleValue;
          console.info('Pinch end');
        })
      )
    }.width('100%')
  }
}
```

### 示例2（实现图片跟手缩放）

通过配置PinchGesture，该示例实现了图片的跟手缩放效果。

```TypeScript
// xxx.ets
import { UIContext, display, matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct PinchGestureExample {
  private uiContext: UIContext = new UIContext();
  private contentWidth: number = 0;
  private contentHeight: number = 0;
  private scaleMin: number = 0.3;
  private scaleMax: number = 30.0;
  private screenWidth: number = 0;
  private screenHeight: number = 0;
  @State pointRatioX: number = 0;
  @State pointRatioY: number = 0;
  @State curScale: number = 1;
  @State preScale: number = 1;
  @State offsetX: number = 0;
  @State offsetY: number = 0;
  @State matrix: matrix4.Matrix4Transit = matrix4.identity()
    .translate({ x: this.offsetX, y: this.offsetY })
    .scale({ x: this.curScale, y: this.curScale });

  public updateMatrix(): void {
    this.matrix = matrix4.identity()
      .scale({ x: this.curScale, y: this.curScale })
      .translate({ x: this.uiContext.vp2px(this.offsetX), y: this.uiContext.vp2px(this.offsetY) });
  }

  aboutToAppear(): void {
    this.uiContext = this.getUIContext();
    let screenSize = display.getDefaultDisplaySync();
    this.screenWidth = this.uiContext.px2vp(screenSize.width);
    this.screenHeight = this.uiContext.px2vp(screenSize.height);
  }

  build() {
    Column() {
      // $r('app.media.img')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.img'))
        .objectFit(ImageFit.Contain)
        .draggable(false)
        .onComplete((event) => {
          this.contentWidth = this.uiContext.px2vp(event!.contentWidth);
          this.contentHeight = this.uiContext.px2vp(event!.contentHeight);
        })
        .transform(this.matrix)
    }
    // 双指捏合触发该手势事件
    .gesture(
      PinchGesture({ fingers: 2 }) // 双指捏合手势，用于缩放图片
        .onActionStart((event: GestureEvent) => {
          // 图片本次缩放前展示大小
          const displayWidth = this.contentWidth * this.curScale;
          const displayHeight = this.contentHeight * this.curScale;
          // 图片本次缩放前左上角顶点
          const left = (this.screenWidth - displayWidth) / 2 + this.offsetX;
          const top = (this.screenHeight - displayHeight) / 2 + this.offsetY;
          // 本次缩放前手指中点相对图片左上角顶点尺寸占图片展示尺寸的百分比
          this.pointRatioX = (event.pinchCenterX - left) / displayWidth;
          this.pointRatioY = (event.pinchCenterY - top) / displayHeight;
          // 图片本次缩放前的缩放比例
          this.preScale = this.curScale;
        })
        .onActionUpdate((event: GestureEvent) => {
          // 目标缩放比
          this.curScale = this.preScale * event.scale;
          let targetDisplayWidth = this.contentWidth * this.curScale;
          let targetDisplayHeight = this.contentHeight * this.curScale;
          // 本次缩放前手指中点在本次缩放后的坐标
          const pointX = (this.screenWidth - targetDisplayWidth) / 2 + targetDisplayWidth * this.pointRatioX;
          const pointY = (this.screenHeight - targetDisplayHeight) / 2 + targetDisplayHeight * this.pointRatioY;
          // 将pointX、pointY移动到缩放后的手指中点，需要移动的距离
          this.offsetX = event.pinchCenterX - pointX;
          this.offsetY = event.pinchCenterY - pointY;
          this.updateMatrix();
        })
        .onActionEnd((event: GestureEvent) => {
          // 缩放比例超出允许范围时，重置图片的缩放比例和偏移量
          if (this.curScale < this.scaleMin || this.curScale > this.scaleMax) {
            this.curScale = 1;
            this.offsetX = 0;
            this.offsetY = 0;
            this.updateMatrix();
          }
        })
    )
  }
}
```
