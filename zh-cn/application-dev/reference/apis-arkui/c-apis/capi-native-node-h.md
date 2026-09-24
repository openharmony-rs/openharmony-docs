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
| [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) | ArkUI_TextChangeEvent | 定义文本变化事件的数据结构，用于在文本输入场景中监听和处理文本变更事件。该结构体包含文本内容、扩展信息和数值参数，支持开发者实时获取文本变更数据，适用于输入框内容监听、实时搜索、字数统计等场景。 |
| [ArkUI_NativeNodeAPI_1](capi-arkui-nativemodule-arkui-nativenodeapi-1.md) | ArkUI_NativeNodeAPI_1 | ArkUI提供的Native侧Node类型接口集合。<br> Node模块相关接口需要在主线程上调用。 |
| [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | OH_ArkUI_TextEditorChangeEvent | 定义TextEditor组件文本内容变化事件的结构体，用于在文本内容变化时通知用户，支持获取变化前后的内容等信息，适用于需要在文本内容变化前进行拦截或校验的场景，例如输入拦截、内容过滤、变更确认等。 |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md) | ArkUI_NodeCustomEvent | Defines the general structure of a custom component event. |
| [ArkUI_NodeAdapter*](capi-arkui-nativemodule-arkui-nodeadapter8h.md) | ArkUI_NodeAdapterHandle | Defines the component adapter, which is used for lazy loading of elements of scrollable components. |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md) | ArkUI_NodeAdapterEvent | Defines the component adapter event. |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md) | ArkUI_NodeContentEvent | Defines the general structure of a node content event. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NodeType](#arkui_nodetype) | ArkUI_NodeType | Enumerates ArkUI component types that can be created on the native side. |
| [ArkUI_NodeAttributeType](capi-arkui-nodeattributetype.md) | ArkUI_NodeAttributeType | 定义ArkUI在Native侧可以设置的属性样式集合。 |
| [ArkUI_NodeEventType](capi-arkui-nodeeventtype.md) | ArkUI_NodeEventType | Enumerates the event types supported by the NativeNode component. |
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
| [int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettargetid) | - | Obtains the custom ID of a component event.<br> The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be applied to the dispatch logic of the same event entry function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver). |
| [ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodehandle) | - | Obtains the component object that triggers a component event. |
| [ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getinputevent) | - | 获取组件事件中的输入事件（如触碰事件）数据。 |
| [ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodecomponentevent) | - | Obtains the numerical data in a component event. |
| [ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getstringasyncevent) | - | Obtains the string data in a component event. |
| [ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettextchangeevent) | - | Obtains the ArkUI_TextChangeEvent data from a component event. |
| [void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getuserdata) | - | Obtains the custom data in a component event.<br> This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the event is triggered. |
| [int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)](#oh_arkui_nodeevent_getnumbervalue) | - | 获取组件回调事件的数字类型参数。 |
| [int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)](#oh_arkui_nodeevent_getstringvalue) | - | 获取组件回调事件的字符串类型参数，字符串数据仅在事件回调过程中有效，需要在事件回调外使用建议进行额外拷贝处理。 |
| [int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)](#oh_arkui_nodeevent_setreturnnumbervalue) | - | 设置组件回调事件的返回值。 |
| [ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_gettouchtestinfo) | - | 获取组件事件中的触摸测试信息。 |
| [OH_ArkUI_TextEditorChangeEvent* OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettexteditoronwillchangeevent) | - | 获取组件事件中的TextEditor组件文本内容变化数据。 |
| [ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()](#oh_arkui_nodeadapter_create) | - | Creates a component adapter. |
| [void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_dispose) | - | Destroys a component adapter. |
| [int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)](#oh_arkui_nodeadapter_settotalnodecount) | - | 设置Adapter中的元素总数。 |
| [uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_gettotalnodecount) | - | Obtains the total number of elements in the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(
ArkUI_NodeAdapterHandle handle, void* userData, void (\*receiver)(ArkUI_NodeAdapterEvent* event))](#oh_arkui_nodeadapter_registereventreceiver) | - | 注册Adapter相关回调事件。在相关回调事件不需要之后，需要执行[OH_ArkUI_NodeAdapter_UnregisterEventReceiver](capi-native-node-h.md#oh_arkui_nodeadapter_unregistereventreceiver)接口注销相关回调事件。 |
| [void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_unregistereventreceiver) | - | Deregisters an event callback for the adapter. |
| [int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_reloadallitems) | - | 通知Adapter进行全量元素变化。 |
| [int32_t OH_ArkUI_NodeAdapter_ReloadItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_reloaditem) | - | 通知Adapter进行局部元素变化。 |
| [int32_t OH_ArkUI_NodeAdapter_RemoveItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_removeitem) | - | 通知Adapter进行局部元素删除。 |
| [int32_t OH_ArkUI_NodeAdapter_InsertItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_insertitem) | - | 通知Adapter进行局部元素插入。 |
| [int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)](#oh_arkui_nodeadapter_moveitem) | - | 通知Adapter进行局部元素移位。 |
| [int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)](#oh_arkui_nodeadapter_getallitems) | - | 获取存储在Adapter中的所有元素。<br> 接口调用会返回元素的数组对象指针，该指针指向的内存数据需要开发者手动释放。 |
| [void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getuserdata) | - | Obtains the custom data passed in during registration of the specified event. |
| [ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gettype) | - | Obtains the event type. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getremovednode) | - | Obtains the element to be removed for the event to be destroyed. |
| [uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getitemindex) | - | Obtains the index of the element to be operated for the specified adapter event. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gethostnode) | - | Obtains the scrollable container node that uses the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)](#oh_arkui_nodeadapterevent_setitem) | - | 设置需要新增到Adapter中的组件。 |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)](#oh_arkui_nodeadapterevent_setnodeid) | - | 设置生成的组件标识。 |
| [ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getlayoutconstraintinmeasure) | - | Obtains the size constraint for measurement through a custom component event. |
| [ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getpositioninlayout) | - | Obtains the expected position of a component relative to its parent component in the layout phase through a custom component event. |
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
| [int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)](#oh_arkui_nodeutils_getlayoutsize) | - | 获取组件布局区域的大小。 布局区域大小不包含图形变化属性，如缩放。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)](#oh_arkui_nodeutils_getlayoutposition) | - | 获取组件布局区域相对父组件的位置。 布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getlayoutpositioninwindow) | - | 获取组件布局区域相对窗口的位置。 布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)](#oh_arkui_nodeutils_getlayoutpositioninscreen) | - | 获取组件布局区域相对屏幕的位置。 布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)](#oh_arkui_nodeutils_getlayoutpositioninglobaldisplay) | - | 获取组件相对于全局屏幕的偏移。 布局区域相对位置不包含图形变化属性，如平移。 |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinwindow) | - | Obtain the position of the component in the window, including the properties of graphic translation changes. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinscreen) | - | Obtain the position of the component on the screen, including the attributes of graphic translation changes. |
| [void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)](#oh_arkui_nodeutils_addcustomproperty) | - | 设置组件的自定义属性。该接口仅在主线程生效。 |
| [void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)](#oh_arkui_nodeutils_removecustomproperty) | - | 移除组件已设置的自定义属性。 |
| [int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)](#oh_arkui_nodeutils_getcustomproperty) | - | 获取组件的自定义属性的值。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getparentinpagetree) | - | 获取父节点，可获取由ArkTs创建的组件节点。 |
| [int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)](#oh_arkui_nodeutils_getactivechildreninfo) | - | 获取某个节点所有活跃的子节点。Span将不会被计入子节点的统计中。 在LazyForEach场景中，推荐使用[OH_ArkUI_NodeUtils_GetChildWithExpandMode](capi-native-node-h.md#oh_arkui_nodeutils_getchildwithexpandmode)接口进行遍历。 |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getcurrentpagerootnode) | - | 获取当前页面的根节点。 |
| [bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_iscreatedbyndk) | - | 获取组件是否由C-API创建的标签。 |
| [int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getnodetype) | - | 获取节点的类型。 |
| [int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)](#oh_arkui_nodeutils_getwindowinfo) | - | 获取节点所属的窗口信息。 |
| [int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getfirstchildindexwithoutexpand) | - | 获取目标节点在树上的第一个子节点的下标。 |
| [int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getlastchildindexwithoutexpand) | - | 获取目标节点在树上的最后一个子节点的下标。 |
| [int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)](#oh_arkui_nodeutils_getchildwithexpandmode) | - | 用不同的展开模式获取对应下标的子节点。 |
| [int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_list_closeallswipeactions) | - | 收起展开状态下的ListItem。 |
| [ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)](#oh_arkui_getcontextbynode) | - | Obtain the UIContext pointer to the page where the node is located. |
| [int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))](#oh_arkui_registersystemcolormodechangeevent) | - | The event called when the system color mode changes. Only one system color change callback can be registered for the same component. |
| [void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemcolormodechangeevent) | - | Unregister the event callback when the system color mode changes. |
| [int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))](#oh_arkui_registersystemfontstylechangeevent) | - | The event called when the system font style changes. Only one system font change callback can be registered for the same component. |
| [void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemfontstylechangeevent) | - | Unregister the event callback when the system font style changes. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontsizescale) | - | Retrieve the font size value for system font change events. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontweightscale) | - | Retrieve the font thickness values for system font change events. |
| [int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getattachednodehandlebyid) | - | 根据用户id获取目标节点。 |
| [int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)](#oh_arkui_nodeutils_moveto) | - | 将节点移动到目标父节点下，作为子节点。 |
| [int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_invalidateattributes) | - | 在当前帧触发节点属性更新。 当前节点的属性在构建阶段后被修改，这些改动不会立即生效，而是延迟到下一帧统一处理。 此功能强制当前帧内即时节点更新，确保同步应用渲染效果。 |
| [int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_setcrosslanguageoption) | - | 设置目标节点跨语言设置属性的能力。 |
| [int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_getcrosslanguageoption) | - | 获取目标节点跨语言设置属性的配置项。 |
| [int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onLayoutCompleted)(void* userData))](#oh_arkui_registerlayoutcallbackonnodehandle) | - | Registers a callback for node when layout is completed. |
| [int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onDrawCompleted)(void* userData))](#oh_arkui_registerdrawcallbackonnodehandle) | - | Registers a callback for node when draw is completed. |
| [int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterlayoutcallbackonnodehandle) | - | Unregisters the layout completed callback for node. |
| [int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterdrawcallbackonnodehandle) | - | Unregisters the draw completed callback for node. |
| [int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelmap)](#oh_arkui_getnodesnapshot) | - | Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered, the snapshot operation will fail. When the <b>Pixelmap</b> object created is no longer in use, it should be released by calling {@link OH_PixelmapNative_Release}. |
| [int32_t OH_ArkUI_GetNodeSnapshotSizeLimitation(int32_t* maxWidth, int32_t* maxHeight)](#oh_arkui_getnodesnapshotsizelimitation) | - | Query the size limitation of the component snapshot. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getpositiontoparent) | - | 获取目标节点相对于父节点的偏移值，单位：px。 |
| [ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)](#oh_arkui_addsupporteduistates) | - | 设置组件支持的多态样式状态。为了更高效地处理，需传入所关注的状态值及对应的状态处理函数，当关注的状态发生时，处理函数会被执行。 可在回调中根据当前状态调整UI样式。当在同一个节点上多次调用该方法时，将以最后一次传入的状态及处理函数为准。 有些类型的组件节点，系统内部已有对某些状态的默认处理。例如，Button组件默认具备对PRESSED状态的样式变化，当在此类组件上使用此方法自定义状态处理时， 会先应用系统默认样式变化，再执行自定义的样式处理，最终效果为两者叠加。 可以通过指定excludeInner为true来禁用系统内部的默认样式效果，但这通常取决于系统内部实现规范是否允许。当调用该函数时，传入的statesChangeHandler函数会立即执行一次， 且无需特意注册对NORMAL状态的监听，只要注册了非NORMAL状态，当状态从任意状态变化回NORMAL时，系统都会进行回调，以便应用进行样式复原。 |
| [ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)](#oh_arkui_removesupporteduistates) | - | 删除注册的状态处理。当通过OH_ArkUI_AddSupportedUIStates注册的状态都被删除时，所注册的stateChangeHandler也不会再被执行。 |
| [int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(\*callback)(void* userData))](#oh_arkui_runtaskinscope) | - | 在目标UI上下文中执行传入的自定义回调函数。示例请参考：[在NDK中保证多实例场景功能正常](../../../ui/ndk-scope-task.md)。 |
| [int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getnodehandlebyuniqueid) | - | Get the node handle by uniqueId. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)](#oh_arkui_nodeutils_getnodeuniqueid) | - | 获取目标节点的uniqueId。 |
| [int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)](#oh_arkui_nativemodule_isinrenderstate) | - | 获取节点是否处于渲染状态，如果一个节点的对应RenderNode在渲染树上，则处于渲染状态。 |
| [int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_adoptchild) | - | 当前节点接纳目标节点为附属节点。被接纳的节点不能已有父节点。 调用该接口实际上不会将其添加为子节点，而是仅允许其接收对应子节点的生命周期回调。 |
| [int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_removeadoptedchild) | - | 移除被接纳的目标附属节点。 |
| [int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (\*colorInvertFunc)(uint32_t color))](#oh_arkui_setforcedarkconfig) | - | 为组件和实例设置反色算法。详细介绍请参考：[利用反色能力快速适配深色模式](../../../ui/ui-dark-light-color-adaptation.md#利用反色能力快速适配深色模式)。 |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonevent) | - | 注册目标节点的基础事件回调。<br> 当前支持的事件类型如下: 参考[ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype)中的NODE_ON_CLICK_EVENT、NODE_TOUCH_EVENT、NODE_EVENT_ON_APPEAR、 NODE_EVENT_ON_DISAPPEAR、NODE_ON_KEY_EVENT、NODE_ON_FOCUS、NODE_ON_BLUR、NODE_ON_HOVER、NODE_ON_MOUSE、NODE_ON_SIZE_CHANGE。 |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)](#oh_arkui_nativemodule_unregistercommonevent) | - | 注销目标节点的基础事件回调。 当前支持的事件类型请参考[OH_ArkUI_NativeModule_RegisterCommonEvent](capi-native-node-h.md#oh_arkui_nativemodule_registercommonevent)。 |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonvisibleareaapproximatechangeevent) | - | 注册限制回调间隔的可见区域变化的基础事件回调。 |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonvisibleareaapproximatechangeevent) | - | 注销限制回调间隔的可见区域变化的基础事件回调。 |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)](#oh_arkui_nativemodule_convertpositiontowindow) | - | 将点的坐标从指定节点的坐标系转换至当前窗口的坐标系。节点的坐标系考虑节点本身的变换，例如，节点A的变换效果为向左平移100，会使得其坐标系中的点的坐标也向左平移100。 |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)](#oh_arkui_nativemodule_convertpositionfromwindow) | - | 将点的坐标从当前窗口的坐标系转换至目标节点的坐标系。节点的坐标系考虑节点本身的变换，例如，节点A的变换效果为向左平移100，会使得其坐标系中的点的坐标也向左平移100。 |
| [int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)](#oh_arkui_swiper_finishanimation) | - | 停止指定的Swiper节点正在执行的翻页动画。 |
| [int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (\*asyncUITask)(void* asyncUITaskData), void (\*onFinish)(void* asyncUITaskData))](#oh_arkui_postasyncuitask) | - | 将asyncUITask函数提交至ArkUI框架提供的非UI线程中执行，asyncUITask函数执行完毕后，在UI线程调用onFinish函数。 适用于多线程创建UI组件的场景，开发者可使用此接口在非UI线程创建UI组件，随后在UI线程将创建完成的组件挂载至主树上。 |
| [int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitask) | - | 将task函数提交至UI线程中执行。 适用于多线程创建UI组件的场景，当开发者在自建的线程中创建UI组件时，可以使用此接口将创建完成的组件挂载到UI线程的主树上。 |
| [int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)](#oh_arkui_nativemodule_atomicservicemenubarsetvisible) | - | 设置菜单栏的可见性。 |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonareaapproximatechangeevent) | - | Registers a callback for listening for component dimension and area changes.<br> This function can be called for a valid [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node at any time. The newly registered callback will replace the previously registered callback for this event and will take effect from the next frame. When the callback is no longer needed, call [OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent](capi-native-node-h.md#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) to unregister it. Otherwise, the callback will be automatically unregistered when the node is released. |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) | - | Unregisters the callback bound to the dimensions and area changes of a component. |
| [int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitaskandwait) | - | 将task函数提交至UI线程中执行，调用此接口的线程将阻塞，直至task函数执行完成。在UI线程调用此接口等同于同步调用task函数。 适用于多线程创建UI组件的场景，当开发者在多线程创建组件过程中需要调用仅支持UI线程的函数时，使用此接口返回UI线程调用函数，调用完成后继续多线程创建组件。 当UI线程负载较高时，调用此接口的非UI线程可能长时间阻塞，影响多线程创建UI组件的性能，不建议频繁使用。 |
| [int32_t OH_ArkUI_Swiper_StartFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_startfakedrag) | - | Start a fake drag of the Swiper node. Call OH_ArkUI_Swiper_FakeDragBy to simulate the drag motion. Call OH_ArkUI_Swiper_StopFakeDrag to complete the fake drag. A fake drag can be interrupted by a real drag. If you need to ignore touch events and other user input during a fake drag, use NODE_SWIPER_DISABLE_SWIPE. |
| [int32_t OH_ArkUI_Swiper_FakeDragBy(ArkUI_NodeHandle node, float offset, bool* isConsumedOffset)](#oh_arkui_swiper_fakedragby) | - | Fake drag by an offset of the Swiper node. The OH_ArkUI_Swiper_StartFakeDrag must be called first. |
| [int32_t OH_ArkUI_Swiper_StopFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_stopfakedrag) | - | Stop a fake drag of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_IsFakeDragging(ArkUI_NodeHandle node, bool* isFakeDragging)](#oh_arkui_swiper_isfakedragging) | - | Get the fake drag state of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_ShowPrevious(ArkUI_NodeHandle node)](#oh_arkui_swiper_showprevious) | - | Show the previous page of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_ShowNext(ArkUI_NodeHandle node)](#oh_arkui_swiper_shownext) | - | Show the next page of the Swiper node. |
| [int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)](#oh_arkui_nativemodule_getpagerootnodehandlebycontext) | - | 获取指定实例的页面的根节点。 |
| [ArkUI_GestureCollectInterceptInfo* OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_getgesturecollectinterceptinfo) | - | Obtains the <b>ArkUI_GestureCollectInterceptInfo</b> object from a specified <b>ArkUI_NodeEvent</b> object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_SetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy policy)](#oh_arkui_nativemodule_setchildmountpolicy) | - | Set the subnode mounting policy of the target node. |
| [ArkUI_ErrorCode OH_ArkUI_NodeUtils_SetUiDvsyncSwitch(ArkUI_ContextHandle context, bool enable)](#oh_arkui_nodeutils_setuidvsyncswitch) | - | 设置UI Dvsync开关。开启后系统会更及时地响应Vsync请求，更频繁执行渲染任务。通常在自渲染框架中动效开始时使能，结束后关闭，以确保动画效果更加流畅，同时避免频繁的Vsync影响其他业务。在非UI线程上调用此函数将导致应用退出。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event) | Defines the callback function of a node content event.<br>**起始版本：** 12 |

## 枚举类型说明

### ArkUI_NodeType

```c
enum ArkUI_NodeType
```

**描述：**

Enumerates ArkUI component types that can be created on the native side.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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
| ARKUI_NODE_XCOMPONENT_TEXTURE | TEXTURE类型XComponent。 @since 18 |
| ARKUI_NODE_CHECKBOX_GROUP = 21 | Check box group. @since 15 |
| ARKUI_NODE_TEXT_EDITOR = 22 |  |
| ARKUI_NODE_STACK = MAX_NODE_SCOPE_NUM | Stack container. |
| ARKUI_NODE_SWIPER | Swiper. |
| ARKUI_NODE_SCROLL | 滚动容器。 |
| ARKUI_NODE_LIST | 列表。 |
| ARKUI_NODE_LIST_ITEM | 列表项。 |
| ARKUI_NODE_LIST_ITEM_GROUP | 列表item分组。 |
| ARKUI_NODE_COLUMN | Column container. |
| ARKUI_NODE_ROW | Row container. |
| ARKUI_NODE_FLEX | Flex container. |
| ARKUI_NODE_REFRESH | Refresh component. |
| ARKUI_NODE_WATER_FLOW | 瀑布流容器。 |
| ARKUI_NODE_FLOW_ITEM | 瀑布流子组件。 |
| ARKUI_NODE_RELATIVE_CONTAINER | Relative layout component. |
| ARKUI_NODE_GRID | 网格容器。 |
| ARKUI_NODE_GRID_ITEM | 网格子组件。 |
| ARKUI_NODE_CUSTOM_SPAN | Custom span. |
| ARKUI_NODE_EMBEDDED_COMPONENT |  |
| ARKUI_NODE_UNDEFINED |  |
| ARKUI_NODE_PICKER = 1018 |  |
| ARKUI_NODE_ARC_LIST = 1019 |  |
| ARKUI_NODE_ARC_LIST_ITEM = 1020 |  |
| ARKUI_NODE_ARC_SCROLL_BAR = 1021 |  |

### ArkUI_NodeDirtyFlag

```c
enum ArkUI_NodeDirtyFlag
```

**描述：**

Defines the dirty area flag passed in the <b>::markDirty</b> API.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_NEED_MEASURE = 1 | Remeasure.<br> When this type of flag is specified, re-layout is triggered by default. |
| NODE_NEED_LAYOUT | Re-layout. |
| NODE_NEED_RENDER | Re-rendering. |

### ArkUI_NodeCustomEventType

```c
enum ArkUI_NodeCustomEventType
```

**描述：**

Defines the custom component event type.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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

**描述：**

Enumerates component adapter events.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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

**描述：**

Defines the node content event type.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_CONTENT_EVENT_ON_ATTACH_TO_WINDOW = 0 | Defines the attach event. |
| NODE_CONTENT_EVENT_ON_DETACH_FROM_WINDOW = 1 | Defines the detach event. |

### ArkUI_InspectorErrorCode

```c
enum ArkUI_InspectorErrorCode
```

**描述：**

Enumerates the inspector error codes.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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

**描述：**

Obtains the type of a component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) | Returns the type of the component event. |

### OH_ArkUI_NodeEvent_GetTargetId()

```c
int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)
```

**描述：**

Obtains the custom ID of a component event.<br> The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be applied to the dispatch logic of the same event entry function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver).

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the custom ID of the component event. |

