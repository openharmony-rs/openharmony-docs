# 绑定拖拽事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

ArkUI开发框架针对拖拽事件提供了[NODE_ON_PRE_DRAG](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_START](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DROP](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_ENTER](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_MOVE](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_LEAVE](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，[NODE_ON_DRAG_END](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)等组件事件，当拖拽在不同的阶段时会触发对应的组件事件，完成对应的数据处理操作，实现期望的拖拽交互能力。

## 通用拖拽

ArkUI提供了使用C和C++开发拖拽功能的能力，开发者可调用C API实现拖拽功能。以下以Image组件为例，详细介绍C API实现拖拽功能的基本步骤，以及在开发过程中需要注意的事项。完整示例请参考<!--RP1-->[NativeDragDrop](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeDragDrop)<!--RP1End-->。

1. 组件拖拽设置。

   通过[OH_ArkUI_GetModuleInterface](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_getmoduleinterface)接口初始化nodeAPI，创建节点等操作均需通过nodeAPI完成。

   <!-- @[get_nodeAPI](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/manager.cpp) -->
   
   ``` C++
   ArkUI_NativeNodeAPI_1 *nativeNodeAPI = nullptr;
   OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, nativeNodeAPI);
   nodeAPI = nativeNodeAPI;
   ```

   创建Image节点，通过[OH_ArkUI_SetNodeDraggable](../reference/apis-arkui/capi-drag-and-drop-h.md#oh_arkui_setnodedraggable)设置节点可拖拽，并设置其他相关属性。

   <!-- @[create_imageNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/thirdmodule.h) -->
   
   ``` C
   dragImage2 = nodeAPI->createNode(ARKUI_NODE_IMAGE);
   SetId(dragImage2, "dragImage");
   SetCommonAttribute(dragImage2, 140.0f, 140.0f, 0xFFFFFFFF, 5.0f);
   // 图片src/main/resources/base/media/seagull.png需要替换为开发者所需的资源文件
   SetImageSrc(dragImage2, "/resources/base/media/seagull.png");
   OH_ArkUI_SetNodeDraggable(dragImage2, true);
   nodeAPI->registerNodeEvent(dragImage2, NODE_ON_DRAG_START, 1, nullptr);
   ```
   <!-- @[set_common](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/common.h) -->
   
   ``` C
   #define DEFAULT_WIDTH 200.0
   // 设置节点宽度
   void SetWidth(ArkUI_NodeHandle &node, float width = DEFAULT_WIDTH)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue widthValue[] = {width};
       ArkUI_AttributeItem widthItem = {widthValue, 1};
       nodeAPI->setAttribute(node, NODE_WIDTH, &widthItem);
   }
   
   #define DEFAULT_HEIGHT 200.0
   // 设置节点高度
   void SetHeight(ArkUI_NodeHandle &node, float height = DEFAULT_HEIGHT)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue heightValue[] = {height};
       ArkUI_AttributeItem heightItem = {heightValue, 1};
       nodeAPI->setAttribute(node, NODE_HEIGHT, &heightItem);
   }
   
   #define DEFAULT_BG_COLOR 0xFFFFFFFF
   // 设置节点背景颜色
   void SetBackgroundColor(ArkUI_NodeHandle &node, uint32_t color = DEFAULT_BG_COLOR)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue colorValue[] = {{.u32 = color}};
       ArkUI_AttributeItem colorItem = {colorValue, 1};
       nodeAPI->setAttribute(node, NODE_BACKGROUND_COLOR, &colorItem);
   }
   
   #define DEFAULT_MARGIN 5.0
   // 设置节点外边距
   void SetMargin(ArkUI_NodeHandle &node, float margin = DEFAULT_MARGIN)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue marginValue[] = {margin};
       ArkUI_AttributeItem marginItem = {marginValue, 1};
       nodeAPI->setAttribute(node, NODE_MARGIN, &marginItem);
   }
   
   // 设置Button节点标签
   void SetButtonLabel(ArkUI_NodeHandle &node, const char *label)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_AttributeItem NODE_Button_SRC_Item = {.string = label};
       nodeAPI->setAttribute(node, NODE_BUTTON_LABEL, &NODE_Button_SRC_Item);
   }
   
   // 设置节点标识符
   void SetId(ArkUI_NodeHandle &node, const char *id)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_AttributeItem idItem = {.string = id};
       nodeAPI->setAttribute(node, NODE_ID, &idItem);
   }
   
   #define DEFAULT_BORDER_WIDTH 0.0
   // 设置节点边框宽度
   void SetBorderWidth(ArkUI_NodeHandle &node, float width = DEFAULT_BORDER_WIDTH)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue borderWidthValue[] = {width};
       ArkUI_AttributeItem borderWidthItem = {borderWidthValue, 1};
       nodeAPI->setAttribute(node, NODE_BORDER_WIDTH, &borderWidthItem);
   }
   
   #define DEFAULT_BORDER_COLOR 0xFF000000
   // 设置节点边框颜色
   void SetBorderColor(ArkUI_NodeHandle &node, uint32_t color = DEFAULT_BORDER_COLOR)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue borderColorValue[] = {{.u32 = color}};
       ArkUI_AttributeItem borderColorItem = {borderColorValue, 1};
       nodeAPI->setAttribute(node, NODE_BORDER_COLOR, &borderColorItem);
   }
   
   // 设置节点常用属性（宽高、背景色、外边距、边框样式）
   void SetCommonAttribute(ArkUI_NodeHandle &node, float width = DEFAULT_WIDTH, float height = DEFAULT_HEIGHT,
                           unsigned int color = DEFAULT_BG_COLOR, float margin = DEFAULT_MARGIN)
   {
       SetWidth(node, width);
       SetHeight(node, height);
       SetBackgroundColor(node, color);
       SetMargin(node, margin);
       SetBorderWidth(node, DEFAULT_BORDER_WIDTH);
       SetBorderColor(node);
   }
   ```
   <!-- @[set_imageSrc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/common.h) -->
   
   ``` C
   void SetImageSrc(ArkUI_NodeHandle &node, const char *src)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_AttributeItem imageSrcItem = {.string = src};
       nodeAPI->setAttribute(node, NODE_IMAGE_SRC, &imageSrcItem);
   }
   ```

2. 自定义拖拽预览和背板图。

   创建[pixelMap](../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_createpixelmap)，设置pixelMap的宽高等各项属性。设置Image节点的[ArkUI_DragPreviewOption](../reference/apis-arkui/capi-arkui-nativemodule-arkui-dragpreviewoption.md)，可用于设置跟手图的圆角、角标等。

   <!-- @[create_pixelMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/firstmodule.h) -->
   
   ``` C
   // 创建pixelMap
   uint8_t data[960000];
   size_t dataSize = 960000;
   for (int i = 0; i < dataSize; i++) {
       data[i] = i + 1;
   }
   // 创建参数结构体实例，并设置参数
   OH_Pixelmap_InitializationOptions *createOpts;
   OH_PixelmapInitializationOptions_Create(&createOpts);
   OH_PixelmapInitializationOptions_SetWidth(createOpts, 200U);
   OH_PixelmapInitializationOptions_SetHeight(createOpts, 200U);
   OH_PixelmapInitializationOptions_SetPixelFormat(createOpts, PIXEL_FORMAT_BGRA_8888);
   OH_PixelmapInitializationOptions_SetAlphaType(createOpts, PIXELMAP_ALPHA_TYPE_UNKNOWN);
   // 设置自定义跟手图
   OH_PixelmapNative *pixelmap = nullptr;
   OH_PixelmapNative_CreatePixelmap(data, dataSize, createOpts, &pixelmap);
   OH_PixelmapNative_Opacity(pixelmap, 0.1f);
   OH_ArkUI_SetNodeDragPreview(node, pixelmap);
   // 设置跟手图选项
   auto *previewOptionsText = OH_ArkUI_CreateDragPreviewOption();
   OH_ArkUI_DragPreviewOption_SetScaleMode(previewOptionsText, ARKUI_DRAG_PREVIEW_SCALE_DISABLED);
   OH_ArkUI_DragPreviewOption_SetNumberBadgeEnabled(previewOptionsText, true);
   OH_ArkUI_DragPreviewOption_SetBadgeNumber(previewOptionsText, 10U);
   OH_ArkUI_DragPreviewOption_SetDefaultShadowEnabled(previewOptionsText, true);
   OH_ArkUI_DragPreviewOption_SetDefaultRadiusEnabled(previewOptionsText, true);
   int returnValue = OH_ArkUI_DragPreviewOption_SetDefaultAnimationBeforeLiftingEnabled(previewOptionsText, true);
   OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "Manager",
       "dragTest DragPreviewOption_SetDefaultAnimationBeforeLiftingEnabled returnValue = %{public}d",
       returnValue);
   OH_ArkUI_SetNodeDragPreviewOption(node, previewOptionsText);
   ```

3. 设置相关事件。

   C API的事件通过统一的回调来接收，当收到事件时通过[eventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)进行区分。

   <!-- @[event_Type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/firstmodule.h) -->
   
   ``` C
   nodeAPI->addNodeEventReceiver(dragNode, [](ArkUI_NodeEvent *event) {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "RegisterNodeEventFirstReceiver called");
       auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
       auto preDragStatus = OH_ArkUI_NodeEvent_GetPreDragStatus(event);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "eventType = %{public}d, preDragStatus = %{public}d", eventType, preDragStatus);
       auto *dragEvent = OH_ArkUI_NodeEvent_GetDragEvent(event);
       switch (eventType) {
           case NODE_ON_PRE_DRAG:
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_PRE_DRAG Event Receive");
               break;
           case NODE_ON_CLICK:
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_CLICK Event Receive");
               break;
           case NODE_ON_DROP:
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_DROP Event Receive");
               break;
           case NODE_ON_DRAG_ENTER:
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_DRAG_ENTER Event Receive");
               break;
           case NODE_ON_DRAG_MOVE:
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_DRAG_MOVE Event Receive");
               break;
           case NODE_ON_DRAG_LEAVE:
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_DRAG_LEAVE Event Receive");
               break;
           case NODE_ON_DRAG_START: {
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_DRAG_START Event Receive");
               // ...
               break;
           }
           case NODE_ON_DRAG_END: {
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_DRAG_END Event Receive");
               // ...
               break;
           }
           default:
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "UNKNOWN Event Receive");
               break;
       }
   });
   ```

4. 处理NODE_ON_DRAG_START事件。

   在NODE_ON_DRAG_START事件中，应用可以执行起拖阶段所需的操作，通常涉及处理起拖过程的数据。例如，创建[OH_UdmfRecord](../reference/apis-arkdata/capi-udmf-oh-udmfrecord.md)，将用于拖拽图片所需的数据imageValue以[OH_UdsFileUri](../reference/apis-arkdata/capi-udmf-oh-udsfileuri.md)类型添加到OH_UdmfRecord中，接着将OH_UdmfRecord设置到[OH_UdmfData](../reference/apis-arkdata/capi-udmf-oh-udmfdata.md)中，最后将OH_UdmfData设置到[DragEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-dragevent.md)中。

   <!-- @[drag_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/thirdmodule.h) -->
   
   ``` C
   void SetImageData(ArkUI_DragEvent* dragEvent)
   {
       int returnValue;
       OH_UdmfRecord *record = OH_UdmfRecord_Create();
       OH_UdsFileUri *imageValue = OH_UdsFileUri_Create();
       // 图片src/main/resources/base/media/seagull.png需要替换为开发者所需的资源文件
       returnValue = OH_UdsFileUri_SetFileUri(imageValue, "/resources/base/media/seagull.png");
       returnValue = OH_UdmfRecord_AddFileUri(record, imageValue);
       OH_UdmfData *data = OH_UdmfData_Create();
       returnValue = OH_UdmfData_AddRecord(data, record);
       returnValue = OH_ArkUI_DragEvent_SetData(dragEvent, data);
   }
   // ...
               case NODE_ON_DRAG_START: {
                   OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_DRAG_START EventReceiver");
                   SetImageData(dragEvent);
                   break;
               }
   ```

5. 处理NODE_ON_DROP事件。

   在NODE_ON_DROP事件中，应用可以执行与落入阶段相关的操作，通常需要获取拖拽过程中传递的数据。例如，引用[udmf_meta.h](../reference/apis-arkdata/capi-udmf-meta-h.md)头文件，获取[OH_UdmfData](../reference/apis-arkdata/capi-udmf-oh-udmfdata.md)，判断是否存在所需的数据类型，从[OH_UdmfRecord](../reference/apis-arkdata/capi-udmf-oh-udmfrecord.md)中提取相应的数据，最后销毁指针。

   <!-- @[on_drop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/firstmodule.h) --> 
   
   ``` C
   void GetDragData(ArkUI_DragEvent* dragEvent)
   {
       // 获取UDMF data
       int returnValue;
       // 创建OH_UdmfData对象
       OH_UdmfData *data = OH_UdmfData_Create();
       returnValue = OH_ArkUI_DragEvent_GetUdmfData(dragEvent, data);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "OH_ArkUI_DragEvent_GetUdmfData returnValue = %{public}d", returnValue);
       // 判断OH_UdmfData是否有对应的类型
       bool resultUdmf = OH_UdmfData_HasType(data, UDMF_META_GENERAL_FILE);
       if (resultUdmf) {
           // 获取OH_UdmfData的记录
           unsigned int recordsCount = 0;
           OH_UdmfRecord **records = OH_UdmfData_GetRecords(data, &recordsCount);
           // 获取records中的元素
           int returnStatus;
           for (int i = 0; i < recordsCount; i++) {
               // 从OH_UdmfRecord中获取文件类型数据
               OH_UdsFileUri *imageValue = OH_UdsFileUri_Create();
               returnStatus = OH_UdmfRecord_GetFileUri(records[i], imageValue);
               const char *fileUri = OH_UdsFileUri_GetFileUri(imageValue);
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
                   "dragTest OH_UdsFileUri_GetFileUri "
                   "returnStatus= %{public}d "
                   "fileUri= %{public}s",
                   returnStatus, fileUri);
               // 使用结束后销毁指针
               OH_UdsFileUri_Destroy(imageValue);
           }
           if (recordsCount != 0) {
               OH_ArkUI_DragEvent_SetDragResult(dragEvent, ARKUI_DRAG_RESULT_SUCCESSFUL);
               ArkUI_DropOperation option;
               OH_ArkUI_DragEvent_GetDropOperation(dragEvent, &option);
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
                   "OH_ArkUI_DragEvent_GetDropOperation returnValue = %{public}d", option);
           }
       } else {
           OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
               "OH_UdmfData_HasType not contain UDMF_META_GENERAL_FILE");
       }
       int32_t count;
       OH_ArkUI_DragEvent_GetDataTypeCount(dragEvent, &count);
       if (count <= 0 || count >= 128U) {
           return;
       }
       char **eventTypeArray = new char *[count];
       for (int i = 0; i < count; i++) {
           eventTypeArray[i] = new char[128U];
       }
       OH_ArkUI_DragEvent_GetDataTypes(dragEvent, eventTypeArray, count, 128U);
       for (int i = 0; i < count; i++) {
           OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
               "OH_ArkUI_DragEvent_GetDataTypes returnValue = %{public}s", eventTypeArray[i]);
       }
   }
   // ...
               case NODE_ON_DROP: {
                   OH_ArkUI_DragEvent_SetSuggestedDropOperation(dragEvent, ARKUI_DROP_OPERATION_COPY);
                   OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_DROP EventReceiver");
                   GetDragData(dragEvent);
                   break;
               }
   ```

## 虚拟文件拖拽

从API版本26.1.0开始，支持通过[OH_UDMF_SetFileUriVirtualEntry](../reference/apis-arkdata/capi-uds-h.md#oh_udmf_setfileurivirtualentry)提供虚拟文件拖拽能力。起拖方先声明文件信息，在落入方读取时提供内容，适用于网络文件尚未完整下载、压缩内容尚未解压等场景。

以下以拖拽文件或目录为例，介绍C API实现虚拟文件拖拽的基本步骤。完整示例请参考<!--RP2-->[VirtualFileDrag_C](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkData/Udmf/VirtualFileDrag_C)<!--RP2End-->。

1. 定义虚拟文件回调。

   实现[OH_UDMF_VirtualFileCallbacks](../reference/apis-arkdata/capi-udmf-oh-udmf-virtualfilecallbacks.md)中的回调，业务可替换为自己的数据源实现。

   <!-- @[virtual_drag_c_callbacks](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/VirtualFileDrag_C/entry/src/main/cpp/virtual_file_provider.cpp) -->
   
   ``` C++
   OH_UDMF_VirtualItem* OnStat(void* opaque, const char* id)
   {
       if (opaque == nullptr || id == nullptr) {
           return nullptr;
       }
       auto* context = static_cast<ProviderContext*>(opaque);
       std::lock_guard<std::mutex> lock(context->mutex);
       auto source = context->files.find(id);
       // 返回独立节点，返回后由UDMF接管，不能再次销毁该节点。
       return source == context->files.end() ? nullptr : CreateFileItem(source->second);
   }
   
   int OnRead(void* opaque, const char* id, int64_t offset, uint32_t length,
       uint8_t* data, uint32_t* bytesRead)
   {
       if (opaque == nullptr || id == nullptr || data == nullptr || bytesRead == nullptr ||
           offset < 0 || length == 0 || length > MAX_READ) {
           return UDMF_ERR;
       }
       *bytesRead = 0; // 返回值表示成功或失败，实际读取长度通过bytesRead输出。
       auto* context = static_cast<ProviderContext*>(opaque);
       std::lock_guard<std::mutex> lock(context->mutex);
       auto source = context->files.find(id);
       if (source == context->files.end()) {
           return UDMF_ERR;
       }
       SourceFile& file = source->second;
       if (offset >= file.size) {
           return UDMF_E_OK; // 成功且bytesRead为 0，表示已到文件末尾。
       }
       if (!PrepareFileContent(file)) {
           return UDMF_ERR;
       }
       const auto count = static_cast<uint32_t>(std::min<int64_t>(length, file.size - offset));
       if (static_cast<uint64_t>(offset) + count > file.content.size()) {
           return UDMF_ERR;
       }
       // data由UDMF提供，本回调只填充数据，不释放、不保存该地址。
       std::copy_n(file.content.data() + offset, count, data);
       *bytesRead = count;
       return UDMF_E_OK;
   }
   
   int OnCancel(void* opaque, const char* const* idList, uint32_t count)
   {
       // 此示例无异步读取任务；真实提供方可在此停止对应id的待处理任务。
       if (opaque == nullptr || (count > 0 && idList == nullptr)) {
           return UDMF_ERR;
       }
       return UDMF_E_OK;
   }
   
   void Finalize(void* opaque)
   {
       // UDMF最后一个相关引用释放后才调用此函数。
       delete static_cast<ProviderContext*>(opaque);
   }
   ```


2. 创建拖拽数据。

   通过[OH_UDMF_CreateVirtualFileInfo](../reference/apis-arkdata/capi-uds-h.md#oh_udmf_createvirtualfileinfo)关联节点和回调，再通过[OH_UDMF_SetFileUriVirtualEntry](../reference/apis-arkdata/capi-uds-h.md#oh_udmf_setfileurivirtualentry)构造拖拽数据。目录节点的构造参见[OH_UDMF_CreateVirtualDirectoryItem](../reference/apis-arkdata/capi-uds-h.md#oh_udmf_createvirtualdirectoryitem)和[OH_UDMF_AddVirtualItemChild](../reference/apis-arkdata/capi-uds-h.md#oh_udmf_addvirtualitemchild)。

   <!-- @[virtual_drag_c_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/VirtualFileDrag_C/entry/src/main/cpp/virtual_file_provider.cpp) -->
   
   ``` C++
   OH_UdmfData* CreateVirtualDragData(bool directory, bool compressed)
   {
       auto context = std::make_unique<ProviderContext>();
       for (int index = 0; index < (directory ? DIRECTORY_FILE_COUNT : 1); ++index) {
           if (!AddFile(*context, index, compressed)) {
               return nullptr;
           }
       }
       // 1. 声明根文件或目录；每个文件都必须设置准确大小。
       auto* root = CreateRoot(*context, directory);
       // 2. 将文件信息、回调和业务上下文组合为VirtualFileInfo。
       OH_UDMF_VirtualFileCallbacks callbacks {};
       callbacks.structSize = sizeof(callbacks);
       callbacks.onStat = OnStat;
       callbacks.onRead = OnRead;
       callbacks.onCancel = OnCancel;
       auto* info = OH_UDMF_CreateVirtualFileInfo(root, &callbacks, context.get(), Finalize);
       OH_UDMF_DestroyVirtualItem(root);
       if (info == nullptr) {
           return nullptr; // context仍由调用方管理。
       }
       context.release(); // 创建成功，交由UDMF在最后一个引用释放后调用Finalize。
       // 3. 附加到FileUri，再放入Record和UnifiedData，供起拖事件使用。
       auto* uri = OH_UdsFileUri_Create();
       auto* record = OH_UdmfRecord_Create();
       auto* data = OH_UdmfData_Create();
       bool ok = uri != nullptr && record != nullptr && data != nullptr;
       if (ok) {
           ok = OH_UdsFileUri_SetFileUri(uri, directory ? "file:///virtual/exported-documents" :
               "file:///virtual/document-1.txt") == UDMF_E_OK &&
               OH_UdsFileUri_SetFileType(uri, directory ? "general.directory" : "general.file") == UDMF_E_OK &&
               OH_UDMF_SetFileUriVirtualEntry(uri, info) == UDMF_E_OK &&
               OH_UdmfRecord_AddFileUri(record, uri) == UDMF_E_OK &&
               OH_UdmfData_AddRecord(data, record) == UDMF_E_OK;
       }
       // 4. Record已持有独立引用，可释放临时包装对象。
       // Clear只解除此临时FileUri的附加关系，不清除Record中已有的引用。
       if (uri != nullptr) {
           OH_UDMF_ClearFileUriVirtualEntry(uri);
       }
       OH_UDMF_DestroyVirtualFileInfo(info);
       OH_UdsFileUri_Destroy(uri);
       OH_UdmfRecord_Destroy(record);
       if (!ok) {
           OH_UdmfData_Destroy(data);
           return nullptr;
       }
       return data;
   }
   ```


3. 设置起拖数据。

   注册[NODE_ON_DRAG_START和NODE_ON_DRAG_END](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件，通过[OH_ArkUI_DragEvent_SetData](../reference/apis-arkui/capi-drag-and-drop-h.md#oh_arkui_dragevent_setdata)设置起拖数据。完整节点初始化见示例中的`napi_init.cpp`。

   <!-- @[virtual_drag_c_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/VirtualFileDrag_C/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   void OnNodeEvent(ArkUI_NodeEvent* event)
   {
       if (event == nullptr) {
           return;
       }
       const auto type = OH_ArkUI_NodeEvent_GetEventType(event);
       if (type == NODE_ON_DROP) {
           OnDrop(OH_ArkUI_NodeEvent_GetDragEvent(event));
           return;
       }
       if (type == NODE_ON_DRAG_END) {
           OH_UdmfData_Destroy(g_dragData);
           g_dragData = nullptr;
           return;
       }
       if (type != NODE_ON_DRAG_START || g_dragData != nullptr) {
           return;
       }
       auto* drag = OH_ArkUI_NodeEvent_GetDragEvent(event);
       auto* data = CreateVirtualDragData(g_directory, g_compressed);
       if (drag == nullptr || data == nullptr) {
           OH_UdmfData_Destroy(data);
           return;
       }
       const int result = OH_ArkUI_DragEvent_SetData(drag, data);
       // ArkUI暂存此指针，必须保留到拖拽结束；随后会话中的回调引用由UDMF管理。
       if (result == 0) {
           g_dragData = data;
       } else {
           OH_UdmfData_Destroy(data);
       }
   }
   ```


4. 配置落入节点。

   通过[OH_ArkUI_SetNodeAllowedDropDataTypes](../reference/apis-arkui/capi-drag-and-drop-h.md#oh_arkui_setnodealloweddropdatatypes)配置接收节点，并注册[NODE_ON_DROP](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件。

   <!-- @[virtual_drag_c_drop_target](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/VirtualFileDrag_C/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   bool ConfigureDropTarget(std::string& error)
   {
       ArkUI_AttributeItem text {};
       // 本地化文字由ArkTS资源传入，原生节点不硬编码界面文字。
       text.string = g_dropText.c_str();
       if (!CheckNodeResult(g_nodeApi->setAttribute(g_drop, NODE_TEXT_CONTENT, &text), "Set drop text", error)) {
           return false;
       }
       SetAreaLayout(g_drop, 0xFFDCF2DF);
       const char* types[] = {"general.file-uri"};
       return CheckNodeResult(OH_ArkUI_SetNodeAllowedDropDataTypes(g_drop, types, 1), "Set drop types", error) &&
           CheckNodeResult(g_nodeApi->registerNodeEvent(g_drop, NODE_ON_DROP, 1, nullptr), "Register drop", error) &&
           CheckNodeResult(g_nodeApi->addNodeEventReceiver(g_drop, OnNodeEvent), "Add drop receiver", error);
   }
   ```


5. 获取文件URI。

   在落入事件中，通过[OH_ArkUI_DragEvent_GetUdmfData](../reference/apis-arkui/capi-drag-and-drop-h.md#oh_arkui_dragevent_getudmfdata)取得数据，再使用[OH_UdmfRecord_GetFileUri](../reference/apis-arkdata/capi-udmf-h.md#oh_udmfrecord_getfileuri)和[OH_UdsFileUri_GetFileUri](../reference/apis-arkdata/capi-uds-h.md#oh_udsfileuri_getfileuri)提取文件URI。

   <!-- @[virtual_drag_c_receive_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/VirtualFileDrag_C/entry/src/main/cpp/virtual_file_receiver.cpp) -->


6. 处理文件URI。

   在`NODE_ON_DROP`分支将URI列表交给业务处理，并通过[OH_ArkUI_DragEvent_SetDragResult](../reference/apis-arkui/capi-drag-and-drop-h.md#oh_arkui_dragevent_setdragresult)设置拖拽结果。示例的`NotifyUris()`将URI列表传递给ArkTS侧的`handleUris()`。

   <!-- @[virtual_drag_c_drop_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/VirtualFileDrag_C/entry/src/main/cpp/napi_init.cpp) -->


回调参数、返回值及资源释放要求参见[OH_UDMF_VirtualFileOnRead](../reference/apis-arkdata/capi-uds-h.md#oh_udmf_virtualfileonread)、[OH_UDMF_VirtualFileOnCancel](../reference/apis-arkdata/capi-uds-h.md#oh_udmf_virtualfileoncancel)和[OH_UDMF_VirtualFileFinalize](../reference/apis-arkdata/capi-uds-h.md#oh_udmf_virtualfilefinalize)。

## DragAction主动发起拖拽

除了通用拖拽以外，ArkUI还提供了使用C API实现主动发起拖拽的能力。以下以文本拖拽为例，详细介绍C-API实现主动发起拖拽的基本步骤，以及在开发过程中需要注意的事项。完整示例请参考<!--RP1-->[NativeDragDrop](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeDragDrop)<!--RP1End-->。

1. 节点注册事件。

   创建Button节点，设置按钮相关属性，同时需要注册[NODE_ON_TOUCH_INTERCEPT](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件。

   <!-- @[touch_intercept](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/forthmodule.h) -->
   
   ``` C
   // buttonTouch作为targetId，用于区分不同target的事件。
   enum {
       BUTTON_TOUCH = 1
   };
   
   dragButton = nodeAPI->createNode(ARKUI_NODE_BUTTON);
   SetId(dragButton, "dragBt3");
   SetCommonAttribute(dragButton, 80.0f, 50.0f, 0xFFFF0000, 20.0f);
   SetButtonLabel(dragButton, "拖起");
   nodeAPI->registerNodeEvent(dragButton, NODE_ON_TOUCH_INTERCEPT, BUTTON_TOUCH, nullptr);
   ```
   <!-- @[set_common](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/common.h) -->
   
   ``` C
   #define DEFAULT_WIDTH 200.0
   // 设置节点宽度
   void SetWidth(ArkUI_NodeHandle &node, float width = DEFAULT_WIDTH)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue widthValue[] = {width};
       ArkUI_AttributeItem widthItem = {widthValue, 1};
       nodeAPI->setAttribute(node, NODE_WIDTH, &widthItem);
   }
   
   #define DEFAULT_HEIGHT 200.0
   // 设置节点高度
   void SetHeight(ArkUI_NodeHandle &node, float height = DEFAULT_HEIGHT)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue heightValue[] = {height};
       ArkUI_AttributeItem heightItem = {heightValue, 1};
       nodeAPI->setAttribute(node, NODE_HEIGHT, &heightItem);
   }
   
   #define DEFAULT_BG_COLOR 0xFFFFFFFF
   // 设置节点背景颜色
   void SetBackgroundColor(ArkUI_NodeHandle &node, uint32_t color = DEFAULT_BG_COLOR)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue colorValue[] = {{.u32 = color}};
       ArkUI_AttributeItem colorItem = {colorValue, 1};
       nodeAPI->setAttribute(node, NODE_BACKGROUND_COLOR, &colorItem);
   }
   
   #define DEFAULT_MARGIN 5.0
   // 设置节点外边距
   void SetMargin(ArkUI_NodeHandle &node, float margin = DEFAULT_MARGIN)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue marginValue[] = {margin};
       ArkUI_AttributeItem marginItem = {marginValue, 1};
       nodeAPI->setAttribute(node, NODE_MARGIN, &marginItem);
   }
   
   // 设置Button节点标签
   void SetButtonLabel(ArkUI_NodeHandle &node, const char *label)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_AttributeItem NODE_Button_SRC_Item = {.string = label};
       nodeAPI->setAttribute(node, NODE_BUTTON_LABEL, &NODE_Button_SRC_Item);
   }
   
   // 设置节点标识符
   void SetId(ArkUI_NodeHandle &node, const char *id)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_AttributeItem idItem = {.string = id};
       nodeAPI->setAttribute(node, NODE_ID, &idItem);
   }
   
   #define DEFAULT_BORDER_WIDTH 0.0
   // 设置节点边框宽度
   void SetBorderWidth(ArkUI_NodeHandle &node, float width = DEFAULT_BORDER_WIDTH)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue borderWidthValue[] = {width};
       ArkUI_AttributeItem borderWidthItem = {borderWidthValue, 1};
       nodeAPI->setAttribute(node, NODE_BORDER_WIDTH, &borderWidthItem);
   }
   
   #define DEFAULT_BORDER_COLOR 0xFF000000
   // 设置节点边框颜色
   void SetBorderColor(ArkUI_NodeHandle &node, uint32_t color = DEFAULT_BORDER_COLOR)
   {
       if (!nodeAPI) {
           return;
       }
       ArkUI_NumberValue borderColorValue[] = {{.u32 = color}};
       ArkUI_AttributeItem borderColorItem = {borderColorValue, 1};
       nodeAPI->setAttribute(node, NODE_BORDER_COLOR, &borderColorItem);
   }
   
   // 设置节点常用属性（宽高、背景色、外边距、边框样式）
   void SetCommonAttribute(ArkUI_NodeHandle &node, float width = DEFAULT_WIDTH, float height = DEFAULT_HEIGHT,
                           unsigned int color = DEFAULT_BG_COLOR, float margin = DEFAULT_MARGIN)
   {
       SetWidth(node, width);
       SetHeight(node, height);
       SetBackgroundColor(node, color);
       SetMargin(node, margin);
       SetBorderWidth(node, DEFAULT_BORDER_WIDTH);
       SetBorderColor(node);
   }
   ```

2. 接收NODE_ON_TOUCH_INTERCEPT事件。

   DragAction主动发起拖拽需通过事件触发，在NODE_ON_TOUCH_INTERCEPT事件中执行发起拖拽所需的操作，通过[targetId](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeevent_gettargetid)区分不同按钮触发的事件。

   <!-- @[on_touchIntercept](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/forthmodule.h) -->
   
   ``` C
   nodeAPI->addNodeEventReceiver(dragButton, [](ArkUI_NodeEvent *event) {
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "RegisterNodeEventForthReceiver called");
       auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
       auto preDragStatus = OH_ArkUI_NodeEvent_GetPreDragStatus(event);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "eventType = %{public}d, preDragStatus = %{public}d", eventType, preDragStatus);
   
       auto *dragEvent = OH_ArkUI_NodeEvent_GetDragEvent(event);
       switch (eventType) {
           case NODE_ON_TOUCH_INTERCEPT: {
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_TOUCH_INTERCEPT EventReceiver");
               // ...
               break;
           }
           default: {
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "UNKNOWN EventReceiver");
               break;
           }
       }
   });
   ```
3. 起拖阶段设置。

   在NODE_ON_TOUCH_INTERCEPT事件中，需要对DragAction进行相关设置。为了主动发起拖拽，需要创建[pixelMap](../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_createpixelmap)，设置[ArkUI_DragPreviewOption](../reference/apis-arkui/capi-arkui-nativemodule-arkui-dragpreviewoption.md)和跟手点，并将拖拽过程中的文本数据设置到DragAction中。

   <!-- @[set_dragAction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/forthmodule.h) -->
   
   ``` C
               case NODE_ON_TOUCH_INTERCEPT: {
                   OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_TOUCH_INTERCEPT EventReceiver");
                   // 创建DragAction
                   action = OH_ArkUI_CreateDragActionWithNode(dragButton);
                   OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
                       "OH_ArkUI_CreateDragActionWithNode returnValue = %{public}p", action);
                   // 设置pixelMap
                   std::vector<OH_PixelmapNative *> pixelVector;
                   SetPixelMap(pixelVector);
                   // 设置DragPreviewOption
                   SetDragPreviewOption();
                   // 设置pointerId、touchPoint
                   PrintDragActionInfos();
                   // 设置unifiedData
                   SetDragActionData();
                   // startDrag
                   int returnValue = OH_ArkUI_StartDrag(action);
                   OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
                       "OH_ArkUI_StartDrag returnValue = %{public}d",
                       returnValue);
                   if (returnValue != ARKUI_ERROR_CODE_NO_ERROR && action) {
                       OH_ArkUI_DragAction_UnregisterStatusListener(action);
                       OH_ArkUI_DragAction_Dispose(action);
                       ReleaseDragUdmfData();
                       ReleaseDragPixelMaps();
                       action = nullptr;
                   }
                   break;
               }
               // ...
   void SetDragActionData()
   {
       // 创建OH_UdmfRecord对象
       OH_UdmfRecord *record = OH_UdmfRecord_Create();
       // 向OH_UdmfRecord中添加纯文本类型数据
       OH_UdsPlainText *plainText = OH_UdsPlainText_Create();
       int returnStatus;
       OH_UdsPlainText_SetAbstract(plainText, "this is plainText Abstract example");
       OH_UdsPlainText_SetContent(plainText, "this is plainText Content example");
       returnStatus = OH_UdmfRecord_AddPlainText(record, plainText);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "dragTest OH_UdmfRecord_AddPlainText returnStatus = %{public}d", returnStatus);
       // 创建OH_UdmfData对象
       ReleaseDragUdmfData();
       OH_UdmfData *data = OH_UdmfData_Create();
       dragUdmfData = data;
       // 向OH_UdmfData中添加OH_UdmfRecord
       returnStatus = OH_UdmfData_AddRecord(data, record);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "dragTest OH_UdmfData_AddRecord returnStatus = %{public}d", returnStatus);
       int returnValue = OH_ArkUI_DragAction_SetData(action, data);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "OH_ArkUI_DragAction_SetData returnValue = %{public}d", returnValue);
       // 注册拖拽状态监听回调
       OH_ArkUI_DragAction_RegisterStatusListener(action, data, &DragStatusListener);
   }
   ```
   <!-- @[prepare_dragAction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/common.h) -->
   
   ``` C
   void SetPixelMap(std::vector<OH_PixelmapNative *> &pixelVector)
   {
       uint8_t data[960000];
       size_t dataSize = 960000;
       for (int i = 0; i < dataSize; i++) {
           data[i] = i + 1;
       }
       // 创建参数结构体实例，并设置参数
       OH_Pixelmap_InitializationOptions *createOpts = nullptr;
       OH_PixelmapInitializationOptions_Create(&createOpts);
       if (!createOpts) {
           return;
       }
       OH_PixelmapInitializationOptions_SetWidth(createOpts, 200U);
       OH_PixelmapInitializationOptions_SetHeight(createOpts, 300U);
       OH_PixelmapInitializationOptions_SetPixelFormat(createOpts, PIXEL_FORMAT_BGRA_8888);
       OH_PixelmapInitializationOptions_SetAlphaType(createOpts, PIXELMAP_ALPHA_TYPE_UNKNOWN);
       // 创建Pixelmap实例
       OH_PixelmapNative *pixelmap = nullptr;
       OH_PixelmapNative_CreatePixelmap(data, dataSize, createOpts, &pixelmap);
       OH_PixelmapInitializationOptions_Release(createOpts);
       if (!pixelmap) {
           return;
       }
       OH_PixelmapNative_Flip(pixelmap, true, true);
       pixelVector.push_back(pixelmap);
       int returnValue = OH_ArkUI_DragAction_SetPixelMaps(action, pixelVector.data(), pixelVector.size());
       if (returnValue == ARKUI_ERROR_CODE_NO_ERROR) {
           dragPixelMaps.push_back(pixelmap);
       } else {
           OH_PixelmapNative_Release(pixelmap);
       }
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "OH_ArkUI_DragAction_SetPixelMaps returnValue = %{public}d", returnValue);
   }
   
   void SetDragPreviewOption()
   {
       auto *previewOptions = OH_ArkUI_CreateDragPreviewOption();
       OH_ArkUI_DragPreviewOption_SetScaleMode(previewOptions,
           ArkUI_DragPreviewScaleMode::ARKUI_DRAG_PREVIEW_SCALE_DISABLED);
       OH_ArkUI_DragPreviewOption_SetDefaultShadowEnabled(previewOptions, true);
       OH_ArkUI_DragPreviewOption_SetDefaultRadiusEnabled(previewOptions, true);
       int returnValue = OH_ArkUI_DragAction_SetDragPreviewOption(action, previewOptions);
       OH_ArkUI_DragPreviewOption_Dispose(previewOptions);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "OH_ArkUI_DragAction_SetDragPreviewOption returnValue = %{public}d", returnValue);
   }
   
   void PrintDragActionInfos()
   {
       // 设置pointerId
       int returnValue = OH_ArkUI_DragAction_SetPointerId(action, 0);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "OH_ArkUI_DragAction_SetPointerId returnValue = %{public}d", returnValue);
       // 设置touchPoint
       returnValue = OH_ArkUI_DragAction_SetTouchPointX(action, 200.0f);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "OH_ArkUI_DragAction_SetTouchPointX returnValue = %{public}d", returnValue);
       returnValue = OH_ArkUI_DragAction_SetTouchPointY(action, 200.0f);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "OH_ArkUI_DragAction_SetTouchPointY returnValue = %{public}d", returnValue);
   }
   ```
4. 处理NODE_ON_DROP事件。

   在NODE_ON_DROP事件中，应用可以执行与落入阶段相关的操作。通常情况下，需要从DragEvent中获取拖拽过程中传递的数据，DragAction中的拖拽数据也需要通过DragEvent获取。

   <!-- @[get_dragAction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDragDrop/entry/src/main/cpp/forthmodule.h) -->
   
   ``` C
               case NODE_ON_DROP: {
                   OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest", "NODE_ON_DROP EventReceiver");
                   GetUdmfDataText(dragEvent);
                   break;
               }
               // ...
   void GetUdmfDataText(ArkUI_DragEvent* dragEvent)
   {
       // 获取UDMF data
       int returnValue;
       // 创建OH_UdmfData对象
       OH_UdmfData *data = OH_UdmfData_Create();
       returnValue = OH_ArkUI_DragEvent_GetUdmfData(dragEvent, data);
       OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
           "OH_ArkUI_DragEvent_GetUdmfData returnValue = %{public}d", returnValue);
       // 判断OH_UdmfData是否有对应的类型
       bool resultUdmf = OH_UdmfData_HasType(data, UDMF_META_PLAIN_TEXT);
       if (resultUdmf) {
           // 获取OH_UdmfData的记录
           unsigned int recordsCount = 0;
           OH_UdmfRecord **records = OH_UdmfData_GetRecords(data, &recordsCount);
           // 获取records中的元素
           int returnStatus;
           for (int i = 0; i < recordsCount; i++) {
               // 从OH_UdmfRecord中获取纯文本类型数据
               OH_UdsPlainText *plainTextValue = OH_UdsPlainText_Create();
               returnStatus = OH_UdmfRecord_GetPlainText(records[i], plainTextValue);
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
                   "dragTest OH_UdmfRecord_GetPlainText "
                   "returnStatus= %{public}d",
                   returnStatus);
               auto getAbstract = OH_UdsPlainText_GetAbstract(plainTextValue);
               auto getContent = OH_UdsPlainText_GetContent(plainTextValue);
               OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
                   "OH_UdsPlainText_GetAbstract = "
                   "%{public}s, OH_UdsPlainText_GetContent = "
                   "%{public}s",
                   getAbstract, getContent);
               // 使用结束后销毁指针
               OH_UdsPlainText_Destroy(plainTextValue);
           }
       } else {
           OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00U, "dragTest",
               "OH_UdmfData_HasType not contain UDMF_META_PLAIN_TEXT");
       }
       OH_UdmfData_Destroy(data);
   }
   ```