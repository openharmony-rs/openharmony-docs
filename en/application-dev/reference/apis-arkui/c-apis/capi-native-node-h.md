# native_node.h

## Overview

Provides type definitions for <b>NativeNode</b> APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | ArkUI_NodeComponentEvent | Defines the parameter type of a component callback event, which is used to pass event-related data when the component callback is triggered, so that the application can obtain the callback event parameters. |
| [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) | ArkUI_StringAsyncEvent | Defines the type of string parameters used in component callback events. This struct is used to pass string data in the asynchronous event callback of a component. It is applicable to scenarios where the component callback event needs to carry text information. |
| [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) | ArkUI_TextChangeEvent | Defines a text change event, which is used to listen to and handle text change events in text input scenarios. This struct contains the text content, extended information, and numeric parameters. It allows you to obtain text change data in real time, making it suitable for scenarios such as listening to text box content, real-time search, and word count. |
| [ArkUI_NativeNodeAPI_1](capi-arkui-nativemodule-arkui-nativenodeapi-1.md) | ArkUI_NativeNodeAPI_1 | Provides a collection of native-side APIs of the Node type provided by ArkUI, supporting capabilities such as component node creation and destruction, node tree operations, attribute and event management, measurement, and layout. It is suitable for scenarios where native APIs are used to build and operate ArkUI component nodes. APIs related to the Node module must be called on the main thread. |
| [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | OH_ArkUI_TextEditorChangeEvent | Defines the text content change event of the **TextEditor** component, which is used to notify users when the text content changes and supports obtaining information such as the content before and after the change. It is applicable to scenarios where interception or validation is required before the text content changes, such as input interception, content filtering, and change confirmation. |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md) | ArkUI_NodeCustomEvent | Defines a custom component event. This is a general struct type. This struct is used to pass event information in the measurement, layout, and drawing event callbacks of a custom component. |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) | ArkUI_NodeAdapterHandle | Defines the pointer to a component adapter object, which is used for lazy loading of elements in scrollable components. This is applicable to scenarios where a large amount of scrollable content needs to be loaded on demand. It prevents all elements from being created at once, reducing memory usage and improving scrolling performance. |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md) | ArkUI_NodeAdapterEvent | Defines a component adapter event object, used to pass information such as the event type, host node, and data item index in the event callback of the node adapter. |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md) | ArkUI_NodeContentEvent | Defines a node content event. This is a general struct type. It is used as the event parameter of the node content event callback to obtain the event type and the node content object that triggers the event. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NodeType](#arkui_nodetype) | ArkUI_NodeType | Enumerates the component types that can be created by ArkUI on the native side. |
| [ArkUI_NodeAttributeType](capi-arkui-nodeattributetype.md) | ArkUI_NodeAttributeType | Enumerates the attribute types that can be set by ArkUI on the native side. |
| [ArkUI_NodeEventType](capi-arkui-nodeeventtype.md) | ArkUI_NodeEventType | Enumerates the event types supported by the NativeNode component. |
| [ArkUI_NodeDirtyFlag](#arkui_nodedirtyflag) | ArkUI_NodeDirtyFlag | Enumerates the flags passed to indicate the need to re-execute measurement, layout, or rendering when a custom component calls the <b>::markDirty</b> API. |
| [ArkUI_NodeAdapterEventType](#arkui_nodeadaptereventtype) | ArkUI_NodeAdapterEventType | Enumerates node adapter event types. |
| [ArkUI_NodeContentEventType](#arkui_nodecontenteventtype) | ArkUI_NodeContentEventType | Enumerates the event types of NodeContent. |
| [ArkUI_InspectorErrorCode](#arkui_inspectorerrorcode) | ArkUI_InspectorErrorCode | Enumerates inspector error codes. |
| [OH_ArkUI_AdoptPolicy](#oh_arkui_adoptpolicy) | OH_ArkUI_AdoptPolicy | Enumerates the policy for adopting a child node. |

### Macro

| Name | Description |
| -- | -- |
| MAX_NODE_SCOPE_NUM 1000 | Define components max function size.<br>**Since**: 12 |
| MAX_COMPONENT_EVENT_ARG_NUM 12 | Define component event max args size.<br>**Since**: 12 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_geteventtype) | - | Obtains the type of a component event. |
| [int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettargetid) | - | Obtains the custom ID of a component event.<br> The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be applied to the dispatch logic of the same event entry point function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver). |
| [ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodehandle) | - | Obtains the component object that triggers an event. |
| [ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getinputevent) | - | Obtains input event (for example, touch event) data for a component event. |
| [ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodecomponentevent) | - | Obtains the numerical data in a component event. |
| [ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getstringasyncevent) | - | Obtains the string data in a component event. |
| [ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettextchangeevent) | - | Obtains the ArkUI_TextChangeEvent data from the specified component event. |
| [void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getuserdata) | - | Obtains the custom data in a component event.<br> This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the event is triggered. |
| [int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)](#oh_arkui_nodeevent_getnumbervalue) | - | Obtains the numeric-type parameter of a component event. |
| [int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)](#oh_arkui_nodeevent_getstringvalue) | - | Obtains the string-type parameter of a component event. The string data is valid only during an event callback. To use it outside an event callback, you are advised to copy the string data. |
| [int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)](#oh_arkui_nodeevent_setreturnnumbervalue) | - | Sets the return value for a component event. |
| [ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_gettouchtestinfo) | - | Obtains the touch test information in the component event. |
| [OH_ArkUI_TextEditorChangeEvent* OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettexteditoronwillchangeevent) | - | Obtains the text content change data of the **TextEditor** component in the component event. |
| [ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()](#oh_arkui_nodeadapter_create) | - | Creates a component adapter. |
| [void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_dispose) | - | Disposes of a component adapter. |
| [int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)](#oh_arkui_nodeadapter_settotalnodecount) | - | Sets the total number of elements in the specified adapter. |
| [uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_gettotalnodecount) | - | Obtains the total number of elements in the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(
ArkUI_NodeAdapterHandle handle, void* userData, void (\*receiver)(ArkUI_NodeAdapterEvent* event))](#oh_arkui_nodeadapter_registereventreceiver) | - | Registers an event callback for the specified adapter. After the callback event is no longer needed, you need to call [OH_ArkUI_NodeAdapter_UnregisterEventReceiver](capi-native-node-h.md#oh_arkui_nodeadapter_unregistereventreceiver) to deregister it. |
| [void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_unregistereventreceiver) | - | Unregisters an event callback for the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_reloadallitems) | - | Instructs the specified adapter to reload all elements. |
| [int32_t OH_ArkUI_NodeAdapter_ReloadItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_reloaditem) | - | Instructs the specified adapter to reload certain elements. |
| [int32_t OH_ArkUI_NodeAdapter_RemoveItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_removeitem) | - | Instructs the specified adapter to remove certain elements. |
| [int32_t OH_ArkUI_NodeAdapter_InsertItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_insertitem) | - | Instructs the specified adapter to insert certain elements. |
| [int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)](#oh_arkui_nodeadapter_moveitem) | - | Instructs the specified adapter to move certain elements. |
| [int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)](#oh_arkui_nodeadapter_getallitems) | - | Obtains all elements stored in the specified adapter. When the API is called, the array object pointer of the element is returned. You must release the memory data to which the pointer points. |
| [void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getuserdata) | - | Obtains the custom data passed in during registration of the specified event. |
| [ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gettype) | - | Obtains the event type. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getremovednode) | - | Obtains the element to be removed for the event to be destroyed. |
| [uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getitemindex) | - | Obtains the index of the element to be operated for the specified adapter event. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gethostnode) | - | Obtains the scrollable container node that uses the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)](#oh_arkui_nodeadapterevent_setitem) | - | Sets the component to be added to the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)](#oh_arkui_nodeadapterevent_setnodeid) | - | Sets the component ID to be generated. |
| [ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getlayoutconstraintinmeasure) | - | Obtains the size constraint for measurement through a custom component event. |
| [ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getpositioninlayout) | - | Obtains the expected position of a component relative to its parent component in the layout phase through a custom component event. |
| [ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getdrawcontextindraw) | - | Obtains the drawing context through a custom component event. You need to release the obtained drawing context in a timely manner after use. |
| [int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_geteventtargetid) | - | Obtains the ID of a custom component event. |
| [void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getuserdata) | - | Obtains a custom event parameter through a custom component event. |
| [ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getnodehandle) | - | Obtains a component object through a custom component event. |
| [ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_geteventtype) | - | Obtains the event type through a custom component event. |
| [int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_nodecustomevent_getcustomspanmeasureinfo) | - | Obtains the measurement information of a custom span through a custom component event. |
| [int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)](#oh_arkui_nodecustomevent_setcustomspanmetrics) | - | Sets the measurement metrics of a custom span through a custom component event. |
| [int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_nodecustomevent_getcustomspandrawinfo) | - | Obtains the drawing information of a custom span through a custom component event. |
| [typedef void (\*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)](#arkui_nodecontentcallback) | ArkUI_NodeContentCallback | Defines a callback for the **NodeContent** event. |
| [int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)](#oh_arkui_nodecontent_registercallback) | - | Registers an event callback for **NodeContent**. |
| [ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_geteventtype) | - | Obtains the type of the specified **NodeContent** event. |
| [ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_getnodecontenthandle) | - | Obtains the object that triggers the specified **NodeContent** event. |
| [int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)](#oh_arkui_nodecontent_setuserdata) | - | Saves custom data to the specified **NodeContent** object. |
| [void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)](#oh_arkui_nodecontent_getuserdata) | - | Obtains the custom data saved on the specified **NodeContent** object. |
| [int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_addnode) | - | Adds an ArkUI component node to the specified **NodeContent** object. |
| [int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_removenode) | - | Removes an ArkUI component node from the specified **NodeContent** object. |
| [int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)](#oh_arkui_nodecontent_insertnode) | - | Inserts an ArkUI component node into a specific position of the specified **NodeContent** object. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)](#oh_arkui_nodeutils_getlayoutsize) | - | Obtains the layout area size of the component. The size does not count in transformation attributes, such as scale. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)](#oh_arkui_nodeutils_getlayoutposition) | - | Obtains the position of the component's layout area relative to its parent component. The relative position does not count in transformation attributes, such as translate. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getlayoutpositioninwindow) | - | Obtains the position of the component's layout area relative to the window. The relative position does not count in transformation attributes, such as translate. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)](#oh_arkui_nodeutils_getlayoutpositioninscreen) | - | Obtains the position of the component's layout area relative to the screen. The relative position does not count in transformation attributes, such as translate. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)](#oh_arkui_nodeutils_getlayoutpositioninglobaldisplay) | - | Obtains the offset of the specified component relative to the global display. The relative position does not count in transformation attributes, such as translate. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinwindow) | - | Obtains the position of the component in the window, including the translate attribute. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinscreen) | - | Obtains the position of the component on the screen, including the translate attribute. |
| [void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)](#oh_arkui_nodeutils_addcustomproperty) | - | Sets a custom property for a component. This API takes effect only in the main thread. |
| [void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)](#oh_arkui_nodeutils_removecustomproperty) | - | Removes a custom property that has been set for the specified component. |
| [int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)](#oh_arkui_nodeutils_getcustomproperty) | - | Obtains the custom property of a component and returns an **ArkUI_CustomProperty** instance through a handle. |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getparentinpagetree) | - | Obtains the parent node, which can be a component node created with ArkTS. |
| [int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)](#oh_arkui_nodeutils_getactivechildreninfo) | - | Obtains the FrameNode child node whose internal active state is **true** and generates an [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md) instance. Spans are not counted as child nodes.<br> After the child node is obtained, you can call [OH_ArkUI_ActiveChildrenInfo_GetCount](capi-native-type-h.md#oh_arkui_activechildreninfo_getcount) to obtain the number of child nodes and call [OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex](capi-native-type-h.md#oh_arkui_activechildreninfo_getnodebyindex) to read the child nodes by index. After the instance is used, you must call [OH_ArkUI_ActiveChildrenInfo_Destroy](capi-native-type-h.md#oh_arkui_activechildreninfo_destroy) to destroy it. In **LazyForEach**<br>scenarios, you are advised to use the [OH_ArkUI_NodeUtils_GetChildWithExpandMode](capi-native-node-h.md#oh_arkui_nodeutils_getchildwithexpandmode) API for traversal. |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getcurrentpagerootnode) | - | Obtains the root node of the current page. |
| [bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_iscreatedbyndk) | - | Checks whether the specified component is created with C APIs. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getnodetype) | - | Obtains the type of the specified node. |
| [int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)](#oh_arkui_nodeutils_getwindowinfo) | - | Obtains the information about the window to which a node belongs. |
| [int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getfirstchildindexwithoutexpand) | - | Obtains the index of the first child node of the target node in the tree without expanding any nodes. |
| [int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getlastchildindexwithoutexpand) | - | Obtains the index of the last child node of the target node in the tree without expanding any nodes. |
| [int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)](#oh_arkui_nodeutils_getchildwithexpandmode) | - | Obtains a child node at the specified index using different expansion modes. |
| [int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_list_closeallswipeactions) | - | Collapses the list items in the expanded state. |
| [ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)](#oh_arkui_getcontextbynode) | - | Obtains the pointer to the UI context object of the specified node. |
| [int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))](#oh_arkui_registersystemcolormodechangeevent) | - | Registers an event listener for system color mode changes. A single component can only register one callback for system color mode changes. For implementation examples, see Adding an Event Listener. |
| [void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemcolormodechangeevent) | - | Unregisters the event listener for system color mode changes. |
| [int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))](#oh_arkui_registersystemfontstylechangeevent) | - | Registers an event listener for system font style changes. A single component can only register one callback for system font style changes. |
| [void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemfontstylechangeevent) | - | Unregisters the event listener for system font style changes. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontsizescale) | - | Obtains the font size in the system font style change event. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontweightscale) | - | Obtains the font weight in the system font style change event. |
| [int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getattachednodehandlebyid) | - | Obtains the target node based on the provided user ID. |
| [int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)](#oh_arkui_nodeutils_moveto) | - | Moves a node to a target parent node as a child. |
| [int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_invalidateattributes) | - | Triggers the node attribute update in this frame.<br> If the attributes of the current node are modified after the build phase, these changes do not take effect immediately but are deferred for batch processing in the next frame.<br> This API forces immediate node updates within the current frame, ensuring that rendering effects are applied synchronously. |
| [int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_setcrosslanguageoption) | - | Sets the cross-language option for the target node. |
| [int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_getcrosslanguageoption) | - | Obtains the cross-language option of the target node. |
| [int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onLayoutCompleted)(void* userData))](#oh_arkui_registerlayoutcallbackonnodehandle) | - | Registers a layout completion callback function for a specific node. |
| [int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onDrawCompleted)(void* userData))](#oh_arkui_registerdrawcallbackonnodehandle) | - | Registers a drawing completion callback function for a specific node. |
| [int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterlayoutcallbackonnodehandle) | - | Unregisters the layout completion callback function for a specific node. |
| [int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterdrawcallbackonnodehandle) | - | Unregisters the drawing completion callback function for a specific node. |
| [int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelmap)](#oh_arkui_getnodesnapshot) | - | Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered, the snapshot operation will fail. When the PixelMap is no longer used, you should call OH_PixelmapNative_Release to release it. |
| [int32_t OH_ArkUI_GetNodeSnapshotSizeLimitation(int32_t* maxWidth, int32_t* maxHeight)](#oh_arkui_getnodesnapshotsizelimitation) | - | Obtains the size limit of a component screenshot. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getpositiontoparent) | - | Obtains the offset of the target node relative to its parent node, in px. |
| [ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)](#oh_arkui_addsupporteduistates) | - | Adds the polymorphic style states supported by the component. To handle states efficiently, specify the states of interest and their corresponding handlers. When a state of interest occurs, the handler will be executed. You can adjust the UI style based on the current state within the callback. If this API is called multiple times on the same node, the last set of states and handlers will take precedence. Some component types have default system handling for certain states. For example, the **Button** component has a default style effect for the PRESSED state. When custom state handling is implemented on such components, the default style effect will be applied first, followed by the custom style changes, resulting in a combined effect. To disable the default style effects, set **excludeInner** to **true**, if this is allowed by the system implementation. When this API is called, the provided handler function will be executed immediately. There is no need to explicitly register a listener for the NORMAL state. Once a non-NORMAL state is registered, the system will automatically notify your application when the state changes back to NORMAL. |
| [ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)](#oh_arkui_removesupporteduistates) | - | Removes registered UI states. When all states registered using **OH_ArkUI_AddSupportedUIStates** are removed, the registered **stateChangeHandler** will no longer be executed. |
| [int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(\*callback)(void* userData))](#oh_arkui_runtaskinscope) | - | Executes the specified callback in the target UI context. For the implementation example, see Ensuring Multi-Instance Functionality in the NDK. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getnodehandlebyuniqueid) | - | Obtain a node by its unique ID. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)](#oh_arkui_nodeutils_getnodeuniqueid) | - | Obtains the unique ID of the target node. |
| [int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)](#oh_arkui_nativemodule_isinrenderstate) | - | Obtains whether a node is in the render state. If RenderNode of a node is in the render tree, the node is in the render state. |
| [int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_adoptchild) | - | Adopts the target node as an affiliated node. The adopted node must not have an existing parent. This API is not used to add a node as a child node. Instead, it only allows the node to receive lifecycle callbacks of the corresponding child node. |
| [int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_removeadoptedchild) | - | Removes a previously-adopted affiliated node. |
| [int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (\*colorInvertFunc)(uint32_t color))](#oh_arkui_setforcedarkconfig) | - | Sets the color inversion algorithm for the component and instance. For details, see Using Color Inversion for Quick Dark Mode Adaptation. |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonevent) | - | Registers a basic event callback for the target node.<br> Currently, the following event types are supported: **NODE_ON_CLICK_EVENT**, **NODE_TOUCH_EVENT**, **NODE_EVENT_ON_APPEAR**, **NODE_EVENT_ON_DISAPPEAR**, **NODE_ON_KEY_EVENT**, **NODE_ON_FOCUS**, **NODE_ON_BLUR**, **NODE_ON_HOVER**, **NODE_ON_MOUSE**, and **NODE_ON_SIZE_CHANGE**. For details, see [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype). |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)](#oh_arkui_nativemodule_unregistercommonevent) | - | Unregisters the basic event callback for the target node.<br> For details about the supported event types, see [OH_ArkUI_NativeModule_RegisterCommonEvent](capi-native-node-h.md#oh_arkui_nativemodule_registercommonevent). |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonvisibleareaapproximatechangeevent) | - | Registers a basic event callback for visible area changes with a constrained callback interval. |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonvisibleareaapproximatechangeevent) | - | Unregisters the basic event callback for visible area changes with a constrained callback interval. |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)](#oh_arkui_nativemodule_convertpositiontowindow) | - | Converts the coordinates of a point from the coordinate system of a specified node to that of the current window. For a coordinate system of a node, transformation of the node is considered. For example, if node A is translated leftward by 100, the coordinates of the points in its coordinate system will also be translated leftward by 100.<br> [](../../../../reference/apis-arkui/figures/ConvertToWindow.png)<br> As shown in the preceding figure, the coordinates (x0, y0) in the coordinate system of the specified node are converted to the coordinates (x1, y1) in the coordinate system of the window. |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)](#oh_arkui_nativemodule_convertpositionfromwindow) | - | Converts the coordinates of a point from the current window's coordinate system to the target node's coordinate system. For a coordinate system of a node, transformation of the node is considered. For example, if node A is translated leftward by 100, the coordinates of the points in its coordinate system will also be translated leftward by 100.<br> [](../../../../reference/apis-arkui/figures/ConvertFromWindow.png)<br> As shown in the preceding figure, the coordinates (x1, y1) in the window coordinate system are converted to the coordinates (x0, y0) in the coordinate system of the target node. |
| [int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)](#oh_arkui_swiper_finishanimation) | - | Stops the page turning animation that is being executed on the specified **Swiper** node. |
| [int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (\*asyncUITask)(void* asyncUITaskData), void (\*onFinish)(void* asyncUITaskData))](#oh_arkui_postasyncuitask) | - | Submits the **asyncUITask** function to a non-UI thread provided by the ArkUI framework for execution. After **asyncUITask** finishes execution, the **onFinish** function is called in the UI thread.<br> This is suitable for scenarios involving multi-threaded UI component creation. You can use this API to create UI components in non-UI threads and then mount the created components to the main tree in the UI thread. |
| [int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitask) | - | Submits the **task** function to the UI thread for execution.<br> This is suitable for scenarios involving multi-threaded UI component creation. When you create UI components in a self-built thread, you can use this API to mount the created components to the main tree on the UI thread. |
| [int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)](#oh_arkui_nativemodule_atomicservicemenubarsetvisible) | - | Sets the visibility of the menu bar. |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonareaapproximatechangeevent) | - | Registers a callback for listening for component size and area changes. This API can be called for a valid [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node at any time. The newly registered callback will replace the previously registered callback for this event and take effect from the next frame. When the callback is no longer needed, use [OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent](capi-native-node-h.md#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) to unregister it. Otherwise, the callback will be automatically unregistered when the node is released. |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) | - | Unregisters the callback for listening for component size and area changes. |
| [int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitaskandwait) | - | Submits the **task** function to the UI thread for execution. The thread calling this API will block until the **task** function completes execution. Calling this API from the UI thread is equivalent to synchronously calling the **task** function.<br> This is suitable for scenarios involving multi-threaded UI component creation. When you need to call functions that are only supported on the UI thread during the multi-threaded component creation process, you can use this API to return to the UI thread to call the function and then resume multi-threaded component creation after the call completes.<br> When the UI thread is under high load, non-UI threads calling this API may block for extended periods, affecting the performance of multi-threaded UI component creation. Frequent use is not recommended. |
| [int32_t OH_ArkUI_Swiper_StartFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_startfakedrag) | - | Starts a simulated drag on a **Swiper** node. [OH_ArkUI_Swiper_FakeDragBy](capi-native-node-h.md#oh_arkui_swiper_fakedragby) can be used to simulate a drag action. [OH_ArkUI_Swiper_StopFakeDrag](capi-native-node-h.md#oh_arkui_swiper_stopfakedrag) can be used to stop the drag simulation.<br> A simulated drag can be interrupted by a real drag. To ignore a drag event from a user during the simulated drag, use [NODE_SWIPER_DISABLE_SWIPE](capi-native-node-h.md#arkui_nodeattributetype). |
| [int32_t OH_ArkUI_Swiper_FakeDragBy(ArkUI_NodeHandle node, float offset, bool* isConsumedOffset)](#oh_arkui_swiper_fakedragby) | - | Simulates the drag effect by setting the offset of a **Swiper** node. Before calling this API, you must call [OH_ArkUI_Swiper_StartFakeDrag](capi-native-node-h.md#oh_arkui_swiper_startfakedrag) to start the drag simulation. |
| [int32_t OH_ArkUI_Swiper_StopFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_stopfakedrag) | - | Stops the drag simulation on a **Swiper** node. |
| [int32_t OH_ArkUI_Swiper_IsFakeDragging(ArkUI_NodeHandle node, bool* isFakeDragging)](#oh_arkui_swiper_isfakedragging) | - | Obtains the drag simulation status on a **Swiper** node. |
| [int32_t OH_ArkUI_Swiper_ShowPrevious(ArkUI_NodeHandle node)](#oh_arkui_swiper_showprevious) | - | Displays the previous page of a **Swiper** node. |
| [int32_t OH_ArkUI_Swiper_ShowNext(ArkUI_NodeHandle node)](#oh_arkui_swiper_shownext) | - | Displays the next page of a **Swiper** node. |
| [int32_t OH_ArkUI_ArcSwiper_ShowPrevious(ArkUI_NodeHandle node)](#oh_arkui_arcswiper_showprevious) | - | Displays the previous page of the **ArcSwiper** node. |
| [int32_t OH_ArkUI_ArcSwiper_ShowNext(ArkUI_NodeHandle node)](#oh_arkui_arcswiper_shownext) | - | Displays the next page of the **ArcSwiper** node. |
| [int32_t OH_ArkUI_ArcSwiper_FinishAnimation(ArkUI_NodeHandle node)](#oh_arkui_arcswiper_finishanimation) | - | Finishes the animation being executed by the **ArcSwiper** node. |
| [int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)](#oh_arkui_nativemodule_getpagerootnodehandlebycontext) | - | Obtains the root node of the page of a specified instance. |
| [ArkUI_GestureCollectInterceptInfo* OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_getgesturecollectinterceptinfo) | - | Obtains the **ArkUI_GestureCollectInterceptInfo** object from a specified **ArkUI_NodeEvent** object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_SetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy policy)](#oh_arkui_nativemodule_setchildmountpolicy) | - | Sets the child node mounting policy for a target node. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy* policy)](#oh_arkui_nativemodule_getchildmountpolicy) | - | Obtains the current child node mounting policy of a target node. The default child node mounting policy of a target node is OH_ARKUI_NODE_MOUNT_POLICY_SINGLE_IF_RENDER_NODE. |
| [ArkUI_ErrorCode OH_ArkUI_NodeUtils_SetUiDvsyncSwitch(ArkUI_ContextHandle context, bool enable)](#oh_arkui_nodeutils_setuidvsyncswitch) | - | Sets the UI Dvsync switch.<br> When enabled, the system responds to Vsync requests more promptly and executes rendering tasks more frequently. It is typically enabled at the start of an animation in a self-rendering framework and disabled when the animation ends, to ensure smoother animation effects while preventing frequent Vsync requests from affecting other functionalities. Calling this function on a non-UI thread will cause the application to exit. |
| [int32_t OH_ArkUI_NativeModule_AdoptChildWithPolicy(ArkUI_NodeHandle node, ArkUI_NodeHandle child, OH_ArkUI_AdoptPolicy policy)](#oh_arkui_nativemodule_adoptchildwithpolicy) | - | Adopts the target node as an affiliated node. The adopted node must not have an existing parent. This API is not used to add a node as a child node. Instead, it only allows the node to receive lifecycle callbacks of the corresponding child node. Configure the render position of the overlay node of the adopted node by policy. |
| [int32_t OH_ArkUI_NativeModule_SetAdoptedChildOverlayPositionCompensation(ArkUI_NodeHandle adoptedChild, const ArkUI_PointF* compensationOffset, const ArkUI_Matrix4* compensationTransform)](#oh_arkui_nativemodule_setadoptedchildoverlaypositioncompensation) | - | Sets the position compensation from an adopted child to its adopt parent. The compensation represents the aggregate effect of the pure rendering node tree between them. First, the translation is performed using compensationOffset, and then the transformation is performed using compensationTransform. Compensation only takes effect if the child node has been adopted using the following policy [OH_ARKUI_NATIVE_MODULE_ADOPT_POLICY_OVERLAY_POSITION_FOLLOWS_ADOPT_PARENT_CHAIN](capi-native-node-h.md#oh_arkui_adoptpolicy). |

### Variable

| Name | Description |
| -- | -- |
| void (*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event) | Defines a callback for the **NodeContent** event.<br>**Since**: 12<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

## Enum type description

### ArkUI_NodeType

```c
enum ArkUI_NodeType
```

**Description**

Enumerates the component types that can be created by ArkUI on the native side.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
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
| ARKUI_NODE_BUTTON = 9 | Icon. |
| ARKUI_NODE_PROGRESS = 10 | Progress indicator. |
| ARKUI_NODE_CHECKBOX = 11 | Check box. |
| ARKUI_NODE_XCOMPONENT = 12 | XComponent of the SURFACE type. |
| ARKUI_NODE_DATE_PICKER = 13 | Date picker. |
| ARKUI_NODE_TIME_PICKER = 14 | Time picker. |
| ARKUI_NODE_TEXT_PICKER = 15 | Text picker. |
| ARKUI_NODE_CALENDAR_PICKER = 16 | Calendar picker. |
| ARKUI_NODE_SLIDER = 17 | Slider. |
| ARKUI_NODE_RADIO = 18 | Radio button. |
| ARKUI_NODE_IMAGE_ANIMATOR = 19 | Frame animation component. |
| ARKUI_NODE_XCOMPONENT_TEXTURE | XComponent of the TEXTURE type. @since 18 |
| ARKUI_NODE_CHECKBOX_GROUP = 21 | Check box group. @since 15 |
| ARKUI_NODE_TEXT_EDITOR = 22 |  |
| ARKUI_NODE_ARC_ALPHABET_INDEXER = 23 |  |
| ARKUI_NODE_STACK = MAX_NODE_SCOPE_NUM | Stack container. |
| ARKUI_NODE_SWIPER | Swiper. |
| ARKUI_NODE_SCROLL | Scrollable container. |
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
| ARKUI_NODE_CUSTOM_SPAN | Custom span. Common attributes cannot be set or obtained. You can use [OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo](capi-native-node-h.md#oh_arkui_nodecustomevent_getcustomspanmeasureinfo), [OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics](capi-native-node-h.md#oh_arkui_nodecustomevent_setcustomspanmetrics), and [OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo](capi-native-node-h.md#oh_arkui_nodecustomevent_getcustomspandrawinfo) to obtain and set the node information of components of this type. For details about the usage, see text_capi_sample. |
| ARKUI_NODE_EMBEDDED_COMPONENT |  |
| ARKUI_NODE_UNDEFINED |  |
| ARKUI_NODE_PICKER = 1018 |  |
| ARKUI_NODE_ARC_LIST = 1019 |  |
| ARKUI_NODE_ARC_LIST_ITEM = 1020 |  |
| ARKUI_NODE_ARC_SCROLL_BAR = 1021 |  |
| ARKUI_NODE_ARC_SWIPER = 1022 |  |

### ArkUI_NodeDirtyFlag

```c
enum ArkUI_NodeDirtyFlag
```

**Description**

Enumerates the flags passed to indicate the need to re-execute measurement, layout, or rendering when a custom component calls the <b>::markDirty</b> API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| NODE_NEED_MEASURE = 1 | Remeasure.<br> When this type of flag is specified, re-layout is triggered by default. |
| NODE_NEED_LAYOUT | Re-layout. |
| NODE_NEED_RENDER | Re-rendering. |

### ArkUI_NodeAdapterEventType

```c
enum ArkUI_NodeAdapterEventType
```

**Description**

Enumerates node adapter event types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
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

**Description**

Enumerates the event types of NodeContent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| NODE_CONTENT_EVENT_ON_ATTACH_TO_WINDOW = 0 | Attach event. |
| NODE_CONTENT_EVENT_ON_DETACH_FROM_WINDOW = 1 | Detach event. |

### ArkUI_InspectorErrorCode

```c
enum ArkUI_InspectorErrorCode
```

**Description**

Enumerates inspector error codes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL = 0 | &nbsp;Operation successful. |
| ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER = -1 | &nbsp;Parameter error. |

### OH_ArkUI_AdoptPolicy

```c
enum OH_ArkUI_AdoptPolicy
```

**Description**

Enumerates the policy for adopting a child node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_ADOPT_POLICY_OVERLAY_POSITION_FOLLOWS_ADOPT_PARENT_CHAIN = 0 |  |


## Function description

### OH_ArkUI_NodeEvent_GetEventType()

```c
ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)
```

**Description**

Obtains the type of a component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeEventType](capi-arkui-nodeeventtype.md) | Type of the [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) component event. |

### OH_ArkUI_NodeEvent_GetTargetId()

```c
int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)
```

**Description**

Obtains the custom ID of a component event.<br> The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be applied to the dispatch logic of the same event entry point function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Custom ID of the component event. |

### OH_ArkUI_NodeEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)
```

**Description**

Obtains the component object that triggers an event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) | Component object that triggers the event. |

### OH_ArkUI_NodeEvent_GetInputEvent()

```c
ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains input event (for example, touch event) data for a component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_UIInputEvent*](capi-arkui-eventmodule-arkui-uiinputevent.md) | Pointer to the input event data. |

### OH_ArkUI_NodeEvent_GetNodeComponentEvent()

```c
ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains the numerical data in a component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeComponentEvent*](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | Pointer to the numerical data. |

### OH_ArkUI_NodeEvent_GetStringAsyncEvent()

```c
ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains the string data in a component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_StringAsyncEvent*](capi-arkui-nativemodule-arkui-stringasyncevent.md) | Pointer to the string data. |

### OH_ArkUI_NodeEvent_GetTextChangeEvent()

```c
ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains the ArkUI_TextChangeEvent data from the specified component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. It cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextChangeEvent*](capi-arkui-nativemodule-arkui-textchangeevent.md) | Pointer to the ArkUI_TextChangeEvent object. |

### OH_ArkUI_NodeEvent_GetUserData()

```c
void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)
```

**Description**

Obtains the custom data in a component event.<br> This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the event is triggered.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to the custom data. |

### OH_ArkUI_NodeEvent_GetNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)
```

**Description**

Obtains the numeric-type parameter of a component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |
| int32_t index | Return value index. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Pointer to the return value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE if the parameter index in the component event is out of range. <br>Returns ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID if the data requested by the caller does not exist in the component event. |

### OH_ArkUI_NodeEvent_GetStringValue()

```c
int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)
```

**Description**

Obtains the string-type parameter of a component event. The string data is valid only during an event callback. To use it outside an event callback, you are advised to copy the string data.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |
| int32_t index | Return value index. |
| char** string | Double pointer to the string array. |
| int32_t* stringSize | Pointer to the size of the string array. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE if the parameter index in the component event is out of range. <br>Returns ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID if the data requested by the caller does not exist in the component event. |

### OH_ArkUI_NodeEvent_SetReturnNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)
```

**Description**

Sets the return value for a component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Pointer to the event numeric type array. |
| int32_t size | Size of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID if the data requested by the caller does not exist in the component event. |

### OH_ArkUI_NodeEvent_GetTouchTestInfo()

```c
ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)
```

**Description**

Obtains the touch test information in the component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* nodeEvent | Pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TouchTestInfo*](capi-arkui-eventmodule-arkui-touchtestinfo.md) | Pointer to the [ArkUI_TouchTestInfo](capi-arkui-eventmodule-arkui-touchtestinfo.md) object. If the input parameter is invalid or is not touch test information, **null** is returned. |

### OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent()

```c
OH_ArkUI_TextEditorChangeEvent* OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains the text content change data of the **TextEditor** component in the component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) component event object. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextEditorChangeEvent*](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | Pointer to the [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) data object.<br>         If the input parameter is invalid or is not the text content change event information of the **TextEditor** component, **null** is returned. |

### OH_ArkUI_NodeAdapter_Create()

```c
ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()
```

**Description**

Creates a component adapter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

### OH_ArkUI_NodeAdapter_Dispose()

```c
void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)
```

**Description**

Disposes of a component adapter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |

### OH_ArkUI_NodeAdapter_SetTotalNodeCount()

```c
int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)
```

**Description**

Sets the total number of elements in the specified adapter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |
| uint32_t size | Number of elements. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_GetTotalNodeCount()

```c
uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)
```

**Description**

Obtains the total number of elements in the specified adapter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Total number of elements in the adapter. |

### OH_ArkUI_NodeAdapter_RegisterEventReceiver()

```c
int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(
ArkUI_NodeAdapterHandle handle, void* userData, void (*receiver)(ArkUI_NodeAdapterEvent* event))
```

**Description**

Registers an event callback for the specified adapter. After the callback event is no longer needed, you need to call [OH_ArkUI_NodeAdapter_UnregisterEventReceiver](capi-native-node-h.md#oh_arkui_nodeadapter_unregistereventreceiver) to deregister it.

> **Note**:
>
> In versions earlier than API version 26.0.0, if the event receiving callback processes the [NODE_ADAPTER_EVENT_WILL_ATTACH_TO_NODE](capi-native-node-h.md#arkui_nodeadaptereventtype) event, this event will be triggered when the host node is attached to the main tree. You can register an event listener after the **NodeAdapter** is bound to the host node and before the host node is attached to the main tree. In this case, you will receive this event when the host node is attached to the main tree. In API version 26.0.0 and later, this event is triggered immediately when the **NodeAdapter** is bound to the host node, instead of when the host node is attached to the main tree. In this case, the host node may not have been attached to the main tree. If the node on which the callback logic depends has been mounted (for example, accessing layout information or executing animation), you are advised to place the related logic in the **onAppear** callback of the host node. Register an event listener before the **NodeAdapter** is bound to the host node. Otherwise, this event may not be triggered.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |
| void* userData | Pointer to the custom data. |
| void (*receiver)(ArkUI_NodeAdapterEvent* event) | Event receiving callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_UnregisterEventReceiver()

```c
void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)
```

**Description**

Unregisters an event callback for the specified adapter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |

### OH_ArkUI_NodeAdapter_ReloadAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)
```

**Description**

Instructs the specified adapter to reload all elements.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_ReloadItem()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**Description**

Instructs the specified adapter to reload certain elements.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |
| uint32_t startPosition | Start position of an element change. |
| uint32_t itemCount | Number of changed elements. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. Returns ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapter_RemoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_RemoveItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**Description**

Instructs the specified adapter to remove certain elements.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |
| uint32_t startPosition | Start position for deleting an element. |
| uint32_t itemCount | Number of deleted elements. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. Returns ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapter_InsertItem()

```c
int32_t OH_ArkUI_NodeAdapter_InsertItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**Description**

Instructs the specified adapter to insert certain elements.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |
| uint32_t startPosition | Start position for inserting an element. |
| uint32_t itemCount | Number of inserted elements. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. Returns ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapter_MoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)
```

**Description**

Instructs the specified adapter to move certain elements.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |
| uint32_t from | Start position of the element shift. |
| uint32_t to | End position of the element shift. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. Returns ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapter_GetAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)
```

**Description**

Obtains all elements stored in the specified adapter. When the API is called, the array object pointer of the element is returned. You must release the memory data to which the pointer points.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapterhandle.md) handle | Component adapter object. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md)** items | Double pointer to the array of nodes in the adapter. |
| uint32_t* size | Pointer to the number of elements. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. Returns ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapterEvent_GetUserData()

```c
void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the custom data passed in during registration of the specified event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Pointer to the adapter event object. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to the custom data. |

### OH_ArkUI_NodeAdapterEvent_GetType()

```c
ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the event type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Pointer to the adapter event object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeAdapterEventType](capi-native-node-h.md#arkui_nodeadaptereventtype) | Event type. |

### OH_ArkUI_NodeAdapterEvent_GetRemovedNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the element to be removed for the event to be destroyed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Pointer to the adapter event object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) | Element to be removed. |

### OH_ArkUI_NodeAdapterEvent_GetItemIndex()

```c
uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the index of the element to be operated for the specified adapter event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Pointer to the adapter event object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Sequence number of an element. |

### OH_ArkUI_NodeAdapterEvent_GetHostNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the scrollable container node that uses the specified adapter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Pointer to the adapter event object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) | Scrollable container node that uses the specified adapter. |

### OH_ArkUI_NodeAdapterEvent_SetItem()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)
```

**Description**

Sets the component to be added to the specified adapter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Pointer to the adapter event object. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Component to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeAdapterEvent_SetNodeId()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)
```

**Description**

Sets the component ID to be generated.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Pointer to the adapter event object. |
| int32_t id | Component ID to be returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure()

```c
ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the size constraint for measurement through a custom component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_LayoutConstraint*](capi-arkui-nativemodule-arkui-layoutconstraint.md) | Pointer to the size constraint. |

### OH_ArkUI_NodeCustomEvent_GetPositionInLayout()

```c
ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the expected position of a component relative to its parent component in the layout phase through a custom component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | Expected position relative to the parent component. |

### OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw()

```c
ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the drawing context through a custom component event. You need to release the obtained drawing context in a timely manner after use.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_DrawContext*](capi-arkui-nativemodule-arkui-drawcontext.md) | Pointer to the drawing context. |

### OH_ArkUI_NodeCustomEvent_GetEventTargetId()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the ID of a custom component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Custom event ID. |

### OH_ArkUI_NodeCustomEvent_GetUserData()

```c
void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains a custom event parameter through a custom component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to the custom event parameter. |

### OH_ArkUI_NodeCustomEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains a component object through a custom component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) | Component object. |

### OH_ArkUI_NodeCustomEvent_GetEventType()

```c
ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the event type through a custom component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeCustomEventType](capi-custom-attributes-h.md#arkui_nodecustomeventtype) | Type of the custom component event. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)
```

**Description**

Obtains the measurement information of a custom span through a custom component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |
| ArkUI_CustomSpanMeasureInfo* info | Pointer to the measurement information to be obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br> A possible cause is that mandatory parameters are left unspecified. |

### OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics()

```c
int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)
```

**Description**

Sets the measurement metrics of a custom span through a custom component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |
| ArkUI_CustomSpanMetrics* metrics | Pointer to the measurement metrics to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br> A possible cause is that mandatory parameters are left unspecified. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the drawing information of a custom span through a custom component event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |
| ArkUI_CustomSpanDrawInfo* info | Pointer to the drawing information to be obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br> A possible cause is that mandatory parameters are left unspecified. |

### ArkUI_NodeContentCallback()

```c
typedef void (*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)
```

**Description**

Defines a callback for the **NodeContent** event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Pointer to the **NodeContent** event. |

### OH_ArkUI_NodeContent_RegisterCallback()

```c
int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)
```

**Description**

Registers an event callback for **NodeContent**.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontenthandle.md) content | **NodeContent** object for which a callback needs to be registered. |
| [ArkUI_NodeContentCallback](capi-native-node-h.md#arkui_nodecontentcallback) callback | Callback to be executed when the event is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeContentEvent_GetEventType()

```c
ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)
```

**Description**

Obtains the type of the specified **NodeContent** event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Pointer to the **NodeContent** event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeContentEventType](capi-native-node-h.md#arkui_nodecontenteventtype) | Type of the **NodeContent** event. |

### OH_ArkUI_NodeContentEvent_GetNodeContentHandle()

```c
ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)
```

**Description**

Obtains the object that triggers the specified **NodeContent** event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Pointer to the **NodeContent** event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontenthandle.md) | **NodeContent** object that triggers the event. |

### OH_ArkUI_NodeContent_SetUserData()

```c
int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)
```

**Description**

Saves custom data to the specified **NodeContent** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontenthandle.md) content | **NodeContent** object to which custom data needs to be saved. |
| void* userData | Pointer to the custom data to be saved. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeContent_GetUserData()

```c
void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)
```

**Description**

Obtains the custom data saved on the specified **NodeContent** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontenthandle.md) content | **NodeContent** object on which custom data needs to be saved. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to the custom data. |

### OH_ArkUI_NodeContent_AddNode()

```c
int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**Description**