### OH_ArkUI_NodeEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)
```

**描述：**

Obtains the component object that triggers a component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_NodeHandle | Returns the component object that triggers the component event. |

### OH_ArkUI_NodeEvent_GetInputEvent()

```c
ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)
```

**描述：**

获取组件事件中的输入事件（如触碰事件）数据。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | 组件事件指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_UIInputEvent* | ArkUI_UIInputEvent 输入事件数据指针。 |

### OH_ArkUI_NodeEvent_GetNodeComponentEvent()

```c
ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)
```

**描述：**

Obtains the numerical data in a component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeComponentEvent*](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | Returns the pointer to the numerical data. |

### OH_ArkUI_NodeEvent_GetStringAsyncEvent()

```c
ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)
```

**描述：**

Obtains the string data in a component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_StringAsyncEvent*](capi-arkui-nativemodule-arkui-stringasyncevent.md) | Returns the pointer to the string data. |

### OH_ArkUI_NodeEvent_GetTextChangeEvent()

```c
ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)
```

**描述：**

Obtains the ArkUI_TextChangeEvent data from a component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | Pointer to a component event. It cannot be null. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextChangeEvent*](capi-arkui-nativemodule-arkui-textchangeevent.md) | Returns the pointer to the <b>ArkUI_TextChangeEvent</b> object. |

### OH_ArkUI_NodeEvent_GetUserData()

```c
void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)
```

**描述：**

Obtains the custom data in a component event.<br> This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the event is triggered.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| void* | Returns the pointer to the custom data. |

### OH_ArkUI_NodeEvent_GetNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)
```

