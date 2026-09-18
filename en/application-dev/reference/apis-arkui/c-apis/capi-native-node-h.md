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
| [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | ArkUI_NodeComponentEvent | Defines the parameter type of the component callback event. |
| [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) | ArkUI_StringAsyncEvent | Defines the string type parameter used by the component callback event. |
| [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) | ArkUI_TextChangeEvent | Defines a hybrid data structure for component events. |
| [ArkUI_NativeNodeAPI_1](capi-arkui-nativemodule-arkui-nativenodeapi-1.md) | ArkUI_NativeNodeAPI_1 | Provides a collection of native-side Node type APIs provided by ArkUI. APIs related to the Node module must be called on the main thread. |
| [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | OH_ArkUI_TextEditorChangeEvent | Defines a struct for the text content change event of the **TextEditor** component. |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md) | ArkUI_NodeCustomEvent | Defines the general structure of a custom component event. |
| [ArkUI_NodeAdapter*](capi-arkui-nativemodule-arkui-nodeadapter8h.md) | ArkUI_NodeAdapterHandle | Defines the component adapter, which is used for lazy loading of elements of scrollable components. |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md) | ArkUI_NodeAdapterEvent | Defines the component adapter event. |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md) | ArkUI_NodeContentEvent | Defines the general structure of a node content event. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NodeType](#arkui_nodetype) | ArkUI_NodeType | Enumerates ArkUI component types that can be created on the native side. |
| [ArkUI_NodeAttributeType](capi-arkui-nodeattributetype.md) | ArkUI_NodeAttributeType | Defines the ArkUI style attributes that can be set on the native side. |
| [ArkUI_NodeEventType](capi-arkui-nodeeventtype.md) | ArkUI_NodeEventType | Enumerates the event types supported by the NativeNode component. |
| [ArkUI_NodeDirtyFlag](#arkui_nodedirtyflag) | ArkUI_NodeDirtyFlag | Defines the dirty area flag passed in the <b>::markDirty</b> API. |
| [ArkUI_NodeAdapterEventType](#arkui_nodeadaptereventtype) | ArkUI_NodeAdapterEventType | Enumerates component adapter events. |
| [ArkUI_NodeContentEventType](#arkui_nodecontenteventtype) | ArkUI_NodeContentEventType | Defines the node content event type. |
| [ArkUI_InspectorErrorCode](#arkui_inspectorerrorcode) | ArkUI_InspectorErrorCode | Enumerates the inspector error codes. |

### Macro

| Name | Description |
| -- | -- |
| MAX_NODE_SCOPE_NUM 1000 | Define components max function size.<br>**Since**: 12 |
| MAX_COMPONENT_EVENT_ARG_NUM 12 | Define component event max args size.<br>**Since**: 12 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_geteventtype) | - | Obtains the type of a component event. |
| [int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettargetid) | - | Obtains the custom ID of a component event.<br> The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be applied to the dispatch logic of the same event entry function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver). |
| [ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodehandle) | - | Obtains the component object that triggers a component event. |
| [ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getinputevent) | - | Obtains input event (for example, touch event) data for a component event. |
| [ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodecomponentevent) | - | Obtains the numerical data in a component event. |
| [ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getstringasyncevent) | - | Obtains the string data in a component event. |
| [ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettextchangeevent) | - | Obtains the ArkUI_TextChangeEvent data from a component event. |
| [void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getuserdata) | - | Obtains the custom data in a component event.<br> This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the event is triggered. |
| [int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)](#oh_arkui_nodeevent_getnumbervalue) | - | Obtains the numeric-type parameter of a component event. |
| [int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)](#oh_arkui_nodeevent_getstringvalue) | - | Obtains the string-type parameter of a component event. The string data is valid only during an event callback. To use it outside an event callback, you are advised to copy the string data. |
| [int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)](#oh_arkui_nodeevent_setreturnnumbervalue) | - | Sets the return value for a component event. |
| [ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_gettouchtestinfo) | - | Obtains the touch test information in a component event. |
| [OH_ArkUI_TextEditorChangeEvent* OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettexteditoronwillchangeevent) | - | Obtains the text content change data of the **TextEditor** component in the component event. |
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
| [int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)](#oh_arkui_nodeadapter_getallitems) | - | Obtains all elements stored in the specified adapter.<br> This API returns the pointer to the array of the elements. You need to manually release the memory data to which the pointer points. |
| [void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getuserdata) | - | Obtains the custom data passed in during registration of the specified event. |
| [ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gettype) | - | Obtains the event type. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getremovednode) | - | Obtains the element to be removed for the event to be destroyed. |
| [uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getitemindex) | - | Obtains the index of the element to be operated for the specified adapter event. |
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gethostnode) | - | Obtains the scrollable container node that uses the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)](#oh_arkui_nodeadapterevent_setitem) | - | Sets the component to be added to the specified adapter. |
| [int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)](#oh_arkui_nodeadapterevent_setnodeid) | - | Sets the component ID to be generated. |
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
| [int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)](#oh_arkui_nodecontent_registercallback) | - | register a callback function to a node content. |
| [ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_geteventtype) | - | Obtains the type of a node content event. |
| [ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_getnodecontenthandle) | - | Obtains the node content object that triggers a node content event. |
| [int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)](#oh_arkui_nodecontent_setuserdata) | - | Saves custom data on the specified node content. |
| [void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)](#oh_arkui_nodecontent_getuserdata) | - | Obtains the custom data saved on the specified node content. |
| [int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_addnode) | - | Adds an ArkUI component node to the specified **NodeContent** object. |
| [int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_removenode) | - | Removes an ArkUI component node from the specified **NodeContent** object. |
| [int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)](#oh_arkui_nodecontent_insertnode) | - | Inserts an ArkUI component node into a specific position of the specified **NodeContent** object. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)](#oh_arkui_nodeutils_getlayoutsize) | - | Get the size of the component layout area. The layout area size does not include graphic variation attributes such as scaling. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)](#oh_arkui_nodeutils_getlayoutposition) | - | Obtain the position of the component layout area relative to the parent component. The relative position of the layout area does not include graphic variation attributes, such as translation. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getlayoutpositioninwindow) | - | Obtain the position of the component layout area relative to the window. The relative position of the layout area does not include graphic variation attributes, such as translation. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)](#oh_arkui_nodeutils_getlayoutpositioninscreen) | - | Obtain the position of the component layout area relative to the screen. The relative position of the layout area does not include graphic variation attributes, such as translation. |
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)](#oh_arkui_nodeutils_getlayoutpositioninglobaldisplay) | - | Obtains the offset of a component relative to the global display. The relative position does not count in transformation attributes, such as translate. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinwindow) | - | Obtain the position of the component in the window, including the properties of graphic translation changes. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinscreen) | - | Obtain the position of the component on the screen, including the attributes of graphic translation changes. |
| [void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)](#oh_arkui_nodeutils_addcustomproperty) | - | Sets a custom property for a component. This API takes effect only in the main thread. |
| [void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)](#oh_arkui_nodeutils_removecustomproperty) | - | Removes a custom property that has been set for the specified component. |
| [int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)](#oh_arkui_nodeutils_getcustomproperty) | - | Obtains the value of a custom property of the specified component. |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getparentinpagetree) | - | Obtains the parent node, which can be a component node created with ArkTS. |
| [int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)](#oh_arkui_nodeutils_getactivechildreninfo) | - | Obtains all active child nodes of the specified node. Spans are not counted as child nodes. In **LazyForEach**<br>scenarios, you are advised to use the [OH_ArkUI_NodeUtils_GetChildWithExpandMode](capi-native-node-h.md#oh_arkui_nodeutils_getchildwithexpandmode) API for traversal. |
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getcurrentpagerootnode) | - | Obtains the root node of the current page. |
| [bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_iscreatedbyndk) | - | Checks whether the specified component is created with C APIs. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getnodetype) | - | Obtains the type of the specified node. |
| [int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)](#oh_arkui_nodeutils_getwindowinfo) | - | Obtains the information about the window to which a node belongs. |
| [int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getfirstchildindexwithoutexpand) | - | Obtains the index of the first child node of the target node in the tree without expanding any nodes. |
| [int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getlastchildindexwithoutexpand) | - | Obtains the index of the last child node of the target node in the tree without expanding any nodes. |
| [int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)](#oh_arkui_nodeutils_getchildwithexpandmode) | - | Obtains a child node at the specified index using different expansion modes. |
| [int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_list_closeallswipeactions) | - | Collapse the ListItem in its expanded state. |
| [ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)](#oh_arkui_getcontextbynode) | - | Obtain the UIContext pointer to the page where the node is located. |
| [int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))](#oh_arkui_registersystemcolormodechangeevent) | - | The event called when the system color mode changes. Only one system color change callback can be registered for the same component. |
| [void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemcolormodechangeevent) | - | Unregister the event callback when the system color mode changes. |
| [int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node, void* userData, void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))](#oh_arkui_registersystemfontstylechangeevent) | - | The event called when the system font style changes. Only one system font change callback can be registered for the same component. |
| [void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemfontstylechangeevent) | - | Unregister the event callback when the system font style changes. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontsizescale) | - | Retrieve the font size value for system font change events. |
| [float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontweightscale) | - | Retrieve the font thickness values for system font change events. |
| [int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getattachednodehandlebyid) | - | Get the node handle by id. |
| [int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)](#oh_arkui_nodeutils_moveto) | - | Moves a node to a target parent node as a child. |
| [int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_invalidateattributes) | - | Triggers the node attribute update in this frame. If the attributes of the current node are modified after the build phase, these changes do not take effect immediately but are deferred for batch processing in the next frame. This API forces immediate node updates within the current frame, ensuring that rendering effects are applied synchronously. |
| [int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_setcrosslanguageoption) | - | Sets the cross-language option for the target node. |
| [int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_getcrosslanguageoption) | - | Obtains the cross-language option of the target node. |
| [int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onLayoutCompleted)(void* userData))](#oh_arkui_registerlayoutcallbackonnodehandle) | - | Registers a callback for node when layout is completed. |
| [int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (\*onDrawCompleted)(void* userData))](#oh_arkui_registerdrawcallbackonnodehandle) | - | Registers a callback for node when draw is completed. |
| [int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterlayoutcallbackonnodehandle) | - | Unregisters the layout completed callback for node. |
| [int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterdrawcallbackonnodehandle) | - | Unregisters the draw completed callback for node. |
| [int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelmap)](#oh_arkui_getnodesnapshot) | - | Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered, the snapshot operation will fail. When the <b>Pixelmap</b> object created is no longer in use, it should be released by calling {@link OH_PixelmapNative_Release}. |
| [int32_t OH_ArkUI_GetNodeSnapshotSizeLimitation(int32_t* maxWidth, int32_t* maxHeight)](#oh_arkui_getnodesnapshotsizelimitation) | - | Query the size limitation of the component snapshot. |
| [int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getpositiontoparent) | - | Obtains the offset of a specific node relative to its parent node. |
| [ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)](#oh_arkui_addsupporteduistates) | - | Adds the UI state style supported by the component. To handle states change efficiently, need to specify the states of interest and the corresponding handler. When a state of interest occurs, the handler will be executed. - You can adjust the UI style based on the current state within the callback. If this API is called multiple times on the same node, the last set of states and handler will take precedence. - Some component types have default system handling for certain states. For example, the <b>Button</b> component has a default style effect for the PRESSED state. When custom state handling is implemented on such components, the default style effect will be applied first, followed by the custom style changes, resulting in a combined effect. To disable the default style effects, set <b>excludeInner</b> to <b>true</b>, if this is allowed by the system implementation. - And when this API is called, the provided handler function will be executed immediately. - There is no need to explicitly register a listener for the NORMAL state. Once a non-NORMAL state is registered, the system will automatically notify your application when the state changes back to NORMAL. |
| [ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)](#oh_arkui_removesupporteduistates) | - | Removes registered UI states. When all states registered using **OH_ArkUI_AddSupportedUIStates** are removed, the registered **stateChangeHandler** will no longer be executed. |
| [int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(\*callback)(void* userData))](#oh_arkui_runtaskinscope) | - | Executes the specified callback in the target UI context. For the implementation example, see {@link Ensuring Multi-Instance Functionality in the NDK}. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getnodehandlebyuniqueid) | - | Obtain a node by its unique ID. |
| [int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)](#oh_arkui_nodeutils_getnodeuniqueid) | - | Obtains the unique ID of the target node. |
| [int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)](#oh_arkui_nativemodule_isinrenderstate) | - | Obtains whether a node is in the render state. If {@link RenderNode} of a node is in the render tree, the node is in the render state. |
| [int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_adoptchild) | - | Adopts the target node as an affiliated node. The adopted node must not have an existing parent. This API is not used to add a node as a child node. Instead, it only allows the node to receive lifecycle callbacks of the corresponding child node. |
| [int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_removeadoptedchild) | - | Removes a previously-adopted affiliated node. |
| [int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (\*colorInvertFunc)(uint32_t color))](#oh_arkui_setforcedarkconfig) | - | Sets the inverse color algorithm for components and instances. |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonevent) | - | Registers a basic event callback for the target node.<br> Currently, the following event types are supported: **NODE_ON_CLICK_EVENT**, **NODE_TOUCH_EVENT**, **NODE_EVENT_ON_APPEAR**, **NODE_EVENT_ON_DISAPPEAR**, **NODE_ON_KEY_EVENT**, **NODE_ON_FOCUS**, **NODE_ON_BLUR**, **NODE_ON_HOVER**, **NODE_ON_MOUSE**, and **NODE_ON_SIZE_CHANGE**. For details, see @{link ArkUI_NodeEventType}. |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)](#oh_arkui_nativemodule_unregistercommonevent) | - | Unregisters the basic event callback for the target node.<br> For details about the supported event types, see [OH_ArkUI_NativeModule_RegisterCommonEvent](capi-native-node-h.md#oh_arkui_nativemodule_registercommonevent). |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonvisibleareaapproximatechangeevent) | - | Registers a basic event callback for visible area changes with a constrained callback interval. |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonvisibleareaapproximatechangeevent) | - | Unregisters the basic event callback for visible area changes with a constrained callback interval. |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)](#oh_arkui_nativemodule_convertpositiontowindow) | - | Converts the coordinates of a point from the coordinate system of a specified node to that of the current window. For a coordinate system of a node, transformation of the node is considered. For example, if node A is translated leftward by 100, the coordinates of the points in its coordinate system will also be translated leftward by 100.<br> [](docroot://reference/apis-arkui/figures/ConvertToWindow.png)<br> As shown in the preceding figure, the coordinates (x0, y0) in the coordinate system of the specified node are converted to the coordinates (x1, y1) in the coordinate system of the window. |
| [int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)](#oh_arkui_nativemodule_convertpositionfromwindow) | - | Converts the coordinates of a point from the current window's coordinate system to the target node's coordinate system. For a coordinate system of a node, transformation of the node is considered. For example, if node A is translated leftward by 100, the coordinates of the points in its coordinate system will also be translated leftward by 100.<br> [](docroot://reference/apis-arkui/figures/ConvertFromWindow.png)<br> As shown in the preceding figure, the coordinates (x1, y1) in the window coordinate system are converted to the coordinates (x0, y0) in the coordinate system of the target node. |
| [int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)](#oh_arkui_swiper_finishanimation) | - | Stop the animation being executed by the Swiper node. |
| [int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (\*asyncUITask)(void* asyncUITaskData), void (\*onFinish)(void* asyncUITaskData))](#oh_arkui_postasyncuitask) | - | Submits the **asyncUITask** function to a non-UI thread provided by the ArkUI framework for execution. After **asyncUITask** finishes execution, the **onFinish** function is called in the UI thread.<br> This is suitable for scenarios involving multi-threaded UI component creation. You can use this API to create UI components in non-UI threads and then mount the created components to the main tree in the UI thread. |
| [int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitask) | - | Submits the **task** function to the UI thread for execution.<br> This is suitable for scenarios involving multi-threaded UI component creation. When you create UI components in a self-built thread, you can use this API to mount the created components to the main tree on the UI thread. |
| [int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)](#oh_arkui_nativemodule_atomicservicemenubarsetvisible) | - | set the visiblity of the menubar. |
| [int32_t OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node, float expectedUpdateInterval, void* userData, void (\*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonareaapproximatechangeevent) | - | Registers a callback for listening for component dimension and area changes.<br> This function can be called for a valid {@link ArkUI_NodeHandle} node at any time. The newly registered callback will replace the previously registered callback for this event and will take effect from the next frame. When the callback is no longer needed, call [OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent](capi-native-node-h.md#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) to unregister it. Otherwise, the callback will be automatically unregistered when the node is released. |
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) | - | Unregisters the callback bound to the dimensions and area changes of a component. |
| [int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (\*task)(void* taskData))](#oh_arkui_postuitaskandwait) | - | Post UI task to UI thread and wait until UI task finished. |
| [int32_t OH_ArkUI_Swiper_StartFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_startfakedrag) | - | Start a fake drag of the Swiper node. Call OH_ArkUI_Swiper_FakeDragBy to simulate the drag motion. Call OH_ArkUI_Swiper_StopFakeDrag to complete the fake drag. A fake drag can be interrupted by a real drag. If you need to ignore touch events and other user input during a fake drag, use NODE_SWIPER_DISABLE_SWIPE. |
| [int32_t OH_ArkUI_Swiper_FakeDragBy(ArkUI_NodeHandle node, float offset, bool* isConsumedOffset)](#oh_arkui_swiper_fakedragby) | - | Fake drag by an offset of the Swiper node. The OH_ArkUI_Swiper_StartFakeDrag must be called first. |
| [int32_t OH_ArkUI_Swiper_StopFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)](#oh_arkui_swiper_stopfakedrag) | - | Stop a fake drag of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_IsFakeDragging(ArkUI_NodeHandle node, bool* isFakeDragging)](#oh_arkui_swiper_isfakedragging) | - | Get the fake drag state of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_ShowPrevious(ArkUI_NodeHandle node)](#oh_arkui_swiper_showprevious) | - | Show the previous page of the Swiper node. |
| [int32_t OH_ArkUI_Swiper_ShowNext(ArkUI_NodeHandle node)](#oh_arkui_swiper_shownext) | - | Show the next page of the Swiper node. |
| [int32_t OH_ArkUI_ArcSwiper_ShowPrevious(ArkUI_NodeHandle node)](#oh_arkui_arcswiper_showprevious) | - | Show the previous page of the ArcSwiper node. |
| [int32_t OH_ArkUI_ArcSwiper_ShowNext(ArkUI_NodeHandle node)](#oh_arkui_arcswiper_shownext) | - | Show the next page of the ArcSwiper node. |
| [int32_t OH_ArkUI_ArcSwiper_FinishAnimation(ArkUI_NodeHandle node)](#oh_arkui_arcswiper_finishanimation) | - | Stop the animation executed by the ArcSwiper node. |
| [int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)](#oh_arkui_nativemodule_getpagerootnodehandlebycontext) | - | Obtains the root node of the page of a specified instance. |
| [ArkUI_GestureCollectInterceptInfo* OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_getgesturecollectinterceptinfo) | - | Obtains the <b>ArkUI_GestureCollectInterceptInfo</b> object from a specified <b>ArkUI_NodeEvent</b> object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_SetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy policy)](#oh_arkui_nativemodule_setchildmountpolicy) | - | Set the subnode mounting policy of the target node. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy* policy)](#oh_arkui_nativemodule_getchildmountpolicy) | - | Get the current child mount policy of the specified node. |
| [ArkUI_ErrorCode OH_ArkUI_NodeUtils_SetUiDvsyncSwitch(ArkUI_ContextHandle context, bool enable)](#oh_arkui_nodeutils_setuidvsyncswitch) | - | Sets the UI Dvsync switch.<br> When enabled, the system responds to Vsync requests more promptly and executes rendering tasks more frequently. It is typically enabled at the start of an animation in a self-rendering framework and disabled when the animation ends, to ensure smoother animation effects while preventing frequent Vsync requests from affecting other functionalities. Calling this function on a non-UI thread will cause the application to exit. |

### Variable

| Name | Description |
| -- | -- |
| void (*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event) | Defines the callback function of a node content event.<br>**Since**: 12 |

## Enum type description

### ArkUI_NodeType

```c
enum ArkUI_NodeType
```

**Description**

Enumerates ArkUI component types that can be created on the native side.

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
| ARKUI_NODE_XCOMPONENT_TEXTURE | XComponent of type TEXTURE. @since 18 |
| ARKUI_NODE_CHECKBOX_GROUP = 21 | Check box group. @since 15 |
| ARKUI_NODE_TEXT_EDITOR = 22 |  |
| ARKUI_NODE_ARC_ALPHABET_INDEXER = 23 |  |
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
| ARKUI_NODE_ARC_SWIPER = 1022 |  |

### ArkUI_NodeDirtyFlag

```c
enum ArkUI_NodeDirtyFlag
```

**Description**

Defines the dirty area flag passed in the <b>::markDirty</b> API.

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

Enumerates component adapter events.

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

Defines the node content event type.

**Since**: 12

| Enum item | Description |
| -- | -- |
| NODE_CONTENT_EVENT_ON_ATTACH_TO_WINDOW = 0 | Defines the attach event. |
| NODE_CONTENT_EVENT_ON_DETACH_FROM_WINDOW = 1 | Defines the detach event. |

### ArkUI_InspectorErrorCode

```c
enum ArkUI_InspectorErrorCode
```

**Description**

Enumerates the inspector error codes.

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL = 0 | Success. |
| ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER = -1 | Invalid parameter. |


## Function description

### OH_ArkUI_NodeEvent_GetEventType()

```c
ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)
```

**Description**

Obtains the type of a component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) | Returns the type of the component event. |

### OH_ArkUI_NodeEvent_GetTargetId()

```c
int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)
```

**Description**

Obtains the custom ID of a component event.<br> The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be applied to the dispatch logic of the same event entry function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the custom ID of the component event. |

### OH_ArkUI_NodeEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)
```

**Description**

Obtains the component object that triggers a component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeHandle | Returns the component object that triggers the component event. |

### OH_ArkUI_NodeEvent_GetInputEvent()

```c
ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains input event (for example, touch event) data for a component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_UIInputEvent* | Pointer to the input event data. |

### OH_ArkUI_NodeEvent_GetNodeComponentEvent()

```c
ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains the numerical data in a component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeComponentEvent*](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | Returns the pointer to the numerical data. |

### OH_ArkUI_NodeEvent_GetStringAsyncEvent()

```c
ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains the string data in a component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_StringAsyncEvent*](capi-arkui-nativemodule-arkui-stringasyncevent.md) | Returns the pointer to the string data. |

### OH_ArkUI_NodeEvent_GetTextChangeEvent()

```c
ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains the ArkUI_TextChangeEvent data from a component event.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Pointer to a component event. It cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextChangeEvent*](capi-arkui-nativemodule-arkui-textchangeevent.md) | Returns the pointer to the <b>ArkUI_TextChangeEvent</b> object. |

### OH_ArkUI_NodeEvent_GetUserData()

```c
void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)
```

**Description**

Obtains the custom data in a component event.<br> This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the event is triggered.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Returns the pointer to the custom data. |

### OH_ArkUI_NodeEvent_GetNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)
```

**Description**

Obtains the numeric-type parameter of a component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |
| int32_t index | Indicates the index of the return value. |
| ArkUI_NumberValue* value | Indicates the return value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE} if the parameter length exceeds<br>        the limit.<br>        Returns {@link ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID} if the data does not exist in the component event. |

### OH_ArkUI_NodeEvent_GetStringValue()

```c
int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)
```

**Description**

Obtains the string-type parameter of a component event. The string data is valid only during an event callback. To use it outside an event callback, you are advised to copy the string data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |
| int32_t index | Indicates the index of the return value. |
| char** string | Indicates the pointer to the string array. |
| int32_t* stringSize | Indicates the length of the string array. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE} if the parameter length exceeds<br>        the limit.<br>        Returns {@link ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID} if the data does not exist in the component event. |

### OH_ArkUI_NodeEvent_SetReturnNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)
```

**Description**

Sets the return value for a component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Indicates the pointer to the component event. |
| ArkUI_NumberValue* value | Indicates the numeric-type array. |
| int32_t size | Indicates the array length. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN} if the component event does not support return values.<br>        Returns {@link ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID} if data does not exist in the component event. |

### OH_ArkUI_NodeEvent_GetTouchTestInfo()

```c
ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)
```

**Description**

Obtains the touch test information in a component event.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| {pointer} | nodeEvent Indicates the pointer to an <b>ArkUI_NodeEvent</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_TouchTestInfo* | Pointer to the {@link ArkUI_TouchTestInfo} object. If the input parameter is invalid or is not touch test      information, null is returned. |

### OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent()

```c
OH_ArkUI_TextEditorChangeEvent* OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent(ArkUI_NodeEvent* event)
```

**Description**

Obtains the text content change data of the **TextEditor** component in the component event.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* event | Pointer to the {@link ArkUI_NodeEvent} component event object. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextEditorChangeEvent*](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) | Returns the pointer to an <b>OH_ArkUI_TextEditorChangeEvent</b> object.      Returns <b>null</b> if the input parameter is invalid or does not represent a text editor change event. |

### OH_ArkUI_NodeAdapter_Create()

```c
ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()
```

**Description**

Creates a component adapter.

**Since**: 12

### OH_ArkUI_NodeAdapter_Dispose()

```c
void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)
```

**Description**

Destroys a component adapter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

### OH_ArkUI_NodeAdapter_SetTotalNodeCount()

```c
int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)
```

**Description**

Sets the total number of elements in the specified adapter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t size | Indicates the number of elements. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_GetTotalNodeCount()

```c
uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)
```

**Description**

Obtains the total number of elements in the specified adapter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the total number of elements in the adapter. |

### OH_ArkUI_NodeAdapter_RegisterEventReceiver()

```c
int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(
ArkUI_NodeAdapterHandle handle, void* userData, void (*receiver)(ArkUI_NodeAdapterEvent* event))
```

**Description**

Registers an event callback for the adapter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| void\* userData | Indicates custom data. |
| void (\*receiver)(ArkUI_NodeAdapterEvent\* event) | Indicates the event receiver callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_UnregisterEventReceiver()

```c
void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)
```

**Description**

Deregisters an event callback for the adapter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

### OH_ArkUI_NodeAdapter_ReloadAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)
```