Adds an ArkUI component node to the specified **NodeContent** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontenthandle.md) content | **NodeContent** object to which a node is to be added. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Node to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_NODE_IS_ADOPTED if a child node has been accepted. This specification is supported since API version 22. |

### OH_ArkUI_NodeContent_RemoveNode()

```c
int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**Description**

Removes an ArkUI component node from the specified **NodeContent** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontenthandle.md) content | **NodeContent** object from which a node is to be removed. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Node to be removed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeContent_InsertNode()

```c
int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)
```

**Description**

Inserts an ArkUI component node into a specific position of the specified **NodeContent** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontenthandle.md) content | **NodeContent** object into which a node is to be inserted. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Node to be inserted. |
| int32_t position | Position where a node is to be inserted. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_NODE_IS_ADOPTED if a child node has been accepted. This specification is supported since API version 22. |

### OH_ArkUI_NodeUtils_GetLayoutSize()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)
```

**Description**

Obtains the layout area size of the component. The size does not count in transformation attributes, such as scale.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md)* size | Pointer to the size of the component handle layout area, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPosition()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)
```

**Description**

Obtains the position of the component's layout area relative to its parent component. The relative position does not count in transformation attributes, such as translate.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* localOffset | Pointer to the offset of the component handle relative to the parent component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**Description**

Obtains the position of the component's layout area relative to the window. The relative position does not count in transformation attributes, such as translate.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | Pointer to the offset of the component handle relative to the window, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)
```