**描述：**

获取组件回调事件的数字类型参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | 组件事件指针。 |
| int32_t index | 返回值索引。 |
| ArkUI_NumberValue* value | 具体返回值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 组件事件中参数长度超限。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 组件事件中不存在该数据。 |

### OH_ArkUI_NodeEvent_GetStringValue()

```c
int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)
```

**描述：**

获取组件回调事件的字符串类型参数，字符串数据仅在事件回调过程中有效，需要在事件回调外使用建议进行额外拷贝处理。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | 组件事件指针。 |
| int32_t index | 返回值索引。 |
| char** string | 字符串数组的指针。 |
| int32_t* stringSize | 字符串数组的长度。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 组件事件中参数长度超限。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 组件事件中不存在该数据。 |

### OH_ArkUI_NodeEvent_SetReturnNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)
```

**描述：**

设置组件回调事件的返回值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | 组件事件指针。 |
| ArkUI_NumberValue* value | 事件数字类型数组。 |
| int32_t size | 数组长度。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 组件事件中不存在该数据。 |

### OH_ArkUI_NodeEvent_GetTouchTestInfo()

```c
ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)
```

**描述：**

获取组件事件中的触摸测试信息。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| {pointer} | nodeEvent Indicates the pointer to an <b>ArkUI_NodeEvent</b> object. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_TouchTestInfo* | 返回指向[ArkUI_TouchTestInfo](capi-arkui-eventmodule-arkui-touchtestinfo.md)对象的指针。若传入的参数无效或并非触摸测试信息，则返回null。 |

### OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent()

```c
OH_ArkUI_TextEditorChangeEvent* OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent(ArkUI_NodeEvent* event)
```

**描述：**

获取组件事件中的TextEditor组件文本内容变化数据。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* event | 指向[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)组件事件对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorChangeEvent*](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | 指向[OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md)数据对象的指针。      <br>若传入的参数无效或并非TextEditor组件文本内容变化事件信息，则返回<b>null</b>。 |

### OH_ArkUI_NodeAdapter_Create()

```c
ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()
```

**描述：**

Creates a component adapter.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

### OH_ArkUI_NodeAdapter_Dispose()

```c
void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)
```

**描述：**

Destroys a component adapter.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

### OH_ArkUI_NodeAdapter_SetTotalNodeCount()

```c
int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)
```

**描述：**

设置Adapter中的元素总数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t size | 元素数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapter_GetTotalNodeCount()

```c
uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)
```

**描述：**

Obtains the total number of elements in the specified adapter.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Returns the total number of elements in the adapter. |

### OH_ArkUI_NodeAdapter_RegisterEventReceiver()

```c
int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(
ArkUI_NodeAdapterHandle handle, void* userData, void (*receiver)(ArkUI_NodeAdapterEvent* event))
```

**描述：**

注册Adapter相关回调事件。在相关回调事件不需要之后，需要执行[OH_ArkUI_NodeAdapter_UnregisterEventReceiver](capi-native-node-h.md#oh_arkui_nodeadapter_unregistereventreceiver)接口注销相关回调事件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| void\* userData | 自定义数据。 |
| void (\*receiver)(ArkUI_NodeAdapterEvent\* event) | 事件接收回调。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapter_UnregisterEventReceiver()

```c
void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)
```

**描述：**

Deregisters an event callback for the adapter.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

### OH_ArkUI_NodeAdapter_ReloadAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)
```