**Description**

Instructs the specified adapter to reload all elements.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_ReloadItem()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**Description**

Instructs the specified adapter to reload certain elements.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t startPosition | Indicates the start position of the elements to reload. |
| uint32_t itemCount | Indicates the number of the elements to reload. @return Returns the error code. Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_RemoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_RemoveItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**Description**

Instructs the specified adapter to remove certain elements.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t startPosition | Indicates the start position of the elements to remove. |
| uint32_t itemCount | Indicates the number of the elements to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_InsertItem()

```c
int32_t OH_ArkUI_NodeAdapter_InsertItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)
```

**Description**

Instructs the specified adapter to insert certain elements.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t startPosition | Indicates the start position of the elements to insert. |
| uint32_t itemCount | Indicates the number of the elements to insert. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_MoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)
```

**Description**

Instructs the specified adapter to move certain elements.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| uint32_t from | Indicates the start position of the elements to move. |
| uint32_t to |  Indicates the end position of the elements to move. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_GetAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)
```

**Description**

Obtains all elements stored in the specified adapter.<br> This API returns the pointer to the array of the elements. You need to manually release the memory data to which the pointer points.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Indicates the target component adapter. |
| ArkUI_NodeHandle** items | Indicates the pointer to the array of the elements in the adapter. |
| uint32_t* size | Indicates the number of elements. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeAdapterEvent_GetUserData()