**Description**

Obtains the position of the component's layout area relative to the screen. The relative position does not count in transformation attributes, such as translate.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* screenOffset | Pointer to the offset of the component handle relative to the screen, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)
```

**Description**

Obtains the offset of the specified component relative to the global display. The relative position does not count in transformation attributes, such as translate.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* offset | Pointer to the offset of the component handle relative to the screen, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**Description**

Obtains the position of the component in the window, including the translate attribute.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* translateOffset | Pointer to the accumulated offset of the component handle, its parent component, and its ancestor node, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**Description**

Obtains the position of the component on the screen, including the translate attribute.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | ArkUI_NodeHandle pointer. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* translateOffset | Pointer to the accumulated offset of the component handle, its parent component, and its ancestor node, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_AddCustomProperty()

```c
void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)
```

**Description**

Sets a custom property for a component. This API takes effect only in the main thread.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | **ArkUI_NodeHandle** pointer. |
| const char* name | Pointer to the name of the custom property. A null pointer is not allowed. |
| const char* value | Pointer to the value of the custom property corresponding to the key parameter name. A null pointer is not allowed. |

### OH_ArkUI_NodeUtils_RemoveCustomProperty()

```c
void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)
```

**Description**

Removes a custom property that has been set for the specified component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | **ArkUI_NodeHandle** pointer. |
| const char* name | Pointer to the name of the custom property. |

### OH_ArkUI_NodeUtils_GetCustomProperty()

```c
int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)
```

**Description**

Obtains the custom property of a component and returns an **ArkUI_CustomProperty** instance through a handle.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | **ArkUI_NodeHandle** pointer. |
| const char* name | Pointer to the name of the custom property. |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)** handle | Double pointer to the struct that receives the custom property corresponding to the key parameter name. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetParentInPageTree()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)
```