**描述：**

通知Adapter进行全量元素变化。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapter_ReloadItem()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述：**

通知Adapter进行局部元素变化。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t startPosition | 元素变化起始位置。 |
| uint32_t itemCount | 元素变化数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_RemoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_RemoveItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述：**

通知Adapter进行局部元素删除。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t startPosition | 元素删除起始位置。 |
| uint32_t itemCount | 元素删除数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_InsertItem()

```c
int32_t OH_ArkUI_NodeAdapter_InsertItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述：**

通知Adapter进行局部元素插入。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t startPosition | 元素插入起始位置。 |
| uint32_t itemCount | 元素插入数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_MoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)
```

**描述：**

通知Adapter进行局部元素移位。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| uint32_t from | 元素移位起始位置。 |
| uint32_t to | 元素移位结束位置。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapter_GetAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)
```

**描述：**

获取存储在Adapter中的所有元素。<br> 接口调用会返回元素的数组对象指针，该指针指向的内存数据需要开发者手动释放。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | 组件适配器对象。 |
| ArkUI_NodeHandle** items | 适配器内节点数组。 |
| uint32_t* size | 元素数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n         {@link ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR} NodeAdapter需要添加监听器。 |

### OH_ArkUI_NodeAdapterEvent_GetUserData()

```c
void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)
```

**描述：**

Obtains the custom data passed in during registration of the specified event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

### OH_ArkUI_NodeAdapterEvent_GetType()

```c
ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)
```

**描述：**

Obtains the event type.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeAdapterEventType](capi-native-node-h.md#arkui_nodeadaptereventtype) | Returns the event type. |

### OH_ArkUI_NodeAdapterEvent_GetRemovedNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)
```

**描述：**

Obtains the element to be removed for the event to be destroyed.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_NodeHandle | Returns the element to be removed. |

### OH_ArkUI_NodeAdapterEvent_GetItemIndex()

```c
uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)
```

**描述：**

Obtains the index of the element to be operated for the specified adapter event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Returns the index of the element. |

### OH_ArkUI_NodeAdapterEvent_GetHostNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)
```

**描述：**

Obtains the scrollable container node that uses the specified adapter.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_NodeHandle | Returns the scrollable container node that uses the specified adapter. |

### OH_ArkUI_NodeAdapterEvent_SetItem()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)
```

**描述：**

设置需要新增到Adapter中的组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |
| ArkUI_NodeHandle node | 待添加的组件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeAdapterEvent_SetNodeId()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)
```

**描述：**

设置生成的组件标识。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | 适配器事件对象。 |
| int32_t id | 设置返回的组件标识。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n         [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure()

```c
ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)
```

**描述：**

Obtains the size constraint for measurement through a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_LayoutConstraint* | Returns the pointer to the size constraint. |

### OH_ArkUI_NodeCustomEvent_GetPositionInLayout()

```c
ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)
```

**描述：**

Obtains the expected position of a component relative to its parent component in the layout phase through a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_IntOffset | Returns the expected position relative to the parent component. |

### OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw()

```c
ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)
```

**描述：**

Obtains the drawing context through a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_DrawContext* | Returns the drawing context. |

### OH_ArkUI_NodeCustomEvent_GetEventTargetId()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)
```

**描述：**

Obtains the ID of a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the ID of the custom component event. |

