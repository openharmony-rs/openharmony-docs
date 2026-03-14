# PinchGesture

用于触发捏合手势，触发捏合手势的最少手指为2指，最大为5指，最小识别距离为5vp。

>  **说明：**
>
>  - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
>  - 从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
>  - 在捏合手势触发成功后，需要抬起所有手指，重新按下进行捏合才能再次触发捏合手势。


## 接口

PinchGesture(value?: { fingers?: number, distance?: number })

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[PinchGesture<sup>15+</sup>](#pinchgesture15)。

**ArkTS-Dyn起始版本：** 7

#### 参数

| 参数名称 | 参数类型 | 必填 | 参数描述 |
| -------- | -------- | -------- | -------- |
| fingers | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 触发捏合的最少手指数，&nbsp;最小为2指，最大为5指。<br/>默认值：2 <br/>触发手势手指可以多于fingers数目，但只有先落下的与fingers相同数目的手指参与手势计算。<br/>**ArkTS-Dyn起始版本：** 7<br/>**ArkTS-Sta起始版本：** 23 |
| distance | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否 | 最小识别距离，单位为vp。<br/>默认值：5 <br/>**说明：** <br/>取值范围：[0, +∞)。当识别距离的值小于等于0时，会被转化为默认值。<br/>**ArkTS-Dyn起始版本：** 7<br/>**ArkTS-Sta起始版本：** 23 |

### PinchGesture<sup>15+</sup>

PinchGesture(options?: PinchGestureHandlerOptions)

创建捏合手势对象。与[PinchGesture](#pinchgesture-1)相比，options参数新增了对isFingerCountLimited参数的支持。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明                     |
| ------- | ------------------------------------------------------------ | ---- | ------------------------ |
| options | [PinchGestureHandlerOptions](./ts-gesturehandler.md#pinchgesturehandleroptions) | 否   | 捏合手势处理器配置参数。 |


## 事件

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

>  **说明：**
>
>  在[GestureEvent](ts-gesture-settings.md#gestureevent对象说明)的fingerList元素中，手指索引编号与位置相对应，即fingerList[index]的id为index。对于先按下但未参与当前手势触发的手指，fingerList中对应的位置为空。建议优先使用fingerInfos。

| 名称 | 功能描述 |
| -------- | -------- |
| onActionStart(event:(event:&nbsp;[GestureEvent](ts-gesture-settings.md#gestureevent对象说明))&nbsp;=&gt;&nbsp;void) | Pinch手势识别成功回调。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 7<br/>**ArkTS-Sta起始版本：** 23 |
| onActionUpdate(event:(event:&nbsp;[GestureEvent](ts-gesture-settings.md#gestureevent对象说明))&nbsp;=&gt;&nbsp;void) | Pinch手势移动过程中回调。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 7<br/>**ArkTS-Sta起始版本：** 23 |
| onActionEnd(event:(event:&nbsp;[GestureEvent](ts-gesture-settings.md#gestureevent对象说明))&nbsp;=&gt;&nbsp;void) | Pinch手势识别成功，手指抬起后触发回调。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 7<br/>**ArkTS-Sta起始版本：** 23 |
| onActionCancel(event:&nbsp;()&nbsp;=&gt;&nbsp;void) | Pinch手势识别成功，接收到触摸取消事件触发回调。不返回手势事件信息。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 7<br/>**ArkTS-Sta起始版本：** 23 |
| onActionCancel(event:&nbsp;Callback<[GestureEvent](ts-gesture-settings.md#gestureevent对象说明)>)<sup>18+</sup> | Pinch手势识别成功，接收到触摸取消事件触发回调。返回手势事件信息。<br/>**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 18<br/>**ArkTS-Sta起始版本：** 23 |

## 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型    |描述                                        |
| ----  | ------  | ---------------------------------------- |
| tag<sup>11+</sup>   | string  | 设置Pinch手势标志，用于自定义手势判定时区分绑定的手势。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 23 |
| allowedTypes<sup>14+</sup> | Array\<[SourceTool](ts-gesture-settings.md#sourcetool枚举说明9)> | 设置Pinch手势支持的事件输入源。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 14<br/>**ArkTS-Sta起始版本：** 23 |

## 示例

该示例通过配置PinchGesture实现了三指捏合手势的识别。

```ts
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
      PinchGesture({ fingers: 3 })
        .onActionStart((event: GestureEvent) => {
          console.info('Pinch start')
        })
        .onActionUpdate((event: GestureEvent) => {
          if (event) {
            this.scaleValue = this.pinchValue * event.scale
            this.pinchX = event.pinchCenterX
            this.pinchY = event.pinchCenterY
          }
        })
        .onActionEnd((event: GestureEvent) => {
          this.pinchValue = this.scaleValue
          console.info('Pinch end')
        })
      )
    }.width('100%')
  }
}
```

 ![zh-cn_image_0000001174582848](figures/zh-cn_image_0000001174582848.png)