**Description**

Obtains the parent node, which can be a component node created with ArkTS.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) | Pointer to the component if the component exists; **NULL** otherwise. |

### OH_ArkUI_NodeUtils_GetActiveChildrenInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)
```

**Description**

Obtains the FrameNode child node whose internal active state is **true** and generates an [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md) instance. Spans are not counted as child nodes.<br> After the child node is obtained, you can call [OH_ArkUI_ActiveChildrenInfo_GetCount](capi-native-type-h.md#oh_arkui_activechildreninfo_getcount) to obtain the number of child nodes and call [OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex](capi-native-type-h.md#oh_arkui_activechildreninfo_getnodebyindex) to read the child nodes by index. After the instance is used, you must call [OH_ArkUI_ActiveChildrenInfo_Destroy](capi-native-type-h.md#oh_arkui_activechildreninfo_destroy) to destroy it. In **LazyForEach**<br>scenarios, you are advised to use the [OH_ArkUI_NodeUtils_GetChildWithExpandMode](capi-native-node-h.md#oh_arkui_nodeutils_getchildwithexpandmode) API for traversal.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) head | Node for which to obtain the child nodes. |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)** handle | Double pointer to the struct containing information about the child nodes of the head node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetCurrentPageRootNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)
```

**Description**

Obtains the root node of the current page.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) | Pointer to the root node if the node exists; **NULL** otherwise. |