### OH_ArkUI_NodeCustomEvent_GetUserData()

```c
void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)
```

**描述：**

Obtains custom event parameters through a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| void* | Returns the custom event parameters. |

### OH_ArkUI_NodeCustomEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)
```

**描述：**

Obtains a component object through a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_NodeHandle | Returns the component object. |

### OH_ArkUI_NodeCustomEvent_GetEventType()

```c
ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)
```

**描述：**

Obtains the event type through a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeCustomEventType](capi-native-node-h.md#arkui_nodecustomeventtype) | Returns the type of the custom component event. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)
```

**描述：**

Obtains the measurement information of a custom span through a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |
| ArkUI_CustomSpanMeasureInfo* info | Indicates the measurement information to be obtained. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.         Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.         <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics()

```c
int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)
```

**描述：**

Sets the measurement metrics of a custom span through a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |
| ArkUI_CustomSpanMetrics* metrics | Indicates the measurement metrics to set. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.         Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.         <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)
```

**描述：**

Obtains the drawing information of a custom span through a custom component event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |
| ArkUI_CustomSpanDrawInfo* info | Indicates the drawing information to obtain. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.         Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.         <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### ArkUI_NodeContentCallback()

```c
typedef void (*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)
```

**描述：**

Defines the callback function of a node content event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

### OH_ArkUI_NodeContent_RegisterCallback()

```c
int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)
```

**描述：**

注册NodeContent事件函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeContentHandle content | 需要注册事件的NodeContent对象。 |
| [ArkUI_NodeContentCallback](capi-native-node-h.md#arkui_nodecontentcallback) callback | 事件触发时需要执行的函数回调。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeContentEvent_GetEventType()

```c
ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)
```

**描述：**

Obtains the type of a node content event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Indicates the pointer to the node content event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeContentEventType](capi-native-node-h.md#arkui_nodecontenteventtype) | Returns the type of the node content event. |

### OH_ArkUI_NodeContentEvent_GetNodeContentHandle()

```c
ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)
```

**描述：**

Obtains the node content object that triggers a node content event.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Indicates the pointer to the node content event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_NodeContentHandle | Returns the node content object that triggers the node content event. |

### OH_ArkUI_NodeContent_SetUserData()

```c
int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)
```

**描述：**

Saves custom data on the specified node content.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeContentHandle content | Indicates the node content on which the custom data will be saved. |
| void* userData | Indicates the custom data to be saved. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeContent_GetUserData()

```c
void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)
```

**描述：**

Obtains the custom data saved on the specified node content.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeContentHandle content | Indicates the target node content. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| void* | Returns the custom data. |

### OH_ArkUI_NodeContent_AddNode()

```c
int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**描述：**

将一个ArkUI组件节点添加到对应的NodeContent对象下。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeContentHandle content | 需要被添加节点的NodeContent对象。 |
| ArkUI_NodeHandle node | 需要被添加的节点。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 子节点已经被接纳。从API version 22开始支持。 |

### OH_ArkUI_NodeContent_RemoveNode()

```c
int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**描述：**

删除NodeContent对象下的一个ArkUI组件节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeContentHandle content | 需要被删除节点的NodeContent对象。 |
| ArkUI_NodeHandle node | 需要被删除的节点。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeContent_InsertNode()

```c
int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)
```

**描述：**

将一个ArkUI组件节点插入到对应的NodeContent对象的特定位置下。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeContentHandle content | 需要被插入节点的NodeContent对象。 |
| ArkUI_NodeHandle node | 需要被插入的节点。 |
| int32_t position | 需要被插入的位置。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 子节点已经被接纳。从API version 22开始支持。 |

### OH_ArkUI_NodeUtils_GetLayoutSize()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)
```

**描述：**

获取组件布局区域的大小。 布局区域大小不包含图形变化属性，如缩放。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针。 |
| ArkUI_IntSize* size | 组件handle的绘制区域尺寸，单位：px。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPosition()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)
```

**描述：**

获取组件布局区域相对父组件的位置。 布局区域相对位置不包含图形变化属性，如平移。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针。 |
| ArkUI_IntOffset* localOffset | 组件handle相对父组件的偏移值，单位：px。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPositionInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**描述：**

获取组件布局区域相对窗口的位置。 布局区域相对位置不包含图形变化属性，如平移。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针。 |
| ArkUI_IntOffset* globalOffset | 组件handle相对窗口的偏移值，单位：px。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPositionInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)
```

**描述：**

获取组件布局区域相对屏幕的位置。 布局区域相对位置不包含图形变化属性，如平移。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针。 |
| ArkUI_IntOffset* screenOffset | 组件handle相对屏幕的偏移值，单位：px。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)
```

**描述：**

获取组件相对于全局屏幕的偏移。 布局区域相对位置不包含图形变化属性，如平移。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针。 |
| ArkUI_IntOffset* offset | 组件handle相对屏幕的偏移值，单位：px。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**描述：**

Obtain the position of the component in the window, including the properties of graphic translation changes.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| ArkUI_IntOffset* translateOffset | The cumulative offset value of the component handle itself, parent components, and ancestor nodes, in px. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**描述：**

Obtain the position of the component on the screen, including the attributes of graphic translation changes.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| ArkUI_IntOffset* translateOffset | The cumulative offset value of the component handle itself, parent components, and ancestor nodes, in px. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_AddCustomProperty()

```c
void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)
```

**描述：**

设置组件的自定义属性。该接口仅在主线程生效。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针。 |
| const char* name | 自定义属性的名称。不允许传入空指针。 |
| const char* value | 对应key参数名称的自定义属性的值。不允许传入空指针。 |

### OH_ArkUI_NodeUtils_RemoveCustomProperty()

```c
void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)
```

**描述：**

移除组件已设置的自定义属性。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针。 |
| const char* name | 自定义属性的名称。 |

### OH_ArkUI_NodeUtils_GetCustomProperty()

```c
int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)
```

**描述：**

获取组件的自定义属性的值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针。 |
| const char* name | 自定义属性的名称。 |
| ArkUI_CustomProperty** handle | 获取的对应key参数名称的自定义属性的结构体。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetParentInPageTree()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)
```

**描述：**

获取父节点，可获取由ArkTs创建的组件节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_NodeHandle | 组件的指针，如果没有返回NULL。 |

### OH_ArkUI_NodeUtils_GetActiveChildrenInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)
```

**描述：**

获取某个节点所有活跃的子节点。Span将不会被计入子节点的统计中。 在LazyForEach场景中，推荐使用[OH_ArkUI_NodeUtils_GetChildWithExpandMode](capi-native-node-h.md#oh_arkui_nodeutils_getchildwithexpandmode)接口进行遍历。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle head | 传入需要获取的节点。 |
| ArkUI_ActiveChildrenInfo** handle | 对应head节点子节点信息的结构体。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetCurrentPageRootNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)
```

**描述：**

获取当前页面的根节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_NodeHandle | 根节点的指针，如果没有返回NULL。 |

### OH_ArkUI_NodeUtils_IsCreatedByNDK()

```c
bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)
```

**描述：**

获取组件是否由C-API创建的标签。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| bool | 节点是否由C-API创建的Tag，true代表由C-API创建，false代表非C-API创建。 |

### OH_ArkUI_NodeUtils_GetNodeType()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)
```

**描述：**

获取节点的类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 节点的类型，具体已开放类型参考[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)，未开放结点返回-1。 |

### OH_ArkUI_NodeUtils_GetWindowInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)
```

**描述：**

