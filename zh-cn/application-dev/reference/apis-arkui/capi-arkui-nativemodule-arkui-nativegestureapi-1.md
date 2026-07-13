# ArkUI_NativeGestureAPI_1
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_NativeGestureAPI_1
```

## 概述

ArkUI_NativeGestureAPI_1提供创建敲击、长按、滑动、捏合、旋转、快滑等手势及手势组的接口，并支持将手势绑定到ArkUI组件、移除手势、设置手势打断回调和并行内部手势回调，用于配置和管理组件的触控交互识别与事件处理。

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
| [ArkUI_GestureRecognizer* (\*createTapGesture)(int32_t countNum, int32_t fingersNum)](#createtapgesture) | 创建敲击手势。1. 支持单击、双击和多次点击事件的识别。<br>        2. 当配置多击时，上一次的最后一根手指抬起和下一次的第一根手指按下的超时时间为300毫秒。<br>        3. 当上次点击的位置与当前点击的位置距离超过60vp等效像素点时，手势识别失败。<br>        4. 当配置多指时，第一根手指按下后300毫秒内未有足够的手指数按下，手势识别失败，<br>           第一根手指抬起后300毫秒内未有足够的手指抬起，手势识别失败。<br>        5. 实际点击手指数超过配置值，手势识别成功。<br> |
| [ArkUI_GestureRecognizer* (\*createLongPressGesture)(int32_t fingersNum, bool repeatResult, int32_t durationNum)](#createlongpressgesture) | 创建长按手势。1. 用于触发长按手势事件，触发长按手势的最少手指数为1，最短长按时间为500毫秒。<br>        2. 当组件默认支持可拖拽时，如Text、TextInput、TextArea、HyperLink、Image和RichEditor等组件。<br>           长按手势与拖拽会出现冲突，事件优先级如下：<br>           长按触发时间 < 500ms，长按事件优先拖拽事件响应。<br>           长按触发时间 >= 500ms，拖拽事件优先长按事件响应。<br>        3. 手指按下后若发生超过15px的移动，则判定当前长按手势识别失败。<br> |
| [ArkUI_GestureRecognizer* (\*createPanGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double distanceNum)](#createpangesture) | 创建滑动手势。1. 当滑动的最小距离超过设定的最小值时触发滑动手势事件。<br>        2. Tabs组件滑动与该滑动手势事件同时存在时，可将distanceNum值设为1，使拖动更灵敏，避免造成事件错乱。<br> |
| [ArkUI_GestureRecognizer* (\*createPinchGesture)(int32_t fingersNum, double distanceNum)](#createpinchgesture) | 创建捏合手势。1. 触发捏合手势的最少手指为2指，最大为5指，最小识别距离为distanceNum 像素点。<br>        2. 触发手势手指可以多于fingersNum数目，但只有先落下的与fingersNum相同数目的手指参与手势计算。<br> |
| [ArkUI_GestureRecognizer* (\*createRotationGesture)(int32_t fingersNum, double angleNum)](#createrotationgesture) | 创建旋转手势。1. 触发旋转手势的最少手指为2指，最大为5指，最小改变度数为1度。<br>        2. 触发手势手指可以多于fingersNum数目，但只有先落下的两指参与手势计算。<br> |
| [ArkUI_GestureRecognizer* (\*createSwipeGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double speedNum)](#createswipegesture) | 创建快滑手势。1. 用于触发快滑事件，滑动速度大于speedNum px/s时可识别成功。<br> |
| [ArkUI_GestureRecognizer* (\*createGroupGesture)(ArkUI_GroupGestureMode gestureMode)](#creategroupgesture) | 创建手势组。 |
| [void (\*dispose)(ArkUI_GestureRecognizer* recognizer)](#dispose) | 销毁手势，释放资源。 |
| [int32_t (\*addChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)](#addchildgesture) | 手势组增加子手势。 |
| [int32_t (\*removeChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)](#removechildgesture) | 删除子手势。 |
| [int32_t (\*setGestureEventTarget)(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventActionTypeMask actionTypeMask, void* extraParams,void (\*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams))](#setgestureeventtarget) | 创建手势关联回调方法。 |
| [int32_t (\*addGestureToNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer, ArkUI_GesturePriority mode, ArkUI_GestureMask mask)](#addgesturetonode) | 将手势添加到UI组件。 |
| [int32_t (\*removeGestureFromNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer)](#removegesturefromnode) | 在节点中移除手势。 |
| [int32_t (\*setGestureInterrupterToNode)(ArkUI_NodeHandle node, ArkUI_GestureInterruptResult (\*interrupter)(ArkUI_GestureInterruptInfo* info))](#setgestureinterruptertonode) | 设置节点手势打断回调。 |
| [ArkUI_GestureRecognizerType (\*getGestureType)(ArkUI_GestureRecognizer* recognizer)](#getgesturetype) | 获取手势类别。 |
| [int32_t (\*setInnerGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (\*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event))](#setinnergestureparallelto) | 设置并行内部手势事件回调。 |
| [ArkUI_GestureRecognizer* (\*createTapGestureWithDistanceThreshold)(int32_t countNum, int32_t fingersNum, double distanceThreshold)](#createtapgesturewithdistancethreshold) | 创建带移动范围限制的敲击手势。1. 支持单击、双击和多次点击事件的识别。<br>        2. 当配置多击时，上一次的最后一根手指抬起和下一次的第一根手指按下的超时时间为300毫秒。<br>        3. 当上次点击的位置与当前点击的位置距离超过60vp等效像素点时，手势识别失败。<br>        4. 当配置多指时，第一根手指按下后300毫秒内未有足够的手指数按下，手势识别失败，<br>           第一根手指抬起后300毫秒内未有足够的手指抬起，手势识别失败。<br>        5. 实际点击手指数超过配置值，手势识别成功。<br>        6. 当手指移动距离超出所设置的距离值时，手势识别失败。<br> |

## 成员函数说明

### createTapGesture()

```c
ArkUI_GestureRecognizer* (*createTapGesture)(int32_t countNum, int32_t fingersNum)
```

**描述：**

创建敲击手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时应先按需通过removeGestureFromNode()从节点移除，再调用dispose()释放资源，释放后不得继续使用该手势识别器。
1. 支持单击、双击和多次点击事件的识别。
2. 当配置多击时，上一次的最后一根手指抬起和下一次的第一根手指按下的超时时间为300毫秒。
3. 当上次点击的位置与当前点击的位置距离超过60vp等效像素点时，手势识别失败。
4. 当配置多指时，第一根手指按下后300毫秒内未有足够的手指数按下，手势识别失败，第一根手指抬起后300毫秒内未有足够的手指抬起，手势识别失败。
5. 实际点击手指数超过配置值，手势识别成功。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t countNum | 识别的连续点击次数。当设置的值小于1或不设置时，会被转化为默认值 1。 |
|  int32_t fingersNum | 触发点击的手指数，最小为1指，最大为10指。当设置小于1的值、不设置或大于10指时，会被转化为默认值1。 |

**返回：**

| 类型                           | 说明 |
|------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | 返回创建的长按手势指针，可用于后续绑定节点、注册回调或管理长按手势识别。 |

### createLongPressGesture()

```c
ArkUI_GestureRecognizer* (*createLongPressGesture)(int32_t fingersNum, bool repeatResult, int32_t durationNum)
```

**描述：**

创建长按手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时应先按需通过removeGestureFromNode()从节点移除，再调用dispose()释放资源，释放后不得继续使用该手势识别器。
1. 用于触发长按手势事件，触发长按手势的最少手指数为1，最短长按时间为500毫秒。
2. 当组件默认支持可拖拽时，如Text、TextInput、TextArea、HyperLink、Image和RichEditor等组件。

   长按手势与拖拽会出现冲突，事件优先级如下：

   长按触发时间 < 500ms，长按事件优先拖拽事件响应。

   长按触发时间 >= 500ms，拖拽事件优先长按事件响应。
3. 手指按下后若发生超过15px的移动，则判定当前长按手势识别失败。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fingersNum | 触发长按的最少手指数，最小为1指，最大取值为10指。超出取值范围时按照默认值1处理。|
|  bool repeatResult | 是否连续触发事件回调。<br>true：连续触发；false：不连续触发。 |
|  int32_t durationNum | 触发长按的最短时间，单位为毫秒（ms）。设置小于等于0时，按照默认值500处理。当组件默认支持可拖拽时，长按触发时间小于500ms时长按事件优先拖拽事件响应；长按触发时间大于等于500ms时，拖拽事件优先长按事件响应。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | 返回创建的长按手势指针。 |

### createPanGesture()

```c
ArkUI_GestureRecognizer* (*createPanGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double distanceNum)
```

**描述：**

创建滑动手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时应先按需通过removeGestureFromNode()从节点移除，再调用dispose()释放资源，释放后不得继续使用该手势识别器。
1. 当滑动的最小距离超过设定的最小值时触发滑动手势事件。
2. Tabs组件滑动与该滑动手势事件同时存在时，可将distanceNum值设为1，使拖动更灵敏，避免Tabs组件滑动事件与该滑动手势事件响应冲突。

**参数：**

| 参数项                                                                  | 描述 |
|----------------------------------------------------------------------| -- |
| int32_t fingersNum                                                   | 用于指定触发滑动的最少手指数，最小为1指，最大取值为10指。当设置的值小于1、不设置或大于10指时，会被转化为默认值1。 |
| [ArkUI_GestureDirectionMask](capi-native-gesture-h.md#变量) directions | 用于指定触发滑动的手势方向，此枚举值支持逻辑与(&)和逻辑或（\|）运算。可根据业务需要选择方向：GESTURE_DIRECTION_HORIZONTAL适用于只识别水平滑动的场景，GESTURE_DIRECTION_VERTICAL适用于只识别垂直滑动的场景，GESTURE_DIRECTION_LEFT/RIGHT/UP/DOWN适用于只识别单一方向滑动的场景，GESTURE_DIRECTION_ALL适用于任意方向均可触发的场景，GESTURE_DIRECTION_NONE表示任何方向都不触发手势事件。 |
| double distanceNum                                                   | 用于指定触发滑动手势事件的最小拖动距离，单位为px。当设定的值小于等于0时，按默认值5px处理。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | 返回创建的滑动手势指针，可用于后续绑定节点、注册回调或管理滑动手势识别。 |

### createPinchGesture()

```c
ArkUI_GestureRecognizer* (*createPinchGesture)(int32_t fingersNum, double distanceNum)
```

**描述：**

创建捏合手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时应先按需通过removeGestureFromNode()从节点移除，再调用dispose()释放资源，释放后不得继续使用该手势识别器。
1. 触发捏合手势的最少手指为2指，最大为5指，最小识别距离为distanceNum 像素点。
2. 触发手势手指可以多于fingersNum数目，但只有先落下的与fingersNum相同数目的手指参与手势计算。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fingersNum | 触发捏合的最少手指数，最小为2指，最大为5指。超出取值范围时按照默认值2处理。 |
|  double distanceNum | 最小识别距离，单位为px。当设置识别距离的值小于等于0时，会被转化为默认值5px处理。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | 返回创建的捏合手势指针，可用于后续绑定节点、注册回调或管理捏合手势识别。 |

### createRotationGesture()

```c
ArkUI_GestureRecognizer* (*createRotationGesture)(int32_t fingersNum, double angleNum)
```

**描述：**

创建旋转手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时应先按需通过removeGestureFromNode()从节点移除，再调用dispose()释放资源，释放后不得继续使用该手势识别器。
1. 触发旋转手势的最少手指为2指，最大为5指，触发旋转手势的最小改变度数由angleNum指定。
2. 触发手势手指可以多于fingersNum数目，但只有先落下的两指参与手势计算。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fingersNum | 触发旋转的最少手指数，最小为2指，最大为5指。超出取值范围时按照默认值2处理。 |
|  double angleNum | 触发旋转手势的最小改变度数，单位为deg。默认值：1。当改变度数的值小于等于0或大于360时，会被转化为默认值 1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | 返回创建的旋转手势指针，可用于后续绑定节点、注册回调或管理旋转手势识别。 |

### createSwipeGesture()

```c
ArkUI_GestureRecognizer* (*createSwipeGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double speedNum)
```

**描述：**

创建快滑手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时应先按需通过removeGestureFromNode()从节点移除，再调用dispose()释放资源，释放后不得继续使用该手势识别器。
1. 用于触发快滑事件，滑动速度大于speedNum px/s时可识别成功。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t fingersNum | 触发滑动的最少手指数，默认为1，最小为1指，最大为10指。超出取值范围或不设置时，按照默认值1处理。 |
|  [ArkUI_GestureDirectionMask](capi-native-gesture-h.md#变量) directions | 触发快滑手势的滑动方向。可根据需要识别的快滑方向选择：GESTURE_DIRECTION_HORIZONTAL适用于水平快滑场景，GESTURE_DIRECTION_VERTICAL适用于垂直快滑场景，GESTURE_DIRECTION_LEFT/RIGHT/UP/DOWN适用于只识别指定单一方向快滑的场景，GESTURE_DIRECTION_ALL适用于任意方向快滑均可触发的场景，GESTURE_DIRECTION_NONE表示任何方向都不触发手势事件。 |
|  double speedNum | 识别滑动的最小速度，单位 px/s。当设置滑动速度的值小于等于0时，会被转化为默认值100px/s。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | 返回创建的快滑手势指针，可用于后续绑定节点、注册回调或管理快滑手势识别。 |

### createGroupGesture()

```cc
ArkUI_GestureRecognizer* (*createGroupGesture)(ArkUI_GroupGestureMode gestureMode)
```

**描述：**


创建手势组。创建成功后，可调用addChildGesture()向该手势组添加子手势，再通过addGestureToNode()将手势组绑定到节点；不再使用时可按需调用removeChildGesture()移除子手势，并通过dispose()释放手势组资源。

**参数：**

| 参数项                                                                                   | 描述 |
|---------------------------------------------------------------------------------------| -- |
| [ArkUI_GroupGestureMode](capi-native-gesture-h.md#arkui_groupgesturemode) gestureMode | 手势组模式。SEQUENTIAL_GROUP适用于需要按注册顺序依次识别多个手势的场景；PARALLEL_GROUP适用于多个手势需要同时识别且互不影响的场景；EXCLUSIVE_GROUP适用于多个手势同时竞争、任一手势识别成功后结束其他识别的互斥场景。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | 返回创建的手势组指针，可用于后续添加、移除或组合管理子手势。 |

### dispose()

```c
void (*dispose)(ArkUI_GestureRecognizer* recognizer)
```

**描述：**


销毁通过createTapGesture()、createLongPressGesture()、createPanGesture()、createPinchGesture()、createRotationGesture()、createSwipeGesture()、createGroupGesture() 或 createTapGestureWithDistanceThreshold()创建的手势，释放资源。若手势已通过addGestureToNode()添加到节点，建议先调用removeGestureFromNode()解除节点绑定后再调用dispose()；调用dispose()后不得继续使用该手势指针。

**参数：**

| 参数项                                                                                   | 描述 |
|---------------------------------------------------------------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer| 需要销毁的手势的指针。 |

### addChildGesture()

```c
int32_t (*addChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)
```

**描述：**


向通过createGroupGesture()创建的手势组中增加子手势。需要先创建手势组和子手势，再调用addChildGesture()建立关联；添加后，子手势将参与该手势组的识别流程。不再需要该子手势参与手势组识别时，可调用removeChildGesture()解除关联。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* group | 需要被关联子手势的手势组。 |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* child | 需要添加到手势组中的子手势识别器指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 参数错误。比如添加手势到非手势组对象内。 |

### removeChildGesture()

```c
int32_t (*removeChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)
```

**描述：**


从手势组中删除已通过addChildGesture()添加的子手势。调用后，该子手势不再作为该手势组的子手势参与手势组识别。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* group | 需要被删除子手势的手势组。 |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* child | 需要从手势组中删除的子手势识别器指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 参数错误。 |

### setGestureEventTarget()

```c
int32_t (*setGestureEventTarget)(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventActionTypeMask actionTypeMask, void* extraParams,void (*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams))
```

**描述：**


创建手势关联回调方法，用于需要监听手势触发、更新或结束等事件并执行业务处理的场景。

**参数：**

| 参数项                                                                                       | 描述 |
|-------------------------------------------------------------------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | 需要被绑定回调事件的各类手势指针。 |
| [ArkUI_GestureEventActionTypeMask](capi-native-gesture-h.md#变量) actionTypeMask            | 需要响应的手势事件类型集合，一次性可以注册多个事件类型，在回调中区分回调事件类型。例：actionTypeMask = GESTURE_EVENT_ACTION_ACCEPT \| GESTURE_EVENT_ACTION_UPDATE; |
| void* extraParams                                                                         | targetReceiver 回调时传入的上下文数据。 |
| targetReceiver                                                                            | 手势事件回调函数，签名为void (\*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams)，用于处理已注册手势类型的事件。其中event为手势回调数据，extraParams为注册时传入的上下文数据，无返回值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 参数错误。 |

### addGestureToNode()

```c
int32_t (*addGestureToNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer, ArkUI_GesturePriority mode, ArkUI_GestureMask mask)
```

**描述：**


将通过createTapGesture()、createLongPressGesture()等接口创建的手势添加到UI组件。应先创建手势识别器，再调用addGestureToNode()绑定到节点；不再需要节点响应该手势时，调用removeGestureFromNode()解除绑定，释放资源时再调用dispose()。

**参数：**

| 参数项                                                                                       | 描述 |
|-------------------------------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node                          | 需要被绑定手势的ArkUI组件节点指针。 |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | 绑定此节点的手势。 |
| [ArkUI_GesturePriority](capi-native-gesture-h.md#arkui_gesturepriority) mode              | 手势优先级模式，用于设置该手势添加到节点后的响应优先级和与其他手势的竞争关系，取值为ArkUI_GesturePriority枚举值。 |
| [ArkUI_GestureMask](capi-native-gesture-h.md#arkui_gesturemask) mask                      | 手势屏蔽模式，用于控制该手势添加到节点后与其他手势之间的屏蔽或透传关系，取值为ArkUI_GestureMask枚举值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 参数错误。 |

### removeGestureFromNode()

```c
int32_t (*removeGestureFromNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer)
```

**描述：**


从节点中移除已通过addGestureToNode()添加的手势。调用后，该节点不再响应该手势；如需释放该手势资源，建议先调用removeGestureFromNode()解除节点绑定，再调用dispose()。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要被移除手势的节点指针。 |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | 需要被移除的手势。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 参数错误。 |

### setGestureInterrupterToNode()

```c
int32_t (*setGestureInterrupterToNode)(ArkUI_NodeHandle node, ArkUI_GestureInterruptResult (*interrupter)(ArkUI_GestureInterruptInfo* info))
```

**描述：**


设置节点手势打断回调，用于需要根据业务条件决定手势是否继续识别的场景，例如处理父子节点手势冲突或动态控制手势响应时使用。

**参数：**

| 参数项                                                              | 描述 |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要被设置手势打断回调的ArkUI节点指针。 |
| [ArkUI_GestureInterruptResult](./capi-native-gesture-h.md#arkui_gestureinterruptresult) (\*interrupter)([ArkUI_GestureInterruptInfo](./capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* info)     | 打断回调，info返回手势打断数据。interrupter返回GESTURE_INTERRUPT_RESULT_CONTINUE，手势正常进行；返回GESTURE_INTERRUPT_RESULT_REJECT，手势打断。设置此参数为nullptr时将取消注册回调函数。<br>**说明：** 该事件中断回调注册后，后续在单次手势处理流程中都会存在。即使在单次事件处理流程中使用setGestureInterrupterToNode接口将手势打断回调重置为nullptr，或者使用[dispose](#dispose)接口使即将被触发的手势销毁，该回调在满足触发条件后仍会响应。如果在该回调中使用到的对象，在回调触发前已被释放，需要对该对象进行保护。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 参数错误。 |

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

| 类型                                                                                  | 说明 |
|-------------------------------------------------------------------------------------| -- |
| [ArkUI_GestureRecognizerType](capi-native-gesture-h.md#arkui_gesturerecognizertype) | 手势类型。 |

### setInnerGestureParallelTo()

```c
int32_t (*setInnerGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event))
```

**描述：**


设置并行内部手势事件回调，用于需要让组件内部手势与外部自定义手势并行识别的场景。

**参数：**

| 参数项                                                              | 描述 |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要被设置并行内部手势事件回调的ArkUI节点指针。 |
| void* userData                                                         | 用户自定义数据，设置后会作为并行内部手势事件回调的上下文数据透传，供开发者在处理回调时使用。 |
| parallelInnerGesture                                             | 并行内部手势事件回调函数，签名为ArkUI_GestureRecognizer* (\*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event)，用于根据并行内部手势事件数据返回需要与内部手势并行识别的手势识别器指针。其中event为并行内部手势事件数据，返回值为需要并行的手势识别器指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) - 成功。<br>            [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) - 参数错误。 |

### createTapGestureWithDistanceThreshold()

```c
ArkUI_GestureRecognizer* (*createTapGestureWithDistanceThreshold)(int32_t countNum, int32_t fingersNum, double distanceThreshold)
```

**描述：**

创建带移动范围限制的敲击手势。创建成功后返回的手势识别器可通过addGestureToNode()添加到节点；不再使用时应先按需通过removeGestureFromNode()从节点移除，再调用dispose()释放资源，释放后不得继续使用该手势识别器。
1. 支持单击、双击和多次点击事件的识别。
2. 当配置多击时，上一次的最后一根手指抬起和下一次的第一根手指按下的超时时间为300毫秒。
3. 当上次点击的位置与当前点击的位置距离超过60vp等效像素点时，手势识别失败。
4. 当配置多指时，第一根手指按下后300毫秒内未有足够的手指数按下，手势识别失败，第一根手指抬起后300毫秒内未有足够的手指抬起，手势识别失败。
5. 实际点击手指数超过配置值，手势识别成功。
6. 当手指移动距离超出所设置的距离值时，手势识别失败。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t countNum | 识别的连续点击次数。当设置的值小于1或不设置时，会被转化为默认值1。 |
|  int32_t fingersNum | 触发点击的手指数，最小为1指，最大为10指。当设置小于1的值、不设置或大于10指时，会被转化为默认值1。 |
|  double distanceThreshold | 手指允许的移动距离范围，单位为vp。当设置的值小于0或者不设置时，会被转化为默认值无穷大。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | 返回创建的带移动范围限制的敲击手势指针，可用于后续绑定节点、注册回调或管理敲击手势识别。 |