### OH_ArkUI_NodeUtils_IsCreatedByNDK()

```c
bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)
```

**Description**

Checks whether the specified component is created with C APIs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether the node is created with the C API. The value **true** means that the node is created with the C API, and **false** means the opposite. |

### OH_ArkUI_NodeUtils_GetNodeType()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)
```

**Description**

Obtains the type of the specified node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Type of the node. Returns **-1** if the type is not supported yet. For details about the available types, see [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype). |

### OH_ArkUI_NodeUtils_GetWindowInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)
```

**Description**

Obtains the information about the window to which a node belongs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node object. |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)** info | Double pointer to the window information object. The memory allocated for this object must be released using [OH_ArkUI_HostWindowInfo_Destroy](capi-native-type-h.md#oh_arkui_hostwindowinfo_destroy). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if a C API initialization error occurs. <br>Returns ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE if the node is not mounted to the node tree. |

### OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**Description**

Obtains the index of the first child node of the target node in the tree without expanding any nodes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Pointer to the target node. |
| uint32_t* index | Pointer to the index of the child node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**Description**

Obtains the index of the last child node of the target node in the tree without expanding any nodes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Pointer to the target node. |
| uint32_t* index | Pointer to the index of the child node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetChildWithExpandMode()

```c
int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)
```

**Description**

Obtains a child node at the specified index using different expansion modes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Pointer to the target node. |
| int32_t position | Index of the child node to obtain. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md)* subnode | Pointer to the obtained child node. |
| uint32_t expandMode | Expansion mode for node traversal. For details, see [ArkUI_ExpandMode](capi-native-type-h.md#arkui_expandmode). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_List_CloseAllSwipeActions()

```c
int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (*onFinish)(void* userData))
```

**Description**

Collapses the list items in the expanded state.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Node object for which an event needs to be registered. |
| void* userData | Pointer to the custom event parameter, which is passed in the callback when the event is triggered. |
| void (*onFinish)(void* userData) | Pointer to the callback invoked when the collapse animation is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED if the event is not supported. |

### OH_ArkUI_GetContextByNode()

```c
ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)
```

**Description**

Obtains the pointer to the UI context object of the specified node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) | Pointer to the UI context object. If a null pointer is returned, it may be because the node is empty. |

