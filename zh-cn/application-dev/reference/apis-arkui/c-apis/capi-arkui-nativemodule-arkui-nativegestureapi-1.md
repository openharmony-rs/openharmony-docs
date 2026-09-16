# ArkUI_NativeGestureAPI_1

```c
typedef struct ArkUI_NativeGestureAPI_1 {...} ArkUI_NativeGestureAPI_1
```

## 概述

提供创建敲击、长按、滑动、捏合、旋转、快滑手势及手势组的接口，并支持绑定手势、移除手势、设置手势打断回调和并行内部手势回调，用于配置和管理组件的触控交互识别与事件处理。<br>使用该模块配置手势时，推荐按以下流程操作：调用[createTapGesture](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#createtapgesture)等接口创建手势识别器，调用[setGestureEventTarget](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setgestureeventtarget)注册手势事件回调，再调用[addGestureToNode](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#addgesturetonode)将手势识别器绑定至组件节点；不再使用该手势时，调用[dispose](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#dispose)释放手势资源，如需先解除节点绑定，可在调用dispose()前调用[removeGestureFromNode](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#removegesturefromnode)。对于手势竞争场景，可通过手势优先级、屏蔽模式或[setGestureInterrupterToNode](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setgestureinterruptertonode)配置响应策略；对于组件内部手势与外部自定义手势需要并行识别的场景，可调用[setInnerGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setinnergestureparallelto)设置并行内部手势事件回调。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t version | 结构版本号 = 1。 |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_GestureRecognizer* (\*createTapGesture)(int32_t countNum, int32_t fingersNum)](#createtapgesture) | 创建敲击手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。 |
| [ArkUI_GestureRecognizer* (\*createLongPressGesture)(int32_t fingersNum, bool repeatResult, int32_t durationNum)](#createlongpressgesture) | 创建长按手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。 |
| [ArkUI_GestureRecognizer* (\*createPanGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double distanceNum)](#createpangesture) | 创建滑动手势。与[createSwipeGesture](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#createswipegesture)（快滑手势）不同，滑动手势基于最小拖动距离触发，快滑手势基于最小滑动速度触发。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。 |
| [ArkUI_GestureRecognizer* (\*createPinchGesture)(int32_t fingersNum, double distanceNum)](#createpinchgesture) | 创建捏合手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。 |
| [ArkUI_GestureRecognizer* (\*createRotationGesture)(int32_t fingersNum, double angleNum)](#createrotationgesture) | 创建旋转手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。 |
| [ArkUI_GestureRecognizer* (\*createSwipeGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double speedNum)](#createswipegesture) | 创建快滑手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。 |
| [ArkUI_GestureRecognizer* (\*createGroupGesture)(ArkUI_GroupGestureMode gestureMode)](#creategroupgesture) | 创建手势组。创建成功后，可调用addChildGesture()向该手势组添加子手势，再通过addGestureToNode()将手势组绑定到节点；不再使用时可按需调用removeChildGesture()移除子手势，并调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。 |
| [void (\*dispose)(ArkUI_GestureRecognizer* recognizer)](#dispose) | 销毁通过createTapGesture()、createLongPressGesture()、createPanGesture()、createPinchGesture()、createRotationGesture()、createSwipeGesture()、createGroupGesture()或createTapGestureWithDistanceThreshold()创建的手势，释放资源。若手势已通过addGestureToNode()添加到节点，建议先调用removeGestureFromNode()解除节点绑定后再调用dispose()；调用dispose()后不得继续使用该手势指针。 |
| [int32_t (\*addChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)](#addchildgesture) | Adds a gesture to a gesture group. |
| [int32_t (\*removeChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)](#removechildgesture) | Removes a gesture from a gesture group. |
| [int32_t (\*setGestureEventTarget)(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventActionTypeMask actionTypeMask, void* extraParams,void (\*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams))](#setgestureeventtarget) | Registers a callback for gestures. |
| [int32_t (\*addGestureToNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer, ArkUI_GesturePriority mode,ArkUI_GestureMask mask)](#addgesturetonode) | Adds a gesture to a UI component. |
| [int32_t (\*removeGestureFromNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer)](#removegesturefromnode) | Removes a gesture from a node. |
| [int32_t (\*setGestureInterrupterToNode)(ArkUI_NodeHandle node, ArkUI_GestureInterruptResult (\*interrupter)(ArkUI_GestureInterruptInfo* info))](#setgestureinterruptertonode) | Sets a gesture interruption callback for a node. |
| [ArkUI_GestureRecognizerType (\*getGestureType)(ArkUI_GestureRecognizer* recognizer)](#getgesturetype) | 获取手势类别。 |
| [int32_t (\*setInnerGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (\*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event))](#setinnergestureparallelto) | Sets the callback function for the parallel internal gesture event. |
| [ArkUI_GestureRecognizer* (\*createTapGestureWithDistanceThreshold)(int32_t countNum, int32_t fingersNum, double distanceThreshold)](#createtapgesturewithdistancethreshold) | 创建带移动范围限制的敲击手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。 |

## 成员函数说明

### createTapGesture()

```c
ArkUI_GestureRecognizer* (*createTapGesture)(int32_t countNum, int32_t fingersNum)
```

**描述：**

创建敲击手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t countNum | 识别的连续点击次数，取值范围为大于0的整数。当设置的值小于1时，会被转化为默认值1。 |
|  int32_t fingersNum | 触发点击的手指数，最小为1指，最大为10指。当设置小于1的值时，按照最小值1处理；当设置大于10的值时，按照最大值10处理。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createLongPressGesture()

```c
ArkUI_GestureRecognizer* (*createLongPressGesture)(int32_t fingersNum, bool repeatResult, int32_t durationNum)
```

**描述：**

创建长按手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fingersNum | 触发长按的最少手指数，最小为1指，最大取值为10指。超出取值范围时按照默认值1处理。 |
|  bool repeatResult | 是否连续触发事件回调。<br>true：连续触发；false：不连续触发。 |
|  int32_t durationNum | 触发长按的最短时间，单位为毫秒（ms），有效值大于0。当传入的值小于等于0时，按照默认值500ms处理。当组件默认支持可拖拽时，长按触发时间小于500ms时长按事件优先拖拽事件响应；长按触发时间大于等于500ms时，拖拽事件优先长按事件响应。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createPanGesture()

```c
ArkUI_GestureRecognizer* (*createPanGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double distanceNum)
```

**描述：**

创建滑动手势。与[createSwipeGesture](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#createswipegesture)（快滑手势）不同，滑动手势基于最小拖动距离触发，快滑手势基于最小滑动速度触发。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fingersNum | 用于指定触发滑动的最少手指数，最小为1指，最大取值为10指。超出取值范围时按照默认值1处理。 |
|  ArkUI_GestureDirectionMask directions | 用于指定触发滑动的手势方向，此枚举值支持逻辑与(&)和逻辑或（\|）运算。可根据业务需要选择方向：GESTURE_DIRECTION_HORIZONTAL适用于只识别水平滑动的场景，GESTURE_DIRECTION_VERTICAL适用于只识别垂直滑动的场景，GESTURE_DIRECTION_LEFT/RIGHT/UP/DOWN适用于只识别单一方向滑动的场景，GESTURE_DIRECTION_ALL适用于任意方向均可触发的场景，GESTURE_DIRECTION_NONE表示任何方向都不触发手势事件。 |
|  double distanceNum | 用于指定触发滑动手势事件的最小拖动距离，取值范围(0, +∞)，单位为px。当设定的值小于等于0时，按默认值5px处理。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Pointer to the created gesture. |

### createPinchGesture()

```c
ArkUI_GestureRecognizer* (*createPinchGesture)(int32_t fingersNum, double distanceNum)
```

**描述：**

创建捏合手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fingersNum | 触发捏合的最少手指数，最小为2指，最大为5指。超出取值范围时按照默认值2处理。 |
|  double distanceNum | 最小识别距离，取值范围(0, +∞)，单位为px。当设置识别距离的值小于等于0时，会被转化为默认值5px处理。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createRotationGesture()

```c
ArkUI_GestureRecognizer* (*createRotationGesture)(int32_t fingersNum, double angleNum)
```

**描述：**

创建旋转手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fingersNum | 触发旋转的最少手指数，最小为2指，最大为5指。超出取值范围时按照默认值2处理。 |
|  double angleNum | 触发旋转手势的最小改变度数，取值范围(0, 360]，单位为deg。默认值：1deg。当传入的值小于等于0或大于360时，会被转化为默认值1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createSwipeGesture()

```c
ArkUI_GestureRecognizer* (*createSwipeGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double speedNum)
```

**描述：**

创建快滑手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fingersNum | 触发滑动的最少手指数，最小为1指，最大为10指。超出取值范围时，按照默认值1处理。 |
|  ArkUI_GestureDirectionMask directions | 触发快滑手势的滑动方向。可根据需要识别的快滑方向选择：GESTURE_DIRECTION_HORIZONTAL适用于水平快滑场景，GESTURE_DIRECTION_VERTICAL适用于垂直快滑场景，GESTURE_DIRECTION_LEFT/RIGHT/UP/DOWN适用于只识别指定单一方向快滑的场景，GESTURE_DIRECTION_ALL适用于任意方向快滑均可触发的场景，GESTURE_DIRECTION_NONE表示任何方向都不触发手势事件。 |
|  double speedNum | 识别滑动的最小速度，取值范围(0, +∞)，单位px/s。当设置滑动速度的值小于等于0时，会被转化为默认值100px/s。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createGroupGesture()

```c
ArkUI_GestureRecognizer* (*createGroupGesture)(ArkUI_GroupGestureMode gestureMode)
```

**描述：**

创建手势组。创建成功后，可调用addChildGesture()向该手势组添加子手势，再通过addGestureToNode()将手势组绑定到节点；不再使用时可按需调用removeChildGesture()移除子手势，并调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GroupGestureMode](capi-native-gesture-h.md#arkui_groupgesturemode) gestureMode | 手势组模式。SEQUENTIAL_GROUP适用于需要按注册顺序依次识别多个手势的场景；PARALLEL_GROUP适用于多个手势需要同时识别且互不影响的场景；EXCLUSIVE_GROUP适用于多个手势同时竞争、任一手势识别成功后结束其他识别的互斥场景。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture group. |

### dispose()

```c
void (*dispose)(ArkUI_GestureRecognizer* recognizer)
```

**描述：**

销毁通过createTapGesture()、createLongPressGesture()、createPanGesture()、createPinchGesture()、createRotationGesture()、createSwipeGesture()、createGroupGesture()或createTapGestureWithDistanceThreshold()创建的手势，释放资源。若手势已通过addGestureToNode()添加到节点，建议先调用removeGestureFromNode()解除节点绑定后再调用dispose()；调用dispose()后不得继续使用该手势指针。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture to be disposed of. |

### addChildGesture()

```c
int32_t (*addChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)
```

**描述：**

Adds a gesture to a gesture group.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* group | Pointer to the target gesture group. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* child | Pointer to the target gesture. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.          <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs, for example, attempting to          add a gesture to an object that is not a gesture group. |

### removeChildGesture()

```c
int32_t (*removeChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)
```

**描述：**

Removes a gesture from a gesture group.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* group | Pointer to the target gesture group. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* child | Pointer to the target gesture. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.          <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setGestureEventTarget()

```c
int32_t (*setGestureEventTarget)(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventActionTypeMask actionTypeMask, void* extraParams,void (*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams))
```

**描述：**

Registers a callback for gestures.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| recognizer | Pointer to a gesture recognizer. |
| actionTypeMask | Gesture event types. Multiple callbacks can be registered at once, with the callback eventtypes distinguished in the callbacks. Example: actionTypeMask = GESTURE_EVENT_ACTION_ACCEPT \|GESTURE_EVENT_ACTION_UPDATE; |
|  void* extraParams | Context passed in the **targetReceiver** callback. |
| targetReceiver | Callback to register for processing the gesture event types. **event** indicates thegesture callback data. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.          <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### addGestureToNode()

```c
int32_t (*addGestureToNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer, ArkUI_GesturePriority mode,ArkUI_GestureMask mask)
```

**描述：**

Adds a gesture to a UI component.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the ArkUI component node to which you want to add the gesture. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Gesture to be added to the UI component. |
|  [ArkUI_GesturePriority](capi-native-gesture-h.md#arkui_gesturepriority) mode | Mode of the gesture. |
| [ArkUI_GestureMask](capi-native-gesture-h.md#arkui_gesturemask) mask | Gesture masking mode. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.          <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### removeGestureFromNode()

```c
int32_t (*removeGestureFromNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer)
```

**描述：**

Removes a gesture from a node.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the node from which you want to remove the gesture. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Gesture to be removed. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.          <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setGestureInterrupterToNode()

```c
int32_t (*setGestureInterrupterToNode)(ArkUI_NodeHandle node, ArkUI_GestureInterruptResult (*interrupter)(ArkUI_GestureInterruptInfo* info))
```

**描述：**

Sets a gesture interruption callback for a node.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | Pointer to the ArkUI node for which you want to set a gesture interruption callback. |
| interrupter | Indicates the gesture interruption callback to set.<b>info</b> indicates the gesture interruption data. If <b>interrupter</b> returns<b>GESTURE_INTERRUPT_RESULT_CONTINUE</b>, the gesture recognition process continues. If it returns<b>GESTURE_INTERRUPT_RESULT_REJECT</b>, the gesture recognition process is paused. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.          <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### getGestureType()

```c
ArkUI_GestureRecognizerType (*getGestureType)(ArkUI_GestureRecognizer* recognizer)
```

**描述：**

获取手势类别。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | 手势指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizerType](capi-native-gesture-h.md#arkui_gesturerecognizertype) | Returns the gesture type. |

### setInnerGestureParallelTo()

```c
int32_t (*setInnerGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event))
```

**描述：**

Sets the callback function for the parallel internal gesture event.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | Pointer to the ArkUI node for which you want to set the callback of the parallel internal gestureevent. |
| userData | Custom data. |
| parallelInnerGesture | Parallel internal gesture event. **event** returns the data of the parallel internalgesture event. **parallelInnerGesture** returns the pointer to the gesture recognizer that requires parallelrecognition. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.          <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### createTapGestureWithDistanceThreshold()

```c
ArkUI_GestureRecognizer* (*createTapGestureWithDistanceThreshold)(int32_t countNum, int32_t fingersNum, double distanceThreshold)
```

**描述：**

创建带移动范围限制的敲击手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时，调用dispose()释放资源，释放后不得继续使用该手势识别器。如需先解除节点绑定，可在dispose()前调用removeGestureFromNode()。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t countNum | 识别的连续点击次数，取值范围为大于0的整数。当设置的值小于1时，会被转化为默认值1。 |
|  int32_t fingersNum | 触发点击的手指数，最小为1指，最大为10指。当设置小于1的值时，按照最小值1处理；当设置大于10的值时，按照最大值10处理。 |
|  double distanceThreshold | 手指允许的移动距离范围，取值范围(0, +∞)，单位为vp。当设置的值小于等于0时，会被转化为默认值无穷大。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |


