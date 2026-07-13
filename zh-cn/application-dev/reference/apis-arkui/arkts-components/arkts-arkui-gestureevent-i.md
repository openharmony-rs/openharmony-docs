# GestureEvent

定义手势的事件信息。继承自[BaseEvent](arkts-arkui-baseevent-i.md)。

**继承/实现关系：** GestureEvent extends [BaseEvent](arkts-arkui-baseevent-i.md)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: number
```

用于RotationGesture手势触发场景时，表示旋转角度，单位为deg。

用于SwipeGesture手势触发场景时，表示快滑手势的角度，即手指滑动的瞬时方向与水平正方向的夹角，单位为deg。

**说明：**

旋转角度计算方式：RotationGesture手势被识别到后，连接两根手指之间的线被识别为起始线条，随着手指的滑动，手指之间的线条会发生旋转，根据起始线条两端点和当前线条两端点的坐标，使用反正切函数分别计算其相对于水平方向的夹
角，最后arctan2(cy2-cy1,cx2-cx1)-arctan2(y2-y1,x2-x1)为旋转的角度。以起始线条为坐标系，顺时针旋转为0到180度，逆时针旋转为0到-180度。

取值范围：[-180, 180]

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingerInfos

```TypeScript
fingerInfos?: FingerInfo[]
```

由触屏产生的手势，fingerInfos中会包含触发事件的所有触点信息；由鼠标发起的手势，fingerInfos中只会有一条记录；触摸板的事件大类与鼠标一致，所以由触摸板发起的手势，fingerInfos只会携带一条记录。

**说明：**

fingerInfos只会记录参与触摸的有效手指信息，先按下但未参与当前手势触发的手指在fingerInfos中不会显示。默认值为空数组[]，返回空数组时，表示当前无有效触点信息。

**类型：** FingerInfo[]

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingerList

```TypeScript
fingerList: FingerInfo[]
```

输入源为触屏产生的手势，fingerList中会包含触发事件的所有触点信息；由鼠标发起的手势，fingerList中只会有一条记录；触摸板的事件大类与鼠标一致，所以由触摸板发起的手势，fingerList只会携带一条记录。

**说明：**

1. 手指索引编号与位置对应，即fingerList[index]的id为index。先按下且未参与当前手势触发的手指在fingerList中对应位置为空。
2. 当使用键盘或手柄触发手势时，不存在手指信息，fingerList为空。

**类型：** FingerInfo[]

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX: number
```

手势事件相对于手指按下时的偏移量X，单位为vp，用于PanGesture手势触发场景，从左向右滑动offsetX为正，反之为负。

取值范围：(-∞, +∞)

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY: number
```

手势事件相对于手指按下时的偏移量Y，单位为vp，用于PanGesture手势触发场景，从上向下滑动offsetY为正，反之为负。

取值范围：(-∞, +∞)

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pinchCenterX

```TypeScript
pinchCenterX: number
```

捏合手势中心点相对于当前组件元素原始区域左上角的x轴坐标，单位为vp，用于PinchGesture手势触发场景。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pinchCenterY

```TypeScript
pinchCenterY: number
```

捏合手势中心点相对于当前组件元素原始区域左上角的y轴坐标，单位为vp，用于PinchGesture手势触发场景。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat: boolean
```

是否为重复触发事件，用于LongPressGesture手势触发场景。true表示重复触发事件，false表示非重复触发事件。

**类型：** boolean

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale: number
```

缩放比例，用于PinchGesture手势触发场景。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed: number
```

快滑手势速度，即所有手指相对当前组件元素原始区域滑动的平均速度，单位为vp/s，用于SwipeGesture手势触发场景。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tapLocation

```TypeScript
tapLocation?: EventLocationInfo
```

用于点击手势中，获取当前手势的坐标信息。在非点击手势中，tapLocation返回值为undefined。

**类型：** EventLocationInfo

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity: number
```

用于[PanGesture](arkts-arkui-tapgesture-con.md#pangesture)手势中，获取当前手势的主方向速度。为xy轴方向速度的平方和的算术平方根。单位为vp/s。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocityX

```TypeScript
velocityX: number
```

用于[PanGesture](arkts-arkui-tapgesture-con.md#pangesture)手势中，获取当前手势的x轴方向速度。坐标轴原点为屏幕左上角，分正负方向速度，从左往右为正，反之为负。单位为vp/s。

取值范围：(-∞, +∞)

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocityY

```TypeScript
velocityY: number
```

用于[PanGesture](arkts-arkui-tapgesture-con.md#pangesture)手势中，获取当前手势的y轴方向速度。坐标轴原点为屏幕左上角，分正负方向速度，从上往下为正，反之为负。单位为vp/s。

取值范围：(-∞, +∞)

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