### OH_ArkUI_RegisterSystemColorModeChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node, void* userData, void (*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))
```

**Description**

Registers an event listener for system color mode changes. A single component can only register one callback for system color mode changes. For implementation examples, see Adding an Event Listener.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Specified node. |
| void* userData | Pointer to the custom event parameter, which is passed in the callback when the event is triggered. |
| void (*onColorModeChange)(ArkUI_SystemColorMode colorMode | Pointer to the callback to be executed when the event is triggered. [ArkUI_SystemColorMode](capi-native-type-h.md#arkui_systemcolormode) defines the system color mode (light/dark). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_UnregisterSystemColorModeChangeEvent()

```c
void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)
```

**Description**

Unregisters the event listener for system color mode changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |

### OH_ArkUI_RegisterSystemFontStyleChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node, void* userData, void (*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))
```

**Description**

Registers an event listener for system font style changes. A single component can only register one callback for system font style changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Specified node. |
| void* userData | Pointer to the custom event parameter, which is passed in the callback when the event is triggered. |
| void (*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event | Pointer to the callback to be executed when the event is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_UnregisterSystemFontStyleChangeEvent()

```c
void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)
```

**Description**

Unregisters the event listener for system font style changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |

### OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)
```

**Description**

Obtains the font size in the system font style change event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md)* event | Pointer to the current system font style change event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Font size scale after the change. Default value: **1.0**. |

### OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)
```

**Description**

Obtains the font weight in the system font style change event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md)* event | Pointer to the current system font style change event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Font weight scale after the change. Default value: **1.0**. |

### OH_ArkUI_NodeUtils_GetAttachedNodeHandleById()

```c
int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)
```

**Description**

Obtains the target node based on the provided user ID.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* id | ID of the target node. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md)* node | Pointer to the target node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_MoveTo()

```c
int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)
```

**Description**

Moves a node to a target parent node as a child.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Node to be moved. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) target_parent | Pointer to the target parent node. |
| int32_t index | Index of the node after the movement. If the index is invalid, the node will be added to the end of the target parent node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if a C API initialization error occurs. <br>Returns ARKUI_ERROR_CODE_NODE_IS_ADOPTED if a child node has been accepted. This specification is supported since API version 22. |

### OH_ArkUI_NativeModule_InvalidateAttributes()

```c
int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)
```

**Description**

Triggers the node attribute update in this frame.<br> If the attributes of the current node are modified after the build phase, these changes do not take effect immediately but are deferred for batch processing in the next frame.<br> This API forces immediate node updates within the current frame, ensuring that rendering effects are applied synchronously.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Node whose attributes are to be updated. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_SetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**Description**