```c
void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the custom data passed in during registration of the specified event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

### OH_ArkUI_NodeAdapterEvent_GetType()

```c
ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the event type.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeAdapterEventType](capi-native-node-h.md#arkui_nodeadaptereventtype) | Returns the event type. |

### OH_ArkUI_NodeAdapterEvent_GetRemovedNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the element to be removed for the event to be destroyed.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeHandle | Returns the element to be removed. |

### OH_ArkUI_NodeAdapterEvent_GetItemIndex()

```c
uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the index of the element to be operated for the specified adapter event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the index of the element. |

### OH_ArkUI_NodeAdapterEvent_GetHostNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)
```

**Description**

Obtains the scrollable container node that uses the specified adapter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeHandle | Returns the scrollable container node that uses the specified adapter. |

### OH_ArkUI_NodeAdapterEvent_SetItem()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)
```

**Description**

Sets the component to be added to the specified adapter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |
| ArkUI_NodeHandle node | Indicates the component to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeAdapterEvent_SetNodeId()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)
```

**Description**

Sets the component ID to be generated.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Indicates the target adapter event. |
| int32_t id | Indicates the component ID to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure()

```c
ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the size constraint for measurement through a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_LayoutConstraint* | Returns the pointer to the size constraint. |

### OH_ArkUI_NodeCustomEvent_GetPositionInLayout()

```c
ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the expected position of a component relative to its parent component in the layout phase through a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_IntOffset | Returns the expected position relative to the parent component. |

### OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw()

```c
ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the drawing context through a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_DrawContext* | Returns the drawing context. |

### OH_ArkUI_NodeCustomEvent_GetEventTargetId()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the ID of a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the ID of the custom component event. |

### OH_ArkUI_NodeCustomEvent_GetUserData()

```c
void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains custom event parameters through a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Returns the custom event parameters. |

### OH_ArkUI_NodeCustomEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains a component object through a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeHandle | Returns the component object. |

### OH_ArkUI_NodeCustomEvent_GetEventType()

```c
ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)
```

**Description**

Obtains the event type through a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeCustomEventType | Returns the type of the custom component event. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)
```

**Description**

Obtains the measurement information of a custom span through a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |
| ArkUI_CustomSpanMeasureInfo* info | Indicates the measurement information to be obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.         <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics()

```c
int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)
```

**Description**

Sets the measurement metrics of a custom span through a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |
| ArkUI_CustomSpanMetrics* metrics | Indicates the measurement metrics to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.         <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the drawing information of a custom span through a custom component event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Indicates the pointer to the custom component event. |
| ArkUI_CustomSpanDrawInfo* info | Indicates the drawing information to obtain. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.         Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.         <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### ArkUI_NodeContentCallback()

```c
typedef void (*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)
```

**Description**

Defines the callback function of a node content event.

**Since**: 12

### OH_ArkUI_NodeContent_RegisterCallback()

```c
int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)
```

**Description**

register a callback function to a node content.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeContentHandle content | Indicates the pointer to the node content instance. |
| [ArkUI_NodeContentCallback](capi-native-node-h.md#arkui_nodecontentcallback) callback | Indicates the callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeContentEvent_GetEventType()

```c
ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)
```

**Description**

Obtains the type of a node content event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Indicates the pointer to the node content event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_NodeContentEventType](capi-native-node-h.md#arkui_nodecontenteventtype) | Returns the type of the node content event. |

### OH_ArkUI_NodeContentEvent_GetNodeContentHandle()

```c
ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)
```

**Description**

Obtains the node content object that triggers a node content event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Indicates the pointer to the node content event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeContentHandle | Returns the node content object that triggers the node content event. |

### OH_ArkUI_NodeContent_SetUserData()

```c
int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)
```

**Description**

Saves custom data on the specified node content.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeContentHandle content | Indicates the node content on which the custom data will be saved. |
| void* userData | Indicates the custom data to be saved. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeContent_GetUserData()

```c
void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)
```

**Description**

Obtains the custom data saved on the specified node content.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeContentHandle content | Indicates the target node content. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Returns the custom data. |

### OH_ArkUI_NodeContent_AddNode()

```c
int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**Description**

