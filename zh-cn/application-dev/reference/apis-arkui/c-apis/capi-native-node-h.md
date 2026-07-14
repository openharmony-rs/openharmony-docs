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
| [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) | ArkUI_AttributeItem | Defines the general input parameter structure of the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) function. The propertysetting interfaces can utilize the member variables within it to store data of specific parameter types. |
| [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | ArkUI_NodeComponentEvent | Defines the parameter type of the component callback event. |
| [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) | ArkUI_StringAsyncEvent | Defines the string type parameter used by the component callback event. |
| [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) | ArkUI_TextChangeEvent | Defines a hybrid data structure for component events. |
| [ArkUI_NativeNodeAPI_1](capi-arkui-nativemodule-arkui-nativenodeapi-1.md) | ArkUI_NativeNodeAPI_1 | Declares a collection of native node APIs provided by ArkUI.The APIs related to the native node must be called in the main thread. |
| [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | OH_ArkUI_TextEditorChangeEvent | 定义TextEditor组件文本内容变化事件的结构体。 |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) | ArkUI_NodeEvent | Defines the common structure type of a component event. |
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
| [int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)](#oh_arkui_nodeevent_getnumbervalue) | - | Obtains the numeric-type parameter of a component event. |
| [int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)](#oh_arkui_nodeevent_getstringvalue) | - | Obtains the string-type parameter of a component event. The string data is valid only during an eventcallback. To use it outside an event callback, you are advised to copy the string data. |
| [int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)](#oh_arkui_nodeevent_setreturnnumbervalue) | - | Sets the return value for a component event. |
| [ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_gettouchtestinfo) | - | 获取组件事件中的触摸测试信息。 |
| [OH_ArkUI_TextEditorChangeEvent* OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettexteditoronwillchangeevent) | - | 获取组件事件中的TextEditor组件文本内容变化数据。 |
| [ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()](#oh_arkui_nodeadapter_create) | - | Creates a component adapter. |
| [void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_dispose) | - | Destroys a component adapter. |
| [int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)](#oh_arkui_nodeadapter_settotalnodecount) | - | Sets the total number of elements in the specified adapter. |
| [uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_gettotalnodecount) | - | Obtains the total number of elements in the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(
ArkUI_NodeAdapterHandle handle, void* userData, void (\*receiver)(ArkUI_NodeAdapterEvent* event))](#oh_arkui_nodeadapter_registereventreceiver) | - | Registers an event callback for the adapter. |
| [void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_unregistereventreceiver) | - | Deregisters an event callback for the adapter. |
| [int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_reloadallitems) | - | Instructs the specified adapter to reload all elements. |
| [int32_t OH_ArkUI_NodeAdapter_ReloadItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_reloaditem) | - | Instructs the specified adapter to reload certain elements. |
| [int32_t OH_ArkUI_NodeAdapter_RemoveItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_removeitem) | - | Instructs the specified adapter to remove certain elements. |
| [int32_t OH_ArkUI_NodeAdapter_InsertItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_insertitem) | - | Instructs the specified adapter to insert certain elements. |
| [int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)](#oh_arkui_nodeadapter_moveitem) | - | Instructs the specified adapter to move certain elements. |
| [int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)](#oh_arkui_nodeadapter_getallitems) | - | Obtains all elements stored in the specified adapter.This API returns the pointer to the array of the elements. You need to manually release the memory datato which the pointer points. |
| [void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getuserdata) | - | Obtains the custom data passed in during registration of the specified event. |
| [ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gettype) | - | Obtains the event type. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getremovednode) | - | Obtains the element to be removed for the event to be destroyed. |
| [uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getitemindex) | - | Obtains the index of the element to be operated for the specified adapter event. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gethostnode) | - | Obtains the scrollable container node that uses the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)](#oh_arkui_nodeadapterevent_setitem) | - | Sets the component to be added to the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)](#oh_arkui_nodeadapterevent_setnodeid) | - | Sets the component ID to be generated. |
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
| [int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)](#oh_arkui_nodecontent_registercallback) | - | register a callback function to a node content. |
| [ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_geteventtype) | - | Obtains the type of a node content event. |
| [ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_getnodecontenthandle) | - | Obtains the node content object that triggers a node content event. |
| [int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)](#oh_arkui_nodecontent_setuserdata) | - | Saves custom data on the specified node content. |
| [void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)](#oh_arkui_nodecontent_getuserdata) | - | Obtains the custom data saved on the specified node content. |
| [int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_addnode) | - | Add a node to a node content. |
| [int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_removenode) | - | remove a node from a node content. |
| [int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)](#oh_arkui_nodecontent_insertnode) | - | insert a node into a node content at a given position. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)](#oh_arkui_nodeutils_getlayoutsize) | - | Get the size of the component layout area.The layout area size does not include graphic variation attributes such as scaling. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)](#oh_arkui_nodeutils_getlayoutposition) | - | Obtain the position of the component layout area relative to the parent component.The relative position of the layout area does not include graphic variation attributes, such as translation. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getlayoutpositioninwindow) | - | Obtain the position of the component layout area relative to the window.The relative position of the layout area does not include graphic variation attributes, such as translation. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)](#oh_arkui_nodeutils_getlayoutpositioninscreen) | - | Obtain the position of the component layout area relative to the screen.The relative position of the layout area does not include graphic variation attributes, such as translation. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)](#oh_arkui_nodeutils_getlayoutpositioninglobaldisplay) | - | Obtains the offset of a component relative to the global display.The relative position does not count in transformation attributes, such as translate. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinwindow) | - | Obtain the position of the component in the window, including the properties of graphic translation changes. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinscreen) | - | Obtain the position of the component on the screen, including the attributes of graphic translation changes. |
| [void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)](#oh_arkui_nodeutils_addcustomproperty) | - | Add the custom property of the component. This interface only works on the main thread. |
| [void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)](#oh_arkui_nodeutils_removecustomproperty) | - | Remove the custom property of the component. |
| [int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)](#oh_arkui_nodeutils_getcustomproperty) | - | Get the value of the custom property of the component. |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getparentinpagetree) | - | Get the parent node to obtain the component nodes created by ArkTs. |
| [int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)](#oh_arkui_nodeutils_getactivechildreninfo) | - | Retrieve all active child nodes of a node. Span will not be counted in the children. |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getcurrentpagerootnode) | - | Retrieve the root node of the current page. |
| [bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_iscreatedbyndk) | - | Retrieve whether the component is labeled by C-API. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getnodetype) | - | Get the type of node. |
| [int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)](#oh_arkui_nodeutils_getwindowinfo) | - | Get info of the window to which the node belongs. |
| [int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getfirstchildindexwithoutexpand) | - | Obtains the index of the current FrameNode's first child node which is on the tree. |
| [int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getlastchildindexwithoutexpand) | - | Obtains the index of the current FrameNode's last child node which is on the tree. |
| [int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)](#oh_arkui_nodeutils_getchildwithexpandmode) | - | Obtains a subnode by position with the expand mode. |
| [int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_list_closeallswipeactions) | - | Collapse the ListItem in its expanded state. |
| [ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)](#oh_arkui_getcontextbynode) | - | Obtain the UIContext pointer to the page where the node is located. |
| [int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))](#oh_arkui_registersystemcolormodechangeevent) | - | The event called when the system color mode changes.Only one system color change callback can be registered for the same component. |
| [void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemcolormodechangeevent) | - | Unregister the event callback when the system color mode changes. |
| [int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))](#oh_arkui_registersystemfontstylechangeevent) | - | The event called when the system font style changes.Only one system font change callback can be registered for the same component. |
| [void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemfontstylechangeevent) | - | Unregister the event callback when the system font style changes. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontsizescale) | - | Retrieve the font size value for system font change events. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontweightscale) | - | Retrieve the font thickness values for system font change events. |
| [int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getattachednodehandlebyid) | - | Get the node handle by id. |
| [int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)](#oh_arkui_nodeutils_moveto) | - | Move the node handle to target parent node as child. |
| [int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_invalidateattributes) | - | Triggers node updates in the current frame.When node attributes are modified after the current frame's build phase,the node updates will be deferred to the nextframe. This function forces immediate node updates within the current frame toensure rendering effects are applied synchronously. |
| [int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_setcrosslanguageoption) | - | Set the cross-language option of the target node handle. |
| [int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_getcrosslanguageoption) | - | Get the cross-language option of the target node handle. |
| [int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onLayoutCompleted)(void* userData))](#oh_arkui_registerlayoutcallbackonnodehandle) | - | Registers a callback for node when layout is completed. |
| [int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onDrawCompleted)(void* userData))](#oh_arkui_registerdrawcallbackonnodehandle) | - | Registers a callback for node when draw is completed. |
| [int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterlayoutcallbackonnodehandle) | - | Unregisters the layout completed callback for node. |
| [int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterdrawcallbackonnodehandle) | - | Unregisters the draw completed callback for node. |
| [int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelmap)](#oh_arkui_getnodesnapshot) | - | Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered,the snapshot operation will fail. When the <b>Pixelmap</b> object created is no longer in use, it should be releasedby calling {@link OH_PixelmapNative_Release}. |
| [int32_t OH_ArkUI_GetNodeSnapshotSizeLimitation(int32_t* maxWidth, int32_t* maxHeight)](#oh_arkui_getnodesnapshotsizelimitation) | - | Query the size limitation of the component snapshot. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getpositiontoparent) | - | Obtains the offset of a specific node relative to its parent node. |
| [ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)](#oh_arkui_addsupporteduistates) | - | 设置组件支持的{@link 多态样式}状态。为了更高效地处理，需传入所关注的状态值及对应的状态处理函数，当关注的状态发生时，处理函数会被执行。可在回调中根据当前状态调整UI样式。当在同一个节点上多次调用该方法时，将以最后一次传入的状态及处理函数为准。有些类型的组件节点，系统内部已有对某些状态的默认处理。例如，Button组件默认具备对PRESSED状态的样式变化，当在此类组件上使用此方法自定义状态处理时，会先应用系统默认样式变化，再执行自定义的样式处理，最终效果为两者叠加。可以通过指定excludeInner为true来禁用系统内部的默认样式效果，但这通常取决于系统内部实现规范是否允许。当调用该函数时，传入的statesChangeHandler函数会立即执行一次，且无需特意注册对NORMAL状态的监听，只要注册了非NORMAL状态，当状态从任意状态变化回NORMAL时，系统都会进行回调，以便应用进行样式复原。 |
| [ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)](#oh_arkui_removesupporteduistates) | - | 删除注册的状态处理。当通过OH_ArkUI_AddSupportedUIStates注册的状态都被删除时，所注册的stateChangeHandler也不会再被执行。 |
| [int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(\*callback)(void* userData))](#oh_arkui_runtaskinscope) | - | Run a custom function inside the UIContext scope. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getnodehandlebyuniqueid) | - | Get the node handle by uniqueId. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)](#oh_arkui_nodeutils_getnodeuniqueid) | - | Get the uniqueId of the target node handle. |
| [int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)](#oh_arkui_nativemodule_isinrenderstate) | - | Returns true if the node is in the render state. A node is considered to be in the render state if itscorresponding RenderNode is on the render tree. |
| [int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_adoptchild) | - | The current node adopts the target child node. The node being adopted must not have an existing parent node.This operation does not actually append it as a child, but only allows it to receive life-cyclecallbacks as if it were a child. |
| [int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_removeadoptedchild) | - | Remove the target adopted child node. |
| [int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (\*colorInvertFunc)(uint32_t color))](#oh_arkui_setforcedarkconfig) | - | Sets the inverse color algorithm for components and instances. |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonevent) | - | 注册目标节点的基础事件回调。当前支持的事件类型如下: 参考[ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype)中的NODE_ON_CLICK_EVENT、NODE_TOUCH_EVENT、NODE_EVENT_ON_APPEAR、NODE_EVENT_ON_DISAPPEAR、NODE_ON_KEY_EVENT、NODE_ON_FOCUS、NODE_ON_BLUR、NODE_ON_HOVER、NODE_ON_MOUSE、NODE_ON_SIZE_CHANGE。 |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)](#oh_arkui_nativemodule_unregistercommonevent) | - | 注销目标节点的基础事件回调。当前支持的事件类型请参考[OH_ArkUI_NativeModule_RegisterCommonEvent](capi-native-node-h.md#oh_arkui_nativemodule_registercommonevent)。 |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonvisibleareaapproximatechangeevent) | - | 注册限制回调间隔的可见区域变化的基础事件回调。 |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonvisibleareaapproximatechangeevent) | - | 注销限制回调间隔的可见区域变化的基础事件回调。 |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)](#oh_arkui_nativemodule_convertpositiontowindow) | - | Converts a point's coordinates from the target node's coordinate system to the current window's coordinate system, with consideration of the node’s transformation. |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)](#oh_arkui_nativemodule_convertpositionfromwindow) | - | Converts a point's coordinates from the current window's coordinate system to the target node's coordinate system, with consideration of the node’s transformation. |
| [int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)](#oh_arkui_swiper_finishanimation) | - | Stop the animation being executed by the Swiper node. |
| [int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (\*asyncUITask)(void* asyncUITaskData), void (\*onFinish)(void* asyncUITaskData))](#oh_arkui_postasyncuitask) | - | Post UI task to background threads. |
| [int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitask) | - | Post UI task to UI thread. |
| [int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)](#oh_arkui_nativemodule_atomicservicemenubarsetvisible) | - | set the visiblity of the menubar. |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonareaapproximatechangeevent) | - | Registers a callback for listening for component dimension and area changes.This function can be called for a valid [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node at any time. <br> The newly registered callback will replace the previously registered callback for this event and will take effect from the next frame. <br> When the callback is no longer needed, call [OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent](capi-native-node-h.md#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) to unregister it. <br> Otherwise, the callback will be automatically unregistered when the node is released. |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) | - | Unregisters the callback bound to the dimensions and area changes of a component. |
| [int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitaskandwait) | - | Post UI task to UI thread and wait until UI task finished. |
| [int32_t OH_ArkUI_Swiper_StartFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_startfakedrag) | - | Start a fake drag of the Swiper node.Call OH_ArkUI_Swiper_FakeDragBy to simulate the drag motion. Call OH_ArkUI_Swiper_StopFakeDrag to complete thefake drag. A fake drag can be interrupted by a real drag. If you need to ignore touch events and other user inputduring a fake drag, use NODE_SWIPER_DISABLE_SWIPE. |
| [int32_t OH_ArkUI_Swiper_FakeDragBy(ArkUI_NodeHandle node, float offset, bool* isConsumedOffset)](#oh_arkui_swiper_fakedragby) | - | Fake drag by an offset of the Swiper node.The OH_ArkUI_Swiper_StartFakeDrag must be called first. |
| [int32_t OH_ArkUI_Swiper_StopFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_stopfakedrag) | - | Stop a fake drag of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_IsFakeDragging(ArkUI_NodeHandle node, bool* isFakeDragging)](#oh_arkui_swiper_isfakedragging) | - | Get the fake drag state of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_ShowPrevious(ArkUI_NodeHandle node)](#oh_arkui_swiper_showprevious) | - | Show the previous page of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_ShowNext(ArkUI_NodeHandle node)](#oh_arkui_swiper_shownext) | - | Show the next page of the Swiper node. |
| [int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)](#oh_arkui_nativemodule_getpagerootnodehandlebycontext) | - | Get the root node handle of the corresponding page of the Context. |
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
| ARKUI_NODE_XCOMPONENT = 12 | XComponent. |
| ARKUI_NODE_DATE_PICKER = 13 | Date picker. |
| ARKUI_NODE_TIME_PICKER = 14 | Time picker. |
| ARKUI_NODE_TEXT_PICKER = 15 | Text picker. |
| ARKUI_NODE_CALENDAR_PICKER = 16 | Calendar picker. |
| ARKUI_NODE_SLIDER = 17 | Slider. |
| ARKUI_NODE_RADIO = 18 | Radio |
| ARKUI_NODE_IMAGE_ANIMATOR = 19 | Image animator. |
| ARKUI_NODE_XCOMPONENT_TEXTURE | XComponent of type TEXTURE.@since 18 |
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

### ArkUI_NodeAttributeType

```c
enum ArkUI_NodeAttributeType
```

**描述**

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_WIDTH = 0 | Defines the width attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width, in vp.<br> |
| NODE_HEIGHT | Defines the height attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: height, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: height, in vp.<br> |
| NODE_BACKGROUND_COLOR | 背景色属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].u32</b>：背景色数值，0xargb格式，形如 `0xFFFF0000` 表示红色。<br>*返回：<br><b>.value[0].u32</b>：背景色数值，0xargb格式，形如 `0xFFFF0000` 表示红色。 |
| NODE_BACKGROUND_IMAGE | 背景色图片属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.string</b>：图片地址。API version 22及之前版本，支持网络图片资源地址、本地图片资源地址、Base64和{@link PixelMap}资源，不支持{@link svg}图片、gif和webp等类型的动图。从API version 23开始，新增支持webp和gif类型的动图，显示动图第一帧，不支持其他类型的动图。<br><b>.value[0]?.i32</b>：可选值，repeat参数，参数类型[ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat)，默认值为ARKUI_IMAGE_REPEAT_NONE。<br><b>.object</b>：PixelMap图片数据，参数类型为{@link ArkUI_DrawableDescriptor}。`.object`参数和`.string`参数二选一，不可同时设置。<br>*返回：<br><b>.string</b>：图片地址。API version 22及之前版本，支持网络图片资源地址、本地图片资源地址、Base64和PixelMap资源，不支持svg图片、gif和webp等类型的动图。从APIversion 23开始，新增支持webp和gif类型的动图，显示动图第一帧，不支持其他类型的动图。<br><b>.value[0].i32</b>：repeat参数，参数类型[ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat)。<br><b>.object</b>：PixelMap图片数据，参数类型为{@link ArkUI_DrawableDescriptor}。 |
| NODE_PADDING | Defines the padding attribute, which can be set, reset, and obtained as required through APIs.There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:<br> 1: Specify the same padding for the four directions. <br> .value[0].f32: padding, in vp.<br> 2: Specify different paddings for different directions. <br> .value[0].f32: top padding, in vp.<br> .value[1].f32: right padding, in vp.<br> .value[2].f32: bottom padding, in vp.<br> .value[3].f32: left padding, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: top padding, in vp.<br> .value[1].f32: right padding, in vp.<br> .value[2].f32: bottom padding, in vp.<br> .value[3].f32: left padding, in vp.<br> |
| NODE_ID | Defines the component ID attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component ID.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component ID.<br> |
| NODE_ENABLED | 设置组件是否可交互，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：false表示不可交互，true表示可交互。<br>*返回：<br><b>.value[0].i32</b>：0表示不可交互，1表示可交互。 |
| NODE_MARGIN | Defines the margin attribute, which can be set, reset, and obtained as required through APIs.There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:<br> 1: Specify the same margin for the four directions. <br> .value[0].f32: margin, in vp.<br> 2: Specify different margins for different directions. <br> .value[0].f32: top margin, in vp.<br> .value[1].f32: right margin, in vp.<br> .value[2].f32: bottom margin, in vp.<br> .value[3].f32: left margin, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: top margin, in vp.<br> .value[1].f32: right margin, in vp.<br> .value[2].f32: bottom margin, in vp.<br> .value[3].f32: left margin, in vp.<br> |
| NODE_TRANSLATE | Defines the translate attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: distance to translate along the x-axis, in vp. The default value is <b>0</b>.<br> .value[1].f32: distance to translate along the y-axis, in vp. The default value is <b>0</b>.<br> .value[2].f32: distance to translate along the z-axis, in vp. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: distance to translate along the x-axis, in vp.<br> .value[1].f32: distance to translate along the y-axis, in vp.<br> .value[2].f32: distance to translate along the z-axis, in vp. <br> |
| NODE_SCALE | Defines the scale attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: scale factor along the x-axis. The default value is <b>1</b>.<br> .value[1].f32: scale factor along the y-axis. The default value is <b>1</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: scale factor along the x-axis.<br> .value[1].f32: scale factor along the y-axis. <br> |
| NODE_ROTATE | Defines the rotate attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: X coordinate of the rotation axis vector. The default value is <b>0</b>.<br> .value[1].f32: Y coordinate of the rotation axis vector. The default value is <b>0</b>.<br> .value[2].f32: Z coordinate of the rotation axis vector. The default value is <b>0</b>.<br> .value[3].f32: rotation angle. The default value is <b>0</b>.<br> .value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp.The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate of the rotation axis vector.<br> .value[1].f32: Y coordinate of the rotation axis vector.<br> .value[2].f32: Z coordinate of the rotation axis vector.<br> .value[3].f32: rotation angle.<br> .value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp. <br> |
| NODE_BRIGHTNESS | Sets the brightness attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: brightness value. The default value is <b>1.0</b>, and the recommended value range is [0, 2]. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: brightness value. <br> |
| NODE_SATURATION | Sets the saturation attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].f32: saturation value. The default value is <b>1.0</b>, and the recommended value range is [0, 50). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].f32: saturation value. <br> |
| NODE_BLUR | Sets the blur attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].f32: blur radius. A larger value indicates a higher blur degree. If the value is <b>0</b>,the component is not blurred. The unit is vp. The default value is <b>0.0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: blur radius. The larger the fuzzy radius, the more blurred the image. If the value is <b>0</b>,the image is not blurred. The unit is vp. <br> |
| NODE_LINEAR_GRADIENT | Sets the gradient attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: start angle of the linear gradient. This attribute takes effect only when[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection) is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>.A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>. <br> .value[1].i32: direction of the linear gradient. When it is set, the <b>angle</b> attribute does not take effect.The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection): <br> .value[2].i32: whether the colors are repeated. The default value is <b>false</b>. <br> .object: array of color stops, each of which consists of a color and its stop position.Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].f32: start angle of the linear gradient. <br> .value[1].i32: direction of the linear gradient. It does not take effect when <b>angle</b> is set. <br> .value[2].i32: whether the colors are repeated. <br> .object: array of color stops, each of which consists of a color and its stop position.Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> |
| NODE_ALIGNMENT | Sets the alignment attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment).The default value is <b>ARKUI_ALIGNMENT_CENTER</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). <br> |
| NODE_OPACITY | Defines the opacity attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: opacity value. The value ranges from 0 to 1. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: opacity value. The value ranges from 0 to 1. <br> |
| NODE_BORDER_WIDTH | Defines the border width attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].f32: width of the four borders. <br> 2: .value[0].f32: width of the top border. <br> .value[1].f32: width of the right border. <br> .value[2].f32: width of the bottom border. <br> .value[3].f32: width of the left border. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width of the top border. <br> .value[1].f32: width of the right border. <br> .value[2].f32: width of the bottom border. <br> .value[3].f32: width of the left border. <br> |
| NODE_BORDER_RADIUS | Defines the border corner radius attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].f32: radius of the four corners. <br> 2: .value[0].f32: radius of the upper left corner. <br> .value[1].f32: radius of the upper right corner. <br> .value[2].f32: radius of the lower left corner. <br> .value[3].f32: radius of the lower right corner. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: radius of the upper left corner. <br> .value[1].f32: radius of the upper right corner. <br> .value[2].f32: radius of the lower left corner. <br> .value[3].f32: radius of the lower right corner. <br> |
| NODE_BORDER_COLOR | Defines the border color attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].u32: color of the four borders, in 0xARGB format, for example, <b>0xFFFF11FF</b>. <br> 2: .value[0].u32: color of the top border, in 0xARGB format, for example, <b>0xFFFF11FF</b>. <br> .value[1].u32: color of the right border, in 0xARGB format, for example, <b>0xFFFF11FF</b>. <br> .value[2].u32: color of the lower border, in 0xARGB format, for example, <b>0xFFFF11FF</b>. <br> .value[3].u32: color of the left border, in 0xARGB format, for example, <b>0xFFFF11FF</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the top border, in 0xARGB format, for example, <b>0xFFFF11FF</b>. <br> .value[1].u32: color of the right border, in 0xARGB format, for example, <b>0xFFFF11FF</b>. <br> .value[2].u32: color of the lower border, in 0xARGB format, for example, <b>0xFFFF11FF</b>. <br> .value[3].u32: color of the left border, in 0xARGB format, for example, <b>0xFFFF11FF</b>. <br> |
| NODE_BORDER_STYLE | Defines the border line style attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].i32: line style of the four borders. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle).The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>. <br> 2: .value[0].i32: line style of the top border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle).The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>. <br> .value[1].i32: line style of the right border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle).The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>. <br> .value[2].i32: line style of the bottom border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle).The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>. <br> .value[3].i32: line style of the left border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle).The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: line style of the top border. <br> .value[1].i32: line style of the right border. <br> .value[2].i32: line style of the bottom border. <br> .value[3].i32: line style of the left border. <br> |
| NODE_Z_INDEX | 组件的堆叠顺序属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：堆叠顺序数值。<br>*返回：<br><b>.value[0].i32</b>：堆叠顺序数值。 |
| NODE_VISIBILITY | 组件是否可见属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：控制当前组件显示或隐藏，参数类型[ArkUI_Visibility](capi-common-attributes-h.md#arkui_visibility)，默认值为ARKUI_VISIBILITY_VISIBLE。<br>*返回：<br><b>.value[0].i32</b>：控制当前组件显示或隐藏，参数类型[ArkUI_Visibility](capi-common-attributes-h.md#arkui_visibility)，默认值为ARKUI_VISIBILITY_VISIBLE。 |
| NODE_CLIP | Defines the clipping and masking attribute, which can be set, reset, and obtained as required throughAPIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to clip the component based on the parent container bounds.The value <b>1</b> means to clip the component, and <b>0</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to clip the component based on the parent container bounds.The value <b>1</b> means to clip the component, and <b>0</b> means the opposite. <br> |
| NODE_CLIP_SHAPE | Defines the clipping region on the component.This attribute can be set and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute,which supports four types of shapes:<br> 1. Rectangle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_RECTANGLE</b> for the rectangle shape. <br> .value[1].f32: width of the rectangle.<br> .value[2].f32: height of rectangle.<br> .value[3].f32: width of the rounded corner of the rectangle.<br> .value[4].f32: height of the rounded corner of the rectangle.<br> .value[5]?.f32: radius of the top left corner of the rectangular shape.<br> .value[6]?.f32: radius of the bottom left corner of the rectangular shape.<br> .value[7]?.f32: radius of the top right corner of the rectangular shape.<br> .value[8]?.f32: radius of the bottom right corner of the rectangular shape.<br> ?.object: clipOption of the rectangle. The parameter type is {@link ArkUI_RenderNodeClipOption} type.It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is rectangle, and .size must be equal to 1.2. Circle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_CIRCLE</b> for the circle shape.<br> .value[1].f32: width of the circle.<br> .value[2].f32: height of the circle.<br> ?.object: clipOption of the circle. The parameter type is {@link ArkUI_RenderNodeClipOption} type.It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is circle, and .size must be equal to 1.3.Ellipse:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[1].f32: width of the ellipse.<br> .value[2].f32: height of the ellipse.<br> ?.object: clipOption of the ellipse. The parameter type is {@link ArkUI_RenderNodeClipOption} type.It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is ellipse, and .size must be equal to 1.4. Path:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_PATH</b> for the path shape.<br> .value[1].f32: width of the path.<br> .value[2].f32: height of the path.<br> .string: command for drawing the path.<br> ?.object: clipOption of the path. The parameter type is {@link ArkUI_RenderNodeClipOption} type.It takes effect when only the .object parameter is passed, ArkUI_RenderNodeClipOption type is path, and .size must be equal to 1.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md), which supports four types of shapes: <br> 1. Rectangle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_RECTANGLE</b> for the rectangle shape. <br> .value[1].f32: width of the rectangle.<br> .value[2].f32: height of rectangle.<br> .value[3].f32: width of the rounded corner of the rectangle.<br> .value[4].f32: height of the rounded corner of the rectangle.<br> .value[5].f32: radius of the top left corner of the rectangular shape; <br> .value[6].f32: radius of the bottom left corner of the rectangular shape; <br> .value[7].f32: radius of the top right corner of the rectangular shape; <br> .value[8].f32: radius of the bottom right corner of the rectangular shape; <br> .value[9]?.f32: horizontal coordinate offset of the rectangle. <br> .value[10]?.f32: vertical coordinate offset of the rectangle. <br> 2. Circle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_CIRCLE</b> for the circle shape.<br> .value[1].f32: width of the circle.<br> .value[2].f32: height of the circle.<br> .value[3]?.f32: horizontal coordinate offset of the circle.<br> .value[4]?.f32: vertical coordinate offset of the circle.<br> 3.Ellipse:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[1].f32: width of the ellipse.<br> .value[2].f32: height of the ellipse.<br> .value[3]?.f32: horizontal coordinate offset of the ellipse.<br> .value[4]?.f32: vertical coordinate offset of the ellipse.<br> 4. Path:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype).The value is <b>ARKUI_CLIP_TYPE_PATH</b> for the path shape.<br> .value[1].f32: width of the path.<br> .value[2].f32: height of the path.<br> .string: command for drawing the path.<br> |
| NODE_TRANSFORM | Defines the transform attribute, which can be used to translate, rotate, and scale images.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0...15].f32: 16 floating-point numbers. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0...15].f32: 16 floating-point numbers. <br> |
| NODE_HIT_TEST_BEHAVIOR | 触摸测试类型，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：控制当前组件的触摸测试类型，参数类型[ArkUI_HitTestMode](capi-common-attributes-h.md#arkui_hittestmode)，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。<br>*返回：<br><b>.value[0].i32</b>：控制当前组件的触摸测试类型，参数类型[ArkUI_HitTestMode](capi-common-attributes-h.md#arkui_hittestmode)，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。 |
| NODE_POSITION | Defines the offset attribute, which specifies the offset of the component's upper left corner relativeto the parent container's. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: X coordinate. <br> .value[1].f32: Y coordinate. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate. <br> .value[1].f32: Y coordinate. <br> |
| NODE_SHADOW | Defines the shadow attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: shadow effect. The parameter type is [ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: shadow effect. The parameter type is [ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle). <br> |
| NODE_CUSTOM_SHADOW | Defines the custom shadow effect. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: blur radius of the shadow, in vp.<br> .value[1]?.i32: whether to enable the coloring strategy. The value <b>1</b> means to enable the coloringstrategy, and <b>0</b> (default value) means the opposite.<br> .value[2]?.f32: offset of the shadow along the x-axis, in px.<br> .value[3]?.f32: offset of the shadow along the y-axis, in px.<br> .value[4]?.i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is <b>ARKUI_SHADOW_TYPE_COLOR</b>.<br> .value[5]?.u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> .value[6]?.u32: whether to fill the shadow. The value <b>1</b> means to fill the shadow, and <b>0</b>means the opposite.<br>     <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: blur radius of the shadow, in vp.<br> .value[1].i32: whether to enable the coloring strategy. <br> .value[2].f32: offset of the shadow along the x-axis, in px.<br> .value[3].f32: offset of the shadow along the y-axis, in px.<br> .value[4].i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is <b>ARKUI_SHADOW_TYPE_COLOR</b>.<br> .value[5].u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> .value[6].u32: whether to fill the shadow. The value <b>1</b> means to fill the shadow, and <b>0</b>means the opposite.<br> |
| NODE_BACKGROUND_IMAGE_SIZE | 背景图片的宽高属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].f32</b>：图片的宽度值，取值范围`[0,+∞)`，单位为vp。<br><b>.value[1].f32</b>：图片的高度值，取值范围`[0,+∞)`，单位为vp。<br>*返回：<br><b>.value[0].f32</b>：图片的宽度值，单位为vp。<br><b>.value[1].f32</b>：图片的高度值，单位为vp。 |
| NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE | 背景图片的宽高样式属性，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：背景图片的宽高样式，取[ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize)枚举值。<br>*返回：<br><b>.value[0].i32</b>：背景图片的宽高样式，取[ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize)枚举值。 |
| NODE_BACKGROUND_BLUR_STYLE | Defines the background blur attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: blue type. The value is an enum of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle). <br> .value[1]?.i32: color mode. The value is an enum of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode). <br> .value[2]?.i32: adaptive color mode. The value is an enum of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor). <br> .value[3]?.f32: blur degree. The value range is [0.0, 1.0]. <br> .value[4]?.f32: start boundary of grayscale blur. <br> .value[5]?.f32: end boundary of grayscale blur. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: blue type. The value is an enum of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle). <br> .value[1].i32: color mode. The value is an enum of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode). <br> .value[2].i32: adaptive color mode. The value is an enum of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor). <br> .value[3].f32: blur degree. The value range is [0.0, 1.0]. <br> .value[4].f32: start boundary of grayscale blur. <br> .value[5].f32: end boundary of grayscale blur. <br> |
| NODE_TRANSFORM_CENTER | Defines the transform center attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: X coordinate of the center point, in vp.<br> .value[1]?.f32: Y coordinate of the center point, in vp.<br> .value[2]?.f32: Z coordinate of the center point, in vp.<br> .value[3]?.f32 : X coordinate of the center point, expressed in a number that represents a percentage.For example, 0.2 indicates 20%. This attribute overwrites value[0].f32. The default value is <b>0.5f</b>. <br> .value[4]?.f32 : Y coordinate of the center point, expressed in a number that represents a percentage.For example, 0.2 indicates 20%. This attribute overwrites value[1].f32. The default value is <b>0.5f</b>. <br> .value[5]?.f32 : Z coordinate of the center point, expressed in a number that represents a percentage.For example, 0.2 indicates 20%. This attribute overwrites value[2].f32. The default value is <b>0.0f</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate of the center point, in vp.<br> .value[1].f32: Y coordinate of the center point, in vp.<br> .value[2].f32: Z coordinate of the center point, in vp.<br> Note: If the coordinate is expressed in a number that represents a percentage, the attribute obtaining APIreturns the calculated value in vp. |
| NODE_OPACITY_TRANSITION | Defines the transition opacity attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: opacity values of the start and end points.<br> .value[1].i32: animation duration, in milliseconds.<br> .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3]?.i32: animation delay duration, in milliseconds.<br> .value[4]?.i32: number of times that the animation is played.<br> .value[5]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[6]?.f32: animation playback speed.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: opacity values of the start and end points.<br> .value[1].i32: animation duration, in milliseconds.<br> .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3].i32: animation delay duration, in milliseconds. <br> .value[4].i32: number of times that the animation is played. <br> .value[5].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[6].f32: animation playback speed. <br> |
| NODE_ROTATE_TRANSITION | Defines the transition rotation attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: X-component of the rotation vector. <br> .value[1].f32: Y-component of the rotation vector. <br> .value[2].f32: Z-component of the rotation vector <br> .value[3].f32: angle. <br> .value[4].f32: line of sight. The default value is <b>0.0f</b>. <br> .value[5].i32: animation duration, in milliseconds. <br> .value[6].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> .value[7]?.i32: animation delay duration, in milliseconds. <br> .value[8]?.i32: number of times that the animation is played. <br> .value[9]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[10]?.f32: animation playback speed. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X-component of the rotation vector. <br> .value[1].f32: Y-component of the rotation vector. <br> .value[2].f32: Z-component of the rotation vector <br> .value[3].f32: angle. <br> .value[4].f32: line of sight. <br> .value[5].i32: animation duration, in milliseconds. <br> .value[6].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> .value[7].i32: animation delay duration, in milliseconds. <br> .value[8].i32: number of times that the animation is played. <br> .value[9].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[10].f32: animation playback speed. <br> |
| NODE_SCALE_TRANSITION | Defines the transition scaling attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: scale factor along the x-axis. <br> .value[1].f32: scale factor along the y-axis. <br> .value[2].f32: scale factor along the z-axis. <br> .value[3].i32: animation duration, in milliseconds. <br> .value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> .value[5]?.i32: animation delay duration, in milliseconds. <br> .value[6]?.i32: number of times that the animation is played. <br> .value[7]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[8]?.f32: animation playback speed. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: scale factor along the x-axis. <br> .value[1].f32: scale factor along the y-axis. <br> .value[2].f32: scale factor along the z-axis. <br> .value[3].i32: animation duration, in milliseconds. <br> .value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> .value[5].i32: animation delay duration, in milliseconds. <br> .value[6].i32: number of times that the animation is played. <br> .value[7].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[8].f32: animation playback speed. <br> |
| NODE_TRANSLATE_TRANSITION | Defines the transition translation attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].f32: translation distance along the x-axis, in vp.<br> value[1].f32: translation distance along the y-axis, in vp.<br> value[2].f32: translation distance along the z-axis, in vp.<br> value[3].i32: animation duration, in milliseconds. <br> value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> value[5]?.i32: animation delay duration, in milliseconds. <br> value[6]?.i32: number of times that the animation is played. <br> value[7]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> value[8]?.f32: animation playback speed. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: translation distance along the x-axis, in vp.<br> value[1].f32: translation distance along the y-axis, in vp.<br> value[2].f32: translation distance along the z-axis, in vp.<br> value[3].i32: animation duration, in milliseconds. <br> value[4].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). <br> value[5].i32: animation delay duration, in milliseconds. <br> value[6].i32: number of times that the animation is played. <br> value[7].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> value[8].f32: animation playback speed. <br> |
| NODE_MOVE_TRANSITION | Defines the slide-in and slide-out of the component from the screen edge during transition.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge). <br> .value[1].i32: animation duration, in milliseconds.<br> .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3]?.i32: animation delay duration, in milliseconds.<br> .value[4]?.i32: number of times that the animation is played.<br> .value[5]?.i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[6]?.f32: animation playback speed.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge). <br> .value[1].i32: animation duration, in milliseconds.<br> .value[2].i32: animation curve type. The value is an enum of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3].i32: animation delay duration, in milliseconds. <br> .value[4].i32: number of times that the animation is played. <br> .value[5].i32: animation playback mode. The value is an enum of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode). <br> .value[6].f32: animation playback speed. <br> |
| NODE_FOCUSABLE | 获焦属性，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：参数类型为1表示可获焦，为0表示不可获焦。默认为不可获焦。<br>*返回：<br><b>.value[0].i32</b>：参数类型为1表示可获焦，为0表示不可获焦。 |
| NODE_DEFAULT_FOCUS | 默认焦点属性，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：参数值为1表示是默认焦点，为0表示不是默认焦点。<br>*返回：<br><b>.value[0].i32</b>：参数值为1表示是默认焦点，为0表示不是默认焦点。 |
| NODE_RESPONSE_REGION | 触摸热区属性，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*说明：<br>设置时data数据大小无数量限制，均可以设置成功，但仅支持获取到前20个。<br>*参数：<br><b>.data[0].f32</b>：触摸点相对于组件左上角的x轴坐标，单位为vp。<br><b>.data[1].f32</b>：触摸点相对于组件左上角的y轴坐标，单位为vp。<br><b>.data[2].f32</b>：触摸热区的宽度，单位为百分比。<br><b>.data[3].f32</b>：触摸热区的高度，单位为百分比。<br><b>.data[4...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。<br>*返回：<br><b>.data[0].f32</b>：触摸点相对于组件左上角的x轴坐标，单位为vp。<br><b>.data[1].f32</b>：触摸点相对于组件左上角的y轴坐标，单位为vp。<br><b>.data[2].f32</b>：触摸热区的宽度，单位为百分比。<br><b>.data[3].f32</b>：触摸热区的高度，单位为百分比。<br><b>.data[4...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。 |
| NODE_OVERLAY | 定义遮罩属性，支持属性设置，属性重置和属性获取。开发者可以通过如下.string或.object设置浮层内容，.string有更高的优先级。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.string</b>：遮罩文本。<br><b>.value[0]?.i32</b>：可选值，浮层相对于组件的位置，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_TOP_START。<br><b>.value[1]?.f32</b>：可选值，浮层基于自身左上角的偏移量X，单位为vp，默认值为0vp。<br><b>.value[2]?.f32</b>：可选值，浮层基于自身左上角的偏移量Y，单位为vp，默认值为0vp。<br><b>.value[3]?.i32</b>：可选值，浮层的布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_LTR。<br>在大部分场景下，这个参数都应该被设置成Auto，这个模式允许系统自动处理布局方向，如果在某些场景下需要保持特定的方向，设置这个属性为LTR（Left-to-Right）或者RTL（Right-to-Left）。从API version 21开始支持。<br><b>.object</b>：用于overlay的节点树，参数类型为[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)，默认值为nullptr。从API version 21开始支持。<br>*返回：<br><b>.string</b>：遮罩文本。<br><b>.value[0].i32</b>：浮层相对于组件的位置，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_TOP_START。<br><b>.value[1].f32</b>：浮层基于自身左上角的偏移量X，单位为vp。<br><b>.value[2].f32</b>：浮层基于自身左上角的偏移量Y，单位为vp。<br><b>.value[3].i32</b>：浮层的布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_LTR。从API version 21开始支持。<br><b>.object</b>：用于overlay的节点树，参数类型为[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。从API version 21开始支持。 |
| NODE_SWEEP_GRADIENT | Defines the sweep gradient effect.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: X coordinate of the sweep gradient center relative to the upper left corner of the component.<br> .value[1]?.f32: Y coordinate of the sweep gradient center relative to the upper left corner of the component.<br> .value[2]?.f32: start point of the sweep gradient. The default value is <b>0</b>. <br> .value[3]?.f32: end point of the sweep gradient. The default value is <b>0</b>. <br> .value[4]?.f32: rotation angle of the sweep gradient. The default value is <b>0</b>. <br> .value[5]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,and <b>0</b> means the opposite.<br> .object: array of color stops, each of which consists of a color and its stop position. Invalid colors areautomatically skipped.<br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate of the sweep gradient center relative to the upper left corner of the component. <br> .value[1].f32: Y coordinate of the sweep gradient center relative to the upper left corner of the component. <br> .value[2].f32: start point of the sweep gradient. The default value is <b>0</b>. <br> .value[3].f32: end point of the sweep gradient. The default value is <b>0</b>. <br> .value[4].f32: rotation angle of the sweep gradient. The default value is <b>0</b>. <br> .value[5].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,and <b>0</b> means the opposite.<br> .object: array of color stops, each of which consists of a color and its stop position. Invalid colors areautomatically skipped.<br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> |
| NODE_RADIAL_GRADIENT | Defines the radial gradient effect.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0]?.f32: X coordinate of the radial gradient center relative to the upper left corner of the component. <br> .value[1]?.f32: Y coordinate of the radial gradient center relative to the upper left corner of the component. <br> .value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,and <b>0</b> means the opposite. <br> .object: array of color stops, each of which consists of a color and its stop position. Invalid colors areautomatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate of the radial gradient center relative to the upper left corner of the component. <br> .value[1].f32: Y coordinate of the radial gradient center relative to the upper left corner of the component. <br> .value[2].f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated,and <b>0</b> means the opposite.<br> .object: array of color stops, each of which consists of a color and its stop position. Invalid colors areautomatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> |
| NODE_MASK | Adds a mask of the specified shape to the component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute, which supports five types ofshapes:<br> 1. Rectangle:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_RECTANGLE</b> for the rectangle shape.<br> .value[4].f32: width of the rectangle.<br> .value[5].f32: height of the rectangle.<br> .value[6].f32: width of the rounded corner of the rectangle.<br> .value[7].f32: height of the rounded corner of the rectangle.<br> .value[8]?.f32: radius of the top left corner of the rectangular shape.<br> .value[9]?.f32: radius of the bottom left corner of the rectangular shape.<br> .value[10]?.f32: radius of the top right corner of the rectangular shape.<br> .value[11]?.f32: radius of the bottom right corner of the rectangular shape.<br> 2. Circle:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_CIRCLE</b> for the circle shape.<br> .value[4].f32: width of the circle.<br> .value[5].f32: height of the circle.<br> 3. Ellipse:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[4].f32: width of the ellipse.<br> .value[5].f32: height of the ellipse.<br> 4. Path:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_PATH</b> for the path shape.<br> .value[4].f32: width of the path.<br> .value[5].f32: height of the path.<br> .string: command for drawing the path.<br> 5. Progress:<br> .value[0].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype).The value is <b>ARKUI_MASK_TYPE_PROGRESS</b> for the progress shape.<br> .value[1].f32: current value of the progress indicator.<br> .value[2].f32: maximum value of the progress indicator.<br> .value[3].u32: color of the progress indicator, in 0xARGB format.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md), which supports five types of shapes:<br> 1. Rectangle:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type.<br> .value[4].f32: width of the rectangle.<br> .value[5].f32: height of the rectangle.<br> .value[6].f32: width of the rounded corner of the rectangle.<br> .value[7].f32: height of the rounded corner of the rectangle.<br> .value[8].f32: radius of the top left corner of the rectangular shape.<br> .value[9].f32: radius of the bottom left corner of the rectangular shape.<br> .value[10].f32: radius of the top right corner of the rectangular shape.<br> .value[11].f32: radius of the bottom right corner of the rectangular shape.<br> 2. Circle:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type.<br> .value[4].f32: width of the circle.<br> .value[5].f32: height of the circle.<br> 3. Ellipse:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type.<br> .value[4].f32: width of the ellipse.<br> .value[5].f32: height of the ellipse.<br> 4. Path:<br> .value[0].u32 fill color, in 0xARGB format. <br> .value[1].u32: stroke color, in 0xARGB format. <br> .value[2].f32: stroke width, in vp. <br> .value[3].i32: mask type.<br> .value[4].f32: width of the path.<br> .value[5].f32: height of the path.<br> .string: command for drawing the path.<br> 5. Progress:<br> .value[0].i32: mask type.<br> .value[1].f32: current value of the progress indicator.<br> .value[2].f32: maximum value of the progress indicator.<br> .value[3].u32: color of the progress indicator.<br> |
| NODE_BLEND_MODE | Blends the component's background with the content of the component's child node.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: blend mode. The parameter type is [ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode). The default value is<b>ARKUI_BLEND_MODE_NONE</b>. <br> .value[1].?i32: how the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype).The default value is <b>BLEND_APPLY_TYPE_FAST</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: blend mode. The parameter type is [ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode). The default value is<b>ARKUI_BLEND_MODE_NONE</b>. <br> .value[1].i32: how the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype).The default value is <b>BLEND_APPLY_TYPE_FAST</b>. <br> |
| NODE_DIRECTION | Sets the direction of the main axis.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: direction of the main axis.<br> The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is <b>ARKUI_DIRECTION_AUTO</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: direction of the main axis.<br> The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is <b>ARKUI_DIRECTION_AUTO</b>. <br> |
| NODE_CONSTRAINT_SIZE | Defines the size constraints.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum width, in vp.<br> .value[1].f32: maximum width, in vp.<br> .value[2].f32: minimum height, in vp.<br> .value[3].f32: maximum height, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum width, in vp.<br> .value[1].f32: maximum width, in vp.<br> .value[2].f32: minimum height, in vp.<br> .value[3].f32: maximum height, in vp.<br> |
| NODE_GRAY_SCALE | Defines the grayscale effect.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1.For example, 0.5 indicates a 50% grayscale conversion ratio. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1.<br> |
| NODE_INVERT | Inverts the image.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: image inversion ratio. The value ranges from 0 to 1.For example, 0.5 indicates a 50% image inversion ratio.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: image inversion ratio. The value ranges from 0 to 1.<br> |
| NODE_SEPIA | Defines the sepia conversion ratio.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: sepia conversion ratio. The value ranges from 0 to 1.For example, 0.5 indicates that a 50% sepia conversion ratio.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: sepia conversion ratio. The value ranges from 0 to 1.<br> |
| NODE_CONTRAST | Defines the contrast attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: contrast. If the value is <b>1</b>, the source image is displayed.A larger value indicates a higher contrast. Value range: [0, 10).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: contrast. Value range: [0, 10).<br> |
| NODE_FOREGROUND_COLOR | Defines the foreground color attribute, which can be set, reset, and obtained as required through APIs.There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:<br> 1: .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> 2: .value[0].i32: color enum {@link ArkUI_ColoringStrategy}.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format.<br> |
| NODE_OFFSET | Defines the offset of the component's child relative to the component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32 : offset along the x-axis, in vp. <br> .value[1].f32 : offset along the y-axis, in vp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32 : offset along the x-axis, in vp. <br> .value[1].f32 : offset along the y-axis, in vp. <br> |
| NODE_MARK_ANCHOR | Sets the anchor for locating the component's child.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: X coordinate of the anchor, in vp.<br> .value[1].f32: Y coordinate of the anchor, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X coordinate of the anchor, in vp.<br> .value[1].f32: Y coordinate of the anchor, in vp.<br> |
| NODE_BACKGROUND_IMAGE_POSITION | 背景图在组件中显示位置，即相对于组件左上角的坐标，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].f32</b>：x轴位置，单位为px。<br><b>.value[1].f32</b>：y轴位置，单位为px。<br><b>.value[2]?.i32</b>：可选值，对齐方式，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_TOP_START。该参数从API version21开始支持。<br><b>.value[3]?.i32</b>：可选值，布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。多数场景下建议设置为AUTO，由系统自动处理布局方向；若需要固定方向，可设置为LTR或RTL。该参数从API version 21开始支持。<br>*返回：<br><b>.value[0].f32</b>：x轴位置，单位为px。<br><b>.value[1].f32</b>：y轴位置，单位为px。<br><b>.value[2].i32</b>：对齐方式，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)。该返回值从API version 21开始支持。<br><b>.value[3].i32</b>：布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)。该返回值从API version 21开始支持。 |
| NODE_ALIGN_RULES | Sets the alignment rules in the relative container.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: Use the {@link ArkUI_AlignmentRuleOption} object as the component’s alignment rule. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: Use the {@link ArkUI_AlignmentRuleOption} object as the component’s alignment rule. <br> |
| NODE_ALIGN_SELF | Sets the alignment mode of the child components along the cross axis of the parent container.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode of the child components along the cross axis of the parent container.<br> The parameter type is [ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment). The default value is <b>ARKUI_ITEM_ALIGNMENT_AUTO</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode of the child components along the cross axis of the parent container.<br> The parameter type is [ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment). The default value is <b>ARKUI_ITEM_ALIGNMENT_AUTO</b>. <br> |
| NODE_FLEX_GROW | Sets the percentage of the parent container's remaining space that is allocated to the component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: percentage of the parent container's remaining space that is allocated to the component. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: percentage of the parent container's remaining space that is allocated to the component. <br> |
| NODE_FLEX_SHRINK | Sets the percentage of the parent container's shrink size that is allocated to the component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: percentage of the parent container's shrink size that is allocated to the component. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: percentage of the parent container's shrink size that is allocated to the component. <br> |
| NODE_FLEX_BASIS | Sets the base size of the component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: percentage of the parent container's remaining space that is allocated to the component. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: percentage of the parent container's remaining space that is allocated to the component. <br> |
| NODE_ACCESSIBILITY_GROUP | Sets the accessibility group. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Accessibility group. The value <b>1</b> means that the component and all its child componentsform an entire selectable component.In this case, the accessibility service will no longer be available for the content of its child components.The value is <b>1</b> or <b>0</b>.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Accessibility group. The value <b>1</b> means that the component and all its child componentsform an entire selectable component.In this case, the accessibility service will no longer be available for the content of its child components.The value is <b>1</b> or <b>0</b>. |
| NODE_ACCESSIBILITY_TEXT | Sets the accessibility text. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: accessibility text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: accessibility text. |
| NODE_ACCESSIBILITY_MODE | Sets the accessibility service model. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: accessibility service model. The parameter type is [ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: accessibility service model. The parameter type is [ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode). |
| NODE_ACCESSIBILITY_DESCRIPTION | Sets the accessibility description.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: accessibility description.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: accessibility description. |
| NODE_FOCUS_STATUS | 组件获取焦点属性，支持属性设置，属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*说明：<br>设置参数为0时，当前层级页面获焦组件失焦，焦点转移到根容器上。<br>*参数：<br><b>.value[0].i32</b>：参数值为1表示组件获焦，为0表示组件失焦。<br>*返回：<br><b>.value[0].i32</b>：参数值为1表示组件获焦，为0表示组件失焦。 |
| NODE_ASPECT_RATIO | Defines the aspect ratio attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: aspect ratio of the component, in width/height format. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: aspect ratio of the component, in width/height format. <br> |
| NODE_LAYOUT_WEIGHT | Defines the weight of the component within its row, column, or flex container for proportionaldistribution of available space within the container.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: weight of the component along the main axis. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: weight of the component along the main axis. <br> |
| NODE_DISPLAY_PRIORITY | Sets the display priority for the component in the row, column, or flex  (single-line) container.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: display priority of the component in the container. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: display priority of the component in the container. <br> |
| NODE_OUTLINE_WIDTH | Sets the thickness of an element's outline.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: thickness of the left outline. <br> .value[1].f32: thickness of the top outline. <br> .value[2].f32: thickness of the right outline. <br> .value[3].f32: thickness of the bottom outline. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: thickness of the left outline. <br> .value[1].f32: thickness of the top outline. <br> .value[2].f32: thickness of the right outline. <br> .value[3].f32: thickness of the bottom outline. <br> |
| NODE_WIDTH_PERCENT | Defines the width attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width, in percentage.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width, in percentage.<br> |
| NODE_HEIGHT_PERCENT | Defines the height attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: height, in percentage.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: height, in percentage.<br> |
| NODE_PADDING_PERCENT | Defines the padding attribute, which can be set, reset, and obtained as required through APIs.There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:<br> 1: Specify the same padding for the four directions. <br> .value[0].f32: padding, in percentage.<br> 2: Specify different paddings for different directions. <br> .value[0].f32: top padding, in percentage.<br> .value[1].f32: right padding, in percentage.<br> .value[2].f32: bottom padding, in percentage.<br> .value[3].f32: left padding, in percentage.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: top padding, in percentage.<br> .value[1].f32: right padding, in percentage.<br> .value[2].f32: bottom padding, in percentage.<br> .value[3].f32: left padding, in percentage.<br> |
| NODE_MARGIN_PERCENT | Defines the margin attribute, which can be set, reset, and obtained as required through APIs.There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:<br> 1: Specify the same margin for the four directions. <br> .value[0].f32: margin, in percentage.<br> 2: Specify different margins for different directions. <br> .value[0].f32: top margin, in percentage.<br> .value[1].f32: right margin, in percentage.<br> .value[2].f32: bottom margin, in percentage.<br> .value[3].f32: left margin, in percentage.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: top margin, in percentage.<br> .value[1].f32: right margin, in percentage.<br> .value[2].f32: bottom margin, in percentage.<br> .value[3].f32: left margin, in percentage.<br> |
| NODE_GEOMETRY_TRANSITION | The implicit shared element transition within the component supports attribute setting,attribute reset, and attribute acquisition interfaces.Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .value[0]?.i32: The parameter type is 1 or 0. 2 components that share element bindings,Whether to continue to participate in the shared element animation when the appearance element is not deleted,the default is false, and the original position will remain unchanged if not involved. <br> .string is used to set the binding relationship. Set the id to "" toclear the binding relationship to avoid participating in sharing behavior. <br> The id can be changed and the binding relationship re-established.The same ID can only be bound to two components and they are in/out roles of different types.Multiple components cannot be bound to the same id. <br><br> Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .value[0].i32: The parameter type is 1 or 0. 2 components that share element bindings,Whether to continue to participate in the shared element animation when the appearance element is not deleted,the default is not false, if not involved, the original position will remain unchanged. <br> .string is used to set the binding relationship. Set the id to "" toclear the binding relationship to avoid participating in sharing behavior. <br> The id can be changed and the binding relationship re-established.The same ID can only be bound to two components and they are in/out roles of different types.Multiple components cannot be bound to the same id. |
| NODE_RELATIVE_LAYOUT_CHAIN_MODE | specifies the parameters of the chain formed by this component as the chain head,and supports attribute setting, attribute reset and attribute acquisition interfaces.Only takes effect when the parent container is RelativeContainerAttribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .value[0].i32: The direction of the chain. Enum [ArkUI_Axis](capi-native-type-h.md#arkui_axis). <br> .value[1].i32: Chain style. Enum {@link ArkUI_RelativeLayoutChainStyle}. <br><br> .value[0].i32: The direction of the chain. Enum [ArkUI_Axis](capi-native-type-h.md#arkui_axis). <br> .value[1].i32: Chain style. Enum {@link ArkUI_RelativeLayoutChainStyle}. |
| NODE_RENDER_FIT | Set the component content filling method in the process of width and height animation,support property setting, property reset, property acquisition interface.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32 Content filling mode [ArkUI_RenderFit](capi-native-type-h.md#arkui_renderfit).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32 Content filling mode [ArkUI_RenderFit](capi-native-type-h.md#arkui_renderfit).<br> |
| NODE_OUTLINE_COLOR | External stroke color properties, support property setting,property reset and property acquisition interface.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].u32: Set the border color of the four sides uniformly, using 0xargb, such as 0xFFFF11FF. <br> 2: .value[0].u32: Set the top border color, represented by 0xargb, such as 0xFFFF11FF. <br> .value[1].u32: Set the right border color, represented by 0xargb, such as 0xFFFF11FF. <br> .value[2].u32: Set the lower side box color, denoted by 0xargb, such as 0xFFFF11FF. <br> .value[3].u32: Set the left border color, denoted by 0xargb, such as 0xFFFF11FF. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: Set the top border color, represented by 0xargb, such as 0xFFFF11FF. <br> .value[1].u32: Set the right border color, represented by 0xargb, such as 0xFFFF11FF. <br> .value[2].u32: Set the lower side box color, denoted by 0xargb, such as 0xFFFF11FF. <br> .value[3].u32: Set the left border color, denoted by 0xargb, such as 0xFFFF11FF. <br> |
| NODE_SIZE | Set the height and width dimensions, support property setting,property reset and property acquisition interface.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: Width value, unit is vp;<br> .value[1].f32: Height value, unit is vp;<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: Width value, unit is vp;<br> .value[1].f32: Height value, unit is vp;<br> |
| NODE_RENDER_GROUP | Set whether the current component and child component arerendered off the screen first and then fused with the parent control,supporting property setting, property reset and property acquisition.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is 1 or 0.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is 1 or 0. |
| NODE_COLOR_BLEND | Add color overlay effect to components, support property setting,property reset and property acquisition interface.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: The color of the overlay is represented by 0xargb, such as 0xFFFF11FF. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: The color of the overlay is represented by 0xargb, such as 0xFFFF11FF. <br> |
| NODE_FOREGROUND_BLUR_STYLE | Provide content ambiguity capability for the current component,support property setting, property reset, property acquisition interface.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32 Represents the content blurring style, and uses the [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle) enumeration value.<br> .value[1]?.i32 Represents the dark and light mode used by the content blur effect,<br> with the {@link ArkUI_ThemeColorMode} enumeration value.<br> .value[2]?.i32 The color extraction mode used to represent the content blur effect takes<br> the [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor) enumeration value.<br> .value[3]?.f32: blur degree. The value range is [0.0, 1.0]. <br> .value[4]?.f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br> .value[5]?.f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32 Represents the content blurring style, and uses the [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle) enumeration value.<br> .value[1].i32 Represents the dark and light mode used by the content blur effect,<br> with the {@link ArkUI_ThemeColorMode} enumeration value.<br> .value[2].i32 The color extraction mode used to represent the content blur effect takes<br> the [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor) enumeration value.<br> .value[3].f32: blur degree. The value range is [0.0, 1.0]. <br> .value[4].f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br> .value[5].f32 It is a gray-level fuzzy parameter. The value range is [0,127].<br> |
| NODE_LAYOUT_RECT | Defines the component size and position for layout.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: X coordinate of the component, in px. <br> .value[1].i32: Y coordinate of the component, in px. <br> .value[2].i32: width of the component, in px. <br> .value[3].i32: height of the component, in px. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: X coordinate of the component, in px. <br> .value[1].i32: Y coordinate of the component, in px. <br> .value[2].i32: width of the component, in px. <br> .value[3].i32: height of the component, in px. <br> |
| NODE_FOCUS_ON_TOUCH | 设置当前组件是否支持点击获焦能力，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：参数值为1表示支持点击获焦，为0表示不支持点击获焦。<br>*返回：<br><b>.value[0].i32</b>：参数值为1表示支持点击获焦，为0表示不支持点击获焦。 |
| NODE_BORDER_WIDTH_PERCENT = 85 | Defines the border width attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].f32: width of the four borders, in percentage. <br> 2: .value[0].f32: width of the top border, in percentage. <br> .value[1].f32: width of the right border, in percentage. <br> .value[2].f32: width of the bottom border, in percentage. <br> .value[3].f32: width of the left border, in percentage. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width of the top border, in percentage. <br> .value[1].f32: width of the right border, in percentage. <br> .value[2].f32: width of the bottom border, in percentage. <br> .value[3].f32: width of the left border, in percentage. <br> |
| NODE_BORDER_RADIUS_PERCENT = 86 | Defines the border corner radius attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].f32: radius of the four corners, in percentage. <br> 2: .value[0].f32: radius of the upper left corner, in percentage. <br> .value[1].f32: radius of the upper right corner, in percentage. <br> .value[2].f32: radius of the lower left corner, in percentage. <br> .value[3].f32: radius of the lower right corner, in percentage. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: radius of the upper left corner, in percentage. <br> .value[1].f32: radius of the upper right corner, in percentage. <br> .value[2].f32: radius of the lower left corner, in percentage. <br> .value[3].f32: radius of the lower right corner, in percentage. <br> |
| NODE_ACCESSIBILITY_ID = 87 | Accessible ID, which can be obtained as required through APIs.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32：Accessible ID。<br> |
| NODE_ACCESSIBILITY_ACTIONS = 88 | Define accessible actions, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32：accessible action types，and uses the [ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype) enumeration value.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32：accessible action types，and uses the [ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype) enumeration value.<br> |
| NODE_ACCESSIBILITY_ROLE = 89 | Define accessible role, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32：accessible role type，and uses the [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype) enumeration value.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32：accessible role type，and uses the [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype) enumeration value.<br> |
| NODE_ACCESSIBILITY_STATE = 90 | Define accessible state, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object：the parameter type is [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md).<br> <br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object：the parameter type is [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md).<br> |
| NODE_ACCESSIBILITY_VALUE = 91 | Define accessible value, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object：the parameter type is [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object：the parameter type is [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md).<br> |
| NODE_EXPAND_SAFE_AREA = 92 | defines control components to extend their security zones,supporting property setting, property reset, and property fetching.Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Parameter format: <br> .value[0]? .u32: Set of extended security zone enumerated values [ArkUI_SafeAreaType](capi-native-type-h.md#arkui_safeareatype),For example, ARKUI_SAFE_AREA_TYPE_SYSTEM \| ARKUI_SAFE_AREA_TYPE_CUTOUT; <br> .value[1]? .u32: set of directional enum values for extended security zones [ArkUI_SafeAreaEdge](capi-native-type-h.md#arkui_safeareaedge); <br> For example: ARKUI_SAFE_AREA_EDGE_TOP \| ARKUI_SAFE_AREA_EDGE_BOTTOM; <br> <br> Attribute fetch method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br>.value[0].u32: extends the security zone. . <br>.value[1].u32: indicates the direction to extend the security zone. . <br> |
| NODE_VISIBLE_AREA_CHANGE_RATIO = 93 | Defines the visible area ratio (visible area/total area of the component) threshold for invoking thevisible area change event of the component. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting theattribute:<br>.value[...].f32: threshold array. The value ranges from 0 to 1.<br>.object: The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[...].f32: threshold array.<br>.object: The return type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).<br>**起始版本：** 12 |
| NODE_TRANSITION = 94 | Sets the transition effect when the component is inserted or deleted.This attribute can be set, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: transition effect. The parameter type is {@link ArkUI_TransitionEffect}. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: transition effect. The parameter type is {@link ArkUI_TransitionEffect}. <br> |
| NODE_UNIQUE_ID = 95 | Defines the component ID.This attribute can be obtained through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for obtaining the attribute:<br> .value[0].i32: component ID. <br><br>**废弃版本：** 20<br>**替代接口：** OH_ArkUI_NodeUtils_GetNodeUniqueId |
| NODE_FOCUS_BOX = 96 | 设置当前组件系统焦点框样式。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].f32</b>：焦点框相对组件边缘的距离。正数代表外侧，负数代表内侧。不支持百分比。<br><b>.value[1].f32</b>：焦点框宽度。不支持负数和百分比。<br><b>.value[2].u32</b>：焦点框颜色。 |
| NODE_CLICK_DISTANCE = 97 | 组件所绑定的点击手势移动距离限制，支持属性设置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].f32</b>：表示识别点击手势时允许手指在该范围内移动，单位为vp。 |
| NODE_TAB_STOP = 98 | 控制焦点是否能停在当前组件，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：参数值为1表示焦点能停在当前组件，为0表示焦点不能停在当前组件。默认值为0。<br>*返回：<br><b>.value[0].i32</b>：参数值为1表示焦点停在当前组件，为0表示焦点未停在当前组件。<br>**起始版本：** 14 |
| NODE_BACKDROP_BLUR = 99 | Defines the backdrop blur attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32：backdrop blur radius, in px. The value range is [0, +∞).<br> .value[1]?.f32：grayscale blur settings that control the brightness of the black color.<br> The value range is [0, 127].<br> .value[2]?.f32：grayscale blur settings that control the darkness of the white color.<br> The value range is [0, 127].<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32：backdrop blur radius, in px. The value range is [0, +∞).<br> .value[1].f32：grayscale blur settings that control the brightness of the black color.<br> The value range is [0, 127].<br> .value[2].f32：grayscale blur settings that control the darkness of the white color.<br> The value range is [0, 127].<br><br>**起始版本：** 15 |
| NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE = 100 | Defines the background image resizable attribute, which can be set, reset,and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width of the left edge. The unit is vp. <br> .value[1].f32: width of the top edge. The unit is vp. <br> .value[2].f32: width of the right edge. The unit is vp. <br> .value[3].f32: width of the bottom edge. The unit is vp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width of the left edge. The unit is vp. <br> .value[1].f32: width of the top edge. The unit is vp. <br> .value[2].f32: width of the right edge. The unit is vp. <br> .value[3].f32: width of the bottom edge. The unit is vp. <br><br>**起始版本：** 19 |
| NODE_NEXT_FOCUS = 101 | 设置下一个走焦节点。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：走焦类型，定义在[ArkUI_FocusMove](capi-common-attributes-h.md#arkui_focusmove)。<br><b>.object</b>：下一个焦点。参数类型为[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。<br>**起始版本：** 18 |
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO = 102 | 设置可见区域变化监听的参数。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*说明：<br>非实时回调，实际回调与预期间隔可能存在差别。两次可见区域回调的时间间隔不小于预期更新间隔。当开发者设置的预期间隔过小时，由系统负载决定实际回调间隔时间。当前接口的可见区域回调阈值默认包含0。例如，开发者设置回调阈值为[0.5]，实际生效的阈值为[0.0, 0.5]。<br>*参数：<br><b>.object</b>：参数类型为[ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)。<br>*返回：<br><b>.object</b>：参数类型为[ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)。<br>**起始版本：** 17 |
| NODE_TRANSLATE_WITH_PERCENT = 103 | Defines the translate attribute, which supports for percentile translation input, and can be set, reset,and obtained as required through APIs.<br>     Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: distance to translate along the x-axis. The default unit is percentage.The unit is vp only if value[3] exists and value[3] is 0. The default value of value[0] is <b>0</b>.<br> .value[1].f32: distance to translate along the y-axis. The default unit is percentage.The unit is vp only if value[4] exists and value[4] is 0. The default value of value[1] is <b>0</b>.<br> .value[2].f32: distance to translate along the z-axis, in vp. The default value is <b>0</b>.<br> .value[3]?.i32: Whether the translation distance along the x-axis is specified as a percentage.The value can be 0 or 1. When the value is 1, it is specified as a percentage.For example, value[0].f32=0.1 and value[3].i32=1 indicates a 10% shift in the x direction.The default value is <b>1</b>.<br> .value[4]?.i32: Whether the translation distance along the y-axis is specified as a percentage.The value can be 0 or 1. When the value is 1, it is specified as a percentage.For example, value[1].f32=0.1 and value[4].i32=1 indicates a 10% shift in the y direction.The default value is <b>1</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: distance to translate along the x-axis. The unit depends on value[3].<br> .value[1].f32: distance to translate along the y-axis. The unit depends on value[4].<br> .value[2].f32: distance to translate along the z-axis. The unit is vp.<br> .value[3].i32: Whether the unit of the X-axis translation distance is in percentage. When value[3].i32 is 0,the unit of the X-axis translation distance is vp; when value[3].i32 is 1, the unit of the X-axis translationdistance is percentage;<br> .value[4].i32: Whether the unit of the Y-axis translation distance is in percentage. When value[4].i32 is 0,the unit of the Y-axis translation distance is vp; when value[4].i32 is 1, the unit of the Y-axis translationdistance is percentage;<br><br>**起始版本：** 20 |
| NODE_ROTATE_ANGLE = 104 | Sets component rotation with multi-axis angle control. This attribute can be set, reset,and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: x-axis rotation angle. The default value is <b>0</b>. <br> .value[1].f32: y-axis rotation angle. The default value is <b>0</b>. <br> .value[2].f32: z-axis rotation angle. The default value is <b>0</b>. <br> .value[3].f32: perspective distance from the viewpoint to the z=0 plane, in px. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: x-axis rotation angle. The default value is <b>0</b>..value[1].f32: y-axis rotation angle. The default value is <b>0</b>. <br> .value[2].f32: z-axis rotation angle. The default value is <b>0</b>. <br> .value[3].f32: perspective distance from the viewpoint to the z=0 plane, in px. The default value is <b>0</b>. <br><br>**起始版本：** 20 |
| NODE_WIDTH_LAYOUTPOLICY = 105 | Defines the width attribute with param type LayoutPolicy, which can be set, reset, and obtainedas required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: the LayoutPolicy that the width of the component follows.<br> The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: the LayoutPolicy that the width of the component follows.<br> The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy). <br><br>**起始版本：** 21 |
| NODE_HEIGHT_LAYOUTPOLICY = 106 | Defines the height attribute with param type LayoutPolicy, which can be set, reset, and obtainedas required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: the LayoutPolicy that the height of the component follows.<br> The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: the LayoutPolicy that the height of the component follows.<br> The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy). <br><br>**起始版本：** 21 |
| NODE_POSITION_EDGES = 107 | Defines the position attribute in param type Edges, which specifies the position of the componentby the distance relative to the parent container's four edges. This attribute can be set, reset, and obtained asrequired through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object indicates struct of edges for position. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object indicates struct of edges for position. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md). <br><br>**起始版本：** 21 |
| NODE_ALLOW_FORCE_DARK = 108 | Set whether the component enables the ability to invert colors.This attribute can be set , and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is 1 or 0.<br><br>**起始版本：** 21 |
| NODE_PIXEL_ROUND = 109 | Defines the pixelRound attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object indicates struct of policy for pixelRound. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object indicates struct of policy for pixelRound. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md). <br><br>**起始版本：** 21 |
| NODE_ENABLE_CLICK_SOUND_EFFECT = 110 | 设置组件是否启用默认点击音效。此功能仅在TV上生效，在其他设备上启用默认点击音效也不会播放音效。是否能够发音依赖设备声音相关的设置，如静音模式下不会播放音效。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：参数取值为1或0，1表示启用默认点击音效，0表示禁用默认点击音效，默认值为1。<br>*返回：<br><b>.value[0].i32</b>：表示此节点是否启用了默认的点击音效。参数取值为1或0，1表示启用默认点击音效，0表示禁用默认点击音效。<br>**起始版本：** 24 |
| NODE_MOTION_PATH = 111 | Defines the motion path attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is[ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .object indicates a pointer to the ArkUI_MotionPathOptions. The parameter type is[ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). <br><br>**起始版本：** 23 |
| NODE_HOVER_EFFECT = 112 | 定义组件被悬停时的效果。该属性可根据需要通过API进行设置、重置和获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：组件在悬停状态下的悬停效果。参数类型为[ArkUI_HoverEffect](capi-common-attributes-h.md#arkui_hovereffect)。默认值为ARKUI_HOVER_EFFECT_AUTO。<br>*返回：<br><b>.value[0].i32</b>：组件在悬停状态下的悬停效果。参数类型为[ArkUI_HoverEffect](capi-common-attributes-h.md#arkui_hovereffect)。<br>**起始版本：** 23 |
| NODE_FOCUS_SCOPE_ID = 113 | 将容器设置为具有特定标识符的焦点组，支持属性设置、属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.string</b>：焦点作用域标识符。<br><b>.value[0].i32</b>：该作用域是否为焦点组，默认值为0。取值范围为1或0。1表示设置为焦点组，0表示组件未被设置为焦点组。<br><b>.value[1].i32</b>：箭头键是否可以将焦点从焦点组内部移至外部，仅当isGroup为true时有效，默认值为1。取值范围为1或0。1表示箭头键可以将焦点从焦点组内部移至外部，0表示箭头键无法将焦点从焦点组内部移至外部。<br>*返回：<br><b>.string</b>：焦点作用域标识符。<br><b>.value[0].i32</b>：该作用域是否为焦点组，默认值为0。取值范围为1或0。1表示设置为焦点组，0表示组件未被设置为焦点组。<br><b>.value[1].i32</b>：箭头键是否可以将焦点从焦点组内部移至外部，仅当isGroup为true时有效，默认值为1。取值范围为1或0。1表示箭头键可以将焦点从焦点组内部移至外部，0表示箭头键无法将焦点从焦点组内部移至外部。<br>**起始版本：** 23 |
| NODE_FOCUS_SCOPE_PRIORITY = 114 | 设置组件在特定焦点作用域内的焦点优先级，支持属性设置、属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.string</b>：焦点作用域标识符。<br><b>.value[0].i32</b>：焦点作用域内获焦优先级。参数类型为[ArkUI_FocusPriority](capi-common-attributes-h.md#arkui_focuspriority)。默认值为ARKUI_FOCUS_PRIORITY_AUTO。<br>*返回：<br><b>.string</b>：焦点作用域标识符。<br><b>.value[0].i32</b>：焦点作用域优先级。参数类型为[ArkUI_FocusPriority](capi-common-attributes-h.md#arkui_focuspriority)。<br>**起始版本：** 23 |
| NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD = 115 | 设置点击事件的距离阈值，支持属性设置、属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].f32</b>：点击事件移动阈值。取值范围(0, +∞)。默认值为+∞，单位vp。<br>*返回：<br><b>.value[0].f32</b>：点击事件移动阈值。<br>**起始版本：** 23 |
| NODE_RESPONSE_REGION_LIST = 116 | 设置组件事件的响应区域，支持属性设置，属性重置和属性获取接口。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*说明：<br>设置时data数据大小无数量限制，均可以设置成功，但仅支持获取到20个。获取到的data数组顺序与设置顺序可能存在差异。<br>*参数：<br><b>.data[0].i32</b>：适用于此响应区域的事件工具类型。参数类型为[ArkUI_ResponseRegionSupportedTool](capi-common-attributes-h.md#arkui_responseregionsupportedtool)。默认值：ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL。<br><b>.data[1].f32</b>：触摸点相对于组件左上角的x轴坐标，默认值：0.0，单位为vp。<br><b>.data[2].f32</b>：触摸点相对于组件左上角的y轴坐标，默认值：0.0，单位为vp。<br><b>.data[3].f32</b>：触摸热区的宽度，默认值：100.0，单位为百分比。<br><b>.data[4].f32</b>：触摸热区的高度，默认值：100.0，单位为百分比。<br><b>.data[5...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。<br>*返回：<br><b>.data[0].i32</b>：适用于此响应区域的事件工具类型。参数类型为[ArkUI_ResponseRegionSupportedTool](capi-common-attributes-h.md#arkui_responseregionsupportedtool)。默认值：ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL。<br><b>.data[1].f32</b>：触摸点相对于组件左上角的x轴坐标，默认值：0.0，单位为vp。<br><b>.data[2].f32</b>：触摸点相对于组件左上角的y轴坐标，默认值：0.0，单位为vp。<br><b>.data[3].f32</b>：触摸热区的宽度，默认值：100.0，单位为百分比。<br><b>.data[4].f32</b>：触摸热区的高度，默认值：100.0，单位为百分比。<br><b>.data[5...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。<br>**起始版本：** 23 |
| NODE_MONOPOLIZE_EVENTS = 117 | 定义独占事件属性，该属性可根据需要通过API进行设置、重置和获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br><b>.value[0].i32</b>：取值范围为1或0。1表示设置组件独占，0表示组件未设置独占属性。<br>*返回：<br><b>.value[0].i32</b>：取值范围为1或0。1表示设置组件独占，0表示组件未设置独占属性。<br>**起始版本：** 23 |
| NODE_CHAIN_WEIGHT = 118 | Sets the weight of the component in a chain, which is used to re-lay out components that form the chain.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: Horizontal ChainWeight.<br> .value[1].f32: Vertical ChainWeight.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: Horizontal ChainWeight.<br> .value[1].f32: Vertical ChainWeight.<br><br>**起始版本：** 23 |
| NODE_IGNORE_LAYOUT_SAFE_AREA = 119 | Expands the layout safe area of a component.,supporting property setting, property reset, and property fetching.Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Parameter format: <br> .value[0].u32: The region type to expand the component's layout safe area into. The default value is LayoutSafeAreaType.SYSTEM. [ArkUI_LayoutSafeAreaType](capi-native-type-h.md#arkui_layoutsafeareatype),For example, ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM; <br> .value[1].u32: The set of edges for which to ignore layout safe area. The default value is LayoutSafeAreaEdge.ALL. [ArkUI_LayoutSafeAreaEdge](capi-native-type-h.md#arkui_layoutsafeareaedge); <br> For example: ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_START; <br> <br> Attribute fetch method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br>.value[0].u32: The region type to expand the component's layout safe area into. <br>.value[1].u32: The set of edges for which to ignore layout safe area. <br><br>**起始版本：** 23 |
| NODE_DASH_WIDTH = 120 | Defines the length of dash when BorderStyle is dashed, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: The length of dash on the top border. <br> .value[1].f32: The length of dash on the right border. <br> .value[2].f32: The length of dash on the bottom border. <br> .value[3].f32: The length of dash on the left border. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: The length of dash on the top border. <br> .value[1].f32: The length of dash on the right border. <br> .value[2].f32: The length of dash on the bottom border. <br> .value[3].f32: The length of dash on the left border. <br><br>**起始版本：** 23 |
| NODE_DASH_GAP = 121 | Defines the gap of dash when BorderStyle is dashed, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: The gap of dash on the top border. <br> .value[1].f32: The gap of dash on the right border. <br> .value[2].f32: The gap of dash on the bottom border. <br> .value[3].f32: The gap of dash on the left border. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: The gap of dash on the top border.   .value[1].f32: The gap of dash on the right border. <br> .value[2].f32: The gap of dash on the bottom border. <br> .value[3].f32: The gap of dash on the left border. <br><br>**起始版本：** 23 |
| NODE_LAYOUT_GRAVITY = 122 | Defines the align rules of child component in Stack container, which can be set, reset, and obtained as required through APIs.<br> The default value is <b>ARKUI_LOCALIZED_ALIGNMENT_CENTER</b>. <br>     Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: LocalizedAlignment mode. The data type is [ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: LocalizedAlignment mode. The data type is [ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment). <br><br>**起始版本：** 23 |
| NODE_BORDER_RADIUS_TYPE = 123 | Defines the render types for drawing rounded corners when the radius of the border rounded corners is set, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Render types for drawing rounded corners. The data type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy).The default value is <b>ARKUI_RENDERSTRATEGY_FAST</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Render types for drawing rounded corners. The data type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy). <br><br>**起始版本：** 23 |
| NODE_INSPECTOR_LABEL = 126 | Defines the inspector label attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: inspector label.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: inspector label.<br><br>**起始版本：** 26.0.0 |
| NODE_ACCESSIBILITY_NEXT_FOCUS_ID = 124 | Defines the next accessibility focus id of current component for accessibility processing to find the next focus component. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: accessibility next focus ID.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: accessibility next focus ID.<br>**起始版本：** 26.0.0 |
| NODE_ACCESSIBILITY_DEFAULT_FOCUS = 125 | Sets the accessibility default focus flag for accessibility services to find the default focus component. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Accessibility default focus. The value <b>1</b> means that the component is defined as default focus in accessibility services.<br> The value is <b>1</b> or <b>0</b>.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Accessibility default focus. The value <b>1</b> means that the component is defined as default focus in accessibility services.<br> The value is <b>1</b> or <b>0</b>.<br>**起始版本：** 26.0.0 |
| NODE_SYSTEM_MATERIAL = 127 | Defines the system material attribute, which can be set, reset, and obtained as required through APIs.Only devices that support systemMaterial can use this attribute. Otherwise, when setting this attribute,the error code [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) will be returned.Whether a device supports materials can be determined by calling{@link OH_ArkUI_NativeModule_GetSystemMaterialSupported}.The material effect behaves differently on devices with different level of computing powers.The level is defined by {@link ArkUI_MaterialLevel}, which can be obtained by{@link OH_ArkUI_NativeModule_GetGlobalMaterialLevel}.On devices with the computing power level of ARKUI_MATERIAL_LEVEL_SMOOTH, it affects attributes such as thebackgroundColor, borderWidth, borderColor, shadow.On devices with the computing power levels of ARKUI_MATERIAL_LEVEL_EXQUISITE or ARKUI_MATERIAL_LEVEL_GENTLE,it affects shadow attribute and adds a filter effect at the system material layer, which can produce an effectsimilar to glass.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: system material object. The parameter type is {@link ArkUI_ImmersiveMaterialHandle}.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: system material object. The parameter type is {@link ArkUI_ImmersiveMaterialHandle}.<br> The ArkUI_ImmersiveMaterialHandle object of the return value is a pointer to static member, so do not releasethe return object by calling {@link OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy}.<br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT | Defines the text content attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: text content.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: text content.<br> |
| NODE_FONT_COLOR | Defines the font color attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: font color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: font color value, in 0xARGB format.<br> |
| NODE_FONT_SIZE | Defines the font size attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: font size, in fp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: font size, in fp.<br> |
| NODE_FONT_STYLE | Defines the font style attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).<br> |
| NODE_FONT_WEIGHT | Defines the font weight attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).<br> |
| NODE_TEXT_LINE_HEIGHT | Defines the text line height attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: line height, in fp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: line height, in fp.<br> |
| /** | Defines the text decoration style and color.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype).The default value is <b>ARKUI_TEXT_DECORATION_TYPE_NONE</b>.<br> .value[1]?.u32: text decoration color, in 0xARGB format. For example, 0xFFFF0000 indicates red. Optional.<br> .value[2]?.i32: text decoration style [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype).<br> .value[1].u32: text decoration color, in 0xARGB format. <br> .value[2].i32: text decoration style [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle). <br> |
| NODE_TEXT_DECORATION | Defines the text decoration style and color.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype).The default value is <b>ARKUI_TEXT_DECORATION_TYPE_NONE</b>.<br> .value[1]?.u32: text decoration color, in 0xARGB format. For example, 0xFFFF0000 indicates red. Optional.<br> .value[2]?.i32: text decoration style [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle). <br> .value[3]?.f32: text decoration thickness scale. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype).<br> .value[1].u32: text decoration color, in 0xARGB format. <br> .value[2].i32: text decoration style [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle). <br> .value[3].f32: text decoration thickness scale. <br>     since 22 |
| NODE_TEXT_CASE | Defines the text case attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text case.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text case.<br> |
| NODE_TEXT_LETTER_SPACING | Defines the letter spacing attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: letter spacing, in fp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: letter spacing, in fp.<br> |
| NODE_TEXT_MAX_LINES | Sets the maximum number of lines in the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: maximum number of lines in the text.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: maximum number of lines in the text.<br> |
| NODE_TEXT_ALIGN | Horizontal alignment mode of the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: horizontal alignment mode of the text. The value is an enum of [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: horizontal alignment mode of the text. The value is an enum of [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment). <br> |
| NODE_TEXT_OVERFLOW | Defines the text overflow attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: display mode when the text is too long. {@ArkUI_TextOverflow}<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: display mode when the text is too long. {@ArkUI_TextOverflow}<br> |
| NODE_FONT_FAMILY | Defines the font family attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: fonts, separated by commas (,).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: fonts, separated by commas (,). |
| NODE_TEXT_COPY_OPTION | Defines the copy option attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: copy option [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions). The default value is <b>ARKUI_COPY_OPTIONS_NONE</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: copy option {@link ArkUI_CopyOptions. <br> |
| NODE_TEXT_BASELINE_OFFSET | Defines the text baseline offset attributeThis attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: baseline offset, in fp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: baseline offset, in fp. <br> |
| NODE_TEXT_TEXT_SHADOW | Defines the text shadow attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: blur radius of the shadow, in vp.<br> .value[1].i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is <b>ARKUI_SHADOW_TYPE_COLOR</b>.<br> .value[2].u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> .value[3].f32: offset of the shadow along the x-axis, in vp.<br> .value[4].f32: offset of the shadow along the y-axis, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: blur radius of the shadow, in vp.<br> .value[1].i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype).<br> .value[2].u32: shadow color, in 0xARGB format.<br> .value[3].f32: offset of the shadow along the x-axis, in vp.<br> .value[4].f32: offset of the shadow along the y-axis, in vp.<br> |
| NODE_TEXT_MIN_FONT_SIZE | Defines the minimum font size attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum font size, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum font size, in fp. |
| NODE_TEXT_MAX_FONT_SIZE | Defines the maximum font size attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum font size, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum font size, in fp. |
| NODE_TEXT_FONT | Defines the text style attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string?: font family. Optional. Use commas (,) to separate multiple fonts. <br> .value[0].f32: font size, in fp. <br> .value[1]?.i32: font weight. Optional. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>. <br> .value[2]?.i32: font style. Optional. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: font family. Use commas (,) to separate multiple fonts. <br> .value[0].f32: font size, in fp. <br> .value[1].i32: font weight. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>. <br> .value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>. |
| NODE_TEXT_HEIGHT_ADAPTIVE_POLICY | Defines how the adaptive height is determined for the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: how the adaptive height is determined for the text.The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-native-type-h.md#arkui_textheightadaptivepolicy).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: how the adaptive height is determined for the text.The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-native-type-h.md#arkui_textheightadaptivepolicy) |
| NODE_TEXT_INDENT | Defines the indentation of the first line.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: indentation of the first line. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: indentation of the first line. <br> |
| NODE_TEXT_WORD_BREAK | Defines the line break rule. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak). <br> |
| NODE_TEXT_ELLIPSIS_MODE | Defines the ellipsis position. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode). <br> |
| NODE_TEXT_LINE_SPACING | Defines the text line spacing attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: line spacing, in fp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: line spacing, in fp.<br> |
| NODE_FONT_FEATURE | Set the text feature effect and the NODE_FONT_FEATURE attribute,NODE_FONT_FEATURE is the advanced typesetting capability of OpenTypeFeatures such as ligatures and equal-width digits are generally used in customized fonts. <br> The capabilities need to be supported by the fonts, <br> Interfaces for setting, resetting, and obtaining attributes are supported. <br> Attribute setting method parameter {@Link ArkUI_AttributeItem} format: <br> .string: complies with the text feature format. The format is normal \| <br> is in the format of [ \| on \| off],.There can be multiple values separated by commas (,). <br> For example, the input format of a number with the same width is ss01 on. <br> <br> Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:<br> .string indicates the content of the text feature. Multiple text features are separated by commas (,). |
| NODE_TEXT_ENABLE_DATA_DETECTOR | Setting Enable Text Recognition.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:Enable text recognition, default value false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32：Enable Text Recognition<br> |
| NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG | Set the text recognition configuration.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0...].i32: Array of entity types, parameter types[ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype)。<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0...].i32：Array of entity types, parameter types[ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype)。<br> |
| NODE_TEXT_SELECTED_BACKGROUND_COLOR | Defines the background color of the selected text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_TEXT_CONTENT_WITH_STYLED_STRING | The text component uses a formatted string object to set text content properties,and supports property setting, property reset, and property acquisition interfaces.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object indicates ArkUI_StyledString formatted string data. The parameter type is {@link ArkUI_StyledString}. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object indicates ArkUI_StyledString formatted string data. The parameter type is {@link ArkUI_StyledString}. |
| NODE_TEXT_HALF_LEADING = 1029 | Sets whether to center text vertically in the text component.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to center text vertically. The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to center text vertically. <br> |
| NODE_IMMUTABLE_FONT_WEIGHT = 1030 | Defines the font weight attribute, which can be set, reset, and obtained as required through APIs.The font weight specified by this API is not affected by any changes in the system font weight settings.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).<br><br>**起始版本：** 15 |
| NODE_TEXT_LINE_COUNT = 1031 | Defines the text line count attribute, which can only be obtained as required through APIs.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: line count of the node.<br>**起始版本：** 20 |
| NODE_TEXT_OPTIMIZE_TRAILING_SPACE = 1032 | Sets whether to optimize the trailing spaces at the end of each line during text layout.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].i32: whether to optimize trailing spaces at the end of each line during text layout.The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: whether to optimize trailing spaces at the end of each line during text layout. <br><br>**起始版本：** 20 |
| NODE_TEXT_LINEAR_GRADIENT = 1033 | Sets a linear gradient effect for text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: start angle of the linear gradient.The setting takes effect only when <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>.A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>. <br> .value[1].i32: direction of the linear gradient. When a direction other than<b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> is set, the <b>angle</b> property is ignored.The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection). <br> .value[2].i32: whether the colors are repeated. The default value is <b>false</b>..object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: start angle of the linear gradient.When <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>, <b>angle</b> at the set value;otherwise, it is at default value. <br> .value[1].i32: direction of the linear gradient. <br> .value[2].i32: whether the colors are repeated. <br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br><br>**起始版本：** 20 |
| NODE_TEXT_RADIAL_GRADIENT = 1034 | Sets a radial gradient effect for text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3]?.i32: whether the colors are repeated.The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite. <br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[1].f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[2].f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3].i32: whether the colors are repeated.The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.  <br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br><br>**起始版本：** 20 |
| NODE_TEXT_VERTICAL_ALIGN = 1035 | Sets the vertical alignment of the text content.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: vertical alignment of the text content, specified using the [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment)enum. The default value is <b>ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: vertical alignment of the text content, specified using the [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment)enum. <br><br>**起始版本：** 20 |
| NODE_TEXT_CONTENT_ALIGN = 1036 | Sets the content align of the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: content align of the text, specified using the [ArkUI_TextContentAlign](capi-native-type-h.md#arkui_textcontentalign)enum. The default value is <b>ARKUI_TEXT_CONTENT_ALIGN_CENTER</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: content align of the text, specified using the [ArkUI_TextContentAlign](capi-native-type-h.md#arkui_textcontentalign)enum. <br><br>**起始版本：** 21 |
| NODE_TEXT_MIN_LINES = 1037 | Sets the minimum number of lines in the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: minimum number of lines in the text.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: minimum number of lines in the text.<br><br>**起始版本：** 22 |
| NODE_TEXT_ENABLE_SELECTED_DATA_DETECTOR = 1038 | Enables the selected data detector.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Enable selected text recognition, default value true.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether selected text recognition is enabled.<br><br>**起始版本：** 22 |
| NODE_TEXT_MIN_LINE_HEIGHT = 1040 | Defines the minimum text line height attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum line height.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum line height.<br><br>**起始版本：** 22 |
| NODE_TEXT_MAX_LINE_HEIGHT = 1041 | Defines the maximum text line height attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum line height.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum line height.<br><br>**起始版本：** 22 |
| NODE_TEXT_LINE_HEIGHT_MULTIPLE = 1042 | Defines line height multiple value of text, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: line height multiple value of text.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: line height multiple value of text.<br><br>**起始版本：** 22 |
| NODE_TEXT_LAYOUT_MANAGER = 1043 | Get the text layout manager of the text.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: the layout manager of text. The parameter type is {@link ArkUI_TextLayoutManager}.<br><br>**起始版本：** 22 |
| NODE_TEXT_EDIT_MENU_OPTIONS = 1044 | Set the edit menu options of the text.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: the edit menu options of text. The parameter type is [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md).<br><br>**起始版本：** 22 |
| NODE_TEXT_BIND_SELECTION_MENU = 1045 | Bind the selection menu for text.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: the custom selection menu of text.The parameter type is {@link ArkUI_SelectionMenuOptions}.<br><br>**起始版本：** 22 |
| NODE_TEXT_TEXT_SELECTION = 1046 | Sets the text selection area, which will be highlighted.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. <br> .object: selection options including the menu popup policy.The parameter type is {@link ArkUI_SelectionOptions}. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. <br> .object: selection options including the menu popup policy.The parameter type is {@link ArkUI_SelectionOptions}. <br><br>**起始版本：** 23 |
| 	  NODE_TEXT_ORPHAN_CHAR_OPTIMIZATION = 1047 | Whether to avoid an orphan word on the last line of the paragraph.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:  Whether enable the feature, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The current state of this feature.<br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_COMPRESS_LEADING_PUNCTUATION = 1048 | Whether to compress punctuation at the beginning of line.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:  Whether enable the feature, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether compress punctuation at the beginning of line.<br><br>**起始版本：** 23 |
| NODE_TEXT_INCLUDE_FONT_PADDING = 1049 | Determines whether the layout adds extra padding at the top and bottom to make space for characters.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Enable include the font padding, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether include the font padding.<br><br>**起始版本：** 23 |
| NODE_TEXT_FALLBACK_LINE_SPACING = 1050 | Whether to include ascent/descent from fallback fonts to prevent overlapping lines.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:  Whether enable the feature, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether fallback line spacing.<br><br>**起始版本：** 23 |
| NODE_TEXT_MARQUEE_OPTIONS = 1051 | Set the marquee options of text.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: the marquee options of text. The parameter type is [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: the marquee options of text. The parameter type is [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md).<br><br>**起始版本：** 23 |
| NODE_TEXT_DIRECTION = 1052 | Writing direction of the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: writing direction of the text. The value is an enum of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: writing direction the text. The value is an enum of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). <br><br>**起始版本：** 23 |
| NODE_TEXT_SELECTED_DRAG_PREVIEW_STYLE = 1053 | Used to set the selected drag preview style.Format of the {@link Arkui_AttributeItem} parameter for setting the attribute:<br> .object: selected drag preview style configuration.<br> The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br> <br> Format of the return value {@link Arkui_AttributeItem}:<br> .object: selected drag preview style configuration.<br> The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br><br>**起始版本：** 23 |
| NODE_TEXT_CONTROLLER = 1054 | Sets the controller of the text.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: the controller of the text. The parameter type is[OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md).<br><br>**起始版本：** 26.0.0 |
| NODE_SPAN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SPAN | Defines the text content attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: content of the text span. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: content of the text span. <br> |
| NODE_SPAN_TEXT_BACKGROUND_STYLE | Defines the text background style.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the text background, in 0xARGB format, for example, <b>0xFFFF0000</b> indicating red. <br> The second parameter indicates the rounded corners of the text background. Two setting modes are available: <br> 1: .value[1].f32: radius of the four corners, in vp. <br> 2: .value[1].f32: radius of the upper left corner, in vp. <br> .value[2].f32: radius of the upper right corner, in vp. <br> .value[3].f32: radius of the lower left corner, in vp. <br> .value[4].f32: radius of the lower right corner, in vp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the text background, in 0xARGB format. <br> .value[1].f32: radius of the upper left corner, in vp. <br> .value[2].f32: radius of the upper right corner, in vp. <br> .value[3].f32: radius of the lower left corner, in vp. <br> .value[4].f32: radius of the lower right corner, in vp. <br> |
| NODE_SPAN_BASELINE_OFFSET | Defines the text baseline offset attributeThis attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: baseline offset, in fp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: baseline offset, in fp. <br> |
| NODE_SPAN_FONT = 2003 | Defines the text style attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> ?.string: font family. Optional. Use commas (,) to separate multiple fonts. <br> .value[0].f32: font size, in fp. <br> .value[1]?.i32: font weight. Optional..value[2]?.i32: font style. Optional. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.?.object: Optional. The font configurations. The parameter type is [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: font family. Use commas (,) to separate multiple fonts. <br> .value[0].f32: font size, in fp. <br> .value[1].i32: font weight. <br> .value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>..object: the font configurations. The parameter type is [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md).<br><br>**起始版本：** 24 |
| NODE_SPAN_FONT_WEIGHT = 2004 | Defines the font weight attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: font weight. The default value is 400.<br> ?.object: Optional. The font weight configurations. The parameter type is [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: font weight.<br> .object: the font weight configurations. The parameter type is [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md).<br><br>**起始版本：** 24 |
| NODE_IMAGE_SPAN_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_SPAN | Defines the image source of the image span.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: image address of the image span.<br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: image address of the image span.<br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}.<br> |
| NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT | Defines the alignment mode of the image with the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode of the image with the text.The value is an enum of [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode of the image with the text.The value is an enum of [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment). <br> |
| NODE_IMAGE_SPAN_ALT | Defines the placeholder image source.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: placeholder image source. <br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: placeholder image source. <br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}.<br> |
| NODE_IMAGE_SPAN_BASELINE_OFFSET = 3003 | Defines the baseline offset attribute of the <b>ImageSpan</b> component.This attribute can be set, reset, and obtained as required through APIs.A positive value means an upward offset, while a negative value means a downward offset.The default value is <b>0</b>, and the unit is fp. <br>     Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: baseline offset, in fp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: baseline offset, in fp. <br><br>**起始版本：** 13 |
| NODE_IMAGE_SPAN_COLOR_FILTER = 3004 | Defines the color filter of the image span.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value [0].f32 to . value [19].f32: filter matrix array.  .size :5 x 4 filter array size.  .object : the pointer to OH_Drawing_ColorFilter. Either . value or . object is set.   Format of the return value {@ link ArkUI_AttributeItem ): .value [0].f32 to .value [19].f32: filter matrix array.  .size: 5 x 4 filter array size.  .object: the pointer to OH_Drawing_ColorFilter.<br>**起始版本：** 22 |
| NODE_IMAGE_SPAN_SUPPORT_SVG2 = 3005 | Set the range of SVG parsing capabilities supported through enable switch.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether color fliter support svg. The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: enable switch.<br><br>**起始版本：** 22 |
| NODE_IMAGE_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE | Defines the image source of the <Image> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: image source.<br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: image source.<br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}.<br> |
| NODE_IMAGE_OBJECT_FIT | Defines how the image is resized to fit its container.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: how the image is resized to fit its container. The value is an enum of [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: how the image is resized to fit its container. The value is an enum of [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit). <br> |
| NODE_IMAGE_INTERPOLATION | Defines the interpolation effect of the image.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: interpolation effect of the image. The value is an enum of [ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: interpolation effect of the image. The value is an enum of [ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation). <br> |
| NODE_IMAGE_OBJECT_REPEAT | Defines how the image is repeated.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: how the image is repeated. The value is an enum of [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: how the image is repeated. The value is an enum of [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat). <br> |
| NODE_IMAGE_COLOR_FILTER | Defines the color filter of the image.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32 to .value[19].f32: filter matrix array. <br> .size: 5 x 4 filter array size. <br> .object: the pointer to OH_Drawing_ColorFilter. Either .value or .object is set. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32 to .value[19].f32: filter matrix array. <br> .size: 5 x 4 filter array size. <br> .object: the pointer to OH_Drawing_ColorFilter. <br> |
| NODE_IMAGE_AUTO_RESIZE | Defines the auto resize attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32 : whether to resize the image source. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32 : whether to resize the image source. <br> |
| NODE_IMAGE_ALT | Defines the placeholder image source.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: placeholder image source. <br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: placeholder image source. <br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}.<br> |
| NODE_IMAGE_DRAGGABLE | Defines whether the image is draggable.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the image is draggable. The value <b>true</b> means that the image is draggable. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the image is draggable. <br> |
| NODE_IMAGE_RENDER_MODE | Defines the image rendering mode. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode). <br> |
| NODE_IMAGE_FIT_ORIGINAL_SIZE | Defines whether the image display size follows the image source size.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: wheter to follow, true means to follow.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: wheter to follow, true means to follow.<br> |
| NODE_IMAGE_FILL_COLOR | Defines the fill color of the swiper.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: fill color, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: fill color, in 0xARGB format. <br> |
| NODE_IMAGE_RESIZABLE | Resize the image when stretching it with array or a lattice object.The parameter types for setting and getting should be the same.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width of the left edge. The unit is vp. <br> .value[1].f32: width of the top edge. The unit is vp. <br> .value[2].f32: width of the right edge. The unit is vp. <br> .value[3].f32: width of the bottom edge. The unit is vp. <br> .object: The parameter type is {@link OH_Drawing_Lattice},add since api 24.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width of the left edge. The unit is vp. <br> .value[1].f32: width of the top edge. The unit is vp. <br> .value[2].f32: width of the right edge. The unit is vp. <br> .value[3].f32: width of the bottom edge. The unit is vp. <br> .object: The parameter type is {@link OH_Drawing_Lattice},add since api 24.<br> |
| NODE_IMAGE_SYNC_LOAD = 4012 | Defines the synchronous image loading attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to load the image synchronously. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to load the image synchronously. <br><br>**起始版本：** 20 |
| NODE_IMAGE_SOURCE_SIZE = 4013 | Defines the image decoding size attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: width of the image decoding, in px.<br> .value[1].i32: height of the image decoding, in px.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: width of the image decoding, in px.<br> .value[1].i32: height of the image decoding, in px.<br><br>**起始版本：** 21 |
| NODE_IMAGE_IMAGE_MATRIX = 4014 | Support the implementation of affine image transformations using floating-point numbers.This attribute can be set, reset, and obtained as required through APIs.The parameter types for setting and getting should be the same.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0...15].f32: 16 floating-point numbers.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0...15].f32: 16 floating-point numbers.<br><br>**起始版本：** 21 |
| NODE_IMAGE_MATCH_TEXT_DIRECTION = 4015 | Defines the image follow text direction attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to follows the text direction.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to follows the text direction.<br><br>**起始版本：** 21 |
| NODE_IMAGE_COPY_OPTION = 4016 | Defines the image copy attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: copy option [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions). The default value is <b>ARKUI_COPY_OPTIONS_NONE</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: copy option {@link ArkUI_CopyOptions.<br><br>**起始版本：** 21 |
| NODE_IMAGE_ENABLE_ANALYZER = 4017 | Defines the image AI analysis enable attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable AI analysis for the image.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable AI analysis for the image.<br><br>**起始版本：** 21 |
| NODE_IMAGE_DYNAMIC_RANGE_MODE = 4018 | Defines the image dynamic display range attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: dynamic range mode [ArkUI_DynamicRangeMode](capi-native-type-h.md#arkui_dynamicrangemode).The default value is <b>ARKUI_DYNAMIC_RANGE_MODE_STANDARD</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: dynamic range mode {@link ArkUI_DynamicRangeMode.<br><br>**起始版本：** 21 |
| NODE_IMAGE_HDR_BRIGHTNESS = 4019 | Defines the image dynamic display brightness attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: hdr brightness. value range [0, 1]<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: hdr brightness. value range [0, 1]<br><br>**起始版本：** 21 |
| NODE_IMAGE_ORIENTATION = 4020 | Defines the image display direction attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: orientation {@link ArkUI_Orientation}.The default value is <b>ARKUI_ORIENTATION_UP</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: orientation {@link ArkUI_Orientation.<br><br>**起始版本：** 21 |
| NODE_IMAGE_SUPPORT_SVG2 = 4021 | Set the range of SVG parsing capabilities supported through enable switch.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: enable switch.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: enable switch.<br><br>**起始版本：** 21 |
| NODE_IMAGE_CONTENT_TRANSITION = 4022 | Set the animation effect for the image content transformation.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).<br><br>**起始版本：** 21 |
| NODE_IMAGE_ALT_PLACEHOLDER = 4023 | Defines the placeholder image during loading process.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: placeholder image source. <br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: placeholder image source. <br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}.<br><br>**起始版本：** 22 |
| NODE_IMAGE_ALT_ERROR = 4024 | Defines the placeholder image when loading fails.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: placeholder image source. <br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: placeholder image source. <br> .object: The parameter type is {@link ArkUI_DrawableDescriptor}.<br><br>**起始版本：** 22 |
| NODE_IMAGE_ANTIALIASED = 4025 | Configure image edge anti-aliasing via an enable switch.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: enable switch,the default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: enable switch.<br><br>**起始版本：** 23 |
| NODE_TOGGLE_SELECTED_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE | Defines the color of the component when it is selected.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format. <br> |
| NODE_TOGGLE_SWITCH_POINT_COLOR | Defines the color of the circular slider for the component of the switch type.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the circular slider, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the circular slider, in 0xARGB format. <br> |
| NODE_TOGGLE_VALUE | Defines the toggle switch value. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the toggle. The value <b>true</b> means to enable the toggle. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the toggle. <br> |
| NODE_TOGGLE_UNSELECTED_COLOR | Defines the color of the component when it is deselected.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format. <br> |
| NODE_LOADING_PROGRESS_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LOADING_PROGRESS | Defines the foreground color of the loading progress bar.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: foreground color, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: foreground color, in 0xARGB format. <br> |
| NODE_LOADING_PROGRESS_ENABLE_LOADING | Defines whether to show the loading animation for the <LoadingProgress> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show the loading animation.The value <b>true</b> means to show the loading animation, and <b>false</b> means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value <b>1</b> means to show the loading animation, and <b>0</b> means the opposite. <br> |
| NODE_TEXT_INPUT_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT | Defines the default placeholder text of the single-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default placeholder text. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default placeholder text. <br> |
| NODE_TEXT_INPUT_TEXT | Defines the default text content of the single-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default text content. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default text content. <br> |
| NODE_TEXT_INPUT_CARET_COLOR | Defines the caret color attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: caret color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: caret color, in 0xARGB format. <br> |
| NODE_TEXT_INPUT_CARET_STYLE | Defines the caret style attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: caret width, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: caret width, in vp. <br> |
| NODE_TEXT_INPUT_SHOW_UNDERLINE | Defines the underline attribute of the single-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show an underline.The value <b>true</b> means to show an underline, and <b>false</b> means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value <b>1</b> means to show an underline, and <b>0</b> means the opposite. <br> |
| NODE_TEXT_INPUT_MAX_LENGTH | Defines the maximum number of characters in the text input.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: maximum number of characters in the text input, without a unit. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: maximum number of characters in the text input. <br> |
| NODE_TEXT_INPUT_ENTER_KEY_TYPE | Defines the type of the Enter key.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of the Enter key[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype). The default value is <b>ARKUI_ENTER_KEY_TYPE_DONE</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of the Enter key[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype). <br> |
| NODE_TEXT_INPUT_PLACEHOLDER_COLOR | Defines the placeholder text color.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_TEXT_INPUT_PLACEHOLDER_FONT | Defines the placeholder text font.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: font size, in fp. Optional. The default value is <b>16.0</b>.<br> .value[1]?.i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). Optional.The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>. <br> .value[2]?.i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). Optional.The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>. <br> ?.string: font family. Multiple font families are separated by commas (,).Example: "font weight; font family 1, font family 2". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: font size, in fp.<br> .value[1].i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).<br> .value[2].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).<br> .string: font family. Multiple font families are separated by commas (,). <br> |
| NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS | Defines whether to enable the input method when the component obtains focus.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the input method when the component obtains focus.The value <b>true</b> means to enable the input method, and <b>false</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value <b>1</b> means to enable the input method when the component obtains focus,and <b>0</b> means the opposite. <br> |
| NODE_TEXT_INPUT_TYPE | Defines the text box type. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text box type [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype).The default value is <b>ARKUI_TEXTINPUT_TYPE_NORMAL</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text box type [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype). <br> |
| NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR | Defines the background color of the selected text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_TEXT_INPUT_SHOW_PASSWORD_ICON | Defines whether to display the password icon at the end of the password text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to display the password icon at the end of the password text box.The value <b>true</b> means to display the password icon, and <b>false</b> means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value <b>1</b> means to display the password icon at the end of the password text box,and <b>0</b> means the opposite. <br> |
| NODE_TEXT_INPUT_EDITING | Defines the editable state for the single-line text box.This attribute can be set as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].i32: whether to remain in the editable state. The value<b>true</b> means to remain in the editable state, and <b>false</b> means to exit the editable state. <br> <br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for obtaining the attribute:.value[0].i32: whether to remain in the editable state. The value <b>true</b> means to remain in the editablestate, and <b>false</b> means to exit the editable state. <br> |
| NODE_TEXT_INPUT_CANCEL_BUTTON | Defines the style of the cancel button on the right of the single-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].i32: button style [ArkUI_CancelButtonStyle](capi-native-type-h.md#arkui_cancelbuttonstyle).The default value is <b>ARKUI_CANCELBUTTON_STYLE_INPUT</b>.<br> .value[1]?.f32: button icon size, in vp.<br> .value[2]?.u32: button icon color, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> ?.string: button icon image source. The value is the local address of the image, for example, /pages/icon.png. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: button style [ArkUI_CancelButtonStyle](capi-native-type-h.md#arkui_cancelbuttonstyle).<br> .value[1].f32: icon size, in vp.<br> .value[2].u32: button icon color, in 0xARGB format.<br> .string: button icon image source. <br> |
| NODE_TEXT_INPUT_TEXT_SELECTION | Sets the text selection area, which will be highlighted.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. <br> |
| NODE_TEXT_INPUT_UNDERLINE_COLOR | Sets the color of the text underline when it is enabled.The default underline color configured for the theme is <b>'0x33182431'</b>.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the underline applied to the text being typed in.The value is in 0xARGB format. <br> .value[1].u32: color of the underline applied to the text in the normal state.The value is in 0xARGB format. <br> .value[2].u32: color of the underline applied to the text when an error is detected.The value is in 0xARGB format. <br> .value[3].u32: color of the underline applied to the text when it is disabled.The value is in 0xARGB format. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the underline applied to the text being typed in. The value is in 0xARGB format. <br> .value[1].u32: color of the underline applied to the text in the normal state. The value is in 0xARGB format. <br> .value[2].u32: color of the underline applied to the text when an error is detected.The value is in 0xARGB format. <br> .value[3].u32: color of the underline applied to the text when it is disabled. The value is in 0xARGB format. <br> |
| NODE_TEXT_INPUT_ENABLE_AUTO_FILL | Sets whether to enable autofill.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable autofill. The default value is <b>true</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable autofill. <br> |
| NODE_TEXT_INPUT_CONTENT_TYPE | Sets the autofill type.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype). <br> |
| NODE_TEXT_INPUT_PASSWORD_RULES | Defines the rules for generating passwords. When autofill is used, these rules are transparentlytransmitted to Password Vault for generating a new password.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: rules for generating passwords. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: rules for generating passwords. <br> |
| NODE_TEXT_INPUT_SELECT_ALL | Sets whether to select all text in the initial state. The inline mode is not supported.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to select all text in the initial state. The default value is b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to select all text in the initial state. <br> |
| NODE_TEXT_INPUT_INPUT_FILTER | Sets the regular expression for input filtering.Only inputs that comply with the regular expression can be displayed.Other inputs are filtered out. The specified regular expression can match single characters,but not strings.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: regular expression. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: regular expression. <br> |
| NODE_TEXT_INPUT_STYLE | Sets the text box to the default style or inline input style.For the inline input style, only <b>InputType.Normal</b> is supported.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text input style. The parameter type is [ArkUI_TextInputStyle](capi-native-type-h.md#arkui_textinputstyle). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text input style. The parameter type is [ArkUI_TextInputStyle](capi-native-type-h.md#arkui_textinputstyle). <br> |
| NODE_TEXT_INPUT_CARET_OFFSET | Sets or obtains the caret position.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> In the case of setting the caret position:.value[0].i32: character count from the beginning of a string to the caret position. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> In the case of obtaining the caret position: If this API is called when the caret position is updated in thecurrent frame, it will not take effect..value[0].i32: index of the caret position. <br> .value[1].f32: X coordinate of the caret relative to the text box. <br> .value[2].f32: Y coordinate of the caret relative to the text box. |
| NODE_TEXT_INPUT_CONTENT_RECT | Obtains the position of the edited text area relative to the component and its size.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: horizontal coordinate. <br> .value[1].f32: vertical coordinate. <br> .value[2].f32: content width. <br> .value[3].f32: content height. <br> |
| NODE_TEXT_INPUT_CONTENT_LINE_COUNT | Obtains the number of lines of the edited text.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of lines of the edited text. <br> |
| NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN | Sets whether to hide the text selection menu when the text box is long-pressed, double-click, orright-clicked. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-click, orright-clicked. The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-click, orright-clicked. <br> |
| NODE_TEXT_INPUT_BLUR_ON_SUBMIT | Sets whether the text box loses focus after the Enter key is pressed to submit information.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the text box loses focus. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the text box loses focus. <br> |
| NODE_TEXT_INPUT_CUSTOM_KEYBOARD | Set up a custom keyboard.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object：custom keyboard,The parameter type is{@Link ArkUI_NodeHandle}。<br> .value[0]?.i32：Sets whether the custom keyboard supports the avoidance feature, default value false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object:custom keyboard,The parameter type is{@Link ArkUI_NodeHandle}。<br> .value[0].i32：Set whether the custom keyboard supports the avoidance function.<br> |
| NODE_TEXT_INPUT_WORD_BREAK | Defines the line break rule. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak). <br> |
| NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS | Sets whether the keyboard pops up when the input box gains focus.It supports property setting, property reset and property acquisition interfaces.Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:<br> .value[0].i32: Whether to pop up the keyboard. <br> <br> Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .value[0].i32: Whether to pop up the keyboard. <br> |
| NODE_TEXT_INPUT_NUMBER_OF_LINES | When this property is set, the height of the textInput component is calculated using this property.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: set the value of numberOfLines.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: the value of numberOfLines.<br> |
| NODE_TEXT_INPUT_LETTER_SPACING = 7032 | Sets the letter spacing of the <b>TextInput</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: letter spacing. The default unit is fp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: letter spacing. The default unit is fp. <br><br>**起始版本：** 15 |
| NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT = 7033 | Sets whether to enable preview text for the <b>TextInput</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable preview tex. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable preview tex. <br><br>**起始版本：** 15 |
| NODE_TEXT_INPUT_HALF_LEADING = 7034 | Sets whether to center text vertically in the textInput component.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to center text vertically. The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to center text vertically. <br><br>**起始版本：** 18 |
| NODE_TEXT_INPUT_KEYBOARD_APPEARANCE = 7035 | Set the keyboard style of textInputFormat of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32：keyboard style，the parameter type is {@link ArkUI_KeyboardAppearanceType}。<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> .value[0].i32：keyboard style，the parameter type is {@link ArkUI_KeyboardAppearanceType}。<br><br>**起始版本：** 15 |
| NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036 | Set whether to enable the auto fill animation or not.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Whether to enable the auto fill animation.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].i32: Get the flag of whether the auto fill animation is enabled.<br><br>**起始版本：** 20 |
| NODE_TEXT_INPUT_LINE_HEIGHT = 7037 | Set the line height of the input node.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: line height value.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].i32: line height value<br>**起始版本：** 20 |
| NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR = 7038 | Enables selected data detector.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Enable selected text recognition, default value true.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether selected text recognition is enabled.<br><br>**起始版本：** 22 |
| NODE_TEXT_INPUT_SHOW_COUNTER = 7040 | Defines the counter settings. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show a character counter. The value <b>true</b> means to show a character counter. <br> .value[1]?.f32: threshold percentage for displaying the character counter. The character counter is displayedwhen the number of characters that have been entered is greater than the maximum number of characters multipliedby the threshold percentage value. The value range is 1 to 100. If the value is a decimal, it is rounded down. <br> .value[2]?.i32: whether to highlight the border when the number of entered characters reaches the maximum. <br> .object: counter configuration. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show a character counter. <br> .value[1].f32: threshold percentage for displaying the character counter. The character counter is displayedwhen the number of characters that have been entered is greater than the maximum number of characters multipliedby the threshold percentage value. The value range is 1 to 100. <br> .value[2].i32: whether to highlight the border when the number of entered characters reaches the maximum.The default value is <b>true</b>. <br> .object: counter configuration. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md).<br><br>**起始版本：** 22 |
| NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE = 7041 | Used to set or get the text content base controller.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .object: the text content base controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: the text content base controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_ELLIPSIS_MODE = 7042 | Defines the ellipsis position.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode), the default valueis ARKUI_ELLIPSIS_MODE_END. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode). <br> @since 24 |
| 	  NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION = 7043 | Whether to avoid an orphan word on the last line of the paragraph.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:  Whether enable the feature, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The current state of this feature.<br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION = 7044 | Whether to compress punctuation at the beginning of line.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:  Whether enable the feature, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether compress punctuation at the beginning of line.<br><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_INCLUDE_FONT_PADDING = 7045 | Determines whether the layout adds extra padding at the top and bottom to make space for characters.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Enable include the font padding, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether include the font padding.<br><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_FALLBACK_LINE_SPACING = 7046 | Whether to include ascent/descent from fallback fonts to prevent overlapping lines.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:  Whether enable the feature, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether fallback line spacing.<br><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_DIRECTION = 7047 | Writing direction of the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: writing direction of the text. The value is an enum of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: writing direction the text. The value is an enum of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). <br><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE = 7048 | Used to set the selected drag preview style.Format of the {@link Arkui_AttributeItem} parameter for setting the attribute:<br> .object: selected drag preview style configuration.The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br> <br> Format of the return value {@link Arkui_AttributeItem}:<br> .object: selected drag preview style configuration.<br> The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br><br>**起始版本：** 23 |
| NODE_TEXT_INPUT_TEXT_OVERFLOW = 7049 | Defines the textinput textOverflow attribute.which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow). <br> @since 24 |
| NODE_TEXT_INPUT_DECORATION = 7050 | Defines the text decoration style and color for single-line text box.This attribute can be set, reset, and obtained as required through APIs.?.object: Optional. The decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).<br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_LINEAR_GRADIENT = 7051 | Sets a linear gradient effect for text in the single-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: start angle of the linear gradient.The setting takes effect only when <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>.A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>. <br> .value[1].i32: direction of the linear gradient. When a direction other than<b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> is set, the <b>angle</b> property is ignored.The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection). <br> .value[2].i32: whether the colors are repeated. The default value is <b>false</b>..object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: start angle of the linear gradient.When <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>, <b>angle</b> at the set value;otherwise, it is at default value. <br> .value[1].i32: direction of the linear gradient. <br> .value[2].i32: whether the colors are repeated. <br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_RADIAL_GRADIENT = 7052 | Sets a radial gradient effect for text in the single-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3]?.i32: whether the colors are repeated.The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite. <br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[1].f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[2].f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3].i32: whether the colors are repeated.The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.  <br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA | Defines the default placeholder text for the multi-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default placeholder text. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default placeholder text. <br> |
| NODE_TEXT_AREA_TEXT | Defines the default text content for the multi-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default text content. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default text content. <br> |
| NODE_TEXT_AREA_MAX_LENGTH | Defines the maximum number of characters in the text input.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: maximum number of characters in the text input. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: maximum number of characters in the text input. <br> |
| NODE_TEXT_AREA_PLACEHOLDER_COLOR | Defines the placeholder text color.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_TEXT_AREA_PLACEHOLDER_FONT | Defines the placeholder text font.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: font size, in fp. Optional. The default value is <b>16.0</b>.<br> .value[1]?.i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). Optional. The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.<br> .value[2]?.i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). Optional. The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.<br> ?.string: font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: font size, in fp.<br> .value[1].i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).<br> .value[2].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).<br> .string: font family. Multiple font families are separated by commas (,). <br> |
| NODE_TEXT_AREA_CARET_COLOR | Defines the caret color attribute.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format. <br> |
| NODE_TEXT_AREA_EDITING | Defines the editable state for the multi-line text box.This attribute can be set as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to remain in the editable state. The value <b>true</b> means to remain in theeditable state, and <b>false</b> means to exit the editable state. <br> <br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for obtaining the attribute:.value[0].i32: whether to remain in the editable state. The value <b>true</b> means to remain in the editablestate, and <b>false</b> means to exit the editable state. <br> |
| NODE_TEXT_AREA_TYPE | Defines the text box type. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text box type [ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype).The default value is <b>ARKUI_TEXTAREA_TYPE_NORMAL</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text box type [ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype). <br> |
| NODE_TEXT_AREA_SHOW_COUNTER | Defines the counter settings. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show a character counter. The value <b>true</b> means to show a character counter. <br> .value[1]?.f32: threshold percentage for displaying the character counter. The character counter is displayedwhen the number of characters that have been entered is greater than the maximum number of characters multipliedby the threshold percentage value. The value range is 1 to 100. If the value is a decimal, it is rounded down. <br> .value[2]?.i32: whether to highlight the border when the number of entered characters reaches the maximum. <br> .object: counter configuration. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show a character counter. <br> .value[1].f32: threshold percentage for displaying the character counter. The character counter is displayedwhen the number of characters that have been entered is greater than the maximum number of characters multipliedby the threshold percentage value. The value range is 1 to 100. <br> .value[2].i32: whether to highlight the border when the number of entered characters reaches the maximum.The default value is <b>true</b>. <br> .object: counter configuration. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md). <br> |
| NODE_TEXT_AREA_SELECTION_MENU_HIDDEN | Sets whether to hide the text selection menu when the text box is long-pressed, double-click,or right-clicked. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-click,or right-clicked. The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-click,or right-clicked. <br> |
| NODE_TEXT_AREA_BLUR_ON_SUBMIT | Sets whether the multi-line text box loses focus after the Enter key is pressed to submit information.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the text box loses focus. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the text box loses focus. <br> |
| NODE_TEXT_AREA_INPUT_FILTER | Sets the regular expression for input filtering.Only inputs that comply with the regular expression can be displayed.Other inputs are filtered out. The specified regular expression can match single characters,but not strings.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: regular expression. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: regular expression. <br> |
| NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR | Defines the background color of the selected text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_TEXT_AREA_ENTER_KEY_TYPE | Defines the type of the Enter key.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of the Enter key[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype). The default value is <b>ARKUI_ENTER_KEY_TYPE_DONE</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of the Enter key[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype). <br> |
| NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS | Defines whether to enable the input method when the component obtains focus.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the input method when the component obtains focus.The value <b>true</b> means to enable the input method, and <b>false</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value <b>1</b> means to enable the input method when the component obtains focus,and <b>0</b> means the opposite. <br> |
| NODE_TEXT_AREA_CARET_OFFSET | Defines whether to enable the input method when the component obtains focus.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the input method when the component obtains focus.The value <b>true</b> means to enable the input method, and <b>false</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value <b>1</b> means to enable the input method when the component obtains focus,and <b>0</b> means the opposite. <br> |
| NODE_TEXT_AREA_CONTENT_RECT | Obtains the position of the edited text area relative to the component and its size.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: horizontal coordinate. <br> .value[1].f32: vertical coordinate. <br> .value[2].f32: content width. <br> .value[3].f32: content height. <br> |
| NODE_TEXT_AREA_CONTENT_LINE_COUNT | Obtains the number of lines of the edited text.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of lines of the edited text. <br> |
| NODE_TEXT_AREA_TEXT_SELECTION | Sets the text selection area, which will be highlighted.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. <br> |
| NODE_TEXT_AREA_ENABLE_AUTO_FILL | Sets whether to enable autofill.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable autofill. The default value is <b>true</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable autofill. <br> |
| NODE_TEXT_AREA_CONTENT_TYPE | Sets the autofill type.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype). <br> |
| NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS | Sets whether the keyboard pops up when the input box gains focus.It supports property setting, property reset and property acquisition interfaces.Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:<br> .value[0].i32: Whether to pop up the keyboard. <br> <br> Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .value[0].i32: Whether to pop up the keyboard. <br> |
| NODE_TEXT_AREA_NUMBER_OF_LINES | When this property is set, the height of the textArea component is calculated using this property.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: set the value of numberOfLines.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Set the value of numberOfLines<br> |
| NODE_TEXT_AREA_LETTER_SPACING = 8023 | Sets the letter spacing of the <b>TextArea</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: letter spacing. The default unit is fp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: letter spacing. The default unit is fp. <br><br>**起始版本：** 15 |
| NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024 | Sets whether to enable preview text for the <b>TextArea</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable preview tex. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable preview tex. <br><br>**起始版本：** 15 |
| NODE_TEXT_AREA_HALF_LEADING = 8025 | Sets whether to center text vertically in the textArea component.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to center text vertically. The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to center text vertically. <br><br>**起始版本：** 18 |
| NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026 | Set the keyboard style of textAreaFormat of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32：keyboard style，the parameter type is {@link ArkUI_KeyboardAppearanceType}。<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)：<br> .value[0].i32：keyboard style，the parameter type is {@link ArkUI_KeyboardAppearanceType}。<br><br>**起始版本：** 15 |
| NODE_TEXT_AREA_MAX_LINES = 8027 | Set the max lines of the node. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: max lines count.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: max lines count.<br><br>**起始版本：** 20 |
| NODE_TEXT_AREA_LINE_SPACING = 8028 | Set line spacing of the node. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: line spacing value. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: line spacing value. <br><br>**起始版本：** 20 |
| NODE_TEXT_AREA_MIN_LINES = 8029 | Set the min lines of the node. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: min lines count.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].i32: min line count.<br><br>**起始版本：** 20 |
| NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL = 8030 | Set the max lines of the node with scroll.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: max lines count with scroll.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].i32: max line count with scroll.<br><br>**起始版本：** 20 |
| NODE_TEXT_AREA_LINE_HEIGHT = 8031 | Set the line height of the node. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: line height value.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].i32: line height value<br>**起始版本：** 20 |
| NODE_TEXT_AREA_BAR_STATE = 8032 | Define bar state of the text area.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: bar state of the text area, specified using the [ArkUI_BarState](capi-native-type-h.md#arkui_barstate) enum.The default value is <b>ARKUI_BAR_STATE_AUTO</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: bar state of the text area, specified using the [ArkUI_BarState](capi-native-type-h.md#arkui_barstate) enum. <br><br>**起始版本：** 22 |
| NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR = 8033 | Enables selected data detector.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Enable selected text recognition, default value true.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether selected text recognition is enabled.<br><br>**起始版本：** 22 |
| NODE_TEXT_AREA_SCROLL_BAR_COLOR = 8035 | Defines the color of the scrollbar. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .data[0].u32: color of the scroll bar thumb, in 0xARGB format. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .data[0].u32: color of the scroll bar thumb, in 0xARGB format. <br><br>**起始版本：** 22 |
| NODE_TEXT_AREA_CUSTOM_KEYBOARD = 8036 | Sets up a custom keyboard.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: custom keyboard,The parameter type is {@Link ArkUI_NodeHandle}.<br> .value[0]?.i32: Sets whether the custom keyboard supports the avoidance feature, default value false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object:custom keyboard,The parameter type is {@Link ArkUI_NodeHandle}.<br> .value[0].i32: Set whether the custom keyboard supports the avoidance function.<br><br>**起始版本：** 22 |
| NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE = 8037 | Used to set or get the text content base controller.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .object: the text content base controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: the text content base controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br><br>**起始版本：** 23 |
| NODE_TEXT_AREA_ELLIPSIS_MODE = 8038 | Defines the ellipsis position.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode), the default valueis ARKUI_ELLIPSIS_MODE_END. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode). <br> @since 24 |
| NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION = 8039 | Whether to avoid an orphan word on the last line of the paragraph.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:  Whether enable the feature true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The current state of this feature.<br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION = 8040 | Whether to compress punctuation at the beginning of line.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:  Whether enable the feature, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether compress punctuation at the beginning of line.<br><br>**起始版本：** 23 |
| NODE_TEXT_AREA_INCLUDE_FONT_PADDING = 8041 | Determines whether the layout adds extra padding at the top and bottom to make space for characters.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Enable include the font padding, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether include the font padding.<br><br>**起始版本：** 23 |
| NODE_TEXT_AREA_FALLBACK_LINE_SPACING = 8042 | Whether to include ascent/descent from fallback fonts to prevent overlapping lines.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32:  Whether enable the feature, true means enable this feature, false means disable.The default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether fallback line spacing.<br><br>**起始版本：** 23 |
| NODE_TEXT_AREA_HORIZONTAL_SCROLLING = 8043 | Whether to enable horizontal scrolling when text is wider than the view.The default value is false, and text will be wrapped by the view.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Whether enable the feature, true means enable this feature, false means disable. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Whether enable the feature. <br><br>**起始版本：** 24 |
| NODE_TEXT_AREA_DIRECTION = 8044 | Writing direction of the text.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: writing direction of the text. The value is an enum of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: writing direction the text. The value is an enum of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). <br><br>**起始版本：** 23 |
| NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE = 8045 | Used to set the selected drag preview style.Format of the {@link Arkui_AttributeItem} parameter for setting the attribute:<br> .object: selected drag preview style configuration. The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br> <br> Format of the return value {@link Arkui_AttributeItem}:<br> .object: selected drag preview style configuration. The parameter type is {@link Arkui_SelectedDragPreviewStyle}.<br><br>**起始版本：** 23 |
| NODE_TEXT_AREA_TEXT_OVERFLOW = 8046 | Defines the textarea textOverflow attribute.which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow). <br> @since 24 |
| NODE_TEXT_AREA_DECORATION = 8047 | Defines the text decoration style and color for multi-line text box.This attribute can be set, reset, and obtained as required through APIs.?.object: Optional. The decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).<br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_LINEAR_GRADIENT = 8048 | Sets a linear gradient effect for text in the multi-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: start angle of the linear gradient.The setting takes effect only when <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>.A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>. <br> .value[1].i32: direction of the linear gradient. When a direction other than<b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> is set, the <b>angle</b> property is ignored.The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection). <br> .value[2].i32: whether the colors are repeated. The default value is <b>false</b>..object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: start angle of the linear gradient.When <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>, <b>angle</b> at the set value;otherwise, it is at default value. <br> .value[1].i32: direction of the linear gradient. <br> .value[2].i32: whether the colors are repeated. <br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_RADIAL_GRADIENT = 8049 | Sets a radial gradient effect for text in the multi-line text box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3]?.i32: whether the colors are repeated.The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite. <br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[1].f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text. <br> .value[2].f32: radius of the radial gradient. The default value is <b>0</b>. <br> .value[3].i32: whether the colors are repeated.The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.  <br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br><br>**起始版本：** 26.0.0 |
| NODE_BUTTON_LABEL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_BUTTON | Defines the button text content. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default text content. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default text content. <br> |
| NODE_BUTTON_TYPE | Sets the button type. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype).The default value is <b>ARKUI_BUTTON_TYPE_CAPSULE</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype).The default value is <b>ARKUI_BUTTON_TYPE_CAPSULE</b>. <br> |
| NODE_BUTTON_MIN_FONT_SCALE | Defines the minimum font scale attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum font scale, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum font scale, in fp.<br>**起始版本：** 18 |
| NODE_BUTTON_MAX_FONT_SCALE | Defines the maximum font scale attribute, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum font scale, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum font scale, in fp.<br>**起始版本：** 18 |
| NODE_PROGRESS_VALUE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PROGRESS | Defines the current value of the progress indicator.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: current value of the progress indicator. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current value of the progress indicator. <br> |
| NODE_PROGRESS_TOTAL | Defines the total value of the progress indicator.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: total value of the progress indicator. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: total value of the progress indicator. <br> |
| NODE_PROGRESS_COLOR | Defines the color for the progress value on the progress indicator.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format. <br> |
| NODE_PROGRESS_TYPE | Defines the type of the progress indicator.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of the progress indicator [ArkUI_ProgressType](capi-native-type-h.md#arkui_progresstype).The default value is <b>ARKUI_PROGRESS_TYPE_LINEAR</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of the progress indicator [ArkUI_ProgressType](capi-native-type-h.md#arkui_progresstype). <br> |
| NODE_PROGRESS_LINEAR_STYLE | Sets the style of the linear progress indicator.This attribute can be set, reset, and obtained as required through APIs.If the progress indicator type is not linear, it will not take effect.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: Use the [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) object to set the style. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: Use the [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) object to get the style. <br><br>**起始版本：** 15 |
| NODE_CHECKBOX_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX | Defines whether the check box is selected.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the check box is selected.The value <b>1</b> means that the check box is selected, and <b>0</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value <b>1</b> means that the check box is selected, and <b>0</b> means the opposite. <br> |
| NODE_CHECKBOX_SELECT_COLOR | Defines the color of the check box when it is selected.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the check box when it is selected, in 0xARGB format, for example, <b>0xFF1122FF</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the check box when it is selected, in 0xARGB format, for example, <b>0xFF1122FF</b>. |
| NODE_CHECKBOX_UNSELECT_COLOR | Defines the border color of the check box when it is not selected.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>. |
| NODE_CHECKBOX_MARK | Defines the internal icon style of the check box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.<br> .value[1]?.f32: size of the internal mark, in vp. Optional.<br> .value[2]?.f32: stroke width of the internal mark, in vp. Optional. The default value is <b>2</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.<br> .value[1].f32: size of the internal mark, in vp. <br> .value[2].f32: stroke width of the internal mark, in vp. The default value is <b>2</b>. <br> |
| NODE_CHECKBOX_SHAPE | Defines the shape of the check box.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape). |
| NODE_CHECKBOX_NAME | Defines the name of the checkbox.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component name. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component name. <br><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP | Defines the name of the checkbox.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component name. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component name. <br><br>**起始版本：** 15 |
| NODE_XCOMPONENT_ID = MAX_NODE_SCOPE_NUM * ARKUI_NODE_XCOMPONENT | Defines the ID of the <b><XComponent></b> component.This attribute can be set and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component ID. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component ID. <br> |
| NODE_XCOMPONENT_TYPE | Specifies the type of the <b>XComponent</b> component. This attribute is read-only. <br> The type of the <b>XComponent</b> component must be explicitly set during creation using [ARKUI_NODE_XCOMPONENT](capi-native-node-h.md#arkui_nodetype) or [ARKUI_NODE_XCOMPONENT_TEXTURE](capi-native-node-h.md#arkui_nodetype), and cannot be modified afterward. <br> Attempting to change the type through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) will cause rendering exceptions.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type [ArkUI_XComponentType](capi-native-type-h.md#arkui_xcomponenttype). <br> |
| NODE_XCOMPONENT_SURFACE_SIZE | Specifies the size of the <b>XComponent</b> component. This attribute is read-only. <br> Attempting to modify the size through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) will have no effect.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: width, in px. <br> .value[1].u32: height, in px. <br> |
| NODE_XCOMPONENT_SURFACE_RECT | Defines the rectangle information of surface created by the <b><XComponent></b> component.This attribute can be set and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The horizontal offset of the surface relative to XComponent, in pixels. <br> .value[1].i32: The vertical offset of the surface relative to XComponent, in pixels. <br> .value[2].i32: The width of the surface created by XComponent, in pixels. <br> .value[3].i32: The height of the surface created by XComponent, in pixels. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The horizontal offset of the surface relative to XComponent, in pixels. <br> .value[1].i32: The vertical offset of the surface relative to XComponent, in pixels. <br> .value[2].i32: The width of the surface created by XComponent, in pixels. <br> .value[3].i32: The height of the surface created by XComponent, in pixels.<br>**起始版本：** 18 |
| NODE_XCOMPONENT_ENABLE_ANALYZER | Defines whether to enable the AI analyzer for the <b><XComponent></b> component.This attribute can be set and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].i32: The parameter type is 1 or 0.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: The parameter type is 1 or 0.<br>**起始版本：** 18 |
| NODE_DATE_PICKER_LUNAR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER | Defines whether to display the lunar calendar in the date picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to display the lunar calendar in the date picker. The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to display the lunar calendar in the date picker. |
| NODE_DATE_PICKER_START | Defines the start date of the date picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The default value is <b>"1970-1-1"</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date. <br> |
| NODE_DATE_PICKER_END | Defines the end date of the date picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The default value is <b>"2100-12-31"</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date. <br> |
| NODE_DATE_PICKER_SELECTED | Defines the selected date of the date picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The default value is <b>"2024-01-22"</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date. |
| NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE | Defines the font color, font size, and font weight for the top and bottom items in the date picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> |
| NODE_DATE_PICKER_TEXT_STYLE | Defines the font color, font size, and font weight of all items except the top, bottom, and selecteditems in the date picker. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> |
| NODE_DATE_PICKER_SELECTED_TEXT_STYLE | Defines the font color, font size, and font weight of the selected item in the date picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> |
| NODE_DATE_PICKER_MODE = 13007 | Defines the mode of the date picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].i32: the mode. The value is and enum of [ArkUI_DatePickerMode](capi-native-type-h.md#arkui_datepickermode)..<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: the mode. The value is and enum of [ArkUI_DatePickerMode](capi-native-type-h.md#arkui_datepickermode)..<br>**起始版本：** 18 |
| NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK = 13008 | Defines whether haptic feedback.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and<b>false</b> means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: whether to feedback.<br><br>**起始版本：** 18 |
| NODE_DATE_PICKER_CAN_LOOP = 13009 | Defines whether to support scroll looping for the date picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to support scroll looping. The value <b>true</b> means to support scroll looping, and<b>false</b> means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: The value <b>1</b> means to support scroll looping, and <b>0</b> means the opposite. <br><br>**起始版本：** 20 |
|  | Defines the time of the selected item. in the timer picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: time. The default value is the current system time. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: time. |
| NODE_TIME_PICKER_USE_MILITARY_TIME | Defines whether the display time is in 24-hour format.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the display time is in 24-hour format. The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the display time is in 24-hour format. |
| NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE | Defines the font color, font size, and font weight for the top and bottom items in the time picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> |
| NODE_TIME_PICKER_TEXT_STYLE | Defines the font color, font size, and font weight of all items except the top, bottom, and selected itemsin the time picker. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> |
| NODE_TIME_PICKER_SELECTED_TEXT_STYLE | Defines the font color, font size, and font weight of the selected item in the time picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> |
| NODE_TIME_PICKER_START = 14005 | Defines the start time of the time picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: time. The default value is <b>"00:00:00"</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: time. The default value is <b>"00:00:00"</b>.<br><br>**起始版本：** 18 |
| NODE_TIME_PICKER_END = 14006 | Defines the end time of the time picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: time. The default value is <b>"23:59:59"</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: time. The default value is <b>"23:59:59"</b>.<br><br>**起始版本：** 18 |
| NODE_TIME_PICKER_ENABLE_CASCADE = 14007 | Defines whether the AM/PM option is cascaded with the time in 12-hour mode.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable cascade. The default value is <b>false</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable cascade.<br><br>**起始版本：** 18 |
| NODE_TEXT_PICKER_OPTION_RANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER | Defines the data selection range of the text picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of the text picker [ArkUI_TextPickerRangeType](capi-native-type-h.md#arkui_textpickerrangetype).The default value is <b>ARKUI_TEXTPICKER_RANGETYPE_SINGLE</b>. <br> ?.string: string input, whose format varies by picker type.<br> 1: single-column picker. The input format is a group of strings separated by semicolons (;).<br> 2: multi-column picker. Multiple pairs of plain text strings are supported. The pairs are separated bysemicolons (;), and strings within each pair are separated by commas (,). <br> ?.object: Object input, whose format varies by picker type.<br> 1: single-column picker with image support. The input structure is [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md).<br> 2: multi-column interconnected picker. The input structure is [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md).<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of the text picker [ArkUI_TextPickerRangeType](capi-native-type-h.md#arkui_textpickerrangetype).<br> ?.string: string output, whose format varies by picker type.<br> 1: single-column picker. The output format is a group of strings separated by semicolons (;).<br> 2: multi-column picker. Multiple pairs of plain text strings are supported. The pairs are separated bysemicolons (;), and strings within each pair are separated by commas (,). <br> ?.string: Object output, whose format varies by picker type.<br> 1: single-column picker with image support. The output structure is [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md).<br> 2: multi-column interconnected picker. The output structure is [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md).<br> |
| NODE_TEXT_PICKER_OPTION_SELECTED | Defines the index of the default selected item in the data selection range of the text picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: index. If there are multiple index values, add them one by one. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: index. If there are multiple index values, add them one by one.<br> |
| NODE_TEXT_PICKER_OPTION_VALUE | Defines the value of the default selected item in the text picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: value of the selected item. If there are multiple values, add them one by one andseparate them with semicolons (;). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: value of the selected item. If there are multiple values, add them one by one andseparate them with semicolons (;).<br> |
| NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE | Defines the font color, font size, and font weight for the top and bottom items in the text picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> |
| NODE_TEXT_PICKER_TEXT_STYLE | Defines the font color, font size, and font weight for all items except the top, bottom, and selecteditems in the text picker. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> |
| NODE_TEXT_PICKER_SELECTED_TEXT_STYLE | Defines the font color, font size, and font weight for the selected item in the text picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: array of five parameters of the string type, separated by semicolons (;).<br> Parameter 1: font color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular")..Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal". <br> |
| NODE_TEXT_PICKER_SELECTED_INDEX | Defines the index of the default selected item in the data selection range of the text picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0...].i32: index of the default item in the data selection range. |
| NODE_TEXT_PICKER_CAN_LOOP | Defines whether to support scroll looping for the text picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to support scroll looping. The value <b>true</b> means to support scroll looping, and<b>false</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: The value <b>1</b> means to support scroll looping, and <b>0</b> means the opposite. <br> |
| NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT | Defines the height of each item in the picker. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: item height, in vp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: item height, in vp. <br> |
| NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK = 15010 | Defines whether haptic feedback.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and<b>false</b> means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: whether to feedback.<br><br>**起始版本：** 18 |
| NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE = 15011 | Defines the background color and border radius of the selected items.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>. <br> 1: .value[1].f32: radius of the four corners. <br> 2: .value[1].f32: radius of the upper left corner. <br> .value[2].f32: radius of the upper right corner. <br> .value[3].f32: radius of the lower left corner. <br> .value[4].f32: radius of the lower right corner. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>. .value[1].f32: radius of the upper left corner. <br> .value[2].f32: radius of the upper right corner. <br> .value[3].f32: radius of the lower left corner. <br> .value[4].f32: radius of the lower right corner. <br><br>**起始版本：** 20 |
| NODE_CALENDAR_PICKER_HINT_RADIUS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER | Defines the style of the background in the selected state of the calendar picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: style of the background in the selected state of the calendar picker.The value range is [0, +∞). If the value is <b>0</b>, the background is a rectangle with square corners.     If the value is in the 0–16 range, the background is a rectangle with rounded corners. If the value is equal toor greater than 16, the background is a circle. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: style of the background in the selected state of the calendar picker. The value range is [0, +∞).If the value is <b>0</b>, the background is a rectangle with square corners.     If the value is in the 0–16 range, the background is a rectangle with rounded corners. If the value is equal to orgreater than 16, the background is a circle. <br> |
| NODE_CALENDAR_PICKER_SELECTED_DATE | Defines the date of the selected item in the calendar picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: year of the selected date. <br> .value[1].u32: month of the selected date. <br> .value[2].u32: day of the selected date. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: year of the selected date. <br> .value[1].u32: month of the selected date. <br> .value[2].u32: day of the selected date. <br> |
| NODE_CALENDAR_PICKER_EDGE_ALIGNMENT | Defines how the calendar picker is aligned with the entry component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-native-type-h.md#arkui_calendaralignment). <br> .value[1]?.f32: offset of the picker relative to the entry component along the x-axis after alignment based onthe specified alignment mode. <br> .value[2]?.f32: offset of the picker relative to the entry component along the y-axis after alignment based onthe specified alignment mode. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-native-type-h.md#arkui_calendaralignment). <br> .value[1]?.f32: offset of the picker relative to the entry component along the x-axis after alignment based onthe specified alignment mode. <br> .value[2]?.f32: offset of the picker relative to the entry component along the y-axis after alignment based onthe specified alignment mode. <br> |
| NODE_CALENDAR_PICKER_TEXT_STYLE | Defines the font color, font size, and font weight in the entry area of the calendar picker.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.u32: font color of the entry area. <br> .value[1]?.f32: font size of the entry area, in fp. <br> .value[2]?.i32: font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: font color of the entry area. <br> .value[1].f32: font size of the entry area, in fp. <br> .value[2].i32: font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). <br> |
| NODE_CALENDAR_PICKER_START = 16004 | Defines the start date of the calendar picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The value like <b>"1970-1-1"</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date. <br><br>**起始版本：** 18 |
| NODE_CALENDAR_PICKER_END = 16005 | Defines the end date of the calendar picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The value like <b>"2100-12-31"</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date. <br><br>**起始版本：** 18 |
| NODE_SLIDER_BLOCK_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER | Defines the color of the slider. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the slider, in 0xARGB format, for example, <b>0xFF1122FF</b>.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the slider, in 0xARGB format, for example, <b>0xFF1122FF</b>. |
| NODE_SLIDER_TRACK_COLOR | Defines the background color of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>. |
| NODE_SLIDER_SELECTED_COLOR | Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtainedas required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, <b>0xFF1122FF</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, <b>0xFF1122FF</b>. |
| NODE_SLIDER_SHOW_STEPS | Sets whether to display the stepping value. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to display the stepping value. The value <b>1</b> means to display the stepping value,and <b>0</b> (default value) means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to display the stepping value. The value <b>1</b> means to display the stepping value,and <b>0</b> (default value) means the opposite. <br> |
| NODE_SLIDER_BLOCK_STYLE | Defines the slider shape, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle). <br> .string?: depending on the shape. Optional. <br> ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png. <br> ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider. <br> There are five types:<br> 1. Rectangle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape.<br> .value[2].f32: width of the rectangle.<br> .value[3].f32: height of the rectangle.<br> .value[4].f32: width of the rounded corner of the rectangle.<br> .value[5].f32: height of the rounded corner of the rectangle.<br> 2. Circle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape.<br> .value[2].f32: width of the circle.<br> .value[3].f32: height of the circle.<br> 3.Ellipse:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[2].f32: width of the ellipse.<br> .value[3].f32: height of the ellipse;<br> 4. Path:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape.<br> .value[2].f32: width of the path.<br> .value[3].f32: height of the path.<br> .string: command for drawing the path.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle). <br> .string?: depending on the shape. Optional. <br> ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png. <br> ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider. <br> There are five types:<br> 1. Rectangle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape.<br> .value[2].f32: width of the rectangle.<br> .value[3].f32: height of the rectangle.<br> .value[4].f32: width of the rounded corner of the rectangle.<br> .value[5].f32: height of the rounded corner of the rectangle.<br> 2. Circle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape.<br> .value[2].f32: width of the circle.<br> .value[3].f32: height of the circle.<br> 3.Ellipse:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape.<br> .value[2].f32: width of the ellipse.<br> .value[3].f32: height of the ellipse;<br> 4. Path:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype).The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape.<br> .value[2].f32: width of the path.<br> .value[3].f32: height of the path.<br> .string: command for drawing the path.<br> |
| NODE_SLIDER_VALUE | Defines the current value of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: current value. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current value. |
| NODE_SLIDER_MIN_VALUE | Defines the minimum value of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum value. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum value. |
| NODE_SLIDER_MAX_VALUE | Defines the maximum value of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum value. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum value. |
| NODE_SLIDER_STEP | Defines the step of the slider. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: step. The value range is [0.01, 100]. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: step. The value range is [0.01, 100]. |
| NODE_SLIDER_DIRECTION | Defines whether the slider moves horizontally or vertically. This attribute can be set, reset, andobtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the slider moves horizontally or vertically.The parameter type is [ArkUI_SliderDirection](capi-slider-h.md#arkui_sliderdirection). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the slider moves horizontally or vertically. |
| NODE_SLIDER_REVERSE | Defines whether the slider values are reversed. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the slider values are reversed. The value <b>1</b> means that the slider values arereversed, and <b>0</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the slider values are reversed. The value <b>1</b> means that the slider values arereversed, and <b>0</b> means the opposite. |
| NODE_SLIDER_STYLE | Defines the style of the slider thumb and track. This attribute can be set, reset, and obtainedas required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: style of the slider thumb and track. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: style of the slider thumb and track. The parameter type is [ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle). |
| NODE_SLIDER_TRACK_THICKNESS | Sets the track thickness of the slider.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: track thickness of the slider, in vp. The default value is 4.0 vp when <b>NODE_SLIDER_STYLE</b>is set to <b>ARKUI_SLIDER_STYLE_OUT_SET</b> and 20.0 vp when <b>NODE_SLIDER_STYLE</b> is set to<b>ARKUI_SLIDER_STYLE_IN_SET</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: track thickness of the slider, in vp. <br> |
| NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013 | Defines whether haptic feedback.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and<b>false</b> means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: whether to feedback.<br> When enabling haptic feedback, you need to add "ohos.permission.VIBRATE" in therequestPermissions field of the module.json5 file to enable vibration permission.<br><br>**起始版本：** 18 |
| NODE_SLIDER_PREFIX | Sets a custom component on the leading side of the Slider component.Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter format:<br> .object: Parameter type [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).The prefix component will be placed at the start position of the Slider，typically on the left side in LTR layouts.	 *	<br>**起始版本：** 20 |
| NODE_SLIDER_SUFFIX | Sets a custom component on the trailing side of the Slider component.Attribute setting method {@link link ArkUI_AttributeItem} parameter format:<br> .object: Parameter type [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).The suffix component will be placed at the end position of the Slider,typically on the right side in LTR layouts.	 *	<br>**起始版本：** 20 |
| NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR | Defines the color of the slider block. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br><br>**起始版本：** 21 |
| NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR | Defines the background color of the slider. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br><br>**起始版本：** 21 |
| NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR | Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtainedas required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: array of color stops, each of which consists of a color and its stop position.The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped.  <br> colors: colors of the color stops. <br> stops: stop positions of the color stops. <br> size: number of colors. <br><br>**起始版本：** 21 |
| NODE_RADIO_CHECKED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO | Set the selection status of an option button. Attribute setting,attribute resetting, and attribute obtaining are supported.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .value[0].i32: check status of an option button. The default value is false.Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:<br> .value[0].i32: selection status of an option button. |
| NODE_RADIO_STYLE | Set the styles of the selected and deselected states of the option button.The attribute setting, attribute resetting, and attribute obtaining are supported.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .value[0]?. u32: color of the mother board in enabled state. <br> The type is 0xARGB, and the default value is 0xFF007DFF. <br> .value[1]?. u32: stroke color in the close state. The type is 0xARGB, <br> and the default value is 0xFF182431. <br> .value[2]?. u32: color of the internal round pie in the enabled state. <br> The type is 0xARGB, and the default value is 0xFFFFFFFF. <br> Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:<br> .value[0]. u32: color of the mother board in enabled state. <br> The type is 0xARGB, and the default value is 0xFF007DFF. <br> .value[1]. u32: stroke color in the close state. The type is 0xARGB, <br> and the default value is 0xFF182431. <br> .value[2]. u32: color of the internal round pie in the enabled state. <br> The type is 0xARGB, and the default value is 0xFFFFFFF. |
| NODE_RADIO_VALUE | Sets the value of the current radio.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .string: radio value.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: radio value.<br> |
| NODE_RADIO_GROUP | Set the group name of the current Radio group, only one radio of the same group can be selected.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .string: name of the group to which the current option box belongs.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: name of the group to which the current option box belongs.<br> |
| NODE_IMAGE_ANIMATOR_IMAGES = ARKUI_NODE_IMAGE_ANIMATOR * MAX_NODE_SCOPE_NUM | Set the image frames for the image animator. Dynamic updates is not supported.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .size: number of the images.<br> .object: array of the images, the type is {@ArkUI_ImageAnimatorFrameInfo} array.<br> <br> Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:<br> .size: number of the images.<br> .object: array of the images, the type is {@ArkUI_ImageAnimatorFrameInfo} array.<br> |
| NODE_IMAGE_ANIMATOR_STATE = 19001 | Set the playback status of the animation for the image animator.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .value[0].i32: the playback status of the animation, the type is [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus),and the default value is ARKUI_ANIMATION_STATUS_INITIAL.Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:<br> .value[0].i32: the playback status of the animation, the type is [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus).<br> |
| NODE_IMAGE_ANIMATOR_DURATION = 19002 | Set the playback duration for the image animator. When the duration is 0, no image is played.The value change takes effect only at the beginning of the next cycle.When a separate duration is set in images, the setting of this attribute is invalid.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .value[0].i32: the playback duration, the unit is ms and the default value is 1000.<br>     Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:<br> .value[0].i32: the playback duration, the unit is ms.<br> |
| NODE_IMAGE_ANIMATOR_REVERSE = 19003 | Set the playback direction for the image animator.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .value[0].i32: the playback direction. 0 indicates that images are played from the first one to the last one,and 1 indicates that images are played from the last one to the first one.<br>     Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:<br> .value[0].i32: the playback direction. 0 indicates that images are played from the first one to the last one,and 1 indicates that images are played from the last one to the first one.<br> |
| NODE_IMAGE_ANIMATOR_FIXED_SIZE = 19004 | Set whether the image size is the same as the component size.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .value[0].i32: whether the image size is the same as the component size.1 indicates the image size is the same as the component size.In this case, the width, height, top, and left attributes of the image are invalid.0 indicates the image size is customized.The width, height, top, and left attributes of each image must be set separately.Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:<br> .value[0].i32: whether the image size is the same as the component size.1 indicates the image size is the same as the component size.0 indicates the image size is customized. |
| NODE_IMAGE_ANIMATOR_FILL_MODE = 19005 | Set the status before and after execution of the animation in the current playback direction.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .value[0].i32: the status before and after execution of the animation in the current playback direction,the type is {ArkUI_AnimationFillMode} and the default value is ARKUI_ANIMATION_FILL_MODE_FORWARDS.<br>     Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:<br> .value[0].i32: the status before and after execution of the animation in the current playback direction,the type is {ArkUI_AnimationFillMode}. |
| NODE_IMAGE_ANIMATOR_ITERATION = 19006 | Set the number of times that the animation is played.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .value[0].i32: the number of times that the animation is played.<br>     Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:<br> .value[0].i32: the number of times that the animation is played.<br> |
| NODE_CHECKBOX_GROUP_NAME  = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP | Defines the name of the checkboxgroup.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component name. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component name. <br><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_SELECT_ALL | Defines whether the checkboxgroup is selected.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the checkboxgroup is selected.The value <b>1</b> means that the checkboxgroup is selected, and <b>0</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value <b>1</b> means that the checkboxgroup is selected, and <b>0</b> means the opposite. <br><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_SELECTED_COLOR | Defines the color of the checkboxgroup when it is selected.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the checkboxgroup when it is selected, in 0xARGB format,for example, <b>0xFF1122FF</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the checkboxgroup when it is selected, in 0xARGB format, for example, <b>0xFF1122FF</b>.<br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_UNSELECTED_COLOR | Defines the border color of the checkboxgroup when it is not selected.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.<br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_MARK | Defines the internal icon style of the checkboxgroup.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.<br> .value[1]?.f32: size of the internal mark, in vp. Optional.<br> .value[2]?.f32: stroke width of the internal mark, in vp. Optional. The default value is <b>2</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.<br> .value[1].f32: size of the internal mark, in vp. <br> .value[2].f32: stroke width of the internal mark, in vp. The default value is <b>2</b>. <br><br>**起始版本：** 15 |
| NODE_CHECKBOX_GROUP_SHAPE | Defines the shape of the checkboxgroup.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).<br>**起始版本：** 15 |
| NODE_TEXT_EDITOR_ENTER_KEY_TYPE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR | TextEditor组件回车键类型，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：回车键类型，参数类型[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_NEW_LINE。<br>*返回：<br>.value[0].i32：回车键类型，参数类型[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_CARET_COLOR | TextEditor组件光标颜色，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].u32：光标颜色，采用0xARGB格式，例如0xFFFF0000表示红色。<br>*返回：<br>.value[0].u32：光标颜色，采用0xARGB格式。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_SCROLL_BAR_COLOR | TextEditor组件滚动条颜色，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.data[0].u32：滚动条颜色，采用0xARGB格式。<br>*返回：<br>.data[0].u32：滚动条颜色，采用0xARGB格式。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_BAR_STATE | TextEditor组件滚动条显示模式，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：文本区域的滚动条显示模式，参数类型[ArkUI_BarState](capi-native-type-h.md#arkui_barstate)，默认值为ARKUI_BAR_STATE_AUTO。<br>*返回：<br>.value[0].i32：文本区域的滚动条显示模式，参数类型[ArkUI_BarState](capi-native-type-h.md#arkui_barstate)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR | TextEditor组件文本实体识别功能开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用文本实体识别功能，0表示禁用，1表示启用，默认值为0。<br>*返回：<br>.value[0].i32：是否启用了文本实体识别功能。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG | TextEditor组件识别配置，支持属性设置和属性重置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：识别配置，参数类型{@link ArkUI_TextDataDetectorConfig}。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS | TextEditor组件扩展菜单选项，支持属性设置和属性重置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：扩展菜单选项，参数类型[ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_PLACEHOLDER | TextEditor组件无输入时的提示文本选项，支持属性设置和属性重置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：无输入时的提示文本选项，参数类型{@link ArkUI_TextEditorPlaceholderOptions}。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER | TextEditor组件属性字符串控制器，支持属性设置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：属性字符串控制器，参数类型{@link ArkUI_TextEditorStyledStringController}。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT | TextEditor组件预上屏功能开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用预上屏功能，0表示禁用，1表示启用，默认值为1。<br>*返回：<br>.value[0].i32：是否启用预上屏功能，0表示禁用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_LAYOUT_MANAGER | TextEditor组件TextLayoutManager获取，支持属性获取。<br>作为属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*返回：<br>.object：布局管理器，参数类型{@link ArkUI_TextLayoutManager}。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR | TextEditor组件文本选择识别AI菜单开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用文本选择识别的AI菜单，0表示禁用，1表示启用，默认值为1。<br>*返回：<br>.value[0].i32：是否启用了文本选择识别的AI菜单。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR | TextEditor组件选中内容背景颜色，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.data[0].u32：选中内容的背景颜色，采用0xARGB格式。<br>*返回：<br>.data[0].u32：选中内容的背景颜色，采用0xARGB格式。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS | TextEditor组件非点击获焦时拉起输入法开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：非点击获焦时是否拉起输入法，0表示不拉起，1表示拉起，默认值为1。<br>*返回：<br>.value[0].i32：非点击获焦时是否拉起输入法，0表示不拉起，1表示拉起。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_MAX_LENGTH | TextEditor组件最大字符数，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：最大字符数。<br>*返回：<br>.value[0].i32：最大字符数。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_MAX_LINES | TextEditor组件内容最大行数，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：文本编辑器中内容的最大行数。<br>*返回：<br>.value[0].i32：文本编辑器中内容的最大行数。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK | TextEditor组件触觉反馈开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否在文本编辑器中启用触觉反馈，0表示不启用，1表示启用，默认值为1。<br>*返回：<br>.value[0].i32：是否启用了触觉反馈，0表示不启用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_COPY_OPTIONS | TextEditor组件复制选项，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：复制选项，参数类型[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)，默认值为ARKUI_COPY_OPTIONS_LOCAL_DEVICE。<br>*返回：<br>.value[0].i32：复制选项，参数类型[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE | TextEditor组件键盘外观，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：键盘外观，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)，默认值为ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE。<br>*返回：<br>.value[0].i32：键盘外观，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_STOP_BACK_PRESS | TextEditor组件是否阻止返回事件传播，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否阻止返回事件传播，0表示不阻止，1表示阻止，默认值为0。<br>*返回：<br>.value[0].i32：是否阻止返回事件传播，0表示不阻止，1表示阻止。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING | TextEditor组件中西文自动间距开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用自动间距，0表示不启用，1表示启用，默认值为0。<br>*返回：<br>.value[0].i32：是否启用自动间距，0表示不启用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_CUSTOM_KEYBOARD | TextEditor组件自定义键盘，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。<br>.value[0]?.i32：设置自定义键盘是否支持避让功能，0表示不支持，1表示支持，默认值为0。<br>*返回：<br>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。<br>.value[0].i32：设置自定义键盘是否支持避让功能，0表示不支持，1表示支持。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_BIND_SELECTION_MENU | TextEditor组件自定义文本选择菜单绑定，支持属性设置和属性重置。<br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：文本选择菜单，参数类型{@link ArkUI_TextEditorSelectionMenuOptions}。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING | TextEditor组件首行末行防截断间距开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否添加间距，0表示不添加，1表示添加，默认值为0。<br>*返回：<br>.value[0].i32：是否添加间距，0表示不添加，1表示添加。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING | TextEditor组件行高自适应开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：行高是否自适应，0表示不自适应，1表示自适应，默认值为0。<br>*返回：<br>.value[0].i32：行高是否自适应，0表示不自适应，1表示自适应。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION | TextEditor组件行首标点符号压缩开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用标点符号压缩，0表示不启用，1表示启用，默认值为0。<br>*返回：<br>.value[0].i32：是否启用标点符号压缩，0表示不启用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE | TextEditor组件选中拖拽预览样式，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.object：选中拖拽预览样式配置，参数类型[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。<br>*返回：<br>.object：选中拖拽预览样式配置，参数类型[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_SINGLE_LINE | TextEditor组件单行模式开关，支持属性设置、属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用单行模式，0表示不启用，1表示启用，默认值为0。<br>*返回：<br>.value[0].i32：是否启用单行模式，0表示不启用，1表示启用。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION | 设置TextEditor文本排版时是否使能孤字优化，设置后，通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局。使能后，它会调整换行点以尽可能避免孤立字符。孤字优化特性需在[ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否使能，1表示使能，0表示不使能。默认值为0。<br>*返回：<br>.value[0].i32：是否使能孤字优化。<br>**起始版本：** 26.0.0 |
| NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING | 设置TextEditor组件在文本宽度超过内容区宽度时是否启用水平滚动，支持属性设置，属性重置和属性获取。<br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>*参数：<br>.value[0].i32：是否启用水平滚动。1表示启用水平滚动，0表示不启用水平滚动。默认值为0。<br>*返回：<br>.value[0].i32：是否启用水平滚动。<br>**起始版本：** 26.0.0 |
| NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW | Sets whether to enable punctuation overflow at the end of a line.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable punctuation overflow, the default value is false.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable punctuation overflow.<br><br>**起始版本：** 26.0.0 |
| NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK | Defines the alignment mode of the child components in the container. This attribute can be set, reset,and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment).The default value is <b>ARKUI_ALIGNMENT_CENTER</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). <br> |
| NODE_SCROLL_BAR_DISPLAY_MODE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SCROLL | Defines the scrollbar status. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: scrollbar status. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-native-type-h.md#arkui_scrollbardisplaymode). The default value is<b>ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO</b> for the <b>List</b>, <b>Grid</b>, and <b>Scroll</b> components, and<b>ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF</b> for the <b>WaterFlow</b> component. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: scrollbar status. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-native-type-h.md#arkui_scrollbardisplaymode). <br> |
| NODE_SCROLL_BAR_WIDTH | Defines the width of the scrollbar. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width of the scrollbar, in vp. The default value is <b>4</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width of the scrollbar, in vp. <br> |
| NODE_SCROLL_BAR_COLOR | Defines the color of the scrollbar. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .data[0].u32: color of the scrollbar, in 0xARGB format. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .data[0].u32: color of the scrollbar, in 0xARGB format. <br> |
| NODE_SCROLL_SCROLL_DIRECTION | Defines the scroll direction. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: scroll direction. The parameter type is [ArkUI_ScrollDirection](capi-native-type-h.md#arkui_scrolldirection).The default value is <b>ARKUI_SCROLL_DIRECTION_VERTICAL</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: scroll direction. The parameter type is [ArkUI_ScrollDirection](capi-native-type-h.md#arkui_scrolldirection). <br> |
| NODE_SCROLL_EDGE_EFFECT | Defines the effect used at the edges of the component when the boundary of the scrollable content isreached. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached.The parameter type is [ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect). The default value is <b>ARKUI_EDGE_EFFECT_NONE</b>.<br> .value[1]?.i32: whether to enable the scroll effect when the component content size is smaller than thecomponent itself. Optional. The value <b>1</b> means to enable the scroll effect, and <b>0</b> means theopposite. The default value for the List/Grid/WaterFlow component is <b>0</b>, and the default value for theScroll component is <b>1</b>. <br> .value[2]?.i32: direction in which the effect takes effect. The parameter type is [ArkUI_EffectEdge](capi-native-type-h.md#arkui_effectedge).The default value is <b>ARKUI_EFFECT_EDGE_START \| ARKUI_EFFECT_EDGE_END</b>. This parameter is supported sinceAPI version 16. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached.The parameter type is [ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect). <br> .value[1].i32: whether to enable the scroll effect when the component content size is smaller than the componentitself. Optional. The value <b>1</b> means to enable the scroll effect, and <b>0</b> means the opposite. <br> .value[2].i32: edge for which the effect takes effect when the boundary of the scrollable content is reached.The parameter type is [ArkUI_EffectEdge](capi-native-type-h.md#arkui_effectedge). This parameter is supported since API version 16. <br> |
| NODE_SCROLL_ENABLE_SCROLL_INTERACTION | Defines whether to support scroll gestures. When this attribute is set to <b>false</b>, scrolling byfinger or mouse is not supported, but the scroll controller API is not affected.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to support scroll gestures. The default value is <b>true</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to support scroll gestures. <br> |
| NODE_SCROLL_FRICTION | Defines the friction coefficient. It applies only to gestures in the scrolling area, and it affects onlyindirectly the scroll chaining during the inertial scrolling process.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: friction coefficient. The default value is <b>0.6</b> for non-wearable devices and <b>0.9</b>for wearable devices. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: friction coefficient. |
| NODE_SCROLL_SNAP | Defines the scroll snapping mode. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode for the scroll snap position. The parameter type is [ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign).The default value is <b>ARKUI_SCROLL_SNAP_ALIGN_NONE</b>.<br> .value[1].i32: whether to enable the snap to start feature. When scroll snapping is defined for the<b><Scroll></b> component, setting this attribute to <b>false</b> enables the component to scroll between thestart edge and the first snap point. The default value is <b>true</b>. It is valid only when there are multiplesnap points.<br> .value[2].i32: Whether to enable the snap to end feature. When scroll snapping is defined for the<b><Scroll></b> component, setting this attribute to <b>false</b> enables the component to scroll between theend edge and the last snap point. The default value is <b>true</b>. It is valid only when there are multiplesnap points.<br> .value[3...].f32: snap points for the <b><Scroll></b> component. Each snap point defines the offset from anedge to which the <b><Scroll></b> component can scroll.  <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode for the scroll snap position. The parameter type is [ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign).<br> .value[1].i32: whether to enable the snap to start feature. When scroll snapping is defined for the<b><Scroll></b> component, setting this attribute to <b>false</b> enables the component to scroll between thestart edge and the first snap point.<br> .value[2].i32: Whether to enable the snap to end feature. When scroll snapping is defined for the<b><Scroll></b> component, setting this attribute to <b>false</b> enables the component to scroll between theend edge and the last snap point.<br> .value[3...].f32: snap points for the <b><Scroll></b> component. Each snap point defines the offset from an edgeto which the <b><Scroll></b> component can scroll. <br> |
| NODE_SCROLL_NESTED_SCROLL | Defines the nested scrolling options. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: nested scrolling option when the component scrolls forward.The parameter type is [ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode). <br> .value[1].i32: nested scrolling option when the component scrolls backward.The parameter type is [ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: nested scrolling option when the component scrolls forward.The parameter type is [ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode). <br> .value[1].i32: nested scrolling option when the component scrolls backward.The parameter type is [ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode). |
| NODE_SCROLL_OFFSET | Defines the specified position to scroll to. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: horizontal scrolling offset, in vp. <br> .value[1].f32: vertical scrolling offset, in vp. <br> .value[2]?.i32: scrolling duration, in milliseconds. Optional. <br> .value[3]?.i32: scrolling curve. Optional. The parameter type is [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).The default value is <b>ARKUI_CURVE_EASE</b>. <br> .value[4]?.i32: whether to enable the default spring animation. Optional.The default value <b>0</b> means not to enable the default spring animation. <br> .value[5]?.i32: whether to convert the scroll animation to an overshoot animation when the boundary is reached.Optional. <br> .value[6]?.i32: whether the component can stop at an overscrolled position.This parameter is supported since API version 20. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: horizontal scrolling offset, in vp. <br> .value[1].f32: vertical scrolling offset, in vp. <br> |
| NODE_SCROLL_EDGE | Defines the edge position to scroll to. This attribute can be set and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: edge position to scroll to. The parameter type is [ArkUI_ScrollEdge](capi-native-type-h.md#arkui_scrolledge). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the container at the edge position. The value <b>-1</b> means that the container is notat the edge position. If the container is at the edge position, the parameter type is [ArkUI_ScrollEdge](capi-native-type-h.md#arkui_scrolledge). |
| NODE_SCROLL_ENABLE_PAGING | Defines whether to enable the swipe-to-turn-pages feature. This attribute can be set, reset, and obtainedas required through APIs.If both <b>enablePaging</b> and <b>scrollSnap</b> are set, <b>scrollSnap</b> takes effect, but<b>enablePaging</b> does not. <br> <br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the swipe-to-turn-pages feature. The default value is <b>false</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the swipe-to-turn-pages feature. <br> |
| NODE_SCROLL_PAGE | Scroll to the next or previous page.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32 Indicates whether to scroll to next page. Value 0 indicates scroll to next page and value 1indicates scroll to previous page. <br> .value[1]?.i32 Indicates whether to enable animation. Value 1 indicates enable and 0 indicates disable. <br> |
| NODE_SCROLL_BY | Scroll a specified distance.List/Scroll/WaterFlow support since API version 12, Grid support since API version 26.0.0.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32：Horizontal scrolling distance in vp; <br> .value[1].f32: Vertical scrolling distance in vp; <br> |
| NODE_SCROLL_FLING | Performs inertial scrolling based on the initial velocity passed in.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: Initial velocity of inertial scrolling. Unit: vp/s. If the value specified is 0, it isconsidered as invalid, and the scrolling for this instance will not take effect. If the value is positive,the scroll will move downward; if the value is negative, the scroll will move upward. <br><br>**起始版本：** 13 |
| NODE_SCROLL_FADING_EDGE | Sets the fading effect for the edges of scrollable components.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:.value[0].i32: whether to enable the fading effect on edges. The value 0 means to disable the fading effect,and 1 means to enable it..value[1]?.f32: length of the fading effect on edges, in vp. Default value: 32.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):.value[0].i32: whether the fading effect on edges is enabled. The value 0 means that the fading effect isdisabled, and 1 means that it is enabled..value[1].f32: length of the fading effect on edges, in vp.<br>**起始版本：** 14 |
| NODE_SCROLL_SIZE | Obtains the total size of all child components when fully expanded in the scrollable component.Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: total width of all child components when fully expanded in the scrollable component.The default unit is vp. <br> .value[1].f32: total height of all child components when fully expanded in the scrollable component.The default unit is vp. <br> When <b>NODE_PADDING</b>, <b>NODE_MARGIN</b>, or <b>NODE_BORDER_WIDTH</b> is set, the values are rounded to thenearest pixel when being converted from vp to px.The returned values are calculated based on these rounded pixel values. <br><br>**起始版本：** 14 |
| NODE_SCROLL_CONTENT_START_OFFSET | Sets the offset from the start of the scrollable components content.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: offset from the start of the content, in vp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: offset from the start of the content, in vp. <br><br>**起始版本：** 15 |
| NODE_SCROLL_CONTENT_END_OFFSET | Sets the offset from the end of the scrollable components content.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: offset from the end of the content, in vp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: offset from the end of the content, in vp. <br><br>**起始版本：** 15 |
| NODE_SCROLL_FLING_SPEED_LIMIT = 1002019 | Defines the maximum starting fling speed of the scrollable when the fling animation starts.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].f32: maximum starting fling speed, Unit: vp/s <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].f32: maximum starting fling speed, Unit: vp/s <br><br>**起始版本：** 18 |
| NODE_SCROLL_CLIP_CONTENT = 1002020 | Defines the clip mode of the scrollable.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].i32: clip content mode. The parameter type is [ArkUI_ContentClipMode](capi-native-type-h.md#arkui_contentclipmode). The default value is<b>ARKUI_CONTENT_CLIP_MODE_BOUNDARY</b> for the <b>Grid</b> and <b>Scroll</b> components, and<b>ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY</b> for the <b>List</b> and <b>WaterFlow</b> components. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].i32: clip content mode, The parameter type is [ArkUI_ContentClipMode](capi-native-type-h.md#arkui_contentclipmode). <br><br>**起始版本：** 18 |
| NODE_SCROLL_BACK_TO_TOP = 1002021 | Defines whether the scrollable scrolls back to top when status bar is clicked.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].i32: whether the scrollable scrolls back to top when status bar is clicked.The value <b>1</b> means to scroll back to top, and <b>0</b> means the opposite. The default value is <b>0</b>for API versions earlier than 18. For API version 18 and later, the default value is <b>0</b> for thehorizontal scroll direction and <b>1</b> for the vertical scroll direction. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].i32: whether the scrollable scrolls back to top when status bar is clicked. <br><br>**起始版本：** 15 |
| NODE_SCROLL_BAR_MARGIN = 1002022 | Defines the margin of the scrollbar.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: start margin of the scrollbar, in vp. The default value is <b>0</b>. <br> .value[1].f32: end margin of the scrollbar, in vp. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: start margin of the scrollbar, in vp. <br> .value[1].f32: end margin of the scrollbar, in vp. <br><br>**起始版本：** 20 |
| NODE_SCROLL_MAX_ZOOM_SCALE = 1002023 | Sets the maximum zoom scale for scrollable content.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum zoom scale to set. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current maximum zoom scale. <br><br>**起始版本：** 20 |
| NODE_SCROLL_MIN_ZOOM_SCALE = 1002024 | Sets the minimum zoom scale for scrollable content.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum zoom scale to set. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current minimum zoom scale. <br><br>**起始版本：** 20 |
| NODE_SCROLL_ZOOM_SCALE = 1002025 | Sets the zoom scale for scrollable content.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: zoom scale to set. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current zoom scale. <br><br>**起始版本：** 20 |
| NODE_SCROLL_ENABLE_BOUNCES_ZOOM = 1002026 | Sets whether to enable the zoom bounce effect when the scaling exceeds the limits.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the zoom bounce effect when the scaling exceeds the limits.The value <b>1</b> means to enable the effect, and <b>0</b> means the opposite. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the zoom bounce effect when the scaling exceeds the limits.The value <b>1</b> means to enable the effect, and <b>0</b> means the opposite. <br><br>**起始版本：** 20 |
| NODE_SCROLL_ENABLE_SCROLL_WITH_MOUSE = 1002027 | Sets whether dragging scrolling with the left mouse button pressed is supported.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether dragging scrolling with the left mouse button pressed is supported. <b>0</b>: no; <b>1</b>: yes. Default value: <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether dragging scrolling with the left mouse button pressed is supported. <b>0</b>: no; <b>1</b>: yes. <br><br>**起始版本：** 26.0.0 |
| NODE_SCROLL_AUTO_ADJUST_MARGIN = 1002028 | Sets whether to automatically adjust the margin of the scrollbar to avoid the component's <b>NODE_PADDING</b>, <b>NODE_SCROLL_CONTENT_START_OFFSET</b>, and <b>NODE_SCROLL_CONTENT_END_OFFSET</b> areas.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute<br> .value[0].i32: whether to automatically adjust the margin of the scrollbar. <b>0</b>: yes; <b>1</b>: no. Default value: <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to automatically adjust the margin of the scrollbar. <b>0</b>: yes; <b>1</b>: no. <br><br>**起始版本：** 26.0.0 |
| NODE_LIST_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST | Sets the direction in which the list items are arranged.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: direction in which the list items are arranged. The parameter type is [ArkUI_Axis](capi-native-type-h.md#arkui_axis).The default value is <b>ARKUI_AXIS_VERTICAL</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: direction in which the list items are arranged. The parameter type is [ArkUI_Axis](capi-native-type-h.md#arkui_axis). <br> |
| NODE_LIST_STICKY | Defines whether to pin the header to the top or the footer to the bottom in the <b><ListItemGroup></b>component. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to pin the header to the top or the footer to the bottom in the <b><ListItemGroup></b>component. It is used together with the <b><ListItemGroup></b> component. The parameter type is[ArkUI_StickyStyle](capi-native-type-h.md#arkui_stickystyle). The default value is <b>ARKUI_STICKY_STYLE_NONE</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to pin the header to the top or the footer to the bottom in the <b><ListItemGroup></b>component. It is used together with the <b><ListItemGroup></b> component. The parameter type is[ArkUI_StickyStyle](capi-native-type-h.md#arkui_stickystyle). |
| NODE_LIST_SPACE | Defines the spacing between list items. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: spacing between list items along the main axis. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: spacing between list items along the main axis. <br> |
| NODE_LIST_NODE_ADAPTER | Defines the list adapter. The attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: {@link ArkUI_NodeAdapter} object as the adapter. |
| NODE_LIST_CACHED_COUNT | list组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：配合List组件Adapter使用，设置adapter中的缓存数量<br> .value[1]?.i32：是否显示缓存节点，0：不显示，1：显示，默认值：0。该参数从API version 15开始支持。 <br> .value[2]?.i32：设置List最大缓存数量，默认值与第一个参数相同。该参数从API version 22开始支持。 <br> <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].f32：adapter中的缓存数量。<br>  .value[1].i32：是否显示缓存节点，0：不显示，1：显示。该参数从API version 15开始支持。 <br> .value[2].i32：List最大缓存数量。该参数从API version 22开始支持。 <br> |
| NODE_LIST_SCROLL_TO_INDEX | Scroll to the specified index.When activating the smooth animation, all items passed through will be loaded and layout calculated, which canlead to performance issues when loading a large number of items.<br> <br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32：The index value of the target element to be slid to in the current container.<br> .value[1]?.i32：Set whether there is an action when sliding to the index value of a list item in the list, where1 indicates an action and 0 indicates no action. Default value: 0.<br> .value[2]?.i32：Specify the alignment of the sliding element with the current container,The parameter type is[ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment), default value is ARKUI_SCROLL_ALIGNMENT_START. <br> .value[3]?.f32: extra offset, in vp. The default value is <b>0</b>.This parameter is supported since API version 15. <br> |
| NODE_LIST_ALIGN_LIST_ITEM | Sets the alignment mode of list items along the cross axis when the cross-axis width of the list isgreater than the cross-axis width of list items multiplied by the value of lanes.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode of list items along the cross axis.The parameter type is [ArkUI_ListItemAlignment](capi-native-type-h.md#arkui_listitemalignment). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode of list items along the cross axis.The parameter type is [ArkUI_ListItemAlignment](capi-native-type-h.md#arkui_listitemalignment). |
| NODE_LIST_CHILDREN_MAIN_SIZE = 1003007 | Set the default spindle size for the List subcomponent.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The parameter format is {@ ArkUI-ListChildrenMainSize} <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The parameter format is {@ ArkUI-ListChildrenMainSize} |
| NODE_LIST_INITIAL_INDEX = 1003008 | Set the index value of the item displayed at the start of the viewportwhen the current List is first loaded.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: index value of the item displayed atthe start of the viewport when the current List is loaded for the first time. Default value: 0.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: index value of the item displayed atthe start of the viewport when the current List is loaded for the first time. Default value: 0. |
| NODE_LIST_DIVIDER = 1003009 | sets the ListItem splitter style. By default, there is no splitter.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Format: <br>.value[0].u32: divider color, type 0xargb; <br>.value[1].f32: dividing line width; <br>.value[2].f32: the distance between the divider and the beginning of the side of the list, unit vp; <br>.value[3].f32: the distance between the divider and the end of the side of the list (unit: vp). <br> <br> Attribute fetch method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br>.value[0].u32: divider color, type 0xargb; <br>.value[1].f32: dividing line width; <br>.value[2].f32: the distance between the divider and the beginning of the side of the list, unit vp; <br>.value[3].f32: the distance between the divider and the end of the side of the list (unit: vp). <br> |
| NODE_LIST_SCROLL_TO_INDEX_IN_GROUP = 1003010 | Scrolls to the item with the specified index in the specified list item group.When <b>smooth</b> is set to <b>true</b>, all passed items are loaded and counted in layout calculation.This may result in performance issues if a large number of items are involved. <br> <br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: index of the target list item group in the current list. <br>.value[1].i32: index of the target list item in the list item group. <br> .value[2]?.i32: whether to enable the smooth animation for scrolling to the item with the specified index.The value <b>1</b> means to enable the animation, and <b>0</b> means the opposite.The default value is <b>0</b>. <br> .value[3]?.i32: how the item to scroll to is aligned with the container. The parameter type is[ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment). The default value is <b>ARKUI_SCROLL_ALIGNMENT_START</b>. <br><br>**起始版本：** 15 |
| NODE_LIST_LANES = 1003011 | Sets the number of lanes in the list.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: number of lanes in the list. If the maximum and minimum lane widths are set, setting the numberof lanes will not take effect. <br> .value[1]?.f32: minimum lane width, in vp. <br> .value[2]?.f32: maximum column width, in vp. <br> .value[3]?.f32: lane spacing, in vp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: number of lanes in the list. <br> .value[1].f32: minimum lane width, in vp. <br> .value[2].f32: maximum column width, in vp. <br> .value[3].f32: lane spacing, in vp.  <br><br>**起始版本：** 15 |
| NODE_LIST_SCROLL_SNAP_ALIGN = 1003012 | Sets the list snap alignment mode.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode for the list snap position. The parameter type is [ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign).The default value is <b>ARKUI_SCROLL_SNAP_ALIGN_NONE</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].i32: alignment mode for the list snap position. The parameter type is [ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign).<br><br>**起始版本：** 15 |
| NODE_LIST_MAINTAIN_VISIBLE_CONTENT_POSITION = 1003013 | Sets whether to maintain the visible content's position when data is inserted or deleted outside thedisplay area of the <b>List</b> component.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside thedisplay area of the <b>List</b> component. The value <b>0</b> means not to maintain the visible content'sposition, and <b>1</b> means the opposite. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside thedisplay area of the <b>List</b> component. The value <b>0</b> means not to maintain the visible content'sposition, and <b>1</b> means the opposite. The default value is <b>0</b>. <br><br>**起始版本：** 15 |
| NODE_LIST_STACK_FROM_END = 1003014 | Sets whether the <b>List</b> component starts layout from the end.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the <b>List</b> component starts layout from the end. The value <b>0</b> means layoutstarts from the top, and <b>1</b> means layout starts from the end. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the <b>List</b> component starts layout from the end. The value <b>0</b> means layoutstarts from the top, and <b>1</b> means layout starts from the end. The default value is <b>0</b>. <br><br>**起始版本：** 19 |
| NODE_LIST_FOCUS_WRAP_MODE = 1003015 | Defines the focus wrap mode for the <b>List</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: focus wrap mode of the <b>List</b> component.The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: focus wrap mode of the <b>List</b> component.The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode). <br><br>**起始版本：** 20 |
| NODE_LIST_SYNC_LOAD = 1003016 | Defines whether the <b>List</b> component loads child nodes synchronously.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the <b>List</b> component synchronously loads child nodes.The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the <b>List</b> component synchronously loads child nodes.The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading. <br><br>**起始版本：** 20 |
| NODE_LIST_SCROLL_SNAP_ANIMATION_SPEED = 1003017 | Defines the scroll snap animation speed for the <b>List</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.value[0].i32: scroll snap animation speed for the <b>List</b> component.The parameter type is [ArkUI_ScrollSnapAnimationSpeed](capi-native-type-h.md#arkui_scrollsnapanimationspeed).Default value: <b>ARKUI_SCROLL_SNAP_ANIMATION_NORMAL</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].i32: scroll snap animation speed for the <b>List</b> component.The parameter type is [ArkUI_ScrollSnapAnimationSpeed](capi-native-type-h.md#arkui_scrollsnapanimationspeed). <br><br>**起始版本：** 22 |
| NODE_LIST_LANES_ITEMFILLPOLICY = 1003018 | List组件的响应式列数布局策略，支持属性设置，属性重置和属性获取接口。 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)；<br> .value[1]?.f32：列间距，单位vp，默认值：0<br> <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)；<br> .value[1].f32：列间距，单位vp。<br><br>**起始版本：** 22 |
| NODE_LIST_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1003019 | <b>List</b>容器是否支持懒加载空分支渲染。该属性可以通过API根据需要设置、重置和获取。在懒加载模式下启用时，<b>List</b>中的空分支（没有内容的项）将被渲染并设置为宽度0和高度0。这可能会影响整体布局和滚动行为。这通常用于数据源可能存在间隙或需要维护特定布局位置的场景。设置属性[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：懒加载模式下是否支持空分支渲染。<b>0</b>：禁用空分支支持。空分支不会被渲染。<b>1</b>：启用空分支支持。空分支将被渲染为占位符项。默认值：<b>0</b>.<br> <br> 属性获取[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)的格式为：<br> .value[0].i32：是否启用空分支渲染。<b>0</b>：关闭。<b>1</b>：启用。<br><br>**起始版本：** 23 |
| NODE_LIST_BACK_PRESS_BEHAVIOR = 1003020 | 设置List组件的返回键行为。支持属性设置、重置、获取接口。[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)设置属性的参数格式如下：.value[0].i32：单击后退按钮时是否折叠滚动菜单。0：不支持，1：支持。默认值：1。[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)获取属性的参数格式如下：.value[0].i32：单击返回按钮时是否收起划出菜单。0：不支持，1：支持。<br>**起始版本：** 26.0.0 |
| NODE_LIST_ENABLE_EDIT_MODE = 1003021 | List组件是否使能编辑模式。设置为1（可编辑）时，默认显示复选框，且在编辑模式内支持单指滑动多选。编辑模式状态变更时，会触发[NODE_LIST_ON_EDIT_MODE_CHANGE](capi-native-node-h.md#arkui_nodeeventtype)事件回调。状态变更途径有两种：1. 直接设置本属性。2. 在[NODE_LIST_EDIT_MODE_OPTIONS](capi-native-node-h.md#arkui_nodeattributetype)启用双指滑动多选且注册了[NODE_LIST_ON_EDIT_MODE_CHANGE](capi-native-node-h.md#arkui_nodeeventtype)回调时，通过双指滑动手势触发。支持属性设置，属性重置和属性获取接口。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：List组件是否使能编辑模式。0：不可编辑，1：可以编辑。默认值：0属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：List组件是否使能编辑模式。0：不可编辑，1：可以编辑。<br>**起始版本：** 26.0.0 |
| NODE_LIST_EDIT_MODE_OPTIONS = 1003022 | List组件编辑模式选项配置。支持属性设置，属性重置和属性获取接口。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：List组件是否使用默认多选样式， 使用默认多选样式时，List进入编辑模式后会显示复选框。0：不使用默认样式，1：使用默认样式。默认值：1.value[1].i32：List组件是否启用双指滑动多选，该参数在注册[NODE_LIST_ON_EDIT_MODE_CHANGE](capi-native-node-h.md#arkui_nodeeventtype)事件回调后生效。0：使用双指划动手势不能让List组件进入编辑模式，但通过其他方式进入编辑模式后，编辑模式内的单指滑动多选不受影响。1：使用双指划动手势能让List组件从非编辑模式进入编辑模式并执行划动多选。默认值：1属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：List组件是否使用默认多选样式。0：不使用默认样式，1：使用默认样式。.value[1].i32：List组件是否启用双指滑动多选。0：不启用，1：启用。<br>**起始版本：** 26.0.0 |
| NODE_SWIPER_LOOP = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER | Defines whether to enable loop playback for the swiper.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable loop playback. The value <b>1</b> means to enable loop playback, and <b>0</b>means the opposite. The default value is <b>1/b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable loop playback. The value <b>1</b> means to enable loop playback, and <b>0</b>means the opposite. The default value is <b>1</b>. <br> |
| NODE_SWIPER_AUTO_PLAY | Defines whether to enable automatic playback for child component switching in the swiper.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable automatic playback for child component switching. The value <b>1</b>means to enable automatic playback, and <b>0</b> means the opposite. The default value is <b>0</b>. <br> <br> .value[1]?.i32: whether to stop automatic playback when the user touches the screen. The value <b>1</b> meansto stop automatic playback, and <b>0</b> means the opposite. The default value is <b>1</b>. This parameter issupported since API version 16. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable automatic playback for child component switching. The value <b>1</b> meansto enable automatic playback, and <b>0</b> means the opposite. The default value is <b>0</b>. <br> .value[1].i32: whether to stop automatic playback when the user touches the screen. The value <b>1</b> means tostop automatic playback, and <b>0</b> means the opposite. This parameter is supported since API version 16. <br> |
| NODE_SWIPER_SHOW_INDICATOR | Defines whether to enable the navigation point indicator for the swiper. This attribute can be set,reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the navigation point indicator. The value <b>1</b> means to enable thenavigation point indicator, and <b>0</b> means the opposite. The default value is <b>1</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the navigation point indicator. The value <b>1</b> means to enable thenavigation point indicator, and <b>0</b> means the opposite. The default value is <b>1</b>. <br> |
| NODE_SWIPER_INTERVAL | Defines the interval for automatic playback. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: interval for automatic playback, in milliseconds. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: interval for automatic playback, in milliseconds. <br> |
| NODE_SWIPER_VERTICAL | Defines whether vertical swiping is used for the swiper. This attribute can be set, reset, and obtainedas required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether vertical swiping is used. The value <b>1</b> means that vertical swiping is used, and<b>0</b> means the opposite. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether vertical swiping is used. The value <b>1</b> means that vertical swiping is used, and<b>0</b> means the opposite. The default value is <b>0</b>. <br> |
| NODE_SWIPER_DURATION | Defines the duration of the animation for switching child components. This attribute can be set, reset,and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: duration of the animation for switching child components, in milliseconds. The default value is<b>400</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: duration of the animation for switching child components, in milliseconds. The default value is<b>400</b>. <br> |
| NODE_SWIPER_CURVE | Defines the animation curve for the swiper. This attribute can be set, reset, and obtained as requiredthrough APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).The default value is <b>ARKUI_CURVE_LINEAR</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).The default value is <b>ARKUI_CURVE_LINEAR</b>. <br> |
| NODE_SWIPER_ITEM_SPACE | Defines the spacing between child components in the swiper.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: spacing between child components. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: spacing between child components. <br> |
| NODE_SWIPER_INDEX | Defines the index of the child component currently displayed in the swiper.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: index value of the child component. <br> .value[1]?.i32: animation mode, the parameter type is [ArkUI_SwiperAnimationMode](capi-native-type-h.md#arkui_swiperanimationmode). <br> The default value is ARKUI_SWIPER_NO_ANIMATION. This parameter is valid only for the current call. <br> This parameter is supported since API version 15. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: index value of the child component. <br> |
| NODE_SWIPER_DISPLAY_COUNT | Defines the number of elements to display per page.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of elements to display per page. <br> .value[1]?.i32: whether to turn pages by group. The value <b>0</b> means to turn pages by child element,and <b>1</b> means to turn pages by group. This parameter is supported since API version 19. <br> .string?: this parameter can only be set to 'auto'. When 'auto' is set, the value[] parameters are ignored.This parameter is supported since API version 19. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of elements to display per page. <br> .value[1].i32: whether to turn pages by group. This parameter is supported since API version 19. <br> .string: 'auto' or empty string. |
| NODE_SWIPER_DISABLE_SWIPE | Defines whether to disable the swipe feature.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to disable the swipe feature. The value <b>1</b> means to disablethe swipe feature, and <b>0</b> means the opposite. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to disable the swipe feature. The value <b>1</b> means to disable the swipefeature, and <b>0</b> means the opposite. The default value is <b>0</b>. <br> |
| NODE_SWIPER_SHOW_DISPLAY_ARROW | Defines whether to show the arrow when the mouse pointer hovers over the navigation point indicator.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator.The parameter type is [ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow).<br> The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>. <br> .?object: arrow style. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). <br> This parameter is supported since API version 19. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator.The parameter type is [ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow).<br> The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>. <br> .object: arrow style. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). <br> This parameter is supported since API version 19. <br> |
| NODE_SWIPER_EDGE_EFFECT_MODE | Defines the effect used at the edges of the swiper when the boundary of the scrollable content is reached.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached.The parameter type is [ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect).<br> The default value is <b>ARKUI_EDGE_EFFECT_SPRING</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached.The parameter type is [ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect). <br> |
| NODE_SWIPER_NODE_ADAPTER | Defines the swiper adapter. The attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: {@link ArkUI_NodeAdapter} object as the adapter. |
| NODE_SWIPER_CACHED_COUNT | Sets the number of cached items in the swiper adapter.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of cached items in the swiper adapter. <br> .value[1]?.i32: whether the cached items will be displayed. <br> The value <b>0</b> indicates that cached items will not be displayed, <br> and <b>1</b> indicates that cached items will be displayed. The default value is <b>0</b>. <br> This parameter is supported from API version 19. <br> .value[2]?.i32: whether the cachedCount is independent of group calculation. <br> The value <b>1</b> indicates that cachedCount is calculated by actual child component count,<br> and is independent of displayCount group calculation.<br> The value <b>0</b> indicates that, when NODE_SWIPER_DISPLAY_COUNT is enabled to turn pages by group,<br> cachedCount is calculated by group.The default value is <b>0</b>. <br> This parameter is supported from API version 24. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of cached items in the swiper adapter. <br> .value[1].i32: whether the cached items will be displayed. This parameter is supported from API version 19. <br> .value[2].i32: whether the cachedCount is independent of group calculation. This parameter is supported from API version 24. |
| NODE_SWIPER_PREV_MARGIN | Defines the front margin of the wiper.The attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: the front margin. The unit is vp. The default value is <b>0.0</b><br> .value[1]?.i32: whether to ignore blanks, the default value is 0.The value <b>1</b> means to ignore blank areas, and <b>0</b> means the opposite. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: the front margin, the unit is vp. <br> .value[1].i32: whether to ignore blank areas. The value <b>1</b> means to ignore blank areas, and <b>0</b> meansthe opposite. |
| NODE_SWIPER_NEXT_MARGIN | Defines the back margin of the wiper.The attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: the back margin. The unit is vp. The default value is <b>0.0</b><br> .value[1]?.i32: whether to ignore blanks, the default value is 0.The value <b>1</b> means to ignore blank areas, and <b>0</b> means the opposite. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: the back margin, the unit is vp. <br> .value[1].i32: whether to ignore blank areas. The value <b>1</b> means to ignore blank areas, and <b>0</b> meansthe opposite. |
| NODE_SWIPER_INDICATOR | Defines the navigation indicator type of the swiper.The attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: navigation indicator type, the parameter type is [ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype).<br> .object: The parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) when the indicator type <br> is <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b>. The parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)when the indicator type is <b>ARKUI_SWIPER_INDICATOR_TYPE_DIGIT</b>. <br> [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) is supported since API version 19. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: navigation indicator type, the parameter type is [ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype).<br> .object: The parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) when the indicator type <br> is <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b>. The parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)when the indicator type is <b>ARKUI_SWIPER_INDICATOR_TYPE_DIGIT</b>. <br> [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) is supported since API version 19. <br> |
| NODE_SWIPER_NESTED_SCROLL | Set the nested scrolling mode for the Swiper component and parent component.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32：Nested scrolling patterns for Swiper components and parent components. The parameter type is[ArkUI_SwiperNestedScrollMode](capi-native-type-h.md#arkui_swipernestedscrollmode) <br> The default value is <b>ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY<b> <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32：Nested scrolling patterns for Swiper components and parent components. The parameter type is[ArkUI_SwiperNestedScrollMode](capi-native-type-h.md#arkui_swipernestedscrollmode) |
| NODE_SWIPER_SWIPE_TO_INDEX | Set the switcher component to flip to the specified page.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32：Specify the index value of the page in Swiper.<br> .value[1]?.i32：Set whether there is an animation effect when flipping to the specified page. 1 indicates activeeffect, 0 indicates no active effect, default value is 0。 |
| NODE_SWIPER_INDICATOR_INTERACTIVE | Set to disable component navigation point interaction function。Property setting method parameter {@link ArkUI-AttributeItem} format: <br> .value[0].i32：Set to disable the interaction function of component navigation points. When set to true, itindicates that the navigation points are interactive. The default value is true. <br> The return value of the attribute acquisition method is in the format of {@ link ArkUI-AttributeItem}： <br> .value[0].i32：Set to disable component navigation point interaction. |
| NODE_SWIPER_PAGE_FLIP_MODE | Sets the page flipping mode using the mouse wheel.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-native-type-h.md#arkui_pageflipmode). <br> <br> Format of the return value [ArkUI_PageFlipMode](capi-native-type-h.md#arkui_pageflipmode):<br> .value[0].i32: page flipping mode using the mouse wheel. <br><br>**起始版本：** 15 |
| NODE_SWIPER_AUTO_FILL | Defines the minimum main axis size of child element for swiper to works out the display count.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum main axis size of the child element, Unit: vp. <br> .value[1]?.i32: whether to turn pages by group. The value <b>0</b> means to turn pages by child element,and <b>1</b> means to turn pages by group. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum main axis size of the child element, Unit: vp. <br> .value[1].i32: whether to turn pages by group. <br><br>**起始版本：** 19 |
| NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023 | Sets whether to maintain the visible content's position when data is inserted or deleted outsidethe display area of the <b>Swiper</b> component.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outsidethe display area of the <b>Swiper</b> component. The value <b>0</b> means not to maintain the visible content'sposition, and <b>1</b> means the opposite. The default value is <b>0</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outsidethe display area of the <b>Swiper</b> component. The value <b>0</b> means not to maintain the visible content'sposition, and <b>1</b> means the opposite. The default value is <b>0</b>. <br><br>**起始版本：** 20 |
| NODE_SWIPER_ITEMFILLPOLICY = 1001024 | Specifies the responsive column layout policy for the <b>Swiper</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].i32: number of columns at different breakpoint specifications.The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy). <br> .value[1]?.i32: whether to paginate by group. The value <b>0</b> means to paginate by individual child elements,and <b>1</b> means to paginate by groups of child elements displayed within the viewport.The default value is <b>0</b>.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].i32: number of columns at different breakpoint specifications.The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy). <br> .value[1].i32: whether to paginate by group. <br><br>**起始版本：** 22 |
| NODE_LIST_ITEM_SWIPE_ACTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM | @brief: Set the delineation component of the ListItem, supporting property settings, property resets, andproperty acquisition interfaces.Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .object: Construct using the {@link ArkUI_ListitemSwipeActionOption} object. <br> <br> The return value of the attribute acquisition method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .object: Construct using the {@link ArkUI_ListitemSwipeActionOption} object. <br> |
| NODE_LIST_ITEM_GROUP_SET_HEADER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM_GROUP | Defines the header of the list item group.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) object to be used as the header of the list item group. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) object to be used as the header of the list item group. <br> |
| NODE_LIST_ITEM_GROUP_SET_FOOTER | Defines the footer of the list item group. This attribute can be set, reset, and obtained asrequired through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) object to be used as the footer of the list item group. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) object to be used as the footer of the list item group. <br> |
| NODE_LIST_ITEM_GROUP_SET_DIVIDER | Defines the style of the divider for the list items. This attribute can be set, reset, and obtainedas required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the divider, in 0xARGB format.<br> .value[1].f32: stroke width of the divider, in vp.<br> .value[2].f32: distance between the divider and the start of the list, in vp.<br> .value[3].f32: distance between the divider and the end of the list, in vp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the divider, in 0xARGB format.<br> .value[1].f32: stroke width of the divider, in vp.<br> .value[2].f32: distance between the divider and the start of the list, in vp.<br> .value[3].f32: distance between the divider and the end of the list, in vp. <br> |
| NODE_LIST_ITEM_GROUP_CHILDREN_MAIN_SIZE = 1005003 | Set the default spindle size for the ListItem Group subcomponent.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The parameter format is {@ ArkUI-ListChildrenMainSize} <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The parameter format is {@ ArkUI-ListChildrenMainSize} |
| NODE_LIST_ITEM_GROUP_NODE_ADAPTER = 1005004 | Defines the list item group adapter.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: {@link ArkUI_NodeAdapter} object as the adapter. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: {@link ArkUI_NodeAdapter} object. <br><br>**起始版本：** 15 |
| NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN | Defines the horizontal alignment mode of child components in the column.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: horizontal alignment mode of child components.The parameter type is [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment).<br> Default value: <b>ARKUI_HORIZONTAL_ALIGNMENT_CENTER</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: horizontal alignment mode of child components.The parameter type is [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment). <br> |
| NODE_COLUMN_JUSTIFY_CONTENT | Defines the vertical alignment mode of child components in the column.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment).<br> Default value: <b>ARKUI_FLEX_ALIGNMENT_START</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment). <br> |
| NODE_LINEAR_LAYOUT_SPACE | Defines Row constructor options or Column constructor options used for settting the spacing of child components, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: The space of child components, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: The space of child components, in vp.<br><br>**起始版本：** 23 |
| NODE_LINEAR_LAYOUT_REVERSE | Defines whether the arrangement of child components along the main axis in a Column or Row is reversed, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The value that determines whether the arrangement of child components along the main axis is reversed.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value that determines whether the arrangement of child components along the main axis is reversed.<br><br>**起始版本：** 23 |
| NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW | Defines the vertical alignment mode of child components in the row.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: vertical alignment mode of child components.The parameter type is [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment).<br> Default value: <b>ARKUI_VERTICAL_ALIGNMENT_CENTER</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: vertical alignment mode of child components.The parameter type is [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment). <br> |
| NODE_ROW_JUSTIFY_CONTENT | Defines the horizontal alignment mode of child components in the row.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: horizontal alignment mode of child components.The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment).<br> Default value: <b>ARKUI_FLEX_ALIGNMENT_START</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: horizontal alignment mode of child components.The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment). <br> |
| NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX | Defines the flex attribute. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.i32: direction in which flex items are arranged. The parameter type is [ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection).The default value is <b>ARKUI_FLEX_DIRECTION_ROW</b>.<br> .value[1]?.i32: how the flex items are wrapped. The parameter type is [ArkUI_FlexWrap](capi-native-type-h.md#arkui_flexwrap).The default value is <b>ARKUI_FLEX_WRAP_NO_WRAP</b>.<br> .value[2]?.i32: alignment mode along the main axis. The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment).The default value is <b>ARKUI_FLEX_ALIGNMENT_START</b>.<br> .value[3]?.i32: alignment mode along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment).The default value is <b>ARKUI_ITEM_ALIGNMENT_START</b>.<br> .value[4]?.i32: alignment mode along the cross axis for multi-line content. The parameter type is[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment). The default value is <b>ARKUI_FLEX_ALIGNMENT_START</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: direction in which flex items are arranged. <br> .value[1].i32: how the flex items are wrapped. <br> .value[2].i32: alignment mode along the main axis. <br> .value[3].i32: alignment mode along the cross axis. <br> .value[4].i32: alignment mode along the cross axis for multi-line content.<br> |
| NODE_FLEX_SPACE | Defines Row constructor options used for settting the spacing of child components, which can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: Space on the main axis of the flex container., in vp.<br> .value[1].f32: Space on the cross axis of a flex container., in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: Space on the main axis of the flex container., in vp.<br> .value[1].f32: Space on the cross axis of a flex container., in vp.<br><br>**起始版本：** 23 |
| NODE_REFRESH_REFRESHING = MAX_NODE_SCOPE_NUM * ARKUI_NODE_REFRESH | Sets whether the component is being refreshed.This attribute can be set and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The parameter type is 1 or 0.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The parameter type is 1 or 0. |
| NODE_REFRESH_CONTENT | Sets the custom content in the pull-down area.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The parameter type is {@Link ArkUI_NodeHandle}. |
| NODE_REFRESH_PULL_DOWN_RATIO = 1009002 | Set the pull-down hand coefficient.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32：Pull-down hand coefficient, valid value between 0 and 1.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32：Pull-down hand coefficient, valid value between 0 and 1. |
| NODE_REFRESH_OFFSET = 1009003 | Sets the pull-down offset that initiates a refresh.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: pull-down offset, in vp. The default value is <b>64vp</b>.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: pull-down offset, in vp. The default value is <b>64vp</b>. |
| NODE_REFRESH_PULL_TO_REFRESH = 1009004 | Sets whether to initiate a refresh when the pull-down distance exceeds the value of <b>refreshOffset</b>.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to initiate a refresh. The value <b>true</b> means to initiate a refresh, and<b>false</b> means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to initiate a refresh. The value <b>1</b> means to initiate a refresh, and<b>0</b> means the opposite. |
| NODE_REFRESH_MAX_PULL_DOWN_DISTANCE = 1009005 | Sets the maximum pull-down distance for refreshing.This attribute can be set, reset, and obtained through the API as required.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum pull-down distance, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum pull-down distance, in vp.<br>**起始版本：** 20 |
| NODE_REFRESH_PULL_UP_TO_CANCEL_REFRESH = 1009006 | 设置上划是否取消刷新。支持属性设置，属性重置和属性获取。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)的参数格式：<br>  .value[0].i32：上划是否取消刷新。0为上划不取消刷新，1为上划取消刷新。默认值：1。<br>  属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)的格式：<br>  .value[0].i32：上划是否取消刷新。0为上划不取消刷新，1为上划取消刷新。<br>**起始版本：** 23 |
| NODE_WATER_FLOW_LAYOUT_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_WATER_FLOW | Defines the main axis direction of the <b><WaterFlow></b> component layout.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: main axis direction. The parameter type is {@Link ArkUI_FlexDirection}.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: main axis direction. The parameter type is {@Link ArkUI_FlexDirection}. |
| NODE_WATER_FLOW_COLUMN_TEMPLATE | Sets the number of columns in the water flow layout. If this parameter is not set, one column is usedby default. This attribute can be set, reset, and obtained as required through APIs.For example, <b>'1fr 1fr 2fr'</b> indicates three columns, with the first column taking up 1/4 of the parentcomponent's full width, the second column 1/4, and the third column 2/4.You can use <b>columnsTemplate('repeat(auto-fill,track-size)')</b> to automatically calculate the number ofcolumns based on the specified column width <b>track-size</b>.<b>repeat</b> and <b>auto-fill</b> are keywords. The units for <b>track-size</b> can be px, vp (default), %,or a valid number.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: number of columns in the layout.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: number of columns in the layout.<br> |
| NODE_WATER_FLOW_ROW_TEMPLATE | Sets the number of rows in the water flow layout. If this parameter is not set, one row is usedby default. This attribute can be set, reset, and obtained as required through APIs.For example, <b>'1fr 1fr 2fr'</b> indicates three rows, with the first row taking up 1/4 of the parentcomponent's full height, the second row 1/4, and the third row 2/4.You can use <b>rowsTemplate('repeat(auto-fill,track-size)')</b> to automatically calculate the number of rowsbased on the specified row height <b>track-size</b>.<b>repeat</b> and <b>auto-fill</b> are keywords. The units for <b>track-size</b> can be px, vp (default), %,or a valid number.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: number of rows in the layout. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: number of rows in the layout. <br> |
| NODE_WATER_FLOW_COLUMN_GAP | Sets the gap between columns.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: gap between columns, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: gap between columns, in vp.<br> |
| NODE_WATER_FLOW_ROW_GAP | Sets the gap between rows.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: gap between lines, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: gap between lines, in vp.<br> |
| NODE_WATER_FLOW_SECTION_OPTION | Defines the water flow section configuration.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: An index calculated from 0 is converted to an integer,indicating that you want to start changing the position of the group..object: {@ArkUI_WaterFlowSectionOption} object.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: {@ArkUI_WaterFlowSectionOption} object.<br> |
| NODE_WATER_FLOW_NODE_ADAPTER | Defines the water flow adapter. The attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: {@link ArkUI_NodeAdapter} object as the adapter. |
| NODE_WATER_FLOW_CACHED_COUNT | Sets the number of cached items in the water flow adapter.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].i32：number of cached items in the water flow adapter. <br> .value[1]?.i32：whether to the cached items will be displayed, 0: not displayed, 1: displayed, default value: 0.This parameter is supported since API version 16. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of cached items in the water flow adapter. <br> .value[1].i32: whether to the cached items will be displayed, 0: not displayed, 1: displayed, default value: 0.This parameter is supported since API version 16. |
| NODE_WATER_FLOW_FOOTER | Set the custom display component at the end of the waterfall flow component.Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter format: <br> .object: Parameter type [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). |
| NODE_WATER_FLOW_SCROLL_TO_INDEX | Scroll to the specified index.When activating the smooth animation, all items passed through will be loaded and layout calculated, which canlead to performance issues when loading a large number of items.<br> <br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The index value of the target element to be slid to in the current container.<br> .value[1].i32: Set whether there is an action when sliding to the index value of a list item in the list, where1 indicates an action and 0 indicates no action. This parameter is optional, default value is 0.<br> .value[2].i32: Specify the alignment of the sliding element with the current container, The parameter type is[ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment). This parameter is optional, default value is </b>ARKUI_SCROLL_ALIGNMENT_START</b>. <br> .value[3].f32: Extra offset after scrolling to a specified index, in vp. This parameter is optional, the defaultvalue is <b>0</b>.If value[3] is positive, it will offset further towards the bottom.If value[3] is negative, it will offset further towards the top.This parameter is supported since API version 23. <br> |
| NODE_WATER_FLOW_ITEM_CONSTRAINT_SIZE | Defines the size constraints to apply to water flow items.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum width, in vp.<br> .value[1].f32: maximum width, in vp.<br> .value[2].f32: minimum height, in vp.<br> .value[3].f32: maximum height, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum width, in vp.<br> .value[1].f32: maximum width, in vp.<br> .value[2].f32: minimum height, in vp.<br> .value[3].f32: maximum height, in vp.<br> |
| NODE_WATER_FLOW_LAYOUT_MODE | Defines the layout mode of the <b><WaterFlow></b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: waterflow layout mode. The parameter type is {@Link ArkUI_WaterFlowLayoutMode}.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: waterflow layout mode. The parameter type is {@Link ArkUI_WaterFlowLayoutMode}.<br>**起始版本：** 18 |
| NODE_WATER_FLOW_SYNC_LOAD = 1010012 | Defines whether the <b>WaterFlow</b> component loads child nodes synchronously.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the <b>WaterFlow</b> component synchronously loads child nodes.The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the <b>WaterFlow</b> component synchronously loads child nodes.The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading. <br><br>**起始版本：** 20 |
| NODE_WATER_FLOW_COLUMN_TEMPLATE_ITEMFILLPOLICY = 1010013 | Specifies the responsive column layout policy for the <b>WaterFlow</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of columns at different breakpoint specifications.The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of columns at different breakpoint specifications.The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy). <br><br>**起始版本：** 22 |
| NODE_WATER_FLOW_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1010014 | Specifies whether to support empty branch rendering in lazy loading mode for the <b>WaterFlow</b> container.This attribute can be set, reset, and obtained as required through APIs. When enabled in lazy loading mode, empty branches (items without content) in the <b>WaterFlow</b> will be rendered and set to width 0 and height 0, which may affect the overall layout and scrolling behavior. This is typically used in scenarios where thedata source may have gaps or when maintaining specific layout positions is required.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to support empty branch rendering in lazy loading mode.<b>0</b>: Disable empty branch support. Empty branches will not be rendered. <b>1</b>: Enable empty branch support. Empty branches will be rendered as placeholder items. Default value: <b>0</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether empty branch rendering is enabled. <b>0</b>: Disabled. <b>1</b>: Enabled.<br><br>**起始版本：** 26.0.0 |
| NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER | Set the auxiliary line in the RelativeContaine container, supporting property setting,property reset and property acquisition interfaces.Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .object: Auxiliary lines within the RelativeContaine container: <br><br> Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .object: Auxiliary lines within the RelativeContaine container: <br> |
| NODE_RELATIVE_CONTAINER_BARRIER | Sets the barrier within the RelativeContaine container and supports property setting,property reset and property acquisition interfaces.Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .object: Auxiliary lines within the RelativeContaine container: <br><br> Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .object: Barrier within the RelativeContaine container: <br> |
| NODE_GRID_COLUMN_TEMPLATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID | Sets the number of columns in the grid layout. If this parameter is not set, one column is usedby default. This attribute can be set, reset, and obtained as required through APIs.For example, <b>'1fr 1fr 2fr'</b> indicates three columns, with the first column taking up 1/4 of the parentcomponent's full width, the second column 1/4, and the third column 2/4.You can use <b>columnsTemplate('repeat(auto-fill,track-size)')</b> to automatically calculate the number ofcolumns based on the specified column width <b>track-size</b>.<b>repeat</b> and <b>auto-fill</b> are keywords. The units for <b>track-size</b> can be px, vp (default), %,or a valid number.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: number of columns in the layout.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: number of columns in the layout.<br> |
| NODE_GRID_ROW_TEMPLATE | Sets the number of rows in the grid layout. If this parameter is not set, one row is usedby default. This attribute can be set, reset, and obtained as required through APIs.For example, <b>'1fr 1fr 2fr'</b> indicates three rows, with the first row taking up 1/4 of the parentcomponent's full height, the second row 1/4, and the third row 2/4.You can use <b>rowsTemplate('repeat(auto-fill,track-size)')</b> to automatically calculate the number of rowsbased on the specified row height <b>track-size</b>.<b>repeat</b> and <b>auto-fill</b> are keywords. The units for <b>track-size</b> can be px, vp (default), %,or a valid number.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: number of rows in the layout. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: number of rows in the layout. <br> |
| NODE_GRID_COLUMN_GAP | Sets the gap between columns. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: gap between columns, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: gap between columns, in vp.<br> |
| NODE_GRID_ROW_GAP | Sets the gap between rows. This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: gap between lines, in vp.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: gap between lines, in vp.<br> |
| NODE_GRID_NODE_ADAPTER | Defines the grid adapter. The attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: {@link ArkUI_NodeAdapter} object as the adapter. |
| NODE_GRID_CACHED_COUNT | 设置网格适配器中缓存项的数量。该属性可以通过API根据需要设置、重置和获取。设置属性[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：网格适配器中缓存的项数。<br> .value[1].i32：是否显示缓存节点。0表示不显示，1表示显示。可选参数，默认值为0。此参数从API版本26.0.0开始支持。<br> <br> 返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)的格式为：<br> .value[0].i32：网格适配器中缓存的项数。<br> .value[1].i32：是否显示缓存节点。0表示不显示，1表示显示。此参数从API版本26.0.0开始支持。 |
| NODE_GRID_FOCUS_WRAP_MODE = 1013006 | Defines the focus wrap mode for the <b>Grid</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: focus wrap mode of the <b>Grid</b> component.The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode). <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: focus wrap mode of the <b>Grid</b> component.The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode). <br><br>**起始版本：** 20 |
| NODE_GRID_SYNC_LOAD = 1013007 | Defines whether the <b>Grid</b> component loads child nodes synchronously.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the <b>Grid</b> component synchronously loads child nodes.The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the <b>Grid</b> component synchronously loads child nodes.The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading. <br><br>**起始版本：** 20 |
| NODE_GRID_ALIGN_ITEMS = 1013008 | 设置Grid中GridItem的对齐方式，支持属性设置，属性重置和属性获取接口。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid中GridItem的对齐方式，参数类型[ArkUI_GridItemAlignment](capi-native-type-h.md#arkui_griditemalignment)。默认值：GRID_ITEM_ALIGNMENT_DEFAULT。<br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid中GridItem的对齐方式，参数类型[ArkUI_GridItemAlignment](capi-native-type-h.md#arkui_griditemalignment)。<br><br>**起始版本：** 22 |
| NODE_GRID_LAYOUT_OPTIONS = 1013009 | 设置Grid布局选项，支持属性设置，属性重置和属性获取接口。属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式：.object：参数格式为[ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)。属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.object：返回值格式为[ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)。<br>**起始版本：** 22 |
| NODE_GRID_COLUMN_TEMPLATE_ITEMFILLPOLICY = 1013010 | Grid组件的响应式列数布局策略，支持属性设置，属性重置和属性获取接口。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)；属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)；<br>**起始版本：** 22 |
| NODE_GRID_EDIT_MODE = 1013011 | Grid组件是否进入编辑模式，进入编辑模式可以通过NODE_GRID_ON_ITEM_DRAG_START事件拖拽GridItem。支持属性设置，属性重置和属性获取接口。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid组件是否进入编辑模式。0：不可编辑，1：可以编辑。默认值：0属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid组件是否进入编辑模式。0：不可编辑，1：可以编辑。<br>**起始版本：** 23 |
| NODE_GRID_DRAG_ANIMATION = 1013012 | Grid组件是否启用GridItem拖拽动画。支持属性设置，属性重置和属性获取接口。仅在滚动模式下（只设置rowsTemplate、columnsTemplate其中一个）支持动画。仅在大小规则的Grid中支持拖拽动画，跨行或跨列场景不支持。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid组件是否启用GridItem拖拽动画。0：不启用，1：启用。默认值：0属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid组件是否启用GridItem拖拽动画。0：不启用，1：启用。<br>**起始版本：** 23 |
| NODE_GRID_MULTI_SELECTABLE = 1013013 | 指定是否在<b>Grid</b>容器中启用基于鼠标的多选。这个属性可以通过API根据需要设置、重置和获取。启用后在Grid范围内鼠标框选会触发GridItem的NODE_GRID_ITEM_EVENT_ON_SELECT事件。设置属性[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：是否启用鼠标多选。<b>0</b>：关闭鼠标多选功能。<b>1</b>：启用基于鼠标的多选。默认值：<b>0</b>. 返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： .value[0].i32是否启用基于鼠标的多选。<b>0</b>：关闭鼠标多选功能。<b>1</b>：启用基于鼠标的多选.<br><br>**起始版本：** 23 |
| NODE_GRID_SCROLL_TO_INDEX = 1013014 | 滑动到指定index。开启动效时，会对经过的所有子组件进行加载和布局计算，当大量加载子组件时会导致性能问题。<br> <br> 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：要滑动到的目标元素在当前容器中的索引值。<br> .value[1].i32：设置滑动到目标元素时是否有动效，1表示有动效，0表示没有动效。该参数是可选的，默认值：0。<br> .value[2].i32：指定滑动到的目标元素与当前容器的对齐方式，参数类型[ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment), 该参数是可选的，默认值：ARKUI_SCROLL_ALIGNMENT_AUTO。<br> .value[3].f32：滑动到目标元素后的额外偏移量，该参数是可选的，默认值：0，单位：vp。如果值为正数，则向底部额外偏移；如果值为负数，则向顶部额外偏移。<br><br>**起始版本：** 23 |
| NODE_GRID_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1013015 | <b>Grid</b>容器是否支持懒加载空分支渲染。该属性可以通过API根据需要设置、重置和获取。在懒加载模式下启用时，<b>Grid</b>中的空分支（没有内容的项）将被渲染并设置为宽度0和高度0。这可能会影响整体布局和滚动行为。这通常用于数据源可能存在间隙或需要维护特定布局位置的场景。设置属性[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：懒加载模式下是否支持空分支渲染。<b>0</b>：禁用空分支支持。空分支不会被渲染。<b>1</b>：启用空分支支持。空分支将被渲染为占位符项。默认值：<b>0</b>.<br> <br> 返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)的格式为：<br> .value[0].i32：是否启用空分支渲染。<b>0</b>：关闭。<b>1</b>：启用。<br><br>**起始版本：** 23 |
| NODE_GRID_ENABLE_EDIT_MODE = 1013016 | Grid组件是否使能编辑模式。设置为1（可编辑）时，默认显示复选框，且在编辑模式内支持单指滑动多选。该属性为编辑模式的主开关，其他编辑相关属性（如[NODE_GRID_EDIT_MODE_OPTIONS](capi-native-node-h.md#arkui_nodeattributetype)）仅在本属性为1时生效。编辑模式状态变更时，会触发[NODE_GRID_ON_EDIT_MODE_CHANGE](capi-native-node-h.md#arkui_nodeeventtype)事件回调。状态变更途径有两种：1. 直接设置本属性。2. 在[NODE_GRID_EDIT_MODE_OPTIONS](capi-native-node-h.md#arkui_nodeattributetype)启用双指滑动多选且注册了[NODE_GRID_ON_EDIT_MODE_CHANGE](capi-native-node-h.md#arkui_nodeeventtype)回调时，通过双指滑动手势触发。支持属性设置，属性重置和属性获取接口。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid组件是否使能编辑模式。0：不可编辑，1：可以编辑。默认值：0属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid组件是否使能编辑模式。0：不可编辑，1：可以编辑。<br>**起始版本：** 26.0.0 |
| NODE_GRID_EDIT_MODE_OPTIONS = 1013017 | Grid组件编辑模式选项配置。支持属性设置，属性重置和属性获取接口。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid组件是否使用默认多选样式， 使用默认多选样式时，Grid进入编辑模式后会显示复选框。0：不使用默认样式，1：使用默认样式。默认值：1.value[1].i32：Grid组件是否启用双指滑动多选，该参数在注册[NODE_GRID_ON_EDIT_MODE_CHANGE](capi-native-node-h.md#arkui_nodeeventtype)事件回调后生效。0：使用双指划动手势不能让Grid组件进入编辑模式，但通过其他方式进入编辑模式后，编辑模式内的单指滑动多选不受影响。1：使用双指划动手势能让Grid组件从非编辑模式进入编辑模式并执行划动多选。默认值：1属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：Grid组件是否使用默认多选样式。0：不使用默认样式，1：使用默认样式。.value[1].i32：Grid组件是否启用双指滑动多选。0：不启用，1：启用。<br>**起始版本：** 26.0.0 |
| NODE_GRID_ITEM_STYLE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID_ITEM | Sets the style of the <b>GridItem</b> component.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].i32: style of the <b>GridItem</b> component, specified using [ArkUI_GridItemStyle](capi-native-type-h.md#arkui_griditemstyle). <br> The default value is <b>GRID_ITEM_STYLE_NONE</b>. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: style of the <b>GridItem</b> component, specified using [ArkUI_GridItemStyle](capi-native-type-h.md#arkui_griditemstyle). <br><br>**起始版本：** 22 |
| NODE_GRID_ITEM_SELECTABLE = 1014001 | 设置GridItem是否可以被鼠标框选。支持属性设置，属性重置和属性获取接口。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：GridItem是否可以被鼠标框选。0：不可以，1：可以。默认值：1属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：.value[0].i32：GridItem是否可以被鼠标框选。0：不可以，1：可以。<br><br>**起始版本：** 23 |
| NODE_GRID_ITEM_SELECTED = 1014002 | 设置GridItem选中状态。支持属性设置，属性重置和属性获取接口。属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：GridItem选中状态。0：未选中，1：已选中。默认值：0<br> <br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：<br> .value[0].i32：GridItem选中状态。0：未选中，1：已选中。<br><br>**起始版本：** 23 |
| NODE_TEXT_PICKER_COLUMN_WIDTHS = 15009 | Defines the column width of the text picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: percentage of total width. The default value is that all colulmns are equal width.<br> .value[1]?.f32: percentage of total width. The default value is that all colulmns are equal width.<br> .value[2]?.f32: percentage of total width. The default value is that all colulmns are equal width.<br> ...<br> .value[n]?.f32: percentage of total width. The default value is that all colulmns are equal width.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: percentage of total width.<br> value[1].f32: percentage of total width.<br> value[2].f32: percentage of total width.<br> ...<br> value[n].f32: percentage of total width.<br><br>**起始版本：** 18 |
| NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE = 16006 | Defines the disabled date range of the calendar picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: A string of dates. The `1st start date`,`1st end date`,`2nd start date`,`2nd end date`,...,`nth start date`,`nth end date` of the disabled date range.<br>  Example: 1910-01-01,1910-12-31,2020-01-01,2020-12-31<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: A string of dates.<br><br>**起始版本：** 19 |
| NODE_CALENDAR_PICKER_MARK_TODAY = 16007 | Defines whether the calendar picker marks today.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].i32: whether the calendar picker marks today. The default value is <b>false</b>.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: whether the calendar picker marks today.<br><br>**起始版本：** 19 |
| NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT | Defines the want used to start EmbeddedAbility.This attribute can be set as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The want of EmbeddedComponent, with parameter type {@AbilityBase_Want}.The default value is <b>nullptr</b>.<br><br>**起始版本：** 20 |
| NODE_EMBEDDED_COMPONENT_OPTION | Set onError and onTerminated callbacks for EMBEDDED_COMPONENT.This attribute can be set as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The option for EmbeddedComponent, with parameter type {@ArkUI_EmbeddedComponentOption}.<br><br>**起始版本：** 20 |
| NODE_PICKER_OPTION_SELECTED_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER | Defines the index of the default selected item in the data selection range of the picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: index. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: index. <br><br>**起始版本：** 23 |
| NODE_PICKER_ENABLE_HAPTIC_FEEDBACK = 1018001 | Defines whether haptic feedback.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and<b>false</b> means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: whether to feedback.<br><br>**起始版本：** 23 |
| NODE_PICKER_CAN_LOOP = 1018002 | Defines whether to support scroll looping for the picker.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to support scroll looping. The value <b>true</b> means to support scroll looping, and<b>false</b> means the opposite.<br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: The value <b>1</b> means to support scroll looping, and <b>0</b> means the opposite. <br><br>**起始版本：** 23 |
| NODE_PICKER_SELECTION_INDICATOR = 1018003 | Sets the type and parameters of the selection indicator.This attribute can be set, reset, and obtained as required through APIs.Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Format: <br> .object: Parameter type [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md).<br> Attribute fetch method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format: <br> .object: Parameter type [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md).<br>**起始版本：** 23 |
| NODE_PICKER_DISPLAYED_ITEM_COUNT = 1018004 | Sets the total number of visible items.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].i32: number of visible items. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].i32: number of visible items. <br><br>**起始版本：** 26.0.0 |
| NODE_PICKER_ITEM_HEIGHT = 1018005 | Sets the height of each item.This attribute can be set, reset, and obtained as required through APIs.Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: <br> .value[0].f32: the height of each item, in vp. <br> <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): <br> .value[0].f32: the height of each item, in vp. <br><br>**起始版本：** 26.0.0 |

### ArkUI_NodeEventType

```c
enum ArkUI_NodeEventType
```

**描述**

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NODE_TOUCH_EVENT = 0 | Defines the gesture event type.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). |
| NODE_EVENT_ON_APPEAR | Defines the mount event.This event is triggered when the component is mounted and displayed. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_EVENT_ON_DISAPPEAR | Defines the unmount event.This event is triggered when the component is unmounted and hidden. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_EVENT_ON_AREA_CHANGE | Defines the area change event.This event is triggered when the component's size, position, or any other attribute that mayaffect its display area changes. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 12 parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: original width of the target element, in vp.The value type is number. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: original height of the target element, in vp.The value type is number. <br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: original X coordinate of the target element's upper left cornerrelative to the parent element's, in vp. The value type is number. <br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>: original Y coordinate of the target element's upper left cornerrelative to the parent element's, in vp. The value type is number. <br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>: original X coordinate of the target element's upper left cornerrelative to the page's, in vp. The value type is number. <br> <b>ArkUI_NodeComponentEvent.data[5].f32</b>: original Y coordinate of the target element's upper left cornerrelative to the page's, in vp. The value type is number. <br> <b>ArkUI_NodeComponentEvent.data[6].f32</b>: new width of the target element, in vp. The value is a number. <br> <b>ArkUI_NodeComponentEvent.data[7].f32</b>: new height of the target element, in vp. The value is a number. <br> <b>ArkUI_NodeComponentEvent.data[8].f32</b>: new X coordinate of the target element's upper left corner relativeto the parent element's, in vp. The value type is number. <br> <b>ArkUI_NodeComponentEvent.data[9].f32</b>: new Y coordinate of the target element's upper left corner relativeto the parent element's, in vp. The value type is number. <br> <b>ArkUI_NodeComponentEvent.data[10].f32</b>: new X coordinate of the target element's upper left corner relativeto the page's, in vp. The value type is number. <br> <b>ArkUI_NodeComponentEvent.data[11].f32</b>: new Y coordinate of the target element's upper left corner relativeto the page's, in vp. The value type is number. |
| NODE_ON_FOCUS | Defines the focus event.This event is triggered when the component obtains the focus. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_ON_BLUR | Defines the blur event.This event is triggered when the component loses the focus. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_ON_CLICK | Defines the click event.This event is triggered when the component is clicked. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 12 parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: X coordinate of the click relative to the upper left corner of theclicked component's original area, in vp. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: Y coordinate of the click relative to the upper left corner of theclicked component's original area, in vp. <br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: event timestamp. It is the interval between the time when the eventis triggered and the time when the system starts, in microseconds. <br> <b>ArkUI_NodeComponentEvent.data[3].i32</b>: event input device. The value <b>1</b> indicates the mouse,<b>2</b> indicates the touchscreen, and <b>4</b> indicates the key. <br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>: X coordinate of the click relative to the upper left corner of theapplication window, in vp. <br> <b>ArkUI_NodeComponentEvent.data[5].f32</b>: Y coordinate of the click relative to the upper left corner of theapplication window, in vp. <br> <b>ArkUI_NodeComponentEvent.data[6].f32</b>: X coordinate of the click relative to the upper left corner of theapplication screen, in vp. <br> <b>ArkUI_NodeComponentEvent.data[7].f32</b>: Y coordinate of the click relative to the upper left corner of theapplication screen, in vp. |
| NODE_ON_TOUCH_INTERCEPT | Defines event interception.This event is triggered when the component is touched. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). |
| NODE_EVENT_ON_VISIBLE_AREA_CHANGE | Defines the visible area change event.This event is triggered when the ratio of the component's visible area to its total area is greater than or lessthan the threshold.Before registering this event, you must set <b>NODE_VISIBLE_AREA_CHANGE_RATIO</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: how the ratio of the component's visible area to its total areachanges compared to the previous one. The value <b>1</b> indicates an increase, and <b>0</b> indicates adecrease. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total area when thiscallback is invoked. |
| NODE_ON_HOVER | Defines the event triggered when the mouse pointer is moved over or away from the component.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: whether the mouse pointer is hovered over the component.The value <b>1</b> indicates that the mouse pointer is hovered over the component, and <b>0</b> indicates thatthe mouse pointer is moved away from the component. |
| NODE_ON_MOUSE | Defines the click event.This event is triggered when the component is clicked by a mouse device button or when the mouse pointer moveswithin the component. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). |
| NODE_EVENT_ON_ATTACH | Defines the attach event.This event is triggered when the component is attached. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_EVENT_ON_DETACH | Defines the detach event.This event is triggered when the component is detached. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_ON_ACCESSIBILITY_ACTIONS = 13 | Defines the accessibility action event.This event is triggered when The accessibility operation type has been set andcorresponding operations have been carried out. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].u32</b>: accessibility action type，the union type is[ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype) <br> |
| NODE_ON_PRE_DRAG = 14 | Notifies the listener of the interaction state prior to a drop and drop operation.This event is triggered when a drag operation is about to start on a draggable item. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: corresponds to {@link ArkUI_PreDragStatus}. |
| NODE_ON_DRAG_START = 15 | Called when the user starts to drag an iteA drag operation is recognized only when the dragged item is moved far enough. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_DRAG_ENTER = 16 | Called when a dragged item enters the boundaries of the current component.The current component refers to the component that listens for this event. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_DRAG_MOVE = 17 | Called  when a dragged item moves in the current component.The current component refers to the component that listens for this event. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_DRAG_LEAVE = 18 | Called when a dragged item leaves the boundaries of the current component.The current component refers to the component that listens for this event. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_DROP = 19 | Called when a dragged item is dropped on the current component.The component can obtain the drag data for processing through the callback.The current component refers to the component that listens for this event. <br> When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_DRAG_END = 20 | Called when a drag operation ends.The drag source can obtain the drag result by registering this callback.A drag operation ends when the dragged item is released.When the event callback occurs, the {@link ArkUI_DragEvent} object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_KEY_EVENT = 21 | Defines the event triggered when a key event occurs.The callback can be triggered during interactions with a focused window using an external keyboard or other inputdevice. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br><br>**起始版本：** 14 |
| NODE_ON_KEY_PRE_IME = 22 | Defines the event triggered before the input method responds to the key action.If the return value of this callback is <b>true</b>, it is considered that the key event has been consumed, andsubsequent event callbacks (<b>keyboardShortcut</b>, input method events, <b>onKeyEvent</b>) will be interceptedand no longer triggered.The callback can be triggered during interactions with a focused window using an external keyboard or other inputdevice. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br><br>**起始版本：** 14 |
| NODE_ON_FOCUS_AXIS = 23 | Defines the event triggered when the bound component receives a focus axis event after gaining focus.The event callback is triggered by interactions with a joystick and a focused component. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). <br><br>**起始版本：** 15 |
| NODE_DISPATCH_KEY_EVENT = 24 | Dispatch key event on the component node.When the component node receives a key event, this callback will be triggered instead of dispatching event to itschildren. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br><br>**起始版本：** 15 |
| NODE_ON_AXIS = 25 | Defines the event triggered when the bound component receives an axis event.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). <br><br>**起始版本：** 17 |
| NODE_ON_CLICK_EVENT = 26 | Defines the event triggered when the bound component is clicked.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).  <br><br>**起始版本：** 18 |
| NODE_ON_HOVER_EVENT = 27 | Defines the event triggered when the mouse pointer hovers over or moves away from a component.This event is triggered when the mouse pointer enters or leaves the component's bounding box. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). <br>     @since 17 |
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT = 28 | Sets the callback for the NODE_EVENT_ON_VISIBLE_AREA_CHANGE event, which limits the callback interval.The callback is triggered when the ratio of the component's visible area to its total area is greater than orless than the threshold. Before registering the callback, you must configure the threshold and update intervalusing <b>NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: how the ratio of the component's visible area to its total areachanges compared to the previous one. The value <b>1</b> indicates an increase, and <b>0</b> indicatesa decrease. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total areawhen this callback is invoked. <br><br>**起始版本：** 17 |
| NODE_ON_HOVER_MOVE = 29 | Defines the hover event.The event is triggered when the pointer is hovered by a pen device.within the component. <br> When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object.<br>**起始版本：** 15 |
| NODE_ON_SIZE_CHANGE = 30 | Defines the size change event.The event will be triggered when the component size changes.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains four parameters:<b>ArkUI_NodeComponentEvent.data[0].f32</b>: the width of the old rectangle.<b>ArkUI_NodeComponentEvent.data[1].f32</b>: the height of the old rectangle.<b>ArkUI_NodeComponentEvent.data[2].f32</b>: the width of the new rectangle.<b>ArkUI_NodeComponentEvent.data[3].f32</b>: the height of the new rectangle.<br>**起始版本：** 21 |
| NODE_ON_COASTING_AXIS_EVENT = 31 | Defines the coasting axis event.The event is triggered when user swipes with two fingers on the touchpad, the system constructssliding events based on the speed at the moment the fingers are lifted, according to a certaindecay curve. You can listen for such events to handle the flick effect immediately after theregular axis events. <br> When the event callback occurs, the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object through [OH_ArkUI_NodeEvent_GetInputEvent](capi-native-node-h.md#oh_arkui_nodeevent_getinputevent).And the [ArkUI_CoastingAxisEvent](capi-arkui-eventmodule-arkui-coastingaxisevent.md) object can be obtained from the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)object through [OH_ArkUI_UIInputEvent_GetCoastingAxisEvent](capi-ui-input-event-h.md#oh_arkui_uiinputevent_getcoastingaxisevent). <br><br>**起始版本：** 22 |
| NODE_ON_CHILD_TOUCH_TEST = 32 | Defines the pre-touch test of sub component in touch events. Called to specify how to perform the touch test on the children of this component.The event is triggered when the component is touched. <br> When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_TouchTestInfo](capi-arkui-eventmodule-arkui-touchtestinfo.md) object.<br>**起始版本：** 22 |
| NODE_ON_DIGITAL_CROWN = 33 | Defines the crown event.This event is triggered when the crown is rotated. <br> When the event callback occurs, the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.<br>**起始版本：** 24 |
| NODE_ON_CUSTOM_OVERFLOW_SCROLL = 34 | Defines the event is triggered when the <b>ARKUI_NODE_CUSTOM</b> content is scrolled.The event is triggered when the component's content is scrolled. <br> When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameters:<br> ArkUI_NodeComponentEvent.data[0].i32: id of scrolling child component. <br> ArkUI_NodeComponentEvent.data[1].f32: offset of the frame scrolling, measured in px.<br>**起始版本：** 24 |
| NODE_ON_STACK_OVERFLOW_SCROLL = 35 | Defines the event is triggered when the <b>ARKUI_NODE_STACK</b> content is scrolled.The event is triggered when the component's content is scrolled. <br> When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameters:<br> ArkUI_NodeComponentEvent.data[0].i32: id of scrolling child component. <br> ArkUI_NodeComponentEvent.data[1].f32: offset of the frame scrolling, measured in px.<br>**起始版本：** 24 |
| NODE_ON_NEED_SOFTKEYBOARD = 36 | Defines the event triggered when the component is focused and need to decide whether softkeyboard is needed.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.<br>**起始版本：** 24 |
| NODE_ON_GESTURE_COLLECT_INTERCEPT = 37 | This callback is invoked when the events and gestures on this node andhigher-priority nodes are collected. <br> This callback is used to intervene in the collection result of events and gestures. <br> When the event callback occurs, the [ArkUI_GestureCollectInterceptInfo](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md) object can be obtained from the[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_ON_DETECT_RESULT_UPDATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT | Triggers onDetectResultUpdate callbackwhen the text is set to TextDataDetectorConfig and recognized successfully.Trigger this event when TextDataDetectorConfig is set and recognized successfully.<br> When the event callback occurs, the event parameter[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)The union type in the object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)contains 1 parameter<br> <b>ArkUI_StringAsyncEvent.pStr</b>：Indicates the result of text recognition, in Json format.<br> |
| NODE_TEXT_SPAN_ON_LONG_PRESS = 1001 | Defines the long press event for span.The event is triggered when the span is long pressed.When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the[ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object.<br>**起始版本：** 20 |
| NODE_TEXT_ON_TEXT_SELECTION_CHANGE = 1002 | Defines the event triggered when the text selection position changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: start position of the text selection area. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: end position of the text selection area. <br><br>**起始版本：** 26.0.0 |
| NODE_TEXT_ON_COPY = 1003 | Defines the event triggered when the copy button on the pasteboard, which displays when the text boxis long pressed, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_ON_WILL_COPY = 1004 | Defines the event triggered before copying text.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_IMAGE_ON_COMPLETE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE | Defines the image loading success event.This event is triggered when an image is successfully loaded or decoded. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains nine parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: loading status. The value <b>0</b> indicates that the image isloaded successfully, and the value <b>1</b> indicates that the image is decoded successfully. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: width of the image, in px. <br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: height of the image, in px. <br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>: width of the component, in px. <br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>: height of the component, in px. <br> <b>ArkUI_NodeComponentEvent.data[5].f32</b>: offset of the rendered content relative to the component on thex-axis, in px. <br> <b>ArkUI_NodeComponentEvent.data[6].f32</b>: offset of the rendered content relative to the component on they-axis, in px. <br> <b>ArkUI_NodeComponentEvent.data[7].f32</b>: actual rendered width of the image, in px. <br> <b>ArkUI_NodeComponentEvent.data[8].f32</b>: actual rendered height of the image, in px. |
| NODE_IMAGE_ON_ERROR | Defines the image loading failure event.This event is triggered when an error occurs during image loading. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>error code:<br> 401: The image could not be obtained because the image path is invalid. <br> 103101: The image format is not supported. |
| NODE_IMAGE_ON_SVG_PLAY_FINISH | Defines the SVG animation playback completion event.This event is triggered when the animation playback in the loaded SVG image is complete. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_IMAGE_ON_DOWNLOAD_PROGRESS | Defines image download process event.This event is triggered when downloading webpage images from page components.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].u32</b>: the num of bytes downloaded. <br> <b>ArkUI_NodeComponentEvent.data[1].u32</b>: the total number of bytes to download. |
| NODE_TOGGLE_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE | Defines the event triggered when the toggle status changes.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter: <br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: toggle status. <b>1</b>: on; <b>0</b>: off. |
| NODE_TEXT_INPUT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT | Defines the event triggered when the text input content changes.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text input. |
| NODE_TEXT_INPUT_ON_SUBMIT | Defines the event triggered when the Enter key of the text input method is pressed.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: Enter key type of the input method. |
| NODE_TEXT_INPUT_ON_CUT | Defines the event triggered when the cut button on the pasteboard, which displays when the text boxis long pressed, is clicked.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is cut. |
| NODE_TEXT_INPUT_ON_PASTE | Defines the event triggered when the paste button on the pasteboard, which displays when the text boxis long pressed, is clicked.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is pasted<br> Since 26.0.0, the callback can return whether the paste is allowed. |
| NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE | Defines the event triggered when the text selection position changes.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: start position of the text selection area. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: end position of the text selection area. <br> |
| NODE_TEXT_INPUT_ON_EDIT_CHANGE | Defines the event triggered when the input status changes.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: <b>true</b> indicates that text input is in progress. <br> |
| NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE | textInput This event is triggered when the input content changes.Conditions for triggering this event: When the input content changes. <br> When the event callback occurs, the union type in the event parameter[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 2 parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: Indicates the width of the text. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: Indicates the height of the text. <br> |
| NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR | Defines the event triggered when matching with the regular expression specified by<b>NODE_TEXT_INPUT_INPUT_FILTER</b> fails.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: content that is filtered out when regular expression matching fails. <br> |
| NODE_TEXT_INPUT_ON_CONTENT_SCROLL | This callback is triggered when the text content is scrolled.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: Indicates the horizontal offset of the text in the content area. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: Indicates the vertical coordinate offset of <br> the text in the content area. <br> |
| NODE_TEXT_INPUT_ON_WILL_INSERT = 7009 | Defines the event triggered when text is about to be entered.The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <br> value.f32: position of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. <br> buffer: string value of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetStringValue</b>. |
| NODE_TEXT_INPUT_ON_DID_INSERT = 7010 | Defines the event triggered when text is entered.The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <br> value.f32: position of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. <br> buffer: string value of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetStringValue</b>. |
| NODE_TEXT_INPUT_ON_WILL_DELETE = 7011 | Defines the event triggered when text is about to be deleted.The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <br> value.f32: position of the text to delete, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. <br> value.i32: direction for deleting the text, with the index of <b>1</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. The value <b>0</b> indicates backward-delete, and <b>1</b> indicatesforward-delete. <br> buffer: string value of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetStringValue</b>. |
| NODE_TEXT_INPUT_ON_DID_DELETE = 7012 | Defines the event triggered when text is deleted.The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <br> value.f32: position of the text deleted, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. <br> value.i32: direction for deleting the text, with the index of <b>1</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. The value <b>0</b> indicates backward-delete, and <b>1</b> indicatesforward-delete. <br> buffer: string value of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetStringValue</b>. |
| NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT = 7013 | Defines the event triggered when content (including preview text) changes in the <b>TextInput</b>component.When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). <br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters: <br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the <b>TextInput</b> component.<b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the <b>TextInput</b> component.<b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the <b>TextInput</b> component.<br>**起始版本：** 15 |
| NODE_TEXT_INPUT_ON_WILL_CHANGE = 7014 | Defines the event triggered before content changesWhen the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). <br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters: <br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the <b>TextInput</b> component.<b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the <b>TextInput</b> component.<b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the <b>TextInput</b> component.<br>**起始版本：** 20 |
| NODE_TEXT_INPUT_ON_COPY = 7015 | Defines the event triggered when the copy button on the pasteboard, which displays when text isselected, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_ON_WILL_COPY = 7016 | Defines the event triggered before copying text.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_INPUT_ON_WILL_CUT = 7017 | Defines the event triggered before cutting text.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is cut.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA | Defines the event triggered when the input in the text box changes.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text entered. |
| NODE_TEXT_AREA_ON_PASTE | Defines the event triggered when the paste button on the pasteboard, which displays when the text box islong pressed, is clicked.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is pasted<br> Since 26.0.0, the callback can return whether the paste is allowed. |
| NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE | Defines the event triggered when the text selection position changes.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: start position of the text selection area. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: end position of the text selection area. <br> |
| NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR | Defines the event triggered when matching with the regular expression specified by<b>NODE_TEXT_AREA_INPUT_FILTER</b> fails.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: content that is filtered out when regular expression matching fails. <br> |
| NODE_TEXT_AREA_ON_CONTENT_SCROLL | This callback is triggered when the text content is scrolled.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: Indicates the horizontal offset of the text in the content area. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: Indicates the vertical coordinate offset of <br> the text in the content area. <br> |
| NODE_TEXT_AREA_ON_EDIT_CHANGE | Defines the event triggered when the input status changes.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: <b>true</b> indicates that text input is in progress. <br> |
| NODE_TEXT_AREA_ON_SUBMIT | Defines the event triggered when the Enter key on the keyboard is pressed for the multi-line text box.This event is not triggered when <b>keyType</b> is <b>ARKUI_ENTER_KEY_TYPE_NEW_LINE</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: type of the Enter key. |
| NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE | textArea This event is triggered when the input content changes.Conditions for triggering this event: When the input content changes. <br> When the event callback occurs, the union type in the event parameter [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 2 parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: Indicates the width of the text. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: Indicates the height of the text. <br> |
| NODE_TEXT_AREA_ON_WILL_INSERT = 8008 | Defines the event triggered when text is about to be entered.The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <br> value.f32: position of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. <br> buffer: string value of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetStringValue</b>. |
| NODE_TEXT_AREA_ON_DID_INSERT = 8009 | Defines the event triggered when text is entered.The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <br> value.f32: position of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. <br> buffer: string value of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetStringValue</b>. |
| NODE_TEXT_AREA_ON_WILL_DELETE = 8010 | Defines the event triggered when text is about to be deleted.The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <br> value.f32: position of the text to delete, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. <br> value.i32: direction for deleting the text, with the index of <b>1</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. The value <b>0</b> indicates backward-delete, and <b>1</b> indicatesforward-delete. <br> buffer: string value of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetStringValue</b>. |
| NODE_TEXT_AREA_ON_DID_DELETE = 8011 | Defines the event triggered when text is deleted.The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <br> value.f32: position of the text deleted, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. <br> value.i32: direction for deleting the text, with the index of <b>1</b>; obtained using<b>OH_ArkUI_NodeEvent_GetNumberValue</b>. The value <b>0</b> indicates backward-delete, and <b>1</b> indicatesforward-delete. <br> buffer: string value of the text, with the index of <b>0</b>; obtained using<b>OH_ArkUI_NodeEvent_GetStringValue</b>. |
| NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT = 8012 | Defines the event triggered when content (including preview text) changes in the <b>TextArea</b>component.When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). <br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters: <br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the <b>TextArea</b> component.<b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the <b>TextArea</b> component.<b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the <b>TextArea</b> component.<br>**起始版本：** 15 |
| NODE_TEXT_AREA_ON_WILL_CHANGE = 8013 | Defines the event triggered before content changes.When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). <br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters: <br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the <b>TextArea</b> component.<b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the <b>TextArea</b> component.<b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the <b>TextArea</b> component.<br>**起始版本：** 20 |
| NODE_TEXT_AREA_ON_COPY = 8014 | Defines the event triggered when the copy button on the pasteboard, which displays when the text boxis long pressed, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_ON_WILL_COPY = 8015 | Defines the event triggered before copying text.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is copied.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_ON_CUT = 8016 | Defines the event triggered when the cut button on the pasteboard, which displays when the text boxis long pressed, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is cut.<br>**起始版本：** 26.0.0 |
| NODE_TEXT_AREA_ON_WILL_CUT = 8017 | Defines the event triggered before cutting text.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is cut.<br>**起始版本：** 26.0.0 |
| NODE_CHECKBOX_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX | Defines the event triggered when the selected status of the <b>ARKUI_NODE_CHECKBOX</b> component changes.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> <b>ArkUI_NodeComponentEvent.data[0].i32</b><b>1</b>: selected; <b>0</b>: not selected. |
| NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER | Defines the event triggered when a date is selected in the <b>ARKUI_NODE_DATE_PICKER</b> component.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains three parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: year of the selected date. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: month of the selected date. Value range: [0-11]. <br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: day of the selected date. |
| NODE_TIME_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER | Defines the event triggered when a time is selected in the <b>ARKUI_NODE_TIME_PICKER</b> component.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: hour of the selected time. Value range: [0-23]. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: minute of the selected time. Value range: [0-59]. |
| NODE_TEXT_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER | Defines the event triggered when an item is selected in the <b>ARKUI_NODE_TEXT_PICKER</b> component.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0...11].i32</b>: value of the selected item. |
| NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP = 15001 | Defines the event triggered when an item is selected and scrolling has stopped in the<b>ARKUI_NODE_TEXT_PICKER</b> component.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0...11].i32</b>: value of the selected item. <br><br>**起始版本：** 14 |
| NODE_CALENDAR_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER | Defines the event triggered when a date is selected in the <b>NODE_CALENDAR_PICKER</b>.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> <b>ArkUI_NodeComponent.data[0].u32</b>: year of the selected date. <br> <b>ArkUI_NodeComponent.data[1].u32</b>: month of the selected date. <br> <b>ArkUI_NodeComponent.data[2].u32</b>: day of the selected date. |
| NODE_SLIDER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER | Defines the event triggered when the <b>ARKUI_NODE_SLIDER</b> component is dragged or clicked.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: current slider value. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: state triggered by the event. |
| NODE_RADIO_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO | Defines the event callback function triggered when an object is dragged or clicked by ARKUI_NODE_RADIO.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains one parameter:<br> ArkUI_NodeComponentEvent.data[0].i32: option button status. |
| NODE_IMAGE_ANIMATOR_EVENT_ON_START = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_ANIMATOR | Defines the event callback function triggered when the animation starts to play.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_IMAGE_ANIMATOR_EVENT_ON_PAUSE = 19001 | Defines the event callback function triggered when the animation playback is paused.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_IMAGE_ANIMATOR_EVENT_ON_REPEAT = 19002 | Defines the event callback function triggered when the animation playback is repeated.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_IMAGE_ANIMATOR_EVENT_ON_CANCEL = 19003 | Defines the event callback function when the animation playback returns to the initial state.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_IMAGE_ANIMATOR_EVENT_ON_FINISH = 19004 | Defines the event callback function triggered when the animation playback is complete or stopped.When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains no parameter:<br> |
| NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP | Defines the callback triggered when the selected status of the <b>ARKUI_NODE_CHECKBOX_GROOUP</b>or checkbox changes.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br> <b>ArkUI_StringAsyncEvent.pStr</b>Name: The names of the selected checkboxes;Status:0: All checkboxes are selected.1: Some checkboxes are selected.2: No checkboxes are selected. <br><br>**起始版本：** 15 |
| NODE_TEXT_EDITOR_ON_SELECTION_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR | 定义TextEditor组件中选区或光标位置发生变化时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含两个参数：<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：选区起始索引。<br><b>ArkUI_NodeComponentEvent.data[1].i32</b>：选区结束索引。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_READY | 定义TextEditor组件首次初始化完成时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_PASTE | 定义TextEditor组件执行粘贴时触发的事件。<br>系统会根据回调函数返回值判断是否拦截组件的默认行为。<br>可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。<br>返回值中索引为0的value.i32表示是否拦截组件的默认行为。<br>0：不拦截。1：拦截。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_EDITING_CHANGE | 定义TextEditor组件编辑状态发生变化时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含一个参数：<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：组件的编辑状态。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_SUBMIT | 定义TextEditor组件输入法的回车键被按下时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含一个参数：<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：输入法的回车键类型[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_CUT | 定义TextEditor组件执行剪切时触发的事件。<br>系统会根据回调函数返回值判断是否拦截组件的默认行为。<br>可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。<br>返回值中索引为0的value.i32表示是否拦截组件的默认行为。<br>0：不拦截。1：拦截。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_COPY | 定义TextEditor组件执行复制时触发的事件。<br>系统会根据回调函数返回值判断是否拦截组件的默认行为。<br>可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。<br>返回值中索引为0的value.i32表示是否拦截组件的默认行为。<br>0：不拦截。1：拦截。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_WILL_CHANGE | 定义TextEditor组件在内容将要改变时触发的事件。<br>在任何导致文本内容发生变化的操作生效之前会触发该回调，开发者可根据回调事件中的信息决定是否拦截本次内容变更。<br>当事件回调发生时，可以通过[OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent](capi-native-node-h.md#oh_arkui_nodeevent_gettexteditoronwillchangeevent)从[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获得[OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md)对象。<br>使用OH_ArkUI_TextEditorChangeEvent_XXX系列接口可以从该对象中获取更多信息。<br>系统会根据回调函数返回值判断当前内容是否允许被更改。<br>可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。<br>返回值中索引为0的value.i32表示当前内容是否允许被更改。<b>0</b>：不允许更改。<b>1</b>：允许更改。<br>**起始版本：** 24 |
| NODE_TEXT_EDITOR_ON_DID_CHANGE | 定义TextEditor组件在内容改变时触发的事件。<br>事件回调触发时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含四个参数：<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：文本变化前将要被替换的文本范围的起始索引。<br><b>ArkUI_NodeComponentEvent.data[1].i32</b>：文本变化前将要被替换的文本范围的结束索引。<br><b>ArkUI_NodeComponentEvent.data[2].i32</b>：文本变化后新增内容的文本范围的起始索引。<br><b>ArkUI_NodeComponentEvent.data[3].i32</b>：文本变化后新增内容的文本范围的结束索引。<br>**起始版本：** 24 |
| NODE_SWIPER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER | Defines the event triggered when the index of the currently displayed element of this<b>ARKUI_NODE_SWIPER</b> instance changes.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently displayed element. |
| NODE_SWIPER_EVENT_ON_ANIMATION_START | Defines the event triggered when the switching animation of this <b>ARKUI_NODE_SWIPER</b> instance starts.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains five parameters: <br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently displayed element. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: index of the target element to switch to. <br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: offset of the currently displayed element relative to thestart position of the swiper along the main axis. <br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>: offset of the target element relative to the start positionof the swiper along the main axis. <br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>: hands-off velocity. |
| NODE_SWIPER_EVENT_ON_ANIMATION_END | Defines the event triggered when the switching animation of this <b>ARKUI_NODE_SWIPER</b> instance ends.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently displayed element. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: offset of the currently displayed element relative to thestart position of the swiper along the main axis. |
| NODE_SWIPER_EVENT_ON_GESTURE_SWIPE | Defines the event triggered on a frame-by-frame basis when the page is turned by a swipe in this<b>ARKUI_NODE_SWIPER</b> instance.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently displayed element. <br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: offset of the currently displayed element relative to thestart position of the swiper along the main axis. |
| NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL | Define the <b>ARKUI_NODE_SWIPER</b> to listen for Swiper page slide events.Instruction: <br> 1. If the {@link ArkUI_SwiperDisplayModeType} attribute is set to <br> ARKUI_SWIPER_DISPLAY_MODE_AUTO_LINEAR, the interface does not take effect. <br> 2, circular scenario, set prevMargin and nextMargin attributes, <br> so that Swiper front and back end display the same page, the interface does not take effect. <br> 3. During page sliding, the ContentDidScrollCallback callback is <br> triggered frame-by-frame for all pages in the window. <br> For example, when there are two pages in the window with subscripts 0 and 1, <br> callbacks with index values 0 and 1 are triggered twice per frame. <br> 4, set the swipeByGroup parameter of the displayCount property to <br> true if at least one page in the same group is in the window, <br> A callback is triggered for all pages in the group. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains four parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b> : indicates the index of the Swiper component, <br> which is consistent with the index change in the onChange event. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b> : The index of a page in the window. <br> <b>ArkUI_NodeComponentEvent.data[2].f32</b> : The proportion of page movement relative to <br> the start position of the Swiper spindle (selectedIndex corresponds to the start position of the page). <br> <b>ArkUI_NodeComponentEvent.data[3].f32</b> : The length of the page in the axis direction. |
| NODE_SWIPER_EVENT_ON_SELECTED = 1001005 | Defines the event triggered when the selected index of the <b>ARKUI_NODE_SWIPER</b> changed.This event is triggered under the following scenarios: <br> 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meetsthe threshold for page turning. <br> 2. When the page is changed programmatically using either <b>NODE_SWIPER_INDEX</b> or<b>NODE_SWIPER_SWIPE_TO_INDEX</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently selected element. <br><br>**起始版本：** 18 |
| NODE_SWIPER_EVENT_ON_UNSELECTED = 1001006 | Defines the event triggered when the selected index of the <b>ARKUI_NODE_SWIPER</b> changed.This event is triggered under the following scenarios: <br> 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meetsthe threshold for page turning. <br> 2. When the page is changed programmatically using either <b>NODE_SWIPER_INDEX</b> or<b>NODE_SWIPER_SWIPE_TO_INDEX</b>. <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: the index of the element becomes unselected. <br><br>**起始版本：** 18 |
| NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL = 1001007 | Defines the event triggered when content in the swiper component will scroll.Instructions: Before page scrolling, the </b>ContentWillScrollCallback</b> callback is invoked.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains three parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: the index value of the current child page. <br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: the index value of the child page that will display. <br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: the sliding offset of each frame.Positive numbers indicating slide backward(e.g. from index=1 to index=0), negative numbers indicatingslide forward(e.g. from index=0 to index=1). <br><br>**起始版本：** 15 |
| NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED = 1001008 | Defines the <b>ARKUI_NODE_SWIPER</b> scroll state change event.This event is triggered when the scroll state of the <b>Swiper</b> component changes during user dragging,during the animation phase after the user lifts their finger, or upon stopping of scrolling.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: current scroll state. The parameter type is[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate). <br><br>**起始版本：** 20 |
| NODE_SCROLL_EVENT_ON_SCROLL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SCROLL | Event triggered when scrolling occurs. This event is triggered under the following scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: horizontal scrolling offset.<br>*ArkUI_NodeComponentEvent.data[1].f32**: vertical scrolling offset. |
| NODE_SCROLL_EVENT_ON_SCROLL_FRAME_BEGIN | Event triggered when the scrollable container starts scrolling in each frame. The **List**, **Scroll**,and **WaterFlow** components support this event since API version 12, and the **Grid** component supports thisevent since API version 22.<br>This event is triggered under the following scenarios:<br>1. This event is triggered when scrolling is started by the scrollable component (supports keyboard, mouse,and other input methods that trigger scrolling).<br>2. This event is not triggered when the controller API is called.<br>3. This event is not triggered when the component bounces back out of bounds.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: amount to scroll by.<br>*ArkUI_NodeComponentEvent.data[1].i32**: current scroll state.<br>*::ArkUI_NodeComponentEvent** contains one return value:<br>*ArkUI_NodeComponentEvent.data[0].f32**: The event handler can work out the amount by which the componentneeds to scroll based on the real-world situation and return the result in this parameter. |
| NODE_SCROLL_EVENT_ON_WILL_SCROLL | Event triggered when the scrollable container is about to scroll. This event is triggered under thefollowing scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame, in vp. The offset is positive whenthe content is scrolled left and negative when the content is scrolled right.<br>*ArkUI_NodeComponentEvent.data[1].f32**: scroll offset of each frame, in vp. The offset is positive whenthe content is scrolled up and negative when the content is scrolled down.<br>*ArkUI_NodeComponentEvent.data[2].i32**: current scroll state. The parameter type is[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate).<br>*ArkUI_NodeComponentEvent.data[3].i32**: current scroll source. The parameter type is[ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource). |
| NODE_SCROLL_EVENT_ON_DID_SCROLL | Event triggered when the scrollable container scrolls. This event is triggered under the followingscenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame, in vp. The offset is positive whenthe content is scrolled left and negative when the content is scrolled right.<br>*ArkUI_NodeComponentEvent.data[1].f32**: scroll offset of each frame, in vp. The offset is positive whenthe content is scrolled up and negative when the content is scrolled down.<br>*ArkUI_NodeComponentEvent.data[2].i32**: current scroll state. The parameter type is[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate). |
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
| NODE_LIST_ON_WILL_SCROLL | Event triggered when the [ARKUI_NODE_LIST](capi-native-node-h.md#arkui_nodetype) component is about to scroll. This event is triggered inthe following scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame. The offset is positive when the listis scrolled up and negative when the list is scrolled down.<br>*ArkUI_NodeComponentEvent.data[1].i32**: current scroll state. The parameter type is[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate).<br>*ArkUI_NodeComponentEvent.data[2].i32**: current scroll source. The parameter type is[ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource). |
| NODE_LIST_ON_DID_SCROLL | Event triggered when the [ARKUI_NODE_LIST](capi-native-node-h.md#arkui_nodetype) component scrolls. This event is triggered under thefollowing scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame. The offset is positive when the listis scrolled up and negative when the list is scrolled down.<br>*ArkUI_NodeComponentEvent.data[1].i32**: current scroll state. |
| NODE_LIST_ON_SCROLL_VISIBLE_CONTENT_CHANGE | 定义ARKUI_NODE_LIST当前显示内容发生改变的时候触发事件枚举值。触发该事件的条件 ：列表初始化时会触发一次，List显示区域内第一个子组件的索引值或最后一个子组件的索引值有变化时会触发。计算触发条件时，每一个ListItem、ListItemGroup中的header或footer都算一个子组件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含6个参数：<b>ArkUI_NodeComponentEvent.data[0].i32</b>：List显示区域内第一个子组件的索引值。<b>ArkUI_NodeComponentEvent.data[1].i32</b>：List显示区域起始端在ListItemGroup中的区域。类型为[ArkUI_ListItemGroupArea](capi-native-type-h.md#arkui_listitemgrouparea)。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：List显示区域起始端在ListItemGroup中的ListItem索引号，如果List显示区域起始端不在ListItem上，该值为-1。<b>ArkUI_NodeComponentEvent.data[3].i32</b>：List显示区域内最后一个子组件的索引值。<b>ArkUI_NodeComponentEvent.data[4].i32</b>：List显示区域末尾端在ListItemGroup中的区域。类型为[ArkUI_ListItemGroupArea](capi-native-type-h.md#arkui_listitemgrouparea)。<b>ArkUI_NodeComponentEvent.data[5].i32</b>：List显示区域末尾端在ListItemGroup中的ListItem索引号，如果List显示区域末尾端不在ListItem上，该值为-1。<br>**起始版本：** 15 |
| NODE_LIST_ON_EDIT_MODE_CHANGE = 1003004 | 定义List组件编辑模式状态变更事件枚举值。触发该事件的条件 ：1. 设置NODE_LIST_ENABLE_EDIT_MODE属性改变编辑模式状态。2. 当NODE_LIST_EDIT_MODE_OPTIONS开启双指滑动多选时，双指滑动触发多选状态变更。注册该事件回调是双指滑动进入多选状态的必要条件。如未注册该回调，双指滑动将不会进入多选状态。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<b>ArkUI_NodeComponentEvent.data[0].i32</b>：编辑模式状态。0：非编辑模式。1：编辑模式。<br>**起始版本：** 26.0.0 |
| NODE_LIST_ITEM_ON_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM | Defines the selected state change event of the <b>ListItem</b> component.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<b>ArkUI_NodeComponentEvent.data[0].i32</b>: selected state. <b>0</b>: not selected. <b>1</b>: selected.<br>**起始版本：** 26.0.0 |
| NODE_REFRESH_STATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_REFRESH | Defines the event triggered when the refresh state of the <b>ARKUI_NODE_REFRESH</b> object changes.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: refresh state. |
| NODE_REFRESH_ON_REFRESH | 定义ARKUI_NODE_REFRESH进入刷新状态时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中不包含参数： |
| NODE_REFRESH_ON_OFFSET_CHANGE | 定义ARKUI_NODE_REFRESH下拉距离发生变化时触发该事件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：下拉距离。 |
| NODE_ON_WILL_SCROLL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_WATER_FLOW | Event triggered when the **ARKUI_NODE_WATER_FLOW** component is about to scroll. This event is triggeredunder the following scenarios:<br>1. Scrolling is started by the scrollable component (supports keyboard, mouse, and other input methods thattrigger scrolling).<br>2. Scrolling is initiated by calling the controller API.<br>3. The out-of-bounds bounce effect is active.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].f32**: scroll offset of each frame. The offset is positive when thecontent is scrolled up and negative when the content is scrolled down.<br>*ArkUI_NodeComponentEvent.data[1].i32**: current scroll state. The parameter type is[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate).<br>*ArkUI_NodeComponentEvent.data[2].i32**: current scroll source. The parameter type is[ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource). |
| NODE_WATER_FLOW_ON_DID_SCROLL | 定义ARKUI_NODE_WATER_FLOW组件的滑动时触发事件枚举值。触发该事件的条件 ：1. 滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。2. 通过滚动控制器API接口调用。3. 越界回弹。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：每帧滚动的偏移量，内容向上滚动时偏移量为正，向下滚动时偏移量为负。<b>ArkUI_NodeComponentEvent.data[1].i32</b>：当前滑动状态。 |
| NODE_WATER_FLOW_ON_SCROLL_INDEX | Defines the enumerated values of the event triggered,when the subcomponent of the start position or end position displayed in the current waterfall changes.Condition for triggering the event: <br> This event is triggered when the index value of the <br> first or last subcomponent in the waterfall display area changes. <br> When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br> {@Link ArkUI_NodeComponentEvent}. <br> {@Link ArkUI_NodeComponentEvent} contains two parameters: <br> ArkUI_NodeComponentEvent.data[0].i32: The index value of the <br> start position of the currently displayed WaterFlow. <br> ArkUI_NodeComponentEvent.data[1].i32: The index value of <br> the end position of the currently displayed waterfall. |
| NODE_GRID_ON_SCROLL_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID | Event triggered when a child component of **ARKUI_NODE_GRID** enters or leaves the grid display area.This event is triggered under the following scenarios:<br>This event is triggered once when the grid is initialized and when the index of the first child component orthe last child component in the grid display area changes.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br>*ArkUI_NodeComponentEvent.data[0].i32**: index of the first child component in the grid display area.<br>*ArkUI_NodeComponentEvent.data[1].i32**: index of the last child component in the grid display area.<br>**起始版本：** 22 |
| NODE_GRID_ON_WILL_SCROLL = 1013001 | 定义ARKUI_NODE_GRID组件的滑动前触发事件枚举值。触发该事件的条件 ：1. 滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。2. 通过滚动控制器API接口调用。3. 越界回弹。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：每帧滚动的偏移量，Grid内容向上滚动时偏移量为正，向下滚动时偏移量为负。<b>ArkUI_NodeComponentEvent.data[1].i32</b>：当前滑动状态，参数类型[ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate)。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：当前滚动的来源，参数类型[ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource)。<br>**起始版本：** 22 |
| NODE_GRID_ON_DID_SCROLL = 1013002 | 定义ARKUI_NODE_GRID组件的滑动时触发事件枚举值。触发该事件的条件 ：1. 滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。2. 通过滚动控制器API接口调用。3. 越界回弹。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：每帧滚动的偏移量，Grid内容向上滚动时偏移量为正，向下滚动时偏移量为负。<b>ArkUI_NodeComponentEvent.data[1].i32</b>：当前滑动状态。<br>**起始版本：** 22 |
| NODE_GRID_ON_SCROLL_BAR_UPDATE = 1013003 | 定义ARKUI_NODE_GRID组件每帧布局结束时触发用于设置滚动条的位置及长度的事件枚举值。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.i32：当前显示的网格起始位置的索引值。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.f32：当前显示的网格起始位置元素相对网格显示起始位置的偏移，单位vp。<br>**起始版本：** 22 |
| NODE_GRID_ON_ITEM_DRAG_START = 1013004 | 定义ARKUI_NODE_GRID组件拖拽子组件开始事件枚举值。触发该事件的条件：1. 设置NODE_GRID_EDIT_MODE为1。2. 在Grid子组件上长按并拖动产生足够位移距离时触发。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：当前拖拽点相对Grid组件的x坐标，单位vp。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.f32：当前拖拽点相对Grid组件的y坐标，单位vp。通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为2的value.i32：被拖拽子组件在Grid组件中的索引值。<br>**起始版本：** 23 |
| NODE_GRID_ON_ITEM_DRAG_ENTER = 1013005 | 定义拖拽子组件进入当前Grid组件范围事件枚举值。触发该事件的条件：通过NODE_GRID_ON_ITEM_DRAG_START事件成功拖拽的子组件进入当前Grid组件范围。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：当前拖拽点相对Grid组件的x坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[1].f32</b>：当前拖拽点相对Grid组件的y坐标，单位vp。<br>**起始版本：** 23 |
| NODE_GRID_ON_ITEM_DRAG_MOVE = 1013006 | 定义拖拽子组件在当前Grid组件范围内移动事件枚举值。触发该事件的条件：通过NODE_GRID_ON_ITEM_DRAG_START事件成功拖拽的子组件在当前Grid组件范围内移动。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含4个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：当前拖拽点相对Grid组件的x坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[1].f32</b>：当前拖拽点相对Grid组件的y坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：被拖拽子组件在被拖拽Grid组件中的索引值。<b>ArkUI_NodeComponentEvent.data[3].i32</b>：被拖拽子组件当前位置在当前Grid组件中的索引值。<br>**起始版本：** 23 |
| NODE_GRID_ON_ITEM_DRAG_LEAVE = 1013007 | 定义拖拽子组件离开当前Grid组件范围事件枚举值。触发该事件的条件：通过NODE_GRID_ON_ITEM_DRAG_START事件成功拖拽的子组件离开当前Grid组件范围。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含3个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：当前拖拽点相对Grid组件的x坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[1].f32</b>：当前拖拽点相对Grid组件的y坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：被拖拽子组件在被拖拽Grid组件中的索引值。<br>**起始版本：** 23 |
| NODE_GRID_ON_ITEM_DROP = 1013008 | 定义松手释放拖拽子组件事件枚举值。触发该事件的条件：松手释放通过NODE_GRID_ON_ITEM_DRAG_START事件成功拖拽的子组件。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含5个参数：<b>ArkUI_NodeComponentEvent.data[0].f32</b>：当前拖拽点相对Grid组件的x坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[1].f32</b>：当前拖拽点相对Grid组件的y坐标，单位vp。<b>ArkUI_NodeComponentEvent.data[2].i32</b>：被拖拽子组件在被拖拽Grid中的索引值。<b>ArkUI_NodeComponentEvent.data[3].i32</b>：被拖拽子组件当前位置在当前Grid组件中的索引值。<b>ArkUI_NodeComponentEvent.data[4].i32</b>：被拖拽子组件是否成功释放，1表示释放位置在Grid组件范围内，0表示释放位置在Grid组件范围外。<br>**起始版本：** 23 |
| NODE_GRID_ON_EDIT_MODE_CHANGE = 1013009 | 定义Grid组件编辑模式状态变更事件枚举值。触发该事件的条件 ：1. 设置NODE_GRID_ENABLE_EDIT_MODE属性改变编辑模式状态。2. 当NODE_GRID_EDIT_MODE_OPTIONS开启双指滑动多选时，双指滑动触发多选状态变更。注册该事件回调是双指滑动进入多选状态的必要条件。如未注册该回调，双指滑动将不会进入多选状态。事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：<b>ArkUI_NodeComponentEvent.data[0].i32</b>：编辑模式状态。0：非编辑模式。1：编辑模式。<br>**起始版本：** 26.0.0 |
| NODE_GRID_ITEM_ON_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID_ITEM | Selected state change event of the **ARKUI_NODE_GRID_ITEM** component.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:<br>*ArkUI_NodeComponentEvent.data[0].i32**: **0** (not selected) or **1** (selected).<br>**起始版本：** 23 |
| NODE_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER | Defines the event triggered when an item is selected in the <b>ARKUI_NODE_PICKER</b> component.      <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0...11].i32</b>: value of the selected item. <br><br>**起始版本：** 23 |
| NODE_PICKER_EVENT_ON_SCROLL_STOP = 1018001 | Defines the event triggered when an item is selected and scrolling has stopped in the<b>ARKUI_NODE_PICKER</b> component.When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br> <b>ArkUI_NodeComponentEvent.data[0...11].i32</b>: value of the selected item. <br><br>**起始版本：** 23 |

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
| [ArkUI_UIInputEvent*](capi-arkui-eventmodule-arkui-uiinputevent.md) | ArkUI_UIInputEvent 输入事件数据指针。 |

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

Obtains the numeric-type parameter of a component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Indicates the pointer to the component event. |
| int32_t index | Indicates the index of the return value. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Indicates the return value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) if the parameter length exceeds<br>         the limit.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the data does not exist in the component event. |

### OH_ArkUI_NodeEvent_GetStringValue()

```c
int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)
```

**描述**

Obtains the string-type parameter of a component event. The string data is valid only during an eventcallback. To use it outside an event callback, you are advised to copy the string data.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Indicates the pointer to the component event. |
| int32_t index | Indicates the index of the return value. |
| char** string | Indicates the pointer to the string array. |
| int32_t* stringSize | Indicates the length of the string array. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) if the parameter length exceeds<br>         the limit.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the data does not exist in the component event. |

### OH_ArkUI_NodeEvent_SetReturnNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)
```

**描述**

Sets the return value for a component event.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Indicates the pointer to the component event. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Indicates the numeric-type array. |
| int32_t size | Indicates the array length. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN](capi-native-type-h.md#arkui_errorcode) if the component event does not support return values.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if data does not exist in the component event. |

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
| [ArkUI_TouchTestInfo*](capi-arkui-eventmodule-arkui-touchtestinfo.md) | 返回指向[ArkUI_TouchTestInfo](capi-arkui-eventmodule-arkui-touchtestinfo.md)对象的指针。若传入的参数无效或并非触摸测试信息，则返回null。 |

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
| [OH_ArkUI_TextEditorChangeEvent*](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | 指向[OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md)数据对象的指针。<br>     <br>若传入的参数无效或并非TextEditor组件文本内容变化事件信息，则返回<b>null</b>。 |

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

Sets the total number of elements in the specified adapter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t size | Indicates the number of elements. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

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
int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(
ArkUI_NodeAdapterHandle handle, void* userData, void (*receiver)(ArkUI_NodeAdapterEvent* event))
```

**描述**

Registers an event callback for the adapter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| void\* userData | Indicates custom data. |
| void (\*receiver)(ArkUI_NodeAdapterEvent\* event) | Indicates the event receiver callback. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

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

Instructs the specified adapter to reload all elements.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_ReloadItem()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述**

Instructs the specified adapter to reload certain elements.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t startPosition | Indicates the start position of the elements to reload. |
| uint32_t itemCount | Indicates the number of the elements to reload.@return Returns the error code.Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_RemoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_RemoveItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述**

Instructs the specified adapter to remove certain elements.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t startPosition | Indicates the start position of the elements to remove. |
| uint32_t itemCount | Indicates the number of the elements to remove. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_InsertItem()

```c
int32_t OH_ArkUI_NodeAdapter_InsertItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**描述**

Instructs the specified adapter to insert certain elements.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t startPosition | Indicates the start position of the elements to insert. |
| uint32_t itemCount | Indicates the number of the elements to insert. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_MoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)
```

**描述**

Instructs the specified adapter to move certain elements.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t from | Indicates the start position of the elements to move. |
| uint32_t to |  Indicates the end position of the elements to move. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_GetAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)
```

**描述**

Obtains all elements stored in the specified adapter.This API returns the pointer to the array of the elements. You need to manually release the memory datato which the pointer points.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)** items | Indicates the pointer to the array of the elements in the adapter. |
| uint32_t* size | Indicates the number of elements. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

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

Sets the component to be added to the specified adapter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the component to be added. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapterEvent_SetNodeId()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)
```

**描述**

Sets the component ID to be generated.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |
| int32_t id | Indicates the component ID to set. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

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
| int32_t | Returns the result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

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
| int32_t | Returns the result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

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
| int32_t | Returns the result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

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

register a callback function to a node content.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | Indicates the pointer to the node content instance. |
| [ArkUI_NodeContentCallback](capi-native-node-h.md#arkui_nodecontentcallback) callback | Indicates the callback function. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

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
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

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

Add a node to a node content.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | Indicates the pointer to the node content instance. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the pointer to the node |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-native-type-h.md#arkui_errorcode) if the node has already been adopted. add since api 22. |

### OH_ArkUI_NodeContent_RemoveNode()

```c
int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**描述**

remove a node from a node content.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | Indicates the pointer to the node content instance. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the pointer to the node |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeContent_InsertNode()

```c
int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)
```

**描述**

insert a node into a node content at a given position.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | Indicates the pointer to the node content instance. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the pointer to the node |
| int32_t position | Indicates the position for inserting the node |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-native-type-h.md#arkui_errorcode) if the node has already been adopted. add since api 22. |

### OH_ArkUI_NodeUtils_GetLayoutSize()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)
```

**描述**

Get the size of the component layout area.The layout area size does not include graphic variation attributes such as scaling.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md)* size | The drawing area size of the component handle, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPosition()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)
```

**描述**

Obtain the position of the component layout area relative to the parent component.The relative position of the layout area does not include graphic variation attributes, such as translation.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* localOffset | The offset value of the component handle relative to the parent component, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**描述**

Obtain the position of the component layout area relative to the window.The relative position of the layout area does not include graphic variation attributes, such as translation.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | The offset value of the component handle relative to the window, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)
```

**描述**

Obtain the position of the component layout area relative to the screen.The relative position of the layout area does not include graphic variation attributes, such as translation.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* screenOffset | The offset value of the component handle relative to the screen, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)
```

**描述**

Obtains the offset of a component relative to the global display.The relative position does not count in transformation attributes, such as translate.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the <b>ArkUI_NodeHandle</b> representing the component. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* offset | Offset of the component relative to the global display, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Result code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

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
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

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
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_AddCustomProperty()

```c
void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)
```

**描述**

Add the custom property of the component. This interface only works on the main thread.

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| const char* name | The name of the custom property. Passing null pointers is not allowed. |
| const char* value | The value of the custom property. Passing null pointers is not allowed. |

### OH_ArkUI_NodeUtils_RemoveCustomProperty()

```c
void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)
```

**描述**

Remove the custom property of the component.

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| const char* name | The name of the custom property. |

### OH_ArkUI_NodeUtils_GetCustomProperty()

```c
int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)
```

**描述**

Get the value of the custom property of the component.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI-NodeHandle pointer. |
| const char* name | The name of the custom attribute. |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)** handle | The structure of the custom attribute corresponding to the key parameter name obtained. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NodeUtils_GetParentInPageTree()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)
```

**描述**

Get the parent node to obtain the component nodes created by ArkTs.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Return the pointer of the component. |

### OH_ArkUI_NodeUtils_GetActiveChildrenInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)
```

**描述**

Retrieve all active child nodes of a node. Span will not be counted in the children.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) head | Pass in the node that needs to be obtained. |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)** handle | The structure corresponding to the sub node information of the head node. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NodeUtils_GetCurrentPageRootNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)
```

**描述**

Retrieve the root node of the current page.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Return the pointer of the component. |

### OH_ArkUI_NodeUtils_IsCreatedByNDK()

```c
bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)
```

**描述**

Retrieve whether the component is labeled by C-API.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | Return whether the node is a Tag created by C-API,<br>         true represents created by C-API, false represents not created by C-API. |

### OH_ArkUI_NodeUtils_GetNodeType()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)
```

**描述**

Get the type of node.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Return the type of the node.<br>         For specific open types, refer to [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype). For unopened nodes, return -1. |

### OH_ArkUI_NodeUtils_GetWindowInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)
```

**描述**

Get info of the window to which the node belongs.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node object. |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)** info | Window info. Use [OH_ArkUI_HostWindowInfo_Destroy](capi-native-type-h.md#oh_arkui_hostwindowinfo_destroy) to release memory. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>         [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) The node is not mounted. |

### OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**描述**

Obtains the index of the current FrameNode's first child node which is on the tree.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |
| uint32_t* index | The index of the subnode. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**描述**

Obtains the index of the current FrameNode's last child node which is on the tree.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |
| uint32_t* index | the index of the subnode. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NodeUtils_GetChildWithExpandMode()

```c
int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)
```

**描述**

Obtains a subnode by position with the expand mode.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |
| int32_t position | Indicates the position of the subnode. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* subnode | The pointer to the subnode. |
| uint32_t expandMode | Indicates the expand mode. [ArkUI_ExpandMode](capi-native-type-h.md#arkui_expandmode). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_List_CloseAllSwipeActions()

```c
int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (*onFinish)(void* userData))
```

**描述**

Collapse the ListItem in its expanded state.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Node objects that need to be registered for events. |
| void\* userData | Custom event parameters are carried back in the callback parameter when the event is triggered. |
| void (\*onFinish)(void\* userData) | The callback triggered after the completion of the folding animation. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>         [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) The component does not support this event. |

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
| ArkUI_ContextHandle | The UIContext pointer.<br>        If a null pointer is returned, it may be because the node is empty. |

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
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode | Callback Events. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

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
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent\* event | Callback Events. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

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

Get the node handle by id.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* id | The id of the target node handle. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | The handle of target node handle. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NodeUtils_MoveTo()

```c
int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)
```

**描述**

Move the node handle to target parent node as child.

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | The node handle of the node to move. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) target_parent | The node handle of target parent. |
| int32_t index | Indicates the index which the node is moved to. If the value is a nagative number of invalid, thenode is moved to the end of the target parent node. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if the CAPI init error.<br>         [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-native-type-h.md#arkui_errorcode) if the node has already been adopted. add since api 22. |

### OH_ArkUI_NativeModule_InvalidateAttributes()

```c
int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)
```

**描述**

Triggers node updates in the current frame.When node attributes are modified after the current frame's build phase,the node updates will be deferred to the nextframe. This function forces immediate node updates within the current frame toensure rendering effects are applied synchronously.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NodeUtils_SetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**描述**

Set the cross-language option of the target node handle.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | The target node handle. |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | The cross-language option [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NodeUtils_GetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**描述**

Get the cross-language option of the target node handle.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | The target node handle. |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | The cross-language option [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

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
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |
| void\* userData | Indicates the custom data used in onLayoutCompleted callback function. |
| void (\*onLayoutCompleted)(void\* userData) | Indicates the function when layout completed is callback. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter is incorrect. |

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
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Indicates the target node. |
| void\* userData | Indicates the custom data used in onDrawCompleted callback function. |
| void (\*onDrawCompleted)(void\* userData) | Indicates the function when draw completed is callback. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | error code<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter is incorrect. |

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
| int32_t | error code<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter is incorrect. |

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
| int32_t | error code<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter is incorrect. |

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
| ArkUI_SnapshotOptions* snapshotOptions | Snapshot settings. If the value is null, the default settings are used.Snapshot settings include scaling, color space, and dynamic range configuration.Scaling: floating-point value greater than 0.Color space: <b>3</b> (DISPLAY_P3), <b>4</b> (SRGB), <b>27</b> (DISPLAY_BT2020_SRGB).Dynamic range: [ArkUI_DynamicRangeMode](capi-native-type-h.md#arkui_dynamicrangemode). |
| OH_PixelmapNative** pixelmap | Pointer to the <b>Pixelmap</b> object created by the system. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Result code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INTERNAL_ERROR](capi-native-type-h.md#arkui_errorcode) if the snapshot fails, returning a null pointer.<br>         Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT](capi-native-type-h.md#arkui_errorcode) if the snapshot operation times out.<br>         Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) if the provided color space or<br>         dynamic range mode is not supported.<br>         Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) if the isAuto parameter of the color<br>         space or dynamic range mode is set to true for offscreen node snapshot. |

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
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Invalid function parameter. |

### OH_ArkUI_NodeUtils_GetPositionToParent()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**描述**

Obtains the offset of a specific node relative to its parent node.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | Offset of the target node relative to its parent node, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_AddSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)
```

**描述**

设置组件支持的{@link 多态样式}状态。为了更高效地处理，需传入所关注的状态值及对应的状态处理函数，当关注的状态发生时，处理函数会被执行。可在回调中根据当前状态调整UI样式。当在同一个节点上多次调用该方法时，将以最后一次传入的状态及处理函数为准。有些类型的组件节点，系统内部已有对某些状态的默认处理。例如，Button组件默认具备对PRESSED状态的样式变化，当在此类组件上使用此方法自定义状态处理时，会先应用系统默认样式变化，再执行自定义的样式处理，最终效果为两者叠加。可以通过指定excludeInner为true来禁用系统内部的默认样式效果，但这通常取决于系统内部实现规范是否允许。当调用该函数时，传入的statesChangeHandler函数会立即执行一次，且无需特意注册对NORMAL状态的监听，只要注册了非NORMAL状态，当状态从任意状态变化回NORMAL时，系统都会进行回调，以便应用进行样式复原。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点。 |
| int32_t uiStates | 目标节点需要处理的目标UI状态。所有目标UI状态的组合结果可以通过“\|”操作来计算。例如：targetUIStates = ArkUI_UIState::PRESSED \|ArkUI_UIState::FOCUSED。 |
| void (statesChangeHandler)(int32_t currentStates | Handler for UI state changes.It rturns the current UI status. The value is the result of combining all current state enum values using the<b>|</b> operator. You can determine the state using the <b>&</b> operator.Example: <b>if (currentStates & ArkUI_UIState::PRESSED == ArkUI_UIState::PRESSED)</b>.However, for checking the normal state, use the equality operator directly.Example: <b>if (currentStates == ArkUI_UIState::NORMAL)</b>. |
| bool excludeInner | 禁止内部默认状态样式的标志。​​true​​表示禁用系统内部的默认样式，false表示不禁用。 |
| void\* userData) | statesChangeHandler回调函数中使用的自定义数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_RunTaskInScope()

```c
int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(*callback)(void* userData))
```

**描述**

Run a custom function inside the UIContext scope.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle uiContext | Indicates the pointer to a UI instance. |
| void\* userData | Indicates the pointer to the custom data. |
| void(\*callback)(void\* userData) | The custom function. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if the CAPI init error.<br>         Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-native-type-h.md#arkui_errorcode) if the uiContext is invalid.<br>         Returns [ARKUI_ERROR_CODE_CALLBACK_INVALID](capi-native-type-h.md#arkui_errorcode) if the callback function is invalid. |

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
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if the CAPI init error. |

### OH_ArkUI_NodeUtils_GetNodeUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)
```

**描述**

Get the uniqueId of the target node handle.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | The ArkUI-NodeHandle pointer. |
| int32_t* uniqueId | The uniqueId of the target node handle, default value is -1. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if the CAPI init error. |

### OH_ArkUI_NativeModule_IsInRenderState()

```c
int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)
```

**描述**

Returns true if the node is in the render state. A node is considered to be in the render state if itscorresponding RenderNode is on the render tree.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |
| bool* isInRenderState | If the node is in the render state. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if the CAPI init error. |

### OH_ArkUI_NativeModule_AdoptChild()

```c
int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**描述**

The current node adopts the target child node. The node being adopted must not have an existing parent node.This operation does not actually append it as a child, but only allows it to receive life-cyclecallbacks as if it were a child.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer, the parent node that will adopt the child node. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | ArkUI_NodeHandle pointer, the target node being adopted. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if the CAPI init error.<br>         [ARKUI_ERROR_CODE_NODE_HAS_PARENT](capi-native-type-h.md#arkui_errorcode) The child already has a parent node.<br>         [ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED](capi-native-type-h.md#arkui_errorcode) The child can not be adopted.<br>         [ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO](capi-native-type-h.md#arkui_errorcode) The node can not adopt children. |

### OH_ArkUI_NativeModule_RemoveAdoptedChild()

```c
int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**描述**

Remove the target adopted child node.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer, the parent node. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | ArkUI_NodeHandle pointer, the node being removed. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if the CAPI init error.<br>         [ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN](capi-native-type-h.md#arkui_errorcode) This child node is not adopted by the parent node. |

### OH_ArkUI_SetForceDarkConfig()

```c
int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (*colorInvertFunc)(uint32_t color))
```

**描述**

Sets the inverse color algorithm for components and instances.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle uiContext | Indicates the context in which the inverse color feature should take effect.If the value is null, the feature applies to the entire application process. |
| bool forceDark | Indicates whether the inverse color feature is enabled. |
| [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype) nodeType | Indicates the component type for which to enable the inverse color feature.If the value is ARKUI_NODE_UNDEFINED, enabling the feature for all components. |
| uint32_t (\*colorInvertFunc)(uint32_t color) | Indicates the user-defined inverse color algorithm. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if CAPI init error.<br>         Returns [ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID](capi-native-type-h.md#arkui_errorcode) if force dark config is invalid. |

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
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点。 |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | 事件类型。 |
| void\* userData | 开发者自定义的数据指针，以便在回调函数中处理自定义数据，需确保自定义函数执行时数据有效。 |
| void (\*callback)(ArkUI_NodeEvent\* event) | 开发者自定义的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>     <br>[ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE](capi-native-type-h.md#arkui_errorcode) 暂不支持该事件类型。 |

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
| int32_t | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>     <br>[ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE](capi-native-type-h.md#arkui_errorcode) 暂不支持该事件类型。 |

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
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 目标节点。 |
| float\* ratios | 阈值数组，表示组件的可见区域。 |
| int32_t size | 阈值数组的大小。 |
| float expectedUpdateInterval | 开发人员预期的计算间隔。 |
| void\* userData | 开发者自定义的数据指针，以便在回调函数中处理自定义数据，需确保自定义函数执行时数据有效。 |
| void (\*callback)(ArkUI_NodeEvent\* event) | 开发者自定义的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

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
| int32_t | 错误码。<br>     <br>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>     <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_NativeModule_ConvertPositionToWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)
```

**描述**

Converts a point's coordinates from the target node's coordinate system to the current window's coordinate system, with consideration of the node’s transformation.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| {ArkUI_NodeHandle} | currentNode ArkUI_NodeHandle The target node. |
| {ArkUI_IntOffset} | localPosition The point's coordinates in the target node's local coordinate system, in px. |
| {ArkUI_IntOffset*} | windowPosition The converted coordinates in the current window's coordinate system, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>         [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) The target node is not on main tree. |

### OH_ArkUI_NativeModule_ConvertPositionFromWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)
```

**描述**

Converts a point's coordinates from the current window's coordinate system to the target node's coordinate system, with consideration of the node’s transformation.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| {ArkUI_NodeHandle | } targetNode ArkUI_NodeHandle The target node. |
| {ArkUI_IntOffset} | windowPosition The point's coordinates in the current window's coordinate system, in px. |
| {ArkUI_IntOffset*} | localPosition The converted coordinates in the target node's local coordinate system, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>         [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) The target node is not on main tree. |

### OH_ArkUI_Swiper_FinishAnimation()

```c
int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)
```

**描述**

Stop the animation being executed by the Swiper node.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_PostAsyncUITask()

```c
int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (*asyncUITask)(void* asyncUITaskData), void (*onFinish)(void* asyncUITaskData))
```

**描述**

Post UI task to background threads.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | UIContext pointer of the page where the UI task located. |
| void\* asyncUITaskData | Parameter of asyncUITask and onFinish. |
| void (\*asyncUITask)(void\* asyncUITaskData) | Function executed by a background thread. |
| void (\*onFinish)(void\* asyncUITaskData) | Function executed by UI thread after async UI task is executed. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if context or asyncUITask is nullptr. |

### OH_ArkUI_PostUITask()

```c
int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**描述**

Post UI task to UI thread.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | UIContext pointer of the page where the UI task located. |
| void\* taskData | Parameter of task. |
| void (\*task)(void\* taskData) | Function executed by UI thread. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if context or task is nullptr. |

### OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible()

```c
int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)
```

**描述**

set the visiblity of the menubar.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle uiContext | ArkUI_ContextHandle. - The designated ArkUI container context. |
| bool visible | visibility. true indicate the menubar is visible,          false indicate the menubar is invisible. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-native-type-h.md#arkui_errorcode) if the uiContext is invalid.<br>          for example, 1.uiContext is nullptr 2.can not get container by uiContext.<br>          3. the uiContext is not belong to atomic service. |

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
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). |
| float expectedUpdateInterval | Expected calculation interval, in milliseconds. |
| void\* userData | Pointer to custom data. |
| void (\*callback)(ArkUI_NodeEvent\* event) | Event callback. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Result code. <br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful. <br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

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
| int32_t | Result code. <br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful. <br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_PostUITaskAndWait()

```c
int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**描述**

Post UI task to UI thread and wait until UI task finished.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | UIContext pointer of the page where the UI task located. |
| void\* taskData | Parameter of task. |
| void (\*task)(void\* taskData) | Function executed by UI thread. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if context or task is nullptr. |

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
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

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
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

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
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

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
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

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
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

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
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception. |

### OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext()

```c
int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)
```

**描述**

Get the root node handle of the corresponding page of the Context.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_ContextHandle context | A UIContext pointer. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* rootNode | The handle of target root node handle. If the context's correspondingpage has no root node, the pointed-to value will be set to null. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if the CAPI init error.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-native-type-h.md#arkui_errorcode) if the uiContext is invalid. |

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
| [ArkUI_GestureCollectInterceptInfo*](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md) | Returns the pointer to the <b>ArkUI_GestureCollectInterceptInfo</b> object.<br>         It is valid only during callback and does not need to be released.<br>         Returns <b>null</b> if the input parameter is invalid or the<br>         information is not gesture collection interception information. |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Error code.<br>     <ul><li>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>     </li><li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>     </li><li>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if CAPI init error.</li></ul> |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Error code.<br>     <ul><li>[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>     </li><li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) Function parameter exception.<br>     </li><li>[ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if CAPI init error.</li></ul> |


