# GestureEvent

定义手势的事件信息。继承自BaseEvent。

**继承/实现关系：** GestureEvent extends BaseEvent

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface GestureEvent--><!--Device-unnamed-export interface GestureEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: double
```

用于RotationGesture手势触发场景时，表示旋转角度。 用于SwipeGesture手势触发场景时，表示快滑手势的角度，即两根手指间的线段与水平方向的夹角变化的度数。 **说明：** 角度计算方式：快滑手势被识别到后，连接两根手指之间的线被识别为起始线条，随着手指的滑动，手指之间的线条会发生旋转，根据起始线条两端点和当前线条两端点的坐标，使用反正切函数分别计算其相对于水平方向的夹角，最后arctan2(cy 2-cy1,cx2-cx1)-arctan2(y2-y1,x2-x1)为旋转的角度。以起始线条为坐标系，顺时针旋转为0到180度，逆时针旋转为-180到0度。 取值范围：[-180, +180]

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-angle: double--><!--Device-GestureEvent-angle: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingerInfos

```TypeScript
fingerInfos?: FingerInfo[]
```

由触屏产生的手势，fingerInfos中会包含触发事件的所有触点信息；由鼠标发起的手势，fingerInfos中只会有一条记录；触摸板的事件大类与鼠标一致，所以由触摸板发起的手势，fingerInfos只会携带一条记录。 **说明：** fingerInfos只会记录参与触摸的有效手指信息，先按下但未参与当前手势触发的手指在fingerInfos中不会显示。默认值为空数组[]，返回空数组时，表示当前无有效触点信息。

**类型：** [FingerInfo](arkts-arkui-gesture-fingerinfo-i.md)[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-fingerInfos?: FingerInfo[]--><!--Device-GestureEvent-fingerInfos?: FingerInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingerList

```TypeScript
fingerList: FingerInfo[]
```

输入源为触屏产生的手势，fingerList中会包含触发事件的所有触点信息；由鼠标发起的手势，fingerList中只会有一条记录；触摸板的事件大类与鼠标一致，所以由触摸板发起的手势，fingerList只会携带一条记录。 **说明：** 1. 手指索引编号与位置对应，即fingerList[index]的id为index。先按下且未参与当前手势触发的手指在fingerList中对应位置为空。 2. 当使用键盘或手柄触发手势时，不存在手指信息，fingerList为空。

**类型：** [FingerInfo](arkts-arkui-gesture-fingerinfo-i.md)[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-fingerList: FingerInfo[]--><!--Device-GestureEvent-fingerList: FingerInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX: double
```

手势事件相对于手指按下时的偏移量X，单位为vp，用于PanGesture手势触发场景，从左向右滑动offsetX为正，反之为负。 取值范围：(-∞, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-offsetX: double--><!--Device-GestureEvent-offsetX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY: double
```

手势事件相对于手指按下时的偏移量Y，单位为vp，用于PanGesture手势触发场景，从上向下滑动offsetY为正，反之为负。 取值范围：(-∞, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-offsetY: double--><!--Device-GestureEvent-offsetY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pinchCenterX

```TypeScript
pinchCenterX: double
```

捏合手势中心点相对于当前组件元素原始区域左上角的x轴坐标，单位为vp，用于PinchGesture手势触发场景。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-pinchCenterX: double--><!--Device-GestureEvent-pinchCenterX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pinchCenterY

```TypeScript
pinchCenterY: double
```

捏合手势中心点相对于当前组件元素原始区域左上角的y轴坐标，单位为vp，用于PinchGesture手势触发场景。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-pinchCenterY: double--><!--Device-GestureEvent-pinchCenterY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat: boolean
```

是否为重复触发事件，用于LongPressGesture手势触发场景。true表示重复触发事件，false表示非重复触发事件。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-repeat: boolean--><!--Device-GestureEvent-repeat: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale: double
```

缩放比例，用于PinchGesture手势触发场景。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-scale: double--><!--Device-GestureEvent-scale: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed: double
```

快滑手势速度，即所有手指相对当前组件元素原始区域滑动的平均速度，单位为vp/s，用于SwipeGesture手势触发场景。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-speed: double--><!--Device-GestureEvent-speed: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tapLocation

```TypeScript
tapLocation?: EventLocationInfo
```

用于点击手势中，获取当前手势的坐标信息。在非点击手势中，tapLocation返回值为undefined。

**类型：** [EventLocationInfo](arkts-arkui-gesture-eventlocationinfo-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-tapLocation?: EventLocationInfo--><!--Device-GestureEvent-tapLocation?: EventLocationInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity: double
```

用于PanGesture手势中，获取当前手势的主方向速度。为xy轴方向速度的平方和的算术平方根。单位为vp/s。 取值范围：0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-velocity: double--><!--Device-GestureEvent-velocity: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocityX

```TypeScript
velocityX: double
```

用于[PanGesture手势中，获取当前手势的x轴方向速度。坐标轴原点为屏幕左上角，分正负方向速度，从左往右为正，反之为负。单位为vp/s。 取值范围：(-∞, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-velocityX: double--><!--Device-GestureEvent-velocityX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocityY

```TypeScript
velocityY: double
```

用于PanGesture手势中，获取当前手势的y轴方向速度。坐标轴原点为屏幕左上角，分正负方向速度，从上往下为正，反之为负。单位为vp/s。 取值范围：(-∞, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureEvent-velocityY: double--><!--Device-GestureEvent-velocityY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