Adds an ArkUI component node to the specified **NodeContent** object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeContentHandle content | **NodeContent** object to which a node is to be added. |
| ArkUI_NodeHandle node | Node to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_IS_ADOPTED} if a child node has been accepted. This specification is      supported since API version 22. |

### OH_ArkUI_NodeContent_RemoveNode()

```c
int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)
```

**Description**

Removes an ArkUI component node from the specified **NodeContent** object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeContentHandle content | **NodeContent** object from which a node is to be removed. |
| ArkUI_NodeHandle node | Node to be removed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeContent_InsertNode()

```c
int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)
```

**Description**

Inserts an ArkUI component node into a specific position of the specified **NodeContent** object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeContentHandle content | **NodeContent** object into which a node is to be inserted. |
| ArkUI_NodeHandle node | Node to be inserted. |
| int32_t position | Position where a node is to be inserted. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_IS_ADOPTED} if a child node has been accepted. This specification is      supported since API version 22. |

### OH_ArkUI_NodeUtils_GetLayoutSize()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)
```

**Description**

Get the size of the component layout area. The layout area size does not include graphic variation attributes such as scaling.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| ArkUI_IntSize* size | The drawing area size of the component handle, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPosition()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)
```

**Description**

Obtain the position of the component layout area relative to the parent component. The relative position of the layout area does not include graphic variation attributes, such as translation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| ArkUI_IntOffset* localOffset | The offset value of the component handle relative to the parent component, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**Description**