Sets the cross-language option for the target node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Pointer to the target node. |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | Pointer to the cross-language configuration option ([ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**Description**

Obtains the cross-language option of the target node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Pointer to the target node. |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | Pointer to the cross-language configuration option ([ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_RegisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (*onLayoutCompleted)(void* userData))
```

**Description**

Registers a layout completion callback function for a specific node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Target node for which the callback function is to be registered. |
| void* userData | Pointer to the custom parameter passed to the callback function when it is invoked. |
| void (*onLayoutCompleted)(void* userData) | Pointer to the callback function to be invoked when layout is completed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_RegisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (*onDrawCompleted)(void* userData))
```

**Description**

Registers a drawing completion callback function for a specific node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Target node for which the callback function is to be registered. |
| void* userData | Pointer to the custom parameter passed to the callback function when it is invoked. |
| void (*onDrawCompleted)(void* userData) | Pointer to the callback function to be invoked when drawing is completed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**Description**

Unregisters the layout completion callback function for a specific node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node for which the callback function is to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_UnregisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**Description**

Unregisters the drawing completion callback function for a specific node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node for which the callback function is to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_GetNodeSnapshot()

```c
int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelmap)
```

**Description**

Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered, the snapshot operation will fail. When the PixelMap is no longer used, you should call OH_PixelmapNative_Release to release it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node to capture a snapshot. |
| ArkUI_SnapshotOptions* snapshotOptions | Pointer to the snapshot configuration. If the value is null, the default configuration is used.<br>The screenshot configuration includes the scaling attribute, color space, and dynamic range mode. The color space and dynamic range mode are supported since API version 23.<br>The scaling attribute value is a floating point number greater than 0. The default value is **1.0**.<br>The color space value can be **3**<br>(RGB color gamut is of the Display P3 type), **4** (RGB color gamut is of the SRGB type), or **27** (RGB color gamut is of the Display BT2020 type). The default value is **4**.<br> The dynamic range mode value is specified using [ArkUI_DynamicRangeMode](capi-image-h.md#arkui_dynamicrangemode). The default value is **ARKUI_DYNAMIC_RANGE_MODE_STANDARD**. |
| OH_PixelmapNative** pixelmap | Pointer to the Pixelmap created by the system. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_INTERNAL_ERROR if the snapshot fails, returning a null pointer. <br>Returns ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT if the snapshot operation times out. <br>Returns ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED if the color space or dynamic range mode set in the screenshot options is not supported. <br>Returns ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED if the **isAuto** parameter of the color space or dynamic range mode cannot be set to **true** for the offscreen node snapshot. |

### OH_ArkUI_GetNodeSnapshotSizeLimitation()

```c
int32_t OH_ArkUI_GetNodeSnapshotSizeLimitation(int32_t* maxWidth, int32_t* maxHeight)
```

**Description**

Obtains the size limit of a component screenshot.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t* maxWidth | Pointer to the maximum width of a component screenshot, in px. |
| int32_t* maxHeight | Pointer to the maximum height of a component screenshot, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionToParent()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**Description**

Obtains the offset of the target node relative to its parent node, in px.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | Pointer to the offset of the target node relative to its parent node, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_AddSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)
```

**Description**

Adds the polymorphic style states supported by the component. To handle states efficiently, specify the states of interest and their corresponding handlers. When a state of interest occurs, the handler will be executed. You can adjust the UI style based on the current state within the callback. If this API is called multiple times on the same node, the last set of states and handlers will take precedence. Some component types have default system handling for certain states. For example, the **Button** component has a default style effect for the PRESSED state. When custom state handling is implemented on such components, the default style effect will be applied first, followed by the custom style changes, resulting in a combined effect. To disable the default style effects, set **excludeInner** to **true**, if this is allowed by the system implementation. When this API is called, the provided handler function will be executed immediately. There is no need to explicitly register a listener for the NORMAL state. Once a non-NORMAL state is registered, the system will automatically notify your application when the state changes back to NORMAL.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Target node. |
| int32_t uiStates | Target UI states to be handled on the node. The combination of all target UI states can be calculated using the **\|** operator. Example: targetUIStates = ArkUI_UIState::PRESSED \| ArkUI_UIState::FOCUSED |
| void (statesChangeHandler)(int32_t currentStates | Handler for UI state changes. It returns the current UI status. The value is the result of combining all current state enum values using the **\|** operator. You can determine the state using the **&** operator. Example: **if (currentStates & ArkUI_UIState::PRESSED == ArkUI_UIState::PRESSED)**. However, for checking the normal state, use the equality operator directly. Example: **if (currentStates == ArkUI_UIState::NORMAL)**. |
| bool excludeInner | Whether to disable the default state styles. **true**: Disable the default state styles. **false**: Do not disable the default state styles. |
| void* userData) | Pointer to the custom data used in the **onDrawCompleted** callback. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_RemoveSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)
```

**Description**

Removes registered UI states. When all states registered using **OH_ArkUI_AddSupportedUIStates** are removed, the registered **stateChangeHandler** will no longer be executed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node. |
| int32_t uiStates | Target UI states to be removed. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_RunTaskInScope()

```c
int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(*callback)(void* userData))
```

**Description**

Executes the specified callback in the target UI context. For the implementation example, see Ensuring Multi-Instance Functionality in the NDK.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle uiContext | Pointer to the target UI context. |
| void* userData | Pointer to the user-defined data for processing custom data within the callback function. You are responsible for ensuring the validity of the data when the custom function is executed. |
| void(*callback)(void* userData) | Pointer to the user-defined callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if C API initialization failed. <br>Returns ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if the **UIContext** object is invalid. <br>Returns ARKUI_ERROR_CODE_CALLBACK_INVALID if the callback function is invalid. |

### OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)
```

**Description**

Obtain a node by its unique ID.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const uint32_t uniqueId | Unique ID of the target node. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md)* node | Pointer to the target node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if C API initialization failed. |

### OH_ArkUI_NodeUtils_GetNodeUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)
```

**Description**

Obtains the unique ID of the target node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | ArkUI node pointer. |
| int32_t* uniqueId | Pointer to the unique ID of the target node. The component ID is read-only and unique in the process. If the node exists, the unique ID of the node is returned. Otherwise, **-1** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if C API initialization failed. |

### OH_ArkUI_NativeModule_IsInRenderState()

```c
int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)
```

**Description**

Obtains whether a node is in the render state. If RenderNode of a node is in the render tree, the node is in the render state.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | ArkUI node pointer. |
| bool* isInRenderState | Pointer to the **isInRenderState** parameter indicating whether the node is in render state. *<br>*true**: The node is in the render state. **false**: The node is not in the render state. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if C API initialization failed. |

### OH_ArkUI_NativeModule_AdoptChild()

```c
int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**Description**

Adopts the target node as an affiliated node. The adopted node must not have an existing parent. This API is not used to add a node as a child node. Instead, it only allows the node to receive lifecycle callbacks of the corresponding child node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | **ArkUI_NodeHandle** pointer, which specifies the parent node of the node to be adopted. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) child | **ArkUI_NodeHandle** pointer, which specifies the child node to be adopted. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if C API initialization failed. <br>Returns ARKUI_ERROR_CODE_NODE_HAS_PARENT if the adopted node already has a parent node. <br>Returns ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED if the node cannot be adopted as an affiliated node. <br>Returns ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO if the node cannot adopt other affiliated nodes. |

### OH_ArkUI_NativeModule_RemoveAdoptedChild()

```c
int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**Description**

Removes a previously-adopted affiliated node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | **ArkUI_NodeHandle** pointer, which specifies the parent node. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) child | **ArkUI_NodeHandle** pointer, which specifies the child node to be removed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if C API initialization failed. <br>Returns ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN if the node is not an affiliated node adopted by the target node. |

### OH_ArkUI_SetForceDarkConfig()

```c
int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (*colorInvertFunc)(uint32_t color))
```

**Description**

Sets the color inversion algorithm for the component and instance. For details, see Using Color Inversion for Quick Dark Mode Adaptation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle uiContext | Pointer to the UI instance object.<br>  If the value is **null**, this function applies to the entire application process. |
| bool forceDark | Whether to use the color inversion capability. **true** to use; **false** otherwise. |
| [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype) nodeType | Component scope where the color inversion capability takes effect.<br>   **ARKUI_NODE_UNDEFINED**<br>indicates that the setting takes effect for all component types. |
| uint32_t (*colorInvertFunc)(uint32_t color) | Pointer to the custom color inversion algorithm function.<br> If the value is **nullptr**, the default color inversion algorithm is used for the component, that is, the three primary colors are inverted. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if a C API initialization error occurs. <br>Returns ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID if the input parameter of the color inversion capability is incorrect. |

### OH_ArkUI_NativeModule_RegisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**Description**

Registers a basic event callback for the target node.<br> Currently, the following event types are supported: **NODE_ON_CLICK_EVENT**, **NODE_TOUCH_EVENT**, **NODE_EVENT_ON_APPEAR**, **NODE_EVENT_ON_DISAPPEAR**, **NODE_ON_KEY_EVENT**, **NODE_ON_FOCUS**, **NODE_ON_BLUR**, **NODE_ON_HOVER**, **NODE_ON_MOUSE**, and **NODE_ON_SIZE_CHANGE**. For details, see [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Target node. |
| [ArkUI_NodeEventType](capi-arkui-nodeeventtype.md) eventType | Event type. |
| void* userData | Pointer to the user-defined data for processing custom data within the callback function. You are responsible for ensuring the validity of the data when the custom function is executed. |
| void (*callback)(ArkUI_NodeEvent* event) | Pointer to the user-defined callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE if the event type is not supported. |

### OH_ArkUI_NativeModule_UnregisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)
```

**Description**

Unregisters the basic event callback for the target node.<br> For details about the supported event types, see [OH_ArkUI_NativeModule_RegisterCommonEvent](capi-native-node-h.md#oh_arkui_nativemodule_registercommonevent).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node. |
| [ArkUI_NodeEventType](capi-arkui-nodeeventtype.md) eventType | Event type. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE if the event type is not supported. |

### OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**Description**

Registers a basic event callback for visible area changes with a constrained callback interval.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Target node. |
| float* ratios | Pointer to the array of threshold ratios, representing the visible area of the component. |
| int32_t size | Size of the array of threshold ratios. |
| float expectedUpdateInterval | Expected calculation interval. |
| void* userData | Pointer to the user-defined data for processing custom data within the callback function. You are responsible for ensuring the validity of the data when the custom function is executed. |
| void (*callback)(ArkUI_NodeEvent* event) | Pointer to the user-defined callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)
```

**Description**

Unregisters the basic event callback for visible area changes with a constrained callback interval.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NativeModule_ConvertPositionToWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)
```

**Description**

Converts the coordinates of a point from the coordinate system of a specified node to that of the current window. For a coordinate system of a node, transformation of the node is considered. For example, if node A is translated leftward by 100, the coordinates of the points in its coordinate system will also be translated leftward by 100.<br> [](../../../../reference/apis-arkui/figures/ConvertToWindow.png)<br> As shown in the preceding figure, the coordinates (x0, y0) in the coordinate system of the specified node are converted to the coordinates (x1, y1) in the coordinate system of the window.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) currentNode | Specified node. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) localPosition | Coordinates of the point in the coordinate system of the specified node, in px. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* windowPosition | Pointer to the converted coordinates (in the current window coordinate system, in px). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE if the node is not mounted on the main component tree. |

### OH_ArkUI_NativeModule_ConvertPositionFromWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)
```

**Description**

Converts the coordinates of a point from the current window's coordinate system to the target node's coordinate system. For a coordinate system of a node, transformation of the node is considered. For example, if node A is translated leftward by 100, the coordinates of the points in its coordinate system will also be translated leftward by 100.<br> [](../../../../reference/apis-arkui/figures/ConvertFromWindow.png)<br> As shown in the preceding figure, the coordinates (x1, y1) in the window coordinate system are converted to the coordinates (x0, y0) in the coordinate system of the target node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) targetNode | Target node. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) windowPosition | Coordinates of the point in the current window coordinate system, in px. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* localPosition | Pointer to the converted coordinates (in the coordinate system of the target node, in px). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE if the node is not mounted on the main component tree. |

### OH_ArkUI_Swiper_FinishAnimation()

```c
int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)
```

**Description**

Stops the page turning animation that is being executed on the specified **Swiper** node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_PostAsyncUITask()

```c
int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (*asyncUITask)(void* asyncUITaskData), void (*onFinish)(void* asyncUITaskData))
```

**Description**

Submits the **asyncUITask** function to a non-UI thread provided by the ArkUI framework for execution. After **asyncUITask** finishes execution, the **onFinish** function is called in the UI thread.<br> This is suitable for scenarios involving multi-threaded UI component creation. You can use this API to create UI components in non-UI threads and then mount the created components to the main tree in the UI thread.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle context | Pointer to the UI instance object. |
| void* asyncUITaskData | Pointer to the user-defined data, which is passed as the input parameter of **asyncUITask**<br>and **onFinish**. A null pointer is allowed. |
| void (*asyncUITask)(void* asyncUITaskData) | Pointer to the function executed in the non-UI thread. |
| void (*onFinish)(void* asyncUITaskData) | Pointer to the function executed on the UI thread after **asyncUITask** is completed. A null pointer is allowed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if the context object is invalid, or **asyncUITask** is a null pointer. |

### OH_ArkUI_PostUITask()

```c
int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**Description**

Submits the **task** function to the UI thread for execution.<br> This is suitable for scenarios involving multi-threaded UI component creation. When you create UI components in a self-built thread, you can use this API to mount the created components to the main tree on the UI thread.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle context | Pointer to the UI instance object. |
| void* taskData | Pointer to the user-defined data, which is passed as the input parameter of **task**. A null pointer is allowed. |
| void (*task)(void* taskData) | Pointer to the function executed in the UI thread. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if the context object is invalid, or **task** is a null pointer. |

### OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible()

```c
int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)
```

**Description**

Sets the visibility of the menu bar.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | ArkUI context handle, which specifies the context of the ArkUI container. |
| bool visible | Whether the menu bar is visible. The value **true** indicates that the menu bar is visible, and **false** indicates the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if an instance error occurs (for example, the **uiContext** pointer is null, the container cannot be obtained through **uiContext**, or **uiContext** does not belong to atomic services). |

### OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**Description**

Registers a callback for listening for component size and area changes. This API can be called for a valid [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node at any time. The newly registered callback will replace the previously registered callback for this event and take effect from the next frame. When the callback is no longer needed, use [OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent](capi-native-node-h.md#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) to unregister it. Otherwise, the callback will be automatically unregistered when the node is released.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) pointer. |
| float expectedUpdateInterval | Interval at which the callback is triggered by the expected calculation area change, in ms. |
| void* userData | Pointer to the custom data. |
| void (*callback)(ArkUI_NodeEvent* event) | Pointer to the event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node)
```

**Description**

Unregisters the callback for listening for component size and area changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_PostUITaskAndWait()

