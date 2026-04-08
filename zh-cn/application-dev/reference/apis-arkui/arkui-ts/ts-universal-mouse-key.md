# 鼠标事件

在鼠标的单个动作触发多个事件时，事件的顺序是固定的，鼠标事件默认透传。

>  **说明：**
>
>  - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
>  - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  - 目前仅支持通过外接鼠标触发。

## onMouse

ArkTS-Dyn: onMouse(event: (event: MouseEvent) => void): T

ArkTS-Sta: onMouse(event: ((event: MouseEvent) => void) | undefined): this

当前组件被鼠标按键点击时或者鼠标在组件上悬浮移动时，触发该回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                              | 必填 | 说明                                                         |
| ------- | --------------------------------- | ---- | ------------------------------------------------------------ |
| event | ArkTS-Dyn: (event: [MouseEvent](#mouseevent对象说明)) => void <br/>ArkTS-Sta: ((event: [MouseEvent](#mouseevent对象说明)) => void) \|&nbsp;undefined | 是   | 返回触发事件时的时间戳、鼠标按键、动作、鼠标位置在整个屏幕上的坐标和相对于当前组件的坐标。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前组件。 |

## MouseEvent对象说明

继承于[BaseEvent](ts-gesture-customize-judge.md#baseevent对象说明8)。

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                     | 属性类型                                     | 描述                           |
| ---------------------- | ---------------------------------------- | ---------------------------- |
| x                      | ArkTS-Dyn: number<br/>ArkTS-Sta: double  | 鼠标位置相对于当前组件左上角的x轴坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23         |
| y                      | ArkTS-Dyn: number<br/>ArkTS-Sta: double  | 鼠标位置相对于当前组件左上角的y轴坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23         |
| button                 | [MouseButton](ts-appendix-enums.md#mousebutton8) | 鼠标按键。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23                        |
| action                 | [MouseAction](ts-appendix-enums.md#mouseaction8) | 鼠标动作。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23                        |
| stopPropagation        | () => void                               | 阻塞事件冒泡。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23                      |
| windowX<sup>10+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double   | 鼠标位置相对于应用窗口左上角的x轴坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 23 |
| windowY<sup>10+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double   | 鼠标位置相对于应用窗口左上角的y轴坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 23 |
| displayX<sup>10+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double  | 鼠标位置相对于应用屏幕左上角的x轴坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 23 |
| displayY<sup>10+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double  | 鼠标位置相对于应用屏幕左上角的y轴坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 23 |
| screenX<sup>(deprecated)</sup> | number                 | 鼠标位置相对于应用窗口左上角的x轴坐标。<br>单位：vp<br/>从API version 10开始不再维护，建议使用windowX代替。<br/>**ArkTS模式：** 该字段仅适用于ArkTS-Dyn。<br/>**ArkTS-Dyn起始版本：** 8 |
| screenY<sup>(deprecated)</sup> | number                 | 鼠标位置相对于应用窗口左上角的y轴坐标。<br>单位：vp<br/>从API version 10开始不再维护，建议使用windowY代替。<br/>**ArkTS模式：** 该字段仅适用于ArkTS-Dyn。<br/>**ArkTS-Dyn起始版本：** 8 |
| rawDeltaX<sup>15+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 相对于先前上报的鼠标指针位置的X轴偏移量。当鼠标指针处于屏幕边缘时，该值可能小于两次上报的X坐标之差。<br/>单位：vp<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 15<br/>**ArkTS-Sta起始版本：** 23 |
| rawDeltaY<sup>15+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 相对于先前上报的鼠标指针位置的Y轴偏移量。<br/>单位：vp<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 15<br/>**ArkTS-Sta起始版本：** 23 |
| pressedButtons<sup>15+</sup> | MouseButton[] | 所有鼠标上按着的按钮集合。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 15<br/>**ArkTS-Sta起始版本：** 23 |
| targetDisplayId<sup>15+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 事件发生的屏幕ID。<br/>默认值：0<br/>取值范围：[0, +∞)<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 15<br/>**ArkTS-Sta起始版本：** 23 |
| globalDisplayX<sup>20+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 鼠标位置相对于全局屏幕的左上角的X坐标。<br/>单位：vp<br/>取值范围：[0, +∞)<br/>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**模型约束：** 此接口仅可在Stage模型下使用。  <br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 24 |
| globalDisplayY<sup>20+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 鼠标位置相对于全局屏幕的左上角的Y坐标。<br/>单位：vp<br/>取值范围：[0, +∞)<br/>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。<br/>**模型约束：** 此接口仅可在Stage模型下使用。  <br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 24 |

### getHistoricalPoints
 
ArkTS-Dyn: getHistoricalPoints?(): Array&lt;MouseHistoricalPoint&gt;

ArkTS-Sta: getHistoricalPoints(): MouseHistoricalPoint[] | undefined
 
获取当前帧的所有历史点信息。历史点可用于实现更平滑的绘制效果。

 **模型约束：** 此接口仅可在Stage模型下使用。
 
 **原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。
 
 **系统能力：** SystemCapability.ArkUI.ArkUI.Full

 **ArkTS-Dyn起始版本：** 26.0.0

 **ArkTS-Sta起始版本：** 26.0.0
 
 **返回值：**
 
 | 类型                                                 | 说明              |
 | -------------------------------------------------- | --------------- |
 | ArkTS-Dyn: Array&lt;[MouseHistoricalPoint](#mousehistoricalpoint)&gt;<br/>ArkTS-Sta: [MouseHistoricalPoint](#mousehistoricalpoint)[]&nbsp;\|&nbsp;undefined | 当前帧的所有历史点信息。当系统内部运行环境损坏时，将返回undefined。 |
 
## MouseHistoricalPoint
 
鼠标事件历史点信息。

历史点按时间顺序排列，获取到的第一个历史点是最早发生的事件的信息，最后一个是最新发生事件的信息。历史点的数量取决于系统事件队列的配置和硬件性能。历史点主要用于如下场景：
 
 1. 平滑绘制：使用历史点可以实现更平滑的绘制效果，特别是在鼠标快速移动时。
 
 2. 手势识别：通过分析历史点的轨迹，可以识别各种鼠标手势。
 
 3. 性能优化：在一个事件回调中处理多个历史点，减少事件处理频率，提升性能。
 
 4. 轨迹分析：分析鼠标移动轨迹，用于绘图应用或手势控制。

 5. 数据分析：历史点中的timestamp可用于计算鼠标移动速度。

 **模型约束：** 此接口仅可在Stage模型下使用。
 
 **原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。
 
 **系统能力：** SystemCapability.ArkUI.ArkUI.Full

 **ArkTS-Dyn起始版本：** 26.0.0

 **ArkTS-Sta起始版本：** 26.0.0
 
 | 名称         | 类型        | 只读 | 可选 | 说明                                      |
 | ---------- | --------- | ---- | ---- | --------------------------------------- |
 | x          | ArkTS-Dyn: number<br/>ArkTS-Sta: double    | 是   | 否   | 鼠标指针相对于被点击组件左上角的X坐标。<br>单位：vp          |
 | y          | ArkTS-Dyn: number<br/>ArkTS-Sta: double    | 是   | 否   | 鼠标指针相对于被点击组件左上角的Y坐标。<br>单位：vp          |
 | displayX   | ArkTS-Dyn: number<br/>ArkTS-Sta: double    | 是   | 否   | 鼠标指针相对于整个屏幕左上角的X坐标。<br>单位：vp            |
 | displayY   | ArkTS-Dyn: number<br/>ArkTS-Sta: double    | 是   | 否   | 鼠标指针相对于整个屏幕左上角的Y坐标。<br>单位：vp            |
 | windowX    | ArkTS-Dyn: number<br/>ArkTS-Sta: double    | 是   | 否   | 鼠标指针相对于应用窗口左上角的X坐标。<br>单位：vp            |
 | windowY    | ArkTS-Dyn: number<br/>ArkTS-Sta: double    | 是   | 否   | 鼠标指针相对于应用窗口左上角的Y坐标。<br>单位：vp            |
 | globalDisplayX | ArkTS-Dyn: number<br/>ArkTS-Sta: double| 是   | 否   |鼠标位置在[全局坐标系](../../../windowmanager/window-terminology.md#全局坐标系)中的X坐标。<br>单位：vp  |
 | globalDisplayY | ArkTS-Dyn: number<br/>ArkTS-Sta: double| 是   | 否   |鼠标位置在[全局坐标系](../../../windowmanager/window-terminology.md#全局坐标系)中的Y坐标。<br>单位：vp  |
 | timestamp  | ArkTS-Dyn: number<br/>ArkTS-Sta: long      | 是   | 否   | 鼠标事件的时间戳。<br>单位：ns                              |

## 示例

### 示例1（使用鼠标事件）

该示例通过按钮设置了鼠标事件，通过鼠标点击按钮可以触发onMouse事件，获取鼠标事件相关参数。
鼠标滚轮的处理请参考[轴事件示例](ts-universal-events-axis.md#示例)。

```ts
// xxx.ets
@Entry
@Component
struct MouseEventExample {
  @State hoverText: string = 'no hover';
  @State mouseText: string = '';
  @State action: string = '';
  @State mouseBtn: string = '';
  @State color: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Button(this.hoverText)
        .width(180).height(80)
        .backgroundColor(this.color)
        .onHover((isHover: boolean, event: HoverEvent) => {
          // 通过onHover事件动态修改按钮在是否有鼠标悬浮时的文本内容与背景颜色
          if (isHover) {
            this.hoverText = 'hover';
            this.color = Color.Pink;
          } else {
            this.hoverText = 'no hover';
            this.color = Color.Blue;
          }
        })
      Button('onMouse')
        .width(180).height(80)
        .onMouse((event: MouseEvent):void => {
          if(event){
            switch (event.button) {
              case MouseButton.None:
                this.mouseBtn = 'None';
                break;
              case MouseButton.Left:
                this.mouseBtn = 'Left';
                break;
              case MouseButton.Right:
                this.mouseBtn = 'Right';
                break;
              case MouseButton.Back:
                this.mouseBtn = 'Back';
                break;
              case MouseButton.Forward:
                this.mouseBtn = 'Forward';
                break;
              case MouseButton.Middle:
                this.mouseBtn = 'Middle';
                break;
            }
            switch (event.action) {
              case MouseAction.Hover:
                this.action = 'Hover';
                break;
              case MouseAction.Press:
                this.action = 'Press';
                break;
              case MouseAction.Move:
                this.action = 'Move';
                break;
              case MouseAction.Release:
                this.action = 'Release';
                break;
            }
            this.mouseText = 'onMouse:\nButton = ' + this.mouseBtn +
            '\nAction = ' + this.action + '\nXY=(' + event.x + ',' + event.y + ')' +
            '\nwindowXY=(' + event.windowX + ',' + event.windowY + ')' +
            '\ntargetDisplayId = ' + event.targetDisplayId +
            '\nrawDeltaX = ' + event.rawDeltaX +
            '\nrawDeltaY = ' + event.rawDeltaY +
            '\nlength = ' + event.pressedButtons?.length;
          }
        })
      Text(this.mouseText)
    }.padding({ top: 30 }).width('100%')
  }
}
```

示意图：

鼠标点击时：

![mouse](figures/mouse.gif)

### 示例2（获取当前帧历史点）

该示例通过调用[getHistoricalPoints](#gethistoricalpoints)接口，获取到触发重采样时的历史点，可以用来实现更平滑的绘制等操作。

从API版本26.0.0开始，新增getHistoricalPoints接口。

ArkTS-Dyn示例：
```ts
@Entry
@Component
struct HistoricalPointsExample {
  historicalPointsInfo: string = ''

  build() {
    Column() {
      Button('鼠标移动获取历史点')
        .width(180)
        .height(80)
        .onMouse((event: MouseEvent) => {
          if (event.action === MouseAction.Move) {
            const historicalPoints = event.getHistoricalPoints?.();
            if (historicalPoints) {
              this.historicalPointsInfo = `历史点数量: ${historicalPoints.length}\n`;
              historicalPoints.forEach((point: MouseHistoricalPoint, index: number) => {
                this.historicalPointsInfo += `点${index}: (${point.x}, ${point.y})\n`;
              });
              console.info(this.historicalPointsInfo);
            }
          }
        })
    }.padding({ top: 30 })
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：
```ts
import { Entry, Column, Component, Button, MouseEvent, MouseHistoricalPoint, MouseAction } from '@kit.ArkUI';

@Entry
@Component
struct MouseEventExample {
  historicalPointsInfo: string = ''

  build() {
    Column() {
      Button('鼠标移动获取历史点')
        .width(180)
        .height(80)
        .onMouse((event: MouseEvent): void => {
          if (event.action === MouseAction.Move) {
            let historicalPoints: MouseHistoricalPoint[] | undefined = event.getHistoricalPoints();
            if (historicalPoints !== undefined) {
              this.historicalPointsInfo = `历史点数量: ${historicalPoints.length}\n`;
              for (let index: int = 0; index < historicalPoints.length; index++) {
                this.historicalPointsInfo += `点${index}: (${historicalPoints[index].x}, ${historicalPoints[index].y})\n`;
              }
            }
            console.info(this.historicalPointsInfo);
          }
        })
    }.padding({ top: 30 })
    .width('100%')
  }
}
```