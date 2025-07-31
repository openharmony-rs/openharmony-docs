# ArkUI_NativeModule


## 概述

提供ArkUI在Native侧的通用拖拽及主动发起拖拽能力。更多详细介绍请参考[拖拽事件](../../ui/ndk-drag-event.md)。

提供ArkUI在Native侧的通用按键事件能力。

提供ArkUI在Native侧的注册手势回调的能力。更多详细介绍请参考[绑定手势事件](../../ui/ndk-bind-gesture-events.md)。

提供ArkUI在Native侧动画回调的能力。更多详细介绍请参考[使用动画](../../ui/ndk-use-animation.md)。

提供ArkUI在Native侧的UI能力，如UI组件创建销毁、树节点操作，属性设置，事件监听等。更多详细介绍请参考[接入ArkTS页面](../../ui/ndk-access-the-arkts-page.md)。

**起始版本：** 12


## 汇总


### 文件

| 名称 | 描述 |
| -------- | -------- |
| [drag_and_drop.h](drag__and__drop_8h.md) | 提供NativeDrag相关接口定义。  |
| [drawable_descriptor.h](drawable__descriptor_8h.md) | 提供NativeDrawableDescriptor接口的类型定义。  |
| [native_animate.h](native__animate_8h.md) | 提供ArkUI在Native侧的动画接口定义集合。  |
| [native_dialog.h](native__dialog_8h.md) | 提供ArkUI在Native侧的自定义弹窗接口定义集合。  |
| [native_gesture.h](native__gesture_8h.md) | 提供NativeGesture接口的类型定义。  |
| [native_interface.h](native__interface_8h.md) | 提供NativeModule接口的统一入口函数。  |
| [native_interface_focus.h](native__interface__focus_8h.md) | 提供NativeFocus相关接口定义。 |
| [native_key_event.h](native__key_event_8h.md) | 提供NativeKeyEvent相关接口定义。  |
| [native_node.h](native__node_8h.md) | 提供NativeNode接口的类型定义。  |
| [native_node_napi.h](native__node__napi_8h.md) | 提供ArkTS侧的FrameNode转换NodeHandle的方式。  |
| [native_type.h](native__type_8h.md) | 提供NativeModule公共的类型定义。  |
| [styled_string.h](styled__string_8h.md) | 提供ArkUI在Native侧的属性字符串能力。  |


### 结构体

| 名称 | 描述 |
| -------- | -------- |
| struct&nbsp;&nbsp;[ArkUI_Node](_ark_u_i___margin.md) | 提供ArkUI native组件实例对象定义。|
| struct&nbsp;&nbsp;[ArkUI_NativeDialog](_ark_ui__native_dialog.md)| 提供ArkUI在Native侧的自定义弹窗控制器对象定义。|
| struct&nbsp;&nbsp;[ArkUI_Context](_ark_ui__context.md)| 提供ArkUI native UI的上下文实例对象定义。|
| struct&nbsp;&nbsp;[ArkUI_ExpectedFrameRateRange](_ark_u_i___expected_frame_rate_range.md) | 设置动画的期望帧率。  |
| struct&nbsp;&nbsp;[ArkUI_AnimateCompleteCallback](_ark_u_i___animate_complete_callback.md) | 动画播放完成回调类型。  |
| struct&nbsp;&nbsp;[ArkUI_NativeAnimateAPI_1](_ark_u_i___native_animate_a_p_i__1.md) | ArkUI提供的Native侧动画接口集合。  |
| struct&nbsp;&nbsp;[ArkUI_NativeDialogAPI_1](_ark_u_i___native_dialog_a_p_i__1.md) | ArkUI提供的Native侧自定义弹窗接口集合。  |
| struct&nbsp;&nbsp;[ArkUI_NativeGestureAPI_1](_ark_u_i___native_gesture_a_p_i__1.md) | 手势模块接口集合。  |
| struct&nbsp;&nbsp;[ArkUI_NativeGestureAPI_2](_ark_u_i___native_gesture_a_p_i__2.md) | 新增手势模块接口集合，支持设置手势中断事件的回调函数。 |
| struct&nbsp;&nbsp;[ArkUI_AttributeItem](_ark_u_i___attribute_item.md) | 定义**setAttribute**函数通用入参结构。  |
| struct&nbsp;&nbsp;[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md) | 定义组件回调事件的参数类型。  |
| struct&nbsp;&nbsp;[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md) | 定义组件回调事件使用字符串参数的类型。  |
| struct&nbsp;&nbsp;[ArkUI_NativeNodeAPI_1](_ark_u_i___native_node_a_p_i__1.md) | ArkUI提供的Native侧Node类型接口集合。  |
| struct&nbsp;&nbsp;[ArkUI_ContextCallback](_ark_u_i___context_callback.md) | 事件回调类型。  |
| union&nbsp;&nbsp;[ArkUI_NumberValue](union_ark_u_i___number_value.md) | ArkUI在Native侧的数字类型定义。  |
| struct&nbsp;&nbsp;[ARKUI_TextPickerRangeContent](_a_r_k_u_i___text_picker_range_content.md) | 定义单列滑动数据选择器支持图片资源的输入结构体。  |
| struct&nbsp;&nbsp;[ARKUI_TextPickerCascadeRangeContent](_a_r_k_u_i___text_picker_cascade_range_content.md) | 定义多列带联动能力的滑动数据选择器的输入结构体。  |
| struct&nbsp;&nbsp;[ArkUI_ColorStop](_ark_u_i___color_stop.md) | 定义渐变色结构。  |
| struct&nbsp;&nbsp;[ArkUI_Rect](_ark_u_i___rect.md) | 定义遮罩屏蔽区域的范围结构体。  |
| struct&nbsp;&nbsp;[ArkUI_IntSize](_ark_u_i___int_size.md) | 尺寸类型，用于描述组件的宽高。  |
| struct&nbsp;&nbsp;[ArkUI_IntOffset](_ark_u_i___int_offset.md) | 位置，用于描述组件的位置。  |
| struct&nbsp;&nbsp;[ArkUI_Margin](_ark_u_i___margin.md) | 外边距属性，用于描述组件的外边距属性。  |
| struct&nbsp;&nbsp;[ArkUI_TranslationOptions](_ark_u_i___translation_options.md) | 定义组件转场时的平移效果对象。  |
| struct&nbsp;&nbsp;[ArkUI_ScaleOptions](_ark_u_i___scale_options.md) | 定义组件转场时的缩放效果对象。  |
| struct&nbsp;&nbsp;[ArkUI_RotationOptions](_ark_u_i___rotation_options.md) | 定义组件转场时的旋转效果对象。  |
| struct&nbsp;&nbsp;[ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md) | 定义输入框内容改变（包含预上屏内容）回调事件的返回值类型。  |


### 宏定义

| 名称 | 描述 |
| -------- | -------- |
| [OH_ArkUI_GetModuleInterface](#oh_arkui_getmoduleinterface)(nativeAPIVariantKind, structType, structPtr) | 基于结构体类型获取对应结构体指针的宏函数。  |
| **MAX_NODE_SCOPE_NUM** | 1000 |
| **MAX_COMPONENT_EVENT_ARG_NUM** | 12 |
| **UDMF_KEY_BUFFER_LEN** | 512 |


### 类型定义

| 名称 | 描述 |
| -------- | -------- |
| typedef struct [ArkUI_NodeEvent](#arkui_nodeevent-12) [ArkUI_NodeEvent](#arkui_nodeevent-12) | 组件事件的通用结构类型。  |
| typedef struct [ArkUI_Context](#arkui_context) [ArkUI_Context](#arkui_context) | native UI的上下文实例对象。  |
| typedef struct [ArkUI_Context](#arkui_context) \* [ArkUI_ContextHandle](#arkui_contexthandle-12) | native UI的上下文实例对象指针定义。  |
| typedef struct [ArkUI_DragEvent](#arkui_dragevent) [ArkUI_DragEvent](#arkui_dragevent) | 拖拽事件。  |
| typedef struct [ArkUI_DragPreviewOption](#arkui_dragpreviewoption) [ArkUI_DragPreviewOption](#arkui_dragpreviewoption) | 设置拖拽跟手图的相关自定义参数。  |
| typedef struct [ArkUI_DragAction](#arkui_dragaction) [ArkUI_DragAction](#arkui_dragaction) | 拖拽行为，用于主动发起拖拽。  |
| typedef struct [ArkUI_DragAndDropInfo](#arkui_draganddropinfo) [ArkUI_DragAndDropInfo](#arkui_draganddropinfo) | 主动发起拖拽后，通过拖拽状态监听返回的系统拖拽相关数据。  |
| typedef struct [OH_UdmfData](#oh_udmfdata) [OH_UdmfData](#oh_udmfdata) | UDMF 统一数据定义。  |
| typedef struct [OH_PixelmapNative](#oh_pixelmapnative) [OH_PixelmapNative](#oh_pixelmapnative) | Pixelmap结构体类型，用于执行Pixelmap相关操作。  |
| typedef struct [ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) [ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) | 定义 DrawableDescriptor 对象。  |
| typedef struct [OH_PixelmapNative](#oh_pixelmapnative) \* [OH_PixelmapNativeHandle](#oh_pixelmapnativehandle) | 定义OH_PixelmapNative对象指针类型。  |
| typedef struct [ArkUI_AnimateOption](#arkui_animateoption) [ArkUI_AnimateOption](#arkui_animateoption) | 设置动画效果相关参数。  |
| typedef struct [ArkUI_Curve](#arkui_curve) [ArkUI_Curve](#arkui_curve) | 提供曲线的插值对象定义。  |
| typedef struct ArkUI_Curve \* [ArkUI_CurveHandle](#arkui_curvehandle) | 定义曲线的插值对象指针定义。  |
| typedef struct [ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) [ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) | 定义关键帧动画参数对象。  |
| typedef struct [ArkUI_AnimatorOption](#arkui_animatoroption) [ArkUI_AnimatorOption](#arkui_animatoroption) | 定义animator动画参数对象。  |
| typedef struct ArkUI_Animator \* [ArkUI_AnimatorHandle](#arkui_animatorhandle) | 定义animator动画对象指针。  |
| typedef struct [ArkUI_AnimatorEvent](#arkui_animatorevent) [ArkUI_AnimatorEvent](#arkui_animatorevent) | 定义animator回调事件对象。  |
| typedef struct [ArkUI_AnimatorOnFrameEvent](#arkui_animatoronframeevent) [ArkUI_AnimatorOnFrameEvent](#arkui_animatoronframeevent) | 定义animator接收到帧时回调对象。  |
| typedef struct [ArkUI_TransitionEffect](#arkui_transitioneffect) [ArkUI_TransitionEffect](#arkui_transitioneffect) | 定义transition属性配置转场参数对象。  |
| typedef bool(\* [ArkUI_OnWillDismissEvent](#arkui_onwilldismissevent)) (int32_t reason) | 弹窗关闭的回调函数。  |
| typedef struct [ArkUI_DialogDismissEvent](#arkui_dialogdismissevent) [ArkUI_DialogDismissEvent](#arkui_dialogdismissevent) | 定义弹窗关闭事件对象。  |
| typedef struct [ArkUI_CustomDialogOptions ](#arkui_customdialogoptions) [ArkUI_CustomDialogOptions ](#arkui_customdialogoptions) | 定义自定义弹窗的内容对象。  |
| typedef uint32_t [ArkUI_GestureEventActionTypeMask](#arkui_gestureeventactiontypemask) | 定义手势事件类型集合。  |
| typedef uint32_t [ArkUI_GestureDirectionMask](#arkui_gesturedirectionmask) | 定义滑动手势方向集合。  |
| typedef ArkUI_GestureRecognizer \* [ArkUI_GestureRecognizerHandle](#arkui_gesturerecognizerhandle) | 提供手势识别器句柄类型对象定义。  |
| typedef [ArkUI_GestureRecognizerHandle](#arkui_gesturerecognizerhandle) \* [ArkUI_GestureRecognizerHandleArray](#arkui_gesturerecognizerhandlearray) | 提供手势识别器句柄类型数组对象定义。  |
| typedef ArkUI_TouchRecognizer  \* [ArkUI_TouchRecognizerHandle](#arkui_touchrecognizerhandle) | 提供触摸识别器句柄类型对象定义。  |
| typedef [ArkUI_TouchRecognizerHandle](#arkui_touchrecognizerhandle) \* [ArkUI_TouchRecognizerHandleArray](#arkui_touchrecognizerhandlearray) | 提供触摸识别器句柄类型数组对象定义。  |
| typedef struct [ArkUI_GestureEventTargetInfo](#arkui_gestureeventtargetinfo) [ArkUI_GestureEventTargetInfo](#arkui_gestureeventtargetinfo) | 提供手势事件目标信息类型对象定义。  |
| typedef struct [ArkUI_ParallelInnerGestureEvent](#arkui_parallelinnergestureevent) [ArkUI_ParallelInnerGestureEvent](#arkui_parallelinnergestureevent) | 提供并行内部手势事件类型对象定义。  |
| typedef void(\* [ArkUI_GestureRecognizerDisposeNotifyCallback](#arkui_gesturerecognizerdisposenotifycallback)) (ArkUI_GestureRecognizer \*recognizer, void \*userData) | 定义手势识别器析构通知事件的回调函数类型。  |
| typedef struct [ArkUI_NodeEvent](#arkui_nodeevent-12) [ArkUI_NodeEvent](#arkui_nodeevent-12) | 定义组件事件的通用结构类型。  |
| typedef struct [ArkUI_NodeCustomEvent](#arkui_nodecustomevent) [ArkUI_NodeCustomEvent](#arkui_nodecustomevent) | 定义自定义组件事件的通用结构类型。  |
| typedef struct ArkUI_NodeAdapter \* [ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) | 定义组件适配器对象，用于滚动类组件的元素懒加载。  |
| typedef struct [ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) [ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) | 定义适配器事件对象。  |
| typedef struct [ArkUI_NodeContentEvent](#arkui_nodecontentevent) [ArkUI_NodeContentEvent](#arkui_nodecontentevent) | 定义NodeContent事件的通用结构类型。  |
| typedef void(\* [ArkUI_NodeContentCallback](#arkui_nodecontentcallback)) ([ArkUI_NodeContentEvent](#arkui_nodecontentevent) \*event) | 定义NodeContent事件的回调函数类型。  |
| typedef struct [ArkUI_LayoutConstraint](#arkui_layoutconstraint) [ArkUI_LayoutConstraint](#arkui_layoutconstraint) | 约束尺寸，组件布局时，进行尺寸范围限制。  |
| typedef struct [ArkUI_DrawContext](#arkui_drawcontext) [ArkUI_DrawContext](#arkui_drawcontext) | 定义组件绘制上下文类型结构。  |
| typedef struct ArkUI_Node \* [ArkUI_NodeHandle](#arkui_nodehandle) | 定义ArkUI native组件实例对象指针定义。  |
| typedef struct ArkUI_NativeDialog \* [ArkUI_NativeDialogHandle](#arkui_nativedialoghandle) | 定义ArkUI在Native侧的自定义弹窗控制器对象指针。  |
| typedef struct [ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) [ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) | 定义FlowItem分组配置信息。  |
| typedef struct [ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) [ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) | 定义ListItemSwipeActionOption方法内Item的配置信息。  |
| typedef struct [ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) [ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) | 定义ListItemSwipeActionOption方法的配置信息。  |
| typedef struct [ArkUI_Context](#arkui_context) \* [ArkUI_ContextHandle](#arkui_contexthandle-12) | 定义ArkUI native UI的上下文实例对象指针定义。  |
| typedef struct ArkUI_NodeContent \* [ArkUI_NodeContentHandle](#arkui_nodecontenthandle) | 定义ArkUI NodeContent实例在Native侧的实例对象指针定义。  |
| typedef struct [ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) [ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) | 指定设置在相对容器中子组件的对齐规则。  |
| typedef struct [ArkUI_GuidelineOption](#arkui_guidelineoption) [ArkUI_GuidelineOption](#arkui_guidelineoption) | guideLine参数，用于定义guideline的id、方向和位置。  |
| typedef struct [ArkUI_BarrierOption](#arkui_barrieroption) [ArkUI_BarrierOption](#arkui_barrieroption) | barrier参数，用于定义barrier的id、方向和生成时所依赖的组件。  |
| typedef struct [ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) [ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) | 定义图片帧信息。  |
| typedef struct [ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) [ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) | 定义List的ChildrenMainSize类信息。  |
| typedef struct [ArkUI_AccessibilityState](#arkui_accessibilitystate) [ArkUI_AccessibilityState](#arkui_accessibilitystate) | 定义组件无障碍状态。  |
| typedef struct [ArkUI_AccessibilityValue](#arkui_accessibilityvalue) [ArkUI_AccessibilityValue](#arkui_accessibilityvalue) | 定义组件无障碍信息值。  |
| typedef struct [ArkUI_SystemFontStyleEvent](#arkui_systemfontstyleevent) [ArkUI_SystemFontStyleEvent](#arkui_systemfontstyleevent) | 系统字体变更事件定义。  |
| typedef struct [ArkUI_CustomSpanMeasureInfo](#arkui_customspanmeasureinfo) [ArkUI_CustomSpanMeasureInfo](#arkui_customspanmeasureinfo) | 自定义段落组件的测量信息。  |
| typedef struct [ArkUI_CustomSpanMetrics](#arkui_customspanmetrics) [ArkUI_CustomSpanMetrics](#arkui_customspanmetrics) | 自定义段落组件的度量指标。  |
| typedef struct [ArkUI_CustomSpanDrawInfo](#arkui_customspandrawinfo) [ArkUI_CustomSpanDrawInfo](#arkui_customspandrawinfo) | 自定义段落组件的绘制信息。  |
| typedef struct [ArkUI_SwiperIndicator](#arkui_swiperindicator) [ArkUI_SwiperIndicator](#arkui_swiperindicator) | 定义 Swiper 组件的导航指示器风格。  |
| typedef struct [ArkUI_StyledString_Descriptor](#arkui_styledstring_descriptor) [ArkUI_StyledString_Descriptor](#arkui_styledstring_descriptor) | 定义文本组件支持的属性字符串的数据对象。  |
| typedef struct [ArkUI_SnapshotOptions](#arkui_snapshotoptions) [ArkUI_SnapshotOptions](#arkui_snapshotoptions) | 组件截图参数。  | 
| typedef struct [ArkUI_StyledString](#arkui_styledstring) [ArkUI_StyledString](#arkui_styledstring) | 定义文本组件支持的格式化字符串数据对象。  |
| typedef struct [OH_UdmfGetDataParams](#oh_udmfgetdataparams) [OH_UdmfGetDataParams](#oh_udmfgetdataparams) | 从UDMF获取数据时的参数。  |
| typedef struct [ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption) [ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption) | 定义进度条线性进度条样式对象。 |
| typedef struct [ArkUI_VisibleAreaEventOptions](#arkui_visibleareaeventoptions) [ArkUI_VisibleAreaEventOptions](#arkui_visibleareaeventoptions) | 可见区域变化监听的参数。  |
| typedef struct [ArkUI_CustomProperty](#arkui_customproperty) [ArkUI_CustomProperty](#arkui_customproperty) | 定义自定义属性的CustomProperty类信息。  |
| typedef struct [ArkUI_HostWindowInfo](#arkui_hostwindowinfo) [ArkUI_HostWindowInfo](#arkui_hostwindowinfo) | 定义窗口属性的HostWindowInfo类信息。  |
| typedef struct [ArkUI_ActiveChildrenInfo](#arkui_activechildreninfo) [ArkUI_ActiveChildrenInfo](#arkui_activechildreninfo) | 定义ActiveChildrenInfo类信息。  |
| typedef struct [AbilityBase_Want](#abilitybase_want) [AbilityBase_Want](#abilitybase_want) | 声明want。 | 

### 枚举

| 名称 | 描述 |
| -------- | -------- |
| [ArkUI_DragResult](#arkui_dragresult) { ARKUI_DRAG_RESULT_SUCCESSFUL = 0, ARKUI_DRAG_RESULT_FAILED, ARKUI_DRAG_RESULT_CANCELED } | 拖拽结果定义，由数据接收方设置，并由系统传递给数据拖出方，拖出方可感知接收方对数据的处理结果。  |
| [ArkUI_DropOperation](#arkui_dropoperation) { ARKUI_DROP_OPERATION_COPY = 0, ARKUI_DROP_OPERATION_MOVE } | 定义拖拽释放时的数据处理方式，可影响角标的显示。  |
| [ArkUI_PreDragStatus](#arkui_predragstatus) {<br/>ARKUI_PRE_DRAG_STATUS_UNKNOWN = -1, ARKUI_PRE_DRAG_STATUS_ACTION_DETECTING, ARKUI_PRE_DRAG_STATUS_READY_TO_TRIGGER_DRAG, ARKUI_PRE_DRAG_STATUS_PREVIEW_LIFT_STARTED,<br/>ARKUI_PRE_DRAG_STATUS_PREVIEW_LIFT_FINISHED, ARKUI_PRE_DRAG_STATUS_PREVIEW_LANDING_STARTED, ARKUI_PRE_DRAG_STATUS_PREVIEW_LANDING_FINISHED, ARKUI_PRE_DRAG_STATUS_CANCELED_BEFORE_DRAG<br/>} | 定义拖拽发起前的长按交互阶段的变化状态。  |
| [ArkUI_DragPreviewScaleMode](#arkui_dragpreviewscalemode) { ARKUI_DRAG_PREVIEW_SCALE_AUTO = 0, ARKUI_DRAG_PREVIEW_SCALE_DISABLED } | 拖拽预览缩放模式。  |
| [ArkUI_DragStatus](#arkui_dragstatus) { ARKUI_DRAG_STATUS_UNKNOWN = -1, ARKUI_DRAG_STATUS_STARTED, ARKUI_DRAG_STATUS_ENDED } | 拖拽状态。  |
| [ArkUI_DismissReason](#arkui_dismissreason) { DIALOG_DISMISS_BACK_PRESS = 0, DIALOG_DISMISS_TOUCH_OUTSIDE, DIALOG_DISMISS_CLOSE_BUTTON, DIALOG_DISMISS_SLIDE_DOWN } | 弹窗关闭的触发方式。  |
| [ArkUI_LevelMode](#arkui_levelmode) { ARKUI_LEVEL_MODE_OVERLAY = 0, ARKUI_LEVEL_MODE_EMBEDDED } | 设置弹窗显示层级。  |
| [ArkUI_ImmersiveMode](#arkui_immersivemode) { ARKUI_IMMERSIVE_MODE_DEFAULT = 0, ARKUI_IMMERSIVE_MODE_EXTEND } | 指定嵌入式弹窗的蒙层覆盖区域。  |
| [ArkUI_GestureEventActionType](#arkui_gestureeventactiontype) { GESTURE_EVENT_ACTION_ACCEPT = 0x01, GESTURE_EVENT_ACTION_UPDATE = 0x02, GESTURE_EVENT_ACTION_END = 0x04, GESTURE_EVENT_ACTION_CANCEL = 0x08 } | 定义手势事件类型。  | 
| [ArkUI_GesturePriority](#arkui_gesturepriority) { NORMAL = 0, PRIORITY = 1, PARALLEL = 2 } | 定义手势事件模式。  | 
| [ArkUI_GroupGestureMode](#arkui_groupgesturemode) { SEQUENTIAL_GROUP = 0, PARALLEL_GROUP = 1, EXCLUSIVE_GROUP = 2 } | 定义手势组事件模式。  | 
| [ArkUI_GestureDirection](#arkui_gesturedirection) {<br/>GESTURE_DIRECTION_ALL = 0b1111, GESTURE_DIRECTION_HORIZONTAL = 0b0011, GESTURE_DIRECTION_VERTICAL = 0b1100, GESTURE_DIRECTION_LEFT = 0b0001,<br/>GESTURE_DIRECTION_RIGHT = 0b0010, GESTURE_DIRECTION_UP = 0b0100, GESTURE_DIRECTION_DOWN = 0b1000, GESTURE_DIRECTION_NONE = 0<br/>} | 定义滑动手势方向。  | 
| [ArkUI_GestureMask](#arkui_gesturemask) { NORMAL_GESTURE_MASK = 0, IGNORE_INTERNAL_GESTURE_MASK } | 定义手势屏蔽模式。  | 
| [ArkUI_GestureRecognizerType](#arkui_gesturerecognizertype) {<br/>TAP_GESTURE = 0, LONG_PRESS_GESTURE, PAN_GESTURE, PINCH_GESTURE,<br/>ROTATION_GESTURE, SWIPE_GESTURE, GROUP_GESTURE, CLICK_GESTURE, DRAG_DROP<br/>} | 定义手势类型。  | 
| [ArkUI_GestureInterruptResult](#arkui_gestureinterruptresult) { GESTURE_INTERRUPT_RESULT_CONTINUE = 0, GESTURE_INTERRUPT_RESULT_REJECT } | 定义手势打断结果。  | 
| [ArkUI_GestureRecognizerState](#arkui_gesturerecognizerstate) {<br/>ARKUI_GESTURE_RECOGNIZER_STATE_READY = 0, ARKUI_GESTURE_RECOGNIZER_STATE_DETECTING = 1, ARKUI_GESTURE_RECOGNIZER_STATE_PENDING = 2, ARKUI_GESTURE_RECOGNIZER_STATE_BLOCKED = 3,<br/>ARKUI_GESTURE_RECOGNIZER_STATE_SUCCESSFUL = 4, ARKUI_GESTURE_RECOGNIZER_STATE_FAILED = 5<br/>} | 定义手势识别器状态。  | 
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) { ARKUI_NATIVE_NODE, ARKUI_NATIVE_DIALOG, ARKUI_NATIVE_GESTURE, ARKUI_NATIVE_ANIMATE } | 定义Native接口集合类型。  | 
| [ArkUI_KeyCode](#arkui_keycode) {<br/>ARKUI_KEYCODE_UNKNOWN = -1, ARKUI_KEYCODE_FN = 0, ARKUI_KEYCODE_VOLUME_UP = 16, ARKUI_KEYCODE_VOLUME_DOWN = 17,<br/>ARKUI_KEYCODE_POWER = 18, ARKUI_KEYCODE_CAMERA = 19, ARKUI_KEYCODE_VOLUME_MUTE = 22, ARKUI_KEYCODE_MUTE = 23,<br/>ARKUI_KEYCODE_BRIGHTNESS_UP = 40, ARKUI_KEYCODE_BRIGHTNESS_DOWN = 41, ARKUI_KEYCODE_0 = 2000, ARKUI_KEYCODE_1 = 2001,<br/>ARKUI_KEYCODE_2 = 2002, ARKUI_KEYCODE_3 = 2003, ARKUI_KEYCODE_4 = 2004, ARKUI_KEYCODE_5 = 2005,<br/>ARKUI_KEYCODE_6 = 2006, ARKUI_KEYCODE_7 = 2007, ARKUI_KEYCODE_8 = 2008, ARKUI_KEYCODE_9 = 2009,<br/>ARKUI_KEYCODE_STAR = 2010, ARKUI_KEYCODE_POUND = 2011, ARKUI_KEYCODE_DPAD_UP = 2012, ARKUI_KEYCODE_DPAD_DOWN = 2013,<br/>ARKUI_KEYCODE_DPAD_LEFT = 2014, ARKUI_KEYCODE_DPAD_RIGHT = 2015, ARKUI_KEYCODE_DPAD_CENTER = 2016, ARKUI_KEYCODE_A = 2017,<br/>ARKUI_KEYCODE_B = 2018, ARKUI_KEYCODE_C = 2019, ARKUI_KEYCODE_D = 2020, ARKUI_KEYCODE_E = 2021,<br/>ARKUI_KEYCODE_F = 2022, ARKUI_KEYCODE_G = 2023, ARKUI_KEYCODE_H = 2024, ARKUI_KEYCODE_I = 2025,<br/>ARKUI_KEYCODE_J = 2026, ARKUI_KEYCODE_K = 2027, ARKUI_KEYCODE_L = 2028, ARKUI_KEYCODE_M = 2029,<br/>ARKUI_KEYCODE_N = 2030, ARKUI_KEYCODE_O = 2031, ARKUI_KEYCODE_P = 2032, ARKUI_KEYCODE_Q = 2033,<br/>ARKUI_KEYCODE_R = 2034, ARKUI_KEYCODE_S = 2035, ARKUI_KEYCODE_T = 2036, ARKUI_KEYCODE_U = 2037,<br/>ARKUI_KEYCODE_V = 2038, ARKUI_KEYCODE_W = 2039, ARKUI_KEYCODE_X = 2040, ARKUI_KEYCODE_Y = 2041,<br/>ARKUI_KEYCODE_Z = 2042, ARKUI_KEYCODE_COMMA = 2043, ARKUI_KEYCODE_PERIOD = 2044, ARKUI_KEYCODE_ALT_LEFT = 2045,<br/>ARKUI_KEYCODE_ALT_RIGHT = 2046, ARKUI_KEYCODE_SHIFT_LEFT = 2047, ARKUI_KEYCODE_SHIFT_RIGHT = 2048, ARKUI_KEYCODE_TAB = 2049,<br/>ARKUI_KEYCODE_SPACE = 2050, ARKUI_KEYCODE_SYM = 2051, ARKUI_KEYCODE_EXPLORER = 2052, ARKUI_KEYCODE_ENVELOPE = 2053,<br/>ARKUI_KEYCODE_ENTER = 2054, ARKUI_KEYCODE_DEL = 2055, ARKUI_KEYCODE_GRAVE = 2056, ARKUI_KEYCODE_MINUS = 2057,<br/>ARKUI_KEYCODE_EQUALS = 2058, ARKUI_KEYCODE_LEFT_BRACKET = 2059, ARKUI_KEYCODE_RIGHT_BRACKET = 2060, ARKUI_KEYCODE_BACKSLASH = 2061,<br/>ARKUI_KEYCODE_SEMICOLON = 2062, ARKUI_KEYCODE_APOSTROPHE = 2063, ARKUI_KEYCODE_SLASH = 2064, ARKUI_KEYCODE_AT = 2065,<br/>ARKUI_KEYCODE_PLUS = 2066, ARKUI_KEYCODE_MENU = 2067, ARKUI_KEYCODE_PAGE_UP = 2068, ARKUI_KEYCODE_PAGE_DOWN = 2069,<br/>ARKUI_KEYCODE_ESCAPE = 2070, ARKUI_KEYCODE_FORWARD_DEL = 2071, ARKUI_KEYCODE_CTRL_LEFT = 2072, ARKUI_KEYCODE_CTRL_RIGHT = 2073,<br/>ARKUI_KEYCODE_CAPS_LOCK = 2074, ARKUI_KEYCODE_SCROLL_LOCK = 2075, ARKUI_KEYCODE_META_LEFT = 2076, ARKUI_KEYCODE_META_RIGHT = 2077,<br/>ARKUI_KEYCODE_FUNCTION = 2078, ARKUI_KEYCODE_SYSRQ = 2079, ARKUI_KEYCODE_BREAK = 2080, ARKUI_KEYCODE_MOVE_HOME = 2081,<br/>ARKUI_KEYCODE_MOVE_END = 2082, ARKUI_KEYCODE_INSERT = 2083, ARKUI_KEYCODE_FORWARD = 2084, ARKUI_KEYCODE_MEDIA_PLAY = 2085,<br/>ARKUI_KEYCODE_MEDIA_PAUSE = 2086, ARKUI_KEYCODE_MEDIA_CLOSE = 2087, ARKUI_KEYCODE_MEDIA_EJECT = 2088, ARKUI_KEYCODE_MEDIA_RECORD = 2089,<br/>ARKUI_KEYCODE_F1 = 2090, ARKUI_KEYCODE_F2 = 2091, ARKUI_KEYCODE_F3 = 2092, ARKUI_KEYCODE_F4 = 2093,<br/>ARKUI_KEYCODE_F5 = 2094, ARKUI_KEYCODE_F6 = 2095, ARKUI_KEYCODE_F7 = 2096, ARKUI_KEYCODE_F8 = 2097,<br/>ARKUI_KEYCODE_F9 = 2098, ARKUI_KEYCODE_F10 = 2099, ARKUI_KEYCODE_F11 = 2100, ARKUI_KEYCODE_F12 = 2101,<br/>ARKUI_KEYCODE_NUM_LOCK = 2102, ARKUI_KEYCODE_NUMPAD_0 = 2103, ARKUI_KEYCODE_NUMPAD_1 = 2104, ARKUI_KEYCODE_NUMPAD_2 = 2105,<br/>ARKUI_KEYCODE_NUMPAD_3 = 2106, ARKUI_KEYCODE_NUMPAD_4 = 2107, ARKUI_KEYCODE_NUMPAD_5 = 2108, ARKUI_KEYCODE_NUMPAD_6 = 2109,<br/>ARKUI_KEYCODE_NUMPAD_7 = 2110, ARKUI_KEYCODE_NUMPAD_8 = 2111, ARKUI_KEYCODE_NUMPAD_9 = 2112, ARKUI_KEYCODE_NUMPAD_DIVIDE = 2113,<br/>ARKUI_KEYCODE_NUMPAD_MULTIPLY = 2114, ARKUI_KEYCODE_NUMPAD_SUBTRACT = 2115, ARKUI_KEYCODE_NUMPAD_ADD = 2116, ARKUI_KEYCODE_NUMPAD_DOT = 2117,<br/>ARKUI_KEYCODE_NUMPAD_COMMA = 2118, ARKUI_KEYCODE_NUMPAD_ENTER = 2119, ARKUI_KEYCODE_NUMPAD_EQUALS = 2120, ARKUI_KEYCODE_NUMPAD_LEFT_PAREN = 2121,<br/>ARKUI_KEYCODE_NUMPAD_RIGHT_PAREN = 2122<br/>} | 按键事件的键码  | 
| [ArkUI_KeyEventType](#arkui_keyeventtype) {<br/>ARKUI_KEY_EVENT_UNKNOWN = -1, ARKUI_KEY_EVENT_DOWN = 0, ARKUI_KEY_EVENT_UP = 1, ARKUI_KEY_EVENT_LONG_PRESS = 2,<br/>ARKUI_KEY_EVENT_CLICK = 3<br/>} | 按键的类型。  | 
| [ArkUI_KeySourceType](#arkui_keysourcetype) { ARKUI_KEY_SOURCE_UNKNOWN = 0, ARKUI_KEY_SOURCE_TYPE_MOUSE = 1, ARKUI_KEY_SOURCE_TYPE_KEYBOARD = 4, ARKUI_KEY_SOURCE_TYPE_JOYSTICK = 5 } | 触发当前按键的输入设备类型。  | 
| [ArkUI_KeyIntension](#arkui_keyintension) {<br/>ARKUI_KEY_INTENSION_UNKNOWN = -1, ARKUI_KEY_INTENSION_UP = 1, ARKUI_KEY_INTENSION_DOWN = 2, ARKUI_KEY_INTENSION_LEFT = 3,<br/>ARKUI_KEY_INTENSION_RIGHT = 4, ARKUI_KEY_INTENSION_SELECT = 5, ARKUI_KEY_INTENSION_ESCAPE = 6, ARKUI_KEY_INTENSION_BACK = 7,<br/>ARKUI_KEY_INTENSION_FORWARD = 8, ARKUI_KEY_INTENSION_MENU = 9, ARKUI_KEY_INTENSION_HOME = 10, ARKUI_KEY_INTENSION_PAGE_UP = 11,<br/>ARKUI_KEY_INTENSION_PAGE_DOWN = 12, ARKUI_KEY_INTENSION_ZOOM_OUT = 13, ARKUI_KEY_INTENSION_ZOOM_IN = 14, ARKUI_KEY_INTENTION_MEDIA_PLAY_PAUSE = 100,<br/>ARKUI_KEY_INTENTION_MEDIA_FAST_FORWARD = 101, ARKUI_KEY_INTENTION_MEDIA_FAST_PLAYBACK = 103, ARKUI_KEY_INTENTION_MEDIA_NEXT = 104, ARKUI_KEY_INTENTION_MEDIA_PREVIOUS = 105,<br/>ARKUI_KEY_INTENTION_MEDIA_MUTE = 106, ARKUI_KEY_INTENTION_VOLUME_UP = 107, ARKUI_KEY_INTENTION_VOLUME_DOWN = 108, ARKUI_KEY_INTENTION_CALL = 200,<br/>ARKUI_KEY_INTENTION_CAMERA = 300<br/>} | 按键对应的意图。  | 
| [ArkUI_NodeType](#arkui_nodetype) {<br/>ARKUI_NODE_CUSTOM = 0, ARKUI_NODE_TEXT = 1, ARKUI_NODE_SPAN = 2, ARKUI_NODE_IMAGE_SPAN = 3,<br/>ARKUI_NODE_IMAGE = 4, ARKUI_NODE_TOGGLE = 5, ARKUI_NODE_LOADING_PROGRESS = 6, ARKUI_NODE_TEXT_INPUT = 7,<br/>ARKUI_NODE_TEXT_AREA = 8, ARKUI_NODE_BUTTON = 9, ARKUI_NODE_PROGRESS = 10, ARKUI_NODE_CHECKBOX = 11,<br/>ARKUI_NODE_XCOMPONENT = 12, ARKUI_NODE_DATE_PICKER = 13, ARKUI_NODE_TIME_PICKER = 14, ARKUI_NODE_TEXT_PICKER = 15,<br/>ARKUI_NODE_CALENDAR_PICKER = 16, ARKUI_NODE_SLIDER = 17, ARKUI_NODE_RADIO = 18, ARKUI_NODE_IMAGE_ANIMATOR = 19,<br/>ARKUI_NODE_XCOMPONENT_TEXTURE = 20,<br/>ARKUI_NODE_CHECKBOX_GROUP = 21,<br/>ARKUI_NODE_STACK = MAX_NODE_SCOPE_NUM, ARKUI_NODE_SWIPER, ARKUI_NODE_SCROLL,<br/>ARKUI_NODE_LIST, ARKUI_NODE_LIST_ITEM, ARKUI_NODE_LIST_ITEM_GROUP, ARKUI_NODE_COLUMN,<br/>ARKUI_NODE_ROW, ARKUI_NODE_FLEX, ARKUI_NODE_REFRESH, ARKUI_NODE_WATER_FLOW,<br/>ARKUI_NODE_FLOW_ITEM, ARKUI_NODE_RELATIVE_CONTAINER, ARKUI_NODE_GRID, ARKUI_NODE_GRID_ITEM,<br/>ARKUI_NODE_CUSTOM_SPAN, ARKUI_NODE_EMBEDDED_COMPONENT<br/>} | 提供ArkUI在Native侧可创建组件类型。  | 
| [ArkUI_NodeAttributeType](#arkui_nodeattributetype) {<br/>NODE_WIDTH = 0, NODE_HEIGHT, NODE_BACKGROUND_COLOR, NODE_BACKGROUND_IMAGE,<br/>NODE_PADDING, NODE_ID, NODE_ENABLED, NODE_MARGIN,<br/>NODE_TRANSLATE, NODE_SCALE, NODE_ROTATE, NODE_BRIGHTNESS,<br/>NODE_SATURATION, NODE_BLUR, NODE_LINEAR_GRADIENT, NODE_ALIGNMENT,<br/>NODE_OPACITY, NODE_BORDER_WIDTH, NODE_BORDER_RADIUS, NODE_BORDER_COLOR,<br/>NODE_BORDER_STYLE, NODE_Z_INDEX, NODE_VISIBILITY, NODE_CLIP,<br/>NODE_CLIP_SHAPE, NODE_TRANSFORM, NODE_HIT_TEST_BEHAVIOR, NODE_POSITION,<br/>NODE_SHADOW, NODE_CUSTOM_SHADOW, NODE_BACKGROUND_IMAGE_SIZE, NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE,<br/>NODE_BACKGROUND_BLUR_STYLE, NODE_TRANSFORM_CENTER, NODE_OPACITY_TRANSITION, NODE_ROTATE_TRANSITION,<br/>NODE_SCALE_TRANSITION, NODE_TRANSLATE_TRANSITION, NODE_MOVE_TRANSITION, NODE_FOCUSABLE,<br/>NODE_DEFAULT_FOCUS, NODE_RESPONSE_REGION, NODE_OVERLAY, NODE_SWEEP_GRADIENT,<br/>NODE_RADIAL_GRADIENT, NODE_MASK, NODE_BLEND_MODE, NODE_DIRECTION,<br/>NODE_CONSTRAINT_SIZE, NODE_GRAY_SCALE, NODE_INVERT, NODE_SEPIA,<br/>NODE_CONTRAST, NODE_FOREGROUND_COLOR, NODE_OFFSET, NODE_MARK_ANCHOR,<br/>NODE_BACKGROUND_IMAGE_POSITION, NODE_ALIGN_RULES, NODE_ALIGN_SELF, NODE_FLEX_GROW,<br/>NODE_FLEX_SHRINK, NODE_FLEX_BASIS, NODE_ACCESSIBILITY_GROUP, NODE_ACCESSIBILITY_TEXT,<br/>NODE_ACCESSIBILITY_MODE, NODE_ACCESSIBILITY_DESCRIPTION, NODE_FOCUS_STATUS, NODE_ASPECT_RATIO,<br/>NODE_LAYOUT_WEIGHT, NODE_DISPLAY_PRIORITY, NODE_OUTLINE_WIDTH, NODE_WIDTH_PERCENT,<br/>NODE_HEIGHT_PERCENT, NODE_PADDING_PERCENT, NODE_MARGIN_PERCENT, NODE_GEOMETRY_TRANSITION,<br/>NODE_RELATIVE_LAYOUT_CHAIN_MODE, NODE_RENDER_FIT, NODE_OUTLINE_COLOR, NODE_SIZE,<br/>NODE_RENDER_GROUP, NODE_COLOR_BLEND, NODE_FOREGROUND_BLUR_STYLE, NODE_LAYOUT_RECT,<br/>NODE_FOCUS_ON_TOUCH, NODE_BORDER_WIDTH_PERCENT, NODE_BORDER_RADIUS_PERCENT, NODE_ACCESSIBILITY_ID = 87,<br/>NODE_ACCESSIBILITY_ACTIONS = 88, NODE_ACCESSIBILITY_ROLE = 89, NODE_ACCESSIBILITY_STATE = 90, NODE_ACCESSIBILITY_VALUE = 91,<br/>NODE_EXPAND_SAFE_AREA = 92, NODE_VISIBLE_AREA_CHANGE_RATIO = 93, NODE_TRANSITION = 94, NODE_UNIQUE_ID = 95, NODE_FOCUS_BOX = 96,<br/>NODE_CLICK_DISTANCE = 97, NODE_TAB_STOP = 98,  NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE = 100, NODE_NEXT_FOCUS = 101, NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO = 102, NODE_TRANSLATE_WITH_PERCENT = 103,  NODE_ROTATE_ANGLE = 104, NODE_TEXT_CONTENT = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TEXT, NODE_FONT_COLOR,<br/>NODE_FONT_SIZE, NODE_FONT_STYLE, NODE_FONT_WEIGHT, NODE_TEXT_LINE_HEIGHT,<br/>NODE_TEXT_DECORATION, NODE_TEXT_CASE, NODE_TEXT_LETTER_SPACING, NODE_TEXT_MAX_LINES,<br/>NODE_TEXT_ALIGN, NODE_TEXT_OVERFLOW, NODE_FONT_FAMILY, NODE_TEXT_COPY_OPTION,<br/>NODE_TEXT_BASELINE_OFFSET, NODE_TEXT_TEXT_SHADOW, NODE_TEXT_MIN_FONT_SIZE, NODE_TEXT_MAX_FONT_SIZE,<br/>NODE_TEXT_FONT, NODE_TEXT_HEIGHT_ADAPTIVE_POLICY, NODE_TEXT_INDENT, NODE_TEXT_WORD_BREAK,<br/>NODE_TEXT_ELLIPSIS_MODE, NODE_TEXT_LINE_SPACING, NODE_FONT_FEATURE, NODE_TEXT_ENABLE_DATA_DETECTOR,<br/>NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG, NODE_TEXT_SELECTED_BACKGROUND_COLOR, NODE_TEXT_CONTENT_WITH_STYLED_STRING, NODE_TEXT_HALF_LEADING = 1029,NODE_IMMUTABLE_FONT_WEIGHT = 1030,NODE_TEXT_LINE_COUNT = 1031,NODE_TEXT_OPTIMIZE_TRAILING_SPACE = 1032, NODE_TEXT_LINEAR_GRADIENT = 1033, NODE_TEXT_RADIAL_GRADIENT = 1034, NODE_TEXT_VERTICAL_ALIGN = 1035,<br/>NODE_SPAN_CONTENT = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_SPAN, NODE_SPAN_TEXT_BACKGROUND_STYLE, NODE_SPAN_BASELINE_OFFSET, NODE_IMAGE_SPAN_SRC = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_IMAGE_SPAN,<br/>NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT, NODE_IMAGE_SPAN_ALT, NODE_IMAGE_SPAN_BASELINE_OFFSET = 3003, NODE_IMAGE_SRC = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_IMAGE,<br/>NODE_IMAGE_OBJECT_FIT, NODE_IMAGE_INTERPOLATION, NODE_IMAGE_OBJECT_REPEAT, NODE_IMAGE_COLOR_FILTER,<br/>NODE_IMAGE_AUTO_RESIZE, NODE_IMAGE_ALT, NODE_IMAGE_DRAGGABLE, NODE_IMAGE_RENDER_MODE,<br/>NODE_IMAGE_FIT_ORIGINAL_SIZE, NODE_IMAGE_FILL_COLOR, NODE_IMAGE_RESIZABLE, NODE_IMAGE_SYNC_LOAD, NODE_TOGGLE_SELECTED_COLOR = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TOGGLE,<br/>NODE_TOGGLE_SWITCH_POINT_COLOR, NODE_TOGGLE_VALUE, NODE_TOGGLE_UNSELECTED_COLOR, NODE_LOADING_PROGRESS_COLOR = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_LOADING_PROGRESS,<br/>NODE_LOADING_PROGRESS_ENABLE_LOADING, NODE_TEXT_INPUT_PLACEHOLDER = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TEXT_INPUT, NODE_TEXT_INPUT_TEXT, NODE_TEXT_INPUT_CARET_COLOR,<br/>NODE_TEXT_INPUT_CARET_STYLE, NODE_TEXT_INPUT_SHOW_UNDERLINE, NODE_TEXT_INPUT_MAX_LENGTH, NODE_TEXT_INPUT_ENTER_KEY_TYPE,<br/>NODE_TEXT_INPUT_PLACEHOLDER_COLOR, NODE_TEXT_INPUT_PLACEHOLDER_FONT, NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS, NODE_TEXT_INPUT_TYPE,<br/>NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR, NODE_TEXT_INPUT_SHOW_PASSWORD_ICON, NODE_TEXT_INPUT_EDITING, NODE_TEXT_INPUT_CANCEL_BUTTON,<br/>NODE_TEXT_INPUT_TEXT_SELECTION, NODE_TEXT_INPUT_UNDERLINE_COLOR, NODE_TEXT_INPUT_ENABLE_AUTO_FILL, NODE_TEXT_INPUT_CONTENT_TYPE,<br/>NODE_TEXT_INPUT_PASSWORD_RULES, NODE_TEXT_INPUT_SELECT_ALL, NODE_TEXT_INPUT_INPUT_FILTER, NODE_TEXT_INPUT_STYLE,<br/>NODE_TEXT_INPUT_CARET_OFFSET, NODE_TEXT_INPUT_CONTENT_RECT, NODE_TEXT_INPUT_CONTENT_LINE_COUNT, NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN,<br/>NODE_TEXT_INPUT_BLUR_ON_SUBMIT, NODE_TEXT_INPUT_CUSTOM_KEYBOARD, NODE_TEXT_INPUT_WORD_BREAK, NODE_TEXT_INPUT_NUMBER_OF_LINES,<br/>NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS, NODE_TEXT_INPUT_LETTER_SPACING = 7032, NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT = 7033, NODE_TEXT_INPUT_HALF_LEADING = 7034, NODE_TEXT_INPUT_KEYBOARD_APPEARANCE = 7035, NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036, NODE_TEXT_INPUT_LINE_HEIGHT = 7037, NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TEXT_AREA, NODE_TEXT_AREA_TEXT, NODE_TEXT_AREA_MAX_LENGTH,<br/>NODE_TEXT_AREA_PLACEHOLDER_COLOR, NODE_TEXT_AREA_PLACEHOLDER_FONT, NODE_TEXT_AREA_CARET_COLOR, NODE_TEXT_AREA_EDITING,<br/>NODE_TEXT_AREA_TYPE, NODE_TEXT_AREA_SHOW_COUNTER, NODE_TEXT_AREA_SELECTION_MENU_HIDDEN, NODE_TEXT_AREA_BLUR_ON_SUBMIT,<br/>NODE_TEXT_AREA_INPUT_FILTER, NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR, NODE_TEXT_AREA_ENTER_KEY_TYPE, NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS,<br/>NODE_TEXT_AREA_CARET_OFFSET, NODE_TEXT_AREA_CONTENT_RECT, NODE_TEXT_AREA_CONTENT_LINE_COUNT, NODE_TEXT_AREA_TEXT_SELECTION,<br/>NODE_TEXT_AREA_ENABLE_AUTO_FILL, NODE_TEXT_AREA_CONTENT_TYPE, NODE_TEXT_AREA_NUMBER_OF_LINES, NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS, NODE_TEXT_AREA_LETTER_SPACING = 8023, NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024, NODE_TEXT_AREA_HALF_LEADING = 8025, NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026, NODE_TEXT_AREA_MAX_LINES = 8027, NODE_TEXT_AREA_LINE_SPACING = 8028, NODE_TEXT_AREA_LINE_HEIGHT = 8031,<br/>NODE_BUTTON_LABEL = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_BUTTON, NODE_BUTTON_TYPE, NODE_BUTTON_MIN_FONT_SCALE, NODE_BUTTON_MAX_FONT_SCALE, NODE_PROGRESS_VALUE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_PROGRESS, NODE_PROGRESS_TOTAL,<br/>NODE_PROGRESS_COLOR, NODE_PROGRESS_TYPE, NODE_PROGRESS_LINEAR_STYLE, NODE_CHECKBOX_SELECT = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_CHECKBOX, NODE_CHECKBOX_SELECT_COLOR,<br/>NODE_CHECKBOX_UNSELECT_COLOR, NODE_CHECKBOX_MARK, NODE_CHECKBOX_SHAPE, NODE_XCOMPONENT_ID = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_XCOMPONENT,<br/>NODE_XCOMPONENT_TYPE, NODE_XCOMPONENT_SURFACE_SIZE, NODE_XCOMPONENT_SURFACE_RECT, NODE_XCOMPONENT_ENABLE_ANALYZER, NODE_DATE_PICKER_LUNAR = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_DATE_PICKER, NODE_DATE_PICKER_START,<br/>NODE_DATE_PICKER_END, NODE_DATE_PICKER_SELECTED, NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE, NODE_DATE_PICKER_TEXT_STYLE,<br/>NODE_DATE_PICKER_SELECTED_TEXT_STYLE, NODE_DATE_PICKER_MODE, NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK = 13008, NODE_DATE_PICKER_CAN_LOOP = 13009, NODE_TIME_PICKER_SELECTED = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TIME_PICKER, NODE_TIME_PICKER_USE_MILITARY_TIME, NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE,<br/>NODE_TIME_PICKER_TEXT_STYLE, NODE_TIME_PICKER_SELECTED_TEXT_STYLE, NODE_TIME_PICKER_START, NODE_TIME_PICKER_END, NODE_TIME_PICKER_ENABLE_CASCADE = 14007, NODE_TEXT_PICKER_OPTION_RANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TEXT_PICKER, NODE_TEXT_PICKER_OPTION_SELECTED,<br/>NODE_TEXT_PICKER_OPTION_VALUE, NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE, NODE_TEXT_PICKER_TEXT_STYLE, NODE_TEXT_PICKER_SELECTED_TEXT_STYLE,<br/>NODE_TEXT_PICKER_SELECTED_INDEX, NODE_TEXT_PICKER_CAN_LOOP, NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT,NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK = 15010, NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE = 15011, NODE_CALENDAR_PICKER_HINT_RADIUS = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_CALENDAR_PICKER,<br/>NODE_CALENDAR_PICKER_SELECTED_DATE, NODE_CALENDAR_PICKER_EDGE_ALIGNMENT, NODE_CALENDAR_PICKER_TEXT_STYLE, NODE_CALENDAR_PICKER_START = 16004, NODE_CALENDAR_PICKER_END = 16005,<br/>NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE = 16006, NODE_CALENDAR_PICKER_MARK_TODAY = 16007,<br/>NODE_SLIDER_BLOCK_COLOR = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_SLIDER,<br/>NODE_SLIDER_TRACK_COLOR, NODE_SLIDER_SELECTED_COLOR, NODE_SLIDER_SHOW_STEPS, NODE_SLIDER_BLOCK_STYLE,<br/>NODE_SLIDER_VALUE, NODE_SLIDER_MIN_VALUE, NODE_SLIDER_MAX_VALUE, NODE_SLIDER_STEP,<br/>NODE_SLIDER_DIRECTION, NODE_SLIDER_REVERSE, NODE_SLIDER_STYLE, NODE_SLIDER_TRACK_THICKNESS,NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013,NODE_SLIDER_PREFIX, NODE_SLIDER_SUFFIX,<br/>NODE_RADIO_CHECKED = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_RADIO, NODE_RADIO_STYLE, NODE_RADIO_VALUE, NODE_RADIO_GROUP,<br/>NODE_CHECKBOX_GROUP_NAME = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_CHECKBOX_GROUP, NODE_CHECKBOX_GROUP_SELECT_ALL, NODE_CHECKBOX_GROUP_SELECTED_COLOR, NODE_CHECKBOX_GROUP_UNSELECTED_COLOR, NODE_CHECKBOX_GROUP_MARK, NODE_CHECKBOX_GROUP_SHAPE,<br/>NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_STACK, NODE_SCROLL_BAR_DISPLAY_MODE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_SCROLL, NODE_SCROLL_BAR_WIDTH, NODE_SCROLL_BAR_COLOR, NODE_SCROLL_BAR_MARGIN = 1002022,<br/>NODE_SCROLL_SCROLL_DIRECTION, NODE_SCROLL_EDGE_EFFECT, NODE_SCROLL_ENABLE_SCROLL_INTERACTION, NODE_SCROLL_FRICTION,<br/>NODE_SCROLL_SNAP, NODE_SCROLL_NESTED_SCROLL, NODE_SCROLL_OFFSET, NODE_SCROLL_EDGE,<br/>NODE_SCROLL_ENABLE_PAGING, NODE_SCROLL_PAGE, NODE_SCROLL_BY, NODE_SCROLL_FLING,<br/>NODE_SCROLL_FADING_EDGE, NODE_SCROLL_SIZE, NODE_SCROLL_CONTENT_END_OFFSET, NODE_SCROLL_FLING_SPEED_LIMIT = 1002019, NODE_SCROLL_CLIP_CONTENT = 1002020, NODE_SCROLL_BACK_TO_TOP = 1002021, NODE_LIST_DIRECTION = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_LIST, NODE_LIST_STICKY,<br/>NODE_LIST_SPACE, NODE_LIST_NODE_ADAPTER, NODE_LIST_CACHED_COUNT, NODE_LIST_SCROLL_TO_INDEX,<br/>NODE_LIST_ALIGN_LIST_ITEM, NODE_LIST_CHILDREN_MAIN_SIZE = 1003007, NODE_LIST_INITIAL_INDEX = 1003008, NODE_LIST_DIVIDER = 1003009, NODE_LIST_SCROLL_TO_INDEX_IN_GROUP = 1003010, NODE_LIST_LANES = 1003011, NODE_LIST_SCROLL_SNAP_ALIGN = 1003012, NODE_LIST_MAINTAIN_VISIBLE_CONTENT_POSITION = 1003013, NODE_LIST_STACK_FROM_END = 1003014,<br/>NODE_SWIPER_LOOP = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_SWIPER, NODE_SWIPER_AUTO_PLAY, NODE_SWIPER_SHOW_INDICATOR, NODE_SWIPER_INTERVAL,<br/>NODE_SWIPER_VERTICAL, NODE_SWIPER_DURATION, NODE_SWIPER_CURVE, NODE_SWIPER_ITEM_SPACE,<br/>NODE_SWIPER_INDEX, NODE_SWIPER_DISPLAY_COUNT, NODE_SWIPER_DISABLE_SWIPE, NODE_SWIPER_SHOW_DISPLAY_ARROW,<br/>NODE_SWIPER_EDGE_EFFECT_MODE, NODE_SWIPER_NODE_ADAPTER, NODE_SWIPER_CACHED_COUNT, NODE_SWIPER_PREV_MARGIN,<br/>NODE_SWIPER_NEXT_MARGIN, NODE_SWIPER_INDICATOR, NODE_SWIPER_NESTED_SCROLL, NODE_SWIPER_SWIPE_TO_INDEX,<br/>NODE_SWIPER_INDICATOR_INTERACTIVE, NODE_SWIPER_PAGE_FLIP_MODE, NODE_SWIPER_AUTO_FILL, NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023, NODE_LIST_ITEM_SWIPE_ACTION = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_LIST_ITEM, NODE_LIST_ITEM_GROUP_SET_HEADER = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_LIST_ITEM_GROUP,<br/>NODE_LIST_ITEM_GROUP_SET_FOOTER, NODE_LIST_ITEM_GROUP_SET_DIVIDER, NODE_LIST_ITEM_GROUP_CHILDREN_MAIN_SIZE = 1005003, NODE_LIST_ITEM_GROUP_NODE_ADAPTER = 1005004, NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_COLUMN,<br/>NODE_COLUMN_JUSTIFY_CONTENT, NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_ROW, NODE_ROW_JUSTIFY_CONTENT, NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_FLEX,<br/>NODE_REFRESH_REFRESHING = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_REFRESH, NODE_REFRESH_CONTENT, NODE_REFRESH_PULL_DOWN_RATIO = 1009002, NODE_REFRESH_OFFSET = 1009003,NODE_REFRESH_PULL_TO_REFRESH = 1009004, NODE_REFRESH_MAX_PULL_DOWN_DISTANCE = 1009005, <br/>NODE_WATER_FLOW_LAYOUT_DIRECTION = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_WATER_FLOW, NODE_WATER_FLOW_COLUMN_TEMPLATE, NODE_WATER_FLOW_ROW_TEMPLATE,<br/>NODE_WATER_FLOW_COLUMN_GAP, NODE_WATER_FLOW_ROW_GAP, NODE_WATER_FLOW_SECTION_OPTION, NODE_WATER_FLOW_NODE_ADAPTER,<br/>NODE_WATER_FLOW_CACHED_COUNT, NODE_WATER_FLOW_FOOTER, NODE_WATER_FLOW_SCROLL_TO_INDEX, NODE_WATER_FLOW_ITEM_CONSTRAINT_SIZE, NODE_WATER_FLOW_LAYOUT_MODE,<br/>NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_RELATIVE_CONTAINER, NODE_RELATIVE_CONTAINER_BARRIER, NODE_GRID_COLUMN_TEMPLATE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_GRID, NODE_GRID_ROW_TEMPLATE,<br/>NODE_GRID_COLUMN_GAP, NODE_GRID_ROW_GAP, NODE_GRID_NODE_ADAPTER, NODE_GRID_CACHED_COUNT, NODE_TEXT_PICKER_COLUMN_WIDTHS = 15009,<br/>NODE_IMAGE_ANIMATOR_IMAGES = ARKUI_NODE_IMAGE_ANIMATOR \* MAX_NODE_SCOPE_NUM, NODE_IMAGE_ANIMATOR_STATE, NODE_IMAGE_ANIMATOR_DURATION, NODE_IMAGE_ANIMATOR_REVERSE,<br/>NODE_IMAGE_ANIMATOR_FIXED_SIZE, NODE_IMAGE_ANIMATOR_FILL_MODE, NODE_IMAGE_ANIMATOR_ITERATION,<br/>NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_EMBEDDED_COMPONENT, NODE_EMBEDDED_COMPONENT_OPTION<br/>} | 定义ArkUI在Native侧可以设置的属性样式集合。  |
| [ArkUI_NodeEventType](#arkui_nodeeventtype) {<br/>NODE_TOUCH_EVENT = 0, NODE_EVENT_ON_APPEAR, NODE_EVENT_ON_DISAPPEAR, NODE_EVENT_ON_AREA_CHANGE,<br/>NODE_ON_FOCUS, NODE_ON_BLUR, NODE_ON_CLICK, NODE_ON_TOUCH_INTERCEPT,<br/>NODE_EVENT_ON_VISIBLE_AREA_CHANGE, NODE_ON_HOVER, NODE_ON_MOUSE, NODE_EVENT_ON_ATTACH,<br/>NODE_EVENT_ON_DETACH, NODE_ON_ACCESSIBILITY_ACTIONS = 13, NODE_ON_PRE_DRAG = 14, NODE_ON_DRAG_START = 15,<br/>NODE_ON_DRAG_ENTER = 16, NODE_ON_DRAG_MOVE = 17, NODE_ON_DRAG_LEAVE = 18, NODE_ON_DROP = 19,<br/>NODE_ON_DRAG_END = 20, NODE_ON_KEY_EVENT = 21, NODE_ON_KEY_PRE_IME = 22, NODE_ON_FOCUS_AXIS = 23, NODE_DISPATCH_KEY_EVENT = 24, NODE_ON_AXIS = 25, NODE_ON_CLICK_EVENT = 26, NODE_ON_HOVER_EVENT = 27, NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT = 28, NODE_ON_HOVER_MOVE = 29, NODE_TEXT_ON_DETECT_RESULT_UPDATE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TEXT, NODE_TEXT_SPAN_ON_LONG_PRESS = 1001,<br/>NODE_IMAGE_ON_COMPLETE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_IMAGE, NODE_IMAGE_ON_ERROR, NODE_IMAGE_ON_SVG_PLAY_FINISH, NODE_IMAGE_ON_DOWNLOAD_PROGRESS,<br/>NODE_TOGGLE_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TOGGLE, NODE_TEXT_INPUT_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TEXT_INPUT, NODE_TEXT_INPUT_ON_SUBMIT, NODE_TEXT_INPUT_ON_CUT,<br/>NODE_TEXT_INPUT_ON_PASTE, NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE, NODE_TEXT_INPUT_ON_EDIT_CHANGE, NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR,<br/>NODE_TEXT_INPUT_ON_CONTENT_SCROLL, NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE, NODE_TEXT_INPUT_ON_WILL_INSERT = 7009, NODE_TEXT_INPUT_ON_DID_INSERT = 7010,<br/>NODE_TEXT_INPUT_ON_WILL_DELETE = 7011, NODE_TEXT_INPUT_ON_DID_DELETE = 7012, NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT = 7013, NODE_TEXT_INPUT_ON_WILL_CHANGE = 7014, NODE_TEXT_AREA_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TEXT_AREA, NODE_TEXT_AREA_ON_PASTE,<br/>NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE, NODE_TEXT_AREA_ON_EDIT_CHANGE, NODE_TEXT_AREA_ON_SUBMIT, NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR,<br/>NODE_TEXT_AREA_ON_CONTENT_SCROLL, NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE, NODE_TEXT_AREA_ON_WILL_INSERT = 8008, NODE_TEXT_AREA_ON_DID_INSERT = 8009,<br/>NODE_TEXT_AREA_ON_WILL_DELETE = 8010, NODE_TEXT_AREA_ON_DID_DELETE = 8011, NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT = 8012, NODE_TEXT_AREA_ON_WILL_CHANGE = 8013, NODE_CHECKBOX_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_CHECKBOX, NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_DATE_PICKER,<br/>NODE_TIME_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TIME_PICKER, NODE_TEXT_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_TEXT_PICKER, NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP, NODE_CALENDAR_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_CALENDAR_PICKER, NODE_SLIDER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_SLIDER,<br/>NODE_RADIO_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_RADIO, NODE_IMAGE_ANIMATOR_EVENT_ON_START = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_IMAGE_ANIMATOR, NODE_IMAGE_ANIMATOR_EVENT_ON_PAUSE, NODE_IMAGE_ANIMATOR_EVENT_ON_REPEAT,<br/>NODE_IMAGE_ANIMATOR_EVENT_ON_CANCEL, NODE_IMAGE_ANIMATOR_EVENT_ON_FINISH, <br/>NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_CHECKBOX_GROUP,<br/> NODE_SWIPER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_SWIPER, NODE_SWIPER_EVENT_ON_ANIMATION_START,<br/>NODE_SWIPER_EVENT_ON_ANIMATION_END, NODE_SWIPER_EVENT_ON_GESTURE_SWIPE, NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL, NODE_SWIPER_EVENT_ON_SELECTED = 1001005, NODE_SWIPER_EVENT_ON_UNSELECTED = 1001006, NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL = 1001007, NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED =1001008, NODE_SCROLL_EVENT_ON_SCROLL = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_SCROLL,<br/>NODE_SCROLL_EVENT_ON_SCROLL_FRAME_BEGIN, NODE_SCROLL_EVENT_ON_WILL_SCROLL, NODE_SCROLL_EVENT_ON_DID_SCROLL, NODE_SCROLL_EVENT_ON_SCROLL_START,<br/>NODE_SCROLL_EVENT_ON_SCROLL_STOP, NODE_SCROLL_EVENT_ON_SCROLL_EDGE, NODE_SCROLL_EVENT_ON_REACH_START, NODE_SCROLL_EVENT_ON_REACH_END,<br/>NODE_LIST_ON_SCROLL_INDEX = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_LIST, NODE_LIST_ON_WILL_SCROLL, NODE_LIST_ON_DID_SCROLL, NODE_LIST_ON_SCROLL_VISIBLE_CONTENT_CHANGE, NODE_REFRESH_STATE_CHANGE = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_REFRESH,<br/>NODE_REFRESH_ON_REFRESH, NODE_REFRESH_ON_OFFSET_CHANGE, NODE_ON_WILL_SCROLL = MAX_NODE_SCOPE_NUM \* ARKUI_NODE_WATER_FLOW, NODE_WATER_FLOW_ON_DID_SCROLL,<br/>NODE_WATER_FLOW_ON_SCROLL_INDEX<br/>} | 提供NativeNode组件支持的事件类型定义。  | 
| [ArkUI_NodeDirtyFlag](#arkui_nodedirtyflag) { NODE_NEED_MEASURE = 1, NODE_NEED_LAYOUT, NODE_NEED_RENDER } | 自定义组件调用&lt;b&gt;::markDirty是传递的脏区标识类型。  | 
| [ArkUI_NodeCustomEventType](#arkui_nodecustomeventtype) {<br/>ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE = 1 &lt;&lt; 0, ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT = 1 &lt;&lt; 1, ARKUI_NODE_CUSTOM_EVENT_ON_DRAW = 1 &lt;&lt; 2, ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW = 1 &lt;&lt; 3, ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW = 1 &lt;&lt; 4, ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT = 1 &lt;&lt; 5, ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND = 1 &lt;&lt; 6<br/>} | 定义自定义组件事件类型。  | 
| [ArkUI_NodeAdapterEventType](#arkui_nodeadaptereventtype) {<br/>NODE_ADAPTER_EVENT_WILL_ATTACH_TO_NODE = 1, NODE_ADAPTER_EVENT_WILL_DETACH_FROM_NODE = 2, NODE_ADAPTER_EVENT_ON_GET_NODE_ID = 3, NODE_ADAPTER_EVENT_ON_ADD_NODE_TO_ADAPTER = 4,<br/>NODE_ADAPTER_EVENT_ON_REMOVE_NODE_FROM_ADAPTER = 5<br/>} | 定义节点适配器事件枚举值。  | 
| [ArkUI_NodeContentEventType](#arkui_nodecontenteventtype) { NODE_CONTENT_EVENT_ON_ATTACH_TO_WINDOW = 0, NODE_CONTENT_EVENT_ON_DETACH_FROM_WINDOW = 1 } | 定义NodeContent事件类型。  |
| [ArkUI_InspectorErrorCode](#arkui_inspectorerrorcode) { ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL = 0, ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER = -1 } | 定义Inspector错误码。  |
| [ArkUI_Alignment](#arkui_alignment) {<br/>ARKUI_ALIGNMENT_TOP_START = 0, ARKUI_ALIGNMENT_TOP, ARKUI_ALIGNMENT_TOP_END, ARKUI_ALIGNMENT_START,<br/>ARKUI_ALIGNMENT_CENTER, ARKUI_ALIGNMENT_END, ARKUI_ALIGNMENT_BOTTOM_START, ARKUI_ALIGNMENT_BOTTOM,<br/>ARKUI_ALIGNMENT_BOTTOM_END<br/>} | 定义布局对齐枚举值。  | 
| [ArkUI_ImageRepeat](#arkui_imagerepeat) { ARKUI_IMAGE_REPEAT_NONE = 0, ARKUI_IMAGE_REPEAT_X, ARKUI_IMAGE_REPEAT_Y, ARKUI_IMAGE_REPEAT_XY } | 定义图片重复铺设枚举值。  | 
| [ArkUI_FontStyle](#arkui_fontstyle) { ARKUI_FONT_STYLE_NORMAL = 0, ARKUI_FONT_STYLE_ITALIC } | 定义字体样式枚举值。  | 
| [ArkUI_FontWeight](#arkui_fontweight) {<br/>ARKUI_FONT_WEIGHT_W100 = 0, ARKUI_FONT_WEIGHT_W200, ARKUI_FONT_WEIGHT_W300, ARKUI_FONT_WEIGHT_W400,<br/>ARKUI_FONT_WEIGHT_W500, ARKUI_FONT_WEIGHT_W600, ARKUI_FONT_WEIGHT_W700, ARKUI_FONT_WEIGHT_W800,<br/>ARKUI_FONT_WEIGHT_W900, ARKUI_FONT_WEIGHT_BOLD, ARKUI_FONT_WEIGHT_NORMAL, ARKUI_FONT_WEIGHT_BOLDER,<br/>ARKUI_FONT_WEIGHT_LIGHTER, ARKUI_FONT_WEIGHT_MEDIUM, ARKUI_FONT_WEIGHT_REGULAR<br/>} | 定义字体粗细/字重枚举值。  | 
| [ArkUI_TextAlignment](#arkui_textalignment) { ARKUI_TEXT_ALIGNMENT_START = 0, ARKUI_TEXT_ALIGNMENT_CENTER, ARKUI_TEXT_ALIGNMENT_END, ARKUI_TEXT_ALIGNMENT_JUSTIFY } | 定义字体水平对齐样式枚举值。  | 
| [ArkUI_TextVerticalAlignment](#arkui_textverticalalignment) { ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE = 0, ARKUI_TEXT_VERTICAL_ALIGNMENT_BOTTOM, ARKUI_TEXT_VERTICAL_ALIGNMENT_CENTER, ARKUI_TEXT_VERTICAL_ALIGNMENT_TOP } | 定义文本垂直对齐样式枚举值。  | 
| [ArkUI_EnterKeyType](#arkui_enterkeytype) {<br/>ARKUI_ENTER_KEY_TYPE_GO = 2, ARKUI_ENTER_KEY_TYPE_SEARCH = 3, ARKUI_ENTER_KEY_TYPE_SEND, ARKUI_ENTER_KEY_TYPE_NEXT,<br/>ARKUI_ENTER_KEY_TYPE_DONE, ARKUI_ENTER_KEY_TYPE_PREVIOUS, ARKUI_ENTER_KEY_TYPE_NEW_LINE<br/>} | 定义单行文本输入法回车键类型枚举值。  | 
| [ArkUI_TextInputType](#arkui_textinputtype) {<br/>ARKUI_TEXTINPUT_TYPE_NORMAL = 0, ARKUI_TEXTINPUT_TYPE_NUMBER = 2, ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3, ARKUI_TEXTINPUT_TYPE_EMAIL = 5,<br/>ARKUI_TEXTINPUT_TYPE_PASSWORD = 7, ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8, ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9, ARKUI_TEXTINPUT_TYPE_USER_NAME = 10,<br/>ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11, ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12, ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14<br/>} | 定义单行文本输入法类型枚举值。  | 
| [ArkUI_TextAreaType](#arkui_textareatype) { ARKUI_TEXTAREA_TYPE_NORMAL = 0, ARKUI_TEXTAREA_TYPE_NUMBER = 2, ARKUI_TEXTAREA_TYPE_PHONE_NUMBER = 3, ARKUI_TEXTAREA_TYPE_EMAIL = 5, ARKUI_TEXTAREA_TYPE_ONE_TIME_CODE = 14 } | 定义多行文本输入法类型枚举值。  | 
| [ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle) { ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0, ARKUI_CANCELBUTTON_STYLE_INVISIBLE, ARKUI_CANCELBUTTON_STYLE_INPUT } | 定义清除按钮样式枚举值。  | 
| [ArkUI_XComponentType](#arkui_xcomponenttype) { ARKUI_XCOMPONENT_TYPE_SURFACE = 0, ARKUI_XCOMPONENT_TYPE_TEXTURE = 2 } | 定义XComponent类型枚举值。  | 
| [ArkUI_ProgressType](#arkui_progresstype) {<br/>ARKUI_PROGRESS_TYPE_LINEAR = 0, ARKUI_PROGRESS_TYPE_RING, ARKUI_PROGRESS_TYPE_ECLIPSE, ARKUI_PROGRESS_TYPE_SCALE_RING,<br/>ARKUI_PROGRESS_TYPE_CAPSULE<br/>} | 定义进度条类型枚举值。  | 
| [ArkUI_TextDecorationType](#arkui_textdecorationtype) { ARKUI_TEXT_DECORATION_TYPE_NONE = 0, ARKUI_TEXT_DECORATION_TYPE_UNDERLINE, ARKUI_TEXT_DECORATION_TYPE_OVERLINE, ARKUI_TEXT_DECORATION_TYPE_LINE_THROUGH } | 定义装饰线类型枚举值。  | 
| [ArkUI_TextDecorationStyle](#arkui_textdecorationstyle) {<br/>ARKUI_TEXT_DECORATION_STYLE_SOLID = 0, ARKUI_TEXT_DECORATION_STYLE_DOUBLE, ARKUI_TEXT_DECORATION_STYLE_DOTTED, ARKUI_TEXT_DECORATION_STYLE_DASHED,<br/>ARKUI_TEXT_DECORATION_STYLE_WAVY<br/>} | 定义装饰线样式枚举值。  | 
| [ArkUI_TextCase](#arkui_textcase) { ARKUI_TEXT_CASE_NORMAL = 0, ARKUI_TEXT_CASE_LOWER, ARKUI_TEXT_CASE_UPPER } | 定义文本大小写枚举值。  | 
| [ArkUI_CopyOptions](#arkui_copyoptions) { ARKUI_COPY_OPTIONS_NONE = 0, ARKUI_COPY_OPTIONS_IN_APP, ARKUI_COPY_OPTIONS_LOCAL_DEVICE, ARKUI_COPY_OPTIONS_CROSS_DEVICE } | 定义文本复制黏贴模式枚举值。  | 
| [ArkUI_ShadowType](#arkui_shadowtype) { ARKUI_SHADOW_TYPE_COLOR = 0, ARKUI_SHADOW_TYPE_BLUR } | 定义阴影类型枚举值。  | 
| [ArkUI_TextPickerRangeType](#arkui_textpickerrangetype) { ARKUI_TEXTPICKER_RANGETYPE_SINGLE = 0, ARKUI_TEXTPICKER_RANGETYPE_MULTI, ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT, ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT } | 定义滑动选择文本选择器输入类型。  | 
| [ArkUI_AccessibilityCheckedState](#arkui_accessibilitycheckedstate) { ARKUI_ACCESSIBILITY_UNCHECKED = 0, ARKUI_ACCESSIBILITY_CHECKED } | 定义无障碍复选框状态类型枚举值。  | 
| [ArkUI_AccessibilityActionType](#arkui_accessibilityactiontype) {<br/>ARKUI_ACCESSIBILITY_ACTION_CLICK = 1 &lt;&lt; 0, ARKUI_ACCESSIBILITY_ACTION_LONG_CLICK = 1 &lt;&lt; 1, ARKUI_ACCESSIBILITY_ACTION_CUT = 1 &lt;&lt; 2, ARKUI_ACCESSIBILITY_ACTION_COPY = 1 &lt;&lt; 3,<br/>ARKUI_ACCESSIBILITY_ACTION_PASTE = 1 &lt;&lt; 4<br/>} | 定义无障碍操作类型。  | 
| [ArkUI_EdgeEffect](#arkui_edgeeffect) { ARKUI_EDGE_EFFECT_SPRING = 0, ARKUI_EDGE_EFFECT_FADE, ARKUI_EDGE_EFFECT_NONE } | 定义边缘滑动效果枚举值。  | 
| [ArkUI_EffectEdge](#arkui_effectedge) { ARKUI_EFFECT_EDGE_START = 1, ARKUI_EFFECT_EDGE_END = 2 } | 定义边缘效果生效边缘的方向枚举值。  | 
| [ArkUI_ScrollDirection](#arkui_scrolldirection) { ARKUI_SCROLL_DIRECTION_VERTICAL = 0, ARKUI_SCROLL_DIRECTION_HORIZONTAL, ARKUI_SCROLL_DIRECTION_NONE = 3 } | 定义Scroll组件排列方向枚举值。  | 
| [ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign) { ARKUI_SCROLL_SNAP_ALIGN_NONE = 0, ARKUI_SCROLL_SNAP_ALIGN_START, ARKUI_SCROLL_SNAP_ALIGN_CENTER, ARKUI_SCROLL_SNAP_ALIGN_END } | 定义列表项滚动结束对齐效果枚举值。  | 
| [ArkUI_ScrollBarDisplayMode](#arkui_scrollbardisplaymode) { ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF = 0, ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO, ARKUI_SCROLL_BAR_DISPLAY_MODE_ON } | 定义滚动条状态枚举值。  | 
| [ArkUI_Axis](#arkui_axis) { ARKUI_AXIS_VERTICAL = 0, ARKUI_AXIS_HORIZONTAL } | 定义滚动方向和List组件排列方向枚举值。  | 
| [ArkUI_StickyStyle](#arkui_stickystyle) { ARKUI_STICKY_STYLE_NONE = 0, ARKUI_STICKY_STYLE_HEADER = 1, ARKUI_STICKY_STYLE_FOOTER = 2, ARKUI_STICKY_STYLE_BOTH = 3 } | 定义列表是否吸顶和吸底枚举值。  | 
| [ArkUI_BorderStyle](#arkui_borderstyle) { ARKUI_BORDER_STYLE_SOLID = 0, ARKUI_BORDER_STYLE_DASHED, ARKUI_BORDER_STYLE_DOTTED } | 边框线条样式枚举值。  | 
| [ArkUI_HitTestMode](#arkui_hittestmode) { ARKUI_HIT_TEST_MODE_DEFAULT = 0, ARKUI_HIT_TEST_MODE_BLOCK, ARKUI_HIT_TEST_MODE_TRANSPARENT, ARKUI_HIT_TEST_MODE_NONE, ARKUI_HIT_TEST_MODE_BLOCK_HIERARCHY, ARKUI_HIT_TEST_MODE_BLOCK_DESCENDANTS } | 触摸测试控制枚举值。  | 
| [ArkUI_ShadowStyle](#arkui_shadowstyle) {<br/>ARKUI_SHADOW_STYLE_OUTER_DEFAULT_XS = 0, ARKUI_SHADOW_STYLE_OUTER_DEFAULT_SM, ARKUI_SHADOW_STYLE_OUTER_DEFAULT_MD, ARKUI_SHADOW_STYLE_OUTER_DEFAULT_LG,<br/>ARKUI_SHADOW_STYLE_OUTER_FLOATING_SM, ARKUI_SHADOW_STYLE_OUTER_FLOATING_MD<br/>} | 阴影效果枚举值。  | 
| [ArkUI_AnimationCurve](#arkui_animationcurve) {<br/>ARKUI_CURVE_LINEAR = 0, ARKUI_CURVE_EASE, ARKUI_CURVE_EASE_IN, ARKUI_CURVE_EASE_OUT,<br/>ARKUI_CURVE_EASE_IN_OUT, ARKUI_CURVE_FAST_OUT_SLOW_IN, ARKUI_CURVE_LINEAR_OUT_SLOW_IN, ARKUI_CURVE_FAST_OUT_LINEAR_IN,<br/>ARKUI_CURVE_EXTREME_DECELERATION, ARKUI_CURVE_SHARP, ARKUI_CURVE_RHYTHM, ARKUI_CURVE_SMOOTH,<br/>ARKUI_CURVE_FRICTION<br/>} | 动画曲线枚举值。  | 
| [ArkUI_SwiperArrow](#arkui_swiperarrow) { ARKUI_SWIPER_ARROW_HIDE = 0, ARKUI_SWIPER_ARROW_SHOW, ARKUI_SWIPER_ARROW_SHOW_ON_HOVER } | Swiper导航点箭头枚举值。  | 
| [ArkUI_SwiperNestedScrollMode](#arkui_swipernestedscrollmode) { ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY = 0, ARKUI_SWIPER_NESTED_SRCOLL_SELF_FIRST } | Swiper组件和父组件的嵌套滚动模式。  | 
| [ArkUI_PageFlipMode](#arkui_pageflipmode) { ARKUI_PAGE_FLIP_MODE_CONTINUOUS = 0, ARKUI_PAGE_FLIP_MODE_SINGLE } | Swiper组件鼠标滚轮翻页模式。  | 
| [ArkUI_SwiperAnimationMode](#arkui_swiperanimationmode) { ARKUI_SWIPER_NO_ANIMATION = 0, ARKUI_SWIPER_DEFAULT_ANIMATION = 1, ARKUI_SWIPER_FAST_ANIMATION = 2 } | Swiper组件跳转到目标index的动画模式。  | 
| [ArkUI_AccessibilityMode](#arkui_accessibilitymode) { ARKUI_ACCESSIBILITY_MODE_AUTO = 0, ARKUI_ACCESSIBILITY_MODE_ENABLED, ARKUI_ACCESSIBILITY_MODE_DISABLED, ARKUI_ACCESSIBILITY_MODE_DISABLED_FOR_DESCENDANTS } | 定义无障碍辅助服务模式。  | 
| [ArkUI_TextCopyOptions](#arkui_textcopyoptions) { ARKUI_TEXT_COPY_OPTIONS_NONE = 0, ARKUI_TEXT_COPY_OPTIONS_IN_APP, ARKUI_TEXT_COPY_OPTIONS_LOCAL_DEVICE, ARKUI_TEXT_COPY_OPTIONS_CROSS_DEVICE } | 定义组件支持设置文本是否可复制粘贴。  | 
| [ArkUI_TextHeightAdaptivePolicy](#arkui_textheightadaptivepolicy) { ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST = 0, ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MIN_FONT_SIZE_FIRST, ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_LAYOUT_CONSTRAINT_FIRST } | 定义文本自适应高度的方式。  | 
| [ArkUI_ScrollNestedMode](#arkui_scrollnestedmode) { ARKUI_SCROLL_NESTED_MODE_SELF_ONLY = 0, ARKUI_SCROLL_NESTED_MODE_SELF_FIRST, ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST, ARKUI_SCROLL_NESTED_MODE_PARALLEL } | 定义嵌套滚动选项。  | 
| [ArkUI_ScrollEdge](#arkui_scrolledge) { ARKUI_SCROLL_EDGE_TOP = 0, ARKUI_SCROLL_EDGE_BOTTOM, ARKUI_SCROLL_EDGE_START, ARKUI_SCROLL_EDGE_END } | 定义滚动到的边缘位置。  | 
| [ArkUI_ScrollAlignment](#arkui_scrollalignment) { ARKUI_SCROLL_ALIGNMENT_START = 0, ARKUI_SCROLL_ALIGNMENT_CENTER, ARKUI_SCROLL_ALIGNMENT_END, ARKUI_SCROLL_ALIGNMENT_AUTO } | 滚动到具体item时的对齐方式。  | 
| [ArkUI_ScrollState](#arkui_scrollstate) { ARKUI_SCROLL_STATE_IDLE = 0, ARKUI_SCROLL_STATE_SCROLL, ARKUI_SCROLL_STATE_FLING } | 定义当前滚动状态。  | 
| [ArkUI_SliderBlockStyle](#arkui_sliderblockstyle) { ARKUI_SLIDER_BLOCK_STYLE_DEFAULT = 0, ARKUI_SLIDER_BLOCK_STYLE_IMAGE, ARKUI_SLIDER_BLOCK_STYLE_SHAPE } | 定义滑块形状。  | 
| [ArkUI_SliderDirection](#arkui_sliderdirection) { ARKUI_SLIDER_DIRECTION_VERTICAL = 0, ARKUI_SLIDER_DIRECTION_HORIZONTAL } | 定义滑动条滑动方向。  | 
| [ArkUI_SliderStyle](#arkui_sliderstyle) { ARKUI_SLIDER_STYLE_OUT_SET = 0, ARKUI_SLIDER_STYLE_IN_SET, ARKUI_SLIDER_STYLE_NONE } | 定义滑块与滑轨显示样式。  | 
| [ArkUI_CheckboxShape](#arkui_checkboxshape) { ArkUI_CHECKBOX_SHAPE_CIRCLE = 0, ArkUI_CHECKBOX_SHAPE_ROUNDED_SQUARE } | 定义CheckBox组件形状。  | 
| [ArkUI_AnimationPlayMode](#arkui_animationplaymode) { ARKUI_ANIMATION_PLAY_MODE_NORMAL = 0, ARKUI_ANIMATION_PLAY_MODE_REVERSE, ARKUI_ANIMATION_PLAY_MODE_ALTERNATE, ARKUI_ANIMATION_PLAY_MODE_ALTERNATE_REVERSE } | 定义动画播放模式。  | 
| [ArkUI_ImageSize](#arkui_imagesize) { ARKUI_IMAGE_SIZE_AUTO = 0, ARKUI_IMAGE_SIZE_COVER, ARKUI_IMAGE_SIZE_CONTAIN } | 定义图片宽高样式。  | 
| [ArkUI_AdaptiveColor](#arkui_adaptivecolor) { ARKUI_ADAPTIVE_COLOR_DEFAULT = 0, ARKUI_ADAPTIVE_COLOR_AVERAGE } | 定义取色模式。  | 
| [ArkUI_ColorMode](#arkui_colormode) { ARKUI_COLOR_MODE_SYSTEM = 0, ARKUI_COLOR_MODE_LIGHT, ARKUI_COLOR_MODE_DARK } | 定义深浅色模式。  | 
| [ArkUI_SystemColorMode](#arkui_systemcolormode) { ARKUI_SYSTEM_COLOR_MODE_LIGHT = 0, ARKUI_SYSTEM_COLOR_MODE_DARK } | 定义系统深浅色模式。  | 
| [ArkUI_BlurStyle](#arkui_blurstyle) {<br/>ARKUI_BLUR_STYLE_THIN = 0, ARKUI_BLUR_STYLE_REGULAR, ARKUI_BLUR_STYLE_THICK, ARKUI_BLUR_STYLE_BACKGROUND_THIN,<br/>ARKUI_BLUR_STYLE_BACKGROUND_REGULAR, ARKUI_BLUR_STYLE_BACKGROUND_THICK, ARKUI_BLUR_STYLE_BACKGROUND_ULTRA_THICK, ARKUI_BLUR_STYLE_NONE,<br/>ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THIN, ARKUI_BLUR_STYLE_COMPONENT_THIN, ARKUI_BLUR_STYLE_COMPONENT_REGULAR, ARKUI_BLUR_STYLE_COMPONENT_THICK,<br/>ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THICK<br/>} | 定义背景模糊样式。  | 
| [ArkUI_VerticalAlignment](#arkui_verticalalignment) { ARKUI_VERTICAL_ALIGNMENT_TOP = 0, ARKUI_VERTICAL_ALIGNMENT_CENTER, ARKUI_VERTICAL_ALIGNMENT_BOTTOM } | 定义垂直对齐方式。  | 
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) { ARKUI_HORIZONTAL_ALIGNMENT_START = 0, ARKUI_HORIZONTAL_ALIGNMENT_CENTER, ARKUI_HORIZONTAL_ALIGNMENT_END } | 定义语言方向对齐方式。  | 
| [ArkUI_TextOverflow](#arkui_textoverflow) { ARKUI_TEXT_OVERFLOW_NONE = 0, ARKUI_TEXT_OVERFLOW_CLIP, ARKUI_TEXT_OVERFLOW_ELLIPSIS, ARKUI_TEXT_OVERFLOW_MARQUEE } | 定义文本超长时的显示方式。  | 
| [ArkUI_ImageSpanAlignment](#arkui_imagespanalignment) { ARKUI_IMAGE_SPAN_ALIGNMENT_BASELINE = 0, ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM, ARKUI_IMAGE_SPAN_ALIGNMENT_CENTER, ARKUI_IMAGE_SPAN_ALIGNMENT_TOP, ARKUI_IMAGE_SPAN_ALIGNMENT_FOLLOW_PARAGRAPH } | 定义图片基于文本的对齐方式。  | 
| [ArkUI_ObjectFit](#arkui_objectfit) {<br/>ARKUI_OBJECT_FIT_CONTAIN = 0, ARKUI_OBJECT_FIT_COVER, ARKUI_OBJECT_FIT_AUTO, ARKUI_OBJECT_FIT_FILL,<br/>ARKUI_OBJECT_FIT_SCALE_DOWN, ARKUI_OBJECT_FIT_NONE, ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_START, ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP,<br/>ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_END, ARKUI_OBJECT_FIT_NONE_AND_ALIGN_START, ARKUI_OBJECT_FIT_NONE_AND_ALIGN_CENTER, ARKUI_OBJECT_FIT_NONE_AND_ALIGN_END,<br/>ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_START, ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM, ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_END<br/>} | 定义image填充效果。 ImageSpanAlignment  | 
| [ArkUI_ImageInterpolation](#arkui_imageinterpolation) { ARKUI_IMAGE_INTERPOLATION_NONE = 0, ARKUI_IMAGE_INTERPOLATION_LOW, ARKUI_IMAGE_INTERPOLATION_MEDIUM, ARKUI_IMAGE_INTERPOLATION_HIGH } | 定义图片插值效果。  | 
| [ArkUI_BlendMode](#arkui_blendmode) {<br/>ARKUI_BLEND_MODE_NONE = 0, ARKUI_BLEND_MODE_CLEAR, ARKUI_BLEND_MODE_SRC, ARKUI_BLEND_MODE_DST,<br/>ARKUI_BLEND_MODE_SRC_OVER, ARKUI_BLEND_MODE_DST_OVER, ARKUI_BLEND_MODE_SRC_IN, ARKUI_BLEND_MODE_DST_IN,<br/>ARKUI_BLEND_MODE_SRC_OUT, ARKUI_BLEND_MODE_DST_OUT, ARKUI_BLEND_MODE_SRC_ATOP, ARKUI_BLEND_MODE_DST_ATOP,<br/>ARKUI_BLEND_MODE_XOR, ARKUI_BLEND_MODE_PLUS, ARKUI_BLEND_MODE_MODULATE, ARKUI_BLEND_MODE_SCREEN,<br/>ARKUI_BLEND_MODE_OVERLAY, ARKUI_BLEND_MODE_DARKEN, ARKUI_BLEND_MODE_LIGHTEN, ARKUI_BLEND_MODE_COLOR_DODGE,<br/>ARKUI_BLEND_MODE_COLOR_BURN, ARKUI_BLEND_MODE_HARD_LIGHT, ARKUI_BLEND_MODE_SOFT_LIGHT, ARKUI_BLEND_MODE_DIFFERENCE,<br/>ARKUI_BLEND_MODE_EXCLUSION, ARKUI_BLEND_MODE_MULTIPLY, ARKUI_BLEND_MODE_HUE, ARKUI_BLEND_MODE_SATURATION,<br/>ARKUI_BLEND_MODE_COLOR, ARKUI_BLEND_MODE_LUMINOSITY<br/>} | 混合模式枚举值。  | 
| [ArkUI_Direction](#arkui_direction) { ARKUI_DIRECTION_LTR = 0, ARKUI_DIRECTION_RTL, ARKUI_DIRECTION_AUTO = 3 } | 设置容器元素内主轴方向上的布局枚举值。  | 
| [ArkUI_ItemAlignment](#arkui_itemalignment) {<br/>ARKUI_ITEM_ALIGNMENT_AUTO = 0, ARKUI_ITEM_ALIGNMENT_START, ARKUI_ITEM_ALIGNMENT_CENTER, ARKUI_ITEM_ALIGNMENT_END,<br/>ARKUI_ITEM_ALIGNMENT_STRETCH, ARKUI_ITEM_ALIGNMENT_BASELINE<br/>} | 设置子组件在父容器交叉轴的对齐格式枚举值。  | 
| [ArkUI_ColorStrategy](#arkui_colorstrategy) { ARKUI_COLOR_STRATEGY_INVERT = 0, ARKUI_COLOR_STRATEGY_AVERAGE, ARKUI_COLOR_STRATEGY_PRIMARY } | 前景色枚举值。  | 
| [ArkUI_FlexAlignment](#arkui_flexalignment) {<br/>ARKUI_FLEX_ALIGNMENT_START = 1, ARKUI_FLEX_ALIGNMENT_CENTER = 2, ARKUI_FLEX_ALIGNMENT_END = 3, ARKUI_FLEX_ALIGNMENT_SPACE_BETWEEN = 6,<br/>ARKUI_FLEX_ALIGNMENT_SPACE_AROUND = 7, ARKUI_FLEX_ALIGNMENT_SPACE_EVENLY = 8<br/>} | 定义垂直方向对齐方式。  | 
| [ArkUI_FlexDirection](#arkui_flexdirection) { ARKUI_FLEX_DIRECTION_ROW = 0, ARKUI_FLEX_DIRECTION_COLUMN, ARKUI_FLEX_DIRECTION_ROW_REVERSE, ARKUI_FLEX_DIRECTION_COLUMN_REVERSE } | 定义Flex容器的主轴方向。  | 
| [ArkUI_FlexWrap](#arkui_flexwrap) { ARKUI_FLEX_WRAP_NO_WRAP = 0, ARKUI_FLEX_WRAP_WRAP, ARKUI_FLEX_WRAP_WRAP_REVERSE } | 定义Flex行列布局模式模式。  | 
| [ArkUI_Visibility](#arkui_visibility) { ARKUI_VISIBILITY_VISIBLE = 0, ARKUI_VISIBILITY_HIDDEN, ARKUI_VISIBILITY_NONE } | 控制组件的显隐枚举值。  | 
| [ArkUI_CalendarAlignment](#arkui_calendaralignment) { ARKUI_CALENDAR_ALIGNMENT_START = 0, ARKUI_CALENDAR_ALIGNMENT_CENTER, ARKUI_CALENDAR_ALIGNMENT_END } | 日历选择器与入口组件对齐方式。  | 
| [ArkUI_MaskType](#arkui_masktype) {<br/>ARKUI_MASK_TYPE_RECTANGLE = 0, ARKUI_MASK_TYPE_CIRCLE, ARKUI_MASK_TYPE_ELLIPSE, ARKUI_MASK_TYPE_PATH,<br/>ARKUI_MASK_TYPE_PROGRESS<br/>} | 遮罩类型枚举。  | 
| [ArkUI_ClipType](#arkui_cliptype) { ARKUI_CLIP_TYPE_RECTANGLE = 0, ARKUI_CLIP_TYPE_CIRCLE, ARKUI_CLIP_TYPE_ELLIPSE, ARKUI_CLIP_TYPE_PATH } | 裁剪类型枚举。  | 
| [ArkUI_ShapeType](#arkui_shapetype) { ARKUI_SHAPE_TYPE_RECTANGLE = 0, ARKUI_SHAPE_TYPE_CIRCLE, ARKUI_SHAPE_TYPE_ELLIPSE, ARKUI_SHAPE_TYPE_PATH } | 自定义形状。  | 
| [ArkUI_LinearGradientDirection](#arkui_lineargradientdirection) {<br/>ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT = 0, ARKUI_LINEAR_GRADIENT_DIRECTION_TOP, ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT, ARKUI_LINEAR_GRADIENT_DIRECTION_BOTTOM,<br/>ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_TOP, ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM, ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_TOP, ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_BOTTOM,<br/>ARKUI_LINEAR_GRADIENT_DIRECTION_NONE, ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM<br/>} | 定义渐变方向结构。  | 
| [ArkUI_WordBreak](#arkui_wordbreak) { ARKUI_WORD_BREAK_NORMAL = 0, ARKUI_WORD_BREAK_BREAK_ALL, ARKUI_WORD_BREAK_BREAK_WORD, ARKUI_WORD_BREAK_HYPHENATION } | 定义文本断行规则。  | 
| [ArkUI_EllipsisMode](#arkui_ellipsismode) { ARKUI_ELLIPSIS_MODE_START = 0, ARKUI_ELLIPSIS_MODE_CENTER, ARKUI_ELLIPSIS_MODE_END } | 定义文本省略位置。  | 
| [ArkUI_ImageRenderMode](#arkui_imagerendermode) { ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0, ARKUI_IMAGE_RENDER_MODE_TEMPLATE } | 定义图片渲染模式。  | 
| [ArkUI_TransitionEdge](#arkui_transitionedge) { ARKUI_TRANSITION_EDGE_TOP = 0, ARKUI_TRANSITION_EDGE_BOTTOM, ARKUI_TRANSITION_EDGE_START, ARKUI_TRANSITION_EDGE_END } | 定义转场从边缘滑入和滑出的效果。  | 
| [ArkUI_FinishCallbackType](#arkui_finishcallbacktype) { ARKUI_FINISH_CALLBACK_REMOVED = 0, ARKUI_FINISH_CALLBACK_LOGICALLY } | 在动画中定义onFinish回调的类型。  | 
| [ArkUI_ListItemAlignment](#arkui_listitemalignment) { ARKUI_LIST_ITEM_ALIGNMENT_START = 0, ARKUI_LIST_ITEM_ALIGNMENT_CENTER, ARKUI_LIST_ITEM_ALIGNMENT_END } | 交叉轴方向的布局方式。  | 
| [ArkUI_BlendApplyType](#arkui_blendapplytype) { BLEND_APPLY_TYPE_FAST = 0, BLEND_APPLY_TYPE_OFFSCREEN } | 指定的混合模式应用于视图的内容选项.  | 
| [ArkUI_LengthMetricUnit](#arkui_lengthmetricunit) { ARKUI_LENGTH_METRIC_UNIT_DEFAULT = -1, ARKUI_LENGTH_METRIC_UNIT_PX = 0, ARKUI_LENGTH_METRIC_UNIT_VP, ARKUI_LENGTH_METRIC_UNIT_FP } | 定义组件的单位模式。  | 
| [ArkUI_TextInputContentType](#arkui_textinputcontenttype) {<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0, ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD, ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD, ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER, ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS, ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS, ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS, ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME, ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME, ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER, ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE, ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER, ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER, ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER, ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME, ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER,<br/>ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER,<br/>} | 定义自动填充类型。  | 
| [ArkUI_BarrierDirection](#arkui_barrierdirection) { ARKUI_BARRIER_DIRECTION_START = 0, ARKUI_BARRIER_DIRECTION_END, ARKUI_BARRIER_DIRECTION_TOP, ARKUI_BARRIER_DIRECTION_BOTTOM } | 定义屏障线的方向。  | 
| [ArkUI_RelativeLayoutChainStyle](#arkui_relativelayoutchainstyle) { ARKUI_RELATIVE_LAYOUT_CHAIN_STYLE_SPREAD = 0, ARKUI_RELATIVE_LAYOUT_CHAIN_STYLE_SPREAD_INSIDE, ARKUI_RELATIVE_LAYOUT_CHAIN_STYLE_PACKED } | 定义链的风格。  | 
| [ArkUI_TextInputStyle](#arkui_textinputstyle) { ARKUI_TEXTINPUT_STYLE_DEFAULT = 0, ARKUI_TEXTINPUT_STYLE_INLINE } | 定义输入框风格。  |
| [ArkUI_KeyboardAppearance](#arkui_keyboardappearance) { ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE = 0, ARKUI_KEYBOARD_APPEARANCE_IMMERSIVE = 1, ARKUI_KEYBOARD_APPEARANCE_LIGHT_IMMERSIVE = 2, ARKUI_KEYBOARD_APPEARANCE_DARK_IMMERSIVE = 3 } | 定义输入框拉起的键盘样式。  | 
| [ArkUI_TextDataDetectorType](#arkui_textdatadetectortype) { ARKUI_TEXT_DATA_DETECTOR_TYPE_PHONE_NUMBER = 0, ARKUI_TEXT_DATA_DETECTOR_TYPE_URL, ARKUI_TEXT_DATA_DETECTOR_TYPE_EMAIL, ARKUI_TEXT_DATA_DETECTOR_TYPE_ADDRESS } | 定义文本识别的实体类型。  | 
| [ArkUI_ButtonType](#arkui_buttontype) { ARKUI_BUTTON_TYPE_NORMAL = 0, ARKUI_BUTTON_TYPE_CAPSULE, ARKUI_BUTTON_TYPE_CIRCLE, ARKUI_BUTTON_ROUNDED_RECTANGLE = 8 } | 定义按钮样式枚举值。  | 
| [ArkUI_RenderFit](#arkui_renderfit) {<br/>ARKUI_RENDER_FIT_CENTER = 0, ARKUI_RENDER_FIT_TOP, ARKUI_RENDER_FIT_BOTTOM, ARKUI_RENDER_FIT_LEFT,<br/>ARKUI_RENDER_FIT_RIGHT, ARKUI_RENDER_FIT_TOP_LEFT, ARKUI_RENDER_FIT_TOP_RIGHT, ARKUI_RENDER_FIT_BOTTOM_LEFT,<br/>ARKUI_RENDER_FIT_BOTTOM_RIGHT, ARKUI_RENDER_FIT_RESIZE_FILL, ARKUI_RENDER_FIT_RESIZE_CONTAIN, ARKUI_RENDER_FIT_RESIZE_CONTAIN_TOP_LEFT,<br/>ARKUI_RENDER_FIT_RESIZE_CONTAIN_BOTTOM_RIGHT, ARKUI_RENDER_FIT_RESIZE_COVER, ARKUI_RENDER_FIT_RESIZE_COVER_TOP_LEFT, ARKUI_RENDER_FIT_RESIZE_COVER_BOTTOM_RIGHT<br/>} | 定义动画终态内容的状态。 | 
| [ArkUI_SwiperIndicatorType](#arkui_swiperindicatortype) { ARKUI_SWIPER_INDICATOR_TYPE_DOT, ARKUI_SWIPER_INDICATOR_TYPE_DIGIT } | 定义 Swiper 组件的导航指示器类型。  | 
| [ArkUI_AnimationDirection](#arkui_animationdirection) { ARKUI_ANIMATION_DIRECTION_NORMAL = 0, ARKUI_ANIMATION_DIRECTION_REVERSE, ARKUI_ANIMATION_DIRECTION_ALTERNATE, ARKUI_ANIMATION_DIRECTION_ALTERNATE_REVERSE } | 动画播放模式。  | 
| [ArkUI_SwiperDisplayModeType](#arkui_swiperdisplaymodetype) { ARKUI_SWIPER_DISPLAY_MODE_STRETCH, ARKUI_SWIPER_DISPLAY_MODE_AUTO_LINEAR } | 定义 Swiper 组件的主轴方向上元素排列的模式。  | 
| [ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate) { ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED = 0, ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_EXPANDED, ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_ACTIONING } | 定义 Listitem 组件SwipeAction方法的显隐模式。  | 
| [ArkUI_ListItemSwipeEdgeEffect](#arkui_listitemswipeedgeeffect) { ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING = 0, ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE } | 定义 Listitem 组件SwipeAction方法的滚动模式。  | 
| [ArkUI_AnimationStatus](#arkui_animationstatus) { ARKUI_ANIMATION_STATUS_INITIAL, ARKUI_ANIMATION_STATUS_RUNNING, ARKUI_ANIMATION_STATUS_PAUSED, ARKUI_ANIMATION_STATUS_STOPPED } | 定义帧动画的播放状态。  | 
| [ArkUI_AnimationFillMode](#arkui_animationfillmode) { ARKUI_ANIMATION_FILL_MODE_NONE, ARKUI_ANIMATION_FILL_MODE_FORWARDS, ARKUI_ANIMATION_FILL_MODE_BACKWARDS, ARKUI_ANIMATION_FILL_MODE_BOTH } | 定义帧动画组件在动画开始前和结束后的状态。  | 
| [ArkUI_ErrorCode](#arkui_errorcode) {<br/>ARKUI_ERROR_CODE_NO_ERROR = 0, ARKUI_ERROR_CODE_PARAM_INVALID = 401, ARKUI_ERROR_CODE_CAPI_INIT_ERROR = 500, ARKUI_ERROR_CODE_INTERNAL_ERROR = 100001,<br/>ARKUI_ERROR_CODE_XCOMPONENT_STATE_INVALID = 103501, ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED = 106102, ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED = 106103, ARKUI_ERROR_CODE_ADAPTER_NOT_BOUND = 106104,<br/>ARKUI_ERROR_CODE_ADAPTER_EXIST = 106105, ARKUI_ERROR_CODE_CHILD_NODE_EXIST = 106106, ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE = 106107, ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID = 106108,<br/>ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN = 106109, ARKUI_ERROR_CODE_NODE_INDEX_INVALID = 106200, ARKUI_ERROR_CODE_GET_INFO_FAILED = 106201, ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR = 106202,<br/>ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE = 106203, ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE = 150001, ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR = 150002, ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT = 150003,<br/>ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT = 160002, ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER = 180001, ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH = 180002, ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT = 180003,<br/>ARKUI_ERROR_CODE_POST_CLONED_COMPONENT_STATUS_ABNORMAL = 180004, ARKUI_ERROR_CODE_POST_CLONED_NO_COMPONENT_HIT_TO_RESPOND_TO_THE_EVENT = 180005, ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED = 180006,<br/>ARKUI_ERROR_CODE_INVALID_STYLED_STRING = 180101, ARKUI_ERROR_CODE_UI_CONTEXT_INVALID = 190001,<br/>ARKUI_ERROR_CODE_CALLBACK_INVALID = 190002, ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED = 180102, ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED = 190004<br/>} | 定义错误码枚举值。  | 
| [ArkUI_ScrollSource](#arkui_scrollsource) {<br/>ARKUI_SCROLL_SOURCE_DRAG = 0, ARKUI_SCROLL_SOURCE_FLING, ARKUI_SCROLL_SOURCE_EDGE_EFFECT, ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT,<br/>ARKUI_SCROLL_SOURCE_SCROLL_BAR, ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING, ARKUI_SCROLL_SOURCE_SCROLLER, ARKUI_SCROLL_SOURCE_ANIMATION<br/>} | 定义滚动来源枚举值。  | 
| [ArkUI_SafeAreaType](#arkui_safeareatype) { ARKUI_SAFE_AREA_TYPE_SYSTEM = 1, ARKUI_SAFE_AREA_TYPE_CUTOUT = 1 &lt;&lt; 1, ARKUI_SAFE_AREA_TYPE_KEYBOARD = 1 &lt;&lt; 2 } | 定义扩展安全区域的枚举值。  | 
| [ArkUI_ListItemGroupArea](#arkui_listitemgrouparea) { ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE = 0, ARKUI_LIST_ITEM_SWIPE_AREA_NONE = 1, ARKUI_LIST_ITEM_SWIPE_AREA_ITEM = 2, ARKUI_LIST_ITEM_SWIPE_AREA_HEADER = 3, ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER = 4<br/>} | 定义组件区域的枚举值。 | 
| [ArkUI_SafeAreaEdge](#arkui_safeareaedge) { ARKUI_SAFE_AREA_EDGE_TOP = 1, ARKUI_SAFE_AREA_EDGE_BOTTOM = 1 &lt;&lt; 1, ARKUI_SAFE_AREA_EDGE_START = 1 &lt;&lt; 2, ARKUI_SAFE_AREA_EDGE_END = 1 &lt;&lt; 3 } | 定义扩展安全区域的方向的枚举值。  | 
| [ArkUI_NavDestinationState](#arkui_navdestinationstate) {<br/>ARKUI_NAV_DESTINATION_STATE_ON_SHOW = 0, ARKUI_NAV_DESTINATION_STATE_ON_HIDE = 1, ARKUI_NAV_DESTINATION_STATE_ON_APPEAR = 2, ARKUI_NAV_DESTINATION_STATE_ON_DISAPPEAR = 3,<br/>ARKUI_NAV_DESTINATION_STATE_ON_WILL_SHOW = 4, ARKUI_NAV_DESTINATION_STATE_ON_WILL_HIDE = 5, ARKUI_NAV_DESTINATION_STATE_ON_WILL_APPEAR = 6, ARKUI_NAV_DESTINATION_STATE_ON_WILL_DISAPPEAR = 7,<br/>ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS = 100<br/>} | 定义NavDestination组件的状态。  |
| [ArkUI_FocusMove](#arkui_focusmove) { ARKUI_FOCUS_MOVE_FORWARD = 0, ARKUI_FOCUS_MOVE_BACKWARD, ARKUI_FOCUS_MOVE_UP, ARKUI_FOCUS_MOVE_DOWN, ARKUI_FOCUS_MOVE_LEFT, ARKUI_FOCUS_MOVE_RIGHT, } | 定义自定义走焦的按键的枚举值。  |
| [ArkUI_RouterPageState](#arkui_routerpagestate) {<br/>ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0, ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1, ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2, ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3,<br/>ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4<br/>} | 定义Router Page的状态。  |
| [ArkUI_DatePickerMode](#arkui_datepickermode) {<br/>ARKUI_DATEPICKER_MODE_DATE = 0, ARKUI_DATEPICKER_YEAR_AND_MONTH = 1, ARKUI_DATEPICKER_MONTH_AND_DAY = 2<br/> } | 定义要显示的日期选项列样式。  |
| [ArkUI_ExpandMode](#arkui_expandmode) { <br/>ARKUI_NOT_EXPAND = 0, ARKUI_EXPAND = 1, ARKUI_LAZY_EXPAND = 2 <br/>} | 定义子节点展开模式枚举值。 |
| [ArkUI_UIState](#arkui_uistate) { <br/>UI_STATE_NORMAL = 0,  UI_STATE_PRESSED = 1 << 0, UI_STATE_FOCUSED = 1 << 1, UI_STATE_DISABLED = 1 << 2, UI_STATE_SELECTED = 1 << 3 <br/>} | 组件的UI状态枚举，用于处理状态样式。 |
| [ArkUI_FocusWrapMode](#arkui_focuswrapmode) { <br/>FOCUS_WRAP_MODE_DEFAULT = 0,  FOCUS_WRAP_WITH_ARROW = 1 <br/>} | 组件走焦换行规则。<br/>**起始版本：** 20 |


### 函数

| 名称 | 描述 |
| -------- | -------- |
| [ArkUI_DragEvent](#arkui_dragevent) \* [OH_ArkUI_NodeEvent_GetDragEvent](#oh_arkui_nodeevent_getdragevent) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*nodeEvent) | 从 NodeEvent 中获取DragEvent。  |
| [ArkUI_PreDragStatus](#arkui_predragstatus) [OH_ArkUI_NodeEvent_GetPreDragStatus](#oh_arkui_nodeevent_getpredragstatus) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*nodeEvent) | 获取预览拖拽事件状态。  |
| int32_t [OH_ArkUI_DragEvent_DisableDefaultDropAnimation](#oh_arkui_dragevent_disabledefaultdropanimation) ([ArkUI_DragEvent](#arkui_dragevent) \*event, bool disable) | 设置是否禁用松手时的系统默认动效，默认不禁用，通常在应用需要自定义落位动效时配置。  |
| int32_t [OH_ArkUI_DragEvent_SetSuggestedDropOperation](#oh_arkui_dragevent_setsuggesteddropoperation) ([ArkUI_DragEvent](#arkui_dragevent) \*event, [ArkUI_DropOperation](#arkui_dropoperation) dropOperation) | 设置数据处理方式  |
| int32_t [OH_ArkUI_DragEvent_SetDragResult](#oh_arkui_dragevent_setdragresult) ([ArkUI_DragEvent](#arkui_dragevent) \*event, [ArkUI_DragResult](#arkui_dragresult) result) | 设置拖拽事件的结果。  |
| int32_t [OH_ArkUI_DragEvent_SetData](#oh_arkui_dragevent_setdata) ([ArkUI_DragEvent](#arkui_dragevent) \*event, [OH_UdmfData](#oh_udmfdata) \*data) | 向ArkUI_DragEvent中设置拖拽数据。  |
| [ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode) [OH_ArkUI_DragEvent_SetDataLoadParams](#oh_arkui_dragevent_setdataloadparams) ([ArkUI_DragEvent](#arkui_dragevent) \*dragEvent, [OH_UdmfDataLoadParams](../apis-arkdata/capi-udmf-oh-udmfdataloadparams.md) \*dataLoadParams) | 使用此方法为系统提供一个数据加载参数，而不是直接提供一个完整的数据对象。当用户拖拽到目标应用程序并落入时，系统将使用dataLoadParams请求数据。可以极大地提高拖拽大量数据的效率，以及目标应用程序中处理落入数据的效率。此方法应始终优先于[OH_ArkUI_DragEvent_SetData](#oh_arkui_dragevent_setdata)使用。[OH_UdmfDataLoadParams_Create](../apis-arkdata/capi-udmf-h.md#oh_udmfdataloadparams_create)了解如何创建和准备数据加载参数。该方法与 [OH_ArkUI_DragEvent_SetData](#oh_arkui_dragevent_setdata)存在冲突，系统始终以最后调用的方法为准。 <br/>**起始版本：** 20 |
| int32_t [OH_ArkUI_DragEvent_GetUdmfData](#oh_arkui_dragevent_getudmfdata) ([ArkUI_DragEvent](#arkui_dragevent) \*event, [OH_UdmfData](#oh_udmfdata) \*data) | 从ArkUI_DragEvent中获取拖拽默认相关数据。  |
| int32_t [OH_ArkUI_DragEvent_GetDataTypeCount](#oh_arkui_dragevent_getdatatypecount) ([ArkUI_DragEvent](#arkui_dragevent) \*event, int32_t \*count) | 从ArkUI_DragEvent中获取所拖拽的数据类型种类个数。  |
| int32_t [OH_ArkUI_DragEvent_GetDataTypes](#oh_arkui_dragevent_getdatatypes) ([ArkUI_DragEvent](#arkui_dragevent) \*event, char \*\*result[], int32_t length) | 从ArkUI_DragEvent中获取拖拽数据的类型列表。  |
| int32_t [OH_ArkUI_DragEvent_GetDragResult](#oh_arkui_dragevent_getdragresult) ([ArkUI_DragEvent](#arkui_dragevent) \*event, [ArkUI_DragResult](#arkui_dragresult) \*result) | 从ArkUI_DragEvent中获取拖拽结果。  |
| int32_t [OH_ArkUI_DragEvent_GetDropOperation](#oh_arkui_dragevent_getdropoperation) ([ArkUI_DragEvent](#arkui_dragevent) \*event, [ArkUI_DropOperation](#arkui_dropoperation) \*operation) | 从ArkUI_DragEvent中获取数据处理方式。  |
| float [OH_ArkUI_DragEvent_GetPreviewTouchPointX](#oh_arkui_dragevent_getpreviewtouchpointx) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取预览图跟手点的x轴坐标。  |
| float [OH_ArkUI_DragEvent_GetPreviewTouchPointY](#oh_arkui_dragevent_getpreviewtouchpointy) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取预览图跟手点的y轴坐标。  |
| float [OH_ArkUI_DragEvent_GetPreviewRectWidth](#oh_arkui_dragevent_getpreviewrectwidth) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取预览图的宽。  |
| float [OH_ArkUI_DragEvent_GetPreviewRectHeight](#oh_arkui_dragevent_getpreviewrectheight) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取预览图的高。  |
| float [OH_ArkUI_DragEvent_GetTouchPointXToWindow](#oh_arkui_dragevent_gettouchpointxtowindow) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取跟手点相对于window的x轴坐标。  |
| float [OH_ArkUI_DragEvent_GetTouchPointYToWindow](#oh_arkui_dragevent_gettouchpointytowindow) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取跟手点相对于window的y轴坐标。  |
| float [OH_ArkUI_DragEvent_GetTouchPointXToGlobalDisplay](#oh_arkui_dragevent_gettouchpointxtoglobaldisplay) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取跟手点相对于全局屏幕的x轴坐标。<br/>**起始版本：** 20  |
| float [OH_ArkUI_DragEvent_GetTouchPointYToGlobalDisplay](#oh_arkui_dragevent_gettouchpointytoglobaldisplay) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取跟手点相对于全局屏幕的y轴坐标。<br/>**起始版本：** 20  |
| float [OH_ArkUI_DragEvent_GetTouchPointXToDisplay](#oh_arkui_dragevent_gettouchpointxtodisplay) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取跟手点相对于当前Display的x轴坐标。  |
| float [OH_ArkUI_DragEvent_GetTouchPointYToDisplay](#oh_arkui_dragevent_gettouchpointytodisplay) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 从ArkUI_DragEvent中获取跟手点相对于当前Display的y轴坐标。  |
| float [OH_ArkUI_DragEvent_GetVelocityX](#oh_arkui_dragevent_getvelocityx) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 获取当前拖拽的x轴方向拖动速度。  |
| float [OH_ArkUI_DragEvent_GetVelocityY](#oh_arkui_dragevent_getvelocityy) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 获取当前拖拽的y轴方向拖动速度。  |
| float [OH_ArkUI_DragEvent_GetVelocity](#oh_arkui_dragevent_getvelocity) ([ArkUI_DragEvent](#arkui_dragevent) \*event) | 获取当前拖拽的主方向拖动速度。  |
| int32_t [OH_ArkUI_DragEvent_GetModifierKeyStates](#oh_arkui_dragevent_getmodifierkeystates) ([ArkUI_DragEvent](#arkui_dragevent) \*event, uint64_t \*keys) | 获取功能键按压状态。  |
| [ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode) [OH_ArkUI_DragEvent_GetDragSource](#oh_arkui_dragevent_getdragsource) ([ArkUI_DragEvent](#arkui_dragevent) \*event, char \*bundleName, int32_t length) | 获取拖拽发起方的应用包名信息，需要传递一个字符数组来接收包名字符串，并显式指明数组长度，该数组长度不小于128个字符。<br/>**起始版本：** 20 |
| [ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode) [OH_ArkUI_DragEvent_IsRemote](#oh_arkui_dragevent_isremote) ([ArkUI_DragEvent](#arkui_dragevent) \*event, bool \*isRemote) | 判断当前的拖拽操作是否是跨设备拖拽。<br/>**起始版本：** 20 |
| [ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode) [OH_ArkUI_DragEvent_GetDisplayId](#oh_arkui_dragevent_getdisplayid) ([ArkUI_DragEvent](#arkui_dragevent) \*event, int32_t \*displayId) | 获取当前拖拽事件发生时所在的屏幕ID，不支持当eventType为NODE_ON_DRAG_END时获取。<br/>**起始版本：** 20  |
| int32_t [OH_ArkUI_SetDragEventStrictReportWithNode](#oh_arkui_setdrageventstrictreportwithnode) ([ArkUI_NodeHandle](#arkui_nodehandle) node, bool enabled) | 控制是否使能严格dragEvent上报，建议开启；默认是不开启的； 当不开启时，从父组件拖移进子组件时，父组件并不会收到leave的通知；而开启之后，只要前后两个组件发生变化，上一个组件就会收到 leave，新的组件收到enter通知；该配置与具体的UI实例相关，需要通过传入一个当前UI实例上的一个具体的组件节点来关联。  |
| int32_t [OH_ArkUI_SetDragEventStrictReportWithContext](#oh_arkui_setdrageventstrictreportwithcontext) ([ArkUI_ContextHandle](#arkui_contexthandle-12) uiContext, bool enabled) | 控制是否使能严格dragEvent上报，建议开启；默认是不开启的; 当不开启时，从父组件拖移进子组件时，父组件并不会收到leave的通知；而开启之后，只要前后两个组件发生变化，上一个组件就会收到 leave，新的组件收到enter通知；该配置与具体的UI实例相关，可通过传入一个UI实例进行关联。  |
| int32_t [OH_ArkUI_SetNodeAllowedDropDataTypes](#oh_arkui_setnodealloweddropdatatypes) ([ArkUI_NodeHandle](#arkui_nodehandle) node, const char \*typesArray[], int32_t count) | 配置组件允许接受落入的数据类型，该接口会重置通过 [OH_ArkUI_DisallowNodeAnyDropDataTypes](#oh_arkui_disallownodeanydropdatatypes) 或 [OH_ArkUI_AllowNodeAllDropDataTypes](#oh_arkui_allownodealldropdatatypes)进行的配置。  |
| int32_t [OH_ArkUI_DisallowNodeAnyDropDataTypes](#oh_arkui_disallownodeanydropdatatypes) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 配置组件不允许接受任何数据类型，该接口会重置通过[OH_ArkUI_SetNodeAllowedDropDataTypes](#oh_arkui_setnodealloweddropdatatypes)配置的数据类型。  |
| int32_t [OH_ArkUI_AllowNodeAllDropDataTypes](#oh_arkui_allownodealldropdatatypes) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 配置组件允许接受任意数据类型，该接口会重置通过[OH_ArkUI_SetNodeAllowedDropDataTypes](#oh_arkui_setnodealloweddropdatatypes)配置的数据类型。  |
| int32_t [OH_ArkUI_SetNodeDraggable](#oh_arkui_setnodedraggable) ([ArkUI_NodeHandle](#arkui_nodehandle) node, bool enabled) | 设置该组件是否允许进行拖拽。  |
| int32_t [OH_ArkUI_SetNodeDragPreview](#oh_arkui_setnodedragpreview) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [OH_PixelmapNative](#oh_pixelmapnative) \*preview) | 设置组件在被拖拽时的自定义跟手图。  |
| [ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \* [OH_ArkUI_CreateDragPreviewOption](#oh_arkui_createdragpreviewoption) (void) | 构建一个ArkUI_DragPreviewOption对象。  |
| void [OH_ArkUI_DragPreviewOption_Dispose](#oh_arkui_dragpreviewoption_dispose) ([ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \*option) | 销毁跟手图自定义参数对象实例。  |
| int32_t [OH_ArkUI_DragPreviewOption_SetScaleMode](#oh_arkui_dragpreviewoption_setscalemode) ([ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \*option, [ArkUI_DragPreviewScaleMode](#arkui_dragpreviewscalemode) scaleMode) | 设置拖拽跟手图是否根据系统定义自动进行缩放。  |
| int32_t [OH_ArkUI_DragPreviewOption_SetDefaultShadowEnabled](#oh_arkui_dragpreviewoption_setdefaultshadowenabled) ([ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \*option, bool enabled) | 设置跟手图背板默认的投影效果，默认使能。  |
| int32_t [OH_ArkUI_DragPreviewOption_SetDefaultRadiusEnabled](#oh_arkui_dragpreviewoption_setdefaultradiusenabled) ([ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \*option, bool enabled) | 设置跟手图背板默认的圆角效果，默认使能。  |
| int32_t [OH_ArkUI_DragPreviewOption_SetNumberBadgeEnabled](#oh_arkui_dragpreviewoption_setnumberbadgeenabled) ([ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \*option, bool enabled) | 设置跟手图背板是否显示角标，默认使能，开启后，系统会根据拖拽数量自动进行角标显示。  |
| int32_t [OH_ArkUI_DragPreviewOption_SetBadgeNumber](#oh_arkui_dragpreviewoption_setbadgenumber) ([ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \*option, uint32_t forcedNumber) | 强制显示角标的数量，覆盖SetDragPreviewNumberBadgeEnabled设置的值。  |
| int32_t [OH_ArkUI_DragPreviewOption_SetDefaultAnimationBeforeLiftingEnabled](#oh_arkui_dragpreviewoption_setdefaultanimationbeforeliftingenabled) ([ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \*option, bool enabled) | 配置是否开启点按时的默认动画。  |
| int32_t [OH_ArkUI_SetNodeDragPreviewOption](#oh_arkui_setnodedragpreviewoption) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \*option) | 将构造的ArkUI_DragPreviewOption设置给组件。  |
| [ArkUI_DragAction](#arkui_dragaction) \* [OH_ArkUI_CreateDragActionWithNode](#oh_arkui_createdragactionwithnode) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 创建一个拖拽操作对象，该对象需与一个UI实例相关联，可通过传入一个当前UI实例的某个组件节点来指定。  |
| [ArkUI_DragAction](#arkui_dragaction) \* [OH_ArkUI_CreateDragActionWithContext](#oh_arkui_createdragactionwithcontext) ([ArkUI_ContextHandle](#arkui_contexthandle-12) uiContext) | 创建一个拖拽操作对象，该对象需与一个UI实例相关联，可通过传入一个UI实例指针来关联。  |
| void [OH_ArkUI_DragAction_Dispose](#oh_arkui_dragaction_dispose) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction) | 销毁创建的 ArkUI_DragAction 对象。  |
| int32_t [OH_ArkUI_DragAction_SetPointerId](#oh_arkui_dragaction_setpointerid) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction, int32_t pointer) | 设置手指ID，当屏幕上仅有一只手指在操作时，pointer ID 为 0；一般情况下，配置 0 即可。  |
| int32_t [OH_ArkUI_DragAction_SetPixelMaps](#oh_arkui_dragaction_setpixelmaps) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction, [OH_PixelmapNative](#oh_pixelmapnative) \*pixelmapArray[], int32_t size) | 设置拖拽跟手图，只能使用 pixelmap 格式对象。  |
| int32_t [OH_ArkUI_DragAction_SetTouchPointX](#oh_arkui_dragaction_settouchpointx) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction, float x) | 设置跟手点，相对于设置的第一个pixelmap的左上角。  |
| int32_t [OH_ArkUI_DragAction_SetTouchPointY](#oh_arkui_dragaction_settouchpointy) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction, float y) | 设置跟手点，相对于设置的第一个pixelmap的左上角。  |
| int32_t [OH_ArkUI_DragAction_SetData](#oh_arkui_dragaction_setdata) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction, [OH_UdmfData](#oh_udmfdata) \*data) | 设置拖拽数据。  |
| [ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode) [OH_ArkUI_DragAction_SetDataLoadParams](#oh_arkui_dragaction_setdataloadparams) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction, [OH_UdmfDataLoadParams](../apis-arkdata/capi-udmf-oh-udmfdataloadparams.md) \*dataLoadParams) | 使用此方法为系统提供一个数据加载参数，而不是直接提供一个完整的数据对象。当用户拖拽到目标应用程序并落入时，系统将使用dataLoadParams请求数据。可以极大地提高拖拽大量数据的效率，以及目标应用程序中处理落入数据的效率。此方法应始终优先于[OH_ArkUI_DragAction_SetData](#oh_arkui_dragaction_setdata)使用。请参阅[OH_UdmfDataLoadParams_Create](../apis-arkdata/capi-udmf-h.md#oh_udmfdataloadparams_create)了解如何创建和准备数据加载参数。该方法与[OH_ArkUI_DragAction_SetData](#oh_arkui_dragaction_setdata)存在冲突，系统始终以最后调用的方法为准。 <br/>**起始版本：** 20 |
| int32_t [OH_ArkUI_DragAction_SetDragPreviewOption](#oh_arkui_dragaction_setdragpreviewoption) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction, [ArkUI_DragPreviewOption](#arkui_dragpreviewoption) \*option) | 将构造的ArkUI_DragPreviewOption设置给ArkUI_DragAction。  |
| int32_t [OH_ArkUI_DragAction_RegisterStatusListener](#oh_arkui_dragaction_registerstatuslistener) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction, void \*userData, void(\*listener)([ArkUI_DragAndDropInfo](#arkui_draganddropinfo) \*dragAndDropInfo, void \*userData)) | 注册拖拽状态监听回调，该回调可感知到拖拽已经发起或用户松手结束的状态，可通过该监听获取到落入方对数据的接收处理是否成功。  |
| void [OH_ArkUI_DragAction_UnregisterStatusListener](#oh_arkui_dragaction_unregisterstatuslistener) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction) | 解注册拖拽状态监听回调。  |
| [ArkUI_DragStatus](#arkui_dragstatus) [OH_ArkUI_DragAndDropInfo_GetDragStatus](#oh_arkui_draganddropinfo_getdragstatus) ([ArkUI_DragAndDropInfo](#arkui_draganddropinfo) \*dragAndDropInfo) | 获取dragaction发起拖拽的状态，获取异常时返回 ArkUI_DRAG_STATUS_UNKNOWN。  |
| [ArkUI_DragEvent](#arkui_dragevent) \* [OH_ArkUI_DragAndDropInfo_GetDragEvent](#oh_arkui_draganddropinfo_getdragevent) ([ArkUI_DragAndDropInfo](#arkui_draganddropinfo) \*dragAndDropInfo) | 通过dragAndDropInfo获取到DragEvent，可通过DragEvent获取释放结果等。  |
| int32_t [OH_ArkUI_StartDrag](#oh_arkui_startdrag) ([ArkUI_DragAction](#arkui_dragaction) \*dragAction) | 通过构造的DragAction对象发起拖拽。  |
| [ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \* [OH_ArkUI_DrawableDescriptor_CreateFromPixelMap](#oh_arkui_drawabledescriptor_createfrompixelmap) ([OH_PixelmapNativeHandle](#oh_pixelmapnativehandle) pixelMap) | 使用 PixelMap 创建 DrawableDescriptor 对象。  |
| [ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \* [OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap](#oh_arkui_drawabledescriptor_createfromanimatedpixelmap) ([OH_PixelmapNativeHandle](#oh_pixelmapnativehandle) \*array, int32_t size) | 使用 PixelMap 图片数组创建DrawableDescriptor 对象。  |
| void [OH_ArkUI_DrawableDescriptor_Dispose](#oh_arkui_drawabledescriptor_dispose) ([ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*drawableDescriptor) | 销毁 DrawableDescriptor 对象指针。  |
| [OH_PixelmapNativeHandle](#oh_pixelmapnativehandle) [OH_ArkUI_DrawableDescriptor_GetStaticPixelMap](#oh_arkui_drawabledescriptor_getstaticpixelmap) ([ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*drawableDescriptor) | 获取 PixelMap 图片对象指针。  |
| [OH_PixelmapNativeHandle](#oh_pixelmapnativehandle) \* [OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray](#oh_arkui_drawabledescriptor_getanimatedpixelmaparray) ([ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*drawableDescriptor) | 获取用于播放动画的 PixelMap 图片数组数据。  |
| int32_t [OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArraySize](#oh_arkui_drawabledescriptor_getanimatedpixelmaparraysize) ([ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*drawableDescriptor) | 获取用于播放动画的 PixelMap 图片数组数据。  |
| void [OH_ArkUI_DrawableDescriptor_SetAnimationDuration](#oh_arkui_drawabledescriptor_setanimationduration) ([ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*drawableDescriptor, int32_t duration) | 设置 PixelMap 图片数组播放总时长。  |
| int32_t [OH_ArkUI_DrawableDescriptor_GetAnimationDuration](#oh_arkui_drawabledescriptor_getanimationduration) ([ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*drawableDescriptor) | 获取 PixelMap 图片数组播放总时长。  |
| void [OH_ArkUI_DrawableDescriptor_SetAnimationIteration](#oh_arkui_drawabledescriptor_setanimationiteration) ([ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*drawableDescriptor, int32_t iteration) | 设置 PixelMap 图片数组播放次数。  |
| int32_t [OH_ArkUI_DrawableDescriptor_GetAnimationIteration](#oh_arkui_drawabledescriptor_getanimationiteration) ([ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*drawableDescriptor) | 获取 PixelMap 图片数组播放次数。  |
| [ArkUI_AnimateOption](#arkui_animateoption) \* [OH_ArkUI_AnimateOption_Create](#oh_arkui_animateoption_create) () | 创建动画效果参数。  |
| void [OH_ArkUI_AnimateOption_Dispose](#oh_arkui_animateoption_dispose) ([ArkUI_AnimateOption](#arkui_animateoption) \*option) | 销毁动画效果参数指针。  |
| uint32_t [OH_ArkUI_AnimateOption_GetDuration](#oh_arkui_animateoption_getduration) ([ArkUI_AnimateOption](#arkui_animateoption) \*option) | 获取动画持续时间，单位为ms(毫秒)。  |
| float [OH_ArkUI_AnimateOption_GetTempo](#oh_arkui_animateoption_gettempo) ([ArkUI_AnimateOption](#arkui_animateoption) \*option) | 获取动画播放速度。  |
| [ArkUI_AnimationCurve](#arkui_animationcurve) [OH_ArkUI_AnimateOption_GetCurve](#oh_arkui_animateoption_getcurve) ([ArkUI_AnimateOption](#arkui_animateoption) \*option) | 获取动画曲线。  |
| int32_t [OH_ArkUI_AnimateOption_GetDelay](#oh_arkui_animateoption_getdelay) ([ArkUI_AnimateOption](#arkui_animateoption) \*option) | 获取动画延迟播放时间，单位为ms(毫秒)。  |
| int32_t [OH_ArkUI_AnimateOption_GetIterations](#oh_arkui_animateoption_getiterations) ([ArkUI_AnimateOption](#arkui_animateoption) \*option) | 获取动画播放次数。  |
| [ArkUI_AnimationPlayMode](#arkui_animationplaymode) [OH_ArkUI_AnimateOption_GetPlayMode](#oh_arkui_animateoption_getplaymode) ([ArkUI_AnimateOption](#arkui_animateoption) \*option) | 获取动画播放模式。  |
| [ArkUI_ExpectedFrameRateRange](_ark_u_i___expected_frame_rate_range.md) \* [OH_ArkUI_AnimateOption_GetExpectedFrameRateRange](#oh_arkui_animateoption_getexpectedframeraterange) ([ArkUI_AnimateOption](#arkui_animateoption) \*option) | 获取动画的期望帧率。  |
| void [OH_ArkUI_AnimateOption_SetDuration](#oh_arkui_animateoption_setduration) ([ArkUI_AnimateOption](#arkui_animateoption) \*option, int32_t value) | 设置动画持续时间。  |
| void [OH_ArkUI_AnimateOption_SetTempo](#oh_arkui_animateoption_settempo) ([ArkUI_AnimateOption](#arkui_animateoption) \*option, float value) | 设置动画播放速度。  |
| void [OH_ArkUI_AnimateOption_SetCurve](#oh_arkui_animateoption_setcurve) ([ArkUI_AnimateOption](#arkui_animateoption) \*option, [ArkUI_AnimationCurve](#arkui_animationcurve) value) | 设置动画曲线。  |
| void [OH_ArkUI_AnimateOption_SetDelay](#oh_arkui_animateoption_setdelay) ([ArkUI_AnimateOption](#arkui_animateoption) \*option, int32_t value) | 设置动画延迟播放时间。  |
| void [OH_ArkUI_AnimateOption_SetIterations](#oh_arkui_animateoption_setiterations) ([ArkUI_AnimateOption](#arkui_animateoption) \*option, int32_t value) | 设置动画播放次数。  |
| void [OH_ArkUI_AnimateOption_SetPlayMode](#oh_arkui_animateoption_setplaymode) ([ArkUI_AnimateOption](#arkui_animateoption) \*option, [ArkUI_AnimationPlayMode](#arkui_animationplaymode) value) | 设置动画播放模式。  |
| void [OH_ArkUI_AnimateOption_SetExpectedFrameRateRange](#oh_arkui_animateoption_setexpectedframeraterange) ([ArkUI_AnimateOption](#arkui_animateoption) \*option, [ArkUI_ExpectedFrameRateRange](_ark_u_i___expected_frame_rate_range.md) \*value) | 设置动画的期望帧率。  |
| void [OH_ArkUI_AnimateOption_SetICurve](#oh_arkui_animateoption_seticurve) ([ArkUI_AnimateOption](#arkui_animateoption) \*option, [ArkUI_CurveHandle](#arkui_curvehandle) value) | 设置动画的动画曲线。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_AnimateOption_GetICurve](#oh_arkui_animateoption_geticurve) ([ArkUI_AnimateOption](#arkui_animateoption) \*option) | 获取动画的动画曲线。  |
| [ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \* [OH_ArkUI_KeyframeAnimateOption_Create](#oh_arkui_keyframeanimateoption_create) (int32_t size) | 获取关键帧动画参数。  |
| void [OH_ArkUI_KeyframeAnimateOption_Dispose](#oh_arkui_keyframeanimateoption_dispose) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option) | 销毁关键帧动画参数。  |
| int32_t [OH_ArkUI_KeyframeAnimateOption_SetDelay](#oh_arkui_keyframeanimateoption_setdelay) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option, int32_t value) | 设置关键帧动画的整体延时时间，单位为ms(毫秒)，默认不延时播放。  |
| int32_t [OH_ArkUI_KeyframeAnimateOption_SetIterations](#oh_arkui_keyframeanimateoption_setiterations) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option, int32_t value) | 设置关键帧动画的动画播放次数。默认播放一次，设置为-1时表示无限次播放。设置为0时表示无动画效果。  |
| int32_t [OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback](#oh_arkui_keyframeanimateoption_registeronfinishcallback) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option, void \*userData, void(\*onFinish)(void \*userData)) | 设置关键帧动画播放完成回调。当keyframe动画所有次数播放完成后调用。  |
| int32_t [OH_ArkUI_KeyframeAnimateOption_SetDuration](#oh_arkui_keyframeanimateoption_setduration) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option, int32_t value, int32_t index) | 设置关键帧动画某段关键帧动画的持续时间，单位为毫秒。  |
| int32_t [OH_ArkUI_KeyframeAnimateOption_SetCurve](#oh_arkui_keyframeanimateoption_setcurve) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option, [ArkUI_CurveHandle](#arkui_curvehandle) value, int32_t index) | 设置关键帧动画某段关键帧使用的动画曲线。  |
| int32_t [OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback](#oh_arkui_keyframeanimateoption_registeroneventcallback) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option, void \*userData, void(\*event)(void \*userData), int32_t index) | 设置关键帧时刻状态的闭包函数，即在该关键帧时刻要达到的状态。  |
| int32_t [OH_ArkUI_KeyframeAnimateOption_GetDelay](#oh_arkui_keyframeanimateoption_getdelay) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option) | 获取关键帧整体延时时间。  |
| int32_t [OH_ArkUI_KeyframeAnimateOption_GetIterations](#oh_arkui_keyframeanimateoption_getiterations) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option) | 获取关键帧动画播放次数。  |
| int32_t [OH_ArkUI_KeyframeAnimateOption_GetDuration](#oh_arkui_keyframeanimateoption_getduration) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option, int32_t index) | 获取关键帧动画某段状态持续时间。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_KeyframeAnimateOption_GetCurve](#oh_arkui_keyframeanimateoption_getcurve) ([ArkUI_KeyframeAnimateOption](#arkui_keyframeanimateoption) \*option, int32_t index) | 获取关键帧动画某段状态动画曲线。  |
| [ArkUI_AnimatorOption](#arkui_animatoroption) \* [OH_ArkUI_AnimatorOption_Create](#oh_arkui_animatoroption_create) (int32_t keyframeSize) | 创建animator动画对象参数。  |
| void [OH_ArkUI_AnimatorOption_Dispose](#oh_arkui_animatoroption_dispose) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 销毁animator动画对象参数。  |
| int32_t [OH_ArkUI_AnimatorOption_SetDuration](#oh_arkui_animatoroption_setduration) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, int32_t value) | 设置animator动画播放的时长，单位毫秒。  |
| int32_t [OH_ArkUI_AnimatorOption_SetDelay](#oh_arkui_animatoroption_setdelay) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, int32_t value) | 设置animator动画延时播放时长，单位毫秒。  |
| int32_t [OH_ArkUI_AnimatorOption_SetIterations](#oh_arkui_animatoroption_setiterations) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, int32_t value) | 设置animator动画播放次数。设置为0时不播放，设置为-1时无限次播放。  |
| int32_t [OH_ArkUI_AnimatorOption_SetFill](#oh_arkui_animatoroption_setfill) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, [ArkUI_AnimationFillMode](#arkui_animationfillmode) value) | 设置animator动画执行后是否恢复到初始状态。  |
| int32_t [OH_ArkUI_AnimatorOption_SetDirection](#oh_arkui_animatoroption_setdirection) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, [ArkUI_AnimationDirection](#arkui_animationdirection) value) | 设置animator动画播放方向。  |
| int32_t [OH_ArkUI_AnimatorOption_SetCurve](#oh_arkui_animatoroption_setcurve) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, [ArkUI_CurveHandle](#arkui_curvehandle) value) | 设置animator动画插值曲线。  |
| int32_t [OH_ArkUI_AnimatorOption_SetBegin](#oh_arkui_animatoroption_setbegin) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, float value) | 设置animator动画插值起点。  |
| int32_t [OH_ArkUI_AnimatorOption_SetEnd](#oh_arkui_animatoroption_setend) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, float value) | 设置animator动画插值终点。  |
| int32_t [OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange](#oh_arkui_animatoroption_setexpectedframeraterange) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, [ArkUI_ExpectedFrameRateRange](_ark_u_i___expected_frame_rate_range.md) \*value) | 设置animator动画期望的帧率范围。  |
| int32_t [OH_ArkUI_AnimatorOption_SetKeyframe](#oh_arkui_animatoroption_setkeyframe) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, float time, float value, int32_t index) | 设置animator动画关键帧参数。  |
| int32_t [OH_ArkUI_AnimatorOption_SetKeyframeCurve](#oh_arkui_animatoroption_setkeyframecurve) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, [ArkUI_CurveHandle](#arkui_curvehandle) value, int32_t index) | 设置animator动画关键帧曲线类型。  |
| int32_t [OH_ArkUI_AnimatorOption_GetDuration](#oh_arkui_animatoroption_getduration) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 获取animator动画播放的时长。  |
| int32_t [OH_ArkUI_AnimatorOption_GetDelay](#oh_arkui_animatoroption_getdelay) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 获取animator动画延时播放时长。  |
| int32_t [OH_ArkUI_AnimatorOption_GetIterations](#oh_arkui_animatoroption_getiterations) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 获取animator动画播放次数。  |
| [ArkUI_AnimationFillMode](#arkui_animationfillmode) [OH_ArkUI_AnimatorOption_GetFill](#oh_arkui_animatoroption_getfill) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 获取animator动画执行后是否恢复到初始状态。  |
| [ArkUI_AnimationDirection](#arkui_animationdirection) [OH_ArkUI_AnimatorOption_GetDirection](#oh_arkui_animatoroption_getdirection) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 获取animator动画播放方向。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_AnimatorOption_GetCurve](#oh_arkui_animatoroption_getcurve) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 获取animator动画插值曲线。  |
| float [OH_ArkUI_AnimatorOption_GetBegin](#oh_arkui_animatoroption_getbegin) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 获取animator动画插值起点。  |
| float [OH_ArkUI_AnimatorOption_GetEnd](#oh_arkui_animatoroption_getend) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 获取animator动画插值终点。  |
| [ArkUI_ExpectedFrameRateRange](_ark_u_i___expected_frame_rate_range.md) \* [OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange](#oh_arkui_animatoroption_getexpectedframeraterange) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 获取animator动画期望的帧率范围。  |
| float [OH_ArkUI_AnimatorOption_GetKeyframeTime](#oh_arkui_animatoroption_getkeyframetime) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, int32_t index) | 获取animator动画关键帧时间。  |
| float [OH_ArkUI_AnimatorOption_GetKeyframeValue](#oh_arkui_animatoroption_getkeyframevalue) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, int32_t index) | 获取animator动画关键帧数值。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_AnimatorOption_GetKeyframeCurve](#oh_arkui_animatoroption_getkeyframecurve) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, int32_t index) | 获取animator动画关键帧动画插值曲线。  |
| void \* [OH_ArkUI_AnimatorEvent_GetUserData](#oh_arkui_animatorevent_getuserdata) (ArkUI_AnimatorEvent \*event) | 获取动画事件对象中的用户自定义对象。  |
| void \* [OH_ArkUI_AnimatorOnFrameEvent_GetUserData](#oh_arkui_animatoronframeevent_getuserdata) (ArkUI_AnimatorOnFrameEvent \*event) | 获取动画事件对象中的用户自定义对象。  |
| float [OH_ArkUI_AnimatorOnFrameEvent_GetValue](#oh_arkui_animatoronframeevent_getvalue) (ArkUI_AnimatorOnFrameEvent \*event) | 获取动画事件对象中的当前进度。  |
| int32_t [OH_ArkUI_AnimatorOption_RegisterOnFrameCallback](#oh_arkui_animatoroption_registeronframecallback) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, void \*userData, void(\*callback)(ArkUI_AnimatorOnFrameEvent \*event)) | 设置animator动画接收到帧时回调。  |
| int32_t [OH_ArkUI_AnimatorOption_RegisterOnFinishCallback](#oh_arkui_animatoroption_registeronfinishcallback) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, void \*userData, void(\*callback)(ArkUI_AnimatorEvent \*event)) | 设置animator动画完成时回调。  |
| int32_t [OH_ArkUI_AnimatorOption_RegisterOnCancelCallback](#oh_arkui_animatoroption_registeroncancelcallback) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, void \*userData, void(\*callback)(ArkUI_AnimatorEvent \*event)) | 设置animator动画被取消时回调。  |
| int32_t [OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback](#oh_arkui_animatoroption_registeronrepeatcallback) ([ArkUI_AnimatorOption](#arkui_animatoroption) \*option, void \*userData, void(\*callback)(ArkUI_AnimatorEvent \*event)) | 设置animator动画重复时回调。  |
| int32_t [OH_ArkUI_Animator_ResetAnimatorOption](#oh_arkui_animator_resetanimatoroption) ([ArkUI_AnimatorHandle](#arkui_animatorhandle) animatorHandle, [ArkUI_AnimatorOption](#arkui_animatoroption) \*option) | 更新animator动画。  |
| int32_t [OH_ArkUI_Animator_Play](#oh_arkui_animator_play) ([ArkUI_AnimatorHandle](#arkui_animatorhandle) animatorHandle) | 启动animator动画。  |
| int32_t [OH_ArkUI_Animator_Finish](#oh_arkui_animator_finish) ([ArkUI_AnimatorHandle](#arkui_animatorhandle) animatorHandle) | 结束animator动画。  |
| int32_t [OH_ArkUI_Animator_Pause](#oh_arkui_animator_pause) ([ArkUI_AnimatorHandle](#arkui_animatorhandle) animatorHandle) | 暂停animator动画。  |
| int32_t [OH_ArkUI_Animator_Cancel](#oh_arkui_animator_cancel) ([ArkUI_AnimatorHandle](#arkui_animatorhandle) animatorHandle) | 取消animator动画。  |
| int32_t [OH_ArkUI_Animator_Reverse](#oh_arkui_animator_reverse) ([ArkUI_AnimatorHandle](#arkui_animatorhandle) animatorHandle) | 以相反的顺序播放animator动画。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_Curve_CreateCurveByType](#oh_arkui_curve_createcurvebytype) ([ArkUI_AnimationCurve](#arkui_animationcurve) curve) | 插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_Curve_CreateStepsCurve](#oh_arkui_curve_createstepscurve) (int32_t count, bool end) | 构造阶梯曲线对象。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_Curve_CreateCubicBezierCurve](#oh_arkui_curve_createcubicbeziercurve) (float x1, float y1, float x2, float y2) | 构造三阶贝塞尔曲线对象。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_Curve_CreateSpringCurve](#oh_arkui_curve_createspringcurve) (float velocity, float mass, float stiffness, float damping) | 构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受animation、animateTo中的duration参数控制。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_Curve_CreateSpringMotion](#oh_arkui_curve_createspringmotion) (float response, float dampingFraction, float overlapDuration) | 构造弹性动画曲线对象。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_Curve_CreateResponsiveSpringMotion](#oh_arkui_curve_createresponsivespringmotion) (float response, float dampingFraction, float overlapDuration) | 构造弹性跟手动画曲线对象，是springMotion的一种特例，仅默认参数不同，可与springMotion混合使用。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_Curve_CreateInterpolatingSpring](#oh_arkui_curve_createinterpolatingspring) (float velocity, float mass, float stiffness, float damping) | 构造插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。  |
| [ArkUI_CurveHandle](#arkui_curvehandle) [OH_ArkUI_Curve_CreateCustomCurve](#oh_arkui_curve_createcustomcurve) (void \*userData, float(\*interpolate)(float fraction, void \*userdata)) | 构造自定义曲线对象。  |
| void [OH_ArkUI_Curve_DisposeCurve](#oh_arkui_curve_disposecurve) ([ArkUI_CurveHandle](#arkui_curvehandle) curveHandle) | 销毁自定义曲线对象。  |
| [ArkUI_TransitionEffect](#arkui_transitioneffect) \* [OH_ArkUI_CreateOpacityTransitionEffect](#oh_arkui_createopacitytransitioneffect) (float opacity) | 创建组件转场时的透明度效果对象。  |
| [ArkUI_TransitionEffect](#arkui_transitioneffect) \* [OH_ArkUI_CreateTranslationTransitionEffect](#oh_arkui_createtranslationtransitioneffect) ([ArkUI_TranslationOptions](_ark_u_i___translation_options.md) \*translate) | 创建组件转场时的平移效果对象。  |
| [ArkUI_TransitionEffect](#arkui_transitioneffect) \* [OH_ArkUI_CreateScaleTransitionEffect](#oh_arkui_createscaletransitioneffect) ([ArkUI_ScaleOptions](_ark_u_i___scale_options.md) \*scale) | 创建组件转场时的缩放效果对象。  |
| [ArkUI_TransitionEffect](#arkui_transitioneffect) \* [OH_ArkUI_CreateRotationTransitionEffect](#oh_arkui_createrotationtransitioneffect) ([ArkUI_RotationOptions](_ark_u_i___rotation_options.md) \*rotate) | 创建组件转场时的旋转效果对象。  |
| [ArkUI_TransitionEffect](#arkui_transitioneffect) \* [OH_ArkUI_CreateMovementTransitionEffect](#oh_arkui_createmovementtransitioneffect) ([ArkUI_TransitionEdge](#arkui_transitionedge) move) | 创建组件平移效果对象。  |
| [ArkUI_TransitionEffect](#arkui_transitioneffect) \* [OH_ArkUI_CreateAsymmetricTransitionEffect](#oh_arkui_createasymmetrictransitioneffect) ([ArkUI_TransitionEffect](#arkui_transitioneffect) \*appear, [ArkUI_TransitionEffect](#arkui_transitioneffect) \*disappear) | 创建非对称的转场效果对象。  |
| void [OH_ArkUI_TransitionEffect_Dispose](#oh_arkui_transitioneffect_dispose) ([ArkUI_TransitionEffect](#arkui_transitioneffect) \*option) | 销毁转场效果对象。  |
| int32_t [OH_ArkUI_TransitionEffect_Combine](#oh_arkui_transitioneffect_combine) ([ArkUI_TransitionEffect](#arkui_transitioneffect) \*option, [ArkUI_TransitionEffect](#arkui_transitioneffect) \*combine) | 设置转场效果链式组合，以形成包含多种转场效果的TransitionEffect。  |
| int32_t [OH_ArkUI_TransitionEffect_SetAnimation](#oh_arkui_transitioneffect_setanimation) ([ArkUI_TransitionEffect](#arkui_transitioneffect) \*option, [ArkUI_AnimateOption](#arkui_animateoption) \*animation) | 设置转场效果动画参数。  |
| void [OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss](#oh_arkui_dialogdismissevent_setshouldblockdismiss) ([ArkUI_DialogDismissEvent](#arkui_dialogdismissevent) \*event, bool shouldBlockDismiss) | 设置是否需要屏蔽系统关闭弹窗行为，true表示屏蔽系统行为不关闭弹窗，false表示不屏蔽。  |
| void \* [OH_ArkUI_DialogDismissEvent_GetUserData](#oh_arkui_dialogdismissevent_getuserdata) ([ArkUI_DialogDismissEvent](#arkui_dialogdismissevent) \*event) | 获取弹窗关闭事件对象中的用户自定义数据指针。  |
| int32_t [OH_ArkUI_DialogDismissEvent_GetDismissReason](#oh_arkui_dialogdismissevent_getdismissreason) ([ArkUI_DialogDismissEvent](#arkui_dialogdismissevent) \*event) | 获取交互式关闭事件指针中的关闭原因。  |
| int32_t [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, void (\*callback)(int32_t dialogId)) | 弹出自定义弹窗。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_UpdateDialog](#oh_arkui_customdialog_updatedialog) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, void (\*callback)(int32_t dialogId)) | 更新自定义弹窗。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_CloseDialog](#oh_arkui_customdialog_closedialog) (int32_t dialogId) | 关闭自定义弹窗。<br/>**起始版本：** 19  |
| ArkUI_CustomDialogOptions\* [OH_ArkUI_CustomDialog_CreateOptions](#oh_arkui_customdialog_createoptions) ([ArkUI_NodeHandle](#arkui_nodehandle) content) | 创建自定义弹窗options。<br/>**起始版本：** 19  |
| void [OH_ArkUI_CustomDialog_DisposeOptions](#oh_arkui_customdialog_disposeoptions) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options) | 销毁自定义弹窗options。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetLevelMode](#oh_arkui_customdialog_setlevelmode) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, [ArkUI_LevelMode](#arkui_levelmode) levelMode) | 设置弹窗的显示层级。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetLevelUniqueId](#oh_arkui_customdialog_setleveluniqueid) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, int32_t uniqueId) | 设置弹窗显示层级页面下的节点id。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetImmersiveMode](#oh_arkui_customdialog_setimmersivemode) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, [ArkUI_ImmersiveMode](#arkui_immersivemode) immersiveMode) | 设置嵌入式弹窗蒙层的显示区域。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetBackgroundColor](#oh_arkui_customdialog_setbackgroundcolor) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, uint32_t backgroundColor) | 设置弹窗的背景颜色。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetCornerRadius](#oh_arkui_customdialog_setcornerradius) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, float topLeft, float topRight, float bottomLeft, float bottomRight) | 设置弹窗的圆角半径。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetBorderWidth](#oh_arkui_customdialog_setborderwidth) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, float top, float right, float bottom, float left, [ArkUI_LengthMetricUnit](#arkui_lengthmetricunit) unit) | 设置弹窗的边框宽度。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetBorderColor](#oh_arkui_customdialog_setbordercolor) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, uint32_t top, uint32_t right, uint32_t bottom, uint32_t left) | 设置弹窗的边框颜色。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetBorderStyle](#oh_arkui_customdialog_setborderstyle) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, int32_t top, int32_t right, int32_t bottom, int32_t left) | 设置弹窗的边框样式。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetWidth](#oh_arkui_customdialog_setwidth) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, float width, [ArkUI_LengthMetricUnit](#arkui_lengthmetricunit) unit) | 设置弹窗的背板宽度。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetHeight](#oh_arkui_customdialog_setheight) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, float height, [ArkUI_LengthMetricUnit](#arkui_lengthmetricunit) unit) | 设置弹窗的背板高度。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetShadow](#oh_arkui_customdialog_setshadow) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, [ArkUI_ShadowStyle](#arkui_shadowstyle) shadow) | 设置弹窗的背板阴影。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetCustomShadow](#oh_arkui_customdialog_setcustomshadow) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, const [ArkUI_AttributeItem](_ark_u_i___attribute_item.md) \*customShadow) | 设置弹窗的自定义阴影。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetBackgroundBlurStyle](#oh_arkui_customdialog_setbackgroundblurstyle) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, [ArkUI_BlurStyle](#arkui_blurstyle) blurStyle) | 设置弹窗的背板模糊材质。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetAlignment](#oh_arkui_customdialog_setalignment) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, int32_t alignment, float offsetX, float offsetY) | 设置弹窗的对齐模式。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetModalMode](#oh_arkui_customdialog_setmodalmode) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, bool isModal) | 设置自定义弹窗是否开启模态样式的弹窗。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetAutoCancel](#oh_arkui_customdialog_setautocancel) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, bool autoCancel) | 设置自定义弹窗是否允许点击遮罩层退出。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetSubwindowMode](#oh_arkui_customdialog_setsubwindowmode) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, bool showInSubwindow) | 设置弹窗是否在子窗口显示此弹窗。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetMask](#oh_arkui_customdialog_setmask) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, uint32_t maskColor, const [ArkUI_Rect](_ark_u_i___rect.md) \*maskRect) | 设置自定义弹窗遮罩属性。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetKeyboardAvoidMode](#oh_arkui_customdialog_setkeyboardavoidmode) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, [ArkUI_KeyboardAvoidMode](_ark_u_i___native_module.md#arkui_keyboardavoidmode) keyboardAvoidMode) | 设置弹窗避让键盘的模式。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetHoverModeEnabled](#oh_arkui_customdialog_sethovermodeenabled) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, bool enabled) | 设置弹窗是否响应悬停态。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetHoverModeArea](#oh_arkui_customdialog_sethovermodearea) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, [ArkUI_HoverModeAreaType](#arkui_hovermodeareatype) hoverModeAreaType) | 设置悬停态下弹窗默认展示区域。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback](#oh_arkui_customdialog_registeronwilldismisscallback) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)([ArkUI_DialogDismissEvent](#arkui_dialogdismissevent) \*event)) | 注册系统关闭自定义弹窗的监听事件。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback](#oh_arkui_customdialog_registeronwillappearcallback) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)(void\* userData)) | 注册自定义弹窗显示动效前的监听事件。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback](#oh_arkui_customdialog_registerondidappearcallback) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)(void\* userData)) | 注册自定义弹窗弹出时的监听事件。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback](#oh_arkui_customdialog_registeronwilldisappearcallback) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)(void\* userData)) | 注册自定义弹窗退出动效前的监听事件。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback](#oh_arkui_customdialog_registerondiddisappearcallback) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)(void\* userData)) | 注册自定义弹窗消失时的监听事件。<br/>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions](#oh_arkui_customdialog_setbackgroundblurstyleoptions) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, const [ArkUI_AttributeItem](_ark_u_i___attribute_item.md) \*backgroundBlurStyleOptions) | 设置弹窗的背景模糊效果。<br>**起始版本：** 19  |
| int32_t [OH_ArkUI_CustomDialog_SetBackgroundEffect](#oh_arkui_customdialog_setbackgroundeffect) ([ArkUI_CustomDialogOptions](#arkui_customdialogoptions) \*options, const [ArkUI_AttributeItem](_ark_u_i___attribute_item.md) \*backgroundEffect) | 设置弹窗的背景效果参数。<br>**起始版本：** 19  |
| bool [OH_ArkUI_GestureInterruptInfo_GetSystemFlag](#oh_arkui_gestureinterruptinfo_getsystemflag) (const ArkUI_GestureInterruptInfo \*event) | 判断是否组件内置手势。  |
| ArkUI_GestureRecognizer \* [OH_ArkUI_GestureInterruptInfo_GetRecognizer](#oh_arkui_gestureinterruptinfo_getrecognizer) (const ArkUI_GestureInterruptInfo \*event) | 返回被打断的手势指针。  |
| ArkUI_GestureEvent \* [OH_ArkUI_GestureInterruptInfo_GetGestureEvent](#oh_arkui_gestureinterruptinfo_getgestureevent) (const ArkUI_GestureInterruptInfo \*event) | 返回打断的手势事件数据。  |
| int32_t [OH_ArkUI_GestureInterruptInfo_GetSystemRecognizerType](#oh_arkui_gestureinterruptinfo_getsystemrecognizertype) (const ArkUI_GestureInterruptInfo \*event) | 当要触发的是系统内部手势时，使用该方法可返回该系统内部手势的类型。  |
| int32_t [OH_ArkUI_GestureInterruptInfo_GetTouchRecognizers](#oh_arkui_gestureinterruptinfo_gettouchrecognizers) (const ArkUI_GestureInterruptInfo \*info, ArkUI_TouchRecognizerHandleArray\* recognizers, int32_t\* size) | 使用该方法可返回与该手势相关的所有触摸识别器。  |
| int32_t [OH_ArkUI_TouchRecognizer_GetNodeHandle](#oh_arkui_touchrecognizer_getnodehandle) (const ArkUI_TouchRecognizerHandle recognizer) | 使用该方法可返回与触摸识别器绑定的组件句柄。  |
| int32_t [OH_ArkUI_TouchRecognizer_CancelTouch](#oh_arkui_touchrecognizer_canceltouch) (ArkUI_TouchRecognizerHandle recognizer, ArkUI_GestureInterruptInfo\* info) | 使用该方法向对应触摸识别器分发Cancel事件拦截后续触摸事件。  |
| [ArkUI_GestureEventActionType](#arkui_gestureeventactiontype) [OH_ArkUI_GestureEvent_GetActionType](#oh_arkui_gestureevent_getactiontype) (const ArkUI_GestureEvent \*event) | 返回手势事件类型。  |
| const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \* [OH_ArkUI_GestureEvent_GetRawInputEvent](#oh_arkui_gestureevent_getrawinputevent) (const ArkUI_GestureEvent \*event) | 返回手势输入。  |
| int32_t [OH_ArkUI_LongPress_GetRepeatCount](#oh_arkui_longpress_getrepeatcount) (const ArkUI_GestureEvent \*event) | 返回长按手势定时触发次数。  |
| float [OH_ArkUI_PanGesture_GetVelocity](#oh_arkui_pangesture_getvelocity) (const ArkUI_GestureEvent \*event) | 滑动手势返回手势主方向速度。  |
| float [OH_ArkUI_PanGesture_GetVelocityX](#oh_arkui_pangesture_getvelocityx) (const ArkUI_GestureEvent \*event) | 滑动手势返回当前手势的x轴方向速度。  |
| float [OH_ArkUI_PanGesture_GetVelocityY](#oh_arkui_pangesture_getvelocityy) (const ArkUI_GestureEvent \*event) | 滑动手势返回当前手势的y轴方向速度。  |
| float [OH_ArkUI_PanGesture_GetOffsetX](#oh_arkui_pangesture_getoffsetx) (const ArkUI_GestureEvent \*event) | 滑动手势返回当前手势事件x轴相对偏移量。  |
| float [OH_ArkUI_PanGesture_GetOffsetY](#oh_arkui_pangesture_getoffsety) (const ArkUI_GestureEvent \*event) | 滑动手势返回当前手势事件y轴相对偏移量。  |
| float [OH_ArkUI_SwipeGesture_GetAngle](#oh_arkui_swipegesture_getangle) (const ArkUI_GestureEvent \*event) | 滑动手势返回当前手势事件角度信息。  |
| float [OH_ArkUI_SwipeGesture_GetVelocity](#oh_arkui_swipegesture_getvelocity) (const ArkUI_GestureEvent \*event) | 滑动手势场景中所有手指滑动平均速度。  |
| float [OH_ArkUI_RotationGesture_GetAngle](#oh_arkui_rotationgesture_getangle) (const ArkUI_GestureEvent \*event) | 旋转手势返回当前手势事件角度信息。  |
| float [OH_ArkUI_PinchGesture_GetScale](#oh_arkui_pinchgesture_getscale) (const ArkUI_GestureEvent \*event) | 捏合手势返回当前手势事件缩放信息。  |
| float [OH_ArkUI_PinchGesture_GetCenterX](#oh_arkui_pinchgesture_getcenterx) (const ArkUI_GestureEvent \*event) | 捏合手势中心点相对于当前组件元素左上角x轴坐标。  |
| float [OH_ArkUI_PinchGesture_GetCenterY](#oh_arkui_pinchgesture_getcentery) (const ArkUI_GestureEvent \*event) | 捏合手势中心点相对于当前组件元素左上角y轴坐标。  |
| [ArkUI_NodeHandle](#arkui_nodehandle) [OH_ArkUI_GestureEvent_GetNode](#oh_arkui_gestureevent_getnode) (const ArkUI_GestureEvent \*event) | 获取被绑定手势的ARKUI组件。  |
| int32_t [OH_ArkUI_GetResponseRecognizersFromInterruptInfo](#oh_arkui_getresponserecognizersfrominterruptinfo) (const ArkUI_GestureInterruptInfo \*event, [ArkUI_GestureRecognizerHandleArray](#arkui_gesturerecognizerhandlearray) \*responseChain, int32_t \*count) | 获取手势响应链的信息。  |
| int32_t [OH_ArkUI_SetGestureRecognizerEnabled](#oh_arkui_setgesturerecognizerenabled) (ArkUI_GestureRecognizer \*recognizer, bool enabled) | 设置手势识别器的使能状态。  |
| int32_t(\* [OH_ArkUI_SetGestureRecognizerLimitFingerCount](#oh_arkui_setgesturerecognizerlimitfingercount) )(ArkUI_GestureRecognizer \*recognizer, bool limitFingerCount) | 设置是否检查触摸屏幕的手指数量。  |
| bool [OH_ArkUI_GetGestureRecognizerEnabled](#oh_arkui_getgesturerecognizerenabled) (ArkUI_GestureRecognizer \*recognizer) | 获取手势识别器的使能状态。  |
| int32_t [OH_ArkUI_GetGestureRecognizerState](#oh_arkui_getgesturerecognizerstate) (ArkUI_GestureRecognizer \*recognizer, [ArkUI_GestureRecognizerState](#arkui_gesturerecognizerstate) \*state) | 获取手势识别器的状态。  |
| int32_t [OH_ArkUI_GetGestureEventTargetInfo](#oh_arkui_getgestureeventtargetinfo) (ArkUI_GestureRecognizer \*recognizer, [ArkUI_GestureEventTargetInfo](#arkui_gestureeventtargetinfo) \*\*info) | 获取手势事件目标信息。  |
| int32_t [OH_ArkUI_GestureEventTargetInfo_IsScrollBegin](#oh_arkui_gestureeventtargetinfo_isscrollbegin) ([ArkUI_GestureEventTargetInfo](#arkui_gestureeventtargetinfo) \*info, bool \*ret) | 当前滚动类容器组件是否在顶部。  |
| int32_t [OH_ArkUI_GestureEventTargetInfo_IsScrollEnd](#oh_arkui_gestureeventtargetinfo_isscrollend) ([ArkUI_GestureEventTargetInfo](#arkui_gestureeventtargetinfo) \*info, bool \*ret) | 当前滚动类容器组件是否在底部。  |
| int32_t [OH_ArkUI_GetPanGestureDirectionMask](#oh_arkui_getpangesturedirectionmask) (ArkUI_GestureRecognizer \*recognizer, [ArkUI_GestureDirectionMask](#arkui_gesturedirectionmask) \*directionMask) | 获取滑动手势的滑动方向。  |
| bool [OH_ArkUI_IsBuiltInGesture](#oh_arkui_isbuiltingesture) (ArkUI_GestureRecognizer \*recognizer) | 当前手势是否为系统内置手势。  |
| int32_t [OH_ArkUI_GetGestureTag](#oh_arkui_getgesturetag) (ArkUI_GestureRecognizer \*recognizer, char \*buffer, int32_t bufferSize, int32_t \*result) | 获取手势识别器的标记。  |
| int32_t [OH_ArkUI_GetGestureBindNodeId](#oh_arkui_getgesturebindnodeid) (ArkUI_GestureRecognizer \*recognizer, char \*nodeId, int32_t size, int32_t \*result) | 获取手势识别器绑定的组件的ID。  |
| bool [OH_ArkUI_IsGestureRecognizerValid](#oh_arkui_isgesturerecognizervalid) (ArkUI_GestureRecognizer \*recognizer) | 当前手势识别器是否有效。  |
| void \* [OH_ArkUI_ParallelInnerGestureEvent_GetUserData](#oh_arkui_parallelinnergestureevent_getuserdata) ([ArkUI_ParallelInnerGestureEvent](#arkui_parallelinnergestureevent) \*event) | 获取并行内部手势事件中的用户自定义数据。  |
| void* [OH_ArkUI_GestureInterrupter_GetUserData](#oh_arkui_gestureinterrupter_getuserdata) ([ArkUI_GestureInterruptInfo](#arkui_gestureinterruptinfo)* event) | 获取手势中断事件中的用户自定义数据。 |
| ArkUI_GestureRecognizer \* [OH_ArkUI_ParallelInnerGestureEvent_GetCurrentRecognizer](#oh_arkui_parallelinnergestureevent_getcurrentrecognizer) ([ArkUI_ParallelInnerGestureEvent](#arkui_parallelinnergestureevent) \*event) | 获取并行内部手势事件中的当前手势识别器。  |
| int32_t [OH_ArkUI_ParallelInnerGestureEvent_GetConflictRecognizers](#oh_arkui_parallelinnergestureevent_getconflictrecognizers) ([ArkUI_ParallelInnerGestureEvent](#arkui_parallelinnergestureevent) \*event, [ArkUI_GestureRecognizerHandleArray](#arkui_gesturerecognizerhandlearray) \*array, int32_t \*size) | 获取并行内部手势事件中的冲突的手势识别器。  |
| int32_t [OH_ArkUI_SetArkUIGestureRecognizerDisposeNotify](#oh_arkui_setarkuigesturerecognizerdisposenotify) (ArkUI_GestureRecognizer \*recognizer, [ArkUI_GestureRecognizerDisposeNotifyCallback](#arkui_gesturerecognizerdisposenotifycallback) callback, void \*userData) | 设置手势识别器对象析构通知回调函数。  |
| void \* [OH_ArkUI_QueryModuleInterfaceByName](#oh_arkui_querymoduleinterfacebyname) ([ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) type, const char \*structName) | 获取指定类型的Native模块接口集合。  |
| [ArkUI_KeyEventType](#arkui_keyeventtype) [OH_ArkUI_KeyEvent_GetType](#oh_arkui_keyevent_gettype) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event) | 获取按键的类型。  |
| int32_t [OH_ArkUI_KeyEvent_GetKeyCode](#oh_arkui_keyevent_getkeycode) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event) | 获取按键的键码。  |
| const char \* [OH_ArkUI_KeyEvent_GetKeyText](#oh_arkui_keyevent_getkeytext) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event) | 获取按键的键值。  |
| [ArkUI_KeySourceType](#arkui_keysourcetype) [OH_ArkUI_KeyEvent_GetKeySource](#oh_arkui_keyevent_getkeysource) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event) | 获取当前按键的输入设备类型。  |
| void [OH_ArkUI_KeyEvent_StopPropagation](#oh_arkui_keyevent_stoppropagation) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event, bool stopPropagation) | 阻塞事件冒泡传递。  |
| void [OH_ArkUI_KeyEvent_Dispatch](#oh_arkui_keyevent_dispatch) ([ArkUI_NodeHandle](#arkui_nodehandle) \*node, const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event) | 将按键事件分发到特定组件节点。  |
| [ArkUI_KeyIntension](#arkui_keyintension) [OH_ArkUI_KeyEvent_GetKeyIntensionCode](#oh_arkui_keyevent_getkeyintensioncode) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event) | 获取按键对应的意图。  |
| [ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode) [OH_ArkUI_KeyEvent_IsNumLockOn](_ark_u_i___native_module.md#oh_arkui_keyevent_isnumlockon) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event, bool \*state) | 获取按键事件发生时NumLock的状态。  |
| [ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode) [OH_ArkUI_KeyEvent_IsCapsLockOn](_ark_u_i___native_module.md#oh_arkui_keyevent_iscapslockon) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event, bool \*state) | 获取按键事件发生时CapsLock的状态。  |
| [ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode) [OH_ArkUI_KeyEvent_IsScrollLockOn](_ark_u_i___native_module.md#oh_arkui_keyevent_isscrolllockon) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event, bool \*state) | 获取按键事件发生时ScrollLock的状态。  |
| uint32_t [OH_ArkUI_KeyEvent_GetUnicode](#oh_arkui_keyevent_getunicode) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event) | 获取按键的unicode码值。支持范围为非空格的基本拉丁字符：0x0021-0x007E，不支持字符为0。组合键场景下，返回当前keyEvent对应按键的unicode码值。  |
| void [OH_ArkUI_KeyEvent_SetConsumed](#oh_arkui_keyevent_setconsumed) (const [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \*event, bool isConsumed) | 在按键事件回调中，设置事件是否被该回调消费  |
| [ArkUI_NodeEventType](#arkui_nodeeventtype) [OH_ArkUI_NodeEvent_GetEventType](#oh_arkui_nodeevent_geteventtype) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event) | 获取组件事件类型。  |
| int32_t [OH_ArkUI_NodeEvent_GetTargetId](#oh_arkui_nodeevent_gettargetid) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event) | 获取事件自定义标识ID。  |
| [ArkUI_NodeHandle](#arkui_nodehandle) [OH_ArkUI_NodeEvent_GetNodeHandle](#oh_arkui_nodeevent_getnodehandle) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event) | 获取触发该事件的组件对象。  |
| [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent) \* [OH_ArkUI_NodeEvent_GetInputEvent](#oh_arkui_nodeevent_getinputevent) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event) | 获取组件事件中的输入事件（如触碰事件）数据。  |
| [ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md) \* [OH_ArkUI_NodeEvent_GetNodeComponentEvent](#oh_arkui_nodeevent_getnodecomponentevent) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event) | 获取组件事件中的数字类型数据。  |
| [ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md) \* [OH_ArkUI_NodeEvent_GetStringAsyncEvent](#oh_arkui_nodeevent_getstringasyncevent) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event) | 获取组件事件中的字符串数据。  |
| void \* [OH_ArkUI_NodeEvent_GetUserData](#oh_arkui_nodeevent_getuserdata) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event) | 获取组件事件中的用户自定义数据。  |
| int32_t [OH_ArkUI_NodeEvent_GetNumberValue](#oh_arkui_nodeevent_getnumbervalue) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event, int32_t index, [ArkUI_NumberValue](union_ark_u_i___number_value.md) \*value) | 获取组件回调事件的数字类型参数。  |
| int32_t [OH_ArkUI_NodeEvent_GetStringValue](#oh_arkui_nodeevent_getstringvalue) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event, int32_t index, char \*\*string, int32_t \*stringSize) | 获取组件回调事件的字符串类型参数，字符串数据仅在事件回调过程中有效，需要在事件回调外使用建议进行额外拷贝处理。  |
| int32_t [OH_ArkUI_NodeEvent_SetReturnNumberValue](#oh_arkui_nodeevent_setreturnnumbervalue) ([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event, [ArkUI_NumberValue](union_ark_u_i___number_value.md) \*value, int32_t size) | 设置组件回调事件的返回值。  |
| [ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) [OH_ArkUI_NodeAdapter_Create](#oh_arkui_nodeadapter_create) () | 创建组件适配器对象。  |
| void [OH_ArkUI_NodeAdapter_Dispose](#oh_arkui_nodeadapter_dispose) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle) | 销毁组件适配器对象。  |
| int32_t [OH_ArkUI_NodeAdapter_SetTotalNodeCount](#oh_arkui_nodeadapter_settotalnodecount) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle, uint32_t size) | 设置Adapter中的元素总数。  |
| uint32_t [OH_ArkUI_NodeAdapter_GetTotalNodeCount](#oh_arkui_nodeadapter_gettotalnodecount) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle) | 获取Adapter中的元素总数。  |
| int32_t [OH_ArkUI_NodeAdapter_RegisterEventReceiver](#oh_arkui_nodeadapter_registereventreceiver) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle, void \*userData, void(\*receiver)([ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) \*event)) | 注册Adapter相关回调事件。  |
| void [OH_ArkUI_NodeAdapter_UnregisterEventReceiver](#oh_arkui_nodeadapter_unregistereventreceiver) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle) | 注销Adapter相关回调事件。  |
| int32_t [OH_ArkUI_NodeAdapter_ReloadAllItems](#oh_arkui_nodeadapter_reloadallitems) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle) | 通知Adapter进行全量元素变化。  |
| int32_t [OH_ArkUI_NodeAdapter_ReloadItem](#oh_arkui_nodeadapter_reloaditem) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle, uint32_t startPosition, uint32_t itemCount) | 通知Adapter进行局部元素变化。  |
| int32_t [OH_ArkUI_NodeAdapter_RemoveItem](#oh_arkui_nodeadapter_removeitem) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle, uint32_t startPosition, uint32_t itemCount) | 通知Adapter进行局部元素删除。  |
| int32_t [OH_ArkUI_NodeAdapter_InsertItem](#oh_arkui_nodeadapter_insertitem) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle, uint32_t startPosition, uint32_t itemCount) | 通知Adapter进行局部元素插入。  |
| int32_t [OH_ArkUI_NodeAdapter_MoveItem](#oh_arkui_nodeadapter_moveitem) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle, uint32_t from, uint32_t to) | 通知Adapter进行局部元素移位。  |
| int32_t [OH_ArkUI_NodeAdapter_GetAllItems](#oh_arkui_nodeadapter_getallitems) ([ArkUI_NodeAdapterHandle](#arkui_nodeadapterhandle) handle, [ArkUI_NodeHandle](#arkui_nodehandle) \*\*items, uint32_t \*size) | 获取存储在Adapter中的所有元素。  |
| void \* [OH_ArkUI_NodeAdapterEvent_GetUserData](#oh_arkui_nodeadapterevent_getuserdata) ([ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) \*event) | 获取注册事件时传入的自定义数据。  |
| [ArkUI_NodeAdapterEventType](#arkui_nodeadaptereventtype) [OH_ArkUI_NodeAdapterEvent_GetType](#oh_arkui_nodeadapterevent_gettype) ([ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) \*event) | 获取事件类型。  |
| [ArkUI_NodeHandle](#arkui_nodehandle) [OH_ArkUI_NodeAdapterEvent_GetRemovedNode](#oh_arkui_nodeadapterevent_getremovednode) ([ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) \*event) | 获取需要销毁的事件中待销毁的元素。  |
| uint32_t [OH_ArkUI_NodeAdapterEvent_GetItemIndex](#oh_arkui_nodeadapterevent_getitemindex) ([ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) \*event) | 获取适配器事件时需要操作的元素序号。  |
| [ArkUI_NodeHandle](#arkui_nodehandle) [OH_ArkUI_NodeAdapterEvent_GetHostNode](#oh_arkui_nodeadapterevent_gethostnode) ([ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) \*event) | 获取使用该适配器的滚动类容器节点。  |
| int32_t [OH_ArkUI_NodeAdapterEvent_SetItem](#oh_arkui_nodeadapterevent_setitem) ([ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) \*event, [ArkUI_NodeHandle](#arkui_nodehandle) node) | 设置需要新增到Adapter中的组件。  |
| int32_t [OH_ArkUI_NodeAdapterEvent_SetNodeId](#oh_arkui_nodeadapterevent_setnodeid) ([ArkUI_NodeAdapterEvent](#arkui_nodeadapterevent) \*event, int32_t id) | 设置生成的组件标识。  |
| [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \* [OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure](#oh_arkui_nodecustomevent_getlayoutconstraintinmeasure) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event) | 通过自定义组件事件获取测算过程中的约束尺寸。  |
| [ArkUI_IntOffset](_ark_u_i___int_offset.md) [OH_ArkUI_NodeCustomEvent_GetPositionInLayout](#oh_arkui_nodecustomevent_getpositioninlayout) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event) | 通过自定义组件事件获取在布局阶段期望自身相对父组件的位置。  |
| [ArkUI_DrawContext](#arkui_drawcontext) \* [OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw](#oh_arkui_nodecustomevent_getdrawcontextindraw) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event) | 通过自定义组件事件获取绘制上下文。  |
| int32_t [OH_ArkUI_NodeCustomEvent_GetEventTargetId](#oh_arkui_nodecustomevent_geteventtargetid) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event) | 通过自定义组件事件获取自定义事件ID。  |
| void \* [OH_ArkUI_NodeCustomEvent_GetUserData](#oh_arkui_nodecustomevent_getuserdata) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event) | 通过自定义组件事件获取自定义事件参数。  |
| [ArkUI_NodeHandle](#arkui_nodehandle) [OH_ArkUI_NodeCustomEvent_GetNodeHandle](#oh_arkui_nodecustomevent_getnodehandle) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event) | 通过自定义组件事件获取组件对象。  |
| [ArkUI_NodeCustomEventType](#arkui_nodecustomeventtype) [OH_ArkUI_NodeCustomEvent_GetEventType](#oh_arkui_nodecustomevent_geteventtype) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event) | 通过自定义组件事件获取事件类型。  |
| int32_t [OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo](#oh_arkui_nodecustomevent_getcustomspanmeasureinfo) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event, [ArkUI_CustomSpanMeasureInfo](#arkui_customspanmeasureinfo) \*info) | 通过自定义组件事件获取自定义段落组件的测量信息。  |
| int32_t [OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics](#oh_arkui_nodecustomevent_setcustomspanmetrics) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event, [ArkUI_CustomSpanMetrics](#arkui_customspanmetrics) \*metrics) | 通过自定义组件事件设置自定义段落的度量指标。  |
| int32_t [OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo](#oh_arkui_nodecustomevent_getcustomspandrawinfo) ([ArkUI_NodeCustomEvent](#arkui_nodecustomevent) \*event, [ArkUI_CustomSpanDrawInfo](#arkui_customspandrawinfo) \*info) | 通过自定义组件事件获取自定义段落组件的绘制信息。  |
| int32_t [OH_ArkUI_NodeContent_RegisterCallback](#oh_arkui_nodecontent_registercallback) ([ArkUI_NodeContentHandle](#arkui_nodecontenthandle) content, [ArkUI_NodeContentCallback](#arkui_nodecontentcallback) callback) | 注册NodeContent事件函数。  |
| [ArkUI_NodeContentEventType](#arkui_nodecontenteventtype) [OH_ArkUI_NodeContentEvent_GetEventType](#oh_arkui_nodecontentevent_geteventtype) ([ArkUI_NodeContentEvent](#arkui_nodecontentevent) \*event) | 获取触发NodeContent事件的事件类型。  |
| [ArkUI_NodeContentHandle](#arkui_nodecontenthandle) [OH_ArkUI_NodeContentEvent_GetNodeContentHandle](#oh_arkui_nodecontentevent_getnodecontenthandle) ([ArkUI_NodeContentEvent](#arkui_nodecontentevent) \*event) | 获取触发事件的NodeContent对象。  |
| int32_t [OH_ArkUI_NodeContent_SetUserData](#oh_arkui_nodecontent_setuserdata) ([ArkUI_NodeContentHandle](#arkui_nodecontenthandle) content, void \*userData) | 在NodeContent对象上保存自定义数据。  |
| void \* [OH_ArkUI_NodeContent_GetUserData](#oh_arkui_nodecontent_getuserdata) ([ArkUI_NodeContentHandle](#arkui_nodecontenthandle) content) | 获取在NodeContent对象上保存的自定义数据。  |
| int32_t [OH_ArkUI_NodeContent_AddNode](#oh_arkui_nodecontent_addnode) ([ArkUI_NodeContentHandle](#arkui_nodecontenthandle) content, [ArkUI_NodeHandle](#arkui_nodehandle) node) | 将一个ArkUI组件节点添加到对应的NodeContent对象下。  |
| int32_t [OH_ArkUI_NodeContent_RemoveNode](#oh_arkui_nodecontent_removenode) ([ArkUI_NodeContentHandle](#arkui_nodecontenthandle) content, [ArkUI_NodeHandle](#arkui_nodehandle) node) | 删除NodeContent对象下的一个ArkUI组件节点  |
| int32_t [OH_ArkUI_NodeContent_InsertNode](#oh_arkui_nodecontent_insertnode) ([ArkUI_NodeContentHandle](#arkui_nodecontenthandle) content, [ArkUI_NodeHandle](#arkui_nodehandle) node, int32_t position) | 将一个ArkUI组件节点插入到对应的NodeContent对象的特定位置下。  |
| int32_t [OH_ArkUI_NodeUtils_GetLayoutSize](#oh_arkui_nodeutils_getlayoutsize) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_IntSize](_ark_u_i___int_size.md) \*size) | 获取组件布局区域的大小。 布局区域大小不包含图形变化属性，如缩放。  |
| int32_t [OH_ArkUI_NodeUtils_GetLayoutPosition](#oh_arkui_nodeutils_getlayoutposition) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_IntOffset](_ark_u_i___int_offset.md) \*localOffset) | 获取组件布局区域相对父组件的位置。 布局区域相对位置不包含图形变化属性，如平移。  |
| int32_t [OH_ArkUI_NodeUtils_GetLayoutPositionInWindow](#oh_arkui_nodeutils_getlayoutpositioninwindow) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_IntOffset](_ark_u_i___int_offset.md) \*globalOffset) | 获取组件布局区域相对窗口的位置。 布局区域相对位置不包含图形变化属性，如平移。  |
| int32_t [OH_ArkUI_NodeUtils_GetLayoutPositionInScreen](#oh_arkui_nodeutils_getlayoutpositioninscreen) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_IntOffset](_ark_u_i___int_offset.md) \*screenOffset) | 获取组件布局区域相对屏幕的位置。 布局区域相对位置不包含图形变化属性，如平移。  |
| int32_t [OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay](#oh_arkui_nodeutils_getlayoutpositioninglobaldisplay) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_IntOffset](_ark_u_i___int_offset.md) \*offset) | 获取组件布局区域相对全局屏幕的位置。 布局区域相对位置不包含图形变化属性，如平移。  |
| int32_t [OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow](#oh_arkui_nodeutils_getpositionwithtranslateinwindow) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_IntOffset](_ark_u_i___int_offset.md) \*translateOffset) | 获取组件在窗口中的位置，包含了图形平移变化属性。  |
| int32_t [OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen](#oh_arkui_nodeutils_getpositionwithtranslateinscreen) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_IntOffset](_ark_u_i___int_offset.md) \*translateOffset) | 获取组件在屏幕中的位置，包含了图形平移变化属性。  |
| void [OH_ArkUI_NodeUtils_AddCustomProperty](#oh_arkui_nodeutils_addcustomproperty) ([ArkUI_NodeHandle](#arkui_nodehandle) node, const char \*name, const char \*value) | 设置组件的自定义属性。该接口仅在主线程生效。  |
| void [OH_ArkUI_NodeUtils_RemoveCustomProperty](#oh_arkui_nodeutils_removecustomproperty) ([ArkUI_NodeHandle](#arkui_nodehandle) node, const char \*name) | 移除组件已设置的自定义属性。  |
| int32_t [OH_ArkUI_NodeUtils_GetCustomProperty](#oh_arkui_nodeutils_getcustomproperty) ([ArkUI_NodeHandle](#arkui_nodehandle) node, const char \*name, [ArkUI_CustomProperty](#arkui_customproperty) \*\*handle) | 获取组件的自定义属性的值。  |
| [ArkUI_NodeHandle](#arkui_nodehandle) [OH_ArkUI_NodeUtils_GetParentInPageTree](#oh_arkui_nodeutils_getparentinpagetree) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 获取父节点，可获取由ArkTs创建的组件节点。  |
| int32_t [OH_ArkUI_NodeUtils_GetActiveChildrenInfo](#oh_arkui_nodeutils_getactivechildreninfo) ([ArkUI_NodeHandle](#arkui_nodehandle) head, ArkUI_ActiveChildrenInfo \*\*handle) | 获取某个节点所有活跃的子节点。Span将不会被计入子结点的统计中。  |
| [ArkUI_NodeHandle](#arkui_nodehandle) [OH_ArkUI_NodeUtils_GetCurrentPageRootNode](#oh_arkui_nodeutils_getcurrentpagerootnode) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 获取当前页面的根节点。  |
| bool [OH_ArkUI_NodeUtils_IsCreatedByNDK](#oh_arkui_nodeutils_iscreatedbyndk) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 获取组件是否由C-API创建的标签。  |
| int32_t [OH_ArkUI_NodeUtils_GetNodeType](#oh_arkui_nodeutils_getnodetype) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 获取节点的类型。  |
| int32_t [OH_ArkUI_List_CloseAllSwipeActions](#oh_arkui_list_closeallswipeactions) ([ArkUI_NodeHandle](#arkui_nodehandle) node, void \*userData, void(\*onFinish)(void \*userData)) | 收起展开状态下的ListItem。  |
| [ArkUI_ContextHandle](#arkui_contexthandle-12) [OH_ArkUI_GetContextByNode](#oh_arkui_getcontextbynode) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 获取当前节点所在页面的UI的上下文实例对象指针。  |
| int32_t [OH_ArkUI_RegisterSystemColorModeChangeEvent](#oh_arkui_registersystemcolormodechangeevent) ([ArkUI_NodeHandle](#arkui_nodehandle) node, void \*userData, void(\*onColorModeChange)([ArkUI_SystemColorMode](#arkui_systemcolormode) colorMode, void \*userData)) | 注册系统深浅色变更事件。同一组件仅能注册一个系统深浅变更回调。  |
| void [OH_ArkUI_UnregisterSystemColorModeChangeEvent](#oh_arkui_unregistersystemcolormodechangeevent) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 注销系统深浅色变更事件。  |
| int32_t [OH_ArkUI_RegisterSystemFontStyleChangeEvent](#oh_arkui_registersystemfontstylechangeevent) ([ArkUI_NodeHandle](#arkui_nodehandle) node, void \*userData, void(\*onFontStyleChange)([ArkUI_SystemFontStyleEvent](#arkui_systemfontstyleevent) \*event, void \*userData)) | 注册系统字体变更事件。同一组件仅能注册一个系统字体变更回调。  |
| void [OH_ArkUI_UnregisterSystemFontStyleChangeEvent](#oh_arkui_unregistersystemfontstylechangeevent) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 注销系统字体变更事件。  |
| float [OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale](#oh_arkui_systemfontstyleevent_getfontsizescale) (const [ArkUI_SystemFontStyleEvent](#arkui_systemfontstyleevent) \*event) | 获取系统字体变更事件的字体大小值。  |
| float [OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale](#oh_arkui_systemfontstyleevent_getfontweightscale) (const [ArkUI_SystemFontStyleEvent](#arkui_systemfontstyleevent) \*event) | 获取系统字体变更事件的字体粗细值。  |
| int32_t [OH_ArkUI_GetNodeHandleFromNapiValue](#oh_arkui_getnodehandlefromnapivalue) (napi_env env, napi_value frameNode, [ArkUI_NodeHandle](#arkui_nodehandle) \*handle) | 获取ArkTS侧创建的FrameNode节点对象映射到Native侧的ArkUI_NodeHandle。  |
| int32_t [OH_ArkUI_GetContextFromNapiValue](#oh_arkui_getcontextfromnapivalue) (napi_env env, napi_value value, [ArkUI_ContextHandle](#arkui_contexthandle-12) \*context) | 获取ArkTS侧创建的UIContext对象映射到Native侧的ArkUI_ContextHandle。  |
| int32_t [OH_ArkUI_GetNodeContentFromNapiValue](#oh_arkui_getnodecontentfromnapivalue) (napi_env env, napi_value value, [ArkUI_NodeContentHandle](#arkui_nodecontenthandle) \*content) | 获取ArkTS侧创建的NodeContent对象映射到Native侧的ArkUI_NodeContentHandle。  |
| int32_t [OH_ArkUI_GetDrawableDescriptorFromNapiValue](#oh_arkui_getdrawabledescriptorfromnapivalue) (napi_env env, napi_value value, [ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*\*drawableDescriptor) | 将ArkTS侧创建的DrawableDescriptor对象映射到Native侧的ArkUI_DrawableDescriptor。  |
| int32_t [OH_ArkUI_GetDrawableDescriptorFromResourceNapiValue](#oh_arkui_getdrawabledescriptorfromresourcenapivalue) (napi_env env, napi_value value, [ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*\*drawableDescriptor) | 将ArkTS侧创建的$r资源对象映射到Native侧的ArkUI_DrawableDescriptor。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetNavigationId](#oh_arkui_getnavigationid) ([ArkUI_NodeHandle](#arkui_nodehandle) node, char \*buffer, int32_t bufferSize, int32_t \*writeLength) | 获取当前节点所在的Navigation组件的ID。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetNavDestinationName](#oh_arkui_getnavdestinationname) ([ArkUI_NodeHandle](#arkui_nodehandle) node, char \*buffer, int32_t bufferSize, int32_t \*writeLength) | 获取当前节点所在的NavDestination组件的名称。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetNavStackLength](#oh_arkui_getnavstacklength) ([ArkUI_NodeHandle](#arkui_nodehandle) node, int32_t \*length) | 根据给定索引值，获取当前节点所在的Navigation栈的长度。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetNavDestinationNameByIndex](#oh_arkui_getnavdestinationnamebyindex) ([ArkUI_NodeHandle](#arkui_nodehandle) node, int32_t index, char \*buffer, int32_t bufferSize, int32_t \*writeLength) | 根据给定索引值，获取当前节点所在的Navigation栈中对应位置的页面名称。 索引值从0开始计数，0为栈底。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetNavDestinationId](#oh_arkui_getnavdestinationid) ([ArkUI_NodeHandle](#arkui_nodehandle) node, char \*buffer, int32_t bufferSize, int32_t \*writeLength) | 获取当前节点所在的NavDestination组件的ID。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetNavDestinationState](#oh_arkui_getnavdestinationstate) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_NavDestinationState](#arkui_navdestinationstate) \*state) | 获取当前节点所在的NavDestination组件的状态。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetNavDestinationIndex](#oh_arkui_getnavdestinationindex) ([ArkUI_NodeHandle](#arkui_nodehandle) node, int32_t \*index) | 获取当前节点所在的NavDestination组件在页面栈的索引。  |
| napi_value [OH_ArkUI_GetNavDestinationParam](#oh_arkui_getnavdestinationparam) ([ArkUI_NodeHandle](#arkui_nodehandle) node) | 获取当前节点所在的NavDestination组件的参数。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetRouterPageIndex](#oh_arkui_getrouterpageindex) ([ArkUI_NodeHandle](#arkui_nodehandle) node, int32_t \*index) | 获取当前节点所在页面在Router页面栈中的索引。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetRouterPageName](#oh_arkui_getrouterpagename) ([ArkUI_NodeHandle](#arkui_nodehandle) node, char \*buffer, int32_t bufferSize, int32_t \*writeLength) | 获取当前节点所在页面的名称。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetRouterPagePath](#oh_arkui_getrouterpagepath) ([ArkUI_NodeHandle](#arkui_nodehandle) node, char \*buffer, int32_t bufferSize, int32_t \*writeLength) | 获取当前节点所在页面的Page组件的路径。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetRouterPageState](#oh_arkui_getrouterpagestate) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_RouterPageState](#arkui_routerpagestate) \*state) | 获取当前节点所在页面的Page组件的状态。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_GetRouterPageId](#oh_arkui_getrouterpageid) ([ArkUI_NodeHandle](#arkui_nodehandle) node, char \*buffer, int32_t bufferSize, int32_t \*writeLength) | 获取当前节点所在页面的Page组件的ID。  |
| [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \* [OH_ArkUI_LayoutConstraint_Create](#oh_arkui_layoutconstraint_create) () | 创建约束尺寸。  |
| [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \* [OH_ArkUI_LayoutConstraint_Copy](#oh_arkui_layoutconstraint_copy) (const [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint) | 约束尺寸深拷贝。  |
| void \* [OH_ArkUI_LayoutConstraint_Dispose](#oh_arkui_layoutconstraint_dispose) ([ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint) | 销毁约束尺寸指针。  |
| int32_t [OH_ArkUI_LayoutConstraint_GetMaxWidth](#oh_arkui_layoutconstraint_getmaxwidth) (const [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint) | 通过约束尺寸获取最大宽度，单位为px。  |
| int32_t [OH_ArkUI_LayoutConstraint_GetMinWidth](#oh_arkui_layoutconstraint_getminwidth) (const [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint) | 通过约束尺寸获取最小宽度，单位为px。  |
| int32_t [OH_ArkUI_LayoutConstraint_GetMaxHeight](#oh_arkui_layoutconstraint_getmaxheight) (const [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint) | 通过约束尺寸获取最大高度，单位为px。  |
| int32_t [OH_ArkUI_LayoutConstraint_GetMinHeight](#oh_arkui_layoutconstraint_getminheight) (const [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint) | 通过约束尺寸获取最小高度，单位为px。  |
| int32_t [OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth](#oh_arkui_layoutconstraint_getpercentreferencewidth) (const [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint) | 通过约束尺寸获取宽度百分比基准，单位为px。  |
| int32_t [OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight](#oh_arkui_layoutconstraint_getpercentreferenceheight) (const [ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint) | 通过约束尺寸获取高度百分比基准，单位为px。  |
| void [OH_ArkUI_LayoutConstraint_SetMaxWidth](#oh_arkui_layoutconstraint_setmaxwidth) ([ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint, int32_t value) | 设置最大宽度。  |
| void [OH_ArkUI_LayoutConstraint_SetMinWidth](#oh_arkui_layoutconstraint_setminwidth) ([ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint, int32_t value) | 设置最小宽度。  |
| void [OH_ArkUI_LayoutConstraint_SetMaxHeight](#oh_arkui_layoutconstraint_setmaxheight) ([ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint, int32_t value) | 设置最大高度。  |
| void [OH_ArkUI_LayoutConstraint_SetMinHeight](#oh_arkui_layoutconstraint_setminheight) ([ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint, int32_t value) | 设置最小高度。  |
| void [OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth](#oh_arkui_layoutconstraint_setpercentreferencewidth) ([ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint, int32_t value) | 设置宽度百分比基准。  |
| void [OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight](#oh_arkui_layoutconstraint_setpercentreferenceheight) ([ArkUI_LayoutConstraint](#arkui_layoutconstraint) \*Constraint, int32_t value) | 设置高度百分比基准。  |
| void \* [OH_ArkUI_DrawContext_GetCanvas](#oh_arkui_drawcontext_getcanvas) ([ArkUI_DrawContext](#arkui_drawcontext) \*context) | 获取绘制canvas指针，可以转换为图形库的OH_Drawing_Canvas指针进行绘制。  |
| [ArkUI_IntSize](_ark_u_i___int_size.md) [OH_ArkUI_DrawContext_GetSize](#oh_arkui_drawcontext_getsize) ([ArkUI_DrawContext](#arkui_drawcontext) \*context) | 获取可绘制区域大小。  |
| [ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \* [OH_ArkUI_WaterFlowSectionOption_Create](#oh_arkui_waterflowsectionoption_create) () | 创建FlowItem分组配置信息。  |
| void [OH_ArkUI_WaterFlowSectionOption_Dispose](#oh_arkui_waterflowsectionoption_dispose) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option) | 销毁FlowItem分组配置信息指针。  |
| void [OH_ArkUI_WaterFlowSectionOption_SetSize](#oh_arkui_waterflowsectionoption_setsize) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t size) | 设置FlowItem分组配置信息数组长度。  |
| int32_t [OH_ArkUI_WaterFlowSectionOption_GetSize](#oh_arkui_waterflowsectionoption_getsize) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option) | 获取FlowItem分组配置信息数组长度。  |
| void [OH_ArkUI_WaterFlowSectionOption_SetItemCount](#oh_arkui_waterflowsectionoption_setitemcount) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index, int32_t itemCount) | 设置分组中FlowItem数量。  |
| int32_t [OH_ArkUI_WaterFlowSectionOption_GetItemCount](#oh_arkui_waterflowsectionoption_getitemcount) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index) | 通过FlowItem分组配置信息获取对应索引下的FlowItem数量。  |
| void [OH_ArkUI_WaterFlowSectionOption_SetCrossCount](#oh_arkui_waterflowsectionoption_setcrosscount) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index, int32_t crossCount) | 设置布局栅格，纵向布局时为列数，横向布局时为行数。  |
| int32_t [OH_ArkUI_WaterFlowSectionOption_GetCrossCount](#oh_arkui_waterflowsectionoption_getcrosscount) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index) | 通过FlowItem分组配置信息获取对应索引下的布局栅格数。  |
| void [OH_ArkUI_WaterFlowSectionOption_SetColumnGap](#oh_arkui_waterflowsectionoption_setcolumngap) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index, float columnGap) | 设置分组的列间距。  |
| float [OH_ArkUI_WaterFlowSectionOption_GetColumnGap](#oh_arkui_waterflowsectionoption_getcolumngap) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index) | 通过FlowItem分组配置信息获取对应索引下的分组的列间距。  |
| void [OH_ArkUI_WaterFlowSectionOption_SetRowGap](#oh_arkui_waterflowsectionoption_setrowgap) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index, float rowGap) | 设置分组的行间距。  |
| float [OH_ArkUI_WaterFlowSectionOption_GetRowGap](#oh_arkui_waterflowsectionoption_getrowgap) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index) | 通过FlowItem分组配置信息获取对应索引下的分组的行间距。  |
| void [OH_ArkUI_WaterFlowSectionOption_SetMargin](#oh_arkui_waterflowsectionoption_setmargin) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index, float marginTop, float marginRight, float marginBottom, float marginLeft) | 设置分组的外边距。  |
| [ArkUI_Margin](_ark_u_i___margin.md) [OH_ArkUI_WaterFlowSectionOption_GetMargin](#oh_arkui_waterflowsectionoption_getmargin) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index) | 通过FlowItem分组配置信息获取对应索引下的分组的外边距。  |
| void [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index, float(\*callback)(int32_t itemIndex)) | 通过FlowItem分组配置信息根据flowItemIndex获取指定Item的主轴大小。  |
| void [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata) ([ArkUI_WaterFlowSectionOption](#arkui_waterflowsectionoption) \*option, int32_t index, void \*userData, float(\*callback)(int32_t itemIndex, void \*userData)) | 通过FlowItem分组配置信息根据flowItemIndex获取指定Item的主轴大小。  |
| [ArkUI_GuidelineOption](#arkui_guidelineoption) \* [OH_ArkUI_GuidelineOption_Create](#oh_arkui_guidelineoption_create) (int32_t size) | 创建RelativeContaine容器内的辅助线信息。  |
| void [OH_ArkUI_GuidelineOption_Dispose](#oh_arkui_guidelineoption_dispose) ([ArkUI_GuidelineOption](#arkui_guidelineoption) \*guideline) | 销毁辅助线信息。  |
| void [OH_ArkUI_GuidelineOption_SetId](#oh_arkui_guidelineoption_setid) ([ArkUI_GuidelineOption](#arkui_guidelineoption) \*guideline, const char \*value, int32_t index) | 设置辅助线的Id。  |
| void [OH_ArkUI_GuidelineOption_SetDirection](#oh_arkui_guidelineoption_setdirection) ([ArkUI_GuidelineOption](#arkui_guidelineoption) \*guideline, [ArkUI_Axis](#arkui_axis) value, int32_t index) | 设置辅助线的方向。  |
| void [OH_ArkUI_GuidelineOption_SetPositionStart](#oh_arkui_guidelineoption_setpositionstart) ([ArkUI_GuidelineOption](#arkui_guidelineoption) \*guideline, float value, int32_t index) | 设置距离容器左侧或者顶部的距离。  |
| void [OH_ArkUI_GuidelineOption_SetPositionEnd](#oh_arkui_guidelineoption_setpositionend) ([ArkUI_GuidelineOption](#arkui_guidelineoption) \*guideline, float value, int32_t index) | 设置距离容器右侧或者底部的距离。  |
| const char \* [OH_ArkUI_GuidelineOption_GetId](#oh_arkui_guidelineoption_getid) ([ArkUI_GuidelineOption](#arkui_guidelineoption) \*guideline, int32_t index) | 获取辅助线的Id。  |
| [ArkUI_Axis](#arkui_axis) [OH_ArkUI_GuidelineOption_GetDirection](#oh_arkui_guidelineoption_getdirection) ([ArkUI_GuidelineOption](#arkui_guidelineoption) \*guideline, int32_t index) | 获取辅助线的方向。  |
| float [OH_ArkUI_GuidelineOption_GetPositionStart](#oh_arkui_guidelineoption_getpositionstart) ([ArkUI_GuidelineOption](#arkui_guidelineoption) \*guideline, int32_t index) | 获取距离容器左侧或者顶部的距离。  |
| float [OH_ArkUI_GuidelineOption_GetPositionEnd](#oh_arkui_guidelineoption_getpositionend) ([ArkUI_GuidelineOption](#arkui_guidelineoption) \*guideline, int32_t index) | 获取距离容器右侧或者底部的距离。  |
| [ArkUI_BarrierOption](#arkui_barrieroption) \* [OH_ArkUI_BarrierOption_Create](#oh_arkui_barrieroption_create) (int32_t size) | 创建RelativeContaine容器内的屏障信息。  |
| void [OH_ArkUI_BarrierOption_Dispose](#oh_arkui_barrieroption_dispose) ([ArkUI_BarrierOption](#arkui_barrieroption) \*barrierStyle) | 销毁屏障信息。  |
| void [OH_ArkUI_BarrierOption_SetId](#oh_arkui_barrieroption_setid) ([ArkUI_BarrierOption](#arkui_barrieroption) \*barrierStyle, const char \*value, int32_t index) | 设置屏障的Id。  |
| void [OH_ArkUI_BarrierOption_SetDirection](#oh_arkui_barrieroption_setdirection) ([ArkUI_BarrierOption](#arkui_barrieroption) \*barrierStyle, [ArkUI_BarrierDirection](#arkui_barrierdirection) value, int32_t index) | 设置屏障的方向。  |
| void [OH_ArkUI_BarrierOption_SetReferencedId](#oh_arkui_barrieroption_setreferencedid) ([ArkUI_BarrierOption](#arkui_barrieroption) \*barrierStyle, const char \*value, int32_t index) | 设置屏障的依赖的组件。  |
| const char \* [OH_ArkUI_BarrierOption_GetId](#oh_arkui_barrieroption_getid) ([ArkUI_BarrierOption](#arkui_barrieroption) \*barrierStyle, int32_t index) | 获取屏障的Id。  |
| [ArkUI_BarrierDirection](#arkui_barrierdirection) [OH_ArkUI_BarrierOption_GetDirection](#oh_arkui_barrieroption_getdirection) ([ArkUI_BarrierOption](#arkui_barrieroption) \*barrierStyle, int32_t index) | 获取屏障的方向。  |
| const char \* [OH_ArkUI_BarrierOption_GetReferencedId](#oh_arkui_barrieroption_getreferencedid) ([ArkUI_BarrierOption](#arkui_barrieroption) \*barrierStyle, int32_t index, int32_t referencedIndex) | 获取屏障的依赖的组件。  |
| int32_t [OH_ArkUI_BarrierOption_GetReferencedIdSize](#oh_arkui_barrieroption_getreferencedidsize) ([ArkUI_BarrierOption](#arkui_barrieroption) \*barrierStyle, int32_t index) | 获取屏障的依赖的组件的个数。  |
| [ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \* [OH_ArkUI_AlignmentRuleOption_Create](#oh_arkui_alignmentruleoption_create) () | 创建相对容器中子组件的对齐规则信息。  |
| void [OH_ArkUI_AlignmentRuleOption_Dispose](#oh_arkui_alignmentruleoption_dispose) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 销毁相对容器中子组件的对齐规则信息。  |
| void [OH_ArkUI_AlignmentRuleOption_SetStart](#oh_arkui_alignmentruleoption_setstart) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option, const char \*id, [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) alignment) | 设置左对齐参数。  |
| void [OH_ArkUI_AlignmentRuleOption_SetEnd](#oh_arkui_alignmentruleoption_setend) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option, const char \*id, [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) alignment) | 设置右对齐参数。  |
| void [OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal](#oh_arkui_alignmentruleoption_setcenterhorizontal) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option, const char \*id, [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) alignment) | 设置横向居中对齐方式的参数。  |
| void [OH_ArkUI_AlignmentRuleOption_SetTop](#oh_arkui_alignmentruleoption_settop) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option, const char \*id, [ArkUI_VerticalAlignment](#arkui_verticalalignment) alignment) | 设置顶部对齐的参数。  |
| void [OH_ArkUI_AlignmentRuleOption_SetBottom](#oh_arkui_alignmentruleoption_setbottom) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option, const char \*id, [ArkUI_VerticalAlignment](#arkui_verticalalignment) alignment) | 设置底部对齐的参数。  |
| void [OH_ArkUI_AlignmentRuleOption_SetCenterVertical](#oh_arkui_alignmentruleoption_setcentervertical) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option, const char \*id, [ArkUI_VerticalAlignment](#arkui_verticalalignment) alignment) | 设置纵向居中对齐方式的参数。  |
| void [OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal](#oh_arkui_alignmentruleoption_setbiashorizontal) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option, float horizontal) | 设置组件在锚点约束下的水平方向上偏移参数。  |
| void [OH_ArkUI_AlignmentRuleOption_SetBiasVertical](#oh_arkui_alignmentruleoption_setbiasvertical) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option, float vertical) | 设置组件在锚点约束下的垂直方向上偏移参数。  |
| const char \* [OH_ArkUI_AlignmentRuleOption_GetStartId](#oh_arkui_alignmentruleoption_getstartid) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取左对齐参数的Id。  |
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) [OH_ArkUI_AlignmentRuleOption_GetStartAlignment](#oh_arkui_alignmentruleoption_getstartalignment) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取左对齐参数的对齐方式。  |
| const char \* [OH_ArkUI_AlignmentRuleOption_GetEndId](#oh_arkui_alignmentruleoption_getendid) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取右对齐参数。  |
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) [OH_ArkUI_AlignmentRuleOption_GetEndAlignment](#oh_arkui_alignmentruleoption_getendalignment) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取右对齐参数。  |
| const char \* [OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal](#oh_arkui_alignmentruleoption_getcenteridhorizontal) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取横向居中对齐方式的参数。  |
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) [OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal](#oh_arkui_alignmentruleoption_getcenteralignmenthorizontal) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取横向居中对齐方式的参数。  |
| const char \* [OH_ArkUI_AlignmentRuleOption_GetTopId](#oh_arkui_alignmentruleoption_gettopid) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取顶部对齐的参数。  |
| [ArkUI_VerticalAlignment](#arkui_verticalalignment) [OH_ArkUI_AlignmentRuleOption_GetTopAlignment](#oh_arkui_alignmentruleoption_gettopalignment) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取顶部对齐的参数。  |
| const char \* [OH_ArkUI_AlignmentRuleOption_GetBottomId](#oh_arkui_alignmentruleoption_getbottomid) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取底部对齐的参数。  |
| [ArkUI_VerticalAlignment](#arkui_verticalalignment) [OH_ArkUI_AlignmentRuleOption_GetBottomAlignment](#oh_arkui_alignmentruleoption_getbottomalignment) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取底部对齐的参数。  |
| const char \* [OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical](#oh_arkui_alignmentruleoption_getcenteridvertical) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取纵向居中对齐方式的参数。  |
| [ArkUI_VerticalAlignment](#arkui_verticalalignment) [OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical](#oh_arkui_alignmentruleoption_getcenteralignmentvertical) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取纵向居中对齐方式的参数。  |
| float [OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal](#oh_arkui_alignmentruleoption_getbiashorizontal) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取水平方向上的bias值。  |
| float [OH_ArkUI_AlignmentRuleOption_GetBiasVertical](#oh_arkui_alignmentruleoption_getbiasvertical) ([ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption) \*option) | 获取垂直方向上的bias值。  |
| [ArkUI_SwiperIndicator](#arkui_swiperindicator) \* [OH_ArkUI_SwiperIndicator_Create](#oh_arkui_swiperindicator_create) ([ArkUI_SwiperIndicatorType](#arkui_swiperindicatortype) type) | 创建 Swiper 组件的导航指示器。  |
| void [OH_ArkUI_SwiperIndicator_Dispose](#oh_arkui_swiperindicator_dispose) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 销毁Swiper组件的导航指示器指针。  |
| void [OH_ArkUI_SwiperIndicator_SetStartPosition](#oh_arkui_swiperindicator_setstartposition) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, float value) | 设置导航点距离 Swiper 组件左边的距离。  |
| float [OH_ArkUI_SwiperIndicator_GetStartPosition](#oh_arkui_swiperindicator_getstartposition) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取导航点距离 Swiper 组件左边的距离。  |
| void [OH_ArkUI_SwiperIndicator_SetTopPosition](#oh_arkui_swiperindicator_settopposition) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, float value) | 设置导航点距离 Swiper 组件顶部的距离。  |
| float [OH_ArkUI_SwiperIndicator_GetTopPosition](#oh_arkui_swiperindicator_gettopposition) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取导航点距离 Swiper 组件顶部的距离。  |
| void [OH_ArkUI_SwiperIndicator_SetEndPosition](#oh_arkui_swiperindicator_setendposition) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, float value) | 设置导航点距离 Swiper 组件右边的距离。  |
| float [OH_ArkUI_SwiperIndicator_GetEndPosition](#oh_arkui_swiperindicator_getendposition) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取导航点距离 Swiper 组件右边的距离。  |
| void [OH_ArkUI_SwiperIndicator_SetBottomPosition](#oh_arkui_swiperindicator_setbottomposition) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, float value) | 设置导航点距离 Swiper 组件底部的距离。  |
| float [OH_ArkUI_SwiperIndicator_GetBottomPosition](#oh_arkui_swiperindicator_getbottomposition) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取导航点距离 Swiper 组件底部的距离。  |
| void [OH_ArkUI_SwiperIndicator_SetItemWidth](#oh_arkui_swiperindicator_setitemwidth) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, float value) | 设置 Swiper 组件圆点导航指示器的宽。  |
| float [OH_ArkUI_SwiperIndicator_GetItemWidth](#oh_arkui_swiperindicator_getitemwidth) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取 Swiper 组件圆点导航指示器的宽。  |
| void [OH_ArkUI_SwiperIndicator_SetItemHeight](#oh_arkui_swiperindicator_setitemheight) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, float value) | 设置 Swiper 组件圆点导航指示器的高。  |
| float [OH_ArkUI_SwiperIndicator_GetItemHeight](#oh_arkui_swiperindicator_getitemheight) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取 Swiper 组件圆点导航指示器的高。  |
| void [OH_ArkUI_SwiperIndicator_SetSelectedItemWidth](#oh_arkui_swiperindicator_setselecteditemwidth) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, float value) | 设置被选中的 Swiper 组件圆点导航指示器的宽。  |
| float [OH_ArkUI_SwiperIndicator_GetSelectedItemWidth](#oh_arkui_swiperindicator_getselecteditemwidth) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取被选中 Swiper 组件圆点导航指示器的宽。  |
| void [OH_ArkUI_SwiperIndicator_SetSelectedItemHeight](#oh_arkui_swiperindicator_setselecteditemheight) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, float value) | 设置被选中的 Swiper 组件圆点导航指示器的高。  |
| float [OH_ArkUI_SwiperIndicator_GetSelectedItemHeight](#oh_arkui_swiperindicator_getselecteditemheight) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取被选中 Swiper 组件圆点导航指示器的高。  |
| void [OH_ArkUI_SwiperIndicator_SetMask](#oh_arkui_swiperindicator_setmask) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, int32_t mask) | 设置是否显示 Swiper 组件圆点导航指示器的蒙版样式。  |
| int32_t [OH_ArkUI_SwiperIndicator_GetMask](#oh_arkui_swiperindicator_getmask) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取是否显示 Swiper 组件圆点导航指示器的蒙版样式。  |
| void [OH_ArkUI_SwiperIndicator_SetColor](#oh_arkui_swiperindicator_setcolor) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, uint32_t color) | 设置 Swiper 组件圆点导航指示器的颜色。  |
| uint32_t [OH_ArkUI_SwiperIndicator_GetColor](#oh_arkui_swiperindicator_getcolor) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取 Swiper 组件圆点导航指示器的颜色。  |
| void [OH_ArkUI_SwiperIndicator_SetSelectedColor](#oh_arkui_swiperindicator_setselectedcolor) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, uint32_t selectedColor) | 设置被选中 Swiper 组件圆点导航指示器的颜色。  |
| uint32_t [OH_ArkUI_SwiperIndicator_GetSelectedColor](#oh_arkui_swiperindicator_getselectedcolor) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取被选中 Swiper 组件圆点导航指示器的颜色。  |
| int32_t [OH_ArkUI_SwiperIndicator_SetMaxDisplayCount](#oh_arkui_swiperindicator_setmaxdisplaycount) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, int32_t maxDisplayCount) | 设置圆点导航点指示器样式下，导航点显示个数的最大值。  |
| int32_t [OH_ArkUI_SwiperIndicator_GetMaxDisplayCount](#oh_arkui_swiperindicator_getmaxdisplaycount) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取圆点导航点指示器样式下，导航点显示个数的最大值。  |
| void [OH_ArkUI_SwiperIndicator_SetSpace](#oh_arkui_swiperindicator_setspace) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, float space) | 设置导航点间距。 |
| float [OH_ArkUI_SwiperIndicator_GetSpace](#oh_arkui_swiperindicator_getspace) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取导航点间距。|
| void [OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom](#oh_arkui_swiperindicator_setignoresizeofbottom) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator, int32_t ignoreSize) | 设置OH_ArkUI_SwiperIndicator_SetBottomPosition是否忽略导航点大小。 |
| int32_t [OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom](#oh_arkui_swiperindicator_getignoresizeofbottom) ([ArkUI_SwiperIndicator](#arkui_swiperindicator) \*indicator) | 获取OH_ArkUI_SwiperDigitIndicator_SetBottomPosition是否忽略导航点大小。|
| [ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* [OH_ArkUI_SwiperDigitIndicator_Create](#oh_arkui_swiperdigitindicator_create)() | 创建 Swiper 组件的数字导航指示器。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetStartPosition](#oh_arkui_swiperdigitindicator_setstartposition)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, float value) | 设置数字导航指示器距离 Swiper 组件左边的距离，在从右至左显示的语言模式下，设置其距离 Swiper 组件右边的距离。  |
| float [OH_ArkUI_SwiperDigitIndicator_GetStartPosition](#oh_arkui_swiperdigitindicator_getstartposition)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取数字导航指示器距离 Swiper 组件左边的距离，在从右至左显示的语言模式下，获取其距离 Swiper 组件右边的距离。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetTopPosition](#oh_arkui_swiperdigitindicator_settopposition)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, float value) | 设置数字导航指示器距离 Swiper 组件顶部的距离。 |
| float [OH_ArkUI_SwiperDigitIndicator_GetTopPosition](#oh_arkui_swiperdigitindicator_gettopposition)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取数字导航指示器距离 Swiper 组件顶部的距离。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetEndPosition](#oh_arkui_swiperdigitindicator_setendposition)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, float value) | 设置数字导航指示器距离 Swiper 组件右边的距离，从右至左显示的语言模式下，设置其距离 Swiper 左边的距离。 |
| float [OH_ArkUI_SwiperDigitIndicator_GetEndPosition](#oh_arkui_swiperdigitindicator_getendposition)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取数字导航指示器距离 Swiper 组件右边的距离，从右至左显示语言模式下，获取其距离 Swiper 组件左边的距离。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetBottomPosition](#oh_arkui_swiperdigitindicator_setbottomposition)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, float value) | 设置数字导航指示器距离 Swiper 组件底部的距离。 |
| float [OH_ArkUI_SwiperDigitIndicator_GetBottomPosition](#oh_arkui_swiperdigitindicator_getbottomposition)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取数字导航指示器距离 Swiper 组件底部的距离。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetFontColor](#oh_arkui_swiperdigitindicator_setfontcolor)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, uint32_t color) | 设置 Swiper 组件数字导航指示器字体颜色。 |
| uint32_t [OH_ArkUI_SwiperDigitIndicator_GetFontColor](#oh_arkui_swiperdigitindicator_getfontcolor)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取 Swiper 组件数字导航指示器字体颜色。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor](#oh_arkui_swiperdigitindicator_setselectedfontcolor)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, uint32_t selectedColor) | 设置被选中 Swiper 组件数字导航指示器字体颜色。 |
| uint32_t [OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor](#oh_arkui_swiperdigitindicator_getselectedfontcolor)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取被选中 Swiper 组件数字导航指示器字体颜色。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetFontSize](#oh_arkui_swiperdigitindicator_setfontsize)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, float size) | 设置 Swiper 组件数字导航指示器字体大小。 |
| float [OH_ArkUI_SwiperDigitIndicator_GetFontSize](#oh_arkui_swiperdigitindicator_getfontsize)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取 Swiper 组件数字导航指示器字体大小。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize](#oh_arkui_swiperdigitindicator_setselectedfontsize)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, float size) | 设置被选中 Swiper 组件数字导航指示器字体大小。 |
| float [OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize](#oh_arkui_swiperdigitindicator_getselectedfontsize)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取被选中 Swiper 组件数字导航指示器字体大小。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetFontWeight](#oh_arkui_swiperdigitindicator_setfontweight)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, [ArkUI_FontWeight](#arkui_fontweight) fontWeight) | 设置 Swiper 组件数字导航指示器字体粗细属性。 |
| [ArkUI_FontWeight](#arkui_fontweight) [OH_ArkUI_SwiperDigitIndicator_GetFontWeight](#oh_arkui_swiperdigitindicator_getfontweight)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取 Swiper 组件数字导航指示器字体粗细属性。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight](#oh_arkui_swiperdigitindicator_setselectedfontweight)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, [ArkUI_FontWeight](#arkui_fontweight) selectedFontWeight) | 设置被选中 Swiper 组件数字导航指示器字体粗细属性。 |
| [ArkUI_FontWeight](#arkui_fontweight) [OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight](#oh_arkui_swiperdigitindicator_getselectedfontweight)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取被选中 Swiper 组件数字导航指示器字体粗细属性。  |
|void [OH_ArkUI_SwiperDigitIndicator_Destroy](#oh_arkui_swiperdigitindicator_destroy)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 销毁Swiper组件的数字导航指示器指针。  |
| void [OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom](#oh_arkui_swiperdigitindicator_setignoresizeofbottom)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator, int32_t ignoreSize) | 设置OH_ArkUI_SwiperDigitIndicator_SetBottomPosition是否忽略导航点大小。 |
| int32_t [OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom](#oh_arkui_swiperdigitindicator_getignoresizeofbottom)([ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)* indicator) | 获取OH_ArkUI_SwiperDigitIndicator_SetBottomPosition是否忽略导航点大小。|
| [ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* [OH_ArkUI_SwiperArrowStyle_Create](#oh_arkui_swiperarrowstyle_create)() | 创建 Swiper 组件的导航箭头。  |
| void [OH_ArkUI_SwiperArrowStyle_SetShowBackground](#oh_arkui_swiperarrowstyle_setshowbackground)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator, int32_t showBackground) | 设置 Swiper 组件导航箭头底板是否显示。 |
| int32_t [OH_ArkUI_SwiperArrowStyle_GetShowBackground](#oh_arkui_swiperarrowstyle_getshowbackground)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator) | 获取 Swiper 组件导航箭头底板是否显示。  |
| void [OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle](#oh_arkui_swiperarrowstyle_setshowsidebarmiddle)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator, int32_t showSidebarMiddle) | 设置 Swiper 组件导航箭头显示位置。 |
| int32_t [OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle](#oh_arkui_swiperarrowstyle_getshowsidebarmiddle)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator) | 获取 Swiper 组件导航箭头显示位置。  |
| void [OH_ArkUI_SwiperArrowStyle_SetBackgroundSize](#oh_arkui_swiperarrowstyle_setbackgroundsize)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator, float backgroundSize) | 设置 Swiper 组件导航箭头底板大小。 |
| float [OH_ArkUI_SwiperArrowStyle_GetBackgroundSize](#oh_arkui_swiperarrowstyle_getbackgroundsize)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator) | 获取 Swiper 组件导航箭头底板大小。  |
| void [OH_ArkUI_SwiperArrowStyle_SetBackgroundColor](#oh_arkui_swiperarrowstyle_setbackgroundcolor)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator, uint32_t backgroundColor) | 设置 Swiper 组件导航箭头底板颜色。 |
| uint32_t [OH_ArkUI_SwiperArrowStyle_GetBackgroundColor](#oh_arkui_swiperarrowstyle_getbackgroundcolor)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator) | 获取 Swiper 组件导航箭头底板颜色。  |
| void [OH_ArkUI_SwiperArrowStyle_SetArrowSize](#oh_arkui_swiperarrowstyle_setarrowsize)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator, float arrowSize) | 设置 Swiper 组件导航箭头大小。 |
| float [OH_ArkUI_SwiperArrowStyle_GetArrowSize](#oh_arkui_swiperarrowstyle_getarrowsize)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator) | 获取 Swiper 组件导航箭头大小。  |
| void [OH_ArkUI_SwiperArrowStyle_SetArrowColor](#oh_arkui_swiperarrowstyle_setarrowcolor)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator, uint32_t arrowColor) | 设置 Swiper 组件导航箭头颜色。 |
| uint32_t [OH_ArkUI_SwiperArrowStyle_GetArrowColor](#oh_arkui_swiperarrowstyle_getarrowcolor)([ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)* indicator) | 获取 Swiper 组件导航箭头颜色。  |
|void [OH_ArkUI_SwiperArrowStyle_Destroy](#oh_arkui_swiperarrowstyle_destroy)() | 销毁Swiper组件的导航箭头指针。  |
| [ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \* [OH_ArkUI_ListItemSwipeActionItem_Create](#oh_arkui_listitemswipeactionitem_create) () | 创建ListItemSwipeActionItem接口设置的配置项。  |
| void [OH_ArkUI_ListItemSwipeActionItem_Dispose](#oh_arkui_listitemswipeactionitem_dispose) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item) | 销毁ListItemSwipeActionItem实例。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetContent](#oh_arkui_listitemswipeactionitem_setcontent) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, [ArkUI_NodeHandle](#arkui_nodehandle) node) | 设置ListItemSwipeActionItem的布局内容。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance](#oh_arkui_listitemswipeactionitem_setactionareadistance) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, float distance) | 设置组件长距离滑动删除距离阈值。  |
| float [OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance](#oh_arkui_listitemswipeactionitem_getactionareadistance) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item) | 获取组件长距离滑动删除距离阈值。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea](#oh_arkui_listitemswipeactionitem_setonenteractionarea) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, void(\*callback)()) | 设置滑动条目进入删除区域时调用的事件。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData](#oh_arkui_listitemswipeactionitem_setonenteractionareawithuserdata) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, void \*userData, void(\*callback)(void \*userData)) | 设置滑动条目进入删除区域时调用的事件。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetOnAction](#oh_arkui_listitemswipeactionitem_setonaction) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, void(\*callback)()) | 设置组件进入长距删除区后删除ListItem时调用的事件。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData](#oh_arkui_listitemswipeactionitem_setonactionwithuserdata) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, void \*userData, void(\*callback)(void \*userData)) | 设置组件进入长距删除区后删除ListItem时调用的事件。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea](#oh_arkui_listitemswipeactionitem_setonexitactionarea) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, void(\*callback)()) | 设置滑动条目退出删除区域时调用的事件。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData](#oh_arkui_listitemswipeactionitem_setonexitactionareawithuserdata) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, void \*userData, void(\*callback)(void \*userData)) | 设置滑动条目退出删除区域时调用的事件。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange](#oh_arkui_listitemswipeactionitem_setonstatechange) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, void(\*callback)([ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate) swipeActionState)) | 设置列表项滑动状态变化时候触发的事件。  |
| void [OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData](#oh_arkui_listitemswipeactionitem_setonstatechangewithuserdata) ([ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item, void \*userData, void(\*callback)([ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate) swipeActionState, void \*userData)) | 设置列表项滑动状态变化时候触发的事件。  |
| [ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) \* [OH_ArkUI_ListItemSwipeActionOption_Create](#oh_arkui_listitemswipeactionoption_create) () | 创建ListItemSwipeActionOption接口设置的配置项。  |
| void [OH_ArkUI_ListItemSwipeActionOption_Dispose](#oh_arkui_listitemswipeactionoption_dispose) ([ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) \*option) | 销毁ListItemSwipeActionOption实例。  |
| void [OH_ArkUI_ListItemSwipeActionOption_SetStart](#oh_arkui_listitemswipeactionoption_setstart) ([ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) \*option, [ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item) | 设置ListItemSwipeActionItem的左侧（垂直布局）或上方（横向布局）布局内容。  |
| void [OH_ArkUI_ListItemSwipeActionOption_SetEnd](#oh_arkui_listitemswipeactionoption_setend) ([ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) \*option, [ArkUI_ListItemSwipeActionItem](#arkui_listitemswipeactionitem) \*item) | 设置ListItemSwipeActionItem的右侧（垂直布局）或下方（横向布局）布局内容。  |
| void [OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect](#oh_arkui_listitemswipeactionoption_setedgeeffect) ([ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) \*option, [ArkUI_ListItemSwipeEdgeEffect](#arkui_listitemswipeedgeeffect) edgeEffect) | 设置滑动效果。  |
| int32_t [OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect](#oh_arkui_listitemswipeactionoption_getedgeeffect) ([ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) \*option) | 获取滑动效果。  |
| void [OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange](#oh_arkui_listitemswipeactionoption_setonoffsetchange) ([ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) \*option, void(\*callback)(float offset)) | 滑动操作偏移量更改时调用的事件。  |
| void [OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData](#oh_arkui_listitemswipeactionoption_setonoffsetchangewithuserdata) ([ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption) \*option, void \*userData, void(\*callback)(float offset, void \*userData)) | 滑动操作偏移量更改时调用的事件。  |
| [ArkUI_AccessibilityState](#arkui_accessibilitystate) \* [OH_ArkUI_AccessibilityState_Create](#oh_arkui_accessibilitystate_create) (void) | 创建无障碍状态。  |
| void [OH_ArkUI_AccessibilityState_Dispose](#oh_arkui_accessibilitystate_dispose) ([ArkUI_AccessibilityState](#arkui_accessibilitystate) \*state) | 销毁无障碍状态指针。  |
| void [OH_ArkUI_AccessibilityState_SetDisabled](#oh_arkui_accessibilitystate_setdisabled) ([ArkUI_AccessibilityState](#arkui_accessibilitystate) \*state, int32_t isDisabled) | 设置无障碍状态是否禁用。  |
| int32_t [OH_ArkUI_AccessibilityState_IsDisabled](#oh_arkui_accessibilitystate_isdisabled) ([ArkUI_AccessibilityState](#arkui_accessibilitystate) \*state) | 获取无障碍状态是否禁用。  |
| void [OH_ArkUI_AccessibilityState_SetSelected](#oh_arkui_accessibilitystate_setselected) ([ArkUI_AccessibilityState](#arkui_accessibilitystate) \*state, int32_t isSelected) | 设置无障碍状态是否选中。  |
| int32_t [OH_ArkUI_AccessibilityState_IsSelected](#oh_arkui_accessibilitystate_isselected) ([ArkUI_AccessibilityState](#arkui_accessibilitystate) \*state) | 获取无障碍状态是否选中。  |
| void [OH_ArkUI_AccessibilityState_SetCheckedState](#oh_arkui_accessibilitystate_setcheckedstate) ([ArkUI_AccessibilityState](#arkui_accessibilitystate) \*state, int32_t checkedState) | 设置无障碍状态复选框状态。  |
| int32_t [OH_ArkUI_AccessibilityState_GetCheckedState](#oh_arkui_accessibilitystate_getcheckedstate) ([ArkUI_AccessibilityState](#arkui_accessibilitystate) \*state) | 获取无障碍状态复选框状态。  |
| [ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \* [OH_ArkUI_AccessibilityValue_Create](#oh_arkui_accessibilityvalue_create) (void) | 创建无障碍信息。  |
| void [OH_ArkUI_AccessibilityValue_Dispose](#oh_arkui_accessibilityvalue_dispose) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value) | 销毁无障碍信息指针。  |
| void [OH_ArkUI_AccessibilityValue_SetMin](#oh_arkui_accessibilityvalue_setmin) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value, int32_t min) | 设置无障碍最小值信息。  |
| int32_t [OH_ArkUI_AccessibilityValue_GetMin](#oh_arkui_accessibilityvalue_getmin) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value) | 获取无障碍最小值信息。  |
| void [OH_ArkUI_AccessibilityValue_SetMax](#oh_arkui_accessibilityvalue_setmax) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value, int32_t max) | 设置无障碍最大值信息。  |
| int32_t [OH_ArkUI_AccessibilityValue_GetMax](#oh_arkui_accessibilityvalue_getmax) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value) | 获取无障碍最大值信息。  |
| void [OH_ArkUI_AccessibilityValue_SetCurrent](#oh_arkui_accessibilityvalue_setcurrent) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value, int32_t current) | 设置无障碍当前值信息。  |
| int32_t [OH_ArkUI_AccessibilityValue_GetCurrent](#oh_arkui_accessibilityvalue_getcurrent) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value) | 获取无障碍当前值信息。  |
| void [OH_ArkUI_AccessibilityValue_SetRangeMin](#oh_arkui_accessibilityvalue_setrangemin) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value, int32_t rangeMin) | 用于设置范围组件的无障碍最小值信息。  |
| int32_t [OH_ArkUI_AccessibilityValue_GetRangeMin](#oh_arkui_accessibilityvalue_getrangemin) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value) | 用于获取范围组件的无障碍最小值信息。  |
| void [OH_ArkUI_AccessibilityValue_SetRangeMax](#oh_arkui_accessibilityvalue_setrangemax) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value, int32_t rangeMax) | 用于设置范围组件的无障碍最大值信息。  |
| int32_t [OH_ArkUI_AccessibilityValue_GetRangeMax](#oh_arkui_accessibilityvalue_getrangemax) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value) | 用于获取范围组件的无障碍最大值信息。  |
| void [OH_ArkUI_AccessibilityValue_SetRangeCurrent](#oh_arkui_accessibilityvalue_setrangecurrent) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value, int32_t rangeCurrent) | 用于设置范围组件的无障碍当前值信息。  |
| int32_t [OH_ArkUI_AccessibilityValue_GetRangeCurrent](#oh_arkui_accessibilityvalue_getrangecurrent) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value) | 用于获取范围组件的无障碍当前值信息。  |
| void [OH_ArkUI_AccessibilityValue_SetText](#oh_arkui_accessibilityvalue_settext) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value, const char \*text) | 设置无障碍文本描述信息。  |
| const char \* [OH_ArkUI_AccessibilityValue_GetText](#oh_arkui_accessibilityvalue_gettext) ([ArkUI_AccessibilityValue](#arkui_accessibilityvalue) \*value) | 获取无障碍文本描述信息。  |
| [ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \* [OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString](#oh_arkui_imageanimatorframeinfo_createfromstring) (char \*src) | 使用图片路径创建帧图片信息，图片格式为svg，png和jpg。  |
| [ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \* [OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor](#oh_arkui_imageanimatorframeinfo_createfromdrawabledescriptor) ([ArkUI_DrawableDescriptor](#arkui_drawabledescriptor) \*drawable) | 使用 DrawableDescriptor 对象创建帧图片信息，图片格式为Resource和PixelMap。  |
| void [OH_ArkUI_ImageAnimatorFrameInfo_Dispose](#oh_arkui_imageanimatorframeinfo_dispose) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo) | 销毁帧图片对象指针。  |
| void [OH_ArkUI_ImageAnimatorFrameInfo_SetWidth](#oh_arkui_imageanimatorframeinfo_setwidth) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo, int32_t width) | 设置图片宽度。  |
| int32_t [OH_ArkUI_ImageAnimatorFrameInfo_GetWidth](#oh_arkui_imageanimatorframeinfo_getwidth) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo) | 获取图片宽度。  |
| void [OH_ArkUI_ImageAnimatorFrameInfo_SetHeight](#oh_arkui_imageanimatorframeinfo_setheight) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo, int32_t height) | 设置图片高度。  |
| int32_t [OH_ArkUI_ImageAnimatorFrameInfo_GetHeight](#oh_arkui_imageanimatorframeinfo_getheight) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo) | 获取图片高度。  |
| void [OH_ArkUI_ImageAnimatorFrameInfo_SetTop](#oh_arkui_imageanimatorframeinfo_settop) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo, int32_t top) | 设置图片相对于组件左上角的纵向坐标。  |
| int32_t [OH_ArkUI_ImageAnimatorFrameInfo_GetTop](#oh_arkui_imageanimatorframeinfo_gettop) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo) | 获取图片相对于组件左上角的纵向坐标。  |
| void [OH_ArkUI_ImageAnimatorFrameInfo_SetLeft](#oh_arkui_imageanimatorframeinfo_setleft) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo, int32_t left) | 设置图片相对于组件左上角的横向坐标。  |
| int32_t [OH_ArkUI_ImageAnimatorFrameInfo_GetLeft](#oh_arkui_imageanimatorframeinfo_getleft) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo) | 获取图片相对于组件左上角的横向坐标。  |
| void [OH_ArkUI_ImageAnimatorFrameInfo_SetDuration](#oh_arkui_imageanimatorframeinfo_setduration) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo, int32_t duration) | 设置图片的播放时长。  |
| int32_t [OH_ArkUI_ImageAnimatorFrameInfo_GetDuration](#oh_arkui_imageanimatorframeinfo_getduration) ([ArkUI_ImageAnimatorFrameInfo](#arkui_imageanimatorframeinfo) \*imageInfo) | 获取图片的播放时长。  |
| [ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) \* [OH_ArkUI_ListChildrenMainSizeOption_Create](#oh_arkui_listchildrenmainsizeoption_create) () | 创建ListChildrenMainSize接口设置的配置项。  |
| void [OH_ArkUI_ListChildrenMainSizeOption_Dispose](#oh_arkui_listchildrenmainsizeoption_dispose) ([ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) \*option) | 销毁ListChildrenMainSize实例。  |
| int32_t [OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize](#oh_arkui_listchildrenmainsizeoption_setdefaultmainsize) ([ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) \*option, float defaultMainSize) | 设置List组件的ChildrenMainSizeOption默认大小。  |
| float [OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize](#oh_arkui_listchildrenmainsizeoption_getdefaultmainsize) ([ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) \*option) | 获取List组件的ChildrenMainSizeOption默认大小。  |
| void [OH_ArkUI_ListChildrenMainSizeOption_Resize](#oh_arkui_listchildrenmainsizeoption_resize) ([ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) \*option, int32_t totalSize) | 重置List组件的ChildrenMainSizeOption的数组大小。  |
| int32_t [OH_ArkUI_ListChildrenMainSizeOption_Splice](#oh_arkui_listchildrenmainsizeoption_splice) ([ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) \*option, int32_t index, int32_t deleteCount, int32_t addCount) | 对List组件的ChildrenMainSizeOption数组操作大小调整。  |
| int32_t [OH_ArkUI_ListChildrenMainSizeOption_UpdateSize](#oh_arkui_listchildrenmainsizeoption_updatesize) ([ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) \*option, int32_t index, float mainSize) | 更新List组件的ChildrenMainSizeOption数组的值。  |
| float [OH_ArkUI_ListChildrenMainSizeOption_GetMainSize](#oh_arkui_listchildrenmainsizeoption_getmainsize) ([ArkUI_ListChildrenMainSize](#arkui_listchildrenmainsize) \*option, int32_t index) | 获取List组件的ChildrenMainSizeOption数组的值。  |
| [ArkUI_CustomSpanMeasureInfo](#arkui_customspanmeasureinfo) \* [OH_ArkUI_CustomSpanMeasureInfo_Create](#oh_arkui_customspanmeasureinfo_create) (void) | 创建自定义段落组件测量信息。  |
| void [OH_ArkUI_CustomSpanMeasureInfo_Dispose](#oh_arkui_customspanmeasureinfo_dispose) ([ArkUI_CustomSpanMeasureInfo](#arkui_customspanmeasureinfo) \*info) | 销毁自定义段落组件测量信息。  |
| float [OH_ArkUI_CustomSpanMeasureInfo_GetFontSize](#oh_arkui_customspanmeasureinfo_getfontsize) ([ArkUI_CustomSpanMeasureInfo](#arkui_customspanmeasureinfo) \*info) | 获取自定义段落组件的父节点Text的字体大小。  |
| [ArkUI_CustomSpanMetrics](#arkui_customspanmetrics) \* [OH_ArkUI_CustomSpanMetrics_Create](#oh_arkui_customspanmetrics_create) (void) | 创建自定义段落组件度量信息。  |
| void [OH_ArkUI_CustomSpanMetrics_Dispose](#oh_arkui_customspanmetrics_dispose) ([ArkUI_CustomSpanMetrics](#arkui_customspanmetrics) \*metrics) | 销毁自定义段落组件度量信息。  |
| int32_t [OH_ArkUI_CustomSpanMetrics_SetWidth](#oh_arkui_customspanmetrics_setwidth) ([ArkUI_CustomSpanMetrics](#arkui_customspanmetrics) \*metrics, float width) | 设置自定义段落组件的宽度。  |
| int32_t [OH_ArkUI_CustomSpanMetrics_SetHeight](#oh_arkui_customspanmetrics_setheight) ([ArkUI_CustomSpanMetrics](#arkui_customspanmetrics) \*metrics, float height) | 设置自定义段落组件的高度。  |
| [ArkUI_CustomSpanDrawInfo](#arkui_customspandrawinfo) \* [OH_ArkUI_CustomSpanDrawInfo_Create](#oh_arkui_customspandrawinfo_create) (void) | 创建自定义段落组件绘制信息。  |
| void [OH_ArkUI_CustomSpanDrawInfo_Dispose](#oh_arkui_customspandrawinfo_dispose) ([ArkUI_CustomSpanDrawInfo](#arkui_customspandrawinfo) \*info) | 销毁自定义段落组件绘制信息。  |
| float [OH_ArkUI_CustomSpanDrawInfo_GetXOffset](#oh_arkui_customspandrawinfo_getxoffset) ([ArkUI_CustomSpanDrawInfo](#arkui_customspandrawinfo) \*info) | 获取自定义段落组件相对于挂载组件的x轴偏移值。  |
| float [OH_ArkUI_CustomSpanDrawInfo_GetLineTop](#oh_arkui_customspandrawinfo_getlinetop) ([ArkUI_CustomSpanDrawInfo](#arkui_customspandrawinfo) \*info) | 获取自定义段落组件相对于挂载组件的上边距。  |
| float [OH_ArkUI_CustomSpanDrawInfo_GetLineBottom](#oh_arkui_customspandrawinfo_getlinebottom) ([ArkUI_CustomSpanDrawInfo](#arkui_customspandrawinfo) \*info) | 获取自定义段落组件相对于挂载组件的下边距。  |
| float [OH_ArkUI_CustomSpanDrawInfo_GetBaseline](#oh_arkui_customspandrawinfo_getbaseline) ([ArkUI_CustomSpanDrawInfo](#arkui_customspandrawinfo) \*info) | 获取自定义段落组件相对于挂载组件的基线偏移量。  |
| void [OH_ArkUI_CustomProperty_Destroy](#oh_arkui_customproperty_destroy) ([ArkUI_CustomProperty](#arkui_customproperty) \*handle) | 销毁CustomProperty实例。  |
| const char \* [OH_ArkUI_CustomProperty_GetStringValue](#oh_arkui_customproperty_getstringvalue) ([ArkUI_CustomProperty](#arkui_customproperty) \*handle) | 获取自定义属性value信息。  |
| void [OH_ArkUI_ActiveChildrenInfo_Destroy](#oh_arkui_activechildreninfo_destroy) (ArkUI_ActiveChildrenInfo \*handle) | 销毁ActiveChildrenInfo实例。  |
| [ArkUI_NodeHandle](#arkui_nodehandle) [OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex](#oh_arkui_activechildreninfo_getnodebyindex) (ArkUI_ActiveChildrenInfo \*handle, int32_t index) | 获取ActiveChildrenInfo结构体的下标为index的子节点。  |
| int32_t [OH_ArkUI_ActiveChildrenInfo_GetCount](#oh_arkui_activechildreninfo_getcount) (ArkUI_ActiveChildrenInfo \*handle) | 获取ActiveChildrenInfo结构体内的节点数量。  |
| [ArkUI_StyledString](#arkui_styledstring) \* [OH_ArkUI_StyledString_Create](#oh_arkui_styledstring_create) (OH_Drawing_TypographyStyle \*style, OH_Drawing_FontCollection \*collection) | 创建指向ArkUI_StyledString对象的指针。  |
| void [OH_ArkUI_StyledString_Destroy](#oh_arkui_styledstring_destroy) ([ArkUI_StyledString](#arkui_styledstring) \*handle) | 释放被ArkUI_StyledString对象占据的内存。  |
| void [OH_ArkUI_StyledString_PushTextStyle](#oh_arkui_styledstring_pushtextstyle) ([ArkUI_StyledString](#arkui_styledstring) \*handle, OH_Drawing_TextStyle \*style) | 将新的排版风格设置到当前格式化字符串样式栈顶。  |
| void [OH_ArkUI_StyledString_AddText](#oh_arkui_styledstring_addtext) ([ArkUI_StyledString](#arkui_styledstring) \*handle, const char \*content) | 基于当前格式化字符串样式设置对应的文本内容。  |
| void [OH_ArkUI_StyledString_PopTextStyle](#oh_arkui_styledstring_poptextstyle) ([ArkUI_StyledString](#arkui_styledstring) \*handle) | 将当前格式化字符串对象中栈顶样式出栈。  |
| OH_Drawing_Typography \* [OH_ArkUI_StyledString_CreateTypography](#oh_arkui_styledstring_createtypography) ([ArkUI_StyledString](#arkui_styledstring) \*handle) | 基于格式字符串对象创建指向OH_Drawing_Typography对象的指针，用于提前进行文本测算排版。  |
| void [OH_ArkUI_StyledString_AddPlaceholder](#oh_arkui_styledstring_addplaceholder) ([ArkUI_StyledString](#arkui_styledstring) \*handle, OH_Drawing_PlaceholderSpan \*placeholder) | 设置占位符。  |
| [ArkUI_StyledString_Descriptor](#arkui_styledstring_descriptor) \* [OH_ArkUI_StyledString_Descriptor_Create](#oh_arkui_styledstring_descriptor_create) (void) | 创建属性字符串数据对象。  |
| void [OH_ArkUI_StyledString_Descriptor_Destroy](#oh_arkui_styledstring_descriptor_destroy) ([ArkUI_StyledString_Descriptor](#arkui_styledstring_descriptor) \*descriptor) | 释放被ArkUI_StyledString_Descriptor对象占据的内存。  |
| int32_t [OH_ArkUI_UnmarshallStyledStringDescriptor](#oh_arkui_unmarshallstyledstringdescriptor) (uint8_t \*buffer, size_t bufferSize, [ArkUI_StyledString_Descriptor](#arkui_styledstring_descriptor) \*descriptor) | 将包含属性字符串信息的字节数组反序列化为属性字符串。  |
| int32_t [OH_ArkUI_MarshallStyledStringDescriptor](#oh_arkui_marshallstyledstringdescriptor) (uint8_t \*buffer, size_t bufferSize, [ArkUI_StyledString_Descriptor](#arkui_styledstring_descriptor) \*descriptor, size_t \*resultSize) | 将属性字符串信息序列化为字节数组。  |
| const char \* [OH_ArkUI_ConvertToHtml](#oh_arkui_converttohtml) ([ArkUI_StyledString_Descriptor](#arkui_styledstring_descriptor) \*descriptor) | 将属性字符串信息转化成html。  |
| int32_t [OH_ArkUI_PostFrameCallback](#oh_arkui_postframecallback)([ArkUI_ContextHandle](#arkui_contexthandle-12) uiContext, void\* userData, void (\*callback)(uint64_t nanoTimestamp, uint32_t frameCount, void\* userData))| 注册一个回调函数，以便在下一帧渲染时执行。不允许在非UI线程调用，检查到非UI线程调用程序会主动abort。 |
| int32_t [OH_ArkUI_PostIdleCallback](#oh_arkui_postframecallback)([ArkUI_ContextHandle](#arkui_contexthandle-12) uiContext, void\* userData, void (\*callback)(uint64_t nanoTimeLeft, uint32_t frameCount, void\* userData))| 注册一个回调函数，以便在下一帧渲染完成时执行。如果当前没有下一帧，将自动请求下一帧。 |
| int32_t [OH_ArkUI_RegisterLayoutCallbackOnNodeHandle](#oh_arkui_registerlayoutcallbackonnodehandle)([ArkUI_NodeHandle](#arkui_nodehandle) node, void\* userData, void (\*onLayoutCompleted)(void\* userData))| 注册组件布局完成回调方法。同一组件仅能注册一个布局完成回调方法。  |
| int32_t [OH_ArkUI_RegisterDrawCallbackOnNodeHandle](#oh_arkui_registerdrawcallbackonnodehandle)([ArkUI_NodeHandle](#arkui_nodehandle) node, void\* userData, void (\*onDrawCompleted)(void\* userData))| 注册组件绘制完成回调方法。同一组件仅能注册一个绘制完成回调方法。  |
| int32_t [OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle](#oh_arkui_unregisterlayoutcallbackonnodehandle)([ArkUI_NodeHandle](#arkui_nodehandle) node)| 取消注册组件布局完成回调方法。  |
| int32_t [OH_ArkUI_UnregisterDrawCallbackOnNodeHandle](#oh_arkui_unregisterdrawcallbackonnodehandle)([ArkUI_NodeHandle](#arkui_nodehandle) node)| 取消注册组件绘制完成回调方法。  |
| [ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md) [OH_ArkUI_NodeEvent_GetTextChangeEvent](#oh_arkui_nodeevent_gettextchangeevent)([ArkUI_NodeEvent](#arkui_nodeevent-12) \*event) | 获取输入框内容改变（包括预上屏内容）事件的相关数据。  |
|[ArkUI_ErrorCode](_ark_u_i___native_module.md#arkui_errorcode)  OH_ArkUI_FocusRequest([ArkUI_NodeHandle](_ark_u_i___native_module.md#arkui_nodehandle) node); | 请求焦点。|
| void OH_ArkUI_FocusClear([ArkUI_ContextHandle](_ark_u_i___native_module.md#arkui_contexthandle-12) uiContext); | 将当前焦点清除到根容器节点。 |
| void OH_ArkUI_FocusActivate([ArkUI_ContextHandle](_ark_u_i___native_module.md#arkui_contexthandle-12) uiContext, bool isActive, bool isAutoInactive); | 设置当前界面的焦点激活态，获焦节点显示焦点框。|
| void OH_ArkUI_FocusSetAutoTransfer([ArkUI_ContextHandle](_ark_u_i___native_module.md#arkui_contexthandle-12) uiContext, bool autoTransfer); | 设置页面切换时，焦点转移行为。 |
| void OH_ArkUI_FocusSetKeyProcessingMode([ArkUI_ContextHandle](_ark_u_i___native_module.md#arkui_contexthandle-12) uiContext, ArkUI_KeyProcessingMode mode); | 设置按键事件处理的优先级。 |
| void [OH_ArkUI_DragEvent_StartDataLoading](#oh_arkui_dragevent_startdataloading)([ArkUI_DragEvent](_ark_u_i___native_module.md#arkui_dragevent)\* event, [OH_UdmfGetDataParams](#oh_udmfgetdataparams)\* options, char\* key, unsigned int keyLen); | 使用指定的同步参数开始数据同步。 |
| void [OH_ArkUI_CancelDataLoading](#oh_arkui_canceldataloading)([ArkUI_Context](_ark_u_i___native_module.md#arkui_context) uiContext, const char\* key); | 取消正在进行的数据同步。 |
| void OH_ArkUI_[DisableDropDataPrefetchOnNode](#oh_arkui_disabledropdataprefetchonnode)([ArkUI_NodeHandle](_ark_u_i___native_module.md#arkui_nodehandle) node, bool disable); | 设置拖拽是否提前获取数据。true为不提前获取数据，默认值为false。 |
| [ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)\* [OH_ArkUI_ProgressLinearStyleOption_Create](#oh_arkui_progresslinearstyleoption_create)(void) | 创建线性进度条样式信息。 |
| void [OH_ArkUI_ProgressLinearStyleOption_Destroy](#oh_arkui_progresslinearstyleoption_destroy)([ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)* option) | 销毁线性进度条样式信息。 |
| void [OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled](#oh_arkui_progresslinearstyleoption_setscaneffectenabled)([ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)\* option, bool enabled) | 设置线性进度条进度平滑动效的开关。 |
| void [OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled](#oh_arkui_progresslinearstyleoption_setsmootheffectenabled)([ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)\* option, bool enabled) | 设置线性进度条扫光效果的开关。 |
| void [OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth](#oh_arkui_progresslinearstyleoption_setstrokewidth)([ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)\* option, float strokeWidth) | 设置线性进度条宽度。 |
| void [OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius](#oh_arkui_progresslinearstyleoption_setstrokeradius)([ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)\* option, float strokeRadius) | 设置线性进度条圆角半径。 |
| bool [OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled](#oh_arkui_progresslinearstyleoption_getscaneffectenabled)([ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)\* option) | 获取线性进度条进度平滑动效的开关信息。 |
| bool [OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled](#oh_arkui_progresslinearstyleoption_getsmootheffectenabled)([ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)\* option) | 获取线性进度条扫光效果的开关信息。 |
| float [OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth](#oh_arkui_progresslinearstyleoption_getstrokewidth)([ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)\* option) | 获取线性进度条宽度。 |
| float [OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius](#oh_arkui_progresslinearstyleoption_getstrokeradius)([ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)\* option) | 获取线性进度条圆角半径值。 |
| int32_t [OH_ArkUI_NodeUtils_GetPositionToParent](#oh_arkui_nodeutils_getpositiontoparent) ([ArkUI_NodeHandle](#arkui_nodehandle) node, [ArkUI_IntOffset](_ark_u_i___int_offset.md)\* globalOffset) | 获取目标节点相对于父节点的偏移值。  |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_AddSupportedUIStates](#oh_arkui_addsupporteduistates) ([ArkUI_NodeHandle](#arkui_nodehandle) node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData) | 设置组件支持的多态样式状态。 |
| [ArkUI_ErrorCode](#arkui_errorcode) [OH_ArkUI_RemoveSupportedUIStates](#oh_arkui_removesupporteduistates) ([ArkUI_NodeHandle](#arkui_nodehandle) node, int32_t uiStates) | 删除注册的状态。 |
| int32_t [OH_ArkUI_GetGestureParam_DirectMask](#oh_arkui_getgestureparam_directmask) (ArkUI_GestureRecognizer \*recognizer, [ArkUI_GestureDirectionMask](#arkui_gesturedirectionmask)\* directMask) | 获取手势识别器的滑动方向。 |
| int32_t [OH_ArkUI_GetGestureParam_FingerCount](#oh_arkui_getgestureparam_fingercount) (ArkUI_GestureRecognizer \*recognizer, int\* finger) | 获取手势识别器的手指数。 |
| int32_t [OH_ArkUI_GetGestureParam_limitFingerCount](#oh_arkui_getgestureparam_limitfingercount) (ArkUI_GestureRecognizer \*recognizer, bool\* isLimited) | 获取手势识别器是否有手指数限制。  |
| int32_t [OH_ArkUI_GetGestureParam_repeat](#oh_arkui_getgestureparam_repeat) (ArkUI_GestureRecognizer \*recognizer, bool\* isRepeat) | 获取手势识别器是否连续触发事件回调。 |
| int32_t [OH_ArkUI_GetGestureParam_distance](#oh_arkui_getgestureparam_distance) (ArkUI_GestureRecognizer \*recognizer, double\* distance) | 获取手势识别器的手指允许的移动距离范围。 |
| int32_t [OH_ArkUI_GetGestureParam_speed](#oh_arkui_getgestureparam_speed) (ArkUI_GestureRecognizer \*recognizer, double\* speed) | 获取手势识别器的识别滑动的最小速度。 |
| int32_t [OH_ArkUI_GetGestureParam_duration](#oh_arkui_getgestureparam_duration) (ArkUI_GestureRecognizer \*recognizer, int\* duration) | 获取手势识别器的触发长按的最短时间。 |
| int32_t [OH_ArkUI_GetGestureParam_angle](#oh_arkui_getgestureparam_angle) (ArkUI_GestureRecognizer \*recognizer, double\* angle) | 获取手势识别器的旋转手势的最小改变度数。 |
| int32_t [OH_ArkUI_GetGestureParam_distanceThreshold](#oh_arkui_getgestureparam_distancethreshold) (ArkUI_GestureRecognizer \*recognizer, double\* distanceThreshold) | 获取手势识别器的手势移动阈值。 |
| ArkUI_ErrorCode [OH_ArkUI_PanGesture_SetDistanceMap](#oh_arkui_pangesture_setdistancemap) (ArkUI_GestureRecognizer \*recognizer, int size, int\* toolTypeArray, double\* distanceArray) | 设置手势最小滑动阈值表。当设备类型为非法值时，设置不生效。 |
| ArkUI_ErrorCode [OH_ArkUI_PanGesture_GetDistanceByToolType](#oh_arkui_pangesture_getdistancebytooltype) (ArkUI_GestureRecognizer \*recognizer, int toolType, double\* distance) | 获取手势识别器的手势移动阈值表。 |
|int32_t [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending)([ArkUI_DragEvent](_ark_u_i___native_module.md#arkui_dragevent)\* event, int32_t* requestIdentify); | 请求延迟执行拖拽结束。|
|int32_t [OH_ArkUI_NotifyDragResult](#oh_arkui_notifydragresult)(int32_t requestIdentify, [ArkUI_DragResult](#arkui_dragresult) \* result); | 通知拖拽结果。|
|int32_t [OH_ArkUI_NotifyDragEndPendingDone](#oh_arkui_notifydragendpendingdone)(int32_t requestIdentify);| 通知拖拽延迟执行结束。|
|[ArkUI_TextPickerRangeContentArray](_ark_u_i___native_module.md#arkui_textpickerrangecontentarray)\* [OH_ArkUI_TextPickerRangeContentArray_Create](#oh_arkui_textpickerrangecontentarray_create)(int32_t length);| 创建TextPickerRangeContent数组的对象。<br/>**起始版本：** 19|
|void [OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex](#oh_arkui_textpickerrangecontentarray_seticonatindex)([ArkUI_TextPickerRangeContentArray](_ark_u_i___native_module.md#arkui_textpickerrangecontentarray)\* handle, char* icon, int32_t index);| 指定TextPickerRangeContent数组指定位置的icon数据。<br/>**起始版本：** 19|
|void [OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex](#oh_arkui_textpickerrangecontentarray_settextatindex)([ArkUI_TextPickerRangeContentArray](_ark_u_i___native_module.md#arkui_textpickerrangecontentarray)\* handle, char* text, int32_t index);| 指定TextPickerRangeContent数组指定位置的text数据。<br/>**起始版本：** 19|
|void [OH_ArkUI_TextPickerRangeContentArray_Destroy](#oh_arkui_textpickerrangecontentarray_destroy)([ArkUI_TextPickerRangeContentArray](_ark_u_i___native_module.md#arkui_textpickerrangecontentarray)\* handle);| 删除TextPickerRangeContent数组对象。<br/>**起始版本：** 19|
|[ArkUI_TextCascadePickerRangeContentArray](_ark_u_i___native_module.md#arkui_textcascadepickerrangecontentarray)\* [OH_ArkUI_TextCascadePickerRangeContentArray_Create](#oh_arkui_textcascadepickerrangecontentarray_create)(int32_t length);| 创建TextCascadePickerRangeContent数组对象。<br/>**起始版本：** 19|
|void [OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex](#oh_arkui_textcascadepickerrangecontentarray_settextatindex)([ArkUI_TextCascadePickerRangeContentArray](_ark_u_i___native_module.md#arkui_textcascadepickerrangecontentarray)\* handle, char* text, int32_t index);| 指定TextCascadePickerRangeContent数组指定位置的text数据。<br/>**起始版本：** 19|
|void [OH_ArkUI_TextCascadePickerRangeContentArray_setChildAtIndex](#oh_arkui_textcascadepickerrangecontentarray_setchildatindex)([ArkUI_TextCascadePickerRangeContentArray](_ark_u_i___native_module.md#arkui_textcascadepickerrangecontentarray)\* handle, [ArkUI_TextCascadePickerRangeContentArray](_ark_u_i___native_module.md#arkui_textcascadepickerrangecontentarray)\* child, int32_t index);| 指定TextCascadePickerRangeContent数组指定位置的child数据。<br/>**起始版本：** 19|
|void [OH_ArkUI_TextCascadePickerRangeContentArray_Destroy](#oh_arkui_textcascadepickerrangecontentarray_destroy)([ArkUI_TextCascadePickerRangeContentArray](_ark_u_i___native_module.md#arkui_textcascadepickerrangecontentarray)\* handle);| 删除TextCascadePickerRangeContent数组对象。<br/>**起始版本：** 19|
| int32_t [OH_ArkUI_GetNodeSnapshot](#oh_arkui_getnodesnapshot)(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelMap);| 获取指定组件节点的截图，执行过程为同步，调用时应确保对应节点已被渲染(避免在把节点挂树时就立即执行截图，因为图形的渲染一般需要一帧时间生效)。|
| ArkUI_SnapshotOptions* [OH_ArkUI_CreateSnapshotOptions](#oh_arkui_createsnapshotoptions)();| 创建一个截图选项，当返回值不再使用时必须通过`OH_ArkUI_SnapshotOptions_Dispose`释放。|
| void [OH_ArkUI_DestroySnapshotOptions](#oh_arkui_destroysnapshotoptions)(ArkUI_SnapshotOptions* snapshotOptions);| 销毁截图选项指针。|
| int32_t [OH_ArkUI_SnapshotOptions_SetScale](#oh_arkui_snapshotoptions_setscale)(ArkUI_SnapshotOptions* snapshotOptions, float scale);| 配置截图选项中的缩放属性。|
| [ArkUI_VisibleAreaEventOptions](#arkui_visibleareaeventoptions) \* [OH_ArkUI_VisibleAreaEventOptions_Create](#oh_arkui_visibleareaeventoptions_create) (void) | 创建可见区域变化监听的参数。  | 
| void [OH_ArkUI_VisibleAreaEventOptions_Dispose](#oh_arkui_visibleareaeventoptions_dispose)(ArkUI_VisibleAreaEventOptions \*option) | 销毁可见区域变化监听的参数。<br/>**起始版本：** 17  | 
| int32_t [OH_ArkUI_VisibleAreaEventOptions_SetRatios](#oh_arkui_visibleareaeventoptions_setratios) ([ArkUI_VisibleAreaEventOptions](#arkui_visibleareaeventoptions) \*option, float\* value, int32_t size) | 设置阈值数组。<br/>**起始版本：** 17  | 
| int32_t [OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval](#oh_arkui_visibleareaeventoptions_setexpectedupdateinterval) ([ArkUI_VisibleAreaEventOptions](#arkui_visibleareaeventoptions) \*option, int32_t value) | 设置预期更新间隔，单位为ms。定义了开发者期望的更新间隔。<br/>**起始版本：** 17 |
| int32_t [OH_ArkUI_VisibleAreaEventOptions_GetRatios](#oh_arkui_visibleareaeventoptions_getratios) ([ArkUI_VisibleAreaEventOptions](#arkui_visibleareaeventoptions) \*option, float\* value, int32_t\* size) | 获取阈值数组。<br/>**起始版本：** 17  | 
| int32_t [OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval](#oh_arkui_visibleareaeventoptions_getexpectedupdateinterval) ([ArkUI_VisibleAreaEventOptions](#arkui_visibleareaeventoptions) \*option,) |  获取预期更新间隔。<br/>**起始版本：** 17 | 
| int32_t [OH_ArkUI_EnableDropDisallowedBadge](#oh_arkui_enabledropdisallowedbadge) ([ArkUI_ContextHandle](#arkui_contexthandle-12) uiContext, bool enabled) | 设置是否可以显示禁用角标。<br />**起始版本：** 20  | 


## 宏定义说明


### OH_ArkUI_GetModuleInterface

```
#define OH_ArkUI_GetModuleInterface( nativeAPIVariantKind,  structType,  structPtr )
```
**Value:**
```
 do { \
 void* anyNativeAPI = OH_ArkUI_QueryModuleInterfaceByName(nativeAPIVariantKind, #structType); \
 if (anyNativeAPI) { \
 structPtr = (structType*)(anyNativeAPI); \
 } \
 } while (0)
#include<arkui/native_interface.h>
#include<arkui/native_node.h>
 
ArkUI_NativeNodeAPI_1* nativeNodeApi = nullptr;
OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, nativeNodeApi);
```
**描述：**

基于结构体类型获取对应结构体指针的宏函数。

**起始版本：** 12


## 类型定义说明


### ArkUI_AccessibilityState

```
typedef struct ArkUI_AccessibilityState ArkUI_AccessibilityState
```
**描述：**

定义组件无障碍状态。

**起始版本：** 12


### ArkUI_AccessibilityValue

```
typedef struct ArkUI_AccessibilityValue ArkUI_AccessibilityValue
```
**描述：**

定义组件无障碍信息值。

**起始版本：** 12


### ArkUI_AlignmentRuleOption

```
typedef struct ArkUI_AlignmentRuleOption ArkUI_AlignmentRuleOption
```
**描述：**

指定设置在相对容器中子组件的对齐规则。

**起始版本：** 12


### ArkUI_AnimateOption

```
typedef struct ArkUI_AnimateOption ArkUI_AnimateOption
```
**描述：**

设置动画效果相关参数。

**起始版本：** 12


### ArkUI_AnimatorHandle

```
typedef struct ArkUI_Animator* ArkUI_AnimatorHandle
```
**描述：**

定义animator动画对象指针。

**起始版本：** 12


### ArkUI_AnimatorEvent

```
typedef struct ArkUI_AnimatorEvent ArkUI_AnimatorEvent
```
**描述：**

定义animator回调事件对象。

**起始版本：** 12


### ArkUI_AnimatorOnFrameEvent

```
typedef struct ArkUI_AnimatorOnFrameEvent ArkUI_AnimatorOnFrameEvent
```
**描述：**

定义animator接收到帧时回调对象。

**起始版本：** 12


### ArkUI_AnimatorOption

```
typedef struct ArkUI_AnimatorOption ArkUI_AnimatorOption
```
**描述：**

定义animator动画参数对象。

**起始版本：** 12


### ArkUI_BarrierOption

```
typedef struct ArkUI_BarrierOption ArkUI_BarrierOption
```
**描述：**

barrier参数，用于定义barrier的id、方向和生成时所依赖的组件。

**起始版本：** 12


### ArkUI_Context

```
typedef struct ArkUI_Context ArkUI_Context
```
**描述：**

native UI的上下文实例对象。

**起始版本：** 12


### ArkUI_ContextHandle [1/2]

```
typedef struct ArkUI_Context* ArkUI_ContextHandle
```
**描述：**

native UI的上下文实例对象指针定义。

**起始版本：** 12


### ArkUI_ContextHandle [2/2]

```
typedef struct ArkUI_Context* ArkUI_ContextHandle
```
**描述：**

定义ArkUI native UI的上下文实例对象指针定义。

**起始版本：** 12

### ArkUI_Curve

```
typedef struct ArkUI_Curve ArkUI_Curve
```
**描述：**

提供曲线的插值对象定义。

**起始版本：** 12


### ArkUI_CurveHandle

```
typedef struct ArkUI_Curve* ArkUI_CurveHandle
```
**描述：**

定义曲线的插值对象指针定义。

**起始版本：** 12


### ArkUI_CustomSpanDrawInfo

```
typedef struct ArkUI_CustomSpanDrawInfo ArkUI_CustomSpanDrawInfo
```
**描述：**

自定义段落组件的绘制信息。

**起始版本：** 12


### ArkUI_CustomSpanMeasureInfo

```
typedef struct ArkUI_CustomSpanMeasureInfo ArkUI_CustomSpanMeasureInfo
```
**描述：**

自定义段落组件的测量信息。

**起始版本：** 12


### ArkUI_CustomSpanMetrics

```
typedef struct ArkUI_CustomSpanMetrics ArkUI_CustomSpanMetrics
```
**描述：**

自定义段落组件的度量指标。

**起始版本：** 12


### ArkUI_DialogDismissEvent

```
typedef struct ArkUI_DialogDismissEvent ArkUI_DialogDismissEvent
```
**描述：**

定义弹窗关闭事件对象。

**起始版本：** 12

### ArkUI_CustomDialogOptions

```
typedef struct ArkUI_CustomDialogOptions ArkUI_CustomDialogOptions
```
**描述：**

定义自定义弹窗的内容对象。

**起始版本：** 19


### ArkUI_DragAction

```
typedef struct ArkUI_DragAction ArkUI_DragAction
```
**描述：**

拖拽行为，用于主动发起拖拽。

**起始版本：** 12


### ArkUI_DragAndDropInfo

```
typedef struct ArkUI_DragAndDropInfo ArkUI_DragAndDropInfo
```
**描述：**

主动发起拖拽后，通过拖拽状态监听返回的系统拖拽相关数据。

**起始版本：** 12

### ArkUI_DragEvent

```
typedef struct ArkUI_DragEvent ArkUI_DragEvent
```
**描述：**

拖拽事件。

**起始版本：** 12


### ArkUI_DragPreviewOption

```
typedef struct ArkUI_DragPreviewOption ArkUI_DragPreviewOption
```
**描述：**

设置拖拽跟手图的相关自定义参数。

**起始版本：** 12


### ArkUI_DrawableDescriptor

```
typedef struct ArkUI_DrawableDescriptor ArkUI_DrawableDescriptor
```
**描述：**

定义 DrawableDescriptor 对象。

**起始版本：** 12


### ArkUI_DrawContext

```
typedef struct ArkUI_DrawContext ArkUI_DrawContext
```
**描述：**

定义组件绘制上下文类型结构。

**起始版本：** 12


### ArkUI_GestureDirectionMask

```
typedef uint32_t ArkUI_GestureDirectionMask
```
**描述：**

定义滑动手势方向集合。

**起始版本：** 12


### ArkUI_GestureEvent

```
typedef struct ArkUI_GestureEvent ArkUI_GestureEvent
```

**描述：**

提供手势事件数据类型对象定义。

**起始版本：** 12


### ArkUI_GestureEventActionTypeMask

```
typedef uint32_t ArkUI_GestureEventActionTypeMask
```
**描述：**

定义手势事件类型集合。

例：ArkUI_GestureEventActionTypeMask actions = GESTURE_EVENT_ACTION_ACCEPT | GESTURE_EVENT_ACTION_UPDATE;

**起始版本：** 12


### ArkUI_GestureEventTargetInfo

```
typedef struct ArkUI_GestureEventTargetInfo ArkUI_GestureEventTargetInfo
```
**描述：**

提供手势事件目标信息类型对象定义。

**起始版本：** 12


### ArkUI_GestureRecognizer

```
typedef struct ArkUI_GestureRecognizer ArkUI_GestureRecognizer
```

**描述：**

提供手势组件实例对象定义。

**起始版本：** 12


### ArkUI_GestureRecognizerDisposeNotifyCallback

```
typedef void(* ArkUI_GestureRecognizerDisposeNotifyCallback) (ArkUI_GestureRecognizer *recognizer, void *userData)
```
**描述：**

定义手势识别器析构通知事件的回调函数类型。

**起始版本：** 12


### ArkUI_GestureRecognizerHandle

```
typedef ArkUI_GestureRecognizer* ArkUI_GestureRecognizerHandle
```
**描述：**

提供手势识别器句柄类型对象定义。

**起始版本：** 12


### ArkUI_GestureRecognizerHandleArray

```
typedef ArkUI_GestureRecognizerHandle* ArkUI_GestureRecognizerHandleArray
```
**描述：**

提供手势识别器句柄类型数组对象定义。

**起始版本：** 12


### ArkUI_TouchRecognizer

```
typedef ArkUI_TouchRecognizer ArkUI_TouchRecognizer
```
**描述：**

定义触摸识别器。

**起始版本：** 15


### ArkUI_TouchRecognizerHandle

```
typedef ArkUI_TouchRecognizer* ArkUI_TouchRecognizerHandle
```
**描述：**

提供触摸识别器句柄类型对象定义。

**起始版本：** 15


### ArkUI_TouchRecognizerHandleArray

```
typedef ArkUI_TouchRecognizerHandle* ArkUI_TouchRecognizerHandleArray
```
**描述：**

提供触摸识别器句柄类型数组对象定义。

**起始版本：** 15

### ArkUI_GuidelineOption

```
typedef struct ArkUI_GuidelineOption ArkUI_GuidelineOption
```
**描述：**

guideLine参数，用于定义guideline的id、方向和位置。

**起始版本：** 12


### ArkUI_ImageAnimatorFrameInfo

```
typedef struct ArkUI_ImageAnimatorFrameInfo ArkUI_ImageAnimatorFrameInfo
```
**描述：**

定义图片帧信息。

**起始版本：** 12


### ArkUI_KeyframeAnimateOption

```
typedef struct ArkUI_KeyframeAnimateOption ArkUI_KeyframeAnimateOption
```
**描述：**

定义关键帧动画参数对象。

**起始版本：** 12


### ArkUI_LayoutConstraint

```
typedef struct ArkUI_LayoutConstraint ArkUI_LayoutConstraint
```
**描述：**

约束尺寸，组件布局时，进行尺寸范围限制。

**起始版本：** 12


### ArkUI_ListChildrenMainSize

```
typedef struct ArkUI_ListChildrenMainSize ArkUI_ListChildrenMainSize
```
**描述：**

定义List的ChildrenMainSize类信息。

**起始版本：** 12


### ArkUI_ListItemSwipeActionItem

```
typedef struct ArkUI_ListItemSwipeActionItem ArkUI_ListItemSwipeActionItem
```
**描述：**

定义ListItemSwipeActionOption方法内Item的配置信息。

**起始版本：** 12


### ArkUI_ListItemSwipeActionOption

```
typedef struct ArkUI_ListItemSwipeActionOption ArkUI_ListItemSwipeActionOption
```
**描述：**

定义ListItemSwipeActionOption方法的配置信息。

**起始版本：** 12


### ArkUI_NativeDialogHandle

```
typedef struct ArkUI_NativeDialog* ArkUI_NativeDialogHandle
```
**描述：**

定义ArkUI在Native侧的自定义弹窗控制器对象指针。

**起始版本：** 12


### ArkUI_NodeAdapterEvent

```
typedef struct ArkUI_NodeAdapterEvent ArkUI_NodeAdapterEvent
```
**描述：**

定义适配器事件对象。

**起始版本：** 12


### ArkUI_NodeAdapterHandle

```
typedef struct ArkUI_NodeAdapter* ArkUI_NodeAdapterHandle
```
**描述：**

定义组件适配器对象，用于滚动类组件的元素懒加载。

**起始版本：** 12


### ArkUI_NodeContentCallback

```
typedef void(* ArkUI_NodeContentCallback) (ArkUI_NodeContentEvent *event)
```
**描述：**

定义NodeContent事件的回调函数类型。

**起始版本：** 12


### ArkUI_NodeContentEvent

```
typedef struct ArkUI_NodeContentEvent ArkUI_NodeContentEvent
```
**描述：**

定义NodeContent事件的通用结构类型。

**起始版本：** 12


### ArkUI_NodeContentHandle

```
typedef struct ArkUI_NodeContent* ArkUI_NodeContentHandle
```
**描述：**

定义ArkUI NodeContent实例在Native侧的实例对象指针定义。

**起始版本：** 12


### ArkUI_NodeCustomEvent

```
typedef struct ArkUI_NodeCustomEvent ArkUI_NodeCustomEvent
```
**描述：**

定义自定义组件事件的通用结构类型。

**起始版本：** 12


### ArkUI_NodeEvent [1/2]

```
typedef struct ArkUI_NodeEvent ArkUI_NodeEvent
```
**描述：**

组件事件的通用结构类型。

**起始版本：** 12


### ArkUI_NodeEvent [2/2]

```
typedef struct ArkUI_NodeEventArkUI_NodeEvent
```
**描述：**

定义组件事件的通用结构类型。

**起始版本：** 12


### ArkUI_NodeHandle

```
typedef struct ArkUI_Node* ArkUI_NodeHandle
```
**描述：**

定义ArkUI native组件实例对象指针定义。

**起始版本：** 12


### ArkUI_OnWillDismissEvent

```
typedef bool(* ArkUI_OnWillDismissEvent) (int32_t reason)
```
**描述：**

弹窗关闭的回调函数。

**起始版本：** 12


### ArkUI_ParallelInnerGestureEvent

```
typedef struct ArkUI_ParallelInnerGestureEvent ArkUI_ParallelInnerGestureEvent
```
**描述：**

提供并行内部手势事件类型对象定义。

**起始版本：** 12


### ArkUI_GestureInterruptInfo

```
typedef struct ArkUI_GestureInterruptInfo ArkUI_GestureInterruptInfo
```

**描述：**

提供手势中断信息对象定义。

**起始版本：** 12


### ArkUI_StyledString

```
typedef struct ArkUI_StyledString ArkUI_StyledString
```
**描述：**

定义文本组件支持的格式化字符串数据对象。

**起始版本：** 12


### ArkUI_StyledString_Descriptor

```
typedef struct ArkUI_StyledString_Descriptor ArkUI_StyledString_Descriptor
```
**描述：**

定义文本组件支持的属性字符串的数据对象。

**起始版本：** 14


### ArkUI_SwiperIndicator

```
typedef struct ArkUI_SwiperIndicator ArkUI_SwiperIndicator
```
**描述：**

定义 Swiper 组件的导航指示器风格。

**起始版本：** 12


### ArkUI_SystemFontStyleEvent

```
typedef struct ArkUI_SystemFontStyleEvent ArkUI_SystemFontStyleEvent
```
**描述：**

系统字体变更事件定义。

**起始版本：** 12

### ArkUI_SwiperDigitIndicator

```
typedef struct ArkUI_SwiperDigitIndicator ArkUI_SwiperDigitIndicator
```
**描述：**

定义 Swiper 组件的数字导航指示器风格。

**起始版本：** 19

### ArkUI_SwiperArrowStyle

```
typedef struct ArkUI_SwiperArrowStyle ArkUI_SwiperArrowStyle
```
**描述：**

定义 Swiper 组件的导航箭头风格。

**起始版本：** 19

### ArkUI_TransitionEffect

```
typedef struct ArkUI_TransitionEffect ArkUI_TransitionEffect
```
**描述：**

定义transition属性配置转场参数对象。

**起始版本：** 12


### ArkUI_WaterFlowSectionOption

```
typedef struct ArkUI_WaterFlowSectionOption ArkUI_WaterFlowSectionOption
```
**描述：**

定义FlowItem分组配置信息。

**起始版本：** 12


### OH_PixelmapNative

```
struct OH_PixelmapNative OH_PixelmapNative
```
**描述：**

Pixelmap结构体类型，用于执行Pixelmap相关操作。

**起始版本：** 12


### OH_PixelmapNativeHandle

```
typedef struct OH_PixelmapNative* OH_PixelmapNativeHandle
```
**描述：**

定义OH_PixelmapNative对象指针类型。

**起始版本：** 12


### OH_UdmfData

```
typedef struct OH_UdmfData OH_UdmfData
```
**描述：**

UDMF 统一数据定义。

**起始版本：** 12


### ArkUI_ProgressLinearStyleOption

```
typedef struct ArkUI_ProgressLinearStyleOption ArkUI_ProgressLinearStyleOption
```
**描述：**

定义Progress的ProgressLinearStyle信息。

**起始版本：** 15

### ArkUI_HostWindowInfo

```
typedef struct ArkUI_HostWindowInfo ArkUI_HostWindowInfo
```
**描述：**

定义窗口属性的HostWindowInfo类信息。

**起始版本：** 15


### OH_UdmfGetDataParams

```
typedef struct OH_UdmfGetDataParams OH_UdmfGetDataParams
```
**描述：**

从UDMF获取数据时的参数。

**起始版本：** 15

### ArkUI_VisibleAreaEventOptions

```
typedef struct ArkUI_VisibleAreaEventOptions ArkUI_VisibleAreaEventOptions
```
**描述：**

可见区域变化监听的参数。

**起始版本：** 17


### ArkUI_TextPickerRangeContentArray
```
typedef struct ArkUI_TextPickerRangeContentArray ArkUI_TextPickerRangeContentArray
```
**描述：**

定义文本选择器的数据选择列表。

**起始版本：** 19

### ArkUI_TextCascadePickerRangeContentArray

```
typedef struct ArkUI_TextCascadePickerRangeContentArray ArkUI_TextCascadePickerRangeContentArray
```
**描述：**

定义多列联动数据选择器的多列联动数据选择列表。

**起始版本：** 19

### ArkUI_SnapshotOptions

```
typedef struct ArkUI_SnapshotOptions ArkUI_SnapshotOptions
```

**描述**

定义截图的可选项。

**起始版本：** 15

### ArkUI_CustomProperty

```
typedef struct ArkUI_CustomProperty ArkUI_CustomProperty
```
**描述：**

定义自定义属性的CustomProperty类信息。

**起始版本：** 14


### ArkUI_ActiveChildrenInfo

```
typedef struct ArkUI_ActiveChildrenInfo ArkUI_ActiveChildrenInfo
```
**描述：**

定义ActiveChildrenInfo类信息。

**起始版本：** 14

### AbilityBase_Want

```
typedef struct AbilityBase_Want AbilityBase_Want
```
**描述：**

声明want。

**起始版本：** 20

### ArkUI_EmbeddedComponentOption

```
typedef struct ArkUI_EmbeddedComponentOption ArkUI_EmbeddedComponentOption
```
**描述：**

为EmbeddedComponent定义EmbeddedComponentOption。

**起始版本：** 20


## 枚举类型说明


### ArkUI_AccessibilityActionType

```
enum ArkUI_AccessibilityActionType
```
**描述：**

定义无障碍操作类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ACCESSIBILITY_ACTION_CLICK  | 点击操作。  |
| ARKUI_ACCESSIBILITY_ACTION_LONG_CLICK  | 长按操作。  |
| ARKUI_ACCESSIBILITY_ACTION_CUT  | 剪切操作。  |
| ARKUI_ACCESSIBILITY_ACTION_COPY  | 复制操作。  |
| ARKUI_ACCESSIBILITY_ACTION_PASTE  | 粘贴操作。  |


### ArkUI_AccessibilityCheckedState

```
enum ArkUI_AccessibilityCheckedState
```
**描述：**

定义无障碍复选框状态类型枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ACCESSIBILITY_UNCHECKED  | 复选框未被选中。  |
| ARKUI_ACCESSIBILITY_CHECKED  | 复选框被选中。  |


### ArkUI_AccessibilityMode

```
enum ArkUI_AccessibilityMode
```
**描述：**

定义无障碍辅助服务模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ACCESSIBILITY_MODE_AUTO  | 根据组件不同会转换为“enabled”或者“disabled”。  |
| ARKUI_ACCESSIBILITY_MODE_ENABLED  | 当前组件可被无障碍辅助服务所识别。  |
| ARKUI_ACCESSIBILITY_MODE_DISABLED  | 当前组件不可被无障碍辅助服务所识别。  |
| ARKUI_ACCESSIBILITY_MODE_DISABLED_FOR_DESCENDANTS  | 当前组件及其所有子组件不可被无障碍辅助服务所识别。  |


### ArkUI_AdaptiveColor

```
enum ArkUI_AdaptiveColor
```
**描述：**

定义取色模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ADAPTIVE_COLOR_DEFAULT  | 不使用取色模糊。  |
| ARKUI_ADAPTIVE_COLOR_AVERAGE  | 使用取色模糊。  |


### ArkUI_Alignment

```
enum ArkUI_Alignment
```
**描述：**

定义布局对齐枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ALIGNMENT_TOP_START  | 顶部起始。  |
| ARKUI_ALIGNMENT_TOP  | 顶部居中。  |
| ARKUI_ALIGNMENT_TOP_END  | 顶部尾端。  |
| ARKUI_ALIGNMENT_START  | 起始端纵向居中。  |
| ARKUI_ALIGNMENT_CENTER  | 横向和纵向居中。  |
| ARKUI_ALIGNMENT_END  | 尾端纵向居中。  |
| ARKUI_ALIGNMENT_BOTTOM_START  | 底部起始端。  |
| ARKUI_ALIGNMENT_BOTTOM  | 底部横向居中。  |
| ARKUI_ALIGNMENT_BOTTOM_END  | 底部尾端。  |


### ArkUI_AnimationCurve

```
enum ArkUI_AnimationCurve
```
**描述：**

动画曲线枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_CURVE_LINEAR  | 动画从头到尾的速度都是相同。  |
| ARKUI_CURVE_EASE  | 动画以低速开始，然后加快，在结束前变慢。  |
| ARKUI_CURVE_EASE_IN  | 动画以低速开始。  |
| ARKUI_CURVE_EASE_OUT  | 动画以低速结束。  |
| ARKUI_CURVE_EASE_IN_OUT  | 动画以低速开始和结束。  |
| ARKUI_CURVE_FAST_OUT_SLOW_IN  | 动画标准曲线。  |
| ARKUI_CURVE_LINEAR_OUT_SLOW_IN  | 动画减速曲线。  |
| ARKUI_CURVE_FAST_OUT_LINEAR_IN  | 动画加速曲线。  |
| ARKUI_CURVE_EXTREME_DECELERATION  | 动画急缓曲线。  |
| ARKUI_CURVE_SHARP  | 动画锐利曲线。  |
| ARKUI_CURVE_RHYTHM  | 动画节奏曲线。  |
| ARKUI_CURVE_SMOOTH  | 动画平滑曲线。  |
| ARKUI_CURVE_FRICTION  | 动画阻尼曲线。  |


### ArkUI_AnimationDirection

```
enum ArkUI_AnimationDirection
```
**描述：**

动画播放模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ANIMATION_DIRECTION_NORMAL  | 动画正向循环播放。  |
| ARKUI_ANIMATION_DIRECTION_REVERSE  | 动画反向循环播放。  |
| ARKUI_ANIMATION_DIRECTION_ALTERNATE  | 动画交替循环播放，奇数次正向播放，偶数次反向播放。  |
| ARKUI_ANIMATION_DIRECTION_ALTERNATE_REVERSE  | 动画反向交替循环播放，奇数次反向播放，偶数次正向播放。  |


### ArkUI_AnimationFillMode

```
enum ArkUI_AnimationFillMode
```
**描述：**

定义帧动画组件在动画开始前和结束后的状态。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ANIMATION_FILL_MODE_NONE  | 动画未执行时不会将任何样式应用于目标，动画播放完成之后恢复初始默认状态。  |
| ARKUI_ANIMATION_FILL_MODE_FORWARDS  | 目标将保留动画执行期间最后一个关键帧的状态。  |
| ARKUI_ANIMATION_FILL_MODE_BACKWARDS  | 动画将在应用于目标时立即应用第一个关键帧中定义的值，并在delay期间保留此值。  |
| ARKUI_ANIMATION_FILL_MODE_BOTH  | 动画将遵循Forwards和Backwards的规则，从而在两个方向上扩展动画属性。  |


### ArkUI_AnimationPlayMode

```
enum ArkUI_AnimationPlayMode
```
**描述：**

定义动画播放模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ANIMATION_PLAY_MODE_NORMAL  | 动画正向播放。  |
| ARKUI_ANIMATION_PLAY_MODE_REVERSE  | 动画反向播放。  |
| ARKUI_ANIMATION_PLAY_MODE_ALTERNATE  | 动画在奇数次（1、3、5...）正向播放，在偶数次（2、4、6...）反向播放。  |
| ARKUI_ANIMATION_PLAY_MODE_ALTERNATE_REVERSE  | 动画在奇数次（1、3、5...）反向播放，在偶数次（2、4、6...）正向播放。  |


### ArkUI_AnimationStatus

```
enum ArkUI_AnimationStatus
```
**描述：**

定义帧动画的播放状态。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ANIMATION_STATUS_INITIAL  | 动画初始状态。  |
| ARKUI_ANIMATION_STATUS_RUNNING  | 动画处于播放状态。  |
| ARKUI_ANIMATION_STATUS_PAUSED  | 动画处于暂停状态。  |
| ARKUI_ANIMATION_STATUS_STOPPED  | 动画处于停止状态。  |


### ArkUI_Axis

```
enum ArkUI_Axis
```
**描述：**

定义滚动方向和List组件排列方向枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_AXIS_VERTICAL  | 仅支持竖直方向滚动。  |
| ARKUI_AXIS_HORIZONTAL  | 仅支持水平方向滚动。  |


### ArkUI_BarrierDirection

```
enum ArkUI_BarrierDirection
```
**描述：**

定义屏障线的方向。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_BARRIER_DIRECTION_START  | 屏障在其所有referencedId的最左侧。  |
| ARKUI_BARRIER_DIRECTION_END  | 屏障在其所有referencedId的最右侧。  |
| ARKUI_BARRIER_DIRECTION_TOP  | 屏障在其所有referencedId的最上方。  |
| ARKUI_BARRIER_DIRECTION_BOTTOM  | 屏障在其所有referencedId的最下方。  |


### ArkUI_BlendApplyType

```
enum ArkUI_BlendApplyType
```
**描述：**

指定的混合模式应用于视图的内容选项。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| BLEND_APPLY_TYPE_FAST  | 在目标图像上按顺序混合视图的内容。  |
| BLEND_APPLY_TYPE_OFFSCREEN  | 将此组件和子组件内容绘制到离屏画布上，然后整体进行混合。 |


### ArkUI_BlendMode

```
enum ArkUI_BlendMode
```
**描述：**

混合模式枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_BLEND_MODE_NONE  | 将上层图像直接覆盖到下层图像上，不进行任何混合操作。  |
| ARKUI_BLEND_MODE_CLEAR  | 将源像素覆盖的目标像素清除为完全透明。  |
| ARKUI_BLEND_MODE_SRC  | r = s，只显示源像素。  |
| ARKUI_BLEND_MODE_DST  | r = d，只显示目标像素。  |
| ARKUI_BLEND_MODE_SRC_OVER  | r = s + (1 - sa) \* d，将源像素按照透明度进行混合，覆盖在目标像素上。  |
| ARKUI_BLEND_MODE_DST_OVER  | r = d + (1 - da) \* s，将目标像素按照透明度进行混合，覆盖在源像素上。  |
| ARKUI_BLEND_MODE_SRC_IN  | r = s \* da，只显示源像素中与目标像素重叠的部分。  |
| ARKUI_BLEND_MODE_DST_IN  | r = d \* sa，只显示目标像素中与源像素重叠的部分。  |
| ARKUI_BLEND_MODE_SRC_OUT  | r = s \* (1 - da)，只显示源像素中与目标像素不重叠的部分。  |
| ARKUI_BLEND_MODE_DST_OUT  | r = d \* (1 - sa)，只显示目标像素中与源像素不重叠的部分。  |
| ARKUI_BLEND_MODE_SRC_ATOP  | r = s \* da + d \* (1 - sa)，在源像素和目标像素重叠的地方绘制源像素，在源像素和目标像素不重叠的地方绘制目标像素。  |
| ARKUI_BLEND_MODE_DST_ATOP  | r = d \* sa + s \* (1 - da)，在源像素和目标像素重叠的地方绘制目标像素，在源像素和目标像素不重叠的地方绘制源像素。  |
| ARKUI_BLEND_MODE_XOR  | r = s \* (1 - da) + d \* (1 - sa)，只显示源像素与目标像素不重叠的部分。  |
| ARKUI_BLEND_MODE_PLUS  | r = min(s + d, 1)，将源像素值与目标像素值相加，并将结果作为新的像素值。  |
| ARKUI_BLEND_MODE_MODULATE  | r = s \* d，将源像素与目标像素进行乘法运算，并将结果作为新的像素值。  |
| ARKUI_BLEND_MODE_SCREEN  | r = s + d - s \* d，将两个图像的像素值相加，然后减去它们的乘积来实现混合。  |
| ARKUI_BLEND_MODE_OVERLAY  | 根据目标像素来决定使用MULTIPLY混合模式还是SCREEN混合模式。  |
| ARKUI_BLEND_MODE_DARKEN  | rc = s + d - max(s \* da, d \* sa), ra = kSrcOver，当两个颜色重叠时，较暗的颜色会覆盖较亮的颜色。  |
| ARKUI_BLEND_MODE_LIGHTEN  | rc = s + d - min(s \* da, d \* sa), ra = kSrcOver，将源图像和目标图像中的像素进行比较，选取两者中较亮的像素作为最终的混合结果。  |
| ARKUI_BLEND_MODE_COLOR_DODGE  | 使目标像素变得更亮来反映源像素。  |
| ARKUI_BLEND_MODE_COLOR_BURN  | 使目标像素变得更暗来反映源像素。  |
| ARKUI_BLEND_MODE_HARD_LIGHT  | 根据源像素的值来决定目标像素变得更亮或者更暗。根据源像素来决定使用MULTIPLY混合模式还是SCREEN混合模式。  |
| ARKUI_BLEND_MODE_SOFT_LIGHT  | 根据源像素来决定使用LIGHTEN混合模式还是DARKEN混合模式。  |
| ARKUI_BLEND_MODE_DIFFERENCE  | rc = s + d - 2 \* (min(s \* da, d \* sa)), ra = kSrcOver，对比源像素和目标像素，亮度更高的像素减去亮度更低的像素，产生高对比度的效果。  |
| ARKUI_BLEND_MODE_EXCLUSION  | rc = s + d - two(s \* d), ra = kSrcOver，对比源像素和目标像素，亮度更高的像素减去亮度更低的像素，产生柔和的效果。  |
| ARKUI_BLEND_MODE_MULTIPLY  | r = s \* (1 - da) + d \* (1 - sa) + s \* d，将源图像与目标图像进行乘法混合，得到一张新的图像。 |
| ARKUI_BLEND_MODE_HUE  | 保留源图像的亮度和饱和度，但会使用目标图像的色调来替换源图像的色调。  |
| ARKUI_BLEND_MODE_SATURATION  | 保留目标像素的亮度和色调，但会使用源像素的饱和度来替换目标像素的饱和度。  |
| ARKUI_BLEND_MODE_COLOR  | 保留源像素的饱和度和色调，但会使用目标像素的亮度来替换源像素的亮度。  |
| ARKUI_BLEND_MODE_LUMINOSITY  | 保留目标像素的色调和饱和度，但会用源像素的亮度替换目标像素的亮度。  |


### ArkUI_BlurStyle

```
enum ArkUI_BlurStyle
```
**描述：**

定义背景模糊样式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_BLUR_STYLE_THIN  | 轻薄材质模糊。  |
| ARKUI_BLUR_STYLE_REGULAR  | 普通厚度材质模糊。  |
| ARKUI_BLUR_STYLE_THICK  | 厚材质模糊。  |
| ARKUI_BLUR_STYLE_BACKGROUND_THIN  | 近距景深模糊。  |
| ARKUI_BLUR_STYLE_BACKGROUND_REGULAR  | 中距景深模糊。  |
| ARKUI_BLUR_STYLE_BACKGROUND_THICK  | 远距景深模糊。  |
| ARKUI_BLUR_STYLE_BACKGROUND_ULTRA_THICK  | 超远距景深模糊。  |
| ARKUI_BLUR_STYLE_NONE  | 关闭模糊。  |
| ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THIN  | 组件超轻薄材质模糊。  |
| ARKUI_BLUR_STYLE_COMPONENT_THIN  | 组件轻薄材质模糊。  |
| ARKUI_BLUR_STYLE_COMPONENT_REGULAR  | 组件普通材质模糊。  |
| ARKUI_BLUR_STYLE_COMPONENT_THICK  | 组件厚材质模糊。  |
| ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THICK  | 组件超厚材质模糊。  |


### ArkUI_BlurStyleActivePolicy

```
enum ArkUI_BlurStyleActivePolicy
```
**描述：**

定义背景模糊激活策略。

**起始版本：** 19

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_FOLLOWS_WINDOW_ACTIVE_STATE  | 模糊效果跟随窗口焦点状态变化，非焦点不模糊，焦点模糊。  |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_ALWAYS_ACTIVE  | 一直有模糊效果。  |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_ALWAYS_INACTIVE  | 一直无模糊效果。  |


### ArkUI_BorderStyle

```
enum ArkUI_BorderStyle
```
**描述：**

边框线条样式枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_BORDER_STYLE_SOLID  | 显示为一条实线。  |
| ARKUI_BORDER_STYLE_DASHED  | 显示为一系列短的方形虚线。  |
| ARKUI_BORDER_STYLE_DOTTED  | 显示为一系列圆点。  |


### ArkUI_ButtonType

```
enum ArkUI_ButtonType
```
**描述：**

定义按钮样式枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_BUTTON_TYPE_NORMAL  | 普通按钮，默认不带圆角。  |
| ARKUI_BUTTON_TYPE_CAPSULE  | 胶囊型按钮，圆角默认为高度的一半。  |
| ARKUI_BUTTON_TYPE_CIRCLE  | 圆形按钮。  |
| ARKUI_BUTTON_ROUNDED_RECTANGLE | 圆角矩形按钮。<br/>**起始版本：** 19  |


### ArkUI_CalendarAlignment

```
enum ArkUI_CalendarAlignment
```
**描述：**

日历选择器与入口组件对齐方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_CALENDAR_ALIGNMENT_START  | 选择器和入口组件左对齐方式。  |
| ARKUI_CALENDAR_ALIGNMENT_CENTER  | 选择器和入口组件居中对齐方式。  |
| ARKUI_CALENDAR_ALIGNMENT_END  | 选择器和入口组件右对齐方式。  |


### ArkUI_CancelButtonStyle

```
enum ArkUI_CancelButtonStyle
```
**描述：**

定义清除按钮样式枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_CANCELBUTTON_STYLE_CONSTANT  | 清除按钮常显样式。  |
| ARKUI_CANCELBUTTON_STYLE_INVISIBLE  | 清除按钮常隐样式。  |
| ARKUI_CANCELBUTTON_STYLE_INPUT  | 清除按钮输入样式。  |


### ArkUI_CheckboxShape

```
enum ArkUI_CheckboxShape
```
**描述：**

定义CheckBox组件形状。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ArkUI_CHECKBOX_SHAPE_CIRCLE  | 圆形。  |
| ArkUI_CHECKBOX_SHAPE_ROUNDED_SQUARE  | 圆角方形。  |


### ArkUI_ClipType

```
enum ArkUI_ClipType
```
**描述：**

裁剪类型枚举。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_CLIP_TYPE_RECTANGLE  | 矩形类型。  |
| ARKUI_CLIP_TYPE_CIRCLE  | 圆形类型。  |
| ARKUI_CLIP_TYPE_ELLIPSE  | 椭圆形类型。  |
| ARKUI_CLIP_TYPE_PATH  | 路径类型。  |


### ArkUI_ColorMode

```
enum ArkUI_ColorMode
```
**描述：**

定义深浅色模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_COLOR_MODE_SYSTEM  | 跟随系统深浅色模式。  |
| ARKUI_COLOR_MODE_LIGHT  | 固定使用浅色模式。  |
| ARKUI_COLOR_MODE_DARK  | 固定使用深色模式。  |


### ArkUI_ColorStrategy

```
enum ArkUI_ColorStrategy
```
**描述：**

前景色枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_COLOR_STRATEGY_INVERT  | 前景色为控件背景色的反色。  |
| ARKUI_COLOR_STRATEGY_AVERAGE  | 控件背景阴影色为控件背景阴影区域的平均色。  |
| ARKUI_COLOR_STRATEGY_PRIMARY  | 控件背景阴影色为控件背景阴影区域的主色。  |


### ArkUI_CopyOptions

```
enum ArkUI_CopyOptions
```
**描述：**

定义文本复制黏贴模式枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_COPY_OPTIONS_NONE  | 不支持复制。  |
| ARKUI_COPY_OPTIONS_IN_APP  | 支持应用内复制。  |
| ARKUI_COPY_OPTIONS_LOCAL_DEVICE  | 支持设备内复制。  |
| ARKUI_COPY_OPTIONS_CROSS_DEVICE  | 支持跨设备复制。  |


### ArkUI_ContentClipMode

```
enum ArkUI_ContentClipMode
```
**描述：**

定义滚动容器的内容层裁剪区域枚举值。

**起始版本：** 18

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY  | 按内容区裁剪。  |
| ARKUI_CONTENT_CLIP_MODE_BOUNDARY  | 按组件区域裁剪。  |
| ARKUI_CONTENT_CLIP_MODE_SAFE_AREA  | 按组件配置的SafeArea区域裁剪。  |


### ArkUI_Direction

```
enum ArkUI_Direction
```
**描述：**

设置容器元素内主轴方向上的布局枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_DIRECTION_LTR  | 元素从左到右布局。  |
| ARKUI_DIRECTION_RTL  | 元素从右到左布局。  |
| ARKUI_DIRECTION_AUTO  | 使用系统默认布局方向。  |


### ArkUI_DismissReason

```
enum ArkUI_DismissReason
```
**描述：**

弹窗关闭的触发方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| DIALOG_DISMISS_BACK_PRESS  | 系统定义的返回操作、键盘ESC触发。  |
| DIALOG_DISMISS_TOUCH_OUTSIDE  | 点击遮障层触发。  |
| DIALOG_DISMISS_CLOSE_BUTTON  | 点击关闭按钮。  |
| DIALOG_DISMISS_SLIDE_DOWN  | 下拉关闭。  |


### ArkUI_LevelMode

```
enum ArkUI_LevelMode
```
**描述：**

设置弹窗显示层级。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_LEVEL_MODE_OVERLAY  | 显示在应用最上层。  |
| ARKUI_LEVEL_MODE_EMBEDDED  | 嵌入式显示在应用的页面内。  |

### ArkUI_ImmersiveMode

```
enum ArkUI_ImmersiveMode
```
**描述：**

指定嵌入式弹窗的蒙层覆盖区域。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_IMMERSIVE_MODE_DEFAULT  | 弹窗蒙层按照显示页面给定的布局约束显示。  |
| ARKUI_IMMERSIVE_MODE_EXTEND  | 弹窗蒙层可扩展至覆盖状态栏和导航条。  |


### ArkUI_DialogState

```
enum ArkUI_DialogState
```
**描述：**

枚举对话框的状态。

**起始版本：** 20

| 枚举值 | 描述 |
| -------- | -------- |
| DIALOG_UNINITIALIZED  | 未初始化，控制器未与dialog绑定时。  |
| DIALOG_INITIALIZED  | 已初始化，控制器与dialog绑定后。  |
| DIALOG_APPEARING  | 显示中，dialog显示动画过程中。  |
| DIALOG_APPEARED  | 已显示，dialog显示动画结束。  |
| DIALOG_DISAPPEARING  | 消失中，dialog消失动画过程中。  |
| DIALOG_DISAPPEARED  | 已消失，dialog消失动画结束后。  |

### ArkUI_DragPreviewScaleMode

```
enum ArkUI_DragPreviewScaleMode
```
**描述：**

拖拽预览缩放模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_DRAG_PREVIEW_SCALE_AUTO  | 系统根据拖拽场景自动改变跟手点位置，根据规则自动对拖拽背板图进行缩放变换等。  |
| ARKUI_DRAG_PREVIEW_SCALE_DISABLED  | 禁用系统对拖拽背板图的缩放行为。  |


### ArkUI_DragResult

```
enum ArkUI_DragResult
```
**描述：**

拖拽结果定义，由数据接收方设置，并由系统传递给数据拖出方，拖出方可感知接收方对数据的处理结果。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_DRAG_RESULT_SUCCESSFUL  | 拖拽处理成功。  |
| ARKUI_DRAG_RESULT_FAILED  | 拖拽处理失败。  |
| ARKUI_DRAG_RESULT_CANCELED  | 拖拽处理取消。  |


### ArkUI_DragStatus

```
enum ArkUI_DragStatus
```
**描述：**

拖拽状态。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ArkUI_DRAG_STATUS_UNKNOWN  | Unknown。  |
| ArkUI_DRAG_STATUS_STARTED  | Started。  |
| ArkUI_DRAG_STATUS_ENDED  | Ended。  |


### ArkUI_DropOperation

```
enum ArkUI_DropOperation
```
**描述：**

定义拖拽释放时的数据处理方式，可影响角标的显示。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_DROP_OPERATION_COPY  | 复制行为。  |
| ARKUI_DROP_OPERATION_MOVE  | 剪切行为。  |


### ArkUI_EdgeEffect

```
enum ArkUI_EdgeEffect
```
**描述：**

定义边缘滑动效果枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_EDGE_EFFECT_SPRING  | 弹性物理动效，滑动到边缘后可以根据初始速度或通过触摸事件继续滑动一段距离，松手后回弹。  |
| ARKUI_EDGE_EFFECT_FADE  | 阴影效果，滑动到边缘后会有圆弧状的阴影。  |
| ARKUI_EDGE_EFFECT_NONE  | 滑动到边缘后无效果。  |


### ArkUI_EffectEdge

```
enum ArkUI_EffectEdge
```
**描述：**

定义边缘效果生效边缘的方向枚举值。

**起始版本：** 18

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_EFFECT_EDGE_START  | 起始边生效。  |
| ARKUI_EFFECT_EDGE_END  | 末尾边生效。  |


### ArkUI_EllipsisMode

```
enum ArkUI_EllipsisMode
```
**描述：**

定义文本省略位置。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ELLIPSIS_MODE_START  | 省略行首内容。  |
| ARKUI_ELLIPSIS_MODE_CENTER  | 省略行中内容。  |
| ARKUI_ELLIPSIS_MODE_END  | 省略行末内容。  |


### ArkUI_EnterKeyType

```
enum ArkUI_EnterKeyType
```
**描述：**

定义单行文本输入法回车键类型枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ENTER_KEY_TYPE_GO  | 显示为开始样式。  |
| ARKUI_ENTER_KEY_TYPE_SEARCH  | 显示为搜索样式。  |
| ARKUI_ENTER_KEY_TYPE_SEND  | 显示为发送样式。  |
| ARKUI_ENTER_KEY_TYPE_NEXT  | 显示为下一个样式。  |
| ARKUI_ENTER_KEY_TYPE_DONE  | 显示为完成样式。  |
| ARKUI_ENTER_KEY_TYPE_PREVIOUS  | 显示为上一个样式。  |
| ARKUI_ENTER_KEY_TYPE_NEW_LINE  | 显示为换行样式。  |


### ArkUI_ErrorCode

```
enum ArkUI_ErrorCode
```
**描述：**

定义错误码枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ERROR_CODE_NO_ERROR  | 无错误。  |
| ARKUI_ERROR_CODE_PARAM_INVALID  | 参数错误。  |
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR  | 接口初始化错误。<br/>起始版本：18  |
| ARKUI_ERROR_CODE_INTERNAL_ERROR  | 出现内部错误，例如内部环境错误导致失败，或者由于内部执行失败导致操作失败。<br/>起始版本：15  |
| ARKUI_ERROR_CODE_XCOMPONENT_STATE_INVALID = 103501  | 当前XComponent状态异常，方法调用失败。<br/>起始版本：19<br/>错误码的详细介绍请参见[XComponent组件错误码](../apis-arkui/errorcode-xcomponent.md)。  |
| ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED = 106102  | 组件不支持特定的属性或者事件。<br/>错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。  |
| ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED = 106103  | 对应的操作不支持ArkTS创建的节点。<br/>错误码的详细介绍请参见[自定义节点错误码](../apis-arkui/errorcode-node.md)。  |
| ARKUI_ERROR_CODE_ADAPTER_NOT_BOUND = 106104 | 懒加载适配器未绑定到组件上，错误码详细参见[编译错误码](../apis-arkui/errorcode-nodeadapter.md#106104-适配器未绑定)。  |
| ARKUI_ERROR_CODE_ADAPTER_EXIST = 106105 | 适配器已存在，错误码详细参见[编译错误码](../apis-arkui/errorcode-nodeadapter.md#106105-适配器已存在)。  |
| ARKUI_ERROR_CODE_CHILD_NODE_EXIST = 106106 | 对应节点已存在子节点，无法添加适配器，错误码详细参见[编译错误码](../apis-arkui/errorcode-nodeadapter.md#106106-子节点已存在)。  |
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE = 106107 | 组件事件中参数长度超限。错误码的详细介绍请参见[106107-参数下标越界](../apis-arkui/errorcode-nodeadapter.md#106107-参数下标越界)。  |
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID = 106108  | 组件事件中不存在该数据。错误码的详细介绍请参见[106108-数据不存在](../apis-arkui/errorcode-nodeadapter.md#106108-数据不存在)。  |
| ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN = 106109 | 组件事件不支持返回值。错误码的详细介绍请参见[106109-不支持返回值](../apis-arkui/errorcode-nodeadapter.md#106109-不支持返回值)。  |
| ARKUI_ERROR_CODE_NODE_INDEX_INVALID = 106200  | 传入的索引值非法。<br/>错误码的详细介绍请参见[导航错误码](../apis-arkui/errorcode-router.md#106200-传入的索引值非法)。  |
| ARKUI_ERROR_CODE_GET_INFO_FAILED = 106201  | 查询路由导航信息失败。 <br/>错误码的详细介绍请参见[导航错误码](../apis-arkui/errorcode-router.md#106201-查询路由导航信息失败)。 |
| ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR = 106202  | 传入的buffer size异常。 <br/>错误码的详细介绍请参见[导航错误码](../apis-arkui/errorcode-router.md#106202-传入的buffer-size异常)。 |
| ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE = 106203  | 传入的节点未挂载到组件树上。<br/>错误码的详细介绍请参见[自定义节点错误码](../apis-arkui/errorcode-node.md)。<br/>起始版本：15  |
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE = 150001  | 当前节点无法获得焦点。<br/>错误码的详细介绍请参见[焦点错误码](../apis-arkui/errorcode-focus.md#150001-节点无法获得焦点)。<br/>起始版本：15  |
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR = 150002  | 当前节点对应的祖先节点中存在无法获焦节点。<br/>错误码的详细介绍请参见[焦点错误码](../apis-arkui/errorcode-focus.md#150002-祖先节点无法获得焦点)。<br/>起始版本：15  |
| ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT = 150003  | 当前节点不存在。<br/>错误码的详细介绍请参见[焦点错误码](../apis-arkui/errorcode-focus.md#150003-节点不存在)。<br/>起始版本：15  |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT = 160002  | 截图超时。<br/>错误码的详细介绍请参见[截图错误码](../apis-arkui/errorcode-snapshot.md)。<br/>起始版本：15  |
| ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER = 180001  | 非滚动类容器。<br/>错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。  |
| ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH = 180002  | 存储区大小不足。<br/>错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。  |
| ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT = 180003  | 该事件不是克隆事件。<br/>错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。<br/>起始版本：15  |
| ARKUI_ERROR_CODE_POST_CLONED_COMPONENT_STATUS_ABNORMAL = 180004  | 组件状态异常。<br/>错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。<br/>起始版本：15  |
| ARKUI_ERROR_CODE_POST_CLONED_NO_COMPONENT_HIT_TO_RESPOND_TO_THE_EVENT = 180005  | 未命中可响应事件的组件。<br/>错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。<br/>起始版本：15  |
| ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED = 180006  | 接口不支持此输入事件类型。<br/>**起始版本：** 20  |
| ARKUI_ERROR_CODE_INVALID_STYLED_STRING = 180101  | 无效的属性字符串。<br/>错误码的详细介绍请参见[属性字符串错误码](../apis-arkui/errorcode-styled-string.md)。<br/>**起始版本：** 14  |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID = 190001  | 无效的UIContext对象。<br/>错误码的详细介绍请参见[UI上下文错误码](../apis-arkui/errorcode-uicontext.md)。<br/>起始版本：18  |
| ARKUI_ERROR_CODE_CALLBACK_INVALID = 190002  | 无效的回调函数。<br/>错误码的详细介绍请参见[UI上下文错误码](../apis-arkui/errorcode-uicontext.md)。<br/>起始版本：18  |
| ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED = 180102  | 不支持手势识别器类型。<br/>错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。<br/>起始版本：18  |
| ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED = 190004  | 当前阶段不允许该操作。<br/>错误码的详细介绍请参见[拖拽事件错误码](../apis-arkui/errorcode-drag-event.md)。<br/>起始版本：19  |


### ArkUI_FinishCallbackType

```
enum ArkUI_FinishCallbackType
```
**描述：**

在动画中定义onFinish回调的类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_FINISH_CALLBACK_REMOVED  | 当整个动画结束并立即删除时，将触发回调。  |
| ARKUI_FINISH_CALLBACK_LOGICALLY  | 当动画在逻辑上处于下降状态，但可能仍处于其长尾状态时，将触发回调。  |


### ArkUI_FlexAlignment

```
enum ArkUI_FlexAlignment
```
**描述：**

定义垂直方向对齐方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_FLEX_ALIGNMENT_START  | 主轴方向首端对齐。  |
| ARKUI_FLEX_ALIGNMENT_CENTER  | 主轴方向中心对齐。  |
| ARKUI_FLEX_ALIGNMENT_END  | 主轴方向尾部对齐。  |
| ARKUI_FLEX_ALIGNMENT_SPACE_BETWEEN  | Flex主轴方向均匀分配弹性元素，相邻元素之间距离相同，第一个元素行首对齐，最后的元素行尾对齐。  |
| ARKUI_FLEX_ALIGNMENT_SPACE_AROUND  | Flex主轴方向均匀分配弹性元素，相邻元素之间距离相同，第一个元素到行首的距离时相邻元素间距离的一半。  |
| ARKUI_FLEX_ALIGNMENT_SPACE_EVENLY  | Flex主轴方向均匀分配弹性元素，相邻元素之间距离、第一个元素到行首的距离和最后的元素到行尾的距离均相等。  |


### ArkUI_FlexDirection

```
enum ArkUI_FlexDirection
```
**描述：**

定义Flex容器的主轴方向。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_FLEX_DIRECTION_ROW  | 主轴与行方向一致。  |
| ARKUI_FLEX_DIRECTION_COLUMN  | 主轴与列方向一致。  |
| ARKUI_FLEX_DIRECTION_ROW_REVERSE  | 主轴与行方向相反。  |
| ARKUI_FLEX_DIRECTION_COLUMN_REVERSE  | 主轴与列方向相反。  |


### ArkUI_FlexWrap

```
enum ArkUI_FlexWrap
```
**描述：**

定义Flex行列布局模式模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_FLEX_WRAP_NO_WRAP  | 单行/单列布局，子项不能超出容器。  |
| ARKUI_FLEX_WRAP_WRAP  | 多行/多列布局，子项允许超出容器。  |
| ARKUI_FLEX_WRAP_WRAP_REVERSE  | 反向多行/多列布局，子项允许超出容器。  |


### ArkUI_FontStyle

```
enum ArkUI_FontStyle
```
**描述：**

定义字体样式枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_FONT_STYLE_NORMAL  | 标准字体样式。  |
| ARKUI_FONT_STYLE_ITALIC  | 斜体字体样式。  |


### ArkUI_FontWeight

```
enum ArkUI_FontWeight
```
**描述：**

定义字体粗细/字重枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_FONT_WEIGHT_W100  | 100  |
| ARKUI_FONT_WEIGHT_W200  | 200  |
| ARKUI_FONT_WEIGHT_W300  | 300  |
| ARKUI_FONT_WEIGHT_W400  | 400  |
| ARKUI_FONT_WEIGHT_W500  | 500  |
| ARKUI_FONT_WEIGHT_W600  | 600  |
| ARKUI_FONT_WEIGHT_W700  | 700  |
| ARKUI_FONT_WEIGHT_W800  | 800  |
| ARKUI_FONT_WEIGHT_W900  | 900  |
| ARKUI_FONT_WEIGHT_BOLD  | 字体较粗。  |
| ARKUI_FONT_WEIGHT_NORMAL  | 字体粗细正常。  |
| ARKUI_FONT_WEIGHT_BOLDER  | 字体非常粗。  |
| ARKUI_FONT_WEIGHT_LIGHTER  | 字体较细。  |
| ARKUI_FONT_WEIGHT_MEDIUM  | 字体粗细适中。  |
| ARKUI_FONT_WEIGHT_REGULAR  | 字体粗细正常。  |


### ArkUI_GestureDirection

```
enum ArkUI_GestureDirection
```
**描述：**

定义滑动手势方向。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| GESTURE_DIRECTION_ALL  | 所有方向。  |
| GESTURE_DIRECTION_HORIZONTAL  | 水平方向。  |
| GESTURE_DIRECTION_VERTICAL  | 竖直方向。  |
| GESTURE_DIRECTION_LEFT  | 向左方向。  |
| GESTURE_DIRECTION_RIGHT  | 向右方向。  |
| GESTURE_DIRECTION_UP  | 向上方向。  |
| GESTURE_DIRECTION_DOWN  | 向下方向。  |
| GESTURE_DIRECTION_NONE  | 任何方向都不触发手势事件。  |


### ArkUI_GestureEventActionType

```
enum ArkUI_GestureEventActionType
```
**描述：**

定义手势事件类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| GESTURE_EVENT_ACTION_ACCEPT  | 手势事件触发。  |
| GESTURE_EVENT_ACTION_UPDATE  | 手势事件更新。  |
| GESTURE_EVENT_ACTION_END  | 手势事件结束。  |
| GESTURE_EVENT_ACTION_CANCEL  | 手势事件取消。  |


### ArkUI_GestureInterruptResult

```
enum ArkUI_GestureInterruptResult
```
**描述：**

定义手势打断结果。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| GESTURE_INTERRUPT_RESULT_CONTINUE  | 手势继续。  |
| GESTURE_INTERRUPT_RESULT_REJECT  | 手势打断。  |


### ArkUI_GestureMask

```
enum ArkUI_GestureMask
```
**描述：**

定义手势屏蔽模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| NORMAL_GESTURE_MASK  | 不屏蔽子组件的手势，按照默认手势识别顺序进行识别。  |
| IGNORE_INTERNAL_GESTURE_MASK  | 屏蔽子组件的手势，包括子组件上系统内置的手势。  |


### ArkUI_GesturePriority

```
enum ArkUI_GesturePriority
```
**描述：**

定义手势事件模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| NORMAL  | 正常手势。  |
| PRIORITY  | 高优先级手势。  |
| PARALLEL  | 并发手势。  |


### ArkUI_GestureRecognizerState

```
enum ArkUI_GestureRecognizerState
```
**描述：**

定义手势识别器状态。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_GESTURE_RECOGNIZER_STATE_READY  | 准备状态。  |
| ARKUI_GESTURE_RECOGNIZER_STATE_DETECTING  | 检测状态。  |
| ARKUI_GESTURE_RECOGNIZER_STATE_PENDING  | 等待状态。  |
| ARKUI_GESTURE_RECOGNIZER_STATE_BLOCKED  | 阻塞状态。  |
| ARKUI_GESTURE_RECOGNIZER_STATE_SUCCESSFUL  | 成功状态。  |
| ARKUI_GESTURE_RECOGNIZER_STATE_FAILED  | 失败状态。  |


### ArkUI_GestureRecognizerType

```
enum ArkUI_GestureRecognizerType
```
**描述：**

定义手势类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| TAP_GESTURE  | 敲击手势。  |
| LONG_PRESS_GESTURE  | 长按手势。  |
| PAN_GESTURE  | 拖动手势。  |
| PINCH_GESTURE  | 捏合手势。  |
| ROTATION_GESTURE  | 旋转手势。  |
| SWIPE_GESTURE  | 滑动手势。  |
| GROUP_GESTURE  | 手势组合。  |
| CLICK_GESTURE  | 通过onClick注册的点击手势。<br/>**起始版本：** 20  |
| DRAG_DROP  | 用于拖放的拖拽手势。<br/>**起始版本：** 20  |


### ArkUI_GroupGestureMode

```
enum ArkUI_GroupGestureMode
```
**描述：**

定义手势组事件模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| SEQUENTIAL_GROUP  | 顺序手势模式，按照注册顺序识别手势，直到所有手势识别成功。若有识别失败，后续识别均失败。仅有最后一个手势响应结束事件。  |
| PARALLEL_GROUP  | 并发手势模式，注册的手势同时识别，直到所有手势识别结束，手势识别互相不影响。  |
| EXCLUSIVE_GROUP  | 互斥手势模式，注册的手势同时识别，若有一个手势识别成功，则结束手势识别。  |


### ArkUI_HitTestMode

```
enum ArkUI_HitTestMode
```
**描述：**

触摸测试控制枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_HIT_TEST_MODE_DEFAULT  | 默认触摸测试效果。自身及子节点响应触摸测试，但阻塞兄弟节点的触摸测试，不影响祖先节点的触摸测试。  |
| ARKUI_HIT_TEST_MODE_BLOCK  | 自身响应触摸测试，阻塞子节点、兄弟节点和祖先节点的触摸测试。  |
| ARKUI_HIT_TEST_MODE_TRANSPARENT  | 自身和子节点都响应触摸测试，不会阻塞兄弟节点和祖先节点的触摸测试。  |
| ARKUI_HIT_TEST_MODE_NONE  | 自身不响应触摸测试，不会阻塞子节点、兄弟节点和祖先节点的触摸测试。  |
| ARKUI_HIT_TEST_MODE_BLOCK_HIERARCHY  | 自身和子节点响应触摸测试，阻止所有优先级较低的兄弟节点和父节点参与触摸测试。<br/>**起始版本：** 20  |
| ARKUI_HIT_TEST_MODE_BLOCK_DESCENDANTS  | 自身不响应触摸测试，并且所有的后代（孩子，孙子等）也不响应触摸测试，不会影响祖先节点的触摸测试。<br/>**起始版本：** 20  |


### ArkUI_HorizontalAlignment

```
enum ArkUI_HorizontalAlignment
```
**描述：**

定义语言方向对齐方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_HORIZONTAL_ALIGNMENT_START  | 按照语言方向起始端对齐。  |
| ARKUI_HORIZONTAL_ALIGNMENT_CENTER  | 居中对齐，默认对齐方式。  |
| ARKUI_HORIZONTAL_ALIGNMENT_END  | 按照语言方向末端对齐。  |


### ArkUI_ImageInterpolation

```
enum ArkUI_ImageInterpolation
```
**描述：**

定义图片插值效果。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_IMAGE_INTERPOLATION_NONE  | 不使用图片插值。  |
| ARKUI_IMAGE_INTERPOLATION_LOW  | 低图片插值。  |
| ARKUI_IMAGE_INTERPOLATION_MEDIUM  | 中图片插值。  |
| ARKUI_IMAGE_INTERPOLATION_HIGH  | 高图片插值，插值质量最高。  |


### ArkUI_ImageRenderMode

```
enum ArkUI_ImageRenderMode
```
**描述：**

定义图片渲染模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL  | 原色渲染模式。  |
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE  | 黑白渲染模式。  |


### ArkUI_ImageRepeat

```
enum ArkUI_ImageRepeat
```
**描述：**

定义图片重复铺设枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_IMAGE_REPEAT_NONE  | 不重复。  |
| ARKUI_IMAGE_REPEAT_X  | 在X轴方向重复。  |
| ARKUI_IMAGE_REPEAT_Y  | 在Y轴方向重复。  |
| ARKUI_IMAGE_REPEAT_XY  | 在X轴和Y轴方向重复。  |


### ArkUI_ImageSize

```
enum ArkUI_ImageSize
```
**描述：**

定义图片宽高样式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_IMAGE_SIZE_AUTO  | 保持原图的比例不变。  |
| ARKUI_IMAGE_SIZE_COVER  | 保持宽高比进行缩小或者放大，使得图片两边都大于或等于显示边界。  |
| ARKUI_IMAGE_SIZE_CONTAIN  | 保持宽高比进行缩小或者放大，使得图片完全显示在显示边界内。  |


### ArkUI_ImageSpanAlignment

```
enum ArkUI_ImageSpanAlignment
```
**描述：**

定义图片基于文本的对齐方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_IMAGE_SPAN_ALIGNMENT_BASELINE  | 图片下边沿与文本BaseLine对齐。  |
| ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM  | 图片下边沿与文本下边沿对齐。  |
| ARKUI_IMAGE_SPAN_ALIGNMENT_CENTER  | 图片中间与文本中间对齐。  |
| ARKUI_IMAGE_SPAN_ALIGNMENT_TOP  | 图片上边沿与文本上边沿对齐。  |
| ARKUI_IMAGE_SPAN_ALIGNMENT_FOLLOW_PARAGRAPH  | 图片对齐方式跟随Text组件对齐方式。<br/>**起始版本：** 20  |


### ArkUI_ItemAlignment

```
enum ArkUI_ItemAlignment
```
**描述：**

设置子组件在父容器交叉轴的对齐格式枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ITEM_ALIGNMENT_AUTO  | 使用Flex容器中默认配置。  |
| ARKUI_ITEM_ALIGNMENT_START  | 元素在Flex容器中，交叉轴方向首部对齐。  |
| ARKUI_ITEM_ALIGNMENT_CENTER  | 元素在Flex容器中，交叉轴方向居中对齐。  |
| ARKUI_ITEM_ALIGNMENT_END  | 元素在Flex容器中，交叉轴方向底部对齐。  |
| ARKUI_ITEM_ALIGNMENT_STRETCH  | 元素在Flex容器中，交叉轴方向拉伸填充。  |
| ARKUI_ITEM_ALIGNMENT_BASELINE  | 元素在Flex容器中，交叉轴方向文本基线对齐。  |


### ArkUI_KeyCode

```
enum ArkUI_KeyCode
```
**描述：**

按键事件的键码

**起始版本：** 14

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_KEYCODE_UNKNOWN  | 未知按键  |
| ARKUI_KEYCODE_FN  | 功能（Fn）键  |
| ARKUI_KEYCODE_VOLUME_UP  | 音量增加键  |
| ARKUI_KEYCODE_VOLUME_DOWN  | 音量减小键  |
| ARKUI_KEYCODE_POWER  | 电源键  |
| ARKUI_KEYCODE_CAMERA  | 拍照键  |
| ARKUI_KEYCODE_VOLUME_MUTE  | 扬声器静音键  |
| ARKUI_KEYCODE_MUTE  | 话筒静音键  |
| ARKUI_KEYCODE_BRIGHTNESS_UP  | 亮度调节按键 调亮  |
| ARKUI_KEYCODE_BRIGHTNESS_DOWN  | 亮度调节按键 调暗  |
| ARKUI_KEYCODE_0  | 按键'0'  |
| ARKUI_KEYCODE_1  | 按键'1'  |
| ARKUI_KEYCODE_2  | 按键'2'  |
| ARKUI_KEYCODE_3  | 按键'3'  |
| ARKUI_KEYCODE_4  | 按键'4'  |
| ARKUI_KEYCODE_5  | 按键'5'  |
| ARKUI_KEYCODE_6  | 按键'6'  |
| ARKUI_KEYCODE_7  | 按键'7'  |
| ARKUI_KEYCODE_8  | 按键'8'  |
| ARKUI_KEYCODE_9  | 按键'9'  |
| ARKUI_KEYCODE_STAR  | 按键'\*'  |
| ARKUI_KEYCODE_POUND  | 按键'\#'  |
| ARKUI_KEYCODE_DPAD_UP  | 导航键 向上  |
| ARKUI_KEYCODE_DPAD_DOWN  | 导航键 向下  |
| ARKUI_KEYCODE_DPAD_LEFT  | 导航键 向左  |
| ARKUI_KEYCODE_DPAD_RIGHT  | 导航键 向右  |
| ARKUI_KEYCODE_DPAD_CENTER  | 导航键 确定键  |
| ARKUI_KEYCODE_A  | 按键'A'  |
| ARKUI_KEYCODE_B  | 按键'B'  |
| ARKUI_KEYCODE_C  | 按键'C'  |
| ARKUI_KEYCODE_D  | 按键'D'  |
| ARKUI_KEYCODE_E  | 按键'E'  |
| ARKUI_KEYCODE_F  | 按键'F'  |
| ARKUI_KEYCODE_G  | 按键'G'  |
| ARKUI_KEYCODE_H  | 按键'H'  |
| ARKUI_KEYCODE_I  | 按键'I'  |
| ARKUI_KEYCODE_J  | 按键'J'  |
| ARKUI_KEYCODE_K  | 按键'K'  |
| ARKUI_KEYCODE_L  | 按键'L'  |
| ARKUI_KEYCODE_M  | 按键'M'  |
| ARKUI_KEYCODE_N  | 按键'N'  |
| ARKUI_KEYCODE_O  | 按键'O'  |
| ARKUI_KEYCODE_P  | 按键'P'  |
| ARKUI_KEYCODE_Q  | 按键'R'  |
| ARKUI_KEYCODE_R  | 按键'R'  |
| ARKUI_KEYCODE_S  | 按键'S'  |
| ARKUI_KEYCODE_T  | 按键'T'  |
| ARKUI_KEYCODE_U  | 按键'U'  |
| ARKUI_KEYCODE_V  | 按键'V'  |
| ARKUI_KEYCODE_W  | 按键'W'  |
| ARKUI_KEYCODE_X  | 按键'X'  |
| ARKUI_KEYCODE_Y  | 按键'Y'  |
| ARKUI_KEYCODE_Z  | 按键'Z'  |
| ARKUI_KEYCODE_COMMA  | 按键','  |
| ARKUI_KEYCODE_PERIOD  | 按键'.'  |
| ARKUI_KEYCODE_ALT_LEFT  | 左Alt键  |
| ARKUI_KEYCODE_ALT_RIGHT  | 右Alt键  |
| ARKUI_KEYCODE_SHIFT_LEFT  | 左Shift键  |
| ARKUI_KEYCODE_SHIFT_RIGHT  | 右Shift键  |
| ARKUI_KEYCODE_TAB  | Tab键  |
| ARKUI_KEYCODE_SPACE  | 空格键  |
| ARKUI_KEYCODE_SYM  | 符号修改器按键  |
| ARKUI_KEYCODE_EXPLORER  | 浏览器功能键，此键用于启动浏览器应用程序。  |
| ARKUI_KEYCODE_ENVELOPE  | 电子邮件功能键，此键用于启动电子邮件应用程序。  |
| ARKUI_KEYCODE_ENTER  | 回车键  |
| ARKUI_KEYCODE_DEL  | 退格键  |
| ARKUI_KEYCODE_GRAVE  | 按键'‘’  |
| ARKUI_KEYCODE_MINUS  | 按键'-'  |
| ARKUI_KEYCODE_EQUALS  | 按键'='  |
| ARKUI_KEYCODE_LEFT_BRACKET  | 按键'['  |
| ARKUI_KEYCODE_RIGHT_BRACKET  | 按键']'  |
| ARKUI_KEYCODE_BACKSLASH  | 按键'\'  |
| ARKUI_KEYCODE_SEMICOLON  | 按键';'  |
| ARKUI_KEYCODE_APOSTROPHE  | 按键''' (单引号)  |
| ARKUI_KEYCODE_SLASH  | 按键'/'  |
| ARKUI_KEYCODE_AT  | 按键'\@'  |
| ARKUI_KEYCODE_PLUS  | 按键'+'  |
| ARKUI_KEYCODE_MENU  | 菜单键  |
| ARKUI_KEYCODE_PAGE_UP  | 向上翻页键  |
| ARKUI_KEYCODE_PAGE_DOWN  | 向下翻页键  |
| ARKUI_KEYCODE_ESCAPE  | ESC键  |
| ARKUI_KEYCODE_FORWARD_DEL  | 删除键  |
| ARKUI_KEYCODE_CTRL_LEFT  | 左Ctrl键  |
| ARKUI_KEYCODE_CTRL_RIGHT  | 右Ctrl键  |
| ARKUI_KEYCODE_CAPS_LOCK  | 大写锁定键  |
| ARKUI_KEYCODE_SCROLL_LOCK  | 滚动锁定键  |
| ARKUI_KEYCODE_META_LEFT  | 左元修改器键  |
| ARKUI_KEYCODE_META_RIGHT  | 右元修改器键  |
| ARKUI_KEYCODE_FUNCTION  | 功能键  |
| ARKUI_KEYCODE_SYSRQ  | 系统请求/打印屏幕键  |
| ARKUI_KEYCODE_BREAK  | Break/Pause键  |
| ARKUI_KEYCODE_MOVE_HOME  | 光标移动到开始键  |
| ARKUI_KEYCODE_MOVE_END  | 光标移动到末尾键  |
| ARKUI_KEYCODE_INSERT  | 插入键  |
| ARKUI_KEYCODE_FORWARD  | 前进键  |
| ARKUI_KEYCODE_MEDIA_PLAY  | 多媒体键 播放  |
| ARKUI_KEYCODE_MEDIA_PAUSE  | 多媒体键 暂停  |
| ARKUI_KEYCODE_MEDIA_CLOSE  | 多媒体键 关闭  |
| ARKUI_KEYCODE_MEDIA_EJECT  | 多媒体键 弹出  |
| ARKUI_KEYCODE_MEDIA_RECORD  | 多媒体键 录音  |
| ARKUI_KEYCODE_F1  | 按键'F1'  |
| ARKUI_KEYCODE_F2  | 按键'F2'  |
| ARKUI_KEYCODE_F3  | 按键'F3'  |
| ARKUI_KEYCODE_F4  | 按键'F4'  |
| ARKUI_KEYCODE_F5  | 按键'F5'  |
| ARKUI_KEYCODE_F6  | 按键'F6'  |
| ARKUI_KEYCODE_F7  | 按键'F7'  |
| ARKUI_KEYCODE_F8  | 按键'F8'  |
| ARKUI_KEYCODE_F9  | 按键'F9'  |
| ARKUI_KEYCODE_F10  | 按键'F10'  |
| ARKUI_KEYCODE_F11  | 按键'F11'  |
| ARKUI_KEYCODE_F12  | 按键'F12'  |
| ARKUI_KEYCODE_NUM_LOCK  | 小键盘锁  |
| ARKUI_KEYCODE_NUMPAD_0  | 小键盘按键'0'  |
| ARKUI_KEYCODE_NUMPAD_1  | 小键盘按键'1'  |
| ARKUI_KEYCODE_NUMPAD_2  | 小键盘按键'2'  |
| ARKUI_KEYCODE_NUMPAD_3  | 小键盘按键'3'  |
| ARKUI_KEYCODE_NUMPAD_4  | 小键盘按键'4'  |
| ARKUI_KEYCODE_NUMPAD_5  | 小键盘按键'5'  |
| ARKUI_KEYCODE_NUMPAD_6  | 小键盘按键'6'  |
| ARKUI_KEYCODE_NUMPAD_7  | 小键盘按键'7'  |
| ARKUI_KEYCODE_NUMPAD_8  | 小键盘按键'8'  |
| ARKUI_KEYCODE_NUMPAD_9  | 小键盘按键'9'  |
| ARKUI_KEYCODE_NUMPAD_DIVIDE  | 小键盘按键'/'  |
| ARKUI_KEYCODE_NUMPAD_MULTIPLY  | 小键盘按键'\*'  |
| ARKUI_KEYCODE_NUMPAD_SUBTRACT  | 小键盘按键'-'  |
| ARKUI_KEYCODE_NUMPAD_ADD  | 小键盘按键'+'  |
| ARKUI_KEYCODE_NUMPAD_DOT  | 小键盘按键'.'  |
| ARKUI_KEYCODE_NUMPAD_COMMA  | 小键盘按键','  |
| ARKUI_KEYCODE_NUMPAD_ENTER  | 小键盘按键回车  |
| ARKUI_KEYCODE_NUMPAD_EQUALS  | 小键盘按键'='  |
| ARKUI_KEYCODE_NUMPAD_LEFT_PAREN  | 小键盘按键'('  |
| ARKUI_KEYCODE_NUMPAD_RIGHT_PAREN  | 小键盘按键')'  |
| ARKUI_KEYCODE_BUTTON_A  | 游戏手柄按键'A'  |
| ARKUI_KEYCODE_BUTTON_B  | 游戏手柄按键'B' |
| ARKUI_KEYCODE_BUTTON_X  | 游戏手柄按键'X'  |
| ARKUI_KEYCODE_BUTTON_Y  | 游戏手柄按键'Y'  |
| ARKUI_KEYCODE_BUTTON_L1  | 游戏手柄按键'L1'  |
| ARKUI_KEYCODE_BUTTON_R1  | 游戏手柄按键'R1'  |
| ARKUI_KEYCODE_BUTTON_L2  | 游戏手柄按键'R2'  |
| ARKUI_KEYCODE_BUTTON_R2  | 游戏手柄按键'L1'  |
| ARKUI_KEYCODE_BUTTON_SELECT  | 游戏手柄按键'Select'  |
| ARKUI_KEYCODE_BUTTON_START  | 游戏手柄按键'Start'  |
| ARKUI_KEYCODE_BUTTON_MODE  | 游戏手柄按键'Mode'  |
| ARKUI_KEYCODE_BUTTON_THUMBL  | 游戏手柄按键'THUMBL'  |
| ARKUI_KEYCODE_BUTTON_THUMBR  | 游戏手柄按键'THUMBR'  |


### ArkUI_KeyEventType

```
enum ArkUI_KeyEventType
```
**描述：**

按键的类型。

**起始版本：** 14

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_KEY_EVENT_UNKNOWN  | 未知类型  |
| ARKUI_KEY_EVENT_DOWN  | 按键按下  |
| ARKUI_KEY_EVENT_UP  | 按键松开  |
| ARKUI_KEY_EVENT_LONG_PRESS  | 按键长按  |
| ARKUI_KEY_EVENT_CLICK  | 按键点击  |


### ArkUI_KeyIntension

```
enum ArkUI_KeyIntension
```
**描述：**

按键对应的意图。

**起始版本：** 14

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_KEY_INTENSION_UNKNOWN  | 未知意图  |
| ARKUI_KEY_INTENSION_UP  | 向上  |
| ARKUI_KEY_INTENSION_DOWN  | 向下  |
| ARKUI_KEY_INTENSION_LEFT  | 向左  |
| ARKUI_KEY_INTENSION_RIGHT  | 向右  |
| ARKUI_KEY_INTENSION_SELECT  | 选中  |
| ARKUI_KEY_INTENSION_ESCAPE  | 返回  |
| ARKUI_KEY_INTENSION_BACK  | 后退  |
| ARKUI_KEY_INTENSION_FORWARD  | 前进  |
| ARKUI_KEY_INTENSION_MENU  | 菜单  |
| ARKUI_KEY_INTENSION_HOME  | 主页  |
| ARKUI_KEY_INTENSION_PAGE_UP  | 上一页  |
| ARKUI_KEY_INTENSION_PAGE_DOWN  | 下一页  |
| ARKUI_KEY_INTENSION_ZOOM_OUT  | 缩小  |
| ARKUI_KEY_INTENSION_ZOOM_IN  | 放大  |
| ARKUI_KEY_INTENTION_MEDIA_PLAY_PAUSE  | 播放  |
| ARKUI_KEY_INTENTION_MEDIA_FAST_FORWARD  | 快进  |
| ARKUI_KEY_INTENTION_MEDIA_FAST_PLAYBACK  | 快速播放  |
| ARKUI_KEY_INTENTION_MEDIA_NEXT  | 下一首  |
| ARKUI_KEY_INTENTION_MEDIA_PREVIOUS  | 上一首  |
| ARKUI_KEY_INTENTION_MEDIA_MUTE  | 静音  |
| ARKUI_KEY_INTENTION_VOLUME_UP  | 音量增加  |
| ARKUI_KEY_INTENTION_VOLUME_DOWN  | 音量降低  |
| ARKUI_KEY_INTENTION_CALL  | 接听电话  |
| ARKUI_KEY_INTENTION_CAMERA  | 拍照  |

### ArkUI_KeyProcessingMode

```
enum ArkUI_KeyProcessingMode
```
**描述：**

当组件无法处理按键事件时，确定按键事件处理的优先级。

**起始版本：** 15

| 名称          | 描述        |
| ----------- | --------- |
| ARKUI_KEY_PROCESSING_MODE_FOCUS_NAVIGATION | 默认值，按键事件用于移动焦点。|
| ARKUI_KEY_PROCESSING_MODE_FOCUS_ANCESTOR_EVENT |  按键事件向上传递给祖先组件。 |

### ArkUI_KeySourceType

```
enum ArkUI_KeySourceType
```
**描述：**

触发当前按键的输入设备类型。

**起始版本：** 14

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_KEY_SOURCE_UNKNOWN  | 未知类型  |
| ARKUI_KEY_SOURCE_TYPE_MOUSE  | 鼠标  |
| ARKUI_KEY_SOURCE_TYPE_KEYBOARD  | 键盘  |
| ARKUI_KEY_SOURCE_TYPE_JOYSTICK  | 游戏手柄。<br/>**起始版本：** 15  |


### ArkUI_LengthMetricUnit

```
enum ArkUI_LengthMetricUnit
```
**描述：**

定义组件的单位模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_LENGTH_METRIC_UNIT_DEFAULT  | 默认，字体类单位为FP，非字体类单位为VP。  |
| ARKUI_LENGTH_METRIC_UNIT_PX  | 单位为PX。  |
| ARKUI_LENGTH_METRIC_UNIT_VP  | 单位为VP。  |
| ARKUI_LENGTH_METRIC_UNIT_FP  | 单位为FP。  |


### ArkUI_LinearGradientDirection

```
enum ArkUI_LinearGradientDirection
```
**描述：**

定义渐变方向结构。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT  | 向左渐变。  |
| ARKUI_LINEAR_GRADIENT_DIRECTION_TOP  | 向上渐变。  |
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT  | 向右渐变。  |
| ARKUI_LINEAR_GRADIENT_DIRECTION_BOTTOM  | 向下渐变。  |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_TOP  | 向左上渐变。  |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM  | 向左下渐变。  |
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_TOP  | 向右上渐变。  |
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_BOTTOM  | 向右下渐变。  |
| ARKUI_LINEAR_GRADIENT_DIRECTION_NONE  | 不渐变。  |
| ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM  | 自定义渐变方向.  |


### ArkUI_ListItemAlignment

```
enum ArkUI_ListItemAlignment
```
**描述：**

交叉轴方向的布局方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_LIST_ITEM_ALIGNMENT_START  | ListItem在List中，交叉轴方向首部对齐。  |
| ARKUI_LIST_ITEM_ALIGNMENT_CENTER  | ListItem在List中，交叉轴方向居中对齐。  |
| ARKUI_LIST_ITEM_ALIGNMENT_END  | ListItem在List中，交叉轴方向尾部对齐。  |


### ArkUI_ListItemSwipeActionState

```
enum ArkUI_ListItemSwipeActionState
```
**描述：**

定义 Listitem 组件SwipeAction方法的显隐模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED  | 收起状态，当ListItem与主轴方向相反滑动时操作项处于隐藏状态。  |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_EXPANDED  | 收起状态，当ListItem与主轴方向相反滑动时操作项处于显示状态。  |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_ACTIONING  | 长距离状态，当ListItem进入长距删除区后删除ListItem的状态。  |


### ArkUI_ListItemSwipeEdgeEffect

```
enum ArkUI_ListItemSwipeEdgeEffect
```
**描述：**

定义 Listitem 组件SwipeAction方法的滚动模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING  | ListItem划动距离超过划出组件大小后可以继续划动。  |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE  | ListItem划动距离不能超过划出组件大小。  |


### ArkUI_MaskType

```
enum ArkUI_MaskType
```
**描述：**

遮罩类型枚举。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_MASK_TYPE_RECTANGLE  | 矩形类型。  |
| ARKUI_MASK_TYPE_CIRCLE  | 圆形类型。  |
| ARKUI_MASK_TYPE_ELLIPSE  | 椭圆形类型。  |
| ARKUI_MASK_TYPE_PATH  | 路径类型。  |
| ARKUI_MASK_TYPE_PROGRESS  | 进度类型。  |


### ArkUI_NativeAPIVariantKind

```
enum ArkUI_NativeAPIVariantKind
```
**描述：**

定义Native接口集合类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_NATIVE_NODE  | UI组件相关接口类型，详见&lt;arkui/native_node.h&gt;中的结构体类型定义。  |
| ARKUI_NATIVE_DIALOG  | 弹窗相关接口类型，详见&lt;arkui/native_dialog.h&gt;中的结构体类型定义。  |
| ARKUI_NATIVE_GESTURE  | 手势相关接口类型，详见&lt;arkui/native_gesture.h&gt;中的结构体类型定义。  |
| ARKUI_NATIVE_ANIMATE  | 动画相关接口类型。详见&lt;arkui/native_animate.h&gt;中的结构体类型定义。  |


### ArkUI_NavDestinationState

```
enum ArkUI_NavDestinationState
```
**描述：**

定义NavDestination组件的状态。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_NAV_DESTINATION_STATE_ON_SHOW  | NavDestination组件显示。  |
| ARKUI_NAV_DESTINATION_STATE_ON_HIDE  | NavDestination组件隐藏。  |
| ARKUI_NAV_DESTINATION_STATE_ON_APPEAR  | NavDestination从组件树上挂载。  |
| ARKUI_NAV_DESTINATION_STATE_ON_DISAPPEAR  | NavDestination从组件树上卸载。  |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_SHOW  | NavDestination组件显示之前。  |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_HIDE  | NavDestination组件隐藏之前。  |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_APPEAR  | NavDestination挂载到组件树之前。  |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_DISAPPEAR  | NavDestination从组件树上卸载之前。  |
| ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS  | NavDestination从组件返回。  |


### ArkUI_NodeAdapterEventType

```
enum ArkUI_NodeAdapterEventType
```
**描述：**

定义节点适配器事件枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| NODE_ADAPTER_EVENT_WILL_ATTACH_TO_NODE  | 组件和adapter关联时产生该事件。  |
| NODE_ADAPTER_EVENT_WILL_DETACH_FROM_NODE  | 组件和adapter取消关联时产生该事件。  |
| NODE_ADAPTER_EVENT_ON_GET_NODE_ID  | Adapter需要添加新元素时获取新元素的唯一标识符时产生该事件。  |
| NODE_ADAPTER_EVENT_ON_ADD_NODE_TO_ADAPTER  | Adapter需要添加新元素时获取新元素的内容时产生该事件。  |
| NODE_ADAPTER_EVENT_ON_REMOVE_NODE_FROM_ADAPTER  | Adapter将元素移除时产生该事件。  |

### ArkUI_NodeAttributeType

```
enum ArkUI_NodeAttributeType
```
**描述：**

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| NODE_WIDTH  | 宽度属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：宽度数值，单位为vp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：宽度数值，单位为vp； |
| NODE_HEIGHT  | 高度属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：高度数值，单位为vp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：高度数值，单位为vp； |
| NODE_BACKGROUND_COLOR  | 背景色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色； |
| NODE_BACKGROUND_IMAGE  | 背景色图片属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: 图片地址，支持网络图片地址、本地图片地址、Base64或PixelMap对象。不支持SVG类型的图片。<br/>.value[0]?.i32：可选值，repeat参数，参数类型[ArkUI_ImageRepeat](#arkui_imagerepeat)，默认值为ARKUI_IMAGE_REPEAT_NONE；<br/>.object：PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: 图片地址，支持网络图片地址、本地图片地址、Base64或PixelMap对象。不支持SVG类型的图片。<br/>.value[0].i32：repeat参数，参数类型[ArkUI_ImageRepeat](#arkui_imagerepeat)；<br/>.object：PixelMap 图片数据， 参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)；.object参数和.string参数二选一，不可同时设置。 |
| NODE_PADDING  | 内间距属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式有两种：<br/>1：上下左右四个位置的内间距值相等。<br/>.value[0].f32：内间距数值，单位为vp；<br/>2：分别指定上下左右四个位置的内间距值。<br/>.value[0].f32：上内间距数值，单位为vp；<br/>.value[1].f32：右内间距数值，单位为vp；<br/>.value[2].f32：下内间距数值，单位为vp；<br/>.value[3].f32：左内间距数值，单位为vp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：上内间距数值，单位为vp；<br/>.value[1].f32：右内间距数值，单位为vp；<br/>.value[2].f32：下内间距数值，单位为vp；<br/>.value[3].f32：左内间距数值，单位为vp； |
| NODE_ID  | 组件ID属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: ID的内容；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: ID的内容； |
| NODE_ENABLED  | 设置组件是否可交互，支持属性设置，属性重置和属性获取。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示不可交互，true表示可交互；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：0表示不可交互，1表示可交互； |
| NODE_MARGIN  | 外间距属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式有两种：<br/>1：上下左右四个位置的外间距值相等。<br/>.value[0].f32：外间距数值，单位为vp；<br/>2：分别指定上下左右四个位置的外间距值。<br/>.value[0].f32：上外间距数值，单位为vp；<br/>.value[1].f32：右外间距数值，单位为vp；<br/>.value[2].f32：下外间距数值，单位为vp；<br/>.value[3].f32：左外间距数值，单位为vp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：上外间距数值，单位为vp；<br/>.value[1].f32：右外间距数值，单位为vp；<br/>.value[2].f32：下外间距数值，单位为vp；<br/>.value[3].f32：左外间距数值，单位为vp； |
| NODE_TRANSLATE  | 设置组件平移，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： x轴移动距离，单位vp，默认值0；<br/>.value[1].f32： y轴移动距离，单位vp，默认值0；<br/>.value[2].f32： z轴移动距离，单位vp，默认值0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： x轴移动距离，单位vp；<br/>.value[1].f32： y轴移动距离，单位vp；<br/>.value[2].f32： z轴移动距离，单位vp。<br/>**说明：**<br/>设置的参数个数超过3个时，当次设置不生效，也不返回错误码。 |
| NODE_SCALE  | 设置组件缩放，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： x轴的缩放系数，默认值1；<br/>.value[1].f32： y轴的缩放系数，默认值1。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： x轴的缩放系数；<br/>.value[1].f32： y轴的缩放系数。 |
| NODE_ROTATE  | 设置组件旋转，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 旋转轴向量x坐标，默认值0；<br/>.value[1].f32： 旋转轴向量y坐标，默认值0；<br/>.value[2].f32： 旋转轴向量z坐标，默认值0；<br/>.value[3].f32： 旋转角度，默认值0；<br/>.value[4].f32： 视距，即视点到z=0平面的距离，单位vp，默认值0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 旋转轴向量x坐标；<br/>.value[1].f32： 旋转轴向量y坐标；<br/>.value[2].f32： 旋转轴向量z坐标；<br/>.value[3].f32： 旋转角度；<br/>.value[4].f32： 视距，即视点到z=0平面的距离，单位vp。 |
| NODE_BRIGHTNESS  | 设置组件高光效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 亮度值，默认值1.0，推荐取值范围[0,2]。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 亮度值。 |
| NODE_SATURATION  | 设置组件饱和度效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 饱和度值，默认值1.0，推荐取值范围[0,50)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 饱和度值。 |
| NODE_BLUR  | 设置组件内容模糊效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 模糊半径，模糊半径越大越模糊，为0时不模糊，小于0时按0处理且不会返回错误码。单位px，默认值0.0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 模糊半径，模糊半径越大越模糊，为0时不模糊。单位px。 |
| NODE_LINEAR_GRADIENT  | 设置组件颜色渐变效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 线性渐变的起始角度，当[ArkUI_LinearGradientDirection](#arkui_lineargradientdirection) 为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle属性生效，否则按direction为主要布局方式。 0点方向顺时针旋转为正向角度，默认值：180；<br/>.value[1].i32：线性渐变的方向，设置除ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM的线性渐变方向后，angle不生效。数据类型[ArkUI_LinearGradientDirection](#arkui_lineargradientdirection)<br/>.value[2].i32： 为渐变的颜色重复着色，默认值 false。<br/>.object: 参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色颜色。<br/>stops：渐变位置。<br/>size：颜色个数。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 线性渐变的起始角度。 当为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle为设置值，其他情况均为默认值。<br/>.value[1].i32：线性渐变的方向。<br/>.value[2].i32： 为渐变的颜色重复着色。<br/>.object: 参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色颜色。<br/>stops：渐变位置。<br/>size：颜色个数。 |
| NODE_ALIGNMENT  | 设置组件内容在元素绘制区域内的对齐方式，支持属性设置，属性重置和属性获取接口。<br/>在Stack中该属性与NODE_STACK_ALIGN_CONTENT效果一致，只能设置子组件在容器内的对齐方式。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 对齐方式，数据类型[ArkUI_Alignment](#arkui_alignment)，默认值ARKUI_ALIGNMENT_CENTER。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 对齐方式，数据类型[ArkUI_Alignment](#arkui_alignment)。 |
| NODE_OPACITY  | 透明度属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：透明度数值，取值范围为0到1。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：透明度数值，取值范围为0到1。 |
| NODE_BORDER_WIDTH  | 边框宽度属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>1: .value[0].f32：统一设置四条边的边框宽度。<br/>2: .value[0].f32：设置上边框的边框宽度。<br/>.value[1].f32：设置右边框的边框宽度。<br/>.value[2].f32：设置下边框的边框宽度。<br/>.value[3].f32：设置左边框的边框宽度。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：设置上边框的边框宽度。<br/>.value[1].f32：设置右边框的边框宽度。<br/>.value[2].f32：设置下边框的边框宽度。<br/>.value[3].f32：设置左边框的边框宽度。 |
| NODE_BORDER_RADIUS  | 边框圆角属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>1: .value[0].f32：统一设置四条边的边框圆角。<br/>2: .value[0].f32：设置左上角圆角半径。<br/>.value[1].f32：设置右上角圆角半径。<br/>.value[2].f32：设置左下角圆角半径。<br/>.value[3].f32：设置右下角圆角半径。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：设置左上角圆角半径。<br/>.value[1].f32：设置右上角圆角半径。<br/>.value[2].f32：设置左下角圆角半径。<br/>.value[3].f32：设置右下角圆角半径。 |
| NODE_BORDER_COLOR  | 边框颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>1: .value[0].u32：统一设置四条边的边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>2: .value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。 |
| NODE_BORDER_STYLE  | 边框线条样式属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>1: .value[0].i32：统一设置四条边的边框线条样式，参数类型[ArkUI_BorderStyle](#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。<br/>2:.value[0].i32：设置上侧边框线条样式，参数类型{\@linkArkUI_BorderStyle}，默认值为ARKUI_BORDER_STYLE_SOLID。<br/>.value[1].i32：设置右侧边框线条样式，参数类型[ArkUI_BorderStyle](#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。<br/>.value[2].i32：设置下侧边框线条样式，参数类型[ArkUI_BorderStyle](#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。<br/>.value[3].i32：设置左侧边框线条样式，参数类型[ArkUI_BorderStyle](#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：上侧边框线条样式对应的数值。<br/>.value[1].i32：右侧边框线条样式对应的数值。<br/>.value[2].i32：下侧边框线条样式对应的数值。<br/>.value[3].i32：左侧边框线条样式对应的数值。 |
| NODE_Z_INDEX  | 组件的堆叠顺序属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：堆叠顺序数值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：堆叠顺序数值。 |
| NODE_VISIBILITY  | 组件是否可见属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制当前组件显示或隐藏，参数类型[ArkUI_Visibility](#arkui_visibility)，默认值为ARKUI_VISIBILITY_VISIBLE。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制当前组件显示或隐藏，参数类型[ArkUI_Visibility](#arkui_visibility)，默认值为ARKUI_VISIBILITY_VISIBLE。 |
| NODE_CLIP  | 组件进行裁剪、遮罩处理属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制是否按照父容器边缘轮廓进行裁剪，0表示不裁切，1表示裁切。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制是否按照父容器边缘轮廓进行裁剪，0表示不裁切，1表示裁切。 |
| NODE_CLIP_SHAPE  | 组件上指定形状的裁剪，支持属性设置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式,共有5种类型：<br/>1.rect类型：<br/>.value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](#arkui_cliptype)，ARKUI_CLIP_TYPE_RECTANGLE；<br/>.value[1].f32：矩形宽度；<br/>.value[2].f32：矩形高度；<br/>.value[3].f32：矩形圆角宽度；<br/>.value[4].f32：矩形圆角高度；<br/>.value[5]?.f32：矩形形状的左上圆角半径；<br/>.value[6]?.f32：矩形形状的左下圆角半径；<br/>.value[7]?.f32：矩形形状的右上圆角半径；<br/>.value[8]?.f32：矩形形状的右下圆角半径；<br/>2.circle类型：<br/>.value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](#arkui_cliptype)，ARKUI_CLIP_TYPE_CIRCLE；<br/>.value[1].f32：圆形宽度；<br/>.value[2].f32：圆形高度；<br/>3.ellipse类型：<br/>.value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](#arkui_cliptype)，ARKUI_CLIP_TYPE_ELLIPSE；<br/>.value[1].f32：椭圆形宽度；<br/>.value[2].f32：椭圆形高度；<br/>4.path类型：<br/>.value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](#arkui_cliptype)，ARKUI_CLIP_TYPE_PATH；<br/>.value[1].f32：路径宽度；<br/>.value[2].f32：路径高度；<br/>.string：路径绘制的命令字符串；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式,共有5种类型：<br/>1.rect类型：<br/>.value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](#arkui_cliptype)，ARKUI_CLIP_TYPE_RECTANGLE；<br/>.value[1].f32：矩形宽度；<br/>.value[2].f32：矩形高度；<br/>.value[3].f32：矩形圆角宽度；<br/>.value[4].f32：矩形圆角高度；<br/>.value[5]?.f32：矩形形状的左上圆角半径；<br/>.value[6]?.f32：矩形形状的左下圆角半径；<br/>.value[7]?.f32：矩形形状的右上圆角半径；<br/>.value[8]?.f32：矩形形状的右下圆角半径；<br/>2.circle类型：<br/>.value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](#arkui_cliptype)，ARKUI_CLIP_TYPE_CIRCLE；<br/>.value[1].f32：圆形宽度；<br/>.value[2].f32：圆形高度；<br/>3.ellipse类型:：<br/>.value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](#arkui_cliptype)，ARKUI_CLIP_TYPE_ELLIPSE；<br/>.value[1].f32：椭圆形宽度；<br/>.value[2].f32：椭圆形高度；<br/>4.path类型：<br/>.value[0].i32：裁剪类型，参数类型[ArkUI_ClipType](#arkui_cliptype)，ARKUI_CLIP_TYPE_PATH；<br/>.value[1].f32：路径宽度；<br/>.value[2].f32：路径高度；<br/>.string：路径绘制的命令字符串； |
| NODE_TRANSFORM  | 矩阵变换功能，可对图形进行平移、旋转和缩放等，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0...15].f32: 16个浮点数字。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0...15].f32: 16个浮点数字。 |
| NODE_HIT_TEST_BEHAVIOR  | 触摸测试类型，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制当前组件的触摸测试类型，参数类型[ArkUI_HitTestMode](#arkui_hittestmode)，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制当前组件的触摸测试类型，参数类型**ArkKUI_HitTestMode**，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。 |
| NODE_POSITION  | 元素左上角相对于父容器左上角偏移位置，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：x轴坐标。<br/>.value[1].f32: y轴坐标。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：x轴坐标。<br/>.value[1].f32: y轴坐标。 |
| NODE_SHADOW  | 阴影效果属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置当前组件阴影效果，参数类型[ArkUI_ShadowStyle](#arkui_shadowstyle)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置当前组件阴影效果，参数类型[ArkUI_ShadowStyle](#arkui_shadowstyle)。 |
| NODE_CUSTOM_SHADOW  | 自定义阴影效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.f32：阴影模糊半径，单位为vp；<br/>.value[1]?.i32：是否开启智能取色，0代表不开启，1代表开启，默认不开启；<br/>.value[2]?.f32：阴影X轴偏移量，单位为px；<br/>.value[3]?.f32：阴影Y轴偏移量，单位为px；<br/>.value[4]?.i32：阴影类型[ArkUI_ShadowType](#arkui_shadowtype)，默认值为ARKUI_SHADOW_TYPE_COLOR；<br/>.value[5]?.u32：阴影颜色，0xargb格式，形如 0xFFFF0000 表示红色；<br/>.value[6]?.u32：阴影是否内部填充，0表示不填充，1表示填充；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：阴影模糊半径，单位为vp；<br/>.value[1].i32：是否开启智能取色；<br/>.value[2].f32：阴影X轴偏移量，单位为px；<br/>.value[3].f32：阴影Y轴偏移量，单位为px；<br/>.value[4].i32：阴影类型[ArkUI_ShadowType](#arkui_shadowtype)，默认值为ARKUI_SHADOW_TYPE_COLOR；<br/>.value[5].u32：阴影颜色，0xargb格式，形如 0xFFFF0000 表示红色；<br/>.value[6].u32：阴影是否内部填充，0表示不填充，1表示填充； |
| NODE_BACKGROUND_IMAGE_SIZE  | 背景图片的宽高属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示图片的宽度值，取值范围[0,+∞)，单位为vp。<br/>.value[1].f32 表示图片的高度值，取值范围[0,+∞)，单位为vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示图片的宽度值，单位为vp。<br/>.value[1].f32 表示图片的高度值，单位为vp。 |
| NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE  | 背景图片的宽高样式属性，支持属性设置，属性重置，属性获取接口。默认值：ARKUI_IMAGE_SIZE_AUTO<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示背景图片的宽高样式，取[ArkUI_ImageSize](#arkui_imagesize)枚举值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示背景图片的宽高样式，取[ArkUI_ImageSize](#arkui_imagesize)枚举值。 |
| NODE_BACKGROUND_BLUR_STYLE  | 背景和内容之间的模糊属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示模糊类型，取[ArkUI_BlurStyle](#arkui_blurstyle)枚举值。<br/>.value[1]?.i32 表示深浅色模式，取[ArkUI_ColorMode](#arkui_colormode)枚举值。<br/>.value[2]?.i32 表示取色模式，取[ArkUI_AdaptiveColor](#arkui_adaptivecolor)枚举值。<br/>.value[3]?.f32 表示模糊效果程度，取[0.0,1.0]范围内的值。<br/>.value[4]?.f32 表示灰阶模糊起始边界。<br/>.value[5]?.f32 表示灰阶模糊终点边界。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示模糊类型，取[ArkUI_BlurStyle](#arkui_blurstyle)枚举值。<br/>.value[1].i32 表示深浅色模式，取[ArkUI_ColorMode](#arkui_colormode)枚举值。<br/>.value[2].i32 表示取色模式，取[ArkUI_AdaptiveColor](#arkui_adaptivecolor)枚举值。<br/>.value[3].f32 表示模糊效果程度，取[0.0,1.0]范围内的值。<br/>.value[4].f32 表示灰阶模糊起始边界。<br/>.value[5].f32 表示灰阶模糊终点边界。 |
| NODE_TRANSFORM_CENTER  | 图形变换和转场的中心点属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.f32 表示中心点X轴坐标值，单位为vp<br/>.value[1]?.f32 表示中心点Y轴坐标，单位为vp<br/>.value[2]?.f32 表示中心点Z轴坐标，单位为vp<br/>.value[3]?.f32 表示中心点X轴坐标的百分比位置，如0.2表示百分之20的位置，该属性覆盖value[0].f32，默认值:0.5f。<br/>.value[4]?.f32 表示中心点Y轴坐标的百分比位置，如0.2表示百分之20的位置，该属性覆盖value[1].f32，默认值:0.5f。<br/>.value[5]?.f32 表示中心点Z轴坐标的百分比位置，如0.2表示百分之20的位置，该属性覆盖value[2].f32，默认值:0.0f。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示中心点X轴坐标，单位为vp<br/>.value[1].f32 表示中心点Y轴坐标，单位为vp<br/>.value[2].f32 表示中心点Z轴坐标，单位为vp<br/>注：如果设置坐标百分比位置，属性获取方法返回计算后的vp为单位的值。 |
| NODE_OPACITY_TRANSITION  | 转场时的透明度效果属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示起终点的透明度值<br/>.value[1].i32 表示动画时长，单位ms<br/>.value[2].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值<br/>.value[3]?.i32 表示动画延迟时长，单位ms<br/>.value[4]?.i32 表示动画播放次数<br/>.value[5]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值<br/>.value[6]?.f32 表示动画播放速度<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示起终点的透明度值<br/>.value[1].i32 表示动画时长，单位ms<br/>.value[2].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值<br/>.value[3].i32 表示动画延迟时长，单位ms<br/>.value[4].i32 表示动画播放次数<br/>.value[5].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值<br/>.value[6].f32 表示动画播放速度 |
| NODE_ROTATE_TRANSITION  | 转场时的旋转效果属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示横向旋转分量。<br/>.value[1].f32 表示纵向的旋转分量。<br/>.value[2].f32 表示竖向的旋转分量。<br/>.value[3].f32 表示角度。<br/>.value[4].f32 表示视距，默认值：0.0f。<br/>.value[5].i32 表示动画时长，单位ms。<br/>.value[6].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值。<br/>.value[7]?.i32 表示动画延迟时长，单位ms。<br/>.value[8]?.i32 表示动画播放次数。<br/>.value[9]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值。<br/>.value[10]?.f32 表示动画播放速度。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示横向旋转分量。<br/>.value[1].f32 表示纵向的旋转分量。<br/>.value[2].f32 表示竖向的旋转分量。<br/>.value[3].f32 表示角度。<br/>.value[4].f32 表示视距。<br/>.value[5].i32 表示动画时长，单位ms。<br/>.value[6].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值。<br/>.value[7].i32 表示动画延迟时长，单位ms。<br/>.value[8].i32 表示动画播放次数。<br/>.value[9].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值。<br/>.value[10].f32 表示动画播放速度。 |
| NODE_SCALE_TRANSITION  | 转场时的缩放效果属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 横向放大倍数。<br/>.value[1].f32 纵向放大倍数。<br/>.value[2].f32 竖向放大倍数。<br/>.value[3].i32 表示动画时长，单位ms。<br/>.value[4].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值。<br/>.value[5]?.i32 表示动画延迟时长，单位ms。<br/>.value[6]?.i32 表示动画播放次数。<br/>.value[7]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值。<br/>.value[8]?.f32 表示动画播放速度。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 横向放大倍数。<br/>.value[1].f32 纵向放大倍数。<br/>.value[2].f32 竖向放大倍数。<br/>.value[3].i32 表示动画时长，单位ms。<br/>.value[4].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值。<br/>.value[5].i32 表示动画延迟时长，单位ms。<br/>.value[6].i32 表示动画播放次数。<br/>.value[7].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值。<br/>.value[8].f32 表示动画播放速度。 |
| NODE_TRANSLATE_TRANSITION  | 转场时的平移效果属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].f32 表示横向平移距离值，单位为vp<br/>value[1].f32 表示纵向平移距离值，单位为vp<br/>value[2].f32 表示竖向平移距离值，单位为vp<br/>value[3].i32 表示动画时长，单位ms。<br/>value[4].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值。<br/>value[5]?.i32 表示动画延迟时长，单位ms。<br/>value[6]?.i32 表示动画播放次数。<br/>value[7]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值。<br/>value[8]?.f32 表示动画播放速度。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].f32 表示横向平移距离值，单位为vp<br/>value[1].f32 表示纵向平移距离值，单位为vp<br/>value[2].f32 表示竖向平移距离值，单位为vp<br/>value[3].i32 表示动画时长，单位ms。<br/>value[4].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值。<br/>value[5].i32 表示动画延迟时长，单位ms。<br/>value[6].i32 表示动画播放次数。<br/>value[7].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值。<br/>value[8].f32 表示动画播放速度。 |
| NODE_MOVE_TRANSITION  | 转场时从屏幕边缘滑入和滑出的效果属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 参数类型[ArkUI_TransitionEdge](#arkui_transitionedge)<br/>.value[1].i32 表示动画时长，单位ms<br/>.value[2].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值<br/>.value[3]?.i32 表示动画延迟时长，单位ms<br/>.value[4]?.i32 表示动画播放次数<br/>.value[5]?.i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值<br/>.value[6]?.f32 表示动画播放速度<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 参数类型[ArkUI_TransitionEdge](#arkui_transitionedge)<br/>.value[1].i32 表示动画时长，单位ms<br/>.value[2].i32 表示动画曲线类型，取[ArkUI_AnimationCurve](#arkui_animationcurve)枚举值<br/>.value[3].i32 表示动画延迟时长，单位ms<br/>.value[4].i32 表示动画播放次数<br/>.value[5].i32 表示动画播放模式，取[ArkUI_AnimationPlayMode](#arkui_animationplaymode)枚举值<br/>.value[6].f32 表示动画播放速度 |
| NODE_FOCUSABLE  | 获焦属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：参数类型为1或者0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：参数类型为1或者0。 |
| NODE_DEFAULT_FOCUS  | 默认焦点属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>value[0].i32：参数类型为1或者0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].i32：参数类型为1或者0。 |
| NODE_RESPONSE_REGION  | 触摸热区属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.data[0].f32：触摸点相对于组件左上角的x轴坐标,单位为vp。<br/>.data[1].f32：触摸点相对于组件左上角的y轴坐标,单位为vp。<br/>.data[2].f32：触摸热区的宽度 ，单位为百分比。<br/>.data[3].f32：触摸热区的高度，单位为百分比。<br/>.data[4...].f32:可以设置多个手势响应区域，顺序和上述一致。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.data[0].f32：触摸点相对于组件左上角的x轴坐标,单位为vp。<br/>.data[1].f32：触摸点相对于组件左上角的y轴坐标,单位为vp。<br/>.data[2].f32：触摸热区的宽度 ，单位为百分比。<br/>.data[3].f32：触摸热区的高度，单位为百分比。<br/>.data[4...].f32:可以设置多个手势响应区域，顺序和上述一致。 |
| NODE_OVERLAY  | 遮罩文本属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string 遮罩文本；<br/>.value[0]?.i32：可选值，浮层相对于组件的位置，参数类型[ArkUI_Alignment](#arkui_alignment)， 默认值为ARKUI_ALIGNMENT_TOP_START。<br/>.value[1]?.f32：可选值，浮层基于自身左上角的偏移量X，单位为vp。<br/>.value[2]?.f32：可选值，浮层基于自身左上角的偏移量Y，单位为vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 遮罩文本；<br/>.value[0].i32：浮层相对于组件的位置，参数类型[ArkUI_Alignment](#arkui_alignment)， 默认值为ARKUI_ALIGNMENT_TOP_START。<br/>.value[1].f32：浮层基于自身左上角的偏移量X，单位为vp。<br/>.value[2].f32：浮层基于自身左上角的偏移量Y，单位为vp。 |
| NODE_SWEEP_GRADIENT  | 角度渐变效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.f32:为角度渐变的中心点，即相对于当前组件左上角的坐标,X轴坐标<br/>.value[1]?.f32:为角度渐变的中心点，即相对于当前组件左上角的坐标,Y轴坐标<br/>.value[2]?.f32:角度渐变的起点，默认值0。<br/>.value[3]?.f32:角度渐变的终点，默认值0。<br/>.value[4]?.f32:角度渐变的旋转角度，默认值0。<br/>.value[5]?.i32:为渐变的颜色重复着色，0表示不重复着色，1表示重复着色<br/>.object: 参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色颜色。<br/>stops：渐变位置。<br/>size：颜色个数。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32:为角度渐变的中心点，即相对于当前组件左上角的坐标,X轴坐标<br/>.value[1].f32:为角度渐变的中心点，即相对于当前组件左上角的坐标,Y轴坐标<br/>.value[2].f32:角度渐变的起点，默认值0。<br/>.value[3].f32:角度渐变的终点，默认值0。<br/>.value[4].f32:角度渐变的旋转角度，默认值0。<br/>.value[5].i32:为渐变的颜色重复着色，0表示不重复着色，1表示重复着色<br/>.object: 参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色颜色。<br/>stops：渐变位置。<br/>size：颜色个数。 |
| NODE_RADIAL_GRADIENT  | 径向渐变渐变效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.f32:为径向渐变的中心点，即相对于当前组件左上角的坐标,X轴坐标<br/>.value[1]?.f32:为径向渐变的中心点，即相对于当前组件左上角的坐标,Y轴坐标<br/>.value[2]?.f32:径向渐变的半径，默认值0。<br/>.value[3]?.i32:为渐变的颜色重复着色，0表示不重复着色，1表示重复着色<br/>.object: 参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色颜色。<br/>stops：渐变位置。<br/>size：颜色个数。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32:为径向渐变的中心点，即相对于当前组件左上角的坐标,X轴坐标<br/>.value[1].f32:为径向渐变的中心点，即相对于当前组件左上角的坐标,Y轴坐标<br/>.value[2].f32:径向渐变的半径，默认值0。<br/>.value[3].i32:为渐变的颜色重复着色，0表示不重复着色，1表示重复着色<br/>.object: 参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色颜色。<br/>stops：渐变位置。<br/>size：颜色个数。 |
| NODE_MASK  | 组件上加上指定形状的遮罩，支持属性设置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式,共有5种类型：<br/>1.rect类型：<br/>.value[0].u32：填充颜色，0xargb类型；<br/>.value[1].u32：描边颜色，0xargb类型；<br/>.value[2].f32：描边宽度，单位为vp；<br/>.value[3].i32：遮罩类型，参数类型[ArkUI_MaskType](#arkui_masktype)，ARKUI_MASK_TYPE_RECTANGLE；<br/>.value[4].f32：矩形宽度；<br/>.value[5].f32：矩形高度；<br/>.value[6].f32：矩形圆角宽度；<br/>.value[7].f32：矩形圆角高度；<br/>.value[8]?.f32：矩形形状的左上圆角半径；<br/>.value[9]?.f32：矩形形状的左下圆角半径；<br/>.value[10]?.f32：矩形形状的右上圆角半径；<br/>.value[11]?.f32：矩形形状的右下圆角半径；<br/>2.circle类型：<br/>.value[0].u32：填充颜色，0xargb类型；<br/>.value[1].u32：描边颜色，0xargb类型；<br/>.value[2].f32：描边宽度，单位为vp；<br/>.value[3].i32：遮罩类型，参数类型[ArkUI_MaskType](#arkui_masktype)，ARKUI_MASK_TYPE_CIRCLE；<br/>.value[4].f32：圆形宽度；<br/>.value[5].f32：圆形高度；<br/>3.ellipse类型：<br/>.value[0].u32：填充颜色，0xargb类型；<br/>.value[1].u32：描边颜色，0xargb类型；<br/>.value[2].f32：描边宽度，单位为vp；<br/>.value[3].i32：遮罩类型，参数类型[ArkUI_MaskType](#arkui_masktype)，ARKUI_MASK_TYPE_ELLIPSE；<br/>.value[4].f32：椭圆形宽度；<br/>.value[5].f32：椭圆形高度；<br/>4.path类型：<br/>.value[0].u32：填充颜色，0xargb类型；<br/>.value[1].u32：描边颜色，0xargb类型；<br/>.value[2].f32：描边宽度，单位为vp；<br/>.value[3].i32：遮罩类型，参数类型[ArkUI_MaskType](#arkui_masktype)，ARKUI_MASK_TYPE_PATH；<br/>.value[4].f32：路径宽度；<br/>.value[5].f32：路径高度；<br/>.string：路径绘制的命令字符串；<br/>5.progress类型：<br/>.value[0].i32：遮罩类型，参数类型[ArkUI_MaskType](#arkui_masktype)，ARKUI_MASK_TYPE_PROGRESS；<br/>.value[1].f32：进度遮罩的当前值；<br/>.value[2].f32：进度遮罩的最大值；<br/>.value[3].u32：进度遮罩的颜色；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式,共有5种类型：<br/>1.rect类型：<br/>.value[0].u32：填充颜色，0xargb类型；<br/>.value[1].u32：描边颜色，0xargb类型；<br/>.value[2].f32：描边宽度，单位为vp；<br/>.value[3].i32：遮罩类型；<br/>.value[4].f32：矩形宽度；<br/>.value[5].f32：矩形高度；<br/>.value[6].f32：矩形圆角宽度；<br/>.value[7].f32：矩形圆角高度；<br/>.value[8]?.f32：矩形形状的左上圆角半径；<br/>.value[9]?.f32：矩形形状的左下圆角半径；<br/>.value[10]?.f32：矩形形状的右上圆角半径；<br/>.value[11]?.f32：矩形形状的右下圆角半径；<br/>2.circle类型：<br/>.value[0].u32：填充颜色，0xargb类型；<br/>.value[1].u32：描边颜色，0xargb类型；<br/>.value[2].f32：描边宽度，单位为vp；<br/>.value[3].i32：遮罩类型；<br/>.value[4].f32：圆形宽度；<br/>.value[5].f32：圆形高度；<br/>3.ellipse类型：<br/>.value[0].u32：填充颜色，0xargb类型；<br/>.value[1].u32：描边颜色，0xargb类型；<br/>.value[2].f32：描边宽度，单位为vp；<br/>.value[3].i32：遮罩类型；<br/>.value[4].f32：椭圆形宽度；<br/>.value[5].f32：椭圆形高度；<br/>4.path类型：<br/>.value[0].u32：填充颜色，0xargb类型；<br/>.value[1].u32：描边颜色，0xargb类型；<br/>.value[2].f32：描边宽度，单位为vp；<br/>.value[3].i32：遮罩类型；<br/>.value[4].f32：路径宽度；<br/>.value[5].f32：路径高度；<br/>.string：路径绘制的命令字符串；<br/>5.progress类型：<br/>.value[0].i32：遮罩类型；<br/>.value[1].f32：进度遮罩的当前值；<br/>.value[2].f32：进度遮罩的最大值；<br/>.value[3].u32：进度遮罩的颜色； |
| NODE_BLEND_MODE  | 当前控件背景与子节点内容进行混合，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制当前组件的混合模式类型，参数类型[ArkUI_BlendMode](#arkui_blendmode)，默认值为ARKUI_BLEND_MODE_NONE。<br/>.value[1].?i32：blendMode实现方式是否离屏，参数类型[ArkUI_BlendApplyType](#arkui_blendapplytype)，默认值为BLEND_APPLY_TYPE_FAST。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制当前组件的混合模式类型，参数类型[ArkUI_BlendMode](#arkui_blendmode)，默认值为ARKUI_BLEND_MODE_NONE。<br/>.value[1].i32：blendMode实现方式是否离屏，参数类型[ArkUI_BlendApplyType](#arkui_blendapplytype)，默认值为BLEND_APPLY_TYPE_FAST。 |
| NODE_DIRECTION  | 设置容器元素内主轴方向上的布局，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置容器元素内主轴方向上的布局类型，<br/>参数类型[ArkUI_Direction](#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置容器元素内主轴方向上的布局类型，<br/>参数类型[ArkUI_Direction](#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。 |
| NODE_CONSTRAINT_SIZE  | 约束尺寸属性，组件布局时，进行尺寸范围限制，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：最小宽度，单位vp；<br/>.value[1].f32：最大宽度，单位vp；<br/>.value[2].f32：最小高度，单位vp；<br/>.value[3].f32：最大高度，单位vp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：最小宽度，单位vp；<br/>.value[1].f32：最大宽度，单位vp；<br/>.value[2].f32：最小高度，单位vp；<br/>.value[3].f32：最大高度，单位vp； |
| NODE_GRAY_SCALE  | 灰度效果属性，支持属性设置，属性重置和属性获取接口.<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：灰度转换比例，范围0-1之间，比如0.5指按照50进行灰度处理；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：灰度转换比例，范围0-1之间； |
| NODE_INVERT  | 反转输入的图像比例属性，支持属性设置，属性重置和属性获取接口.<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：图像反转比例，范围0-1之间，比如0.5指按照50进行反转处理；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：图像反转比例，范围0-1之间； |
| NODE_SEPIA  | 图像转换为深褐色比例属性，支持属性设置，属性重置和属性获取接口.<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：图像转换为深褐色比例，范围0-1之间，比如0.5指按照50进行深褐色处理；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：图像转换为深褐色比例，范围0-1之间； |
| NODE_CONTRAST  | 对比度属性，支持属性设置，属性重置和属性获取接口.<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：对比度，等于1时为原图，越大则对比度越高，取值范围：[0, 10)；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：对比度，取值范围：[0, 10)； |
| NODE_FOREGROUND_COLOR  | 前景颜色属性，支持属性设置和属性获取接口。属性重置接口无效果。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式，支持两种入参格式：<br/>1：.value[0].u32：颜色数值，0xargb类型，如0xFFFF0000表示红色；<br/>2：.value[0].i32：颜色数值枚举**ArkUI_ColoringStrategy**；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb类型； |
| NODE_OFFSET  | 组件子元素相对组件自身的额外偏移属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示x轴方向的偏移值, 单位为vp。<br/>.value[1].f32 表示y轴方向的偏移值, 单位为vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示x轴方向的偏移值, 单位为vp。<br/>.value[1].f32 表示y轴方向的偏移值, 单位为vp。 |
| NODE_MARK_ANCHOR  | 组件子元素在位置定位时的锚点属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示锚点x坐标值, 单位为vp<br/>.value[1].f32 表示锚点y坐标值, 单位为vp<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示锚点x坐标值, 单位为vp<br/>.value[1].f32 表示锚点y坐标值, 单位为vp |
| NODE_BACKGROUND_IMAGE_POSITION  | 背景图在组件中显示位置，即相对于组件左上角的坐标，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示x轴方向的位置，单位为px。<br/>.value[1].f32 表示y轴方向的位置，单位为px。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示x轴方向的位置，单位为px。<br/>.value[1].f32 表示y轴方向的位置，单位为px。 |
| NODE_ALIGN_RULES  | 相对容器中子组件的对齐规则属性，支持属性设置，属性重置，获取属性接口。<br/>.object：使用[ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption)对象作为组件的对齐规则。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用[ArkUI_AlignmentRuleOption](#arkui_alignmentruleoption)对象作为组件的对齐规则。 |
| NODE_ALIGN_SELF  | 设置子组件在父容器交叉轴的对齐格式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置子组件在父容器交叉轴的对齐格式类型，<br/>参数类型[ArkUI_ItemAlignment](#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_AUTO。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置子组件在父容器交叉轴的对齐格式类型，<br/>参数类型[ArkUI_ItemAlignment](#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_AUTO。 |
| NODE_FLEX_GROW  | 设置组件在父容器的剩余空间所占比例，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：父容器的剩余空间所占比例。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：父容器的剩余空间所占比例。 |
| NODE_FLEX_SHRINK  | 设置父容器压缩尺寸分配给此属性所在组件的比例，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：父容器压缩尺寸分配给此属性所在组件的比例数值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：父容器压缩尺寸分配给此属性所在组件的比例数值。 |
| NODE_FLEX_BASIS  | 设置组件的基准尺寸，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：组件在父容器主轴方向上的基准尺寸。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：组件在父容器主轴方向上的基准尺寸。 |
| NODE_ACCESSIBILITY_GROUP  | 无障碍组属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：为1时表示该组件及其所有子组件为一整个可以选中的组件 无障碍服务将不再关注其子组件内容。参数类型为1或者0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：为1时表示该组件及其所有子组件为一整个可以选中的组件 无障碍服务将不再关注其子组件内容。参数类型为1或者0。 |
| NODE_ACCESSIBILITY_TEXT  | 无障碍文本属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string：无障碍文本。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：无障碍文本。 |
| NODE_ACCESSIBILITY_MODE  | 无障碍辅助服务模式，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：辅助服务模式，参数类型[ArkUI_AccessibilityMode](#arkui_accessibilitymode)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：辅助服务模式，参数类型[ArkUI_AccessibilityMode](#arkui_accessibilitymode)。 |
| NODE_ACCESSIBILITY_DESCRIPTION  | 无障碍说明属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string：无障碍说明。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：无障碍说明。 |
| NODE_FOCUS_STATUS  | 组件获取焦点属性，支持属性设置，属性获取。<br/>注解<br/>设置参数为0时，当前层级页面获焦组件失焦，焦点转移到根容器上。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：参数类型为1或者0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：参数类型为1或者0。 |
| NODE_ASPECT_RATIO  | 设置组件的宽高比，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：组件的宽高比，输入值为 width/height。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：组件的宽高比，width/height的比值。 |
| NODE_LAYOUT_WEIGHT  | Row/Column/Flex 布局下的子组件布局权重参数，支持属性设置、属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：子组件占主轴尺寸的权重。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：子组件占主轴尺寸的权重。 |
| NODE_DISPLAY_PRIORITY  | Row/Column/Flex(单行) 布局下的子组件在布局容器中显示的优先级，支持属性设置、属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：子组件在父容器中的显示优先级。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：子组件在父容器中的显示优先级。 |
| NODE_OUTLINE_WIDTH  | 设置元素的外描边宽度。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：元素左边的外描边宽度。<br/>.value[1].f32：元素上边的外描边宽度。<br/>.value[2].f32：元素右边的外描边宽度。<br/>.value[3].f32：元素下边的外描边宽度。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：元素左边的外描边宽度。<br/>.value[1].f32：元素上边的外描边宽度。<br/>.value[2].f32：元素右边的外描边宽度。<br/>.value[3].f32：元素下边的外描边宽度。 |
| NODE_WIDTH_PERCENT  | 宽度属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：宽度数值，单位为百分比；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：宽度数值，单位为百分比； |
| NODE_HEIGHT_PERCENT  | 高度属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：高度数值，单位为百分比；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：高度数值，单位为百分比； |
| NODE_PADDING_PERCENT  | 内间距属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式有两种：<br/>1：上下左右四个位置的内间距值相等。<br/>.value[0].f32：内间距数值，单位为百分比；<br/>2：分别指定上下左右四个位置的内间距值。<br/>.value[0].f32：上内间距数值，单位为百分比；<br/>.value[1].f32：右内间距数值，单位为百分比；<br/>.value[2].f32：下内间距数值，单位为百分比；<br/>.value[3].f32：左内间距数值，单位为百分比；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：上内间距数值，单位为百分比；<br/>.value[1].f32：右内间距数值，单位为百分比；<br/>.value[2].f32：下内间距数值，单位为百分比；<br/>.value[3].f32：左内间距数值，单位为百分比； |
| NODE_MARGIN_PERCENT  | 外间距属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式有两种：<br/>1：上下左右四个位置的外间距值相等。<br/>.value[0].f32：外间距数值，单位为百分比；<br/>2：分别指定上下左右四个位置的外间距值。<br/>.value[0].f32：上外间距数值，单位为百分比；<br/>.value[1].f32：右外间距数值，单位为百分比；<br/>.value[2].f32：下外间距数值，单位为百分比；<br/>.value[3].f32：左外间距数值，单位为百分比；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：上外间距数值，单位为百分比；<br/>.value[1].f32：右外间距数值，单位为百分比；<br/>.value[2].f32：下外间距数值，单位为百分比；<br/>.value[3].f32：左外间距数值，单位为百分比； |
| NODE_GEOMETRY_TRANSITION  | 组件内隐式共享元素转场，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.i32：参数类型为1或者0。共享元素绑定的2个组件， 针对出场元素未进行删除时是否要继续参与共享元素动画，默认为false，不参与保持原始位置不动。<br/>.string 用于设置绑定关系，id置""清除绑定关系避免参与共享行为， id可更换重新建立绑定关系。同一个id只能有两个组件绑定且是in/out不同类型角色， 不能多个组件绑定同一个id。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：参数类型为1或者0。共享元素绑定的2个组件， 针对出场元素未进行删除时是否要继续参与共享元素动画，默认未false，不参与保持原始位置不动。<br/>.string 用于设置绑定关系，id置""清除绑定关系避免参与共享行为， id可更换重新建立绑定关系。同一个id只能有两个组件绑定且是in/out不同类型角色， 不能多个组件绑定同一个id。 |
| NODE_RELATIVE_LAYOUT_CHAIN_MODE  | 指定以该组件为链头所构成的链的参数，支持属性设置、属性重置和属性获取接口。<br/>仅当父容器为RelativeContainer时生效<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：链的方向。枚举[ArkUI_Axis](#arkui_axis)。<br/>.value[1].i32：链的样式。枚举[ArkUI_RelativeLayoutChainStyle](#arkui_relativelayoutchainstyle)。<br/>.value[0].i32：链的方向。枚举[ArkUI_Axis](#arkui_axis)。<br/>.value[1].i32：链的样式。枚举[ArkUI_RelativeLayoutChainStyle](#arkui_relativelayoutchainstyle)。 |
| NODE_RENDER_FIT  | 设置宽高动画过程中的组件内容填充方式，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 内容填充方式，使用[ArkUI_RenderFit](#arkui_renderfit)枚举值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 内容填充方式，使用[ArkUI_RenderFit](#arkui_renderfit)枚举值。 |
| NODE_OUTLINE_COLOR  | 外描边颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>1: .value[0].u32：统一设置四条边的边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>2: .value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。<br/>.value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。 |
| NODE_SIZE  | 设置高宽尺寸，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：宽度数值，单位为vp；<br/>.value[1].f32：高度数值，单位为vp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：宽度数值，单位为vp；<br/>.value[1].f32：高度数值，单位为vp； |
| NODE_RENDER_GROUP  | 设置当前组件和子组件是否先整体离屏渲染绘制后再与父控件融合绘制，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：参数类型为1或者0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：参数类型为1或者0。 |
| NODE_COLOR_BLEND  | 为组件添加颜色叠加效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：叠加的颜色，使用0xargb表示，如0xFFFF11FF。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：叠加的颜色，使用0xargb表示，如0xFFFF11FF。 |
| NODE_FOREGROUND_BLUR_STYLE  | 为当前组件提供内容模糊能力，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示内容模糊样式，取[ArkUI_BlurStyle](#arkui_blurstyle)枚举值。<br/>.value[1]?.i32 表示内容模糊效果使用的深浅色模式，取[ArkUI_ColorMode](#arkui_colormode)枚举值。<br/>.value[2]?.i32 表示内容模糊效果使用的取色模式，取[ArkUI_AdaptiveColor](#arkui_adaptivecolor)枚举值。<br/>.value[3]?.f32 表示模糊效果程度，取[0.0,1.0]范围内的值。<br/>.value[4]?.i32 表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。<br/>.value[5]?.i32 表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示内容模糊样式，取[ArkUI_BlurStyle](#arkui_blurstyle)枚举值。<br/>.value[1].i32 表示内容模糊效果使用的深浅色模式，取[ArkUI_ColorMode](#arkui_colormode)枚举值。<br/>.value[2].i32 表示内容模糊效果使用的取色模式，取[ArkUI_AdaptiveColor](#arkui_adaptivecolor)枚举值。<br/>.value[3].f32 表示模糊效果程度，取[0.0,1.0]范围内的值。<br/>.value[4].i32 表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。<br/>.value[5].i32 表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。 |
| NODE_LAYOUT_RECT  | 组件布局大小位置属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：组件X轴坐标，单位为px；<br/>.value[1].i32：组件Y轴坐标，单位为px；<br/>.value[2].i32：组件宽度，单位为px；<br/>.value[3].i32：组件高度，单位为px；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：组件X轴坐标，单位为px；<br/>.value[1].i32：组件Y轴坐标，单位为px；<br/>.value[2].i32：组件宽度，单位为px；<br/>.value[3].i32：组件高度，单位为px； |
| NODE_FOCUS_ON_TOUCH  | 设置当前组件是否支持点击获焦能力，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：参数类型为1或者0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：参数类型为1或者0。 |
| NODE_BORDER_WIDTH_PERCENT  | 边框宽度属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>1: .value[0].f32：统一设置四条边的边框宽度，单位为百分比。<br/>2: .value[0].f32：设置上边框的边框宽度，单位为百分比。<br/>.value[1].f32：设置右边框的边框宽度，单位为百分比。<br/>.value[2].f32：设置下边框的边框宽度，单位为百分比。<br/>.value[3].f32：设置左边框的边框宽度，单位为百分比。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：设置上边框的边框宽度，单位为百分比。<br/>.value[1].f32：设置右边框的边框宽度，单位为百分比。<br/>.value[2].f32：设置下边框的边框宽度，单位为百分比。<br/>.value[3].f32：设置左边框的边框宽度，单位为百分比。 |
| NODE_BORDER_RADIUS_PERCENT  | 边框圆角属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>1: .value[0].f32：统一设置四条边的边框圆角半径，单位为百分比。<br/>2: .value[0].f32：设置左上角圆角半径，单位为百分比。<br/>.value[1].f32：设置右上角圆角半径，单位为百分比。<br/>.value[2].f32：设置左下角圆角半径，单位为百分比。<br/>.value[3].f32：设置右下角圆角半径，单位为百分比。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：设置左上角圆角半径，单位为百分比。<br/>.value[1].f32：设置右上角圆角半径，单位为百分比。<br/>.value[2].f32：设置左下角圆角半径，单位为百分比。<br/>.value[3].f32：设置右下角圆角半径，单位为百分比。 |
| NODE_ACCESSIBILITY_ID  | 无障碍自定义标识ID，支持属性获取。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：无障碍自定义标识ID。 |
| NODE_ACCESSIBILITY_ACTIONS  | 定义无障碍支持操作类型属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：配置无障碍操作类型，参数类型[ArkUI_AccessibilityActionType](#arkui_accessibilityactiontype)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：配置无障碍操作类型，参数类型[ArkUI_AccessibilityActionType](#arkui_accessibilityactiontype)。 |
| NODE_ACCESSIBILITY_ROLE  | 定义无障碍组件类型属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：无障碍组件类型，参数类型[ArkUI_NodeType](#arkui_nodetype)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：无障碍组件类型，参数类型[ArkUI_NodeType](#arkui_nodetype)。 |
| NODE_ACCESSIBILITY_STATE  | 定义无障碍状态属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.object：参数类型为[ArkUI_AccessibilityState](#arkui_accessibilitystate)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：参数类型为[ArkUI_AccessibilityState](#arkui_accessibilitystate)。 |
| NODE_ACCESSIBILITY_VALUE  | 定义无障碍信息属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.object：参数类型为[ArkUI_AccessibilityValue](#arkui_accessibilityvalue)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：参数类型为[ArkUI_AccessibilityValue](#arkui_accessibilityvalue)。 |
| NODE_EXPAND_SAFE_AREA  | 定义控制组件扩展其安全区域，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0]?.u32：扩展安全区域的枚举值集合[ArkUI_SafeAreaType](#arkui_safeareatype)， 例如：ARKUI_SAFE_AREA_TYPE_SYSTEM \| ARKUI_SAFE_AREA_TYPE_CUTOUT；<br/>.value[1]?.u32：扩展安全区域的方向枚举值集合[ArkUI_SafeAreaEdge](#arkui_safeareaedge)；<br/>例如：ARKUI_SAFE_AREA_EDGE_TOP \| ARKUI_SAFE_AREA_EDGE_BOTTOM；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：扩展安全区域；<br/>。<br/>.value[1].u32：扩展安全区域的方向；<br/>。 |
| NODE_VISIBLE_AREA_CHANGE_RATIO  | 定义控制组件触发可视区域面积变更事件的可视区域面积占组件本身面积的比例阈值。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[...].f32：占比数值，输入范围0-1。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[...].f32：占比数值。 |
| NODE_TRANSITION  | 定义组件插入和删除时显示过渡动效，支持属性设置，属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.object：参数类型为[ArkUI_TransitionEffect](#arkui_transitioneffect)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：参数类型为[ArkUI_TransitionEffect](#arkui_transitioneffect)。 |
| NODE_UNIQUE_ID  | 组件标识ID，支持属性获取。<br/>注解<br/>组件标识ID只读，且进程内唯一。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：组件标识ID。 |
| NODE_FOCUS_BOX  | 设置当前组件系统焦点框样式。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 焦点框相对组件边缘的距离。正数代表外侧，负数代表内侧。不支持百分比。<br/>.value[1].f32： 焦点框宽度。 不支持负数和百分比。<br/>.value[2].u32： 焦点框颜色。 |
| NODE_CLICK_DISTANCE  | 组件所绑定的点击手势移动距离限制，支持属性设置。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示识别点击手势时允许手指在该范围内移动，单位为vp |
| NODE_TAB_STOP  | 控制焦点是否能停在当前组件，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：参数类型为1或者0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：参数类型为1或者0。<br />**起始版本：** 14 |
| NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE  | 设置背景图在拉伸时可调整大小的属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32: 图片左部拉伸时，图片的像素值保持不变，单位为vp。<br/>.value[1].f32: 图片顶部拉伸时，图片的像素值保持不变，单位为vp。<br/>.value[2].f32: 图片右部拉伸时，图片的像素值保持不变，单位为vp。<br/>.value[3].f32: 图片底部拉伸时，图片的像素值保持不变，单位为vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 图片左部拉伸时，图片的像素值保持不变，单位为vp。<br/>.value[1].f32: 图片顶部拉伸时，图片的像素值保持不变，单位为vp。<br/>.value[2].f32: 图片右部拉伸时，图片的像素值保持不变，单位为vp。<br/>.value[3].f32: 图片底部拉伸时，图片的像素值保持不变，单位为vp。 <br/>起始版本：<br/>19 |
| NODE_NEXT_FOCUS   | 设置下一个走焦节点。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：走焦类型。参数类型为{@link ArkUI_FocusMove}。<br/>.object：下一个焦点。参数类型为{@link ArkUI_NodeHandle}。 <br/>起始版本：<br/>18 |
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO  | 设置可见区域变化监听的参数。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.object：参数类型为{@link ArkUI_VisibleAreaEventOptions}。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>object：参数类型为{@link ArkUI_VisibleAreaEventOptions}。 <br/>起始版本：<br/>17 |
| NODE_TEXT_CONTENT  | text组件设置文本内容属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示文本内容<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示文本内容 |
| NODE_FONT_COLOR  | 组件字体颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：字体颜色数值，0xargb格式，形如 0xFFFF0000 表示红色；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：字体颜色数值，0xargb格式； |
| NODE_FONT_SIZE  | 组件字体大小属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：字体大小数值，单位为fp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：字体大小数值，单位为fp； |
| NODE_FONT_STYLE  | 组件字体样式属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：字体样式[ArkUI_FontStyle](#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：字体样式[ArkUI_FontStyle](#arkui_fontstyle)； |
| NODE_FONT_WEIGHT  | 组件字体粗细属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)； |
| NODE_TEXT_LINE_HEIGHT  | 文本行高属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示lineHeight值，单位为fp<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示lineHeight值，单位为fp |
| NODE_TEXT_DECORATION  | 置文本装饰线样式及其颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本装饰线类型[ArkUI_TextDecorationType](#arkui_textdecorationtype)，默认值为ARKUI_TEXT_DECORATION_TYPE_NONE；<br/>.value[1]?.u32：可选值，装饰线颜色，0xargb格式，形如 0xFFFF0000 表示红色；<br/>.value[2]?.i32：文本装饰线样式[ArkUI_TextDecorationStyle](#arkui_textdecorationstyle)；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本装饰线类型[ArkUI_TextDecorationType](#arkui_textdecorationtype)；<br/>.value[1].u32：装饰线颜色，0xargb格式。<br/>.value[2].i32：文本装饰线样式[ArkUI_TextDecorationStyle](#arkui_textdecorationstyle)； |
| NODE_TEXT_CASE  | 文本大小写属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：表示文本大小写类型[ArkUI_TextCase](#arkui_textcase)，默认值为ARKUI_TEXT_CASE_NORMAL。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：表示文本大小写类型[ArkUI_TextCase](#arkui_textcase)。 |
| NODE_TEXT_LETTER_SPACING  | 文本字符间距属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示字符间距值，单位为fp<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示字符间距值，单位为fp |
| NODE_TEXT_MAX_LINES  | 文本最大行数属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示最大行数<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示最大行数 |
| NODE_TEXT_ALIGN  | 文本水平对齐方式，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：表示文本水平对齐方式，取[ArkUI_TextAlignment](#arkui_textalignment)枚举值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：表示文本水平对齐方式，取[ArkUI_TextAlignment](#arkui_textalignment)枚举值。 |
| NODE_TEXT_OVERFLOW  | 文本超长时的显示方式属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：表示文本超长时的显示方式。{\@ArkUI_TextOverflow}<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：表示文本超长时的显示方式。{\@ArkUI_TextOverflow} |
| NODE_FONT_FAMILY  | Text字体列表属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string：字体字符串，多个用“,”分隔。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：字体字符串，多个用“,”分隔。 |
| NODE_TEXT_COPY_OPTION  | 文本复制粘贴属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：复制粘贴方式[ArkUI_CopyOptions](#arkui_copyoptions)，默认值为ARKUI_COPY_OPTIONS_NONE；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：复制粘贴方式[ArkUI_CopyOptions](#arkui_copyoptions)。 |
| NODE_TEXT_BASELINE_OFFSET  | 文本基线的偏移量属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：偏移量数值，单位为fp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：偏移量数值，单位为fp。 |
| NODE_TEXT_TEXT_SHADOW  | 文字阴影效果属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：阴影模糊半径，单位为vp；<br/>.value[1].i32：阴影类型[ArkUI_ShadowType](#arkui_shadowtype)，默认值为ARKUI_SHADOW_TYPE_COLOR；<br/>.value[2].u32：阴影颜色，0xargb格式，形如 0xFFFF0000 表示红色；<br/>.value[3].f32：阴影X轴偏移量，单位为vp；<br/>.value[4].f32：阴影Y轴偏移量，单位为vp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：阴影模糊半径，单位为vp；<br/>.value[1].i32：阴影类型[ArkUI_ShadowType](#arkui_shadowtype)；<br/>.value[2].u32：阴影颜色，0xargb格式；<br/>.value[3].f32：阴影X轴偏移量，单位为vp；<br/>.value[4].f32：阴影Y轴偏移量，单位为vp； |
| NODE_TEXT_MIN_FONT_SIZE  | Text最小显示字号，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：文本最小显示字号，单位FP。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：文本最小显示字号，单位FP。 |
| NODE_TEXT_MAX_FONT_SIZE  | Text最大显示字号，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：文本最大显示字号 单位FP。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：文本最大显示字号 单位FP。 |
| NODE_TEXT_FONT  | Text样式，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string?：可选值 字体列表，使用多个字体，使用','进行分割。<br/>.value[0].f32：文本尺寸 单位FP。<br/>.value[1]?.i32：可选值，文本的字体粗细，参数类型[ArkUI_FontWeight](#arkui_fontweight)。 默认值为ARKUI_FONT_WEIGHT_NORMAL。<br/>.value[2]?.i32：可选值，字体样式，参数类型[ArkUI_FontStyle](#arkui_fontstyle)。 默认值为ARKUI_FONT_STYLE_NORMAL。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：字体列表，使用多个字体，使用','进行分割。<br/>.value[0].f32：文本尺寸 单位FP。<br/>.value[1].i32：文本的字体粗细，参数类型[ArkUI_FontWeight](#arkui_fontweight)。 默认值为ARKUI_FONT_WEIGHT_NORMAL。<br/>.value[2].i32：字体样式，参数类型[ArkUI_FontStyle](#arkui_fontstyle)。 默认值为ARKUI_FONT_STYLE_NORMAL。 |
| NODE_TEXT_HEIGHT_ADAPTIVE_POLICY  | Text自适应高度的方式，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：参数类型[ArkUI_TextHeightAdaptivePolicy](#arkui_textheightadaptivepolicy)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：参数类型[ArkUI_TextHeightAdaptivePolicy](#arkui_textheightadaptivepolicy)。 |
| NODE_TEXT_INDENT  | 文本首行缩进属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 表示首行缩进值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 表示首行缩进值。 |
| NODE_TEXT_WORD_BREAK  | 文本断行规则属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 参数类型[ArkUI_WordBreak](#arkui_wordbreak)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 参数类型[ArkUI_WordBreak](#arkui_wordbreak)。 |
| NODE_TEXT_ELLIPSIS_MODE  | 设置文本省略位置，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 参数类型[ArkUI_EllipsisMode](#arkui_ellipsismode)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 参数类型[ArkUI_EllipsisMode](#arkui_ellipsismode)。 |
| NODE_TEXT_LINE_SPACING  | 文本行间距属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示lineSpacing值，单位为fp<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示lineSpacing值，单位为fp |
| NODE_FONT_FEATURE  | 设置文本特性效果，设置NODE_FONT_FEATURE属性， NODE_FONT_FEATURE是 OpenType 字体的高级排版能力，<br/>如支持连字、数字等宽等特性，一般用在自定义字体中，其能力需要字体本身支持，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 符合文本特性格式的字符串，格式为normal \| &lt;feature-tag-value&gt;,<br/>&lt;feature-tag-value&gt;的格式为：&lt;string&gt; [ &lt;integer&gt; \| on \| off ],<br/>&lt;feature-tag-value&gt;的个数可以有多个，中间用','隔开，例如，使用等宽数字的输入格式为：ss01 on。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示文本特性的内容，多个文本特性之间使用逗号分隔。 |
| NODE_TEXT_ENABLE_DATA_DETECTOR  | 设置使能文本识别。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：使能文本识别，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：使能文本识别。 |
| NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG  | 设置文本识别配置。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0...].i32: 实体类型数组，参数类型[ArkUI_TextDataDetectorType](#arkui_textdatadetectortype)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0...].i32：实体类型数组，参数类型[ArkUI_TextDataDetectorType](#arkui_textdatadetectortype)。 |
| NODE_TEXT_SELECTED_BACKGROUND_COLOR  | 文本选中时的背景色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式。 |
| NODE_TEXT_CONTENT_WITH_STYLED_STRING  | text组件使用格式化字符串对象设置文本内容属性，支持属性设置，属性重置，属性获取接口。 配置自定义**OH_Drawing_Typography**对象到text组件，会跳过文本控件的布局测算阶段，需要注意：<br/>1、需要保证**OH_ArkUI_StyledString**对象、**OH_Drawing_Typography**对象的生命周期跟随Text 组件生命周期，Text组件析构时重置**OH_ArkUI_StyledString**对象，否则会导致应用出现空指针崩溃。<br/>2、保证**OH_Drawing_TypographyLayout**方法调用时序在Text组件的布局测算之前。<br/>3、释放**OH_ArkUI_StyledString**对象、**OH_Drawing_Typography**对象时，需要同步调用Text 组件的reset方法，否则会导致应用出现空指针崩溃。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object 表示 ArkUI_StyledString 格式化字符串数据，参数类型为[ArkUI_StyledString](#arkui_styledstring)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object 表示 ArkUI_StyledString 格式化字符串数据，参数类型为[ArkUI_StyledString](#arkui_styledstring)。 |
| NODE_TEXT_HALF_LEADING  | text组件设置文本纵向居中显示。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本是否纵向居中显示，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本是否纵向居中显示。 |
| NODE_IMMUTABLE_FONT_WEIGHT  | 组件字体粗细属性，支持属性设置，属性重置和属性获取接口。通过此接口设置的文字粗细属性不会跟随系统字体粗细而变化。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)； |
| NODE_TEXT_LINEAR_GRADIENT  | 设置文本线性渐变效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：线性渐变的起始角度。当direction属性设置为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle属性生效；否则，以direction属性为主要布局方式，0点方向顺时针旋转为正向角度。<br/>默认值：180<br/>.value[1].i32：线性渐变的方向[ArkUI_LinearGradientDirection](#arkui_lineargradientdirection)。设置除ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM之外的线性渐变方向后，angle不生效。<br/>默认值：ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM<br/>.value[2].i32：为渐变的颜色重复着色，false表示不重复着色，true表示重复着色。<br/>默认值：false<br/>.object：参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。<br/>stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。想要实现多个颜色渐变效果时，数组元素建议递增设置，如后一个数组元素比前一个数组元素小的话，按照等于前一个数组元素的值处理。<br/>size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置大于colors数组长度或小于等于0的值以及异常值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：线性渐变的起始角度。当为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle为设置值，其他情况均为默认值0。<br/>.value[1].i32：线性渐变的方向[ArkUI_LinearGradientDirection](#arkui_lineargradientdirection)。<br/>.value[2].i32：为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。<br/>默认值：0<br/>.object：参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。<br/>stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。<br/>size：生效后渐变色的颜色个数。<br/>**起始版本：** 20| 
| NODE_TEXT_RADIAL_GRADIENT  | 设置文本径向渐变效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的X轴坐标。<br/>.value[1]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的Y轴坐标。<br/>文本框左上角的坐标为[0,0]。<br/>.value[2]?.f32：径向渐变的半径，默认值为0。<br/>.value[3]?.i32：为渐变的颜色重复着色，false表示不重复着色，true表示重复着色。<br/>默认值：false<br/>.object：参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。<br/>stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。想要实现多个颜色渐变效果时，数组元素建议递增设置，如后一个数组元素比前一个数组元素小的话，按照等于前一个数组元素的值处理。<br/>size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置大于colors数组长度或小于等于0的值以及异常值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：为径向渐变的中心点，即相对于当前文本框左上角的X轴坐标。<br/>.value[1].f32：为径向渐变的中心点，即相对于当前文本框左上角的Y轴坐标。<br/>文本框左上角的坐标为[0,0]。<br/>.value[2].f32：径向渐变的半径，默认值0。<br/>.value[3].i32：为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。<br/>默认值：0<br/>.object：参数类型为[ArkUI_ColorStop](_ark_u_i___color_stop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过：<br/>colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。<br/>stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。<br/>size：生效后渐变色的颜色个数。<br/>**起始版本：** 20| 
| NODE_TEXT_LINE_COUNT  | 文本行数属性，支持属性获取。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本的行数。<br/>**起始版本：** 20  |
| NODE_TEXT_OPTIMIZE_TRAILING_SPACE | Text组件设置是否优化每行末尾的空格。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否优化每行末尾的空格，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否优化每行末尾的空格。<br/>**起始版本：** 20  |
| NODE_TEXT_VERTICAL_ALIGN | 设置文本内容垂直对齐方式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本内容垂直对齐方式[ArkUI_TextVerticalAlignment](#arkui_textverticalalignment)，默认值：ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本内容垂直对齐方式[ArkUI_TextVerticalAlignment](#arkui_textverticalalignment)。<br/>**起始版本：** 20  |
| NODE_SPAN_CONTENT  | 文本内容属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示span的文本内容。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示span的文本内容。 |
| NODE_SPAN_TEXT_BACKGROUND_STYLE  | 文本背景色属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32 表示文本背景颜色，0xargb格式，形如0xFFFF0000 表示红色。<br/>第二个参数为文本背景圆角设置，支持如下两种设置方式：<br/>1：.value[1].f32：四个方向的圆角半径统一设置，单位为vp。<br/>2: .value[1].f32：设置左上角圆角半径，单位为vp。<br/>.value[2].f32：设置右上角圆角半径，单位为vp。<br/>.value[3].f32：设置左下角圆角半径，单位为vp。<br/>.value[4].f32：设置右下角圆角半径，单位为vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：文本背景颜色，0xargb格式。<br/>.value[1].f32：左上角圆角半径，单位为vp。<br/>.value[2].f32：右上角圆角半径，单位为vp。<br/>.value[3].f32：左下角圆角半径，单位为vp。<br/>.value[4].f32：右下角圆角半径，单位为vp。 |
| NODE_SPAN_BASELINE_OFFSET  | 文本基线的偏移量属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：偏移量数值，单位为fp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：偏移量数值，单位为fp。 |
| NODE_IMAGE_SPAN_SRC  | imageSpan组件图片地址属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示imageSpan的图片地址<br/>.object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示imageSpan的图片地址<br/>.object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)；.object参数和.string参数二选一，不可同时设置。 |
| NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT  | 图片基于文本的对齐方式属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示图片基于文本的对齐方式，取[ArkUI_ImageSpanAlignment](#arkui_imagespanalignment)枚举值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示图片基于文本的对齐方式，取[ArkUI_ImageSpanAlignment](#arkui_imagespanalignment)枚举值。 |
| NODE_IMAGE_SPAN_ALT  | imageSpan组件占位图地址属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示image组件占位图地址(不支持gif类型图源)。<br/>.object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)；.object参数和.string参数二选一，不可同时设置。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示image组件占位图地址。<br/>.object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)。 |
| NODE_IMAGE_SPAN_BASELINE_OFFSET  | imageSpan组件的基线偏移量属性，支持属性设置，属性重置和属性获取接口。 偏移量数值为正数时向上偏移，负数时向下偏移，默认值0，单位为fp。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：偏移量数值，单位为fp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：偏移量数值，单位为fp。 |
| NODE_IMAGE_SRC  | image组件设置图片地址属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示image组件地址。<br/>.object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)；.object参数和.string参数二选一，不可同时设置。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示image组件地址。<br/>.object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)。 |
| NODE_IMAGE_OBJECT_FIT  | 图片填充效果属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示图片填充效果，取[ArkUI_ObjectFit](#arkui_objectfit)枚举值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示图片填充效果，取[ArkUI_ObjectFit](#arkui_objectfit)枚举值。 |
| NODE_IMAGE_INTERPOLATION  | 图片插值效果效果属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示插值效果效果，取[ArkUI_ImageInterpolation](#arkui_imageinterpolation)枚举值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示插值效果效果，取[ArkUI_ImageInterpolation](#arkui_imageinterpolation)枚举值。 |
| NODE_IMAGE_OBJECT_REPEAT  | 图片重复样式属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示图片重复样式，取[ArkUI_ImageRepeat](#arkui_imagerepeat)枚举值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示图片重复样式，取[ArkUI_ImageRepeat](#arkui_imagerepeat)枚举值。 |
| NODE_IMAGE_COLOR_FILTER  | 图片滤镜效果属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 ~ .value[19].f32 表示滤镜矩阵数组。<br/>.size 表示滤镜数组大小 5\*4。<br/>.object 颜色滤波器指针，参数类型为**OH_Drawing_ColorFilter**，.object和.size参数只能二选一，不可同时设置。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 ~ .value[19].f32 表示滤镜矩阵数组。<br/>.size 表示滤镜数组大小 5\*4。<br/>.object 颜色滤波器指针，参数类型为**OH_Drawing_ColorFilter**。 |
| NODE_IMAGE_AUTO_RESIZE  | 图源自动缩放属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示是否缩放布尔值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示是否缩放布尔值。 |
| NODE_IMAGE_ALT  | 占位图地址属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示image组件占位图地址。<br/>.object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)；.object参数和.string参数二选一，不可同时设置。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string 表示image组件占位图地址。<br/>.object 表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](#arkui_drawabledescriptor)。 |
| NODE_IMAGE_DRAGGABLE  | 图片拖拽效果属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示是否支持拖拽，设置为true表示支持。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示是否支持拖拽。 |
| NODE_IMAGE_RENDER_MODE  | 图片渲染模式属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 参数类型[ArkUI_ImageRenderMode](#arkui_imagerendermode)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 参数类型[ArkUI_ImageRenderMode](#arkui_imagerendermode)。 |
| NODE_IMAGE_FIT_ORIGINAL_SIZE  | 设置图片的显示尺寸是否跟随图源尺寸，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32，设置图片的显示尺寸是否跟随图源尺寸，1表示跟随，0表示不跟随，默认值为0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32，1表示图片的显示尺寸跟随图源尺寸，0表示图片的显示尺寸不跟随图源尺寸。 |
| NODE_IMAGE_FILL_COLOR  | 设置填充颜色，设置后填充颜色会覆盖在图片上，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：填充色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：填充色数值，0xargb格式。 |
| NODE_IMAGE_RESIZABLE  | 设置图像拉伸时，可调整大小的图像选项。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 图片左部拉伸时，保持不变距离。单位vp。<br/>.value[1].f32 图片上部拉伸时，保持不变距离。单位vp。<br/>.value[2].f32 图片右部拉伸时，保持不变距离。单位vp。<br/>.value[3].f32 图片下部拉伸时，保持不变距离。单位vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 图片左部拉伸时，保持不变距离。单位vp。<br/>.value[1].f32 图片上部拉伸时，保持不变距离。单位vp。<br/>.value[2].f32 图片右部拉伸时，保持不变距离。单位vp。<br/>.value[3].f32 图片下部拉伸时，保持不变距离。单位vp。 |
| NODE_IMAGE_SYNC_LOAD  | 图源同步加载属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示是否同步，1表示同步，0表示异步。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示是否同步，1表示同步，0表示异步。 <br/>**起始版本：** 20 |
| NODE_TOGGLE_SELECTED_COLOR  | 组件打开状态的背景颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：背景色数值，0xargb格式。 |
| NODE_TOGGLE_SWITCH_POINT_COLOR  | Switch类型的圆形滑块颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：圆形滑块颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：圆形滑块颜色数值，0xargb格式。 |
| NODE_TOGGLE_VALUE  | Switch类型的开关值，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置开关的值，true表示开启。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置开关的值。 |
| NODE_TOGGLE_UNSELECTED_COLOR  | 组件关闭状态的背景颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：背景色数值，0xargb格式。 |
| NODE_LOADING_PROGRESS_COLOR  | 加载进度条前景色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：前景颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：前景颜色数值，0xargb格式。 |
| NODE_LOADING_PROGRESS_ENABLE_LOADING  | LoadingProgress动画显示属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false时不显示动画，true时可以显示动画；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：0时不显示动画，1时可以显示动画。 |
| NODE_TEXT_INPUT_PLACEHOLDER  | 单行文本输入框的默认提示文本内容属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认提示文本的内容。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认提示文本的内容。 |
| NODE_TEXT_INPUT_TEXT  | 单行文本输入框的默认文本内容属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认文本的内。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认文本的内容。 |
| NODE_TEXT_INPUT_CARET_COLOR  | 光标颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：光标颜色数值，0xargb格式，形如 0xFFFF0000 表示红色；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：光标颜色数值，0xargb格式。 |
| NODE_TEXT_INPUT_CARET_STYLE  | 光标风格属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：光标宽度数值，单位为vp；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：光标宽度数值，单位为vp。 |
| NODE_TEXT_INPUT_SHOW_UNDERLINE  | 单行文本输入框下划线属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示不展示下划线，true表示展示下划线；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：0表示不展示下划线，1表示展示下划线。 |
| NODE_TEXT_INPUT_MAX_LENGTH  | 输入框支持的最大文本数属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：最大文本数的数字，无单位。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：最大文本数的数字。 |
| NODE_TEXT_INPUT_ENTER_KEY_TYPE  | 回车键类型属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_DONE。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](#arkui_enterkeytype)。 |
| NODE_TEXT_INPUT_PLACEHOLDER_COLOR  | 无输入时默认提示文本的颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式。 |
| NODE_TEXT_INPUT_PLACEHOLDER_FONT  | 无输入时默认提示文本的字体配置（包括大小、字重、样式、字体列表）属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.f32：可选字体大小数值，默认值16.0，单位为fp；<br/>.value[1]?.i32：可选字体样式[ArkUI_FontStyle](#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL；<br/>.value[2]?.i32：可选字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL；<br/>?.string: 字体族内容，多个字体族之间使用逗号分隔，形如“字重；字体族1，字体族2”。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：字体大小数值，单位为fp；<br/>.value[1].i32：字体样式[ArkUI_FontStyle](#arkui_fontstyle)；<br/>.value[2].i32：字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)；<br/>.string: 字体族内容，多个字体族之间使用逗号分隔。 |
| NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS  | 聚焦时是否绑定输入法属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示聚焦不拉起输入法，true表示拉起。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起。 |
| NODE_TEXT_INPUT_TYPE  | 输入框的类型属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：输入框类型枚举[ArkUI_TextInputType](#arkui_textinputtype)，默认值为ARKUI_TEXTINPUT_TYPE_NORMAL。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：输入框类型枚举[ArkUI_TextInputType](#arkui_textinputtype)。 |
| NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR  | 输入框文本选中时的背景色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式。 |
| NODE_TEXT_INPUT_SHOW_PASSWORD_ICON  | 密码输入模式时是否显示末尾图标属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示不显示图标，true表示显示图标；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：0表示不显示图标，1表示显示图标。 |
| NODE_TEXT_INPUT_EDITING  | 控制单行文本输入框编辑态属性，支持属性设置。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示退出编辑态，true表示维持现状。<br/>属性获取方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示退出编辑态，true表示维持现状。 |
| NODE_TEXT_INPUT_CANCEL_BUTTON  | 单行文本右侧清除按钮样式属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：按钮样式[ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle)，默认值为ARKUI_CANCELBUTTON_STYLE_INPUT；<br/>.value[1]?.f32：图标大小数值，单位为vp；<br/>.value[2]?.u32：按钮图标颜色数值，0xargb格式，形如 0xFFFF0000 表示红色；<br/>?.string：按钮图标地址，入参内容为图片本地地址，例如 /pages/icon.png。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：按钮样式[ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle)；<br/>.value[1].f32：图标大小数值，单位为vp；<br/>.value[2].u32：按钮图标颜色数值，0xargb格式；<br/>.string：按钮图标地址。 |
| NODE_TEXT_INPUT_TEXT_SELECTION  | 单行文本设置文本选中并高亮的区域，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：选中文本的起始位置；<br/>.value[1].i32：选中文本的终止位置；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：选中文本的起始位置；<br/>.value[1].i32：选中文本的终止位置； |
| NODE_TEXT_INPUT_UNDERLINE_COLOR  | 开启下划线时，支持配置下划线颜色。<br/>主题配置的默认下划线颜色为'0x33182431'。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：typing，必填，键入时下划线颜色，0xargb类型；<br/>.value[1].u32：normal，必填，非特殊状态时下划线颜色，0xargb类型；<br/>.value[2].u32：error，必填，错误时下划线颜色，0xargb类型；<br/>.value[3].u32：disable，必填，禁用时下划线颜色，0xargb类型；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：typing，键入时下划线颜色，0xargb类型；<br/>.value[1].u32：normal，非特殊状态时下划线颜色，0xargb类型；<br/>.value[2].u32：error，错误时下划线颜色，0xargb类型；<br/>.value[3].u32：disable，禁用时下划线颜色，0xargb类型； |
| NODE_TEXT_INPUT_ENABLE_AUTO_FILL  | 设置是否启用自动填充。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否启用自动填充，默认值true。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否启用自动填充。 |
| NODE_TEXT_INPUT_CONTENT_TYPE  | 自动填充类型。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 参数类型[ArkUI_TextInputContentType](#arkui_textinputcontenttype)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 参数类型[ArkUI_TextInputContentType](#arkui_textinputcontenttype)。 |
| NODE_TEXT_INPUT_PASSWORD_RULES  | 定义生成密码的规则。在触发自动填充时，所设置的密码规则会透传给密码保险箱，用于新密码的生成。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 定义生成密码的规则。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 定义生成密码的规则。 |
| NODE_TEXT_INPUT_SELECT_ALL  | 设置当初始状态，是否全选文本。不支持内联模式。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否全选文本，默认值：false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否全选文本。 |
| NODE_TEXT_INPUT_INPUT_FILTER  | 通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。仅支持单个字符匹配，不支持字符串匹配。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 正则表达式。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 正则表达式。 |
| NODE_TEXT_INPUT_STYLE  | 设置输入框为默认风格或内联输入风格。<br/>内联输入风格只支持InputType.Normal类型<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 参数类型[ArkUI_TextInputStyle](#arkui_textinputstyle)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 参数类型[ArkUI_TextInputStyle](#arkui_textinputstyle)。 |
| NODE_TEXT_INPUT_CARET_OFFSET  | 设置或获取光标所在位置信息。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>设置输入光标的位置。 .value[0].i32： 从字符串开始到光标所在位置的字符长度。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>返回当前光标所在位置信息。在当前帧更新光标位置同时调用该接口，该接口不生效 value[0].i32：光标所在位置的索引值。<br/>value[1].f32：光标相对输入框的x坐标位值。<br/>value[2].f32：光标相对输入框的y坐标位值。 |
| NODE_TEXT_INPUT_CONTENT_RECT  | 获取已编辑文本内容区域相对组件的位置和大小。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].f32：水平方向横坐标。<br/>value[1].f32：竖直方向纵坐标。<br/>value[2].f32：内容宽度大小。<br/>value[3].f32：内容高度大小。 |
| NODE_TEXT_INPUT_CONTENT_LINE_COUNT  | 获取已编辑文本内容的行数。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].i32：已编辑文本内容行数。 |
| NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN  | 设置长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。 |
| NODE_TEXT_INPUT_BLUR_ON_SUBMIT  | 设置输入框在submit状态下，触发回车键是否失焦。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否失焦。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否失焦。 |
| NODE_TEXT_INPUT_CUSTOM_KEYBOARD  | 设置自定义键盘。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：自定义键盘，参数类型{\@Link ArkUI_NodeHandle}。<br/>.value[0]?.i32：设置自定义键盘是否支持避让功能，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：自定义键盘，参数类型{\@Link ArkUI_NodeHandle}。<br/>.value[0].i32：设置自定义键盘是否支持避让功能。 |
| NODE_TEXT_INPUT_WORD_BREAK  | 文本断行规则属性，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 参数类型[ArkUI_WordBreak](#arkui_wordbreak)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 参数类型[ArkUI_WordBreak](#arkui_wordbreak)。 |
| NODE_TEXT_INPUT_NUMBER_OF_LINES  | 设置该属性后，通过该属性计算textInput组件的高度。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 设置numberOfLines的值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 设置numberOfLines的值。 |
| NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS  | 设置输入框获取焦点时是否弹出键盘，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否弹出键盘。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否弹出键盘。 |
| NODE_TEXT_INPUT_LETTER_SPACING  | 设置输入框字符间距，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 字符间距，默认单位为FP。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 字符间距，默认单位为FP。 |
| NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT  | 设置输入框开启字符预上屏，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启字符预上屏。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启字符预上屏。 |
| NODE_TEXT_INPUT_HALF_LEADING  | 设置文本将行间距平分至行的顶部与底部。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 文本是否将行间距平分至行的顶部与底部，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 文本是否将行间距平分至行的顶部与底部。<br/>**起始版本：** 18 |
| NODE_TEXT_INPUT_KEYBOARD_APPEARANCE  | 设置输入框拉起的键盘样式。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 设置对应的键盘样式，类型为[ArkUI_KeyboardAppearance](#arkui_keyboardappearance)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 对应的键盘样式，类型为[ArkUI_KeyboardAppearance](#arkui_keyboardappearance)。<br/>起始版本：<br/>15 |
| NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION  | 设置是否启用自动填充动效。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否启用自动填充动效。<br/>true表示启用，false表示不启用。<br/>默认值true。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否启用自动填充动效。<br/>**说明：**<br/>启用之后，仅[输入模式](#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_PASSWORD、ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD或ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD的输入框在进行自动填充时动效可生效。<br/>**起始版本：** 20 |
| NODE_TEXT_INPUT_LINE_HEIGHT  | 设置输入框文本的高度，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本的高度的数字。默认值是自适应字体大小，单位为fp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本的高度的数字。<br/>**说明：**<br/>设置为undefined时，文本的高度设置为5。<br/>**起始版本：** 20 |
| NODE_TEXT_AREA_PLACEHOLDER  | 多行文本输入框的默认提示文本内容属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认提示文本的内容。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认提示文本的内容。 |
| NODE_TEXT_AREA_TEXT  | 多行文本输入框的默认文本内容属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认文本的内容。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认文本的内容。 |
| NODE_TEXT_AREA_MAX_LENGTH  | 输入框支持的最大文本数属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：最大文本数的数字。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：最大文本数的数字。 |
| NODE_TEXT_AREA_PLACEHOLDER_COLOR  | 无输入时默认提示文本的颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式。 |
| NODE_TEXT_AREA_PLACEHOLDER_FONT  | 无输入时默认提示文本的字体配置（包括大小、字重、样式、字体列表）属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.f32：可选字体大小数值，默认值16.0，单位为fp；<br/>.value[1]?.i32：可选字体样式[ArkUI_FontStyle](#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL；<br/>.value[2]?.i32：可选字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL；<br/>?.string: 字体族内容，多个字体族之间使用逗号分隔，形如“字重；字体族1，字体族2”。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：字体大小数值，单位为fp；<br/>.value[1].i32：字体样式[ArkUI_FontStyle](#arkui_fontstyle)；<br/>.value[2].i32：字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)；<br/>.string: 字体族内容，多个字体族之间使用逗号分隔。 |
| NODE_TEXT_AREA_CARET_COLOR  | 光标颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：背景色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：背景色数值，0xargb格式。 |
| NODE_TEXT_AREA_EDITING  | 控制多行文本输入框编辑态属性，支持属性设置。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示退出编辑态，true表示维持现状。<br/>属性获取方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示退出编辑态，true表示维持现状。 |
| NODE_TEXT_AREA_TYPE  | 输入框的类型属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：输入框类型枚举[ArkUI_TextAreaType](#arkui_textareatype)，默认值为ARKUI_TEXTAREA_TYPE_NORMAL。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：输入框类型枚举[ArkUI_TextAreaType](#arkui_textareatype)。 |
| NODE_TEXT_AREA_SHOW_COUNTER  | 设置输入的字符数超过阈值时是否显示计数器并设置计数器样式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否开启计数器，值为true时为开启。<br/>.value[1]?.f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围1-100，小数时向下取整。<br/>.value[2]?.i32：输入字符超出限制时是否高亮边框。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否开启计数器。<br/>.value[1].f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围1-100。<br/>.value[2].i32：输入字符超出限制时是否高亮边框，默认高亮。 |
| NODE_TEXT_AREA_SELECTION_MENU_HIDDEN  | 设置长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。 |
| NODE_TEXT_AREA_BLUR_ON_SUBMIT  | 设置多行输入框在submit状态下，触发回车键是否失焦。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否失焦。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否失焦。 |
| NODE_TEXT_AREA_INPUT_FILTER  | 通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。仅支持单个字符匹配，不支持字符串匹配。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 正则表达式。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 正则表达式。 |
| NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR  | 设置文本选中底板颜色，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式。 |
| NODE_TEXT_AREA_ENTER_KEY_TYPE  | 设置输入法回车键类型，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_DONE。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](#arkui_enterkeytype)。 |
| NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS  | 设置TextArea通过点击以外的方式获焦时，是否绑定输入法，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示聚焦不拉起输入法，true表示拉起，默认值为true。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起。 |
| NODE_TEXT_AREA_CARET_OFFSET  | 设置或获取光标所在位置信息。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>设置输入光标的位置。 .value[0].i32： 从字符串开始到光标所在位置的字符长度。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>返回当前光标所在位置信息。在当前帧更新光标位置同时调用该接口，该接口不生效 value[0].i32：光标所在位置的索引值。<br/>value[1].f32：光标相对输入框的x坐标位值。<br/>value[2].f32：光标相对输入框的y坐标位值。 |
| NODE_TEXT_AREA_CONTENT_RECT  | 获取已编辑文本内容区域相对组件的位置和大小。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].f32：水平方向横坐标。<br/>value[1].f32：竖直方向纵坐标。<br/>value[2].f32：内容宽度大小。<br/>value[3].f32：内容高度大小。 |
| NODE_TEXT_AREA_CONTENT_LINE_COUNT  | 获取已编辑文本内容的行数。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].i32：已编辑文本内容行数。 |
| NODE_TEXT_AREA_TEXT_SELECTION  | 组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取、高亮显示。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：选中文本的起始位置；<br/>.value[1].i32：选中文本的终止位置；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：选中文本的起始位置；<br/>.value[1].i32：选中文本的终止位置； |
| NODE_TEXT_AREA_ENABLE_AUTO_FILL  | 设置是否启用自动填充。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否启用自动填充，默认值true。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否启用自动填充。 |
| NODE_TEXT_AREA_CONTENT_TYPE  | 自动填充类型。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 参数类型[ArkUI_TextInputContentType](#arkui_textinputcontenttype)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 参数类型[ArkUI_TextInputContentType](#arkui_textinputcontenttype)。 |
| NODE_TEXT_AREA_NUMBER_OF_LINES  | 设置该属性后，通过该属性计算textArea组件的高度。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 设置numberOfLines的值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 设置numberOfLines的值。 |
| NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS  | 设置输入框获取焦点时是否弹出键盘，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否弹出键盘。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否弹出键盘。 |
| NODE_TEXT_AREA_LETTER_SPACING  | 设置输入框字符间距，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 字符间距，默认单位为FP。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 字符间距，默认单位为FP。 |
| NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT  | 设置输入框开启字符预上屏，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启字符预上屏。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启字符预上屏。 |
| NODE_TEXT_AREA_HALF_LEADING  | 设置文本将行间距平分至行的顶部与底部。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 文本是否将行间距平分至行的顶部与底部，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 文本是否将行间距平分至行的顶部与底部。<br/>**起始版本：** 18 |
| NODE_TEXT_AREA_KEYBOARD_APPEARANCE  | 设置输入框拉起的键盘样式。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 设置对应的键盘样式，类型为[ArkUI_KeyboardAppearance](#arkui_keyboardappearance)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 对应的键盘样式，类型为[ArkUI_KeyboardAppearance](#arkui_keyboardappearance)。<br/>起始版本：<br/>15 |
| NODE_TEXT_AREA_MAX_LINES  | 设置输入框内联模式编辑态时文本可显示的最大行数，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：内联输入风格编辑态时文本可显示的最大行数。内联模式下，默认值是3，非内联模式下，默认值是+∞，不限制最大行数。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：最大行数的数字。<br/>**说明：**<br/>设置为undefined时，最大行数设置为5。<br/>**起始版本：** 20 |
| NODE_TEXT_AREA_LINE_SPACING  | 设置输入框文本的行间距，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本的行间距的数字。默认值是0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本的行间距的数字。<br/>**说明：**<br/>设置为undefined时，行间距设置为5。<br/>**起始版本：** 20 |
| NODE_TEXT_AREA_MIN_LINES   | 设置节点的最小行数，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：最小行数的数字。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：最小行数的数字。<br/>**起始版本：** 20 |
| NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL  | 设置支持滚动时节点的最大行数，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：支持滚动时的最大行数的数字。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：支持滚动时的最大行数的数字。<br/>**起始版本：** 20 |
| NODE_TEXT_AREA_LINE_HEIGHT  | 设置输入框文本的高度，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本的高度的数字。默认值是自适应字体大小，单位为fp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：文本的高度的数字。<br/>**说明：**<br/>设置为undefined时，文本的高度设置为5。<br/>**起始版本：** 20 |
| NODE_BUTTON_LABEL  | button按钮的文本内容属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认文本的内容。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：默认文本的内容。 |
| NODE_BUTTON_TYPE  | Button按钮的样式属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置Button按钮的样式，参数类型[ArkUI_ButtonType](#arkui_buttontype)，默认值为ARKUI_BUTTON_TYPE_CAPSULE。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：获取Button按钮的样式，参数类型[ArkUI_ButtonType](#arkui_buttontype)，默认值为ARKUI_BUTTON_TYPE_CAPSULE。 | 
| NODE_BUTTON_MIN_FONT_SCALE<sup>18+</sup>  | 设置文本最小的字体缩放倍数，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 设置Button按钮的最小字体缩放倍数，默认单位fp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 获取Button按钮的最小字体缩放倍数，默认单位fp。 |
| NODE_BUTTON_MAX_FONT_SCALE<sup>18+</sup>  | 设置文本最大的字体缩放倍数，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 设置Button按钮的最大字体缩放倍数，默认单位fp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 获取Button按钮的最大字体缩放倍数，默认单位fp。 |
| NODE_PROGRESS_VALUE  | 进度条的当前进度值属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：进度条当前值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：进度条当前值。 |
| NODE_PROGRESS_TOTAL  | 进度条的总长属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：进度条总长。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：进度条总长。 |
| NODE_PROGRESS_COLOR  | 进度条显示进度值的颜色属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：颜色数值，0xargb格式。 |
| NODE_PROGRESS_TYPE  | 进度条的类型属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：进度条类型枚举值[ArkUI_ProgressType](#arkui_progresstype)，默认值为ARKUI_PROGRESS_TYPE_LINEAR。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：进度条类型枚举值[ArkUI_ProgressType](#arkui_progresstype)。 |
| NODE_PROGRESS_LINEAR_STYLE | 线性进度条样式，支持属性设置，属性重置和属性获取接口，如果进度条类型不是线性样式则不生效。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用{@link [ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)}对象设置组件样式。 <br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用{@link [ArkUI_ProgressLinearStyleOption](#arkui_progresslinearstyleoption)}对象获取组件样式。<br/>**起始版本：** 15|
| NODE_CHECKBOX_SELECT  | CheckBox多选框是否选中，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：1表示选中，0表示不选中。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：1表示选中，0表示不选中。 |
| NODE_CHECKBOX_SELECT_COLOR  | CheckBox多选框选中状态颜色，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：多选框选中状态颜色, 类型为0xargb，如0xFF1122FF。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：多选框选中状态颜色, 类型为0xargb，如0xFF1122FF。 |
| NODE_CHECKBOX_UNSELECT_COLOR  | CheckBox多选框非选中状态边框颜色，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：边框颜色, 类型为0xargb，如0xFF1122FF。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：边框颜色, 类型为0xargb，如0xFF1122FF。 |
| NODE_CHECKBOX_MARK  | CheckBox多选框内部图标样式，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：边框颜色, 类型为0xargb，如0xFF1122FF；<br/>.value[1]?.f32：可选，内部图标大小，单位vp；<br/>.value[2]?.f32：可选，内部图标粗细，单位vp，默认值2。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：边框颜色, 类型为0xargb，如0xFF1122FF；<br/>.value[1].f32：内部图标大小，单位vp；<br/>.value[2].f32：内部图标粗细，单位vp，默认值2。 |
| NODE_CHECKBOX_SHAPE  | CheckBox组件形状, 支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：组件形状，参数类型[ArkUI_CheckboxShape](#arkui_checkboxshape)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：组件形状，参数类型[ArkUI_CheckboxShape](#arkui_checkboxshape)。 |
| NODE_CHECKBOX_NAME  | CheckBox名称设置, 支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string：多选框名称。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：多选框名称。<br/>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP  | CheckBox多选框所属群组的名称设置, 支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string：多选框所属群组的名称。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：多选框所属群组的名称。<br/>**起始版本：** 15 |
| NODE_XCOMPONENT_ID  | XComponent组件ID属性，支持属性设置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: ID的内容。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: ID的内容。 |
| NODE_XCOMPONENT_TYPE  | XComponent的类型，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：字体样式[ArkUI_XComponentType](#arkui_xcomponenttype)，默认值为ARKUI_XCOMPONENT_TYPE_SURFACE；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：字体样式[ArkUI_XComponentType](#arkui_xcomponenttype)。 |
| NODE_XCOMPONENT_SURFACE_SIZE  | 设置XComponent的宽高，支持属性设置和获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：宽数值，单位为px；<br/>.value[1].u32：高数值，单位为px；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：宽数值，单位为px；<br/>.value[1].u32：高数值，单位为px； |
| NODE_XCOMPONENT_SURFACE_RECT | 设置XComponent组件持有Surface的显示区域，支持属性设置和获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：Surface显示区域相对于XComponent组件左上角的x轴坐标, 单位为px。<br/>.value[1].i32：Surface显示区域相对于XComponent组件左上角的y轴坐标, 单位为px。<br/>.value[2].i32：Surface显示区域的宽度, 单位为px。<br/>.value[3].i32：Surface显示区域的高度, 单位为px。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：Surface显示区域相对于XComponent组件左上角的x轴坐标, 单位为px。<br/>.value[1].i32：Surface显示区域相对于XComponent组件左上角的y轴坐标, 单位为px。<br/>.value[2].i32：Surface显示区域的宽度, 单位为px。<br/>.value[3].i32：Surface显示区域的高度, 单位为px。<br/>**起始版本：** 18 |
| NODE_XCOMPONENT_ENABLE_ANALYZER | 设置XComponent组件是否支持图像分析，支持属性设置和获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否支持图像分析，1表示支持图像分析，0表示不支持图像分析。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否支持图像分析，1表示支持图像分析，0表示不支持图像分析。<br/>**起始版本：** 18 |
| NODE_DATE_PICKER_LUNAR  | 设置日期选择器组件的日期是否显示农历，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否显示农历，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否显示农历。 |
| NODE_DATE_PICKER_START  | 设置日期选择器组件选择器的起始日期，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 日期，默认值"1970-1-1"。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 日期。<br/>**起始版本：** 18 |
| NODE_DATE_PICKER_END  | 设置日期选择器组件选择器的结束日期，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 日期，默认值"2100-12-31"。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 日期。<br/>**起始版本：** 18 |
| NODE_DATE_PICKER_SELECTED  | 设置日期选择器组件选中项的日期，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 日期，默认值"2024-01-22"。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 日期。 |
| NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE  | 设置日期选择器组件的所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 入参5个，格式为字符串，以 ';' 分割：<br/>入参1： 文本颜色，::argb类型<br/>入参2： 文本大小，数字类型，单位fp<br/>入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>入参4： 文本字体列表，使用 ',' 进行分割<br/>入参5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 参数5个，格式为字符串，以 ';' 分割：<br/>参数1： 文本颜色，::argb类型<br/>参数2： 文本大小，数字类型，单位fp<br/>参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>参数4： 文本字体列表，使用 ',' 进行分割<br/>参数5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_DATE_PICKER_TEXT_STYLE  | 设置日期选择器组件的所有选项中除了最上、最下及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 入参5个，格式为字符串，以 ';' 分割：<br/>入参1： 文本颜色，::argb类型<br/>入参2： 文本大小，数字类型，单位fp<br/>入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>入参4： 文本字体列表，使用 ',' 进行分割<br/>入参5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 参数5个，格式为字符串，以 ';' 分割：<br/>参数1： 文本颜色，::argb类型<br/>参数2： 文本大小，数字类型，单位fp<br/>参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>参数4： 文本字体列表，使用 ',' 进行分割<br/>参数5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_DATE_PICKER_SELECTED_TEXT_STYLE  | 设置日期选择器组件的选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 入参5个，格式为字符串，以 ';' 分割：<br/>入参1： 文本颜色，::argb类型<br/>入参2： 文本大小，数字类型，单位fp<br/>入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>入参4： 文本字体列表，使用 ',' 进行分割<br/>入参5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 参数5个，格式为字符串，以 ';' 分割：<br/>参数1： 文本颜色，::argb类型<br/>参数2： 文本大小，数字类型，单位fp<br/>参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>参数4： 文本字体列表，使用 ',' 进行分割<br/>参数5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_DATE_PICKER_MODE | 设置要显示的日期选项列。DatePicker显示不同样式的日期列，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：显示的日期列类型，参数类型[ArkUI_DatePickerMode](#arkui_datepickermode)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：显示的日期列类型，参数类型[ArkUI_DatePickerMode](#arkui_datepickermode)。<br/>**起始版本：** 18 |
| NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK | 设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启触控反馈，默认值true。true表示开启触控反馈，false表示不开启触控反馈。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启触控反馈。<br/>**起始版本：** 18 |
| NODE_DATE_PICKER_CAN_LOOP | Picker组件可循环滚动属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示不可循环，true表示可循环。默认值：true，设置异常值时使用默认值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].i32：0表示不可循环，1表示可循环。<br/>**说明：** 可循环情况下，年份随着月份的循环滚动进行联动加减，月份随着日的循环滚动进行联动加减。<br/>不可循环情况下，年/月/日到达本列的顶部或底部时，无法再进行滚动，年/月/日之间也无法再联动加减。<br/>**起始版本：** 20 |
| NODE_TIME_PICKER_SELECTED  | 设置时间选择组件选中项的时间，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 时间，默认值当前系统时间。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 时间。 |
| NODE_TIME_PICKER_USE_MILITARY_TIME  | 设置时间选择组件展示时间是否为24小时制，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否为24小时制，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否为24小时制。 |
| NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE  | 设置时间选择组件所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 入参5个，格式为字符串，以 ';' 分割：<br/>入参1： 文本颜色，::argb类型<br/>入参2： 文本大小，数字类型，单位fp<br/>入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>入参4： 文本字体列表，使用 ',' 进行分割<br/>入参5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 参数5个，格式为字符串，以 ';' 分割：<br/>参数1： 文本颜色，::argb类型<br/>参数2： 文本大小，数字类型，单位fp<br/>参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>参数4： 文本字体列表，使用 ',' 进行分割<br/>参数5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TIME_PICKER_TEXT_STYLE  | 设置时间选择组件所有选项中除了最上、最下及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 入参5个，格式为字符串，以 ';' 分割：<br/>入参1： 文本颜色，::argb类型<br/>入参2： 文本大小，数字类型，单位fp<br/>入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>入参4： 文本字体列表，使用 ',' 进行分割<br/>入参5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 参数5个，格式为字符串，以 ';' 分割：<br/>参数1： 文本颜色，::argb类型<br/>参数2： 文本大小，数字类型，单位fp<br/>参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>参数4： 文本字体列表，使用 ',' 进行分割<br/>参数5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TIME_PICKER_SELECTED_TEXT_STYLE  | 设置时间选择组件选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 入参5个，格式为字符串，以 ';' 分割：<br/>入参1： 文本颜色，::argb类型<br/>入参2： 文本大小，数字类型，单位fp<br/>入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>入参4： 文本字体列表，使用 ',' 进行分割<br/>入参5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 参数5个，格式为字符串，以 ';' 分割：<br/>参数1： 文本颜色，::argb类型<br/>参数2： 文本大小，数字类型，单位fp<br/>参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>参数4： 文本字体列表，使用 ',' 进行分割<br/>参数5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TIME_PICKER_START  | 设置时间选择器组件的起始时间，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 时间，默认值"00:00"，仅生效设置的小时和分钟。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 时间，默认值"00:00"。<br/>**起始版本**：18 |
| NODE_TIME_PICKER_END  | 设置时间选择器组件的结束日期，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 时间，默认值"23:59"，仅生效设置的小时和分钟。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 时间，默认值"23:59"。<br/>**起始版本**：18 |
| NODE_TIME_PICKER_ENABLE_CASCADE  | 在设置12小时制时，上午和下午的标识会根据小时数自动切换。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 在12小时制时，设置上午和下午的标识是否会根据小时数自动切换，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 在12小时制时，设置上午和下午的标识是否会根据小时数自动切换。<br/>**起始版本**：18 |
| NODE_TEXT_PICKER_OPTION_RANGE  | 设置滑动选择文本选择器的选择列表，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：使用的选择器类型[ArkUI_TextPickerRangeType](#arkui_textpickerrangetype)，默认值为ARKUI_TEXTPICKER_RANGETYPE_SINGLE；<br/>?.string：针对不同选择器类型有如下输入范式：<br/>1：单列选择器，入参格式为用分号分隔的一组字符串；<br/>2：多列选择器，支持多对纯文本字符串对，多对之间使用分号分隔，每对内部使用逗号分隔；<br/>?.object：针对不同选择器类型有如下输入范式：<br/>1：单列支持图片的选择器，输入结构体为[ARKUI_TextPickerRangeContent](_a_r_k_u_i___text_picker_range_content.md)；<br/>2：多列联动选择器，输入结构体为[ARKUI_TextPickerCascadeRangeContent](_a_r_k_u_i___text_picker_cascade_range_content.md)；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：使用的选择器类型[ArkUI_TextPickerRangeType](#arkui_textpickerrangetype)；<br/>?.string：针对不同选择器类型有如下输出范式：<br/>1：单列选择器，输出格式为用分号分隔的一组字符串；<br/>2：多列选择器，输出多对纯文本字符串对，多对之间使用分号分隔，每对内部使用逗号分隔；<br/>?.object：针对不同选择器类型有如下输出范式：<br/>1：单列支持图片的选择器，输出结构体为[ARKUI_TextPickerRangeContent](_a_r_k_u_i___text_picker_range_content.md)；<br/>2：多列联动选择器，输出结构体为[ARKUI_TextPickerCascadeRangeContent](_a_r_k_u_i___text_picker_cascade_range_content.md)； |
| NODE_TEXT_PICKER_OPTION_SELECTED  | 设置滑动选择文本内容的组件默认选中项在数组中的索引值，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：索引值，如存在多个索引值则逐个添加。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：索引值，如存在多个索引值则逐个添加； |
| NODE_TEXT_PICKER_OPTION_VALUE  | 设置滑动选择文本内容的组件默认选中项的值，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：选中项的值，如存在多个值则逐个添加，用分号分隔。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：选中项的值，如存在多个值则逐个添加，用分号分隔； |
| NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE  | 设置滑动选择文本内容的组件所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 入参5个，格式为字符串，以 ';' 分割：<br/>入参1： 文本颜色，::argb类型<br/>入参2： 文本大小，数字类型，单位fp<br/>入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>入参4： 文本字体列表，使用 ',' 进行分割<br/>入参5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 参数5个，格式为字符串，以 ';' 分割：<br/>参数1： 文本颜色，::argb类型<br/>参数2： 文本大小，数字类型，单位fp<br/>参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>参数4： 文本字体列表，使用 ',' 进行分割<br/>参数5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TEXT_PICKER_TEXT_STYLE  | 设置滑动选择文本内容的组件所有选项中除了最上、最下及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 入参5个，格式为字符串，以 ';' 分割：<br/>入参1： 文本颜色，::argb类型<br/>入参2： 文本大小，数字类型，单位fp<br/>入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>入参4： 文本字体列表，使用 ',' 进行分割<br/>入参5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 参数5个，格式为字符串，以 ';' 分割：<br/>参数1： 文本颜色，::argb类型<br/>参数2： 文本大小，数字类型，单位fp<br/>参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")<br/>参数4： 文本字体列表，使用 ',' 进行分割<br/>参数5： 文本样式，字符串枚举("normal", "italic")<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TEXT_PICKER_SELECTED_TEXT_STYLE  | 设置滑动选择文本内容的组件选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 入参5个，格式为字符串，以 ';' 分割：<br/>入参1： 文本颜色，::argb类型；<br/>入参2： 文本大小，数字类型，单位fp；<br/>入参3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")；<br/>入参4： 文本字体列表，使用 ',' 进行分割；<br/>入参5： 文本样式，字符串枚举("normal", "italic")；<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string： 参数5个，格式为字符串，以 ';' 分割：<br/>参数1： 文本颜色，::argb类型；<br/>参数2： 文本大小，数字类型，单位fp；<br/>参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")；<br/>参数4： 文本字体列表，使用 ',' 进行分割；<br/>参数5： 文本样式，字符串枚举("normal", "italic")；<br/>如 "\#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 |
| NODE_TEXT_PICKER_SELECTED_INDEX  | 设置滑动选择文本内容的组件默认选中项在数组中的索引值，支持属性设置，属性重置和属性获取接口。<br/>[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数类型：<br/>.value[0...].i32：默认选中项在数组中的索引值数组。 |
| NODE_TEXT_PICKER_CAN_LOOP  | Picker组件可循环滚动属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：false表示不可循环，true表示可循环。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].i32：0表示不可循环，1表示可循环。 |
| NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT  | Picker各选择项的高度属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：子项高度属性，单位为vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>value[0].f32：子项高度属性，单位为vp。 |
| NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK | 设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启触控反馈。默认值：true，true表示开启触控反馈，false则表示不开启触控反馈。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启触控反馈。<br/>**起始版本：** 18 |
| NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE | 设置选中项背景样式。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>入参为5个：<br/> .value[0].u32 选中项背景颜色 ::argb类型；<br/> .value[1].f32 选中项背景左上方圆角半径， 单位为vp；<br/> .value[2].f32 选中项背景右上方圆角半径，单位为vp；<br/> .value[3].f32 选中项背景左下方圆角半径，单位为vp；<br/> .value[4].f32 选中项背景右下方圆角半径，单位为vp。<br/>注意：当入参只有两个时，.value[1].f32将用于设置四个圆角半径的值。<br/>默认值：背景颜色：0x0c182431，四个圆角半径：24vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>参数为5个：<br/> .value[0].u32 选中项背景颜色 ::argb类型；<br/> .value[1].f32 选中项背景左上方圆角半径，单位为vp；<br/>.value[2].f32 选中项背景右上方圆角半径，单位为vp；<br/>.value[3].f32 选中项背景左下方圆角半径，单位为vp；<br/>.value[4].f32 选中项背景右下方圆角半径，单位为vp。<br/>**起始版本：** 20|
| NODE_CALENDAR_PICKER_HINT_RADIUS  | 设置日历选中态底板圆角半径的参数，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 日历选中态底板圆角半径，取值范围[0,+∞)，其中取值为0表示底板样式为直角矩形； 取值范围为(0, 16)时，底板样式为圆角矩形；取值范围为[16,+∞)时，底板样式为圆形。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 日历选中态底板圆角半径，取值范围[0,+∞)，其中取值为0表示底板样式为直角矩形； 取值范围为(0, 16)时，底板样式为圆角矩形；取值范围为[16,+∞)时，底板样式为圆形。 |
| NODE_CALENDAR_PICKER_SELECTED_DATE  | 设置日历选择选中日期的参数，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32： 选中的年。<br/>.value[1].u32： 选中的月。<br/>.value[2].u32： 选中的日。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32： 选中的年。<br/>.value[1].u32： 选中的月。<br/>.value[2].u32： 选中的日。 |
| NODE_CALENDAR_PICKER_EDGE_ALIGNMENT  | 设置日历选择器与入口组件的对齐方式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 对齐方式类型，参数类型[ArkUI_CalendarAlignment](#arkui_calendaralignment)。<br/>.value[1]?.f32： 按照对齐方式对齐后，选择器相对入口组件的x轴方向相对偏移。<br/>.value[2]?.f32： 按照对齐方式对齐后，选择器相对入口组件的y轴方向相对偏移。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 对齐方式类型，参数类型[ArkUI_CalendarAlignment](#arkui_calendaralignment)。<br/>.value[1].f32： 按照对齐方式对齐后，选择器相对入口组件的x轴方向相对偏移。<br/>.value[2].f32： 按照对齐方式对齐后，选择器相对入口组件的y轴方向相对偏移。 |
| NODE_CALENDAR_PICKER_TEXT_STYLE  | 设置日历选择器入口区的文本颜色、字号、字体粗细。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.u32： 入口区的文本颜色。<br/>.value[1]?.f32： 入口区的文本字号，单位为fp。<br/>.value[2]?.i32： 入口区的文本字体粗细，参数类型[ArkUI_FontWeight](#arkui_fontweight)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32： 入口区的文本颜色。<br/>.value[1].f32： 入口区的文本字号，单位为fp。<br/>.value[2].i32： 入口区的文本字体粗细，参数类型[ArkUI_FontWeight](#arkui_fontweight)。 |
| NODE_CALENDAR_PICKER_START | 设置日历选择器的开始日期。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：开始日期字符串。<br/>设置开始日期格式："2025-02-14"。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：开始日期字符串。<br/>**起始版本：** 18 |
| NODE_CALENDAR_PICKER_END  | 设置日历选择器的结束日期。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：结束日期字符串。<br/>设置结束日期格式："2025-02-27"。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：结束日期字符串。<br/>**起始版本：** 18 |
| NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE  | 设置日历选择器的禁用日期区间。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：禁用日期区间字符串。禁用日期区间："第一个区间开始日期，第一个区间结束日期，第二个区间开始日期，第二个区间结束日期，...，第n个区间开始日期，第n个区间结束日期"。<br/>设置的禁用日期区间格式："1910-01-01，1910-12-31，2020-01-01，2020-12-31"。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>string：禁用日期区间字符串。<br/>**起始版本：** 19 |
| NODE_CALENDAR_PICKER_MARK_TODAY  | 设置日历选择器在系统当前日期时，是否保持高亮显示。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：true代表日历选择器在系统当前日期时，保持高亮显示。false代表日历选择器在系统当前日期时，不保持高亮显示。默认值：false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：1代表日历选择器在系统当前日期时，保持高亮显示。0代表日历选择器在系统当前日期时，不保持高亮显示。<br/>**起始版本：** 19 |
| NODE_SLIDER_BLOCK_COLOR  | Slider滑块的颜色，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：滑块的颜色，类型为0xargb，如0xFF1122FF。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：滑块的颜色，类型为0xargb，如0xFF1122FF。 |
| NODE_SLIDER_TRACK_COLOR  | Slider滑轨的背景颜色，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：背景颜色，类型为0xargb，如0xFF1122FF。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：背景颜色，类型为0xargb，如0xFF1122FF。 |
| NODE_SLIDER_SELECTED_COLOR  | Slider滑轨的已滑动部分颜色，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：已滑动部分颜色，类型为0xargb，如0xFF1122FF。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：已滑动部分颜色，类型为0xargb，如0xFF1122FF。 |
| NODE_SLIDER_SHOW_STEPS  | 设置是否显示步长刻度值，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：是否显示步长刻度值，1表示显示，0表示不显示，默认值为0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否显示步长刻度值，1表示显示，0表示不显示，默认值为0。 |
| NODE_SLIDER_BLOCK_STYLE  | Slider滑块形状参数，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：形状参数。参数类型[ArkUI_SliderBlockStyle](#arkui_sliderblockstyle)。<br/>.string? 可选值，根据形状参数而定。<br/>ARKUI_SLIDER_BLOCK_STYLE_IMAGE：滑块图片资源。如/pages/common/icon.png。<br/>ARKUI_SLIDER_BLOCK_STYLE_SHAPE：滑块使用的自定义形状。<br/>共有5种类型：<br/>1.rect类型：<br/>.value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](#arkui_shapetype)，ARKUI_SHAPE_TYPE_RECTANGLE；<br/>.value[2].f32：矩形宽度；<br/>.value[3].f32：矩形高度；<br/>.value[4].f32：矩形圆角宽度；<br/>.value[5].f32：矩形圆角高度。<br/>2.circle类型：<br/>.value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](#arkui_shapetype)，ARKUI_SHAPE_TYPE_CIRCLE；<br/>.value[2].f32：圆形宽度；<br/>.value[3].f32：圆形高度。<br/>3.ellipse类型：<br/>.value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](#arkui_shapetype)，ARKUI_SHAPE_TYPE_ELLIPSE；<br/>.value[2].f32：椭圆形宽度；<br/>.value[3].f32：椭圆形高度。<br/>4.path类型：<br/>.value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](#arkui_shapetype)，ARKUI_SHAPE_TYPE_PATH；<br/>.value[2].f32：路径宽度；<br/>.value[3].f32：路径高度；<br/>.string：路径绘制的命令字符串。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：形状参数。参数类型[ArkUI_SliderBlockStyle](#arkui_sliderblockstyle)。<br/>.string? 可选值，根据形状参数而定。<br/>ARKUI_SLIDER_BLOCK_STYLE_IMAGE：滑块图片资源。如/pages/common/icon.png。<br/>ARKUI_SLIDER_BLOCK_STYLE_SHAPE：滑块使用的自定义形状。<br/>共有5种类型：<br/>1.rect类型：<br/>.value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](#arkui_shapetype)，ARKUI_SHAPE_TYPE_RECTANGLE；<br/>.value[2].f32：矩形宽度；<br/>.value[3].f32：矩形高度；<br/>.value[4].f32：矩形圆角宽度；<br/>.value[5].f32：矩形圆角高度。<br/>2.circle类型：<br/>.value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](#arkui_shapetype)，ARKUI_SHAPE_TYPE_CIRCLE；<br/>.value[2].f32：圆形宽度；<br/>.value[3].f32：圆形高度。<br/>3.ellipse类型：<br/>.value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](#arkui_shapetype)，ARKUI_SHAPE_TYPE_ELLIPSE；<br/>.value[2].f32：椭圆形宽度；<br/>.value[3].f32：椭圆形高度。<br/>4.path类型：<br/>.value[1].i32：裁剪类型，参数类型[ArkUI_ShapeType](#arkui_shapetype)，ARKUI_SHAPE_TYPE_PATH；<br/>.value[2].f32：路径宽度；<br/>.value[3].f32：路径高度；<br/>.string：路径绘制的命令字符串。 |
| NODE_SLIDER_VALUE  | slider进度值，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：进度值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：进度值。 |
| NODE_SLIDER_MIN_VALUE  | slider最小值，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：进度值的最小值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：进度值的最小值。 |
| NODE_SLIDER_MAX_VALUE  | slider最大值，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：进度值的最大值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：进度值的最大值。 |
| NODE_SLIDER_STEP  | Slider滑动步长，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：滑动步长，取值范围：[0.01, 100]。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：滑动步长，取值范围：[0.01, 100]。 |
| NODE_SLIDER_DIRECTION  | Slider滑动条滑动方向，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：显示样式，参数类型[ArkUI_SliderDirection](#arkui_sliderdirection)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：显示样式，参数类型[ArkUI_SliderDirection](#arkui_sliderdirection)。 |
| NODE_SLIDER_REVERSE  | Slider滑动条取值范围是否反向，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：是否反向，1表示反向，0表示不反向。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否反向，1表示反向，0表示不反向。 |
| NODE_SLIDER_STYLE  | Slider的滑块与滑轨显示样式，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：显示样式，参数类型[ArkUI_SliderStyle](#arkui_sliderstyle)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：显示样式，参数类型[ArkUI_SliderStyle](#arkui_sliderstyle)。 |
| NODE_SLIDER_TRACK_THICKNESS  | Slider滑块的滑轨粗细属性，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：滑轨的粗细，单位为vp；当参数NODE_SLIDER_STYLE的值设置为ARKUI_SLIDER_STYLE_OUT_SET时为4.0vp，设置为ARKUI_SLIDER_STYLE_IN_SET时为20.0vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：滑轨的粗细，单位为vp。 |
| NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK | 设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启触控反馈。默认值：true，表示开启触控反馈，false则表示不开启触控反馈。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否开启触控反馈。<br/>开启触控反馈时，需要在工程的module.json5的requestPermissions字段中增加"name": "ohos.permission.VIBRATE"，开启振动权限。 <br/>**起始版本：** 18 |
| NODE_SLIDER_PREFIX  | 在Slider组件的前缀设置自定义组件。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.object：参数类型[ArkUI_NodeHandle](#arkui_nodehandle)。 <br/>**起始版本：** 20 | 
| NODE_SLIDER_SUFFIX  | 在Slider组件的后缀设置自定义组件。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.object：参数类型[ArkUI_NodeHandle](#arkui_nodehandle)。 <br/>**起始版本：** 20 | 
| NODE_RADIO_CHECKED  | 设置单选框的选中状态，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：单选框的选中状态，默认值false。 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：单选框的选中状态。 |
| NODE_RADIO_STYLE  | 设置单选框选中状态和非选中状态的样式，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0]?.u32：开启状态底板颜色，类型为0xargb，默认值为0xFF007DFF。<br/>.value[1]?.u32：关闭状态描边颜色，类型为0xargb，默认值为0xFF182431。<br/>.value[2]?.u32：开启状态内部圆饼颜色，类型为0xargb，默认值为0xFFFFFFFF。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：开启状态底板颜色，类型为0xargb，默认值为0xFF007DFF。<br/>.value[1].u32：关闭状态描边颜色，类型为0xargb，默认值为0xFF182431。<br/>.value[2].u32：开启状态内部圆饼颜色，类型为0xargb，默认值为0xFFFFFFF。 |
| NODE_RADIO_VALUE  | 设置当前单选框的值，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string：单选框的值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：单选框的值。 |
| NODE_RADIO_GROUP  | 设置当前单选框的所属群组名称，相同group的Radio只能有一个被选中，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string：当前单选框的所属群组名称。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：当前单选框的所属群组名称。 |
| NODE_CHECKBOX_GROUP_NAME  | 设置多选框组名称，多个相同群组名称的CheckboxGroup，仅第一个CheckboxGroup生效，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string：当前多选框组名称。<br/> 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string：多选框组名称。<br/>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_SELECT_ALL  | 是否全选。设置是否全选。若同组的checkbox显式设置了select属性，则Checkbox的优先级高，支持属性设置，属性重置和属性获取。<br/>默认值：false<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：1表示选中，0表示未选中。<br/> 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：1表示选中，0表示未选中。<br/>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_SELECTED_COLOR  | 被选中或部分选中状态的颜色，支持属性设置，属性重置和属性获取。<br/>默认值：false<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：多选框组被选中状态的颜色，类型为0xargb，如0xFF1122FF。<br/> 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：多选框组被选中状态的颜色，类型为0xargb，如0xFF1122FF。<br/>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_UNSELECTED_COLOR  | 非选中状态多选框组颜色，支持属性设置，属性重置和属性获取。<br/>默认值：false<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：边框颜色，类型为0xargb，如0xFF1122FF。<br/> 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：边框颜色，类型为0xargb，如0xFF1122FF。<br/>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_MARK  | 多选框内部图标样式，支持属性设置，属性重置和属性获取。<br/>默认值：false<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].u32：边框颜色，类型为0xargb，如0xFF1122FF;<br/>.value[1]?.f32：可选，内部图标大小，单位vp;<br/>.value[2]?.f32：可选，内部图标粗细，单位vp,默认值2。<br/> 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：边框颜色，类型为0xargb，如0xFF1122FF;<br/>.value[1]?.f32：可选，内部图标大小，单位vp;<br/>.value[2]?.f32：可选，内部图标粗细，单位vp，默认值2。<br/>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_SHAPE  | CheckboxGroup组件形状，支持属性设置，属性重置和属性获取。<br/>默认值：false<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：组件形状，参数类型[ArkUI_CheckboxShape](#arkui_checkboxshape)。<br/> 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：组件形状，参数类型[ArkUI_CheckboxShape](#arkui_checkboxshape)。<br/>**起始版本：** 15 |
| NODE_STACK_ALIGN_CONTENT  | 设置子组件在容器内的对齐方式，支持属性设置，属性重置和属性获取接口。<br/>该属性与通用属性NODE_ALIGNMENT同时设置时，后设置的属性生效。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：对齐方式，数据类型[ArkUI_Alignment](#arkui_alignment)，默认值ARKUI_ALIGNMENT_CENTER。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：对齐方式，数据类型[ArkUI_Alignment](#arkui_alignment)。 |
| NODE_SCROLL_BAR_DISPLAY_MODE  | 设置滚动条状态，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](#arkui_scrollbardisplaymode)，默认值ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](#arkui_scrollbardisplaymode)。 |
| NODE_SCROLL_BAR_WIDTH  | 设置滚动条的宽度，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 滚动条宽度，单位vp，默认值4。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 滚动条宽度，单位vp。 |
| NODE_SCROLL_BAR_COLOR  | 设置滚动条的颜色，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.data[0].u32： 滚动条颜色，0xargb类型。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.data[0].u32： 滚动条颜色，0xargb类型。 |
| NODE_SCROLL_BAR_MARGIN  | 设置滚动条的边距，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：设置滚动条起始边距，默认值为0，单位：vp。<br/>.value[1].f32：设置滚动条末尾边距，默认值为0，单位：vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：滚动条起始边距，单位：vp。<br/>.value[1].f32：滚动条末尾边距，单位：vp。<br/>**起始版本：** 20 |
| NODE_SCROLL_SCROLL_DIRECTION  | 设置滚动方向，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：滚动方向，数据类型[ArkUI_ScrollDirection](#arkui_scrolldirection)，默认值ARKUI_SCROLL_DIRECTION_VERTICAL。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：滚动方向，数据类型[ArkUI_ScrollDirection](#arkui_scrolldirection)。 |
| NODE_SCROLL_EDGE_EFFECT  | 设置边缘滑动效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：边缘滑动效果，参数类型[ArkUI_EdgeEffect](#arkui_edgeeffect)，默认值ARKUI_EDGE_EFFECT_NONE；<br/>.value[1]?.i32：可选值，组件内容大小小于组件自身时，设置是否开启滑动效果，开启为1，关闭为0，List/Grid/WaterFlow组件默认值为0，Scroll组件默认值为1；<br/>.value[2]?.i32：边缘效果生效的方向，参数类型[ArkUI_EffectEdge](#arkui_effectedge)，默认值ARKUI_EFFECT_EDGE_START \| ARKUI_EFFECT_EDGE_END。该参数从API version 18开始支持。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：边缘滑动效果，参数类型[ArkUI_EdgeEffect](#arkui_edgeeffect)；<br/>.value[1].i32：组件内容大小小于组件自身时，设置是否开启滑动效果，开启为1，关闭为0；<br/>.value[2].i32：边缘效果生效的方向，参数类型[ArkUI_EffectEdge](#arkui_effectedge)。该参数从API version 18开始支持。 |
| NODE_SCROLL_ENABLE_SCROLL_INTERACTION  | 设置是否支持滚动手势，当设置为false时，无法通过手指或者鼠标滚动，但不影响控制器的滚动接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否支持滚动手势，默认值true。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否支持滚动手势。 |
| NODE_SCROLL_FRICTION  | 设置摩擦系数，手动划动滚动区域时生效，只对惯性滚动过程有影响，对惯性滚动过程中的链式效果有间接影响。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 摩擦系数，默认值：非可穿戴设备为0.6，可穿戴设备为0.9。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 摩擦系数。 |
| NODE_SCROLL_SNAP  | 设置Scroll组件的限位滚动模式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： Scroll组件限位滚动时的对齐方式，数据类型[ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign)，默认值ARKUI_SCROLL_SNAP_ALIGN_NONE；<br/>.value[1].i32： 在Scroll组件限位滚动模式下，该属性设置为false后，允许Scroll在开头和第一页间自由滑动。默认值true，仅在分页点为多个时生效；<br/>.value[2].i32： 在Scroll组件限位滚动模式下，该属性设置为false后，允许Scroll在最后一页和末尾间自由滑动。默认值true，仅在分页点为多个时生效；<br/>.value[3...].f32： Scroll组件限位滚动时的分页点。分页点为1个时，系统按照该大小进行分页；分页点为多个时，系统按照分页点进行分页。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： Scroll组件限位滚动时的对齐方式，数据类型[ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign)；<br/>.value[1].i32： 在Scroll组件限位滚动模式下，该属性设置为false后，允许Scroll在开头和第一页间自由滑动；<br/>.value[2].i32： 在Scroll组件限位滚动模式下，该属性设置为false后，允许Scroll在最后一页和末尾间自由滑动；<br/>.value[3...].f32： Scroll组件限位滚动时的分页点。 |
| NODE_SCROLL_NESTED_SCROLL  | Scroll嵌套滚动选项，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：可滚动组件往末尾端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](#arkui_scrollnestedmode)。<br/>.value[1].i32：可滚动组件往起始端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](#arkui_scrollnestedmode)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：可滚动组件往末尾端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](#arkui_scrollnestedmode)。<br/>.value[1].i32：可滚动组件往起始端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](#arkui_scrollnestedmode)。 |
| NODE_SCROLL_OFFSET  | Scroll滑动到指定位置，支持属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：水平滑动偏移，单位为vp。<br/>.value[1].f32：垂直滑动偏移，单位为vp。<br/>.value[2]?.i32：可选值，滚动时长，单位为毫秒。<br/>.value[3]?.i32：可选值，滚动曲线，参数类型[ArkUI_AnimationCurve](#arkui_animationcurve)。默认值为ARKUI_CURVE_EASE。<br/>.value[4]?.i32：可选值，是否使能默认弹簧动效，默认值为0不使能。<br/>.value[5]?.i32：可选值，设置滚动是否可越界。<br/>.value[6]?.i32：可选值，设置滚动是否可以停留在越界位置。该参数从API version 20开始支持。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：水平滑动偏移，单位为vp。<br/>.value[1].f32：垂直滑动偏移，单位为vp。 |
| NODE_SCROLL_EDGE  | Scroll滚动到容器边缘，支持属性设置，属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：容器边缘，参数类型[ArkUI_ScrollEdge](#arkui_scrolledge)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：容器是否位于边缘，-1：表示未处于边缘，如果处于边缘状态参数类型[ArkUI_ScrollEdge](#arkui_scrolledge)。 |
| NODE_SCROLL_ENABLE_PAGING  | 设置是否支持滑动翻页，支持属性设置，属性重置和属性获取接口。<br/>如果同时设置了划动翻页enablePaging和限位滚动scrollSnap，则scrollSnap优先生效，enablePaging不生效。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否支持划动翻页，默认值false。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32： 是否支持划动翻页。 |
| NODE_SCROLL_PAGE  | 滚动到下一页或者上一页。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 是否向下翻页。0表示向下翻页，1表示向上翻页。<br/>.value[1]?.i32 是否开启翻页动画效果。1有动画，0无动画。默认值：0。 |
| NODE_SCROLL_BY  | 滑动指定距离。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：水平方向滚动距离，默认单位为vp;<br/>.value[1].f32: 竖直方向滚动距离，默认单位为vp。 |
| NODE_SCROLL_FLING  | 滚动类组件按传入的初始速度进行惯性滚动。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：惯性滚动的初始速度，默认单位为vp/s。值设置为0，视为异常值，本次滚动不生效。如果值为正数，则向下滚动；如果值为负数，则向上滚动。<br/>**起始版本：** 13 |
| NODE_SCROLL_FADING_EDGE  | 设置滚动类组件边缘渐隐效果。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否使能边缘渐隐效果。0表示关闭边缘效果。1表示开启边缘效果。<br/>.value[1]?.f32：边缘渐隐效果长度。单位：vp，默认值：32。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否使能边缘渐隐效果。0表示关闭边缘效果。1表示开启边缘效果。<br/>.value[1].f32：边缘渐隐效果长度。单位：vp。<br/>**起始版本：** 14 |
| NODE_SCROLL_SIZE  | 获取滚动类组件所有子组件全展开尺寸。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：滚动类组件所有子组件全展开的宽度，默认单位为vp。<br/>.value[1].f32：滚动类组件所有子组件全展开的高度，默认单位为vp。<br/>设置NODE_PADDING、NODE_MARGIN或NODE_BORDER_WIDTH后，NODE_PADDING、NODE_MARGIN或NODE_BORDER_WIDTH在单位vp转换成单位px时会进行像素取整， 返回值根据取整后的值计算。<br/>**起始版本：** 14 |
| NODE_SCROLL_CONTENT_START_OFFSET | 设置内容区域起始偏移量。列表滚动到起始位置时，列表内容与列表显示区域边界保留指定距离。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：内容区域起始偏移量，默认值：0，单位：vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：内容区域起始偏移量，单位：vp。<br/>**起始版本：** 15 |
| NODE_SCROLL_CONTENT_END_OFFSET | 设置内容区末尾偏移量。列表滚动到末尾位置时，列表内容与列表显示区域边界保留指定距离。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：内容区末尾偏移量，默认值：0，单位：vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：内容区末尾偏移量，单位：vp。<br/>**起始版本：** 15 |
| NODE_SCROLL_FLING_SPEED_LIMIT | 限制跟手滑动结束后，Fling动效开始时的最大初始速度。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：Fling动效开始时的最大初始速度，单位：vp/s。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：Fling动效开始时的最大初始速度。<br/>**起始版本：** 18 |
| NODE_SCROLL_CLIP_CONTENT | 设置滚动容器的内容层裁剪区域。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：内容裁剪模式，参数类型[ArkUI_ContentClipMode](_ark_u_i___native_module.md#arkui_contentclipmode)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：内容裁剪模式，参数类型[ArkUI_ContentClipMode](_ark_u_i___native_module.md#arkui_contentclipmode)。<br/>**起始版本：** 18 |
| NODE_SCROLL_BACK_TO_TOP | 设置滚动容器是否在点击状态栏时回到顶部。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否回到顶部，1表示回到顶部，0表示保持当前位置不变，默认值：<br/>API version 18之前：0。<br/>API version 18及以后：滚动方向是水平方向时为0，是垂直方向时为1。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否回到顶部。<br/>**起始版本：** 15 |
| NODE_LIST_DIRECTION  | 设置List组件排列方向，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：List组件排列方向，数据类型[ArkUI_Axis](#arkui_axis)，默认值ARKUI_AXIS_VERTICAL。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：List组件排列方向，数据类型[ArkUI_Axis](#arkui_axis)。 |
| NODE_LIST_STICKY  | 配合ListItemGroup组件使用，设置ListItemGroup中header和footer是否要吸顶或吸底，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：配合ListItemGroup组件使用，设置ListItemGroup中header和footer是否要吸顶或吸底。数据类型[ArkUI_StickyStyle](#arkui_stickystyle)，默认值ARKUI_STICKY_STYLE_NONE。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：配合ListItemGroup组件使用，设置ListItemGroup中header和footer是否要吸顶或吸底。数据类型[ArkUI_StickyStyle](#arkui_stickystyle)。 |
| NODE_LIST_SPACE  | 设置列表项间距，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 子组件主轴方向的间隔。默认值0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： 子组件主轴方向的间隔。 |
| NODE_LIST_NODE_ADAPTER  | list组件适配器，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用**ArkUI_NodeAdapter**对象作为适配器。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：返回值格式为**ArkUI_NodeAdapter**。 |
| NODE_LIST_CACHED_COUNT  | list组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：配合List组件Adapter使用，设置adapter中的缓存数量；<br/>.value[1].i32：是否显示缓存节点，0：不显示，1：显示，默认值：0。该参数从API version 15开始支持。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：adapter中的缓存数量；<br/>.value[1].i32：是否显示缓存节点，0：不显示，1：显示。该参数从API version 15开始支持。 |
| NODE_LIST_SCROLL_TO_INDEX  | 滑动到指定index。<br/>开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：要滑动到的目标元素在当前容器中的索引值。<br/>.value[1]?.i32：设置滑动到列表项在列表中的索引值时是否有动效，1表示有动效，0表示没有动效。默认值：0。<br/>.value[2]?.i32：指定滑动到的元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](#arkui_scrollalignment), 默认值：ARKUI_SCROLL_ALIGNMENT_START。<br/>.value[3]?.f32：设置滑动到指定Index的选项，如额外偏移量，单位vp。|
| NODE_LIST_ALIGN_LIST_ITEM  | 设置List交叉轴方向宽度大于ListItem交叉轴宽度 \* lanes时， ListItem在List交叉轴方向的布局方式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：交叉轴方向的布局方式。参数类型**ArkUI_ListItemAlign**<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：交叉轴方向的布局方式。参数类型**ArkUI_ListItemAlign** |
| NODE_LIST_CHILDREN_MAIN_SIZE  | 设置List子组件默认主轴尺寸。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>object: 参数格式为{\@ArkUI_ListChildrenMainSize}.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: 参数格式为{\@ArkUI_ListChildrenMainSize}. |
| NODE_LIST_INITIAL_INDEX  | 设置当前List初次加载时视口起始位置显示的item的索引值， 支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 当前List初次加载时视口起始位置显示的item的索引值，默认值：0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 当前List初次加载时视口起始位置显示的item的索引值，默认值：0。 |
| NODE_LIST_DIVIDER  | 设置ListItem分割线样式，默认无分割线，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32： 分割线颜色，0xargb类型；<br/>.value[1].f32： 分割线宽；<br/>.value[2].f32： 分割线距离列表侧边起始端的距离，单位vp；<br/>.value[3].f32： 分割线距离列表侧边结束端的距离，单位vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32： 分割线颜色，0xargb类型；<br/>.value[1].f32： 分割线宽；<br/>.value[2].f32： 分割线距离列表侧边起始端的距离，单位vp；<br/>.value[3].f32： 分割线距离列表侧边结束端的距离，单位vp。 |
| NODE_LIST_SCROLL_TO_INDEX_IN_GROUP | 滑动到指定的ListItemGroup中指定的ListItem。<br/>开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：要滑动到的目标元素所在的ListItemGroup在当前容器中的索引值。<br/>.value[1].i32：要滑动到的目标元素在index指定的ListItemGroup中的索引值。<br/>.value[2]?.i32：设置滑动到列表项在列表中的索引值时是否有动效，1表示有动效，0表示没有动效。默认值：0。<br/>.value[3]?.i32：指定滑动到的元素与当前容器的对齐方式。参数类型[ArkUI_ScrollAlignment](#arkui_scrollalignment), 默认值：ARKUI_SCROLL_ALIGNMENT_START。<br/>**起始版本：** 15 |
| NODE_LIST_LANES | 设置List组件的布局列数或行数，支持属性设置，属性重置和属性获取接口。<br/>使用规则：<br/>lanes为指定的数量时，根据指定的数量与List组件的交叉轴尺寸除以列数作为列的宽度。<br/>设置了{minLength，maxLength}时，lanse的指定数量不会生效，实际会根据List组件的宽度自适应决定lanes数量（即列数），保证缩放过程中lane的宽度符合{minLength，maxLength}的限制，其中，minLength条件会被优先满足，即优先保证符合ListItem的交叉轴尺寸符合最小限制。如果父组件交叉轴方向尺寸约束为无穷大时，固定按一列排列，列宽度按显示区域内最大的ListItem计算。ListItemGroup在多列模式下也是独占一行，ListItemGroup中的ListItem按照List组件的lanes属性设置值来布局，计算列数会按照ListItemGroup的交叉轴尺寸计算。当ListItemGroup交叉轴尺寸与List交叉轴尺寸不一致时ListItemGroup中的列数与List中的列数可能不一样。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32：设置list组件行数或列数（lanes）的数量，默认值为0。<br/>.value[1]?.f32：设置组件listItem的minLength，默认值为1，单位vp。<br/>.value[2]?.f32：设置组件listItem的maxLength，默认值为1，单位vp。<br/>.value[3]?.f32：设置组件listItem的列间距，当列数大于1时生效，默认值为1，单位vp。 <br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：list组件行列数的设定值，如果设置了{minLength，maxLength}时返回值为1。<br/>.value[1].f32：组件listItem的minLength，单位vp。<br/>.value[2].f32：组件listItem的maxLength，单位vp。<br/>.value[3].f32：组件listItem的列间距，单位vp。<br/>**起始版本：** 15 |
| NODE_LIST_SCROLL_SNAP_ALIGN | 设置列表项滚动结束对齐效果。只支持ListItem等高情况下，设置列表项滚动结束对齐效果。触控板和鼠标滑动List结束后不支持对齐效果。对齐动画期间onWillScroll事件上报的滚动操作来源类型为ScrollSource.FLING。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置列表项滚动结束对齐效果。数据类型[ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign)，默认值ARKUI_SCROLL_SNAP_ALIGN_NONE。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置列表项滚动结束对齐效果。数据类型[ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign)。<br/>**起始版本：** 15 |
| NODE_LIST_MAINTAIN_VISIBLE_CONTENT_POSITION | 设置显示区域上方插入或删除数据时是否要保持可见内容位置不变。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置显示区域上方插入或删除数据时是否要保持可见内容位置不变。0表示显示区域上方插入或删除数据时可见内容位置会跟随变化，1表示显示区域上方插入或删除数据时可见内容位置不变。默认值为0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置显示区域上方插入或删除数据时是否要保持可见内容位置不变。0表示显示区域上方插入或删除数据时可见内容位置会跟随变化，1表示显示区域上方插入或删除数据时可见内容位置不变。<br/>**起始版本：** 15 |
| NODE_LIST_STACK_FROM_END | 设置List从末尾开始布局。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置List是否从末尾开始布局。0表示从顶部开始布局，1表示从末尾开始布局，默认值为0。<br/> 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置List是否从末尾开始布局。0表示从顶部开始布局，1表示从末尾开始布局。<br/>**起始版本：** 19|
| NODE_LIST_FOCUS_WRAP_MODE | List组件走焦换行模式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：List组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](#arkui_focuswrapmode)。<br/> 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: List组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](#arkui_focuswrapmode)。<br/>**起始版本：** 20|
| NODE_LIST_SYNC_LOAD | List组件是否同步加载子节点，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：List组件是否同步加载子节点。0：分帧加载，1：同步加载。<br/> 属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: List组件是否同步加载子节点。0：分帧加载，1：同步加载。<br/>**起始版本：** 20|
| NODE_SWIPER_LOOP  | Swiper是否开启循环，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制是否开启循环，0表示不循环，1表示循环，默认值为1。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制是否开启循环，0表示不循环，1表示循环，默认值为1。 |
| NODE_SWIPER_AUTO_PLAY  | Swiper子组件是否自动播放，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制子组件是否自动播放，0表示不自动播放，1表示自动播放，默认值为0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制子组件是否自动播放，0表示不自动播放，1表示自动播放，默认值为0。 |
| NODE_SWIPER_SHOW_INDICATOR  | Swiper是否显示导航点指示器，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否显示导航点指示器，0表示不显示导航点指示器，1表示显示导航点指示器，默认值为1。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否显示导航点指示器，0表示不显示导航点指示器，1表示显示导航点指示器，默认值为1。 |
| NODE_SWIPER_INTERVAL  | 设置Swiper自动播放时播放的时间间隔，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：使用自动播放时播放的时间间隔，单位为毫秒。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：使用自动播放时播放的时间间隔，单位为毫秒。 |
| NODE_SWIPER_VERTICAL  | 设置Swiper是否为纵向滑动，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否为纵向滑动，0表示横向滑动，1表示纵向滑动，默认值为0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否为纵向滑动，0表示横向滑动，1表示纵向滑动，默认值为0。 |
| NODE_SWIPER_DURATION  | 设置Swiper子组件切换的动画时长，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：子组件切换的动画时长，单位为毫秒, 默认值为400。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：子组件切换的动画时长，单位为毫秒, 默认值为400。 |
| NODE_SWIPER_CURVE  | 设置Swiper的动画曲线，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置动画曲线参数，参数类型[ArkUI_AnimationCurve](#arkui_animationcurve)，默认值为ARKUI_CURVE_LINEAR。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置动画曲线参数，参数类型[ArkUI_AnimationCurve](#arkui_animationcurve)，默认值为ARKUI_CURVE_LINEAR。 |
| NODE_SWIPER_ITEM_SPACE  | 设置Swiper子组件与子组件之间间隙，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：子组件与子组件之间间隙数值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：子组件与子组件之间间隙数值。 |
| NODE_SWIPER_INDEX  | 设置Swiper当前在容器中显示的子组件的索引值，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件的索引值。<br/>.value[1]?.i32：跳转动画模式，参数类型[ArkUI_SwiperAnimationMode](#arkui_swiperanimationmode)。仅当次调用有效。<br/>该参数自API 15开始支持。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件的索引值。 |
| NODE_SWIPER_DISPLAY_COUNT  | 设置Swiper一页内元素显示个数，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：视窗内显示的子元素个数。<br/>.value[1]?.i32：是否按组翻页，0：按子元素翻页，1：视窗内显示的子元素按组翻页，默认值：0。<br/>.string?：此参数只能设置为“auto”。当设置为“auto”时，value[] 参数将被忽略。<br/>该参数从API version 19开始支持。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：视窗内显示的子元素个数。<br/> .value[1].i32：是否按组翻页。<br/>该参数从API version 19开始支持。 |
| NODE_SWIPER_DISABLE_SWIPE  | 设置Swiper禁用组件滑动切换功能，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否禁用组件滑动切换功能，0表示不禁用滑动切换功能，1表示禁用滑动切换功能，默认值为0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否禁用组件滑动切换功能，0表示不禁用滑动切换功能，1表示禁用滑动切换功能，默认值为0。 |
| NODE_SWIPER_SHOW_DISPLAY_ARROW  | 设置Swiper是否显示导航点箭头，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置是否显示导航点箭头，参数类型[ArkUI_SwiperArrow](#arkui_swiperarrow)，<br/>默认值为ARKUI_SWIPER_ARROW_HIDE。<br/> .?object：显示导航箭头时设置箭头样式，参数类型[ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)。该参数从API version 19开始支持。 </br>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置是否显示导航点箭头，参数类型[ArkUI_SwiperArrow](#arkui_swiperarrow)，<br/>默认值为ARKUI_SWIPER_ARROW_HIDE。<br/> .object：箭头样式，参数类型[ArkUI_SwiperArrowStyle](#arkui_swiperarrowstyle)。该参数从API version 19开始支持。 |
| NODE_SWIPER_EDGE_EFFECT_MODE  | 设置Swiper的边缘滑动效果，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 边缘滑动效果，参数类型[ArkUI_EdgeEffect](#arkui_edgeeffect)，<br/>默认值为ARKUI_EDGE_EFFECT_SPRING。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: 边缘滑动效果，参数类型[ArkUI_EdgeEffect](#arkui_edgeeffect)， |
| NODE_SWIPER_NODE_ADAPTER  | swiper组件适配器，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用**ArkUI_NodeAdapter**对象作为适配器。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：返回值格式为**ArkUI_NodeAdapter**。 |
| NODE_SWIPER_CACHED_COUNT  | swiper组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：配合swiper组件Adapter使用，设置adapter中的缓存数量<br/>.value[1]?.i32：是否显示缓存节点，0：不显示，1：显示，默认值：0。该参数从API version 19开始支持。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：adapter中的缓存数量。<br/>.value[1].i32：是否显示缓存节点，0：不显示，1：显示。该参数从API version 19开始支持。 |
| NODE_SWIPER_PREV_MARGIN  | 设置 Swiper 组件的前边距，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：前边距数值，单位为vp，默认值为0。<br/>.value[1]?.i32：是否忽略空白，1表示忽略空白，0表示不忽略空白。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：前边距数值，单位为vp。 .value[1].i32：是否忽略空白，1表示忽略空白，0表示不忽略空白。 |
| NODE_SWIPER_NEXT_MARGIN  | 设置 Swiper 组件的后边距，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：后边距数值，单位为vp，默认值为0。<br/>.value[1]?.i32：是否忽略空白，1表示忽略空白，0表示不忽略空白。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：后边距数值，单位为vp。 .value[1].i32：是否忽略空白，1表示忽略空白，0表示不忽略空白。 |
| NODE_SWIPER_INDICATOR  | 设置 Swiper 组件的导航指示器类型，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置导航指示器的类型，参数类型[ArkUI_SwiperIndicatorType](#arkui_swiperindicatortype)。<br/>.object：导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DOT时参数类型[ArkUI_SwiperIndicator](#arkui_swiperindicator)。<br/> 导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DIGIT时参数类型[ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)。<br/> 类型[ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)从API version 19开始支持。 <br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：导航指示器的类型，参数类型[ArkUI_SwiperIndicatorType](#arkui_swiperindicatortype)。<br/>.object：导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DOT时参数类型[ArkUI_SwiperIndicator](#arkui_swiperindicator)。<br/> 导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DIGIT时参数类型[ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)。<br/> 类型[ArkUI_SwiperDigitIndicator](#arkui_swiperdigitindicator)从API version 19开始支持。 |
| NODE_SWIPER_NESTED_SCROLL  | 设置Swiper组件和父组件的嵌套滚动模式。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：Swiper组件和父组件的嵌套滚动模式，参数类型[ArkUI_SwiperNestedScrollMode](#arkui_swipernestedscrollmode)<br/>默认值为：ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：Swiper组件和父组件的嵌套滚动模式，参数类型[ArkUI_SwiperNestedScrollMode](#arkui_swipernestedscrollmode) |
| NODE_SWIPER_SWIPE_TO_INDEX  | 设置swiper组件翻至指定页面。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：指定页面在Swiper中的索引值。<br/>.value[1]?.i32：设置翻至指定页面时是否有动效。1表示有动效，0表示没有动效, 默认值：0。 |
| NODE_SWIPER_INDICATOR_INTERACTIVE  | 设置禁用组件导航点交互功能。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置禁用组件导航点交互功能，设置为true时表示导航点可交互，默认值true。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置禁用组件导航点交互功能。 |
| NODE_SWIPER_PAGE_FLIP_MODE  | 设置组件鼠标滚轮翻页模式。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置组件鼠标滚轮翻页模式，参数类型[ArkUI_PageFlipMode](#arkui_pageflipmode)。<br/>属性获取方法返回值[ArkUI_PageFlipMode](#arkui_pageflipmode)格式：<br/>.value[0].i32：鼠标滚轮翻页模式。<br/>起始版本：<br/>15 |
| NODE_SWIPER_AUTO_FILL  | 设置Swiper一页内元素显示个数根据元素最小宽度自适应，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：元素显示最小宽度，单位：vp。<br/> .value[1]?.i32：是否按组翻页，0：按子元素翻页，1：视窗内显示的子元素按组翻页，默认值：0。 <br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：元素显示最小宽度，单位：vp。<br/> .value[1].i32：是否按组翻页。<br/>**起始版本：** 19 |
| NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION  | 设置Swiper显示区域外插入或删除数据是否保持可见内容位置不变。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：Swiper显示区域外插入或删除数据是否保持可见内容位置不变。0表示不保持可见内容位置，1表示保持可见内容位置，默认值为0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：Swiper显示区域外插入或删除数据是否保持可见内容位置不变。0表示不保持可见内容位置，1表示保持可见内容位置，默认值为0。 <br/>**起始版本：** 20 |
| NODE_LIST_ITEM_SWIPE_ACTION  | 设置ListItem的划出组件，支持属性设置，属性重置，属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用[ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption)对象构造。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用[ArkUI_ListItemSwipeActionOption](#arkui_listitemswipeactionoption)对象构造。 |
| NODE_LIST_ITEM_GROUP_SET_HEADER  | 设置 ListItemGroup 头部组件，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用[ArkUI_NodeHandle](#arkui_nodehandle)对象作为ListItemGroup头部组件。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用[ArkUI_NodeHandle](#arkui_nodehandle)对象作为ListItemGroup头部组件。 |
| NODE_LIST_ITEM_GROUP_SET_FOOTER  | 设置 ListItemGroup 尾部组件，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用[ArkUI_NodeHandle](#arkui_nodehandle)对象作为ListItemGroup尾部组件。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用[ArkUI_NodeHandle](#arkui_nodehandle)对象作为ListItemGroup尾部组件。 |
| NODE_LIST_ITEM_GROUP_SET_DIVIDER  | 设置ListItem分割线样式，默认无分割线，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32： 颜色，0xargb类型；<br/>.value[1].f32： 分割线宽，单位vp；<br/>.value[2].f32： 分割线距离列表侧边起始端的距离，单位vp；<br/>.value[3].f32： 分割线距离列表侧边结束端的距离，单位vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].u32： 颜色，0xargb类型；<br/>.value[1].f32： 分割线宽，单位vp；<br/>.value[2].f32： 分割线距离列表侧边起始端的距离，单位vp；<br/>.value[3].f32： 分割线距离列表侧边结束端的距离，单位vp。 |
| NODE_LIST_ITEM_GROUP_CHILDREN_MAIN_SIZE  | 设置ListItemGroup子组件默认主轴尺寸。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>object: 参数格式为{\@ArkUI_ListChildrenMainSize}.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: 参数格式为{\@ArkUI_ListChildrenMainSize}. |
| NODE_LIST_ITEM_GROUP_NODE_ADAPTER | ListItemGroup组件适配器，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用**ArkUI_NodeAdapter**对象作为适配器。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：返回值格式为**ArkUI_NodeAdapter**。<br/>**起始版本：** 15  |
| NODE_COLUMN_ALIGN_ITEMS  | 设置Column子组件在水平方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_HorizontalAlignment](#arkui_horizontalalignment)，<br/>默认值ARKUI_HORIZONTAL_ALIGNMENT_CENTER。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_HorizontalAlignment](#arkui_horizontalalignment)。 |
| NODE_COLUMN_JUSTIFY_CONTENT  | 设置Column子组件在垂直方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_FlexAlignment](#arkui_flexalignment)，<br/>默认值ARKUI_FLEX_ALIGNMENT_START。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_FlexAlignment](#arkui_flexalignment)。 |
| NODE_ROW_ALIGN_ITEMS  | 设置Row子组件在垂直方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_VerticalAlignment](#arkui_verticalalignment)，<br/>默认值ARKUI_VERTICAL_ALIGNMENT_CENTER。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_VerticalAlignment](#arkui_verticalalignment)。 |
| NODE_ROW_JUSTIFY_CONTENT  | 设置Row子组件在水平方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_FlexAlignment](#arkui_flexalignment)，<br/>默认值ARKUI_FLEX_ALIGNMENT_START。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_FlexAlignment](#arkui_flexalignment)。 |
| NODE_FLEX_OPTION  | 设置Flex属性，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0]?.i32：子组件在Flex容器上排列的方向[ArkUI_FlexDirection](#arkui_flexdirection)，默认值为ARKUI_FLEX_DIRECTION_ROW；<br/>.value[1]?.i32：排列规则[ArkUI_FlexWrap](#arkui_flexwrap)，默认值为ARKUI_FLEX_WRAP_NO_WRAP；<br/>.value[2]?.i32：主轴上的对齐格式[ArkUI_FlexAlignment](#arkui_flexalignment)，默认值为ARKUI_FLEX_ALIGNMENT_START；<br/>.value[3]?.i32：交叉轴上的对齐格式[ArkUI_ItemAlignment](#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_START；<br/>.value[4]?.i32： 交叉轴中有额外的空间时，多行内容的对齐方式[ArkUI_FlexAlignment](#arkui_flexalignment)，默认值为ARKUI_FLEX_ALIGNMENT_START；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：子组件在Flex容器上排列的方向的枚举值；<br/>.value[1].i32：排列规则的枚举值；<br/>.value[2].i32：主轴上的对齐格式的枚举值；<br/>.value[3].i32：交叉轴上的对齐格式的枚举值；<br/>.value[4].i32：交叉轴中有额外的空间时，多行内容的对齐方式的枚举值； |
| NODE_REFRESH_REFRESHING  | 设置组件是否正在刷新，支持属性设置，属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：参数类型为1或者0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：参数类型为1或者0。 |
| NODE_REFRESH_CONTENT  | 设置下拉区域的自定义内容，支持属性设置和重置。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.object：参数类型{\@Link ArkUI_NodeHandle}。 |
| NODE_REFRESH_PULL_DOWN_RATIO  | 设置下拉跟手系数，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：下拉跟手系数,有效值为0-1之间的值。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：下拉跟手系数,有效值为0-1之间的值。 |
| NODE_REFRESH_OFFSET  | 设置触发刷新的下拉偏移量，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32：下拉偏移量，单位vp， 默认值：64vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：下拉偏移量，单位vp， 默认值：64vp。 |
| NODE_REFRESH_PULL_TO_REFRESH  | 设置当下拉距离超过refreshOffset时是否触发刷新，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32：是否触发刷新，true为触发刷新，false为不触发刷新。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：是否触发刷新，1为触发刷新，0为不触发刷新。 |
| NODE_REFRESH_MAX_PULL_DOWN_DISTANCE | 设置刷新的最大下拉距离，此属性可以根据需要通过api进行属性设置，属性重置和属性获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)的参数格式：<br/>.value[0].f32：最大下拉距离，单位：vp。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)的格式：<br/>.value[0].f32：最大下拉距离，单位：vp。 <br/>**起始版本：** 20 | 
| NODE_WATER_FLOW_LAYOUT_DIRECTION  | 定义瀑布流组件布局主轴方向，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32 主轴方向，参数类型{\@Link ArkUI_FlexDirection}。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 主轴方向，参数类型{\@Link ArkUI_FlexDirection}。 |
| NODE_WATER_FLOW_COLUMN_TEMPLATE  | 设置当前瀑布流组件布局列的数量，不设置时默认1列，支持属性设置、重置和获取。 例如，'1fr 1fr 2fr' 是将父组件分3列，将父组件允许的宽分为4等份，第1列占1份，第2列占1份，第3列占2份。 可使用columnsTemplate('repeat(auto-fill,track-size)')根据给定的列宽track-size自动计算列数， 其中repeat、auto-fill为关键字，track-size为可设置的宽度，支持的单位包括px、vp、或有效数字，默认单位为vp。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string: 布局列的数量.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: 布局列的数量. |
| NODE_WATER_FLOW_ROW_TEMPLATE  | 设置当前瀑布流组件布局行的数量，不设置时默认1行，支持属性设置、重置和获取。 例如，'1fr 1fr 2fr'是将父组件分3行，将父组件允许的高分为4等份，第1行占1份，第2行占1份，第3行占2份。 可使用rowsTemplate('repeat(auto-fill,track-size)')根据给定的行高track-size自动计算行数， 其中repeat、auto-fill为关键字，track-size为可设置的高度，支持的单位包括px、vp、或有效数字，默认单位为vp。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string: 布局行的数量.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: 布局行的数量. |
| NODE_WATER_FLOW_COLUMN_GAP  | 设置列与列的间距，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32: 列与列的间距, 单位vp.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 列与列的间距, 单位vp. |
| NODE_WATER_FLOW_ROW_GAP  | 设置行与行的间距，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32: 行与行的间距, 单位vp.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 行与行的间距, 单位vp. |
| NODE_WATER_FLOW_SECTION_OPTION  | 设置FlowItem分组配置信息，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].i32: 从0开始计算的索引，会转换为整数，表示要开始改变分组的位置.<br/>.object: 参数格式为{\@ArkUI_WaterFlowSectionOption}.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: 返回值格式为{\@ArkUI_WaterFlowSectionOption}. |
| NODE_WATER_FLOW_NODE_ADAPTER  | waterFlow组件适配器，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用**ArkUI_NodeAdapter**对象作为适配器。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: 返回值格式为**ArkUI_NodeAdapter**. |
| NODE_WATER_FLOW_CACHED_COUNT  | waterFlow组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：配合waterFlow组件Adapter使用，设置adapter中的缓存数量。<br/>.value[1].i32：是否显示缓存节点，0：不显示，1：显示，默认值：0。该参数从API version 16开始支持。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：adapter中的缓存数量。<br/>.value[1].f32：是否显示缓存节点，0：不显示，1：显示。该参数从API version 16开始支持。 |
| NODE_WATER_FLOW_FOOTER  | 设置瀑布流组件末尾的自定义显示组件。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.object：参数类型[ArkUI_NodeHandle](#arkui_nodehandle)。 |
| NODE_WATER_FLOW_SCROLL_TO_INDEX  | 滑动到指定index。<br/>开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：要滑动到的目标元素在当前容器中的索引值。<br/>.value[1]?.i32：设置滑动到列表项在列表中的索引值时是否有动效，1表示有动效，0表示没有动效。默认值：0。<br/>.value[2]?.i32：指定滑动到的元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](#arkui_scrollalignment)。默认值为：ARKUI_SCROLL_ALIGNMENT_START。 |
| NODE_WATER_FLOW_ITEM_CONSTRAINT_SIZE  | 设置当前瀑布流子组件的约束尺寸属性，组件布局时，进行尺寸范围限制，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：最小宽度，使用-1表示不设置；<br/>.value[1].f32：最大宽度，使用-1表示不设置；<br/>.value[2].f32：最小高度，使用-1表示不设置；<br/>.value[3].f32：最大高度，使用-1表示不设置；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：最小宽度，使用-1表示不设置；<br/>.value[1].f32：最大宽度，使用-1表示不设置；<br/>.value[2].f32：最小高度，使用-1表示不设置；<br/>.value[3].f32：最大高度，使用-1表示不设置； |
| NODE_WATER_FLOW_LAYOUT_MODE  | 定义瀑布流组件布局模式，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32: 布局模式，参数类型[ArkUI_WaterFlowLayoutMode](_ark_u_i___native_module.md#arkui_waterflowlayoutmode)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 布局模式，参数类型[ArkUI_WaterFlowLayoutMode](_ark_u_i___native_module.md#arkui_waterflowlayoutmode)。<br/>**起始版本：** 18 |
| NODE_WATER_FLOW_SYNC_LOAD  | WaterFlow组件是否同步加载子节点，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：WaterFlow组件是否同步加载子节点。0：分帧加载，1：同步加载。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32: WaterFlow组件是否同步加载子节点。0：分帧加载，1：同步加载。<br/>**起始版本：** 20 |
| NODE_RELATIVE_CONTAINER_GUIDE_LINE  | 设置RelativeContaine容器内的辅助线，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: RelativeContaine容器内的辅助线：<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: RelativeContaine容器内的辅助线： |
| NODE_RELATIVE_CONTAINER_BARRIER  | 设置RelativeContaine容器内的屏障，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: RelativeContaine容器内的辅助线：<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: RelativeContaine容器内的屏障： |
| NODE_GRID_COLUMN_TEMPLATE  | 设置当前Grid组件布局列的数量，不设置时默认1列，支持属性设置、重置和获取。 例如，'1fr 1fr 2fr' 是将父组件分3列，将父组件允许的宽分为4等份，第1列占1份，第2列占1份，第3列占2份。 可使用columnsTemplate('repeat(auto-fill,track-size)')根据给定的列宽track-size自动计算列数， 其中repeat、auto-fill为关键字，track-size为可设置的宽度，支持的单位包括px、vp、或有效数字，默认单位为vp。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string: 布局列的数量.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: 布局列的数量. |
| NODE_GRID_ROW_TEMPLATE  | 设置当前网格布局行的数量或最小行高值，不设置时默认1行，支持属性设置、重置和获取。 例如，'1fr 1fr 2fr'是将父组件分3行，将父组件允许的高分为4等份，第1行占1份，第2行占1份，第3行占2份。 可使用rowsTemplate('repeat(auto-fill,track-size)')根据给定的行高track-size自动计算行数， 其中repeat、auto-fill为关键字，track-size为可设置的高度，支持的单位包括px、vp、或有效数字，默认单位为vp。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.string: 布局行的数量.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.string: 布局行的数量. |
| NODE_GRID_COLUMN_GAP  | 设置列与列的间距，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32: 列与列的间距, 单位vp.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 列与列的间距, 单位vp. |
| NODE_GRID_ROW_GAP  | 设置行与行的间距，支持属性设置、重置和获取。<br/>属性设置方法[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)参数格式：<br/>.value[0].f32: 行与行的间距, 单位vp.<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32: 行与行的间距, 单位vp. |
| NODE_GRID_NODE_ADAPTER  | grid组件适配器，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：使用**ArkUI_NodeAdapter**对象作为适配器。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: 返回值格式为**ArkUI_NodeAdapter**. |
| NODE_GRID_CACHED_COUNT  | grid组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：配合Grid组件Adapter使用，设置adapter中的缓存数量。 |
| NODE_GRID_FOCUS_WRAP_MODE  | Grid组件走焦换行模式，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：Grid组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](#arkui_focuswrapmode)。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/> .value[0].i32: Grid组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](#arkui_focuswrapmode)。<br/>**起始版本：** 20 |
| NODE_GRID_SYNC_LOAD  | Grid组件是否同步加载子节点，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：Grid组件是否同步加载子节点。0：分帧加载，1：同步加载。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/> .value[0].i32: Grid组件是否同步加载子节点。0：分帧加载，1：同步加载。<br/>**起始版本：** 20 |
| NODE_TEXT_PICKER_COLUMN_WIDTHS<sup>18+</sup>  | 设置每一个选择项列宽。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：设置的第1个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等；<br/>.value[1].f32：设置的第2个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等；<br/>.value[2].f32：设置的第3个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等；<br/>...<br/>.value[n].f32：设置的第n+1个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：第1列宽度，总宽度的百分；<br/>.value[1].f32：第2列宽度，总宽度的百分；<br/>.value[2].f32：第3列宽度，总宽度的百分；<br/>...<br/>.value[n].f32：第n+1列宽度，总宽度的百分； |
| NODE_IMAGE_ANIMATOR_IMAGES  | 设置帧动画组件的图片帧信息集合。不支持动态更新。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.size：图片帧的数量；<br/>.object：图片帧数组，参数类型为{\@ArkUI_ImageAnimatorFrameInfo}数组；<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.size：图片帧的数量；<br/>.object：图片帧数组，参数类型为{\@ArkUI_ImageAnimatorFrameInfo}数组； |
| NODE_IMAGE_ANIMATOR_STATE  | 控制帧动画组件的播放状态。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制动画的播放状态，参数类型为[ArkUI_AnimationStatus](#arkui_animationstatus)，默认值为初始状态。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：控制动画的播放状态，参数类型为[ArkUI_AnimationStatus](#arkui_animationstatus)。 |
| NODE_IMAGE_ANIMATOR_DURATION  | 设置帧动画的播放时长，当数组中任意一帧图片单独设置了duration属性后，该属性设置无效。 支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：播放时长，单位为毫秒，默认值1000。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：播放时长，单位为毫秒，默认值1000。 |
| NODE_IMAGE_ANIMATOR_REVERSE  | 设置帧动画的播放方向。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：播放方向，0表示从第一张图片播放到最后一张，1表示从最后一张图片播放到第一张，默认值为0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：播放方向，0表示从第一张图片播放到最后一张，1表示从最后一张图片播放到第一张。 |
| NODE_IMAGE_ANIMATOR_FIXED_SIZE  | 设置图片大小是否固定为组件大小。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置图片大小是否固定为组件大小，1表示图片大小与组件大小一致。0表示每一张图片的width、height、top和left都要单独设置，默认值为1。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：设置图片大小是否固定为组件大小，1表示图片大小与组件大小一致。0表示每一张图片的width、height、top和left都要单独设置。 |
| NODE_IMAGE_ANIMATOR_FILL_MODE  | 设置帧动画在当前播放方向下，动画开始前和结束后的状态。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：当前播放方向下，动画开始前和结束后的状态，参数类型为{ArkUI_AnimationFillMode}，默认值为FORWARDS。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：当前播放方向下，动画开始前和结束后的状态，参数类型为{ArkUI_AnimationFillMode}。 |
| NODE_IMAGE_ANIMATOR_ITERATION  | 设置帧动画的播放次数。支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：播放次数。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32：播放次数。 |
| NODE_BACKDROP_BLUR  | 设置背景模糊效果，支持属性设置，属性重置和属性获取。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：表示背景模糊半径，取值范围[0,+∞)。单位px，默认值0.0。<br/>.value[1]?.f32：表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。<br/>.value[2]?.f32：表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：表示背景模糊半径，取值范围[0,+∞)。单位px。<br/>.value[1].f32：表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。<br/>.value[2].f32：表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。<br/>起始版本：15。 |
| NODE_TRANSLATE_WITH_PERCENT  | 通过百分比或具体数值形式设置组件平移，支持属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： x轴移动距离，单位取决于value[3]，默认单位为百分比；<br/>.value[1].f32： y轴移动距离，单位取决于value[4]，默认单位为百分比；<br/>.value[2].f32： z轴移动距离，单位vp，默认值0。<br/>.value[3]?.i32： x轴的参数单位，默认值1，取值范围0或1。<br/>.value[4]?.i32： y轴的参数单位，默认值1，取值范围0或1。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32： x轴移动距离，单位取决于value[3]；<br/>.value[1].f32： y轴移动距离，单位取决于value[4]；<br/>.value[2].f32： z轴移动距离，单位vp。<br/>.value[3].i32： x轴的参数单位。<br/>.value[4].i32： y轴的参数单位。<br/>**说明：**<br/>设置的参数个数超过5个或少于3个时返回错误码。<br/>参数单位1表示百分比单位，0表示不使用百分比单位，默认vp。<br/>**起始版本：** 20 | 
| NODE_EMBEDDED_COMPONENT_WANT  | 定义用于启动EmbeddedAbility的want。支持参数属性设置。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object: EmbeddedCompont的want参数。参数类型为[AbilityBase_Want](#abilitybase_want)。默认值为nullptr。<br/>**起始版本：** 20  | 
| NODE_EMBEDDED_COMPONENT_OPTION  | EmbeddedCompont的选项。支持参数属性设置。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.object：EmbeddedCompont的选项列表，参数类型为[ArkUI_EmbeddedComponentOption](#arkui_embeddedcomponentoption)。<br/>**起始版本：** 20  | 
| NODE_ROTATE_ANGLE | 设置组件旋转，支持各轴旋转角属性设置，属性重置和属性获取接口。<br/>属性设置方法参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：x轴方向旋转角度，默认值0；<br/>.value[1].f32：y轴方向旋转角度，默认值0；<br/>.value[2].f32：z轴方向旋转角度，默认值0；<br/>.value[3].f32：视距，即视点到z=0平面的距离，单位px，默认值0。<br/>属性获取方法返回值[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32：x轴方向旋转角度，默认值0；<br/>.value[1].f32：y轴方向旋转角度，默认值0；<br/>.value[2].f32：z轴方向旋转角度，默认值0；<br/>.value[3].f32：视距，即视点到z=0平面的距离，单位px，默认值0。 <br/>**起始版本：** 20 |

### ArkUI_DatePickerMode

```
enum ArkUI_DatePickerMode
```
**描述：**

定义要显示的日期选项列类型。

**起始版本：** 18

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_DATEPICKER_MODE_DATE  | 默认值。日期列显示年、月、日三列。 |
| ARKUI_DATEPICKER_YEAR_AND_MONTH  | 日期列显示年、月二列。 |
| ARKUI_DATEPICKER_MONTH_AND_DAY  | 日期列显示月、日二列。<br/>此模式下，如果月份从12月变化到1月，年份不增加1年；如果月份从1月变化到12月，年份不减少1年；年份始终在当前设置的年份。 |

### ArkUI_NodeContentEventType

```
enum ArkUI_NodeContentEventType
```
**描述：**

定义NodeContent事件类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| NODE_CONTENT_EVENT_ON_ATTACH_TO_WINDOW  | 上树事件。  |
| NODE_CONTENT_EVENT_ON_DETACH_FROM_WINDOW  | 下树事件。  |

### ArkUI_InspectorErrorCode

```
enum ArkUI_InspectorErrorCode
```
**描述：**

定义Inspector错误码。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL  | 成功。  |
| ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER  | 参数错误。  |

### ArkUI_NodeCustomEventType

```
enum ArkUI_NodeCustomEventType
```
**描述：**

定义自定义组件事件类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE  | measure 类型。  |
| ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT  | layout 类型。  |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW  | draw 类型。  |
| ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW  | foreground 类型。  |
| ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW  | overlay 类型。  |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT  | front 类型。  <br>起始版本：20|
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND  | behind 类型。  <br>起始版本：20|

### ArkUI_NodeDirtyFlag

```
enum ArkUI_NodeDirtyFlag
```
**描述：**

自定义组件调用&lt;b&gt;::markDirty是传递的脏区标识类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| NODE_NEED_MEASURE  | 重新测算大小。<br/>该flag类型触发时，同时也默认会触发重新布局。 |
| NODE_NEED_LAYOUT  | 重新布局位置。  |
| NODE_NEED_RENDER  | 重新进行绘制。  |


### ArkUI_NodeEventType

```
enum ArkUI_NodeEventType
```
**描述：**

提供NativeNode组件支持的事件类型定义。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| NODE_TOUCH_EVENT  | 手势事件类型。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent)。 |
| NODE_EVENT_ON_APPEAR  | 挂载事件。<br/>触发该事件的条件 ：组件挂载显示时触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_EVENT_ON_DISAPPEAR  | 卸载事件。<br/>触发该事件的条件 ：组件卸载时触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_EVENT_ON_AREA_CHANGE  | 组件区域变化事件<br/>触发该事件的条件：组件区域变化时触发该回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含12个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**：表示过去目标元素的宽度，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：表示过去目标元素的高度，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].f32**：表示过去目标元素左上角相对父元素左上角的位置的x轴坐标，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[3].f32**：表示过去目标元素左上角相对父元素左上角的位置的y轴坐标，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[4].f32**：表示过去目标元素目标元素左上角相对页面左上角的位置的x轴坐标，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[5].f32**：表示过去目标元素目标元素左上角相对页面左上角的位置的y轴坐标，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[6].f32**：表示最新目标元素的宽度，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[7].f32**：表示最新目标元素的高度，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[8].f32**：表示最新目标元素左上角相对父元素左上角的位置的x轴坐标，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[9].f32**：表示最新目标元素左上角相对父元素左上角的位置的y轴坐标，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[10].f32**：表示最新目标元素目标元素左上角相对页面左上角的位置的x轴坐标，类型为number，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[11].f32**：表示最新目标元素目标元素左上角相对页面左上角的位置的y轴坐标，类型为number，单位vp。 |
| NODE_ON_FOCUS  | 获焦事件。<br/>触发该事件的条件：组件获焦时触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_ON_BLUR  | 失去焦点事件。<br/>触发该事件的条件：组件失去焦点时触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_ON_CLICK  | 组件点击事件。<br/>触发该事件的条件：组件被点击时触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含8个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**：点击位置相对于被点击元素原始区域左上角的X坐标，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：点击位置相对于被点击元素原始区域左上角的Y坐标，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].f32**：事件时间戳。触发事件时距离系统启动的时间间隔，单位微秒。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[3].i32**：事件输入设备，1表示鼠标，2表示触屏，4表示按键。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[4].f32**：点击位置相对于应用窗口左上角的X坐标，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[5].f32**：点击位置相对于应用窗口左上角的Y坐标，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[6].f32**：点击位置相对于应用屏幕左上角的X坐标，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[7].f32**：点击位置相对于应用屏幕左上角的Y坐标，单位px。 |
| NODE_ON_CLICK_EVENT | 组件点击事件。<br/>触发该事件的条件：组件被点击时触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent)。 <br/>起始版本：18。|
| NODE_ON_TOUCH_INTERCEPT  | 组件自定义事件拦截。<br/>触发该事件的条件：组件被触摸时触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent)。 |
| NODE_EVENT_ON_VISIBLE_AREA_CHANGE  | 组件可见区域变化事件。<br/>触发该事件的条件：组件可见面积与自身面积的比值接近设置的阈值时触发回调，注册事件前需先使用 NODE_VISIBLE_AREA_CHANGE_RATIO 配置阈值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：组件可见面积与自身面积的比值与上次变化相比的情况，变大为1，变小为0。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：触发回调时组件可见面积与自身面积的比值。 |
| NODE_ON_HOVER  | 鼠标进入或退出组件事件。<br/>触发该事件的条件：鼠标进入或退出组件时触发回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：鼠标是否悬浮在组件上，鼠标进入时为1，退出时为0。 |
| NODE_ON_HOVER_EVENT  | 鼠标进入或退出组件事件。<br/>触发该事件的条件：鼠标进入或退出组件时触发回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent)。 <br />**起始版本：** 17|
| NODE_ON_MOUSE  | 组件点击事件。<br/>触发该事件的条件：组件被鼠标按键点击或者鼠标在组件上悬浮移动时触发该回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent)。 |
| NODE_EVENT_ON_ATTACH  | 上树事件。<br/>触发该事件的条件 ：组件上树时触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_EVENT_ON_DETACH  | 下树事件。<br/>触发该事件的条件 ：组件下树时触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_ON_ACCESSIBILITY_ACTIONS  | 无障碍支持操作事件触发。<br/>触发该事件的条件：已设置无障碍操作类型，并进行相应操作。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].u32**: 触发回调的操作类型，参数类型[ArkUI_AccessibilityActionType](#arkui_accessibilityactiontype) |
| NODE_ON_PRE_DRAG  | 在拖拽行为开始之前告诉侦听器详细的交互状态。<br/>触发该事件的条件：组件可拖拽，当长按浮起/松手/发起拖拽时，回调触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：对应[ArkUI_PreDragStatus](#arkui_predragstatus)。 |
| NODE_ON_DRAG_START  | 用户已移动足够距离，即将发起拖拽。<br/>触发该事件的条件：长按拖动产生足够位移距离时触发。<br/>事件回调发生时，可从事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中获取[ArkUI_DragEvent](#arkui_dragevent)。 |
| NODE_ON_DRAG_ENTER  | 用户拖拽进入当前组件范围。<br/>触发该事件的条件: 拖拽对象进入监听了该事件的组件边界时触发。<br/>事件回调发生时，可从事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中获取[ArkUI_DragEvent](#arkui_dragevent)。 |
| NODE_ON_DRAG_MOVE  | 用户拖拽在当前组件范围内移动。<br/>触发该事件的条件: 拖拽对象在监听了该事件的组件范围内移动时触发。<br/>事件回调发生时，可从事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中获取[ArkUI_DragEvent](#arkui_dragevent)。 |
| NODE_ON_DRAG_LEAVE  | 用户拖拽从当前组件范围离开。<br/>触发该事件的条件: 拖拽对象离开监听了该事件的组件边界时触发。<br/>事件回调发生时，可从事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中获取[ArkUI_DragEvent](#arkui_dragevent)。 |
| NODE_ON_DROP  | 当用户在组件上方松手时，该组件上可通过该回调拿到拖拽数据进行处理。<br/>触发该事件的条件: 拖拽对象并在组件上方松手时触发。<br/>事件回调发生时，可从事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中获取[ArkUI_DragEvent](#arkui_dragevent)。 |
| NODE_ON_DRAG_END  | 拖拽发起方可通过注册该回调感知拖拽结束后的结果。<br/>触发该事件的条件：用户松手，拖拽行为结束时触发。 事件回调发生时，可从事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中获取[ArkUI_DragEvent](#arkui_dragevent)。 |
| NODE_ON_KEY_EVENT  | 绑定该方法的组件获焦后，按键动作触发该回调。<br/>触发该事件的条件 ：由外设键盘等设备与获焦窗口交互触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>起始版本：<br/>14 |
| NODE_ON_KEY_PRE_IME  | 绑定该方法的组件获焦后，按键动作在响应输入法前优先触发该回调。<br/>该回调的返回值为true时，视作该按键事件已被消费，后续的事件回调（keyboardShortcut、输入法事件、onKeyEvent）会被拦截，不再触发。 触发该事件的条件 ：由外设键盘等设备与获焦窗口交互触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>起始版本：<br/>14 |
| NODE_ON_FOCUS_AXIS  | 绑定该方法的组件获焦后，收到焦点轴事件时触发该回调。<br/>触发该事件的条件 ：由游戏手柄与获焦组件交互触发此回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent)。<br />**起始版本：** 15 |
| NODE_ON_AXIS | 绑定该方法的组件收到轴事件时触发该回调。<br/>当绑定组件接收到轴事件时，会触发该事件回调。<br/>事件发生时， [ArkUI_NodeEvent](#arkui_nodeevent-12) 对象中的联合类型为 [ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent)。<br />**起始版本：** 17|
| NODE_DISPATCH_KEY_EVENT  | 组件按键事件重新派发事件。当组件节点接收到按键事件时，将触发此回调函数，而非将事件分发给其子节点。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>起始版本：<br/>15 |
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT  | 组件可见区域变化事件。<br/>触发该事件的条件：组件可见面积与自身面积的比值接近设置的阈值时触发回调，注册事件前需先使用 NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO 配置阈值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：组件可见面积与自身面积的比值与上次变化相比的情况，变大为1，变小为0。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：触发回调时组件可见面积与自身面积的比值。 <br/>起始版本：<br/>17 |
| NODE_ON_HOVER_MOVE  | 当手写笔设备指针悬停在组件内时会触发该事件。<br/>事件回调发生时, 事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象可以从[ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent)对象中获取。<br/>起始版本：<br/>15 |
| NODE_TEXT_ON_DETECT_RESULT_UPDATE  | 文本设置TextDataDetectorConfig且识别成功时，触发onDetectResultUpdate回调。<br/>触发该事件的条件：文本设置TextDataDetectorConfig且识别成功后。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)。<br/>[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)中包含1个参数：<br/>**[ArkUI_StringAsyncEvent.pStr](_ark_u_i___string_async_event.md#pstr)**：表示文本识别的结果，Json格式。 |
| NODE_TEXT_SPAN_ON_LONG_PRESS  | Span组件长按事件。<br/>组件被长按时触发此回调。<br/>事件回调发生时，可从事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中获取[ArkUI_UIInputEvent](_ark_u_i___event_module.md#arkui_uiinputevent)。<br/>**起始版本：** 20 |
| NODE_IMAGE_ON_COMPLETE  | 图片加载成功事件。<br/>触发该事件的条件 ：图片数据加载成功和解码成功均触发该回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含9个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示加载状态，0表示数据加载成功，1表示解码成功。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：表示图片的宽度，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].f32**：表示图片的高度，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[3].f32**：表示当前组件的宽度，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[4].f32**：表示当前组件的高度，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[5].f32**：图片绘制区域相对组件X轴位置，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[6].f32**：图片绘制区域相对组件Y轴位置，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[7].f32**：图片绘制区域宽度，单位px。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[8].f32**：图片绘制区域高度，单位px。 |
| NODE_IMAGE_ON_ERROR  | 图片加载失败事件。<br/>触发该事件的条件：图片加载异常时触发该回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**错误码信息：<br/>401: 图片路径参数异常，无法获取到图片数据。<br/>103101: 图片格式不支持。 |
| NODE_IMAGE_ON_SVG_PLAY_FINISH  | SVG图片动效播放完成事件。<br/>触发该事件的条件：带动效的SVG图片动画结束时触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_IMAGE_ON_DOWNLOAD_PROGRESS  | 定义图片下载过程中触发事件。<br/>触发该事件的条件 ：页面组件下载网页图片时触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].u32**: 到目前为止已下载的字节数。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].u32**: 要下载图片的总字节数。 |
| NODE_TOGGLE_ON_CHANGE  | 开关状态发生变化时触发给事件。<br/>触发该事件的条件：开关状态发生变化。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：当前开关状态，1表示开，0表示关。 |
| NODE_TEXT_INPUT_ON_CHANGE  | textInput输入内容发生变化时触发该事件。<br/>触发该事件的条件：输入内容发生变化时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)。<br/>[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)中包含1个参数：<br/>**[ArkUI_StringAsyncEvent.pStr](_ark_u_i___string_async_event.md#pstr)**：输入的文本内容。 |
| NODE_TEXT_INPUT_ON_SUBMIT  | textInput按下输入法回车键触发该事件。<br/>触发该事件的条件：按下输入法回车键。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：输入法回车键类型。 |
| NODE_TEXT_INPUT_ON_CUT  | 长按输入框内部区域弹出剪贴板后，点击剪切板剪切按钮，触发该回调。<br/>触发该事件的条件：长按输入框内部区域弹出剪贴板后，点击剪切板剪切按钮。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)。<br/>[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)中包含1个参数：<br/>**[ArkUI_StringAsyncEvent.pStr](_ark_u_i___string_async_event.md#pstr)**：剪切的文本内容。 |
| NODE_TEXT_INPUT_ON_PASTE  | 长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮，触发该回调。<br/>触发该事件的条件：长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)。<br/>[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)中包含1个参数：<br/>**[ArkUI_StringAsyncEvent.pStr](_ark_u_i___string_async_event.md#pstr)**：粘贴的文本内容。 |
| NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE  | 文本选择的位置发生变化时，触发该回调。<br/>触发该事件的条件：文本选择的位置发生变化时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示所选文本的起始位置。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：表示所选文本的结束位置。 |
| NODE_TEXT_INPUT_ON_EDIT_CHANGE  | 输入状态变化时，触发该回调。<br/>触发该事件的条件：输入状态变化时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示true表示正在输入。 |
| NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR  | 设置NODE_TEXT_INPUT_INPUT_FILTER，正则匹配失败时触发。<br/>触发该事件的条件：正则匹配失败时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)。<br/>[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)中包含1个参数：<br/>**[ArkUI_StringAsyncEvent.pStr](_ark_u_i___string_async_event.md#pstr)**：表示正则匹配失败时，被过滤的内容。 |
| NODE_TEXT_INPUT_ON_CONTENT_SCROLL  | 文本内容滚动时，触发该回调。<br/>触发该事件的条件：文本内容滚动时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示文本在内容区的横坐标偏移。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：表示文本在内容区的纵坐标偏移。 |
| NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE  | textInput输入内容发生变化时触发该事件。<br/>触发该事件的条件：输入内容发生变化时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**：表示文本的宽度。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：表示文本的高度。 |
| NODE_TEXT_INPUT_ON_WILL_INSERT  | 定义在将要输入时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：插入的值的位置信息。<br/>通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：插入的值。<br/>返回<br/>在返回true时，表示正常插入，返回false时，表示不插入。 可通过OH_ArkUI_NodeEvent_SetReturnNumberValue设置返回值。 |
| NODE_TEXT_INPUT_ON_DID_INSERT  | 定义在输入完成时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：插入的值的位置信息。<br/>通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：插入的值。 |
| NODE_TEXT_INPUT_ON_WILL_DELETE  | 定义在将要删除时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：删除的值的位置信息。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br/>通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：删除的值。<br/>返回<br/>在返回true时，表示正常插入，返回false时，表示不插入。<br/>可通过OH_ArkUI_NodeEvent_SetReturnNumberValue设置返回值。 |
| NODE_TEXT_INPUT_ON_DID_DELETE  | 定义在删除完成时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：删除的值的位置信息。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br/>通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：删除的值。 |
| NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT  | 定义在文本内容（包含预上屏内容）改变时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md)。<br/>[ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md)中包含3个参数：<br/>**[ArkUI_TextChangeEvent.pStr](_ark_u_i___text_change_event.md#pstr)**：输入的文本内容。<br/>**[ArkUI_TextChangeEvent.pExtendStr](_ark_u_i___text_change_event.md#pextendstr)**：预上屏输入的文本内容。<br/>**[ArkUI_TextChangeEvent.number](_ark_u_i___text_change_event.md#number)**：预上屏文本插入的位置。<br/>**起始版本：** 15 |
| NODE_TEXT_INPUT_ON_WILL_CHANGE  | 定义TextInput组件在内容将要改变时（包含预上屏内容），触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md)。<br/>[ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md)中包含3个参数：<br/>**[ArkUI_TextChangeEvent.pStr](_ark_u_i___text_change_event.md#pstr)**：输入的文本内容。<br/>**[ArkUI_TextChangeEvent.pExtendStr](_ark_u_i___text_change_event.md#pextendstr)**：预上屏输入的文本内容。<br/>**[ArkUI_TextChangeEvent.number](_ark_u_i___text_change_event.md#number)**：预上屏文本插入的位置。<br/>**起始版本：** 20 | 
| NODE_TEXT_AREA_ON_CHANGE  | 输入内容发生变化时，触发该回调。<br/>触发该事件的条件：输入内容发生变化时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)。<br/>[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)中包含1个参数：<br/>**[ArkUI_StringAsyncEvent.pStr](_ark_u_i___string_async_event.md#pstr)**：当前输入的文本内容。 |
| NODE_TEXT_AREA_ON_PASTE  | 长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮，触发该回调。<br/>触发该事件的条件：长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)。<br/>[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)中包含1个参数：<br/>**[ArkUI_StringAsyncEvent.pStr](_ark_u_i___string_async_event.md#pstr)**：粘贴的文本内容。 |
| NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE  | 文本选择的位置发生变化时，触发该回调。<br/>触发该事件的条件：文本选择的位置发生变化时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示所选文本的起始位置。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：表示所选文本的结束位置。 |
| NODE_TEXT_AREA_ON_EDIT_CHANGE  | 输入状态变化时，触发该回调。<br/>触发该事件的条件：输入状态变化时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示true表示正在输入。 |
| NODE_TEXT_AREA_ON_SUBMIT  | textArea按下输入法回车键触发该事件。<br/>触发该事件的条件：按下输入法回车键。keyType为ARKUI_ENTER_KEY_TYPE_NEW_LINE时不触发<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：输入法回车键类型。 |
| NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR  | 设置NODE_TEXT_AREA_INPUT_FILTER，正则匹配失败时触发。<br/>触发该事件的条件：正则匹配失败时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)。<br/>[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)中包含1个参数：<br/>**[ArkUI_StringAsyncEvent.pStr](_ark_u_i___string_async_event.md#pstr)**：表示正则匹配失败时，被过滤的内容。 |
| NODE_TEXT_AREA_ON_CONTENT_SCROLL  | 文本内容滚动时，触发该回调。<br/>触发该事件的条件：文本内容滚动时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示文本在内容区的横坐标偏移。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：表示文本在内容区的纵坐标偏移。 |
| NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE  | textArea输入内容发生变化时触发该事件。<br/>触发该事件的条件：输入内容发生变化时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**：表示文本的宽度。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：表示文本的高度。 |
| NODE_TEXT_AREA_ON_WILL_INSERT  | 定义在将要输入时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：插入的值的位置信息。<br/>通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：插入的值。<br/>返回<br/>在返回true时，表示正常插入，返回false时，表示不插入。 可通过OH_ArkUI_NodeEvent_SetReturnNumberValue设置返回值。 |
| NODE_TEXT_AREA_ON_DID_INSERT  | 定义在输入完成时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：插入的值的位置信息。<br/>通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：插入的值。 |
| NODE_TEXT_AREA_ON_WILL_DELETE  | 定义在将要删除时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：删除的值的位置信息。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br/>通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：删除的值。<br/>返回<br/>在返回true时，表示正常插入，返回false时，表示不插入。<br/>可通过OH_ArkUI_NodeEvent_SetReturnNumberValue设置返回值。 |
| NODE_TEXT_AREA_ON_DID_DELETE  | 定义在删除完成时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：删除的值的位置信息。<br/>通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br/>通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：删除的值。 |
| NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT  | 定义在文本内容（包含预上屏内容）改变时，触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md)。<br/>[ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md)中包含3个参数：<br/>**[ArkUI_TextChangeEvent.pStr](_ark_u_i___text_change_event.md#pstr)**：输入的文本内容。<br/>**[ArkUI_TextChangeEvent.pExtendStr](_ark_u_i___text_change_event.md#pextendstr)**：预上屏输入的文本内容。<br/>**[ArkUI_TextChangeEvent.number](_ark_u_i___text_change_event.md#number)**：预上屏文本插入的位置。<br/>**起始版本：** 15 |
| NODE_CHECKBOX_EVENT_ON_CHANGE  | 定义ARKUI_NODE_CHECKBOX当选中状态发生变化时，触发该回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32：** 1表示已选中, 0表示未选中 |
| NODE_TEXT_AREA_ON_WILL_CHANGE  | 定义TextArea组件在内容将要改变时（包含预上屏内容），触发回调的枚举值。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md)。<br/>[ArkUI_TextChangeEvent](_ark_u_i___text_change_event.md)中包含3个参数：<br/>**[ArkUI_TextChangeEvent.pStr](_ark_u_i___text_change_event.md#pstr)**：输入的文本内容。<br/>**[ArkUI_TextChangeEvent.pExtendStr](_ark_u_i___text_change_event.md#pextendstr)**：预上屏输入的文本内容。<br/>**[ArkUI_TextChangeEvent.number](_ark_u_i___text_change_event.md#number)**：预上屏文本插入的位置。<br/>**起始版本：** 20 | 
| NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE  | 定义ARKUI_NODE_DATE_PICKER列表组件的滚动触摸事件枚举值。<br/>触发该事件的条件：选择日期时触发该事件。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含3个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示选中时间的年。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：表示选中时间的月，取值范围：[0-11]。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].i32**：表示选中时间的天。 |
| NODE_TIME_PICKER_EVENT_ON_CHANGE  | 定义ARKUI_NODE_TIME_PICKER列表组件的滚动触摸事件枚举值。<br/>触发该事件的条件：选择时间时触发该事件。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示选中时间的时，取值范围：[0-23]。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：表示选中时间的分，取值范围：[0-59]。 |
| NODE_TEXT_PICKER_EVENT_ON_CHANGE  | 定义ARKUI_NODE_TEXT_PICKER列表组件的滚动触摸事件枚举值。<br/>触发该事件的条件 ：选择文本时触发该事件。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0...11].i32**表示选中数据的维度。 |
| NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP  | 定义ARKUI_NODE_TEXT_PICKER列表组件的滚动触摸事件枚举值。<br/>触发该事件的条件 ：滑动选择文本项停止时触发该事件。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0...11].i32**表示选中数据的维度。 |
| NODE_CALENDAR_PICKER_EVENT_ON_CHANGE  | 定义NODE_CALENDAR_PICKER选中日期时触发的事件。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>**ArkUI_NodeComponent.data[0].u32**选中的年。<br/>**ArkUI_NodeComponent.data[1].u32**选中的月。<br/>**ArkUI_NodeComponent.data[2].u32**选中的日。 |
| NODE_SLIDER_EVENT_ON_CHANGE  | 定义ARKUI_NODE_SLIDER拖动或点击时触发事件回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**：当前滑动进度值。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：事件触发的相关状态值 |
| NODE_RADIO_EVENT_ON_CHANGE  | 定义ARKUI_NODE_RADIO拖动或点击时触发事件回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：单选框的状态。 |
| NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE  | 定义ARKUI_NODE_CHECKBOX_GROUP的选中状态或群组内的Checkbox的选中状态发生变化时，触发回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)。<br/>[ArkUI_StringAsyncEvent](_ark_u_i___string_async_event.md)中包含一个参数：<br/>**[ArkUI_StringAsyncEvent.pStr](_ark_u_i___string_async_event.md#pstr)**：<br/>Name：被选中的checkbox的名字。<br/>Status：<b>0</b>表示群组多选择框全部选择; <b>1</b>群组多选择框部分选择; <b>2</b>群组多选择框全部没有选择。<br/>**起始版本：** 15 |
| NODE_IMAGE_ANIMATOR_EVENT_ON_START  | 定义帧动画开始的状态回调。<br/>触发该事件的条件：<br/>1、帧动画开始播放时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_IMAGE_ANIMATOR_EVENT_ON_PAUSE  | 定义帧动画播放暂停时的状态回调。<br/>触发该事件的条件：<br/>1、帧动画暂停播放时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_IMAGE_ANIMATOR_EVENT_ON_REPEAT  | 定义帧动画c重复播放时的状态回调。<br/>触发该事件的条件：<br/>1、帧动画重复播放时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_IMAGE_ANIMATOR_EVENT_ON_CANCEL  | 定义帧动画返回最初状态时的状态回调。<br/>触发该事件的条件：<br/>1、帧动画返回最初状态时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_IMAGE_ANIMATOR_EVENT_ON_FINISH  | 定义帧动画播放完成时或者停止播放时的状态回调。<br/>触发该事件的条件：<br/>1、帧动画播放完成时或停止播放时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_SWIPER_EVENT_ON_CHANGE  | 定义ARKUI_NODE_SWIPER当前元素索引变化时触发事件回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示当前显示元素的索引。 |
| NODE_SWIPER_EVENT_ON_ANIMATION_START  | 定义ARKUI_NODE_SWIPER切换动画开始时触发回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含5个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示当前显示元素的索引。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：表示切换动画目标元素的索引。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].f32**：表示主轴方向上当前显示元素相对Swiper起始位置的位移。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[3].f32**：表示主轴方向上目标元素相对Swiper起始位置的位移。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[4].f32**：表示离手速度。 |
| NODE_SWIPER_EVENT_ON_ANIMATION_END  | 定义ARKUI_NODE_SWIPER切换动画结束是触发回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示当前显示元素的索引。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：表示主轴方向上当前显示元素相对Swiper起始位置的位移。 |
| NODE_SWIPER_EVENT_ON_GESTURE_SWIPE  | 定义ARKUI_NODE_SWIPER在页面跟手滑动过程中，逐帧触发该回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示当前显示元素的索引。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：表示主轴方向上当前显示元素相对Swiper起始位置的位移。 |
| NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL  | 定义ARKUI_NODE_SWIPER监听Swiper页面滑动事件。 使用说明 ：<br/>1、设置[ArkUI_SwiperDisplayModeType](#arkui_swiperdisplaymodetype)属性为ARKUI_SWIPER_DISPLAY_MODE_AUTO_LINEAR时，该接口不生效。<br/>2、循环场景下，设置prevMargin和nextMargin属性，使得Swiper前后端显示同一页面时，该接口不生效。<br/>3、在页面滑动过程中，会对视窗内所有页面逐帧触发ContentDidScrollCallback回调。<br/>例如，当视窗内有下标为0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。<br/>4、设置displayCount属性的swipeByGroup参数为true时，若同组中至少有一个页面在视窗内时，<br/>则会对同组中所有页面触发回调。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含4个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：Swiper组件的索引，和onChange事件中的index值变化保持一致。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：视窗内某个页面的索引。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].f32**：页面相对于Swiper主轴起始位置（selectedIndex对应页面的起始位置）的移动比例。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[3].f32**：主轴方向上页面的长度。 |
| NODE_SWIPER_EVENT_ON_SELECTED  | 定义当ARKUI_NODE_SWIPER选中元素改变时触发回调。<br/>触发该事件的条件 ：<br/>1、滑动离手时满足翻页阈值，开始切换动画时。 <br/>2、通过NODE_SWIPER_INDEX或NODE_SWIPER_SWIPE_TO_INDEX切换页面时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示当前选中元素的索引。<br/>**起始版本：** 18 |
| NODE_SWIPER_EVENT_ON_UNSELECTED  | 定义当ARKUI_NODE_SWIPER选中元素改变时触发回调。<br/>触发该事件的条件 ：<br/>1、滑动离手时满足翻页阈值，开始切换动画时。 <br/>2、通过NODE_SWIPER_INDEX或NODE_SWIPER_SWIPE_TO_INDEX切换页面时。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：表示将要隐藏元素的索引。<br/>**起始版本：** 18 |
| NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL | 定义ARKUI_NODE_SWIPER滑动行为拦截事件。 使用说明 ：<br/>1、触发该事件的场景仅限于手势操作，具体包括手指滑动、滚动鼠标滚轮以及使用键盘方向键进行焦点移动。<br/>2、在手指滑动的过程中，每帧都将触发该事件，系统会依据事件的返回值判断是否对每帧的滑动做出响应。<br/>3、对于滚动鼠标滚轮和使用键盘方向键进行焦点移动的场景，每次翻页操作都会触发一次该事件，翻页是否被允许将根据事件的返回值来决定。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含3个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：当前页面对应的index。在一次跟手滑动过程中，只要手指未离开屏幕，该值将保持不变，即使该页面已完全移出视窗，如在涉及多个页面的场景中。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：滑动方向上即将显示的页面index。。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].f32**：此次滑动的位移，带有符号，正负分别指示不同的翻页方向。正数表示从index=1向index=0翻页，负数表示从index=0向index=1翻页。<br>在手指滑动的场景中，该值为滑动事件中每帧传递下来的偏移量。在滚动鼠标滚轮和使用键盘方向键导航的场景中，该值代表即将翻页的距离。 <br/>**[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)**中包含1个返回值：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：事件处理函数中可将是否允许本次滑动的值存于data[0].i32中，Swiper将根据返回值决定本次滑动是否响应。<br/>**起始版本：** 15|
| NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED | 定义ARKUI_NODE_SWIPER滑动状态变化事件。<br/>触发该事件的条件 ：<br/>Swiper在跟手滑动、离手动画、停止三种滑动状态变化时触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：当前滑动状态，参数类型[ArkUI_ScrollState](#arkui_scrollstate)。<br/>**起始版本：** 20|
| NODE_SCROLL_EVENT_ON_SCROLL  | 定义滚动容器组件的滚动事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用。<br/>3、越界回弹。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**：表示距离上一次事件触发的X轴增量。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**：表示距离上一次事件触发的Y轴增量。 |
| NODE_SCROLL_EVENT_ON_SCROLL_FRAME_BEGIN  | 定义滚动容器组件的滚动帧始事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件触发滚动时触发，包括键鼠操作等其他触发滚动的输入设置。<br/>2、调用控制器接口时不触发。<br/>3、越界回弹不触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**：表示即将发生的滚动量。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：表示当前滚动状态。<br/>**[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)**中包含1个返回值：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**：事件处理函数中可根据应用场景计算实际需要的滚动量并存于data[0].f32中，Scroll将按照返回值的实际滚动量进行滚动。 |
| NODE_SCROLL_EVENT_ON_WILL_SCROLL  | 定义滚动容器组件的滑动前触发事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用。<br/>3、越界回弹。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含4个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**: 每帧滚动的偏移量，内容向左滚动时偏移量为正，向右滚动时偏移量为负，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**: 每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].i32**: 当前滑动状态，参数类型[ArkUI_ScrollState](#arkui_scrollstate)。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[3].i32**: 当前滚动的来源，参数类型[ArkUI_ScrollSource](#arkui_scrollsource)。<br/>返回<br/>不返回或返回一个number，用于设置滚动组件实际的滚动距离。 |
| NODE_SCROLL_EVENT_ON_DID_SCROLL  | 定义滚动容器组件的滑动时触发事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用。<br/>3、越界回弹。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含3个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**: 每帧滚动的偏移量，内容向左滚动时偏移量为正，向右滚动时偏移量为负，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].f32**: 每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负，单位vp。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].i32**: 当前滑动状态，参数类型[ArkUI_ScrollState](#arkui_scrollstate)。 |
| NODE_SCROLL_EVENT_ON_SCROLL_START  | 定义滚动容器组件的滚动开始事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件开始滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用后开始，带过渡动效。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_SCROLL_EVENT_ON_SCROLL_STOP  | 定义滚动容器组件的滚动停止事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件触发滚动后停止，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用后停止，带过渡动效。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_SCROLL_EVENT_ON_SCROLL_EDGE  | 定义滚动容器组件的滚动边缘事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件滚动到边缘时触发，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用。<br/>3、越界回弹。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**表示当前碰到的是上下左右哪个边。 |
| NODE_SCROLL_EVENT_ON_REACH_START  | 定义滚动容器组件到达起始位置时触发回调。<br/>触发该事件的条件 ：<br/>1、组件到达起始位置时触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_SCROLL_EVENT_ON_REACH_END  | 定义滚动容器组件到底末尾位置时触发回调。<br/>触发该事件的条件 ：<br/>1、组件到底末尾位置时触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数。 |
| NODE_LIST_ON_SCROLL_INDEX  | 定义ARKUI_NODE_LIST有子组件划入或划出List显示区域时触发事件枚举值。<br/>触发该事件的条件 ：<br/>列表初始化时会触发一次，List显示区域内第一个子组件的索引值或最后一个子组件的索引值有变化时会触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含3个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**: List显示区域内第一个子组件的索引值.<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**: List显示区域内最后一个子组件的索引值.<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].i32**: List显示区域内中间位置子组件的索引值. |
| NODE_LIST_ON_WILL_SCROLL  | 定义ARKUI_NODE_LIST组件的滑动前触发事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用。<br/>3、越界回弹。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含3个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**: 每帧滚动的偏移量，list内容向上滚动时偏移量为正，向下滚动时偏移量为负.<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**: 当前滑动状态，参数类型[ArkUI_ScrollState](#arkui_scrollstate)。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].i32**: 当前滚动的来源，参数类型[ArkUI_ScrollSource](#arkui_scrollsource)。<br/>返回<br/>不返回或返回一个number，用于设置滚动组件实际的滚动距离。 |
| NODE_LIST_ON_DID_SCROLL  | 定义ARKUI_NODE_LIST组件的滑动时触发事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用。<br/>3、越界回弹。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**: 每帧滚动的偏移量，list内容向上滚动时偏移量为正，向下滚动时偏移量为负.<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**: 当前滑动状态. |
| NODE_LIST_ON_SCROLL_VISIBLE_CONTENT_CHANGE | 有子组件划入或划出List显示区域时触发。计算触发条件时，每一个ListItem、ListItemGroup中的header或footer都算一个子组件。List的边缘效果为弹簧效果时，在List划动到边缘继续划动和松手回弹过程不会触发NODE_LIST_ON_SCROLL_VISIBLE_CONTENT_CHANGE事件。<br/>触发该事件的条件 ：<br/> 列表初始化时会触发一次，List显示区域内第一个子组件的索引值或最后一个子组件的索引值有变化时会触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含6个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：列表显示区域中第一个子组件的索引。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**：列表项组中列表显示区域开始的区域，参数类型为[ArkUI_ListItemGroupArea](#arkui_listitemgrouparea)。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].i32**：列表显示区域开头的列表项的索引，在ListItemGroup中如果列表显示区域的开头不在列表项上，则值为1。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[3].i32**：列表显示区域中最后一个子组件的索引。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[4].i32**：列表项组中列表显示区域结束的区域，参数类型为[ArkUI_ListItemGroupArea](#arkui_listitemgrouparea)。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[5].i32**：列表显示区域末尾的列表项的索引，在ListItemGroup中如果列表显示区域的末尾不在列表项上，则值为1。<br/>**起始版本：** 15 |
| NODE_REFRESH_STATE_CHANGE  | 定义ARKUI_NODE_REFRESH刷新状态变更触发该事件。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**：刷新状态。 |
| NODE_REFRESH_ON_REFRESH  | 定义ARKUI_NODE_REFRESH进入刷新状态时触发该事件。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中不包含参数： |
| NODE_REFRESH_ON_OFFSET_CHANGE  | 定义ARKUI_NODE_REFRESH下拉距离发生变化时触发该事件。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含1个参数：<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**：下拉距离。 |
| NODE_ON_WILL_SCROLL  | 定义ARKUI_NODE_WATER_FLOW组件的滑动前触发事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用。<br/>3、越界回弹。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含3个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**: 每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负.<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**: 当前滑动状态，参数类型[ArkUI_ScrollState](#arkui_scrollstate)。<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[2].i32**: 当前滚动的来源，参数类型[ArkUI_ScrollSource](#arkui_scrollsource)。<br/>返回<br/>不返回或返回一个number，用于设置滚动组件实际的滚动距离。 |
| NODE_WATER_FLOW_ON_DID_SCROLL  | 定义ARKUI_NODE_WATER_FLOW组件的滑动时触发事件枚举值。<br/>触发该事件的条件 ：<br/>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br/>2、通过滚动控制器API接口调用。<br/>3、越界回弹。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含2个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].f32**: 每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负.<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**: 当前滑动状态. |
| NODE_WATER_FLOW_ON_SCROLL_INDEX  | 定义ARKUI_NODE_WATER_FLOW当前瀑布流显示的起始位置/终止位置的子组件发生变化时触发事件枚举值。<br/>触发该事件的条件 ：<br/>瀑布流显示区域上第一个子组件/最后一个组件的索引值有变化就会触发。<br/>事件回调发生时，事件参数[ArkUI_NodeEvent](#arkui_nodeevent-12)对象中的联合体类型为[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)。<br/>[ArkUI_NodeComponentEvent](_ark_u_i___node_component_event.md)中包含3个参数:<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[0].i32**: 当前显示的WaterFlow起始位置的索引值.<br/>**[ArkUI_NodeComponentEvent.data](_ark_u_i___node_component_event.md#data)[1].i32**: 当前显示的瀑布流终止位置的索引值. |


### ArkUI_NodeType

```
enum ArkUI_NodeType
```
**描述：**

提供ArkUI在Native侧可创建组件类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_NODE_CUSTOM  | 自定义节点。  |
| ARKUI_NODE_TEXT  | 文本。  |
| ARKUI_NODE_SPAN  | 文本段落。  |
| ARKUI_NODE_IMAGE_SPAN  | 文本图片段落。  |
| ARKUI_NODE_IMAGE  | 图片。  |
| ARKUI_NODE_TOGGLE  | 状态开关。  |
| ARKUI_NODE_LOADING_PROGRESS  | 等待图标。  |
| ARKUI_NODE_TEXT_INPUT  | 单行文本输入。  |
| ARKUI_NODE_TEXT_AREA  | 多行文本。  |
| ARKUI_NODE_BUTTON  | 按钮。  |
| ARKUI_NODE_PROGRESS  | 进度条。  |
| ARKUI_NODE_CHECKBOX  | 复选框。  |
| ARKUI_NODE_XCOMPONENT  | SURFACE类型XComponent。  |
| ARKUI_NODE_DATE_PICKER  | 日期选择器组件。  |
| ARKUI_NODE_TIME_PICKER  | 时间选择组件。  |
| ARKUI_NODE_TEXT_PICKER  | 滑动选择文本内容的组件。  |
| ARKUI_NODE_CALENDAR_PICKER  | 日历选择器组件。  |
| ARKUI_NODE_SLIDER  | 滑动条组件  |
| ARKUI_NODE_RADIO  | 单选框  |
| ARKUI_NODE_IMAGE_ANIMATOR  | 帧动画组件  |
| ARKUI_NODE_XCOMPONENT_TEXTURE  | TEXTURE类型XComponent。 <br> **起始版本：** 18 |
| ARKUI_NODE_CHECKBOX_GROUP | 复选框组。 <br> **起始版本：** 15 |
| ARKUI_NODE_STACK  | 堆叠容器。  |
| ARKUI_NODE_SWIPER  | 翻页容器。  |
| ARKUI_NODE_SCROLL  | 滚动容器。  |
| ARKUI_NODE_LIST  | 列表。  |
| ARKUI_NODE_LIST_ITEM  | 列表项。  |
| ARKUI_NODE_LIST_ITEM_GROUP  | 列表item分组。  |
| ARKUI_NODE_COLUMN  | 垂直布局容器。  |
| ARKUI_NODE_ROW  | 水平布局容器。  |
| ARKUI_NODE_FLEX  | 弹性布局容器。  |
| ARKUI_NODE_REFRESH  | 刷新组件。  |
| ARKUI_NODE_WATER_FLOW  | 瀑布流容器。  |
| ARKUI_NODE_FLOW_ITEM  | 瀑布流子组件。  |
| ARKUI_NODE_RELATIVE_CONTAINER  | 相对布局组件。  |
| ARKUI_NODE_GRID  | 网格容器。  |
| ARKUI_NODE_GRID_ITEM  | 网格子组件。  |
| ARKUI_NODE_CUSTOM_SPAN  | 自定义文本段落。  |
| ARKUI_NODE_EMBEDDED_COMPONENT  | 同应用进程嵌入式组件。 <br> **起始版本：** 20  |


### ArkUI_ObjectFit

```
enum ArkUI_ObjectFit
```
**描述：**

定义image填充效果。 ImageSpanAlignment

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_OBJECT_FIT_CONTAIN  | 保持宽高比进行缩小或者放大，使得图片完全显示在显示边界内。  |
| ARKUI_OBJECT_FIT_COVER  | 保持宽高比进行缩小或者放大，使得图片两边都大于或等于显示边界。  |
| ARKUI_OBJECT_FIT_AUTO  | 自适应显示。  |
| ARKUI_OBJECT_FIT_FILL  | 不保持宽高比进行放大缩小，使得图片充满显示边界。  |
| ARKUI_OBJECT_FIT_SCALE_DOWN  | 保持宽高比显示，图片缩小或者保持不变。  |
| ARKUI_OBJECT_FIT_NONE  | 保持原有尺寸显示。  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_START  | 图片大小不变，在image组件中顶部起始端对齐。  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP  | 图片大小不变，在image组件中顶部横向居中对齐。  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_END  | 图片大小不变，在image组件中顶部尾端对齐。  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_START  | 图片大小不变，在image组件中起始端纵向居中对齐。  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_CENTER  | 图片大小不变，在image组件中横向和纵向居中对齐。  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_END  | 图片大小不变，在image组件中尾端纵向居中对齐。  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_START  | 图片大小不变，在image组件中底部起始端对齐。  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM  | 图片大小不变，在image组件中底部横向居中对齐。  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_END  | 图片大小不变，在image组件中底部尾端对齐。  |


### ArkUI_PageFlipMode

```
enum ArkUI_PageFlipMode
```
**描述：**

Swiper组件鼠标滚轮翻页模式。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_PAGE_FLIP_MODE_CONTINUOUS  | 鼠标滚轮连续滚动时翻多页，根据鼠标事件上报次数确定。  |
| ARKUI_PAGE_FLIP_MODE_SINGLE  | 一次翻页动画结束前不响应其他鼠标滚轮事件。  |


### ArkUI_SwiperAnimationMode

```
enum ArkUI_SwiperAnimationMode
```
**描述：**

Swiper组件跳转到目标index的动画模式。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SWIPER_NO_ANIMATION  | 无动画跳转到目标index。  |
| ARKUI_SWIPER_DEFAULT_ANIMATION  | 做动画跳转到目标index。  |
| ARKUI_SWIPER_FAST_ANIMATION  | 先无动画跳转到目标附近再做动画跳转到目标index。  |


### ArkUI_PreDragStatus

```
enum ArkUI_PreDragStatus
```
**描述：**

定义拖拽发起前的长按交互阶段的变化状态。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_PRE_DRAG_STATUS_UNKNOWN  | Unknown。  |
| ARKUI_PRE_DRAG_STATUS_ACTION_DETECTING  | 拖拽手势启动阶段。  |
| ARKUI_PRE_DRAG_STATUS_READY_TO_TRIGGER_DRAG  | 拖拽准备完成，可发起拖拽阶段。  |
| ARKUI_PRE_DRAG_STATUS_PREVIEW_LIFT_STARTED  | 拖拽浮起动效发起阶段。  |
| ARKUI_PRE_DRAG_STATUS_PREVIEW_LIFT_FINISHED  | 拖拽浮起动效结束阶段。  |
| ARKUI_PRE_DRAG_STATUS_PREVIEW_LANDING_STARTED  | 拖拽落回动效发起阶段。  |
| ARKUI_PRE_DRAG_STATUS_PREVIEW_LANDING_FINISHED  | 拖拽落回动效结束阶段。  |
| ARKUI_PRE_DRAG_STATUS_CANCELED_BEFORE_DRAG  | 拖拽浮起落位动效中断。  |


### ArkUI_ProgressType

```
enum ArkUI_ProgressType
```
**描述：**

定义进度条类型枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_PROGRESS_TYPE_LINEAR  | 线性样式。  |
| ARKUI_PROGRESS_TYPE_RING  | 环形无刻度样式。  |
| ARKUI_PROGRESS_TYPE_ECLIPSE  | 圆形样式。  |
| ARKUI_PROGRESS_TYPE_SCALE_RING  | 环形有刻度样式。  |
| ARKUI_PROGRESS_TYPE_CAPSULE  | 胶囊样式。  |


### ArkUI_RelativeLayoutChainStyle

```
enum ArkUI_RelativeLayoutChainStyle
```
**描述：**

定义链的风格。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_RELATIVE_LAYOUT_CHAIN_STYLE_SPREAD  | 组件在约束锚点间均匀分布。  |
| ARKUI_RELATIVE_LAYOUT_CHAIN_STYLE_SPREAD_INSIDE  | 除首尾2个子组件的其他组件在约束锚点间均匀分布。  |
| ARKUI_RELATIVE_LAYOUT_CHAIN_STYLE_PACKED  | 链内子组件无间隙。  |


### ArkUI_RenderFit

```
enum ArkUI_RenderFit
```

**描述：**

定义动画终态内容的状态。

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_RENDER_FIT_CENTER  | 保持动画终态的内容大小，并且内容始终与组件保持中心对齐。  |
| ARKUI_RENDER_FIT_TOP  | 保持动画终态的内容大小，并且内容始终与组件保持顶部中心对齐。  |
| ARKUI_RENDER_FIT_BOTTOM  | 保持动画终态的内容大小，并且内容始终与组件保持底部中心对齐。  |
| ARKUI_RENDER_FIT_LEFT  | 保持动画终态的内容大小，并且内容始终与组件保持左侧对齐。  |
| ARKUI_RENDER_FIT_RIGHT  | 保持动画终态的内容大小，并且内容始终与组件保持右侧对齐。  |
| ARKUI_RENDER_FIT_TOP_LEFT  | 保持动画终态的内容大小，并且内容始终与组件保持左上角对齐。  |
| ARKUI_RENDER_FIT_TOP_RIGHT  | 保持动画终态的内容大小，并且内容始终与组件保持右上角对齐。  |
| ARKUI_RENDER_FIT_BOTTOM_LEFT  | 保持动画终态的内容大小，并且内容始终与组件保持左下角对齐。  |
| ARKUI_RENDER_FIT_BOTTOM_RIGHT  | 保持动画终态的内容大小，并且内容始终与组件保持右下角对齐。  |
| ARKUI_RENDER_FIT_RESIZE_FILL  | 不考虑动画终态内容的宽高比，并且内容始终缩放到组件的大小。  |
| ARKUI_RENDER_FIT_RESIZE_CONTAIN  | 保持动画终态内容的宽高比进行缩小或放大，使内容完整显示在组件内，且与组件保持中心对齐。  |
| ARKUI_RENDER_FIT_RESIZE_CONTAIN_TOP_LEFT  | 保持动画终态内容的宽高比进行缩小或放大，使内容完整显示在组件内。当组件宽方向有剩余时，内容与组件保持左侧对齐，当组件高方向有剩余时，内容与组件保持顶部对齐。  |
| ARKUI_RENDER_FIT_RESIZE_CONTAIN_BOTTOM_RIGHT  | 保持动画终态内容的宽高比进行缩小或放大，使内容完整显示在组件内。当组件宽方向有剩余时，内容与组件保持右侧对齐，当组件高方向有剩余时，内容与组件保持底部对齐。  |
| ARKUI_RENDER_FIT_RESIZE_COVER  | 保持动画终态内容的宽高比进行缩小或放大，使内容两边都大于或等于组件两边，且与组件保持中心对齐，显示内容的中间部分。  |
| ARKUI_RENDER_FIT_RESIZE_COVER_TOP_LEFT  | 保持动画终态内容的宽高比进行缩小或放大，使内容的两边都恰好大于或等于组件两边。当内容宽方向有剩余时，内容与组件保持左侧对齐，显示内容的左侧部分。当内容高方向有剩余时，内容与组件保持顶部对齐，显示内容的顶侧部分。  |
| ARKUI_RENDER_FIT_RESIZE_COVER_BOTTOM_RIGHT  | 保持动画终态内容的宽高比进行缩小或放大，使内容的两边都恰好大于或等于组件两边。当内容宽方向有剩余时，内容与组件保持右侧对齐，显示内容的右侧部分。当内容高方向有剩余时，内容与组件保持底部对齐，显示内容的底侧部分。  |


### ArkUI_RouterPageState

```
enum ArkUI_RouterPageState
```
**描述：**

定义Router Page的状态。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR  | Router Page即将创建。  |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR  | Router Page即将销毁。  |
| ARKUI_ROUTER_PAGE_STATE_ON_SHOW  | Router Page显示。  |
| ARKUI_ROUTER_PAGE_STATE_ON_HIDE  | Router Page隐藏。  |
| ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS  | Router Page返回时。  |


### ArkUI_SafeAreaEdge

```
enum ArkUI_SafeAreaEdge
```
**描述：**

定义扩展安全区域的方向的枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SAFE_AREA_EDGE_TOP  | 上方区域。  |
| ARKUI_SAFE_AREA_EDGE_BOTTOM  | 下方区域。  |
| ARKUI_SAFE_AREA_EDGE_START  | 前部区域。  |
| ARKUI_SAFE_AREA_EDGE_END  | 尾部区域。  |


### ArkUI_SafeAreaType

```
enum ArkUI_SafeAreaType
```
**描述：**

定义扩展安全区域的枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SAFE_AREA_TYPE_SYSTEM  | 系统默认非安全区域，包括状态栏、导航栏。  |
| ARKUI_SAFE_AREA_TYPE_CUTOUT  | 设备的非安全区域，例如刘海屏或挖孔屏区域。  |
| ARKUI_SAFE_AREA_TYPE_KEYBOARD  | 软键盘区域。  |


### ArkUI_ListItemGroupArea

```
enum ArkUI_ListItemGroupArea
```
**描述：**

定义组件区域的枚举值。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE   | 组件的区域之外。  |
| ARKUI_LIST_ITEM_SWIPE_AREA_NONE  | 组件没有页眉、页脚或列表项时的区域。  |
| ARKUI_LIST_ITEM_SWIPE_AREA_ITEM  | 组件的列表项区域。  |
| ARKUI_LIST_ITEM_SWIPE_AREA_HEADER  | 组件的标题区域。  |
| ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER  | 组件的页脚区域。  |


### ArkUI_FocusMove

```
enum ArkUI_FocusMove
```
**描述：**

定义自定义走焦的按键的枚举值。

**起始版本：** 18

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_FOCUS_MOVE_FORWARD  | 向前移动焦点。  |
| ARKUI_FOCUS_MOVE_BACKWARD  | 向后移动焦点。  |
| ARKUI_FOCUS_MOVE_UP  | 向上移动焦点。  |
| ARKUI_FOCUS_MOVE_DOWN  | 向下移动焦点。  |
| ARKUI_FOCUS_MOVE_LEFT  | 向左移动焦点。  |
| ARKUI_FOCUS_MOVE_RIGHT  | 向右移动焦点。  |

### ArkUI_ScrollAlignment

```
enum ArkUI_ScrollAlignment
```
**描述：**

滚动到具体item时的对齐方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SCROLL_ALIGNMENT_START  | 首部对齐。指定item首部与容器首部对齐。  |
| ARKUI_SCROLL_ALIGNMENT_CENTER  | 居中对齐。指定item主轴方向居中对齐于容器。  |
| ARKUI_SCROLL_ALIGNMENT_END  | 尾部对齐。指定item尾部与容器尾部对齐。  |
| ARKUI_SCROLL_ALIGNMENT_AUTO  | 自动对齐。若指定item完全处于显示区，不做调整。否则依照滑动距离最短的原则，将指定item首部对齐或尾部对齐于容器,使指定item完全处于显示区。  |


### ArkUI_ScrollBarDisplayMode

```
enum ArkUI_ScrollBarDisplayMode
```
**描述：**

定义滚动条状态枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF  | 不显示。  |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO  | 按需显示(触摸时显示，2s后消失)。  |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_ON  | 常驻显示。  |


### ArkUI_ScrollDirection

```
enum ArkUI_ScrollDirection
```
**描述：**

定义Scroll组件排列方向枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SCROLL_DIRECTION_VERTICAL  | 仅支持竖直方向滚动。  |
| ARKUI_SCROLL_DIRECTION_HORIZONTAL  | 仅支持水平方向滚动。  |
| ARKUI_SCROLL_DIRECTION_NONE  | 禁止滚动。  |


### ArkUI_ScrollEdge

```
enum ArkUI_ScrollEdge
```
**描述：**

定义滚动到的边缘位置。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SCROLL_EDGE_TOP  | 竖直方向上边缘。  |
| ARKUI_SCROLL_EDGE_BOTTOM  | 竖直方向下边缘。  |
| ARKUI_SCROLL_EDGE_START  | 水平方向起始位置。  |
| ARKUI_SCROLL_EDGE_END  | 水平方向末尾位置。  |


### ArkUI_ScrollNestedMode

```
enum ArkUI_ScrollNestedMode
```
**描述：**

定义嵌套滚动选项。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SCROLL_NESTED_MODE_SELF_ONLY  | 只自身滚动，不与父组件联动。  |
| ARKUI_SCROLL_NESTED_MODE_SELF_FIRST  | 自身先滚动，自身滚动到边缘以后父组件滚动。父组件滚动到边缘以后 如果父组件有边缘效果，则父组件触发边缘效果，否则子组件触发边缘效果。  |
| ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST  | 父组件先滚动，父组件滚动到边缘以后自身滚动。 身滚动到边缘后，如果有边缘效果，会触发自身的边缘效果，否则触发父组件的边缘效果。  |
| ARKUI_SCROLL_NESTED_MODE_PARALLEL  | 自身和父组件同时滚动，自身和父组件都到达边缘以后 如果自身有边缘效果，则自身触发边缘效果，否则父组件触发边缘效果。  |


### ArkUI_ScrollSnapAlign

```
enum ArkUI_ScrollSnapAlign
```
**描述：**

定义列表项滚动结束对齐效果枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SCROLL_SNAP_ALIGN_NONE  | 默认无项目滚动对齐效果。  |
| ARKUI_SCROLL_SNAP_ALIGN_START  | 视图中的第一项将在列表的开头对齐。  |
| ARKUI_SCROLL_SNAP_ALIGN_CENTER  | 视图中的中间项将在列表中心对齐。  |
| ARKUI_SCROLL_SNAP_ALIGN_END  | 视图中的最后一项将在列表末尾对齐。  |


### ArkUI_ScrollSource

```
enum ArkUI_ScrollSource
```
**描述：**

定义滚动来源枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SCROLL_SOURCE_DRAG  | 手指拖动。  |
| ARKUI_SCROLL_SOURCE_FLING  | 手指拖动后的惯性滚动。  |
| ARKUI_SCROLL_SOURCE_EDGE_EFFECT  | 在过界时执行EdgeEffect.Spring边缘特效。  |
| ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT  | 除了拖动以外的其他用户输入，如鼠标滚轮、键盘事件等。  |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR  | 拖动滚动条。  |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING  | 拖动滚动条后的惯性滚动。  |
| ARKUI_SCROLL_SOURCE_SCROLLER  | 滚动控制器引起的无动画的滚动。  |
| ARKUI_SCROLL_SOURCE_ANIMATION  | 滚动控制器引起的带动画的滚动。  |


### ArkUI_ScrollState

```
enum ArkUI_ScrollState
```
**描述：**

定义当前滚动状态。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SCROLL_STATE_IDLE  | 空闲状态。使用控制器提供的方法控制滚动时触发，拖动滚动条滚动时触发。  |
| ARKUI_SCROLL_STATE_SCROLL  | 滚动状态。使用手指拖动容器滚动时触发。  |
| ARKUI_SCROLL_STATE_FLING  | 惯性滚动状态。快速划动松手后进行惯性滚动和划动到边缘回弹时触发。  |


### ArkUI_ShadowStyle

```
enum ArkUI_ShadowStyle
```
**描述：**

阴影效果枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_XS  | 超小阴影。  |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_SM  | 小阴影。  |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_MD  | 中阴影。  |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_LG  | 大阴影。  |
| ARKUI_SHADOW_STYLE_OUTER_FLOATING_SM  | 浮动小阴影。  |
| ARKUI_SHADOW_STYLE_OUTER_FLOATING_MD  | 浮动中阴影。  |


### ArkUI_ShadowType

```
enum ArkUI_ShadowType
```
**描述：**

定义阴影类型枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SHADOW_TYPE_COLOR  | 颜色。  |
| ARKUI_SHADOW_TYPE_BLUR  | 模糊。  |

### ArkUI_ShapeType

```
enum ArkUI_ShapeType
```
**描述：**

自定义形状。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SHAPE_TYPE_RECTANGLE  | 矩形类型。  |
| ARKUI_SHAPE_TYPE_CIRCLE  | 圆形类型。  |
| ARKUI_SHAPE_TYPE_ELLIPSE  | 椭圆形类型。  |
| ARKUI_SHAPE_TYPE_PATH  | 路径类型。  |


### ArkUI_SliderBlockStyle

```
enum ArkUI_SliderBlockStyle
```
**描述：**

定义滑块形状。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SLIDER_BLOCK_STYLE_DEFAULT  | 使用默认滑块（圆形）。  |
| ARKUI_SLIDER_BLOCK_STYLE_IMAGE  | 使用图片资源作为滑块。  |
| ARKUI_SLIDER_BLOCK_STYLE_SHAPE  | 使用自定义形状作为滑块。  |


### ArkUI_SliderDirection

```
enum ArkUI_SliderDirection
```
**描述：**

定义滑动条滑动方向。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SLIDER_DIRECTION_VERTICAL  | 方向为纵向。  |
| ARKUI_SLIDER_DIRECTION_HORIZONTAL  | 方向为横向。  |


### ArkUI_SliderStyle

```
enum ArkUI_SliderStyle
```
**描述：**

定义滑块与滑轨显示样式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SLIDER_STYLE_OUT_SET  | 滑块在滑轨上。  |
| ARKUI_SLIDER_STYLE_IN_SET  | 滑块在滑轨内。  |
| ARKUI_SLIDER_STYLE_NONE  | 无滑块。  |


### ArkUI_StickyStyle

```
enum ArkUI_StickyStyle
```
**描述：**

定义列表是否吸顶和吸底枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_STICKY_STYLE_NONE  | ListItemGroup的header不吸顶，footer不吸底。  |
| ARKUI_STICKY_STYLE_HEADER  | ListItemGroup的header吸顶，footer不吸底。  |
| ARKUI_STICKY_STYLE_FOOTER  | ListItemGroup的footer吸底，header不吸顶。  |
| ARKUI_STICKY_STYLE_BOTH  | ListItemGroup的footer吸底，header吸顶。  |


### ArkUI_SwiperArrow

```
enum ArkUI_SwiperArrow
```
**描述：**

Swiper导航点箭头枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SWIPER_ARROW_HIDE  | 不显示swiper中导航点箭头。  |
| ARKUI_SWIPER_ARROW_SHOW  | 显示swiper中导航点箭头。  |
| ARKUI_SWIPER_ARROW_SHOW_ON_HOVER  | 在hover状态下显示swiper中导航点箭头。  |


### ArkUI_SwiperDisplayModeType

```
enum ArkUI_SwiperDisplayModeType
```
**描述：**

定义 Swiper 组件的主轴方向上元素排列的模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SWIPER_DISPLAY_MODE_STRETCH  | Swiper滑动一页的宽度为Swiper组件自身的宽度。  |
| ARKUI_SWIPER_DISPLAY_MODE_AUTO_LINEAR  | Swiper滑动一页的宽度为视窗内最左侧子组件的宽度。  |


### ArkUI_SwiperIndicatorType

```
enum ArkUI_SwiperIndicatorType
```
**描述：**

定义 Swiper 组件的导航指示器类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SWIPER_INDICATOR_TYPE_DOT  | 圆点指示器类型。  |
| ARKUI_SWIPER_INDICATOR_TYPE_DIGIT  | 数字指示器类型。  |


### ArkUI_SwiperNestedScrollMode

```
enum ArkUI_SwiperNestedScrollMode
```
**描述：**

Swiper组件和父组件的嵌套滚动模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY  | Swiper只自身滚动，不与父组件联动。  |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_FIRST  | Swiper自身先滚动，自身滚动到边缘以后父组件滚动。父组件滚动到边缘以后，如果父组件有边缘效果，则父组件触发边缘效果，否则Swiper触发边缘效果。  |


### ArkUI_SystemColorMode

```
enum ArkUI_SystemColorMode
```
**描述：**

定义系统深浅色模式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_SYSTEM_COLOR_MODE_LIGHT  | 浅色模式  |
| ARKUI_SYSTEM_COLOR_MODE_DARK  | 深色模式  |


### ArkUI_TextAlignment

```
enum ArkUI_TextAlignment
```
**描述：**

定义字体水平对齐样式枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXT_ALIGNMENT_START  | 水平对齐首部。  |
| ARKUI_TEXT_ALIGNMENT_CENTER  | 水平居中对齐。  |
| ARKUI_TEXT_ALIGNMENT_END  | 水平对齐尾部。  |
| ARKUI_TEXT_ALIGNMENT_JUSTIFY  | 双端对齐。  |


### ArkUI_TextVerticalAlignment

```
enum ArkUI_TextVerticalAlignment
```
**描述：**

定义文本垂直对齐样式枚举值。

**起始版本：** 20

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE  | 基线对齐。  |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_BOTTOM  | 底部对齐。  |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_CENTER  | 居中对齐。  |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_TOP  | 顶部对齐。  |


### ArkUI_TextAreaType

```
enum ArkUI_TextAreaType
```
**描述：**

定义多行文本输入法类型枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXTAREA_TYPE_NORMAL  | 基本输入模式。  |
| ARKUI_TEXTAREA_TYPE_NUMBER  | 纯数字模式。  |
| ARKUI_TEXTAREA_TYPE_PHONE_NUMBER  | 电话号码输入模式。  |
| ARKUI_TEXTAREA_TYPE_EMAIL  | 邮箱地址输入模式。  |
| ARKUI_TEXTAREA_TYPE_ONE_TIME_CODE  | 验证码输入模式。<br/>**起始版本：** 20  |


### ArkUI_TextCase

```
enum ArkUI_TextCase
```
**描述：**

定义文本大小写枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXT_CASE_NORMAL  | 保持原有大小写。  |
| ARKUI_TEXT_CASE_LOWER  | 文本全小写。  |
| ARKUI_TEXT_CASE_UPPER  | 文本全大写。  |


### ArkUI_TextCopyOptions

```
enum ArkUI_TextCopyOptions
```
**描述：**

定义组件支持设置文本是否可复制粘贴。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXT_COPY_OPTIONS_NONE  | 不支持复制。  |
| ARKUI_TEXT_COPY_OPTIONS_IN_APP  | 支持应用内复制。  |
| ARKUI_TEXT_COPY_OPTIONS_LOCAL_DEVICE  | 支持设备内复制。  |
| ARKUI_TEXT_COPY_OPTIONS_CROSS_DEVICE  | 支持跨设备复制。  |


### ArkUI_TextDataDetectorType

```
enum ArkUI_TextDataDetectorType
```
**描述：**

定义文本识别的实体类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_PHONE_NUMBER  | 电话号码。  |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_URL  | 链接。  |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_EMAIL  | 邮箱。  |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_ADDRESS  | 地址。  |


### ArkUI_TextDecorationStyle

```
enum ArkUI_TextDecorationStyle
```
**描述：**

定义装饰线样式枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXT_DECORATION_STYLE_SOLID  | 单实线。  |
| ARKUI_TEXT_DECORATION_STYLE_DOUBLE  | 双实线。  |
| ARKUI_TEXT_DECORATION_STYLE_DOTTED  | 点线。  |
| ARKUI_TEXT_DECORATION_STYLE_DASHED  | 虚线。  |
| ARKUI_TEXT_DECORATION_STYLE_WAVY  | 波浪线。  |


### ArkUI_TextDecorationType

```
enum ArkUI_TextDecorationType
```
**描述：**

定义装饰线类型枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXT_DECORATION_TYPE_NONE  | 不使用装饰线。  |
| ARKUI_TEXT_DECORATION_TYPE_UNDERLINE  | 文字下划线修饰。  |
| ARKUI_TEXT_DECORATION_TYPE_OVERLINE  | 文字上划线修饰。  |
| ARKUI_TEXT_DECORATION_TYPE_LINE_THROUGH  | 穿过文本的修饰线。  |


### ArkUI_TextHeightAdaptivePolicy

```
enum ArkUI_TextHeightAdaptivePolicy
```
**描述：**

定义文本自适应高度的方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST  | 设置文本高度自适应方式为以MaxLines优先。  |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MIN_FONT_SIZE_FIRST  | 设置文本高度自适应方式为以缩小字体优先。  |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_LAYOUT_CONSTRAINT_FIRST  | 设置文本高度自适应方式为以布局约束（高度）优先。  |


### ArkUI_TextInputContentType

```
enum ArkUI_TextInputContentType
```
**描述：**

定义自动填充类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME  | 【用户名】在已启用密码保险箱的情况下，支持用户名的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD  | 【密码】在已启用密码保险箱的情况下，支持密码的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD  | 【新密码】在已启用密码保险箱的情况下，支持自动生成新密码。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS  | 【详细地址】在已启用情景化自动填充的情况下，支持详细地址的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER  | 【门牌号】在已启用情景化自动填充的情况下，支持门牌号的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS  | 【区/县】在已启用情景化自动填充的情况下，支持区/县的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS  | 【市】在已启用情景化自动填充的情况下，支持市的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS  | 【省】在已启用情景化自动填充的情况下，支持省的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS  | 【国家】在已启用情景化自动填充的情况下，支持国家的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME  | 【姓名】在已启用情景化自动填充的情况下，支持姓名的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME  | 【姓氏】在已启用情景化自动填充的情况下，支持姓氏的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME  | 【名字】在已启用情景化自动填充的情况下，支持名字的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER  | 【手机号】在已启用情景化自动填充的情况下，支持手机号的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE  | 【国家代码】在已启用情景化自动填充的情况下，支持国家代码的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER  | 【包含国家代码的手机号】在已启用情景化自动填充的情况下，支持包含国家代码的手机号的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS  | 【邮箱地址】在已启用情景化自动填充的情况下，支持邮箱地址的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER  | 【银行卡号】在已启用情景化自动填充的情况下，支持银行卡号的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER  | 【身份证号】在已启用情景化自动填充的情况下，支持身份证号的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME  | 【昵称】在已启用情景化自动填充的情况下，支持昵称的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET  | 【无街道地址】在已启用情景化自动填充的情况下，支持无街道地址的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS  | 【标准地址】在已启用情景化自动填充的情况下，支持标准地址的自动保存和自动填充。  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER  | 【护照号】在已启用情景化自动填充的情况下，支持护照号的自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY  | 【护照有效期】在已启用情景化自动填充的情况下，支持护照有效期的自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT  | 【护照签发地】在已启用情景化自动填充的情况下，支持护照签发地的自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION  | 【发票抬头名称】在已启用情景化自动填充的情况下，支持发票抬头名称的自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID  | 【税号】在已启用情景化自动填充的情况下，支持税号的自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE  | 【所在地区】在已启用情景化自动填充的情况下，支持所在地区的自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER  | 【航班号】暂不支持自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER  | 【驾驶证号】暂不支持自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER  | 【驾驶证档案编号】暂不支持自动保存和自动填充。<br/>起始版本：18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE  | 【车牌号】在已启用情景化自动填充的情况下，支持车牌号的自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER  | 【行驶证发动机号】暂不支持自动保存和自动填充。<br/>起始版本：18  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER  | 【车牌识别号】暂不支持自动保存和自动填充。<br/>起始版本：18  |


### ArkUI_TextInputStyle

```
enum ArkUI_TextInputStyle
```
**描述：**

定义输入框风格。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXTINPUT_STYLE_DEFAULT  | 默认风格，光标宽1.5vp，光标高度与文本选中底板高度和字体大小相关。  |
| ARKUI_TEXTINPUT_STYLE_INLINE  | 内联输入风格。文本选中底板高度与输入框高度相同。  |


### ArkUI_TextInputType

```
enum ArkUI_TextInputType
```
**描述：**

定义单行文本输入法类型枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXTINPUT_TYPE_NORMAL  | 基本输入模式。  |
| ARKUI_TEXTINPUT_TYPE_NUMBER  | 纯数字模式。  |
| ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER  | 电话号码输入模式。  |
| ARKUI_TEXTINPUT_TYPE_EMAIL  | 邮箱地址输入模式。  |
| ARKUI_TEXTINPUT_TYPE_PASSWORD  | 密码输入模式。  |
| ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD  | 纯数字密码输入模式。  |
| ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD  | 锁屏应用密码输入模式。  |
| ARKUI_TEXTINPUT_TYPE_USER_NAME  | 用户名输入模式。  |
| ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD  | 新密码输入模式。  |
| ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL  | 带小数点的数字输入模式。  |
| ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE  | 验证码输入模式。<br/>**起始版本：** 20  |


### ArkUI_TextOverflow

```
enum ArkUI_TextOverflow
```
**描述：**

定义文本超长时的显示方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXT_OVERFLOW_NONE  | 文本超长时不裁剪显示。  |
| ARKUI_TEXT_OVERFLOW_CLIP  | 文本超长时进行裁剪显示。  |
| ARKUI_TEXT_OVERFLOW_ELLIPSIS  | 文本超长时显示不下的文本用省略号代替。  |
| ARKUI_TEXT_OVERFLOW_MARQUEE  | 文本超长时以跑马灯的方式展示。  |


### ArkUI_TextPickerRangeType

```
enum ArkUI_TextPickerRangeType
```
**描述：**

定义滑动选择文本选择器输入类型。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TEXTPICKER_RANGETYPE_SINGLE  | 单列数据选择器。  |
| ARKUI_TEXTPICKER_RANGETYPE_MULTI  | 多列数据选择器。  |
| ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT  | 支持图片资源的单列数据选择器。  |
| ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT  | 支持联动的多列数据选择器。  |

### ArkUI_TransitionEdge

```
enum ArkUI_TransitionEdge
```
**描述：**

定义转场从边缘滑入和滑出的效果。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_TRANSITION_EDGE_TOP  | 窗口的上边缘。  |
| ARKUI_TRANSITION_EDGE_BOTTOM  | 窗口的下边缘。  |
| ARKUI_TRANSITION_EDGE_START  | 窗口的左边缘。  |
| ARKUI_TRANSITION_EDGE_END  | 窗口的右边缘。  |


### ArkUI_VerticalAlignment

```
enum ArkUI_VerticalAlignment
```
**描述：**

定义垂直对齐方式。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_VERTICAL_ALIGNMENT_TOP  | 顶部对齐。  |
| ARKUI_VERTICAL_ALIGNMENT_CENTER  | 居中对齐，默认对齐方式。  |
| ARKUI_VERTICAL_ALIGNMENT_BOTTOM  | 底部对齐。  |


### ArkUI_Visibility

```
enum ArkUI_Visibility
```
**描述：**

控制组件的显隐枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_VISIBILITY_VISIBLE  | 显示。  |
| ARKUI_VISIBILITY_HIDDEN  | 隐藏，但参与布局进行占位。  |
| ARKUI_VISIBILITY_NONE  | 隐藏，但不参与布局，不进行占位。  |


### ArkUI_WaterFlowLayoutMode

```
enum ArkUI_WaterFlowLayoutMode
```
**描述：**

定义WaterFlow组件布局模式枚举值。

**起始版本：** 18

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_WATER_FLOW_LAYOUT_MODE_ALWAYS_TOP_DOWN  | 从上到下布局。列数切换场景需要从第一个FlowItem开始布局到当前显示的FlowItem。  |
| ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW  | 移动窗口布局。列数切换场景只重新布局当前显示范围到FlowItem，手指向下滑动再布局从上方进入显示范围的FlowItem。  |


### ArkUI_WordBreak

```
enum ArkUI_WordBreak
```
**描述：**

定义文本断行规则。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_WORD_BREAK_NORMAL  | CJK(中文、日文、韩文)文本可以在任意2个字符间断行，而Non-CJK文本（如英文等）只能在空白符处断行。  |
| ARKUI_WORD_BREAK_BREAK_ALL  | 对于Non-CJK的文本，可在任意2个字符间断行。CJK(中文、日文、韩文)文本可以在任意2个字符间断行。  |
| ARKUI_WORD_BREAK_BREAK_WORD  | 对于Non-CJK的文本可在任意2个字符间断行，一行文本中有断行破发点（如空白符）时，优先按破发点换行。 CJK(中文、日文、韩文)文本可以在任意2个字符间断行  |
| ARKUI_WORD_BREAK_HYPHENATION  | 对于Non-CJK的文本，可以按照音节断行。对于CJK的文本，换行效果与NORMAL效果保持一致。<br/>起始版本：18  |


### ArkUI_XComponentType

```
enum ArkUI_XComponentType
```
**描述：**

定义XComponent类型枚举值。

**起始版本：** 12

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_XCOMPONENT_TYPE_SURFACE  | 用于EGL/OpenGLES和媒体数据写入，开发者定制绘制内容单独显示在屏幕上。  |
| ARKUI_XCOMPONENT_TYPE_TEXTURE  | 用于EGL/OpenGLES和媒体数据写入，开发者定制绘制内容和XComponent组件内容合成后展示在屏幕上。  |

### ArkUI_KeyboardAppearance

```
enum ArkUI_KeyboardAppearance
```
**描述：**

定义输入框拉起的键盘样式。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE   | 默认模式，不使用沉浸式样式。  |
| ARKUI_KEYBOARD_APPEARANCE_IMMERSIVE   | 沉浸式模式，由系统决定采用的样式。  |
| ARKUI_KEYBOARD_APPEARANCE_LIGHT_IMMERSIVE   | 浅色沉浸式样式。  |
| ARKUI_KEYBOARD_APPEARANCE_DARK_IMMERSIVE   | 深色沉浸式样式。  |

### ArkUI_KeyboardAvoidMode

```
enum ArkUI_KeyboardAvoidMode
```
**描述：**

设置弹窗避让键盘模式。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_KEYBOARD_AVOID_MODE_DEFAULT   | 默认避让软键盘并在到达极限高度之后进行高度压缩。  |
| ARKUI_KEYBOARD_AVOID_MODE_NONE   | 不避让软键盘。  |

### ArkUI_HoverModeAreaType

```
enum ArkUI_HoverModeAreaType
```
**描述：**

设置悬停态下弹窗默认展示区域。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_HOVER_MODE_AREA_TYPE_TOP   | 上半屏。  |
| ARKUI_HOVER_MODE_AREA_TYPE_BOTTOM   | 下半屏。  |

### ArkUI_ExpandMode

```
enum ArkUI_ExpandMode
```
**描述：**

定义子节点展开模式枚举值。

**起始版本：** 15

| 枚举值 | 描述 |
| -------- | -------- |
| ARKUI_NOT_EXPAND   | 不展开。  |
| ARKUI_EXPAND   | 展开。  |
| ARKUI_LAZY_EXPAND   | 懒展开，按需展开当前节点的子节点。  |

### ArkUI_UIState

```
enum ArkUI_UIState
```
**描述：**

组件的UI状态枚举，用于处理状态样式。

**起始版本：** 20

| 枚举值 | 描述 |
| -------- | -------- |
| UI_STATE_NORMAL | 正常状态。 |
| UI_STATE_PRESSED | 按压状态。 |
| UI_STATE_FOCUSED | 获焦状态。 |
| UI_STATE_DISABLED | 禁用状态。 |
| UI_STATE_SELECTED | 选中状态。此状态仅由某些特定类型的组件支持，分别是Checkbox、Radio、Toggle、List、Grid和MenuItem。 |

### ArkUI_FocusWrapMode

```
enum ArkUI_FocusWrapMode
```
**描述：**

组件走焦换行规则。

**起始版本：** 20

| 枚举值 | 描述 |
| -------- | -------- |
| FOCUS_WRAP_MODE_DEFAULT | 默认规则，使用方向键走焦不换行。 |
| FOCUS_WRAP_WITH_ARROW | 使用方向键走焦自动换行。 |

## 函数说明


### OH_ArkUI_AccessibilityState_Create()

```
ArkUI_AccessibilityState* OH_ArkUI_AccessibilityState_Create (void )
```
**描述：**

创建无障碍状态。

**起始版本：** 12

**返回：**

无障碍状态对象指针。如果对象返回空指针，表示创建失败，失败的可能原因是应用地址空间满。


### OH_ArkUI_AccessibilityState_Dispose()

```
void OH_ArkUI_AccessibilityState_Dispose (ArkUI_AccessibilityState * state)
```
**描述：**

销毁无障碍状态指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| state | 无障碍状态对象指针。  |


### OH_ArkUI_AccessibilityState_GetCheckedState()

```
int32_t OH_ArkUI_AccessibilityState_GetCheckedState (ArkUI_AccessibilityState * state)
```
**描述：**

获取无障碍状态复选框状态。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| state | 无障碍状态对象指针。  |

**返回：**

复选框状态，参数类型[ArkUI_AccessibilityCheckedState](#arkui_accessibilitycheckedstate), 默认值：ARKUI_ACCESSIBILITY_UNCHECKED; 若函数参数异常，返回默认值。


### OH_ArkUI_AccessibilityState_IsDisabled()

```
int32_t OH_ArkUI_AccessibilityState_IsDisabled (ArkUI_AccessibilityState * state)
```
**描述：**

获取无障碍状态是否禁用。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| state | 无障碍状态对象指针。  |

**返回：**

是否禁用， 1表示禁用，0表示未禁用，默认为0; 若state为空，返回默认值。


### OH_ArkUI_AccessibilityState_IsSelected()

```
int32_t OH_ArkUI_AccessibilityState_IsSelected (ArkUI_AccessibilityState * state)
```
**描述：**

获取无障碍状态是否选中。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| state | 无障碍状态对象指针。  |

**返回：**

是否被选中， 1表示选中，0表示未选中，默认为0; 若state为空，返回默认值。


### OH_ArkUI_AccessibilityState_SetCheckedState()

```
void OH_ArkUI_AccessibilityState_SetCheckedState (ArkUI_AccessibilityState * state, int32_t checkedState )
```
**描述：**

设置无障碍状态复选框状态。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| state | 无障碍状态对象指针。  |
| checkedState | 复选框状态，参数类型[ArkUI_AccessibilityCheckedState](#arkui_accessibilitycheckedstate), 默认值：ARKUI_ACCESSIBILITY_UNCHECKED。  |


### OH_ArkUI_AccessibilityState_SetDisabled()

```
void OH_ArkUI_AccessibilityState_SetDisabled (ArkUI_AccessibilityState * state, int32_t isDisabled )
```
**描述：**

设置无障碍状态是否禁用。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| state | 无障碍状态对象指针。  |
| isDisabled | 无障碍状态是否禁用， 1表示禁用，0表示不禁用，默认为0。  |


### OH_ArkUI_AccessibilityState_SetSelected()

```
void OH_ArkUI_AccessibilityState_SetSelected (ArkUI_AccessibilityState * state, int32_t isSelected )
```
**描述：**

设置无障碍状态是否选中。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| state | 无障碍状态对象指针。  |
| isSelected | 是否被选中， 1表示选中，0表示未选中，默认为0。  |


### OH_ArkUI_AccessibilityValue_Create()

```
ArkUI_AccessibilityValue* OH_ArkUI_AccessibilityValue_Create (void )
```
**描述：**

创建无障碍信息。

**起始版本：** 12

**返回：**

无障碍信息对象指针。


### OH_ArkUI_AccessibilityValue_Dispose()

```
void OH_ArkUI_AccessibilityValue_Dispose (ArkUI_AccessibilityValue * value)
```
**描述：**

销毁无障碍信息指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| state | 无障碍信息对象指针。  |


### OH_ArkUI_AccessibilityValue_GetCurrent()

```
int32_t OH_ArkUI_AccessibilityValue_GetCurrent (ArkUI_AccessibilityValue * value)
```
**描述：**

获取无障碍当前值信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| value | 无障碍信息对象指针。  |

**返回：**

基于范围组件的当前值，默认为-1；若函数参数异常，返回-1。


### OH_ArkUI_AccessibilityValue_GetMax()

```
int32_t OH_ArkUI_AccessibilityValue_GetMax (ArkUI_AccessibilityValue * value)
```
**描述：**

获取无障碍最大值信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| value | 无障碍信息对象指针。  |

**返回：**

基于范围组件的最大值，默认为-1；若函数参数异常，返回-1。


### OH_ArkUI_AccessibilityValue_GetMin()

```
int32_t OH_ArkUI_AccessibilityValue_GetMin (ArkUI_AccessibilityValue * value)
```
**描述：**

获取无障碍最小值信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| value | 无障碍信息对象指针。  |

**返回：**

基于范围组件的最小值，默认为-1；若函数参数异常，返回-1。


### OH_ArkUI_AccessibilityValue_GetText()

```
const char* OH_ArkUI_AccessibilityValue_GetText (ArkUI_AccessibilityValue * value)
```
**描述：**

获取无障碍文本描述信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| value | 无障碍信息对象指针。  |

**返回：**

组件的文本描述信息，默认为空字符串；若函数参数异常，返回空指针。


### OH_ArkUI_AccessibilityValue_SetCurrent()

```
void OH_ArkUI_AccessibilityValue_SetCurrent (ArkUI_AccessibilityValue * value, int32_t current )
```
**描述：**

设置无障碍当前值信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| value | 无障碍信息对象指针。  |
| current | 基于范围组件的当前值，默认为-1。  |


### OH_ArkUI_AccessibilityValue_SetMax()

```
void OH_ArkUI_AccessibilityValue_SetMax (ArkUI_AccessibilityValue * value, int32_t max )
```
**描述：**

设置无障碍最大值信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| value | 无障碍信息对象指针。  |
| max | 基于范围组件的最大值，默认为-1。  |


### OH_ArkUI_AccessibilityValue_SetMin()

```
void OH_ArkUI_AccessibilityValue_SetMin (ArkUI_AccessibilityValue * value, int32_t min )
```
**描述：**

设置无障碍最小值信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| value | 无障碍信息对象指针。  |
| min | 基于范围组件的最小值，默认为-1。  |


### OH_ArkUI_AccessibilityValue_SetText()

```
void OH_ArkUI_AccessibilityValue_SetText (ArkUI_AccessibilityValue * value, const char * text )
```
**描述：**

设置无障碍文本描述信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| value | 无障碍信息对象指针。  |
| text | 组件的文本描述信息，默认为空字符串。  |


### OH_ArkUI_ActiveChildrenInfo_Destroy()

```
void OH_ArkUI_ActiveChildrenInfo_Destroy (ArkUI_ActiveChildrenInfo * handle)
```
**描述：**

销毁ActiveChildrenInfo实例。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 要销毁的ActiveChildrenInfo实例。  |


### OH_ArkUI_ActiveChildrenInfo_GetCount()

```
int32_t OH_ArkUI_ActiveChildrenInfo_GetCount (ArkUI_ActiveChildrenInfo * handle)
```
**描述：**

获取ActiveChildrenInfo结构体内的节点数量。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 要获取信息的ActiveChildrenInfo实例。  |

**返回：**

子节点数量，默认值 0。


### OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex()

```
ArkUI_NodeHandle OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex (ArkUI_ActiveChildrenInfo * handle, int32_t index )
```
**描述：**

获取ActiveChildrenInfo结构体的下标为index的子节点。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 要获取信息的ActiveChildrenInfo实例。  |
| index | 子节点的下标。  |

**返回：**

下标对应的子节点指针，异常时返回nullptr。


### OH_ArkUI_AlignmentRuleOption_Create()

```
ArkUI_AlignmentRuleOption* OH_ArkUI_AlignmentRuleOption_Create ()
```
**描述：**

创建相对容器中子组件的对齐规则信息。

**起始版本：** 12

**返回：**

对齐规则信息。


### OH_ArkUI_AlignmentRuleOption_Dispose()

```
void OH_ArkUI_AlignmentRuleOption_Dispose (ArkUI_AlignmentRuleOption * option)
```
**描述：**

销毁相对容器中子组件的对齐规则信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |


### OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal()

```
float OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取水平方向上的bias值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

水平方向上的bias值。


### OH_ArkUI_AlignmentRuleOption_GetBiasVertical()

```
float OH_ArkUI_AlignmentRuleOption_GetBiasVertical (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取垂直方向上的bias值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

垂直方向上的bias值。


### OH_ArkUI_AlignmentRuleOption_GetBottomAlignment()

```
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetBottomAlignment (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取底部对齐的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

底部对齐的参数的对齐方式。


### OH_ArkUI_AlignmentRuleOption_GetBottomId()

```
const char* OH_ArkUI_AlignmentRuleOption_GetBottomId (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取底部对齐的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

底部对齐的参数的id。


### OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal()

```
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取横向居中对齐方式的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

横向居中对齐方式的参数的对齐方式。


### OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical()

```
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取纵向居中对齐方式的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

纵向居中对齐方式的参数的对齐方式。


### OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal()

```
const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取横向居中对齐方式的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

横向居中对齐方式的参数的id。


### OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical()

```
const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取纵向居中对齐方式的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

纵向居中对齐方式的参数的id。


### OH_ArkUI_AlignmentRuleOption_GetEndAlignment()

```
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetEndAlignment (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取右对齐参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

右对齐参数的对齐方式。


### OH_ArkUI_AlignmentRuleOption_GetEndId()

```
const char* OH_ArkUI_AlignmentRuleOption_GetEndId (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取右对齐参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

右对齐参数id。


### OH_ArkUI_AlignmentRuleOption_GetStartAlignment()

```
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetStartAlignment (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取左对齐参数的对齐方式。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

参数的对齐方式。


### OH_ArkUI_AlignmentRuleOption_GetStartId()

```
const char* OH_ArkUI_AlignmentRuleOption_GetStartId (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取左对齐参数的Id。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

锚点的组件的id值。


### OH_ArkUI_AlignmentRuleOption_GetTopAlignment()

```
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetTopAlignment (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取顶部对齐的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

顶部对齐的参数的对齐方式。


### OH_ArkUI_AlignmentRuleOption_GetTopId()

```
const char* OH_ArkUI_AlignmentRuleOption_GetTopId (ArkUI_AlignmentRuleOption * option)
```
**描述：**

获取顶部对齐的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |

**返回：**

顶部对齐的参数id。


### OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal()

```
void OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal (ArkUI_AlignmentRuleOption * option, float horizontal )
```
**描述：**

设置组件在锚点约束下的水平方向上偏移参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |
| horizontal | 水平方向上的bias值。  |


### OH_ArkUI_AlignmentRuleOption_SetBiasVertical()

```
void OH_ArkUI_AlignmentRuleOption_SetBiasVertical (ArkUI_AlignmentRuleOption * option, float vertical )
```
**描述：**

设置组件在锚点约束下的垂直方向上偏移参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |
| horizontal | 垂直方向上的bias值。  |


### OH_ArkUI_AlignmentRuleOption_SetBottom()

```
void OH_ArkUI_AlignmentRuleOption_SetBottom (ArkUI_AlignmentRuleOption * option, const char * id, ArkUI_VerticalAlignment alignment )
```
**描述：**

设置底部对齐的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |
| id | 锚点的组件的id值。  |
| value | 相对于锚点组件的对齐方式。  |


### OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal()

```
void OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal (ArkUI_AlignmentRuleOption * option, const char * id, ArkUI_HorizontalAlignment alignment )
```
**描述：**

设置横向居中对齐方式的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |
| id | 锚点的组件的id值。  |
| value | 相对于锚点组件的对齐方式  |


### OH_ArkUI_AlignmentRuleOption_SetCenterVertical()

```
void OH_ArkUI_AlignmentRuleOption_SetCenterVertical (ArkUI_AlignmentRuleOption * option, const char * id, ArkUI_VerticalAlignment alignment )
```
**描述：**

设置纵向居中对齐方式的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |
| id | 锚点的组件的id值。  |
| value | 相对于锚点组件的对齐方式。  |


### OH_ArkUI_AlignmentRuleOption_SetEnd()

```
void OH_ArkUI_AlignmentRuleOption_SetEnd (ArkUI_AlignmentRuleOption * option, const char * id, ArkUI_HorizontalAlignment alignment )
```
**描述：**

设置右对齐参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |
| id | 锚点的组件的id值。  |
| value | 相对于锚点组件的对齐方式。  |


### OH_ArkUI_AlignmentRuleOption_SetStart()

```
void OH_ArkUI_AlignmentRuleOption_SetStart (ArkUI_AlignmentRuleOption * option, const char * id, ArkUI_HorizontalAlignment alignment )
```
**描述：**

设置左对齐参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |
| id | 锚点的组件的id值。  |
| value | 相对于锚点组件的对齐方式。  |


### OH_ArkUI_AlignmentRuleOption_SetTop()

```
void OH_ArkUI_AlignmentRuleOption_SetTop (ArkUI_AlignmentRuleOption * option, const char * id, ArkUI_VerticalAlignment alignment )
```
**描述：**

设置顶部对齐的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 相对容器中子组件的对齐规则信息。  |
| id | 锚点的组件的id值。  |
| value | 相对于锚点组件的对齐方式。  |


### OH_ArkUI_AllowNodeAllDropDataTypes()

```
int32_t OH_ArkUI_AllowNodeAllDropDataTypes (ArkUI_NodeHandle node)
```
**描述：**

配置组件允许接受任意数据类型，该接口会重置通过[OH_ArkUI_SetNodeAllowedDropDataTypes](#oh_arkui_setnodealloweddropdatatypes)配置的数据类型。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 组件节点指针。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimateOption_Create()

```
ArkUI_AnimateOption* OH_ArkUI_AnimateOption_Create ()
```
**描述：**

创建动画效果参数。

**起始版本：** 12

**返回：**

新的动画效果参数指针。


### OH_ArkUI_AnimateOption_Dispose()

```
void OH_ArkUI_AnimateOption_Dispose (ArkUI_AnimateOption * option)
```
**描述：**

销毁动画效果参数指针。

**起始版本：** 12


### OH_ArkUI_AnimateOption_GetCurve()

```
ArkUI_AnimationCurve OH_ArkUI_AnimateOption_GetCurve (ArkUI_AnimateOption * option)
```
**描述：**

获取动画曲线。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |

**返回：**

动画曲线。


### OH_ArkUI_AnimateOption_GetDelay()

```
int32_t OH_ArkUI_AnimateOption_GetDelay (ArkUI_AnimateOption * option)
```
**描述：**

获取动画延迟播放时间，单位为ms(毫秒)。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |

**返回：**

动画延迟播放时间。


### OH_ArkUI_AnimateOption_GetDuration()

```
uint32_t OH_ArkUI_AnimateOption_GetDuration (ArkUI_AnimateOption * option)
```
**描述：**

获取动画持续时间，单位为ms(毫秒)。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |

**返回：**

持续时间。


### OH_ArkUI_AnimateOption_GetExpectedFrameRateRange()

```
ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimateOption_GetExpectedFrameRateRange (ArkUI_AnimateOption * option)
```
**描述：**

获取动画的期望帧率。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |

**返回：**

动画的期望帧率。


### OH_ArkUI_AnimateOption_GetICurve()

```
ArkUI_CurveHandle OH_ArkUI_AnimateOption_GetICurve (ArkUI_AnimateOption * option)
```
**描述：**

获取动画的动画曲线。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |

**返回：**

动画的动画曲线。


### OH_ArkUI_AnimateOption_GetIterations()

```
int32_t OH_ArkUI_AnimateOption_GetIterations (ArkUI_AnimateOption * option)
```
**描述：**

获取动画播放次数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |

**返回：**

动画播放次数。

### OH_ArkUI_AnimateOption_GetPlayMode()

```
ArkUI_AnimationPlayMode OH_ArkUI_AnimateOption_GetPlayMode (ArkUI_AnimateOption * option)
```
**描述：**

获取动画播放模式。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |

**返回：**

动画播放模式。


### OH_ArkUI_AnimateOption_GetTempo()

```
float OH_ArkUI_AnimateOption_GetTempo (ArkUI_AnimateOption * option)
```
**描述：**

获取动画播放速度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |

**返回：**

动画播放速度。


### OH_ArkUI_AnimateOption_SetCurve()

```
void OH_ArkUI_AnimateOption_SetCurve (ArkUI_AnimateOption * option, ArkUI_AnimationCurve value )
```
**描述：**

设置动画曲线。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |
| value | 动画曲线。默认值：ARKUI_CURVE_LINEAR。  |


### OH_ArkUI_AnimateOption_SetDelay()

```
void OH_ArkUI_AnimateOption_SetDelay (ArkUI_AnimateOption * option, int32_t value )
```
**描述：**

设置动画延迟播放时间。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |
| value | 动画延迟播放时间。  |


### OH_ArkUI_AnimateOption_SetDuration()

```
void OH_ArkUI_AnimateOption_SetDuration (ArkUI_AnimateOption * option, int32_t value )
```
**描述：**

设置动画持续时间。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |
| value | 持续时间，单位为ms(毫秒)。  |


### OH_ArkUI_AnimateOption_SetExpectedFrameRateRange()

```
void OH_ArkUI_AnimateOption_SetExpectedFrameRateRange (ArkUI_AnimateOption * option, ArkUI_ExpectedFrameRateRange * value )
```
**描述：**

设置动画的期望帧率。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |
| value | 动画的期望帧率。  |


### OH_ArkUI_AnimateOption_SetICurve()

```
void OH_ArkUI_AnimateOption_SetICurve (ArkUI_AnimateOption * option, ArkUI_CurveHandle value )
```
**描述：**

设置动画的动画曲线。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |
| value | 动画曲线参数。  |

**注解：**

此方法优于OH_ArkUI_AnimateOption_SetCurve设置的值。


### OH_ArkUI_AnimateOption_SetIterations()

```
void OH_ArkUI_AnimateOption_SetIterations (ArkUI_AnimateOption * option, int32_t value )
```
**描述：**

设置动画播放次数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |
| value | 动画播放次数。  |


### OH_ArkUI_AnimateOption_SetPlayMode()

```
void OH_ArkUI_AnimateOption_SetPlayMode (ArkUI_AnimateOption * option, ArkUI_AnimationPlayMode value )
```
**描述：**

设置动画播放模式。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |
| value | 动画播放模式。  |


### OH_ArkUI_AnimateOption_SetTempo()

```
void OH_ArkUI_AnimateOption_SetTempo (ArkUI_AnimateOption * option, float value )
```
**描述：**

设置动画播放速度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 动画效果参数。  |
| value | 动画播放速度。  |


### OH_ArkUI_Animator_Cancel()

```
int32_t OH_ArkUI_Animator_Cancel (ArkUI_AnimatorHandle animatorHandle)
```
**描述：**

取消animator动画。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| animatorHandle | animator动画对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_Animator_Finish()

```
int32_t OH_ArkUI_Animator_Finish (ArkUI_AnimatorHandle animatorHandle)
```
**描述：**

结束animator动画。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| animatorHandle | animator动画对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_Animator_Pause()

```
int32_t OH_ArkUI_Animator_Pause (ArkUI_AnimatorHandle animatorHandle)
```
**描述：**

暂停animator动画。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| animatorHandle | animator动画对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_Animator_Play()

```
int32_t OH_ArkUI_Animator_Play (ArkUI_AnimatorHandle animatorHandle)
```
**描述：**

启动animator动画。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| animatorHandle | animator动画对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_Animator_ResetAnimatorOption()

```
int32_t OH_ArkUI_Animator_ResetAnimatorOption (ArkUI_AnimatorHandle animatorHandle, ArkUI_AnimatorOption * option )
```
**描述：**

更新animator动画。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| animatorHandle | animator动画对象。  |
| option | animator动画参数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_Animator_Reverse()

```
int32_t OH_ArkUI_Animator_Reverse (ArkUI_AnimatorHandle animatorHandle)
```
**描述：**

以相反的顺序播放animator动画。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| animatorHandle | animator动画对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorEvent_GetUserData()

```
void* OH_ArkUI_AnimatorEvent_GetUserData (ArkUI_AnimatorEvent * event)
```
**描述：**

获取动画事件对象中的用户自定义对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 动画事件对象。  |

**返回：**

用户自定义对象。


### OH_ArkUI_AnimatorOnFrameEvent_GetUserData()

```
void* OH_ArkUI_AnimatorOnFrameEvent_GetUserData (ArkUI_AnimatorOnFrameEvent * event)
```
**描述：**

获取动画事件对象中的用户自定义对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 动画事件对象。  |

**返回：**

用户自定义对象。


### OH_ArkUI_AnimatorOnFrameEvent_GetValue()

```
float OH_ArkUI_AnimatorOnFrameEvent_GetValue (ArkUI_AnimatorOnFrameEvent * event)
```
**描述：**

获取动画事件对象中的当前进度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 动画事件对象。  |

**返回：**

动画进度。


### OH_ArkUI_AnimatorOption_Create()

```
ArkUI_AnimatorOption* OH_ArkUI_AnimatorOption_Create (int32_t keyframeSize)
```
**描述：**

创建animator动画对象参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| keyframeSize | 关键帧个数。  |

**注解：**

keyframeSize大于0时，动画插值起点默认是0，动画插值终点模式值是1。不支持设置。

**返回：**

animator动画对象参数指针。


### OH_ArkUI_AnimatorOption_Dispose()

```
void OH_ArkUI_AnimatorOption_Dispose (ArkUI_AnimatorOption * option)
```
**描述：**

销毁animator动画对象参数。

**起始版本：** 12


### OH_ArkUI_AnimatorOption_GetBegin()

```
float OH_ArkUI_AnimatorOption_GetBegin (ArkUI_AnimatorOption * option)
```
**描述：**

获取animator动画插值起点。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |

**返回：**

动画插值起点。


### OH_ArkUI_AnimatorOption_GetCurve()

```
ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetCurve (ArkUI_AnimatorOption * option)
```
**描述：**

获取animator动画插值曲线。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |

**返回：**

动画插值曲线。


### OH_ArkUI_AnimatorOption_GetDelay()

```
int32_t OH_ArkUI_AnimatorOption_GetDelay (ArkUI_AnimatorOption * option)
```
**描述：**

获取animator动画延时播放时长。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |

**返回：**

动画延时播放时长，单位毫秒。


### OH_ArkUI_AnimatorOption_GetDirection()

```
ArkUI_AnimationDirection OH_ArkUI_AnimatorOption_GetDirection (ArkUI_AnimatorOption * option)
```
**描述：**

获取animator动画播放方向。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |

**返回：**

动画播放方向。


### OH_ArkUI_AnimatorOption_GetDuration()

```
int32_t OH_ArkUI_AnimatorOption_GetDuration (ArkUI_AnimatorOption * option)
```
**描述：**

获取animator动画播放的时长。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |

**返回：**

动画播放的时长，单位毫秒。


### OH_ArkUI_AnimatorOption_GetEnd()

```
float OH_ArkUI_AnimatorOption_GetEnd (ArkUI_AnimatorOption * option)
```
**描述：**

获取animator动画插值终点。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |

**返回：**

动画插值终点。


### OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange()

```
ArkUI_ExpectedFrameRateRange* OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange (ArkUI_AnimatorOption * option)
```
**描述：**

获取animator动画期望的帧率范围。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |

**返回：**

期望的帧率范围对象指针。


### OH_ArkUI_AnimatorOption_GetFill()

```
ArkUI_AnimationFillMode OH_ArkUI_AnimatorOption_GetFill (ArkUI_AnimatorOption * option)
```
**描述：**

获取animator动画执行后是否恢复到初始状态。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |

**返回：**

执行后是否恢复到初始状态。


### OH_ArkUI_AnimatorOption_GetIterations()

```
int32_t OH_ArkUI_AnimatorOption_GetIterations (ArkUI_AnimatorOption * option)
```
**描述：**

获取animator动画播放次数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画动画参数。  |

**返回：**

动画播放次数。


### OH_ArkUI_AnimatorOption_GetKeyframeCurve()

```
ArkUI_CurveHandle OH_ArkUI_AnimatorOption_GetKeyframeCurve (ArkUI_AnimatorOption * option, int32_t index )
```
**描述：**

获取animator动画关键帧动画插值曲线。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| index | 关键帧的索引值。  |

**返回：**

动画插值曲线。


### OH_ArkUI_AnimatorOption_GetKeyframeTime()

```
float OH_ArkUI_AnimatorOption_GetKeyframeTime (ArkUI_AnimatorOption * option, int32_t index )
```
**描述：**

获取animator动画关键帧时间。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| index | 关键帧的索引值。  |

**返回：**

关键帧时间。


### OH_ArkUI_AnimatorOption_GetKeyframeValue()

```
float OH_ArkUI_AnimatorOption_GetKeyframeValue (ArkUI_AnimatorOption * option, int32_t index )
```
**描述：**

获取animator动画关键帧数值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| index | 关键帧的索引值。  |

**返回：**

关键帧数值。


### OH_ArkUI_AnimatorOption_RegisterOnCancelCallback()

```
int32_t OH_ArkUI_AnimatorOption_RegisterOnCancelCallback (ArkUI_AnimatorOption * option, void * userData, void(*)(ArkUI_AnimatorEvent *event) callback )
```
**描述：**

设置animator动画被取消时回调。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |
| userData | 用户自定义参数。  |
| callback | 回调函数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_RegisterOnFinishCallback()

```
int32_t OH_ArkUI_AnimatorOption_RegisterOnFinishCallback (ArkUI_AnimatorOption * option, void * userData, void(*)(ArkUI_AnimatorEvent *event) callback )
```
**描述：**

设置animator动画完成时回调。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |
| userData | 用户自定义参数。  |
| callback | 回调函数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_RegisterOnFrameCallback()

```
int32_t OH_ArkUI_AnimatorOption_RegisterOnFrameCallback (ArkUI_AnimatorOption * option, void * userData, void(*)(ArkUI_AnimatorOnFrameEvent *event) callback )
```
**描述：**

设置animator动画接收到帧时回调。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |
| userData | 用户自定义参数。  |
| callback | 回调函数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback()

```
int32_t OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback (ArkUI_AnimatorOption * option, void * userData, void(*)(ArkUI_AnimatorEvent *event) callback )
```
**描述：**

设置animator动画重复时回调。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画参数。  |
| userData | 用户自定义参数。  |
| callback | 回调函数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetBegin()

```
int32_t OH_ArkUI_AnimatorOption_SetBegin (ArkUI_AnimatorOption * option, float value )
```
**描述：**

设置animator动画插值起点。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 动画插值起点。  |

**注解：**

当Animator动画为keyframe动画时，此方法不生效。

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetCurve()

```
int32_t OH_ArkUI_AnimatorOption_SetCurve (ArkUI_AnimatorOption * option, ArkUI_CurveHandle value )
```
**描述：**

设置animator动画插值曲线。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 动画插值曲线。默认值：ARKUI_CURVE_LINEAR。  |

**注解：**

不支持springCurve，springMotion，responsiveSpringMotion，interpolatingSpring customCurve动画曲线。

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetDelay()

```
int32_t OH_ArkUI_AnimatorOption_SetDelay (ArkUI_AnimatorOption * option, int32_t value )
```
**描述：**

设置animator动画延时播放时长，单位毫秒。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 延时播放时长，单位毫秒。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetDirection()

```
int32_t OH_ArkUI_AnimatorOption_SetDirection (ArkUI_AnimatorOption * option, ArkUI_AnimationDirection value )
```
**描述：**

设置animator动画播放方向。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 动画播放方向。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetDuration()

```
int32_t OH_ArkUI_AnimatorOption_SetDuration (ArkUI_AnimatorOption * option, int32_t value )
```
**描述：**

设置animator动画播放的时长，单位毫秒。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 播放的时长，单位毫秒。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetEnd()

```
int32_t OH_ArkUI_AnimatorOption_SetEnd (ArkUI_AnimatorOption * option, float value )
```
**描述：**

设置animator动画插值终点。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 动画插值终点。  |

**注解：**

当Animator动画为keyframe动画时，此方法不生效。

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange()

```
int32_t OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange (ArkUI_AnimatorOption * option, ArkUI_ExpectedFrameRateRange * value )
```
**描述：**

设置animator动画期望的帧率范围。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 期望的帧率范围对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetFill()

```
int32_t OH_ArkUI_AnimatorOption_SetFill (ArkUI_AnimatorOption * option, ArkUI_AnimationFillMode value )
```
**描述：**

设置animator动画执行后是否恢复到初始状态。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 动画执行后是否恢复到初始状态。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetIterations()

```
int32_t OH_ArkUI_AnimatorOption_SetIterations (ArkUI_AnimatorOption * option, int32_t value )
```
**描述：**

设置animator动画播放次数。设置为0时不播放，设置为-1时无限次播放。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 动画播放次数。  |

**注解：**

设置为除-1外其他负数视为无效取值，无效取值动画默认播放1次。

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetKeyframe()

```
int32_t OH_ArkUI_AnimatorOption_SetKeyframe (ArkUI_AnimatorOption * option, float time, float value, int32_t index )
```
**描述：**

设置animator动画关键帧参数。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| time | 关键帧时间。取值范围：[0, 1], 必须是递增。  |
| value | 关键帧数值。  |
| index | 关键帧的索引值。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AnimatorOption_SetKeyframeCurve()

```
int32_t OH_ArkUI_AnimatorOption_SetKeyframeCurve (ArkUI_AnimatorOption * option, ArkUI_CurveHandle value, int32_t index )
```
**描述：**

设置animator动画关键帧曲线类型。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | animator动画对象参数。  |
| value | 动画插值曲线。  |
| index | 关键帧的索引值。  |

**注解：**

不支持springCurve，springMotion，responsiveSpringMotion，interpolatingSpring customCurve动画曲线

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_BarrierOption_Create()

```
ArkUI_BarrierOption* OH_ArkUI_BarrierOption_Create (int32_t size)
```
**描述：**

创建RelativeContaine容器内的屏障信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| size | 屏障数量。  |

**返回：**

屏障信息。


### OH_ArkUI_BarrierOption_Dispose()

```
void OH_ArkUI_BarrierOption_Dispose (ArkUI_BarrierOption * barrierStyle)
```
**描述：**

销毁屏障信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| barrierStyle | 屏障信息。  |


### OH_ArkUI_BarrierOption_GetDirection()

```
ArkUI_BarrierDirection OH_ArkUI_BarrierOption_GetDirection (ArkUI_BarrierOption * barrierStyle, int32_t index )
```
**描述：**

获取屏障的方向。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| barrierStyle | 辅助线信息。  |
| index | 辅助线索引值。  |

**返回：**

屏障的方向。


### OH_ArkUI_BarrierOption_GetId()

```
const char* OH_ArkUI_BarrierOption_GetId (ArkUI_BarrierOption * barrierStyle, int32_t index )
```
**描述：**

获取屏障的Id。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| barrierStyle | 辅助线信息。  |
| index | 辅助线索引值。  |

**返回：**

屏障的Id。


### OH_ArkUI_BarrierOption_GetReferencedId()

```
const char* OH_ArkUI_BarrierOption_GetReferencedId (ArkUI_BarrierOption * barrierStyle, int32_t index, int32_t referencedIndex )
```
**描述：**

获取屏障的依赖的组件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| barrierStyle | 辅助线信息。  |
| index | 辅助线索引值。  |
| referencedIndex | 依赖的组件Id索引值。  |

**返回：**

屏障的依赖的组件。


### OH_ArkUI_BarrierOption_GetReferencedIdSize()

```
int32_t OH_ArkUI_BarrierOption_GetReferencedIdSize (ArkUI_BarrierOption * barrierStyle, int32_t index )
```
**描述：**

获取屏障的依赖的组件的个数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| barrierStyle | 辅助线信息。  |
| index | 辅助线索引值。  |

**返回：**

屏障的依赖的组件的个数。


### OH_ArkUI_BarrierOption_SetDirection()

```
void OH_ArkUI_BarrierOption_SetDirection (ArkUI_BarrierOption * barrierStyle, ArkUI_BarrierDirection value, int32_t index )
```
**描述：**

设置屏障的方向。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| barrierStyle | 屏障信息。  |
| value | 方向。  |
| index | 屏障索引值。  |


### OH_ArkUI_BarrierOption_SetId()

```
void OH_ArkUI_BarrierOption_SetId (ArkUI_BarrierOption * barrierStyle, const char * value, int32_t index )
```
**描述：**

设置屏障的Id。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| barrierStyle | 屏障信息。  |
| value | id，必须是唯一的并且不可与容器内组件重名。  |
| index | 屏障索引值。  |


### OH_ArkUI_BarrierOption_SetReferencedId()

```
void OH_ArkUI_BarrierOption_SetReferencedId (ArkUI_BarrierOption * barrierStyle, const char * value, int32_t index )
```
**描述：**

设置屏障的依赖的组件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| barrierStyle | 屏障信息。  |
| value | 依赖的组件的Id。  |
| index | 屏障索引值。  |


### OH_ArkUI_ConvertToHtml()

```
const char* OH_ArkUI_ConvertToHtml (ArkUI_StyledString_Descriptor * descriptor)
```
**描述：**

将属性字符串信息转化成html。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| descriptor | 指向ArkUI_StyledString_Descriptor对象的指针。  |

**返回：**

html。该指针由内部管理，在OH_ArkUI_StyledString_Descriptor_Destroy()时释放。


### OH_ArkUI_CreateAsymmetricTransitionEffect()

```
ArkUI_TransitionEffect* OH_ArkUI_CreateAsymmetricTransitionEffect (ArkUI_TransitionEffect * appear, ArkUI_TransitionEffect * disappear )
```
**描述：**

创建非对称的转场效果对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| appear | 出现的转场效果。  |
| disappear | 消失的转场效果。  |

**注解：**

如不通过asymmetric函数构造TransitionEffect，则表明该效果在组件出现和消失时均生效。

**返回：**

非对称的转场效果对象。如果参数异常返回NULL。


### OH_ArkUI_CreateDragActionWithContext()

```
ArkUI_DragAction* OH_ArkUI_CreateDragActionWithContext (ArkUI_ContextHandle uiContext)
```
**描述：**

创建一个拖拽操作对象，该对象需与一个UI实例相关联，可通过传入一个UI实例指针来关联。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| uiContext | UI实例对象指针。  |

**返回：**

ArkUI_DragAction对象，如果创建失败，则返回空。


### OH_ArkUI_CreateDragActionWithNode()

```
ArkUI_DragAction* OH_ArkUI_CreateDragActionWithNode (ArkUI_NodeHandle node)
```
**描述：**

创建一个拖拽操作对象，该对象需与一个UI实例相关联，可通过传入一个当前UI实例的某个组件节点来指定。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 组件节点指针。  |

**返回：**

ArkUI_DragAction对象指针，如果创建失败，则返回空。


### OH_ArkUI_CreateDragPreviewOption()

```
ArkUI_DragPreviewOption* OH_ArkUI_CreateDragPreviewOption (void )
```
**描述：**

构建一个ArkUI_DragPreviewOption对象。

**起始版本：** 12

**返回：**

ArkUI_DragPreviewOption对象。


### OH_ArkUI_CreateMovementTransitionEffect()

```
ArkUI_TransitionEffect* OH_ArkUI_CreateMovementTransitionEffect (ArkUI_TransitionEdge move)
```
**描述：**

创建组件平移效果对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| move | 平移类型。  |

**返回：**

组件转场时的平移效果对象。如果参数异常返回NULL。


### OH_ArkUI_CreateOpacityTransitionEffect()

```
ArkUI_TransitionEffect* OH_ArkUI_CreateOpacityTransitionEffect (float opacity)
```
**描述：**

创建组件转场时的透明度效果对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| opacity | 透明度，取值范围： [0, 1]。  |

**注解：**

设置小于0的非法值按0处理，大于1的非法值按1处理。

**返回：**

组件转场时的透明度效果对象。


### OH_ArkUI_CreateRotationTransitionEffect()

```
ArkUI_TransitionEffect* OH_ArkUI_CreateRotationTransitionEffect (ArkUI_RotationOptions * rotate)
```
**描述：**

创建组件转场时的旋转效果对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| rotate | 组件转场时的旋转参数对象。  |

**返回：**

组件转场时的旋转效果对象。如果参数异常返回NULL。


### OH_ArkUI_CreateScaleTransitionEffect()

```
ArkUI_TransitionEffect* OH_ArkUI_CreateScaleTransitionEffect (ArkUI_ScaleOptions * scale)
```
**描述：**

创建组件转场时的缩放效果对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| scale | 组件转场时的缩放参数对象。  |

**返回：**

组件转场时的缩放效果对象。如果参数异常返回NULL。


### OH_ArkUI_CreateTranslationTransitionEffect()

```
ArkUI_TransitionEffect* OH_ArkUI_CreateTranslationTransitionEffect (ArkUI_TranslationOptions * translate)
```
**描述：**

创建组件转场时的平移效果对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| translate | 组件转场时的平移参数对象。  |

**返回：**

组件转场时的平移效果对象。如果参数异常返回NULL。

### OH_ArkUI_Curve_CreateCubicBezierCurve()

```
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCubicBezierCurve (float x1, float y1, float x2, float y2 )
```
**描述：**

构造三阶贝塞尔曲线对象。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| x1 | 确定贝塞尔曲线第一点横坐标，取值范围：[0, 1]。 设置的值小于0时，按0处理；设置的值大于1时，按1处理。  |
| y1 | 确定贝塞尔曲线第一点纵坐标。  |
| x2 | 确定贝塞尔曲线第二点横坐标，取值范围：[0, 1]。 设置的值小于0时，按0处理；设置的值大于1时，按1处理。  |
| y2 | 确定贝塞尔曲线第二点纵坐标。  |

**返回：**

曲线的插值对象指针。如果参数异常返回NULL。


### OH_ArkUI_Curve_CreateCurveByType()

```
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCurveByType (ArkUI_AnimationCurve curve)
```
**描述：**

插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| curve | 曲线类型。  |

**返回：**

曲线的插值对象指针。如果参数异常返回NULL。


### OH_ArkUI_Curve_CreateCustomCurve()

```
ArkUI_CurveHandle OH_ArkUI_Curve_CreateCustomCurve (void * userData, float(*)(float fraction, void *userdata) interpolate )
```
**描述：**

构造自定义曲线对象。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| userData | 用户自定义数据。  |
| interpolate | 用户自定义的插值回调函数。fraction为动画开始时的插值输入x值。取值范围：[0,1] 返回值为曲线的y值。取值范围：[0,1]。 fraction等于0时，返回值为0对应动画起点，返回不为0，动画在起点处有跳变效果。 fraction等于1时，返回值为1对应动画终点，返回值不为1将导致动画的终值不是状态变量的值， 出现大于或者小于状态变量值，再跳变到状态变量值的效果。  |

**返回：**

曲线的插值对象指针。如果参数异常返回NULL。


### OH_ArkUI_Curve_CreateInterpolatingSpring()

```
ArkUI_CurveHandle OH_ArkUI_Curve_CreateInterpolatingSpring (float velocity, float mass, float stiffness, float damping )
```
**描述：**

构造插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| velocity | 初始速度。外部因素对弹性动效产生的影响参数， 目的是保证对象从之前的运动状态平滑地过渡到弹性动效。该速度是归一化速度， 其值等于动画开始时的实际速度除以动画属性改变值。  |
| mass | 质量。弹性系统的受力对象，会对弹性系统产生惯性影响。 质量越大，震荡的幅度越大，恢复到平衡位置的速度越慢。  |
| stiffness | 刚度。表示物体抵抗施加的力而形变的程度。 刚度越大，抵抗变形的能力越强，恢复到平衡位置的速度越快。  |
| damping | 阻尼。用于描述系统在受到扰动后震荡及衰减的情形。 阻尼越大，弹性运动的震荡次数越少、震荡幅度越小。  |

**注解：**

动画时间由曲线参数决定，不受animation、animateTo中的duration参数控制。

**返回：**

曲线的插值对象指针。如果参数异常返回NULL。


### OH_ArkUI_Curve_CreateResponsiveSpringMotion()

```
ArkUI_CurveHandle OH_ArkUI_Curve_CreateResponsiveSpringMotion (float response, float dampingFraction, float overlapDuration )
```
**描述：**

构造弹性跟手动画曲线对象，是springMotion的一种特例，仅默认参数不同，可与springMotion混合使用。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| response | 弹簧自然振动周期，决定弹簧复位的速度。  |
| dampingFraction | 阻尼系数。 大于0小于1的值为欠阻尼，运动过程中会超出目标值； 等于1为临界阻尼； 大于1为过阻尼，运动过程中逐渐趋于目标值。  |
| overlapDuration | 弹性动画衔接时长。发生动画继承时，如果前后两个弹性动画response不一致， response参数会在overlapDuration时间内平滑过渡。  |

**注解：**

动画时间由曲线参数决定，不受animation、animateTo中的duration参数控制。

**返回：**

曲线的插值对象指针。如果参数异常返回NULL。


### OH_ArkUI_Curve_CreateSpringCurve()

```
ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringCurve (float velocity, float mass, float stiffness, float damping )
```
**描述：**

构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受animation、animateTo中的duration参数控制。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| velocity | 初始速度。是由外部因素对弹性动效产生的影响参数， 其目的是保证对象从之前的运动状态平滑的过渡到弹性动效。该速度是归一化速度，其值等于动画开始时的实际速度除以动画属性改变值。  |
| mass | 质量。弹性系统的受力对象，会对弹性系统产生惯性影响。质量越大，震荡的幅度越大，恢复到平衡位置的速度越慢。  |
| stiffness | 刚度。是物体抵抗施加的力而形变的程度。在弹性系统中，刚度越大，抵抗变形的能力越强，恢复到平衡位置的速度就越快。  |
| damping | 阻尼。用于描述系统在受到扰动后震荡及衰减的情形。阻尼越大，弹性运动的震荡次数越少、震荡幅度越小。  |

**返回：**

曲线的插值对象指针。如果参数异常返回NULL。


### OH_ArkUI_Curve_CreateSpringMotion()

```
ArkUI_CurveHandle OH_ArkUI_Curve_CreateSpringMotion (float response, float dampingFraction, float overlapDuration )
```
**描述：**

构造弹性动画曲线对象。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| response | 弹簧自然振动周期，决定弹簧复位的速度。  |
| dampingFraction | 阻尼系数。 大于0小于1的值为欠阻尼，运动过程中会超出目标值； 等于1为临界阻尼； 大于1为过阻尼，运动过程中逐渐趋于目标值。  |
| overlapDuration | 弹性动画衔接时长。发生动画继承时，如果前后两个弹性动画response不一致， response参数会在overlapDuration时间内平滑过渡。  |

**注解：**

动画时间由曲线参数决定，不受animation、animateTo中的duration参数控制。

**返回：**

曲线的插值对象指针。如果参数异常返回NULL。


### OH_ArkUI_Curve_CreateStepsCurve()

```
ArkUI_CurveHandle OH_ArkUI_Curve_CreateStepsCurve (int32_t count, bool end )
```
**描述：**

构造阶梯曲线对象。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| count | 阶梯的数量，需要为正整数，取值范围：[1, +∞)。  |
| end | 在每个间隔的起点或是终点发生阶跃变化， true：在终点发生阶跃变化，false：在起点发生阶跃变化。  |

**返回：**

曲线的插值对象指针。如果参数异常返回NULL。


### OH_ArkUI_Curve_DisposeCurve()

```
void OH_ArkUI_Curve_DisposeCurve (ArkUI_CurveHandle curveHandle)
```
**描述：**

销毁自定义曲线对象。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| curveHandle | 曲线的插值对象指针。  |


### OH_ArkUI_CustomProperty_Destroy()

```
void OH_ArkUI_CustomProperty_Destroy (ArkUI_CustomProperty * handle)
```
**描述：**

销毁CustomProperty实例。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 要销毁的CustomProperty实例。  |


### OH_ArkUI_CustomProperty_GetStringValue()

```
const char* OH_ArkUI_CustomProperty_GetStringValue (ArkUI_CustomProperty * handle)
```
**描述：**

获取自定义属性value信息。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 自定义属性对象指针。  |

**返回：**

自定义属性value信息。


### OH_ArkUI_CustomSpanDrawInfo_Create()

```
ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create (void )
```
**描述：**

创建自定义段落组件绘制信息。

**起始版本：** 12

**返回：**

CustomSpanDrawInfo实例。 如果返回空指针，可能是因为内存不足。


### OH_ArkUI_CustomSpanDrawInfo_Dispose()

```
void OH_ArkUI_CustomSpanDrawInfo_Dispose (ArkUI_CustomSpanDrawInfo * info)
```
**描述：**

销毁自定义段落组件绘制信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 自定义段落组件绘制信息指针。  |


### OH_ArkUI_CustomSpanDrawInfo_GetBaseline()

```
float OH_ArkUI_CustomSpanDrawInfo_GetBaseline (ArkUI_CustomSpanDrawInfo * info)
```
**描述：**

获取自定义段落组件相对于挂载组件的基线偏移量。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 自定义段落组件绘制信息指针。  |

**返回：**

基线偏移量值。若函数参数异常，返回0.0f。 异常返回原因：传入参数验证失败，参数不能为空。

### OH_ArkUI_NodeUtils_GetWindowInfo()

```
int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)
```
**描述：**

获取节点所属的窗口信息。

**起始版本：** 15

**参数：**

| 名称 | 描述 |
| -------- | -------- |
| node | 节点指针。 |
| info | 窗口结构体指针。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。</br >
[ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](_ark_u_i___native_module.md#arkui_errorcode) 节点未挂载到节点树上。</br >

### OH_ArkUI_HostWindowInfo_GetName()

```
const char* OH_ArkUI_HostWindowInfo_GetName(ArkUI_HostWindowInfo* info)
```
**描述：**

获取HostWindowInfo对象中的窗口名称。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | HostWindowInfo对象。 |

**返回：**

HostWindowInfo对象中的窗口名称。 

### OH_ArkUI_HostWindowInfo_Destroy()

```
void OH_ArkUI_HostWindowInfo_Destroy(ArkUI_HostWindowInfo* info)
```
**描述：**

销毁HostWindowInfo对象。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 要销毁的HostWindowInfo对象。 |

### OH_ArkUI_NodeUtils_MoveTo()

```
int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)
```
**描述：**

将节点移动到目标父节点下，作为子节点。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 待移动的节点对象。 |
| target_parent | 目标父节点指针。 |
| index | 转移后的节点下标，如果下标值为非法值，则添加在目标父节点的最后一位。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。</br >

### OH_ArkUI_NodeUtils_GetAttachedNodeHandleById()

```
int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)
```
**描述：**

根据用户id获取目标节点。

**起始版本：** 15

**参数：**

| 名称 | 描述 |
| -------- | -------- |
| id | 目标节点的id。 |
| node | 目标父节点指针。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 方法参数异常。</br >

### OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId()

```
int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)
```
**描述：**

通过uniqueId获取节点。

**起始版本：** 20

**参数：**

| 名称 | 描述 |
| -------- | -------- |
| uniqueId | 目标节点的uniqueId。 |
| node | 目标节点的指针。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 方法参数异常。</br >
[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](_ark_u_i___native_module.md#arkui_errorcode) CAPI初始化错误。</br >

### OH_ArkUI_NodeUtils_GetNodeUniqueId()

```
int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)
```
**描述：**

获取目标节点的uniqueId。

**起始版本：** 20

**参数：**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI节点指针。 |
| uniqueId | 目标节点的uniqueId。组件标识ID只读，且进程内唯一，若该节点存在，返回该节点的Uniqueld值；否则返回-1。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 方法参数异常。</br >
[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](_ark_u_i___native_module.md#arkui_errorcode) CAPI初始化错误。</br >

### OH_ArkUI_NodeUtils_SetCrossLanguageOption()

```
int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```
**描述：**

设置目标节点跨语言设置属性的能力。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点的指针。 |
| option | 跨语言配置类，类型请参考 {@link ArkUI_CrossLanguageOption}。 |

**返回：**

返回错误码。ARKUI_ERROR_CODE_NO_ERROR代表成功，ARKUI_ERROR_CODE_PARAM_INVALID代表函数参数异常。

### OH_ArkUI_NodeUtils_GetCrossLanguageOption()

```
int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```
**描述：**

获取目标节点跨语言设置属性的配置项。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点的指针。 |
| option | 跨语言配置类，类型请参考 {@link ArkUI_CrossLanguageOption}。 |

**返回：**

返回错误码。ARKUI_ERROR_CODE_NO_ERROR代表成功，ARKUI_ERROR_CODE_PARAM_INVALID代表函数参数异常。

### OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand()

```
int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```
**描述：**

获取目标节点在树上的第一个子节点的下标。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点的指针。 |
| index | 子节点的下标值。 |

**返回：**

返回错误码。ARKUI_ERROR_CODE_NO_ERROR代表成功，ARKUI_ERROR_CODE_PARAM_INVALID代表函数参数异常。

### OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand()

```
int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```
**描述：**

获取目标节点在树上的最后一个子节点的下标。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点的指针。 |
| index | 子节点的下标值。 |

**返回：**

返回错误码。ARKUI_ERROR_CODE_NO_ERROR代表成功，ARKUI_ERROR_CODE_PARAM_INVALID代表函数参数异常。

### OH_ArkUI_NodeUtils_GetChildWithExpandMode()

```
int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position,
    ArkUI_NodeHandle* subnode, uint32_t expandMode)
```
**描述：**

用不同的展开模式获取对应下标的子节点。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点的指针。 |
| position | 对应子节点的下标。 |
| subnode | 获取子节点的指针。 |
| expandMode | 节点遍历展开方式，详情请参考[ArkUI_ExpandMode](#arkui_expandmode)。 |

**返回：**

返回错误码。ARKUI_ERROR_CODE_NO_ERROR代表成功，ARKUI_ERROR_CODE_PARAM_INVALID代表函数参数异常。

### OH_ArkUI_CustomSpanDrawInfo_GetLineBottom()

```
float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom (ArkUI_CustomSpanDrawInfo * info)
```
**描述：**

获取自定义段落组件相对于挂载组件的下边距。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 自定义段落组件绘制信息指针。  |

**返回：**

下边距值。若函数参数异常，返回0.0f。 异常返回原因：传入参数验证失败，参数不能为空。


### OH_ArkUI_CustomSpanDrawInfo_GetLineTop()

```
float OH_ArkUI_CustomSpanDrawInfo_GetLineTop (ArkUI_CustomSpanDrawInfo * info)
```
**描述：**

获取自定义段落组件相对于挂载组件的上边距。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 自定义段落组件绘制信息指针。  |

**返回：**

上边距值。若函数参数异常，返回0.0f。 异常返回原因：传入参数验证失败，参数不能为空。


### OH_ArkUI_CustomSpanDrawInfo_GetXOffset()

```
float OH_ArkUI_CustomSpanDrawInfo_GetXOffset (ArkUI_CustomSpanDrawInfo * info)
```
**描述：**

获取自定义段落组件相对于挂载组件的x轴偏移值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 自定义段落组件绘制信息指针。  |

**返回：**

x轴偏移值。若函数参数异常，返回0.0f。 异常返回原因：传入参数验证失败，参数不能为空。


### OH_ArkUI_CustomSpanMeasureInfo_Create()

```
ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create (void )
```
**描述：**

创建自定义段落组件测量信息。

**起始版本：** 12

**返回：**

CustomSpanMeasureInfo实例。 如果返回空指针，可能是因为内存不足。


### OH_ArkUI_CustomSpanMeasureInfo_Dispose()

```
void OH_ArkUI_CustomSpanMeasureInfo_Dispose (ArkUI_CustomSpanMeasureInfo * info)
```
**描述：**

销毁自定义段落组件测量信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 自定义段落组件测量信息指针。  |


### OH_ArkUI_CustomSpanMeasureInfo_GetFontSize()

```
float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize (ArkUI_CustomSpanMeasureInfo * info)
```
**描述：**

获取自定义段落组件的父节点Text的字体大小。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 自定义段落组件测量信息指针。  |

**返回：**

父节点Text的字体大小。若函数参数异常，返回0.0f。 异常返回原因：传入参数验证失败，参数不能为空。


### OH_ArkUI_CustomSpanMetrics_Create()

```
ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create (void )
```
**描述：**

创建自定义段落组件度量信息。

**起始版本：** 12

**返回：**

CustomSpanMetrics实例。 如果返回空指针，可能是因为内存不足。


### OH_ArkUI_CustomSpanMetrics_Dispose()

```
void OH_ArkUI_CustomSpanMetrics_Dispose (ArkUI_CustomSpanMetrics * metrics)
```
**描述：**

销毁自定义段落组件度量信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| metrics | CustomSpanMetrics实例。  |


### OH_ArkUI_CustomSpanMetrics_SetHeight()

```
int32_t OH_ArkUI_CustomSpanMetrics_SetHeight (ArkUI_CustomSpanMetrics * metrics, float height )
```
**描述：**

设置自定义段落组件的高度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| metrics | CustomSpanMetrics实例。  |
| height | 高度大小，单位为vp。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 异常原因：传入参数验证失败，参数不能为空。


### OH_ArkUI_CustomSpanMetrics_SetWidth()

```
int32_t OH_ArkUI_CustomSpanMetrics_SetWidth (ArkUI_CustomSpanMetrics * metrics, float width )
```
**描述：**

设置自定义段落组件的宽度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| metrics | CustomSpanMetrics实例。  |
| width | 宽度大小，单位为vp。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 异常原因：传入参数验证失败，参数不能为空。


### OH_ArkUI_DialogDismissEvent_GetDismissReason()

```
int32_t OH_ArkUI_DialogDismissEvent_GetDismissReason (ArkUI_DialogDismissEvent * event)
```
**描述：**

获取交互式关闭事件指针中的关闭原因。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 弹窗关闭事件对象指针。 |

**返回：**

关闭原因，异常情况返回-1。 DIALOG_DISMISS_BACK_PRESS 对应点击三键back、侧滑（左滑/右滑）、键盘ESC关闭。 DIALOG_DISMISS_TOUCH_OUTSIDE 点击遮障层时。 DIALOG_DISMISS_CLOSE_BUTTON 点击关闭按钮。 DIALOG_DISMISS_SLIDE_DOWN 下拉关闭。

### OH_ArkUI_CustomDialog_OpenDialog()

```
int32_t OH_ArkUI_CustomDialog_OpenDialog(ArkUI_CustomDialogOptions* options, void (*callback)(int32_t dialogId))
```
**描述：**

弹出自定义弹窗。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| callback | 开启弹窗的回调，返回入参是弹窗ID。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_UpdateDialog()

```
int32_t OH_ArkUI_CustomDialog_UpdateDialog(ArkUI_CustomDialogOptions* options, void (*callback)(int32_t dialogId))
```
**描述：**

更新自定义弹窗。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| callback | 更新弹窗的回调，返回入参是弹窗ID。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_CloseDialog()

```
int32_t OH_ArkUI_CustomDialog_CloseDialog(int32_t dialogId)
```
**描述：**

关闭自定义弹窗。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dialogId | 需要关闭的弹窗ID。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_CreateOptions()

```
ArkUI_CustomDialogOptions* OH_ArkUI_CustomDialog_CreateOptions(ArkUI_NodeHandle content)
```
**描述：**

创建自定义弹窗options。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| content | 自定义弹窗的内容。 |

**返回：**

自定义弹窗options的指针。

### OH_ArkUI_CustomDialog_DisposeOptions()

```
void OH_ArkUI_CustomDialog_DisposeOptions(ArkUI_CustomDialogOptions* options)
```
**描述：**

销毁自定义弹窗options。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 自定义弹窗options的指针。 |


### OH_ArkUI_CustomDialog_SetLevelMode()

```
int32_t OH_ArkUI_CustomDialog_SetLevelMode(ArkUI_CustomDialogOptions* options, ArkUI_LevelMode levelMode)
```
**描述：**

设置弹窗的显示层级。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 指向自定义弹窗options的指针。 |
| levelMode | 显示层级的枚举值， 类型为ArkUI_LevelMode。 |

**注解：**

OH_ArkUI_CustomDialog_SetLevelMode方法需要在调用OH_ArkUI_CustomDialog_OpenDialog方法之前调用。

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetLevelUniqueId()

```
int32_t OH_ArkUI_CustomDialog_SetLevelUniqueId(ArkUI_CustomDialogOptions* options, int32_t uniqueId)
```
**描述：**

设置弹窗显示层级页面下的节点id。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 指向自定义弹窗options的指针。 |
| uniqueId | 指定节点id，会查找该节点所在页面，并将弹窗显示在该页面下。 |

**注解：**

OH_ArkUI_CustomDialog_SetLevelUniqueId方法需要在调用OH_ArkUI_CustomDialog_OpenDialog方法之前调用。

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetImmersiveMode()

```
int32_t OH_ArkUI_CustomDialog_SetImmersiveMode(ArkUI_CustomDialogOptions* options, ArkUI_ImmersiveMode immersiveMode)
```
**描述：**

设置嵌入式弹窗蒙层的显示区域。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 指向自定义弹窗options的指针。 |
| immersiveMode | 显示区域类型的枚举值， 类型为ArkUI_ImmersiveMode。 |

**注解：**

OH_ArkUI_CustomDialog_SetImmersiveMode方法需要在调用OH_ArkUI_CustomDialog_OpenDialog方法之前调用。

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetBackgroundColor()

```
int32_t OH_ArkUI_CustomDialog_SetBackgroundColor(ArkUI_CustomDialogOptions* options, uint32_t backgroundColor)
```
**描述：**

设置弹窗的背景颜色。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| backgroundColor | 弹窗背景颜色。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetCornerRadius()

```
int32_t OH_ArkUI_CustomDialog_SetCornerRadius(
    ArkUI_CustomDialogOptions* options, float topLeft, float topRight, float bottomLeft, float bottomRight)
```
**描述：**

设置弹窗的圆角半径。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| topLeft | 弹窗左上角的圆角半径。 |
| topRight | 弹窗右上角的圆角半径。 |
| bottomLeft |弹窗左下角的圆角半径。 |
| bottomRight | 弹窗右下角的圆角半径。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetBorderWidth()

```
int32_t OH_ArkUI_CustomDialog_SetBorderWidth(
    ArkUI_CustomDialogOptions* options, float top, float right, float bottom, float left, ArkUI_LengthMetricUnit unit)
```
**描述：**

设置弹窗的边框宽度。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| top | 弹窗上边框的宽度。 |
| right | 弹窗右边框的宽度。 |
| bottom |弹窗下边框的宽度。 |
| left | 弹窗左边框的宽度。 |
| unit | 指定宽度的单位，默认为vp。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetBorderColor()

```
int32_t OH_ArkUI_CustomDialog_SetBorderColor(
    ArkUI_CustomDialogOptions* options, uint32_t top, uint32_t right, uint32_t bottom, uint32_t left)
```
**描述：**

设置弹窗的边框颜色。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| top | 弹窗上边框的颜色。 |
| right | 弹窗右边框的颜色。 |
| bottom |弹窗下边框的颜色。 |
| left | 弹窗左边框的颜色。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetBorderStyle()

```
int32_t OH_ArkUI_CustomDialog_SetBorderStyle(
    ArkUI_CustomDialogOptions* options, int32_t top, int32_t right, int32_t bottom, int32_t left)
```
**描述：**

设置弹窗的边框样式。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| top | 弹窗上边框的样式。 |
| right | 弹窗右边框的样式。 |
| bottom | 弹窗下边框的样式。 |
| left | 弹窗左边框的样式。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetWidth()

```
int32_t OH_ArkUI_CustomDialog_SetWidth(ArkUI_CustomDialogOptions* options, float width, ArkUI_LengthMetricUnit unit)
```
**描述：**

设置弹窗的背板宽度。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| width | 弹窗的背板宽度。 |
| unit | 指定宽度的单位，默认为vp。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetHeight()

```
int32_t OH_ArkUI_CustomDialog_SetHeight(ArkUI_CustomDialogOptions* options, float height, ArkUI_LengthMetricUnit unit)
```
**描述：**

设置弹窗的背板高度。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| height | 弹窗的背板高度。 |
| unit | 指定宽度的单位，默认为vp。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetShadow()

```
int32_t OH_ArkUI_CustomDialog_SetShadow(ArkUI_CustomDialogOptions* options, ArkUI_ShadowStyle shadow)
```
**描述：**

设置弹窗的背板阴影

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| shadow | 弹窗的背板阴影样式，枚举值。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetCustomShadow()

```
int32_t OH_ArkUI_CustomDialog_SetCustomShadow(
    ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* customShadow)
```
**描述：**

设置弹窗的自定义阴影。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| customShadow | 弹窗的自定义阴影参数，格式与NODE_CUSTOM_SHADOW属性一致。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetBackgroundBlurStyle()

```
int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyle(ArkUI_CustomDialogOptions* options, ArkUI_BlurStyle blurStyle)
```
**描述：**

设置弹窗的背板模糊材质。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| blurStyle | 弹窗的背板模糊材质，枚举值。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetAlignment()

```
int32_t OH_ArkUI_CustomDialog_SetAlignment(
    ArkUI_CustomDialogOptions* options, int32_t alignment, float offsetX, float offsetY)
```
**描述：**

设置弹窗的对齐模式。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| alignment | 弹窗的对齐模式，参数类型{@link ArkUI_Alignment}。 |
| offsetX | 弹窗的水平偏移量，浮点型。 |
| offsetY | 弹窗的垂直偏移量，浮点型。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetModalMode()

```
int32_t OH_ArkUI_CustomDialog_SetModalMode(ArkUI_CustomDialogOptions* options, bool isModal)
```
**描述：**

设置自定义弹窗是否开启模态样式的弹窗。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| isModal | 设置是否开启模态窗口。模态窗口有蒙层,非模态窗口无蒙层。设置为true表示开启模态窗口。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetAutoCancel()

```
int32_t OH_ArkUI_CustomDialog_SetAutoCancel(ArkUI_CustomDialogOptions* options, bool autoCancel)
```
**描述：**

设置自定义弹窗是否允许点击遮罩层退出。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| autoCancel | 设置是否允许点击遮罩层退出，true表示关闭弹窗，false表示不关闭弹窗。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetSubwindowMode()

```
int32_t OH_ArkUI_CustomDialog_SetSubwindowMode(ArkUI_CustomDialogOptions* options, bool showInSubwindow)
```
**描述：**

设置弹窗是否在子窗口显示此弹窗。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| showInSubwindow| 设置弹窗需要显示在主窗口之外时，是否在子窗口显示此弹窗。默认false，弹窗显示在应用内，而非独立子窗口。值为true时，可以在子窗显示。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetMask()

```
int32_t OH_ArkUI_CustomDialog_SetMask(
    ArkUI_CustomDialogOptions* options, uint32_t maskColor, const ArkUI_Rect* maskRect)
```
**描述：**

设置自定义弹窗遮罩属性。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| maskColor | 弹窗的遮罩颜色，0xargb格式。 |
| maskRect | 遮蔽层区域范围的指针，遮蔽层区域内的事件不透传，在遮蔽层区域外的事件透传。参数类型{@link ArkUI_Rect}。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetKeyboardAvoidMode()

```
int32_t OH_ArkUI_CustomDialog_SetKeyboardAvoidMode(
    ArkUI_CustomDialogOptions* options, ArkUI_KeyboardAvoidMode keyboardAvoidMode)
```
**描述：**

设置弹窗避让键盘的模式。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| keyboardAvoidMode | 键盘避让模式，枚举值。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetHoverModeEnabled()

```
int32_t OH_ArkUI_CustomDialog_SetHoverModeEnabled(ArkUI_CustomDialogOptions* options, bool enabled)
```
**描述：**

设置弹窗是否响应悬停态。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| enabled | 是否响应悬停态，默认false。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetHoverModeArea()

```
int32_t OH_ArkUI_CustomDialog_SetHoverModeArea(
    ArkUI_CustomDialogOptions* options, ArkUI_HoverModeAreaType hoverModeAreaType)
```
**描述：**

设置悬停态下弹窗默认展示区域。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| hoverModeAreaType | 悬停态区域，枚举值。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback()

```
int32_t OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback(
    ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(ArkUI_DialogDismissEvent* event))
```
**描述：**

注册系统关闭自定义弹窗的监听事件。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| userData | 用户自定义数据指针。 |
| callback | 监听自定义弹窗关闭的回调事件。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback()

```
int32_t OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback(
    ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```
**描述：**

注册自定义弹窗显示动效前的监听事件。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| userData | 用户自定义数据指针。 |
| callback | 弹窗显示动效前的事件回调。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback()

```
int32_t OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback(
    ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```
**描述：**

注册自定义弹窗弹出时的监听事件。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| userData | 用户自定义数据指针。 |
| callback | 弹窗弹出时的事件回调。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback()

```
int32_t OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback(
    ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```
**描述：**

注册自定义弹窗退出动效前的监听事件。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| userData | 用户自定义数据指针。 |
| callback | 弹窗退出动效前的事件回调。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback()

```
int32_t OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback(
    ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```
**描述：**

注册自定义弹窗消失时的监听事件。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| userData | 用户自定义数据指针。 |
| callback | 弹窗消失时的事件回调。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_GetState()

```
int32_t OH_ArkUI_CustomDialog_GetState(ArkUI_NativeDialogHandle handle, ArkUI_DialogState* state)
```
**描述：**

获取弹窗的状态。

**起始版本：** 20

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 自定义弹窗控制器对象指针。 |
| state | 自定义弹窗的状态。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions()

```
int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundBlurStyleOptions)
```
**描述：**

设置弹窗的背景模糊效果。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| backgroundBlurStyleOptions | 弹窗的背景模糊效果。<br/>参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].i32 表示深浅色模式，取[ArkUI_ColorMode](#arkui_colormode)枚举值。<br/>.value[1]?.i32 表示取色模式，取[ArkUI_AdaptiveColor](#arkui_adaptivecolor)枚举值。<br/>.value[2]?.f32 表示模糊效果程度，取[0.0,1.0]范围内的值。<br/>.value[3]?.u32 表示灰阶模糊参数，对黑色的提亮程度，有效值范围为[0,127]。<br/>.value[4]?.u32 表示灰阶模糊参数，对白色的压暗程度，有效值范围为[0,127]。<br/>.value[5]?.i32 表示模糊激活策略，取[ArkUI_BlurStyleActivePolicy](#arkui_blurstyleactivepolicy)枚举值。<br/>.value[6]?.u32 表示窗口失焦后，窗口内控件模糊效果会被移除，此时控件背板的颜色，0xargb类型。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_CustomDialog_SetBackgroundEffect()

```
int32_t OH_ArkUI_CustomDialog_SetBackgroundEffect(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundEffect)
```
**描述：**

设置弹窗的背景效果参数。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| options | 弹窗参数。 |
| backgroundEffect | 弹窗的背景效果参数。<br/>参数[ArkUI_AttributeItem](_ark_u_i___attribute_item.md)格式：<br/>.value[0].f32 表示模糊半径，单位为vp。<br/>.value[1]?.f32 表示饱和度。<br/>.value[2]?.f32 表示亮度。<br/>.value[3]?.u32 表示颜色，0xargb类型。<br/>.value[4]?.i32 表示取色模式，取[ArkUI_AdaptiveColor](#arkui_adaptivecolor)枚举值。<br/>.value[5]?.u32 表示灰阶模糊参数，对黑色的提亮程度，有效值范围为[0,127]。<br/>.value[6]?.u32 表示灰阶模糊参数，对白色的压暗程度，有效值范围为[0,127]。<br/>.value[7]?.i32 表示模糊激活策略，取[ArkUI_BlurStyleActivePolicy](#arkui_blurstyleactivepolicy)枚举值。<br/>.value[8]?.u32 表示窗口失焦后，窗口内控件模糊效果会被移除，此时控件背板的颜色，0xargb类型。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md) 成功。
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md) 函数参数异常。

### OH_ArkUI_DialogDismissEvent_GetUserData()

```
void* OH_ArkUI_DialogDismissEvent_GetUserData (ArkUI_DialogDismissEvent * event)
```
**描述：**

获取弹窗关闭事件对象中的用户自定义数据指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 弹窗关闭事件对象指针。 |

**返回：**

用户自定义数据指针。


### OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss()

```
void OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss (ArkUI_DialogDismissEvent * event, bool shouldBlockDismiss )
```
**描述：**

设置是否需要屏蔽系统关闭弹窗行为，true表示屏蔽系统行为不关闭弹窗，false表示不屏蔽。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 弹窗关闭事件对象指针。  |
| shouldBlockDismiss | 实现需要屏蔽系统关闭弹窗行为。  |


### OH_ArkUI_DisallowNodeAnyDropDataTypes()

```
int32_t OH_ArkUI_DisallowNodeAnyDropDataTypes (ArkUI_NodeHandle node)
```
**描述：**

配置组件不允许接受任何数据类型，该接口会重置通过[OH_ArkUI_SetNodeAllowedDropDataTypes](#oh_arkui_setnodealloweddropdatatypes)配置的数据类型。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 组件节点指针。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragAction_Dispose()

```
void OH_ArkUI_DragAction_Dispose (ArkUI_DragAction * dragAction)
```
**描述：**

销毁创建的 ArkUI_DragAction 对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |


### OH_ArkUI_DragAction_RegisterStatusListener()

```
int32_t OH_ArkUI_DragAction_RegisterStatusListener (ArkUI_DragAction * dragAction, void * userData, void(*)(ArkUI_DragAndDropInfo *dragAndDropInfo, void *userData) listener )
```
**描述：**

注册拖拽状态监听回调，该回调可感知到拖拽已经发起或用户松手结束的状态，可通过该监听获取到落入方对数据的接收处理是否成功。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |
| userData | 应用自定义数据。  |
| listener | 状态监听回调，回调触发时，系统会返回一个拖拽状态对象指针，该指针会在回调执行完成后被销毁，应用不应再持有。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](#arkui_errorcode) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](#arkui_errorcode) 函数参数异常。


### OH_ArkUI_DragAction_SetData()

```
int32_t OH_ArkUI_DragAction_SetData (ArkUI_DragAction * dragAction, OH_UdmfData * data )
```
**描述：**

设置拖拽数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |
| data | 拖拽数据。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。

### OH_ArkUI_DragAction_SetDataLoadParams()

```
ArkUI_ErrorCode OH_ArkUI_DragAction_SetDataLoadParams(ArkUI_DragAction* dragAction,
    OH_UdmfDataLoadParams* dataLoadParams)
```
**描述：**

使用此方法为系统提供一个数据加载参数，而不是直接提供一个完整的数据对象。当用户拖拽到目标应用程序并落入时，系统将使用dataLoadParams请求数据。可以极大地提高拖拽大量数据的效率，以及目标应用程序中处理落入数据的效率。此方法应始终优先于[OH_ArkUI_DragAction_SetData](#oh_arkui_dragaction_setdata)使用。请参阅[OH_UdmfDataLoadParams_Create](../apis-arkdata/capi-udmf-h.md#oh_udmfdataloadparams_create)了解如何创建和准备数据加载参数。该方法与[OH_ArkUI_DragAction_SetData](#oh_arkui_dragaction_setdata)存在冲突，系统始终以最后调用的方法为准。

**起始版本：** 20

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |
| dataLoadParams |在落入操作时使用的数据加载参数。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](#arkui_errorcode) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](#arkui_errorcode) 函数参数异常。


### OH_ArkUI_DragAction_SetDragPreviewOption()

```
int32_t OH_ArkUI_DragAction_SetDragPreviewOption (ArkUI_DragAction * dragAction, ArkUI_DragPreviewOption * option )
```
**描述：**

将构造的ArkUI_DragPreviewOption设置给ArkUI_DragAction。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |
| option | 自定义参数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragAction_SetPixelMaps()

```
int32_t OH_ArkUI_DragAction_SetPixelMaps (ArkUI_DragAction * dragAction, OH_PixelmapNative * pixelmapArray[], int32_t size )
```
**描述：**

设置拖拽跟手图，只能使用 pixelmap 格式对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |
| pixelmapArray | 拖拽跟手图位图数组。  |
| size | 拖拽跟手图数量。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragAction_SetPointerId()

```
int32_t OH_ArkUI_DragAction_SetPointerId (ArkUI_DragAction * dragAction, int32_t pointer )
```
**描述：**

设置手指ID，当屏幕上仅有一只手指在操作时，pointer ID 为 0；一般情况下，配置 0 即可。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |
| pointer | 手指ID，范围 0～9。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragAction_SetTouchPointX()

```
int32_t OH_ArkUI_DragAction_SetTouchPointX (ArkUI_DragAction * dragAction, float x )
```
**描述：**

设置跟手点，相对于设置的第一个pixelmap的左上角。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |
| x | 跟手点坐标x值。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragAction_SetTouchPointY()

```
int32_t OH_ArkUI_DragAction_SetTouchPointY (ArkUI_DragAction * dragAction, float y )
```
**描述：**

设置跟手点，相对于设置的第一个pixelmap的左上角。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |
| y | 跟手点坐标y值。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragAction_UnregisterStatusListener()

```
void OH_ArkUI_DragAction_UnregisterStatusListener (ArkUI_DragAction * dragAction)
```
**描述：**

解注册拖拽状态监听回调。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽行为对象。  |


### OH_ArkUI_DragAndDropInfo_GetDragEvent()

```
ArkUI_DragEvent* OH_ArkUI_DragAndDropInfo_GetDragEvent (ArkUI_DragAndDropInfo * dragAndDropInfo)
```
**描述：**

通过dragAndDropInfo获取到DragEvent，可通过DragEvent获取释放结果等。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAndDropInfo | 拖拽状态监听返回的拖拽相关信息。  |

**返回：**

ArkUI_DragEvent 拖拽事件，如果获取失败，则返回空。


### OH_ArkUI_DragAndDropInfo_GetDragStatus()

```
ArkUI_DragStatus OH_ArkUI_DragAndDropInfo_GetDragStatus (ArkUI_DragAndDropInfo * dragAndDropInfo)
```
**描述：**

获取dragaction发起拖拽的状态，获取异常时返回 ArkUI_DRAG_STATUS_UNKNOWN。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAndDropInfo | 拖拽状态监听返回的拖拽相关信息。  |

**返回：**

ArkUI_DragStatus 拖拽状态，如果获取失败，返回默认值 ArkUI_DRAG_STATUS_UNKNOWN。


### OH_ArkUI_DragEvent_DisableDefaultDropAnimation()

```
int32_t OH_ArkUI_DragEvent_DisableDefaultDropAnimation (ArkUI_DragEvent * event, bool disable )
```
**描述：**

设置是否禁用松手时的系统默认动效，默认不禁用，通常在应用需要自定义落位动效时配置。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| disable | 是否禁用松手时的系统默认动效，true禁用，false不禁用。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragEvent_GetDataTypes()

```
int32_t OH_ArkUI_DragEvent_GetDataTypes (ArkUI_DragEvent * event, char * eventTypeArray[], int32_t length, int32_t maxStrLen)
```
**描述：**

从ArkUI_DragEvent中获取拖拽数据的类型列表。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| eventTypeArray | 返回拖拽数据的类型列表，需要先自行创建字符串数组。  |
| length | 数组总长度，不应少于使用[OH_ArkUI_DragEvent_GetDataTypeCount](#oh_arkui_dragevent_getdatatypecount)获取到的数量。  |
| maxStrLen | 拖拽数据类型的最大字符串长度。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR 缓冲区大小不足。


### OH_ArkUI_DragEvent_GetDataTypeCount()

```
int32_t OH_ArkUI_DragEvent_GetDataTypeCount (ArkUI_DragEvent * event, int32_t * count )
```
**描述：**

从ArkUI_DragEvent中获取所拖拽的数据类型种类个数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| count | 出参，返回所拖拽数据的类型的数量。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragEvent_GetDragResult()

```
int32_t OH_ArkUI_DragEvent_GetDragResult (ArkUI_DragEvent * event, ArkUI_DragResult * result )
```
**描述：**

从ArkUI_DragEvent中获取拖拽结果。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| result | 出参，返回拖拽事件对应的拖拽结果。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragEvent_GetDropOperation()

```
int32_t OH_ArkUI_DragEvent_GetDropOperation (ArkUI_DragEvent * event, ArkUI_DropOperation * operation)
```
**描述：**

从ArkUI_DragEvent中获取数据处理方式。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| operation | 出参，返回拖拽事件对应的数据处理方式。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragEvent_GetModifierKeyStates()

```
int32_t OH_ArkUI_DragEvent_GetModifierKeyStates (ArkUI_DragEvent * event, uint64_t * keys )
```
**描述：**

获取功能键按压状态。此接口不支持在手写笔场景下使用。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| keys | 返回当前处于按下状态的 modifier key组合，应用可通过位运算进行判断。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。

### OH_ArkUI_DragEvent_GetDragSource()

```
ArkUI_ErrorCode OH_ArkUI_DragEvent_GetDragSource (ArkUI_DragEvent* event, char* bundleName, int32_t length)
```
**描述：**

获取拖起方包名。

**起始版本：** 20

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。 |
| bundleName | 接收拖起方包名的字符串数组。 |
| length | 传入的字符串数组长度，不小于128个字符。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。

### OH_ArkUI_DragEvent_IsRemote()

```
ArkUI_ErrorCode OH_ArkUI_DragEvent_IsRemote (ArkUI_DragEvent * event, bool* isRemote)
```
**描述：**

获取是否是跨设备拖拽，跨设备拖拽时为true。

**起始版本：** 20

**参数**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| isRemote | 布尔变量指针，用来接收是否是跨设备拖拽。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。

### OH_ArkUI_DragEvent_SetDataLoadParams()

```
ArkUI_ErrorCode OH_ArkUI_DragEvent_SetDataLoadParams(ArkUI_DragEvent* event, OH_UdmfDataLoadParams* dataLoadParams)
```
**描述：**

使用此方法为系统提供一个数据加载参数，而不是直接提供一个完整的数据对象。当用户拖拽到目标应用程序并落入时，系统将使用dataLoadParams请求数据。可以极大地提高拖拽大量数据的效率，以及目标应用程序中处理落入数据的效率。此方法应始终优先于 [OH_ArkUI_DragEvent_SetData](#oh_arkui_dragevent_setdata)使用。请参阅[OH_UdmfDataLoadParams_Create](../apis-arkdata/capi-udmf-h.md#oh_udmfdataloadparams_create)了解如何创建和准备数据加载参数。该方法与 [OH_ArkUI_DragEvent_SetData](#oh_arkui_dragevent_setdata)存在冲突，系统始终以最后调用的方法为准。

**起始版本：** 20

**参数**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| dataLoadParams | 落入操作时使用的数据加载参数。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。

### OH_ArkUI_DragEvent_GetDisplayId()

```
ArkUI_ErrorCode OH_ArkUI_DragEvent_GetDisplayId(ArkUI_DragEvent* event, int32_t* displayId)
```
**描述：**

获取当前拖拽事件发生时所在的屏幕ID，不支持当eventType为NODE_ON_DRAG_END时获取。

**起始版本：** 20

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  | 
| displayId | 返回当前拖拽事件发生时所在的屏幕ID。  | 

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。


### OH_ArkUI_DragEvent_GetPreviewRectHeight()

```
float OH_ArkUI_DragEvent_GetPreviewRectHeight (ArkUI_DragEvent * event)
```
**描述：**

从ArkUI_DragEvent中获取预览图的高。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回拖拽跟手图高度，单位为PX，传入参数无效时返回默认值 0。


### OH_ArkUI_DragEvent_GetPreviewRectWidth()

```
float OH_ArkUI_DragEvent_GetPreviewRectWidth (ArkUI_DragEvent * event)
```
**描述：**

从ArkUI_DragEvent中获取预览图的宽。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回拖拽跟手图宽度，单位为PX，传入参数无效时返回默认值 0。


### OH_ArkUI_DragEvent_GetPreviewTouchPointX()

```
float OH_ArkUI_DragEvent_GetPreviewTouchPointX (ArkUI_DragEvent * event)
```
**描述：**

从ArkUI_DragEvent中获取预览图跟手点的x轴坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回拖拽跟手点的x轴坐标，单位为PX，传入参数无效时返回默认值 0。


### OH_ArkUI_DragEvent_GetPreviewTouchPointY()

```
float OH_ArkUI_DragEvent_GetPreviewTouchPointY (ArkUI_DragEvent * event)
```
**描述：**

从ArkUI_DragEvent中获取预览图跟手点的y轴坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回拖拽跟手点的y轴坐标，单位为PX，传入参数无效时返回默认值 0。


### OH_ArkUI_DragEvent_GetTouchPointXToDisplay()

```
float OH_ArkUI_DragEvent_GetTouchPointXToDisplay (ArkUI_DragEvent * event)
```
**描述：**

从ArkUI_DragEvent中获取跟手点相对于当前Display的x轴坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回拖拽跟手点相对于当前Display的x轴坐标，单位为PX，传入参数无效时返回默认值 0。

### OH_ArkUI_DragEvent_GetTouchPointXToGlobalDisplay()

```
float OH_ArkUI_DragEvent_GetTouchPointXToGlobalDisplay (ArkUI_DragEvent * event)
```

**描述：**

从ArkUI_DragEvent中获取跟手点相对于全局屏幕的x轴坐标。

**起始版本：** 20

**参数:**

| 名称  | 描述                      |
| ----- | ------------------------- |
| event | ArkUI_DragEvent事件指针。 |

**返回：**

返回拖拽跟手点相对于全局Display的x轴坐标，单位为PX，传入参数无效时返回默认值0。


### OH_ArkUI_DragEvent_GetTouchPointXToWindow()

```
float OH_ArkUI_DragEvent_GetTouchPointXToWindow (ArkUI_DragEvent * event)
```
**描述：**

从ArkUI_DragEvent中获取跟手点相对于window的x轴坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回跟手点相对于window的x轴坐标，单位为PX，传入参数无效时返回默认值 0。


### OH_ArkUI_DragEvent_GetTouchPointYToDisplay()

```
float OH_ArkUI_DragEvent_GetTouchPointYToDisplay (ArkUI_DragEvent * event)
```
**描述：**

从ArkUI_DragEvent中获取跟手点相对于当前Display的y轴坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回拖拽跟手点相对于当前Display的y轴坐标，单位为PX，传入参数无效时返回默认值 0。

### OH_ArkUI_DragEvent_GetTouchPointYToGlobalDisplay()

```
float OH_ArkUI_DragEvent_GetTouchPointYToGlobalDisplay (ArkUI_DragEvent * event)
```

**描述：**

从ArkUI_DragEvent中获取跟手点相对于全局屏幕的y轴坐标。

**起始版本：** 20

**参数:**

| 名称  | 描述                      |
| ----- | ------------------------- |
| event | ArkUI_DragEvent事件指针。 |

**返回：**

返回拖拽跟手点相对于全局Display的y轴坐标，单位为PX，传入参数无效时返回默认值0。


### OH_ArkUI_DragEvent_GetTouchPointYToWindow()

```
float OH_ArkUI_DragEvent_GetTouchPointYToWindow (ArkUI_DragEvent * event)
```
**描述：**

从ArkUI_DragEvent中获取跟手点相对于window的y轴坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回跟手点相对于window的y轴坐标，单位为PX，传入参数无效时返回默认值 0。


### OH_ArkUI_DragEvent_GetUdmfData()

```
int32_t OH_ArkUI_DragEvent_GetUdmfData (ArkUI_DragEvent * event, OH_UdmfData * data )
```
**描述：**

从ArkUI_DragEvent中获取拖拽默认相关数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| data | OH_UdmfData 拖拽的数据指针，应用在接收时需通过 **OH_UdmfData_Create** 方法创建一个用于接收数据的指针。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragEvent_GetVelocity()

```
float OH_ArkUI_DragEvent_GetVelocity (ArkUI_DragEvent * event)
```
**描述：**

获取当前拖拽的主方向拖动速度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回当前拖拽移动速度，单位为PX/s，传入参数无效时返回默认值 0。


### OH_ArkUI_DragEvent_GetVelocityX()

```
float OH_ArkUI_DragEvent_GetVelocityX (ArkUI_DragEvent * event)
```
**描述：**

获取当前拖拽的x轴方向拖动速度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回当前拖拽的x轴方向移动速度，单位为PX/s，传入参数无效时返回默认值 0。


### OH_ArkUI_DragEvent_GetVelocityY()

```
float OH_ArkUI_DragEvent_GetVelocityY (ArkUI_DragEvent * event)
```
**描述：**

获取当前拖拽的y轴方向拖动速度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |

**返回：**

float 返回当前拖拽的y轴方向移动速度，单位为PX/s，传入参数无效时返回默认值 0。


### OH_ArkUI_DragEvent_SetData()

```
int32_t OH_ArkUI_DragEvent_SetData (ArkUI_DragEvent * event, OH_UdmfData * data )
```
**描述：**

向ArkUI_DragEvent中设置拖拽数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| data | 拖拽数据。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragEvent_SetDragResult()

```
int32_t OH_ArkUI_DragEvent_SetDragResult (ArkUI_DragEvent * event, ArkUI_DragResult result )
```
**描述：**

设置拖拽事件的结果。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| result | 拖拽数据处理结果。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragEvent_SetSuggestedDropOperation()

```
int32_t OH_ArkUI_DragEvent_SetSuggestedDropOperation (ArkUI_DragEvent * event, ArkUI_DropOperation dropOperation)
```
**描述：**

设置数据处理方式

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| dropOperation | 角标显示状态的类型。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragPreviewOption_Dispose()

```
void OH_ArkUI_DragPreviewOption_Dispose (ArkUI_DragPreviewOption * option)
```
**描述：**

销毁跟手图自定义参数对象实例。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 自定义参数。  |


### OH_ArkUI_DragPreviewOption_SetBadgeNumber()

```
int32_t OH_ArkUI_DragPreviewOption_SetBadgeNumber (ArkUI_DragPreviewOption * option, uint32_t forcedNumber )
```
**描述：**

强制显示角标的数量,覆盖SetDragPreviewNumberBadgeEnabled设置的值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 自定义参数。  |
| forcedNumber | 角标的数量。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragPreviewOption_SetDefaultAnimationBeforeLiftingEnabled()

```
int32_t OH_ArkUI_DragPreviewOption_SetDefaultAnimationBeforeLiftingEnabled (ArkUI_DragPreviewOption * option, bool enabled )
```
**描述：**

配置是否开启点按时的默认动画。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 自定义参数。  |
| enabled | 是否开启默认点按效果。true表示开启默认点按效果，false表示不开启默认点按效果。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragPreviewOption_SetDefaultRadiusEnabled()

```
int32_t OH_ArkUI_DragPreviewOption_SetDefaultRadiusEnabled (ArkUI_DragPreviewOption * option, bool enabled )
```
**描述：**

设置跟手图背板默认的圆角效果，默认不开启。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 自定义参数。  |
| enabled | 是否开启圆角效果显示。true表示开启圆角效果显示，false表示不开启圆角效果显示。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragPreviewOption_SetDefaultShadowEnabled()

```
int32_t OH_ArkUI_DragPreviewOption_SetDefaultShadowEnabled (ArkUI_DragPreviewOption * option, bool enabled )
```
**描述：**

设置跟手图背板默认的投影效果，默认不开启。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 自定义参数。  |
| enabled | 是否使用默认投影效果。true表示使用默认投影效果，false表示不使用默认投影效果。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragPreviewOption_SetNumberBadgeEnabled()

```
int32_t OH_ArkUI_DragPreviewOption_SetNumberBadgeEnabled (ArkUI_DragPreviewOption * option, bool enabled )
```
**描述：**

设置跟手图背板是否显示角标，开启后，系统会根据拖拽数量自动进行角标显示。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 自定义参数。  |
| enabled | 是否开启角标显示。true表示开启角标显示，false表示不开启角标显示。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DragPreviewOption_SetScaleMode()

```
int32_t OH_ArkUI_DragPreviewOption_SetScaleMode (ArkUI_DragPreviewOption * option, ArkUI_DragPreviewScaleMode scaleMode )
```
**描述：**

设置拖拽跟手图是否根据系统定义自动进行缩放。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 自定义参数。  |
| scaleMode | 设置组件拖拽过程中的跟手图缩放模式。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap()

```
ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromAnimatedPixelMap (OH_PixelmapNativeHandle * array, int32_t size )
```
**描述：**

使用 PixelMap 图片数组创建DrawableDescriptor 对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| array | PixelMap 图片数组对象指针。  |
| size | PixelMap 图片数组大小。  |

**返回：**

返回 DrawableDescriptor 对象指针。


### OH_ArkUI_DrawableDescriptor_CreateFromPixelMap()

```
ArkUI_DrawableDescriptor* OH_ArkUI_DrawableDescriptor_CreateFromPixelMap (OH_PixelmapNativeHandle pixelMap)
```
**描述：**

使用 PixelMap 创建 DrawableDescriptor 对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| pixelMap | PixelMap 对象指针。  |

**返回：**

返回 DrawableDescriptor 对象指针。


### OH_ArkUI_DrawableDescriptor_Dispose()

```
void OH_ArkUI_DrawableDescriptor_Dispose (ArkUI_DrawableDescriptor * drawableDescriptor)
```
**描述：**

销毁 DrawableDescriptor 对象指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| drawableDescriptor | DrawableDescriptor 对象指针。  |


### OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray()

```
OH_PixelmapNativeHandle* OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArray (ArkUI_DrawableDescriptor * drawableDescriptor)
```
**描述：**

获取用于播放动画的 PixelMap 图片数组数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| drawableDescriptor | DrawableDescriptor 对象指针。  |

**返回：**

PixelMap 图片数组指针。


### OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArraySize()

```
int32_t OH_ArkUI_DrawableDescriptor_GetAnimatedPixelMapArraySize (ArkUI_DrawableDescriptor * drawableDescriptor)
```
**描述：**

获取用于播放动画的 PixelMap 图片数组数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| drawableDescriptor | DrawableDescriptor 对象指针。  |

**返回：**

PixelMap 图片数组大小。


### OH_ArkUI_DrawableDescriptor_GetAnimationDuration()

```
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationDuration (ArkUI_DrawableDescriptor * drawableDescriptor)
```
**描述：**

获取 PixelMap 图片数组播放总时长。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| drawableDescriptor | DrawableDescriptor 对象指针。  |

**返回：**

播放总时长，单位毫秒。


### OH_ArkUI_DrawableDescriptor_GetAnimationIteration()

```
int32_t OH_ArkUI_DrawableDescriptor_GetAnimationIteration (ArkUI_DrawableDescriptor * drawableDescriptor)
```
**描述：**

获取 PixelMap 图片数组播放次数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| drawableDescriptor | DrawableDescriptor 对象指针。  |

**返回：**

播放次数。


### OH_ArkUI_DrawableDescriptor_GetStaticPixelMap()

```
OH_PixelmapNativeHandle OH_ArkUI_DrawableDescriptor_GetStaticPixelMap (ArkUI_DrawableDescriptor * drawableDescriptor)
```
**描述：**

获取 PixelMap 图片对象指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| drawableDescriptor | DrawableDescriptor 对象指针。  |

**返回：**

PixelMap 对象指针。


### OH_ArkUI_DrawableDescriptor_SetAnimationDuration()

```
void OH_ArkUI_DrawableDescriptor_SetAnimationDuration (ArkUI_DrawableDescriptor * drawableDescriptor, int32_t duration )
```
**描述：**

设置 PixelMap 图片数组播放总时长。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| drawableDescriptor | DrawableDescriptor 对象指针。  |
| duration | 播放总时长，单位毫秒。  |


### OH_ArkUI_DrawableDescriptor_SetAnimationIteration()

```
void OH_ArkUI_DrawableDescriptor_SetAnimationIteration (ArkUI_DrawableDescriptor * drawableDescriptor, int32_t iteration )
```
**描述：**

设置 PixelMap 图片数组播放次数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| drawableDescriptor | DrawableDescriptor 对象指针。  |
| iterations | 播放次数。  |


### OH_ArkUI_DrawContext_GetCanvas()

```
void* OH_ArkUI_DrawContext_GetCanvas (ArkUI_DrawContext * context)
```
**描述：**

获取绘制canvas指针，可以转换为图形库的OH_Drawing_Canvas指针进行绘制。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| context | 绘制上下文。  |

**返回：**

用于绘制的canvas指针。


### OH_ArkUI_DrawContext_GetSize()

```
ArkUI_IntSize OH_ArkUI_DrawContext_GetSize (ArkUI_DrawContext * context)
```
**描述：**

获取可绘制区域大小。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| context | 绘制上下文。  |

**返回：**

可绘制区域大小。

### OH_ArkUI_FocusActivate()
```
void OH_ArkUI_FocusActivate(ArkUI_ContextHandle uiContext, bool isActive, bool isAutoInactive);
```
**描述：**

设置当前界面的焦点激活态，获焦节点显示焦点框。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| uiContext | UI实例对象指针。 |
| isActive | 设置是否进入/退出焦点激活态。 |
| isAutoInactive | 当触摸事件或鼠标按下事件触发时，"true" 表示将状态设置为退出焦点激活态，"false" 表示在调用对应设置API前，保持当前状态。|

### OH_ArkUI_FocusClear()
```
void OH_ArkUI_FocusClear(ArkUI_ContextHandle uiContext);
```
**描述：**

将当前焦点清除到根容器节点。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| uiContext | UI实例对象指针。 |

### OH_ArkUI_FocusRequest()
```
ArkUI_ErrorCode OH_ArkUI_FocusRequest(ArkUI_NodeHandle node);
```
**描述：**

请求焦点。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 组件节点指针。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 请求成功。 [ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE](_ark_u_i___native_module.md#arkui_errorcode) - 节点无法获得焦点。 [ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR](_ark_u_i___native_module.md#arkui_errorcode) - 祖先节点无法获得焦点。[ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT](_ark_u_i___native_module.md#arkui_errorcode) - 节点不存在。

### OH_ArkUI_FocusSetAutoTransfer()
```
void OH_ArkUI_FocusSetAutoTransfer(ArkUI_ContextHandle uiContext, bool autoTransfer);
```
**描述：**

 设置页面切换时，焦点转移行为。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| uiContext | UI实例对象指针。 |
| autoTransfer | 页面切换时，是否转移焦点。true表示页面切换时转移焦点，false表示页面切换时焦点不转移。|

### OH_ArkUI_FocusSetKeyProcessingMode()
```
void OH_ArkUI_FocusSetKeyProcessingMode(ArkUI_ContextHandle uiContext, ArkUI_KeyProcessingMode mode)
```
**描述：**

设置按键事件处理的优先级。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| uiContext | UI实例对象指针。 |
| mode | 按键处理模式。 |

### OH_ArkUI_GestureEvent_GetActionType()

```
ArkUI_GestureEventActionType OH_ArkUI_GestureEvent_GetActionType (const ArkUI_GestureEvent * event)
```
**描述：**

返回手势事件类型。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

手势事件类型。


### OH_ArkUI_GestureEvent_GetNode()

```
ArkUI_NodeHandle OH_ArkUI_GestureEvent_GetNode (const ArkUI_GestureEvent * event)
```
**描述：**

获取被绑定手势的ARKUI组件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

ARKUI组件。


### OH_ArkUI_GestureEvent_GetRawInputEvent()

```
const ArkUI_UIInputEvent* OH_ArkUI_GestureEvent_GetRawInputEvent (const ArkUI_GestureEvent * event)
```
**描述：**

返回手势输入。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

手势事件的原始输入事件。


### OH_ArkUI_GestureEventTargetInfo_IsScrollBegin()

```
int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollBegin (ArkUI_GestureEventTargetInfo * info, bool * ret )
```
**描述：**

当前滚动类容器组件是否在顶部。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 手势事件目标信息。  |
| ret | 当前滚动类容器组件是否在顶部。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。 [ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER](_ark_u_i___native_module.md#arkui_errorcode) - 非滚动类容器。


### OH_ArkUI_GestureEventTargetInfo_IsScrollEnd()

```
int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollEnd (ArkUI_GestureEventTargetInfo * info, bool * ret )
```
**描述：**

当前滚动类容器组件是否在底部。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 手势事件目标信息。  |
| ret | 当前滚动类容器组件是否在底部。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。 [ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER](_ark_u_i___native_module.md#arkui_errorcode) - 非滚动类容器。


### OH_ArkUI_GestureInterruptInfo_GetGestureEvent()

```
ArkUI_GestureEvent* OH_ArkUI_GestureInterruptInfo_GetGestureEvent (const ArkUI_GestureInterruptInfo * event)
```
**描述：**

返回打断的手势事件数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 打断回调事件。  |

**返回：**

打断的手势事件数据。

### OH_ArkUI_GestureInterruptInfo_GetRecognizer()

```
ArkUI_GestureRecognizer* OH_ArkUI_GestureInterruptInfo_GetRecognizer (const ArkUI_GestureInterruptInfo * event)
```
**描述：**

返回被打断的手势指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 打断回调事件。  |

**返回：**

被打断的手势指针。


### OH_ArkUI_GestureInterruptInfo_GetSystemFlag()

```
bool OH_ArkUI_GestureInterruptInfo_GetSystemFlag (const ArkUI_GestureInterruptInfo * event)
```
**描述：**

判断是否组件内置手势。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势打断回调事件。  |

**返回：**

true: 系统内置手势； false: 非系统内置手势。


### OH_ArkUI_GestureInterruptInfo_GetSystemRecognizerType()

```
int32_t OH_ArkUI_GestureInterruptInfo_GetSystemRecognizerType (const ArkUI_GestureInterruptInfo * event)
```
**描述：**

当要触发的是系统内部手势时，使用该方法可返回该系统内部手势的类型。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 打断回调事件。  |

**返回：**

要触发的内部手势对应的手势类型，如果当前触发的手势不是系统内部手势，则返回 -1。


### OH_ArkUI_GestureInterruptInfo_GetTouchRecognizers()

```
int32_t OH_ArkUI_GestureInterruptInfo_GetTouchRecognizers(const ArkUI_GestureInterruptInfo* info,
    ArkUI_TouchRecognizerHandleArray* recognizers, int32_t* size)
```
**描述：**

使用该方法可返回与该手势相关的所有触摸识别器。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 打断回调事件。  |
| recognizers | 指向触摸识别器数组的指针。  |
| size | 触摸识别器数组的大小。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。


### OH_ArkUI_TouchRecognizer_GetNodeHandle()

```
ArkUI_NodeHandle OH_ArkUI_TouchRecognizer_GetNodeHandle(const ArkUI_TouchRecognizerHandle recognizer)
```
**描述：**

获取触摸识别器对应的组件句柄。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 触摸识别器的句柄。  | 

**返回：**

触摸识别器对应的组件句柄。


### OH_ArkUI_TouchRecognizer_CancelTouch()

```
int32_t OH_ArkUI_TouchRecognizer_CancelTouch(ArkUI_TouchRecognizerHandle recognizer, ArkUI_GestureInterruptInfo* info)
```
**描述：**

在手势打断回调中向指定的触摸识别器发送取消触摸的事件。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 触摸识别器的句柄。  | 
| info | 指向手势打断信息的指针。  | 

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。


### OH_ArkUI_GetContextByNode()

```
ArkUI_ContextHandle OH_ArkUI_GetContextByNode (ArkUI_NodeHandle node)
```
**描述：**

获取当前节点所在页面的UI的上下文实例对象指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |

**返回：**

UI的上下文实例对象指针。


### OH_ArkUI_GetContextFromNapiValue()

```
int32_t OH_ArkUI_GetContextFromNapiValue (napi_env env, napi_value value, ArkUI_ContextHandle * context )
```
**描述：**

获取ArkTS侧创建的UIContext对象映射到Native侧的ArkUI_ContextHandle。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| env | napi的环境指针。  |
| value | ArkTS侧创建的context对象。  |
| context | ArkUI_ContextHandle指针。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_GetDrawableDescriptorFromNapiValue()

```
int32_t OH_ArkUI_GetDrawableDescriptorFromNapiValue (napi_env env, napi_value value, ArkUI_DrawableDescriptor ** drawableDescriptor )
```
**描述：**

将ArkTS侧创建的DrawableDescriptor对象映射到Native侧的ArkUI_DrawableDescriptor。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| env | napi的环境指针。  |
| value | ArkTS侧创建的DrawableDescriptor对象。  |
| drawableDescriptor | 接受ArkUI_DrawableDescriptor指针的对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_GetDrawableDescriptorFromResourceNapiValue()

```
int32_t OH_ArkUI_GetDrawableDescriptorFromResourceNapiValue (napi_env env, napi_value value, ArkUI_DrawableDescriptor ** drawableDescriptor )
```
**描述：**

将ArkTS侧创建的$r资源对象映射到Native侧的ArkUI_DrawableDescriptor。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| env | napi的环境指针。  |
| value | ArkTS侧创建的$r资源对象。  |
| drawableDescriptor | 接受ArkUI_DrawableDescriptor指针的对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_GetGestureBindNodeId()

```
int32_t OH_ArkUI_GetGestureBindNodeId (ArkUI_GestureRecognizer * recognizer, char * nodeId, int32_t size, int32_t * result )
```
**描述：**

获取手势识别器绑定的组件的ID。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| nodeId | 组件的ID。  |
| size | 存储区大小。  |
| result | 拷贝的字符串长度。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。 [ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH](_ark_u_i___native_module.md#arkui_errorcode) - 存储区大小不足。


### OH_ArkUI_GetGestureEventTargetInfo()

```
int32_t OH_ArkUI_GetGestureEventTargetInfo (ArkUI_GestureRecognizer * recognizer, ArkUI_GestureEventTargetInfo ** info )
```
**描述：**

获取手势事件目标信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| info | 手势事件目标信息。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。


### OH_ArkUI_GetGestureRecognizerEnabled()

```
bool OH_ArkUI_GetGestureRecognizerEnabled (ArkUI_GestureRecognizer * recognizer)
```
**描述：**

获取手势识别器的使能状态。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |

**返回：**

true - 使能。 false - 禁用。


### OH_ArkUI_GetGestureRecognizerState()

```
int32_t OH_ArkUI_GetGestureRecognizerState (ArkUI_GestureRecognizer * recognizer, ArkUI_GestureRecognizerState * state )
```
**描述：**

获取手势识别器的状态。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| state | 手势识别器的状态。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。


### OH_ArkUI_GetGestureTag()

```
int32_t OH_ArkUI_GetGestureTag (ArkUI_GestureRecognizer * recognizer, char * buffer, int32_t bufferSize, int32_t * result )
```
**描述：**

获取手势识别器的标记。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| buffer | 存储区。  |
| bufferSize | 存储区大小。  |
| result | 拷贝的字符串长度。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。 [ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH](_ark_u_i___native_module.md#arkui_errorcode) - 存储区大小不足。


### OH_ArkUI_GetNavDestinationId()

```
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationId (ArkUI_NodeHandle node, char * buffer, int32_t bufferSize, int32_t * writeLength )
```
**描述：**

获取当前节点所在的NavDestination组件的ID。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| buffer | 缓冲区，NavDestinationID写入该内存区域。  |
| bufferSize | 缓冲区大小。  |
| writeLength | 在返回ARKUI_ERROR_CODE_NO_ERROR时表示实际写入到缓冲区的字符串长度， 在返回ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR时表示可以容纳目标的最小缓冲区大小。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败，可能因为当前节点不在Navigation中。 ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR 给定的buffer size小于可以容纳目标的最小缓冲区大小。


### OH_ArkUI_GetNavDestinationIndex()

```
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationIndex (ArkUI_NodeHandle node, int32_t * index )
```
**描述：**

获取当前节点所在的NavDestination组件在页面栈的索引。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| index | 索引值，从0开始计数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败，可能因为当前节点不在Navigation中。


### OH_ArkUI_GetNavDestinationName()

```
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationName (ArkUI_NodeHandle node, char * buffer, int32_t bufferSize, int32_t * writeLength )
```
**描述：**

获取当前节点所在的NavDestination组件的名称。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| buffer | 缓冲区，被查询的NavDestination名称写入该内存区域。  |
| bufferSize | 缓冲区大小。  |
| writeLength | 在返回ARKUI_ERROR_CODE_NO_ERROR时表示实际写入到缓冲区的字符串长度， 在返回ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR时表示可以容纳目标的最小缓冲区大小。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败，可能因为当前节点不在Navigation中。 ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR 给定的buffer size小于可以容纳目标的最小缓冲区大小。


### OH_ArkUI_GetNavDestinationNameByIndex()

```
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationNameByIndex (ArkUI_NodeHandle node, int32_t index, char * buffer, int32_t bufferSize, int32_t * writeLength )
```
**描述：**

根据给定索引值，获取当前节点所在的Navigation栈中对应位置的页面名称。 索引值从0开始计数，0为栈底。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| index | 被查询NavDestination在栈中的索引。  |
| buffer | 缓冲区，被查询页面的名称写入该内存区域。  |
| bufferSize | 缓冲区大小。  |
| writeLength | 在返回ARKUI_ERROR_CODE_NO_ERROR时表示实际写入到缓冲区的字符串长度， 在返回ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR时表示可以容纳目标的最小缓冲区大小。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_NODE_INDEX_INVALID index为非法值。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败，可能因为当前节点不在Navigation中。 ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR 给定的buffer size小于可以容纳目标的最小缓冲区大小。


### OH_ArkUI_GetNavDestinationParam()

```
napi_value OH_ArkUI_GetNavDestinationParam (ArkUI_NodeHandle node)
```
**描述：**

获取当前节点所在的NavDestination组件的参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |

**返回：**

参数对象。


### OH_ArkUI_GetNavDestinationState()

```
ArkUI_ErrorCode OH_ArkUI_GetNavDestinationState (ArkUI_NodeHandle node, ArkUI_NavDestinationState * state )
```
**描述：**

获取当前节点所在的NavDestination组件的状态。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| state | NavDestination的状态值写回该参数中。  |

**返回：**

错误码 ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败，可能因为当前节点不在Navigation中。


### OH_ArkUI_GetNavigationId()

```
ArkUI_ErrorCode OH_ArkUI_GetNavigationId (ArkUI_NodeHandle node, char * buffer, int32_t bufferSize, int32_t * writeLength )
```
**描述：**

获取当前节点所在的Navigation组件的ID。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| buffer | 缓冲区，NavigationID写入该内存区域。  |
| bufferSize | 缓冲区大小。  |
| writeLength | 在返回ARKUI_ERROR_CODE_NO_ERROR时表示实际写入到缓冲区的字符串长度， 在返回ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR时表示可以容纳目标的最小缓冲区大小。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败，可能因为当前节点不在Navigation中。 ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR 给定的buffer size小于可以容纳目标的最小缓冲区大小。


### OH_ArkUI_GetNavStackLength()

```
ArkUI_ErrorCode OH_ArkUI_GetNavStackLength (ArkUI_NodeHandle node, int32_t * length )
```
**描述：**

根据给定索引值，获取当前节点所在的Navigation栈的长度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| length | 栈的长度。查询成功后将结果写回该参数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败，可能因为当前节点不在Navigation中。


### OH_ArkUI_GetNodeContentFromNapiValue()

```
int32_t OH_ArkUI_GetNodeContentFromNapiValue (napi_env env, napi_value value, ArkUI_NodeContentHandle * content )
```
**描述：**

获取ArkTS侧创建的NodeContent对象映射到Native侧的ArkUI_NodeContentHandle。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| env | napi的环境指针。  |
| value | ArkTS侧创建的NodeContent对象。  |
| context | ArkUI_NodeContentHandle指针。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_GetNodeHandleFromNapiValue()

```
int32_t OH_ArkUI_GetNodeHandleFromNapiValue (napi_env env, napi_value frameNode, ArkUI_NodeHandle * handle )
```
**描述：**

获取ArkTS侧创建的FrameNode节点对象映射到Native侧的ArkUI_NodeHandle。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| env | napi的环境指针。  |
| frameNode | ArkTS侧创建的FrameNode对象。  |
| handle | ArkUI_NodeHandle指针。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_GetPanGestureDirectionMask()

```
int32_t OH_ArkUI_GetPanGestureDirectionMask (ArkUI_GestureRecognizer * recognizer, ArkUI_GestureDirectionMask * directionMask )
```
**描述：**

获取滑动手势的滑动方向。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| directionMask | 滑动手势的滑动方向。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。


### OH_ArkUI_GetResponseRecognizersFromInterruptInfo()

```
int32_t OH_ArkUI_GetResponseRecognizersFromInterruptInfo (const ArkUI_GestureInterruptInfo * event, ArkUI_GestureRecognizerHandleArray * responseChain, int32_t * count )
```
**描述：**

获取手势响应链的信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势打断回调事件。  |
| responseChain | 响应链组件上的手势识别器。  |
| count | 响应链组件上的手势识别器的数量。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。


### OH_ArkUI_GetRouterPageId()

```
ArkUI_ErrorCode OH_ArkUI_GetRouterPageId (ArkUI_NodeHandle node, char * buffer, int32_t bufferSize, int32_t * writeLength )
```
**描述：**

获取当前节点所在页面的Page组件的ID。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| buffer | 缓冲区，Page Id写入该内存区域。  |
| bufferSize | 缓冲区大小。  |
| writeLength | 在返回ARKUI_ERROR_CODE_NO_ERROR时表示实际写入到缓冲区的字符串长度， 在返回ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR时表示可以容纳目标的最小缓冲区大小。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败。 ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR 给定的buffer size小于可以容纳目标的最小缓冲区大小。


### OH_ArkUI_GetRouterPageIndex()

```
ArkUI_ErrorCode OH_ArkUI_GetRouterPageIndex (ArkUI_NodeHandle node, int32_t * index )
```
**描述：**

获取当前节点所在页面在Router页面栈中的索引。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| index | 索引值，从1开始计数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败，可能因为当前节点不在Navigation中。


### OH_ArkUI_GetRouterPageName()

```
ArkUI_ErrorCode OH_ArkUI_GetRouterPageName (ArkUI_NodeHandle node, char * buffer, int32_t bufferSize, int32_t * writeLength )
```
**描述：**

获取当前节点所在页面的名称。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| buffer | 缓冲区，页面名称写入该内存区域。  |
| bufferSize | 缓冲区大小。  |
| writeLength | 在返回ARKUI_ERROR_CODE_NO_ERROR时表示实际写入到缓冲区的字符串长度， 在返回ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR时表示可以容纳目标的最小缓冲区大小。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败。 ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR 给定的buffer size小于可以容纳目标的最小缓冲区大小。


### OH_ArkUI_GetRouterPagePath()

```
ArkUI_ErrorCode OH_ArkUI_GetRouterPagePath (ArkUI_NodeHandle node, char * buffer, int32_t bufferSize, int32_t * writeLength )
```
**描述：**

获取当前节点所在页面的Page组件的路径。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| buffer | 缓冲区，Page Path写入该内存区域。  |
| bufferSize | 缓冲区大小。  |
| writeLength | 在返回ARKUI_ERROR_CODE_NO_ERROR时表示实际写入到缓冲区的字符串长度， 在返回ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR时表示可以容纳目标的最小缓冲区大小。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败。 ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR 给定的buffer size小于可以容纳目标的最小缓冲区大小。


### OH_ArkUI_GetRouterPageState()

```
ArkUI_ErrorCode OH_ArkUI_GetRouterPageState (ArkUI_NodeHandle node, ArkUI_RouterPageState * state )
```
**描述：**

获取当前节点所在页面的Page组件的状态。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| state | Router Page的状态值写回该参数中。  |

**返回：**

错误码 ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_GET_INFO_FAILED 查询信息失败。


### OH_ArkUI_GuidelineOption_Create()

```
ArkUI_GuidelineOption* OH_ArkUI_GuidelineOption_Create (int32_t size)
```
**描述：**

创建RelativeContaine容器内的辅助线信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| size | 辅助线数量。  |

**返回：**

辅助线信息。


### OH_ArkUI_GuidelineOption_Dispose()

```
void OH_ArkUI_GuidelineOption_Dispose (ArkUI_GuidelineOption * guideline)
```
**描述：**

销毁辅助线信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| guideline | 辅助线信息。  |


### OH_ArkUI_GuidelineOption_GetDirection()

```
ArkUI_Axis OH_ArkUI_GuidelineOption_GetDirection (ArkUI_GuidelineOption * guideline, int32_t index )
```
**描述：**

获取辅助线的方向。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| guideline | 辅助线信息。  |
| index | 辅助线索引值。  |

**返回：**

方向。


### OH_ArkUI_GuidelineOption_GetId()

```
const char* OH_ArkUI_GuidelineOption_GetId (ArkUI_GuidelineOption * guideline, int32_t index )
```
**描述：**

获取辅助线的Id。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| guideline | 辅助线信息。  |
| index | 辅助线索引值。  |

**返回：**

Id。


### OH_ArkUI_GuidelineOption_GetPositionEnd()

```
float OH_ArkUI_GuidelineOption_GetPositionEnd (ArkUI_GuidelineOption * guideline, int32_t index )
```
**描述：**

获取距离容器右侧或者底部的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| guideline | 辅助线信息。  |
| index | 辅助线索引值。  |

**返回：**

距离容器右侧或者底部的距离。


### OH_ArkUI_GuidelineOption_GetPositionStart()

```
float OH_ArkUI_GuidelineOption_GetPositionStart (ArkUI_GuidelineOption * guideline, int32_t index )
```
**描述：**

获取距离容器左侧或者顶部的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| guideline | 辅助线信息。  |
| index | 辅助线索引值。  |

**返回：**

距离容器左侧或者顶部的距离。


### OH_ArkUI_GuidelineOption_SetDirection()

```
void OH_ArkUI_GuidelineOption_SetDirection (ArkUI_GuidelineOption * guideline, ArkUI_Axis value, int32_t index )
```
**描述：**

设置辅助线的方向。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| guideline | 辅助线信息。  |
| value | 方向。  |
| index | 辅助线索引值。  |


### OH_ArkUI_GuidelineOption_SetId()

```
void OH_ArkUI_GuidelineOption_SetId (ArkUI_GuidelineOption * guideline, const char * value, int32_t index )
```
**描述：**

设置辅助线的Id。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| guideline | 辅助线信息。  |
| value | id，必须是唯一的并且不可与容器内组件重名。  |
| index | 辅助线索引值。  |


### OH_ArkUI_GuidelineOption_SetPositionEnd()

```
void OH_ArkUI_GuidelineOption_SetPositionEnd (ArkUI_GuidelineOption * guideline, float value, int32_t index )
```
**描述：**

设置距离容器右侧或者底部的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| guideline | 辅助线信息。  |
| value | 距离容器右侧或者底部的距离。  |
| index | 辅助线索引值。  |


### OH_ArkUI_GuidelineOption_SetPositionStart()

```
void OH_ArkUI_GuidelineOption_SetPositionStart (ArkUI_GuidelineOption * guideline, float value, int32_t index )
```
**描述：**

设置距离容器左侧或者顶部的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| guideline | 辅助线信息。  |
| value | 距离容器左侧或者顶部的距离。  |
| index | 辅助线索引值。  |


### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor()

```
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor (ArkUI_DrawableDescriptor * drawable)
```
**描述：**

使用 DrawableDescriptor 对象创建帧图片信息，图片格式为Resource和PixelMap。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| drawable | 使用Resource或PixelMap创建的ArkUI_DrawableDescriptor对象指针。  |

**返回：**

帧图片对象指针。


### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString()

```
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString (char * src)
```
**描述：**

使用图片路径创建帧图片信息，图片格式为svg，png和jpg。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| src | 图片路径。  |

**返回：**

帧图片对象指针。


### OH_ArkUI_ImageAnimatorFrameInfo_Dispose()

```
void OH_ArkUI_ImageAnimatorFrameInfo_Dispose (ArkUI_ImageAnimatorFrameInfo * imageInfo)
```
**描述：**

销毁帧图片对象指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |


### OH_ArkUI_ImageAnimatorFrameInfo_GetDuration()

```
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetDuration (ArkUI_ImageAnimatorFrameInfo * imageInfo)
```
**描述：**

获取图片的播放时长。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |

**返回：**

图片的播放时长，单位为毫秒，imageInfo为空指针时返回0。


### OH_ArkUI_ImageAnimatorFrameInfo_GetHeight()

```
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetHeight (ArkUI_ImageAnimatorFrameInfo * imageInfo)
```
**描述：**

获取图片高度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |

**返回：**

图片高度，单位为PX，imageInfo为空指针时返回0。


### OH_ArkUI_ImageAnimatorFrameInfo_GetLeft()

```
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetLeft (ArkUI_ImageAnimatorFrameInfo * imageInfo)
```
**描述：**

获取图片相对于组件左上角的横向坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |

**返回：**

图片相对于组件左上角的横向坐标，单位为PX，imageInfo为空指针时返回0。


### OH_ArkUI_ImageAnimatorFrameInfo_GetTop()

```
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetTop (ArkUI_ImageAnimatorFrameInfo * imageInfo)
```
**描述：**

获取图片相对于组件左上角的纵向坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |

**返回：**

图片相对于组件左上角的纵向坐标，单位为PX，imageInfo为空指针时返回0。


### OH_ArkUI_ImageAnimatorFrameInfo_GetWidth()

```
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetWidth (ArkUI_ImageAnimatorFrameInfo * imageInfo)
```
**描述：**

获取图片宽度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |

**返回：**

图片宽度，单位为PX，imageInfo为空指针时返回0。


### OH_ArkUI_ImageAnimatorFrameInfo_SetDuration()

```
void OH_ArkUI_ImageAnimatorFrameInfo_SetDuration (ArkUI_ImageAnimatorFrameInfo * imageInfo, int32_t duration )
```
**描述：**

设置图片的播放时长。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |
| duration | 图片的播放时长，单位为毫秒。  |


### OH_ArkUI_ImageAnimatorFrameInfo_SetHeight()

```
void OH_ArkUI_ImageAnimatorFrameInfo_SetHeight (ArkUI_ImageAnimatorFrameInfo * imageInfo, int32_t height )
```
**描述：**

设置图片高度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |
| height | 图片高度，单位为PX。  |


### OH_ArkUI_ImageAnimatorFrameInfo_SetLeft()

```
void OH_ArkUI_ImageAnimatorFrameInfo_SetLeft (ArkUI_ImageAnimatorFrameInfo * imageInfo, int32_t left )
```
**描述：**

设置图片相对于组件左上角的横向坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |
| left | 图片相对于组件左上角的横向坐标，单位为PX。  |


### OH_ArkUI_ImageAnimatorFrameInfo_SetTop()

```
void OH_ArkUI_ImageAnimatorFrameInfo_SetTop (ArkUI_ImageAnimatorFrameInfo * imageInfo, int32_t top )
```
**描述：**

设置图片相对于组件左上角的纵向坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |
| top | 图片相对于组件左上角的纵向坐标，单位为PX。  |


### OH_ArkUI_ImageAnimatorFrameInfo_SetWidth()

```
void OH_ArkUI_ImageAnimatorFrameInfo_SetWidth (ArkUI_ImageAnimatorFrameInfo * imageInfo, int32_t width )
```
**描述：**

设置图片宽度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| imageInfo | 帧图片对象指针。  |
| width | 图片宽度，单位为PX。  |


### OH_ArkUI_IsBuiltInGesture()

```
bool OH_ArkUI_IsBuiltInGesture (ArkUI_GestureRecognizer * recognizer)
```
**描述：**

当前手势是否为系统内置手势。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |

**返回：**

true - 是系统内置手势。 false - 不是系统内置手势。


### OH_ArkUI_IsGestureRecognizerValid()

```
bool OH_ArkUI_IsGestureRecognizerValid (ArkUI_GestureRecognizer * recognizer)
```
**描述：**

当前手势识别器是否有效。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |

**返回：**

true - 手势识别器有效。 false - 手势识别器无效。


### OH_ArkUI_KeyEvent_GetKeyCode()

```
int32_t OH_ArkUI_KeyEvent_GetKeyCode (const ArkUI_UIInputEvent * event)
```
**描述：**

获取按键的键码。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |

**返回：**

按键的键码。


### OH_ArkUI_KeyEvent_GetKeyIntensionCode()

```
ArkUI_KeyIntension OH_ArkUI_KeyEvent_GetKeyIntensionCode (const ArkUI_UIInputEvent * event)
```
**描述：**

获取按键对应的意图。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |

**返回：**

ArkUI_KeyIntension 按键对应的意图。


### OH_ArkUI_KeyEvent_GetKeySource()

```
ArkUI_KeySourceType OH_ArkUI_KeyEvent_GetKeySource (const ArkUI_UIInputEvent * event)
```
**描述：**

获取当前按键的输入设备类型。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |

**返回：**

ArkUI_KeySourceType 当前按键的输入设备类型。


### OH_ArkUI_KeyEvent_GetKeyText()

```
const char* OH_ArkUI_KeyEvent_GetKeyText (const ArkUI_UIInputEvent * event)
```
**描述：**

获取按键的键值。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |

**返回：**

按键的键值。


### OH_ArkUI_KeyEvent_GetType()

```
ArkUI_KeyEventType OH_ArkUI_KeyEvent_GetType (const ArkUI_UIInputEvent * event)
```
**描述：**

获取按键的类型。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |

**返回：**

ArkUI_KeyEventType 按键的类型。


### OH_ArkUI_KeyEvent_GetUnicode()

```
uint32_t OH_ArkUI_KeyEvent_GetUnicode (const ArkUI_UIInputEvent * event)
```
**描述：**

获取按键的unicode码值。支持范围为非空格的基本拉丁字符：0x0021-0x007E，不支持字符为0。组合键场景下，返回当前keyEvent对应按键的unicode码值。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |

**返回：**

unicode码值。


### OH_ArkUI_KeyEvent_SetConsumed()

```
void OH_ArkUI_KeyEvent_SetConsumed (const ArkUI_UIInputEvent * event, bool isConsumed )
```
**描述：**

在按键事件回调中，设置事件是否被该回调消费

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |
| isConsumed | 是否被消费。true表示事件被消费，false表示事件未被消费。  |


### OH_ArkUI_KeyEvent_StopPropagation()

```
void OH_ArkUI_KeyEvent_StopPropagation (const ArkUI_UIInputEvent * event, bool stopPropagation )
```
**描述：**

阻塞事件冒泡传递。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |
| stopPropagation | 表示是否阻止事件冒泡。true表示阻止事件冒泡，false表示不阻止事件冒泡。  |


### OH_ArkUI_KeyEvent_Dispatch()

```
void OH_ArkUI_KeyEvent_Dispatch(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)
```
**描述：**

将按键事件分发到特定组件节点。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 需要注册事件的节点对象。  |
| event | ArkUI_UIInputEvent事件指针。  |

### OH_ArkUI_KeyEvent_IsNumLockOn()

```
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsNumLockOn(const ArkUI_UIInputEvent* event, bool* state)
```
**描述：**

获取按键事件发生时NumLock的状态。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |
| state | 输出参数，返回NumLock的状态。true表示处于激活状态，false表示处于未激活状态。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。

### OH_ArkUI_KeyEvent_IsCapsLockOn()

```
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsCapsLockOn(const ArkUI_UIInputEvent* event, bool* state)
```
**描述：**

获取按键事件发生时CapsLock的状态。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |
| state | 输出参数，返回CapsLock的状态。true表示处于激活状态，false表示处于未激活状态。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。

### OH_ArkUI_KeyEvent_IsScrollLockOn()

```
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsScrollLockOn(const ArkUI_UIInputEvent* event, bool* state)
```
**描述：**

获取按键事件发生时ScrollLock的状态。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_UIInputEvent事件指针。  |
| state | 输出参数，返回ScrollLock的状态。true表示处于激活状态，false表示处于未激活状态。 |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。

### OH_ArkUI_KeyframeAnimateOption_Create()

```
ArkUI_KeyframeAnimateOption* OH_ArkUI_KeyframeAnimateOption_Create (int32_t size)
```
**描述：**

获取关键帧动画参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| size | 关键帧动画状态数。  |

**返回：**

关键帧动画参数对象。size小于0时返回NULL。


### OH_ArkUI_KeyframeAnimateOption_Dispose()

```
void OH_ArkUI_KeyframeAnimateOption_Dispose (ArkUI_KeyframeAnimateOption * option)
```
**描述：**

销毁关键帧动画参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数对象。  |


### OH_ArkUI_KeyframeAnimateOption_GetCurve()

```
ArkUI_CurveHandle OH_ArkUI_KeyframeAnimateOption_GetCurve (ArkUI_KeyframeAnimateOption * option, int32_t index )
```
**描述：**

获取关键帧动画某段状态动画曲线。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |
| index | 状态索引值。  |

**返回：**

动画曲线。


### OH_ArkUI_KeyframeAnimateOption_GetDelay()

```
int32_t OH_ArkUI_KeyframeAnimateOption_GetDelay (ArkUI_KeyframeAnimateOption * option)
```
**描述：**

获取关键帧整体延时时间。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |

**返回：**

整体延时时间。


### OH_ArkUI_KeyframeAnimateOption_GetDuration()

```
int32_t OH_ArkUI_KeyframeAnimateOption_GetDuration (ArkUI_KeyframeAnimateOption * option, int32_t index )
```
**描述：**

获取关键帧动画某段状态持续时间。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |
| index | 状态索引值。  |

**返回：**

持续时间。单位为毫秒。


### OH_ArkUI_KeyframeAnimateOption_GetIterations()

```
int32_t OH_ArkUI_KeyframeAnimateOption_GetIterations (ArkUI_KeyframeAnimateOption * option)
```
**描述：**

获取关键帧动画播放次数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |

**返回：**

动画播放次数。

### OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate()

```
ArkUI_ExpectedFrameRateRange* OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate(ArkUI_KeyframeAnimateOption* option)
```
**描述：**

获取关键帧动画参数的期望帧率。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |

**返回：**

关键帧动画参数的期望帧率。


### OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback()

```
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback (ArkUI_KeyframeAnimateOption * option, void * userData, void(*)(void *userData) event, int32_t index )
```
**描述：**

设置关键帧时刻状态的闭包函数，即在该关键帧时刻要达到的状态。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |
| event | 闭包函数。  |
| userData | 用户定义对象指针。  |
| index | 状态索引值。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback()

```
int32_t OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback (ArkUI_KeyframeAnimateOption * option, void * userData, void(*)(void *userData) onFinish )
```
**描述：**

设置关键帧动画播放完成回调。当keyframe动画所有次数播放完成后调用。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |
| userData | 用户自定义对象指针。  |
| onFinish | 回调方法。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_KeyframeAnimateOption_SetCurve()

```
int32_t OH_ArkUI_KeyframeAnimateOption_SetCurve (ArkUI_KeyframeAnimateOption * option, ArkUI_CurveHandle value, int32_t index )
```
**描述：**

设置关键帧动画某段关键帧使用的动画曲线。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |
| value | 该关键帧使用的动画曲线。默认值：EASE_IN_OUT。  |
| index | 状态索引值。  |

**注解：**

由于springMotion、responsiveSpringMotion、interpolatingSpring曲线时长不生效，故不支持这三种曲线。

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_KeyframeAnimateOption_SetDelay()

```
int32_t OH_ArkUI_KeyframeAnimateOption_SetDelay (ArkUI_KeyframeAnimateOption * option, int32_t value )
```
**描述：**

设置关键帧动画的整体延时时间，单位为ms(毫秒)，默认不延时播放。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |
| value | 延时时间, 单位为ms(毫秒)。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_KeyframeAnimateOption_SetDuration()

```
int32_t OH_ArkUI_KeyframeAnimateOption_SetDuration (ArkUI_KeyframeAnimateOption * option, int32_t value, int32_t index )
```
**描述：**

设置关键帧动画某段关键帧动画的持续时间，单位为毫秒。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |
| value | 持续时间。单位为毫秒。  |
| index | 状态索引值。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_KeyframeAnimateOption_SetIterations()

```
int32_t OH_ArkUI_KeyframeAnimateOption_SetIterations (ArkUI_KeyframeAnimateOption * option, int32_t value )
```
**描述：**

设置关键帧动画的动画播放次数。默认播放一次，设置为-1时表示无限次播放。设置为0时表示无动画效果。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |
| value | 动画播放次数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。

### OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate()

```
int32_t OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate(
    ArkUI_KeyframeAnimateOption* option, ArkUI_ExpectedFrameRateRange* frameRate)
```
**描述：**

设置关键帧动画期望帧率。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 关键帧动画参数。  |
| frameRate | 关键帧动画的期望帧率。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_LayoutConstraint_Copy()

```
ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Copy (const ArkUI_LayoutConstraint * Constraint)
```
**描述：**

约束尺寸深拷贝。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |

**返回：**

新的约束尺寸指针。


### OH_ArkUI_LayoutConstraint_Create()

```
ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Create ()
```
**描述：**

创建约束尺寸。

**起始版本：** 12


### OH_ArkUI_LayoutConstraint_Dispose()

```
void* OH_ArkUI_LayoutConstraint_Dispose (ArkUI_LayoutConstraint * Constraint)
```
**描述：**

销毁约束尺寸指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |


### OH_ArkUI_LayoutConstraint_GetMaxHeight()

```
int32_t OH_ArkUI_LayoutConstraint_GetMaxHeight (const ArkUI_LayoutConstraint * Constraint)
```
**描述：**

通过约束尺寸获取最大高度，单位为px。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |

**返回：**

最大高度。


### OH_ArkUI_LayoutConstraint_GetMaxWidth()

```
int32_t OH_ArkUI_LayoutConstraint_GetMaxWidth (const ArkUI_LayoutConstraint * Constraint)
```
**描述：**

通过约束尺寸获取最大宽度，单位为px。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |

**返回：**

最大宽度。


### OH_ArkUI_LayoutConstraint_GetMinHeight()

```
int32_t OH_ArkUI_LayoutConstraint_GetMinHeight (const ArkUI_LayoutConstraint * Constraint)
```
**描述：**

通过约束尺寸获取最小高度，单位为px。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |

**返回：**

最小高度。


### OH_ArkUI_LayoutConstraint_GetMinWidth()

```
int32_t OH_ArkUI_LayoutConstraint_GetMinWidth (const ArkUI_LayoutConstraint * Constraint)
```
**描述：**

通过约束尺寸获取最小宽度，单位为px。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |

**返回：**

最小宽度。


### OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight()

```
int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight (const ArkUI_LayoutConstraint * Constraint)
```
**描述：**

通过约束尺寸获取高度百分比基准，单位为px。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |

**返回：**

高度百分比基准。


### OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth()

```
int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth (const ArkUI_LayoutConstraint * Constraint)
```
**描述：**

通过约束尺寸获取宽度百分比基准，单位为px。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |

**返回：**

宽度百分比基准。


### OH_ArkUI_LayoutConstraint_SetMaxHeight()

```
void OH_ArkUI_LayoutConstraint_SetMaxHeight (ArkUI_LayoutConstraint * Constraint, int32_t value )
```
**描述：**

设置最大高度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |
| value | 最大高度，单位为px。  |


### OH_ArkUI_LayoutConstraint_SetMaxWidth()

```
void OH_ArkUI_LayoutConstraint_SetMaxWidth (ArkUI_LayoutConstraint * Constraint, int32_t value )
```
**描述：**

设置最大宽度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |
| value | 最大宽度，单位为px。  |


### OH_ArkUI_LayoutConstraint_SetMinHeight()

```
void OH_ArkUI_LayoutConstraint_SetMinHeight (ArkUI_LayoutConstraint * Constraint, int32_t value )
```
**描述：**

设置最小高度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |
| value | 最小高度，单位为px。  |


### OH_ArkUI_LayoutConstraint_SetMinWidth()

```
void OH_ArkUI_LayoutConstraint_SetMinWidth (ArkUI_LayoutConstraint * Constraint, int32_t value )
```
**描述：**

设置最小宽度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |
| value | 最小宽度，单位为px。  |


### OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight()

```
void OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight (ArkUI_LayoutConstraint * Constraint, int32_t value )
```
**描述：**

设置高度百分比基准。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |
| value | 高度百分比基准，单位为px。  |


### OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth()

```
void OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth (ArkUI_LayoutConstraint * Constraint, int32_t value )
```
**描述：**

设置宽度百分比基准。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| Constraint | 约束尺寸。  |
| value | 宽度百分比基准，单位为px。  |


### OH_ArkUI_List_CloseAllSwipeActions()

```
int32_t OH_ArkUI_List_CloseAllSwipeActions (ArkUI_NodeHandle node, void * userData, void(*)(void *userData) onFinish )
```
**描述：**

收起展开状态下的ListItem。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 需要注册事件的节点对象。  |
| userData | 自定义事件参数，当事件触发时在回调参数中携带回来。  |
| onFinish | 在收起动画完成后触发的回调。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED 组件不支持该事件。


### OH_ArkUI_ListChildrenMainSizeOption_Create()

```
ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create ()
```
**描述：**

创建ListChildrenMainSize接口设置的配置项。

**起始版本：** 12

**返回：**

ListChildrenMainSize配置项实例。

### OH_ArkUI_ListChildrenMainSizeOption_Dispose()

```
void OH_ArkUI_ListChildrenMainSizeOption_Dispose (ArkUI_ListChildrenMainSize * option)
```
**描述：**

销毁ListChildrenMainSize实例。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 要销毁的ListChildrenMainSize实例。  |


### OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize()

```
float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize (ArkUI_ListChildrenMainSize * option)
```
**描述：**

获取List组件的ChildrenMainSizeOption默认大小。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListChildrenMainSize实例。  |

**返回：**

List下的ListItem的默认大小，默认为0，单位为vp，option为空指针时返回-1。


### OH_ArkUI_ListChildrenMainSizeOption_GetMainSize()

```
float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize (ArkUI_ListChildrenMainSize * option, int32_t index )
```
**描述：**

获取List组件的ChildrenMainSizeOption数组的值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListChildrenMainSize实例。  |
| index | 要获取的值的下标位置。  |

**返回：**

数组具体位置的值。若函数参数异常，返回-1。


### OH_ArkUI_ListChildrenMainSizeOption_Resize()

```
void OH_ArkUI_ListChildrenMainSizeOption_Resize (ArkUI_ListChildrenMainSize * option, int32_t totalSize )
```
**描述：**

重置List组件的ChildrenMainSizeOption的数组大小。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListChildrenMainSize实例。  |
| totalSize | 数组大小。  |


### OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize()

```
int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize (ArkUI_ListChildrenMainSize * option, float defaultMainSize )
```
**描述：**

设置List组件的ChildrenMainSizeOption默认大小。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListChildrenMainSize实例。  |
| defaultMainSize | List下的ListItem的默认大小，单位为vp。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_ListChildrenMainSizeOption_Splice()

```
int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice (ArkUI_ListChildrenMainSize * option, int32_t index, int32_t deleteCount, int32_t addCount )
```
**描述：**

对List组件的ChildrenMainSizeOption数组操作大小调整。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListChildrenMainSize实例。  |
| index | 要修改MainSize的数组起始位置。  |
| deleteCount | 要删除的MainSize数组从index开始的数量。  |
| addCount | 要添加的MainSize数组从index开始的数量。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_ListChildrenMainSizeOption_UpdateSize()

```
int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize (ArkUI_ListChildrenMainSize * option, int32_t index, float mainSize )
```
**描述：**

更新List组件的ChildrenMainSizeOption数组的值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListChildrenMainSize实例。  |
| index | 要修改MainSize的数组起始位置。  |
| mainSize | 实际修改的值。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_ListItemSwipeActionItem_Create()

```
ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create ()
```
**描述：**

创建ListItemSwipeActionItem接口设置的配置项。

**起始版本：** 12

**返回：**

ListItemSwipeActionItem配置项实例。


### OH_ArkUI_ListItemSwipeActionItem_Dispose()

```
void OH_ArkUI_ListItemSwipeActionItem_Dispose (ArkUI_ListItemSwipeActionItem * item)
```
**描述：**

销毁ListItemSwipeActionItem实例。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | 要销毁的ListItemSwipeActionItem实例。  |


### OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance()

```
float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance (ArkUI_ListItemSwipeActionItem * item)
```
**描述：**

获取组件长距离滑动删除距离阈值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |

**返回：**

组件长距离滑动删除距离阈值。异常时返回值：0。


### OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance()

```
void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance (ArkUI_ListItemSwipeActionItem * item, float distance )
```
**描述：**

设置组件长距离滑动删除距离阈值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| distance | 组件长距离滑动删除距离阈值。  |


### OH_ArkUI_ListItemSwipeActionItem_SetContent()

```
void OH_ArkUI_ListItemSwipeActionItem_SetContent (ArkUI_ListItemSwipeActionItem * item, ArkUI_NodeHandle node )
```
**描述：**

设置ListItemSwipeActionItem的布局内容。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| node | 布局信息。  |


### OH_ArkUI_ListItemSwipeActionItem_SetOnAction()

```
void OH_ArkUI_ListItemSwipeActionItem_SetOnAction (ArkUI_ListItemSwipeActionItem * item, void(*)() callback )
```
**描述：**

设置组件进入长距删除区后删除ListItem时调用的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| callback | 回调事件  |


### OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData()

```
void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData (ArkUI_ListItemSwipeActionItem * item, void * userData, void(*)(void *userData) callback )
```
**描述：**

设置组件进入长距删除区后删除ListItem时调用的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| userData | 用户自定义数据。  |
| callback | 回调事件  |


### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea()

```
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea (ArkUI_ListItemSwipeActionItem * item, void(*)() callback )
```
**描述：**

设置滑动条目进入删除区域时调用的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| callback | 回调事件  |


### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData()

```
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData (ArkUI_ListItemSwipeActionItem * item, void * userData, void(*)(void *userData) callback )
```
**描述：**

设置滑动条目进入删除区域时调用的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| userData | 用户自定义数据。  |
| callback | 回调事件  |


### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea()

```
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea (ArkUI_ListItemSwipeActionItem * item, void(*)() callback )
```
**描述：**

设置滑动条目退出删除区域时调用的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| callback | 回调事件  |


### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData()

```
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData (ArkUI_ListItemSwipeActionItem * item, void * userData, void(*)(void *userData) callback )
```
**描述：**

设置滑动条目退出删除区域时调用的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| userData | 用户自定义数据。  |
| callback | 回调事件  |


### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange()

```
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange (ArkUI_ListItemSwipeActionItem * item, void(*)(ArkUI_ListItemSwipeActionState swipeActionState) callback )
```
**描述：**

设置列表项滑动状态变化时候触发的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| callback | 回调事件 swipeActionState 变化后的状态。  |


### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData()

```
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData (ArkUI_ListItemSwipeActionItem * item, void * userData, void(*)(ArkUI_ListItemSwipeActionState swipeActionState, void *userData) callback )
```
**描述：**

设置列表项滑动状态变化时候触发的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| item | ListItemSwipeActionItem实例。  |
| userData | 用户自定义数据。  |
| callback | 回调事件 swipeActionState 变化后的状态。  |


### OH_ArkUI_ListItemSwipeActionOption_Create()

```
ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create ()
```
**描述：**

创建ListItemSwipeActionOption接口设置的配置项。

**起始版本：** 12

**返回：**

ListItemSwipeActionOption配置项实例。


### OH_ArkUI_ListItemSwipeActionOption_Dispose()

```
void OH_ArkUI_ListItemSwipeActionOption_Dispose (ArkUI_ListItemSwipeActionOption * option)
```
**描述：**

销毁ListItemSwipeActionOption实例。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 要销毁的ListItemSwipeActionOption实例。  |


### OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect()

```
int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect (ArkUI_ListItemSwipeActionOption * option)
```
**描述：**

获取滑动效果。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListItemSwipeActionItem实例。  |

**返回：**

滑动效果。默认返回值：ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING。


### OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect()

```
void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect (ArkUI_ListItemSwipeActionOption * option, ArkUI_ListItemSwipeEdgeEffect edgeEffect )
```
**描述：**

设置滑动效果。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListItemSwipeActionItem实例。  |
| edgeEffect | 滑动效果。  |


### OH_ArkUI_ListItemSwipeActionOption_SetEnd()

```
void OH_ArkUI_ListItemSwipeActionOption_SetEnd (ArkUI_ListItemSwipeActionOption * option, ArkUI_ListItemSwipeActionItem * item )
```
**描述：**

设置ListItemSwipeActionItem的右侧（垂直布局）或下方（横向布局）布局内容。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListItemSwipeActionItem实例。  | 
| item | 布局信息。  | 


### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange()

```
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange (ArkUI_ListItemSwipeActionOption * option, void(*)(float offset) callback )
```
**描述：**

滑动操作偏移量更改时调用的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListItemSwipeActionItem实例。  |
| callback | 回调事件 offset 滑动偏移量。  |


### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData()

```
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData (ArkUI_ListItemSwipeActionOption * option, void * userData, void(*)(float offset, void *userData) callback )
```
**描述：**

滑动操作偏移量更改时调用的事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListItemSwipeActionItem实例。  |
| userData | 用户自定义数据。  |
| callback | 回调事件 offset 滑动偏移量。  |


### OH_ArkUI_ListItemSwipeActionOption_SetStart()

```
void OH_ArkUI_ListItemSwipeActionOption_SetStart (ArkUI_ListItemSwipeActionOption * option, ArkUI_ListItemSwipeActionItem * item )
```
**描述：**

设置ListItemSwipeActionItem的左侧（垂直布局）或上方（横向布局）布局内容。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ListItemSwipeActionItem实例。  | 
| item | 布局信息。  | 


### OH_ArkUI_LongPress_GetRepeatCount()

```
int32_t OH_ArkUI_LongPress_GetRepeatCount (const ArkUI_GestureEvent * event)
```
**描述：**

返回长按手势定时触发次数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

长按手势定时触发次数。


### OH_ArkUI_MarshallStyledStringDescriptor()

```
int32_t OH_ArkUI_MarshallStyledStringDescriptor (uint8_t * buffer, size_t bufferSize, ArkUI_StyledString_Descriptor * descriptor, size_t * resultSize )
```
**描述：**

将属性字符串信息序列化为字节数组。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| buffer | 字节数组，用于存储属性字符串序列化后的数据。  |
| bufferSize | 字节数组长度。  |
| descriptor | 指向ArkUI_StyledString_Descriptor对象的指针。  |
| resultSize | 属性字符串转换后的字节数组实际长度。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 ARKUI_ERROR_CODE_INVALID_STYLED_STRING 无效的属性字符串。


### OH_ArkUI_NodeAdapter_Create()

```
ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create ()
```
**描述：**

创建组件适配器对象。

**起始版本：** 12

**返回：**

组件适配器对象。


### OH_ArkUI_NodeAdapter_Dispose()

```
void OH_ArkUI_NodeAdapter_Dispose (ArkUI_NodeAdapterHandle handle)
```
**描述：**

销毁组件适配器对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |


### OH_ArkUI_NodeAdapter_GetAllItems()

```
int32_t OH_ArkUI_NodeAdapter_GetAllItems (ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle ** items, uint32_t * size )
```
**描述：**

获取存储在Adapter中的所有元素。

接口调用会返回元素的数组对象指针，该指针指向的内存数据需要开发者手动释放。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |
| items | 适配器内节点数组。  |
| size | 元素数量。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeAdapter_GetTotalNodeCount()

```
uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount (ArkUI_NodeAdapterHandle handle)
```
**描述：**

获取Adapter中的元素总数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |

**返回：**

Adapter中的元素总数。


### OH_ArkUI_NodeAdapter_InsertItem()

```
int32_t OH_ArkUI_NodeAdapter_InsertItem (ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount )
```
**描述：**

通知Adapter进行局部元素插入。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |
| startPosition | 元素插入起始位置。  |
| itemCount | 元素插入数量。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeAdapter_MoveItem()

```
int32_t OH_ArkUI_NodeAdapter_MoveItem (ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to )
```
**描述：**

通知Adapter进行局部元素移位。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |
| from | 元素移位起始位置。  |
| to | 元素移位结束位置。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeAdapter_RegisterEventReceiver()

```
int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver (ArkUI_NodeAdapterHandle handle, void * userData, void(*)(ArkUI_NodeAdapterEvent *event) receiver )
```
**描述：**

注册Adapter相关回调事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |
| userData | 自定义数据。  |
| receiver | 事件接收回调。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeAdapter_ReloadAllItems()

```
int32_t OH_ArkUI_NodeAdapter_ReloadAllItems (ArkUI_NodeAdapterHandle handle)
```
**描述：**

通知Adapter进行全量元素变化。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeAdapter_ReloadItem()

```
int32_t OH_ArkUI_NodeAdapter_ReloadItem (ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount )
```
**描述：**

通知Adapter进行局部元素变化。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |
| startPosition | 元素变化起始位置。  |
| itemCount | 元素变化数量。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeAdapter_RemoveItem()

```
int32_t OH_ArkUI_NodeAdapter_RemoveItem (ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount )
```
**描述：**

通知Adapter进行局部元素删除。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |
| startPosition | 元素删除起始位置。  |
| itemCount | 元素删除数量。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeAdapter_SetTotalNodeCount()

```
int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount (ArkUI_NodeAdapterHandle handle, uint32_t size )
```
**描述：**

设置Adapter中的元素总数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |
| size | 元素数量。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeAdapter_UnregisterEventReceiver()

```
void OH_ArkUI_NodeAdapter_UnregisterEventReceiver (ArkUI_NodeAdapterHandle handle)
```
**描述：**

注销Adapter相关回调事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 组件适配器对象。  |


### OH_ArkUI_NodeAdapterEvent_GetHostNode()

```
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode (ArkUI_NodeAdapterEvent * event)
```
**描述：**

获取使用该适配器的滚动类容器节点。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 适配器事件对象。  |

**返回：**

适配器的滚动类容器节点。


### OH_ArkUI_NodeAdapterEvent_GetItemIndex()

```
uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex (ArkUI_NodeAdapterEvent * event)
```
**描述：**

获取适配器事件时需要操作的元素序号。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 适配器事件对象。  |

**返回：**

元素序号。


### OH_ArkUI_NodeAdapterEvent_GetRemovedNode()

```
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode (ArkUI_NodeAdapterEvent * event)
```
**描述：**

获取需要销毁的事件中待销毁的元素。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 适配器事件对象。  |

**返回：**

待销毁的元素。


### OH_ArkUI_NodeAdapterEvent_GetType()

```
ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType (ArkUI_NodeAdapterEvent * event)
```
**描述：**

获取事件类型。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 适配器事件对象。  |

**返回：**

事件类型。


### OH_ArkUI_NodeAdapterEvent_GetUserData()

```
void* OH_ArkUI_NodeAdapterEvent_GetUserData (ArkUI_NodeAdapterEvent * event)
```
**描述：**

获取注册事件时传入的自定义数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 适配器事件对象。  |

**返回：**

用户自定义数据的指针。


### OH_ArkUI_NodeAdapterEvent_SetItem()

```
int32_t OH_ArkUI_NodeAdapterEvent_SetItem (ArkUI_NodeAdapterEvent * event, ArkUI_NodeHandle node )
```
**描述：**

设置需要新增到Adapter中的组件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 适配器事件对象。  |
| node | 待添加的组件。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeAdapterEvent_SetNodeId()

```
int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId (ArkUI_NodeAdapterEvent * event, int32_t id )
```
**描述：**

设置生成的组件标识。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 适配器事件对象。  |
| id | 设置返回的组件标识。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeContent_AddNode()

```
int32_t OH_ArkUI_NodeContent_AddNode (ArkUI_NodeContentHandle content, ArkUI_NodeHandle node )
```
**描述：**

将一个ArkUI组件节点添加到对应的NodeContent对象下。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| content | 需要被添加节点的NodeContent对象。  |
| node | 需要被添加的节点。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeContent_GetUserData()

```
void* OH_ArkUI_NodeContent_GetUserData (ArkUI_NodeContentHandle content)
```
**描述：**

获取在NodeContent对象上保存的自定义数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| content | 需要保存自定义数据的NodeContent对象。  |

**返回：**

自定义数据。


### OH_ArkUI_NodeContent_InsertNode()

```
int32_t OH_ArkUI_NodeContent_InsertNode (ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position )
```
**描述：**

将一个ArkUI组件节点插入到对应的NodeContent对象的特定位置下。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| content | 需要被插入节点的NodeContent对象。  |
| node | 需要被插入的节点。  |
| position | 需要被插入的位置。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeContent_RegisterCallback()

```
int32_t OH_ArkUI_NodeContent_RegisterCallback (ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback )
```
**描述：**

注册NodeContent事件函数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| content | 需要注册事件的NodeContent对象。  |
| callback | 事件触发时需要执行的函数回调。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeContent_RemoveNode()

```
int32_t OH_ArkUI_NodeContent_RemoveNode (ArkUI_NodeContentHandle content, ArkUI_NodeHandle node )
```
**描述：**

删除NodeContent对象下的一个ArkUI组件节点

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| content | 需要被删除节点的NodeContent对象。  |
| node | 需要被删除的节点。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeContent_SetUserData()

```
int32_t OH_ArkUI_NodeContent_SetUserData (ArkUI_NodeContentHandle content, void * userData )
```
**描述：**

在NodeContent对象上保存自定义数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| content | 需要保存自定义数据的NodeContent对象。  |
| userData | 要保存的自定义数据。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeContentEvent_GetEventType()

```
ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType (ArkUI_NodeContentEvent * event)
```
**描述：**

获取触发NodeContent事件的事件类型。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | NodeContent事件指针。  |

**返回：**

NodeContent事件类型。


### OH_ArkUI_NodeContentEvent_GetNodeContentHandle()

```
ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle (ArkUI_NodeContentEvent * event)
```
**描述：**

获取触发事件的NodeContent对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | NodeContent事件指针。  |

**返回：**

Returns 触发事件的NodeContent对象。


### OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo()

```
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo (ArkUI_NodeCustomEvent * event, ArkUI_CustomSpanDrawInfo * info )
```
**描述：**

通过自定义组件事件获取自定义段落组件的绘制信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |
| info | 需要获取的绘制信息。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 异常原因：传入参数验证失败，参数不能为空。


### OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo()

```
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo (ArkUI_NodeCustomEvent * event, ArkUI_CustomSpanMeasureInfo * info )
```
**描述：**

通过自定义组件事件获取自定义段落组件的测量信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |
| info | 需要获取的测量信息。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 异常原因：传入参数验证失败，参数不能为空。


### OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw()

```
ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw (ArkUI_NodeCustomEvent * event)
```
**描述：**

通过自定义组件事件获取绘制上下文。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |

**返回：**

绘制上下文。


### OH_ArkUI_NodeCustomEvent_GetEventTargetId()

```
int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId (ArkUI_NodeCustomEvent * event)
```
**描述：**

通过自定义组件事件获取自定义事件ID。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |

**返回：**

自定义事件ID。


### OH_ArkUI_NodeCustomEvent_GetEventType()

```
ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType (ArkUI_NodeCustomEvent * event)
```
**描述：**

通过自定义组件事件获取事件类型。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |

**返回：**

组件自定义事件类型。


### OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure()

```
ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure (ArkUI_NodeCustomEvent * event)
```
**描述：**

通过自定义组件事件获取测算过程中的约束尺寸。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |

**返回：**

约束尺寸指针。


### OH_ArkUI_NodeCustomEvent_GetNodeHandle()

```
ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle (ArkUI_NodeCustomEvent * event)
```
**描述：**

通过自定义组件事件获取组件对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |

**返回：**

组件对象。


### OH_ArkUI_NodeCustomEvent_GetPositionInLayout()

```
ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout (ArkUI_NodeCustomEvent * event)
```
**描述：**

通过自定义组件事件获取在布局阶段期望自身相对父组件的位置。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |

**返回：**

期望自身相对父组件的位置。


### OH_ArkUI_NodeCustomEvent_GetUserData()

```
void* OH_ArkUI_NodeCustomEvent_GetUserData (ArkUI_NodeCustomEvent * event)
```
**描述：**

通过自定义组件事件获取自定义事件参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |

**返回：**

自定义事件参数。


### OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics()

```
int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics (ArkUI_NodeCustomEvent * event, ArkUI_CustomSpanMetrics * metrics )
```
**描述：**

通过自定义组件事件设置自定义段落的度量指标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 自定义组件事件。  |
| metrics | 需要获取的度量指标信息。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 异常原因：传入参数验证失败，参数不能为空。


### OH_ArkUI_NodeEvent_GetDragEvent()

```
ArkUI_DragEvent* OH_ArkUI_NodeEvent_GetDragEvent (ArkUI_NodeEvent * nodeEvent)
```
**描述：**

从 NodeEvent 中获取DragEvent。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeEvent事件指针。  |

**返回：**

ArkUI_DragEvent 事件指针，当传入的 NodeEvent 无效或不是拖拽相关的事件时，则返回空。


### OH_ArkUI_NodeEvent_GetEventType()

```
ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType (ArkUI_NodeEvent * event)
```
**描述：**

获取组件事件类型。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |

**返回：**

ArkUI_NodeEventType 组件事件类型。


### OH_ArkUI_NodeEvent_GetInputEvent()

```
ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent (ArkUI_NodeEvent * event)
```
**描述：**

获取组件事件中的输入事件（如触碰事件）数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |

**返回：**

ArkUI_UIInputEvent\* 输入事件数据指针。


### OH_ArkUI_NodeEvent_GetNodeComponentEvent()

```
ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent (ArkUI_NodeEvent * event)
```
**描述：**

获取组件事件中的数字类型数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |

**返回：**

ArkUI_NodeComponentEvent\* 数字类型数据指针。


### OH_ArkUI_NodeEvent_GetNodeHandle()

```
ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle (ArkUI_NodeEvent * event)
```
**描述：**

获取触发该事件的组件对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |

**返回：**

ArkUI_NodeHandle 触发该组件的组件对象。


### OH_ArkUI_NodeEvent_GetNumberValue()

```
int32_t OH_ArkUI_NodeEvent_GetNumberValue (ArkUI_NodeEvent * event, int32_t index, ArkUI_NumberValue * value )
```
**描述：**

获取组件回调事件的数字类型参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |
| index | 返回值索引。  |
| value | 具体返回值。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE 组件事件中参数长度超限。 ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID 组件事件中不存在该数据。


### OH_ArkUI_NodeEvent_GetPreDragStatus()

```
ArkUI_PreDragStatus OH_ArkUI_NodeEvent_GetPreDragStatus (ArkUI_NodeEvent * nodeEvent)
```
**描述：**

获取预览拖拽事件状态。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| nodeEvent | ArkUI_NodeEvent节点对象。  |

**返回：**

ArkUI_PreDragStatus 拖拽发起前交互状态。


### OH_ArkUI_NodeEvent_GetStringAsyncEvent()

```
ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent (ArkUI_NodeEvent * event)
```
**描述：**

获取组件事件中的字符串数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |

**返回：**

ArkUI_StringAsyncEvent\* 字符串数据指针。


### OH_ArkUI_NodeEvent_GetStringValue()

```
int32_t OH_ArkUI_NodeEvent_GetStringValue (ArkUI_NodeEvent * event, int32_t index, char ** string, int32_t * stringSize )
```
**描述：**

获取组件回调事件的字符串类型参数，字符串数据仅在事件回调过程中有效，需要在事件回调外使用建议进行额外拷贝处理。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |
| index | 返回值索引。  |
| string | 字符串数组的指针。  |
| stringSize | 字符串数组的长度。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE 组件事件中参数长度超限。 ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID 组件事件中不存在该数据。


### OH_ArkUI_NodeEvent_GetTargetId()

```
int32_t OH_ArkUI_NodeEvent_GetTargetId (ArkUI_NodeEvent * event)
```
**描述：**

获取事件自定义标识ID。

该事件id在调用**registerNodeEvent**函数时作为参数传递进来，可应用于同一事件入口函数**registerNodeEventReceiver**分发逻辑。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |

**返回：**

int32_t 事件自定义标识ID。


### OH_ArkUI_NodeEvent_GetUserData()

```
void* OH_ArkUI_NodeEvent_GetUserData (ArkUI_NodeEvent * event)
```
**描述：**

获取组件事件中的用户自定义数据。

该自定义参数在调用**registerNodeEvent**函数时作为参数传递进来，可应用于事件触发时的业务逻辑处理。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |

**返回：**

void\* 用户自定义数据指针。


### OH_ArkUI_NodeEvent_SetReturnNumberValue()

```
int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue (ArkUI_NodeEvent * event, ArkUI_NumberValue * value, int32_t size )
```
**描述：**

设置组件回调事件的返回值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针。  |
| value | 事件数字类型数组。  |
| size | 数组长度。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN 组件事件不支持返回值。 ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID 组件事件中不存在该数据。


### OH_ArkUI_NodeUtils_AddCustomProperty()

```
void OH_ArkUI_NodeUtils_AddCustomProperty (ArkUI_NodeHandle node, const char * name, const char * value )
```
**描述：**

设置组件的自定义属性。该接口仅在主线程生效。

**起始版本：** 13

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| name | 自定义属性的名称。不允许传入空指针。  |
| value | 对应key参数名称的自定义属性的值。不允许传入空指针。  |


### OH_ArkUI_NodeUtils_GetActiveChildrenInfo()

```
int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo (ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo ** handle )
```
**描述：**

获取某个节点所有活跃的子节点。Span将不会被计入子结点的统计中。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| head | 传入需要获取的节点。  |
| handle | 对应head节点子节点信息的结构体。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeUtils_GetCurrentPageRootNode()

```
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode (ArkUI_NodeHandle node)
```
**描述：**

获取当前页面的根节点。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点对象。  |

**返回：**

根节点的指针，如果没有返回NULL。


### OH_ArkUI_NodeUtils_GetCustomProperty()

```
int32_t OH_ArkUI_NodeUtils_GetCustomProperty (ArkUI_NodeHandle node, const char * name, ArkUI_CustomProperty ** handle )
```
**描述：**

获取组件的自定义属性的值。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| name | 自定义属性的名称。  |
| handle | 获取的对应key参数名称的自定义属性的结构体。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeUtils_GetLayoutPosition()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutPosition (ArkUI_NodeHandle node, ArkUI_IntOffset * localOffset )
```
**描述：**

获取组件布局区域相对父组件的位置。 布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| localOffset | 组件handle相对父组件的偏移值，单位：px。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeUtils_GetLayoutPositionInScreen()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen (ArkUI_NodeHandle node, ArkUI_IntOffset * screenOffset )
```
**描述：**

获取组件布局区域相对屏幕的位置。 布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| screenOffset | 组件handle相对屏幕的偏移值，单位：px。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay (ArkUI_NodeHandle node, ArkUI_IntOffset * offset )
```
**描述：**

获取组件布局区域相对全局屏幕的位置。 布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 20

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| offset | 组件handle相对全局屏幕的偏移值，单位：px。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeUtils_GetLayoutPositionInWindow()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow (ArkUI_NodeHandle node, ArkUI_IntOffset * globalOffset )
```
**描述：**

获取组件布局区域相对窗口的位置。 布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| globalOffset | 组件handle相对窗口的偏移值，单位：px。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeUtils_GetLayoutSize()

```
int32_t OH_ArkUI_NodeUtils_GetLayoutSize (ArkUI_NodeHandle node, ArkUI_IntSize * size )
```
**描述：**

获取组件布局区域的大小。 布局区域大小不包含图形变化属性，如缩放。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| size | 组件handle的绘制区域尺寸，单位：px。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeUtils_GetNodeType()

```
int32_t OH_ArkUI_NodeUtils_GetNodeType (ArkUI_NodeHandle node)
```
**描述：**

获取节点的类型。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点对象。  |

**返回：**

节点的类型，具体已开放类型参考[ArkUI_NodeType](#arkui_nodetype)，未开放结点返回-1。


### OH_ArkUI_NodeUtils_GetParentInPageTree()

```
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree (ArkUI_NodeHandle node)
```
**描述：**

获取父节点，可获取由ArkTs创建的组件节点。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点对象。  |

**返回：**

组件的指针，如果没有返回NULL


### OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen()

```
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen (ArkUI_NodeHandle node, ArkUI_IntOffset * translateOffset )
```
**描述：**

获取组件在屏幕中的位置，包含了图形平移变化属性。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| translateOffset | 组件handle自身，父组件及祖先节点的偏移累计值，单位：px。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow()

```
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow (ArkUI_NodeHandle node, ArkUI_IntOffset * translateOffset )
```
**描述：**

获取组件在窗口中的位置，包含了图形平移变化属性。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| translateOffset | 组件handle自身，父组件及祖先节点的偏移累计值，单位：px。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_NodeUtils_IsCreatedByNDK()

```
bool OH_ArkUI_NodeUtils_IsCreatedByNDK (ArkUI_NodeHandle node)
```
**描述：**

获取组件是否由C-API创建的标签。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点对象。  |

**返回：**

节点是否由C-API创建的Tag，true代表由C-API创建，false代表非C-API创建。


### OH_ArkUI_NodeUtils_RemoveCustomProperty()

```
void OH_ArkUI_NodeUtils_RemoveCustomProperty (ArkUI_NodeHandle node, const char * name )
```
**描述：**

移除组件已设置的自定义属性。

**起始版本：** 13

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| name | 自定义属性的名称。  |


### OH_ArkUI_PanGesture_GetOffsetX()

```
float OH_ArkUI_PanGesture_GetOffsetX (const ArkUI_GestureEvent * event)
```
**描述：**

滑动手势返回当前手势事件x轴相对偏移量。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

当前手势事件x轴相对偏移量，单位为px。


### OH_ArkUI_PanGesture_GetOffsetY()

```
float OH_ArkUI_PanGesture_GetOffsetY (const ArkUI_GestureEvent * event)
```
**描述：**

滑动手势返回当前手势事件y轴相对偏移量。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

当前手势事件y轴相对偏移量，单位为px。


### OH_ArkUI_PanGesture_GetVelocity()

```
float OH_ArkUI_PanGesture_GetVelocity (const ArkUI_GestureEvent * event)
```
**描述：**

滑动手势返回手势主方向速度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

当前手势主方向速度，为xy轴方向速度的平方和的算数平方根，单位px/秒。


### OH_ArkUI_PanGesture_GetVelocityX()

```
float OH_ArkUI_PanGesture_GetVelocityX (const ArkUI_GestureEvent * event)
```
**描述：**

滑动手势返回当前手势的x轴方向速度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

当前手势的x轴方向速度，单位px/秒。


### OH_ArkUI_PanGesture_GetVelocityY()

```
float OH_ArkUI_PanGesture_GetVelocityY (const ArkUI_GestureEvent * event)
```
**描述：**

滑动手势返回当前手势的y轴方向速度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

当前手势的y轴方向速度，单位px/秒。


### OH_ArkUI_ParallelInnerGestureEvent_GetConflictRecognizers()

```
int32_t OH_ArkUI_ParallelInnerGestureEvent_GetConflictRecognizers (ArkUI_ParallelInnerGestureEvent * event, ArkUI_GestureRecognizerHandleArray * array, int32_t * size )
```
**描述：**

获取并行内部手势事件中的冲突的手势识别器。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 并行内部手势事件。  |
| array | 冲突的手势识别器数组。  |
| size | 冲突的手势识别器数组的大小。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。


### OH_ArkUI_ParallelInnerGestureEvent_GetCurrentRecognizer()

```
ArkUI_GestureRecognizer* OH_ArkUI_ParallelInnerGestureEvent_GetCurrentRecognizer (ArkUI_ParallelInnerGestureEvent * event)
```
**描述：**

获取并行内部手势事件中的当前手势识别器。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 并行内部手势事件。  |

**返回：**

当前手势识别器的指针。

### OH_ArkUI_ParallelInnerGestureEvent_GetUserData()

```
void* OH_ArkUI_ParallelInnerGestureEvent_GetUserData(ArkUI_ParallelInnerGestureEvent * event)
```
**描述：**

获取并行内部手势事件中的用户自定义数据。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 并行内部手势事件。  |

**返回：**

用户自定义数据的指针。

### OH_ArkUI_GestureInterrupter_GetUserData

```
void* OH_ArkUI_GestureInterrupter_GetUserData(ArkUI_GestureInterruptInfo* event)
```

**描述：**

获取手势中断事件中的用户自定义数据。

**起始版本：** 18

**参数:**

| 名称  | 描述                       |
| ----- | -------------------------- |
| event | 是指向手势中断信息的指针。 |

**返回：**

指向用户自定义数据的指针。

### OH_ArkUI_PreventGestureRecognizerBegin

```
ArkUI_ErrorCode OH_ArkUI_PreventGestureRecognizerBegin(ArkUI_GestureRecognizer* recognizer)
```

**描述：**

在手指全部抬起前阻止手势识别器参与当前手势识别。如果系统已确定该手势识别器的结果（无论成功与否），调用此接口将无效。

**起始版本：** 20

**参数:**

| 名称  | 描述                       |
| ----- | -------------------------- |
| recognizer | 手势识别器指针。       |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 参数错误。

### OH_ArkUI_PinchGesture_GetCenterX()

```
float OH_ArkUI_PinchGesture_GetCenterX (const ArkUI_GestureEvent * event)
```
**描述：**

捏合手势中心点相对于当前组件元素左上角x轴坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

捏合手势中心点相对于当前组件元素左上角x轴坐标，单位为px。


### OH_ArkUI_PinchGesture_GetCenterY()

```
float OH_ArkUI_PinchGesture_GetCenterY (const ArkUI_GestureEvent * event)
```
**描述：**

捏合手势中心点相对于当前组件元素左上角y轴坐标。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

捏合手势中心点相对于当前组件元素左上角y轴坐标，单位为px。


### OH_ArkUI_PinchGesture_GetScale()

```
float OH_ArkUI_PinchGesture_GetScale (const ArkUI_GestureEvent * event)
```
**描述：**

捏合手势返回当前手势事件缩放信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

缩放比例。


### OH_ArkUI_QueryModuleInterfaceByName()

```
void* OH_ArkUI_QueryModuleInterfaceByName (ArkUI_NativeAPIVariantKind type, const char * structName )
```
**描述：**

需调用该函数[初始化](../../ui/ndk-access-the-arkts-page.md#ndk组件模块)C-API环境，并获取指定类型的Native模块接口集合。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| type | ArkUI提供的Native接口集合大类，例如UI组件接口类：ARKUI_NATIVE_NODE, 手势类：ARKUI_NATIVE_GESTURE。  |
| sturctName | native接口结构体的名称，通过查询对应头文件内结构体定义，例如位于&lt;arkui/native_node.h&gt;中的"ArkUI_NativeNodeAPI_1"。  |

**返回：**

void\* 返回Native接口抽象指针，在转化为具体类型后进行使用。 \#include&lt;arkui/native_interface.h&gt; \#include&lt;arkui/native_node.h&gt; \#include&lt;arkui/native_gesture.h&gt; auto\* anyNativeAPI = [OH_ArkUI_QueryModuleInterfaceByName](#oh_arkui_querymoduleinterfacebyname)(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"); if (anyNativeAPI) { auto nativeNodeApi = reinterpret_cast&lt;[ArkUI_NativeNodeAPI_1](_ark_u_i___native_node_a_p_i__1.md)\*&gt;(anyNativeAPI); } auto anyGestureAPI = OH_ArkUI_QueryModuleInterface(ARKUI_NATIVE_GESTURE, "ArkUI_NativeGestureAPI_1"); if (anyNativeAPI) { auto basicGestureApi = reinterpret_cast&lt;[ArkUI_NativeGestureAPI_1](_ark_u_i___native_gesture_a_p_i__1.md)\*&gt;(anyGestureAPI); }


### OH_ArkUI_RegisterSystemColorModeChangeEvent()

```
int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent (ArkUI_NodeHandle node, void * userData, void(*)(ArkUI_SystemColorMode colorMode, void *userData) onColorModeChange )
```
**描述：**

注册系统深浅色变更事件。同一组件仅能注册一个系统深浅变更回调。示例请参考：[监听组件事件](../../ui/ndk-listen-to-component-events.md)。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| userData | 自定义事件参数，当事件触发时在回调参数中携带回来。  |
| onColorModeChange | 事件触发后的回调。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED 组件不支持该事件。


### OH_ArkUI_RegisterSystemFontStyleChangeEvent()

```
int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent (ArkUI_NodeHandle node, void * userData, void(*)(ArkUI_SystemFontStyleEvent *event, void *userData) onFontStyleChange )
```
**描述：**

注册系统字体变更事件。同一组件仅能注册一个系统字体变更回调。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| userData | 自定义事件参数，当事件触发时在回调参数中携带回来。  |
| onFontStyleChange | 事件触发后的回调。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED 组件不支持该事件。


### OH_ArkUI_RotationGesture_GetAngle()

```
float OH_ArkUI_RotationGesture_GetAngle (const ArkUI_GestureEvent * event)
```
**描述：**

旋转手势返回当前手势事件角度信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

旋转角度。


### OH_ArkUI_SetArkUIGestureRecognizerDisposeNotify()

```
int32_t OH_ArkUI_SetArkUIGestureRecognizerDisposeNotify (ArkUI_GestureRecognizer * recognizer, ArkUI_GestureRecognizerDisposeNotifyCallback callback, void * userData )
```
**描述：**

设置手势识别器对象析构通知回调函数。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| callback | 手势识别器对象析构通知回调函数。  |
| userData | 用户自定义数据。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。


### OH_ArkUI_SetDragEventStrictReportWithContext()

```
int32_t OH_ArkUI_SetDragEventStrictReportWithContext (ArkUI_ContextHandle uiContext, bool enabled )
```
**描述：**

控制是否使能严格dragEvent上报，建议开启；默认是不开启的; 当不开启时，从父组件拖移进子组件时，父组件并不会收到leave的通知；而开启之后，只要前后两个组件发生变化，上一个组件就会收到 leave，新的组件收到enter通知；该配置与具体的UI实例相关，可通过传入一个UI实例进行关联。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| uiContext | UI实例指针。  |
| enabled | 是否开启严格上报。true表示开启严格上报，false表示关闭严格上报。|

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_SetDragEventStrictReportWithNode()

```
int32_t OH_ArkUI_SetDragEventStrictReportWithNode (ArkUI_NodeHandle node, bool enabled )
```
**描述：**

控制是否使能严格dragEvent上报，建议开启；默认是不开启的； 当不开启时，从父组件拖移进子组件时，父组件并不会收到leave的通知；而开启之后，只要前后两个组件发生变化，上一个组件就会收到 leave，新的组件收到enter通知；该配置与具体的UI实例相关，需要通过传入一个当前UI实例上的一个具体的组件节点来关联。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 组件节点指针。  |
| enabled | 是否开启严格上报。true表示开启严格上报，false表示关闭严格上报。|

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_SetGestureRecognizerEnabled()

```
int32_t OH_ArkUI_SetGestureRecognizerEnabled (ArkUI_GestureRecognizer * recognizer, bool enabled )
```
**描述：**

设置手势识别器的使能状态。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| enabled | 使能状态。true表示使能，false表示无法使能。|

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。

### OH_ArkUI_SetGestureRecognizerLimitFingerCount

```
int32_t OH_ArkUI_SetGestureRecognizerLimitFingerCount (ArkUI_GestureRecognizer * recognizer, bool limitFingerCount )
```
**描述：**

设置是否严格检查触摸手指数量的标志。实际触摸手指数量不等于设置的手指数量的时候，该手势识别不成功。

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| limitFingerCount | 是否检查触摸屏幕的手指数量。true表示检查手指数量，false表示不检查手指数量。|

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) - 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) - 参数错误。




### OH_ArkUI_SetNodeAllowedDropDataTypes()

```
int32_t OH_ArkUI_SetNodeAllowedDropDataTypes (ArkUI_NodeHandle node, const char * typesArray[], int32_t count )
```
**描述：**

配置组件允许接受落入的数据类型，该接口会重置通过 [OH_ArkUI_DisallowNodeAnyDropDataTypes](#oh_arkui_disallownodeanydropdatatypes) 或 [OH_ArkUI_AllowNodeAllDropDataTypes](#oh_arkui_allownodealldropdatatypes)进行的配置。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 组件节点指针。  |
| typesArray | 允许落入的数据类型数组。  |
| count | 数组的长度。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_SetNodeDraggable()

```
int32_t OH_ArkUI_SetNodeDraggable (ArkUI_NodeHandle node, bool enabled )
```
**描述：**

设置该组件是否允许进行拖拽。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 组件节点指针。  |
| enabled | 是否支持拖出。true表示支持拖出，false表示不支持拖出。|

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_SetNodeDragPreview()

```
int32_t OH_ArkUI_SetNodeDragPreview (ArkUI_NodeHandle node, OH_PixelmapNative * preview )
```
**描述：**

设置组件在被拖拽时的自定义跟手图。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标组件节点指针。  |
| preview | 自定义跟手图，使用 pixelmap 格式。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_SetNodeDragPreviewOption()

```
int32_t OH_ArkUI_SetNodeDragPreviewOption (ArkUI_NodeHandle node, ArkUI_DragPreviewOption * option )
```
**描述：**

将构造的ArkUI_DragPreviewOption设置给组件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 组件节点指针。  |
| option | 自定义参数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_StartDrag()

```
int32_t OH_ArkUI_StartDrag (ArkUI_DragAction * dragAction)
```
**描述：**

通过构造的DragAction对象发起拖拽。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| dragAction | 拖拽action对象。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_StyledString_AddPlaceholder()

```
void OH_ArkUI_StyledString_AddPlaceholder (ArkUI_StyledString * handle, OH_Drawing_PlaceholderSpan * placeholder )
```
**描述：**

设置占位符。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向ArkUI_StyledString对象的指针。  |
| placeholder | 指向OH_Drawing_PlaceholderSpan对象的指针。  |


### OH_ArkUI_StyledString_AddText()

```
void OH_ArkUI_StyledString_AddText (ArkUI_StyledString * handle, const char * content )
```
**描述：**

基于当前格式化字符串样式设置对应的文本内容。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向ArkUI_StyledString对象的指针。  |
| content | 指向文本内容的指针。  |


### OH_ArkUI_StyledString_Create()

```
ArkUI_StyledString* OH_ArkUI_StyledString_Create (OH_Drawing_TypographyStyle * style, OH_Drawing_FontCollection * collection )
```
**描述：**

创建指向ArkUI_StyledString对象的指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| style | 指向OH_Drawing_TypographyStyle的指针，由[**OH_Drawing_CreateTypographyStyle**](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_createtypographystyle)获取。  |
| collection | 指向OH_Drawing_FontCollection的指针，由[**OH_Drawing_CreateFontCollection**](../apis-arkgraphics2d/capi-drawing-font-collection-h.md#oh_drawing_createfontcollection)获取。  |

**返回：**

创建指向ArkUI_StyledString对象的指针。如果对象返回空指针，表示创建失败，失败的原因可能是英语地址空间满，或者是style，collection参数异常如空指针。


### OH_ArkUI_StyledString_CreateTypography()

```
OH_Drawing_Typography* OH_ArkUI_StyledString_CreateTypography (ArkUI_StyledString * handle)
```
**描述：**

基于格式字符串对象创建指向OH_Drawing_Typography对象的指针，用于提前进行文本测算排版。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向ArkUI_StyledString对象的指针。  |

**返回：**

指向OH_Drawing_Typography对象的指针。如果对象返回空指针，表示创建失败，失败的原因可能是handle参数异常如空指针。


### OH_ArkUI_StyledString_Descriptor_Create()

```
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_Create (void )
```
**描述：**

创建属性字符串数据对象。

**起始版本：** 14

**返回：**

指向ArkUI_StyledString_Descriptor对象的指针。


### OH_ArkUI_StyledString_Descriptor_Destroy()

```
void OH_ArkUI_StyledString_Descriptor_Destroy (ArkUI_StyledString_Descriptor * descriptor)
```
**描述：**

释放被ArkUI_StyledString_Descriptor对象占据的内存。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| descriptor | 指向ArkUI_StyledString_Descriptor对象的指针。  |


### OH_ArkUI_StyledString_Destroy()

```
void OH_ArkUI_StyledString_Destroy (ArkUI_StyledString * handle)
```
**描述：**

释放被ArkUI_StyledString对象占据的内存。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向ArkUI_StyledString对象的指针。  |


### OH_ArkUI_StyledString_PopTextStyle()

```
void OH_ArkUI_StyledString_PopTextStyle (ArkUI_StyledString * handle)
```
**描述：**

将当前格式化字符串对象中栈顶样式出栈。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向ArkUI_StyledString对象的指针。  |


### OH_ArkUI_StyledString_PushTextStyle()

```
void OH_ArkUI_StyledString_PushTextStyle (ArkUI_StyledString * handle, OH_Drawing_TextStyle * style )
```
**描述：**

将新的排版风格设置到当前格式化字符串样式栈顶。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向ArkUI_StyledString对象的指针。  |
| style | 指向OH_Drawing_TextStyle对象的指针。  |


### OH_ArkUI_SwipeGesture_GetAngle()

```
float OH_ArkUI_SwipeGesture_GetAngle (const ArkUI_GestureEvent * event)
```
**描述：**

滑动手势返回当前手势事件角度信息。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

滑动手势的角度，即两根手指间的线段与水平方向的夹角变化的度数。


### OH_ArkUI_SwipeGesture_GetVelocity()

```
float OH_ArkUI_SwipeGesture_GetVelocity (const ArkUI_GestureEvent * event)
```
**描述：**

滑动手势场景中所有手指滑动平均速度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 手势事件。  |

**返回：**

滑动手势速度，即所有手指滑动的平均速度，单位为px/秒。


### OH_ArkUI_SwiperIndicator_Create()

```
ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create (ArkUI_SwiperIndicatorType type)
```
**描述：**

创建 Swiper 组件的导航指示器。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| type | 导航指示器的类型。  |

**返回：**

导航指示器对象指针。


### OH_ArkUI_SwiperIndicator_Dispose()

```
void OH_ArkUI_SwiperIndicator_Dispose (ArkUI_SwiperIndicator * indicator)
```
**描述：**

销毁Swiper组件的导航指示器指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |


### OH_ArkUI_SwiperIndicator_GetBottomPosition()

```
float OH_ArkUI_SwiperIndicator_GetBottomPosition (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取导航点距离 Swiper 组件底部的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

导航点距离Swiper组件底部的距离。单位：vp。


### OH_ArkUI_SwiperIndicator_GetColor()

```
uint32_t OH_ArkUI_SwiperIndicator_GetColor (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取 Swiper 组件圆点导航指示器的颜色。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

颜色类型，0xargb格式，形如 0xFFFF0000 表示红色。


### OH_ArkUI_SwiperIndicator_GetEndPosition()

```
float OH_ArkUI_SwiperIndicator_GetEndPosition (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取导航点距离 Swiper 组件右边的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

导航点距离Swiper组件右边的距离。单位：vp。


### OH_ArkUI_SwiperIndicator_GetItemHeight()

```
float OH_ArkUI_SwiperIndicator_GetItemHeight (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取 Swiper 组件圆点导航指示器的高。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

圆点导航指示器的高。单位：vp。


### OH_ArkUI_SwiperIndicator_GetItemWidth()

```
float OH_ArkUI_SwiperIndicator_GetItemWidth (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取 Swiper 组件圆点导航指示器的宽。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

圆点导航指示器的宽。单位：vp。


### OH_ArkUI_SwiperIndicator_GetMask()

```
int32_t OH_ArkUI_SwiperIndicator_GetMask (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取是否显示 Swiper 组件圆点导航指示器的蒙版样式。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

mask 1 表示显示圆点导航指示器的蒙版样式，0 表示不显示。


### OH_ArkUI_SwiperIndicator_GetMaxDisplayCount()

```
int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取圆点导航点指示器样式下，导航点显示个数的最大值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

导航点显示个数最大值，有效取值范围6-9。

### OH_ArkUI_SwiperIndicator_SetSpace()

```
void OH_ArkUI_SwiperIndicator_SetSpace (ArkUI_SwiperIndicator * indicator， float space)
```
**描述：**

设置导航点间距。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| space | 导航点间距。默认值：8，单位：vp。  |

### OH_ArkUI_SwiperIndicator_GetSpace()

```
float OH_ArkUI_SwiperIndicator_GetSpace (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取导航点间距。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

导航点间距。单位：vp。

### OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom()

```
void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom (ArkUI_SwiperIndicator * indicator，int32_t ignoreSize)
```
**描述：**

设置OH_ArkUI_SwiperIndicator_SetBottomPosition是否忽略导航点大小。 

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| ignoreSize | 是否忽略导航点大小。1表示忽略导航点大小，0表示不忽略，默认值0。 |

### OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom()

```
int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取OH_ArkUI_SwiperIndicator_SetBottomPosition是否忽略导航点大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

是否忽略导航点大小。

### OH_ArkUI_SwiperDigitIndicator_Create()

```
ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()
```
**描述：**

创建 Swiper 组件的数字导航指示器。

**起始版本：** 19

**返回：**

数字导航指示器对象指针。

### OH_ArkUI_SwiperDigitIndicator_SetStartPosition()

```
void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```
**描述：**

设置数字导航指示器距离 Swiper 组件左边的距离，从右至左显示的语言模式下，设置其距离 Swiper 组件右边的距离。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| value | 数字导航指示器距离Swiper组件左边的距离，从右至左显示的语言模式下，为其距离 Swiper 组件右边的距离。默认值：0，单位：vp。  |

### OH_ArkUI_SwiperDigitIndicator_GetStartPosition()

```
float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

获取数字导航指示器距离 Swiper 组件左边的距离，从右至左显示的语言模式下，获取其距离 Swiper 组件右边的距离。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

数字导航指示器距离 Swiper 组件左边的距离，从右至左显示的语言模式下，为其距离 Swiper 组件右边的距离。单位：vp。

### OH_ArkUI_SwiperDigitIndicator_SetTopPosition()

```
void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```
**描述：**

设置数字导航指示器距离 Swiper 组件顶部的距离。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| value | 数字导航指示器距离Swiper组件顶部的距离。默认值：0，单位：vp。  |

### OH_ArkUI_SwiperDigitIndicator_GetTopPosition()

```
float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

获取数字导航指示器距离 Swiper 组件顶部的距离。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

数字导航指示器距离Swiper组件顶部的距离。单位：vp。

### OH_ArkUI_SwiperDigitIndicator_SetEndPosition()

```
void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```
**描述：**

设置数字导航指示器距离 Swiper 组件右边的距离，从右至左显示的语言模式下，设置其距离 Swiper 组件左边的距离。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| value | 数字导航指示器距离Swiper组件右边的距离，从右至左显示的语言模式下，其距离 Swiper 组件左边的距离。默认值：0，单位：vp。  |

### OH_ArkUI_SwiperDigitIndicator_GetEndPosition()

```
float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

获取数字导航指示器距离 Swiper 组件右边的距离，从右至左显示的语言模式下，获取其距离 Swiper 组件左边的距离。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

数字导航指示器距离Swiper组件右边的距离，从右至左显示的语言模式下，其距离 Swiper 组件左边的距离。单位：vp。

### OH_ArkUI_SwiperDigitIndicator_SetBottomPosition()

```
void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```
**描述：**

设置数字导航指示器距离 Swiper 组件底部的距离。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| value | 数字导航指示器距离Swiper组件底部的距离。默认值：0，单位：vp。  |

### OH_ArkUI_SwiperDigitIndicator_GetBottomPosition()

```
float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

获取数字导航指示器距离 Swiper 组件底部的距离。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

数字导航指示器距离Swiper组件底部的距离。单位：vp。

### OH_ArkUI_SwiperDigitIndicator_SetFontColor()

```
void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)
```
**描述：**

设置 Swiper 组件数字导航指示器字体颜色。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| color | 颜色类型，0xargb格式，形如 0xFFFF0000 表示红色。默认值：0xFF182431。  |

### OH_ArkUI_SwiperDigitIndicator_GetFontColor()

```
uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

获取 Swiper 组件数字导航指示器字体颜色。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

颜色类型，0xargb格式，形如 0xFFFF0000 表示红色。

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor()

```
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)
```
**描述：**

设置被选中 Swiper 组件数字导航指示器字体颜色。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| selectedColor | 颜色类型，0xargb格式，形如 0xFFFF0000 表示红色。默认值：0xFF182431。  |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor()

```
uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

获取被选中 Swiper 组件数字导航指示器字体颜色。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

颜色类型，0xargb格式，形如 0xFFFF0000 表示红色。

### OH_ArkUI_SwiperDigitIndicator_SetFontSize()

```
void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```
**描述：**

设置 Swiper 组件数字导航指示器字体大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| size | 字体大小数值，单位为fp。  |

### OH_ArkUI_SwiperDigitIndicator_GetFontSize()

```
float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

获取 Swiper 组件数字导航指示器字体大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

字体大小数值，单位为fp。

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize()

```
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```
**描述：**

设置被选中 Swiper 组件数字导航指示器字体大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| size | 字体大小数值，单位为fp。  |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize()

```
float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

获取被选中 Swiper 组件数字导航指示器字体大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

字体大小数值，单位为fp。

### OH_ArkUI_SwiperDigitIndicator_SetFontWeight()

```
void OH_ArkUI_SwiperDigitIndicator_SetFontWeight(ArkUI_SwiperDigitIndicator* indicator, ArkUI_FontWeight fontWeight)
```
**描述：**

设置 Swiper 组件数字导航指示器字体粗细属性。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| fontWeight | 字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)。  |

### OH_ArkUI_SwiperDigitIndicator_GetFontWeight()

```
ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetFontWeight(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

 获取 Swiper 组件数字导航指示器字体粗细属性。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight()

```
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight(ArkUI_SwiperDigitIndicator* indicator, ArkUI_FontWeight selectedFontWeight)
```
**描述：**

设置被选中 Swiper 组件数字导航指示器字体粗细属性。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| selectedFontWeight | 字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)。  |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight()

```
ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

 获取被选中 Swiper 组件数字导航指示器字体粗细属性。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

字体粗细样式[ArkUI_FontWeight](#arkui_fontweight)

### OH_ArkUI_SwiperDigitIndicator_Destroy

```
void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

销毁 Swiper 组件的数字导航指示器指针。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |

### OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom

```
void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)
```
**描述：**

设置OH_ArkUI_SwiperDigitIndicator_SetBottomPosition是否忽略导航点大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。  |
| ignoreSize | 是否忽略导航点大小。1表示忽略导航点大小，0表示不忽略，默认值0。|

### OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom()

```
int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)
```
**描述：**

获取OH_ArkUI_SwiperDigitIndicator_SetBottomPosition是否忽略导航点大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 数字导航指示器对象指针。 |

**返回：**

是否忽略导航点大小。

### OH_ArkUI_SwiperArrowStyle_Create()

```
ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()
```
**描述：**

创建 Swiper 组件的导航箭头。

**起始版本：** 19

**返回：**

导航箭头对象指针。

### OH_ArkUI_SwiperArrowStyle_SetShowBackground()

```
void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle *arrowStyle, int32_t showBackground)
```
**描述：**

设置 Swiper 组件导航箭头底板是否显示。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。  |
| showBackground | 导航箭头底板是否显示，0：不显示，1：显示，默认值：0。  |

### OH_ArkUI_SwiperArrowStyle_GetShowBackground()

```
int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)
```
**描述：**

 获取 Swiper 组件导航箭头底板是否显示。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。 |

**返回：**

导航箭头底板是否显示，0：不显示，1：显示。

### OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle()

```
void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle *arrowStyle, int32_t showSidebarMiddle)
```
**描述：**

设置 Swiper 组件导航箭头显示位置。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。  |
| showSidebarMiddle | 导航箭头显示位置，0：显示在导航指示器两侧，1：显示在Swiper组件两侧，默认值：0。  |

### OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle()

```
int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)
```
**描述：**

获取 Swiper 组件导航箭头显示位置。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。 |

**返回：**

导航箭头显示位置，0：显示在导航指示器两侧，1：显示在Swiper组件两侧。

### OH_ArkUI_SwiperArrowStyle_SetBackgroundSize()

```
void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)
```
**描述：**

设置 Swiper 组件导航箭头底板大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。  |
| backgroundSize | 导航箭头底板大小，单位：vp。默认值：显示在导航指示器两侧24vp，显示在Swiper两侧32vp。  |

### OH_ArkUI_SwiperArrowStyle_GetBackgroundSize()

```
float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle)
```
**描述：**

获取 Swiper 组件导航箭头底板大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。 |

**返回：**

导航箭头底板大小，单位：vp。

### OH_ArkUI_SwiperArrowStyle_SetBackgroundColor()

```
void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t backgroundColor)
```
**描述：**

设置 Swiper 组件导航箭头底板颜色。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。  |
| backgroundColor | 导航箭头底板颜色，0xargb格式，形如 0xFFFF0000 表示红色。默认值：显示在导航指示器两侧为0x00000000，显示在Swiper两侧为0x19182431。  |

### OH_ArkUI_SwiperArrowStyle_GetBackgroundColor()

```
uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)
```
**描述：**

获取 Swiper 组件导航箭头底板颜色。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。 |

**返回：**

导航箭头底板颜色，0xargb格式，形如 0xFFFF0000 表示红色。

### OH_ArkUI_SwiperArrowStyle_SetArrowSize()

```
void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)
```
**描述：**

设置 Swiper 组件导航箭头大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。  |
| arrowSize |  导航箭头大小，单位：vp。默认值：显示在导航指示器两侧18vp，显示在Swiper两侧24vp。 显示导航箭头底板时，arrowSize固定为backgroundSize的3/4。 |

### OH_ArkUI_SwiperArrowStyle_GetArrowSize()

```
float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)
```
**描述：**

获取 Swiper 组件导航箭头大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。 |

**返回：**

导航箭头大小，单位：vp。

### OH_ArkUI_SwiperArrowStyle_SetArrowColor()

```
void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)
```
**描述：**

设置 Swiper 组件导航箭头大小。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。  |
| arrowColor |  导航箭头颜色，0xargb格式，形如 0xFFFF0000 表示红色。 |

### OH_ArkUI_SwiperArrowStyle_GetArrowColor()

```
uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)
```
**描述：**

获取 Swiper 组件导航箭头颜色。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。 |

**返回：**

导航箭头颜色，0xargb格式，形如 0xFFFF0000 表示红色。

### OH_ArkUI_SwiperArrowStyle_Destroy

```
void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle* arrowStyle)
```
**描述：**

销毁 Swiper 组件的导航箭头指针。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| arrowStyle | 导航箭头对象指针。  |

### OH_ArkUI_SwiperIndicator_GetSelectedColor()

```
uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取被选中 Swiper 组件圆点导航指示器的颜色。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

颜色类型，0xargb格式，形如 0xFFFF0000 表示红色。


### OH_ArkUI_SwiperIndicator_GetSelectedItemHeight()

```
float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取被选中 Swiper 组件圆点导航指示器的高。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

圆点导航指示器的高。单位：vp。


### OH_ArkUI_SwiperIndicator_GetSelectedItemWidth()

```
float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取被选中 Swiper 组件圆点导航指示器的宽。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

圆点导航指示器的宽。单位：vp。


### OH_ArkUI_SwiperIndicator_GetStartPosition()

```
float OH_ArkUI_SwiperIndicator_GetStartPosition (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取导航点距离 Swiper 组件左边的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

导航点距离Swiper组件左边的距离。单位：vp。


### OH_ArkUI_SwiperIndicator_GetTopPosition()

```
float OH_ArkUI_SwiperIndicator_GetTopPosition (ArkUI_SwiperIndicator * indicator)
```
**描述：**

获取导航点距离 Swiper 组件顶部的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |

**返回：**

导航点距离Swiper组件顶部的距离。单位：vp。


### OH_ArkUI_SwiperIndicator_SetBottomPosition()

```
void OH_ArkUI_SwiperIndicator_SetBottomPosition (ArkUI_SwiperIndicator * indicator, float value )
```
**描述：**

设置导航点距离 Swiper 组件底部的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| value | 导航点距离Swiper组件底部的距离。默认值：0，单位：vp。  |


### OH_ArkUI_SwiperIndicator_SetColor()

```
void OH_ArkUI_SwiperIndicator_SetColor (ArkUI_SwiperIndicator * indicator, uint32_t color )
```
**描述：**

设置 Swiper 组件圆点导航指示器的颜色。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| color | 颜色类型，0xargb格式，形如 0xFFFF0000 表示红色。  |


### OH_ArkUI_SwiperIndicator_SetEndPosition()

```
void OH_ArkUI_SwiperIndicator_SetEndPosition (ArkUI_SwiperIndicator * indicator, float value )
```
**描述：**

设置导航点距离 Swiper 组件右边的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| value | 导航点距离Swiper组件右边的距离。默认值：0，单位：vp。  |


### OH_ArkUI_SwiperIndicator_SetItemHeight()

```
void OH_ArkUI_SwiperIndicator_SetItemHeight (ArkUI_SwiperIndicator * indicator, float value )
```
**描述：**

设置 Swiper 组件圆点导航指示器的高。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| value | 圆点导航指示器的高。默认值：6，单位：vp。  |


### OH_ArkUI_SwiperIndicator_SetItemWidth()

```
void OH_ArkUI_SwiperIndicator_SetItemWidth (ArkUI_SwiperIndicator * indicator, float value )
```
**描述：**

设置 Swiper 组件圆点导航指示器的宽。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| value | 圆点导航指示器的宽。默认值：12，单位：vp。  |


### OH_ArkUI_SwiperIndicator_SetMask()

```
void OH_ArkUI_SwiperIndicator_SetMask (ArkUI_SwiperIndicator * indicator, int32_t mask )
```
**描述：**

设置是否显示 Swiper 组件圆点导航指示器的蒙版样式。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| mask | 是否显示蒙版样式，1 表示显示，0 表示不显示。  |


### OH_ArkUI_SwiperIndicator_SetMaxDisplayCount()

```
int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount (ArkUI_SwiperIndicator * indicator, int32_t maxDisplayCount )
```
**描述：**

设置圆点导航点指示器样式下，导航点显示个数的最大值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| maxDisplayCount | 导航点显示个数最大值，有效取值范围6-9。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 如果maxDisplayCount设置范围错误, 返回错误码。


### OH_ArkUI_SwiperIndicator_SetSelectedColor()

```
void OH_ArkUI_SwiperIndicator_SetSelectedColor (ArkUI_SwiperIndicator * indicator, uint32_t selectedColor )
```
**描述：**

设置被选中 Swiper 组件圆点导航指示器的颜色。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| selectedColor | 颜色类型，0xargb格式，形如 0xFFFF0000 表示红色。  |


### OH_ArkUI_SwiperIndicator_SetSelectedItemHeight()

```
void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight (ArkUI_SwiperIndicator * indicator, float value )
```
**描述：**

设置被选中的 Swiper 组件圆点导航指示器的高。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| value | 圆点导航指示器的高。默认值：6，单位：vp。  |


### OH_ArkUI_SwiperIndicator_SetSelectedItemWidth()

```
void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth (ArkUI_SwiperIndicator * indicator, float value )
```
**描述：**

设置被选中的 Swiper 组件圆点导航指示器的宽。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| value | 圆点导航指示器的宽。默认值：12，单位：vp。  |


### OH_ArkUI_SwiperIndicator_SetStartPosition()

```
void OH_ArkUI_SwiperIndicator_SetStartPosition (ArkUI_SwiperIndicator * indicator, float value )
```
**描述：**

设置导航点距离 Swiper 组件左边的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| value | 导航点距离Swiper组件左边的距离。默认值：0，单位：vp。  |


### OH_ArkUI_SwiperIndicator_SetTopPosition()

```
void OH_ArkUI_SwiperIndicator_SetTopPosition (ArkUI_SwiperIndicator * indicator, float value )
```
**描述：**

设置导航点距离 Swiper 组件顶部的距离。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| indicator | 导航指示器对象指针。  |
| value | 导航点距离Swiper组件顶部的距离。默认值：0，单位：vp。  |


### OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale()

```
float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale (const ArkUI_SystemFontStyleEvent * event)
```
**描述：**

获取系统字体变更事件的字体大小值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 表示指向当前系统字体变更事件的指针。  |

**返回：**

更新后的系统字体大小缩放系数。默认值：1.0。


### OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale()

```
float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale (const ArkUI_SystemFontStyleEvent * event)
```
**描述：**

获取系统字体变更事件的字体粗细值。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 表示指向当前系统字体变更事件的指针。  |

**返回：**

更新后的系统字体粗细缩放系数。默认值：1.0。


### OH_ArkUI_TransitionEffect_Combine()

```
int32_t OH_ArkUI_TransitionEffect_Combine (ArkUI_TransitionEffect * option, ArkUI_TransitionEffect * combine )
```
**描述：**

设置转场效果链式组合，以形成包含多种转场效果的TransitionEffect。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 转场效果。  |
| combine | 需要链式转场效果。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_TransitionEffect_Dispose()

```
void OH_ArkUI_TransitionEffect_Dispose (ArkUI_TransitionEffect * option)
```
**描述：**

销毁转场效果对象。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 转场效果对象。  |


### OH_ArkUI_TransitionEffect_SetAnimation()

```
int32_t OH_ArkUI_TransitionEffect_SetAnimation (ArkUI_TransitionEffect * option, ArkUI_AnimateOption * animation )
```
**描述：**

设置转场效果动画参数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 转场效果。  |
| animation | 属性显示动画效果相关参数。  |

**注解：**

如果通过combine进行转场效果的组合，前一转场效果的动画参数也可用于后一转场效果。

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_UnmarshallStyledStringDescriptor()

```
int32_t OH_ArkUI_UnmarshallStyledStringDescriptor (uint8_t * buffer, size_t bufferSize, ArkUI_StyledString_Descriptor * descriptor)
```
**描述：**

将包含属性字符串信息的字节数组反序列化为属性字符串。

**起始版本：** 14

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| buffer | 待反序列化的字节数组。  |
| bufferSize | 字节数组长度。  |
| descriptor | 指向ArkUI_StyledString_Descriptor对象的指针。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。 ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_UnregisterSystemColorModeChangeEvent()

```
void OH_ArkUI_UnregisterSystemColorModeChangeEvent (ArkUI_NodeHandle node)
```
**描述：**

注销系统深浅色变更事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |


### OH_ArkUI_UnregisterSystemFontStyleChangeEvent()

```
void OH_ArkUI_UnregisterSystemFontStyleChangeEvent (ArkUI_NodeHandle node)
```
**描述：**

注销系统字体变更事件。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |


### OH_ArkUI_WaterFlowSectionOption_Create()

```
ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create ()
```
**描述：**

创建FlowItem分组配置信息。

**起始版本：** 12

**返回：**

FlowItem分组配置信息。


### OH_ArkUI_WaterFlowSectionOption_Dispose()

```
void OH_ArkUI_WaterFlowSectionOption_Dispose (ArkUI_WaterFlowSectionOption * option)
```
**描述：**

销毁FlowItem分组配置信息指针。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |


### OH_ArkUI_WaterFlowSectionOption_GetColumnGap()

```
float OH_ArkUI_WaterFlowSectionOption_GetColumnGap (ArkUI_WaterFlowSectionOption * option, int32_t index )
```
**描述：**

通过FlowItem分组配置信息获取对应索引下的分组的列间距。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |

**返回：**

列间距。


### OH_ArkUI_WaterFlowSectionOption_GetCrossCount()

```
int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount (ArkUI_WaterFlowSectionOption * option, int32_t index )
```
**描述：**

通过FlowItem分组配置信息获取对应索引下的布局栅格数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |

**返回：**

布局栅格数量。


### OH_ArkUI_WaterFlowSectionOption_GetItemCount()

```
int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount (ArkUI_WaterFlowSectionOption * option, int32_t index )
```
**描述：**

通过FlowItem分组配置信息获取对应索引下的FlowItem数量。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |

**返回：**

分组中FlowItem数量。


### OH_ArkUI_WaterFlowSectionOption_GetMargin()

```
ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin (ArkUI_WaterFlowSectionOption * option, int32_t index )
```
**描述：**

通过FlowItem分组配置信息获取对应索引下的分组的外边距。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |

**返回：**

外边距。


### OH_ArkUI_WaterFlowSectionOption_GetRowGap()

```
float OH_ArkUI_WaterFlowSectionOption_GetRowGap (ArkUI_WaterFlowSectionOption * option, int32_t index )
```
**描述：**

通过FlowItem分组配置信息获取对应索引下的分组的行间距。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |

**返回：**

行间距。


### OH_ArkUI_WaterFlowSectionOption_GetSize()

```
int32_t OH_ArkUI_WaterFlowSectionOption_GetSize (ArkUI_WaterFlowSectionOption * option)
```
**描述：**

获取FlowItem分组配置信息数组长度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |

**返回：**

数组长度。如果返回-1，则返回失败。失败的原因可能是option参数异常，如空指针。


### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex()

```
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex (ArkUI_WaterFlowSectionOption * option, int32_t index, float(*)(int32_t itemIndex) callback )
```
**描述：**

通过FlowItem分组配置信息根据flowItemIndex获取指定Item的主轴大小。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |
| callback | 根据index获取指定Item的主轴大小。  |


### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData()

```
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData (ArkUI_WaterFlowSectionOption * option, int32_t index, void * userData, float(*)(int32_t itemIndex, void *userData) callback )
```
**描述：**

通过FlowItem分组配置信息根据flowItemIndex获取指定Item的主轴大小。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |
| userData | FlowItem自定义数据。  |
| callback | 根据index获取指定Item的主轴大小。  |


### OH_ArkUI_WaterFlowSectionOption_SetColumnGap()

```
void OH_ArkUI_WaterFlowSectionOption_SetColumnGap (ArkUI_WaterFlowSectionOption * option, int32_t index, float columnGap )
```
**描述：**

设置分组的列间距。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |
| columnGap | 列间距。  |


### OH_ArkUI_WaterFlowSectionOption_SetCrossCount()

```
void OH_ArkUI_WaterFlowSectionOption_SetCrossCount (ArkUI_WaterFlowSectionOption * option, int32_t index, int32_t crossCount )
```
**描述：**

设置布局栅格，纵向布局时为列数，横向布局时为行数。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |
| crossCount | 布局栅格数量。  |


### OH_ArkUI_WaterFlowSectionOption_SetItemCount()

```
void OH_ArkUI_WaterFlowSectionOption_SetItemCount (ArkUI_WaterFlowSectionOption * option, int32_t index, int32_t itemCount )
```
**描述：**

设置分组中FlowItem数量。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |
| itemCount | 分组中FlowItem数量。  |


### OH_ArkUI_WaterFlowSectionOption_SetMargin()

```
void OH_ArkUI_WaterFlowSectionOption_SetMargin (ArkUI_WaterFlowSectionOption * option, int32_t index, float marginTop, float marginRight, float marginBottom, float marginLeft )
```
**描述：**

设置分组的外边距。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |
| marginTop | FlowItem上外边距。  |
| marginRight | FlowItem右外边距。  |
| marginBottom | FlowItem下外边距。  |
| marginLeft | FlowItem左外边距。  |


### OH_ArkUI_WaterFlowSectionOption_SetRowGap()

```
void OH_ArkUI_WaterFlowSectionOption_SetRowGap (ArkUI_WaterFlowSectionOption * option, int32_t index, float rowGap )
```
**描述：**

设置分组的行间距。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| index | FlowItem索引值。  |
| rowGap | 行间距。  |


### OH_ArkUI_WaterFlowSectionOption_SetSize()

```
void OH_ArkUI_WaterFlowSectionOption_SetSize (ArkUI_WaterFlowSectionOption * option, int32_t size )
```
**描述：**

设置FlowItem分组配置信息数组长度。

**起始版本：** 12

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | FlowItem分组配置信息。  |
| size | 数组长度。  |


### OH_ArkUI_PostFrameCallback()

```
int32_t OH_ArkUI_PostFrameCallback(ArkUI_ContextHandle uiContext, void* userData, void (*callback)(uint64_t nanoTimestamp, uint32_t frameCount, void* userData))
```
**描述：**

注册一个回调函数，以便在下一帧渲染时执行。不允许在非UI线程调用，检查到非UI线程调用程序会主动abort。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| uiContext | uiContext对象，用以绑定实例。|
| userData | 自定义事件参数，当事件触发时在回调参数中携带回来。|
| callback | 自定义回调函数，会在下一帧事件结束后回调。|
| nanoTimestamp | 帧信号的时间戳。|
| frameCount | 帧号。|

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](_ark_u_i___native_module.md#arkui_errorcode) CAPI初始化错误。</br >
[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](_ark_u_i___native_module.md#arkui_errorcode) uiContext对象无效。</br >
[ARKUI_ERROR_CODE_CALLBACK_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 回调函数无效。</br >


### OH_ArkUI_PostIdleCallback()

```
int32_t OH_ArkUI_PostIdleCallback(ArkUI_ContextHandle uiContext, void* userData, void (*callback)(uint64_t nanoTimeLeft, uint32_t frameCount, void* userData))
```
**描述：**

注册一个回调函数，在下一帧渲染结束后如果距离下一个Vsync信号到来剩余时间大于1ms时，该回调函数将被执行；如果剩余时间小于1ms时，回调函数将被顺延至当某个下一帧的剩余时间大于1ms时再执行。如果当前没有下一帧，将自动请求下一帧。

**起始版本：** 20

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| uiContext | uiContext对象，用以绑定实例。| 
| userData | 自定义事件参数，当自定义回调函数触发时在回调参数中携带回来。| 
| callback | 自定义回调函数，会在下一帧事件结束后剩余时间大于1ms时回调执行。| 
| nanoTimeLeft | 下一帧渲染后的剩余时间。| 
| frameCount | 帧号。| 

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](_ark_u_i___native_module.md#arkui_errorcode) CAPI初始化错误。</br >
[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](_ark_u_i___native_module.md#arkui_errorcode) UIContext对象无效。</br >
[ARKUI_ERROR_CODE_CALLBACK_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 回调函数无效。</br >


### OH_ArkUI_InitModuleForArkTSEnv()

```
ArkUI_ErrorCode OH_ArkUI_InitModuleForArkTSEnv(napi_env env)
```
**描述：**

初始化指定上下文环境的ArkUI相关接口。该函数禁止在非UI线程中调用，否则程序将主动abort。每个上下文环境都会占用一定的内存，当内存消耗超过虚拟机的上限时，将导致内存溢出。有关ArkTS内存管理的详细信息，请参阅[GC垃圾回收](../../arkts-utils/gc-introduction.md)。

**起始版本：** 20

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| env | Node-API的环境指针。| 

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 参数无效（如env为null或设置白名单失败）。</br >
[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](_ark_u_i___native_module.md#arkui_errorcode) CAPI初始化错误。</br >


### OH_ArkUI_NotifyArkTSEnvDestroy()

```
void OH_ArkUI_NotifyArkTSEnvDestroy(napi_env env)
```
**描述：**

通知指定的上下文环境已销毁。该函数禁止在非UI线程中调用，否则程序将主动abort。

**起始版本：** 20

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| env | Node-API的环境指针。| 


### OH_ArkUI_RegisterLayoutCallbackOnNodeHandle()

```
int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle (ArkUI_NodeHandle node, void* userData, void (*onLayoutCompleted)(void* userData))
```
**描述：**

注册组件布局完成回调方法。同一组件仅能注册一个布局完成回调方法。示例请参考：[注册组件布局和绘制送显回调](../../ui/ndk-inspector-component-observer.md)。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| userData | 自定义事件参数，当事件触发时在回调参数中携带回来。  |
| onLayoutCompleted | 事件触发后的回调。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。


### OH_ArkUI_RegisterDrawCallbackOnNodeHandle()

```
int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle (ArkUI_NodeHandle node, void* userData, void (*onDrawCompleted)(void* userData))
```
**描述：**

注册组件绘制送显完成回调方法。同一组件仅能注册一个绘制完成回调方法。示例请参考：[注册组件布局和绘制送显回调](../../ui/ndk-inspector-component-observer.md)。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| userData | 自定义事件参数，当事件触发时在回调参数中携带回来。  |
| onDrawCompleted | 事件触发后的回调。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。


### OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle()

```
int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle (ArkUI_NodeHandle node)
```
**描述：**

取消注册组件布局完成回调方法。示例请参考：[注册组件布局和绘制送显回调](../../ui/ndk-inspector-component-observer.md)。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。


### OH_ArkUI_UnregisterDrawCallbackOnNodeHandle()

```
int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle (ArkUI_NodeHandle node)
```
**描述：**

取消注册组件绘制送显完成回调方法。示例请参考：[注册组件布局和绘制送显回调](../../ui/ndk-inspector-component-observer.md)。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。

### OH_ArkUI_NodeEvent_GetTextChangeEvent()

```
ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)
```
**描述：**

获取组件事件中的ArkUI_TextChangeEvent数据。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 组件事件指针，不应为空。  |

**返回：**

[ArkUI_TextChangeEvent*](_ark_u_i___text_change_event.md) 返回ArkUI_TextChangeEvent对象的指针。


### OH_ArkUI_RunTaskInScope()

```
int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(*callback)(void* userData))
```
**描述：**

在目标UI上下文中执行传入的自定义回调函数。示例请参考：[在NDK中保证多实例场景功能正常](../../ui/ndk-scope-task.md)。

**起始版本：** 20

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| uiContext | 表示目标UI上下文的指针。  |
| userData | 开发者自定义数据指针，以便在回调函数中处理自定义数据，开发者需自行保证自定义函数被执行时的数据有效性。 |
| callback | 开发者自定义回调函数。 |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。</br >
[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](_ark_u_i___native_module.md#arkui_errorcode) CAPI初始化错误。</br >
[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](_ark_u_i___native_module.md#arkui_errorcode) UIContext对象无效。</br >
[ARKUI_ERROR_CODE_CALLBACK_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 回调函数无效。</br >


### OH_ArkUI_ProgressLinearStyleOption_Create

```
ArkUI_ProgressLinearStyleOption* OH_ArkUI_ProgressLinearStyleOption_Create(void)
```
**描述：**

创建线性进度条样式信息。

**起始版本：** 15

**返回：**

ProgressLinearStyleOption实例。


### OH_ArkUI_ProgressLinearStyleOption_Destroy

```
void OH_ArkUI_ProgressLinearStyleOption_Destroy(ArkUI_ProgressLinearStyleOption* option)
```
**描述：**

销毁线性进度条样式信息。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 要销毁的ProgressLinearStyleOption实例。  |


### OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled

```
void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```
**描述：**

设置扫光效果的开关。

**起始版本：** 15


**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ProgressLinearStyleOption实例。  |
| enabled | 扫光效果的开关。默认值：false。 |


### OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled

```
void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```
**描述：**

设置进度平滑动效的开关。

**起始版本：** 15


**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ProgressLinearStyleOption实例。  |
| enabled | 进度平滑动效的开关。开启平滑动效后设置进度，进度会从当前值渐变至设定值，否则进度从当前值突变至设定值。默认值：true。 |


### OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth

```
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth(ArkUI_ProgressLinearStyleOption* option, float strokeWidth)
```
**描述：**

设置线性进度条宽度。

**起始版本：** 15


**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ProgressLinearStyleOption实例。  |
| strokeWidth | 进度条宽度值（不支持百分比设置），默认值：4.0vp。 |


### OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius

```
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius(ArkUI_ProgressLinearStyleOption* option, float strokeRadius)
```
**描述：**

设置线性进度条圆角半径。

**起始版本：** 15


**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ProgressLinearStyleOption实例。  |
| strokeRadius | 进度条圆角半径值，取值范围[0, strokeWidth/2]。默认值：strokeWidth/2。 |


### OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled

```
bool OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```
**描述：**

获取线性进度条扫光效果的开关信息。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ProgressLinearStyleOption实例。  |

**返回：**

是否开启扫光效果。


### OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled

```
bool OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```
**描述：**

获取线性进度条进度平滑动效的开关信息。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ProgressLinearStyleOption实例。  |

**返回：**

是否开启平滑动效。


### OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth

```
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth(ArkUI_ProgressLinearStyleOption* option)
```
**描述：**

获取线性进度条宽度。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ProgressLinearStyleOption实例。  |

**返回：**

进度条宽度值。


### OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius

```
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius(ArkUI_ProgressLinearStyleOption* option)
```
**描述：**

获取线性进度条圆角半径值。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | ProgressLinearStyleOption实例。  |

**返回：**

进度条圆角半径值。


### OH_ArkUI_DragEvent_StartDataLoading()

```
int32_t OH_ArkUI_DragEvent_StartDataLoading (ArkUI_DragEvent* event, OH_UdmfGetDataParams* options, char* key, unsigned int keyLen)
```
**描述：**

使用指定的同步参数开始数据同步。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| options | 从UDMF获取数据时的参数。  |
| key | 数据的唯一标识，当事件触发时在回调参数中携带回来。  |
| keyLen | key的长度，需要大于等于UDMF_KEY_BUFFER_LEN。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_CancelDataLoading()

```
int32_t OH_ArkUI_CancelDataLoading (ArkUI_ContextHandle uiContext, const char* key)
```
**描述：**

取消正在进行的数据同步。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| uiContext | uiContext对象，用以绑定实例。|
| key | 数据的唯一标识。|

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_DisableDropDataPrefetchOnNode()

```
int32_t OH_ArkUI_DisableDropDataPrefetchOnNode (ArkUI_NodeHandle node, bool disable)
```
**描述：**

异步获取拖拽数据。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 指定的节点。  |
| disable | 设置拖拽是否提前获取数据。true为不提前获取数据，默认值为false。当使用OH_ArkUI_DragEvent_StartDataLoading获取数据时，需设置为true。 |


**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。

### OH_ArkUI_CrossLanguageOption_Create()

```
ArkUI_CrossLanguageOption* OH_ArkUI_CrossLanguageOption_Create(void)
```
**描述：**

创建跨语言配置项实例。

**起始版本：** 15

**返回：**

返回跨语言实例。如果对象返回空指针，则表示创建失败，失败的原因可能是地址空间已满。


### OH_ArkUI_CrossLanguageOption_Destroy()

```
void OH_ArkUI_CrossLanguageOption_Destroy(ArkUI_CrossLanguageOption* option)
```
**描述：**

销毁跨语言配置项实例。

**起始版本：** 15

**参数：**

| 名称 | 描述 |
| -------- | -------- |
| option | 要销毁的跨语言配置项实例。  |

### OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus()

```
void OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus(ArkUI_CrossLanguageOption* option, bool enabled)
```
**描述：**

设置配置项中是否允许跨语言修改属性。

**起始版本：** 15

**参数：**

| 名称 | 描述 |
| -------- | -------- |
| option | 跨语言配置项实例。  |
| enabled | 是否允许跨语言修改属性。默认值：false。  |

### OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus()

```
bool OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus(ArkUI_CrossLanguageOption* option)
```
**描述：**

获取配置项中是否允许跨语言修改属性。

**起始版本：** 15

**参数：**

| 名称 | 描述 |
| -------- | -------- |
| option | 跨语言配置项实例。  |

**返回：**

是否允许跨语言修改属性。

### OH_ArkUI_VisibleAreaEventOptions_Create()

```
ArkUI_VisibleAreaEventOptions* OH_ArkUI_VisibleAreaEventOptions_Create()
```
**描述：**

创建可见区域变化监听的参数。

**起始版本：** 17

**返回：**
可见区域变化监听的参数。

### OH_ArkUI_VisibleAreaEventOptions_Dispose()

```
void OH_ArkUI_VisibleAreaEventOptions_Dispose(ArkUI_VisibleAreaEventOptions* option)
```
**描述：**

销毁可见区域变化监听的参数。

**起始版本：** 17

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 需要销毁的实例。  |

### OH_ArkUI_VisibleAreaEventOptions_SetRatios()

```
int32_t OH_ArkUI_VisibleAreaEventOptions_SetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t size)
```
**描述：**

设置阈值数组。

**起始版本：** 17

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 可见区域变化监听的参数实例。|
| value | 阈值数组。|
| size | 阈值数组大小。|

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。

### OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval()

```
int32_t OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval(
    ArkUI_VisibleAreaEventOptions *option, int32_t value)
```
**描述：**

设置预期更新间隔，单位为ms。定义了开发者期望的更新间隔。

**起始版本：** 17

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 可见区域变化监听的参数实例。|
| value | 预期更新间隔，单位为ms。定义了开发者期望的更新间隔。默认值：1000。|

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。

### OH_ArkUI_VisibleAreaEventOptions_GetRatios()

```
int32_t OH_ArkUI_VisibleAreaEventOptions_GetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t* size)
```
**描述：**

 获取阈值数组。

**起始版本：** 17

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 可见区域变化监听的参数实例。|
| value | 阈值数组。|
| size | 阈值数组大小。|

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。
ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR 数组大小不够。

### OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval()

```
int32_t OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions* option)
```
**描述：**

 获取预期更新间隔。

**起始版本：** 17

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 可见区域变化监听的参数实例。|

**返回：**
预期更新间隔，单位为ms。定义了开发者期望的更新间隔。默认值：1000。

### OH_ArkUI_NodeUtils_GetPositionToParent()

```
int32_t OH_ArkUI_NodeUtils_GetPositionToParent (ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset )
```
**描述：**

获取目标节点相对于父节点的偏移值，单位：px。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | ArkUI_NodeHandle指针。  |
| globalOffset | 组件handle相对父节点的偏移值，单位：px。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AddSupportedUIStates()

```
ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)
```
**描述：**

设置组件支持的多态样式状态。为了更高效地处理，需传入所关注的状态值及对应的状态处理函数，当关注的状态发生时，处理函数会被执行。

可在回调中根据当前状态调整UI样式。当在同一个节点上多次调用该方法时，将以最后一次传入的状态及处理函数为准。

有些类型的组件节点，系统内部已有对某些状态的默认处理。例如，Button组件默认具备对PRESSED状态的样式变化，当在此类组件上使用此方法自定义状态处理时，
会先应用系统默认样式变化，再执行自定义的样式处理，最终效果为两者叠加。

可以通过指定excludeInner为true来禁用系统内部的默认样式效果，但这通常取决于系统内部实现规范是否允许。

当调用该函数时，传入的statesChangeHandler函数会立即执行一次，且无需特意注册对NORMAL状态的监听，只要注册了非NORMAL状态，当状态从任意状态变化回NORMAL时，系统都会进行回调，以便应用进行样式复原。

**起始版本：** 20

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点。  |
| uiStates | 目标节点需要处理的目标UI状态。<br>所有目标UI状态的组合结果可以通过“&nbsp;\|&nbsp;”操作来计算。例如：targetUIStates = ArkUI_UIState::PRESSED &nbsp;\|&nbsp; ArkUI_UIState::FOCUSED。  |
| statesChangeHandler | UI状态改变处理函数。<br>返回当前UI状态，该值是所有当前状态枚举值“&nbsp;\|&nbsp;”计算的结果，可以通过执行“&”操作来确定状态。例如：if (currentStates & ArkUI_UIState::PRESSED == ArkUI_UIState::PRESSED)。但是，对于正常状态检查，应直接使用等号。例如：if (currentStates == ArkUI_UIState::NORMAL)。  |
| excludeInner | 禁止内部默认状态样式的标志。  |
| userData | onDrawCompleted回调函数中使用的自定义数据。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。

### OH_ArkUI_RemoveSupportedUIStates()

```
ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)
```
**描述：**

删除注册的状态处理。当通过OH_ArkUI_AddSupportedUIStates注册的状态都被删除时，所注册的stateChangeHandler也不会再被执行。

**起始版本：** 20

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 目标节点。  |
| uiStates | 节点需要删除的目标UI状态。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。

### OH_ArkUI_GetGestureParam_DirectMask()

```
int32_t OH_ArkUI_GetGestureParam_DirectMask(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureDirectionMask* directMask)
```
**描述：**

获取手势识别器的滑动方向。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| directMask | 手势识别器的滑动方向。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 参数错误。

### OH_ArkUI_GetGestureParam_FingerCount()

```
int32_t OH_ArkUI_GetGestureParam_FingerCount(ArkUI_GestureRecognizer* recognizer, int* finger)
```
**描述：**

获取手势识别器的手指数。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| finger | 手势识别器的手指数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 参数错误。

### OH_ArkUI_GetGestureParam_limitFingerCount()

```
int32_t OH_ArkUI_GetGestureParam_limitFingerCount(ArkUI_GestureRecognizer* recognizer, bool* isLimited)
```
**描述：**

获取手势识别器是否有手指数限制。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| isLimited | 手势识别器是否有手指数限制。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 参数错误。

### OH_ArkUI_GetGestureParam_repeat()

```
int32_t OH_ArkUI_GetGestureParam_repeat(ArkUI_GestureRecognizer* recognizer, bool* isRepeat)
```
**描述：**

获取手势识别器是否连续触发事件回调。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| isRepeat | 手势识别器是否连续触发事件回调。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED 不支持手势识别器类型。

### OH_ArkUI_GetGestureParam_distance()

```
int32_t OH_ArkUI_GetGestureParam_distance(ArkUI_GestureRecognizer* recognizer, double* distance)
```
**描述：**

获取手势识别器的手指允许的移动距离范围。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| distance | 手势识别器的手指允许的移动距离范围。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED 不支持手势识别器类型。

### OH_ArkUI_GetGestureParam_speed()

```
int32_t OH_ArkUI_GetGestureParam_speed(ArkUI_GestureRecognizer* recognizer, double* speed)
```
**描述：**

获取手势识别器的识别滑动的最小速度。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| speed | 手势识别器的识别滑动的最小速度。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED 不支持手势识别器类型。

### OH_ArkUI_GetGestureParam_duration()

```
int32_t OH_ArkUI_GetGestureParam_duration(ArkUI_GestureRecognizer* recognizer, int* duration)
```
**描述：**

获取手势识别器的触发长按的最短时间。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| duration | 手势识别器的触发长按的最短时间。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED 不支持手势识别器类型。

### OH_ArkUI_GetGestureParam_angle()

```
int32_t OH_ArkUI_GetGestureParam_angle(ArkUI_GestureRecognizer* recognizer, double* angle)
```
**描述：**

获取手势识别器的旋转手势的最小改变度数。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| angle | 手势识别器的旋转手势的最小改变度数。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED 不支持手势识别器类型。

### OH_ArkUI_GetGestureParam_distanceThreshold()

```
int32_t OH_ArkUI_GetGestureParam_distanceThreshold(ArkUI_GestureRecognizer* recognizer, double* distanceThreshold)
```
**描述：**

获取手势识别器的手势移动阈值。

**起始版本：** 18

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| distanceThreshold | 手势识别器的手势移动阈值。单位：px。  |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED 不支持手势识别器类型。

### OH_ArkUI_PanGesture_SetDistanceMap()

```
ArkUI_ErrorCode OH_ArkUI_PanGesture_SetDistanceMap(ArkUI_GestureRecognizer* recognizer, int size, int* toolTypeArray, double* distanceArray)
```
**描述：**

设置手势最小滑动阈值表。当设备类型为非法值时，设置不生效。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| size | 手势最小滑动阈值数组的大小。 |
| toolTypeArray | 指向输入事件的工具类型数组的指针。 |
| distanceArray | 指向最小滑动阈值数组的指针。单位为px。 |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 参数错误。
ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED 不支持手势识别器类型。

### OH_ArkUI_PanGesture_GetDistanceByToolType()

```
ArkUI_ErrorCode OH_ArkUI_PanGesture_GetDistanceByToolType(ArkUI_GestureRecognizer* recognizer, int toolType, double* distance)
```
**描述：**

获取手势识别器的手势移动阈值表。仅支持对通过OH_ArkUI_PanGesture_SetDistanceMap修改过的设备类型的阈值查询。默认滑动阈值可通过查询UI_INPUT_EVENT_TOOL_TYPE_UNKNOWN类型获得，其他未设置过的类型不会返回。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| recognizer | 手势识别器指针。  |
| toolType | 输入事件的工具类型。 |
| distance | 手势识别器的手势移动阈值。单位为px。 |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 参数错误。
ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED 不支持手势识别器类型。

### OH_ArkUI_SetTouchTestDoneCallback()

```
ArkUI_ErrorCode OH_ArkUI_SetTouchTestDoneCallback(ArkUI_NodeHandle node, void* userData,
    void (*touchTestDone)(ArkUI_GestureEvent* event, ArkUI_GestureRecognizerHandleArray recognizers, int32_t count, void* userData))
```
**描述：**

注册一个在所有手势识别器收集完成后执行的回调函数。当用户开始触摸屏幕时，系统会进行命中测试并根据触摸位置收集手势识别器。随后，在处理移动事件之前，组件可以使用此接口确定将参与识别并相互竞争的手势识别器。

**起始版本：** 20

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| node | 需要设置手势收集完成回调的节点句柄。 |
| userData | 自定义事件参数，在回调触发时在回调函数中携带。 |
| touchTestDone | 手势收集完成后触发的回调函数。<br>- event：手势的基本信息。<br>- recognizers：手势识别器数组。<br>- count：手势识别器个数。  |

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。
[ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 参数错误。

### OH_ArkUI_DragEvent_RequestDragEndPending()

```
int32_t OH_ArkUI_DragEvent_RequestDragEndPending(ArkUI_DragEvent* event, int32_t* requestIdentify)
```
**描述：**

请求延迟执行拖拽结束。在系统通知应用drop时，调用该方法，可以明确告知系统，需要延迟一段时间才能告知拖拽处理结果，系统会推迟结束整个拖拽的结束，等待应用通过 OH_ArkUI_NotifyDragResult 接口返回拖拽处理结果后，再执行后续流程。这通常使用在不想在主线程处理拖拽数据的情况下，以免长时间阻塞主线程，同时又可确保，在整个拖拽流程结束时，拖起方可以拿到准确的拖拽处理结果。但需要注意的时，系统不会无限等待应用，最大超时时间为2s，在超时后，如果仍然无法收到 OH_ArkUI_NotifyDragResult 通知，则会强制结束拖拽流程，并通知拖起方落入失败。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | ArkUI_DragEvent事件指针。  |
| requestIdentify | 此次延迟落入行为的唯一标识。 |


**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。
ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED 执行函数时不在落入的时机。



### OH_ArkUI_NotifyDragResult()

```
int32_t OH_ArkUI_NotifyDragResult(int32_t requestIdentify, ArkUI_DragResult result)
```
**描述：**

通知拖拽结果。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| requestIdentify | 此次延迟落入行为的唯一标识。 |
| result | 拖拽事件对应的拖拽结果。 |


**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。
ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED 执行函数时不允许落入。


### OH_ArkUI_NotifyDragEndPendingDone()

```
int32_t OH_ArkUI_NotifyDragEndPendingDone(int32_t requestIdentify)
```
**描述：**

通知拖拽延迟执行结束。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| requestIdentify | 此次延迟落入行为的唯一标识。 |


**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。
ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED 执行函数时不允许落入。

### OH_ArkUI_TextPickerRangeContentArray_Create()

```
ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)
```
**描述：**

创建TextPickerRangeContent数组的对象。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| length | 指定TextPickerRangeContent数组的长度。  |

**返回：**

返回指向TextPickerRangeContent空数组的指针。

### OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex()

```
void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle,char* icon,int32_t index);
```
**描述：**

 指定TextPickerRangeContent数组指定位置的icon数据。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向TextPickerRangeContent数组的指针。|
| icon | 图片地址。|
| index | 数组位置，从0开始。|


### OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex()

```
void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle,char* text,int32_t index);
```
**描述：**

 指定TextPickerRangeContent数组指定位置的text数据。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向TextPickerRangeContent数组的指针。|
| text | 文本内容。|
| index | 数组位置，从0开始。|


### OH_ArkUI_TextPickerRangeContentArray_Destroy()

```
void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle);
```
**描述：**

 删除TextPickerRangeContent数组对象。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向TextPickerRangeContent数组的指针。|


### OH_ArkUI_TextCascadePickerRangeContentArray_Create()

```
ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length);
```
**描述：**

创建TextCascadePickerRangeContent数组对象。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| length | 指向TextPickerRangeContent数组的长度。|

**返回：**

返回指向TextCascadePickerRangeContent空数组的指针。

### OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex()

```
void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle,char* text,int32_t index);
```
**描述：**

 指定TextCascadePickerRangeContent数组指定位置的text数据。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向TextCascadePickerRangeContentHandle的指针。|
| text | 文本内容。|
| index | 数组位置，从0开始。|


### OH_ArkUI_TextCascadePickerRangeContentArray_setChildAtIndex()

```
void OH_ArkUI_TextCascadePickerRangeContentArray_setChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle,ArkUI_TextCascadePickerRangeContentArray* child,int32_t index);
```
**描述：**

 指定TextCascadePickerRangeContent数组指定位置的child数据。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向TextCascadePickerRangeContentHandle的指针。|
| child | 子节点数组指针。|
| index | 数组位置，从0开始。|


### OH_ArkUI_TextCascadePickerRangeContentArray_Destroy()

```
void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle);
```
**描述：**

 删除TextCascadePickerRangeContent数组对象。

**起始版本：** 19

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| handle | 指向TextCascadePickerRangeContentHandle的指针。|

### OH_ArkUI_GetNodeSnapshot()

```
int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelMap)
```

**描述**

获取指定组件节点的截图，执行过程为同步，调用时应确保对应节点已被渲染(避免在把节点挂树时就立即执行截图，因为图形的渲染一般需要一帧时间生效)。

**注意：**

当返回的Pixelmap不再使用时，应通过 [OH_PixelmapNative_Release](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_release) 释放它。

**起始版本：** 15

**参数:**

| 名称          |  描述                                                     |
| --------------- | ------------------------------------------------------------ |
| node            | 截图的目标节点。                                             |
| snapshotOptions | 给定的截图配置，为空时表示默认配置。              |
| pixelmap        | 通过系统创建的pixelmap指针。 |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。
ARKUI_ERROR_CODE_INTERNAL_ERROR 截图失败，将返回空指针。
ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT 截图超时。


### OH_ArkUI_CreateSnapshotOptions()

```
ArkUI_SnapshotOptions* OH_ArkUI_CreateSnapshotOptions()
```

**描述**

创建一个截图选项，当返回值不再使用时必须通过`OH_ArkUI_SnapshotOptions_Dispose`释放。

**起始版本：** 15

**返回：**

返回指向创建的截图选项对象的指针。


### OH_ArkUI_DestroySnapshotOptions()

```
void OH_ArkUI_DestroySnapshotOptions(ArkUI_SnapshotOptions* snapshotOptions)
```

**描述**

销毁截图选项指针。

**起始版本：** 15

**参数:**

| 名称         | 描述         |
| --------------- | ---- |
| snapshotOptions | 截图选项。 |

### OH_ArkUI_SnapshotOptions_SetScale()

```
int32_t OH_ArkUI_SnapshotOptions_SetScale(ArkUI_SnapshotOptions* snapshotOptions, float scale)
```

**描述**

配置截图选项中的缩放属性。

**起始版本：** 15

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| snapshotOptions | 截图选项。 |
| scale           | 缩放值。<br>取值范围：(0,+∞) |

**返回：**

ARKUI_ERROR_CODE_NO_ERROR 成功。
ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。


### OH_ArkUI_AccessibilityValue_SetRangeMin

```
void OH_ArkUI_AccessibilityValue_SetRangeMin(ArkUI_AccessibilityValue* value, int32_t rangeMin)
```

**描述：**

用于设置范围组件的无障碍最小值信息。

当范围组件未设置无障碍最小值时，默认为-1。

**起始版本：** 18

**参数:**

| 名称      | 描述                   |
| --------- | ---------------------- |
| value | 需要设置最小值的范围组件无障碍信息对象指针。   |
| rangeMin       | 基于范围组件的最小值。              |


### OH_ArkUI_AccessibilityValue_GetRangeMin

```
int32_t OH_ArkUI_AccessibilityValue_GetRangeMin(ArkUI_AccessibilityValue* value)
```

**描述：**

用于获取范围组件的无障碍最小值信息。

若函数参数异常或范围组件未设置最小值信息，返回默认值-1。

**起始版本：** 18

**参数:**

| 名称      | 描述                   |
| --------- | ---------------------- |
| value | 需要获取最小值的范围组件无障碍信息对象指针。   |

**返回：**

范围组件的无障碍最小值。


### OH_ArkUI_AccessibilityValue_SetRangeMax

```
void OH_ArkUI_AccessibilityValue_SetRangeMax(ArkUI_AccessibilityValue* value, int32_t rangeMax)
```

**描述：**

用于设置范围组件的无障碍最大值信息。

当范围组件未设置无障碍最大值时，默认为-1。

**起始版本：** 18

**参数:**

| 名称      | 描述                   |
| --------- | ---------------------- |
| value | 需要设置最大值的范围组件无障碍信息对象指针。   |
| rangeMin       | 基于范围组件的最大值。              |


### OH_ArkUI_AccessibilityValue_GetRangeMax

```
int32_t OH_ArkUI_AccessibilityValue_GetRangeMax(ArkUI_AccessibilityValue* value)
```

**描述：**

用于获取范围组件的无障碍最大值信息。

若函数参数异常或范围组件未设置最大值信息，返回默认值-1。

**起始版本：** 18

**参数:**

| 名称      | 描述                   |
| --------- | ---------------------- |
| value | 需要获取最大值的范围组件无障碍信息对象指针。   |

**返回：**

范围组件的无障碍最大值。


### OH_ArkUI_AccessibilityValue_SetRangeCurrent

```
void OH_ArkUI_AccessibilityValue_SetRangeCurrent(ArkUI_AccessibilityValue* value, int32_t rangeCurrent)
```

**描述：**

用于设置范围组件的无障碍当前值信息。

当范围组件未设置无障碍当前值时，默认为-1。

**起始版本：** 18

**参数:**

| 名称      | 描述                   |
| --------- | ---------------------- |
| value | 需要设置当前值的范围组件无障碍信息对象指针。   |
| rangeCurrent       | 基于范围组件的当前值。              |


### OH_ArkUI_AccessibilityValue_GetRangeCurrent

```
int32_t OH_ArkUI_AccessibilityValue_GetRangeCurrent(ArkUI_AccessibilityValue* value)
```

**描述：**

用于获取范围组件的无障碍当前值信息。

若函数参数异常或范围组件未设置当前值信息，返回默认值-1。

**起始版本：** 18

**参数：** 

| 名称      | 描述                   |
| --------- | ---------------------- |
| value | 需要获取当前值的范围组件无障碍信息对象指针。   |

**返回：**

范围组件的无障碍当前值。
### OH_ArkUI_EnableDropDisallowedBadge()

```
int32_t OH_ArkUI_EnableDropDisallowedBadge(ArkUI_ContextHandle uiContext, bool enabled)
```
**描述：**

设置是否可以显示禁用角标。 

**起始版本：** 20

| 名称 | 描述 | 
| -------- | -------- |
| uiContext | UI实例对象指针。  | 
| enabled | 是否可以显示禁用角标。true表示可以显示禁用角标，false表示不可以显示禁用角标。| 

**返回：**

[ARKUI_ERROR_CODE_NO_ERROR](_ark_u_i___native_module.md#arkui_errorcode) 成功。 [ARKUI_ERROR_CODE_PARAM_INVALID](_ark_u_i___native_module.md#arkui_errorcode) 函数参数异常。

### OH_ArkUI_EmbeddedComponentOption_Create()

```
ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()
```
**描述：**

创建EmbeddedComponent组件选项的对象。

**起始版本：** 20

**返回：**

返回指向EmbeddedComponent组件选项的对象的指针。

### OH_ArkUI_EmbeddedComponentOption_Dispose()

```
void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)
```
**描述：**

删除EmbeddedComponent组件选项的对象。

**起始版本：** 20

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| option | 要销毁的EmbeddedComponent组件选项的对象的指针。|

### OH_ArkUI_EmbeddedComponentOption_SetOnError()

```
void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, const char* name, const char* message))
```


**描述**

设置EmbeddedComponent组件的onError回调。

EmbeddedComponent组件在运行过程中发生异常时触发本回调。

**起始版本：** 20

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| option | EmbeddedComponent组件选项的对象的指针。| 
| code | 接口调用失败返回的错误码信息。业务错误码详细介绍请参见[UIExtension错误码](./errorcode-uiextension.md)。| 
| name | 接口调用失败返回的名称信息。| 
| message | 接口调用失败返回的详细信息。| 

### OH_ArkUI_EmbeddedComponentOption_SetOnTerminated()

```
void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, AbilityBase_Want* want))
```

**描述**

设置EmbeddedComponent组件的onTerminated回调。

EmbeddedComponent组件正常退出时触发本回调。

**起始版本：** 20

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| option | EmbeddedComponent组件选项的对象的指针。| 
| code | 被拉起EmbeddedUIExtensionAbility退出时返回的结果码。若Ability通过调用terminateSelfWithResult退出，结果码为Ability设置的值。若Ability通过调用terminateSelf退出，结果码为默认值"0"。| 
| want | 被拉起EmbeddedUIExtensionAbility退出时返回的数据。| 