Obtain the position of the component layout area relative to the window. The relative position of the layout area does not include graphic variation attributes, such as translation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| ArkUI_IntOffset* globalOffset | The offset value of the component handle relative to the window, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)
```

**Description**

Obtain the position of the component layout area relative to the screen. The relative position of the layout area does not include graphic variation attributes, such as translation.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| ArkUI_IntOffset* screenOffset | The offset value of the component handle relative to the screen, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)
```

**Description**

Obtains the offset of a component relative to the global display. The relative position does not count in transformation attributes, such as translate.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the <b>ArkUI_NodeHandle</b> representing the component. |
| ArkUI_IntOffset* offset | Offset of the component relative to the global display, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.          {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**Description**

Obtain the position of the component in the window, including the properties of graphic translation changes.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| ArkUI_IntOffset* translateOffset | The cumulative offset value of the component handle itself, parent components, and ancestor nodes, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)
```

**Description**

Obtain the position of the component on the screen, including the attributes of graphic translation changes.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| ArkUI_IntOffset* translateOffset | The cumulative offset value of the component handle itself, parent components, and ancestor nodes, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_AddCustomProperty()

```c
void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)
```

**Description**

Sets a custom property for a component. This API takes effect only in the main thread.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | **ArkUI_NodeHandle** pointer. |
| const char* name | Pointer to the name of the custom property. A null pointer is not allowed. |
| const char* value | Pointer to the value of the custom property corresponding to the key parameter name. A null pointer is not allowed. |

### OH_ArkUI_NodeUtils_RemoveCustomProperty()

```c
void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)
```

**Description**

Removes a custom property that has been set for the specified component.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | **ArkUI_NodeHandle** pointer. |
| const char* name | Pointer to the name of the custom property. |

### OH_ArkUI_NodeUtils_GetCustomProperty()

```c
int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)
```

**Description**

Obtains the value of a custom property of the specified component.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | **ArkUI_NodeHandle** pointer. |
| const char* name | Pointer to the name of the custom property. |
| ArkUI_CustomProperty** handle | Double pointer to the struct that receives the custom property corresponding to the key parameter name. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetParentInPageTree()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)
```

**Description**

Obtains the parent node, which can be a component node created with ArkTS.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeHandle | Pointer to the component if the component exists; NULL otherwise. |

### OH_ArkUI_NodeUtils_GetActiveChildrenInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)
```

**Description**

Obtains all active child nodes of the specified node. Spans are not counted as child nodes. In **LazyForEach**<br>scenarios, you are advised to use the [OH_ArkUI_NodeUtils_GetChildWithExpandMode](capi-native-node-h.md#oh_arkui_nodeutils_getchildwithexpandmode) API for traversal.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle head | Node for which to obtain the child nodes. |
| ArkUI_ActiveChildrenInfo** handle | Double pointer to the struct containing information about the child nodes of the head node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetCurrentPageRootNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)
```

**Description**

Obtains the root node of the current page.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeHandle | Pointer to the root node if the node exists; NULL otherwise. |

### OH_ArkUI_NodeUtils_IsCreatedByNDK()

```c
bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)
```

**Description**

Checks whether the specified component is created with C APIs.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether the node is created with the C API. The value true means that the node is created with the C API,       and false means the opposite. |

### OH_ArkUI_NodeUtils_GetNodeType()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)
```

**Description**

Obtains the type of the specified node.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Type of the node. Returns -1 if the type is not supported yet. For details about the available types,      see [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype). |

### OH_ArkUI_NodeUtils_GetWindowInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)
```

**Description**

Obtains the information about the window to which a node belongs.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node object. |
| ArkUI_HostWindowInfo** info | Double pointer to the window information object. The memory allocated for this object must be released using {@link OH_ArkUI_HostWindowInfo_Destroy}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE} if the node is not mounted on the main component tree. |

### OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**Description**

Obtains the index of the first child node of the target node in the tree without expanding any nodes.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the target node. |
| uint32_t* index | Pointer to the index of the child node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)
```

**Description**

Obtains the index of the last child node of the target node in the tree without expanding any nodes.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the target node. |
| uint32_t* index | Pointer to the index of the child node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetChildWithExpandMode()

```c
int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position, ArkUI_NodeHandle* subnode, uint32_t expandMode)
```

**Description**

Obtains a child node at the specified index using different expansion modes.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the target node. |
| int32_t position | Index of the child node to obtain. |
| ArkUI_NodeHandle* subnode | Pointer to the obtained child node. |
| uint32_t expandMode | Expansion mode for node traversal. For details, see {@link ArkUI_ExpandMode}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_List_CloseAllSwipeActions()

```c
int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (*onFinish)(void* userData))
```

**Description**

Collapse the ListItem in its expanded state.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Node objects that need to be registered for events. |
| void\* userData | Custom event parameters are carried back in the callback parameter when the event is triggered. |
| void (\*onFinish)(void\* userData) | The callback triggered after the completion of the folding animation. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception.<br>        {@link ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED} The component does not support this event. |

### OH_ArkUI_GetContextByNode()

```c
ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)
```

**Description**

Obtain the UIContext pointer to the page where the node is located.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | The node. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ContextHandle | The UIContext pointer.         If a null pointer is returned, it may be because the node is empty. |

### OH_ArkUI_RegisterSystemColorModeChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node, void* userData, void (*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))
```

**Description**

The event called when the system color mode changes. Only one system color change callback can be registered for the same component.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode | Callback Events. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.         {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_UnregisterSystemColorModeChangeEvent()

```c
void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)
```

**Description**

Unregister the event callback when the system color mode changes.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the target node. |

### OH_ArkUI_RegisterSystemFontStyleChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node, void* userData, void (*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))
```

**Description**

The event called when the system font style changes. Only one system font change callback can be registered for the same component.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data to be saved. |
| void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent\* event | Callback Events. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.         {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_UnregisterSystemFontStyleChangeEvent()

```c
void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)
```

**Description**

Unregister the event callback when the system font style changes.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the target node. |

### OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)
```