获取节点所属的窗口信息。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点对象。 |
| ArkUI_HostWindowInfo** info | 窗口信息。使用[OH_ArkUI_HostWindowInfo_Destroy](capi-native-type-h.md#oh_arkui_hostwindowinfo_destroy)释放内存。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。      <br>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) CAPI初始化错误。      <br>[ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 节点未挂载到节点树上。 |

### OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**描述：**

获取目标节点在树上的第一个子节点的下标。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点的指针。 |
| uint32_t* index | 子节点的下标值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**描述：**

获取目标节点在树上的最后一个子节点的下标。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点的指针。 |
| uint32_t* index | 子节点的下标值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetChildWithExpandMode()

```c
int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)
```

**描述：**

用不同的展开模式获取对应下标的子节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点的指针。 |
| int32_t position | 对应子节点的下标。 |
| ArkUI_NodeHandle* subnode | 获取子节点的指针。 |
| uint32_t expandMode | 节点遍历展开方式。 [ArkUI_ExpandMode](capi-native-type-h.md#arkui_expandmode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_List_CloseAllSwipeActions()

```c
int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (*onFinish)(void* userData))
```

**描述：**

收起展开状态下的ListItem。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | 需要注册事件的节点对象。 |
| void\* userData | 自定义事件参数，当事件触发时在回调参数中携带回来。 |
| void (\*onFinish)(void\* userData) | 在收起动画完成后触发的回调。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 组件不支持该事件。 |

### OH_ArkUI_GetContextByNode()

```c
ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)
```

**描述：**

Obtain the UIContext pointer to the page where the node is located.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | The node. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ContextHandle | The UIContext pointer.         If a null pointer is returned, it may be because the node is empty. |

### OH_ArkUI_RegisterSystemColorModeChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node, void* userData, void (*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))
```

**描述：**

The event called when the system color mode changes. Only one system color change callback can be registered for the same component.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode | Callback Events. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.         [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_UnregisterSystemColorModeChangeEvent()

```c
void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)
```

**描述：**

Unregister the event callback when the system color mode changes.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the target node. |

### OH_ArkUI_RegisterSystemFontStyleChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node, void* userData, void (*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))
```

**描述：**

The event called when the system font style changes. Only one system font change callback can be registered for the same component.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent\* event | Callback Events. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.         [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.         [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_UnregisterSystemFontStyleChangeEvent()

```c
void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)
```

**描述：**

Unregister the event callback when the system font style changes.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the target node. |

### OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)
```

**描述：**

Retrieve the font size value for system font change events.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const ArkUI_SystemFontStyleEvent* event | Indicates a pointer to the current system font change event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| float | Updated system font size scaling factor. Default value: 1.0. |

### OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)
```

**描述：**

Retrieve the font thickness values for system font change events.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const ArkUI_SystemFontStyleEvent* event | Indicates a pointer to the current system font change event. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| float | The updated system font thickness scaling factor. Default value: 1.0. |

### OH_ArkUI_NodeUtils_GetAttachedNodeHandleById()

```c
int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)
```

**描述：**

根据用户id获取目标节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* id | 目标节点的id。 |
| ArkUI_NodeHandle* node | 目标节点的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_MoveTo()

```c
int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)
```

**描述：**

将节点移动到目标父节点下，作为子节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 待移动的节点对象。 |
| ArkUI_NodeHandle target_parent | 目标父节点指针。 |
| int32_t index | 转移后的节点下标，如果下标值为非法值，则添加在目标父节点的最后一位。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) CAPI初始化错误。          [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 子节点已经被接纳。从API version 22开始支持。 |

### OH_ArkUI_NativeModule_InvalidateAttributes()

```c
int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)
```

**描述：**

在当前帧触发节点属性更新。 当前节点的属性在构建阶段后被修改，这些改动不会立即生效，而是延迟到下一帧统一处理。 此功能强制当前帧内即时节点更新，确保同步应用渲染效果。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 待更新的节点对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_SetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**描述：**

设置目标节点跨语言设置属性的能力。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点的指针。 |
| ArkUI_CrossLanguageOption* option | 跨语言配置项 [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeUtils_GetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**描述：**

获取目标节点跨语言设置属性的配置项。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点的指针。 |
| ArkUI_CrossLanguageOption* option | 跨语言配置项 [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_RegisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (*onLayoutCompleted)(void* userData))
```

**描述：**

Registers a callback for node when layout is completed.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data used in onLayoutCompleted callback function. |
| void (\*onLayoutCompleted)(void\* userData) | Indicates the function when layout completed is callback. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter is incorrect. |

### OH_ArkUI_RegisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (*onDrawCompleted)(void* userData))
```

**描述：**

Registers a callback for node when draw is completed.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data used in onDrawCompleted callback function. |
| void (\*onDrawCompleted)(void\* userData) | Indicates the function when draw completed is callback. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter is incorrect. |

### OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**描述：**

Unregisters the layout completed callback for node.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the target node. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter is incorrect. |

### OH_ArkUI_UnregisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**描述：**

Unregisters the draw completed callback for node.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the target node. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter is incorrect. |

### OH_ArkUI_GetNodeSnapshot()

```c
int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelmap)
```

**描述：**

Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered, the snapshot operation will fail. When the <b>Pixelmap</b> object created is no longer in use, it should be released by calling {@link OH_PixelmapNative_Release}.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | Target node. |
| ArkUI_SnapshotOptions* snapshotOptions | Snapshot settings. If the value is null, the default settings are used. Snapshot settings include scaling, color space, and dynamic range configuration. Scaling: floating-point value greater than 0. Color space: <b>3</b> (DISPLAY_P3), <b>4</b> (SRGB), <b>27</b> (DISPLAY_BT2020_SRGB). Dynamic range: [ArkUI_DynamicRangeMode](capi-image-h.md#arkui_dynamicrangemode). |
| OH_PixelmapNative** pixelmap | Pointer to the <b>Pixelmap</b> object created by the system. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Result code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.          Returns [ARKUI_ERROR_CODE_INTERNAL_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the snapshot fails, returning a null pointer.          Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the snapshot operation times out.          Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the provided color space or          dynamic range mode is not supported.          Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the isAuto parameter of the color          space or dynamic range mode is set to true for offscreen node snapshot. |

### OH_ArkUI_GetNodeSnapshotSizeLimitation()

```c
int32_t OH_ArkUI_GetNodeSnapshotSizeLimitation(int32_t* maxWidth, int32_t* maxHeight)
```

**描述：**

Query the size limitation of the component snapshot.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t* maxWidth | Maximum width limit of the component snapshot, in px. |
| int32_t* maxHeight | Maximum height limit of the component snapshot, in px. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Invalid function parameter. |

### OH_ArkUI_NodeUtils_GetPositionToParent()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**描述：**

获取目标节点相对于父节点的偏移值，单位：px。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点。 |
| ArkUI_IntOffset* globalOffset | 目标节点相对父节点的偏移值，单位：px。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_AddSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)
```

**描述：**

设置组件支持的多态样式状态。为了更高效地处理，需传入所关注的状态值及对应的状态处理函数，当关注的状态发生时，处理函数会被执行。 可在回调中根据当前状态调整UI样式。当在同一个节点上多次调用该方法时，将以最后一次传入的状态及处理函数为准。 有些类型的组件节点，系统内部已有对某些状态的默认处理。例如，Button组件默认具备对PRESSED状态的样式变化，当在此类组件上使用此方法自定义状态处理时， 会先应用系统默认样式变化，再执行自定义的样式处理，最终效果为两者叠加。 可以通过指定excludeInner为true来禁用系统内部的默认样式效果，但这通常取决于系统内部实现规范是否允许。当调用该函数时，传入的statesChangeHandler函数会立即执行一次， 且无需特意注册对NORMAL状态的监听，只要注册了非NORMAL状态，当状态从任意状态变化回NORMAL时，系统都会进行回调，以便应用进行样式复原。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | 目标节点。 |
| int32_t uiStates | 目标节点需要处理的目标UI状态。 所有目标UI状态的组合结果可以通过“\|”操作来计算。例如：targetUIStates = ArkUI_UIState::PRESSED \| ArkUI_UIState::FOCUSED。 |
| void (statesChangeHandler)(int32_t currentStates | UI状态改变处理函数。 返回当前UI状态，该值是所有当前状态枚举值“\|”计算的结果，可以通过执行“&”操作来确定状态。例如：if (currentStates & ArkUI_UIState::PRESSED == ArkUI_UIState::PRESSED)。 但是，对于正常状态检查，应直接使用等号。例如：if (currentStates == ArkUI_UIState::NORMAL) |
| bool excludeInner | 禁止内部默认状态样式的标志。​​true​​表示禁用系统内部的默认样式，false表示不禁用。 |
| void\* userData) | onDrawCompleted回调函数中使用的自定义数据。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_RemoveSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)
```

**描述：**

删除注册的状态处理。当通过OH_ArkUI_AddSupportedUIStates注册的状态都被删除时，所注册的stateChangeHandler也不会再被执行。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点。 |
| int32_t uiStates | 节点需要删除的目标UI状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_RunTaskInScope()

```c
int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(*callback)(void* userData))
```

**描述：**

在目标UI上下文中执行传入的自定义回调函数。示例请参考：[在NDK中保证多实例场景功能正常](../../../ui/ndk-scope-task.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle uiContext | 表示目标UI上下文的指针。 |
| void\* userData | 开发者自定义数据指针，以便在回调函数中处理自定义数据，开发者需自行保证自定义函数被执行时的数据有效性。 |
| void(\*callback)(void\* userData) | 开发者自定义回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) CAPI初始化错误。      <br>[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) UIContext对象无效。      <br>[ARKUI_ERROR_CODE_CALLBACK_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 回调函数无效。 |

### OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)
```

**描述：**

Get the node handle by uniqueId.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const uint32_t uniqueId | The uniqueId of the target node handle. |
| ArkUI_NodeHandle* node | The handle of target node handle. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) success.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception.          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the CAPI init error. |

### OH_ArkUI_NodeUtils_GetNodeUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)
```

**描述：**

获取目标节点的uniqueId。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI节点指针。 |
| int32_t* uniqueId | 目标节点的uniqueId。组件标识ID只读，且进程内唯一，若该节点存在，返回该节点的uniqueId值；否则返回-1。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 方法参数错误。      <br>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) CAPI初始化错误。 |

### OH_ArkUI_NativeModule_IsInRenderState()

```c
int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)
```

**描述：**

获取节点是否处于渲染状态，如果一个节点的对应RenderNode在渲染树上，则处于渲染状态。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI节点指针。 |
| bool* isInRenderState | 节点是否处于渲染状态。true：处于渲染状态；false：不处于渲染状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 方法参数错误。 \n          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) CAPI初始化错误。 |

### OH_ArkUI_NativeModule_AdoptChild()

```c
int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**描述：**

当前节点接纳目标节点为附属节点。被接纳的节点不能已有父节点。 调用该接口实际上不会将其添加为子节点，而是仅允许其接收对应子节点的生命周期回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针，指定待接纳节点的父节点。 |
| ArkUI_NodeHandle child | ArkUI_NodeHandle指针，指定待被接纳的子节点。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) CAPI初始化错误。 \n          [ARKUI_ERROR_CODE_NODE_HAS_PARENT](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 被接纳的节点已有父节点。 \n          [ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 节点无法被接纳为附属节点。 \n          [ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 节点无法接纳其它附属节点。 |

### OH_ArkUI_NativeModule_RemoveAdoptedChild()

```c
int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**描述：**

移除被接纳的目标附属节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle指针，父节点。 |
| ArkUI_NodeHandle child | ArkUI_NodeHandle指针，将要被移除的子节点。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) CAPI初始化错误。 \n          [ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 节点不是被目标节点接纳的附属节点。 |

### OH_ArkUI_SetForceDarkConfig()

```c
int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (*colorInvertFunc)(uint32_t color))
```

**描述：**

为组件和实例设置反色算法。详细介绍请参考：[利用反色能力快速适配深色模式](../../../ui/ui-dark-light-color-adaptation.md#利用反色能力快速适配深色模式)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle uiContext | UI实例对象指针。  如果该值为null，则该功能适用于整个应用进程。 |
| bool forceDark | 是否使用反色能力。取值为true：组件使用反色能力，取值为false：组件不使用反色能力。 |
| [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype) nodeType | 指定使用反色能力生效组件范围。  ARKUI_NODE_UNDEFINED代表对所有组件类型生效。 |
| uint32_t (\*colorInvertFunc)(uint32_t color) | 开发者自定义反色算法函数。  如果该值为nullptr，则对组件使用系统默认反色算法，即三原色取反。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) CAPI初始化错误。 \n          [ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 反色能力入参错误。 |

### OH_ArkUI_NativeModule_RegisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**描述：**

注册目标节点的基础事件回调。<br> 当前支持的事件类型如下: 参考[ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype)中的NODE_ON_CLICK_EVENT、NODE_TOUCH_EVENT、NODE_EVENT_ON_APPEAR、 NODE_EVENT_ON_DISAPPEAR、NODE_ON_KEY_EVENT、NODE_ON_FOCUS、NODE_ON_BLUR、NODE_ON_HOVER、NODE_ON_MOUSE、NODE_ON_SIZE_CHANGE。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | 目标节点。 |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | 事件类型。 |
| void\* userData | 开发者自定义的数据指针，以便在回调函数中处理自定义数据，需确保自定义函数执行时数据有效。 |
| void (\*callback)(ArkUI_NodeEvent\* event) | 开发者自定义的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。      <br>[ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 暂不支持该事件类型。 |

### OH_ArkUI_NativeModule_UnregisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)
```

**描述：**

注销目标节点的基础事件回调。 当前支持的事件类型请参考[OH_ArkUI_NativeModule_RegisterCommonEvent](capi-native-node-h.md#oh_arkui_nativemodule_registercommonevent)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点。 |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | 事件类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 暂不支持该事件类型。 |

### OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**描述：**

注册限制回调间隔的可见区域变化的基础事件回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)
```

**描述：**

注销限制回调间隔的可见区域变化的基础事件回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 目标节点。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_ConvertPositionToWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)
```

**描述：**

将点的坐标从指定节点的坐标系转换至当前窗口的坐标系。节点的坐标系考虑节点本身的变换，例如，节点A的变换效果为向左平移100，会使得其坐标系中的点的坐标也向左平移100。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle currentNode | 指定节点。 |
| ArkUI_IntOffset localPosition | 点在指定节点坐标系中的坐标，单位：px。 |
| ArkUI_IntOffset* windowPosition | 指向接收转换后坐标（位于当前窗口坐标系中，单位：px）的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 节点未挂载到节点树上。 |

### OH_ArkUI_NativeModule_ConvertPositionFromWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)
```

**描述：**

将点的坐标从当前窗口的坐标系转换至目标节点的坐标系。节点的坐标系考虑节点本身的变换，例如，节点A的变换效果为向左平移100，会使得其坐标系中的点的坐标也向左平移100。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle targetNode | 目标节点。 |
| ArkUI_IntOffset windowPosition | 点在当前窗口坐标系中的坐标，单位：px。 |
| ArkUI_IntOffset* localPosition | 指向接收转换后坐标（位于目标节点坐标系中，单位：px）的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 \n          [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 节点未挂载到节点树上。 |

### OH_ArkUI_Swiper_FinishAnimation()

```c
int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)
```

**描述：**

停止指定的Swiper节点正在执行的翻页动画。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 指定的节点。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。 \n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_PostAsyncUITask()

```c
int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (*asyncUITask)(void* asyncUITaskData), void (*onFinish)(void* asyncUITaskData))
```

**描述：**

将asyncUITask函数提交至ArkUI框架提供的非UI线程中执行，asyncUITask函数执行完毕后，在UI线程调用onFinish函数。 适用于多线程创建UI组件的场景，开发者可使用此接口在非UI线程创建UI组件，随后在UI线程将创建完成的组件挂载至主树上。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle context | UI实例对象指针。 |
| void\* asyncUITaskData | 开发者自定义数据指针，作为asyncUITask和onFinish的入参。可以传入空指针。 |
| void (\*asyncUITask)(void\* asyncUITaskData) | 在非UI线程执行的函数。 |
| void (\*onFinish)(void\* asyncUITaskData) | asyncUITask执行完成后，在UI线程执行的函数。可以传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) context对象无效或asyncUITask为空指针。 |

### OH_ArkUI_PostUITask()

```c
int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**描述：**

将task函数提交至UI线程中执行。 适用于多线程创建UI组件的场景，当开发者在自建的线程中创建UI组件时，可以使用此接口将创建完成的组件挂载到UI线程的主树上。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle context | UI实例对象指针。 |
| void\* taskData | 开发者自定义数据指针，作为task的入参。可以传入空指针。 |
| void (\*task)(void\* taskData) | 在UI线程执行的函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) context对象无效或task为空指针。 |

### OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible()

```c
int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)
```

**描述：**

设置菜单栏的可见性。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle uiContext | ArkUI上下文句柄，指定的ArkUI容器上下文。 |
| bool visible | 菜单栏是否可见。true表示菜单栏可见，false表示菜单栏不可见。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。 \n          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 操作成功。 \n          [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 实例异常（uiContext为空指针、无法通过uiContext获取容器、uiContext不属于原子化服务）。 |

### OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**描述：**

Registers a callback for listening for component dimension and area changes.<br> This function can be called for a valid [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node at any time. The newly registered callback will replace the previously registered callback for this event and will take effect from the next frame. When the callback is no longer needed, call [OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent](capi-native-node-h.md#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) to unregister it. Otherwise, the callback will be automatically unregistered when the node is released.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_NodeHandle node | Pointer to [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). |
| float expectedUpdateInterval | Expected calculation interval, in milliseconds. |
| void\* userData | Pointer to custom data. |
| void (\*callback)(ArkUI_NodeEvent\* event) | Event callback. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Result code. \n          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful. \n          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. \n |

### OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node)
```

**描述：**

Unregisters the callback bound to the dimensions and area changes of a component.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Result code. \n          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful. \n          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. \n |

### OH_ArkUI_PostUITaskAndWait()

```c
int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**描述：**

将task函数提交至UI线程中执行，调用此接口的线程将阻塞，直至task函数执行完成。在UI线程调用此接口等同于同步调用task函数。 适用于多线程创建UI组件的场景，当开发者在多线程创建组件过程中需要调用仅支持UI线程的函数时，使用此接口返回UI线程调用函数，调用完成后继续多线程创建组件。 当UI线程负载较高时，调用此接口的非UI线程可能长时间阻塞，影响多线程创建UI组件的性能，不建议频繁使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ContextHandle context | UI实例对象指针。 |
| void\* taskData | 开发者自定义数据指针，作为task的入参。可以传入空指针。 |
| void (\*task)(void\* taskData) | 在UI线程执行的函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) context对象无效或task为空指针。 |

### OH_ArkUI_Swiper_StartFakeDrag()

```c
int32_t OH_ArkUI_Swiper_StartFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)
```

**描述：**

Start a fake drag of the Swiper node. Call OH_ArkUI_Swiper_FakeDragBy to simulate the drag motion. Call OH_ArkUI_Swiper_StopFakeDrag to complete the fake drag. A fake drag can be interrupted by a real drag. If you need to ignore touch events and other user input during a fake drag, use NODE_SWIPER_DISABLE_SWIPE.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| bool* isSuccessful | If the fake drag started successfully, return true. If the Swiper is not ready to start the fake drag, or a real or fake drag is already in progress, return false. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_FakeDragBy()

```c
int32_t OH_ArkUI_Swiper_FakeDragBy(ArkUI_NodeHandle node, float offset, bool* isConsumedOffset)
```

**描述：**

Fake drag by an offset of the Swiper node. The OH_ArkUI_Swiper_StartFakeDrag must be called first.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| float offset | The offset that needs to be scrolled. The unit is vp. |
| bool* isConsumedOffset | If not in a fake drag progress, or no offset is consumed, return false. If any offset is consumed, return true. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_StopFakeDrag()

```c
int32_t OH_ArkUI_Swiper_StopFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)
```

**描述：**

Stop a fake drag of the Swiper node.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| bool* isSuccessful | If the fake drag stopped successfully, return true. If the Swiper is not ready to stop the fake drag, or no fake drag is in progress, return false. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_IsFakeDragging()

```c
int32_t OH_ArkUI_Swiper_IsFakeDragging(ArkUI_NodeHandle node, bool* isFakeDragging)
```

**描述：**

Get the fake drag state of the Swiper node.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| bool* isFakeDragging | If a fake drag is in progress return true, otherwise return false |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_ShowPrevious()

```c
int32_t OH_ArkUI_Swiper_ShowPrevious(ArkUI_NodeHandle node)
```

**描述：**

Show the previous page of the Swiper node.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_Swiper_ShowNext()

```c
int32_t OH_ArkUI_Swiper_ShowNext(ArkUI_NodeHandle node)
```

**描述：**

Show the next page of the Swiper node.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext()

```c
int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)
```

**描述：**

获取指定实例的页面的根节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | UI实例对象指针。 |
| ArkUI_NodeHandle* rootNode | 目标根节点的句柄。如果上下文对应的页面没有根节点，则所指向的值将被设置为null。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 成功。      <br>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) CAPI初始化错误。      <br>[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 实例异常。      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo()

```c
ArkUI_GestureCollectInterceptInfo* OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo(ArkUI_NodeEvent* nodeEvent)
```

**描述：**

Obtains the <b>ArkUI_GestureCollectInterceptInfo</b> object from a specified <b>ArkUI_NodeEvent</b> object.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeEvent* nodeEvent | Pointer to the <b>ArkUI_NodeEvent</b> object. |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_GestureCollectInterceptInfo* | Returns the pointer to the <b>ArkUI_GestureCollectInterceptInfo</b> object.          It is valid only during callback and does not need to be released.          Returns <b>null</b> if the input parameter is invalid or the          information is not gesture collection interception information. |

### OH_ArkUI_NativeModule_SetChildMountPolicy()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_SetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy policy)
```

**描述：**

Set the subnode mounting policy of the target node.

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | the target node handle. |
| OH_ArkUI_NodeMountPolicy policy | the policy to set. Valid values correspond to [OH_ArkUI_NodeMountPolicy](capi-native-type-h.md#oh_arkui_nodemountpolicy). |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | Error code.      <ul><li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Success.      </li><li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) Function parameter exception.      </li><li>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if CAPI init error.</li></ul> |

### OH_ArkUI_NodeUtils_SetUiDvsyncSwitch()

```c
ArkUI_ErrorCode OH_ArkUI_NodeUtils_SetUiDvsyncSwitch(ArkUI_ContextHandle context, bool enable)
```

**描述：**

设置UI Dvsync开关。开启后系统会更及时地响应Vsync请求，更频繁执行渲染任务。通常在自渲染框架中动效开始时使能，结束后关闭，以确保动画效果更加流畅，同时避免频繁的Vsync影响其他业务。在非UI线程上调用此函数将导致应用退出。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | [入参] ArkUI_ContextHandle指针。 |
| bool enable | [入参] 是否启用Dvsync，取值为true时开启Dvsync，取值为false时关闭Dvsync。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 返回结果。  <ul><li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)成功。  </li><li>[RKUI_ERROR_CODE_CAPI_INIT_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)如果CAPI初始化错误。  </li><li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode)函数参数异常。</li></ul> |


