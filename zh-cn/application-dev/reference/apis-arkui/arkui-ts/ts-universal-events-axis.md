# 轴事件

轴事件指组件被鼠标滚轮滚动或触控板双指沿特定方向（轴）滑动进行交互时触发的事件。此处“轴”指的是二维坐标系中的方向，分为水平方向（X轴）和垂直方向（Y轴）。

>  **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 17开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## onAxisEvent

ArkTS-Dyn: onAxisEvent(event: (event: AxisEvent) => void): T

ArkTS-Sta: onAxisEvent(event: Callback<AxisEvent> | undefined): this

鼠标滚轮滚动或触控板双指移动触发该回调。

**卡片能力：** 从API version 17开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 17

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | ArkTS-Dyn: [AxisEvent](#axisevent) <br/>ArkTS-Sta: Callback\<[AxisEvent](#axisevent)> \|&nbsp;undefined | 是   | 获得[AxisEvent](#axisevent)对象。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTs-Dyn: T<br/>ArkTs-Sta: this | 返回当前组件。 |

## AxisEvent

轴事件的对象说明，继承于[BaseEvent](ts-gesture-customize-judge.md#baseevent对象说明8)。

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称            | 类型  | 只读|可选                              | 说明                                                    |
| ------------------- | -----------------------|------|----- | -------------------------------------------------------- |
| action              | [AxisAction](ts-appendix-enums.md#axisaction17)         | 否   | 否   | 轴事件的动作类型。<br/>**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。                    <br/>**ArkTS-Dyn起始版本：** 17<br/>**ArkTS-Sta起始版本：** 23 |
| x                   | ArkTs-Dyn: number<br/>ArkTs-Sta: double                 | 否   | 否   | 鼠标光标相对于被点击元素左边缘的X坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。   <br/>**ArkTS-Dyn起始版本：** 17<br/>**ArkTS-Sta起始版本：** 23 |
| y                   | ArkTs-Dyn: number<br/>ArkTs-Sta: double                 | 否   | 否   | 鼠标光标相对于被点击元素上边缘的Y坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。   <br/>**ArkTS-Dyn起始版本：** 17<br/>**ArkTS-Sta起始版本：** 23 |
| windowX             | ArkTs-Dyn: number<br/>ArkTs-Sta: double                 | 否   | 否   | 鼠标光标相对于当前窗口左上角的X坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。  <br/>**ArkTS-Dyn起始版本：** 17<br/>**ArkTS-Sta起始版本：** 23 |
| windowY             | ArkTs-Dyn: number<br/>ArkTs-Sta: double                 | 否   | 否   | 鼠标光标相对于当前窗口左上角的Y坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。  <br/>**ArkTS-Dyn起始版本：** 17<br/>**ArkTS-Sta起始版本：** 23 |
| displayX            | ArkTs-Dyn: number<br/>ArkTs-Sta: double                 | 否   | 否   | 鼠标光标相对于当前屏幕左上角的X坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。  <br/>**ArkTS-Dyn起始版本：** 17<br/>**ArkTS-Sta起始版本：** 23 |
| displayY            | ArkTs-Dyn: number<br/>ArkTs-Sta: double                 | 否   | 否   | 鼠标光标相对于当前屏幕左上角的Y坐标。<br/>单位：vp<br/>**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。  <br/>**ArkTS-Dyn起始版本：** 17<br/>**ArkTS-Sta起始版本：** 23 |
| scrollStep          | ArkTs-Dyn: number<br/>ArkTs-Sta: int                 | 否   | 是   | 鼠标轴滚动步长配置。<br/> **说明：**&nbsp;仅支持鼠标滚轮，取值范围0~65535。<br/>**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。 <br/>**ArkTS-Dyn起始版本：** 17<br/>**ArkTS-Sta起始版本：** 23 |
| propagation         | Callback\<void>        | 否   | 否   | 激活事件冒泡。<br/>**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。   <br/>**ArkTS-Dyn起始版本：** 17<br/>**ArkTS-Sta起始版本：** 23 |
| globalDisplayX<sup>20+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否 | 是 | 鼠标光标相对于全局屏幕的左上角的X坐标。<br/>单位：vp<br/>取值范围：[0, +∞)<br/>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 <br/>**模型约束：** 此接口仅可在Stage模型下使用。  <br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 24 |
| globalDisplayY<sup>24+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否 | 是 | 鼠标光标相对于全局屏幕的左上角的Y坐标。<br/>单位：vp<br/>取值范围：[0, +∞)<br/>**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。 <br/>**模型约束：** 此接口仅可在Stage模型下使用。  <br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 24 |

### getHorizontalAxisValue

ArkTs-Dyn: getHorizontalAxisValue(): number

ArkTs-Sta: getHorizontalAxisValue(): double

获取此次轴事件的水平轴值。

**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 17

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型              |说明       |
| ------- | --------------------------------- | 
| ArkTs-Dyn: number<br/>ArkTs-Sta: double | 水平轴值。<br>单位：vp |

### getVerticalAxisValue

ArkTs-Dyn: getVerticalAxisValue(): number

ArkTs-Sta: getVerticalAxisValue(): double

获取此次轴事件的垂直轴值。

**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 17

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型              |说明       |
| ------- | --------------------------------- | 
| ArkTs-Dyn: number<br/>ArkTs-Sta: double | 垂直轴值。<br>单位：vp |

## 示例

该示例通过按钮设置了轴事件，在按钮上滚动鼠标滚轮可获取轴事件的相关参数。

```ts
// xxx.ets
@Entry
@Component
struct AxisEventExample {
  @State text: string = ''

  build() {
    Column() {
      Row({ space: 20 }) {
        Button('AxisEvent').width(100).height(40)
          .onAxisEvent((event?: AxisEvent) => {
            if (event) {
              this.text =
                'AxisEvent:' + '\n  action:' + event.action + '\n  displayX:' + event.displayX + '\n  displayY:' +
                event.displayY + '\n  windowX:' + event.windowX + '\n  windowY:' + event.windowY + '\n  x:' + event.x +
                  '\n  y:' + event.y + '\n VerticalAxisValue:' + event.getVerticalAxisValue() +
                  '\n HorizontalAxisValue:' + event.getHorizontalAxisValue()
            }
          })
      }.margin(20)

      Text(this.text).margin(15)
    }.width('100%')
  }
}
```

鼠标滚轮滚动时：

![onAxisEvent](figures/onAxisEvent.png)