**Description**

Retrieve the font size value for system font change events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_SystemFontStyleEvent* event | Indicates a pointer to the current system font change event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Updated system font size scaling factor. Default value: 1.0. |

### OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)
```

**Description**

Retrieve the font thickness values for system font change events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_SystemFontStyleEvent* event | Indicates a pointer to the current system font change event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | The updated system font thickness scaling factor. Default value: 1.0. |

### OH_ArkUI_NodeUtils_GetAttachedNodeHandleById()

```c
int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)
```

**Description**

Get the node handle by id.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* id | The id of the target node handle. |
| ArkUI_NodeHandle* node | The handle of target node handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_NodeUtils_MoveTo()

```c
int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)
```

**Description**

Moves a node to a target parent node as a child.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Node to be moved. |
| ArkUI_NodeHandle target_parent | Pointer to the target parent node. |
| int32_t index | Index of the node after the movement. If the index is invalid, the node will be added to the end of the target parent node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if C API initialization failed.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_IS_ADOPTED} if a child node has been accepted. This specification is      supported since API version 22. |

### OH_ArkUI_NativeModule_InvalidateAttributes()

```c
int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)
```

**Description**

Triggers the node attribute update in this frame. If the attributes of the current node are modified after the build phase, these changes do not take effect immediately but are deferred for batch processing in the next frame. This API forces immediate node updates within the current frame, ensuring that rendering effects are applied synchronously.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Node whose attributes are to be updated. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_SetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**Description**

Sets the cross-language option for the target node.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the target node. |
| ArkUI_CrossLanguageOption* option | Pointer to the cross-language configuration option ({@link ArkUI_CrossLanguageOption}). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)
```

**Description**

Obtains the cross-language option of the target node.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the target node. |
| ArkUI_CrossLanguageOption* option | Pointer to the cross-language configuration option ({@link ArkUI_CrossLanguageOption}). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_RegisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (*onLayoutCompleted)(void* userData))
```

**Description**

Registers a callback for node when layout is completed.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data used in onLayoutCompleted callback function. |
| void (\*onLayoutCompleted)(void\* userData) | Indicates the function when layout completed is callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | error code          {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter is incorrect. |

### OH_ArkUI_RegisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node, void* userData, void (*onDrawCompleted)(void* userData))
```

**Description**

Registers a callback for node when draw is completed.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Indicates the target node. |
| void\* userData | Indicates the custom data used in onDrawCompleted callback function. |
| void (\*onDrawCompleted)(void\* userData) | Indicates the function when draw completed is callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | error code          {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter is incorrect. |

### OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**Description**

Unregisters the layout completed callback for node.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the target node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | error code          {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter is incorrect. |

### OH_ArkUI_UnregisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)
```

**Description**

Unregisters the draw completed callback for node.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the target node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | error code          {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter is incorrect. |

### OH_ArkUI_GetNodeSnapshot()

```c
int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions, OH_PixelmapNative** pixelmap)
```

**Description**

Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered, the snapshot operation will fail. When the <b>Pixelmap</b> object created is no longer in use, it should be released by calling {@link OH_PixelmapNative_Release}.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node. |
| ArkUI_SnapshotOptions* snapshotOptions | Snapshot settings. If the value is null, the default settings are used. Snapshot settings include scaling, color space, and dynamic range configuration. Scaling: floating-point value greater than 0. Color space: <b>3</b> (DISPLAY_P3), <b>4</b> (SRGB), <b>27</b> (DISPLAY_BT2020_SRGB). Dynamic range: {@link ArkUI_DynamicRangeMode}. |
| OH_PixelmapNative** pixelmap | Pointer to the <b>Pixelmap</b> object created by the system. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.          {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>        Returns {@link ARKUI_ERROR_CODE_INTERNAL_ERROR} if the snapshot fails, returning a null pointer.<br>        Returns {@link ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT} if the snapshot operation times out.<br>        Returns {@link ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED} if the provided color space or<br>        dynamic range mode is not supported.<br>        Returns {@link ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED} if the isAuto parameter of the color          space or dynamic range mode is set to true for offscreen node snapshot. |

### OH_ArkUI_GetNodeSnapshotSizeLimitation()

```c
int32_t OH_ArkUI_GetNodeSnapshotSizeLimitation(int32_t* maxWidth, int32_t* maxHeight)
```

**Description**

Query the size limitation of the component snapshot.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t* maxWidth | Maximum width limit of the component snapshot, in px. |
| int32_t* maxHeight | Maximum height limit of the component snapshot, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Invalid function parameter. |

### OH_ArkUI_NodeUtils_GetPositionToParent()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)
```

**Description**

Obtains the offset of a specific node relative to its parent node.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node. |
| ArkUI_IntOffset* globalOffset | Offset of the target node relative to its parent node, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_AddSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates, void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)
```

**Description**

Adds the UI state style supported by the component. To handle states change efficiently, need to specify the states of interest and the corresponding handler. When a state of interest occurs, the handler will be executed. - You can adjust the UI style based on the current state within the callback. If this API is called multiple times on the same node, the last set of states and handler will take precedence. - Some component types have default system handling for certain states. For example, the <b>Button</b> component has a default style effect for the PRESSED state. When custom state handling is implemented on such components, the default style effect will be applied first, followed by the custom style changes, resulting in a combined effect. To disable the default style effects, set <b>excludeInner</b> to <b>true</b>, if this is allowed by the system implementation. - And when this API is called, the provided handler function will be executed immediately. - There is no need to explicitly register a listener for the NORMAL state. Once a non-NORMAL state is registered, the system will automatically notify your application when the state changes back to NORMAL.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Target node. |
| int32_t uiStates | Target UI states to be handled on the node. The combined result of all target UI states can be calculated using the <b>\|</b> operator. Example: <b>targetUIStates = ArkUI_UIState::PRESSED \| ArkUI_UIState::FOCUSED</b>. |
| void (statesChangeHandler)(int32_t currentStates | Handler for UI state changes. It rturns the current UI status. The value is the result of combining all current state enum values using the <b>\|</b> operator. You can determine the state using the <b>&</b> operator. Example: <b>if (currentStates & ArkUI_UIState::PRESSED == ArkUI_UIState::PRESSED)</b>. However, for checking the normal state, use the equality operator directly. Example: <b>if (currentStates == ArkUI_UIState::NORMAL)</b>. |
| bool excludeInner | Whether to disable the default state styles. |
| void\* userData) | Custom data used in the <b>statesChangeHandler</b> callback. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_RemoveSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)
```

**Description**

Removes registered UI states. When all states registered using **OH_ArkUI_AddSupportedUIStates** are removed, the registered **stateChangeHandler** will no longer be executed.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node. |
| int32_t uiStates | Target UI states to be removed. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_RunTaskInScope()

```c
int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(*callback)(void* userData))
```

**Description**

Executes the specified callback in the target UI context. For the implementation example, see {@link Ensuring Multi-Instance Functionality in the NDK}.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle uiContext | Pointer to the target UI context. |
| void\* userData | Pointer to the user-defined data for processing custom data within the callback function. You are responsible for ensuring the validity of the data when the custom function is executed. |
| void(\*callback)(void\* userData) | The custom function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if C API initialization failed.<br>    <br>Returns {@link ARKUI_ERROR_CODE_UI_CONTEXT_INVALID} if the UIContext object is invalid.<br>    <br>Returns {@link ARKUI_ERROR_CODE_CALLBACK_INVALID} if the callback function is invalid. |

### OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)
```

**Description**

Obtain a node by its unique ID.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const uint32_t uniqueId | Unique ID of the target node. |
| ArkUI_NodeHandle* node | Pointer to the target node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if C API initialization failed. |

### OH_ArkUI_NodeUtils_GetNodeUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)
```

**Description**

Obtains the unique ID of the target node.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI node pointer. |
| int32_t* uniqueId | Pointer to the unique ID of the target node. The component ID is read-only and unique in the process. If the node exists, the unique ID of the node is returned. Otherwise, **-1** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if C API initialization failed. |