```c
int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**Description**

Submits the **task** function to the UI thread for execution. The thread calling this API will block until the **task** function completes execution. Calling this API from the UI thread is equivalent to synchronously calling the **task** function.<br> This is suitable for scenarios involving multi-threaded UI component creation. When you need to call functions that are only supported on the UI thread during the multi-threaded component creation process, you can use this API to return to the UI thread to call the function and then resume multi-threaded component creation after the call completes.<br> When the UI thread is under high load, non-UI threads calling this API may block for extended periods, affecting the performance of multi-threaded UI component creation. Frequent use is not recommended.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle context | Pointer to the UI instance object. |
| void* taskData | Pointer to the user-defined data, which is passed as the input parameter of **task**. A null pointer is allowed. |
| void (*task)(void* taskData) | Pointer to the function executed in the UI thread. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if the context object is invalid, or **task** is a null pointer. |

### OH_ArkUI_Swiper_StartFakeDrag()

```c
int32_t OH_ArkUI_Swiper_StartFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)
```

**Description**

Starts a simulated drag on a **Swiper** node. [OH_ArkUI_Swiper_FakeDragBy](capi-native-node-h.md#oh_arkui_swiper_fakedragby) can be used to simulate a drag action. [OH_ArkUI_Swiper_StopFakeDrag](capi-native-node-h.md#oh_arkui_swiper_stopfakedrag) can be used to stop the drag simulation.<br> A simulated drag can be interrupted by a real drag. To ignore a drag event from a user during the simulated drag, use [NODE_SWIPER_DISABLE_SWIPE](capi-native-node-h.md#arkui_nodeattributetype).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |
| bool* isSuccessful | Pointer to the **isSuccessful** parameter indicating whether the simulated drag is successfully started. **true** is returned if the simulated drag is successfully started.<br> **false** is returned if **Swiper** is not ready to start the simulated drag or a real drag or simulated drag is in progress. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_Swiper_FakeDragBy()

```c
int32_t OH_ArkUI_Swiper_FakeDragBy(ArkUI_NodeHandle node, float offset, bool* isConsumedOffset)
```

**Description**

Simulates the drag effect by setting the offset of a **Swiper** node. Before calling this API, you must call [OH_ArkUI_Swiper_StartFakeDrag](capi-native-node-h.md#oh_arkui_swiper_startfakedrag) to start the drag simulation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |
| float offset | Offset to be dragged, in vp. |
| bool* isConsumedOffset | Pointer to the **isConsumedOffset** parameter indicating whether to consume the offset to trigger dragging. **true** is returned if the offset is consumed to trigger dragging.<br> **false** is returned if the dragging is not in progress or no offset is consumed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_Swiper_StopFakeDrag()

```c
int32_t OH_ArkUI_Swiper_StopFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)
```

**Description**

Stops the drag simulation on a **Swiper** node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |
| bool* isSuccessful | Pointer to the **isSuccessful** parameter indicating whether the simulated drag is successfully stopped. **true** is returned if the simulated drag is successfully stopped.<br> **false** is returned if **Swiper** is not ready to stop the simulated drag or no simulated drag is in progress. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_Swiper_IsFakeDragging()

```c
int32_t OH_ArkUI_Swiper_IsFakeDragging(ArkUI_NodeHandle node, bool* isFakeDragging)
```

**Description**

Obtains the drag simulation status on a **Swiper** node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |
| bool* isFakeDragging | Pointer to the **isFakeDragging** parameter indicating whether the simulated drag is in progress. **true** is returned if the simulated drag is in progress; **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_Swiper_ShowPrevious()

```c
int32_t OH_ArkUI_Swiper_ShowPrevious(ArkUI_NodeHandle node)
```

**Description**

Displays the previous page of a **Swiper** node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_Swiper_ShowNext()

```c
int32_t OH_ArkUI_Swiper_ShowNext(ArkUI_NodeHandle node)
```

**Description**

Displays the next page of a **Swiper** node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Specified node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_ArcSwiper_ShowPrevious()

```c
int32_t OH_ArkUI_ArcSwiper_ShowPrevious(ArkUI_NodeHandle node)
```

**Description**

Displays the previous page of the **ArcSwiper** node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | **ArkUI_NodeHandle** pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_ArcSwiper_ShowNext()

```c
int32_t OH_ArkUI_ArcSwiper_ShowNext(ArkUI_NodeHandle node)
```

**Description**

Displays the next page of the **ArcSwiper** node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | **ArkUI_NodeHandle** pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_ArcSwiper_FinishAnimation()

```c
int32_t OH_ArkUI_ArcSwiper_FinishAnimation(ArkUI_NodeHandle node)
```

**Description**

Finishes the animation being executed by the **ArcSwiper** node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | **ArkUI_NodeHandle** pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext()

```c
int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)
```

**Description**

Obtains the root node of the page of a specified instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | Pointer to the UI instance object. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md)* rootNode | Handle to the target root node. If the page corresponding to the context does not have a root node, this parameter is set to null. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if C API initialization failed. <br>Returns ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if an instance error occurs. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo()

```c
ArkUI_GestureCollectInterceptInfo* OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo(ArkUI_NodeEvent* nodeEvent)
```

**Description**

Obtains the **ArkUI_GestureCollectInterceptInfo** object from a specified **ArkUI_NodeEvent** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* nodeEvent | Pointer to the **ArkUI_NodeEvent** object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureCollectInterceptInfo*](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md) | Pointer to the **ArkUI_GestureCollectInterceptInfo** object. This return value is valid only during the callback and does not need to be released.<br>**null** is returned if the input parameter is invalid or is not the gesture collection interception information. |

### OH_ArkUI_NativeModule_SetChildMountPolicy()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_SetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy policy)
```

**Description**

Sets the child node mounting policy for a target node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node. |
| [OH_ArkUI_NodeMountPolicy](capi-native-type-h.md#oh_arkui_nodemountpolicy) policy | Mounting policy to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if a C API initialization error occurs. |

### OH_ArkUI_NativeModule_GetChildMountPolicy()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy* policy)
```

**Description**

Obtains the current child node mounting policy of a target node. The default child node mounting policy of a target node is OH_ARKUI_NODE_MOUNT_POLICY_SINGLE_IF_RENDER_NODE.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | Target node. |
| [OH_ArkUI_NodeMountPolicy](capi-native-type-h.md#oh_arkui_nodemountpolicy)* policy | Pointer to the child node mounting policy of the target node. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if a C API initialization error occurs. |

### OH_ArkUI_NodeUtils_SetUiDvsyncSwitch()

```c
ArkUI_ErrorCode OH_ArkUI_NodeUtils_SetUiDvsyncSwitch(ArkUI_ContextHandle context, bool enable)
```

**Description**

Sets the UI Dvsync switch.<br> When enabled, the system responds to Vsync requests more promptly and executes rendering tasks more frequently. It is typically enabled at the start of an animation in a self-rendering framework and disabled when the animation ends, to ensure smoother animation effects while preventing frequent Vsync requests from affecting other functionalities. Calling this function on a non-UI thread will cause the application to exit.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | [in] Pointer to an ArkUI_ContextHandle. |
| bool enable | [in] Whether to enable Dvsync. The value true enables Dvsync, and false disables Dvsync. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result. <ul><li>ARKUI_ERROR_CODE_NO_ERROR The operation is successful. </li><li>ARKUI_ERROR_CODE_CAPI_INIT_ERROR Failed to initialize the CAPI. </li><li>ARKUI_ERROR_CODE_PARAM_INVALID The function parameter is invalid.</li></ul> |

### OH_ArkUI_NativeModule_AdoptChildWithPolicy()

```c
int32_t OH_ArkUI_NativeModule_AdoptChildWithPolicy(ArkUI_NodeHandle node, ArkUI_NodeHandle child, OH_ArkUI_AdoptPolicy policy)
```

**Description**

Adopts the target node as an affiliated node. The adopted node must not have an existing parent. This API is not used to add a node as a child node. Instead, it only allows the node to receive lifecycle callbacks of the corresponding child node. Configure the render position of the overlay node of the adopted node by policy.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) node | [in] **ArkUI_NodeHandle** pointer, which specifies the parent node of the node to be adopted. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) child | [in] **ArkUI_NodeHandle** pointer, which specifies the child node to be adopted. |
| [OH_ArkUI_AdoptPolicy](capi-native-node-h.md#oh_arkui_adoptpolicy) policy | [in] Rendering position policy of overlay nodes of adopted node. Valid values correspond to [OH_ArkUI_AdoptPolicy](capi-native-node-h.md#oh_arkui_adoptpolicy). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <ul><li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if C API initialization failed.</li> <li>Returns ARKUI_ERROR_CODE_NODE_HAS_PARENT if the adopted node already has a parent node.</li> <li>Returns ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED if the node cannot be adopted as an affiliated node.</li> <li>Returns ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO if the node cannot adopt other affiliated nodes.</li></ul> |

### OH_ArkUI_NativeModule_SetAdoptedChildOverlayPositionCompensation()

```c
int32_t OH_ArkUI_NativeModule_SetAdoptedChildOverlayPositionCompensation(ArkUI_NodeHandle adoptedChild, const ArkUI_PointF* compensationOffset, const ArkUI_Matrix4* compensationTransform)
```

**Description**

Sets the position compensation from an adopted child to its adopt parent. The compensation represents the aggregate effect of the pure rendering node tree between them. First, the translation is performed using compensationOffset, and then the transformation is performed using compensationTransform. Compensation only takes effect if the child node has been adopted using the following policy [OH_ARKUI_NATIVE_MODULE_ADOPT_POLICY_OVERLAY_POSITION_FOLLOWS_ADOPT_PARENT_CHAIN](capi-native-node-h.md#oh_arkui_adoptpolicy).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) adoptedChild | [in] The adopted node that require location compensation. |
| const ArkUI_PointF* compensationOffset | [in] x/y offset compensation, in px. |
| const ArkUI_Matrix4* compensationTransform | [in] Aggregation transformation compensation. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <ul><li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_CAPI_INIT_ERROR if C API initialization failed.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if the parameter is invalid.</li> <li>Returns ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN if the child is not adopted with the required policy.</li></ul> |


