# 绑定手势事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->


ArkUI开发框架在NDK接口主要提供点击手势、滑动手势、快滑手势、长按手势、捏合手势和旋转手势，通过给指定的组件绑定不同的手势并设置相应的回调，实现期望的手势交互能力。


下面通过一个简单的示例来介绍如何实现手势绑定。


1. 创建一个Column节点，用于绑定手势。
    <!-- @[create_column](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
    
    ``` C
    // 创建Column节点
    auto column = nodeAPI->createNode(ARKUI_NODE_COLUMN);
    // 设置背景色
    ArkUI_NumberValue value[] = {{.u32 = 0xff112233}};
    ArkUI_AttributeItem item = {value, 1};
    nodeAPI->setAttribute(column, NODE_BACKGROUND_COLOR, &item);
    // 设置宽度
    ArkUI_NumberValue widthValue[] = {{400}};
    ArkUI_AttributeItem width = {widthValue, 1};
    nodeAPI->setAttribute(column, NODE_WIDTH, &width);
    // 设置高度
    ArkUI_NumberValue heightValue[] = {{400}};
    ArkUI_AttributeItem height = {heightValue, 1};
    nodeAPI->setAttribute(column, NODE_HEIGHT, &height);
    ```


2. 创建一个单指长按1秒并持续响应的长按手势。
    <!-- @[create_long_press_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
    
    ``` C
    // 获取手势Native接口集合
    auto gestureApi = reinterpret_cast<ArkUI_NativeGestureAPI_1 *>(
        OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_GESTURE, "ArkUI_NativeGestureAPI_1"));
    // 创建长按手势
    // DURATION_NUM_1000 = 1000
    auto longPressGesture = gestureApi->createLongPressGesture(1, true, DURATION_NUM_1000);
    ```


3. 将创建的手势和步骤一中创建的Column节点绑定。
    <!-- @[bind_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->


## 单一手势

通过上文的示例已经了解了如何将手势绑定在节点上，接下来将分别介绍不同手势的创建方法。

- 点击手势
  通过给组件绑定点击手势可在组件被点击时触发此回调，可指定触发回调需要的点击次数和手指个数。

    <!-- @[create_tap_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->


- 滑动手势
  通过给组件绑定滑动手势可在用户滑动组件时触发回调，可指定触发回调需要的手指个数、滑动方向、滑动距离。单位为px。
    <!-- @[create_pan_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->


- 长按手势
  通过给组件绑定长按手势可在用户长按组件时触发回调，可指定触发回调需要的手指个数、长按时间（单位毫秒）、是否连续触发。

    <!-- @[create_long_press_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->


- 捏合手势
  通过给组件绑定捏合手势可在用户捏合组件时触发回调，可指定触发回调需要的手指个数（最小为2）、捏合距离（单位px）。

    <!-- @[create_pinch_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->


- 旋转手势
  通过给组件绑定旋转手势可在用户旋转组件时触发回调，可指定触发回调需要的手指个数（最小为2）、旋转角度。

    <!-- @[create_rotation_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->


- 快滑手势
  通过给组件绑定快滑手势可在用户快速滑动组件时触发回调，可指定触发回调需要的手指个数（最小为1）、滑动方向、滑动速度（单位px/s）。

    <!-- @[create_swiper_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->



## 组合手势

可以将多个不同类型的手势组合在一起，形成一个手势组，这个手势组可以作为一个识别整体，达到对用户多个不同类型手势序列的识别目的。

通过设置[ArkUI_GroupGestureMode](../reference/apis-arkui/capi-native-gesture-h.md#arkui_groupgesturemode)来指定这个手势组的识别模式，即组内的手势之间的关系，包含顺序识别SEQUENTIAL_GROUP，并行识别PARALLEL_GROUP，互斥识别EXCLUSIVE_GROUP。


### 顺序识别

顺序识别组合手势对应的ArkUI_GroupGestureMode为SEQUENTIAL_GROUP。顺序识别组合手势将按照手势的注册顺序识别手势，直到所有的手势识别成功。当顺序识别组合手势中有一个手势识别失败时，后续手势识别均失败。顺序识别手势组仅有最后一个手势可以响应[GESTURE_EVENT_ACTION_END](../reference/apis-arkui/capi-native-gesture-h.md#arkui_gestureeventactiontype)。

以顺序识别长按和滑动手势为例：

<!-- @[long_press_and_swipe_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/LongPressAndSwipeGesture.h) -->


**完整示例：**

完整示例请参考[示例工程](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent)。

### 并行识别

并行识别组合手势对应的ArkUI_GroupGestureMode为PARALLEL_GROUP。并行识别组合手势中注册的手势将同时进行识别，直到所有手势识别结束。并行识别手势组合中的手势进行识别时互不影响。

以并行识别长按和快滑手势为例：

<!-- @[long_press_and_flick_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/LongPressAndFlickGesture.h) -->


**完整示例：**

完整示例请参考[示例工程](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent)。

### 互斥识别

互斥识别组合手势对应的ArkUI_GroupGestureMode为EXCLUSIVE_GROUP。互斥识别组合手势中注册的手势将同时进行识别，若有一个手势识别成功，则结束手势识别，其他所有手势识别失败。

以互斥识别滑动手势和捏合手势为例：

<!-- @[swipe_and_pinch_exclusive_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/SwipeAndPinchExclusiveGesture.h) -->


**完整示例：**

完整示例请参考[示例工程](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent)。

### 自定义手势判定

当用户的操作符合某个手势识别器，该识别器即将触发成功时，可通过自定义手势判定能力来动态决策，是否希望该识别器被系统认定为识别成功。通过setGestureInterrupterToNode接口，绑定一个回调在该组件上，但组件上的某个手势即将识别成功时，通过返回CONTINUE或REJECT来决定是否将成功机会让给其它手势识别器。

在上文绑定手势事件的示例中按照如下方式进行调整即可实现自定义手势判定。


1. 创建自定义手势判定回调。
    <!-- @[create_custom_gestures](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->


2. 绑定手势判定和节点。
    <!-- @[bind_gestures](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->



经过上述修改，将原本可以生效的长按手势做了拦截，即，此时再对Column节点长按将不会触发长按的手势回调。

## 获取事件信息

绑定手势事件已详细说明如何将手势绑定到节点上。在回调执行时，ArkUI框架提供了[OH_ArkUI_GestureEvent_GetRawInputEvent()](../reference/apis-arkui/capi-native-gesture-h.md#oh_arkui_gestureevent_getrawinputevent)接口，可从手势事件中获取基础事件对象。之后，可通过调用[OH_ArkUI_PointerEvent_GetDisplayX()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_pointerevent_getdisplayx)、[OH_ArkUI_PointerEvent_GetDisplayXByIndex()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_pointerevent_getdisplayxbyindex)、[OH_ArkUI_UIInputEvent_GetAction()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_uiinputevent_getaction)和[OH_ArkUI_UIInputEvent_GetEventTime()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_uiinputevent_geteventtime)等接口，从基础事件中获取更多信息。应用依据获取的信息，在手势事件执行过程中实现差异化交互逻辑。


  <!-- @[gesture_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkAddInteractionEvent/entry/src/main/cpp/Function.h) -->