### OH_ArkUI_NativeModule_IsInRenderState()

```c
int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)
```

**Description**

Obtains whether a node is in the render state. If {@link RenderNode} of a node is in the render tree, the node is in the render state.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI node pointer. |
| bool* isInRenderState | Pointer to the **isInRenderState** parameter indicating whether the node is in render state. *<br>*true**: The node is in the render state. **false**: The node is not in the render state. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if C API initialization failed. |

### OH_ArkUI_NativeModule_AdoptChild()

```c
int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**Description**

Adopts the target node as an affiliated node. The adopted node must not have an existing parent. This API is not used to add a node as a child node. Instead, it only allows the node to receive lifecycle callbacks of the corresponding child node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | **ArkUI_NodeHandle** pointer, which specifies the parent node of the node to be adopted. |
| ArkUI_NodeHandle child | **ArkUI_NodeHandle** pointer, which specifies the child node to be adopted. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if C API initialization failed.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_HAS_PARENT} if the adopted node already has a parent node.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED} if the node cannot be adopted as an affiliated node.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO} if the node cannot adopt other affiliated nodes. |

### OH_ArkUI_NativeModule_RemoveAdoptedChild()

```c
int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)
```

**Description**

Removes a previously-adopted affiliated node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | **ArkUI_NodeHandle** pointer, which specifies the parent node. |
| ArkUI_NodeHandle child | **ArkUI_NodeHandle** pointer, which specifies the child node to be removed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if C API initialization failed.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN} if the node is not an affiliated node      adopted by the target node. |

### OH_ArkUI_SetForceDarkConfig()

```c
int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (*colorInvertFunc)(uint32_t color))
```

**Description**

Sets the inverse color algorithm for components and instances.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle uiContext | Indicates the context in which the inverse color feature should take effect. If the value is null, the feature applies to the entire application process. |
| bool forceDark | Indicates whether the inverse color feature is enabled. |
| [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype) nodeType | Indicates the component type for which to enable the inverse color feature. If the value is ARKUI_NODE_UNDEFINED, enabling the feature for all components. |
| uint32_t (\*colorInvertFunc)(uint32_t color) | Indicates the user-defined inverse color algorithm. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if CAPI init error.<br>        Returns {@link ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID} if force dark config is invalid. |

### OH_ArkUI_NativeModule_RegisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**Description**

Registers a basic event callback for the target node.<br> Currently, the following event types are supported: **NODE_ON_CLICK_EVENT**, **NODE_TOUCH_EVENT**, **NODE_EVENT_ON_APPEAR**, **NODE_EVENT_ON_DISAPPEAR**, **NODE_ON_KEY_EVENT**, **NODE_ON_FOCUS**, **NODE_ON_BLUR**, **NODE_ON_HOVER**, **NODE_ON_MOUSE**, and **NODE_ON_SIZE_CHANGE**. For details, see @{link ArkUI_NodeEventType}.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Target node. |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | Event type. |
| void\* userData | User-defined data pointer for processing custom data within the callback function. You are responsible for ensuring the validity of the data when the custom function is executed. |
| void (\*callback)(ArkUI_NodeEvent\* event) | User-defined callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE} if the event type is not supported. |

### OH_ArkUI_NativeModule_UnregisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)
```

**Description**

Unregisters the basic event callback for the target node.<br> For details about the supported event types, see [OH_ArkUI_NativeModule_RegisterCommonEvent](capi-native-node-h.md#oh_arkui_nativemodule_registercommonevent).

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node. |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | Event type. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE} if the event type is not supported. |

### OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**Description**

Registers a basic event callback for visible area changes with a constrained callback interval.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Target node. |
| float\* ratios | Array of threshold ratios, representing the visible area of the component. |
| int32_t size | Size of the array of threshold ratios. |
| float expectedUpdateInterval | Expected calculation interval. |
| void\* userData | User-defined data pointer for processing custom data within the callback function. You are responsible for ensuring the validity of the data when the custom function is executed. |
| void (\*callback)(ArkUI_NodeEvent\* event) | User-defined callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)
```

**Description**

Unregisters the basic event callback for visible area changes with a constrained callback interval.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NativeModule_ConvertPositionToWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)
```

**Description**

Converts the coordinates of a point from the coordinate system of a specified node to that of the current window. For a coordinate system of a node, transformation of the node is considered. For example, if node A is translated leftward by 100, the coordinates of the points in its coordinate system will also be translated leftward by 100.<br> [](docroot://reference/apis-arkui/figures/ConvertToWindow.png)<br> As shown in the preceding figure, the coordinates (x0, y0) in the coordinate system of the specified node are converted to the coordinates (x1, y1) in the coordinate system of the window.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle currentNode | Specified node. |
| ArkUI_IntOffset localPosition | Coordinates of the point in the coordinate system of the specified node, in px. |
| ArkUI_IntOffset* windowPosition | Pointer to the converted coordinates (in the current window coordinate system, in px). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE} if the node is not mounted on the main component tree. |

### OH_ArkUI_NativeModule_ConvertPositionFromWindow()

```c
int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)
```

**Description**

Converts the coordinates of a point from the current window's coordinate system to the target node's coordinate system. For a coordinate system of a node, transformation of the node is considered. For example, if node A is translated leftward by 100, the coordinates of the points in its coordinate system will also be translated leftward by 100.<br> [](docroot://reference/apis-arkui/figures/ConvertFromWindow.png)<br> As shown in the preceding figure, the coordinates (x1, y1) in the window coordinate system are converted to the coordinates (x0, y0) in the coordinate system of the target node.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle targetNode | The target node. |
| ArkUI_IntOffset windowPosition | Coordinates of the point in the current window coordinate system, in px. |
| ArkUI_IntOffset* localPosition | Pointer to the converted coordinates (in the coordinate system of the target node, in px). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE} if the node is not mounted on the main component tree. |

### OH_ArkUI_Swiper_FinishAnimation()

```c
int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)
```

**Description**

Stop the animation being executed by the Swiper node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_PostAsyncUITask()

```c
int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (*asyncUITask)(void* asyncUITaskData), void (*onFinish)(void* asyncUITaskData))
```

**Description**

Submits the **asyncUITask** function to a non-UI thread provided by the ArkUI framework for execution. After **asyncUITask** finishes execution, the **onFinish** function is called in the UI thread.<br> This is suitable for scenarios involving multi-threaded UI component creation. You can use this API to create UI components in non-UI threads and then mount the created components to the main tree in the UI thread.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle context | Pointer to the UI instance object. |
| void\* asyncUITaskData | Pointer to the user-defined data, which is passed as the input parameter of **asyncUITask**<br>and **onFinish**. A null pointer is allowed. |
| void (\*asyncUITask)(void\* asyncUITaskData) | Function executed in the non-UI thread. |
| void (\*onFinish)(void\* asyncUITaskData) | Function executed on the UI thread after **asyncUITask** is completed. A null pointer is allowed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the context object is invalid, or asyncUITask is a      null pointer. |

### OH_ArkUI_PostUITask()

```c
int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**Description**

Submits the **task** function to the UI thread for execution.<br> This is suitable for scenarios involving multi-threaded UI component creation. When you create UI components in a self-built thread, you can use this API to mount the created components to the main tree on the UI thread.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle context | Pointer to the UI instance object. |
| void\* taskData | Pointer to the user-defined data, which is passed as the input parameter of **task**. A null pointer is allowed. |
| void (\*task)(void\* taskData) | Function executed in the UI thread. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the context object is invalid, or task is a null      pointer. |

### OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible()

```c
int32_t OH_ArkUI_NativeModule_AtomicServiceMenuBarSetVisible(ArkUI_ContextHandle uiContext, bool visible)
```

**Description**

set the visiblity of the menubar.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle uiContext | ArkUI_ContextHandle. - The designated ArkUI container context. |
| bool visible | visibility. true indicate the menubar is visible,          false indicate the menubar is invisible. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_UI_CONTEXT_INVALID} if the uiContext is invalid.           for example, 1.uiContext is nullptr 2.can not get container by uiContext.           3. the uiContext is not belong to atomic service. |

### OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))
```

