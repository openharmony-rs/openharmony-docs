# native_node.h

## 概述

Provides type definitions for <b>NativeNode</b> APIs.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | ArkUI_NodeComponentEvent | Defines the parameter type of the component callback event. |
| [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) | ArkUI_StringAsyncEvent | Defines the string type parameter used by the component callback event. |
| [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) | ArkUI_TextChangeEvent | Defines a hybrid data structure for component events. |
| [ArkUI_NativeNodeAPI_1](capi-arkui-nativemodule-arkui-nativenodeapi-1.md) | ArkUI_NativeNodeAPI_1 | ArkUI提供的Native侧Node类型接口集合。Node模块相关接口需要在主线程上调用。 |
| [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | OH_ArkUI_TextEditorChangeEvent | 定义TextEditor组件文本内容变化事件的结构体，用于在文本内容变化时通知用户，支持获取变化前后的内容等信息，适用于需要在文本内容变化前进行拦截或校验的场景，例如输入拦截、内容过滤、变更确认等。 |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md) | ArkUI_NodeCustomEvent | Defines the general structure of a custom component event. |
| [ArkUI_NodeAdapter*](capi-arkui-nativemodule-arkui-nodeadapter8h.md) | ArkUI_NodeAdapterHandle | Defines the component adapter, which is used for lazy loading of elements of scrollable components. |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md) | ArkUI_NodeAdapterEvent | Defines the component adapter event. |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md) | ArkUI_NodeContentEvent | Defines the general structure of a node content event. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NodeType](#arkui_nodetype) | ArkUI_NodeType | Enumerates ArkUI component types that can be created on the native side. |
| [ArkUI_NodeAttributeType](#arkui_nodeattributetype) | ArkUI_NodeAttributeType | 定义ArkUI在Native侧可以设置的属性样式集合。 |
| [ArkUI_NodeEventType](#arkui_nodeeventtype) | ArkUI_NodeEventType | Enumerates the event types supported by the NativeNode component. |
| [ArkUI_NodeDirtyFlag](#arkui_nodedirtyflag) | ArkUI_NodeDirtyFlag | Defines the dirty area flag passed in the <b>::markDirty</b> API. |
| [ArkUI_NodeCustomEventType](#arkui_nodecustomeventtype) | ArkUI_NodeCustomEventType | Defines the custom component event type. |
| [ArkUI_NodeAdapterEventType](#arkui_nodeadaptereventtype) | ArkUI_NodeAdapterEventType | Enumerates component adapter events. |
| [ArkUI_NodeContentEventType](#arkui_nodecontenteventtype) | ArkUI_NodeContentEventType | Defines the node content event type. |
| [ArkUI_InspectorErrorCode](#arkui_inspectorerrorcode) | ArkUI_InspectorErrorCode | Enumerates the inspector error codes. |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| MAX_NODE_SCOPE_NUM 1000 | Define components max function size.<br>**起始版本：** 12 |
| MAX_COMPONENT_EVENT_ARG_NUM 12 | Define component event max args size.<br>**起始版本：** 12 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_geteventtype) | - | Obtains the type of a component event. |
| [int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettargetid) | - | Obtains the custom ID of a component event.The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be appliedto the dispatch logic of the same event entry function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver). |
| [ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodehandle) | - | Obtains the component object that triggers a component event. |
| [ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getinputevent) | - | 获取组件事件中的输入事件（如触碰事件）数据。 |
| [ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodecomponentevent) | - | Obtains the numerical data in a component event. |
| [ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getstringasyncevent) | - | Obtains the string data in a component event. |
| [ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettextchangeevent) | - | Obtains the ArkUI_TextChangeEvent data from a component event. |
| [void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getuserdata) | - | Obtains the custom data in a component event.This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the eventis triggered. |
| [int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)](#oh_arkui_nodeevent_getnumbervalue) | - | 获取组件回调事件的数字类型参数。 |
| [int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)](#oh_arkui_nodeevent_getstringvalue) | - | 获取组件回调事件的字符串类型参数，字符串数据仅在事件回调过程中有效，需要在事件回调外使用建议进行额外拷贝处理。 |
| [int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)](#oh_arkui_nodeevent_setreturnnumbervalue) | - | 设置组件回调事件的返回值。 |
| [ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_gettouchtestinfo) | - | 获取组件事件中的触摸测试信息。 |
| [OH_ArkUI_TextEditorChangeEvent* OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettexteditoronwillchangeevent) | - | 获取组件事件中的TextEditor组件文本内容变化数据。 |
| [ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()](#oh_arkui_nodeadapter_create) | - | Creates a component adapter. |
| [void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_dispose) | - | Destroys a component adapter. |
| [int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)](#oh_arkui_nodeadapter_settotalnodecount) | - | 设置Adapter中的元素总数。 |
| [uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_gettotalnodecount) | - | Obtains the total number of elements in the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver( ArkUI_NodeAdapterHandle handle, void* userData, void (\*receiver)(ArkUI_NodeAdapterEvent* event))](#oh_arkui_nodeadapter_registereventreceiver) | - | 注册Adapter相关回调事件。在相关回调事件不需要之后，需要执行[OH_ArkUI_NodeAdapter_UnregisterEventReceiver](capi-native-node-h.md#oh_arkui_nodeadapter_unregistereventreceiver)接口注销相关回调事件。 |
| [void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_unregistereventreceiver) | - | Deregisters an event callback for the adapter. |
| [int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_reloadallitems) | - | 通知Adapter进行全量元素变化。 |
| [int32_t OH_ArkUI_NodeAdapter_ReloadItem( ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_reloaditem) | - | 通知Adapter进行局部元素变化。 |
| [int32_t OH_ArkUI_NodeAdapter_RemoveItem( ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_removeitem) | - | 通知Adapter进行局部元素删除。 |
| [int32_t OH_ArkUI_NodeAdapter_InsertItem( ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_insertitem) | - | 通知Adapter进行局部元素插入。 |
| [int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)](#oh_arkui_nodeadapter_moveitem) | - | 通知Adapter进行局部元素移位。 |
| [int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)](#oh_arkui_nodeadapter_getallitems) | - | 获取存储在Adapter中的所有元素。接口调用会返回元素的数组对象指针，该指针指向的内存数据需要开发者手动释放。 |
| [void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getuserdata) | - | Obtains the custom data passed in during registration of the specified event. |
| [ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gettype) | - | Obtains the event type. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getremovednode) | - | Obtains the element to be removed for the event to be destroyed. |
| [uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getitemindex) | - | Obtains the index of the element to be operated for the specified adapter event. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gethostnode) | - | Obtains the scrollable container node that uses the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)](#oh_arkui_nodeadapterevent_setitem) | - | 设置需要新增到Adapter中的组件。 |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)](#oh_arkui_nodeadapterevent_setnodeid) | - | 设置生成的组件标识。 |
| [ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getlayoutconstraintinmeasure) | - | Obtains the size constraint for measurement through a custom component event. |
| [ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getpositioninlayout) | - | Obtains the expected position of a component relative to its parent component in the layout phase through acustom component event. |
| [ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getdrawcontextindraw) | - | Obtains the drawing context through a custom component event. |
| [int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_geteventtargetid) | - | Obtains the ID of a custom component event. |
| [void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getuserdata) | - | Obtains custom event parameters through a custom component event. |
| [ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getnodehandle) | - | Obtains a component object through a custom component event. |
| [ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_geteventtype) | - | Obtains the event type through a custom component event. |
| [int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_nodecustomevent_getcustomspanmeasureinfo) | - | Obtains the measurement information of a custom span through a custom component event. |
| [int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)](#oh_arkui_nodecustomevent_setcustomspanmetrics) | - | Sets the measurement metrics of a custom span through a custom component event. |
| [int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_nodecustomevent_getcustomspandrawinfo) | - | Obtains the drawing information of a custom span through a custom component event. |
| [typedef void (\*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)](#arkui_nodecontentcallback) | ArkUI_NodeContentCallback | Defines the callback function of a node content event. |
| [int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)](#oh_arkui_nodecontent_registercallback) | - | 注册NodeContent事件函数。 |
| [ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_geteventtype) | - | Obtains the type of a node content event. |
| [ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_getnodecontenthandle) | - | Obtains the node content object that triggers a node content event. |
| [int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)](#oh_arkui_nodecontent_setuserdata) | - | Saves custom data on the specified node content. |
| [void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)](#oh_arkui_nodecontent_getuserdata) | - | Obtains the custom data saved on the specified node content. |
| [int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_addnode) | - | 将一个ArkUI组件节点添加到对应的NodeContent对象下。 |
| [int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_removenode) | - | 删除NodeContent对象下的一个ArkUI组件节点。 |
| [int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)](#oh_arkui_nodecontent_insertnode) | - | 将一个ArkUI组件节点插入到对应的NodeContent对象的特定位置下。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)](#oh_arkui_nodeutils_getlayoutsize) | - | 获取组件布局区域的大小。布局区域大小不包含图形变化属性，如缩放。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)](#oh_arkui_nodeutils_getlayoutposition) | - | 获取组件布局区域相对父组件的位置。布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getlayoutpositioninwindow) | - | 获取组件布局区域相对窗口的位置。布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)](#oh_arkui_nodeutils_getlayoutpositioninscreen) | - | 获取组件布局区域相对屏幕的位置。布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)](#oh_arkui_nodeutils_getlayoutpositioninglobaldisplay) | - | 获取组件相对于全局屏幕的偏移。布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinwindow) | - | Obtain the position of the component in the window, including the properties of graphic translation changes. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinscreen) | - | Obtain the position of the component on the screen, including the attributes of graphic translation changes. |
| [void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)](#oh_arkui_nodeutils_addcustomproperty) | - | 设置组件的自定义属性。该接口仅在主线程生效。 |
| [void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)](#oh_arkui_nodeutils_removecustomproperty) | - | 移除组件已设置的自定义属性。 |
| [int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)](#oh_arkui_nodeutils_getcustomproperty) | - | 获取组件的自定义属性的值。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getparentinpagetree) | - | 获取父节点，可获取由ArkTs创建的组件节点。 |
| [int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)](#oh_arkui_nodeutils_getactivechildreninfo) | - | 获取某个节点所有活跃的子节点。Span将不会被计入子节点的统计中。在LazyForEach场景中，推荐使用[OH_ArkUI_NodeUtils_GetChildWithExpandMode](capi-native-node-h.md#oh_arkui_nodeutils_getchildwithexpandmode)接口进行遍历。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getcurrentpagerootnode) | - | 获取当前页面的根节点。 |
| [bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_iscreatedbyndk) | - | 获取组件是否由C-API创建的标签。 |
| [int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getnodetype) | - | 获取节点的类型。 |
| [int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)](#oh_arkui_nodeutils_getwindowinfo) | - | 获取节点所属的窗口信息。 |
| [int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getfirstchildindexwithoutexpand) | - | 获取目标节点在树上的第一个子节点的下标。 |
| [int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getlastchildindexwithoutexpand) | - | 获取目标节点在树上的最后一个子节点的下标。 |
| [int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)](#oh_arkui_nodeutils_getchildwithexpandmode) | - | 用不同的展开模式获取对应下标的子节点。 |
| [int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_list_closeallswipeactions) | - | 收起展开状态下的ListItem。 |
| [ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)](#oh_arkui_getcontextbynode) | - | Obtain the UIContext pointer to the page where the node is located. |
| [int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))](#oh_arkui_registersystemcolormodechangeevent) | - | The event called when the system color mode changes.Only one system color change callback can be registered for the same component. |
| [void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemcolormodechangeevent) | - | Unregister the event callback when the system color mode changes. |
| [int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))](#oh_arkui_registersystemfontstylechangeevent) | - | The event called when the system font style changes.Only one system font change callback can be registered for the same component. |
| [void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemfontstylechangeevent) | - | Unregister the event callback when the system font style changes. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontsizescale) | - | Retrieve the font size value for system font change events. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontweightscale) | - | Retrieve the font thickness values for system font change events. |
| [int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getattachednodehandlebyid) | - | 根据用户id获取目标节点。 |
| [int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)](#oh_arkui_nodeutils_moveto) | - | 将节点移动到目标父节点下，作为子节点。 |
| [int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_invalidateattributes) | - | 在当前帧触发节点属性更新。当前节点的属性在构建阶段后被修改，这些改动不会立即生效，而是延迟到下一帧统一处理。此功能强制当前帧内即时节点更新，确保同步应用渲染效果。 |
| [int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_setcrosslanguageoption) | - | 设置目标节点跨语言设置属性的能力。 |
| [int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_getcrosslanguageoption) | - | 获取目标节点跨语言设置属性的配置项。 |
| [int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onLayoutCompleted)(void* userData))](#oh_arkui_registerlayoutcallbackonnodehandle) | - | Registers a callback for node when layout is completed. |
| [int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onDrawCompleted)(void* userData))](#oh_arkui_registerdrawcallbackonnodehandle) | - | Registers a callback for node when draw is completed. |
| [int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterlayoutcallbackonnodehandle) | - | Unregisters the layout completed callback for node. |
| [int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterdrawcallbackonnodehandle) | - | Unregisters the draw completed callback for node. |
| [int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelmap)](#oh_arkui_getnodesnapshot) | - | Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered,the snapshot operation will fail. When the <b>Pixelmap</b> object created is no longer in use, it should be releasedby calling {@link OH_PixelmapNative_Release}. |
| [int32_t OH_ArkUI_GetNodeSnapshotSizeLimitation(int32_t* maxWidth, int32_t* maxHeight)](#oh_arkui_getnodesnapshotsizelimitation) | - | Query the size limitation of the component snapshot. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getpositiontoparent) | - | 获取目标节点相对于父节点的偏移值，单位：px。 |
| [ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)](#oh_arkui_addsupporteduistates) | - | 设置组件支持的多态样式状态。为了更高效地处理，需传入所关注的状态值及对应的状态处理函数，当关注的状态发生时，处理函数会被执行。可在回调中根据当前状态调整UI样式。当在同一个节点上多次调用该方法时，将以最后一次传入的状态及处理函数为准。有些类型的组件节点，系统内部已有对某些状态的默认处理。例如，Button组件默认具备对PRESSED状态的样式变化，当在此类组件上使用此方法自定义状态处理时，会先应用系统默认样式变化，再执行自定义的样式处理，最终效果为两者叠加。可以通过指定excludeInner为true来禁用系统内部的默认样式效果，但这通常取决于系统内部实现规范是否允许。当调用该函数时，传入的statesChangeHandler函数会立即执行一次，且无需特意注册对NORMAL状态的监听，只要注册了非NORMAL状态，当状态从任意状态变化回NORMAL时，系统都会进行回调，以便应用进行样式复原。 |
| [ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)](#oh_arkui_removesupporteduistates) | - | 删除注册的状态处理。当通过OH_ArkUI_AddSupportedUIStates注册的状态都被删除时，所注册的stateChangeHandler也不会再被执行。 |
| [int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(\*callback)(void* userData))](#oh_arkui_runtaskinscope) | - | 在目标UI上下文中执行传入的自定义回调函数。示例请参考：[在NDK中保证多实例场景功能正常](../../../ui/ndk-scope-task.md)。 |
| [int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getnodehandlebyuniqueid) | - | Get the node handle by uniqueId. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)](#oh_arkui_nodeutils_getnodeuniqueid) | - | 获取目标节点的uniqueId。 |
| [int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)](#oh_arkui_nativemodule_isinrenderstate) | - | 获取节点是否处于渲染状态，如果一个节点的对应RenderNode在渲染树上，则处于渲染状态。 |
| [int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_adoptchild) | - | 当前节点接纳目标节点为附属节点。被接纳的节点不能已有父节点。调用该接口实际上不会将其添加为子节点，而是仅允许其接收对应子节点的生命周期回调。 |
| [int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_removeadoptedchild) | - | 移除被接纳的目标附属节点。 |
| [int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (\*colorInvertFunc)(uint32_t color))](#oh_arkui_setforcedarkconfig) | - | 为组件和实例设置反色算法。详细介绍请参考：[利用反色能力快速适配深色模式](../../../ui/ui-dark-light-color-adaptation.md#利用反色能力快速适配深色模式)。 |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonevent) | - | 注册目标节点的基础事件回调。当前支持的事件类型如下: 参考[ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype)中的NODE_ON_CLICK_EVENT、NODE_TOUCH_EVENT、NODE_EVENT_ON_APPEAR、NODE_EVENT_ON_DISAPPEAR、NODE_ON_KEY_EVENT、NODE_ON_FOCUS、NODE_ON_BLUR、NODE_ON_HOVER、NODE_ON_MOUSE、NODE_ON_SIZE_CHANGE。 |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)](#oh_arkui_nativemodule_unregistercommonevent) | - | 注销目标节点的基础事件回调。当前支持的事件类型请参考[OH_ArkUI_NativeModule_RegisterCommonEvent](capi-native-node-h.md#oh_arkui_nativemodule_registercommonevent)。 |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonvisibleareaapproximatechangeevent) | - | 注册限制回调间隔的可见区域变化的基础事件回调。 |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonvisibleareaapproximatechangeevent) | - | 注销限制回调间隔的可见区域变化的基础事件回调。 |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)](#oh_arkui_nativemodule_convertpositiontowindow) | - | 将点的坐标从指定节点的坐标系转换至当前窗口的坐标系。节点的坐标系考虑节点本身的变换，例如，节点A的变换效果为向左平移100，会使得其坐标系中的点的坐标也向左平移100。 |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)](#oh_arkui_nativemodule_convertpositionfromwindow) | - | 将点的坐标从当前窗口的坐标系转换至目标节点的坐标系。节点的坐标系考虑节点本身的变换，例如，节点A的变换效果为向左平移100，会使得其坐标系中的点的坐标也向左平移100。 |
| [int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)](#oh_arkui_swiper_finishanimation) | - | 停止指定的Swiper节点正在执行的翻页动画。 |
| [int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (\*asyncUITask)(void* asyncUITaskData), void (\*onFinish)(void* asyncUITaskData))](#oh_arkui_postasyncuitask) | - | 将asyncUITask函数提交至ArkUI框架提供的非UI线程中执行，asyncUITask函数执行完毕后，在UI线程调用onFinish函数。适用于多线程创建UI组件的场景，开发者可使用此接口在非UI线程创建UI组件，随后在UI线程将创建完成的组件挂载至主树上。 |
| [int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitask) | - | 将task函数提交至UI线程中执行。适用于多线程创建UI组件的场景，当开发者在自建的线程中创建UI组件时，可以使用此接口将创建完成的组件挂载到UI线程的主树上。 |
| [int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)](#oh_arkui_nativemodule_atomicservicemenubarsetvisible) | - | 设置菜单栏的可见性。 |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonareaapproximatechangeevent) | - | Registers a callback for listening for component dimension and area changes.This function can be called for a valid [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node at any time. <br> The newly registered callback will replace the previously registered callback for this event and will take effect from the next frame. <br> When the callback is no longer needed, call [OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent](capi-native-node-h.md#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) to unregister it. <br> Otherwise, the callback will be automatically unregistered when the node is released. |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) | - | Unregisters the callback bound to the dimensions and area changes of a component. |
| [int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitaskandwait) | - | 将task函数提交至UI线程中执行，调用此接口的线程将阻塞，直至task函数执行完成。在UI线程调用此接口等同于同步调用task函数。适用于多线程创建UI组件的场景，当开发者在多线程创建组件过程中需要调用仅支持UI线程的函数时，使用此接口返回UI线程调用函数，调用完成后继续多线程创建组件。当UI线程负载较高时，调用此接口的非UI线程可能长时间阻塞，影响多线程创建UI组件的性能，不建议频繁使用。 |
| [int32_t OH_ArkUI_Swiper_StartFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_startfakedrag) | - | Start a fake drag of the Swiper node.Call OH_ArkUI_Swiper_FakeDragBy to simulate the drag motion. Call OH_ArkUI_Swiper_StopFakeDrag to complete thefake drag. A fake drag can be interrupted by a real drag. If you need to ignore touch events and other user inputduring a fake drag, use NODE_SWIPER_DISABLE_SWIPE. |
| [int32_t OH_ArkUI_Swiper_FakeDragBy(ArkUI_NodeHandle node, float offset, bool* isConsumedOffset)](#oh_arkui_swiper_fakedragby) | - | Fake drag by an offset of the Swiper node.The OH_ArkUI_Swiper_StartFakeDrag must be called first. |
| [int32_t OH_ArkUI_Swiper_StopFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_stopfakedrag) | - | Stop a fake drag of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_IsFakeDragging(ArkUI_NodeHandle node, bool* isFakeDragging)](#oh_arkui_swiper_isfakedragging) | - | Get the fake drag state of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_ShowPrevious(ArkUI_NodeHandle node)](#oh_arkui_swiper_showprevious) | - | Show the previous page of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_ShowNext(ArkUI_NodeHandle node)](#oh_arkui_swiper_shownext) | - | Show the next page of the Swiper node. |
| [int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)](#oh_arkui_nativemodule_getpagerootnodehandlebycontext) | - | 获取指定实例的页面的根节点。 |
| [ArkUI_GestureCollectInterceptInfo* OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_getgesturecollectinterceptinfo) | - | Obtains the <b>ArkUI_GestureCollectInterceptInfo</b> object from a specified <b>ArkUI_NodeEvent</b> object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_SetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy policy)](#oh_arkui_nativemodule_setchildmountpolicy) | - | Set the subnode mounting policy of the target node. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy* policy)](#oh_arkui_nativemodule_getchildmountpolicy) | - | Get the current child mount policy of the specified node. |

## 枚举类型说明

### ArkUI_NodeType

```c
enum ArkUI_NodeType
```

**描述**

Enumerates ArkUI component types that can be created on the native side.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NODE_CUSTOM = 0 | Custom node. |
| ARKUI_NODE_TEXT = 1 | Text. |
| ARKUI_NODE_SPAN = 2 | Text span. |
| ARKUI_NODE_IMAGE_SPAN = 3 | Image span. |
| ARKUI_NODE_IMAGE = 4 | Image. |
| ARKUI_NODE_TOGGLE = 5 | Toggle. |
| ARKUI_NODE_LOADING_PROGRESS = 6 | Loading icon. |
| ARKUI_NODE_TEXT_INPUT = 7 | Single-line text input. |
| ARKUI_NODE_TEXT_AREA = 8 | Multi-line text input. |
| ARKUI_NODE_BUTTON = 9 | Button. |
| ARKUI_NODE_PROGRESS = 10 | Progress indicator. |
| ARKUI_NODE_CHECKBOX = 11 | Check box. |
| ARKUI_NODE_XCOMPONENT = 12 | SURFACE类型XComponent。 |
| ARKUI_NODE_DATE_PICKER = 13 | 日期选择器组件。 |
| ARKUI_NODE_TIME_PICKER = 14 | 时间选择组件。 |
| ARKUI_NODE_TEXT_PICKER = 15 | 滑动选择文本内容的组件。 |
| ARKUI_NODE_CALENDAR_PICKER = 16 | 日历选择器组件。 |
| ARKUI_NODE_SLIDER = 17 | Slider. |
| ARKUI_NODE_RADIO = 18 | Radio |
| ARKUI_NODE_IMAGE_ANIMATOR = 19 | Image animator. |
| ARKUI_NODE_XCOMPONENT_TEXTURE | TEXTURE类型XComponent。@since 18 |
| ARKUI_NODE_CHECKBOX_GROUP = 21 | Check box group.@since 15 |
| ARKUI_NODE_TEXT_EDITOR = 22 |  |
| ARKUI_NODE_STACK = MAX_NODE_SCOPE_NUM | Stack container. |
| ARKUI_NODE_SWIPER | Swiper. |
| ARKUI_NODE_SCROLL | Scrolling container. |
| ARKUI_NODE_LIST | List. |
| ARKUI_NODE_LIST_ITEM | List item. |
| ARKUI_NODE_LIST_ITEM_GROUP | List item group. |
| ARKUI_NODE_COLUMN | Column container. |
| ARKUI_NODE_ROW | Row container. |
| ARKUI_NODE_FLEX | Flex container. |
| ARKUI_NODE_REFRESH | Refresh component. |
| ARKUI_NODE_WATER_FLOW | Water flow container. |
| ARKUI_NODE_FLOW_ITEM | Water flow item. |
| ARKUI_NODE_RELATIVE_CONTAINER | Relative layout component. |
| ARKUI_NODE_GRID | Grid. |
| ARKUI_NODE_GRID_ITEM | Grid item. |
| ARKUI_NODE_CUSTOM_SPAN | Custom span. |
| ARKUI_NODE_EMBEDDED_COMPONENT |  |
| ARKUI_NODE_UNDEFINED |  |
| ARKUI_NODE_PICKER = 1018 |  |
| ARKUI_NODE_ARC_LIST = 1019 |  |
| ARKUI_NODE_ARC_LIST_ITEM = 1020 |  |
| ARKUI_NODE_ARC_SCROLL_BAR = 1021 |  |

### ArkUI_NodeAttributeType

```c
enum ArkUI_NodeAttributeType
```

**描述**

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_WIDTH = 0 | 宽度属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置宽度数值，单位为vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：宽度数值，单位为vp。</li></ul> |
| NODE_HEIGHT | 高度属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置高度数值，单位为vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：高度数值，单位为vp。</li></ul> |
| NODE_BACKGROUND_COLOR | 背景色属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li><b>.value[0].u32</b>：背景色数值，0xargb格式，形如 `0xFFFF0000` 表示红色。</li></ul>**返回：<ul><li><b>.value[0].u32</b>：背景色数值，0xargb格式，形如 `0xFFFF0000` 表示红色。</li></ul> |
| NODE_BACKGROUND_IMAGE | 背景色图片属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li><b>.string</b>：图片地址。API version 22及之前版本，支持网络图片资源地址、本地图片资源地址、Base64和{@link PixelMap}资源，不支持{@link svg}图片、gif和webp等类型的动图。从API version 23开始，新增支持webp和gif类型的动图，显示动图第一帧，不支持其他类型的动图。</li><li><b>.value[0]?.i32</b>：可选值，repeat参数，参数类型[ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat)，默认值为ARKUI_IMAGE_REPEAT_NONE。</li><li><b>.object</b>：PixelMap图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。`.object`参数和`.string`参数二选一，不可同时设置。</li></ul>**返回：<ul><li><b>.string</b>：图片地址。API version 22及之前版本，支持网络图片资源地址、本地图片资源地址、Base64和PixelMap资源，不支持svg图片、gif和webp等类型的动图。从APIversion 23开始，新增支持webp和gif类型的动图，显示动图第一帧，不支持其他类型的动图。</li><li><b>.value[0].i32</b>：repeat参数，参数类型[ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat)。</li><li><b>.object</b>：PixelMap图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。</li></ul> |
| NODE_PADDING | 内间距属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1. 只传入一个参数，表示统一设置上下左右四个位置的内间距值。<ul><li>.value[0].f32：统一设置内间距数值，单位为vp。</li></ul>2. 传入四个参数，表示分别设置上下左右四个位置的内间距值。<ul><li>.value[0].f32：设置上内间距数值，单位为vp，默认值为0vp。</li><li>.value[1].f32：设置右内间距数值，单位为vp，默认值为0vp。</li><li>.value[2].f32：设置下内间距数值，单位为vp，默认值为0vp。</li><li>.value[3].f32：设置左内间距数值，单位为vp，默认值为0vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：上内间距数值，单位为vp。</li><li>.value[1].f32：右内间距数值，单位为vp。</li><li>.value[2].f32：下内间距数值，单位为vp。</li><li>.value[3].f32：左内间距数值，单位为vp。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_ID | Defines the component ID attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component ID.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component ID.<br> |
| NODE_ENABLED | 设置组件是否可交互，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：false表示不可交互，true表示可交互。<br>*返回：<br><b>.value[0].i32</b>：0表示不可交互，1表示可交互。 |
| NODE_MARGIN | 外间距属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1. 只传入一个参数，表示统一设置上下左右四个位置的外间距值。<ul><li>.value[0].f32：统一设置上下左右四个位置的外间距值，单位为vp。</li></ul>2. 传入四个参数，表示分别设置上下左右四个位置的外间距值。<ul><li>.value[0].f32：设置上外间距数值，单位为vp，默认值为0vp。</li><li>.value[1].f32：设置右外间距数值，单位为vp，默认值为0vp。</li><li>.value[2].f32：设置下外间距数值，单位为vp，默认值为0vp。</li><li>.value[3].f32：设置左外间距数值，单位为vp，默认值为0vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：上外间距数值，单位为vp。</li><li>.value[1].f32：右外间距数值，单位为vp。</li><li>.value[2].f32：下外间距数值，单位为vp。</li><li>.value[3].f32：左外间距数值，单位为vp。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_TRANSLATE | Defines the translate attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: distance to translate along the x-axis, in vp. The default value is <b>0</b>.<br> .value[1].f32: distance to translate along the y-axis, in vp. The default value is <b>0</b>.<br> .value[2].f32: distance to translate along the z-axis, in vp. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: distance to translate along the x-axis, in vp.<br> .value[1].f32: distance to translate along the y-axis, in vp.<br> .value[2].f32: distance to translate along the z-axis, in vp. <br> |
| NODE_SCALE | Defines the scale attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: scale factor along the x-axis. The default value is <b>1</b>.<br> .value[1].f32: scale factor along the y-axis. The default value is <b>1</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: scale factor along the x-axis.<br> .value[1].f32: scale factor along the y-axis. <br> |
| NODE_ROTATE | Defines the rotate attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: X coordinate of the rotation axis vector. The default value is <b>0</b>.<br> .value[1].f32: Y coordinate of the rotation axis vector. The default value is <b>0</b>.<br> .value[2].f32: Z coordinate of the rotation axis vector. The default value is <b>0</b>.<br> .value[3].f32: rotation angle. The default value is <b>0</b>.<br> .value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp.The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate of the rotation axis vector.<br> .value[1].f32: Y coordinate of the rotation axis vector.<br> .value[2].f32: Z coordinate of the rotation axis vector.<br> .value[3].f32: rotation angle.<br> .value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp. <br> |
| NODE_BRIGHTNESS | Sets the brightness attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: brightness value. The default value is <b>1.0</b>, and the recommended value range is [0, 2]. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: brightness value. <br> |
| NODE_SATURATION | Sets the saturation attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].f32: saturation value. The default value is <b>1.0</b>, and the recommended value range is [0, 50). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].f32: saturation value. <br> |
| NODE_BLUR | Sets the blur attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].f32: blur radius. A larger value indicates a higher blur degree. If the value is <b>0</b>,the component is not blurred. The unit is vp. The default value is <b>0.0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: blur radius. The larger the fuzzy radius, the more blurred the image. If the value is <b>0</b>,the image is not blurred. The unit is vp. <br> |
| NODE_LINEAR_GRADIENT | Sets the gradient attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: start angle of the linear gradient. This attribute takes effect only when[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection) is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>.A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>. <br> .value[1].i32: direction of the linear gradient. When it is set, the <b>angle</b> attribute does not take effect.The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection): <br> .value[2].i32: whether the colors are repeated. The default value is <b>false</b>. <br> .object: array of color stops, each of which consists of a color and its stop position.Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].f32: start angle of the linear gradient. <br> .value[1].i32: direction of the linear gradient. It does not take effect when <b>angle</b> is set. <br> .value[2].i32: whether the colors are repeated. <br> .object: array of color stops, each of which consists of a color and its stop position.Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> |
| NODE_ALIGNMENT | 设置组件内容在元素绘制区域内的对齐方式，支持属性设置，属性重置和属性获取接口。在Stack中该属性与NODE_STACK_ALIGN_CONTENT效果一致，只能设置子组件在容器内的对齐方式。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32： 设置对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值ARKUI_ALIGNMENT_CENTER。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32： 对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)。</li></ul> |
| NODE_OPACITY | Defines the opacity attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: opacity value. The value ranges from 0 to 1. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: opacity value. The value ranges from 0 to 1. <br> |
| NODE_BORDER_WIDTH | 边框宽度属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1. 只传入一个参数，表示统一设置四条边的边框宽度。<ul><li>.value[0].f32：统一设置四条边的边框宽度，单位为vp。</li></ul>2. 传入四个参数，表示分别设置四条边的边框宽度。<ul><li>.value[0].f32：设置上边框的边框宽度，单位为vp，默认值为0vp。</li><li>.value[1].f32：设置右边框的边框宽度，单位为vp，默认值为0vp。</li><li>.value[2].f32：设置下边框的边框宽度，单位为vp，默认值为0vp。</li><li>.value[3].f32：设置左边框的边框宽度，单位为vp，默认值为0vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：上边框的边框宽度。</li><li>.value[1].f32：右边框的边框宽度。</li><li>.value[2].f32：下边框的边框宽度。</li><li>.value[3].f32：左边框的边框宽度。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_BORDER_RADIUS | 边框圆角属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1. 只传入一个参数，表示统一设置四条边的边框圆角。<ul><li>.value[0].f32：统一设置四条边的边框圆角。</li></ul>2. 传入四个参数，表示分别设置四条边的边框圆角。<ul><li>.value[0].f32：设置左上角圆角半径，单位为vp，默认值为0vp。</li><li>.value[1].f32：设置右上角圆角半径，单位为vp，默认值为0vp。</li><li>.value[2].f32：设置左下角圆角半径，单位为vp，默认值为0vp。</li><li>.value[3].f32：设置右下角圆角半径，单位为vp，默认值为0vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：左上角圆角半径。</li><li>.value[1].f32：右上角圆角半径。</li><li>.value[2].f32：左下角圆角半径。</li><li>.value[3].f32：右下角圆角半径。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_BORDER_COLOR | 边框颜色属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1：统一设置四条边的边框颜色。<ul><li>.value[0].u32：统一设置四条边的边框颜色，使用0xargb表示，如`0xFFFF11FF`。</li></ul>2：分别设置四条边的边框颜色。<ul><li>.value[0].u32：设置上侧边框颜色，使用0xargb表示，默认值为0xFF000000。</li><li>.value[1].u32：设置右侧边框颜色，使用0xargb表示，默认值为0xFF000000。</li><li>.value[2].u32：设置下侧边框颜色，使用0xargb表示，默认值为0xFF000000。</li><li>.value[3].u32：设置左侧边框颜色，使用0xargb表示，默认值为0xFF000000。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：上侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><li>.value[1].u32：右侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><li>.value[2].u32：下侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><li>.value[3].u32：左侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_BORDER_STYLE | 边框线条样式属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1. 只传入一个参数，表示统一设置四条边的边框线条样式。<ul><li>.value[0].i32：统一设置四条边的边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li></ul>2. 传入四个参数，表示分别设置四条边的边框线条样式。<ul><li>.value[0].i32：设置上侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li><li>.value[1].i32：设置右侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li><li>.value[2].i32：设置下侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li><li>.value[3].i32：设置左侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：上侧边框线条样式对应的数值。</li><li>.value[1].i32：右侧边框线条样式对应的数值。</li><li>.value[2].i32：下侧边框线条样式对应的数值。</li><li>.value[3].i32：左侧边框线条样式对应的数值。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_Z_INDEX | 组件的堆叠顺序属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：堆叠顺序数值。<br>*返回：<br><b>.value[0].i32</b>：堆叠顺序数值。 |
| NODE_VISIBILITY | 组件是否可见属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li><b>.value[0].i32</b>：控制当前组件显示或隐藏，参数类型[ArkUI_Visibility](capi-common-attributes-h.md#arkui_visibility)，默认值为ARKUI_VISIBILITY_VISIBLE。</li></ul>**返回：<ul><li><b>.value[0].i32</b>：控制当前组件显示或隐藏，参数类型[ArkUI_Visibility](capi-common-attributes-h.md#arkui_visibility)，默认值为ARKUI_VISIBILITY_VISIBLE。</li></ul> |
| NODE_CLIP | Defines the clipping and masking attribute, which can be set, reset, and obtained as required throughAPIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to clip the component based on the parent container bounds.The value <b>1</b> means to clip the component, and <b>0</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to clip the component based on the parent container bounds.The value <b>1</b> means to clip the component, and <b>0</b> means the opposite. <br> |
| NODE_CLIP_SHAPE | Defines the clipping region on the component.This attribute can be set and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute,which supports four types of shapes:<br> 1. Rectangle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_RECTANGLE</b> for the rectangle shape. <br> .value[1].f32: width of the rectangle.<br> .value[2].f32: height of rectangle.<br> .value[3].f32: width of the rounded corner of the rectangle.<br> .value[4].f32: height of the rounded corner of the rectangle.<br> .value[5]?.f32: radius of the top left corner of the rectangular shape.<br> .value[6]?.f32: radius of the bottom left corner of the rectangular shape.<br> .value[7]?.f32: radius of the top right corner of the rectangular shape.<br> .value[8]?.f32: radius of the bottom right corner of the rectangular shape.<br> ?.object: clipOption of the rectangle. The parameter type is {@link ArkUI_RenderNodeClipOption} type.It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is rectangle, and .size must be equal to 1.2. Circle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_CIRCLE</b> for the circle shape.<br> .value[1].f32: width of the circle.<br> .value[2].f32: height of the circle.<br> ?.object: clipOption of the circle. The parameter type is {@link ArkUI_RenderNodeClipOption} type.It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is circle, and .size must be equal to 1.3.Ellipse:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[1].f32: width of the ellipse.<br> .value[2].f32: height of the ellipse.<br> ?.object: clipOption of the ellipse. The parameter type is {@link ArkUI_RenderNodeClipOption} type.It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is ellipse, and .size must be equal to 1.4. Path:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_PATH</b> for the path shape.<br> .value[1].f32: width of the path.<br> .value[2].f32: height of the path.<br> .string: command for drawing the path.<br> ?.object: clipOption of the path. The parameter type is {@link ArkUI_RenderNodeClipOption} type.It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is path, and .size must be equal to 1.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md), which supports four types of shapes: <br> 1. Rectangle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_RECTANGLE</b> for the rectangle shape. <br> .value[1].f32: width of the rectangle.<br> .value[2].f32: height of rectangle.<br> .value[3].f32: width of the rounded corner of the rectangle.<br> .value[4].f32: height of the rounded corner of the rectangle.<br> .value[5].f32: radius of the top left corner of the rectangular shape; <br> .value[6].f32: radius of the bottom left corner of the rectangular shape; <br> .value[7].f32: radius of the top right corner of the rectangular shape; <br> .value[8].f32: radius of the bottom right corner of the rectangular shape; <br> .value[9]?.f32: horizontal coordinate offset of the rectangle. <br> .value[10]?.f32: vertical coordinate offset of the rectangle. <br> 2. Circle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_CIRCLE</b> for the circle shape.<br> .value[1].f32: width of the circle.<br> .value[2].f32: height of the circle.<br> .value[3]?.f32: horizontal coordinate offset of the circle.<br> .value[4]?.f32: vertical coordinate offset of the circle.<br> 3.Ellipse:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[1].f32: width of the ellipse.<br> .value[2].f32: height of the ellipse.<br> .value[3]?.f32: horizontal coordinate offset of the ellipse.<br> .value[4]?.f32: vertical coordinate offset of the ellipse.<br> 4. Path:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_PATH</b> for the path shape.<br> .value[1].f32: width of the path.<br> .value[2].f32: height of the path.<br> .string: command for drawing the path.<br> |
| NODE_TRANSFORM | Defines the transform attribute, which can be used to translate, rotate, and scale images.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0...15].f32: 16 floating-point numbers. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0...15].f32: 16 floating-point numbers. <br> |
| NODE_HIT_TEST_BEHAVIOR | 触摸测试类型，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li><b>.value[0].i32</b>：控制当前组件的触摸测试类型，参数类型[ArkUI_HitTestMode](capi-common-attributes-h.md#arkui_hittestmode)，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。</li></ul>**返回：<ul><li><b>.value[0].i32</b>：控制当前组件的触摸测试类型，参数类型[ArkUI_HitTestMode](capi-common-attributes-h.md#arkui_hittestmode)，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。</li></ul> |
| NODE_POSITION | 元素左上角相对于父容器左上角偏移位置，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置x轴坐标。</li><li>.value[1].f32: 设置y轴坐标。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：x轴坐标。</li><li>.value[1].f32: y轴坐标。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_SHADOW | Defines the shadow attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: shadow effect. The parameter type is [ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: shadow effect. The parameter type is [ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle). <br> |
| NODE_CUSTOM_SHADOW | Defines the custom shadow effect. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: blur radius of the shadow, in vp.<br> .value[1]?.i32: whether to enable the coloring strategy. The value <b>1</b> means to enable the coloringstrategy, and <b>0</b> (default value) means the opposite.<br> .value[2]?.f32: offset of the shadow along the x-axis, in px.<br> .value[3]?.f32: offset of the shadow along the y-axis, in px.<br> .value[4]?.i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is <b>ARKUI_SHADOW_TYPE_COLOR</b>.<br> .value[5]?.u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> .value[6]?.u32: whether to fill the shadow. The value <b>1</b> means to fill the shadow, and <b>0</b>means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: blur radius of the shadow, in vp.<br> .value[1].i32: whether to enable the coloring strategy. <br> .value[2].f32: offset of the shadow along the x-axis, in px.<br> .value[3].f32: offset of the shadow along the y-axis, in px.<br> .value[4].i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is <b>ARKUI_SHADOW_TYPE_COLOR</b>.<br> .value[5].u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> .value[6].u32: whether to fill the shadow. The value <b>1</b> means to fill the shadow, and <b>0</b>means the opposite.<br> |
| NODE_BACKGROUND_IMAGE_SIZE | 背景图片的宽高属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li><b>.value[0].f32</b>：图片的宽度值，取值范围`[0,+∞)`，单位为vp。</li><li><b>.value[1].f32</b>：图片的高度值，取值范围`[0,+∞)`，单位为vp。</li></ul>**返回：<ul><li><b>.value[0].f32</b>：图片的宽度值，单位为vp。</li><li><b>.value[1].f32</b>：图片的高度值，单位为vp。</li></ul> |
| NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE | 背景图片的宽高样式属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li><b>.value[0].i32</b>：背景图片的宽高样式，取[ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize)枚举值。</li></ul>**返回：<ul><li><b>.value[0].i32</b>：背景图片的宽高样式，取[ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize)枚举值。</li></ul> |
| NODE_BACKGROUND_BLUR_STYLE | Defines the background blur attribute, which can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: blue type. The value is an enum of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).</li><li>.value[1]?.i32: color mode. The value is an enum of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).</li><li>.value[2]?.i32: adaptive color mode. The value is an enum of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).</li><li>.value[3]?.f32: blur degree. The value range is [0.0, 1.0].</li><li>.value[4]?.f32: start boundary of grayscale blur.</li><li>.value[5]?.f32: end boundary of grayscale blur.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: blue type. The value is an enum of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).</li><li>.value[1].i32: color mode. The value is an enum of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).</li><li>.value[2].i32: adaptive color mode. The value is an enum of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).</li><li>.value[3].f32: blur degree. The value range is [0.0, 1.0].</li><li>.value[4].f32: start boundary of grayscale blur.</li><li>.value[5].f32: end boundary of grayscale blur.</li></ul> |
| NODE_TRANSFORM_CENTER | Defines the transform center attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: X coordinate of the center point, in vp.<br> .value[1]?.f32: Y coordinate of the center point, in vp.<br> .value[2]?.f32: Z coordinate of the center point, in vp.<br> .value[3]?.f32 : X coordinate of the center point, expressed in a number that represents a percentage.For example, 0.2 indicates 20%. This attribute overwrites value[0].f32. The default value is <b>0.5f</b>. <br> .value[4]?.f32 : Y coordinate of the center point, expressed in a number that represents a percentage.For example, 0.2 indicates 20%. This attribute overwrites value[1].f32. The default value is <b>0.5f</b>. <br> .value[5]?.f32 : Z coordinate of the center point, expressed in a number that represents a percentage.For example, 0.2 indicates 20%. This attribute overwrites value[2].f32. The default value is <b>0.0f</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate of the center point, in vp.<br> .value[1].f32: Y coordinate of the center point, in vp.<br> .value[2].f32: Z coordinate of the center point, in vp.<br> Note: If the coordinate is expressed in a number that represents a percentage, the attribute obtaining APIreturns the calculated value in vp. |
| NODE_OPACITY_TRANSITION | Defines the transition opacity attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: opacity values of the start and end points.<br> .value[1].i32: animation duration, in milliseconds.<br> .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3]?.i32: animation delay duration, in milliseconds.<br> .value[4]?.i32: number of times that the animation is played.<br> .value[5]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[6]?.f32: animation playback speed.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: opacity values of the start and end points.<br> .value[1].i32: animation duration, in milliseconds.<br> .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3].i32: animation delay duration, in milliseconds. <br> .value[4].i32: number of times that the animation is played. <br> .value[5].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[6].f32: animation playback speed. <br> |
| NODE_ROTATE_TRANSITION | Defines the transition rotation attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: X-component of the rotation vector. <br> .value[1].f32: Y-component of the rotation vector. <br> .value[2].f32: Z-component of the rotation vector <br> .value[3].f32: angle. <br> .value[4].f32: line of sight. The default value is <b>0.0f</b>. <br> .value[5].i32: animation duration, in milliseconds. <br> .value[6].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> .value[7]?.i32: animation delay duration, in milliseconds. <br> .value[8]?.i32: number of times that the animation is played. <br> .value[9]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[10]?.f32: animation playback speed. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X-component of the rotation vector. <br> .value[1].f32: Y-component of the rotation vector. <br> .value[2].f32: Z-component of the rotation vector <br> .value[3].f32: angle. <br> .value[4].f32: line of sight. <br> .value[5].i32: animation duration, in milliseconds. <br> .value[6].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> .value[7].i32: animation delay duration, in milliseconds. <br> .value[8].i32: number of times that the animation is played. <br> .value[9].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[10].f32: animation playback speed. <br> |
| NODE_SCALE_TRANSITION | Defines the transition scaling attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: scale factor along the x-axis. <br> .value[1].f32: scale factor along the y-axis. <br> .value[2].f32: scale factor along the z-axis. <br> .value[3].i32: animation duration, in milliseconds. <br> .value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> .value[5]?.i32: animation delay duration, in milliseconds. <br> .value[6]?.i32: number of times that the animation is played. <br> .value[7]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[8]?.f32: animation playback speed. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: scale factor along the x-axis. <br> .value[1].f32: scale factor along the y-axis. <br> .value[2].f32: scale factor along the z-axis. <br> .value[3].i32: animation duration, in milliseconds. <br> .value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> .value[5].i32: animation delay duration, in milliseconds. <br> .value[6].i32: number of times that the animation is played. <br> .value[7].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[8].f32: animation playback speed. <br> |
| NODE_TRANSLATE_TRANSITION | Defines the transition translation attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].f32: translation distance along the x-axis, in vp.<br> value[1].f32: translation distance along the y-axis, in vp.<br> value[2].f32: translation distance along the z-axis, in vp.<br> value[3].i32: animation duration, in milliseconds. <br> value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> value[5]?.i32: animation delay duration, in milliseconds. <br> value[6]?.i32: number of times that the animation is played. <br> value[7]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> value[8]?.f32: animation playback speed. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: translation distance along the x-axis, in vp.<br> value[1].f32: translation distance along the y-axis, in vp.<br> value[2].f32: translation distance along the z-axis, in vp.<br> value[3].i32: animation duration, in milliseconds. <br> value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> value[5].i32: animation delay duration, in milliseconds. <br> value[6].i32: number of times that the animation is played. <br> value[7].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> value[8].f32: animation playback speed. <br> |
| NODE_MOVE_TRANSITION | Defines the slide-in and slide-out of the component from the screen edge during transition.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge). <br> .value[1].i32: animation duration, in milliseconds.<br> .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3]?.i32: animation delay duration, in milliseconds.<br> .value[4]?.i32: number of times that the animation is played.<br> .value[5]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[6]?.f32: animation playback speed.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge). <br> .value[1].i32: animation duration, in milliseconds.<br> .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3].i32: animation delay duration, in milliseconds. <br> .value[4].i32: number of times that the animation is played. <br> .value[5].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[6].f32: animation playback speed. <br> |
| NODE_FOCUSABLE | 获焦属性，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li><b>.value[0].i32</b>：参数类型为1表示可获焦，为0表示不可获焦。默认为不可获焦。</li></ul>**返回：<ul><li><b>.value[0].i32</b>：参数类型为1表示可获焦，为0表示不可获焦。</li></ul> |
| NODE_DEFAULT_FOCUS | 默认焦点属性，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li><b>.value[0].i32</b>：参数值为1表示是默认焦点，为0表示不是默认焦点。</li></ul>**返回：<ul><li><b>.value[0].i32</b>：参数值为1表示是默认焦点，为0表示不是默认焦点。</li></ul> |
| NODE_RESPONSE_REGION | 触摸热区属性，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*说明：<br>设置时data数据大小无数量限制，均可以设置成功，但仅支持获取到前20个。**参数：<ul><li>.data[0].f32</b>：触摸点相对于组件左上角的x轴坐标，单位为vp。</li><li>.data[1].f32</b>：触摸点相对于组件左上角的y轴坐标，单位为vp。</li><li>.data[2].f32</b>：触摸热区的宽度，单位为百分比。</li><li>.data[3].f32</b>：触摸热区的高度，单位为百分比。</li><li>.data[4...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。</li></ul>**返回：<ul><li>.data[0].f32</b>：触摸点相对于组件左上角的x轴坐标，单位为vp。</li><li>.data[1].f32</b>：触摸点相对于组件左上角的y轴坐标，单位为vp。</li><li>.data[2].f32</b>：触摸热区的宽度，单位为百分比。</li><li>.data[3].f32</b>：触摸热区的高度，单位为百分比。</li><li>.data[4...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。</li></ul> |
| NODE_OVERLAY | 定义遮罩属性，支持属性设置，属性重置和属性获取。开发者可以通过如下.string或.object设置浮层内容，.string有更高的优先级。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.string</b>：遮罩文本。</li><li>.value[0]?.i32</b>：可选值，浮层相对于组件的位置，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_TOP_START。</li><li>.value[1]?.f32</b>：可选值，浮层基于自身左上角的偏移量X，单位为vp，默认值为0vp。</li><li>.value[2]?.f32</b>：可选值，浮层基于自身左上角的偏移量Y，单位为vp，默认值为0vp。</li><li>.value[3]?.i32</b>：可选值，浮层的布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_LTR。在大部分场景下，这个参数都应该被设置成Auto，这个模式允许系统自动处理布局方向，如果在某些场景下需要保持特定的方向，设置这个属性为LTR（Left-to-Right）或者RTL（Right-to-Left）。从API version 21开始支持。</li><li>.object</b>：用于overlay的节点树，参数类型为[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)，默认值为nullptr。从API version 21开始支持。</li></ul>**返回：<ul><li>.string</b>：遮罩文本。</li><li>.value[0].i32</b>：浮层相对于组件的位置，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_TOP_START。</li><li>.value[1].f32</b>：浮层基于自身左上角的偏移量X，单位为vp。</li><li>.value[2].f32</b>：浮层基于自身左上角的偏移量Y，单位为vp。</li><li>.value[3].i32</b>：浮层的布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_LTR。从API version 21开始支持。</li><li>.object</b>：用于overlay的节点树，参数类型为[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。从API version 21开始支持。</li></ul> |
| NODE_SWEEP_GRADIENT | Defines the sweep gradient effect.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: X coordinate of the sweep gradient center relative to the upper left corner of the component.<br> .value[1]?.f32: Y coordinate of the sweep gradient center relative to the upper left corner of the component.<br> .value[2]?.f32: start point of the sweep gradient. The default value is <b>0</b>. <br> .value[3]?.f32: end point of the sweep gradient. The default value is <b>0</b>. <br> .value[4]?.f32: rotation angle of the sweep gradient. The default value is <b>0</b>. <br> .value[5]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,and <b>0</b> means the opposite.<br> .object: array of color stops, each of which consists of a color and its stop position. Invalid colors areautomatically skipped.<br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate of the sweep gradient center relative to the upper left corner of the component. <br> .value[1].f32: Y coordinate of the sweep gradient center relative to the upper left corner of the component. <br> .value[2].f32: start point of the sweep gradient. The default value is <b>0</b>. <br> .value[3].f32: end point of the sweep gradient. The default value is <b>0</b>. <br> .value[4].f32: rotation angle of the sweep gradient. The default value is <b>0</b>. <br> .value[5].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,and <b>0</b> means the opposite.<br> .object: array of color stops, each of which consists of a color and its stop position. Invalid colors areautomatically skipped.<br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> |
| NODE_RADIAL_GRADIENT | Defines the radial gradient effect.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0]?.f32: X coordinate of the radial gradient center relative to the upper left corner of the component. <br> .value[1]?.f32: Y coordinate of the radial gradient center relative to the upper left corner of the component. <br> .value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,and <b>0</b> means the opposite. <br> .object: array of color stops, each of which consists of a color and its stop position. Invalid colors areautomatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate of the radial gradient center relative to the upper left corner of the component. <br> .value[1].f32: Y coordinate of the radial gradient center relative to the upper left corner of the component. <br> .value[2].f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,and <b>0</b> means the opposite.<br> .object: array of color stops, each of which consists of a color and its stop position. Invalid colors areautomatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> |
| NODE_MASK | Adds a mask of the specified shape to the component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute, which supports five types ofshapes:<br> 1. Rectangle:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_RECTANGLE</b> for the rectangle shape.<br> .value[4].f32: width of the rectangle.<br> .value[5].f32: height of the rectangle.<br> .value[6].f32: width of the rounded corner of the rectangle.<br> .value[7].f32: height of the rounded corner of the rectangle.<br> .value[8]?.f32: radius of the top left corner of the rectangular shape.<br> .value[9]?.f32: radius of the bottom left corner of the rectangular shape.<br> .value[10]?.f32: radius of the top right corner of the rectangular shape.<br> .value[11]?.f32: radius of the bottom right corner of the rectangular shape.<br> 2. Circle:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_CIRCLE</b> for the circle shape.<br> .value[4].f32: width of the circle.<br> .value[5].f32: height of the circle.<br> 3. Ellipse:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[4].f32: width of the ellipse.<br> .value[5].f32: height of the ellipse.<br> 4. Path:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_PATH</b> for the path shape.<br> .value[4].f32: width of the path.<br> .value[5].f32: height of the path.<br> .string: command for drawing the path.<br> 5. Progress:<br> .value[0].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_PROGRESS</b> for the progress shape.<br> .value[1].f32: current value of the progress indicator.<br> .value[2].f32: maximum value of the progress indicator.<br> .value[3].u32: color of the progress indicator, in 0xARGB format.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md), which supports five types of shapes:<br> 1. Rectangle:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type.<br> .value[4].f32: width of the rectangle.<br> .value[5].f32: height of the rectangle.<br> .value[6].f32: width of the rounded corner of the rectangle.<br> .value[7].f32: height of the rounded corner of the rectangle.<br> .value[8].f32: radius of the top left corner of the rectangular shape.<br> .value[9].f32: radius of the bottom left corner of the rectangular shape.<br> .value[10].f32: radius of the top right corner of the rectangular shape.<br> .value[11].f32: radius of the bottom right corner of the rectangular shape.<br> 2. Circle:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type.<br> .value[4].f32: width of the circle.<br> .value[5].f32: height of the circle.<br> 3. Ellipse:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type.<br> .value[4].f32: width of the ellipse.<br> .value[5].f32: height of the ellipse.<br> 4. Path:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type.<br> .value[4].f32: width of the path.<br> .value[5].f32: height of the path.<br> .string: command for drawing the path.<br> 5. Progress:<br> .value[0].i32: mask type.<br> .value[1].f32: current value of the progress indicator.<br> .value[2].f32: maximum value of the progress indicator.<br> .value[3].u32: color of the progress indicator.<br> |
| NODE_BLEND_MODE | Blends the component's background with the content of the component's child node.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: blend mode. The parameter type is [ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode). The default value is<b>ARKUI_BLEND_MODE_NONE</b>. <br> .value[1].?i32: how the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype).The default value is <b>BLEND_APPLY_TYPE_FAST</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: blend mode. The parameter type is [ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode). The default value is<b>ARKUI_BLEND_MODE_NONE</b>. <br> .value[1].i32: how the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype).The default value is <b>BLEND_APPLY_TYPE_FAST</b>. <br> |
| NODE_DIRECTION | 设置容器元素内主轴方向上的布局，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置容器元素内主轴方向上的布局类型，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：容器元素内主轴方向上的布局类型，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。</li></ul> |
| NODE_CONSTRAINT_SIZE | 约束尺寸属性，组件布局时，进行尺寸范围限制，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置最小宽度，单位vp。</li><li>.value[1].f32：设置最大宽度，单位vp。</li><li>.value[2].f32：设置最小高度，单位vp。</li><li>.value[3].f32：设置最大高度，单位vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：最小宽度，单位vp。</li><li>.value[1].f32：最大宽度，单位vp。</li><li>.value[2].f32：最小高度，单位vp。</li><li>.value[3].f32：最大高度，单位vp。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_GRAY_SCALE | Defines the grayscale effect.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1.For example, 0.5 indicates a 50% grayscale conversion ratio. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1.<br> |
| NODE_INVERT | Inverts the image.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: image inversion ratio. The value ranges from 0 to 1.For example, 0.5 indicates a 50% image inversion ratio.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: image inversion ratio. The value ranges from 0 to 1.<br> |
| NODE_SEPIA | Defines the sepia conversion ratio.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: sepia conversion ratio. The value ranges from 0 to 1.For example, 0.5 indicates that a 50% sepia conversion ratio.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: sepia conversion ratio. The value ranges from 0 to 1.<br> |
| NODE_CONTRAST | Defines the contrast attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: contrast. If the value is <b>1</b>, the source image is displayed.A larger value indicates a higher contrast. Value range: [0, 10).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: contrast. Value range: [0, 10).<br> |
| NODE_FOREGROUND_COLOR | Defines the foreground color attribute, which can be set, reset, and obtained as required through APIs.There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:<br> 1: .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> 2: .value[0].i32: color enum [ArkUI_ColorStrategy](capi-native-type-h.md#arkui_colorstrategy).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format.<br> |
| NODE_OFFSET | 组件子元素相对组件自身的额外偏移属性，支持属性设置，属性重置，属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 设置x轴方向的偏移值, 单位为vp。</li><li>.value[1].f32 设置y轴方向的偏移值, 单位为vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 x轴方向的偏移值, 单位为vp。</li><li>.value[1].f32 y轴方向的偏移值, 单位为vp。</li></ul> |
| NODE_MARK_ANCHOR | 组件子元素在位置定位时的锚点属性，支持属性设置，属性重置，属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 设置锚点x坐标值, 单位为vp。</li><li>.value[1].f32 设置锚点y坐标值, 单位为vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 锚点x坐标值, 单位为vp。</li><li>.value[1].f32 锚点y坐标值, 单位为vp。</li></ul> |
| NODE_BACKGROUND_IMAGE_POSITION | 背景图在组件中显示位置，即相对于组件左上角的坐标，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].f32</b>：x轴位置，单位为px。</li><li>.value[1].f32</b>：y轴位置，单位为px。</li><li>.value[2]?.i32</b>：可选值，对齐方式，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_TOP_START。该参数从API version21开始支持。</li><li>.value[3]?.i32</b>：可选值，布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。多数场景下建议设置为AUTO，由系统自动处理布局方向；若需要固定方向，可设置为LTR或RTL。该参数从API version 21开始支持。</li></ul>**返回：<ul><li>.value[0].f32</b>：x轴位置，单位为px。</li><li>.value[1].f32</b>：y轴位置，单位为px。</li><li>.value[2].i32</b>：对齐方式，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)。该返回值从API version 21开始支持。</li><li>.value[3].i32</b>：布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)。该返回值从API version 21开始支持。</li></ul> |
| NODE_ALIGN_RULES | 相对容器中子组件的对齐规则属性，支持属性设置，属性重置，获取属性接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：设置相对容器中子组件的对齐规则，参数类型为{@link ArkUI_AlignmentRuleOption}。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：相对容器中子组件的对齐规则，参数类型为{@link ArkUI_AlignmentRuleOption}。</li></ul> |
| NODE_ALIGN_SELF | 设置子组件在父容器交叉轴的对齐格式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置子组件在父容器交叉轴的对齐格式类型，参数类型[ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_AUTO。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：子组件在父容器交叉轴的对齐格式类型，参数类型[ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_AUTO。</li></ul> |
| NODE_FLEX_GROW | 设置组件在父容器的剩余空间所占比例，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置父容器的剩余空间所占比例。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：父容器的剩余空间所占比例。</li></ul> |
| NODE_FLEX_SHRINK | 设置父容器压缩尺寸分配给此属性所在组件的比例，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置父容器压缩尺寸分配给此属性所在组件的比例数值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：父容器压缩尺寸分配给此属性所在组件的比例数值。</li></ul> |
| NODE_FLEX_BASIS | 设置组件的基准尺寸，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置组件在父容器主轴方向上的基准尺寸。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：组件在父容器主轴方向上的基准尺寸。</li></ul> |
| NODE_ACCESSIBILITY_GROUP | 无障碍组属性，支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: 为<b>1</b>时表示该组件及其所有子组件为一整个可以选中的组件。</li><li>此时无障碍服务将不再关注其子组件内容。</li><li>参数取值为<b>1</b>或<b>0</b>。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: 为<b>1</b>时表示该组件及其所有子组件为一整个可以选中的组件。</li><li>此时无障碍服务将不再关注其子组件内容。</li><li>参数取值为<b>1</b>或<b>0</b>。</li></ul><br>**起始版本：** 12 |
| NODE_ACCESSIBILITY_TEXT | 无障碍文本属性，支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string: 无障碍文本。</li></ul><br>**起始版本：** 12 |
| NODE_ACCESSIBILITY_MODE | 无障碍辅助服务模式，支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: 辅助服务模式，参数类型为[ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: 辅助服务模式，参数类型为[ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode)。</li></ul><br>**起始版本：** 12 |
| NODE_ACCESSIBILITY_DESCRIPTION | 无障碍说明属性，支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string: 无障碍说明。</li></ul><br>**起始版本：** 12 |
| NODE_FOCUS_STATUS | 组件获取焦点属性，支持属性设置，属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*说明：<br>设置参数为0时，当前层级页面获焦组件失焦，焦点转移到根容器上。**参数：<ul><li>.value[0].i32</b>：参数值为1表示组件获焦，为0表示组件失焦。</li></ul>**返回：<ul><li>.value[0].i32</b>：参数值为1表示组件获焦，为0表示组件失焦。</li></ul> |
| NODE_ASPECT_RATIO | 设置组件的宽高比，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置组件的宽高比，输入值为 width/height。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：组件的宽高比，width/height的比值。</li></ul> |
| NODE_LAYOUT_WEIGHT | Row/Column/Flex 布局下的子组件布局权重参数，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：设置子组件占主轴尺寸的权重。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：子组件占主轴尺寸的权重。</li></ul> |
| NODE_DISPLAY_PRIORITY | Row/Column/Flex(单行) 布局下的子组件在布局容器中显示的优先级。当子组件的displayPriority大于1时，displayPriority数值越大，优先级越高。支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：设置子组件在父容器中的显示优先级。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：子组件在父容器中的显示优先级。</li></ul> |
| NODE_OUTLINE_WIDTH | Sets the thickness of an element's outline.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: thickness of the left outline. <br> .value[1].f32: thickness of the top outline. <br> .value[2].f32: thickness of the right outline. <br> .value[3].f32: thickness of the bottom outline. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: thickness of the left outline. <br> .value[1].f32: thickness of the top outline. <br> .value[2].f32: thickness of the right outline. <br> .value[3].f32: thickness of the bottom outline. <br> |
| NODE_WIDTH_PERCENT | 宽度属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置宽度数值，单位为百分比。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：宽度数值，单位为百分比。</li></ul> |
| NODE_HEIGHT_PERCENT | 高度属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置高度数值，单位为百分比。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：高度数值，单位为百分比。</li></ul> |
| NODE_PADDING_PERCENT | 内间距属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1. 只传入一个参数，表示统一设置上下左右四个位置的内间距百分比数值。<ul><li>.value[0].f32：统一设置上下左右四个位置的内间距数值，单位为百分比。</li></ul>2. 传入四个参数，表示分别设置上下左右四个位置的内间距百分比数值。<ul><li>.value[0].f32：设置上内间距数值，单位为百分比。</li><li>.value[1].f32：设置右内间距数值，单位为百分比。</li><li>.value[2].f32：设置下内间距数值，单位为百分比。</li><li>.value[3].f32：设置左内间距数值，单位为百分比。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：上内间距数值，单位为百分比。</li><li>.value[1].f32：右内间距数值，单位为百分比。</li><li>.value[2].f32：下内间距数值，单位为百分比。</li><li>.value[3].f32：左内间距数值，单位为百分比。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_MARGIN_PERCENT | 外间距属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1. 只传入一个参数，表示统一设置上下左右四个位置的外间距百分比数值。<ul><li>.value[0].f32：统一设置上下左右四个位置的外间距数值，单位为百分比。</li></ul>2. 传入四个参数，表示分别设置上下左右四个位置的外间距百分比数值。<ul><li>.value[0].f32：设置上外间距数值，单位为百分比。</li><li>.value[1].f32：设置右外间距数值，单位为百分比。</li><li>.value[2].f32：设置下外间距数值，单位为百分比。</li><li>.value[3].f32：设置左外间距数值，单位为百分比。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：上外间距数值，单位为百分比。</li><li>.value[1].f32：右外间距数值，单位为百分比。</li><li>.value[2].f32：下外间距数值，单位为百分比。</li><li>.value[3].f32：左外间距数值，单位为百分比。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_GEOMETRY_TRANSITION | The implicit shared element transition within the component supports attribute setting,attribute reset, and attribute acquisition interfaces.Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .value[0]?.i32: The parameter type is 1 or 0. 2 components that share element bindings,Whether to continue to participate in the shared element animation when the appearance element is not deleted,the default is false, and the original position will remain unchanged if not involved. <br> .string is used to set the binding relationship. Set the id to "" toclear the binding relationship to avoid participating in sharing behavior. <br> The id can be changed and the binding relationship re-established.The same ID can only be bound to two components and they are in/out roles of different types.Multiple components cannot be bound to the same id. <br><br> Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .value[0].i32: The parameter type is 1 or 0. 2 components that share element bindings,Whether to continue to participate in the shared element animation when the appearance element is not deleted,the default is not false, if not involved, the original position will remain unchanged. <br> .string is used to set the binding relationship. Set the id to "" toclear the binding relationship to avoid participating in sharing behavior. <br> The id can be changed and the binding relationship re-established.The same ID can only be bound to two components and they are in/out roles of different types.Multiple components cannot be bound to the same id. |
| NODE_RELATIVE_LAYOUT_CHAIN_MODE | 指定以该组件为链头所构成的链的参数，支持属性设置、属性重置和属性获取接口。仅当父容器为RelativeContainer时生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置链的方向。枚举[ArkUI_Axis](capi-native-type-h.md#arkui_axis)。</li><li>.value[1].i32：设置链的样式。枚举{@link ArkUI_RelativeLayoutChainStyle}。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：链的方向。枚举[ArkUI_Axis](capi-native-type-h.md#arkui_axis)。</li><li>.value[1].i32：链的样式。枚举{@link ArkUI_RelativeLayoutChainStyle}。</li></ul> |
| NODE_RENDER_FIT | Set the component content filling method in the process of width and height animation,support property setting, property reset, property acquisition interface.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32 Content filling mode [ArkUI_RenderFit](capi-native-type-h.md#arkui_renderfit).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32 Content filling mode [ArkUI_RenderFit](capi-native-type-h.md#arkui_renderfit).<br> |
| NODE_OUTLINE_COLOR | External stroke color properties, support property setting,property reset and property acquisition interface.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].u32: Set the border color of the four sides uniformly, using 0xargb, such as 0xFFFF11FF. <br> 2: .value[0].u32: Set the top border color, represented by 0xargb, such as 0xFFFF11FF. <br> .value[1].u32: Set the right border color, represented by 0xargb, such as 0xFFFF11FF. <br> .value[2].u32: Set the lower side box color, denoted by 0xargb, such as 0xFFFF11FF. <br> .value[3].u32: Set the left border color, denoted by 0xargb, such as 0xFFFF11FF. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: Set the top border color, represented by 0xargb, such as 0xFFFF11FF. <br> .value[1].u32: Set the right border color, represented by 0xargb, such as 0xFFFF11FF. <br> .value[2].u32: Set the lower side box color, denoted by 0xargb, such as 0xFFFF11FF. <br> .value[3].u32: Set the left border color, denoted by 0xargb, such as 0xFFFF11FF. <br> |
| NODE_SIZE | 设置高宽尺寸，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置宽度数值，单位为vp。</li><li>.value[1].f32：设置高度数值，单位为vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：宽度数值，单位为vp。</li><li>.value[1].f32：高度数值，单位为vp。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_RENDER_GROUP | Set whether the current component and child component arerendered off the screen first and then fused with the parent control,supporting property setting, property reset and property acquisition.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is 1 or 0.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is 1 or 0. |
| NODE_COLOR_BLEND | Add color overlay effect to components, support property setting,property reset and property acquisition interface.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: The color of the overlay is represented by 0xargb, such as 0xFFFF11FF. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: The color of the overlay is represented by 0xargb, such as 0xFFFF11FF. <br> |
| NODE_FOREGROUND_BLUR_STYLE | Provide content ambiguity capability for the current component,support property setting, property reset, property acquisition interface.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32 Represents the content blurring style, and uses the [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle) enumeration value.<br> .value[1]?.i32 Represents the dark and light mode used by the content blur effect,<br> with the [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode) enumeration value.<br> .value[2]?.i32 The color extraction mode used to represent the content blur effect takes<br> the [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor) enumeration value.<br> .value[3]?.f32: blur degree. The value range is [0.0, 1.0]. <br> .value[4]?.f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br> .value[5]?.f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32 Represents the content blurring style, and uses the [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle) enumeration value.<br> .value[1].i32 Represents the dark and light mode used by the content blur effect,<br> with the [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode) enumeration value.<br> .value[2].i32 The color extraction mode used to represent the content blur effect takes<br> the [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor) enumeration value.<br> .value[3].f32: blur degree. The value range is [0.0, 1.0]. <br> .value[4].f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br> .value[5].f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br> |
| NODE_LAYOUT_RECT | 组件布局大小位置属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置组件X轴坐标，单位为px。</li><li>.value[1].i32：设置组件Y轴坐标，单位为px。</li><li>.value[2].i32：设置组件宽度，单位为px。</li><li>.value[3].i32：设置组件高度，单位为px。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：组件X轴坐标，单位为px。</li><li>.value[1].i32：组件Y轴坐标，单位为px。</li><li>.value[2].i32：组件宽度，单位为px。</li><li>.value[3].i32：组件高度，单位为px。</li></ul> |
| NODE_FOCUS_ON_TOUCH | 设置当前组件是否支持点击获焦能力，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].i32：参数值为1表示支持点击获焦，为0表示不支持点击获焦。</li></ul>**返回：<ul><li>.value[0].i32：参数值为1表示支持点击获焦，为0表示不支持点击获焦。</li></ul> |
| NODE_BORDER_WIDTH_PERCENT = 85 | 边框宽度属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1: 只传入一个参数，表示统一设置四条边的边框宽度百分比数值。<ul><li>.value[0].f32：统一设置四条边的边框宽度，单位为百分比。</li></ul>2: 传入四个参数，表示分别设置四条边的边框宽度百分比数值。<ul><li>.value[0].f32：设置上边框的边框宽度，单位为百分比。</li><li>.value[1].f32：设置右边框的边框宽度，单位为百分比。</li><li>.value[2].f32：设置下边框的边框宽度，单位为百分比。</li><li>.value[3].f32：设置左边框的边框宽度，单位为百分比。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：上边框的边框宽度，单位为百分比。</li><li>.value[1].f32：右边框的边框宽度，单位为百分比。</li><li>.value[2].f32：下边框的边框宽度，单位为百分比。</li><li>.value[3].f32：左边框的边框宽度，单位为百分比。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_BORDER_RADIUS_PERCENT = 86 | 边框圆角属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：1: 只传入一个参数，表示统一设置四条边的边框圆角半径百分比数值。<ul><li>.value[0].f32：统一设置四条边的边框圆角半径百分比数值，单位为百分比。</li></ul>2: 传入四个参数，表示分别设置四条边的边框圆角半径百分比数值。<ul><li>.value[0].f32：设置左上角圆角半径，单位为百分比。</li><li>.value[1].f32：设置右上角圆角半径，单位为百分比。</li><li>.value[2].f32：设置左下角圆角半径，单位为百分比。</li><li>.value[3].f32：设置右下角圆角半径，单位为百分比。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：左上角圆角半径，单位为百分比。</li><li>.value[1].f32：右上角圆角半径，单位为百分比。</li><li>.value[2].f32：左下角圆角半径，单位为百分比。</li><li>.value[3].f32：右下角圆角半径，单位为百分比。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_ACCESSIBILITY_ID = 87 | 无障碍自定义标识ID，支持属性获取。**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: 无障碍自定义标识ID。</li></ul><br>**起始版本：** 12 |
| NODE_ACCESSIBILITY_ACTIONS = 88 | 定义无障碍支持操作类型属性，支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32: 配置无障碍操作类型，参数类型为[ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype)。</li></ul><br>**起始版本：** 12 |
| NODE_ACCESSIBILITY_ROLE = 89 | 定义无障碍组件类型属性，支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32: 无障碍组件类型，参数类型为[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)。</li></ul><br>**起始版本：** 12 |
| NODE_ACCESSIBILITY_STATE = 90 | 定义无障碍状态属性，支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object: 参数类型为[ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)。</li></ul><br>**起始版本：** 12 |
| NODE_ACCESSIBILITY_VALUE = 91 | 定义无障碍值属性，支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object: 参数类型为[ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)。</li></ul><br>**起始版本：** 12 |
| NODE_EXPAND_SAFE_AREA = 92 | 定义控制组件扩展其安全区域，支持属性设置，属性重置和属性获取。**属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式：<ul><li>.value[0]?.u32：设置扩展安全区域的枚举值集合[ArkUI_SafeAreaType](capi-native-type-h.md#arkui_safeareatype)，例如：ARKUI_SAFE_AREA_TYPE_SYSTEM \| ARKUI_SAFE_AREA_TYPE_CUTOUT。</li><li>.value[1]?.u32：设置扩展安全区域的方向枚举值集合[ArkUI_SafeAreaEdge](capi-native-type-h.md#arkui_safeareaedge)。例如：ARKUI_SAFE_AREA_EDGE_TOP \| ARKUI_SAFE_AREA_EDGE_BOTTOM。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：扩展安全区域。</li><li>.value[1].u32：扩展安全区域的方向。</li></ul> |
| NODE_VISIBLE_AREA_CHANGE_RATIO = 93 | Defines the visible area ratio (visible area/total area of the component) threshold for invoking thevisible area change event of the component.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting theattribute:<ul><li>.value[...].f32: threshold array. The value ranges from 0 to 1.</li><li>.object: The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[...].f32: threshold array.</li><li>.object: The return type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).</li></ul><br>**起始版本：** 12 |
| NODE_TRANSITION = 94 | Sets the transition effect when the component is inserted or deleted.This attribute can be set, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: transition effect. The parameter type is {@link ArkUI_TransitionEffect}. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: transition effect. The parameter type is {@link ArkUI_TransitionEffect}. <br> |
| NODE_UNIQUE_ID = 95 | Defines the component ID.This attribute can be obtained through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for obtaining the attribute:<br> .value[0].i32: component ID. <br><br>**废弃版本：** 20<br>**替代接口：** OH_ArkUI_NodeUtils_GetNodeUniqueId |
| NODE_FOCUS_BOX = 96 | 设置当前组件系统焦点框样式。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].f32</b>：焦点框相对组件边缘的距离。正数代表外侧，负数代表内侧。不支持百分比。</li><li>.value[1].f32</b>：焦点框宽度。不支持负数和百分比。</li><li>.value[2].u32</b>：焦点框颜色。</li></ul> |
| NODE_CLICK_DISTANCE = 97 | 组件所绑定的点击手势移动距离限制，支持属性设置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].f32</b>：表示识别点击手势时允许手指在该范围内移动，单位为vp。</li></ul> |
| NODE_TAB_STOP = 98 | 控制焦点是否能停在当前组件，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].i32</b>：参数值为1表示焦点能停在当前组件，为0表示焦点不能停在当前组件。默认值为0。</li></ul>**返回：<ul><li>.value[0].i32</b>：参数值为1表示焦点停在当前组件，为0表示焦点未停在当前组件。</li></ul><br>**起始版本：** 14 |
| NODE_BACKDROP_BLUR = 99 | Defines the backdrop blur attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32：backdrop blur radius, in px. The value range is [0, +∞).<br> .value[1]?.f32：grayscale blur settings that control the brightness of the black color.<br> The value range is [0, 127].<br> .value[2]?.f32：grayscale blur settings that control the darkness of the white color.<br> The value range is [0, 127].<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32：backdrop blur radius, in px. The value range is [0, +∞).<br> .value[1].f32：grayscale blur settings that control the brightness of the black color.<br> The value range is [0, 127].<br> .value[2].f32：grayscale blur settings that control the darkness of the white color.<br> The value range is [0, 127].<br><br>**起始版本：** 15 |
| NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE = 100 | Defines the background image resizable attribute, which can be set, reset,and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].f32: width of the left edge. The unit is vp. </li><li>.value[1].f32: width of the top edge. The unit is vp. </li><li>.value[2].f32: width of the right edge. The unit is vp. </li><li>.value[3].f32: width of the bottom edge. The unit is vp.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].f32: width of the left edge. The unit is vp. </li><li>.value[1].f32: width of the top edge. The unit is vp. </li><li>.value[2].f32: width of the right edge. The unit is vp. </li><li>.value[3].f32: width of the bottom edge. The unit is vp. </li></ul><br>**起始版本：** 19 |
| NODE_NEXT_FOCUS = 101 | 设置下一个走焦节点。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].i32</b>：走焦类型，定义在[ArkUI_FocusMove](capi-common-attributes-h.md#arkui_focusmove)。</li><li>.object</b>：下一个焦点。参数类型为[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li></ul><br>**起始版本：** 18 |
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO = 102 | 设置可见区域变化监听的参数。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*说明：<br>非实时回调，实际回调与预期间隔可能存在差别。两次可见区域回调的时间间隔不小于预期更新间隔。当开发者设置的预期间隔过小时，由系统负载决定实际回调间隔时间。当前接口的可见区域回调阈值默认包含0。例如，开发者设置回调阈值为[0.5]，实际生效的阈值为[0.0, 0.5]。**参数：<ul><li>.object</b>：参数类型为[ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)。</li></ul>**返回：<ul><li>.object</b>：参数类型为[ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)。</li></ul><br>**起始版本：** 17 |
| NODE_TRANSLATE_WITH_PERCENT = 103 | Defines the translate attribute, which supports for percentile translation input, and can be set, reset,and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: distance to translate along the x-axis. The default unit is percentage.The unit is vp only if value[3] exists and value[3] is 0. The default value of value[0] is <b>0</b>.<br> .value[1].f32: distance to translate along the y-axis. The default unit is percentage.The unit is vp only if value[4] exists and value[4] is 0. The default value of value[1] is <b>0</b>.<br> .value[2].f32: distance to translate along the z-axis, in vp. The default value is <b>0</b>.<br> .value[3]?.i32: Whether the translation distance along the x-axis is specified as a percentage.The value can be 0 or 1. When the value is 1, it is specified as a percentage.For example, value[0].f32=0.1 and value[3].i32=1 indicates a 10% shift in the x direction.The default value is <b>1</b>.<br> .value[4]?.i32: Whether the translation distance along the y-axis is specified as a percentage.The value can be 0 or 1. When the value is 1, it is specified as a percentage.For example, value[1].f32=0.1 and value[4].i32=1 indicates a 10% shift in the y direction.The default value is <b>1</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: distance to translate along the x-axis. The unit depends on value[3].<br> .value[1].f32: distance to translate along the y-axis. The unit depends on value[4].<br> .value[2].f32: distance to translate along the z-axis. The unit is vp.<br> .value[3].i32: Whether the unit of the X-axis translation distance is in percentage. When value[3].i32 is 0,the unit of the X-axis translation distance is vp; when value[3].i32 is 1, the unit of the X-axis translationdistance is percentage;<br> .value[4].i32: Whether the unit of the Y-axis translation distance is in percentage. When value[4].i32 is 0,the unit of the Y-axis translation distance is vp; when value[4].i32 is 1, the unit of the Y-axis translationdistance is percentage;<br><br>**起始版本：** 20 |
| NODE_ROTATE_ANGLE = 104 | Sets component rotation with multi-axis angle control. This attribute can be set, reset,and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: x-axis rotation angle. The default value is <b>0</b>. <br> .value[1].f32: y-axis rotation angle. The default value is <b>0</b>. <br> .value[2].f32: z-axis rotation angle. The default value is <b>0</b>. <br> .value[3].f32: perspective distance from the viewpoint to the z=0 plane, in px. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: x-axis rotation angle. The default value is <b>0</b>..value[1].f32: y-axis rotation angle. The default value is <b>0</b>. <br> .value[2].f32: z-axis rotation angle. The default value is <b>0</b>. <br> .value[3].f32: perspective distance from the viewpoint to the z=0 plane, in px. The default value is <b>0</b>. <br><br>**起始版本：** 20 |
| NODE_WIDTH_LAYOUTPOLICY = 105 | 设置组件宽度布局策略，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置组件宽度布局策略；参数类型为[ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：组件宽度布局策略；参数类型为[ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy)。</li></ul><br>**起始版本：** 21 |
| NODE_HEIGHT_LAYOUTPOLICY = 106 | 设置组件高度布局策略，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置组件高度布局策略；参数类型为[ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：组件高度布局策略；参数类型为[ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy)。</li></ul><br>**起始版本：** 21 |
| NODE_POSITION_EDGES = 107 | 设置组件相对容器内容区边界的位置，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：设置组件相对容器内容区边界的位置；参数类型为[ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：组件相对容器内容区边界的位置；参数类型为[ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)。</li></ul><br>**起始版本：** 21 |
| NODE_ALLOW_FORCE_DARK = 108 | Set whether the component enables the ability to invert colors.This attribute can be set , and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is 1 or 0.<br><br>**起始版本：** 21 |
| NODE_PIXEL_ROUND = 109 | 设置组件的像素取整策略，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：设置组件的像素取整策略；参数类型为[ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：组件的像素取整策略；参数类型为[ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)。</li></ul><br>**起始版本：** 21 |
| NODE_ENABLE_CLICK_SOUND_EFFECT = 110 | 设置组件是否启用默认点击音效。此功能仅在TV上生效，在其他设备上启用默认点击音效也不会播放音效。是否能够发音依赖设备声音相关的设置，如静音模式下不会播放音效。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].i32</b>：参数取值为1或0，1表示启用默认点击音效，0表示禁用默认点击音效，默认值为1。</li></ul>**返回：<ul><li>.value[0].i32</b>：表示此节点是否启用了默认的点击音效。参数取值为1或0，1表示启用默认点击音效，0表示禁用默认点击音效。</li></ul><br>**起始版本：** 24 |
| NODE_MOTION_PATH = 111 | Defines the motion path attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is[ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is[ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). <br><br>**起始版本：** 23 |
| NODE_HOVER_EFFECT = 112 | 定义组件被悬停时的效果。该属性可根据需要通过API进行设置、重置和获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].i32</b>：组件在悬停状态下的悬停效果。参数类型为[ArkUI_HoverEffect](capi-common-attributes-h.md#arkui_hovereffect)。默认值为ARKUI_HOVER_EFFECT_AUTO。</li></ul>**返回：<ul><li>.value[0].i32</b>：组件在悬停状态下的悬停效果。参数类型为[ArkUI_HoverEffect](capi-common-attributes-h.md#arkui_hovereffect)。</li></ul><br>**起始版本：** 23 |
| NODE_FOCUS_SCOPE_ID = 113 | 将容器设置为具有特定标识符的焦点组，支持属性设置、属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.string</b>：焦点作用域标识符。</li><li>.value[0].i32</b>：该作用域是否为焦点组，默认值为0。取值范围为1或0。1表示设置为焦点组，0表示组件未被设置为焦点组。</li><li>.value[1].i32</b>：箭头键是否可以将焦点从焦点组内部移至外部，仅当isGroup为true时有效，默认值为1。取值范围为1或0。1表示箭头键可以将焦点从焦点组内部移至外部，0表示箭头键无法将焦点从焦点组内部移至外部。</li></ul>**返回：<ul><li>.string</b>：焦点作用域标识符。</li><li>.value[0].i32</b>：该作用域是否为焦点组，默认值为0。取值范围为1或0。1表示设置为焦点组，0表示组件未被设置为焦点组。</li><li>.value[1].i32</b>：箭头键是否可以将焦点从焦点组内部移至外部，仅当isGroup为true时有效，默认值为1。取值范围为1或0。1表示箭头键可以将焦点从焦点组内部移至外部，0表示箭头键无法将焦点从焦点组内部移至外部。</li></ul><br>**起始版本：** 23 |
| NODE_FOCUS_SCOPE_PRIORITY = 114 | 设置组件在特定焦点作用域内的焦点优先级，支持属性设置、属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.string</b>：焦点作用域标识符。</li><li>.value[0].i32</b>：焦点作用域内获焦优先级。参数类型为[ArkUI_FocusPriority](capi-common-attributes-h.md#arkui_focuspriority)。默认值为ARKUI_FOCUS_PRIORITY_AUTO。</li></ul>**返回：<ul><li>.string</b>：焦点作用域标识符。</li><li>.value[0].i32</b>：焦点作用域优先级。参数类型为[ArkUI_FocusPriority](capi-common-attributes-h.md#arkui_focuspriority)。</li></ul><br>**起始版本：** 23 |
| NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD = 115 | 设置点击事件的距离阈值，支持属性设置、属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].f32</b>：点击事件移动阈值。取值范围(0, +∞)。默认值为+∞，单位vp。</li></ul>**返回：<ul><li>.value[0].f32</b>：点击事件移动阈值。</li></ul><br>**起始版本：** 23 |
| NODE_RESPONSE_REGION_LIST = 116 | 设置组件事件的响应区域，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*说明：<br>设置时data数据大小无数量限制，均可以设置成功，但仅支持获取到20个。获取到的data数组顺序与设置顺序可能存在差异。**参数：<ul><li>.data[0].i32</b>：适用于此响应区域的事件工具类型。参数类型为[ArkUI_ResponseRegionSupportedTool](capi-common-attributes-h.md#arkui_responseregionsupportedtool)。默认值：</li><li>ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL。</li><li>.data[1].f32</b>：触摸点相对于组件左上角的x轴坐标，默认值：0.0，单位为vp。</li><li>.data[2].f32</b>：触摸点相对于组件左上角的y轴坐标，默认值：0.0，单位为vp。</li><li>.data[3].f32</b>：触摸热区的宽度，默认值：100.0，单位为百分比。</li><li>.data[4].f32</b>：触摸热区的高度，默认值：100.0，单位为百分比。</li><li>.data[5...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。</li></ul>**返回：<ul><li>.data[0].i32</b>：适用于此响应区域的事件工具类型。参数类型为[ArkUI_ResponseRegionSupportedTool](capi-common-attributes-h.md#arkui_responseregionsupportedtool)。默认值：</li><li>ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL。</li><li>.data[1].f32</b>：触摸点相对于组件左上角的x轴坐标，默认值：0.0，单位为vp。</li><li>.data[2].f32</b>：触摸点相对于组件左上角的y轴坐标，默认值：0.0，单位为vp。</li><li>.data[3].f32</b>：触摸热区的宽度，默认值：100.0，单位为百分比。</li><li>.data[4].f32</b>：触摸热区的高度，默认值：100.0，单位为百分比。</li><li>.data[5...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。</li></ul><br>**起始版本：** 23 |
| NODE_MONOPOLIZE_EVENTS = 117 | 定义独占事件属性，该属性可根据需要通过API进行设置、重置和获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**参数：<ul><li>.value[0].i32</b>：取值范围为1或0。1表示设置组件独占，0表示组件未设置独占属性。</li></ul>**返回：<ul><li>.value[0].i32</b>：取值范围为1或0。1表示设置组件独占，0表示组件未设置独占属性。</li></ul><br>**起始版本：** 23 |
| NODE_CHAIN_WEIGHT = 118 | 父组件为RelativeContainer时，设置已形成链的组件的布局位置，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置组件在水平方向的布局权重，默认值：0。设置异常值时，按默认值显示。</li><li>.value[1].f32：设置组件在竖直方向的布局权重，默认值：0。设置异常值时，按默认值显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：组件在水平方向的布局权重。</li><li>.value[1].f32：组件在竖直方向的布局权重。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。<br>**起始版本：** 23 |
| NODE_IGNORE_LAYOUT_SAFE_AREA = 119 | 设置扩展组件布局时的安全区域，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：设置扩展安全区域的类型。参数类型为[ArkUI_LayoutSafeAreaType](capi-native-type-h.md#arkui_layoutsafeareatype)，默认值：ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM。设置异常值时，按默认值显示。</li><li>.value[1].u32：设置扩展安全区域的方向。参数类型为[ArkUI_LayoutSafeAreaEdge](capi-native-type-h.md#arkui_layoutsafeareaedge)，默认值：ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL。例如：ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_START。设置异常值时，按默认值显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：扩展安全区域的类型。</li><li>.value[1].u32：扩展安全区域的方向。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。<br>**起始版本：** 23 |
| NODE_DASH_WIDTH = 120 | 设置边框样式为虚线时虚线的长度，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置上边框虚线的长度，单位vp。</li><li>.value[1].f32：设置右边框虚线的长度，单位vp。</li><li>.value[2].f32：设置下边框虚线的长度，单位vp。</li><li>.value[3].f32：设置左边框虚线的长度，单位vp。取值范围：[0, +∞)设置异常值时，按默认的虚线效果显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：上边框虚线的长度，单位vp。</li><li>.value[1].f32：右边框虚线的长度，单位vp。</li><li>.value[2].f32：下边框虚线的长度，单位vp。</li><li>.value[3].f32：左边框虚线的长度，单位vp。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。<br>**起始版本：** 23 |
| NODE_DASH_GAP = 121 | 设置边框样式为虚线时虚线的间隙，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置上边框虚线的间隙，单位vp。</li><li>.value[1].f32：设置右边框虚线的间隙，单位vp。</li><li>.value[2].f32：设置下边框虚线的间隙，单位vp。</li><li>.value[3].f32：设置左边框虚线的间隙，单位vp。取值范围：[0, +∞)设置异常值时，按默认的虚线效果显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：上边框虚线的间隙，单位vp。</li><li>.value[1].f32：右边框虚线的间隙，单位vp。</li><li>.value[2].f32：下边框虚线的间隙，单位vp。</li><li>.value[3].f32：左边框虚线的间隙，单位vp。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。<br>**起始版本：** 23 |
| NODE_LAYOUT_GRAVITY = 122 | 设置Stack容器中子组件的对齐规则，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置Stack容器中子组件的对齐规则。参数类型为[ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment)，默认值：ARKUI_ALIGNMENT_CENTER。设置异常值时，按默认值显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：Stack容器中子组件的对齐规则。参数类型为[ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment)。</li></ul><br>**起始版本：** 23 |
| NODE_BORDER_RADIUS_TYPE = 123 | 设置组件绘制圆角的模式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置组件绘制圆角的模式。参数类型为[ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy)，默认值：ARKUI_RENDERSTRATEGY_FAST。设置异常值时，按默认值显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：组件绘制圆角的模式。参数类型为[ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy)。</li></ul><br>**起始版本：** 23 |
| NODE_INSPECTOR_LABEL = 126 | Defines the inspector label attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: inspector label.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: inspector label.<br><br>**起始版本：** 26.0.0 |
| NODE_ACCESSIBILITY_NEXT_FOCUS_ID = 124 | 无障碍下一焦点ID属性，支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string: 无障碍下一焦点ID。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string: 无障碍下一焦点ID。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ACCESSIBILITY_DEFAULT_FOCUS = 125 | 设置无障碍默认焦点标志，用于无障碍服务查找默认焦点组件。支持属性设置，属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: 无障碍默认焦点。为<b>1</b>时表示该组件在无障碍服务中被定义为默认焦点。</li><li>参数取值为<b>1</b>或<b>0</b>。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: 无障碍默认焦点。为<b>1</b>时表示该组件在无障碍服务中被定义为默认焦点。</li><li>参数取值为<b>1</b>或<b>0</b>。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_SYSTEM_MATERIAL = 127 | Defines the system material attribute, which can be set, reset, and obtained as required through APIs.Only devices that support systemMaterial can use this attribute. Otherwise, when setting this attribute,the error code [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) will be returned.Whether a device supports materials can be determined by calling{@link OH_ArkUI_NativeModule_GetSystemMaterialSupported}.The material effect behaves differently on devices with different level of computing powers.The level is defined by {@link ArkUI_MaterialLevel}, which can be obtained by{@link OH_ArkUI_NativeModule_GetGlobalMaterialLevel}.On devices with the computing power level of ARKUI_MATERIAL_LEVEL_SMOOTH, it affects attributes such as thebackgroundColor, borderWidth, borderColor, shadow.On devices with the computing power levels of ARKUI_MATERIAL_LEVEL_EXQUISITE or ARKUI_MATERIAL_LEVEL_GENTLE,it affects shadow attribute and adds a filter effect at the system material layer, which can produce an effectsimilar to glass.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: system material object. The parameter type is {@link ArkUI_ImmersiveMaterialHandle}.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: system material object. The parameter type is {@link ArkUI_ImmersiveMaterialHandle}.<br> The ArkUI_ImmersiveMaterialHandle object of the return value is a pointer to static member, so do not releasethe return object by calling {@link OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy}.<br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT | Text组件设置文本内容属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：表示文本内容。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：表示文本内容。</li></ul> |
| NODE_FONT_COLOR | 组件字体颜色属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：字体颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：字体颜色数值，0xargb格式。</li></ul> |
| NODE_FONT_SIZE | 组件字体大小属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：字体大小数值，单位为fp。取值范围：[0, +∞)。传入负数时参数不生效。默认值：16fp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：字体大小数值，单位为fp。</li></ul> |
| NODE_FONT_STYLE | 组件字体样式属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：字体样式，具体枚举值请参考[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。默认值为ARKUI_FONT_STYLE_NORMAL。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：字体样式[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。</li></ul> |
| NODE_FONT_WEIGHT | 组件字体粗细属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：字体粗细样式[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。取值越大字体越粗。默认值为ARKUI_FONT_WEIGHT_NORMAL。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：字体粗细样式[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。</li></ul> |
| NODE_TEXT_LINE_HEIGHT | 文本行高属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：表示行高值，单位为fp。取值范围：[0, +∞)。传入负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：表示行高值，单位为fp。</li></ul> |
| /** | Defines the text decoration style and color.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype).The default value is <b>ARKUI_TEXT_DECORATION_TYPE_NONE</b>.<br> .value[1]?.u32: text decoration color, in 0xARGB format. For example, 0xFFFF0000 indicates red. Optional.<br> .value[2]?.i32: text decoration style [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype).<br> .value[1].u32: text decoration color, in 0xARGB format. <br> .value[2].i32: text decoration style [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle). <br> |
| NODE_TEXT_DECORATION | 文本装饰线样式及其颜色属性，支持属性设置、属性重置和属性获取接口。适用于添加文本装饰效果，如下划线表示链接、删除线表示已删除内容、或上划线表示强调。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本装饰线类型，具体枚举值请参考[ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype)。默认值为ARKUI_TEXT_DECORATION_TYPE_NONE，无装饰线。</li><li>.value[1]?.u32：可选值，装饰线颜色，0xargb格式，形如 0xFFFF0000 表示红色。默认值：0xFF000000，表示黑色。</li><li>.value[2]?.i32：文本装饰线样式，具体枚举值请参考[ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle)。默认值为ARKUI_TEXT_DECORATION_STYLE_SOLID，实线装饰线。</li><li>.value[3]?.f32：可选值，文本装饰线粗细比例，默认值：1.0，取值范围：[0, +∞)。传入负数时参数不生效。该参数从API version 22开始支持。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本装饰线类型[ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype)。</li><li>.value[1].u32：装饰线颜色，0xargb格式。</li><li>.value[2].i32：文本装饰线样式[ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle)。</li><li>.value[3].f32：文本装饰线粗细比例。该返回值从API version 22开始支持。</li></ul> |
| NODE_TEXT_CASE | 文本大小写属性，支持属性设置、属性重置和属性获取接口。适用于控制文本显示格式，如显示标题时自动大写、或格式化用户输入为统一大小写。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本大小写类型，具体枚举值请参考[ArkUI_TextCase](capi-text-common-h.md#arkui_textcase)。默认值为ARKUI_TEXT_CASE_NORMAL，表示保持原样。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本大小写类型[ArkUI_TextCase](capi-text-common-h.md#arkui_textcase)。</li></ul> |
| NODE_TEXT_LETTER_SPACING | 文本字符间距属性，支持属性设置、属性重置和属性获取接口。适用于调整文本排版效果，如设置标题字符间距以增强视觉效果、或调整特殊文本样式的排版美观度。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：表示字符间距值，单位为fp。取值范围：(-∞, +∞)。当取值为负值时，文字会被压缩。负值过小时会将组件内容区大小压缩为0，导致内容无法显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：表示字符间距值，单位为fp。</li></ul> |
| NODE_TEXT_MAX_LINES | 文本最大行数属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示最大行数，取值范围：[0, +∞)。传入负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示最大行数。</li></ul> |
| NODE_TEXT_ALIGN | 文本水平对齐方式，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本水平对齐方式，具体枚举值请参考[ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment)。默认值为ARKUI_TEXT_ALIGNMENT_START，表示水平对齐首部。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本水平对齐方式，取[ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment)枚举值。</li></ul> |
| NODE_TEXT_OVERFLOW | 文本超长时的显示方式属性，支持属性设置、属性重置和属性获取接口。适用于处理文本内容超出显示区域的场景，如单行标题显示时使用省略号、或卡片内容截断显示等。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本超长时的显示方式，具体枚举值请参考[ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow)。默认值为ARKUI_TEXT_OVERFLOW_NONE，表示文本超长时不裁剪显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本超长时的显示方式[ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow)。</li></ul>说明：支持此属性的[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)为：ARKUI_NODE_TEXT、ARKUI_NODE_TEXT_INPUT、ARKUI_NODE_TEXT_AREA。<br> |
| NODE_FONT_FAMILY | Text字体列表属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：字体字符串，多个字体用英文逗号(,)分隔。不传入时使用系统默认字体。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：字体字符串，多个字体用英文逗号(,)分隔。</li></ul> |
| NODE_TEXT_COPY_OPTION | 文本复制粘贴属性，支持属性设置、属性重置和属性获取接口。适用于控制文本复制粘贴行为，如密码输入框禁止复制、或敏感信息保护。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：复制粘贴方式，具体枚举值请参考[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)。默认值为ARKUI_COPY_OPTIONS_NONE，表示不支持复制。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：复制粘贴方式[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)。</li></ul> |
| NODE_TEXT_BASELINE_OFFSET | 文本基线的偏移量属性，支持属性设置、属性重置和属性获取接口。适用于调整文本基线位置，如显示上下标时调整偏移量、或图文混排时实现文本与图片的精确对齐。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：偏移量数值，单位为fp。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：偏移量数值，单位为fp。</li></ul> |
| NODE_TEXT_TEXT_SHADOW | 文字阴影效果属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：阴影模糊半径，单位为vp。取值范围：[0, +∞)。默认值为0，表示无模糊效果。</li><li>.value[1].i32：阴影类型，具体枚举值请参考[ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype)。默认值为ARKUI_SHADOW_TYPE_COLOR，表示颜色阴影。</li><li>.value[2].u32：阴影颜色，0xargb格式，形如 0xFFFF0000 表示红色。</li><li>.value[3].f32：阴影X轴偏移量，单位为vp。</li><li>.value[4].f32：阴影Y轴偏移量，单位为vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：阴影模糊半径，单位为vp。</li><li>.value[1].i32：阴影类型[ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype)。</li><li>.value[2].u32：阴影颜色，0xargb格式。</li><li>.value[3].f32：阴影X轴偏移量，单位为vp。</li><li>.value[4].f32：阴影Y轴偏移量，单位为vp。</li></ul> |
| NODE_TEXT_MIN_FONT_SIZE | Text最小显示字号，支持属性设置、属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：文本最小显示字号，单位为fp。取值范围：[0, +∞)。传入负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：文本最小显示字号，单位为fp。</li></ul> |
| NODE_TEXT_MAX_FONT_SIZE | Text最大显示字号，支持属性设置、属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：文本最大显示字号，单位为fp。取值范围：[0, +∞)。传入负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：文本最大显示字号，单位为fp。</li></ul> |
| NODE_TEXT_FONT | Text样式，支持属性设置、属性重置和属性获取。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string?：可选值：字体列表，多个字体使用','进行分隔。不传入时使用系统默认字体。</li><li>.value[0].f32：文本尺寸，单位为fp。取值范围：[0, +∞)。传入负数时参数不生效。</li><li>.value[1]?.i32：可选值，文本的字体粗细，具体枚举值请参考[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。取值越大字体越粗。默认值为ARKUI_FONT_WEIGHT_NORMAL。</li><li>.value[2]?.i32：可选值，字体样式，具体枚举值请参考[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。默认值为ARKUI_FONT_STYLE_NORMAL。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：字体列表，使用多个字体，使用','进行分割。</li><li>.value[0].f32：文本尺寸，单位为fp。取值范围：[0, +∞)。</li><li>.value[1].i32：文本的字体粗细，具体枚举值请参考[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。默认值为ARKUI_FONT_WEIGHT_NORMAL。</li><li>.value[2].i32：字体样式，具体枚举值请参考[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。默认值为ARKUI_FONT_STYLE_NORMAL。</li></ul> |
| NODE_TEXT_HEIGHT_ADAPTIVE_POLICY | Text自适应高度的方式，支持属性设置、属性重置和属性获取。适用于文本内容动态变化的场景，如优先按最大行数限制高度、或优先按最小字号确保文本可读性等。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：参数类型，具体枚举值请参考[ArkUI_TextHeightAdaptivePolicy](capi-text-h.md#arkui_textheightadaptivepolicy)。默认值为ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST，表示以MaxLines优先。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：获取的文本自适应高度方式的枚举值，参数类型[ArkUI_TextHeightAdaptivePolicy](capi-text-h.md#arkui_textheightadaptivepolicy)。</li></ul> |
| NODE_TEXT_INDENT | 文本首行缩进属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：表示首行缩进值，入参单位为fp，返回值单位为vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：表示首行缩进值，入参单位为fp，返回值单位为vp。</li></ul> |
| NODE_TEXT_WORD_BREAK | 文本断行规则属性，支持属性设置、属性重置和属性获取接口。适用于控制文本换行方式， <br> 如英文单词完整断行、或中文任意字符断行等不同排版需求。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：参数类型，具体枚举值请参考[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)。默认值为ARKUI_WORD_BREAK_BREAK_WORD，对于Non-CJK的文本可在任意2个字符间断行，一行文本中有断行破发点（如空白符）时，优先按破发点换行。对于CJK的文本，换行效果与NORMAL效果保持一致。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：获取的文本断行规则枚举值，参数类型[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)。</li></ul> |
| NODE_TEXT_ELLIPSIS_MODE | 设置文本省略位置，支持属性设置、属性重置和属性获取接口。适用于控制文本省略号显示位置，如尾部省略适合常规文本、头部省略适合路径显示、中间省略适合长标题等。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：参数类型，具体枚举值请参考[ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode)。默认值为ARKUI_ELLIPSIS_MODE_END，表示省略行末内容。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：获取的文本省略位置枚举值，参数类型[ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode)。</li></ul> |
| NODE_TEXT_LINE_SPACING | 文本行间距属性，支持属性设置、属性重置和属性获取接口。适用于调整多行文本的间距，如优化阅读体验、或实现特定的排版风格效果。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：表示行间距值，单位为fp。取值范围：[0, +∞)。传入负数时参数不生效。</li><li>?.object：可选。指向[OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md)对象的指针，用于设置行间距选项。从API version 26.1.0开始支持。使用[OH_ArkUI_NativeModule_LineSpacingOptions_Create](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_create)创建对象，使用[OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy)销毁对象。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：表示行间距值，单位为fp。</li><li>.object：指向[OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md)对象的指针，用于获取行间距选项。从API version 26.1.0开始支持。</li></ul><br>**起始版本：** 12 |
| NODE_FONT_FEATURE | 设置文本特性效果。NODE_FONT_FEATURE是OpenType字体的高级排版能力，如支持连字、数字等宽等特性，一般用在自定义字体中，其能力需要字体本身支持。支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：符合文本特性格式的字符串，格式为normal \| <feature-tag-value>。 <br> <feature-tag-value>的格式为：string [ <integer> \| on \| off ]。 <br> <feature-tag-value>的个数可以有多个，中间用','隔开，例如，使用等宽数字的输入格式为：ss01 on。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：表示文本特性的内容，多个文本特性之间使用逗号分隔。</li></ul> |
| NODE_TEXT_ENABLE_DATA_DETECTOR | 设置是否使能文本实体识别，识别的实体类型可通过NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG属性配置。适用于识别文本中的特定实体类型（如电话号码、邮箱地址、网址链接等），实现点击跳转、智能交互等功能。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：使能文本识别，1表示文本可实体识别，0表示不可识别。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：使能文本识别。1表示文本可实体识别，0表示不可识别。</li></ul> |
| NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG | 设置文本识别配置。适用于自定义需要识别的实体类型（如电话号码、邮箱地址、网址链接等），实现精准的文本智能识别和交互功能。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0...].i32：实体类型数组，参数类型[ArkUI_TextDataDetectorType](capi-text-h.md#arkui_textdatadetectortype)。数组中可包含电话号码、URL、邮箱等实体类型，具体取值请参考枚举定义。本参数仅在NODE_TEXT_ENABLE_DATA_DETECTOR设置为1（开启文本实体识别）时生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0...].i32：实体类型数组，参数类型[ArkUI_TextDataDetectorType](capi-text-h.md#arkui_textdatadetectortype)。</li></ul> |
| NODE_TEXT_SELECTED_BACKGROUND_COLOR | 文本选中时的背景色属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：颜色数值，0xargb格式。</li></ul> |
| NODE_TEXT_CONTENT_WITH_STYLED_STRING | Text组件使用格式化字符串对象设置文本内容属性，支持属性设置、属性重置和属性获取接口。配置自定义{@link OH_Drawing_Typography}对象到Text组件，会跳过文本控件的布局测算阶段。注意事项：<br> 1. 需要保证OH_ArkUI_StyledString对象、OH_Drawing_Typography对象的生命周期跟随Text组件生命周期，Text组件析构时重置OH_ArkUI_StyledString对象，否则会导致应用出现空指针崩溃。<br> 2. 保证OH_Drawing_TypographyLayout方法调用时序在Text组件的布局测算之前。<br> 3. 释放OH_ArkUI_StyledString对象、OH_Drawing_Typography对象时，需要同步调用Text组件的reset方法，否则会导致应用出现空指针崩溃。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：表示 ArkUI_StyledString 格式化字符串数据，参数类型为{@link ArkUI_StyledString}。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：表示 ArkUI_StyledString 格式化字符串数据，参数类型为{@link ArkUI_StyledString}。</li></ul> |
| NODE_TEXT_HALF_LEADING = 1029 | Text组件设置文本纵向居中显示。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本是否纵向居中显示，默认值：0。<br> 1表示文本是纵向居中显示，0表示文本不是纵向居中显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本是否纵向居中显示。1表示文本纵向居中显示，0表示文本不纵向居中显示。</li></ul> |
| NODE_IMMUTABLE_FONT_WEIGHT = 1030 | 组件字体粗细属性，支持属性设置、属性重置和属性获取接口。通过此接口设置的粗细属性不会跟随系统字体粗细变化。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：字体粗细样式[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。取值越大字体越粗，默认值为ARKUI_FONT_WEIGHT_NORMAL。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：字体粗细样式[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。</li></ul><br>**起始版本：** 15 |
| NODE_TEXT_LINE_COUNT = 1031 | Defines the text line count attribute, which can only be obtained as required through APIs.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: line count of the node.<br>**起始版本：** 20 |
| NODE_TEXT_OPTIMIZE_TRAILING_SPACE = 1032 | 设置文本排版时是否优化每行结尾的空格，支持属性设置、属性重置和属性获取接口。适用于优化文本排版效果，如去除结尾多余空格以实现更好的文本对齐。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置文本排版时是否优化每行结尾的空格，默认值：0。<br> 1表示设置文本排版时优化每行结尾的空格，0表示不优化。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本排版时是否优化每行结尾的空格。1表示已开启优化，0表示未开启优化。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_LINEAR_GRADIENT = 1033 | 设置文本线性渐变效果，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：线性渐变的起始角度，单位为deg。当direction属性设置为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle属性生效； <br> 否则，以direction属性为主要布局方式。0点方向顺时针旋转为正向角度，默认值：180。</li><li>.value[1].i32：线性渐变的方向[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)。设置除ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM之外的线性渐变方向后，angle不生效。 <br> 默认值：ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM。</li><li>.value[2].i32：是否为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。</li><li>colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。</li><li>stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。 <br> 想要实现多个颜色渐变效果时，数组元素建议递增设置，如后一个数组元素比前一个数组元素小的话，按照等于前一个数组元素的值处理。</li><li>size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置大于colors数组长度或小于等于0的值以及异常值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：线性渐变的起始角度。当为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle为设置值，其他情况均为默认值0。</li><li>.value[1].i32：线性渐变的方向[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)。</li><li>.value[2].i32：为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。</li><li>colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。</li><li>stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。</li><li>size：生效后渐变色的颜色个数。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_RADIAL_GRADIENT = 1034 | 设置文本径向渐变效果，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的X轴坐标，单位为vp。默认值：0。</li><li>.value[1]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的Y轴坐标，单位为vp。文本框左上角的坐标为[0,0]。默认值：0。</li><li>.value[2]?.f32：径向渐变的半径，默认值0。取值范围：[0, +∞)。传入负数时参数不生效。</li><li>.value[3]?.i32：是否为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。 <br> colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 <br> stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。 <br> 想要实现多个颜色渐变效果时，数组元素建议递增设置，如后一个数组元素比前一个数组元素小的话，按照等于前一个数组元素的值处理。 <br> size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置大于colors数组长度或小于等于0的值以及异常值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的X轴坐标，单位为vp。</li><li>.value[1]?.f32：为径向渐变的中心点，即相对于当前文本框左上角的Y轴坐标，单位为vp。文本框左上角的坐标为[0,0]。</li><li>.value[2]?.f32：径向渐变的半径，单位为vp。默认值0。</li><li>.value[3]?.i32：为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。 <br> colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 <br> stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。 <br> size：生效后渐变色的颜色个数。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_VERTICAL_ALIGN = 1035 | 设置文本内容垂直对齐方式，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本内容垂直对齐方式[ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment)，默认值：ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本内容垂直对齐方式[ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment)。</li></ul>说明：支持此属性的[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)为：ARKUI_NODE_TEXT。<br><br>**起始版本：** 20 |
| NODE_TEXT_CONTENT_ALIGN = 1036 | 设置文本内容区垂直对齐方式，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本内容垂直对齐方式[ArkUI_TextContentAlign](capi-text-common-h.md#arkui_textcontentalign)，默认值：ARKUI_TEXT_CONTENT_ALIGN_CENTER。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本内容垂直对齐方式[ArkUI_TextContentAlign](capi-text-common-h.md#arkui_textcontentalign)。</li></ul><br>**起始版本：** 21 |
| NODE_TEXT_MIN_LINES = 1037 | 文本最小行数属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本最小行数，取值范围：正整数。传入0或负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本最小行数，取值范围：正整数。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_ENABLE_SELECTED_DATA_DETECTOR = 1038 | 开启选中词的文本实体识别，用于在用户选中文本时识别其中的特定类型数据（如电话号码、邮箱、网址等）。适用于用户选中文本后进行智能识别，如识别选中词的语义类型、实现智能搜索推荐或上下文分析等功能。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：开启选中词文本识别，1表示开启识别，0表示关闭识别。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启选中词文本识别。1表示已开启识别，0表示已关闭识别。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_MIN_LINE_HEIGHT = 1040 | 设置文本最小行高，支持属性设置、属性重置和属性获取接口。适用于限制文本行高的最小值，如确保文本可读性、或防止行高过小导致文字重叠显示。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：文本最小行高，默认值：0。单位为fp。取值范围：[0, +∞)。传入负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：文本最小行高。单位为fp。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_MAX_LINE_HEIGHT = 1041 | 设置文本最大行高，支持属性设置、属性重置和属性获取接口。适用于限制文本行高的最大值，如控制文本布局紧凑度、或防止行高过大导致显示空间浪费。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：文本最大行高，默认值：0，表示最大行高不受限制。单位为fp。取值范围：[0, +∞)。传入负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：文本最大行高。单位为fp。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_LINE_HEIGHT_MULTIPLE = 1042 | 设置倍数行高模式的倍数值，支持属性设置、属性重置和属性获取接口。适用于相对字号设置行高，如实现动态排版、或字号变化时自动调整行高。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：倍数行高模式的倍数值，默认值：0，表示使用默认行高高度。取值范围：[0, +∞)。传入负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：倍数行高模式的倍数值。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_LAYOUT_MANAGER = 1043 | 文本布局管理器，支持属性获取接口。适用于获取文本布局信息，如查询文本行数、字符位置、测量文本尺寸等。**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：文本布局管理器对象，参数类型为{@link ArkUI_TextLayoutManager}。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_EDIT_MENU_OPTIONS = 1044 | 文本菜单扩展项，支持属性设置接口。适用于扩展文本编辑菜单，如添加自定义操作项、或扩展复制粘贴等功能。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：文本菜单扩展项配置数据，参数类型为[ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_BIND_SELECTION_MENU = 1045 | 自定义文本选择菜单，支持属性设置接口。适用于定制文本选择菜单，如添加特定操作按钮、或定制菜单UI风格。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：自定义文本选择菜单配置数据，参数类型为[ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_TEXT_SELECTION = 1046 | 设置文本选择区域，设置后选中区域将被高亮显示，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本选择的起始位置。取值范围：[0, 文本长度]，必须是有效的文本索引。</li><li>.value[1].i32：文本选择的结束位置。取值范围：[0, 文本长度]，必须是有效的文本索引。</li><li>.object：选择选项。参数类型为{@link ArkUI_SelectionOptions}。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本选择的起始位置。</li><li>.value[1].i32：文本选择的结束位置。</li><li>.object：选择选项。参数类型为{@link ArkUI_SelectionOptions}。</li></ul><br>**起始版本：** 23 |
| 	  NODE_TEXT_ORPHAN_CHAR_OPTIMIZATION = 1047 | 设置Text文本排版时是否使能孤字优化，设置后通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局。使能后，它会调整换行点以尽可能避免孤立字符。孤字优化特性需在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否使能孤字优化，1表示使能，0表示不使能。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否使能孤字优化。1表示已使能孤字优化，0表示未使能孤字优化。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_TEXT_COMPRESS_LEADING_PUNCTUATION = 1048 | 文本行首标点压缩开关，支持属性设置、属性重置和属性获取接口。适用于中文排版场景，压缩行首标点以提升排版美观度和阅读体验。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否打开行首标点压缩开关。<br> 1表示开启行首标点压缩，0表示关闭行首标点压缩。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否打开行首标点压缩开关。1表示已开启行首标点压缩，0表示已关闭行首标点压缩。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_INCLUDE_FONT_PADDING = 1049 | 设置是否在首行和尾行增加间距以避免文字截断。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置是否在首行和尾行增加间距以避免文字截断。<br> 1表示开启增加间距，0表示关闭增加间距。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否在首行和尾行增加间距。1表示增加间距，0表示不增加间距。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_FALLBACK_LINE_SPACING = 1050 | 针对多行文字叠加，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：支持行高基于文字实际高度自适应。<br> 1表示开启自适应，0表示关闭自适应。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启行高基于文字实际高度自适应。1表示开启自适应，0表示关闭自适应。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_MARQUEE_OPTIONS = 1051 | 文本跑马灯模式配置项，支持属性设置、属性重置和属性获取接口。适用于长文本滚动显示场景，如通知提醒、标题滚动显示等。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：文本跑马灯模式配置，参数类型为[ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：文本跑马灯模式配置，参数类型为[ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_DIRECTION = 1052 | 文本排版方向。适用于支持不同语言的排版需求，如阿拉伯语、希伯来语等从右向左（RTL）的语言显示。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本的排版方向，取[ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection)枚举值。默认值为ARKUI_TEXT_DIRECTION_DEFAULT，表示文本排版方向遵循组件布局。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示文本的排版方向，对应取值及含义请参考[ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection)枚举值。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_SELECTED_DRAG_PREVIEW_STYLE = 1053 | Used to set the selected drag preview style.Format of the {@link Arkui_AttributeItem} parameter for setting the attribute:<br> .object: selected drag preview style configuration.<br> The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br> <br> Format of the return value {@link Arkui_AttributeItem}:<br> .object: selected drag preview style configuration.<br> The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br><br>**起始版本：** 23 |
| NODE_TEXT_CONTROLLER = 1054 | 设置文本的控制器。适用于管理文本编辑行为，如控制文本显示、管理格式化字符串等。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：文本的控制器，参数类型为[OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md)。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_SPAN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SPAN | 文本内容属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：表示span的文本内容。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：表示span的文本内容。</li></ul> |
| NODE_SPAN_TEXT_BACKGROUND_STYLE | 文本背景色属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：表示文本背景颜色，0xargb格式，形如0xFFFF0000表示红色。</li><li>.value[1].f32：文本背景圆角半径，单位为vp。取值范围：[0, +∞)。传入负数时参数不生效。支持两种设置方式： <br> 1）仅设置.value[1].f32，未设置.value[2].f32~.value[4].f32时，表示四个方向的圆角半径统一设置； <br> 2）设置了.value[2].f32~.value[4].f32中任意项时，.value[1].f32仅表示左上角圆角半径。</li><li>.value[2].f32：设置右上角圆角半径，单位为vp。取值范围：[0, +∞)。传入负数时参数不生效。</li><li>.value[3].f32：设置左下角圆角半径，单位为vp。取值范围：[0, +∞)。传入负数时参数不生效。</li><li>.value[4].f32：设置右下角圆角半径，单位为vp。取值范围：[0, +∞)。传入负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：文本背景颜色，0xargb格式。</li><li>.value[1].f32：左上角圆角半径，单位为vp。</li><li>.value[2].f32：右上角圆角半径，单位为vp。</li><li>.value[3].f32：左下角圆角半径，单位为vp。</li><li>.value[4].f32：右下角圆角半径，单位为vp。</li></ul> |
| NODE_SPAN_BASELINE_OFFSET | 文本基线的偏移量属性，支持属性设置、属性重置和属性获取接口。适用于调整Span文本的基线位置，如显示上下标、或实现特殊排版效果。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：偏移量数值，单位为fp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：偏移量数值，单位为fp。</li></ul> |
| NODE_SPAN_FONT = 2003 | 定义文本样式属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string?：字体列表，多个字体使用`,`进行分割。可选。</li><li>.value[0].f32：文本尺寸，单位为fp。取值范围：[0, +∞)。</li><li>.value[1]?.i32：文本的字体粗细。可选。取值为`[100, 900]`，默认为`400`。取值越大，字体越粗。</li><li>.value[2]?.i32：字体样式。可选。参数类型为[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。默认值为`ARKUI_FONT_STYLE_NORMAL`。</li><li>.object?：字体配置。可选，不设置时使用系统默认配置。参数类型为[OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：字体列表，多个字体使用`,`进行分割。</li><li>.value[0].f32：文本尺寸，单位为fp。取值范围：[0, +∞)。</li><li>.value[1].i32：文本的字体粗细，无单位。取值越大，字体越粗。</li><li>.value[2].i32：字体样式。参数类型为[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。</li><li>.object：字体配置。参数类型为[OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)。</li></ul><br>**起始版本：** 24 |
| NODE_SPAN_FONT_WEIGHT = 2004 | 定义文本字体粗细属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本的字体粗细。取值为`[100, 900]`，默认为`400`。取值越大，字体越粗。超出范围时按默认值400处理。</li><li>.object?：可选，文本字体粗细配置，不设置时使用默认字体粗细配置。参数类型为[OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本字体粗细，无单位。取值越大，字体越粗。</li><li>.object：文本字体粗细配置。参数类型为[OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)。</li></ul><br>**起始版本：** 24 |
| NODE_IMAGE_SPAN_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_SPAN | imageSpan组件图片地址属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：表示imageSpan的图片地址。</li><li>.object：表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。<br> .object参数和.string参数二选一，不可同时设置。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：表示imageSpan的图片地址。</li><li>.object：表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。</li></ul> |
| NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT | 图片基于文本的对齐方式属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示图片基于文本的对齐方式，取[ArkUI_ImageSpanAlignment](capi-image-span-h.md#arkui_imagespanalignment)枚举值。默认值为ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM，图片下边沿与文本下边沿对齐。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：表示图片基于文本的对齐方式，取[ArkUI_ImageSpanAlignment](capi-image-span-h.md#arkui_imagespanalignment)枚举值。</li></ul> |
| NODE_IMAGE_SPAN_ALT | imageSpan组件占位图地址属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：表示imageSpan组件占位图地址（不支持gif类型图源）。</li><li>.object：表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)；<br> .object参数和.string参数二选一，不可同时设置。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：表示imageSpan组件占位图地址。</li><li>.object：表示 PixelMap 图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。</li></ul> |
| NODE_IMAGE_SPAN_BASELINE_OFFSET = 3003 | imageSpan组件的基线偏移量属性，支持属性设置、属性重置和属性获取接口。偏移量数值为正数时向上偏移，负数时向下偏移，默认值0，单位为fp。 <br> 适用于图文混排时调整图片与文本的相对位置，实现精确的排版对齐效果。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：偏移量数值，单位为fp。取值范围：(-∞, +∞)。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：偏移量数值，单位为fp。</li></ul><br>**起始版本：** 13 |
| NODE_IMAGE_SPAN_COLOR_FILTER = 3004 | 图片滤镜效果属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 ~ .value[19].f32：表示5x4颜色滤镜矩阵数组，共20个浮点数元素，按行优先顺序排列。矩阵前4列分别对应红（R）、绿（G）、蓝（B）、透明度（A）通道的颜色变换系数，第5列为各通道的偏移量。用于对图片进行颜色变换处理，如亮度、对比度、色调调整等。</li><li>.size：表示滤镜数组大小为5x4。</li><li>.object：颜色滤波器指针，参数类型为{@link OH_Drawing_ColorFilter}。<br> .object和.size参数只能二选一，不可同时设置。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 ~ .value[19].f32：表示滤镜矩阵数组。</li><li>.size：表示滤镜数组大小为5x4。</li><li>.object：颜色滤波器指针，参数类型为{@link OH_Drawing_ColorFilter}。</li></ul><br>**起始版本：** 22 |
| NODE_IMAGE_SPAN_SUPPORT_SVG2 = 3005 | 通过启用SVG新解析能力开关设置SVG解析功能支持的范围，支持属性设置、属性重置和属性获取接口。ImageSpan组件创建后，不支持动态修改该属性的值。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用SVG新解析能力开关。1表示支持SVG解析新能力；0表示保持原有SVG解析能力。<br> 默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用SVG新解析能力开关。1表示支持SVG解析新能力，0表示保持原有SVG解析能力。</li></ul><br>**起始版本：** 22 |
| NODE_IMAGE_SPAN_RESIZABLE = 3006 | imageSpan组件图片拉伸时，支持通过设置边框大小或者使用矩阵方格对象调整其大小，支持属性设置、属性重置和属性获取接口。接口调用时需要保证设置和获取的参数类型是相同的。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：左边缘宽度，单位为vp。</li><li>.value[1].f32：上边缘宽度，单位为vp。</li><li>.value[2].f32：右边缘宽度，单位为vp。</li><li>.value[3].f32：下边缘宽度，单位为vp。</li><li>.object：参数类型为{@link OH_Drawing_Lattice}。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：左边缘宽度，单位为vp。</li><li>.value[1].f32：上边缘宽度，单位为vp。</li><li>.value[2].f32：右边缘宽度，单位为vp。</li><li>.value[3].f32：下边缘宽度，单位为vp。</li><li>.object：参数类型为{@link OH_Drawing_Lattice}。</li></ul><br>**起始版本：** 26.1.0 |
| NODE_IMAGE_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE | Defines the image source of the <Image> component.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.string: image source.</li><li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either .string or .object must be set.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.string: image source.</li><li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li></ul> |
| NODE_IMAGE_OBJECT_FIT | Defines how the image is resized to fit its container.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: how the image is resized to fit its container. The value is an enum of[ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit).</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: how the image is resized to fit its container. The value is an enum of[ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit).</li></ul> |
| NODE_IMAGE_INTERPOLATION | Defines the interpolation effect of the image.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: interpolation effect of the image. The value is an enum of[ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation).</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: interpolation effect of the image. The value is an enum of[ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation).</li></ul> |
| NODE_IMAGE_OBJECT_REPEAT | Defines how the image is repeated.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: how the image is repeated. The value is an enum of [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat).</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: how the image is repeated. The value is an enum of [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat).</li></ul> |
| NODE_IMAGE_COLOR_FILTER | Defines the color filter of the image.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].f32 to .value[19].f32: filter matrix array.</li><li>.size: 5 x 4 filter array size.</li><li>.object: the pointer to OH_Drawing_ColorFilter. Either .value or .object must be set.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].f32 to .value[19].f32: filter matrix array.</li><li>.size: 5 x 4 filter array size.</li><li>.object: the pointer to OH_Drawing_ColorFilter.</li></ul> |
| NODE_IMAGE_AUTO_RESIZE | Defines the auto resize attribute, which can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether to resize the image source.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether to resize the image source.</li></ul> |
| NODE_IMAGE_ALT | Defines the placeholder image source.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.string: placeholder image source.</li><li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either .string or .object must be set.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.string: placeholder image source.</li><li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li></ul> |
| NODE_IMAGE_DRAGGABLE | Defines whether the image is draggable.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether the image is draggable. The value <b>true</b> means that the image is draggable.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether the image is draggable.</li></ul> |
| NODE_IMAGE_RENDER_MODE | Defines the image rendering mode. This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: The parameter type is [ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode).</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: The parameter type is [ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode).</li></ul> |
| NODE_IMAGE_FIT_ORIGINAL_SIZE | Defines whether the image display size follows the image source size.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether to follow the image source size. The value <b>true</b> means to follow.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether to follow the image source size. The value <b>true</b> means to follow.</li></ul> |
| NODE_IMAGE_FILL_COLOR | Defines the fill color of the image.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].u32: fill color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].u32: fill color, in 0xARGB format.</li></ul> |
| NODE_IMAGE_RESIZABLE | 图片拉伸时，支持通过设置边框大小或者使用矩阵方格对象调整其大小，1）设置边框大小可以设置left/top/right/bottom宽度，2）设置矩阵方格对象：该对象是通过图形侧的接口创建，并将对象地址传入。接口调用时需要保证设置和获取的参数类型是相同的。 |
| NODE_IMAGE_SYNC_LOAD = 4012 | 定义Image是否同步加载这个属性包含设置，重置，获取接口<br>**起始版本：** 20 |
| NODE_IMAGE_SOURCE_SIZE = 4013 | 定义图片的解码尺寸属性。支持属性设置，属性重置和属性获取接口。属性设置方法参数ArkUI_AttributeItem格式：.value[0].i32 表示图片解码的宽，单位px。.value[1].i32 表示图片解码的高，单位px。属性获取方法返回值ArkUI_AttributeItem格式：.value[0].i32 表示图片解码的宽，单位px。.value[1].i32 表示图片解码的高，单位px。<br>**起始版本：** 21 |
| NODE_IMAGE_IMAGE_MATRIX = 4014 | 支持使用浮点数实现仿射图像变换。该属性可以通过API根据需要设置、重置和获取。set和get的参数类型应该是相同的。设置属性[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0....f32表示16个浮点数。<br> 返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)的格式为：<br> .value[0....f32表示16个浮点数。<br><br>**起始版本：** 21 |
| NODE_IMAGE_MATCH_TEXT_DIRECTION = 4015 | Defines the image follow text direction attribute.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether the image follows the text direction.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether the image follows the text direction.</li></ul><br>**起始版本：** 21 |
| NODE_IMAGE_COPY_OPTION = 4016 | 定义图片复制粘贴属性。支持属性设置，属性重置和属性获取接口。属性设置方法参数ArkUI_AttributeItem格式：.value[0].i32：复制粘贴方式ArkUI_CopyOptions，默认值为ARKUI_COPY_OPTIONS_NONE；属性获取方法返回值ArkUI_AttributeItem格式：.value[0].i32：复制粘贴方式ArkUI_CopyOptions。<br>**起始版本：** 21 |
| NODE_IMAGE_ENABLE_ANALYZER = 4017 | Defines the image AI analysis enable attribute.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether to enable AI analysis for the image.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether to enable AI analysis for the image.</li></ul><br>**起始版本：** 21 |
| NODE_IMAGE_DYNAMIC_RANGE_MODE = 4018 | 定义图片显示动态范围属性。支持属性设置，属性重置和属性获取接口。属性设置方法参数ArkUI_AttributeItem格式：.value[0].i32：动态范围类型ArkUI_DynamicRangeMode，默认值为ARKUI_DYNAMIC_RANGE_MODE_STANDARD；属性获取方法返回值ArkUI_AttributeItem格式：.value[0].i32：动态范围类型ArkUI_DynamicRangeMode。<br>**起始版本：** 21 |
| NODE_IMAGE_HDR_BRIGHTNESS = 4019 | 定义图片显示动态范围的亮度属性。支持属性设置，属性重置和属性获取接口。属性设置方法参数ArkUI_AttributeItem格式：.value[0].f32：动态范围亮度，值的范围[0, 1]。属性获取方法返回值ArkUI_AttributeItem格式：.value[0].f32：动态范围亮度，值的范围[0, 1]。<br>**起始版本：** 21 |
| NODE_IMAGE_ORIENTATION = 4020 | 定义图片显示方向属性。支持属性设置，属性重置和属性获取接口。属性设置方法参数ArkUI_AttributeItem格式：.value[0].i32：动态范围类型ArkUI_Orientation，默认值为ARKUI_ORIENTATION_UP；属性获取方法返回值ArkUI_AttributeItem格式：.value[0].i32：动态范围类型ArkUI_Orientation。<br>**起始版本：** 21 |
| NODE_IMAGE_SUPPORT_SVG2 = 4021 | Defines the range of SVG parsing capabilities supported through an enable switch.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: enable switch.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: enable switch.</li></ul><br>**起始版本：** 21 |
| NODE_IMAGE_CONTENT_TRANSITION = 4022 | Set the animation effect for the image content transformation.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).<br><br>**起始版本：** 21 |
| NODE_IMAGE_ALT_PLACEHOLDER = 4023 | Defines the placeholder image during loading process.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.string: placeholder image source.</li><li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either .string or .object must be set.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.string: placeholder image source.</li><li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li></ul><br>**起始版本：** 22 |
| NODE_IMAGE_ALT_ERROR = 4024 | Defines the placeholder image when loading fails.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.string: placeholder image source.</li><li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either .string or .object must be set.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.string: placeholder image source.</li><li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li></ul><br>**起始版本：** 22 |
| NODE_IMAGE_ANTIALIASED = 4025 | 通过开关配置图片边缘抗锯齿使能；true-开启抗锯齿，false-不开启，默认不开启抗锯齿。<br>**起始版本：** 23 |
| NODE_TOGGLE_SELECTED_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE | Defines the color of the component when it is selected.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: background color, in 0xARGB format.</li> <br> </ul> |
| NODE_TOGGLE_SWITCH_POINT_COLOR | Defines the color of the circular slider for the component of the switch type.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: color of the circular slider, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: color of the circular slider, in 0xARGB format.</li> <br> </ul> |
| NODE_TOGGLE_VALUE | Defines the toggle switch value. This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: whether to enable the toggle. The value <b>true</b> means to enable the toggle.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: whether to enable the toggle.</li> <br> </ul> |
| NODE_TOGGLE_UNSELECTED_COLOR | Defines the color of the component when it is deselected.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: background color, in 0xARGB format.</li> <br> </ul> |
| NODE_LOADING_PROGRESS_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LOADING_PROGRESS | 加载进度条前景色属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：前景颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。默认值：跟随主题。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：前景颜色数值，0xargb格式。</li></ul> |
| NODE_LOADING_PROGRESS_ENABLE_LOADING | LoadingProgress动画显示属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：1时不显示动画，1时显示动画。默认值为1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：1时不显示动画，1时显示动画。</li></ul> |
| NODE_TEXT_INPUT_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT | 单行文本输入框的默认提示文本内容属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：默认提示文本的内容。当需要在输入框显示提示信息引导用户输入时设置此属性，例如"请输入用户名"、"请输入密码"等。不设置时输入框无提示文本。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：默认提示文本的内容。</li></ul> |
| NODE_TEXT_INPUT_TEXT | 单行文本输入框的默认文本内容属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：输入框的默认文本内容，用于设置输入框初始显示的文本。当需要在输入框中预置文本时设置此属性，例如表单默认值、编辑初始内容等。不设置时输入框为空。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：默认文本的内容。</li></ul> |
| NODE_TEXT_INPUT_CARET_COLOR | Defines the caret color attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: caret color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: caret color, in 0xARGB format. <br> |
| NODE_TEXT_INPUT_CARET_STYLE | 光标风格属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：光标宽度数值，单位为vp。取值范围：[0, +∞)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：光标宽度数值，单位为vp。</li></ul> |
| NODE_TEXT_INPUT_SHOW_UNDERLINE | 单行文本输入框下划线属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示不展示下划线，1表示展示下划线。默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示不展示下划线，1表示展示下划线。</li></ul> |
| NODE_TEXT_INPUT_MAX_LENGTH | 输入框支持的最大文本数属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：最大文本数，无单位。取值范围：[0, +∞)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：最大文本数，无单位。</li></ul> |
| NODE_TEXT_INPUT_ENTER_KEY_TYPE | 回车键类型属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：回车键类型，具体枚举值请参考[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)。默认值ARKUI_ENTER_KEY_TYPE_DONE，显示为完成样式。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)，用于确定输入框回车键的显示样式。</li></ul> |
| NODE_TEXT_INPUT_PLACEHOLDER_COLOR | Defines the placeholder text color.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_TEXT_INPUT_PLACEHOLDER_FONT | 无输入时默认提示文本的字体配置（包括大小、字重、样式、字体列表）属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0]?.f32：可选字体大小数值，默认值16.0，单位为fp。取值范围：[0, +∞)。传入负数时不生效。</li><li>.value[1]?.i32：可选字体样式，具体枚举值请参考[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。默认值为ARKUI_FONT_STYLE_NORMAL，表示标准字体样式。</li><li>.value[2]?.i32：可选字体粗细样式，具体枚举值请参考[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。默认值ARKUI_FONT_WEIGHT_NORMAL，表示正常字体粗细。</li><li>?.string：字体族内容，多个字体族之间使用逗号分隔，形如“字重；字体族1，字体族2”。不传入时使用系统默认字体族。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：字体大小数值，单位为fp。</li><li>.value[1].i32：字体样式[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。</li><li>.value[2].i32：字体粗细样式[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。</li><li>.string：字体族内容，多个字体族之间使用逗号分隔。</li></ul> |
| NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS | 聚焦时是否绑定输入法属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起，默认值为1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起。</li></ul> |
| NODE_TEXT_INPUT_TYPE | 输入框的类型属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：输入框类型，具体枚举值请参考[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)。默认值为ARKUI_TEXTINPUT_TYPE_NORMAL，表示基本输入模式。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：输入框类型枚举[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)，用于确定输入框的输入内容和键盘样式。</li></ul> |
| NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR | Defines the background color of the selected text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_TEXT_INPUT_SHOW_PASSWORD_ICON | 密码输入模式时是否显示末尾图标属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示不显示图标，1表示显示图标，默认值为0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示不显示图标，1表示显示图标。</li></ul> |
| NODE_TEXT_INPUT_EDITING | 控制单行文本输入框编辑态属性，支持属性设置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示退出编辑态，1表示维持现状。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示退出编辑态，1表示维持现状。</li></ul> |
| NODE_TEXT_INPUT_CANCEL_BUTTON | 单行文本右侧清除按钮样式属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：按钮样式[ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle)，默认值为ARKUI_CANCELBUTTON_STYLE_INPUT，表示清除按钮输入样式。</li><li>.value[1]?.f32：图标大小数值，单位为vp。取值范围：[0, +∞)。传入负数时不生效。不传入时使用系统默认图标大小。</li><li>.value[2]?.u32：按钮图标颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。不传入时使用系统默认图标颜色。</li><li>?.string：按钮图标地址，入参内容为图片本地地址，例如 /pages/icon.png。不传入时使用系统默认清除图标。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：按钮样式[ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle)。</li><li>.value[1].f32：图标大小数值，单位为vp。</li><li>.value[2].u32：按钮图标颜色数值，0xargb格式。</li><li>.string：按钮图标地址。</li></ul> |
| NODE_TEXT_INPUT_TEXT_SELECTION | 组件在获焦状态下，设置文本选中并高亮的区域，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：选中文本的起始位置，取值范围[0, 文本长度]，需小于终止位置才生效。</li><li>.value[1].i32：选中文本的终止位置，取值范围[0, 文本长度]。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：选中文本的起始位置。</li><li>.value[1].i32：选中文本的终止位置。</li></ul> |
| NODE_TEXT_INPUT_UNDERLINE_COLOR | 开启下划线时，支持配置下划线颜色。需先设置NODE_TEXT_INPUT_SHOW_UNDERLINE属性为1以开启下划线后，本属性设置才生效。主题配置的默认下划线颜色为0x33182431，表示深灰色，不透明度为20%。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：typing下划线颜色，必填，表示键入时的下划线颜色，0xargb类型。</li><li>.value[1].u32：normal下划线颜色，必填，表示非特殊状态时下划线颜色，0xargb类型。</li><li>.value[2].u32：error下划线颜色，必填，表示错误时下划线颜色，0xargb类型。</li><li>.value[3].u32：disable下划线颜色，必填，表示禁用时下划线颜色，0xargb类型。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：typing下划线颜色，表示键入时的下划线颜色，0xargb类型。</li><li>.value[1].u32：normal下划线颜色，表示非特殊状态时下划线颜色，0xargb类型。</li><li>.value[2].u32：error下划线颜色，表示错误时下划线颜色，0xargb类型。</li><li>.value[3].u32：disable下划线颜色，表示禁用时下划线颜色，0xargb类型。</li></ul> |
| NODE_TEXT_INPUT_ENABLE_AUTO_FILL | 设置是否启用自动填充。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用自动填充，默认值1。<br> 0表示不启用，1表示启用。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用自动填充。1表示启用，0表示不启用。</li></ul> |
| NODE_TEXT_INPUT_CONTENT_TYPE | 自动填充类型。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：参数类型[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)，用于自动填充场景指定内容类型。具体枚举值及适用场景请参考[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)枚举说明。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：自动填充内容类型枚举[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)，用于确定自动填充的内容类型。</li></ul> |
| NODE_TEXT_INPUT_PASSWORD_RULES | 定义生成密码的规则。在触发自动填充时，所设置的密码规则会透传给密码保险箱，用于新密码的生成。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：定义生成密码的规则，用于在触发自动填充时透传给密码保险箱以控制新密码的生成。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：定义生成密码的规则。</li></ul> |
| NODE_TEXT_INPUT_SELECT_ALL | 设置当初始状态，是否全选文本。不支持内联模式。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否全选文本，默认值：0。<br> 1表示会全选文本，0表示不会全选文本。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否全选文本。1表示会全选文本，0表示不会全选文本。</li></ul> |
| NODE_TEXT_INPUT_INPUT_FILTER | 通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：正则表达式，用于过滤用户输入内容。匹配表达式的输入允许显示，不匹配的输入将被过滤。当需要限制用户只能输入特定格式的字符时设置此属性，例如"^[a-zA-Z]+$"表示只允许字母，"^[0-9]+$"表示只允许数字。不设置时允许所有字符输入。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：正则表达式。</li></ul> |
| NODE_TEXT_INPUT_STYLE | 设置输入框为默认风格或内联输入风格。内联输入风格是一种无边框的嵌入式输入样式，输入框直接融入页面内容中。内联输入风格只支持输入框类型的枚举[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_NORMAL。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：参数类型[ArkUI_TextInputStyle](capi-text-input-h.md#arkui_textinputstyle)。内联输入风格只支持输入框类型[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_NORMAL。默认值为ARKUI_TEXTINPUT_STYLE_DEFAULT。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：输入框样式枚举[ArkUI_TextInputStyle](capi-text-input-h.md#arkui_textinputstyle)，用于确定输入框的显示样式。</li></ul> |
| NODE_TEXT_INPUT_CARET_OFFSET | 设置或获取光标所在位置信息。设置输入光标的位置。返回当前光标所在位置信息。在当前帧更新光标位置同时调用该接口，该接口不生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：从字符串开始到光标所在位置的字符长度，取值范围[0, 文本长度]。超出范围时自动修正为边界值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：光标所在位置的索引值。</li><li>.value[1].f32：光标相对输入框的x坐标值，单位为px。</li><li>.value[2].f32：光标相对输入框的y坐标值，单位为px。</li></ul> |
| NODE_TEXT_INPUT_CONTENT_RECT | 获取已编辑文本内容区域相对组件的位置和大小。**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：水平方向横坐标，单位为px。</li><li>.value[1].f32：竖直方向纵坐标，单位为px。</li><li>.value[2].f32：内容宽度大小，单位为px。</li><li>.value[3].f32：内容高度大小，单位为px。</li></ul> |
| NODE_TEXT_INPUT_CONTENT_LINE_COUNT | Obtains the number of lines of the edited text.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of lines of the edited text. <br> |
| NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN | 设置长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。默认值0。<br> 设置为1时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，隐藏系统文本选择菜单。<br> 设置为0时，显示系统文本选择菜单。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。1表示不弹出菜单，0表示弹出菜单。</li></ul> |
| NODE_TEXT_INPUT_BLUR_ON_SUBMIT | 设置输入框在submit状态下，触发回车键是否失焦。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：触发回车键后是否失焦。默认值1。<br> 0表示不失焦，1表示失焦。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：触发回车键后是否失焦。1表示失焦，0表示不失焦。</li></ul> |
| NODE_TEXT_INPUT_CUSTOM_KEYBOARD | 设置自定义键盘。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li><li>.value[0]?.i32：设置自定义键盘是否支持避让功能，默认值0。<br> 1表示支持避让，0表示不支持避让。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li><li>.value[0].i32：设置自定义键盘是否支持避让功能。0表示不支持避让，1表示支持避让。</li></ul> |
| NODE_TEXT_INPUT_WORD_BREAK | 文本断行规则属性，仅在内联输入风格编辑态生效，支持属性设置，属性重置，属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：参数类型[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)。仅在内联输入风格编辑态生效。默认值ARKUI_WORD_BREAK_BREAK_WORD。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本断行规则枚举[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)，用于确定文本的断行方式。</li></ul> |
| NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS | 设置输入框获取焦点时是否弹出键盘，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否弹出键盘。默认值1。<br> 0表示获取焦点时不弹出键盘，1表示获取焦点时弹出键盘。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否弹出键盘。1表示弹出键盘，0表示不弹出键盘。</li></ul> |
| NODE_TEXT_INPUT_NUMBER_OF_LINES | 设置该属性后，通过该属性计算TextInput组件的高度。例如：设置numberOfLines为3时，组件将默认显示足够容纳3行文本内容的高度。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置行数，取值范围[1, +∞)，用于通过该属性计算TextInput组件的高度。例如：设置为3时，组件将默认显示足够容纳3行文本内容的高度。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置numberOfLines的值。</li></ul> |
| NODE_TEXT_INPUT_LETTER_SPACING = 7032 | Sets the letter spacing of the <b>TextInput</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: letter spacing. The default unit is fp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: letter spacing. The default unit is fp. <br><br>**起始版本：** 15 |
| NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT = 7033 | 设置TextInput组件是否开启输入预上屏。接口支持设置，重置以及获取该属性。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置是否开启输入预上屏。默认值1。<br> 0表示不开启输入预上屏，1表示开启输入预上屏。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：获取是否开启输入预上屏。0表示不开启输入预上屏，1表示开启输入预上屏。</li></ul><br>**起始版本：** 15 |
| NODE_TEXT_INPUT_HALF_LEADING = 7034 | 设置文本将行间距平分至行的顶部与底部。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置文本是否将行间距平分至行的顶部与底部。默认值0。<br> 1表示将行间距平分至行的顶部与底部，0表示不平分。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本行间距是否平分至行的顶部与底部。1表示平分，0表示不平分。</li></ul><br>**起始版本：** 18 |
| NODE_TEXT_INPUT_KEYBOARD_APPEARANCE = 7035 | 设置输入框拉起的键盘样式。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)。具体枚举值请参考ArkUI_KeyboardAppearance枚举说明。默认值ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE，不使用沉浸式样式。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)。具体枚举值请参考ArkUI_KeyboardAppearance枚举说明。默认值ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE。</li></ul><br>**起始版本：** 15 |
| NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036 | 设置是否启用自动填充动效。仅当输入框类型[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_PASSWORD、ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD或ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD时，该动效才生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用自动填充动效。启用之后，仅输入框类型的枚举[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_PASSWORD、ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD或ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD的输入框在进行自动填充时动效可生效。1表示启用，0表示不启用。默认值1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用自动填充动效。0表示不启用，1表示启用。启用之后，仅输入框类型的枚举[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_PASSWORD、ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD或ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD的输入框在进行自动填充时动效可生效。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_INPUT_LINE_HEIGHT = 7037 | 设置输入框文本的高度，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本的高度，单位fp。默认值是自适应字体大小。不传入该参数时，文本的高度设置为5fp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本的高度，单位fp。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR = 7038 | Enables selected data detector.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Enable selected text recognition, default value true.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether selected text recognition is enabled.<br><br>**起始版本：** 22 |
| NODE_TEXT_INPUT_SHOW_COUNTER = 7040 | 设置输入的字符数超过阈值时是否显示计数器并设置计数器样式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启计数器。值为1表示开启计数器，值为0表示不开启计数器。</li><li>.value[1]?.f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]，小数时向下取整，若超出取值范围，则接口属性设置不生效。默认值-1，即始终显示计数器。</li><li>.value[2]?.i32：输入字符超出限制时高亮边框，1表示高亮边框，0表示不高亮边框。默认值1。</li><li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启计数器。0表示不开启计数器，1表示开启计数器。</li><li>.value[1].f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]。</li><li>.value[2].i32：输入字符超出限制时高亮边框。0表示不高亮边框，1表示高亮边框。</li><li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE = 7041 | Used to set or get the text content base controller.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .object: the text content base controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: the text content base controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_ELLIPSIS_MODE = 7042 | Defines the ellipsis position.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode), the default valueis ARKUI_ELLIPSIS_MODE_END. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode). <br><br>**起始版本：** 24 |
| 	  NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION = 7043 | 设置TextInput文本排版时是否使能孤字优化。使能后通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局，调整换行点以尽可能避免孤立字符。注意：该特性需在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否使能孤字优化。该特性需在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。1表示使能，0表示不使能。默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否使能孤字优化。0表示不使能，1表示使能。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION = 7044 | 设置输入字符行首标点压缩开关，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否打开行首标点压缩开关。1表示开启行首标点压缩，0表示关闭行首标点压缩。默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否打开行首标点压缩开关。0表示关闭行首标点压缩，1表示开启行首标点压缩。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_INCLUDE_FONT_PADDING = 7045 | 设置单行输入框内文字是否在首行顶部和尾行底部增加间距以避免文字截断。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置输入框内文字是否在首行顶部和尾行底部增加间距以避免文字截断。1表示开启增加间距，0表示关闭增加间距。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否在首行顶部和尾行底部增加间距。0表示不增加间距，1表示增加间距。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_FALLBACK_LINE_SPACING = 7046 | 针对多行文本显示场景，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。1表示开启自适应，0表示关闭自适应。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启行高基于文字实际高度自适应。0表示关闭自适应，1表示开启自适应。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_DIRECTION = 7047 | Writing direction of the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: writing direction of the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: writing direction the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). <br><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE = 7048 | 用于设置文本输入框内文本选中状态下的拖拽预览样式。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：文本选中状态下的拖拽预览样式。参数类型为[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：文本选中状态下的拖拽预览样式。参数类型为[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_TEXT_OVERFLOW = 7049 | Defines the textinput textOverflow attribute.which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). <br><br>**起始版本：** 24 |
| NODE_TEXT_INPUT_DECORATION = 7050 | 定义单行输入框的文本装饰线样式与颜色，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：装饰样式配置项，为可选参数。参数类型为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)。不传入时不添加装饰线。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：装饰样式配置项。参数类型为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_LINEAR_GRADIENT = 7051 | 设置文本输入框内文本线性渐变效果，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：线性渐变的起始角度，单位为deg。当线性渐变的方向为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)的ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，线性渐变的起始角度属性生效，否则按线性渐变的方向属性为主要布局方式。取值范围为(-∞,+∞)，0点方向顺时针旋转为正向角度，当超过360时，是按照360取余处理，默认值：180。</li><li>.value[1].i32：线性渐变的方向，取值为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)枚举。设置除ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM之外的方向后，起始角度不生效。默认值：ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM。</li><li>.value[2].i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：指定位置处的渐变色颜色，参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。- colors：渐变色颜色数组，元素为0xargb格式，形如0xFFFF0000表示红色。- stops：指定颜色所处位置的数组，取值范围[0,1.0]，0表示容器开始处，1.0表示结尾处。建议递增设置。- size：颜色个数，若小于colors数组长度则仅生效前size个颜色。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：线性渐变的起始角度，单位为deg。当线性渐变的方向为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)的ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，线性渐变的起始角度为设置值，其他情况均为默认值0。</li><li>.value[1].i32：线性渐变的方向。对应取值及含义请参考[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)。</li><li>.value[2].i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。size：生效后渐变色的颜色个数。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_RADIAL_GRADIENT = 7052 | 设置文本输入框的文本径向渐变效果，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0]?.f32：径向渐变的中心点X轴坐标，即相对于当前文本输入框左上角的X轴坐标，单位为vp。默认值为文本输入框宽度的一半。</li><li>.value[1]?.f32：径向渐变的中心点Y轴坐标，即相对于当前文本输入框左上角的Y轴坐标，单位为vp。默认值为文本输入框高度的一半。</li><li>.value[2]?.f32：径向渐变的半径，单位为vp。取值范围[0, +∞)，默认值0。传入负数时不生效。</li><li>.value[3]?.i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。colors：渐变色数组，元素为0xargb格式，形如0xFFFF0000表示红色。stops：指定颜色所处位置的数组，取值范围[0,1.0]，0表示容器开始处，1.0表示结尾处。建议递增设置，若后一元素小于前一元素，则按等于前一元素的值处理。size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置异常值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0]?.f32：径向渐变的中心点X轴坐标，即相对于当前文本输入框左上角的X轴坐标，单位为vp。</li><li>.value[1]?.f32：径向渐变的中心点Y轴坐标，即相对于当前文本输入框左上角的Y轴坐标，单位为vp。</li><li>.value[2]?.f32：径向渐变的半径，单位为vp，默认值0。</li><li>.value[3]?.i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。size：生效后渐变色的颜色个数。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA | Defines the default placeholder text for the multi-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default placeholder text. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default placeholder text. <br> |
| NODE_TEXT_AREA_TEXT | Defines the default text content for the multi-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default text content. <br> <br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.string: default text content.</li> <br> </ul> |
| NODE_TEXT_AREA_MAX_LENGTH | Defines the maximum number of characters in the text input.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: maximum number of characters in the text input. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: maximum number of characters in the text input. <br> |
| NODE_TEXT_AREA_PLACEHOLDER_COLOR | Defines the placeholder text color.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_TEXT_AREA_PLACEHOLDER_FONT | Defines the placeholder text font.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: font size, in fp. Optional. The default value is <b>16.0</b>.<br> .value[1]?.i32: font style [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). Optional. The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.<br> .value[2]?.i32: font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). Optional. The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.<br> ?.string: font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: font size, in fp.<br> .value[1].i32: font style [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).<br> .value[2].i32: font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).<br> .string: font family. Multiple font families are separated by commas (,). <br> |
| NODE_TEXT_AREA_CARET_COLOR | Defines the caret color attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format. <br> |
| NODE_TEXT_AREA_EDITING | 控制多行文本输入框编辑态属性，支持属性设置，属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示退出编辑态，1表示维持现状。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示退出编辑态，1表示维持现状。</li></ul> |
| NODE_TEXT_AREA_TYPE | Defines the text box type. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text box type [ArkUI_TextAreaType](capi-text-area-h.md#arkui_textareatype).The default value is <b>ARKUI_TEXTAREA_TYPE_NORMAL</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text box type [ArkUI_TextAreaType](capi-text-area-h.md#arkui_textareatype). <br> |
| NODE_TEXT_AREA_SHOW_COUNTER | 设置输入的字符数超过阈值时是否显示计数器并设置计数器样式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启计数器。值为1时为开启。默认值0。</li><li>.value[1]?.f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]，小数时向下取整，若超出取值范围，则接口属性设置不生效。默认值-1，即始终显示计数器。</li><li>.value[2]?.i32：输入字符超出限制时是否高亮边框。1表示高亮边框，0表示不高亮边框。默认值1。</li><li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启计数器。0表示不开启计数器，1表示开启计数器。</li><li>.value[1].f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]。</li><li>.value[2].i32：输入字符超出限制时是否高亮边框。0表示不高亮边框，1表示高亮边框。</li><li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li></ul> |
| NODE_TEXT_AREA_SELECTION_MENU_HIDDEN | 设置长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。<br> 设置为1时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，隐藏系统文本选择菜单。<br> 设置为0时，显示系统文本选择菜单。<br> 默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。0表示显示系统文本选择菜单，1表示隐藏系统文本选择菜单。</li></ul> |
| NODE_TEXT_AREA_BLUR_ON_SUBMIT | 设置多行输入框在submit状态下，触发回车键是否失焦。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：触发回车键后是否失焦。<br> 0表示触发回车键后不失焦，1表示触发回车键后失焦。<br> 默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：触发回车键后是否失焦。0表示触发回车键后不失焦，1表示触发回车键后失焦。</li></ul> |
| NODE_TEXT_AREA_INPUT_FILTER | 通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：正则表达式，用于过滤用户输入内容。匹配表达式的输入允许显示，不匹配的输入将被过滤。当需要限制用户只能输入特定格式的字符时设置此属性，例如"^[a-zA-Z]+$"表示只允许字母，"^[0-9]+$"表示只允许数字。不设置时允许所有字符输入。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：正则表达式。</li></ul> |
| NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR | Defines the background color of the selected text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_TEXT_AREA_ENTER_KEY_TYPE | Defines the type of the Enter key.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of the Enter key[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype). The default value is <b>ARKUI_ENTER_KEY_TYPE_DONE</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of the Enter key[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype). <br> |
| NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS | 设置TextArea通过点击以外的方式获焦时，是否绑定输入法，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起。默认值为1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起。</li></ul> |
| NODE_TEXT_AREA_CARET_OFFSET | 设置或获取光标所在位置信息。设置输入光标的位置。返回当前光标所在位置信息。在当前帧更新光标位置同时调用该接口，该接口不生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：从字符串开始到光标所在位置的字符长度，取值范围[0, 文本长度]。超出范围时自动修正为边界值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：光标所在位置的索引值。</li><li>.value[1].f32：光标相对输入框的x坐标位值，单位为px。</li><li>.value[2].f32：光标相对输入框的y坐标位值，单位为px。</li></ul> |
| NODE_TEXT_AREA_CONTENT_RECT | 获取已编辑文本内容区域相对组件的位置和大小。**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：水平方向横坐标，单位为px。</li><li>.value[1].f32：竖直方向纵坐标，单位为px。</li><li>.value[2].f32：内容宽度大小，单位为px。</li><li>.value[3].f32：内容高度大小，单位为px。</li></ul> |
| NODE_TEXT_AREA_CONTENT_LINE_COUNT | Obtains the number of lines of the edited text.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of lines of the edited text. <br> |
| NODE_TEXT_AREA_TEXT_SELECTION | 组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取、高亮显示。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：选中文本的起始位置，取值范围[0, 文本长度]，需小于终止位置才生效。</li><li>.value[1].i32：选中文本的终止位置，取值范围[0, 文本长度]。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：选中文本的起始位置。</li><li>.value[1].i32：选中文本的终止位置。</li></ul> |
| NODE_TEXT_AREA_ENABLE_AUTO_FILL | 设置是否启用自动填充。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用自动填充。<br> 1表示启用，0表示不启用。<br> 默认值1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用自动填充。1表示已启用，0表示未启用。</li></ul> |
| NODE_TEXT_AREA_CONTENT_TYPE | 自动填充类型。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：参数类型[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)。用于指定自动填充的内容类型，以便系统提供更准确的自动填充建议。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：参数类型[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)。用于指定自动填充的内容类型，以便系统提供更准确的自动填充建议。</li></ul> |
| NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS | 设置输入框获取焦点时是否弹出键盘，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：获取焦点时是否弹出键盘。<br> 1表示弹出键盘，0表示不弹出键盘。<br> 默认值1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：获取焦点时是否弹出键盘。1表示弹出键盘，0表示不弹出键盘。</li></ul> |
| NODE_TEXT_AREA_NUMBER_OF_LINES | 设置该属性后，通过该属性计算TextArea组件的高度。例如：设置numberOfLines为3时，组件将默认显示足够容纳3行文本内容的高度。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置行数，取值范围[1, +∞)。用于通过该属性计算TextArea组件的高度。例如：设置为3时，组件将默认显示足够容纳3行文本内容的高度。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置numberOfLines的值。</li></ul> |
| NODE_TEXT_AREA_LETTER_SPACING = 8023 | Sets the letter spacing of the <b>TextArea</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: letter spacing. The default unit is fp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: letter spacing. The default unit is fp. <br><br>**起始版本：** 15 |
| NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024 | 设置TextArea组件是否开启输入预上屏。接口支持设置，重置以及获取该属性。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置是否开启输入预上屏。<br> 0表示不开启输入预上屏，1表示开启输入预上屏。<br> 默认值1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启输入预上屏。1表示已开启，0表示未开启。</li></ul><br>**起始版本：** 15 |
| NODE_TEXT_AREA_HALF_LEADING = 8025 | 设置文本是否将行间距平分至行的顶部与底部。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置文本是否将行间距平分至行的顶部与底部。<br> 1表示将行间距平分至行的顶部与底部，0表示不平分。<br> 默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本行间距是否平分至行的顶部与底部。1表示平分，0表示不平分。</li></ul><br>**起始版本：** 18 |
| NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026 | Set the keyboard style of textAreaFormat of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32：keyboard style，the parameter type is {@link ArkUI_KeyboardAppearanceType}。<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> .value[0].i32：keyboard style，the parameter type is {@link ArkUI_KeyboardAppearanceType}。<br><br>**起始版本：** 15 |
| NODE_TEXT_AREA_MAX_LINES = 8027 | 设置输入框内联模式编辑态时文本可显示的最大行数，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：内联输入风格编辑态时文本可显示的最大行数。取值范围[1, +∞)。<br> 内联模式下，默认值是3，非内联模式下，默认值是+∞，不限制最大行数。<br> 不传入该参数时，使用默认值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：最大行数。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_AREA_LINE_SPACING = 8028 | 设置输入框文本的行间距，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本的行间距，取值范围[0, +∞)，单位为fp。默认值是0。超出范围时自动修正为边界值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本的行间距，单位fp。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_AREA_MIN_LINES = 8029 | 设置节点的最小行数。支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：最小行数，取值范围[1, +∞)。传入0或负数时参数不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：最小行数，取值范围[1, +∞)。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL = 8030 | 设置支持滚动时节点的最大行数。支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：支持滚动时的最大行数。取值范围[1, +∞)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：支持滚动时的最大行数。取值范围[1, +∞)。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_AREA_LINE_HEIGHT = 8031 | 设置输入框文本的高度，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本的高度。默认值是自适应字体大小，单位fp。不传入该参数时，文本的高度设置为5fp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：文本的高度，单位fp。</li></ul><br>**起始版本：** 20 |
| NODE_TEXT_AREA_BAR_STATE = 8032 | Define bar state of the text area.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: bar state of the text area, specified using the [ArkUI_BarState](capi-scroll-h.md#arkui_barstate) enum.The default value is <b>ARKUI_BAR_STATE_AUTO</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: bar state of the text area, specified using the [ArkUI_BarState](capi-scroll-h.md#arkui_barstate) enum. <br><br>**起始版本：** 22 |
| NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR = 8033 | Enables selected data detector.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Enable selected text recognition, default value true.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether selected text recognition is enabled.<br><br>**起始版本：** 22 |
| NODE_TEXT_AREA_SCROLL_BAR_COLOR = 8035 | Defines the color of the scrollbar. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .data[0].u32: color of the scroll bar thumb, in 0xARGB format. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .data[0].u32: color of the scroll bar thumb, in 0xARGB format. <br><br>**起始版本：** 22 |
| NODE_TEXT_AREA_CUSTOM_KEYBOARD = 8036 | 设置文本输入框的自定义键盘。支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li><li>.value[0]?.i32：设置自定义键盘是否支持避让功能，<br> 1表示支持避让，0表示不支持避让。<br> 默认值为0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li><li>.value[0].i32：设置自定义键盘是否支持避让功能。0表示不支持避让，1表示支持避让。</li></ul><br>**起始版本：** 22 |
| NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE = 8037 | Used to set or get the text content base controller.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .object: the text content base controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: the text content base controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br><br>**起始版本：** 23 |
| NODE_TEXT_AREA_ELLIPSIS_MODE = 8038 | Defines the ellipsis position.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode), the default valueis ARKUI_ELLIPSIS_MODE_END. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode). <br><br>**起始版本：** 24 |
| NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION = 8039 | 设置TextArea文本排版时是否使能孤字优化。使能后通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局，调整换行点以尽可能避免孤立字符。注意：该特性需在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否使能孤字优化。该特性需在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。1表示使能，0表示不使能。默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否使能孤字优化。0表示不使能，1表示使能。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION = 8040 | 设置输入字符行首标点压缩开关，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否打开行首标点压缩开关。<br> 1表示开启行首标点压缩，0表示关闭行首标点压缩。默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否打开行首标点压缩开关。0表示关闭行首标点压缩，1表示开启行首标点压缩。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_AREA_INCLUDE_FONT_PADDING = 8041 | 设置多行输入框内文字是否在首行顶部和尾行底部增加间距以避免文字截断。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置输入框内文字是否在首行顶部和尾行底部增加间距以避免文字截断。1表示开启增加间距，0表示关闭增加间距。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否在首行顶部和尾行底部增加间距。0表示不增加间距，1表示增加间距。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_AREA_FALLBACK_LINE_SPACING = 8042 | 针对多行文本显示场景，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。1表示开启自适应，0表示关闭自适应。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启行高基于文字实际高度自适应。0表示关闭自适应，1表示开启自适应。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_AREA_HORIZONTAL_SCROLLING = 8043 | 设置多行输入框在文本宽度超过输入框内容区宽度时是否启用水平滚动。默认值为0，文本会被输入框自动换行。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用水平滚动。1表示启用水平滚动，0表示不启用水平滚动。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用水平滚动。1表示启用水平滚动，0表示不启用水平滚动。</li></ul><br>**起始版本：** 24 |
| NODE_TEXT_AREA_DIRECTION = 8044 | Writing direction of the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: writing direction of the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: writing direction the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). <br><br>**起始版本：** 23 |
| NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE = 8045 | Used to set the selected drag preview style.Format of the {@link Arkui_AttributeItem} parameter for setting the attribute:<br> .object: selected drag preview style configuration. The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br> <br> Format of the return value {@link Arkui_AttributeItem}:<br> .object: selected drag preview style configuration. The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br><br>**起始版本：** 23 |
| NODE_TEXT_AREA_TEXT_OVERFLOW = 8046 | Defines the textarea textOverflow attribute.which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). <br><br>**起始版本：** 24 |
| NODE_TEXT_AREA_DECORATION = 8047 | Defines the text decoration style and color for multi-line text box.This attribute can be set, reset, and obtained as required through APIs.?.object: Optional. The decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).<br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_LINEAR_GRADIENT = 8048 | 设置多行文本输入框的文本线性渐变效果，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：线性渐变的起始角度，单位为deg。当线性渐变的方向为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)的ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，线性渐变的起始角度属性生效，否则按线性渐变的方向属性为主要布局方式。取值范围为(-∞,+∞)，0点方向顺时针旋转为正向角度，当超过360时，是按照360取余处理，默认值：180。</li><li>.value[1].i32：线性渐变的方向，取值为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)枚举。设置除ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM之外的方向后，起始角度不生效。默认值：ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM。</li><li>.value[2].i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：指定位置处的渐变色颜色，参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。<br> - colors：渐变色颜色数组，元素为0xargb格式，形如0xFFFF0000表示红色。<br> - stops：指定颜色所处位置的数组，取值范围[0,1.0]，0表示容器开始处，1.0表示结尾处。建议递增设置。<br> - size：颜色个数，若小于colors数组长度则仅生效前size个颜色。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：线性渐变的起始角度，单位为deg。当线性渐变的方向为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)的ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，线性渐变的起始角度为设置值，其他情况均为默认值0。</li><li>.value[1].i32：线性渐变的方向。对应取值及含义请参考[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)。</li><li>.value[2].i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。<br> colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。<br> stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。<br> size：生效后渐变色的颜色个数。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_RADIAL_GRADIENT = 8049 | 设置多行文本输入框的文本径向渐变效果，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0]?.f32：径向渐变的中心点X轴坐标，即相对于当前多行文本输入框左上角的X轴坐标，单位为vp。默认值为多行文本输入框宽度的一半。</li><li>.value[1]?.f32：径向渐变的中心点Y轴坐标，即相对于当前多行文本输入框左上角的Y轴坐标，单位为vp。默认值为多行文本输入框高度的一半。</li><li>.value[2]?.f32：径向渐变的半径，单位为vp。取值范围[0, +∞)，默认值0。传入负数时不生效。</li><li>.value[3]?.i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。<br> colors：渐变色数组，元素为0xargb格式，形如0xFFFF0000表示红色。<br> stops：指定颜色所处位置的数组，取值范围[0,1.0]，0表示容器开始处，1.0表示结尾处。建议递增设置，若后一元素小于前一元素，则按等于前一元素的值处理。<br> size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置异常值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0]?.f32：径向渐变的中心点X轴坐标，即相对于当前多行文本输入框左上角的X轴坐标，单位为vp。</li><li>.value[1]?.f32：径向渐变的中心点Y轴坐标，即相对于当前多行文本输入框左上角的Y轴坐标，单位为vp。</li><li>.value[2]?.f32：径向渐变的半径，单位为vp，默认值0。</li><li>.value[3]?.i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li><li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。<br> colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。<br> stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。<br> size：生效后渐变色的颜色个数。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_BUTTON_LABEL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_BUTTON | Defines the button text content. This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.string: default text content.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.string: default text content.</li> <br> </ul> |
| NODE_BUTTON_TYPE | Sets the button type. This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype).The default value is <b>ARKUI_BUTTON_TYPE_CAPSULE</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype).The default value is <b>ARKUI_BUTTON_TYPE_CAPSULE</b>.</li> <br> </ul> |
| NODE_BUTTON_MIN_FONT_SCALE | Defines the minimum font scale attribute, which can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].f32: minimum font scale, in fp.</li></ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].f32: minimum font scale, in fp.</li></ul><br>**起始版本：** 18 |
| NODE_BUTTON_MAX_FONT_SCALE | Defines the maximum font scale attribute, which can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].f32: maximum font scale, in fp.</li></ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].f32: maximum font scale, in fp.</li></ul><br>**起始版本：** 18 |
| NODE_PROGRESS_VALUE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PROGRESS | 进度条的当前进度值属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：进度条当前值，取值范围为[0, total]，默认值为0。超出范围时自动修正至有效范围边界值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：进度条当前值，取值范围为[0, total]，默认值为0。</li></ul> |
| NODE_PROGRESS_TOTAL | 进度条的总长属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：进度条总长，取值范围为(0, +∞)，默认值为100，需大于0。传入小于等于0的值时不生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：进度条总长，取值范围为(0, +∞)，默认值为100。</li></ul> |
| NODE_PROGRESS_COLOR | 进度条显示进度值的颜色属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。默认值：跟随主题。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：颜色数值，0xargb格式。</li></ul> |
| NODE_PROGRESS_TYPE | 进度条的类型属性，支持属性设置、属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：进度条类型，具体枚举值及含义参见[ArkUI_ProgressType](capi-progress-h.md#arkui_progresstype)。默认值为ARKUI_PROGRESS_TYPE_LINEAR。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：进度条类型。</li></ul> |
| NODE_PROGRESS_LINEAR_STYLE | 线性进度条样式设置，支持属性设置、属性重置和属性获取接口，如果进度条类型不是线性样式则不生效，需先通过NODE_PROGRESS_TYPE将进度条类型设置为ARKUI_PROGRESS_TYPE_LINEAR。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：使用[ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)对象设置组件样式。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：返回[ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)对象，包含线性进度条的样式信息。</li></ul><br>**起始版本：** 15 |
| NODE_CHECKBOX_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX | Defines whether the check box is selected.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: whether the check box is selected.The value <b>1</b> means that the check box is selected, and <b>0</b> means the opposite.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: The value <b>1</b> means that the check box is selected, and <b>0</b> means the opposite.</li> <br> </ul> |
| NODE_CHECKBOX_SELECT_COLOR | Defines the color of the check box when it is selected.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: color of the check box when it is selected, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: color of the check box when it is selected, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li></ul> |
| NODE_CHECKBOX_UNSELECT_COLOR | Defines the border color of the check box when it is not selected.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li></ul> |
| NODE_CHECKBOX_MARK | Defines the internal icon style of the check box.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li><br> <li>.value[1]?.f32: size of the internal mark, in vp. Optional.</li><br> <li>.value[2]?.f32: stroke width of the internal mark, in vp. Optional. The default value is <b>2</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li><br> <li>.value[1].f32: size of the internal mark, in vp.</li> <br> <li>.value[2].f32: stroke width of the internal mark, in vp. The default value is <b>2</b>.</li> <br> </ul> |
| NODE_CHECKBOX_SHAPE | Defines the shape of the check box.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li></ul> |
| NODE_CHECKBOX_NAME | Defines the name of the checkbox.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.string: component name.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.string: component name.</li> <br> </ul><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP | Defines the name of the checkbox.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.string: component name.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.string: component name.</li> <br> </ul><br>**起始版本：** 15 |
| NODE_XCOMPONENT_ID = MAX_NODE_SCOPE_NUM * ARKUI_NODE_XCOMPONENT | XComponent组件ID属性，支持属性设置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string: ID的内容。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string: ID的内容。</li></ul><br>**起始版本：** 12 |
| NODE_XCOMPONENT_TYPE | XComponent组件的类型，仅支持属性获取接口。XComponent组件的类型需要在组件创建时通过[ARKUI_NODE_XCOMPONENT](capi-native-node-h.md#arkui_nodetype)或[ARKUI_NODE_XCOMPONENT_TEXTURE](capi-native-node-h.md#arkui_nodetype)明确，不允许后续修改。通过[setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)接口尝试修改该类型会导致绘制内容异常。**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: XComponent组件的类型，参数类型为[ArkUI_XComponentType](capi-native-type-h.md#arkui_xcomponenttype)。</li></ul><br>**起始版本：** 12 |
| NODE_XCOMPONENT_SURFACE_SIZE | XComponent组件的宽高，仅支持属性获取接口。通过[setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)接口尝试修改XComponent组件的宽高时设置不会生效。**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32: 宽度数值，单位为px。</li><li>.value[1].u32: 高度数值，单位为px。</li></ul><br>**起始版本：** 12 |
| NODE_XCOMPONENT_SURFACE_RECT | 设置XComponent组件持有Surface的显示区域，支持属性设置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: Surface显示区域相对于XComponent组件左上角的x轴坐标，单位为px。</li><li>.value[1].i32: Surface显示区域相对于XComponent组件左上角的y轴坐标，单位为px。</li><li>.value[2].i32: Surface显示区域的宽度，单位为px。</li><li>.value[3].i32: Surface显示区域的高度，单位为px。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: Surface显示区域相对于XComponent组件左上角的x轴坐标，单位为px。</li><li>.value[1].i32: Surface显示区域相对于XComponent组件左上角的y轴坐标，单位为px。</li><li>.value[2].i32: Surface显示区域的宽度，单位为px。</li><li>.value[3].i32: Surface显示区域的高度，单位为px。</li></ul><br>**起始版本：** 18 |
| NODE_XCOMPONENT_ENABLE_ANALYZER | 设置XComponent组件是否支持图像分析，支持属性设置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: 是否支持图像分析，1表示支持图像分析，0表示不支持图像分析，默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32: 是否支持图像分析，1表示支持图像分析，0表示不支持图像分析，默认值：0。</li></ul><br>**起始版本：** 18 |
| NODE_DATE_PICKER_LUNAR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER | 设置日期选择器组件的日期是否显示农历，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否显示农历，默认值0。0表示不展示农历，1表示展示农历。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否显示农历。返回0表示不展示农历，返回1表示展示农历。</li></ul> |
| NODE_DATE_PICKER_START | 设置日期选择器组件选择器的起始日期，支持属性设置，属性重置和属性获取接口。设置的起始日期会限定日期选择的有效范围，超出范围的选中日期会自动调整。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：日期，默认值"1970-1-1"。格式：年-月-日，年份支持1或4位，月份和日期为1-2位数字。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：设置的起始日期，格式为年-月-日。</li></ul> |
| NODE_DATE_PICKER_END | 设置日期选择器组件选择器的结束日期，支持属性设置，属性重置和属性获取接口。设置的结束日期会限定日期选择的有效范围，超出范围的选中日期会自动调整。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：日期，默认值"2100-12-31"。格式：年-月-日，年份支持1或4位，月份和日期为1-2位数字。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：设置的结束日期，格式为年-月-日。</li></ul> |
| NODE_DATE_PICKER_SELECTED | 设置日期选择器组件选中项的日期，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：日期，默认值"2024-01-22"，未设置时使用默认值。格式：年-月-日，年份支持1或4位，月份和日期为1-2位数字。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：选中的日期，格式为年-月-日。</li></ul> |
| NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE | 设置日期选择器组件的所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1： 文本颜色，#ARGB类型。参数2： 文本大小，数字类型，单位fp。参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4： 文本字体列表，使用 ',' 进行分割。参数5： 文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。</ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1：文本颜色，#argb类型。参数2：文本大小，数字类型，单位fp。参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4：文本字体列表，使用 ',' 进行分割。参数5：文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。</ul> |
| NODE_DATE_PICKER_TEXT_STYLE | 设置日期选择器组件的所有选项中除了边缘项及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1： 文本颜色，#argb类型。参数2： 文本大小，数字类型，单位fp。参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4： 文本字体列表，使用 ',' 进行分割。参数5： 文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。</ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1：文本颜色，#argb类型。参数2：文本大小，数字类型，单位fp。参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4：文本字体列表，使用 ',' 进行分割。参数5：文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。</ul> |
| NODE_DATE_PICKER_SELECTED_TEXT_STYLE | 设置日期选择器组件的选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1： 文本颜色，#argb类型。参数2： 文本大小，数字类型，单位fp。参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4： 文本字体列表，使用 ',' 进行分割。参数5： 文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。</ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1：文本颜色，#argb类型。参数2：文本大小，数字类型，单位fp。参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4：文本字体列表，使用 ',' 进行分割。参数5：文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。</ul> |
| NODE_DATE_PICKER_MODE = 13007 | 设置要显示的日期选项列。DatePicker显示不同样式的日期列，支持属性设置，属性重置和属性获取接口。使用场景：根据应用需求选择合适的日期显示模式，如需要精确选择到日时使用年/月/日模式，只需要月份时使用年/月模式等。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：显示的日期列类型。参数类型[ArkUI_DatePickerMode](capi-native-type-h.md#arkui_datepickermode)。默认值：完整的日期列（年、月、日）。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：当前设置的日期列类型枚举值，类型为[ArkUI_DatePickerMode](capi-native-type-h.md#arkui_datepickermode)。</li></ul><br>**起始版本：** 18 |
| NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK = 13008 | 设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启触控反馈。1表示开启触控反馈，0表示不开启触控反馈。开启后，是否存在触控反馈取决于系统硬件支持情况。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启触控反馈。1表示开启触控反馈，0表示不开启触控反馈。</li></ul><br>**起始版本：** 18 |
| NODE_DATE_PICKER_CAN_LOOP = 13009 | Picker组件可循环滚动属性，支持属性设置，属性重置和属性获取接口。使用场景：循环滚动适用于选项有限且希望提供快速选择体验的场景（如月份选择）；非循环滚动适用于选项有明确边界、需要限制用户选择范围的场景（如日期选择避免跨年混淆）。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否可循环。1表示可循环，0表示不可循环。默认值：1，设置异常值时使用默认值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示不可循环，1表示可循环。</li></ul>说明：可循环情况下，年份随着月份的循环滚动进行联动加减，月份随着日的循环滚动进行联动加减。<br> 不可循环情况下，年/月/日到达本列的顶部或底部时，无法再进行滚动，年/月/日之间也无法再联动加减。<br>**起始版本：** 20 |
|  | 设置时间选择器组件的选中项时间，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：时间。默认值：当前系统时间。设置格式：时:分或时-分（例：23:59或23-59）。返回格式：时,分,秒（例：23,59,0）。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：选中的时间。格式：时,分,秒，使用`,`分隔（例：23,59,0）。</li></ul> |
| NODE_TIME_PICKER_USE_MILITARY_TIME | 设置时间选择组件展示时间是否为24小时制，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否为24小时制，默认值：0。0表示展示时间为12小时制，1表示展示时间为24小时制。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否为24小时制。返回0表示展示时间为12小时制（对应false），返回1表示展示时间为24小时制（对应true）。</li></ul> |
| NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE | 设置边缘项（以选中项为基准向上或向下的第二项）的文本样式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1： 文本颜色，#argb类型。参数2： 文本大小，数字类型，单位fp。参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4： 文本字体列表，使用 ',' 进行分割。参数5： 文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。</ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1：文本颜色，#argb类型。参数2：文本大小，数字类型，单位fp。参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4：文本字体列表，使用 ',' 进行分割。参数5：文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。</ul> |
| NODE_TIME_PICKER_TEXT_STYLE | 设置时间选择组件所有选项中除了边缘项及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1： 文本颜色，#argb类型。参数2： 文本大小，数字类型，单位fp。参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4： 文本字体列表，使用 ',' 进行分割。参数5： 文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。</ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1：文本颜色，#argb类型。参数2：文本大小，数字类型，单位fp。参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4：文本字体列表，使用 ',' 进行分割。参数5：文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。</ul> |
| NODE_TIME_PICKER_SELECTED_TEXT_STYLE | 设置时间选择组件选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1： 文本颜色，#argb类型。参数2： 文本大小，数字类型，单位fp。参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4： 文本字体列表，使用 ',' 进行分割。参数5： 文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。</ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1：文本颜色，#argb类型。参数2：文本大小，数字类型，单位fp。参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4：文本字体列表，使用 ',' 进行分割。参数5：文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。</ul> |
| NODE_TIME_PICKER_START = 14005 | 设置时间选择器组件的起始时间，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：时间。默认值："0:0"。设置时仅支持时:分，使用`:`或`-`分隔（例：12:59或12-59）。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：设置的起始时间。格式：时:分:秒（例：0:0:0）。</li></ul><br>**起始版本：** 18 |
| NODE_TIME_PICKER_END = 14006 | 设置时间选择器组件的结束时间，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：时间。默认值："23:59"。设置时仅支持时:分，使用`:`或`-`分隔（例：23:59或23-59）。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：设置的结束时间。格式：时:分:秒（例：23:59:0）。</li></ul><br>**起始版本：** 18 |
| NODE_TIME_PICKER_ENABLE_CASCADE = 14007 | 在设置12小时制时，上午和下午的标识会根据小时数自动切换，支持属性设置、重置和获取；在24小时制时，该参数不生效。使用场景：适用于需要提供友好的12小时制选择体验的场景，例如用户滚动选择小时时，上午/下午标识自动跟随变化，无需用户手动切换。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：在12小时制时，设置上午和下午的标识是否会根据小时数自动切换，默认值：0。0表示不自动切换，1表示自动切换。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：在12小时制时，上午和下午的标识是否会根据小时数自动切换。返回0表示不自动切换（对应false），返回1表示自动切换（对应true）。</li></ul><br>**起始版本：** 18 |
| NODE_TEXT_PICKER_OPTION_RANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER | 设置滑动选择文本选择器的选择列表，支持属性设置，属性重置和属性获取接口。使用场景：单列选择器适用于单一类别选择（如省份、品牌），多列选择器适用于多个独立类别组合选择（如省-市），多列联动选择器适用于有层级关系的选择场景（如省-市-区，第二列根据第一列自动更新）。需先设置该参数后，才能使用 NODE_TEXT_PICKER_OPTION_SELECTED 和 NODE_TEXT_PICKER_SELECTED_INDEX 设置选中项。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：使用的选择器类型[ArkUI_TextPickerRangeType](capi-native-type-h.md#arkui_textpickerrangetype)，默认值为ARKUI_TEXTPICKER_RANGETYPE_SINGLE。ARKUI_TEXTPICKER_RANGETYPE_SINGLE适用于单列选择，ARKUI_TEXTPICKER_RANGETYPE_MULTI适用于多列独立选择，ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT适用于单列带图片选择，ARKUI_TEXTPICKER_RANGETYPE_CASCADE适用于多列联动选择。</li><li>?.string：针对不同选择器类型有如下输入范式：1：单列选择器，入参格式为用分号分隔的一组字符串；2：多列选择器，支持多对纯文本字符串对，多对之间使用分号分隔，每对内部使用逗号分隔。不传此参数时不设置选择列表。</li><li>?.object：针对不同选择器类型有如下输入范式：1：单列支持图片的选择器，输入结构体为{@link ARKUI_TextPickerRangeContentArray}；2：多列联动选择器，输入结构体为{@link ARKUI_TextCascadePickerRangeContentArray}。不传此参数时不设置选择列表。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：使用的选择器类型[ArkUI_TextPickerRangeType](capi-native-type-h.md#arkui_textpickerrangetype)。</li><li>?.string：针对不同选择器类型有如下输出范式：1：单列选择器，输出格式为用分号分隔的一组字符串；2：多列选择器，输出多对纯文本字符串对，多对之间使用分号分隔，每对内部使用逗号分隔。</li></ul> |
| NODE_TEXT_PICKER_OPTION_SELECTED | 设置滑动选择文本内容的组件默认选中项在数组中的索引值，支持属性设置，属性重置和属性获取接口。需先通过 NODE_TEXT_PICKER_OPTION_RANGE 设置选项列表后才能使用该参数。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：默认选中项在选择器选项数组中的索引值，取值范围为[0, length-1]。超出范围时抛出异常。多列选择器时，如存在多个索引值则逐个添加。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：选中项在选择器选项数组中的索引值，如存在多个索引值则逐个添加。</li></ul> |
| NODE_TEXT_PICKER_OPTION_VALUE | 设置滑动选择文本内容的组件默认选中项的值，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：选中项的值，如存在多个值则逐个添加，用分号分隔。默认值：空字符串，未设置时使用默认值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：选中项的值，如存在多个值则逐个添加，用分号分隔。</li></ul> |
| NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE | 设置滑动选择文本内容的组件所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1： 文本颜色，#argb类型；参数2： 文本大小，数字类型，单位fp；参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")；参数4： 文本字体列表，使用 ',' 进行分割；参数5： 文本样式，字符串枚举("normal", "italic")；如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。</ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1：文本颜色，#argb类型。参数2：文本大小，数字类型，单位fp。参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4：文本字体列表，使用 ',' 进行分割。参数5：文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。</ul> |
| NODE_TEXT_PICKER_TEXT_STYLE | 设置滑动选择文本内容的组件所有选项中除了最上、最下及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1： 文本颜色，#argb类型。参数2： 文本大小，数字类型，单位fp。参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4： 文本字体列表，使用 ',' 进行分割。参数5： 文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。</ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1：文本颜色，#argb类型。参数2：文本大小，数字类型，单位fp。参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4：文本字体列表，使用 ',' 进行分割。参数5：文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。</ul> |
| NODE_TEXT_PICKER_SELECTED_TEXT_STYLE | 设置滑动选择文本内容的组件选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1： 文本颜色，#argb类型；参数2： 文本大小，数字类型，单位fp；参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")；参数4： 文本字体列表，使用 ',' 进行分割；参数5： 文本样式，字符串枚举("normal", "italic")；如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。</ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：参数5个，格式为字符串，以 ';' 分割：</li>参数1：文本颜色，#argb类型。参数2：文本大小，数字类型，单位fp。参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。参数4：文本字体列表，使用 ',' 进行分割。参数5：文本样式，字符串枚举("normal", "italic")。如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。</ul> |
| NODE_TEXT_PICKER_SELECTED_INDEX | 设置滑动选择文本内容的组件默认选中项的索引数组，支持属性设置，属性重置和属性获取接口。需先通过 NODE_TEXT_PICKER_OPTION_RANGE 设置选项列表后才能使用该参数。设置选项列表后，如未通过本参数设置索引数组，则默认选中各列的第1项。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0...].i32：默认选中项在选择器选项数组中的索引值数组。用于多列选择器时设置每列的默认选中项索引。默认值：每列均为0。取值范围：每列索引值为[0, 对应列长度-1]，超出范围时抛出异常。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0...].i32：当前选中的索引值数组，用于多列选择器时表示每列的选中项索引。</li></ul> |
| NODE_TEXT_PICKER_CAN_LOOP | Picker组件可循环滚动属性，支持属性设置，属性重置和属性获取接口。使用场景：循环滚动适用于选项有限且希望提供快速选择体验的场景（如省份选择）；非循环滚动适用于选项有明确边界、需要限制用户选择范围的场景（如数量选择避免误操作）。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示不可循环，1表示可循环。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：0表示不可循环，1表示可循环。</li></ul> |
| NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT | 设置Picker组件各选择项的高度，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：当前设置的选项高度值，单位为vp。默认值：40.0vp，未设置时使用默认值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：当前设置的选项高度值，单位为vp。</li></ul> |
| NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK = 15010 | 设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启触控反馈。1表示开启触控反馈，0表示不开启触控反馈。开启后，是否存在触控反馈取决于系统硬件支持情况。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否开启触控反馈。1表示开启触控反馈，0表示不开启触控反馈。</li></ul><br>**起始版本：** 18 |
| NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE = 15011 | 设置选中项的背景颜色和边框圆角。支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：背景颜色，采用 0xARGB 格式。其中A表示透明度(0x00完全透明~0xFF完全不透明)，RGB表示颜色值(0x000000~0xFFFFFF)，每个字节取值范围0x00~0xFF。例如，0xFF1122FF表示完全不透明的蓝色。</li><li>.value[1].f32：左上角的圆角半径，单位为VP。</li><li>.value[2].f32：右上角的圆角半径，单位为VP。</li><li>.value[3].f32：左下角的圆角半径，单位为VP。</li><li>.value[4].f32：右下角的圆角半径，单位为VP。</li></ul><p>默认值：背景颜色：0x0C182431；圆角半径：24.0。</p>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：背景颜色，采用 0xARGB 格式，例如，<b>0xFF1122FF</b>。</li><li>.value[1].f32：左上角的圆角半径，单位为VP。</li><li>.value[2].f32：右上角的圆角半径，单位为VP。</li><li>.value[3].f32：左下角的圆角半径，单位为VP。</li><li>.value[4].f32：右下角的圆角半径，单位为VP。</li></ul><br>**起始版本：** 20 |
| NODE_CALENDAR_PICKER_HINT_RADIUS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER | 设置日历选中态底板圆角半径的参数，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：日历选中态底板圆角半径，默认值：16.0，单位为vp，表示底板样式为圆形。当输入参数为0.0时表示底板样式为直角矩形；当输入参数为(0.0, 16.0)时，底板样式为圆角矩形；当输入参数为负数或大于16.0时，恢复成默认值16.0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：日历选中态底板圆角半径，默认值：16.0，单位为vp，表示底板样式为圆形。取值范围[0.0, 16.0]，其中取值为0.0表示底板样式为直角矩形。</li></ul> |
| NODE_CALENDAR_PICKER_SELECTED_DATE | 设置日历选择选中日期的参数，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：选中的年。默认值：当前系统年份。传入无效值时使用默认值。</li><li>.value[1].u32：选中的月。默认值：当前系统月份。传入无效值时使用默认值。</li><li>.value[2].u32：选中的日。默认值：当前系统日期。传入无效值时使用默认值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：选中的年。</li><li>.value[1].u32：选中的月。</li><li>.value[2].u32：选中的日。</li></ul> |
| NODE_CALENDAR_PICKER_EDGE_ALIGNMENT | 设置日历选择器与入口组件的对齐方式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：对齐方式类型，参数类型[ArkUI_CalendarAlignment](capi-native-type-h.md#arkui_calendaralignment)。用于设置日历选择器相对入口组件的对齐位置。</li><li>.value[1]?.f32：按照对齐方式对齐后，选择器相对入口组件的x轴方向相对偏移，单位为vp。默认值：0。</li><li>.value[2]?.f32：按照对齐方式对齐后，选择器相对入口组件的y轴方向相对偏移，单位为vp。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：对齐方式类型，参数类型[ArkUI_CalendarAlignment](capi-native-type-h.md#arkui_calendaralignment)。</li><li>.value[1].f32：按照对齐方式对齐后，选择器相对入口组件的x轴方向相对偏移。</li><li>.value[2].f32：按照对齐方式对齐后，选择器相对入口组件的y轴方向相对偏移。</li></ul> |
| NODE_CALENDAR_PICKER_TEXT_STYLE | 设置日历选择器入口区的文本颜色、字号、字体粗细。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0]?.u32：入口区的文本颜色。未设置或执行resetAttribute后，使用系统主题`calendar_picker_entry_font_color` 解析的值（具体色值随主题变化，可通过getAttribute获取）。</li><li>.value[1]?.f32：入口区的文本字号，单位为fp。未设置或执行resetAttribute后，使用系统主题`calendar_picker_entry_font_size` 解析的值（具体数值随主题变化，可通过getAttribute获取）。</li><li>.value[2]?.i32：入口区的文本字体粗细，参数类型[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。未设置或执行resetAttribute后，默认值为ARKUI_FONT_WEIGHT_NORMAL。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：入口区的文本颜色。</li><li>.value[1].f32：入口区的文本字号，单位为fp。</li><li>.value[2].i32：入口区的文本字体粗细，参数类型[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。</li></ul> |
| NODE_CALENDAR_PICKER_START = 16004 | 设置日历选择器的开始日期，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：日期。格式：年-月-日，年份支持1或4位，月份和日期为1-2位数字，如"1970-1-1"、"2024-05-20"。默认值：1970-1-1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：设置的日历选择器开始日期，格式为年-月-日。</li></ul><br>**起始版本：** 18 |
| NODE_CALENDAR_PICKER_END = 16005 | 设置日历选择器的结束日期，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：日期。格式：年-月-日，年份支持1或4位，月份和日期为1-2位数字，如"2100-12-31"、"2025-1-25"。默认值："2100-12-31"。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：设置的日历选择器结束日期，格式为年-月-日。</li></ul><br>**起始版本：** 18 |
| NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE = 16006 | 设置日历选择器的禁用日期区间，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：禁用日期区间字符串。禁用日期区间："第一个区间开始日期,第一个区间结束日期,第二个区间开始日期,第二个区间结束日期,...,第n个区间开始日期,第n个区间结束日期"。设置的禁用日期区间格式："1910-01-01,1910-12-31,2020-01-01,2020-12-31"。默认值：空字符串，表示不设置禁用日期区间。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string：设置的禁用日期区间字符串，格式为"开始日期,结束日期,..."，如"1910-01-01,1910-12-31"。</li></ul><br>**起始版本：** 19 |
| NODE_CALENDAR_PICKER_MARK_TODAY = 16007 | 设置日历选择器在系统当前日期时，是否保持高亮显示，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：日历选择器在系统当前日期时，是否保持高亮显示。返回0表示不保持高亮显示，返回1表示保持高亮显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：日历选择器在系统当前日期时，是否保持高亮显示。</li></ul><br>**起始版本：** 19 |
| NODE_SLIDER_BLOCK_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER | Defines the color of the slider. This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: color of the slider, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li></ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: color of the slider, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li></ul> |
| NODE_SLIDER_TRACK_COLOR | Defines the background color of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li></ul> |
| NODE_SLIDER_SELECTED_COLOR | Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtainedas required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li></ul> |
| NODE_SLIDER_SHOW_STEPS | Sets whether to display the stepping value. This attribute can be set, reset, and obtained as requiredthrough APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: whether to display the stepping value. The value <b>1</b> means to display the stepping value,and <b>0</b> (default value) means the opposite.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: whether to display the stepping value. The value <b>1</b> means to display the stepping value,and <b>0</b> (default value) means the opposite.</li> <br> </ul> |
| NODE_SLIDER_BLOCK_STYLE | Defines the slider shape, which can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).</li> <br> <li>.string?: depending on the shape. Optional.</li> <br> </ul>ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png. <br> ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider. <br> There are five types:<br> 1. Rectangle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape.<br> .value[2].f32: width of the rectangle.<br> .value[3].f32: height of the rectangle.<br> .value[4].f32: width of the rounded corner of the rectangle.<br> .value[5].f32: height of the rounded corner of the rectangle.<br> 2. Circle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape.<br> .value[2].f32: width of the circle.<br> .value[3].f32: height of the circle.<br> 3.Ellipse:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[2].f32: width of the ellipse.<br> .value[3].f32: height of the ellipse;<br> 4. Path:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape.<br> .value[2].f32: width of the path.<br> .value[3].f32: height of the path.<br> .string: command for drawing the path.<br> <br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).</li> <br> <li>.string?: depending on the shape. Optional.</li> <br> </ul>ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png. <br> ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider. <br> There are five types:<br> 1. Rectangle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape.<br> .value[2].f32: width of the rectangle.<br> .value[3].f32: height of the rectangle.<br> .value[4].f32: width of the rounded corner of the rectangle.<br> .value[5].f32: height of the rounded corner of the rectangle.<br> 2. Circle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape.<br> .value[2].f32: width of the circle.<br> .value[3].f32: height of the circle.<br> 3.Ellipse:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[2].f32: width of the ellipse.<br> .value[3].f32: height of the ellipse;<br> 4. Path:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape.<br> .value[2].f32: width of the path.<br> .value[3].f32: height of the path.<br> .string: command for drawing the path.<br> |
| NODE_SLIDER_VALUE | Defines the current value of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].f32: current value.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].f32: current value.</li></ul> |
| NODE_SLIDER_MIN_VALUE | Defines the minimum value of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].f32: minimum value.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].f32: minimum value.</li></ul> |
| NODE_SLIDER_MAX_VALUE | Defines the maximum value of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].f32: maximum value.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].f32: maximum value.</li></ul> |
| NODE_SLIDER_STEP | Defines the step of the slider. This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].f32: step. The value range is [0.01, 100].</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].f32: step. The value range is [0.01, 100].</li></ul> |
| NODE_SLIDER_DIRECTION | Defines whether the slider moves horizontally or vertically. This attribute can be set, reset, andobtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: whether the slider moves horizontally or vertically.The parameter type is [ArkUI_SliderDirection](capi-slider-h.md#arkui_sliderdirection).</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: whether the slider moves horizontally or vertically.</li></ul> |
| NODE_SLIDER_REVERSE | Defines whether the slider values are reversed. This attribute can be set, reset, and obtained as requiredthrough APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: whether the slider values are reversed. The value <b>1</b> means that the slider values arereversed, and <b>0</b> means the opposite.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: whether the slider values are reversed. The value <b>1</b> means that the slider values arereversed, and <b>0</b> means the opposite.</li></ul> |
| NODE_SLIDER_STYLE | Defines the style of the slider thumb and track. This attribute can be set, reset, and obtainedas required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: style of the slider thumb and track. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle).</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: style of the slider thumb and track. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle).</li></ul> |
| NODE_SLIDER_TRACK_THICKNESS | Sets the track thickness of the slider.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].f32: track thickness of the slider, in vp. The default value is 4.0 vp when <b>NODE_SLIDER_STYLE</b>is set to <b>ARKUI_SLIDER_STYLE_OUT_SET</b> and 20.0 vp when <b>NODE_SLIDER_STYLE</b> is set to<b>ARKUI_SLIDER_STYLE_IN_SET</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].f32: track thickness of the slider, in vp.</li> <br> </ul> |
| NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013 | Defines whether haptic feedback.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and<b>false</b> means the opposite.</li><br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>value[0].i32: whether to feedback.<br> When enabling haptic feedback, you need to add "ohos.permission.VIBRATE" in therequestPermissions field of the module.json5 file to enable vibration permission.</li><br> </ul><br>**起始版本：** 18 |
| NODE_SLIDER_PREFIX | Sets a custom component on the leading side of the Slider component.**Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter format:**<br> <ul><li>.object: Parameter type [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).</li></ul>The prefix component will be placed at the start position of the Slider，typically on the left side in LTR layouts. *<br>**起始版本：** 20 |
| NODE_SLIDER_SUFFIX | Sets a custom component on the trailing side of the Slider component.**Attribute setting method {@link link ArkUI_AttributeItem} parameter format:**<br> <ul><li>.object: Parameter type [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).</li></ul>The suffix component will be placed at the end position of the Slider,typically on the right side in LTR layouts. *<br>**起始版本：** 20 |
| NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR | Defines the color of the slider block. This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <br> <li>colors: colors of the color stops.</li> <br> <li>stops: stop positions of the color stops.</li> <br> <li>size: number of colors.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <br> <li>colors: colors of the color stops.</li> <br> <li>stops: stop positions of the color stops.</li> <br> <li>size: number of colors.</li> <br> </ul><br>**起始版本：** 21 |
| NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR | Defines the background color of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <br> <li>colors: colors of the color stops.</li> <br> <li>stops: stop positions of the color stops.</li> <br> <li>size: number of colors.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <br> <li>colors: colors of the color stops.</li> <br> <li>stops: stop positions of the color stops.</li> <br> <li>size: number of colors.</li> <br> </ul><br>**起始版本：** 21 |
| NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR | Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtainedas required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <br> <li>colors: colors of the color stops.</li> <br> <li>stops: stop positions of the color stops.</li> <br> <li>size: number of colors.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.</li> <br> <li>colors: colors of the color stops.</li> <br> <li>stops: stop positions of the color stops.</li> <br> <li>size: number of colors.</li> <br> </ul><br>**起始版本：** 21 |
| NODE_RADIO_CHECKED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO | Set the selection status of an option button. Attribute setting,attribute resetting, and attribute obtaining are supported.**Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:**<br> <ul><li>.value[0].i32: check status of an option button. The default value is false.</li></ul>**Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:**<br> <ul><li>.value[0].i32: selection status of an option button.</li></ul> |
| NODE_RADIO_STYLE | Set the styles of the selected and deselected states of the option button.The attribute setting, attribute resetting, and attribute obtaining are supported.**Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:**<br> <ul><li>.value[0]?. u32: color of the mother board in enabled state. <br> The type is 0xARGB, and the default value is 0xFF007DFF.</li> <br> <li>.value[1]?. u32: stroke color in the close state. The type is 0xARGB, <br> and the default value is 0xFF182431.</li> <br> <li>.value[2]?. u32: color of the internal round pie in the enabled state. <br> The type is 0xARGB, and the default value is 0xFFFFFFFF.</li> <br> </ul>**Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:**<br> <ul><li>.value[0]. u32: color of the mother board in enabled state. <br> The type is 0xARGB, and the default value is 0xFF007DFF.</li> <br> <li>.value[1]. u32: stroke color in the close state. The type is 0xARGB, <br> and the default value is 0xFF182431.</li> <br> <li>.value[2]. u32: color of the internal round pie in the enabled state. <br> The type is 0xARGB, and the default value is 0xFFFFFFF.</li> <br> </ul> |
| NODE_RADIO_VALUE | Sets the value of the current radio.This attribute can be set, reset, and obtained as required through APIs.**Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:**<br> <ul><li>.string: radio value.</li><br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.string: radio value.</li><br> </ul> |
| NODE_RADIO_GROUP | Set the group name of the current Radio group, only one radio of the same group can be selected.This attribute can be set, reset, and obtained as required through APIs.**Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:**<br> <ul><li>.string: name of the group to which the current option box belongs.</li><br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.string: name of the group to which the current option box belongs.</li><br> </ul> |
| NODE_IMAGE_ANIMATOR_IMAGES = ARKUI_NODE_IMAGE_ANIMATOR * MAX_NODE_SCOPE_NUM | Defines the image frames for the image animator. Dynamic updates are not supported.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.size: number of images.</li><li>.object: array of images. The array element type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md).</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.size: number of images.</li><li>.object: array of images. The array element type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md).</li></ul> |
| NODE_IMAGE_ANIMATOR_STATE = 19001 | Defines the playback status of the animation for the image animator.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: playback status of the animation. The parameter type is[ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus). The default value is <b>ARKUI_ANIMATION_STATUS_INITIAL</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: playback status of the animation. The parameter type is [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus).</li></ul> |
| NODE_IMAGE_ANIMATOR_DURATION = 19002 | Defines the playback duration for the image animator. When the duration is 0, no image is played.The value change takes effect only at the beginning of the next cycle.When a separate duration is set in images, the setting of this attribute is invalid.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: playback duration, in ms. The default value is 1000.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: playback duration, in ms.</li></ul> |
| NODE_IMAGE_ANIMATOR_REVERSE = 19003 | Defines the playback direction for the image animator.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: playback direction. <b>0</b> indicates that images are played from the first one tothe last one, and <b>1</b> indicates that images are played from the last one to the first one.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: playback direction. <b>0</b> indicates that images are played from the first one tothe last one, and <b>1</b> indicates that images are played from the last one to the first one.</li></ul> |
| NODE_IMAGE_ANIMATOR_FIXED_SIZE = 19004 | Defines whether the image size is the same as the component size.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether the image size is the same as the component size. <b>1</b> indicates thatthe image size is the same as the component size. In this case, the width, height, top, and leftattributes of the image are invalid. <b>0</b> indicates that the image size is customized. The width,height, top, and left attributes of each image must be set separately.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether the image size is the same as the component size. <b>1</b> indicates thatthe image size is the same as the component size. <b>0</b> indicates that the image size is customized.</li></ul> |
| NODE_IMAGE_ANIMATOR_FILL_MODE = 19005 | Defines the status before and after execution of the animation in the current playback direction.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: status before and after execution of the animation in the current playback direction.The parameter type is [ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode). The default value is<b>ARKUI_ANIMATION_FILL_MODE_FORWARDS</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: status before and after execution of the animation in the current playback direction.The parameter type is [ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode).</li></ul> |
| NODE_IMAGE_ANIMATOR_ITERATION = 19006 | Defines the number of times that the animation is played.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: number of times that the animation is played.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: number of times that the animation is played.</li></ul> |
| NODE_CHECKBOX_GROUP_NAME  = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP | Defines the name of the checkboxgroup.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.string: component name.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.string: component name.</li> <br> </ul><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_SELECT_ALL | Defines whether the checkboxgroup is selected.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: whether the checkboxgroup is selected.The value <b>1</b> means that the checkboxgroup is selected, and <b>0</b> means the opposite.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: The value <b>1</b> means that the checkboxgroup is selected, and <b>0</b> means the opposite.</li> <br> </ul><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_SELECTED_COLOR | Defines the color of the checkboxgroup when it is selected.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: color of the checkboxgroup when it is selected, in 0xARGB format,for example, <b>0xFF1122FF</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: color of the checkboxgroup when it is selected, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li></ul><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_UNSELECTED_COLOR | Defines the border color of the checkboxgroup when it is not selected.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li></ul><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_MARK | Defines the internal icon style of the checkboxgroup.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li><br> <li>.value[1]?.f32: size of the internal mark, in vp. Optional.</li><br> <li>.value[2]?.f32: stroke width of the internal mark, in vp. Optional. The default value is <b>2</b>.</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li><br> <li>.value[1].f32: size of the internal mark, in vp.</li> <br> <li>.value[2].f32: stroke width of the internal mark, in vp. The default value is <b>2</b>.</li> <br> </ul><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_SHAPE | Defines the shape of the checkboxgroup.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br> <ul><li>.value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li> <br> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br> <ul><li>.value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li></ul><br>**起始版本：** 15 |
| NODE_TEXT_EDITOR_ENTER_KEY_TYPE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR | TextEditor组件回车键类型，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：回车键类型，参数类型[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_NEW_LINE。<br>*返回：<br>.value[0].i32：回车键类型，参数类型[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_CARET_COLOR | TextEditor组件光标颜色，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].u32：光标颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。<br>*返回：<br>.value[0].u32：光标颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_SCROLL_BAR_COLOR | TextEditor组件滚动条颜色，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.data[0].u32：滚动条颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。<br>*返回：<br>.data[0].u32：滚动条颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_BAR_STATE | TextEditor组件滚动条显示模式，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：滚动条显示模式，参数类型[ArkUI_BarState](capi-scroll-h.md#arkui_barstate)，默认值为ARKUI_BAR_STATE_AUTO。<br>*返回：<br>.value[0].i32：滚动条显示模式，参数类型[ArkUI_BarState](capi-scroll-h.md#arkui_barstate)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR | TextEditor组件文本实体识别功能开关，启用后，文本中的电话号码、邮箱、链接等实体将被自动识别并标记为可交互内容。配合NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG属性可自定义识别类型和交互行为。支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用文本实体识别功能，0表示禁用，1表示启用，默认值为0。推荐在需要自动识别并高亮文本中实体信息的场景下设置此属性。<br>*返回：<br>.value[0].i32：是否启用了文本实体识别功能，0表示禁用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG | TextEditor组件文本实体识别配置，设置后，可配置识别类型、实体显示样式，并可选择是否开启长按预览功能。配合NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR属性使用，支持属性设置和属性重置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：文本实体识别配置，设置后可指定需要识别的文本实体类型（如电话号码、邮箱、链接等）及识别后的交互行为。仅在启用文本实体识别功能(NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR设置为1)后传入此参数以自定义识别类型，不传入时使用系统默认识别配置。参数类型{@link ArkUI_TextDataDetectorConfig}。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS | TextEditor组件扩展菜单选项，支持属性设置和属性重置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：扩展菜单选项，设置后可自定义默认菜单项的行为，或添加自定义选项内容。参数类型[ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_PLACEHOLDER | TextEditor组件无输入时的提示文本选项，支持属性设置和属性重置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：无输入时的提示文本选项，参数类型{@link ArkUI_TextEditorPlaceholderOptions}。不传入时，编辑器无输入状态下不显示提示文本。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER | TextEditor组件属性字符串控制器，支持属性设置。设置后，可通过该控制器管理TextEditor中的内容、光标、选区、输入样式及编辑状态。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：属性字符串控制器，参数类型{@link ArkUI_TextEditorStyledStringController}。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT | TextEditor组件预上屏功能开关，启用后，组件内显示输入法输入过程中的拼音、笔画字符。支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用预上屏功能，0表示禁用，1表示启用，默认值为1。<br>*返回：<br>.value[0].i32：是否启用预上屏功能，0表示禁用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_LAYOUT_MANAGER | TextEditor组件TextLayoutManager获取，获取后，可通过布局管理器查询文本的布局信息，如行数、行高和内容偏移等。支持属性获取。<br>作为属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*返回：<br>.object：布局管理器，可通过该管理器查询文本的布局信息。参数类型{@link ArkUI_TextLayoutManager}。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR | TextEditor组件的AI菜单开关，用于控制选中特殊文本实体时是否弹出AI识别菜单。该功能支持属性的设置、重置与获取，启用后可基于选中文本内容提供智能识别及操作选项。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用文本选择识别的AI菜单，0表示禁用，1表示启用，默认值为1。<br>*返回：<br>.value[0].i32：是否启用了文本选择识别的AI菜单，0表示禁用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR | TextEditor组件选中内容背景颜色，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.data[0].u32：选中内容的背景颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。<br>*返回：<br>.data[0].u32：选中内容的背景颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS | TextEditor组件非点击获焦时拉起输入法开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：非点击获焦时是否拉起输入法，0表示不拉起，1表示拉起，默认值为1。<br>*返回：<br>.value[0].i32：非点击获焦时是否拉起输入法，0表示不拉起，1表示拉起。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_MAX_LENGTH | TextEditor组件最大字符数，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：文本编辑器允许输入的最大长度，取值范围为[0, +∞)，超出此限制后将阻止继续输入文本。设置为0、负数或未设置该属性时不限制输入长度。<br>*返回：<br>.value[0].i32：文本编辑器允许输入的最大长度。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_MAX_LINES | TextEditor组件内容最大行数，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：文本编辑器最大行数限制，取值范围：(0, +∞)。设置为0、负数或未设置该属性时，取默认值UINT32_MAX，不限制行数。建议在需要固定显示高度的场景下设置该参数。<br>*返回：<br>.value[0].i32：文本编辑器最大行数限制。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK | TextEditor组件触感反馈开关，启用后，在文本拖选等交互操作时将产生触感反馈震动响应，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否在文本编辑器中启用触感反馈，0表示不启用，1表示启用，默认值为1。<br>*返回：<br>.value[0].i32：是否启用了触感反馈，0表示不启用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_COPY_OPTIONS | TextEditor组件复制选项，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：复制选项，参数类型[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)，默认值为ARKUI_COPY_OPTIONS_LOCAL_DEVICE。<br>*返回：<br>.value[0].i32：复制选项，参数类型[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE | TextEditor组件键盘外观，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：键盘外观，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)，默认值为ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE。<br>*返回：<br>.value[0].i32：文本编辑器当前设置的键盘外观类型，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_STOP_BACK_PRESS | TextEditor组件是否阻止返回键事件向上层传播，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否阻止返回事件传播，0表示不阻止，1表示阻止，默认值为0。推荐在编辑器有未保存内容或需要拦截返回键防止意外退出的场景设置为1。<br>*返回：<br>.value[0].i32：是否阻止返回事件传播，0表示不阻止，1表示阻止。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING | TextEditor组件中西文自动间距开关，支持属性设置、属性重置和属性获取。适用于包含中英文混排内容的编辑场景，启用后可在中文与西文之间自动添加间距，改善混排文本的阅读体验。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用中西文自动间距，0表示不启用，1表示启用，默认值为0。推荐在包含中英文混排内容的编辑场景设置为1，以改善混排文本的阅读体验。<br>*返回：<br>.value[0].i32：是否启用中西文自动间距，0表示不启用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_CUSTOM_KEYBOARD | TextEditor组件自定义键盘。当需要替换系统默认键盘时传入此参数（如数字键盘、表情键盘等特殊输入布局），不传入时使用系统默认键盘。支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。<br>.value[0]?.i32：设置自定义键盘是否支持内容避让功能，即键盘弹出时页面内容自动调整位置以避免被键盘遮挡，0表示不支持，1表示支持，默认值为0。<br>*返回：<br>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。<br>.value[0].i32：自定义键盘是否支持内容避让功能，即键盘弹出时页面内容自动调整位置以避免被键盘遮挡，0表示不支持，1表示支持。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_BIND_SELECTION_MENU | TextEditor组件自定义文本选择菜单绑定，支持属性设置和属性重置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：自定义选择菜单，不传入时使用系统默认文本选择菜单。参数类型{@link ArkUI_TextEditorSelectionMenuOptions}。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING | TextEditor组件首行尾行防截断间距开关，启用后，在首行和尾行增加间距以避免文字截断，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否添加首行尾行防截断间距，0表示不添加，1表示添加，默认值为0。<br>*返回：<br>.value[0].i32：是否添加首行尾行防截断间距，0表示不添加，1表示添加。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING | TextEditor组件行高自适应开关，在多行文字叠加时，行高可以基于文字实际高度自适应，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：行高是否自适应，0表示不自适应，1表示自适应，默认值为0。<br>*返回：<br>.value[0].i32：行高是否自适应，0表示不自适应，1表示自适应。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION | TextEditor组件行首标点符号压缩开关，启用后，行首的标点符号将缩减占位宽度，调整文本排版对齐效果，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用行首标点符号压缩，0表示不启用，1表示启用，默认值为0。<br>*返回：<br>.value[0].i32：是否启用行首标点符号压缩，0表示不启用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE | TextEditor组件选中拖拽预览样式，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：选中拖拽预览样式配置，参数类型[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。当需要自定义选中文本拖拽时的预览效果时传入此参数，不传入时使用系统默认拖拽预览样式。<br>*返回：<br>.object：选中拖拽预览样式配置，参数类型[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_SINGLE_LINE | TextEditor组件单行模式开关，支持属性设置、属性重置和属性获取。启用单行模式后，NODE_TEXT_EDITOR_MAX_LINES属性设置的最大行数将不再生效。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用单行模式，0表示不启用，1表示启用，默认值为0。<br>*返回：<br>.value[0].i32：是否启用单行模式，0表示不启用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION | TextEditor组件孤字优化开关，支持属性设置、属性重置和属性获取。启用后会调整换行点以尽可能避免孤字。仅在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用孤字优化，0表示不启用，1表示启用。默认值为0。仅在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。<br>*返回：<br>.value[0].i32：是否启用孤字优化，0表示不启用，1表示启用。<br>**起始版本：** 26.0.0 |
| NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING | 设置TextEditor组件在文本宽度超过内容区宽度时是否启用水平滚动，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用水平滚动，0表示不启用水平滚动，1表示启用水平滚动。默认值为0。<br>*返回：<br>.value[0].i32：是否启用水平滚动，0表示不启用水平滚动，1表示启用水平滚动。<br>**起始版本：** 26.0.0 |
| NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW | 设置TextEditor组件是否启用行尾标点符号悬挂，支持属性设置、属性重置和属性获取。<br>启用后，行尾单个标点符号超出排版宽度而不换行，避免行尾标点符号换行至下一行行首，从而改善文本排版效果。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用行尾标点符号悬挂，0表示不启用标点符号悬挂，1表示启用标点符号悬挂。默认值为0。<br>*返回：<br>.value[0].i32：是否启用行尾标点符号悬挂，0表示不启用行尾标点符号悬挂，1表示启用行尾标点符号悬挂。<br>**起始版本：** 26.0.0 |
| NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK | 设置子组件在Stack容器中的对齐方式，支持属性设置，属性重置和属性获取接口。该属性与通用属性NODE_ALIGNMENT同时设置时，后设置的属性生效。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32： 设置子组件在Stack容器中的对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值ARKUI_ALIGNMENT_CENTER。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32： 子组件在Stack容器中的对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)。</li></ul> |
| NODE_SCROLL_BAR_DISPLAY_MODE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SCROLL | 设置滚动条状态，支持属性设置，属性重置和属性获取接口。List/Scroll/WaterFlow从API version 12开始支持，Grid从API version 22开始支持。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode)，List、Grid、Scroll组件默认值为[ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO](capi-scroll-h.md#arkui_scrollbardisplaymode)，WaterFlow组件默认值为[ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF](capi-scroll-h.md#arkui_scrollbardisplaymode)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode)。</li></ul> |
| NODE_SCROLL_BAR_WIDTH | 设置滚动条的宽度，支持属性设置，属性重置和属性获取接口。List/Scroll/WaterFlow从API version 12开始支持，Grid从API version 22开始支持。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 滚动条宽度，单位vp，默认值4。 取值范围：[0, +∞)。设置为小于0的值时，按默认值处理，儿童智能表则恢复至默认值5vp。设置为0时，不显示滚动条。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 滚动条宽度，单位vp。</li></ul> |
| NODE_SCROLL_BAR_COLOR | 设置滚动条的颜色，支持属性设置，属性重置和属性获取接口。List/Scroll/WaterFlow从API version 12开始支持，Grid从API version 22开始支持。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.data[0].u32 滚动条颜色，0xargb类型。儿童智能表的默认值颜色：0xffffffff，表示白色（100%不透明度）。其他设备默认值：0x66182431，表示深蓝灰色（40%不透明度）。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.data[0].u32 滚动条颜色，0xargb类型。</li></ul> |
| NODE_SCROLL_SCROLL_DIRECTION | 设置滚动方向，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 滚动方向，数据类型[ArkUI_ScrollDirection](capi-scroll-h.md#arkui_scrolldirection)，默认值[ARKUI_SCROLL_DIRECTION_VERTICAL](capi-scroll-h.md#arkui_scrolldirection)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 滚动方向，数据类型[ArkUI_ScrollDirection](capi-scroll-h.md#arkui_scrolldirection)。</li></ul> |
| NODE_SCROLL_EDGE_EFFECT | 设置边缘滑动效果，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 边缘滑动效果，参数类型[ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect)，Grid、Scroll、WaterFlow组件默认值为[ARKUI_EDGE_EFFECT_NONE](capi-scroll-h.md#arkui_edgeeffect)，List组件默认值为[ARKUI_EDGE_EFFECT_SPRING](capi-scroll-h.md#arkui_edgeeffect)。</li><li>.value[1]?.i32 可选值，组件内容大小小于组件自身时，设置是否开启滑动效果，开启为1，关闭为0，List、Grid、WaterFlow组件默认值为0，Scroll组件默认值为1。</li><li>.value[2]?.i32 边缘效果生效的方向，参数类型[ArkUI_EffectEdge](capi-scroll-h.md#arkui_effectedge)，默认值[ARKUI_EFFECT_EDGE_START](capi-scroll-h.md#arkui_effectedge) \| [ARKUI_EFFECT_EDGE_END](capi-scroll-h.md#arkui_effectedge)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 边缘滑动效果，参数类型[ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect)。</li><li>.value[1].i32 组件内容大小小于组件自身时，设置是否开启滑动效果，开启为1，关闭为0。</li><li>.value[2].i32 边缘效果生效的方向，参数类型[ArkUI_EffectEdge](capi-scroll-h.md#arkui_effectedge)。该参数从API version 18开始支持。</li></ul> |
| NODE_SCROLL_ENABLE_SCROLL_INTERACTION | 设置是否支持滚动手势，当设置为0时，无法通过手指或者鼠标滚动，但不影响控制器的滚动接口。List/Scroll/WaterFlow从API version 12开始支持，Grid从API version 22开始支持。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持滚动手势，默认值1。1：支持滚动手势，0：不支持滚动手势。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持滚动手势。1：支持滚动手势，0：不支持滚动手势。</li></ul> |
| NODE_SCROLL_FRICTION | 设置摩擦系数，手动滑动滚动区域时生效，只对惯性滚动过程有影响，对惯性滚动过程中的链式效果有间接影响。List/Scroll/WaterFlow从API version 12开始支持，Grid从API version 22开始支持。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 摩擦系数，默认值：非可穿戴设备为0.6，可穿戴设备为0.9。取值范围：(0, +∞)，设置为小于等于0的值时，按默认值处理。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 摩擦系数。</li></ul> |
| NODE_SCROLL_SNAP | 设置Scroll组件的限位滚动模式，支持属性设置，属性重置和属性获取接口。如果同时设置了滑动翻页和限位滚动，则限位滚动优先生效，滑动翻页不生效。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Scroll组件限位滚动时的对齐方式，数据类型[ArkUI_ScrollSnapAlign](capi-scroll-h.md#arkui_scrollsnapalign)，默认值[ARKUI_SCROLL_SNAP_ALIGN_NONE](capi-scroll-h.md#arkui_scrollsnapalign)。</li><li>.value[1].i32 在Scroll组件限位滚动模式下，该参数设置为1（true）后，不允许Scroll在开头和第一页间自由滑动，设置为0（false）后，允许Scroll在开头和第一页间自由滑动，默认值1（true）。该参数仅在限位点为2个及以上时生效。</li><li>.value[2].i32 在Scroll组件限位滚动模式下，该参数设置为1（true）后，不允许Scroll在最后一页和末尾间自由滑动，设置为0（false）后，允许Scroll在最后一页和末尾间自由滑动，默认值1（true）。该参数仅在限位点为2个及以上时生效。</li><li>.value[3...].f32 Scroll组件限位滚动时的限位点，限位点即为Scroll组件能滑动停靠的偏移量，单位：vp。可以1个或多个。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Scroll组件限位滚动时的对齐方式，数据类型[ArkUI_ScrollSnapAlign](capi-scroll-h.md#arkui_scrollsnapalign)。</li><li>.value[1].i32 在Scroll组件限位滚动模式下，该参数设置为1（true）后，不允许Scroll在开头和第一页间自由滑动，设置为0（false）后，允许Scroll在开头和第一页间自由滑动，默认值1（true）。该参数仅在限位点为2个及以上时生效。</li><li>.value[2].i32 在Scroll组件限位滚动模式下，该参数设置为1（true）后，不允许Scroll在最后一页和末尾间自由滑动，设置为0（false）后，允许Scroll在最后一页和末尾间自由滑动，默认值1（true）。该参数仅在限位点为2个及以上时生效。</li><li>.value[3...].f32 Scroll组件限位滚动时的限位点，限位点即为Scroll组件能滑动停靠的偏移量，单位：vp。</li></ul> |
| NODE_SCROLL_NESTED_SCROLL | 设置嵌套滚动选项，支持属性设置，属性重置和属性获取。List/Scroll/WaterFlow从API version 12开始支持，Grid从API version 22开始支持。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 可滚动组件往末尾端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](capi-scroll-h.md#arkui_scrollnestedmode)。</li><li>.value[1].i32 可滚动组件往起始端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](capi-scroll-h.md#arkui_scrollnestedmode)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 可滚动组件往末尾端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](capi-scroll-h.md#arkui_scrollnestedmode)。</li><li>.value[1].i32 可滚动组件往起始端滚动时的嵌套滚动，参数类型[ArkUI_ScrollNestedMode](capi-scroll-h.md#arkui_scrollnestedmode)。</li></ul> |
| NODE_SCROLL_OFFSET | 设置Scroll组件滑动到指定位置，支持属性设置，属性重置和属性获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 水平滑动偏移，单位为vp。取值范围：[0, +∞)，设置为小于0的值时按0处理。值为0时滚动到起始位置，值大于0时滚动到指定偏移位置。</li><li>.value[1].f32 垂直滑动偏移，单位为vp。取值范围：[0, +∞)，设置为小于0的值时按0处理。值为0时滚动到起始位置，值大于0时滚动到指定偏移位置。</li><li>.value[2]?.i32 可选值，滚动时长，单位为毫秒，默认值1000。滚动时长大于0或使能默认弹簧动效时，滚动带动画效果。</li><li>.value[3]?.i32 可选值，滚动曲线，参数类型[ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve)。默认值为[ARKUI_CURVE_EASE](capi-native-type-h.md#arkui_animationcurve)。</li><li>.value[4]?.i32 可选值，是否使能默认弹簧动效，默认值为0不使能。</li><li>.value[5]?.i32 可选值，设置动画滚动到边界是否转换为越界回弹动画，默认值为0不转换越界回弹动画。</li><li>.value[6]?.i32 可选值，设置滚动是否可以停留在越界位置，默认值为0不停留在越界位置。该参数从API version 20开始支持。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 水平滑动偏移，单位为vp。</li><li>.value[1].f32 垂直滑动偏移，单位为vp。</li></ul> |
| NODE_SCROLL_EDGE | 设置Scroll组件滚动到容器边缘位置，支持属性设置和属性获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 容器边缘位置，参数类型[ArkUI_ScrollEdge](capi-scroll-h.md#arkui_scrolledge)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 容器是否位于边缘。-1表示未处于边缘；处于边缘状态时，返回值为[ArkUI_ScrollEdge](capi-scroll-h.md#arkui_scrolledge)枚举值，表示具体边缘位置。</li></ul> |
| NODE_SCROLL_ENABLE_PAGING | 设置是否支持滑动翻页，支持属性设置，属性重置和属性获取接口。如果同时设置了滑动翻页enablePaging和限位滚动scrollSnap，则scrollSnap优先生效，enablePaging不生效。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持滑动翻页，默认值0。0：不支持滑动翻页，1：支持滑动翻页。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持滑动翻页。0：不支持滑动翻页，1：支持滑动翻页。</li></ul> |
| NODE_SCROLL_PAGE | 滚动到下一页或者上一页。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 翻页方向。0表示向下翻页，1表示向上翻页。</li><li>.value[1]?.i32 是否开启翻页动画效果。1有动画，0无动画。默认值：0。</li></ul> |
| NODE_SCROLL_BY | 滑动指定距离。从API version 12开始List/Scroll/WaterFlow组件支持滑动指定距离，从API版本26.0.0开始Grid组件支持滑动指定距离。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 水平方向滚动距离，单位：vp。</li><li>.value[1].f32 垂直方向滚动距离，单位：vp。</li></ul> |
| NODE_SCROLL_FLING | 滚动类组件按传入的初始速度进行惯性滚动。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 惯性滚动的初始速度，单位：vp/s。值设置为0，视为异常值，本次滚动不生效。如果值为正数，则向下滚动；如果值为负数，则向上滚动。</li></ul><br>**起始版本：** 13 |
| NODE_SCROLL_FADING_EDGE | 设置滚动类组件边缘渐隐效果。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否使能边缘渐隐效果。0表示关闭边缘效果，1表示开启边缘效果，默认值0。</li><li>.value[1]?.f32 边缘渐隐效果长度。单位：vp，默认值：32。 取值范围：值必须大于等于0。仅在开启边缘渐隐效果时生效。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否使能边缘渐隐效果。0表示关闭边缘效果，1表示开启边缘效果。</li><li>.value[1].f32 边缘渐隐效果长度。单位：vp。</li></ul><br>**起始版本：** 14 |
| NODE_SCROLL_SIZE | 获取滚动类组件所有子组件全展开尺寸。作为属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 滚动类组件所有子组件全展开的宽度，默认单位为vp。</li><li>.value[1].f32 滚动类组件所有子组件全展开的高度，默认单位为vp。 设置NODE_PADDING、NODE_MARGIN或NODE_BORDER_WIDTH后，NODE_PADDING、NODE_MARGIN或NODE_BORDER_WIDTH在单位vp转换成单位px时会进行像素取整，返回值根据取整后的值计算。</li></ul><br>**起始版本：** 14 |
| NODE_SCROLL_CONTENT_START_OFFSET | 设置滚动类组件内容起始端偏移量。List组件从API version 15开始支持，Grid/Scroll/WaterFlow从API version 22开始支持。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 内容起始端偏移量，单位vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 内容起始端偏移量，单位vp。</li></ul><br>**起始版本：** 15 |
| NODE_SCROLL_CONTENT_END_OFFSET | 设置滚动类组件内容末尾端偏移量。List组件从API version 15开始支持，Grid/Scroll/WaterFlow从API version 22开始支持。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 内容末尾端偏移量，单位vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 内容末尾端偏移量，单位vp。</li></ul><br>**起始版本：** 15 |
| NODE_SCROLL_FLING_SPEED_LIMIT = 1002019 | 限制跟手滑动结束后，Fling动效开始时的最大初始速度。支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 Fling动效开始时的最大初始速度，单位：vp/s。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 Fling动效开始时的最大初始速度，单位：vp/s。</li></ul><br>**起始版本：** 18 |
| NODE_SCROLL_CLIP_CONTENT = 1002020 | 设置滚动容器的内容层裁剪区域。支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 内容裁剪模式，参数类型[ArkUI_ContentClipMode](capi-scroll-h.md#arkui_contentclipmode)。Grid、Scroll组件默认值为[ARKUI_CONTENT_CLIP_MODE_BOUNDARY](capi-scroll-h.md#arkui_contentclipmode)，List、WaterFlow组件默认值为[ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY](capi-scroll-h.md#arkui_contentclipmode)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 内容裁剪模式，参数类型[ArkUI_ContentClipMode](capi-scroll-h.md#arkui_contentclipmode)。</li></ul><br>**起始版本：** 18 |
| NODE_SCROLL_BACK_TO_TOP = 1002021 | 设置滚动容器是否在点击状态栏时回到顶部。支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否回到顶部，1表示回到顶部，0表示保持当前位置不变，默认值：API version 18之前：0。API version 18及以后：滚动方向是水平方向时为0，是垂直方向时为1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否回到顶部。1表示回到顶部，0表示保持当前位置不变。</li></ul><br>**起始版本：** 15 |
| NODE_SCROLL_BAR_MARGIN = 1002022 | 设置滚动条的边距，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 设置滚动条起始边距，儿童智能表默认值为42，其他设备默认值为0，单位：vp。</li><li>.value[1].f32 设置滚动条末尾边距，默认值为0，单位：vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 滚动条起始边距，单位：vp。</li><li>.value[1].f32 滚动条末尾边距，单位：vp。</li></ul><br>**起始版本：** 20 |
| NODE_SCROLL_MAX_ZOOM_SCALE = 1002023 | 设置滚动内容最大缩放比例。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 设置内容最大缩放比例。默认值：1 取值范围：(0, +∞)，小于或等于0时按默认值1处理。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 获取内容最大缩放比例。</li></ul><br>**起始版本：** 20 |
| NODE_SCROLL_MIN_ZOOM_SCALE = 1002024 | 设置滚动内容最小缩放比例。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 设置内容最小缩放比例，默认值：1 取值范围：(0, NODE_SCROLL_MAX_ZOOM_SCALE]，小于或等于0时按默认值1处理，大于NODE_SCROLL_MAX_ZOOM_SCALE时按NODE_SCROLL_MAX_ZOOM_SCALE处理。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 获取内容最小缩放比例。</li></ul><br>**起始版本：** 20 |
| NODE_SCROLL_ZOOM_SCALE = 1002025 | 设置滚动内容缩放比例。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 设置内容缩放比例，默认值：1 取值范围：(0, +∞)，小于或等于0时按默认值1处理。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 获取内容缩放比例。</li></ul><br>**起始版本：** 20 |
| NODE_SCROLL_ENABLE_BOUNCES_ZOOM = 1002026 | 设置是否支持过缩放回弹效果。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持过缩放回弹效果，0：不支持，1：支持。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持过缩放回弹效果，0：不支持，1：支持。</li></ul><br>**起始版本：** 20 |
| NODE_SCROLL_ENABLE_SCROLL_WITH_MOUSE = 1002027 | 设置是否支持鼠标左键按下拖动滚动，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持鼠标左键按下拖动滚动，0：不支持鼠标左键按下拖动滚动，1：支持鼠标左键按下拖动滚动。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持鼠标左键按下拖动滚动，0：不支持鼠标左键按下拖动滚动，1：支持鼠标左键按下拖动滚动。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_SCROLL_AUTO_ADJUST_MARGIN = 1002028 | 设置滚动条是否自动调整边距以避让组件NODE_PADDING、NODE_SCROLL_CONTENT_START_OFFSET或NODE_SCROLL_CONTENT_END_OFFSET的区域，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否自动调整边距，0：自动调整边距，1：不自动调整边距。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否自动调整边距，0：自动调整边距，1：不自动调整边距。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_SCROLL_BAR_HEIGHT = 1002029 | 设置滚动条滑轨高度。支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 滚动条滑轨高度，单位：vp。默认值：自适应滚动组件高度。 取值范围：[0, +∞)。设置为小于0时使用默认值，儿童智能表则恢复至默认值37vp。设置为0时不显示滚动条。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 滚动条滑轨高度，单位：vp。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_LIST_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST | 设置List组件排列方向。支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件排列方向，数据类型[ArkUI_Axis](capi-native-type-h.md#arkui_axis)，默认值ARKUI_AXIS_VERTICAL。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件排列方向，数据类型[ArkUI_Axis](capi-native-type-h.md#arkui_axis)。</li></ul> |
| NODE_LIST_STICKY | 配合ListItemGroup组件使用，设置ListItemGroup中header和footer是否要吸顶或吸底，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 配合ListItemGroup组件使用，设置ListItemGroup中header和footer是否要吸顶或吸底。数据类型[ArkUI_StickyStyle](capi-list-h.md#arkui_stickystyle)，默认值ARKUI_STICKY_STYLE_NONE。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 配合ListItemGroup组件使用，设置ListItemGroup中header和footer是否要吸顶或吸底。数据类型[ArkUI_StickyStyle](capi-list-h.md#arkui_stickystyle)。</li></ul> |
| NODE_LIST_SPACE | 设置列表项间距，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 子组件主轴方向的间隔，单位vp，默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 子组件主轴方向的间隔。</li></ul> |
| NODE_LIST_NODE_ADAPTER | List组件适配器，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用{@link ArkUI_NodeAdapter}对象作为适配器。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 返回值格式为{@link ArkUI_NodeAdapter}。</li></ul> |
| NODE_LIST_CACHED_COUNT | List组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 配合List组件Adapter使用，设置adapter中的缓存数量。</li><li>.value[1]?.i32 是否显示缓存节点，0：不显示，1：显示，默认值：0。该参数从API version 15开始支持。</li><li>.value[2]?.i32 设置List最大缓存数量，默认值与第一个参数相同。该参数从API version 22开始支持。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 adapter中的缓存数量。</li><li>.value[1].i32 是否显示缓存节点，0：不显示，1：显示。该参数从API version 15开始支持。</li><li>.value[2].i32 List最大缓存数量。该参数从API version 22开始支持。</li></ul> |
| NODE_LIST_SCROLL_TO_INDEX | 滑动到指定index。开启平滑滚动动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 要滑动到的目标元素在当前容器中的索引值。传入-1时，指滑动到当前容器的最后一个元素。</li><li>.value[1]?.i32 设置滑动到列表项在列表中的索引值时是否有动效，1表示有动效，0表示没有动效。默认值：0。</li><li>.value[2]?.i32 指定滑动到的元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment)，默认值：[ARKUI_SCROLL_ALIGNMENT_START](capi-scroll-h.md#arkui_scrollalignment)。</li><li>.value[3]?.f32 额外偏移量，默认值：0，单位：vp。正数表示向末尾端额外偏移，负数表示向起始端额外偏移。该参数从API version 15开始支持。</li></ul> |
| NODE_LIST_ALIGN_LIST_ITEM | 设置List交叉轴方向宽度大于ListItem交叉轴宽度乘以布局数量时，ListItem在List交叉轴方向的布局方式。List垂直滚动时，布局数量为列数；List水平滚动时，布局数量为行数。支持属性设置、属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 交叉轴方向的布局方式。参数类型{@link ArkUI_ListItemAlign}。默认值：ARKUI_LIST_ITEM_ALIGNMENT_START。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 交叉轴方向的布局方式。参数类型{@link ArkUI_ListItemAlign}。</li></ul> |
| NODE_LIST_CHILDREN_MAIN_SIZE = 1003007 | 设置List子组件默认主轴尺寸。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 参数格式为[ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 参数格式为[ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)。</li></ul> |
| NODE_LIST_INITIAL_INDEX = 1003008 | 设置当前List初次加载时视口起始位置显示的item的索引值，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 当前List初次加载时视口起始位置显示的item的索引值。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 当前List初次加载时视口起始位置显示的item的索引值。</li></ul> |
| NODE_LIST_DIVIDER = 1003009 | 设置ListItem分割线样式，默认无分割线，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32 分割线颜色，0xargb类型，默认值为0x08000000。</li><li>.value[1].f32 分割线宽，默认值：0，单位vp。</li><li>.value[2].f32 分割线距离列表侧边起始端的距离，默认值：0，单位vp。</li><li>.value[3].f32 分割线距离列表侧边结束端的距离，默认值：0，单位vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32 分割线颜色，0xargb类型。</li><li>.value[1].f32 分割线宽，单位vp。</li><li>.value[2].f32 分割线距离列表侧边起始端的距离，单位vp。</li><li>.value[3].f32 分割线距离列表侧边结束端的距离，单位vp。</li></ul> |
| NODE_LIST_SCROLL_TO_INDEX_IN_GROUP = 1003010 | 滑动到指定ListItemGroup中指定index。开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 要滑动到的目标ListItemGroup在当前List中的索引值。</li><li>.value[1].i32 要滑动到的目标ListItem在ListItemGroup中的索引值。</li><li>.value[2]?.i32 设置滑动到列表项在列表中的索引值时是否有动效，1表示有动效，0表示没有动效。默认值：0。</li><li>.value[3]?.i32 指定滑动到的元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment)。默认值：[ARKUI_SCROLL_ALIGNMENT_START](capi-scroll-h.md#arkui_scrollalignment)。</li></ul><br>**起始版本：** 15 |
| NODE_LIST_LANES = 1003011 | 设置List列数（List垂直滚动时表示列数，水平滚动时表示行数），支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32 List布局列数或行数，List垂直滚动时表示列数，水平滚动时表示行数；如果同时设置了最小、最大列宽或行高，则设置列数或行数不生效；默认值：1，取值范围：[1, +∞)，设置异常值时使用默认值。</li><li>.value[1]?.f32 最小列宽或行高，单位vp，默认值：-1（未设置）。</li><li>.value[2]?.f32 最大列宽或行高，单位vp，默认值：-1（未设置）。</li><li>.value[3]?.f32 列间距或行间距，默认值：0，单位vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32 当前List布局列数或行数，List垂直滚动时表示列数，水平滚动时表示行数。</li><li>.value[1].f32 最小列宽或行高，单位vp。</li><li>.value[2].f32 最大列宽或行高，单位vp。</li><li>.value[3].f32 列间距或行间距，单位vp。</li></ul><br>**起始版本：** 15 |
| NODE_LIST_SCROLL_SNAP_ALIGN = 1003012 | 设置List限位对齐模式。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件限位滚动时的对齐方式，数据类型[ArkUI_ScrollSnapAlign](capi-scroll-h.md#arkui_scrollsnapalign)，默认值[ARKUI_SCROLL_SNAP_ALIGN_NONE](capi-scroll-h.md#arkui_scrollsnapalign)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件限位滚动时的对齐方式，数据类型[ArkUI_ScrollSnapAlign](capi-scroll-h.md#arkui_scrollsnapalign)。</li></ul><br>**起始版本：** 15 |
| NODE_LIST_MAINTAIN_VISIBLE_CONTENT_POSITION = 1003013 | 设置List显示区域外插入或删除数据是否保持可见内容位置不变。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List显示区域外插入或删除数据是否保持可见内容位置不变。0表示不保持可见内容位置，1表示保持可见内容位置，默认值为0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List显示区域外插入或删除数据是否保持可见内容位置不变。0表示不保持可见内容位置，1表示保持可见内容位置，默认值为0。</li></ul><br>**起始版本：** 15 |
| NODE_LIST_STACK_FROM_END = 1003014 | 设置List从末尾开始布局。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 设置List是否从末尾开始布局。0表示从顶部开始布局，1表示从末尾开始布局，默认值为0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 设置List是否从末尾开始布局。0表示从顶部开始布局，1表示从末尾开始布局，默认值为0。</li></ul><br>**起始版本：** 19 |
| NODE_LIST_FOCUS_WRAP_MODE = 1003015 | List组件走焦换行模式，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件走焦换行模式，参数取值为[ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode)下的枚举，默认值为ARKUI_FOCUS_WRAP_MODE_DEFAULT。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode)。</li></ul><br>**起始版本：** 20 |
| NODE_LIST_SYNC_LOAD = 1003016 | List组件是否同步加载子节点，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件是否同步加载子节点。0：分帧加载，1：同步加载，默认值为1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件是否同步加载子节点。0：分帧加载，1：同步加载。</li></ul><br>**起始版本：** 20 |
| NODE_LIST_SCROLL_SNAP_ANIMATION_SPEED = 1003017 | List组件限位滚动动画速度，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件限位滚动动画速度，数据类型[ArkUI_ScrollSnapAnimationSpeed](capi-scroll-h.md#arkui_scrollsnapanimationspeed)。默认值：ARKUI_SCROLL_SNAP_ANIMATION_NORMAL。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件限位滚动动画速度，数据类型[ArkUI_ScrollSnapAnimationSpeed](capi-scroll-h.md#arkui_scrollsnapanimationspeed)。</li></ul><br>**起始版本：** 22 |
| NODE_LIST_LANES_ITEMFILLPOLICY = 1003018 | List组件的响应式列数布局策略，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)。</li><li>.value[1]?.f32 列间距，单位vp。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)。</li><li>.value[1].f32 列间距，单位vp。</li></ul><br>**起始版本：** 22 |
| NODE_LIST_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1003019 | 设置当前List组件是否支持在LazyForEach或Repeat中使用if/else渲染控制语法生成不包含任何子组件的空分支节点。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件是否支持空分支。0：不支持，1：支持。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件是否支持空分支。0：不支持，1：支持。</li></ul><br>**起始版本：** 23 |
| NODE_LIST_BACK_PRESS_BEHAVIOR = 1003020 | 设置List组件的系统返回键行为，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 系统返回键生效时是否收起ListItem的划出组件。0：不收起，1：收起。默认值：1</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 系统返回键生效时是否收起ListItem的划出组件。0：不收起，1：收起。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_LIST_ENABLE_EDIT_MODE = 1003021 | 设置List组件是否启用编辑模式。进入编辑模式后，默认显示复选框，并支持手指滑动多选。支持属性设置、属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件是否启用编辑模式。0：不启用，1：启用。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件是否启用编辑模式。0：未启用，1：已启用。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_LIST_EDIT_MODE_OPTIONS = 1003022 | 设置List组件的编辑模式选项，支持属性设置、属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件是否使用默认多选样式。0：不使用，1：使用。默认值：1。</li><li>.value[1].i32 List组件是否启用双指滑动多选。0：不启用，1：启用。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 List组件是否使用默认多选样式。0：不使用，1：使用。</li><li>.value[1].i32 List组件是否启用双指滑动多选。0：未启用，1：已启用。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_SWIPER_LOOP = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER | Defines whether to enable loop playback for the swiper.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether to enable loop playback. The value <b>1</b> means to enable loop playback, and<b>0</b> means the opposite. The default value is <b>1</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether to enable loop playback. The value <b>1</b> means to enable loop playback, and<b>0</b> means the opposite. The default value is <b>1</b>.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_AUTO_PLAY | Defines whether to enable automatic playback for child component switching in the swiper.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether to enable automatic playback for child component switching. The value <b>1</b>means to enable automatic playback, and <b>0</b> means the opposite. The default value is <b>0</b>.</li><li>.value[1]?.i32: whether to stop automatic playback when the user touches the screen. The value <b>1</b> meansto stop automatic playback, and <b>0</b> means the opposite. The default value is <b>1</b>. This parameter issupported since API version 16.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether to enable automatic playback for child component switching. The value <b>1</b> meansto enable automatic playback, and <b>0</b> means the opposite. The default value is <b>0</b>.</li><li>.value[1].i32: whether to stop automatic playback when the user touches the screen. The value <b>1</b> meansto stop automatic playback, and <b>0</b> means the opposite. This parameter is supported since API version 16.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_SHOW_INDICATOR | Defines whether to enable the navigation point indicator for the swiper. This attribute can be set,reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether to enable the navigation point indicator. The value <b>1</b> means to enable thenavigation point indicator, and <b>0</b> means the opposite. The default value is <b>1</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether to enable the navigation point indicator. The value <b>1</b> means to enable thenavigation point indicator, and <b>0</b> means the opposite. The default value is <b>1</b>.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_INTERVAL | Defines the interval for automatic playback. This attribute can be set, reset, and obtained as requiredthrough APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].f32: interval for automatic playback, in milliseconds.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].f32: interval for automatic playback, in milliseconds.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_VERTICAL | Defines whether vertical swiping is used for the swiper. This attribute can be set, reset, and obtainedas required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether vertical swiping is used. The value <b>1</b> means that vertical swiping is used, and<b>0</b> means the opposite. The default value is <b>0</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether vertical swiping is used. The value <b>1</b> means that vertical swiping is used, and<b>0</b> means the opposite. The default value is <b>0</b>.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_DURATION | Defines the duration of the animation for switching child components. This attribute can be set, reset,and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].f32: duration of the animation for switching child components, in milliseconds. The default valueis <b>400</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].f32: duration of the animation for switching child components, in milliseconds. The default valueis <b>400</b>.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_CURVE | Defines the animation curve for the swiper. This attribute can be set, reset, and obtained as requiredthrough APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).The default value is <b>ARKUI_CURVE_LINEAR</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).The default value is <b>ARKUI_CURVE_LINEAR</b>.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_ITEM_SPACE | Defines the spacing between child components in the swiper.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].f32: spacing between child components.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].f32: spacing between child components.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_INDEX | Defines the index of the child component currently displayed in the swiper.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: index value of the child component.</li><li>.value[1]?.i32: animation mode, the parameter type is [ArkUI_SwiperAnimationMode](capi-native-type-h.md#arkui_swiperanimationmode).The default value is ARKUI_SWIPER_NO_ANIMATION. This parameter is valid only for the current call.This parameter is supported since API version 15.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: index value of the child component.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_DISPLAY_COUNT | Defines the number of elements to display per page.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: number of elements to display per page.</li><li>.value[1]?.i32: whether to turn pages by group. The value <b>0</b> means to turn pages by child element,and <b>1</b> means to turn pages by group. This parameter is supported since API version 19.</li><li>.string?: this parameter can only be set to 'auto'. When 'auto' is set, the value[] parameters are ignored.This parameter is supported since API version 19.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: number of elements to display per page.</li><li>.value[1].i32: whether to turn pages by group. This parameter is supported since API version 19.</li><li>.string: 'auto' or empty string.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_DISABLE_SWIPE | Defines whether to disable the swipe feature.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether to disable the swipe feature. The value <b>1</b> means to disablethe swipe feature, and <b>0</b> means the opposite. The default value is <b>0</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether to disable the swipe feature. The value <b>1</b> means to disable the swipefeature, and <b>0</b> means the opposite. The default value is <b>0</b>.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_SHOW_DISPLAY_ARROW | Defines whether to show the arrow when the mouse pointer hovers over the navigation point indicator.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator.The parameter type is [ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow).The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>.</li><li>.?object: arrow style. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md).This parameter is supported since API version 19.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator.The parameter type is [ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow).The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>.</li><li>.object: arrow style. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md).This parameter is supported since API version 19.</li></ul> |
| NODE_SWIPER_EDGE_EFFECT_MODE | Defines the effect used at the edges of the swiper when the boundary of the scrollable content is reached.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached.The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).The default value is <b>ARKUI_EDGE_EFFECT_SPRING</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached.The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_NODE_ADAPTER | Defines the swiper adapter. The attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.object: {@link ArkUI_NodeAdapter} object as the adapter.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_CACHED_COUNT | Sets the number of cached items in the swiper adapter.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: number of cached items in the swiper adapter.</li><li>.value[1]?.i32: whether the cached items will be displayed.The value <b>0</b> indicates that cached items will not be displayed,and <b>1</b> indicates that cached items will be displayed. The default value is <b>0</b>.This parameter is supported from API version 19.</li><li>.value[2]?.i32: whether the cachedCount is independent of group calculation.The value <b>1</b> indicates that cachedCount is calculated by actual child component count,and is independent of displayCount group calculation.The value <b>0</b> indicates that, when NODE_SWIPER_DISPLAY_COUNT is enabled to turn pages by group,cachedCount is calculated by group.The default value is <b>0</b>.This parameter is supported from API version 24.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: number of cached items in the swiper adapter.</li><li>.value[1].i32: whether the cached items will be displayed. This parameter is supported from API version 19.</li><li>.value[2].i32: whether the cachedCount is independent of group calculation.This parameter is supported from API version 24.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_PREV_MARGIN | Defines the front margin of the wiper.The attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].f32: the front margin. The unit is vp. The default value is <b>0.0</b></li><li>.value[1]?.i32: whether to ignore blanks, the default value is 0.The value <b>1</b> means to ignore blank areas, and <b>0</b> means the opposite.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].f32: the front margin, the unit is vp.</li><li>.value[1].i32: whether to ignore blank areas. The value <b>1</b> means to ignore blank areas, and <b>0</b>means the opposite.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_NEXT_MARGIN | Defines the back margin of the wiper.The attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].f32: the back margin. The unit is vp. The default value is <b>0.0</b></li><li>.value[1]?.i32: whether to ignore blanks, the default value is 0.The value <b>1</b> means to ignore blank areas, and <b>0</b> means the opposite.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].f32: the back margin, the unit is vp.</li><li>.value[1].i32: whether to ignore blank areas. The value <b>1</b> means to ignore blank areas, and <b>0</b>means the opposite.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_INDICATOR | Defines the navigation indicator type of the swiper.The attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: navigation indicator type, the parameter type is [ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype).</li><li>.object: The parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) when the indicator typeis <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b>. The parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)when the indicator type is <b>ARKUI_SWIPER_INDICATOR_TYPE_DIGIT</b>.[ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) is supported since API version 19.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: navigation indicator type, the parameter type is [ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype).</li><li>.object: The parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) when the indicator typeis <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b>. The parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)when the indicator type is <b>ARKUI_SWIPER_INDICATOR_TYPE_DIGIT</b>.[ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) is supported since API version 19.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_NESTED_SCROLL | Set the nested scrolling mode for the Swiper component and parent component.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32：Nested scrolling patterns for Swiper components and parent components. The parameter type is[ArkUI_SwiperNestedScrollMode](capi-native-type-h.md#arkui_swipernestedscrollmode)The default value is <b>ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY</b></li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32：Nested scrolling patterns for Swiper components and parent components. The parameter type is[ArkUI_SwiperNestedScrollMode](capi-native-type-h.md#arkui_swipernestedscrollmode)</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_SWIPE_TO_INDEX | Set the switcher component to flip to the specified page.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32：Specify the index value of the page in Swiper.</li><li>.value[1]?.i32：Set whether there is an animation effect when flipping to the specified page. 1 indicatesactive effect, 0 indicates no active effect, default value is 0。</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_INDICATOR_INTERACTIVE | Set to disable component navigation point interaction function。**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32：Set to disable the interaction function of component navigation points. When set to true, itindicates that the navigation points are interactive. The default value is true.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32：Set to disable component navigation point interaction.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_PAGE_FLIP_MODE | Sets the page flipping mode using the mouse wheel.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-native-type-h.md#arkui_pageflipmode).</li></ul>**Format of the return value [ArkUI_PageFlipMode](capi-native-type-h.md#arkui_pageflipmode):<ul><li>.value[0].i32: page flipping mode using the mouse wheel.</li></ul><br>**起始版本：** 15 |
| NODE_SWIPER_AUTO_FILL | Defines the minimum main axis size of child element for swiper to works out the display count.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].f32: minimum main axis size of the child element, Unit: vp.</li><li>.value[1]?.i32: whether to turn pages by group. The value <b>0</b> means to turn pages by child element,and <b>1</b> means to turn pages by group. The default value is <b>0</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].f32: minimum main axis size of the child element, Unit: vp.</li><li>.value[1].i32: whether to turn pages by group.</li></ul><br>**起始版本：** 19 |
| NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023 | Sets whether to maintain the visible content's position when data is inserted or deleted outsidethe display area of the <b>Swiper</b> component.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outsidethe display area of the <b>Swiper</b> component. The value <b>0</b> means not to maintain the visible content'sposition, and <b>1</b> means the opposite. The default value is <b>0</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outsidethe display area of the <b>Swiper</b> component. The value <b>0</b> means not to maintain the visible content'sposition, and <b>1</b> means the opposite. The default value is <b>0</b>.</li></ul><br>**起始版本：** 20 |
| NODE_SWIPER_ITEMFILLPOLICY = 1001024 | Specifies the responsive column layout policy for the <b>Swiper</b> component.This attribute can be set, reset, and obtained as required through APIs.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.value[0].i32: number of columns at different breakpoint specifications.The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li><li>.value[1]?.i32: whether to paginate by group. The value <b>0</b> means to paginate by individual childelements, and <b>1</b> means to paginate by groups of child elements displayed within the viewport.The default value is <b>0</b>.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.value[0].i32: number of columns at different breakpoint specifications.The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li><li>.value[1].i32: whether to paginate by group.</li></ul><br>**起始版本：** 22 |
| NODE_LIST_ITEM_SWIPE_ACTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM | @brief: Set the delineation component of the ListItem, supporting property settings, property resets, andproperty acquisition interfaces.**Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<ul><li>.object: Construct using the {@link ArkUI_ListitemSwipeActionOption} object.</li></ul>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<ul><li>.object: Construct using the {@link ArkUI_ListitemSwipeActionOption} object.</li></ul> |
| NODE_LIST_ITEM_GROUP_SET_HEADER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM_GROUP | 设置 ListItemGroup 头部组件，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ListItemGroup头部组件。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ListItemGroup头部组件。</li></ul> |
| NODE_LIST_ITEM_GROUP_SET_FOOTER | 设置 ListItemGroup 尾部组件，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ListItemGroup尾部组件。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ListItemGroup尾部组件。</li></ul> |
| NODE_LIST_ITEM_GROUP_SET_DIVIDER | 设置ListItem分割线样式，默认无分割线，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32 颜色，0xargb类型，默认值为0x08000000。</li><li>.value[1].f32 分割线宽，默认值：0，单位vp。</li><li>.value[2].f32 分割线距离列表侧边起始端的距离，默认值：0，单位vp。</li><li>.value[3].f32 分割线距离列表侧边结束端的距离，默认值：0，单位vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32 颜色，0xargb类型。</li><li>.value[1].f32 分割线宽，单位vp。</li><li>.value[2].f32 分割线距离列表侧边起始端的距离，单位vp。</li><li>.value[3].f32 分割线距离列表侧边结束端的距离，单位vp。</li></ul> |
| NODE_LIST_ITEM_GROUP_CHILDREN_MAIN_SIZE = 1005003 | 设置ListItemGroup子组件默认主轴尺寸。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 参数格式为[ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 参数格式为[ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)。</li></ul> |
| NODE_LIST_ITEM_GROUP_NODE_ADAPTER = 1005004 | ListItemGroup组件适配器，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用{@link ArkUI_NodeAdapter}对象作为适配器。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 返回值格式为{@link ArkUI_NodeAdapter}。</li></ul><br>**起始版本：** 15 |
| NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN | 设置子组件在Column容器中水平方向上的对齐方式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置子组件在Column容器中水平方向上的对齐方式，数据类型[ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment)，默认值ARKUI_HORIZONTAL_ALIGNMENT_CENTER。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：Column子组件在Column容器中水平方向上的对齐方式，数据类型[ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment)。</li></ul> |
| NODE_COLUMN_JUSTIFY_CONTENT | 设置子组件在Column容器中垂直方向上的对齐方式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置子组件在Column容器中垂直方向上的对齐方式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值ARKUI_FLEX_ALIGNMENT_START。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：子组件在Column容器中垂直方向上的对齐方式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)。</li></ul> |
| NODE_LINEAR_LAYOUT_SPACE | 设置Column或Row容器中子组件的间距，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置Column或Row容器中子组件之间的间距，单位vp，默认值：0。取值范围：[0, +∞)设置异常值时，按默认值显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式:<ul><li>.value[0].f32：Column或Row容器中子组件之间的间距，单位vp。</li></ul><br>**起始版本：** 23 |
| NODE_LINEAR_LAYOUT_REVERSE | 设置Column或Row容器中沿主轴方向的子组件排列是否反向，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置Column或Row容器中沿主轴方向的子组件排列是否反向，默认值：false。值为true时，子组件在主轴方向上反转排列。值为false时，子组件在主轴方向上正序排列。设置异常值时，按默认值显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式:<ul><li>.value[0].i32：Column或Row容器中主轴方向的子组件排列是否反向。</li></ul><br>**起始版本：** 23 |
| NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW | 设置子组件在Row容器中垂直方向上的对齐格式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置子组件在Row容器中垂直方向上的对齐方式，数据类型[ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment)，默认值ARKUI_VERTICAL_ALIGNMENT_CENTER。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：子组件在Row容器中垂直方向上的对齐方式，数据类型[ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment)。</li></ul> |
| NODE_ROW_JUSTIFY_CONTENT | 设置Row子组件在水平方向上的对齐格式，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：设置子组件在Row容器中水平方向上的对齐方式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值ARKUI_FLEX_ALIGNMENT_START。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：子组件在Row容器中水平方向上的对齐方式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)。</li></ul> |
| NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX | 设置Flex属性，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0]?.i32：设置子组件在Flex容器上排列的方向[ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection)，默认值为ARKUI_FLEX_DIRECTION_ROW。</li><li>.value[1]?.i32：设置排列规则[ArkUI_FlexWrap](capi-native-type-h.md#arkui_flexwrap)，默认值为ARKUI_FLEX_WRAP_NO_WRAP。</li><li>.value[2]?.i32：设置主轴上的对齐格式[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值为ARKUI_FLEX_ALIGNMENT_START。</li><li>.value[3]?.i32：设置交叉轴上的对齐格式[ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_START。</li><li>.value[4]?.i32：设置交叉轴中有额外的空间时，多行内容的对齐方式[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值为ARKUI_FLEX_ALIGNMENT_START。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：子组件在Flex容器上排列的方向的枚举值。</li><li>.value[1].i32：排列规则的枚举值。</li><li>.value[2].i32：主轴上的对齐格式的枚举值。</li><li>.value[3].i32：交叉轴上的对齐格式的枚举值。</li><li>.value[4].i32：交叉轴中有额外的空间时，多行内容的对齐方式的枚举值。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。 |
| NODE_FLEX_SPACE | 设置Flex容器内子组件的间距，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置Flex容器主轴方向的间距，单位vp，默认值：0。取值范围：[0, +∞)设置异常值时，按默认值显示。</li><li>.value[1].f32：设置Flex容器交叉轴方向的间距，单位vp，默认值：0。取值范围：[0, +∞)设置异常值时，按默认值显示。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式:<ul><li>.value[0].f32：Flex容器主轴方向的间距，单位vp，默认值：0。</li><li>.value[1].f32：Flex容器交叉轴方向的间距，单位vp，默认值：0。</li></ul>属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。<br>**起始版本：** 23 |
| NODE_REFRESH_REFRESHING = MAX_NODE_SCOPE_NUM * ARKUI_NODE_REFRESH | 设置组件是否正在刷新，支持属性设置，属性获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 参数值为1或者0，1表示正在刷新，0表示不在刷新。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 参数值为1或者0，1表示正在刷新，0表示不在刷新。</li></ul> |
| NODE_REFRESH_CONTENT | 设置下拉区域的自定义内容，支持属性设置和重置。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li></ul> |
| NODE_REFRESH_PULL_DOWN_RATIO = 1009002 | 设置下拉跟手系数，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 下拉跟手系数，取值范围：[0, 1]。设置小于0或大于1的值时，属性设置失败。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 下拉跟手系数，取值范围：[0, 1]。</li></ul> |
| NODE_REFRESH_OFFSET = 1009003 | 设置触发刷新的下拉偏移量，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 下拉偏移量，单位vp， 默认值：64vp。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 下拉偏移量，单位vp， 默认值：64vp。</li></ul> |
| NODE_REFRESH_PULL_TO_REFRESH = 1009004 | 设置当下拉距离超过refreshOffset时是否触发刷新，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否触发刷新。支持取值为0或1，其中1为触发刷新，0为不触发刷新。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否触发刷新，1为触发刷新，0为不触发刷新。</li></ul> |
| NODE_REFRESH_MAX_PULL_DOWN_DISTANCE = 1009005 | 设置刷新的最大下拉距离。支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 最大下拉距离，单位：vp。取值范围：[0, +∞)，设置小于0的值时按0处理。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 最大下拉距离，单位：vp。</li></ul><br>**起始版本：** 20 |
| NODE_REFRESH_PULL_UP_TO_CANCEL_REFRESH = 1009006 | 设置上划是否取消刷新。支持属性设置，属性重置和属性获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 上划是否取消刷新。支持取值为0或1，其中0为上划不取消刷新，1为上划取消刷新。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 上划是否取消刷新。0为上划不取消刷新，1为上划取消刷新。</li></ul><br>**起始版本：** 23 |
| NODE_WATER_FLOW_LAYOUT_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_WATER_FLOW | 定义瀑布流组件布局主轴方向，支持属性设置、重置和获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 主轴方向，参数类型[ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection)。默认值[ARKUI_FLEX_DIRECTION_COLUMN](capi-native-type-h.md#arkui_flexdirection)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 主轴方向，参数类型[ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection)。</li></ul> |
| NODE_WATER_FLOW_COLUMN_TEMPLATE | 设置当前瀑布流组件布局列的数量，不设置时默认1列，支持属性设置、重置和获取。例如，'1fr 1fr 2fr' 是将父组件分3列，将父组件允许的宽分为4等份，第1列占1份，第2列占1份，第3列占2份。可使用columnsTemplate('repeat(auto-fill,track-size)')根据给定的列宽track-size自动计算列数，其中repeat、auto-fill为关键字，track-size为可设置的宽度，支持的单位包括px、vp、%或有效数字，默认单位为vp。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string 布局列的数量。默认值：'1fr'。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string 布局列的数量。</li></ul> |
| NODE_WATER_FLOW_ROW_TEMPLATE | 设置当前瀑布流组件布局行的数量，不设置时默认1行，支持属性设置、重置和获取。例如，'1fr 1fr 2fr'是将父组件分3行，将父组件允许的高分为4等份，第1行占1份，第2行占1份，第3行占2份。可使用rowsTemplate('repeat(auto-fill,track-size)')根据给定的行高track-size自动计算行数，其中repeat、auto-fill为关键字，track-size为可设置的高度，支持的单位包括px、vp、%或有效数字，默认单位为vp。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string 布局行的数量。默认值：'1fr'。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string 布局行的数量。</li></ul> |
| NODE_WATER_FLOW_COLUMN_GAP | 设置列与列的间距，支持属性设置、重置和获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 列与列的间距，默认值：0，单位vp。取值范围：[0, +∞)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 列与列的间距，单位vp。</li></ul> |
| NODE_WATER_FLOW_ROW_GAP | 设置行与行的间距，支持属性设置、重置和获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 行与行的间距，默认值：0，单位vp。取值范围：[0, +∞)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 行与行的间距，单位vp。</li></ul> |
| NODE_WATER_FLOW_SECTION_OPTION | 设置FlowItem分组配置信息，支持属性设置、重置和获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 从0开始计算的索引，会转换为整数，表示要开始改变分组的位置。</li><li>.object 参数格式为[ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 返回值格式为[ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)。</li></ul> |
| NODE_WATER_FLOW_NODE_ADAPTER | WaterFlow组件适配器，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用{@link ArkUI_NodeAdapter}对象作为适配器。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 返回值格式为{@link ArkUI_NodeAdapter}。</li></ul> |
| NODE_WATER_FLOW_CACHED_COUNT | WaterFlow组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 配合WaterFlow组件Adapter使用，设置adapter中的缓存数量。</li><li>.value[1]?.i32 是否显示缓存节点，0：不显示，1：显示，默认值：0。该参数从API version 16开始支持。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 adapter中的缓存数量。</li><li>.value[1].i32 是否显示缓存节点，0：不显示，1：显示。该参数从API version 16开始支持。</li></ul> |
| NODE_WATER_FLOW_FOOTER | 设置瀑布流组件末尾的自定义显示组件。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li></ul> |
| NODE_WATER_FLOW_SCROLL_TO_INDEX | 滑动到指定index。开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 要滑动到的目标元素在当前容器中的索引值。</li><li>.value[1]?.i32 设置滑动到列表项在列表中的索引值时是否有动效，1表示有动效，0表示没有动效。默认值：0。</li><li>.value[2]?.i32 指定滑动到的元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment)。默认值为：[ARKUI_SCROLL_ALIGNMENT_START](capi-scroll-h.md#arkui_scrollalignment)。</li><li>.value[3]?.f32 滑动到目标元素后的额外偏移量，默认值：0，单位：vp。如果值为正数，则向底部额外偏移；如果值为负数，则向顶部额外偏移。该参数从API version 23开始支持。</li></ul> |
| NODE_WATER_FLOW_ITEM_CONSTRAINT_SIZE | 设置当前瀑布流子组件的约束尺寸属性，约束子组件尺寸范围，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 最小宽度，单位：vp。使用-1表示不设置。</li><li>.value[1].f32 最大宽度，单位：vp。使用-1表示不设置。</li><li>.value[2].f32 最小高度，单位：vp。使用-1表示不设置。</li><li>.value[3].f32 最大高度，单位：vp。使用-1表示不设置。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 最小宽度，单位：vp。使用-1表示不设置。</li><li>.value[1].f32 最大宽度，单位：vp。使用-1表示不设置。</li><li>.value[2].f32 最小高度，单位：vp。使用-1表示不设置。</li><li>.value[3].f32 最大高度，单位：vp。使用-1表示不设置。</li></ul> |
| NODE_WATER_FLOW_LAYOUT_MODE | 定义瀑布流组件布局模式，支持属性设置、重置和获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 布局模式，参数类型[ArkUI_WaterFlowLayoutMode](capi-water-flow-h.md#arkui_waterflowlayoutmode)，默认值：[ARKUI_WATER_FLOW_LAYOUT_MODE_ALWAYS_TOP_DOWN](capi-water-flow-h.md#arkui_waterflowlayoutmode)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 布局模式，参数类型[ArkUI_WaterFlowLayoutMode](capi-water-flow-h.md#arkui_waterflowlayoutmode)。</li></ul><br>**起始版本：** 18 |
| NODE_WATER_FLOW_SYNC_LOAD = 1010012 | WaterFlow组件是否同步加载子节点，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 WaterFlow组件是否同步加载子节点。0：分帧加载，1：同步加载。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 WaterFlow组件是否同步加载子节点。0：分帧加载，1：同步加载。</li></ul><br>**起始版本：** 20 |
| NODE_WATER_FLOW_COLUMN_TEMPLATE_ITEMFILLPOLICY = 1010013 | WaterFlow组件的响应式列数布局策略，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)。</li></ul><br>**起始版本：** 22 |
| NODE_WATER_FLOW_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1010014 | 设置当前WaterFlow组件是否支持在LazyForEach或Repeat中使用if/else渲染控制语法生成不包含任何子组件的空分支节点。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。> **说明：>> 当通过[NODE_WATER_FLOW_SECTION_OPTION](capi-native-node-h.md#arkui_nodeattributetype)设置了[ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)分组，> 或通过[NODE_WATER_FLOW_LAYOUT_MODE](capi-native-node-h.md#arkui_nodeattributetype)设置为[ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW](capi-water-flow-h.md#arkui_waterflowlayoutmode)> 布局模式时，设置0或1时空分支后的FlowItem都会显示。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 WaterFlow组件是否支持空分支。0：不支持，1：支持。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 WaterFlow组件是否支持空分支。0：不支持，1：支持。</li></ul>当通过[NODE_WATER_FLOW_SECTION_OPTION](capi-native-node-h.md#arkui_nodeattributetype)设置了[ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)分组，或通过[NODE_WATER_FLOW_LAYOUT_MODE](capi-native-node-h.md#arkui_nodeattributetype)设置为[ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW](capi-water-flow-h.md#arkui_waterflowlayoutmode)布局模式时，设置0或1时空分支后的FlowItem都会显示。<br>**起始版本：** 26.0.0 |
| NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER | 设置RelativeContaine容器内的辅助线，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object: 设置RelativeContaine容器内的辅助线。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object: RelativeContaine容器内的辅助线。</li></ul> |
| NODE_RELATIVE_CONTAINER_BARRIER | 设置RelativeContaine容器内的屏障，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object: 设置RelativeContaine容器内的屏障。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object: RelativeContaine容器内的屏障。</li></ul> |
| NODE_GRID_COLUMN_TEMPLATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID | 设置当前Grid组件布局列的数量，不设置时默认1列，支持属性设置、重置和获取。例如，'1fr 1fr 2fr' 是将父组件分3列，将父组件允许的宽分为4等份，第1列占1份，第2列占1份，第3列占2份。可使用columnsTemplate('repeat(auto-fill,track-size)')根据给定的列宽track-size自动计算列数，其中repeat、auto-fill为关键字，track-size为可设置的宽度，支持的单位包括px、vp、%或有效数字，默认单位为vp。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string 布局列的数量。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string 布局列的数量。</li></ul> |
| NODE_GRID_ROW_TEMPLATE | 设置当前Grid布局行的数量或最小行高值，不设置时默认1行，支持属性设置、重置和获取。例如，'1fr 1fr 2fr'是将父组件分3行，将父组件允许的高分为4等份，第1行占1份，第2行占1份，第3行占2份。可使用rowsTemplate('repeat(auto-fill,track-size)')根据给定的行高track-size自动计算行数，其中repeat、auto-fill为关键字，track-size为可设置的高度，支持的单位包括px、vp、%或有效数字，默认单位为vp。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string 布局行的数量。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.string 布局行的数量。</li></ul> |
| NODE_GRID_COLUMN_GAP | 设置列与列的间距，支持属性设置、重置和获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 列与列的间距，默认值：0，单位vp。取值范围：[0, +∞)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 列与列的间距，单位vp。</li></ul> |
| NODE_GRID_ROW_GAP | 设置行与行的间距，支持属性设置、重置和获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 行与行的间距，默认值：0，单位vp。取值范围：[0, +∞)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 行与行的间距，单位vp。</li></ul> |
| NODE_GRID_NODE_ADAPTER | Grid组件适配器，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用{@link ArkUI_NodeAdapter}对象作为适配器。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 返回值格式为{@link ArkUI_NodeAdapter}。</li></ul> |
| NODE_GRID_CACHED_COUNT | Grid组件适配器缓存数量，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 配合Grid组件适配器使用，设置{@link ArkUI_NodeAdapter}的缓存数量。</li><li>.value[1].i32 是否显示缓存节点，0：不显示缓存节点，1：显示缓存节点。可选参数，默认值：0。从API版本26.0.0开始支持。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件适配器的缓存数量。</li><li>.value[1].i32 是否显示缓存节点，0：不显示，1：显示。该参数从API版本26.0.0开始支持。</li></ul> |
| NODE_GRID_FOCUS_WRAP_MODE = 1013006 | Grid组件走焦换行模式，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件走焦换行模式，参数取值为[ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode)下的枚举，默认值为ARKUI_FOCUS_WRAP_MODE_DEFAULT。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件走焦换行模式，参数类型[ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode)。</li></ul><br>**起始版本：** 20 |
| NODE_GRID_SYNC_LOAD = 1013007 | Grid组件是否同步加载子节点，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否同步加载子节点。0：分帧加载，1：同步加载。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否同步加载子节点。0：分帧加载，1：同步加载。</li></ul><br>**起始版本：** 20 |
| NODE_GRID_ALIGN_ITEMS = 1013008 | 设置Grid中GridItem的对齐方式，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid中GridItem的对齐方式，参数取值为[ArkUI_GridItemAlignment](capi-grid-h.md#arkui_griditemalignment)下的枚举，默认值为ARKUI_GRID_ITEM_ALIGNMENT_DEFAULT。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid中GridItem的对齐方式，参数类型[ArkUI_GridItemAlignment](capi-grid-h.md#arkui_griditemalignment)。</li></ul><br>**起始版本：** 22 |
| NODE_GRID_LAYOUT_OPTIONS = 1013009 | 设置Grid布局选项，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 参数格式为[ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 返回值格式为[ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)。</li></ul><br>**起始版本：** 22 |
| NODE_GRID_COLUMN_TEMPLATE_ITEMFILLPOLICY = 1013010 | Grid组件的响应式列数布局策略，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)。</li></ul><br>**起始版本：** 22 |
| NODE_GRID_EDIT_MODE = 1013011 | Grid组件是否进入编辑模式。进入编辑模式后，可以通过NODE_GRID_ON_ITEM_DRAG_START事件拖拽GridItem。支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否进入编辑模式。0：不可编辑，1：可以编辑。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否进入编辑模式。0：不可编辑，1：可以编辑。</li></ul><br>**起始版本：** 23 |
| NODE_GRID_DRAG_ANIMATION = 1013012 | Grid组件是否启用GridItem拖拽动画。支持属性设置，属性重置和属性获取接口。仅在滚动模式下（只设置NODE_GRID_ROW_TEMPLATE、NODE_GRID_COLUMN_TEMPLATE其中一个）支持动画。仅在大小规则的Grid中支持拖拽动画，跨行或跨列场景不支持。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否启用GridItem拖拽动画。0：不启用，1：启用。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否启用GridItem拖拽动画。0：不启用，1：启用。</li></ul><br>**起始版本：** 23 |
| NODE_GRID_MULTI_SELECTABLE = 1013013 | Grid组件是否启用鼠标框选。支持属性设置，属性重置和属性获取接口。启用后在Grid范围内鼠标框选会触发GridItem的[NODE_GRID_ITEM_ON_SELECT](./capi-native-node-h.md#arkui_nodeeventtype)事件。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否启用鼠标框选。0：不启用，1：启用。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否启用鼠标框选。0：不启用，1：启用。</li></ul><br>**起始版本：** 23 |
| NODE_GRID_SCROLL_TO_INDEX = 1013014 | 滑动到指定index。开启动效时，会对经过的所有子组件进行加载和布局计算，当大量加载子组件时会导致性能问题。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 要滑动到的目标元素在当前容器中的索引值。</li><li>.value[1]?.i32 设置滑动到目标元素时是否有动效，1表示有动效，0表示没有动效。默认值：0。</li><li>.value[2]?.i32 指定滑动到的目标元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment)。默认值：ARKUI_SCROLL_ALIGNMENT_AUTO。</li><li>.value[3]?.f32 滑动到目标元素后的额外偏移量，默认值：0，单位：vp。如果值为正数，则向底部额外偏移；如果值为负数，则向顶部额外偏移。</li></ul><br>**起始版本：** 23 |
| NODE_GRID_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1013015 | 设置当前Grid组件是否支持在LazyForEach或Repeat中使用if/else渲染控制语法生成不包含任何子组件的空分支节点。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否支持空分支。0：不支持，1：支持。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否支持空分支。0：不支持，1：支持。</li></ul><br>**起始版本：** 23 |
| NODE_GRID_ENABLE_EDIT_MODE = 1013016 | 设置Grid组件是否启用编辑模式。进入编辑模式后，默认显示复选框，并支持手指滑动多选。支持属性设置、属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否启用编辑模式。0：不启用，1：启用。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否启用编辑模式。0：未启用，1：已启用。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_GRID_EDIT_MODE_OPTIONS = 1013017 | 设置Grid组件的编辑模式选项，支持属性设置、属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否使用默认多选样式。0：不使用，1：使用。默认值：1。</li><li>.value[1].i32 Grid组件是否启用双指滑动多选。0：不启用，1：启用。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 Grid组件是否使用默认多选样式。0：不使用，1：使用。</li><li>.value[1].i32 Grid组件是否启用双指滑动多选。0：未启用，1：已启用。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_GRID_ITEM_STYLE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID_ITEM | 设置GridItem样式，支持属性设置，属性重置和属性获取。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 GridItem样式，参数取值为[ArkUI_GridItemStyle](capi-grid-h.md#arkui_griditemstyle)下的枚举，默认值为ARKUI_GRID_ITEM_STYLE_NONE。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 GridItem样式，参数类型[ArkUI_GridItemStyle](capi-grid-h.md#arkui_griditemstyle)。</li></ul><br>**起始版本：** 22 |
| NODE_GRID_ITEM_SELECTABLE = 1014001 | 设置GridItem是否可以被鼠标框选。支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 GridItem是否可以被鼠标框选。0：不可以，1：可以。默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 GridItem是否可以被鼠标框选。0：不可以，1：可以。</li></ul><br>**起始版本：** 23 |
| NODE_GRID_ITEM_SELECTED = 1014002 | 设置GridItem选中状态。支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 GridItem选中状态。0：未选中，1：已选中。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 GridItem选中状态。0：未选中，1：已选中。</li></ul><br>**起始版本：** 23 |
| NODE_TEXT_PICKER_COLUMN_WIDTHS = 15009 | 设置每一个选择项列宽，支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：设置的第1个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等，默认值为不设置时各列均分。</li><li>.value[1]?.f32：设置的第2个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。</li><li>.value[2]?.f32：设置的第3个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。</li><li>...</li><li>.value[n]?.f32：设置的第n+1个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：第1列宽度，总宽度的百分比。</li><li>.value[1].f32：第2列宽度，总宽度的百分比。</li><li>.value[2].f32：第3列宽度，总宽度的百分比。</li><li>...</li><li>.value[n].f32：第n+1列宽度，总宽度的百分比。</li></ul><br>**起始版本：** 18 |
| NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT | 定义用于启动EmbeddedAbility的want。支持属性设置。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object: EmbeddedComponent的want参数，参数类型为[AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md)。</li><li>默认值为<b>nullptr</b>。</li></ul><br>**起始版本：** 20 |
| NODE_EMBEDDED_COMPONENT_OPTION | EmbeddedComponent的选项。支持属性设置。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object: EmbeddedComponent的选项列表，参数类型为[ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)。</li></ul><br>**起始版本：** 20 |
| NODE_PICKER_OPTION_SELECTED_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER | 定义选择器数据选择范围内默认选中项的索引。支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：索引值。默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].u32：选择器数据选择范围内当前选中项的索引。</li></ul><br>**起始版本：** 23 |
| NODE_PICKER_ENABLE_HAPTIC_FEEDBACK = 1018001 | 定义是否启用触控反馈。支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用触控反馈。1表示启用反馈，0表示不启用。默认值：1。开启后，是否存在触控反馈取决于系统硬件支持情况。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否启用触控反馈。1表示启用反馈，0表示不启用。是否存在触控反馈取决于系统硬件支持情况。</li></ul><br>**起始版本：** 23 |
| NODE_PICKER_CAN_LOOP = 1018002 | 定义选择器是否支持滚动循环。支持属性设置，属性重置和属性获取接口。使用场景：循环滚动适用于选项有限且希望提供快速选择体验的场景（如性别选择）；非循环滚动适用于选项有明确边界、需要限制用户选择范围的场景。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否支持滚动循环。1表示支持滚动循环，0表示不支持。默认值：1。如果子组件的个数小于8个，无论设置为1还是0，都不会循环滚动。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：是否支持滚动循环。返回0表示不支持滚动循环，返回1表示支持滚动循环。</li></ul><br>**起始版本：** 23 |
| NODE_PICKER_SELECTION_INDICATOR = 1018003 | 设置选择指示器的类型和参数。支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：参数类型为[ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)。默认值：{type: PickerIndicatorType.BACKGROUND,borderRadius: {value:12,unit:LengthUnit.vp},backgroundColor: 'sys.color.comp_background_tertiary'}未设置时使用默认值。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object：当前设置的选择指示器样式对象，类型为[ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)。</li></ul><br>**起始版本：** 23 |
| NODE_ARC_LIST_DIGITAL_CROWN_SENSITIVITY = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_LIST | 设置ArcList组件表冠灵敏度，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 表冠灵敏度类型，数据类型{@link ArkUI_CrownSensitivity}，默认值为{@link ARKUI_CROWN_SENSITIVITY_MEDIUM}。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 表冠灵敏度类型，数据类型{@link ArkUI_CrownSensitivity}。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_SPACE = 1019001 | 设置ArcList子组件主轴方向的间隔，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 子组件主轴方向的间隔，单位为vp，默认值0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 子组件主轴方向的间隔，单位：vp。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_CACHED_COUNT = 1019002 | 设置ArcList组件缓存数量，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 缓存数量。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 缓存数量。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_SCROLL_TO_INDEX = 1019003 | 滑动到指定索引值对应的列表项。开启动效时，会对经过的所有列表项进行加载和布局计算，当大量加载列表项时会导致性能问题。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 要滑动到的目标元素在当前容器中的索引值。传入-1时，指滑动到当前容器的最后一个元素。</li><li>.value[1]?.i32 设置滑动到指定索引值对应的列表项时是否有动效，1表示有动效，0表示没有动效。默认值：0。</li><li>.value[2]?.i32 指定滑动到的列表项与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment)，默认值：[ARKUI_SCROLL_ALIGNMENT_START](capi-scroll-h.md#arkui_scrollalignment)。</li><li>.value[3]?.f32 额外偏移量，默认值：0，单位：vp。正数表示向末尾端额外偏移，负数表示向起始端额外偏移。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_CHAIN_ANIMATION = 1019004 | 设置ArcList是否启用链式联动动效，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否启用链式联动动效，0：不启用，1：启用，默认值：0。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否启用链式联动动效。0：不启用，1：启用。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_CHILDREN_MAIN_SIZE = 1019005 | 设置ArcList子组件默认主轴尺寸，支持属性设置和属性重置接口。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 参数格式为[ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)。定义ArcList的所有子项主轴尺寸信息的结构体。通过[OH_ArkUI_ListChildrenMainSizeOption_Create](capi-list-h.md#oh_arkui_listchildrenmainsizeoption_create)接口来创建，并且可以使用[OH_ArkUI_ListChildrenMainSizeOption_Splice](capi-list-h.md#oh_arkui_listchildrenmainsizeoption_splice)方法对ArcList组件子项主轴尺寸数组进行大小调整。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_SET_HEADER = 1019006 | 设置ArcList头部组件，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ArcList头部组件。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为ArcList头部组件。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_SCROLL_BAR = 1019007 | 设置ArcList组件的滚动条状态，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode)，默认值为[ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO](capi-scroll-h.md#arkui_scrollbardisplaymode)。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode)。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_SCROLL_BAR_COLOR = 1019008 | 设置ArcList组件滚动条的颜色，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.data[0].u32 滚动条颜色，0xargb类型。默认值：0x66182431。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.data[0].u32 滚动条颜色，0xargb类型。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_SCROLL_BAR_WIDTH = 1019009 | 设置ArcList组件滚动条的宽度，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 滚动条宽度，单位vp，默认值4。 取值范围：[0, +∞)。设置为小于0的值时，按默认值处理。设置为0时，不显示滚动条。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 滚动条宽度，单位vp。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_ENABLE_SCROLL_INTERACTION = 1019010 | 设置ArcList是否支持滚动手势，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持滚动手势，默认值1。1：支持滚动手势，0：不支持滚动手势。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否支持滚动手势。1：支持滚动手势，0：不支持滚动手势。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_FADING_EDGE = 1019011 | 设置ArcList边缘渐隐效果，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否使能边缘渐隐效果。0表示关闭边缘效果，1表示开启边缘效果。默认值：0。</li><li>.value[1]?.f32 边缘渐隐效果长度。单位：vp，默认值：32。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否使能边缘渐隐效果。0表示关闭边缘效果，1表示开启边缘效果。</li><li>.value[1].f32 边缘渐隐效果长度。单位：vp。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_FRICTION = 1019012 | 设置ArcList摩擦系数，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 摩擦系数，默认值：0.8。取值范围：(0, +∞)，设置为小于等于0的值时，按默认值处理。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 摩擦系数。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_FLING_SPEED_LIMIT = 1019013 | 设置ArcList限制Fling动效最大初始速度，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 Fling动效开始时的最大初始速度，单位：vp/s。默认值：9000。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32 Fling动效开始时的最大初始速度，单位：vp/s。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_ITEM_AUTO_SCALE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_LIST_ITEM | 设置ArcListItem是否启用自动缩放，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否启用自动缩放，0：不启用，1：启用，默认值：1。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 是否启用自动缩放。0：不启用，1：启用。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_LIST_ITEM_SWIPE_ACTION = 1020001 | 设置ArcListItem的划出组件，支持属性设置和属性重置接口。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用[ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)对象构造。定义ArcListItem的划出组件信息的结构体。通过[OH_ArkUI_ListItemSwipeActionOption_Create](capi-list-item-h.md#oh_arkui_listitemswipeactionoption_create)接口来创建，并且可以使用[OH_ArkUI_ListItemSwipeActionOption_SetStart](capi-list-item-h.md#oh_arkui_listitemswipeactionoption_setstart)方法设置ListItemSwipeActionItem左侧（垂直布局）或上方（横向布局）内容。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_SCROLL_BAR_BIND_SCROLLABLE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_SCROLL_BAR | 设置ArcScrollBar绑定的可滚动组件，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为滚动条绑定的可滚动组件。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.object 使用[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)对象作为滚动条绑定的可滚动组件。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_ARC_SCROLL_BAR_DISPLAY_MODE = 1021001 | 设置ArcScrollBar滚动条状态，支持属性设置，属性重置和属性获取接口。作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode)，默认值为ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32 滚动条状态，数据类型[ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode)。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_PICKER_DISPLAYED_ITEM_COUNT = 1018004 | 设置Picker容器可见选项的数量，语义与ArkTS侧UIPickerComponent的displayedItemCount一致。未设置时，可见选项为7行。Picker为立体滚轮样式时，除选中项外的选项会按角度旋转，实际可视高度会小于选项行高；若增大可见行数或行高，请相应增大容器高度，详见UIPickerComponent。支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：可见选项数量。取值范围为<b>[2, 9]</b>内的整数。传入小数时按向下取整处理；传入偶数时，会规范为不小于该值的奇数（例如2变为3、8变为9）。不在取值范围内时使用默认值<b>7</b>。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].i32：当前Picker容器可见选项的数量，取值范围为[2, 9]内的整数。</li></ul><br>**起始版本：** 26.0.0 |
| NODE_PICKER_ITEM_HEIGHT = 1018005 | 设置Picker容器每个选项的高度，语义与ArkTS侧UIPickerComponent的itemHeight一致。未设置时，每个选项高度为40vp。CAPI以vp为单位传入高度值。支持属性设置，属性重置和属性获取接口。**属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：选项高度，单位为vp。有效范围为<b>[40, 64]</b>。小于40vp或大于64vp时使用默认值<b>40</b>vp。不支持百分比。</li></ul>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<ul><li>.value[0].f32：当前选项高度，单位为vp。</li></ul><br>**起始版本：** 26.0.0 |

### ArkUI_NodeEventType

```c
enum ArkUI_NodeEventType
```

**描述**

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_TOUCH_EVENT = 0 | Defines the gesture event type.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). |
| NODE_EVENT_ON_APPEAR | Defines the mount event.This event is triggered when the component is mounted and displayed. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_EVENT_ON_DISAPPEAR | Defines the unmount event.This event is triggered when the component is unmounted and hidden. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_EVENT_ON_AREA_CHANGE | Defines the area change event.This event is triggered when the component's size, position, or any other attribute that mayaffect its display area changes. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 12 parameters:<br> <ul><li><b>ArkUI_NodeComponentEvent.data[0].f32</b>: original width of the target element, in vp.The value type is number.</li><li><b>ArkUI_NodeComponentEvent.data[1].f32</b>: original height of the target element, in vp.The value type is number.</li><li><b>ArkUI_NodeComponentEvent.data[2].f32</b>: original X coordinate of the target element's upper left cornerrelative to the parent element's, in vp. The value type is number.</li><li><b>ArkUI_NodeComponentEvent.data[3].f32</b>: original Y coordinate of the target element's upper left cornerrelative to the parent element's, in vp. The value type is number.</li><li><b>ArkUI_NodeComponentEvent.data[4].f32</b>: original X coordinate of the target element's upper left cornerrelative to the page's, in vp. The value type is number.</li><li><b>ArkUI_NodeComponentEvent.data[5].f32</b>: original Y coordinate of the target element's upper left cornerrelative to the page's, in vp. The value type is number.</li><li><b>ArkUI_NodeComponentEvent.data[6].f32</b>: new width of the target element, in vp. The value is a number.</li><li><b>ArkUI_NodeComponentEvent.data[7].f32</b>: new height of the target element, in vp. The value is a number.</li><li><b>ArkUI_NodeComponentEvent.data[8].f32</b>: new X coordinate of the target element's upper left corner relativeto the parent element's, in vp. The value type is number.</li><li><b>ArkUI_NodeComponentEvent.data[9].f32</b>: new Y coordinate of the target element's upper left corner relativeto the parent element's, in vp. The value type is number.</li><li><b>ArkUI_NodeComponentEvent.data[10].f32</b>: new X coordinate of the target element's upper left corner relativeto the page's, in vp. The value type is number.</li><li><b>ArkUI_NodeComponentEvent.data[11].f32</b>: new Y coordinate of the target element's upper left corner relativeto the page's, in vp. The value type is number.</li></ul> |
| NODE_ON_FOCUS | Defines the focus event.This event is triggered when the component obtains the focus. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_ON_BLUR | Defines the blur event.This event is triggered when the component loses the focus. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_ON_CLICK | Defines the click event.This event is triggered when the component is clicked. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 12 parameters:<br> <ul><li><b>ArkUI_NodeComponentEvent.data[0].f32</b>: X coordinate of the click relative to the upper left corner of theclicked component's original area, in vp.</li><li><b>ArkUI_NodeComponentEvent.data[1].f32</b>: Y coordinate of the click relative to the upper left corner of theclicked component's original area, in vp.</li><li><b>ArkUI_NodeComponentEvent.data[2].f32</b>: event timestamp. It is the interval between the time when the eventis triggered and the time when the system starts, in microseconds.</li><li><b>ArkUI_NodeComponentEvent.data[3].i32</b>: event input device. The value <b>1</b> indicates the mouse,</li><li><b>2</b> indicates the touchscreen, and <b>4</b> indicates the key.</li><li><b>ArkUI_NodeComponentEvent.data[4].f32</b>: X coordinate of the click relative to the upper left corner of theapplication window, in vp.</li><li><b>ArkUI_NodeComponentEvent.data[5].f32</b>: Y coordinate of the click relative to the upper left corner of theapplication window, in vp.</li><li><b>ArkUI_NodeComponentEvent.data[6].f32</b>: X coordinate of the click relative to the upper left corner of theapplication screen, in vp.</li><li><b>ArkUI_NodeComponentEvent.data[7].f32</b>: Y coordinate of the click relative to the upper left corner of theapplication screen, in vp.</li></ul> |
| NODE_ON_TOUCH_INTERCEPT | Defines event interception.This event is triggered when the component is touched. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). <br> |
| NODE_EVENT_ON_VISIBLE_AREA_CHANGE | Defines the visible area change event.This event is triggered when the ratio of the component's visible area to its total area is greater than or lessthan the threshold.Before registering this event, you must set <b>NODE_VISIBLE_AREA_CHANGE_RATIO</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <ul><li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: how the ratio of the component's visible area to its total areachanges compared to the previous one. The value <b>1</b> indicates an increase, and <b>0</b> indicates adecrease.</li><li><b>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total area when thiscallback is invoked.</li></ul> |
| NODE_ON_HOVER | Defines the event triggered when the mouse pointer is moved over or away from the component. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <ul><li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: whether the mouse pointer is hovered over the component.The value <b>1</b> indicates that the mouse pointer is hovered over the component, and <b>0</b> indicates thatthe mouse pointer is moved away from the component.</li></ul> |
| NODE_ON_MOUSE | Defines the click event.This event is triggered when the component is clicked by a mouse device button or when the mouse pointer moveswithin the component. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). <br> |
| NODE_EVENT_ON_ATTACH | Defines the attach event.This event is triggered when the component is attached. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_EVENT_ON_DETACH | Defines the detach event.This event is triggered when the component is detached. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_ON_ACCESSIBILITY_ACTIONS = 13 | Defines the accessibility action event.This event is triggered when The accessibility operation type has been set andcorresponding operations have been carried out. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].u32</b>: accessibility action type，the union type is[ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype) <br> |
| NODE_ON_PRE_DRAG = 14 | Notifies the listener of the interaction state prior to a drop and drop operation.This event is triggered when a drag operation is about to start on a draggable item. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <ul><li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: corresponds to {@link ArkUI_PreDragStatus}.</li></ul> |
| NODE_ON_DRAG_START = 15 | Called when the user starts to drag an iteA drag operation is recognized only when the dragged item is moved far enough. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. <br> |
| NODE_ON_DRAG_ENTER = 16 | Called when a dragged item enters the boundaries of the current component.The current component refers to the component that listens for this event. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. <br> |
| NODE_ON_DRAG_MOVE = 17 | Called when a dragged item moves in the current component.The current component refers to the component that listens for this event. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. <br> |
| NODE_ON_DRAG_LEAVE = 18 | Called when a dragged item leaves the boundaries of the current component.The current component refers to the component that listens for this event. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. <br> |
| NODE_ON_DROP = 19 | Called when a dragged item is dropped on the current component.The component can obtain the drag data for processing through the callback.The current component refers to the component that listens for this event. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. <br> |
| NODE_ON_DRAG_END = 20 | Called when a drag operation ends.The drag source can obtain the drag result by registering this callback.A drag operation ends when the dragged item is released.When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. <br> |
| NODE_ON_KEY_EVENT = 21 | Defines the event triggered when a key event occurs.The callback can be triggered during interactions with a focused window using an external keyboard or other inputdevice. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br><br>**起始版本：** 14 |
| NODE_ON_KEY_PRE_IME = 22 | Defines the event triggered before the input method responds to the key action.If the return value of this callback is <b>true</b>, it is considered that the key event has been consumed, andsubsequent event callbacks (<b>keyboardShortcut</b>, input method events, <b>onKeyEvent</b>) will be interceptedand no longer triggered.The callback can be triggered during interactions with a focused window using an external keyboard or other inputdevice. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br><br>**起始版本：** 14 |
| NODE_ON_FOCUS_AXIS = 23 | Defines the event triggered when the bound component receives a focus axis event after gaining focus.The event callback is triggered by interactions with a joystick and a focused component. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). <br><br>**起始版本：** 15 |
| NODE_DISPATCH_KEY_EVENT = 24 | Dispatch key event on the component node.When the component node receives a key event, this callback will be triggered instead of dispatching event to itschildren. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br><br>**起始版本：** 15 |
| NODE_ON_AXIS = 25 | Defines the event triggered when the bound component receives an axis event.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). <br><br>**起始版本：** 17 |
| NODE_ON_CLICK_EVENT = 26 | Defines the event triggered when the bound component is clicked.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). <br><br>**起始版本：** 18 |
| NODE_ON_HOVER_EVENT = 27 | 定义鼠标指针移至组件上方或远离组件时触发的事件。 <br> 当鼠标指针移到组件上方或远离组件时触发该事件。 <br> 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合类型为[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)。 <br><br>**起始版本：** 17 |
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT = 28 | Sets the callback for the NODE_EVENT_ON_VISIBLE_AREA_CHANGE event, which limits the callback interval.The callback is triggered when the ratio of the component's visible area to its total area is greater than orless than the threshold. Before registering the callback, you must configure the threshold and update intervalusing <b>NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <ul><li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: how the ratio of the component's visible area to its total areachanges compared to the previous one. The value <b>1</b> indicates an increase, and <b>0</b> indicatesa decrease.</li><li><b>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total areawhen this callback is invoked.</li></ul><br>**起始版本：** 17 |
| NODE_ON_HOVER_MOVE = 29 | Defines the hover event.The event is triggered when the pointer is hovered by a pen device.within the component. <br> When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object. <br><br>**起始版本：** 15 |
| NODE_ON_SIZE_CHANGE = 30 | 定义尺寸变化事件，当组件尺寸发生变化时会触发该事件。<br>事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含四个参数：<ul><li>ArkUI_NodeComponentEvent.data[0].f32：尺寸组件变化前的宽度。</li><li>ArkUI_NodeComponentEvent.data[1].f32：尺寸组件变化前的高度。</li><li>ArkUI_NodeComponentEvent.data[2].f32：尺寸组件变化后的宽度。</li><li>ArkUI_NodeComponentEvent.data[3].f32：尺寸组件变化后的高度。</li></ul><br>**起始版本：** 21 |
| NODE_ON_COASTING_AXIS_EVENT = 31 | Defines the coasting axis event.The event is triggered when user swipes with two fingers on the touchpad, the system constructssliding events based on the speed at the moment the fingers are lifted, according to a certaindecay curve. You can listen for such events to handle the flick effect immediately after theregular axis events. <br> When the event callback occurs, the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object through [OH_ArkUI_NodeEvent_GetInputEvent](capi-native-node-h.md#oh_arkui_nodeevent_getinputevent).And the [ArkUI_CoastingAxisEvent](capi-arkui-eventmodule-arkui-coastingaxisevent.md) object can be obtained from the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)object through [OH_ArkUI_UIInputEvent_GetCoastingAxisEvent](capi-ui-input-event-h.md#oh_arkui_uiinputevent_getcoastingaxisevent). <br><br>**起始版本：** 22 |
| NODE_ON_CHILD_TOUCH_TEST = 32 | Defines the pre-touch test of sub component in touch events. Called to specify how to perform the touch test on the children of this component.The event is triggered when the component is touched. <br> When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_TouchTestInfo](capi-arkui-eventmodule-arkui-touchtestinfo.md) object. <br><br>**起始版本：** 22 |
| NODE_ON_DIGITAL_CROWN = 33 | Defines the crown event.This event is triggered when the crown is rotated. <br> When the event callback occurs, the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. <br><br>**起始版本：** 24 |
| NODE_ON_CUSTOM_OVERFLOW_SCROLL = 34 | Defines the event is triggered when the <b>ARKUI_NODE_CUSTOM</b> content is scrolled.The event is triggered when the component's content is scrolled. <br> When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameters:<br> ArkUI_NodeComponentEvent.data[0].i32: id of scrolling child component. <br> ArkUI_NodeComponentEvent.data[1].f32: offset of the frame scrolling, measured in px.<br>**起始版本：** 24 |
| NODE_ON_STACK_OVERFLOW_SCROLL = 35 | Defines the event is triggered when the <b>ARKUI_NODE_STACK</b> content is scrolled.The event is triggered when the component's content is scrolled. <br> When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameters:<br> ArkUI_NodeComponentEvent.data[0].i32: id of scrolling child component. <br> ArkUI_NodeComponentEvent.data[1].f32: offset of the frame scrolling, measured in px.<br>**起始版本：** 24 |
| NODE_ON_NEED_SOFTKEYBOARD = 36 | Defines the event triggered when the component is focused and need to decide whether softkeyboard is needed.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.<br>**起始版本：** 24 |
| NODE_ON_GESTURE_COLLECT_INTERCEPT = 37 | This callback is invoked when the events and gestures on this node andhigher-priority nodes are collected. <br> This callback is used to intervene in the collection result of events and gestures. <br> When the event callback occurs, the [ArkUI_GestureCollectInterceptInfo](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md) object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. <br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_ON_DETECT_RESULT_UPDATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT | Triggers onDetectResultUpdate callbackwhen the text is set to TextDataDetectorConfig and recognized successfully.Trigger this event when TextDataDetectorConfig is set and recognized successfully.<br> When the event callback occurs, the event parameter[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)The union type in the object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)contains 1 parameter<br> <b>ArkUI_StringAsyncEvent.pStr</b>：Indicates the result of text recognition, in Json format.<br> |
| NODE_TEXT_SPAN_ON_LONG_PRESS = 1001 | Defines the long press event for span.The event is triggered when the span is long pressed.When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object.<br>**起始版本：** 20 |
| NODE_TEXT_ON_TEXT_SELECTION_CHANGE = 1002 | 定义文本选择位置改变时触发的事件。<br> 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含两个参数：<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>：文本选择区域的起始位置。<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>：文本选择区域的结束位置。<br>**起始版本：** 26.0.0 |
| NODE_TEXT_ON_COPY = 1003 | Defines the event triggered when the copy button on the pasteboard, which displays when the text boxis long pressed, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_ON_WILL_COPY = 1004 | Defines the event triggered before copying text.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_IMAGE_ON_COMPLETE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE | Defines the image loading success event.This event is triggered when an image is successfully loaded or decoded. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains nine parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: loading status. The value <b>0</b> indicates that the image isloaded successfully, and the value <b>1</b> indicates that the image is decoded successfully. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: width of the image, in px. <br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: height of the image, in px. <br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>: width of the component, in px. <br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>: height of the component, in px. <br> <b>ArkUI_NodeComponentEvent.data[5].f32</b>: offset of the rendered content relative to the component on thex-axis, in px. <br> <b>ArkUI_NodeComponentEvent.data[6].f32</b>: offset of the rendered content relative to the component on they-axis, in px. <br> <b>ArkUI_NodeComponentEvent.data[7].f32</b>: actual rendered width of the image, in px. <br> <b>ArkUI_NodeComponentEvent.data[8].f32</b>: actual rendered height of the image, in px. |
| NODE_IMAGE_ON_ERROR | Defines the image loading failure event.This event is triggered when an error occurs during image loading. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>error code:<br> 401: The image could not be obtained because the image path is invalid. <br> 103101: The image format is not supported. |
| NODE_IMAGE_ON_SVG_PLAY_FINISH | Defines the SVG animation playback completion event.This event is triggered when the animation playback in the loaded SVG image is complete. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_IMAGE_ON_DOWNLOAD_PROGRESS | Defines image download process event.This event is triggered when downloading webpage images from page components.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].u32</b>: the num of bytes downloaded. <br> <b>ArkUI_NodeComponentEvent.data[1].u32</b>: the total number of bytes to download. |
| NODE_TOGGLE_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE | Defines the event triggered when the toggle status changes. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:** <br> <ul><li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: toggle status. <b>1</b>: on; <b>0</b>: off.</li></ul> |
| NODE_TEXT_INPUT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT | Defines the event triggered when the text input content changes. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text input. |
| NODE_TEXT_INPUT_ON_SUBMIT | Defines the event triggered when the Enter key of the text input method is pressed. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: Enter key type of the input method. |
| NODE_TEXT_INPUT_ON_CUT | Defines the event triggered when the cut button on the pasteboard, which displays when the text boxis long pressed, is clicked. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is cut. |
| NODE_TEXT_INPUT_ON_PASTE | Defines the event triggered when the paste button on the pasteboard, which displays when the text boxis long pressed, is clicked. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is pasted<br> Since 26.0.0, the callback can return whether the paste is allowed. |
| NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE | Defines the event triggered when the text selection position changes. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: start position of the text selection area. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: end position of the text selection area. <br> |
| NODE_TEXT_INPUT_ON_EDIT_CHANGE | Defines the event triggered when the input status changes. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: <b>true</b> indicates that text input is in progress. <br> |
| NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE | textInput This event is triggered when the input content changes.Conditions for triggering this event: When the input content changes. <br> When the event callback occurs, the union type in the event parameter[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 2 parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: Indicates the width of the text. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: Indicates the height of the text. <br> |
| NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR | Defines the event triggered when matching with the regular expression specified by<b>NODE_TEXT_INPUT_INPUT_FILTER</b> fails. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: content that is filtered out when regular expression matching fails. <br> |
| NODE_TEXT_INPUT_ON_CONTENT_SCROLL | This callback is triggered when the text content is scrolled. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: Indicates the horizontal offset of the text in the content area. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: Indicates the vertical coordinate offset of <br> the text in the content area. <br> |
| NODE_TEXT_INPUT_ON_WILL_INSERT = 7009 | 定义在将要输入时，触发回调的枚举值。事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：插入的值的位置信息。<br> 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：插入的值。 |
| NODE_TEXT_INPUT_ON_DID_INSERT = 7010 | 定义在输入完成时，触发回调的枚举值。事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：插入的值的位置信息。<br> 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：插入的值。 |
| NODE_TEXT_INPUT_ON_WILL_DELETE = 7011 | 定义在将要删除时，触发回调的枚举值。事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：删除的值的位置信息。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br> 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：删除的值。 |
| NODE_TEXT_INPUT_ON_DID_DELETE = 7012 | 定义在删除完成时，触发回调的枚举值。事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：删除的值的位置信息。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br> 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：删除的值。 |
| NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT = 7013 | Defines the event triggered when content (including preview text) changes in the <b>TextInput</b>component.When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). <br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters: <br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the <b>TextInput</b> component.<b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the <b>TextInput</b> component.<b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the <b>TextInput</b> component.<br>**起始版本：** 15 |
| NODE_TEXT_INPUT_ON_WILL_CHANGE = 7014 | Defines the event triggered before content changesWhen the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). <br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters: <br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the <b>TextInput</b> component.<b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the <b>TextInput</b> component.<b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the <b>TextInput</b> component.<br>**起始版本：** 20 |
| NODE_TEXT_INPUT_ON_COPY = 7015 | Defines the event triggered when the copy button on the pasteboard, which displays when text isselected, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_ON_WILL_COPY = 7016 | Defines the event triggered before copying text.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_ON_WILL_CUT = 7017 | Defines the event triggered before cutting text.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is cut.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA | Defines the event triggered when the input in the text box changes. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text entered. |
| NODE_TEXT_AREA_ON_PASTE | Defines the event triggered when the paste button on the pasteboard, which displays when the text box islong pressed, is clicked. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is pasted<br> Since 26.0.0, the callback can return whether the paste is allowed. |
| NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE | Defines the event triggered when the text selection position changes. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: start position of the text selection area. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: end position of the text selection area. <br> |
| NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR | Defines the event triggered when matching with the regular expression specified by<b>NODE_TEXT_AREA_INPUT_FILTER</b> fails. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: content that is filtered out when regular expression matching fails. <br> |
| NODE_TEXT_AREA_ON_CONTENT_SCROLL | This callback is triggered when the text content is scrolled. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: Indicates the horizontal offset of the text in the content area. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: Indicates the vertical coordinate offset of <br> the text in the content area. <br> |
| NODE_TEXT_AREA_ON_EDIT_CHANGE | Defines the event triggered when the input status changes. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: <b>true</b> indicates that text input is in progress. <br> |
| NODE_TEXT_AREA_ON_SUBMIT | Defines the event triggered when the Enter key on the keyboard is pressed for the multi-line text box.This event is not triggered when <b>keyType</b> is <b>ARKUI_ENTER_KEY_TYPE_NEW_LINE</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: type of the Enter key. |
| NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE | textArea This event is triggered when the input content changes.Conditions for triggering this event: When the input content changes. <br> When the event callback occurs, the union type in the event parameter [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 2 parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: Indicates the width of the text. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: Indicates the height of the text. <br> |
| NODE_TEXT_AREA_ON_WILL_INSERT = 8008 | 定义在将要输入时，触发回调的枚举值。事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：插入的值的位置信息。<br> 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：插入的值。 |
| NODE_TEXT_AREA_ON_DID_INSERT = 8009 | 定义在输入完成时，触发回调的枚举值。事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：插入的值的位置信息。<br> 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：插入的值。 |
| NODE_TEXT_AREA_ON_WILL_DELETE = 8010 | 定义在将要删除时，触发回调的枚举值。事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：删除的值的位置信息。<br> 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。<br> 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：删除的值。 |
| NODE_TEXT_AREA_ON_DID_DELETE = 8011 | Defines the event triggered when text is deleted.The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <br> value.f32: position of the text deleted, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. <br> value.i32: direction for deleting the text, with the index of <b>1</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. The value <b>0</b> indicates backward-delete, and <b>1</b> indicatesforward-delete. <br> buffer: string value of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetStringValue</b>. |
| NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT = 8012 | Defines the event triggered when content (including preview text) changes in the <b>TextArea</b>component.When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). <br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters: <br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the <b>TextArea</b> component.<b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the <b>TextArea</b> component.<b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the <b>TextArea</b> component.<br>**起始版本：** 15 |
| NODE_TEXT_AREA_ON_WILL_CHANGE = 8013 | Defines the event triggered before content changes.When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). <br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters: <br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the <b>TextArea</b> component.<b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the <b>TextArea</b> component.<b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the <b>TextArea</b> component.<br>**起始版本：** 20 |
| NODE_TEXT_AREA_ON_COPY = 8014 | 定义长按输入框文本弹出菜单后点击复制按钮触发的事件。<br> 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：复制的文本。<br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_ON_WILL_COPY = 8015 | Defines the event triggered before copying text.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_ON_CUT = 8016 | 定义长按输入框文本弹出菜单后点击剪切按钮触发的事件。<br> 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数：<br> <b>ArkUI_StringAsyncEvent.pStr</b>：剪切后的文本。<br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_ON_WILL_CUT = 8017 | Defines the event triggered before cutting text.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is cut.<br>**起始版本：** 26.0.0 |
| NODE_CHECKBOX_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX | Defines the event triggered when the selected status of the <b>ARKUI_NODE_CHECKBOX</b> component changes.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> <b>ArkUI_NodeComponentEvent.data[0].i32</b><b>1</b>: selected; <b>0</b>: not selected.<br> |
| NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER | 定义ARKUI_NODE_DATE_PICKER列表组件的滚动触摸事件枚举值。触发该事件的条件：选择日期时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含3个参数：<ul><li>ArkUI_NodeComponentEvent.data[0].i32：表示选中时间的年。</li><li>ArkUI_NodeComponentEvent.data[1].i32：表示选中时间的月，取值范围：[0-11]。</li><li>ArkUI_NodeComponentEvent.data[2].i32：表示选中时间的天。</li></ul> |
| NODE_TIME_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER | 定义ARKUI_NODE_TIME_PICKER列表组件的滚动触摸事件枚举值。触发该事件的条件：选择时间时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含2个参数：<ul><li>ArkUI_NodeComponentEvent.data[0].i32：表示选中时间的时，取值范围：[0-23]。</li><li>ArkUI_NodeComponentEvent.data[1].i32：表示选中时间的分，取值范围：[0-59]。</li></ul> |
| NODE_TEXT_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER | 定义ARKUI_NODE_TEXT_PICKER列表组件的滚动触摸事件枚举值。触发该事件的条件：选择文本时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含1个参数：<ul><li>ArkUI_NodeComponentEvent.data[0...11].i32：表示选中数据的维度。</li></ul> |
| NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP = 15001 | 定义ARKUI_NODE_TEXT_PICKER列表组件的滚动触摸事件枚举值。触发该事件的条件：滑动选择文本项停止时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含1个参数：<ul><li>ArkUI_NodeComponentEvent.data[0...11].i32：表示选中数据的维度。</li></ul><br>**起始版本：** 14 |
| NODE_CALENDAR_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER | 定义NODE_CALENDAR_PICKER选中日期时触发的事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含3个参数：<ul><li>ArkUI_NodeComponentEvent.data[0].u32：选中的年。</li><li>ArkUI_NodeComponentEvent.data[1].u32：选中的月。</li><li>ArkUI_NodeComponentEvent.data[2].u32：选中的日。</li></ul> |
| NODE_SLIDER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER | Defines the event triggered when the <b>ARKUI_NODE_SLIDER</b> component is dragged or clicked.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br> <ul><li><b>ArkUI_NodeComponentEvent.data[0].f32</b>: current slider value.</li> <br> <li><b>ArkUI_NodeComponentEvent.data[1].i32</b>: state triggered by the event.</li><br> </ul> |
| NODE_RADIO_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO | Defines the event callback function triggered when an object is dragged or clicked by ARKUI_NODE_RADIO.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> **{@Link ArkUI_NodeComponentEvent} contains one parameter:**<br> <ul><li>ArkUI_NodeComponentEvent.data[0].i32: option button status.</li> <br> </ul> |
| NODE_IMAGE_ANIMATOR_EVENT_ON_START = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_ANIMATOR | Defines the event callback function triggered when the animation starts to play.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_IMAGE_ANIMATOR_EVENT_ON_PAUSE = 19001 | Defines the event callback function triggered when the animation playback is paused.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_IMAGE_ANIMATOR_EVENT_ON_REPEAT = 19002 | Defines the event callback function triggered when the animation playback is repeated.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_IMAGE_ANIMATOR_EVENT_ON_CANCEL = 19003 | Defines the event callback function when the animation playback returns to the initial state.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_IMAGE_ANIMATOR_EVENT_ON_FINISH = 19004 | Defines the event callback function triggered when the animation playback is complete or stopped.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP | Defines the callback triggered when the selected status of the <b>ARKUI_NODE_CHECKBOX_GROOUP</b>or checkbox changes.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> <b>ArkUI_StringAsyncEvent.pStr contains two parameters</b>Name: The names of the selected checkboxes;Status:0: All checkboxes are selected.1: Some checkboxes are selected.2: No checkboxes are selected. <br><br>**起始版本：** 15 |
| NODE_TEXT_EDITOR_ON_SELECTION_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR | 定义TextEditor组件中选区或光标位置发生变化时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含两个参数：<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：选区起始索引。<br><b>ArkUI_NodeComponentEvent.data[1].i32</b>：选区结束索引。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_READY | 定义TextEditor组件首次初始化完成时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_PASTE | 定义TextEditor组件执行粘贴时触发的事件。系统会根据回调函数返回值判断是否拦截组件的默认行为。 <br> 可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。 <br> 返回值中索引为0的value.i32表示是否拦截组件的默认行为。 <br> 0：不拦截。1：拦截。 <br><br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_EDITING_CHANGE | 定义TextEditor组件编辑状态发生变化时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含一个参数：<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：组件的编辑状态。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_SUBMIT | 定义TextEditor组件输入法的回车键被按下时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含一个参数：<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：输入法的回车键类型[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_CUT | 定义TextEditor组件执行剪切时触发的事件。系统会根据回调函数返回值判断是否拦截组件的默认行为。 <br> 可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。 <br> 返回值中索引为0的value.i32表示是否拦截组件的默认行为。 <br> 0：不拦截。1：拦截。 <br><br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_COPY | 定义TextEditor组件执行复制时触发的事件。系统会根据回调函数返回值判断是否拦截组件的默认行为。 <br> 可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。 <br> 返回值中索引为0的value.i32表示是否拦截组件的默认行为。 <br> 0：不拦截。1：拦截。 <br><br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_WILL_CHANGE | 定义TextEditor组件在内容将要改变时触发的事件。<br>在任何导致文本内容发生变化的操作生效之前会触发该回调，开发者可根据回调事件中的信息决定是否拦截本次内容变更。<br>当事件回调发生时，可以通过[OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent](capi-native-node-h.md#oh_arkui_nodeevent_gettexteditoronwillchangeevent)从[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获得[OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md)对象。<br>使用OH_ArkUI_TextEditorChangeEvent_XXX系列接口可以从该对象中获取更多信息。<br>系统会根据回调函数返回值判断当前内容是否允许被更改。<br>可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。<br>返回值中索引为0的value.i32表示当前内容是否允许被更改。<b>0</b>：不允许更改。<b>1</b>：允许更改。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_DID_CHANGE | 定义TextEditor组件在内容改变时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含四个参数：<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：文本变化前将要被替换的文本范围的起始索引。<br><b>ArkUI_NodeComponentEvent.data[1].i32</b>：文本变化前将要被替换的文本范围的结束索引。<br><b>ArkUI_NodeComponentEvent.data[2].i32</b>：文本变化后新增内容的文本范围的起始索引。<br><b>ArkUI_NodeComponentEvent.data[3].i32</b>：文本变化后新增内容的文本范围的结束索引。<br>**起始版本：** 24 |
| NODE_SWIPER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER | Defines the event triggered when the index of the currently displayed element of this<b>ARKUI_NODE_SWIPER</b> instance changes.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<ul><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_EVENT_ON_ANIMATION_START | Defines the event triggered when the switching animation of this <b>ARKUI_NODE_SWIPER</b> instance starts.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains five parameters:<ul><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li><li>ArkUI_NodeComponentEvent.data[1].i32: index of the target element to switch to.</li><li>ArkUI_NodeComponentEvent.data[2].f32: offset of the currently displayed element relative to thestart position of the swiper along the main axis.</li><li>ArkUI_NodeComponentEvent.data[3].f32: offset of the target element relative to the start positionof the swiper along the main axis.</li><li>ArkUI_NodeComponentEvent.data[4].f32: hands-off velocity.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_EVENT_ON_ANIMATION_END | Defines the event triggered when the switching animation of this <b>ARKUI_NODE_SWIPER</b> instance ends.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<ul><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li><li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to thestart position of the swiper along the main axis.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_EVENT_ON_GESTURE_SWIPE | Defines the event triggered on a frame-by-frame basis when the page is turned by a swipe in this<b>ARKUI_NODE_SWIPER</b> instance.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<ul><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li><li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to thestart position of the swiper along the main axis.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL | Define the <b>ARKUI_NODE_SWIPER</b> to listen for Swiper page slide events.Instruction: <br> 1. If the {@link ArkUI_SwiperDisplayModeType} attribute is set to <br> ARKUI_SWIPER_DISPLAY_MODE_AUTO_LINEAR, the interface does not take effect. <br> 2, circular scenario, set prevMargin and nextMargin attributes, <br> so that Swiper front and back end display the same page, the interface does not take effect. <br> 3. During page sliding, the ContentDidScrollCallback callback is <br> triggered frame-by-frame for all pages in the window. <br> For example, when there are two pages in the window with subscripts 0 and 1, <br> callbacks with index values 0 and 1 are triggered twice per frame. <br> 4, set the swipeByGroup parameter of the displayCount property to <br> true if at least one page in the same group is in the window, <br> A callback is triggered for all pages in the group. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains four parameters:<ul><li>ArkUI_NodeComponentEvent.data[0].i32: indicates the index of the Swiper component,which is consistent with the index change in the onChange event.</li><li>ArkUI_NodeComponentEvent.data[1].i32: The index of a page in the window.</li><li>ArkUI_NodeComponentEvent.data[2].f32: The proportion of page movement relative tothe start position of the Swiper spindle (selectedIndex corresponds to the start position of the page).</li><li>ArkUI_NodeComponentEvent.data[3].f32: The length of the page in the axis direction.</li></ul><br>**起始版本：** 12 |
| NODE_SWIPER_EVENT_ON_SELECTED = 1001005 | Defines the event triggered when the selected index of the <b>ARKUI_NODE_SWIPER</b> changed.This event is triggered under the following scenarios: <br> 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meetsthe threshold for page turning. <br> 2. When the page is changed programmatically using either <b>NODE_SWIPER_INDEX</b> or<b>NODE_SWIPER_SWIPE_TO_INDEX</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<ul><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently selected element.</li></ul><br>**起始版本：** 18 |
| NODE_SWIPER_EVENT_ON_UNSELECTED = 1001006 | Defines the event triggered when the selected index of the <b>ARKUI_NODE_SWIPER</b> changed.This event is triggered under the following scenarios: <br> 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meetsthe threshold for page turning. <br> 2. When the page is changed programmatically using either <b>NODE_SWIPER_INDEX</b> or<b>NODE_SWIPER_SWIPE_TO_INDEX</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<ul><li>ArkUI_NodeComponentEvent.data[0].i32: the index of the element becomes unselected.</li></ul><br>**起始版本：** 18 |
| NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL = 1001007 | Defines the event triggered when content in the swiper component will scroll.Instructions: Before page scrolling, the </b>ContentWillScrollCallback</b> callback is invoked. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains three parameters:<ul><li>ArkUI_NodeComponentEvent.data[0].i32: the index value of the current child page.</li><li>ArkUI_NodeComponentEvent.data[1].i32: the index value of the child page that will display.</li><li>ArkUI_NodeComponentEvent.data[2].f32: the sliding offset of each frame.Positive numbers indicating slide backward(e.g. from index=1 to index=0), negative numbers indicatingslide forward(e.g. from index=0 to index=1).</li></ul><br>**起始版本：** 15 |
| NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED = 1001008 | Defines the <b>ARKUI_NODE_SWIPER</b> scroll state change event.This event is triggered when the scroll state of the <b>Swiper</b> component changes during user dragging,during the animation phase after the user lifts their finger, or upon stopping of scrolling.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<ul><li>ArkUI_NodeComponentEvent.data[0].i32: current scroll state. The parameter type is[ArkUI_ScrollState](capi-scroll-h.md#arkui_scrollstate).</li></ul><br>**起始版本：** 20 |
| NODE_SCROLL_EVENT_ON_SCROLL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SCROLL | Event triggered when scrolling occurs. This event is triggered under the following scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: horizontal scrolling offset.<br>*ArkUI_NodeComponentEvent.data[1].f32**: vertical scrolling offset. |
| NODE_SCROLL_EVENT_ON_SCROLL_FRAME_BEGIN | Event triggered when the scrollable container starts scrolling in each frame. The **List**, **Scroll**,and **WaterFlow** components support this event since API version 12, and the **Grid** component supports thisevent since API version 22.<br>This event is triggered under the following scenarios:<br>1. This event is triggered when scrolling is started by the scrollable component (supports keyboard, mouse,and other input methods that trigger scrolling).<br>2. This event is not triggered when the controller API is called.<br>3. This event is not triggered when the component bounces back out of bounds.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: amount to scroll by.<br>*ArkUI_NodeComponentEvent.data[1].i32**: current scroll state.<br>*::ArkUI_NodeComponentEvent** contains one return value:<br>*ArkUI_NodeComponentEvent.data[0].f32**: The event handler can work out the amount by which the componentneeds to scroll based on the real-world situation and return the result in this parameter. |
| NODE_SCROLL_EVENT_ON_WILL_SCROLL | Event triggered when the scrollable container is about to scroll. This event is triggered under thefollowing scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame, in vp. The offset is positive whenthe content is scrolled left and negative when the content is scrolled right.<br>*ArkUI_NodeComponentEvent.data[1].f32**: scroll offset of each frame, in vp. The offset is positive whenthe content is scrolled up and negative when the content is scrolled down.<br>*ArkUI_NodeComponentEvent.data[2].i32**: current scroll state. The parameter type is[ArkUI_ScrollState](capi-scroll-h.md#arkui_scrollstate).<br>*ArkUI_NodeComponentEvent.data[3].i32**: current scroll source. The parameter type is[ArkUI_ScrollSource](capi-scroll-h.md#arkui_scrollsource). |
| NODE_SCROLL_EVENT_ON_DID_SCROLL | Event triggered when the scrollable container scrolls. This event is triggered under the followingscenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame, in vp. The offset is positive whenthe content is scrolled left and negative when the content is scrolled right.<br>*ArkUI_NodeComponentEvent.data[1].f32**: scroll offset of each frame, in vp. The offset is positive whenthe content is scrolled up and negative when the content is scrolled down.<br>*ArkUI_NodeComponentEvent.data[2].i32**: current scroll state. The parameter type is[ArkUI_ScrollState](capi-scroll-h.md#arkui_scrollstate). |
| NODE_SCROLL_EVENT_ON_SCROLL_START | Event triggered when the scrollable container starts scrolling. The **List**, **Scroll**, and **WaterFlowcomponents support this event since API version 12, and the **Grid** component supports this event since APIversion 22.<br>This event is triggered under the following scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. The controller API is called to start the scrolling, accompanied by a transition animation.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_SCROLL_EVENT_ON_SCROLL_STOP | Defines the event triggered when scrolling of the <b>ARKUI_NODE_SCROLL</b> component stops.Notes for triggering the event:<br> 1. This event is triggered when scrolling is stopped by the <b>ARKUI_NODE_SCROLL</b> component or other inputsettings, such as keyboard and mouse operations. <br> 2. This event is triggered when the controller API is called, accompanied by a transition animation. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_SCROLL_EVENT_ON_SCROLL_EDGE | Event triggered when the scrollable container reaches the scroll boundary. This event is triggered underthe following scenarios:<br>1. Scrolling reaches the edge after being started by the scrollable component (supports keyboard, mouse, andother input methods that trigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:<br>*ArkUI_NodeComponentEvent.data[0].i32**: edge (top, bottom, left, or right) that the scrolling reaches. |
| NODE_SCROLL_EVENT_ON_REACH_START | Event triggered when the scrollable component reaches the start edge.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_SCROLL_EVENT_ON_REACH_END | Event triggered when the scrollable component reaches the end edge.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_SCROLL_EVENT_ON_WILL_STOP_DRAGGING | 定义当用户即将释放可滚动容器组件上的拖动时的回调<br>**起始版本：** 20 |
| NODE_SCROLL_EVENT_ON_DID_ZOOM | 定义Scroll组件缩放开始回调。触发该事件的条件：Scroll组件缩放开始时触发。定义Scroll组件缩放回调。触发该事件的条件：Scroll组件缩放每帧完成时触发。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数: <b>ArkUI_NodeComponentEvent.data[0].f32</b>: 当前缩放比例。<br>**起始版本：** 20 |
| NODE_SCROLL_EVENT_ON_ZOOM_START | 定义Scroll组件缩放开始回调。触发该事件的条件：Scroll组件缩放开始时触发。 <br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。<br><br>**起始版本：** 20 |
| NODE_SCROLL_EVENT_ON_ZOOM_STOP | 定义Scroll组件缩放停止回调。触发该事件的条件：Scroll组件缩放停止时触发。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数。<br>**起始版本：** 20 |
| NODE_SCROLL_EVENT_ON_WILL_START_DRAGGING = 1002013 | Defines the callback for when the scrollable will start dragging.This event is triggered when the scrollable will start dragging. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains no parameters:<br>**起始版本：** 21 |
| NODE_SCROLL_EVENT_ON_DID_STOP_DRAGGING = 1002014 | Defines the callback for when the scrollable did end dragging.This event is triggered when the scrollable did end dragging. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter: <br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: whether start fling animation. <br><br>**起始版本：** 21 |
| NODE_SCROLL_EVENT_ON_WILL_START_FLING = 1002015 | Defines the callback for when the scrollable will start fling.This event is triggered when the scrollable will start fling. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains no parameters:<br>**起始版本：** 21 |
| NODE_SCROLL_EVENT_ON_DID_STOP_FLING = 1002016 | Defines the callback for when the scrollable did end fling.This event is triggered when the scrollable did end fling. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains no parameters:<br>**起始版本：** 21 |
| NODE_LIST_ON_SCROLL_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST | Event triggered when a child component of [ARKUI_NODE_LIST](capi-native-node-h.md#arkui_nodetype) enters or leaves the list display area.This event is triggered in the following scenarios:<br>This event is triggered once when the list is initialized and when the index of the first child component orthe last child component in the list display area changes.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].i32**: index of the first child component in the list display area.<br>*ArkUI_NodeComponentEvent.data[1].i32**: index of the last child component in the list display area.<br>*ArkUI_NodeComponentEvent.data[2].i32**: index of the center child component in the list display area. |
| NODE_LIST_ON_WILL_SCROLL | Event triggered when the [ARKUI_NODE_LIST](capi-native-node-h.md#arkui_nodetype) component is about to scroll. This event is triggered inthe following scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame. The offset is positive when the listis scrolled up and negative when the list is scrolled down.<br>*ArkUI_NodeComponentEvent.data[1].i32**: current scroll state. The parameter type is[ArkUI_ScrollState](capi-scroll-h.md#arkui_scrollstate).<br>*ArkUI_NodeComponentEvent.data[2].i32**: current scroll source. The parameter type is[ArkUI_ScrollSource](capi-scroll-h.md#arkui_scrollsource). |
| NODE_LIST_ON_DID_SCROLL | Event triggered when the [ARKUI_NODE_LIST](capi-native-node-h.md#arkui_nodetype) component scrolls. This event is triggered under thefollowing scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame. The offset is positive when the listis scrolled up and negative when the list is scrolled down.<br>*ArkUI_NodeComponentEvent.data[1].i32**: current scroll state. |
| NODE_LIST_ON_SCROLL_VISIBLE_CONTENT_CHANGE | 定义ARKUI_NODE_LIST当前显示内容发生改变的时候触发事件枚举值。触发该事件的条件 ：列表初始化时会触发一次，List显示区域内第一个子组件的索引值或最后一个子组件的索引值有变化时会触发。计算触发条件时，每一个ListItem、ListItemGroup中的header或footer都算一个子组件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含6个参数：<b>ArkUI_NodeComponentEvent.data[0].i32</b>：List显示区域内第一个子组件的索引值。<b>ArkUI_NodeComponentEvent.data[1].i32</b>：List显示区域起始端在ListItemGroup中的区域。类型为[ArkUI_ListItemGroupArea](capi-list-h.md#arkui_listitemgrouparea)。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：List显示区域起始端在ListItemGroup中的ListItem索引号，如果List显示区域起始端不在ListItem上，该值为-1。<b>ArkUI_NodeComponentEvent.data[3].i32</b>：List显示区域内最后一个子组件的索引值。<b>ArkUI_NodeComponentEvent.data[4].i32</b>：List显示区域末尾端在ListItemGroup中的区域。类型为[ArkUI_ListItemGroupArea](capi-list-h.md#arkui_listitemgrouparea)。<b>ArkUI_NodeComponentEvent.data[5].i32</b>：List显示区域末尾端在ListItemGroup中的ListItem索引号，如果List显示区域末尾端不在ListItem上，该值为-1。<br>**起始版本：** 15 |
| NODE_LIST_ON_EDIT_MODE_CHANGE = 1003004 | 定义List组件编辑模式状态变更事件枚举值。触发该事件的条件 ：1. 设置NODE_LIST_ENABLE_EDIT_MODE属性改变编辑模式状态。2. 当NODE_LIST_EDIT_MODE_OPTIONS开启双指滑动多选时，双指滑动触发多选状态变更。注册该事件回调是双指滑动进入多选状态的必要条件。如未注册该回调，双指滑动将不会进入多选状态。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<b>ArkUI_NodeComponentEvent.data[0].i32</b>：编辑模式状态。0：非编辑模式。1：编辑模式。<br>**起始版本：** 26.0.0 |
| NODE_LIST_ITEM_ON_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM | Defines the selected state change event of the <b>ListItem</b> component.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<b>ArkUI_NodeComponentEvent.data[0].i32</b>: selected state. <b>0</b>: not selected. <b>1</b>: selected.<br>**起始版本：** 26.0.0 |
| NODE_REFRESH_STATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_REFRESH | Defines the event triggered when the refresh state of the <b>ARKUI_NODE_REFRESH</b> object changes.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: refresh state. |
| NODE_REFRESH_ON_REFRESH | 定义ARKUI_NODE_REFRESH进入刷新状态时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数： |
| NODE_REFRESH_ON_OFFSET_CHANGE | 定义ARKUI_NODE_REFRESH下拉距离发生变化时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：下拉距离。 |
| NODE_ON_WILL_SCROLL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_WATER_FLOW | Event triggered when the **ARKUI_NODE_WATER_FLOW** component is about to scroll. This event is triggeredunder the following scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame. The offset is positive when thecontent is scrolled up and negative when the content is scrolled down.<br>*ArkUI_NodeComponentEvent.data[1].i32**: current scroll state. The parameter type is[ArkUI_ScrollState](capi-scroll-h.md#arkui_scrollstate).<br>*ArkUI_NodeComponentEvent.data[2].i32**: current scroll source. The parameter type is[ArkUI_ScrollSource](capi-scroll-h.md#arkui_scrollsource). |
| NODE_WATER_FLOW_ON_DID_SCROLL | 定义ARKUI_NODE_WATER_FLOW组件的滑动时触发事件枚举值。触发该事件的条件 ：1. 滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。2. 通过滚动控制器API接口调用。3. 越界回弹。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负。<b>ArkUI_NodeComponentEvent.data[1].i32</b>：当前滑动状态。 |
| NODE_WATER_FLOW_ON_SCROLL_INDEX | Defines the enumerated values of the event triggered,when the subcomponent of the start position or end position displayed in the current waterfall changes.Condition for triggering the event: <br> This event is triggered when the index value of the <br> first or last subcomponent in the waterfall display area changes. <br> When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains two parameters: <br> ArkUI_NodeComponentEvent.data[0].i32: The index value of the <br> start position of the currently displayed WaterFlow. <br> ArkUI_NodeComponentEvent.data[1].i32: The index value of <br> the end position of the currently displayed waterfall. |
| NODE_GRID_ON_SCROLL_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID | Event triggered when a child component of **ARKUI_NODE_GRID** enters or leaves the grid display area.This event is triggered under the following scenarios:<br>This event is triggered once when the grid is initialized and when the index of the first child component orthe last child component in the grid display area changes.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].i32**: index of the first child component in the grid display area.<br>*ArkUI_NodeComponentEvent.data[1].i32**: index of the last child component in the grid display area.<br>**起始版本：** 22 |
| NODE_GRID_ON_WILL_SCROLL = 1013001 | 定义ARKUI_NODE_GRID组件的滑动前触发事件枚举值。触发该事件的条件 ：1. 滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。2. 通过滚动控制器API接口调用。3. 越界回弹。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：每帧滚动的偏移量，Grid内容向上滚动时偏移量为正，向下滚动时偏移量为负。<b>ArkUI_NodeComponentEvent.data[1].i32</b>：当前滑动状态，参数类型[ArkUI_ScrollState](capi-scroll-h.md#arkui_scrollstate)。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：当前滚动的来源，参数类型[ArkUI_ScrollSource](capi-scroll-h.md#arkui_scrollsource)。<br>**起始版本：** 22 |
| NODE_GRID_ON_DID_SCROLL = 1013002 | 定义ARKUI_NODE_GRID组件的滑动时触发事件枚举值。触发该事件的条件 ：1. 滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。2. 通过滚动控制器API接口调用。3. 越界回弹。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：每帧滚动的偏移量，Grid内容向上滚动时偏移量为正，向下滚动时偏移量为负。<b>ArkUI_NodeComponentEvent.data[1].i32</b>：当前滑动状态。<br>**起始版本：** 22 |
| NODE_GRID_ON_SCROLL_BAR_UPDATE = 1013003 | 定义ARKUI_NODE_GRID组件每帧布局结束时触发用于设置滚动条的位置及长度的事件枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.i32：当前显示的网格起始位置的索引值。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.f32：当前显示的网格起始位置元素相对网格显示起始位置的偏移，单位vp。<br>**起始版本：** 22 |
| NODE_GRID_ON_ITEM_DRAG_START = 1013004 | 定义ARKUI_NODE_GRID组件拖拽子组件开始事件枚举值。触发该事件的条件：1. 设置NODE_GRID_EDIT_MODE为1。2. 在Grid子组件上长按并拖动产生足够位移距离时触发。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：当前拖拽点相对Grid组件的x坐标，单位vp。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.f32：当前拖拽点相对Grid组件的y坐标，单位vp。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为2的value.i32：被拖拽子组件在Grid组件中的索引值。<br>**起始版本：** 23 |
| NODE_GRID_ON_ITEM_DRAG_ENTER = 1013005 | 定义拖拽子组件进入当前Grid组件范围事件枚举值。触发该事件的条件：通过NODE_GRID_ON_ITEM_DRAG_START事件成功拖拽的子组件进入当前Grid组件范围。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：当前拖拽点相对Grid组件的x坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[1].f32</b>：当前拖拽点相对Grid组件的y坐标，单位vp。<br>**起始版本：** 23 |
| NODE_GRID_ON_ITEM_DRAG_MOVE = 1013006 | 定义拖拽子组件在当前Grid组件范围内移动事件枚举值。触发该事件的条件：通过NODE_GRID_ON_ITEM_DRAG_START事件成功拖拽的子组件在当前Grid组件范围内移动。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含4个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：当前拖拽点相对Grid组件的x坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[1].f32</b>：当前拖拽点相对Grid组件的y坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：被拖拽子组件在被拖拽Grid组件中的索引值。<b>ArkUI_NodeComponentEvent.data[3].i32</b>：被拖拽子组件当前位置在当前Grid组件中的索引值。<br>**起始版本：** 23 |
| NODE_GRID_ON_ITEM_DRAG_LEAVE = 1013007 | 定义拖拽子组件离开当前Grid组件范围事件枚举值。触发该事件的条件：通过NODE_GRID_ON_ITEM_DRAG_START事件成功拖拽的子组件离开当前Grid组件范围。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：当前拖拽点相对Grid组件的x坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[1].f32</b>：当前拖拽点相对Grid组件的y坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：被拖拽子组件在被拖拽Grid组件中的索引值。<br>**起始版本：** 23 |
| NODE_GRID_ON_ITEM_DROP = 1013008 | 定义松手释放拖拽子组件事件枚举值。触发该事件的条件：松手释放通过NODE_GRID_ON_ITEM_DRAG_START事件成功拖拽的子组件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含5个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：当前拖拽点相对Grid组件的x坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[1].f32</b>：当前拖拽点相对Grid组件的y坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：被拖拽子组件在被拖拽Grid中的索引值。<b>ArkUI_NodeComponentEvent.data[3].i32</b>：被拖拽子组件当前位置在当前Grid组件中的索引值。<b>ArkUI_NodeComponentEvent.data[4].i32</b>：被拖拽子组件是否成功释放，1表示释放位置在Grid组件范围内，0表示释放位置在Grid组件范围外。<br>**起始版本：** 23 |
| NODE_GRID_ON_EDIT_MODE_CHANGE = 1013009 | 定义Grid组件编辑模式状态变更事件枚举值。触发该事件的条件 ：1. 设置NODE_GRID_ENABLE_EDIT_MODE属性改变编辑模式状态。2. 当NODE_GRID_EDIT_MODE_OPTIONS开启双指滑动多选时，双指滑动触发多选状态变更。注册该事件回调是双指滑动进入多选状态的必要条件。如未注册该回调，双指滑动将不会进入多选状态。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<b>ArkUI_NodeComponentEvent.data[0].i32</b>：编辑模式状态。0：非编辑模式。1：编辑模式。<br>**起始版本：** 26.0.0 |
| NODE_GRID_ITEM_ON_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID_ITEM | Selected state change event of the **ARKUI_NODE_GRID_ITEM** component.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:<br>*ArkUI_NodeComponentEvent.data[0].i32**: **0** (not selected) or **1** (selected).<br>**起始版本：** 23 |
| NODE_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER | 定义Picker容器组件中选择某项时触发的事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含1个参数：<ul><li>ArkUI_NodeComponentEvent.data[0].i32：选中项的值。</li></ul><br>**起始版本：** 23 |
| NODE_PICKER_EVENT_ON_SCROLL_STOP = 1018001 | 定义Picker容器组件中选择某项且滚动停止时触发的事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含1个参数：<ul><li>ArkUI_NodeComponentEvent.data[0].i32：选中项的值。</li></ul><br>**起始版本：** 23 |

### ArkUI_NodeDirtyFlag

```c
enum ArkUI_NodeDirtyFlag
```

**描述**

Defines the dirty area flag passed in the <b>::markDirty</b> API.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_NEED_MEASURE = 1 | Remeasure.When this type of flag is specified, re-layout is triggered by default. |
| NODE_NEED_LAYOUT | Re-layout. |
| NODE_NEED_RENDER | Re-rendering. |

### ArkUI_NodeCustomEventType

```c
enum ArkUI_NodeCustomEventType
```

**描述**

Defines the custom component event type.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE = 1 << 0 | Measure type. |
| ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT = 1 << 1 | Layout type. |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW = 1 << 2 | Draw type. |
| ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW = 1 << 3 | Foreground type. |
| ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW = 1 << 4 | Overlay type. |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT = 1 << 5 |  |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND = 1 << 6 |  |

### ArkUI_NodeAdapterEventType

```c
enum ArkUI_NodeAdapterEventType
```

**描述**

Enumerates component adapter events.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_ADAPTER_EVENT_WILL_ATTACH_TO_NODE = 1 | This event occurs when the component is attached to the adapter. |
| NODE_ADAPTER_EVENT_WILL_DETACH_FROM_NODE = 2 | This event occurs when the component is detached from the adapter. |
| NODE_ADAPTER_EVENT_ON_GET_NODE_ID = 3 | This event occurs when the adapter obtains the unique ID of the new element to add. |
| NODE_ADAPTER_EVENT_ON_ADD_NODE_TO_ADAPTER = 4 | This event occurs when the adapter obtains the content of the new element to add. |
| NODE_ADAPTER_EVENT_ON_REMOVE_NODE_FROM_ADAPTER = 5 | This event occurs when the adapter removes an element. |

### ArkUI_NodeContentEventType

```c
enum ArkUI_NodeContentEventType
```

**描述**

Defines the node content event type.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_CONTENT_EVENT_ON_ATTACH_TO_WINDOW = 0 | Defines the attach event. |
| NODE_CONTENT_EVENT_ON_DETACH_FROM_WINDOW = 1 | Defines the detach event. |

### ArkUI_InspectorErrorCode

```c
enum ArkUI_InspectorErrorCode
```

**描述**

Enumerates the inspector error codes.

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL = 0 | Success. |
| ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER = -1 | Invalid parameter. |


## 函数说明

### OH_ArkUI_NodeEvent_GetEventType()

```c
ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)
```

**描述**

Obtains the type of a component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Indicates the pointer to the component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) | Returns the type of the component event. |

### OH_ArkUI_NodeEvent_GetTargetId()

```c
int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)
```

**描述**

Obtains the custom ID of a component event.The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be appliedto the dispatch logic of the same event entry function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver).

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Indicates the pointer to the component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the custom ID of the component event. |

### OH_ArkUI_NodeEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)
```

**描述**

Obtains the component object that triggers a component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Indicates the pointer to the component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Returns the component object that triggers the component event. |

### OH_ArkUI_NodeEvent_GetInputEvent()

```c
ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)
```

**描述**

获取组件事件中的输入事件（如触碰事件）数据。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_UIInputEvent* | ArkUI_UIInputEvent 输入事件数据指针。 |

### OH_ArkUI_NodeEvent_GetNodeComponentEvent()

```c
ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)
```

**描述**

Obtains the numerical data in a component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Indicates the pointer to the component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeComponentEvent*](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | Returns the pointer to the numerical data. |

### OH_ArkUI_NodeEvent_GetStringAsyncEvent()

```c
ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)
```

**描述**

Obtains the string data in a component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Indicates the pointer to the component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_StringAsyncEvent*](capi-arkui-nativemodule-arkui-stringasyncevent.md) | Returns the pointer to the string data. |

### OH_ArkUI_NodeEvent_GetTextChangeEvent()

```c
ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)
```

**描述**

Obtains the ArkUI_TextChangeEvent data from a component event.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to a component event. It cannot be null. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextChangeEvent*](capi-arkui-nativemodule-arkui-textchangeevent.md) | Returns the pointer to the <b>ArkUI_TextChangeEvent</b> object. |

### OH_ArkUI_NodeEvent_GetUserData()

```c
void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)
```

**描述**

Obtains the custom data in a component event.This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the eventis triggered.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Indicates the pointer to the component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | Returns the pointer to the custom data. |

### OH_ArkUI_NodeEvent_GetNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)
```

**描述**

获取组件回调事件的数字类型参数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |
| int32_t index | 返回值索引。 |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | 具体返回值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) 组件事件中参数长度超限。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 组件事件中不存在该数据。 |

### OH_ArkUI_NodeEvent_GetStringValue()

```c
int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)
```

**描述**

获取组件回调事件的字符串类型参数，字符串数据仅在事件回调过程中有效，需要在事件回调外使用建议进行额外拷贝处理。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |
| int32_t index | 返回值索引。 |
| char** string | 字符串数组的指针。 |
| int32_t* stringSize | 字符串数组的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) 组件事件中参数长度超限。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 组件事件中不存在该数据。 |

### OH_ArkUI_NodeEvent_SetReturnNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)
```

**描述**

设置组件回调事件的返回值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 组件事件指针。 |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | 事件数字类型数组。 |
| int32_t size | 数组长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 组件事件中不存在该数据。 |

### OH_ArkUI_NodeEvent_GetTouchTestInfo()

```c
ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)
```

**描述**

获取组件事件中的触摸测试信息。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| {pointer} | nodeEvent Indicates the pointer to an <b>ArkUI_NodeEvent</b> object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_TouchTestInfo* | 返回指向[ArkUI_TouchTestInfo](capi-arkui-eventmodule-arkui-touchtestinfo.md)对象的指针。若传入的参数无效或并非触摸测试信息，则返回null。 |

### OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent()

```c
OH_ArkUI_TextEditorChangeEvent* OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent(ArkUI_NodeEvent* event)
```

**描述**

获取组件事件中的TextEditor组件文本内容变化数据。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | 指向[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)组件事件对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorChangeEvent*](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | 指向[OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md)数据对象的指针。      <br>若传入的参数无效或并非TextEditor组件文本内容变化事件信息，则返回<b>null</b>。 |

### OH_ArkUI_NodeAdapter_Create()

```c
ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()
```

**描述**

Creates a component adapter.

**起始版本：** 12

### OH_ArkUI_NodeAdapter_Dispose()

```c
void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)
```

**描述**

Destroys a component adapter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

### OH_ArkUI_NodeAdapter_SetTotalNodeCount()

```c
int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)
```

**描述**

设置Adapter中的元素总数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t size | 元素数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapter_GetTotalNodeCount()

```c
uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)
```

**描述**

Obtains the total number of elements in the specified adapter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Returns the total number of elements in the adapter. |

### OH_ArkUI_NodeAdapter_RegisterEventReceiver()

```c
int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver( ArkUI_NodeAdapterHandle handle, void* userData, void (*receiver)(ArkUI_NodeAdapterEvent* event))
```

**描述**

注册Adapter相关回调事件。在相关回调事件不需要之后，需要执行[OH_ArkUI_NodeAdapter_UnregisterEventReceiver](capi-native-node-h.md#oh_arkui_nodeadapter_unregistereventreceiver)接口注销相关回调事件。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| void\* userData | 自定义数据。 |
| void (\*receiver)(ArkUI_NodeAdapterEvent\* event) | 事件接收回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapter_UnregisterEventReceiver()

```c
void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)
```

**描述**

Deregisters an event callback for the adapter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

### OH_ArkUI_NodeAdapter_ReloadAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)
```

**描述**

通知Adapter进行全量元素变化。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapter_ReloadItem()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadItem( ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述**

通知Adapter进行局部元素变化。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t startPosition | 元素变化起始位置。 |
| uint32_t itemCount | 元素变化数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_RemoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_RemoveItem( ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述**

通知Adapter进行局部元素删除。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t startPosition | 元素删除起始位置。 |
| uint32_t itemCount | 元素删除数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_InsertItem()

```c
int32_t OH_ArkUI_NodeAdapter_InsertItem( ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述**

通知Adapter进行局部元素插入。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t startPosition | 元素插入起始位置。 |
| uint32_t itemCount | 元素插入数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_MoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)
```

**描述**

通知Adapter进行局部元素移位。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t from | 元素移位起始位置。 |
| uint32_t to | 元素移位结束位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_GetAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)
```

**描述**

获取存储在Adapter中的所有元素。接口调用会返回元素的数组对象指针，该指针指向的内存数据需要开发者手动释放。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)** items | 适配器内节点数组。 |
| uint32_t* size | 元素数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapterEvent_GetUserData()

```c
void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)
```

**描述**

Obtains the custom data passed in during registration of the specified event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

### OH_ArkUI_NodeAdapterEvent_GetType()

```c
ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)
```

**描述**

Obtains the event type.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeAdapterEventType](capi-native-node-h.md#arkui_nodeadaptereventtype) | Returns the event type. |

### OH_ArkUI_NodeAdapterEvent_GetRemovedNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)
```

**描述**

Obtains the element to be removed for the event to be destroyed.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Returns the element to be removed. |

### OH_ArkUI_NodeAdapterEvent_GetItemIndex()

```c
uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)
```

**描述**

Obtains the index of the element to be operated for the specified adapter event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Returns the index of the element. |

### OH_ArkUI_NodeAdapterEvent_GetHostNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)
```

**描述**

Obtains the scrollable container node that uses the specified adapter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Returns the scrollable container node that uses the specified adapter. |

### OH_ArkUI_NodeAdapterEvent_SetItem()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)
```

**描述**

设置需要新增到Adapter中的组件。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 待添加的组件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapterEvent_SetNodeId()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)
```

**描述**

设置生成的组件标识。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |
| int32_t id | 设置返回的组件标识。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure()

```c
ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)
```

**描述**

Obtains the size constraint for measurement through a custom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_LayoutConstraint*](capi-arkui-nativemodule-arkui-layoutconstraint.md) | Returns the pointer to the size constraint. |

### OH_ArkUI_NodeCustomEvent_GetPositionInLayout()

```c
ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)
```

**描述**

Obtains the expected position of a component relative to its parent component in the layout phase through acustom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | Returns the expected position relative to the parent component. |

### OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw()

```c
ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)
```

**描述**

Obtains the drawing context through a custom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_DrawContext*](capi-arkui-nativemodule-arkui-drawcontext.md) | Returns the drawing context. |

### OH_ArkUI_NodeCustomEvent_GetEventTargetId()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)
```

**描述**

Obtains the ID of a custom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the ID of the custom component event. |

### OH_ArkUI_NodeCustomEvent_GetUserData()

```c
void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)
```

**描述**

Obtains custom event parameters through a custom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | Returns the custom event parameters. |

### OH_ArkUI_NodeCustomEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)
```

**描述**

Obtains a component object through a custom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Returns the component object. |

### OH_ArkUI_NodeCustomEvent_GetEventType()

```c
ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)
```

**描述**

Obtains the event type through a custom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeCustomEventType](capi-native-node-h.md#arkui_nodecustomeventtype) | Returns the type of the custom component event. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)
```

**描述**

Obtains the measurement information of a custom span through a custom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info | Indicates the measurement information to be obtained. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.         <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics()

```c
int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)
```

**描述**

Sets the measurement metrics of a custom span through a custom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Indicates the measurement metrics to set. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.         <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)
```

**描述**

Obtains the drawing information of a custom span through a custom component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Indicates the drawing information to obtain. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.         <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### ArkUI_NodeContentCallback()

```c
typedef void (*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)
```

**描述**

Defines the callback function of a node content event.

**起始版本：** 12

### OH_ArkUI_NodeContent_RegisterCallback()

```c
int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)
```

**描述**

注册NodeContent事件函数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要注册事件的NodeContent对象。 |
| [ArkUI_NodeContentCallback](capi-native-node-h.md#arkui_nodecontentcallback) callback | 事件触发时需要执行的函数回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeContentEvent_GetEventType()

```c
ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)
```

**描述**

Obtains the type of a node content event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Indicates the pointer to the node content event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeContentEventType](capi-native-node-h.md#arkui_nodecontenteventtype) | Returns the type of the node content event. |

### OH_ArkUI_NodeContentEvent_GetNodeContentHandle()

```c
ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)
```

**描述**

Obtains the node content object that triggers a node content event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Indicates the pointer to the node content event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) | Returns the node content object that triggers the node content event. |

### OH_ArkUI_NodeContent_SetUserData()

```c
int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)
```

**描述**

Saves custom data on the specified node content.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | Indicates the node content on which the custom data will be saved. |
| void* userData | Indicates the custom data to be saved. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeContent_GetUserData()

```c
void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)
```

**描述**

Obtains the custom data saved on the specified node content.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | Indicates the target node content. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | Returns the custom data. |

### OH_ArkUI_NodeContent_AddNode()

```c
int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**描述**

将一个ArkUI组件节点添加到对应的NodeContent对象下。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要被添加节点的NodeContent对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要被添加的节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-native-type-h.md#arkui_errorcode) 子节点已经被接纳。从API version 22开始支持。 |

### OH_ArkUI_NodeContent_RemoveNode()

```c
int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**描述**

删除NodeContent对象下的一个ArkUI组件节点。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要被删除节点的NodeContent对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要被删除的节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeContent_InsertNode()

```c
int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)
```

**描述**

将一个ArkUI组件节点插入到对应的NodeContent对象的特定位置下。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | 需要被插入节点的NodeContent对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要被插入的节点。 |
| int32_t position | 需要被插入的位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-native-type-h.md#arkui_errorcode) 子节点已经被接纳。从API version 22开始支持。 |

### OH_ArkUI_NodeUtils_GetLayoutSize()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)
```

**描述**

获取组件布局区域的大小。布局区域大小不包含图形变化属性，如缩放。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md)* size | 组件handle的绘制区域尺寸，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPosition()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)
```

**描述**

获取组件布局区域相对父组件的位置。布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* localOffset | 组件handle相对父组件的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPositionInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**描述**

获取组件布局区域相对窗口的位置。布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | 组件handle相对窗口的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPositionInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)
```

**描述**

获取组件布局区域相对屏幕的位置。布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* screenOffset | 组件handle相对屏幕的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)
```

**描述**

获取组件相对于全局屏幕的偏移。布局区域相对位置不包含图形变化属性，如平移。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* offset | 组件handle相对屏幕的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**描述**

Obtain the position of the component in the window, including the properties of graphic translation changes.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* translateOffset | The cumulative offset value of the component handle itself,parent components, and ancestor nodes, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**描述**

Obtain the position of the component on the screen, including the attributes of graphic translation changes.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* translateOffset | The cumulative offset value of the component handle itself,parent components, and ancestor nodes, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_AddCustomProperty()

```c
void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)
```

**描述**

设置组件的自定义属性。该接口仅在主线程生效。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| const char* name | 自定义属性的名称。不允许传入空指针。 |
| const char* value | 对应key参数名称的自定义属性的值。不允许传入空指针。 |

### OH_ArkUI_NodeUtils_RemoveCustomProperty()

```c
void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)
```

**描述**

移除组件已设置的自定义属性。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| const char* name | 自定义属性的名称。 |

### OH_ArkUI_NodeUtils_GetCustomProperty()

```c
int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)
```

**描述**

获取组件的自定义属性的值。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针。 |
| const char* name | 自定义属性的名称。 |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)** handle | 获取的对应key参数名称的自定义属性的结构体。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetParentInPageTree()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)
```

**描述**

获取父节点，可获取由ArkTs创建的组件节点。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 组件的指针，如果没有返回NULL。 |

### OH_ArkUI_NodeUtils_GetActiveChildrenInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)
```

**描述**

获取某个节点所有活跃的子节点。Span将不会被计入子节点的统计中。在LazyForEach场景中，推荐使用[OH_ArkUI_NodeUtils_GetChildWithExpandMode](capi-native-node-h.md#oh_arkui_nodeutils_getchildwithexpandmode)接口进行遍历。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) head | 传入需要获取的节点。 |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)** handle | 对应head节点子节点信息的结构体。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetCurrentPageRootNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)
```

**描述**

获取当前页面的根节点。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 根节点的指针，如果没有返回NULL。 |

### OH_ArkUI_NodeUtils_IsCreatedByNDK()

```c
bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)
```

**描述**

获取组件是否由C-API创建的标签。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 节点是否由C-API创建的Tag，true代表由C-API创建，false代表非C-API创建。 |

### OH_ArkUI_NodeUtils_GetNodeType()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)
```

**描述**

获取节点的类型。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 节点的类型，具体已开放类型参考[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)，未开放结点返回-1。 |

### OH_ArkUI_NodeUtils_GetWindowInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)
```

**描述**

获取节点所属的窗口信息。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点对象。 |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)** info | 窗口信息。使用[OH_ArkUI_HostWindowInfo_Destroy](capi-native-type-h.md#oh_arkui_hostwindowinfo_destroy)释放内存。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。      <br>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。      <br>[ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) 节点未挂载到节点树上。 |

### OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**描述**

获取目标节点在树上的第一个子节点的下标。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| uint32_t* index | 子节点的下标值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**描述**

获取目标节点在树上的最后一个子节点的下标。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| uint32_t* index | 子节点的下标值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetChildWithExpandMode()

```c
int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)
```

**描述**

用不同的展开模式获取对应下标的子节点。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| int32_t position | 对应子节点的下标。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* subnode | 获取子节点的指针。 |
| uint32_t expandMode | 节点遍历展开方式。 [ArkUI_ExpandMode](capi-native-type-h.md#arkui_expandmode)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_List_CloseAllSwipeActions()

```c
int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (*onFinish)(void* userData))
```

**描述**

收起展开状态下的ListItem。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | 需要注册事件的节点对象。 |
| void\* userData | 自定义事件参数，当事件触发时在回调参数中携带回来。 |
| void (\*onFinish)(void\* userData) | 在收起动画完成后触发的回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) 组件不支持该事件。 |

### OH_ArkUI_GetContextByNode()

```c
ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)
```

**描述**

Obtain the UIContext pointer to the page where the node is located.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | The node. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) | The UIContext pointer.         If a null pointer is returned, it may be because the node is empty. |

### OH_ArkUI_RegisterSystemColorModeChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node, void* userData, void (*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))
```

**描述**

The event called when the system color mode changes.Only one system color change callback can be registered for the same component.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode | Callback Events. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_UnregisterSystemColorModeChangeEvent()

```c
void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)
```

**描述**

Unregister the event callback when the system color mode changes.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |

### OH_ArkUI_RegisterSystemFontStyleChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node, void* userData, void (*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))
```

**描述**

The event called when the system font style changes.Only one system font change callback can be registered for the same component.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent\* event | Callback Events. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_UnregisterSystemFontStyleChangeEvent()

```c
void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)
```

**描述**

Unregister the event callback when the system font style changes.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |

### OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)
```

**描述**

Retrieve the font size value for system font change events.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md)* event | Indicates a pointer to the current system font change event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Updated system font size scaling factor. Default value: 1.0. |

### OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)
```

**描述**

Retrieve the font thickness values for system font change events.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md)* event | Indicates a pointer to the current system font change event. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | The updated system font thickness scaling factor. Default value: 1.0. |

### OH_ArkUI_NodeUtils_GetAttachedNodeHandleById()

```c
int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)
```

**描述**

根据用户id获取目标节点。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* id | 目标节点的id。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | 目标节点的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_MoveTo()

```c
int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)
```

**描述**

将节点移动到目标父节点下，作为子节点。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 待移动的节点对象。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) target_parent | 目标父节点指针。 |
| int32_t index | 转移后的节点下标，如果下标值为非法值，则添加在目标父节点的最后一位。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。          [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-native-type-h.md#arkui_errorcode) 子节点已经被接纳。从API version 22开始支持。 |

### OH_ArkUI_NativeModule_InvalidateAttributes()

```c
int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)
```

**描述**

在当前帧触发节点属性更新。当前节点的属性在构建阶段后被修改，这些改动不会立即生效，而是延迟到下一帧统一处理。此功能强制当前帧内即时节点更新，确保同步应用渲染效果。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 待更新的节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_SetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**描述**

设置目标节点跨语言设置属性的能力。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | 跨语言配置项 [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**描述**

获取目标节点跨语言设置属性的配置项。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点的指针。 |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | 跨语言配置项 [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_RegisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (*onLayoutCompleted)(void* userData))
```

**描述**

Registers a callback for node when layout is completed.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data used in onLayoutCompleted callback function. |
| void (\*onLayoutCompleted)(void\* userData) | Indicates the function when layout completed is callback. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter is incorrect. |

### OH_ArkUI_RegisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (*onDrawCompleted)(void* userData))
```

**描述**

Registers a callback for node when draw is completed.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data used in onDrawCompleted callback function. |
| void (\*onDrawCompleted)(void\* userData) | Indicates the function when draw completed is callback. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter is incorrect. |

### OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**描述**

Unregisters the layout completed callback for node.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter is incorrect. |

### OH_ArkUI_UnregisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**描述**

Unregisters the draw completed callback for node.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter is incorrect. |

### OH_ArkUI_GetNodeSnapshot()

```c
int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelmap)
```

**描述**

Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered,the snapshot operation will fail. When the <b>Pixelmap</b> object created is no longer in use, it should be releasedby calling {@link OH_PixelmapNative_Release}.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node. |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Snapshot settings. If the value is null, the default settings are used.Snapshot settings include scaling, color space, and dynamic range configuration.Scaling: floating-point value greater than 0.Color space: <b>3</b> (DISPLAY_P3), <b>4</b> (SRGB), <b>27</b> (DISPLAY_BT2020_SRGB).Dynamic range: [ArkUI_DynamicRangeMode](capi-native-type-h.md#arkui_dynamicrangemode). |
| [OH_PixelmapNative](capi-arkui-nativemodule-oh-pixelmapnative.md)** pixelmap | Pointer to the <b>Pixelmap</b> object created by the system. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Result code.          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.          Returns [ARKUI_ERROR_CODE_INTERNAL_ERROR](capi-native-type-h.md#arkui_errorcode) if the snapshot fails, returning a null pointer.          Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT](capi-native-type-h.md#arkui_errorcode) if the snapshot operation times out.          Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) if the provided color space or          dynamic range mode is not supported.          Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) if the isAuto parameter of the color          space or dynamic range mode is set to true for offscreen node snapshot. |

### OH_ArkUI_GetNodeSnapshotSizeLimitation()

```c
int32_t OH_ArkUI_GetNodeSnapshotSizeLimitation(int32_t* maxWidth, int32_t* maxHeight)
```

**描述**

Query the size limitation of the component snapshot.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t* maxWidth | Maximum width limit of the component snapshot, in px. |
| int32_t* maxHeight | Maximum height limit of the component snapshot, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Invalid function parameter. |

### OH_ArkUI_NodeUtils_GetPositionToParent()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**描述**

获取目标节点相对于父节点的偏移值，单位：px。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | 目标节点相对父节点的偏移值，单位：px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AddSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)
```

**描述**

设置组件支持的多态样式状态。为了更高效地处理，需传入所关注的状态值及对应的状态处理函数，当关注的状态发生时，处理函数会被执行。可在回调中根据当前状态调整UI样式。当在同一个节点上多次调用该方法时，将以最后一次传入的状态及处理函数为准。有些类型的组件节点，系统内部已有对某些状态的默认处理。例如，Button组件默认具备对PRESSED状态的样式变化，当在此类组件上使用此方法自定义状态处理时，会先应用系统默认样式变化，再执行自定义的样式处理，最终效果为两者叠加。可以通过指定excludeInner为true来禁用系统内部的默认样式效果，但这通常取决于系统内部实现规范是否允许。当调用该函数时，传入的statesChangeHandler函数会立即执行一次，且无需特意注册对NORMAL状态的监听，只要注册了非NORMAL状态，当状态从任意状态变化回NORMAL时，系统都会进行回调，以便应用进行样式复原。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | 目标节点。 |
| int32_t uiStates | 目标节点需要处理的目标UI状态。所有目标UI状态的组合结果可以通过“|”操作来计算。例如：targetUIStates = ArkUI_UIState::PRESSED | ArkUI_UIState::FOCUSED。 |
| void (statesChangeHandler)(int32_t currentStates | UI状态改变处理函数。返回当前UI状态，该值是所有当前状态枚举值“|”计算的结果，可以通过执行“&”操作来确定状态。例如：if (currentStates & ArkUI_UIState::PRESSED == ArkUI_UIState::PRESSED)。但是，对于正常状态检查，应直接使用等号。例如：if (currentStates == ArkUI_UIState::NORMAL) |
| bool excludeInner | 禁止内部默认状态样式的标志。​​true​​表示禁用系统内部的默认样式，false表示不禁用。 |
| void\* userData) | onDrawCompleted回调函数中使用的自定义数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_RemoveSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)
```

**描述**

删除注册的状态处理。当通过OH_ArkUI_AddSupportedUIStates注册的状态都被删除时，所注册的stateChangeHandler也不会再被执行。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点。 |
| int32_t uiStates | 节点需要删除的目标UI状态。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_RunTaskInScope()

```c
int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(*callback)(void* userData))
```

**描述**

在目标UI上下文中执行传入的自定义回调函数。示例请参考：[在NDK中保证多实例场景功能正常](../../../ui/ndk-scope-task.md)。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle uiContext | 表示目标UI上下文的指针。 |
| void\* userData | 开发者自定义数据指针，以便在回调函数中处理自定义数据，开发者需自行保证自定义函数被执行时的数据有效性。 |
| void(\*callback)(void\* userData) | 开发者自定义回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。      <br>[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-native-type-h.md#arkui_errorcode) UIContext对象无效。      <br>[ARKUI_ERROR_CODE_CALLBACK_INVALID](capi-native-type-h.md#arkui_errorcode) 回调函数无效。 |

### OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)
```

**描述**

Get the node handle by uniqueId.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const uint32_t uniqueId | The uniqueId of the target node handle. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | The handle of target node handle. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if the CAPI init error. |

### OH_ArkUI_NodeUtils_GetNodeUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)
```

**描述**

获取目标节点的uniqueId。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI节点指针。 |
| int32_t* uniqueId | 目标节点的uniqueId。组件标识ID只读，且进程内唯一，若该节点存在，返回该节点的uniqueId值；否则返回-1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 方法参数错误。      <br>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。 |

### OH_ArkUI_NativeModule_IsInRenderState()

```c
int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)
```

**描述**

获取节点是否处于渲染状态，如果一个节点的对应RenderNode在渲染树上，则处于渲染状态。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI节点指针。 |
| bool* isInRenderState | 节点是否处于渲染状态。true：处于渲染状态；false：不处于渲染状态。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 方法参数错误。 \n          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。 |

### OH_ArkUI_NativeModule_AdoptChild()

```c
int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**描述**

当前节点接纳目标节点为附属节点。被接纳的节点不能已有父节点。调用该接口实际上不会将其添加为子节点，而是仅允许其接收对应子节点的生命周期回调。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针，指定待接纳节点的父节点。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | ArkUI_NodeHandle指针，指定待被接纳的子节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。 \n          [ARKUI_ERROR_CODE_NODE_HAS_PARENT](capi-native-type-h.md#arkui_errorcode) 被接纳的节点已有父节点。 \n          [ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED](capi-native-type-h.md#arkui_errorcode) 节点无法被接纳为附属节点。 \n          [ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO](capi-native-type-h.md#arkui_errorcode) 节点无法接纳其它附属节点。 |

### OH_ArkUI_NativeModule_RemoveAdoptedChild()

```c
int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**描述**

移除被接纳的目标附属节点。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle指针，父节点。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | ArkUI_NodeHandle指针，将要被移除的子节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。 \n          [ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN](capi-native-type-h.md#arkui_errorcode) 节点不是被目标节点接纳的附属节点。 |

### OH_ArkUI_SetForceDarkConfig()

```c
int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (*colorInvertFunc)(uint32_t color))
```

**描述**

为组件和实例设置反色算法。详细介绍请参考：[利用反色能力快速适配深色模式](../../../ui/ui-dark-light-color-adaptation.md#利用反色能力快速适配深色模式)。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle uiContext | UI实例对象指针。 <br>         如果该值为null，则该功能适用于整个应用进程。 |
| bool forceDark | 是否使用反色能力。取值为true：组件使用反色能力，取值为false：组件不使用反色能力。 |
| [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype) nodeType | 指定使用反色能力生效组件范围。 <br>         ARKUI_NODE_UNDEFINED代表对所有组件类型生效。 |
| uint32_t (\*colorInvertFunc)(uint32_t color) | 开发者自定义反色算法函数。 <br>         如果该值为nullptr，则对组件使用系统默认反色算法，即三原色取反。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。 \n          [ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID](capi-native-type-h.md#arkui_errorcode) 反色能力入参错误。 |

### OH_ArkUI_NativeModule_RegisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**描述**

注册目标节点的基础事件回调。当前支持的事件类型如下: 参考[ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype)中的NODE_ON_CLICK_EVENT、NODE_TOUCH_EVENT、NODE_EVENT_ON_APPEAR、NODE_EVENT_ON_DISAPPEAR、NODE_ON_KEY_EVENT、NODE_ON_FOCUS、NODE_ON_BLUR、NODE_ON_HOVER、NODE_ON_MOUSE、NODE_ON_SIZE_CHANGE。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | 目标节点。 |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | 事件类型。 |
| void\* userData | 开发者自定义的数据指针，以便在回调函数中处理自定义数据，需确保自定义函数执行时数据有效。 |
| void (\*callback)(ArkUI_NodeEvent\* event) | 开发者自定义的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。      <br>[ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE](capi-native-type-h.md#arkui_errorcode) 暂不支持该事件类型。 |

### OH_ArkUI_NativeModule_UnregisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)
```

**描述**

注销目标节点的基础事件回调。当前支持的事件类型请参考[OH_ArkUI_NativeModule_RegisterCommonEvent](capi-native-node-h.md#oh_arkui_nativemodule_registercommonevent)。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点。 |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | 事件类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE](capi-native-type-h.md#arkui_errorcode) 暂不支持该事件类型。 |

### OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**描述**

注册限制回调间隔的可见区域变化的基础事件回调。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | 目标节点。 |
| float\* ratios | 阈值数组，表示组件的可见区域。 |
| int32_t size | 阈值数组的大小。 |
| float expectedUpdateInterval | 开发人员预期的计算间隔。 |
| void\* userData | 开发者自定义的数据指针，以便在回调函数中处理自定义数据，需确保自定义函数执行时数据有效。 |
| void (\*callback)(ArkUI_NodeEvent\* event) | 开发者自定义的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)
```

**描述**

注销限制回调间隔的可见区域变化的基础事件回调。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_ConvertPositionToWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)
```

**描述**

将点的坐标从指定节点的坐标系转换至当前窗口的坐标系。节点的坐标系考虑节点本身的变换，例如，节点A的变换效果为向左平移100，会使得其坐标系中的点的坐标也向左平移100。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) currentNode | 指定节点。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) localPosition | 点在指定节点坐标系中的坐标，单位：px。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* windowPosition | 指向接收转换后坐标（位于当前窗口坐标系中，单位：px）的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) 节点未挂载到节点树上。 |

### OH_ArkUI_NativeModule_ConvertPositionFromWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)
```

**描述**

将点的坐标从当前窗口的坐标系转换至目标节点的坐标系。节点的坐标系考虑节点本身的变换，例如，节点A的变换效果为向左平移100，会使得其坐标系中的点的坐标也向左平移100。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) targetNode | 目标节点。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) windowPosition | 点在当前窗口坐标系中的坐标，单位：px。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* localPosition | 指向接收转换后坐标（位于目标节点坐标系中，单位：px）的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) 节点未挂载到节点树上。 |

### OH_ArkUI_Swiper_FinishAnimation()

```c
int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)
```

**描述**

停止指定的Swiper节点正在执行的翻页动画。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 指定的节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_PostAsyncUITask()

```c
int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (*asyncUITask)(void* asyncUITaskData), void (*onFinish)(void* asyncUITaskData))
```

**描述**

将asyncUITask函数提交至ArkUI框架提供的非UI线程中执行，asyncUITask函数执行完毕后，在UI线程调用onFinish函数。适用于多线程创建UI组件的场景，开发者可使用此接口在非UI线程创建UI组件，随后在UI线程将创建完成的组件挂载至主树上。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle context | UI实例对象指针。 |
| void\* asyncUITaskData | 开发者自定义数据指针，作为asyncUITask和onFinish的入参。可以传入空指针。 |
| void (\*asyncUITask)(void\* asyncUITaskData) | 在非UI线程执行的函数。 |
| void (\*onFinish)(void\* asyncUITaskData) | asyncUITask执行完成后，在UI线程执行的函数。可以传入空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) context对象无效或asyncUITask为空指针。 |

### OH_ArkUI_PostUITask()

```c
int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**描述**

将task函数提交至UI线程中执行。适用于多线程创建UI组件的场景，当开发者在自建的线程中创建UI组件时，可以使用此接口将创建完成的组件挂载到UI线程的主树上。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle context | UI实例对象指针。 |
| void\* taskData | 开发者自定义数据指针，作为task的入参。可以传入空指针。 |
| void (\*task)(void\* taskData) | 在UI线程执行的函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) context对象无效或task为空指针。 |

### OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible()

```c
int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)
```

**描述**

设置菜单栏的可见性。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | ArkUI上下文句柄，指定的ArkUI容器上下文。 |
| bool visible | 菜单栏是否可见。true表示菜单栏可见，false表示菜单栏不可见。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 操作成功。 \n          [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-native-type-h.md#arkui_errorcode) 实例异常（uiContext为空指针、无法通过uiContext获取容器、uiContext不属于原子化服务）。 |

### OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**描述**

Registers a callback for listening for component dimension and area changes.This function can be called for a valid [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node at any time. <br> The newly registered callback will replace the previously registered callback for this event and will take effect from the next frame. <br> When the callback is no longer needed, call [OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent](capi-native-node-h.md#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) to unregister it. <br> Otherwise, the callback will be automatically unregistered when the node is released.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Pointer to [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). |
| float expectedUpdateInterval | Expected calculation interval, in milliseconds. |
| void\* userData | Pointer to custom data. |
| void (\*callback)(ArkUI_NodeEvent\* event) | Event callback. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Result code. \n          Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful. \n          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. \n |

### OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node)
```

**描述**

Unregisters the callback bound to the dimensions and area changes of a component.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Result code. \n          Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful. \n          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. \n |

### OH_ArkUI_PostUITaskAndWait()

```c
int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**描述**

将task函数提交至UI线程中执行，调用此接口的线程将阻塞，直至task函数执行完成。在UI线程调用此接口等同于同步调用task函数。适用于多线程创建UI组件的场景，当开发者在多线程创建组件过程中需要调用仅支持UI线程的函数时，使用此接口返回UI线程调用函数，调用完成后继续多线程创建组件。当UI线程负载较高时，调用此接口的非UI线程可能长时间阻塞，影响多线程创建UI组件的性能，不建议频繁使用。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle context | UI实例对象指针。 |
| void\* taskData | 开发者自定义数据指针，作为task的入参。可以传入空指针。 |
| void (\*task)(void\* taskData) | 在UI线程执行的函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) context对象无效或task为空指针。 |

### OH_ArkUI_Swiper_StartFakeDrag()

```c
int32_t OH_ArkUI_Swiper_StartFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)
```

**描述**

Start a fake drag of the Swiper node.Call OH_ArkUI_Swiper_FakeDragBy to simulate the drag motion. Call OH_ArkUI_Swiper_StopFakeDrag to complete thefake drag. A fake drag can be interrupted by a real drag. If you need to ignore touch events and other user inputduring a fake drag, use NODE_SWIPER_DISABLE_SWIPE.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| bool* isSuccessful | If the fake drag started successfully, return true.If the Swiper is not ready to start the fake drag, or a real or fake drag is already in progress, return false. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_FakeDragBy()

```c
int32_t OH_ArkUI_Swiper_FakeDragBy(ArkUI_NodeHandle node, float offset, bool* isConsumedOffset)
```

**描述**

Fake drag by an offset of the Swiper node.The OH_ArkUI_Swiper_StartFakeDrag must be called first.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| float offset | The offset that needs to be scrolled. The unit is vp. |
| bool* isConsumedOffset | If not in a fake drag progress, or no offset is consumed, return false.If any offset is consumed, return true. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_StopFakeDrag()

```c
int32_t OH_ArkUI_Swiper_StopFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)
```

**描述**

Stop a fake drag of the Swiper node.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| bool* isSuccessful | If the fake drag stopped successfully, return true.If the Swiper is not ready to stop the fake drag, or no fake drag is in progress, return false. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_IsFakeDragging()

```c
int32_t OH_ArkUI_Swiper_IsFakeDragging(ArkUI_NodeHandle node, bool* isFakeDragging)
```

**描述**

Get the fake drag state of the Swiper node.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| bool* isFakeDragging | If a fake drag is in progress return true, otherwise return false |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_ShowPrevious()

```c
int32_t OH_ArkUI_Swiper_ShowPrevious(ArkUI_NodeHandle node)
```

**描述**

Show the previous page of the Swiper node.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_ShowNext()

```c
int32_t OH_ArkUI_Swiper_ShowNext(ArkUI_NodeHandle node)
```

**描述**

Show the next page of the Swiper node.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext()

```c
int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)
```

**描述**

获取指定实例的页面的根节点。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UI实例对象指针。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* rootNode | 目标根节点的句柄。如果上下文对应的页面没有根节点，则所指向的值将被设置为null。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) CAPI初始化错误。      <br>[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-native-type-h.md#arkui_errorcode) 实例异常。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo()

```c
ArkUI_GestureCollectInterceptInfo* OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo(ArkUI_NodeEvent* nodeEvent)
```

**描述**

Obtains the <b>ArkUI_GestureCollectInterceptInfo</b> object from a specified <b>ArkUI_NodeEvent</b> object.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* nodeEvent | Pointer to the <b>ArkUI_NodeEvent</b> object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GestureCollectInterceptInfo*](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md) | Returns the pointer to the <b>ArkUI_GestureCollectInterceptInfo</b> object.          It is valid only during callback and does not need to be released.          Returns <b>null</b> if the input parameter is invalid or the          information is not gesture collection interception information. |

### OH_ArkUI_NativeModule_SetChildMountPolicy()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_SetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy policy)
```

**描述**

Set the subnode mounting policy of the target node.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | the target node handle. |
| [OH_ArkUI_NodeMountPolicy](capi-native-type-h.md#oh_arkui_nodemountpolicy) policy | the policy to set. Valid values correspond to [OH_ArkUI_NodeMountPolicy](capi-native-type-h.md#oh_arkui_nodemountpolicy). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Error code.      <ul><li>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.      </li><li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.      </li><li>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if CAPI init error.</li></ul> |

### OH_ArkUI_NativeModule_GetChildMountPolicy()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy* policy)
```

**描述**

Get the current child mount policy of the specified node.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | the target node handle. |
| [OH_ArkUI_NodeMountPolicy](capi-native-type-h.md#oh_arkui_nodemountpolicy)* policy | the pointer to receive child mounting policy of the target node. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Error code.      <ul><li>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.      </li><li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.      </li><li>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if CAPI init error.</li></ul> |


