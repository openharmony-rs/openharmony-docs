# 拖拽事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

ArkUI开发框架针对拖拽事件提供了[NODE_ON_PRE_DRAG](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_START](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DROP](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_ENTER](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_MOVE](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_LEAVE](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_END](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)等组件事件，当拖拽在不同的阶段时会触发对应的组件事件，完成对应的数据处理操作，实现期望的拖拽交互能力。

## 通用拖拽

ArkUI提供了使用C和C++开发拖拽功能的能力，开发者可调用C API实现拖拽功能。以下以Image组件为例，详细介绍实现C API实现拖拽功能的基本步骤，以及在开发过程中需要注意的事项。

1. 组件拖拽设置。

   获取[Node-API](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_getmoduleinterface)，创建节点等操作均需通过Node-API完成。

   <!-- @[get_nodeAPI](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/manager.cpp) -->
   
   ``` C++
   ArkUI_NativeNodeAPI_1 *nativeNodeAPI = nullptr;
   OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, nativeNodeAPI);
   nodeAPI = nativeNodeAPI;
   ```

   创建Image节点，并设置draggable和其它相关属性。

   <!-- @[create_imageNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/thirdmodule.h) -->
   
   ``` C
   dragImage2 = nodeAPI->createNode(ARKUI_NODE_IMAGE);
   SetId(dragImage2, "dragImage");
   SetCommonAttribute(dragImage2, SIZE_140, SIZE_140, DEFAULT_BG_COLOR, BLANK_5);
   SetImageSrc(dragImage2, "/resources/seagull.png");
   OH_ArkUI_SetNodeDraggable(dragImage2, true);
   nodeAPI->registerNodeEvent(dragImage2, NODE_ON_DRAG_START, 1, nullptr);
   ```
   <!-- @[set_common](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/common.h) -->
   <!-- @[set_imageSrc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/common.h) -->

2. 自定义拖拽预览和背板图。

   创建[pixelMap](../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_createpixelmap)，设置pixelMap的宽高等各项属性。设置Image节点的[dragPreviewOption](../reference/apis-arkui/capi-drag-and-drop-h.md#函数)，可用于设置跟手图的圆角、角标等。

   <!-- @[create_pixelMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/firstmodule.h) -->

3. 设置相关事件。

   C API的事件通过统一的回调来接收，当收到事件时通过[eventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)进行区分。

   <!-- @[event_Type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/firstmodule.h) -->

4. 处理NODE_ON_DRAG_START事件。

   在NODE_ON_DRAG_START事件中，应用可以执行起拖阶段所需的操作，通常涉及处理起拖过程的数据。例如，创建UdmfRecord，将用于拖拽图片所需的数据 imageUri以fileUri类型添加到[UdmfRecord](../reference/apis-arkdata/capi-udmf-oh-udmfrecord.md)中，接着将UdmfRecord设置到[udmfData](../reference/apis-arkdata/capi-udmf-oh-udmfdata.md)中，最后将UdmfData设置到[DragEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-dragevent.md)中。

   <!-- @[drag_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/thirdmodule.h) -->

5. 处理NODE_ON_DROP事件。

   在NODE_ON_DROP事件中，应用可以执行与落入阶段相关的操作，通常需要获取拖拽过程中传递的数据。例如，引用<database/udmf/udmf_meta.h>头文件，获取[udmfData](../reference/apis-arkdata/capi-udmf-oh-udmfdata.md)，判断是否存在所需的数据类型，从[UdmfRecord](../reference/apis-arkdata/capi-udmf-oh-udmfrecord.md)中提取相应的数据，最后销毁指针。

   <!-- @[on_drop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/firstmodule.h) -->

## DragAction主动发起拖拽

除了通用拖拽以外，ArkUI还提供了使用C API实现主动发起拖拽的能力。以下以文本拖拽为例，详细介绍实现C-API实现主动发起拖拽的基本步骤，以及在开发过程中需要注意的事项。

1. 节点注册事件。

   创建Button节点，设置按钮相关属性，同时需要注册[NODE_ON_TOUCH_INTERCEPT](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件。

   <!-- @[touch_intercept](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/forthmodule.h) -->
   <!-- @[set_common](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/common.h) -->

2. 接收NODE_ON_TOUCH_INTERCEPT事件。

   DragAction主动发起拖拽需通过事件触发，在NODE_ON_TOUCH_INTERCEPT事件中执行发起拖拽所需的操作，通过[targetId](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeevent_gettargetid)区分不同按钮触发的事件。

   <!-- @[on_touchIntercept](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/forthmodule.h) -->
3. 起拖阶段设置。

   在NODE_ON_TOUCH_INTERCEPT事件中，需要对DragAction进行相关设置。为了主动发起拖拽，需要创建[pixelMap](../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_createpixelmap)，设置[dragPreviewOption](../reference/apis-arkui/capi-drag-and-drop-h.md#函数)和跟手点，并将拖拽过程中的文本数据设置到DragAction中。

   <!-- @[set_dragAction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/forthmodule.h) -->
   <!-- @[prepare_dragAction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/common.h) -->
4. 处理NODE_ON_DROP事件。

   在NODE_ON_DROP事件中，应用可以执行与落入阶段相关的操作。通常情况下，需要从DragEvent中获取拖拽过程中传递的数据，DragAction中的拖拽数据也需要通过DragEvent获取。

   <!-- @[get_dragAction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/forthmodule.h) -->