**Description**

Registers a callback for listening for component dimension and area changes.<br> This function can be called for a valid {@link ArkUI_NodeHandle} node at any time. The newly registered callback will replace the previously registered callback for this event and will take effect from the next frame. When the callback is no longer needed, call [OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent](capi-native-node-h.md#oh_arkui_nativemodule_unregistercommonareaapproximatechangeevent) to unregister it. Otherwise, the callback will be automatically unregistered when the node is released.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Pointer to {@link ArkUI_NodeHandle}. |
| float expectedUpdateInterval | Expected calculation interval, in milliseconds. |
| void\* userData | Pointer to custom data. |
| void (\*callback)(ArkUI_NodeEvent\* event) | Event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. \n          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful. \n<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. \n |

### OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonAreaApproximateChangeEvent(ArkUI_NodeHandle node)
```

**Description**

Unregisters the callback bound to the dimensions and area changes of a component.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to {@link ArkUI_NodeHandle}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. \n          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful. \n<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. \n |

### OH_ArkUI_PostUITaskAndWait()

```c
int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))
```

**Description**

Post UI task to UI thread and wait until UI task finished.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ContextHandle context | UIContext pointer of the page where the UI task located. |
| void\* taskData | Parameter of task. |
| void (\*task)(void\* taskData) | Function executed by UI thread. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if context or task is nullptr. |

### OH_ArkUI_Swiper_StartFakeDrag()

```c
int32_t OH_ArkUI_Swiper_StartFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)
```

**Description**

Start a fake drag of the Swiper node. Call OH_ArkUI_Swiper_FakeDragBy to simulate the drag motion. Call OH_ArkUI_Swiper_StopFakeDrag to complete the fake drag. A fake drag can be interrupted by a real drag. If you need to ignore touch events and other user input during a fake drag, use NODE_SWIPER_DISABLE_SWIPE.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| bool* isSuccessful | If the fake drag started successfully, return true. If the Swiper is not ready to start the fake drag, or a real or fake drag is already in progress, return false. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_Swiper_FakeDragBy()

```c
int32_t OH_ArkUI_Swiper_FakeDragBy(ArkUI_NodeHandle node, float offset, bool* isConsumedOffset)
```

**Description**

Fake drag by an offset of the Swiper node. The OH_ArkUI_Swiper_StartFakeDrag must be called first.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| float offset | The offset that needs to be scrolled. The unit is vp. |
| bool* isConsumedOffset | If not in a fake drag progress, or no offset is consumed, return false. If any offset is consumed, return true. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_Swiper_StopFakeDrag()

```c
int32_t OH_ArkUI_Swiper_StopFakeDrag(ArkUI_NodeHandle node, bool* isSuccessful)
```

**Description**

Stop a fake drag of the Swiper node.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| bool* isSuccessful | If the fake drag stopped successfully, return true. If the Swiper is not ready to stop the fake drag, or no fake drag is in progress, return false. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_Swiper_IsFakeDragging()

```c
int32_t OH_ArkUI_Swiper_IsFakeDragging(ArkUI_NodeHandle node, bool* isFakeDragging)
```

**Description**

Get the fake drag state of the Swiper node.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |
| bool* isFakeDragging | If a fake drag is in progress return true, otherwise return false |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_Swiper_ShowPrevious()

```c
int32_t OH_ArkUI_Swiper_ShowPrevious(ArkUI_NodeHandle node)
```

**Description**

Show the previous page of the Swiper node.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_Swiper_ShowNext()

```c
int32_t OH_ArkUI_Swiper_ShowNext(ArkUI_NodeHandle node)
```

**Description**

Show the next page of the Swiper node.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_ArcSwiper_ShowPrevious()

```c
int32_t OH_ArkUI_ArcSwiper_ShowPrevious(ArkUI_NodeHandle node)
```

**Description**

Show the previous page of the ArcSwiper node.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_ArcSwiper_ShowNext()

```c
int32_t OH_ArkUI_ArcSwiper_ShowNext(ArkUI_NodeHandle node)
```

**Description**

Show the next page of the ArcSwiper node.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_ArcSwiper_FinishAnimation()

```c
int32_t OH_ArkUI_ArcSwiper_FinishAnimation(ArkUI_NodeHandle node)
```

**Description**

Stop the animation executed by the ArcSwiper node.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | ArkUI_NodeHandle pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception. |

### OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext()

```c
int32_t OH_ArkUI_NativeModule_GetPageRootNodeHandleByContext(ArkUI_ContextHandle context, ArkUI_NodeHandle* rootNode)
```

**Description**

Obtains the root node of the page of a specified instance.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | Pointer to the UI instance object. |
| ArkUI_NodeHandle* rootNode | Handle to the target root node. If the page corresponding to the context does not have a root node, this parameter is set to null. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if C API initialization failed.<br>    <br>Returns {@link ARKUI_ERROR_CODE_UI_CONTEXT_INVALID} if an instance error occurs.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo()

```c
ArkUI_GestureCollectInterceptInfo* OH_ArkUI_NodeEvent_GetGestureCollectInterceptInfo(ArkUI_NodeEvent* nodeEvent)
```

**Description**

Obtains the <b>ArkUI_GestureCollectInterceptInfo</b> object from a specified <b>ArkUI_NodeEvent</b> object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeEvent* nodeEvent | Pointer to the <b>ArkUI_NodeEvent</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_GestureCollectInterceptInfo* | Returns the pointer to the <b>ArkUI_GestureCollectInterceptInfo</b> object.          It is valid only during callback and does not need to be released.          Returns <b>null</b> if the input parameter is invalid or the          information is not gesture collection interception information. |

### OH_ArkUI_NativeModule_SetChildMountPolicy()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_SetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy policy)
```

**Description**

Set the subnode mounting policy of the target node.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | the target node handle. |
| OH_ArkUI_NodeMountPolicy policy | the policy to set. Valid values correspond to {@link OH_ArkUI_NodeMountPolicy}. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Error code.      <ul><li>{@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>    </li><li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception.<br>    </li><li>{@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if CAPI init error.</li></ul> |

### OH_ArkUI_NativeModule_GetChildMountPolicy()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetChildMountPolicy(ArkUI_NodeHandle node, OH_ArkUI_NodeMountPolicy* policy)
```

**Description**

Get the current child mount policy of the specified node.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | the target node handle. |
| OH_ArkUI_NodeMountPolicy* policy | the pointer to receive child mounting policy of the target node. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Error code.      <ul><li>{@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>    </li><li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} Function parameter exception.<br>    </li><li>{@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if CAPI init error.</li></ul> |

### OH_ArkUI_NodeUtils_SetUiDvsyncSwitch()

```c
ArkUI_ErrorCode OH_ArkUI_NodeUtils_SetUiDvsyncSwitch(ArkUI_ContextHandle context, bool enable)
```

**Description**

Sets the UI Dvsync switch.<br> When enabled, the system responds to Vsync requests more promptly and executes rendering tasks more frequently. It is typically enabled at the start of an animation in a self-rendering framework and disabled when the animation ends, to ensure smoother animation effects while preventing frequent Vsync requests from affecting other functionalities. Calling this function on a non-UI thread will cause the application to exit.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | [in] Pointer to an ArkUI_ContextHandle. |
| bool enable | [in] Whether to enable Dvsync. The value true enables Dvsync, and false disables Dvsync. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Returns the result.      <ul><li>{@link ARKUI_ERROR_CODE_NO_ERROR} The operation is successful.<br>    </li><li>{@link RKUI_ERROR_CODE_CAPI_INIT_ERROR} Failed to initialize the CAPI.<br>    </li><li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} The function parameter is invalid.</li></ul> |


