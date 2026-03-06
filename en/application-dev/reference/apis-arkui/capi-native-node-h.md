# native_node.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Designer: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Provides type definitions for **NativeNode** APIs.

**File to include**: <arkui/native_node.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[native_node_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/native_node_sample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description                                                                          |
| -- | -- |------------------------------------------------------------------------------|
| [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) | ArkUI_AttributeItem | Defines the general input parameter structure of the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) function.|
| [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | ArkUI_NodeComponentEvent | Defines a struct for the component callback event.                                                              |
| [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) | ArkUI_StringAsyncEvent | Defines a struct for the component callback event that uses string parameters.                                                         |
| [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) | ArkUI_TextChangeEvent | Defines a hybrid data structure for component events.                                                              |
| [ArkUI_NativeNodeAPI_1](capi-arkui-nativemodule-arkui-nativenodeapi-1.md) | ArkUI_NativeNodeAPI_1 | Defines a struct for node APIs of ArkUI on the native side. APIs related to the Node module must be called on the main thread.                              |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) | ArkUI_NodeEvent | Defines a struct for the component event.                                                              |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md) | ArkUI_NodeCustomEvent | Defines a struct for the custom component event.                                                           |
| [ArkUI_NodeAdapter*](capi-arkui-nativemodule-arkui-nodeadapter8h.md) | ArkUI_NodeAdapterHandle | Defines a struct for the component adapter, which is used for lazy loading of elements of scrollable components.                                                    |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md) | ArkUI_NodeAdapterEvent | Defines a struct for the component adapter event.                                                                  |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md) | ArkUI_NodeContentEvent | Defines a struct for the NodeContent event.                                                     |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_NodeType](#arkui_nodetype) | ArkUI_NodeType | Enumerates ArkUI component types that can be created on the native side.|
| [ArkUI_NodeAttributeType](#arkui_nodeattributetype) | ArkUI_NodeAttributeType | Defines the ArkUI style attributes that can be set on the native side.|
| [ArkUI_NodeEventType](#arkui_nodeeventtype) | ArkUI_NodeEventType | Enumerates the event types supported by the **NativeNode** component.|
| [ArkUI_NodeDirtyFlag](#arkui_nodedirtyflag) | ArkUI_NodeDirtyFlag | Enumerates the flags passed to indicate the need to re-execute measurement, layout, or rendering when a custom component calls the **::markDirty** API.|
| [ArkUI_NodeCustomEventType](#arkui_nodecustomeventtype) | ArkUI_NodeCustomEventType | Enumerates the custom component event types.|
| [ArkUI_NodeAdapterEventType](#arkui_nodeadaptereventtype) | ArkUI_NodeAdapterEventType | Enumerates node adapter events.|
| [ArkUI_NodeContentEventType](#arkui_nodecontenteventtype) | ArkUI_NodeContentEventType | Enumerates the event types for **NodeContent**.|
| [ArkUI_InspectorErrorCode](#arkui_inspectorerrorcode) | ArkUI_InspectorErrorCode | Enumerates the inspector error codes.|

### Functions

<!--Table: 40%; 20%; 40%-->
| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_geteventtype) | - | Obtains the type of a component event.|
| [int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettargetid) | - | Obtains the custom ID of a component event. The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be applied to the dispatch logic of the same event entry point function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver).|
| [ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodehandle) | - | Obtains the component object that triggers an event.|
| [ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getinputevent) | - | Obtains input event (for example, touch event) data for a component event.|
| [ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getnodecomponentevent) | - | Obtains the numerical data in a component event.|
| [ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getstringasyncevent) | - | Obtains the string data in a component event.|
| [ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_gettextchangeevent) | - | Obtains the **ArkUI_TextChangeEvent** data from the specified component event.|
| [void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)](#oh_arkui_nodeevent_getuserdata) | - | Obtains the custom data in a component event. This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the event is triggered.|
| [int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)](#oh_arkui_nodeevent_getnumbervalue) | - | Obtains the numeric-type parameter of a component event.|
| [int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)](#oh_arkui_nodeevent_getstringvalue) | - | Obtains the string-type parameter of a component event. The string data is valid only during an event callback. To use it outside an event callback, you are advised to copy the string data.|
| [int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)](#oh_arkui_nodeevent_setreturnnumbervalue) | - | Sets the return value for a component event.|
| [ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()](#oh_arkui_nodeadapter_create) | - | Creates a component adapter.|
| [void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_dispose) | - | Disposes of a component adapter.|
| [int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)](#oh_arkui_nodeadapter_settotalnodecount) | - | Sets the total number of elements in the specified adapter.|
| [uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_gettotalnodecount) | - | Obtains the total number of elements in the specified adapter.|
| [int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(ArkUI_NodeAdapterHandle handle, void* userData, void (\*receiver)(ArkUI_NodeAdapterEvent* event))](#oh_arkui_nodeadapter_registereventreceiver) | - | Registers an event callback for the specified adapter.|
| [void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_unregistereventreceiver) | - | Unregisters an event callback for the specified adapter.|
| [int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)](#oh_arkui_nodeadapter_reloadallitems) | - | Instructs the specified adapter to reload all elements.|
| [int32_t OH_ArkUI_NodeAdapter_ReloadItem(ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_reloaditem) | - | Instructs the specified adapter to reload certain elements.|
| [int32_t OH_ArkUI_NodeAdapter_RemoveItem(ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_removeitem) | - | Instructs the specified adapter to remove certain elements.|
| [int32_t OH_ArkUI_NodeAdapter_InsertItem(ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)](#oh_arkui_nodeadapter_insertitem) | - | Instructs the specified adapter to insert certain elements.|
| [int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)](#oh_arkui_nodeadapter_moveitem) | - | Instructs the specified adapter to move certain elements.|
| [int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)](#oh_arkui_nodeadapter_getallitems) | - | Obtains all elements stored in the specified adapter. When the API is called, the array object pointer of the element is returned. You must release the memory data to which the pointer points.|
| [void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getuserdata) | - | Obtains the custom data passed in during registration of the specified event.|
| [ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gettype) | - | Obtains the event type.|
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getremovednode) | - | Obtains the element to be removed for the event to be destroyed.|
| [uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_getitemindex) | - | Obtains the index of the element to be operated for the specified adapter event.|
| [ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)](#oh_arkui_nodeadapterevent_gethostnode) | - | Obtains the scrollable container node that uses the specified adapter.|
| [int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)](#oh_arkui_nodeadapterevent_setitem) | - | Sets the component to be added to the specified adapter.|
| [int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)](#oh_arkui_nodeadapterevent_setnodeid) | - | Sets the component ID to be generated.|
| [ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getlayoutconstraintinmeasure) | - | Obtains the size constraint for measurement through a custom component event.|
| [ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getpositioninlayout) | - | Obtains the expected position of a component relative to its parent component in the layout phase through a custom component event.|
| [ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getdrawcontextindraw) | - | Obtains the drawing context through a custom component event.|
| [int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_geteventtargetid) | - | Obtains the ID of a custom component event.|
| [void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getuserdata) | - | Obtains custom event parameters through a custom component event.|
| [ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_getnodehandle) | - | Obtains a component object through a custom component event.|
| [ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)](#oh_arkui_nodecustomevent_geteventtype) | - | Obtains the event type through a custom component event.|
| [int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_nodecustomevent_getcustomspanmeasureinfo) | - | Obtains the measurement information of a custom span through a custom component event.|
| [int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)](#oh_arkui_nodecustomevent_setcustomspanmetrics) | - | Sets the measurement metrics of a custom span through a custom component event.|
| [int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_nodecustomevent_getcustomspandrawinfo) | - | Obtains the drawing information of a custom span through a custom component event.|
| [typedef void (\*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)](#arkui_nodecontentcallback) | ArkUI_NodeContentCallback | Defines a callback for the NodeContent event.|
| [int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)](#oh_arkui_nodecontent_registercallback) | - | Registers an event callback for the **NodeContent**.|
| [ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_geteventtype) | - | Obtains the type of the specified **NodeContent** event.|
| [ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)](#oh_arkui_nodecontentevent_getnodecontenthandle) | - | Obtains the object that triggers the specified **NodeContent** event.|
| [int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)](#oh_arkui_nodecontent_setuserdata) | - | Saves custom data to the specified **NodeContent** object.|
| [void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)](#oh_arkui_nodecontent_getuserdata) | - | Obtains the custom data saved on the specified **NodeContent** object.|
| [int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_addnode) | - | Adds an ArkUI component node to the specified **NodeContent** object.|
| [int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)](#oh_arkui_nodecontent_removenode) | - | Removes an ArkUI component node from the specified **NodeContent** object.|
| [int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)](#oh_arkui_nodecontent_insertnode) | - | Inserts an ArkUI component node into a specific position of the specified **NodeContent** object.|
| [int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)](#oh_arkui_nodeutils_getlayoutsize) | - | Obtains the layout area size of the component. The size does not count in transformation attributes, such as scale.|
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)](#oh_arkui_nodeutils_getlayoutposition) | - | Obtains the position of the component's layout area relative to its parent component. The relative position does not count in transformation attributes, such as translate.|
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getlayoutpositioninwindow) | - | Obtains the position of the component's layout area relative to the window. The relative position does not count in transformation attributes, such as translate.|
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)](#oh_arkui_nodeutils_getlayoutpositioninscreen) | - | Obtains the position of the component's layout area relative to the screen. The relative position does not count in transformation attributes, such as translate.|
| [int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)](#oh_arkui_nodeutils_getlayoutpositioninglobaldisplay) | - | Obtains the offset of the specified component relative to the global display. The relative position does not count in transformation attributes, such as translate.|
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinwindow) | - | Obtains the position of the component in the window, including the translate attribute.|
| [int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)](#oh_arkui_nodeutils_getpositionwithtranslateinscreen) | - | Obtains the position of the component on the screen, including the translate attribute.|
| [void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)](#oh_arkui_nodeutils_addcustomproperty) | - | Sets a custom property for a component. This API takes effect only in the main thread.|
| [void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)](#oh_arkui_nodeutils_removecustomproperty) | - | Removes a custom property that has been set for the specified component.|
| [int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)](#oh_arkui_nodeutils_getcustomproperty) | - | Obtains the value of a custom property of the specified component.|
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getparentinpagetree) | - | Obtains the parent node, which can be a component node created with ArkTS.|
| [int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)](#oh_arkui_nodeutils_getactivechildreninfo) | - | Obtains all active child nodes of the specified node. Spans are not counted as child nodes.|
| [ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getcurrentpagerootnode) | - | Obtains the root node of the current page.|
| [bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_iscreatedbyndk) | - | Checks whether the specified component is created with C APIs.|
| [int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)](#oh_arkui_nodeutils_getnodetype) | - | Obtains the type of the specified node.|
| [int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)](#oh_arkui_nodeutils_getwindowinfo) | - | Obtains the information about the window to which a node belongs.|
| [int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)](#oh_arkui_nodeutils_moveto) | - | Moves a node to a target parent node as a child.|
| [int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_invalidateattributes) | - | Triggers the node attribute update in this frame.|
| [int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (\*onFinish)(void* userData))](#oh_arkui_list_closeallswipeactions) | - | Collapses the list items in the expanded state.|
| [ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)](#oh_arkui_getcontextbynode) | - | Obtains the pointer to the UI context object of the specified node.|
| [int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node,void* userData, void (\*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))](#oh_arkui_registersystemcolormodechangeevent) | - | Registers an event listener for system color mode changes. A single component can only register one callback for system color mode changes. For implementation examples, see [Listening for Component Events](../../ui/ndk-listen-to-component-events.md).|
| [void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemcolormodechangeevent) | - | Unregisters the event listener for system color mode changes.|
| [int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node,void* userData, void (\*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))](#oh_arkui_registersystemfontstylechangeevent) | - | Registers an event listener for system font style changes. A single component can only register one callback for system font style changes.|
| [void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_unregistersystemfontstylechangeevent) | - | Unregisters the event listener for system font style changes.|
| [float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontsizescale) | - | Obtains the font size from the system font style change event.|
| [float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)](#oh_arkui_systemfontstyleevent_getfontweightscale) | - | Obtains the font weight from the system font style change event.|
| [int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node,void* userData, void (\*onLayoutCompleted)(void* userData))](#oh_arkui_registerlayoutcallbackonnodehandle) | - | Registers a layout completion callback function for a specific node.|
| [int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node,void* userData, void (\*onDrawCompleted)(void* userData))](#oh_arkui_registerdrawcallbackonnodehandle) | - | Registers a drawing completion callback function for a specific node.|
| [int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterlayoutcallbackonnodehandle) | - | Unregisters the layout completion callback function for a specific node.|
| [int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)](#oh_arkui_unregisterdrawcallbackonnodehandle) | - | Unregisters the drawing completion callback function for a specific node.|
| [int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions,OH_PixelmapNative** pixelmap)](#oh_arkui_getnodesnapshot) | - | Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered, the snapshot operation will fail. When the **Pixelmap** object created is no longer in use, it should be released by calling **OH_PixelmapNative_Release**.|
| [int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getattachednodehandlebyid) | - | Obtains the target node based on the provided user ID.|
| [int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)](#oh_arkui_nodeutils_getnodehandlebyuniqueid) | - | Obtain a node by its unique ID.|
| [int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)](#oh_arkui_nodeutils_getnodeuniqueid) | - | Obtains the unique ID of the target node.|
| [int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_adoptchild) | - | Adopts the target node as an affiliated node. The adopted node must not have an existing parent. This API is not used to add a node as a child node. Instead, it only allows the node to receive lifecycle callbacks of the corresponding child node.|
| [int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)](#oh_arkui_nativemodule_removeadoptedchild) | - | Removes a previously adopted node.|
| [int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)](#oh_arkui_nativemodule_isinrenderstate) | - | Checks whether this node is in render state. A node is considered to be in render state when its corresponding **RenderNode** is present in the render tree.|
| [int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_setcrosslanguageoption) | - | Sets the cross-language options for the target node.|
| [int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)](#oh_arkui_nodeutils_getcrosslanguageoption) | - | Obtains the cross-language options for the target node.|
| [int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getfirstchildindexwithoutexpand) | - | Obtains the index of the first child node of the target node in the tree without expanding any nodes.|
| [int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)](#oh_arkui_nodeutils_getlastchildindexwithoutexpand) | - | Obtains the index of the last child node of the target node in the tree without expanding any nodes.|
| [int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position,ArkUI_NodeHandle* subnode, uint32_t expandMode)](#oh_arkui_nodeutils_getchildwithexpandmode) | - | Obtains a child node at the specified index using different expansion modes.|
| [int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)](#oh_arkui_nodeutils_getpositiontoparent) | - | Obtains the offset of the target node relative to its parent node, in px.|
| [ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates,void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)](#oh_arkui_addsupporteduistates) | - | Adds the polymorphic style states supported by the component. To handle states efficiently, specify the states of interest and their corresponding handlers. When a state of interest occurs, the handler will be executed. You can adjust the UI style based on the current state within the callback. If this API is called multiple times on the same node, the last set of states and handlers will take precedence. Some component types have default system handling for certain states. For example, the **Button** component has a default style effect for the PRESSED state. When custom state handling is implemented on such components, the default style effect will be applied first, followed by the custom style changes, resulting in a combined effect. To disable the default style effects, set **excludeInner** to **true**, if this is allowed by the system implementation. When this API is called, the provided handler function will be executed immediately. There is no need to explicitly register a listener for the NORMAL state. Once a non-NORMAL state is registered, the system will automatically notify your application when the state changes back to NORMAL.|
| [ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)](#oh_arkui_removesupporteduistates) | - | Removes registered UI states. When all states registered using **OH_ArkUI_AddSupportedUIStates** are removed, the registered **stateChangeHandler** will no longer be executed.|
| [int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(\*callback)(void* userData))](#oh_arkui_runtaskinscope) | - | Executes the specified callback in the target UI context. For the implementation example, see [Ensuring Multi-Instance Functionality in the NDK](../../ui/ndk-scope-task.md).|
| [int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData, void (\*asyncUITask)(void\* asyncUITaskData), void (\*onFinish)(void\* asyncUITaskData))](#oh_arkui_postasyncuitask) | - | Submits the **asyncUITask** function to a non-UI thread provided by the ArkUI framework for execution. After **asyncUITask** finishes execution, the **onFinish** function is called in the UI thread. This is suitable for scenarios involving multi-threaded UI component creation. You can use this API to create UI components in non-UI threads and then mount the created components to the main tree in the UI thread.|
| [int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (\*task)(void\* taskData))](#oh_arkui_postuitask) | - | Submits the **task** function to the UI thread for execution. This is suitable for scenarios involving multi-threaded UI component creation. When you create UI components in a self-built thread, you can use this API to mount the created components to the main tree on the UI thread.|
| [int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (\*task)(void\* taskData))](#oh_arkui_postuitaskandwait) | - | Submits the **task** function to the UI thread for execution. The thread calling this API will block until the **task** function completes execution. Calling this API from the UI thread is equivalent to synchronously calling the **task** function. This is suitable for scenarios involving multi-threaded UI component creation. When you need to call functions that are only supported on the UI thread during the multi-threaded component creation process, you can use this API to return to the UI thread to call the function and then resume multi-threaded component creation after the call completes. When the UI thread is under high load, non-UI threads calling this API may block for extended periods, affecting the performance of multi-threaded UI component creation. Frequent use is not recommended.|
| [int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonevent) | - | Registers a basic event callback for the target node.|
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)](#oh_arkui_nativemodule_unregistercommonevent) | - | Unregisters the basic event callback for the target node.|
| [int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))](#oh_arkui_nativemodule_registercommonvisibleareaapproximatechangeevent) | - | Registers a basic event callback for visible area changes with a constrained callback interval.|
| [int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)](#oh_arkui_nativemodule_unregistercommonvisibleareaapproximatechangeevent) | - | Unregisters the basic event callback for visible area changes with a constrained callback interval.|
| [int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)](#oh_arkui_swiper_finishanimation) | - | Stops the page turning animation being executed by the specified **Swiper** node.|
| [int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (*colorInvertFunc)(uint32_t color))](#oh_arkui_setforcedarkconfig) | - | Sets the color inversion algorithm for the component and instance.|
| [ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_gettouchtestinfo) | - | Obtains the touch test information in the component event.|
| [int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)](#oh_arkui_nativemodule_convertpositiontowindow) | - | Converts the coordinates of a point from the coordinate system of the target node to the coordinate system of the current window.|
| [int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)](#oh_arkui_nativemodule_convertpositionfromwindow) | - | Converts the coordinates of a point from the current window's coordinate system to the target node's coordinate system.|

### Macros

| Name| Description|
| -------- | -------- |
| MAX_NODE_SCOPE_NUM 1000| Defines the maximum number methods for a component.|
| MAX_COMPONENT_EVENT_ARG_NUM 12| Defines the maximum number of parameters for a component event.|

## Enum Description

### ArkUI_NodeType

```c
enum ArkUI_NodeType
```

**Description**


Enumerates ArkUI component types that can be created on the native side.

**Since**: 12

| Value| Description                                  |
| -- |--------------------------------------|
| ARKUI_NODE_CUSTOM = 0 | Custom node.                              |
| ARKUI_NODE_TEXT = 1 | Text.                                 |
| ARKUI_NODE_SPAN = 2 | Text span.                               |
| ARKUI_NODE_IMAGE_SPAN = 3 | Image span.                             |
| ARKUI_NODE_IMAGE = 4 | Image.                                 |
| ARKUI_NODE_TOGGLE = 5 | Toggle.                               |
| ARKUI_NODE_LOADING_PROGRESS = 6 | Loading icon.                               |
| ARKUI_NODE_TEXT_INPUT = 7 | Single-line text input.                             |
| ARKUI_NODE_TEXT_AREA = 8 | Multi-line text input.                               |
| ARKUI_NODE_BUTTON = 9 | Icon.                                 |
| ARKUI_NODE_PROGRESS = 10 | Progress indicator.                                |
| ARKUI_NODE_CHECKBOX = 11 | Check box.                                |
| ARKUI_NODE_XCOMPONENT = 12 | XComponent of the SURFACE type.                |
| ARKUI_NODE_DATE_PICKER = 13 | Date picker.                            |
| ARKUI_NODE_TIME_PICKER = 14 | Time picker.                             |
| ARKUI_NODE_TEXT_PICKER = 15 | Text picker.                        |
| ARKUI_NODE_CALENDAR_PICKER = 16 | Calendar picker.                            |
| ARKUI_NODE_SLIDER = 17 | Slider.                              |
| ARKUI_NODE_RADIO = 18 | Radio button.                                |
| ARKUI_NODE_IMAGE_ANIMATOR = 19 | Frame animation component.                              |
| ARKUI_NODE_XCOMPONENT_TEXTURE | XComponent of the TEXTURE type.<br>**Since**: 18|
| ARKUI_NODE_CHECKBOX_GROUP = 21 | Check box group.<br>**Since**: 15               |
| ARKUI_NODE_STACK = MAX_NODE_SCOPE_NUM | Stack container.                               |
| ARKUI_NODE_SWIPER | Swiper.                               |
| ARKUI_NODE_SCROLL | Scrolling container.                               |
| ARKUI_NODE_LIST | List.                                 |
| ARKUI_NODE_LIST_ITEM | List item.                                |
| ARKUI_NODE_LIST_ITEM_GROUP | List item group.                           |
| ARKUI_NODE_COLUMN | Column container.                             |
| ARKUI_NODE_ROW | Row container.                             |
| ARKUI_NODE_FLEX | Flex container.                             |
| ARKUI_NODE_REFRESH | Refresh component.                               |
| ARKUI_NODE_WATER_FLOW | Water flow container.                              |
| ARKUI_NODE_FLOW_ITEM | Water flow item.                             |
| ARKUI_NODE_RELATIVE_CONTAINER | Relative layout component.                             |
| ARKUI_NODE_GRID | Grid.                               |
| ARKUI_NODE_GRID_ITEM | Grid item.                              |
| ARKUI_NODE_CUSTOM_SPAN | Custom span.                            |
| ARKUI_NODE_EMBEDDED_COMPONENT | In-application embedded component.<br>**Since**: 20 |
| ARKUI_NODE_UNDEFINED | Undefined component type. All component types in the color inversion API.<br>**Since**: 20 |
| ARKUI_NODE_PICKER = 1018 | **Picker** component, which is used to implement user selection operations.<br>**Since**: 23 |

### ArkUI_NodeAttributeType

```c
enum ArkUI_NodeAttributeType
```

**Description**


Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

| Value|Description                                                                                |
| -- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| NODE_WIDTH = 0 | Defines the width attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width, in vp.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width, in vp.|
| NODE_HEIGHT = 1 | Defines the height attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: height, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: height, in vp.|
| NODE_BACKGROUND_COLOR = 2 | Defines the background color attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.|
| NODE_BACKGROUND_IMAGE = 3 | Defines the background image attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: image address. In API version 22 and earlier versions, the value can be network image resource addresses, local image resource addresses, Base64 strings, or PixelMap resources, but cannot be addresses of SVG images, or animated images such as GIF and WebP. In API version 23 and later versions, animated images of the WebP and GIF types are supported. Only the first frame of the animated image is displayed. Other types of animated images are not supported.<br> .value[0]?.i32: whether to repeat the image. Optional. The parameter type is [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat). The default value is **ARKUI_IMAGE_REPEAT_NONE**.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: image address. In API version 22 and earlier versions, the value can be network image resource addresses, local image resource addresses, Base64 strings, or PixelMap resources, but cannot be addresses of SVG images, or animated images such as GIF and WebP. In API version 23 and later versions, animated images of the WebP and GIF types are supported. Only the first frame of the animated image is displayed. Other types of animated images are not supported.<br> .value[0].i32: whether to repeat the image. The parameter type is [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat).<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set.|
| NODE_PADDING = 4 | Defines the padding attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: Specify the same padding for the four directions.<br> .value[0].f32: padding, in vp.<br> 2: Specify different paddings for different directions.<br> .value[0].f32: top padding, in vp.<br> .value[1].f32: right padding, in vp.<br> .value[2].f32: bottom padding, in vp.<br> .value[3].f32: left padding, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: top padding, in vp.<br> .value[1].f32: right padding, in vp.<br> .value[2].f32: bottom padding, in vp.<br> .value[3].f32: left padding, in vp.|
| NODE_ID = 5 | Defines the component ID attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component ID.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component ID.|
| NODE_ENABLED = 6 | Defines the interactivity attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The value **true** means that the component can interact with users, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value **1** means that the component can interact with users, and **0** means the opposite. |
| NODE_MARGIN = 7 | Defines the margin attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: Specify the same margin for the four directions.<br> .value[0].f32: margin, in vp.<br> 2: Specify different margins for different directions.<br> .value[0].f32: top margin, in vp.<br> .value[1].f32: right margin, in vp.<br> .value[2].f32: bottom margin, in vp.<br> .value[3].f32: left margin, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: top margin, in vp.<br> .value[1].f32: right margin, in vp.<br> .value[2].f32: bottom margin, in vp.<br> .value[3].f32: left margin, in vp.|
| NODE_TRANSLATE = 8 | Defines the translate attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: distance to translate along the x-axis, in vp. The default value is **0**.<br> .value[1].f32: distance to translate along the y-axis, in vp. The default value is **0**.<br> .value[2].f32: distance to translate along the z-axis, in vp. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: distance to translate along the x-axis, in vp.<br> .value[1].f32: distance to translate along the y-axis, in vp.<br> .value[2].f32: distance to translate along the z-axis, in vp.|
| NODE_SCALE = 9 | Defines the scale attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: scale factor along the x-axis. The default value is **1**.<br> .value[1].f32: scale factor along the y-axis. The default value is **1**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: scale factor along the x-axis.<br> .value[1].f32: scale factor along the y-axis.|
| NODE_ROTATE = 10 | Defines the rotate attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: X-coordinate of the rotation axis vector. The default value is **0**.<br> .value[1].f32: Y-coordinate of the rotation axis vector. The default value is **0**.<br> .value[2].f32: Z-coordinate of the rotation axis vector. The default value is **0**.<br> .value[3].f32: rotation angle. The default value is **0**.<br> .value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: X-coordinate of the rotation axis vector.<br> .value[1].f32: Y-coordinate of the rotation axis vector.<br> .value[2].f32: Z-coordinate of the rotation axis vector.<br> .value[3].f32: rotation angle.<br> .value[4].f32: line of sight, that is, the distance from the viewpoint to the z=0 plane, in vp.|
| NODE_BRIGHTNESS = 11 | Sets the brightness attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: brightness value. The default value is **1.0**, and the recommended value range is [0, 2].<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: brightness value.|
| NODE_SATURATION = 12 | Sets the saturation attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: saturation value. The default value is **1.0**, and the recommended value range is [0, 50).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: saturation value.|
| NODE_BLUR = 13 | Sets the blur attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: blur radius. A larger value indicates a higher blur degree. If the value is **0**, the component is not blurred. If the value is less than 0, it is treated as **0** and no error code is returned. The unit is vp. The default value is **0.0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: blur radius. The larger the fuzzy radius, the more blurred the image. If the value is **0**, the image is not blurred. The unit is vp.|
| NODE_LINEAR_GRADIENT = 14 | Sets the gradient attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: start angle of the linear gradient. This attribute takes effect only when [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection) is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**. A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is **180**.<br> .value[1].i32: direction of the linear gradient. When it is set to any value other than **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**, the **angle** setting becomes ineffective. The data type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection).<br> .value[2].i32: whether the colors are repeated. The default value is **false**.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops.<br> **stops**: stop positions of the color stops.<br> **size**: number of colors.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: start angle of the linear gradient. The set value is used only when **ArkUI_LinearGradientDirection** is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**. In other cases, the default value is used.<br> .value[1].i32: direction of the linear gradient.<br> .value[2].i32: whether the colors are repeated.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops.<br> **stops**: stop positions of the color stops.<br> **size**: number of colors.|
| NODE_ALIGNMENT = 15 | Sets the alignment attribute, which can be set, reset, and obtained as required through APIs. In the **Stack** component, this attribute has the same effect as **NODE_STACK_ALIGN_CONTENT**, which means that it sets the alignment mode of child components in the container.<br><br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_CENTER**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment).|
| NODE_OPACITY = 16 | Defines the opacity attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: opacity value. The value ranges from 0 to 1.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: opacity value. The value ranges from 0 to 1.|
| NODE_BORDER_WIDTH = 17 | Defines the border width attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].f32: width of the four borders.<br> 2: .value[0].f32: width of the top border.<br> .value[1].f32: width of the right border.<br> .value[2].f32: width of the bottom border.<br> .value[3].f32: width of the left border.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width of the top border.<br> .value[1].f32: width of the right border.<br> .value[2].f32: width of the bottom border.<br> .value[3].f32: width of the left border.|
| NODE_BORDER_RADIUS = 18 | Defines the border corner radius attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].f32: radius of the four corners.<br> 2: .value[0].f32: radius of the upper left corner.<br> .value[1].f32: radius of the upper right corner.<br> .value[2].f32: radius of the lower left corner.<br> .value[3].f32: radius of the lower right corner.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: radius of the upper left corner.<br> .value[1].f32: radius of the upper right corner.<br> .value[2].f32: radius of the lower left corner.<br> .value[3].f32: radius of the lower right corner.|
| NODE_BORDER_COLOR = 19 | Defines the border color attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].u32: color of the four borders, in 0xARGB format, for example, **0xFFFF11FF**.<br> 2: .value[0].u32: color of the top border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[1].u32: color of the right border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[2].u32: color of the lower border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[3].u32: color of the left border, in 0xARGB format, for example, **0xFFFF11FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the top border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[1].u32: color of the right border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[2].u32: color of the lower border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[3].u32: color of the left border, in 0xARGB format, for example, **0xFFFF11FF**.|
| NODE_BORDER_STYLE = 20 | Defines the border line style attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].i32: line style of the four borders. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.<br> 2: .value[0].i32: line style of the top border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.<br> .value[1].i32: line style of the right border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.<br> .value[2].i32: line style of the bottom border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.<br> .value[3].i32: line style of the left border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: line style of the top border.<br> .value[1].i32: line style of the right border.<br> .value[2].i32: line style of the bottom border.<br> .value[3].i32: line style of the left border.|
| NODE_Z_INDEX = 21 | Defines the z-index attribute for the stack sequence. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: z-index value.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: z-index value.|
| NODE_VISIBILITY = 22 | Defines the visibility attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show or hide the component. The parameter type is [ArkUI_Visibility](capi-native-type-h.md#arkui_visibility). The default value is **ARKUI_VISIBILITY_VISIBLE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show or hide the component. The parameter type is [ArkUI_Visibility](capi-native-type-h.md#arkui_visibility). The default value is **ARKUI_VISIBILITY_VISIBLE**.|
| NODE_CLIP = 23 | Defines the clip attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to clip the area of child components that extend beyond the bounds of the parent component. The value **0** indicates no clipping, and the value **1** indicates clipping.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to clip the area of child components that extend beyond the bounds of the parent component. The value **0** indicates no clipping, and the value **1** indicates clipping.|
| NODE_CLIP_SHAPE = 24 | Defines the clipping region on the component. This attribute can be set and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1. Rectangle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype). The value is **ARKUI_CLIP_TYPE_RECTANGLE**.<br> .value[1].f32: width of the rectangle.<br> .value[2].f32: height of the rectangle.<br> .value[3].f32: width of the rounded corner of the rectangle.<br> .value[4].f32: height of the rounded corner of the rectangle.<br> .value[5]?.f32: radius of the upper left corner of the rectangle. <br> .value[6]?.f32: radius of the lower left corner of the rectangle. <br> .value[7]?.f32: radius of the upper right corner of the rectangle. <br> .value[8]?.f32: radius of the lower right corner of the rectangle. <br> .object: coordinate offset of the rectangle. The parameter type is [ArkUI_RenderNodeClipOption](./capi-arkui-nativemodule-arkui-rendernodeclipoption.md). It takes effect when only the **.object** parameter is passed.<br> 2. Circle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype). The value is **ARKUI_CLIP_TYPE_CIRCLE**.<br> .value[1].f32: width of the circle.<br> .value[2].f32: height of the circle.<br> .object: coordinate offset of the circle. The parameter type is [ArkUI_RenderNodeClipOption](./capi-arkui-nativemodule-arkui-rendernodeclipoption.md). It takes effect when only the **.object** parameter is passed.<br> 3. Ellipse:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype). The value is **ARKUI_CLIP_TYPE_ELLIPSE**.<br> .value[1].f32: width of the ellipse.<br> .value[2].f32: height of the ellipse.<br> .object: coordinate offset of the ellipse. The parameter type is [ArkUI_RenderNodeClipOption](./capi-arkui-nativemodule-arkui-rendernodeclipoption.md). It takes effect when only the **.object** parameter is passed.<br> 4. Path:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype). The value is **ARKUI_CLIP_TYPE_PATH**.<br> .value[1].f32: width of the path.<br> .value[2].f32: height of the path.<br> .string: command for drawing the path.<br> .object: command for drawing the path. The parameter type is [ArkUI_RenderNodeClipOption](./capi-arkui-nativemodule-arkui-rendernodeclipoption.md). It takes effect when only the **.object** parameter is passed.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> 1. Rectangle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype). The value is **ARKUI_CLIP_TYPE_RECTANGLE**.<br> .value[1].f32: width of the rectangle.<br> .value[2].f32: height of the rectangle.<br> .value[3].f32: width of the rounded corner of the rectangle.<br> .value[4].f32: height of the rounded corner of the rectangle.<br> .value[5]?.f32: radius of the upper left corner of the rectangle. <br> .value[6]?.f32: radius of the lower left corner of the rectangle. <br> .value[7]?.f32: radius of the upper right corner of the rectangle. <br> .value[8]?.f32: radius of the lower right corner of the rectangle. <br> .value[9]?.f32: horizontal coordinate offset of the rectangle.<br> .value[10]?.f32: vertical coordinate offset of the rectangle.<br> 2. Circle:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype). The value is **ARKUI_CLIP_TYPE_CIRCLE**.<br> .value[1].f32: width of the circle.<br> .value[2].f32: height of the circle.<br> .value[3]?.f32: horizontal coordinate offset of the circle.<br> .value[4]?.f32: vertical coordinate offset of the circle.<br> 3. Ellipse:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype). The value is **ARKUI_CLIP_TYPE_ELLIPSE**.<br> .value[1].f32: width of the ellipse.<br> .value[2].f32: height of the ellipse.<br> .value[3]?.f32: horizontal coordinate offset of the ellipse.<br> .value[4]?.f32: vertical coordinate offset of the ellipse.<br> 4. Path:<br> .value[0].i32: type of shape. The parameter type is [ArkUI_ClipType](capi-native-type-h.md#arkui_cliptype). The value is **ARKUI_CLIP_TYPE_PATH**.<br> .value[1].f32: width of the path.<br> .value[2].f32: height of the path.<br> .string: command for drawing the path.|
| NODE_TRANSFORM = 25 | Defines the transform attribute, which can be used to translate, rotate, and scale images. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0...15].f32: 16 floating-point numbers. In this case, the value of size in [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) cannot be 0.<br> .object: pointer to [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md). The value of size in [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is 0.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0...15].f32: 16 floating-point numbers.|
| NODE_HIT_TEST_BEHAVIOR = 26 | Defines the hit test behavior attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: hit test mode. The parameter type is [ArkUI_HitTestMode](capi-native-type-h.md#arkui_hittestmode). The default value is **ARKUI_HIT_TEST_MODE_DEFAULT**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: hit test mode. The parameter type is **ArkUI_HitTestMode**. The default value is **ARKUI_HIT_TEST_MODE_DEFAULT**.|
| NODE_POSITION = 27 | Defines the offset attribute, which specifies the offset of the component's upper left corner relative to the parent container's. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: x-coordinate.<br> .value[1].f32: y-coordinate.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: x-coordinate.<br> .value[1].f32: y-coordinate.|
| NODE_SHADOW = 28 | Defines the shadow attribute. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: shadow effect. The parameter type is [ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: shadow effect. The parameter type is [ArkUI_ShadowStyle](capi-native-type-h.md#arkui_shadowstyle).|
| NODE_CUSTOM_SHADOW = 29 | Defines the custom shadow effect. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: blur radius of the shadow, in px.<br> .value[1]?.i32: whether to enable the coloring strategy. The value **1** means to enable the coloring strategy, and **0** (default value) means the opposite.<br> .value[2]?.f32: offset of the shadow along the x-axis, in px.<br> .value[3]?.f32: offset of the shadow along the y-axis, in px.<br> .value[4]?.i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is **ARKUI_SHADOW_TYPE_COLOR**.<br> .value[5]?.u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> .value[6]?.u32: whether to fill the shadow. The value **1** means to fill the shadow, and **0** means the opposite.<br><br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: blur radius of the shadow, in px.<br> .value[1].i32: whether to enable the coloring strategy. <br> .value[2].f32: offset of the shadow along the x-axis, in px.<br> .value[3].f32: offset of the shadow along the y-axis, in px.<br> .value[4].i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is **ARKUI_SHADOW_TYPE_COLOR**.<br> .value[5].u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> .value[6].u32: whether to fill the shadow. The value **1** means to fill the shadow, and **0** means the opposite.|
| NODE_BACKGROUND_IMAGE_SIZE = 30 | Defines the background image width and height. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width of the image. The value range is [0, +∞), and the unit is vp.<br> .value[1].f32: height of the image. The value range is [0, +∞), and the unit is vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width of the image, in vp.<br> .value[1].f32: height of the image, in vp.|
| NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE = 31 | Defines the background image size. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: size of the background image. The value is an enumerated value of [ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: size of the background image. The value is an enumerated value of [ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize).|
| NODE_BACKGROUND_BLUR_STYLE = 32 | Defines the background blur attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: blur type. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).<br> .value[1]?.i32: color mode, specified by an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).<br> .value[2]?.i32: adaptive color mode, specified by an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).<br> .value[3]?.f32: blur degree. The value range is [0.0, 1.0].<br> .value[4]?.f32: start boundary of grayscale blur.<br> .value[5]?.f32: end boundary of grayscale blur.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: blur type. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).<br> .value[1].i32: color mode, specified by an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).<br> .value[2].i32: adaptive color mode, specified by an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).<br> .value[3].f32: blur degree. The value range is [0.0, 1.0].<br> .value[4].f32: start boundary of grayscale blur.<br> .value[5].f32: end boundary of grayscale blur.|
| NODE_TRANSFORM_CENTER = 33 | Defines the transform center attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: x-coordinate of the center point, in vp.<br> .value[1]?.f32: y-coordinate of the center point, in vp.<br> .value[2]?.f32: z-coordinate of the center point, in vp.<br> .value[3]?.f32: x-coordinate of the center point, expressed in a number that represents a percentage. For example, 0.2 indicates 20%. This attribute overwrites value[0].f32. The default value is **0.5f**.<br> .value[4]?.f32: y-coordinate of the center point, expressed in a number that represents a percentage. For example, 0.2 indicates 20%. This attribute overwrites value[1].f32. The default value is **0.5f**.<br> .value[5]?.f32: z-coordinate of the center point, expressed in a number that represents a percentage. For example, 0.2 indicates 20%. This attribute overwrites value[2].f32. The default value is **0.0f**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: x-coordinate of the center point, in vp.<br> .value[1].f32: y-coordinate of the center point, in vp.<br> .value[2].f32: z-coordinate of the center point, in vp.<br> Note: If the coordinate is expressed in a number that represents a percentage, the attribute obtaining API returns the calculated value in vp.|
| NODE_OPACITY_TRANSITION = 34 | Defines the transition opacity attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: opacity values of the start and end points.<br> .value[1].i32: animation duration, in ms.<br> .value[2].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3]?.i32: animation delay duration, in ms.<br> .value[4]?.i32: number of times that the animation is played.<br> .value[5]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[6]?.f32: animation playback speed.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: opacity values of the start and end points.<br> .value[1].i32: animation duration, in ms.<br> .value[2].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3].i32: animation delay duration, in ms.<br> .value[4].i32: number of times that the animation is played.<br> .value[5].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[6].f32: animation playback speed.|
| NODE_ROTATE_TRANSITION = 35 | Defines the transition rotation attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: x-component of the rotation vector.<br> .value[1].f32: y-component of the rotation vector.<br> .value[2].f32: z-component of the rotation vector<br> .value[3].f32: angle.<br> .value[4].f32: line of sight. The default value is **0.0f**.<br> .value[5].i32: animation duration, in ms.<br> .value[6].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[7]?.i32: animation delay duration, in ms.<br> .value[8]?.i32: number of times that the animation is played.<br> .value[9]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[10]?.f32: animation playback speed.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: x-component of the rotation vector.<br> .value[1].f32: y-component of the rotation vector.<br> .value[2].f32: z-component of the rotation vector<br> .value[3].f32: angle.<br> .value[4].f32: line of sight.<br> .value[5].i32: animation duration, in ms.<br> .value[6].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[7].i32: animation delay duration, in ms.<br> .value[8].i32: number of times that the animation is played.<br> .value[9].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[10].f32: animation playback speed.|
| NODE_SCALE_TRANSITION = 36 | Defines the transition scaling attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: scale factor along the X-axis.<br> .value[1].f32: scale factor along the Y-axis.<br> .value[2].f32: scale factor along the Z-axis.<br> value[3].i32: animation duration, in ms.<br> .value[4].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[5]?.i32: animation delay duration, in ms.<br> .value[6]?.i32: number of times that the animation is played.<br> .value[7]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> value[8]?.f32: animation playback speed.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: scale factor along the X-axis.<br> .value[1].f32: scale factor along the Y-axis.<br> .value[2].f32: scale factor along the Z-axis.<br> value[3].i32: animation duration, in ms.<br> .value[4].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> value[5].i32: animation delay duration, in ms.<br> value[6].i32: number of times that the animation is played.<br> .value[7].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> value[8].f32: animation playback speed.|
| NODE_TRANSLATE_TRANSITION = 37 | Defines the transition translation attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].f32: translation distance along the x-axis, in vp.<br> value[1].f32: translation distance along the y-axis, in vp.<br> value[2].f32: translation distance along the z-axis, in vp.<br> value[3].i32: animation duration, in ms.<br> value[4].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> value[5]?.i32: animation delay duration, in ms.<br> value[6]?.i32: number of times that the animation is played.<br> value[7]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> value[8]?.f32: animation playback speed.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: translation distance along the x-axis, in vp.<br> value[1].f32: translation distance along the y-axis, in vp.<br> value[2].f32: translation distance along the z-axis, in vp.<br> value[3].i32: animation duration, in ms.<br> value[4].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> value[5].i32: animation delay duration, in ms.<br> value[6].i32: number of times that the animation is played.<br> value[7].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> value[8].f32: animation playback speed.|
| NODE_MOVE_TRANSITION = 38 | Defines the slide-in and slide-out of the component from the screen edge during transition. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: [ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge) type.<br> .value[1].i32: animation duration, in ms.<br> .value[2].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3]?.i32: animation delay duration, in ms.<br> .value[4]?.i32: number of times that the animation is played.<br> .value[5]?.i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[6]?.f32: animation playback speed.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: [ArkUI_TransitionEdge](capi-native-type-h.md#arkui_transitionedge) type.<br> .value[1].i32: animation duration, in ms.<br> .value[2].i32: animation curve type. The value is an enumerated value of [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve).<br> .value[3].i32: animation delay duration, in ms.<br> .value[4].i32: number of times that the animation is played.<br> .value[5].i32: animation playback mode. The value is an enumerated value of [ArkUI_AnimationPlayMode](capi-native-type-h.md#arkui_animationplaymode).<br> .value[6].f32: animation playback speed.|
| NODE_FOCUSABLE = 39 | Defines the focus attribute, which can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The value **1** indicates focusable, and **0** indicates not focusable.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value **1** indicates focusable, and **0** indicates not focusable.|
| NODE_DEFAULT_FOCUS = 40 | Defines the default focus attribute, which can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].i32: The value **1** indicates that the target is the default focus, and **0** indicates that it is not the default focus.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: The value **1** indicates that the target is the default focus, and **0** indicates that it is not the default focus.|
| NODE_RESPONSE_REGION = 41 | Defines the touch target attribute, which can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .data[0].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp.<br> .data[1].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp.<br> .data[2].f32: width of the touch target, in percentage.<br> .data[3].f32: height of the touch target, in percentage.<br> .data[4...].f32: Multiple touch targets can be set. The sequence of the parameters is the same as the preceding.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .data[0].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp.<br> .data[1].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp.<br> .data[2].f32: width of the touch target, in percentage.<br> .data[3].f32: height of the touch target, in percentage.<br> .data[4...].f32: Multiple touch targets can be set. The sequence of the parameters is the same as the preceding.<br>Note: During configuration, the data array can contain any number of values (all will be accepted), but only the first 20 values can be retrieved. |
| NODE_OVERLAY = 42 | Defines the overlay attribute. This attribute can be set, reset, and obtained as required through APIs. You can set the overlay content through .string or .object, with .string having higher priority. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: mask text.<br> .value[0]?.i32: position of the overlay relative to the component. Optional. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_TOP_START**.<br> .value[1]?.f32: offset of the overlay relative to the upper left corner of itself on the x-axis, in vp. Optional. The default value is **0** vp.<br> .value[2]? .f32: offset of the overlay relative to the upper left corner of itself on the y-axis, in vp. Optional. The default value is **0** vp.<br> .value[3]?.i32: layout direction of the overlay. Optional. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_LTR**.<br> In most scenarios, this parameter should be set to **Auto**, which allows the system to automatically handle the layout direction. If specific directions need to be maintained in certain scenarios, set this parameter to **LTR** (left-to-right) or **RTL** (right-to-left). It is supported since API version 21.<br>.object: node tree used for overlay. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md), and the default value is **nullptr**. It is supported since API version 21.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: mask text.<br> .value[0].i32: position of the overlay relative to the component. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_TOP_START**.<br> .value[1].f32: offset of the overlay relative to the upper left corner of itself on the x-axis, in vp.<br> .value[2].f32: offset of the overlay relative to the upper left corner of itself on the y-axis, in vp.<br>.value[3].i32: layout direction of the overlay. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_LTR**. It is supported since API version 21.<br>.object: node tree used for overlay. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). It is supported since API version 21.<br>|
| NODE_SWEEP_GRADIENT = 43 | Defines the sweep gradient effect. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: x-coordinate of the sweep gradient center relative to the upper left corner of the component.<br> .value[1]?.f32: y-coordinate of the sweep gradient center relative to the upper left corner of the component.<br> .value[2]?.f32: start point of the sweep gradient. The default value is **0**.<br> .value[3]?.f32: end point of the sweep gradient. The default value is **0**.<br> .value[4]?.f32: rotation angle of the sweep gradient. The default value is **0**.<br> .value[5]?.i32: whether the colors are repeated. The value **1** means that the colors are repeated, and **0** means the opposite.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops.<br> **stops**: stop positions of the color stops.<br> **size**: number of colors.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: x-coordinate of the sweep gradient center relative to the upper left corner of the component.<br> .value[1].f32: y-coordinate of the sweep gradient center relative to the upper left corner of the component.<br> .value[2].f32: start point of the sweep gradient. The default value is **0**.<br> .value[3].f32: end point of the sweep gradient. The default value is **0**.<br> .value[4].f32: rotation angle of the sweep gradient. The default value is **0**.<br> .value[5].i32: whether the colors are repeated. The value **1** means that the colors are repeated, and **0** means the opposite.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops.<br> **stops**: stop positions of the color stops.<br> **size**: number of colors.|
| NODE_RADIAL_GRADIENT = 44 | Defines the radial gradient effect. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: x-coordinate of the radial gradient center relative to the upper left corner of the component.<br> .value[1]?.f32: y-coordinate of the radial gradient center relative to the upper left corner of the component.<br> .value[2]?.f32: radius of the radial gradient. The default value is **0**.<br> .value[3]?.i32: whether the colors are repeated. The value **1** means that the colors are repeated, and **0** means the opposite.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops.<br> **stops**: stop positions of the color stops.<br> **size**: number of colors.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: x-coordinate of the radial gradient center relative to the upper left corner of the component.<br> .value[1].f32: y-coordinate of the radial gradient center relative to the upper left corner of the component.<br> .value[2].f32: radius of the radial gradient. The default value is **0**.<br> .value[3].i32: whether the colors are repeated. The value **1** means that the colors are repeated, and **0** means the opposite.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops.<br> **stops**: stop positions of the color stops.<br> **size**: number of colors.|
| NODE_MASK = 45 | Adds a mask of the specified shape to the component. This attribute can be set and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1. Rectangle:<br> .value[0].u32: fill color, in 0xARGB format.<br> .value[1].u32: stroke color, in 0xARGB format.<br> .value[2].f32: stroke width, in vp.<br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_RECTANGLE**.<br> .value[4].f32: width of the rectangle, in vp.<br> .value[5].f32: height of the rectangle, in vp.<br> .value[6].f32: corner radius width of the rectangle, in vp.<br> .value[7].f32: corner radius height of the rectangle, in vp.<br> .value[8]?.f32: radius of the upper left corner of the rectangle, in vp.<br> .value[9]?.f32: radius of the lower left corner of the rectangle, in vp.<br> .value[10]?.f32: radius of the upper right corner of the rectangle, in vp.<br> .value[11]?.f32: radius of the lower right corner of the rectangle, in vp.<br> 2. Circle:<br> .value[0].u32: fill color, in 0xARGB format.<br> .value[1].u32: stroke color, in 0xARGB format.<br> .value[2].f32: stroke width, in vp.<br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_CIRCLE**.<br> .value[4].f32: width of the circle, in vp.<br> .value[5].f32: height of the circle, in vp.<br> 3. Ellipse:<br> .value[0].u32: fill color, in 0xARGB format.<br> .value[1].u32: stroke color, in 0xARGB format.<br> .value[2].f32: stroke width, in vp.<br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_ELLIPSE**.<br> .value[4].f32: width of the ellipse, in vp.<br> .value[5].f32: height of the ellipse, in vp.<br> 4. Path:<br> .value[0].u32: fill color, in 0xARGB format.<br> .value[1].u32: stroke color, in 0xARGB format.<br> .value[2].f32: stroke width, in vp.<br> .value[3].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_PATH**.<br> .value[4].f32: width of the path, in vp.<br> .value[5].f32: height of the path, in vp.<br> .string: command for drawing the path.<br> 5. Progress:<br> .value[0].i32: mask type. The parameter type is [ArkUI_MaskType](capi-native-type-h.md#arkui_masktype). The value is **ARKUI_MASK_TYPE_PROGRESS**.<br> .value[1].f32: current value of the progress indicator.<br> .value[2].f32: maximum value of the progress indicator.<br> .value[3].u32: color of the progress indicator.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> 1. Rectangle:<br> .value[0].u32: fill color, in 0xARGB format.<br> .value[1].u32: stroke color, in 0xARGB format.<br> .value[2].f32: stroke width, in vp.<br> .value[3].i32: mask type.<br> .value[4].f32: width of the rectangle, in vp.<br> .value[5].f32: height of the rectangle, in vp.<br> .value[6].f32: corner radius width of the rectangle, in vp.<br> .value[7].f32: corner radius height of the rectangle, in vp.<br> .value[8]?.f32: radius of the upper left corner of the rectangle, in vp.<br> .value[9]?.f32: radius of the lower left corner of the rectangle, in vp.<br> .value[10]?.f32: radius of the upper right corner of the rectangle, in vp.<br> .value[11]?.f32: radius of the lower right corner of the rectangle, in vp.<br> 2. Circle:<br> .value[0].u32 fill color, in 0xARGB format.<br> .value[1].u32: stroke color, in 0xARGB format.<br> .value[2].f32: stroke width, in vp.<br> .value[3].i32: mask type.<br> .value[4].f32: width of the circle, in vp.<br> .value[5].f32: height of the circle, in vp.<br> 3. Ellipse:<br> .value[0].u32: fill color, in 0xARGB format.<br> .value[1].u32: stroke color, in 0xARGB format.<br> .value[2].f32: stroke width, in vp.<br> .value[3].i32: mask type.<br> .value[4].f32: width of the ellipse, in vp.<br> .value[5].f32: height of the ellipse, in vp.<br> 4. Path:<br> .value[0].u32: fill color, in 0xARGB format.<br> .value[1].u32: stroke color, in 0xARGB format.<br> .value[2].f32: stroke width, in vp.<br> .value[3].i32: mask type.<br> .value[4].f32: width of the path, in vp.<br> .value[5].f32: height of the path, in vp.<br> .string: command for drawing the path.<br> 5. Progress:<br> .value[0].i32: mask type.<br> .value[1].f32: current value of the progress indicator.<br> .value[2].f32: maximum value of the progress indicator.<br> .value[3].u32: color of the progress indicator.<br>|
| NODE_BLEND_MODE = 46 | Blends the component's background with the content of the component's child node. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: blend mode. The parameter type is [ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode). The default value is **ARKUI_BLEND_MODE_NONE**.<br> .value[1].?i32: how the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype). The default value is **BLEND_APPLY_TYPE_FAST**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: blend mode. The parameter type is [ArkUI_BlendMode](capi-native-type-h.md#arkui_blendmode). The default value is **ARKUI_BLEND_MODE_NONE**.<br> .value[1].i32: how the specified blend mode is applied. The parameter type is [ArkUI_BlendApplyType](capi-native-type-h.md#arkui_blendapplytype). The default value is **BLEND_APPLY_TYPE_FAST**.|
| NODE_DIRECTION = 47 | Sets the direction of the main axis. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: direction of the main axis.<br> The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_AUTO**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: direction of the main axis.<br> The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_AUTO**.|
| NODE_CONSTRAINT_SIZE = 48 | Defines the size constraints. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum width, in vp.<br> .value[1].f32: maximum width, in vp.<br> .value[2].f32: minimum height, in vp.<br> .value[3].f32: maximum height, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum width, in vp.<br> .value[1].f32: maximum width, in vp.<br> .value[2].f32: minimum height, in vp.<br> .value[3].f32: maximum height, in vp.|
| NODE_GRAY_SCALE = 49 | Defines the grayscale effect. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1. For example, 0.5 indicates a 50% grayscale conversion ratio.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: grayscale conversion ratio. The value ranges from 0 to 1.|
| NODE_INVERT = 50 | Inverts the image. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: image inversion ratio. The value ranges from 0 to 1. For example, 0.5 indicates a 50% image inversion ratio.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: image inversion ratio. The value ranges from 0 to 1.|
| NODE_SEPIA = 51 | Defines the sepia conversion ratio. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: sepia conversion ratio. The value ranges from 0 to 1. For example, 0.5 indicates that a 50% sepia conversion ratio.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: sepia conversion ratio. The value ranges from 0 to 1. |
| NODE_CONTRAST = 52 | Defines the contrast attribute. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: contrast. If the value is **1**, the source image is displayed. A larger value indicates a higher contrast. Value range: [0, 10).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: contrast. Value range: [0, 10). |
| NODE_FOREGROUND_COLOR = 53 | Sets the foreground color attribute. This attribute can be set and reset as required through APIs. However, the reset API has no effect on this attribute.<br>There are two parameter formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute:<br> 1: .value[0].u32: color value, in 0xARGB format. For example, **0xFFFF0000** indicates red.<br> 2: .value[0].i32: color enum **ArkUI_ColoringStrategy**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format.|
| NODE_OFFSET = 54 | Defines the offset of the component's child relative to the component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32 : offset along the x-axis, in vp.<br> .value[1].f32 : offset along the y-axis, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32 : offset along the x-axis, in vp.<br> .value[1].f32 : offset along the y-axis, in vp.|
| NODE_MARK_ANCHOR = 55 | Sets the anchor for locating the component's child. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: x-coordinate of the anchor, in vp.<br> .value[1].f32: y-coordinate of the anchor, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: x-coordinate of the anchor, in vp.<br> .value[1].f32: y-coordinate of the anchor, in vp. |
| NODE_BACKGROUND_IMAGE_POSITION = 56 | Defines the position of the background image in the component, that is, the coordinates relative to the upper left corner of the component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: position along the x-axis, in px.<br> .value[1].f32: position along the y-axis, in px.<br> .value[2].?i32: alignment mode. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_TOP_START**. **Since**: 21<br> .value[3].?i32: layout direction. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_AUTO**. **Since**: 21<br> In most scenarios, this parameter should be set to **AUTO**, which allows the system to automatically handle the layout direction. If specific directions need to be maintained in certain scenarios, set this parameter to **LTR** (left-to-right) or **RTL** (right-to-left).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: position along the x-axis, in px.<br> .value[1].f32: position along the y-axis, in px.<br> .value[2].?i32: alignment mode. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_TOP_START**. **Since**: 21<br> .value[3].i32: layout direction. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_AUTO**. **Since**: 21|
| NODE_ALIGN_RULES = 57 | Sets the alignment rules in the relative container. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.object: [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md) object that defines the alignment rules.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md) object that defines the alignment rules.|
| NODE_ALIGN_SELF = 58 | Sets the alignment mode of the child components along the cross axis of the parent container. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode of the child components along the cross axis of the parent container. <br> The parameter type is [ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment). The default value is **ARKUI_ITEM_ALIGNMENT_AUTO**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode of the child components along the cross axis of the parent container. <br> The parameter type is [ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment). The default value is **ARKUI_ITEM_ALIGNMENT_AUTO**.|
| NODE_FLEX_GROW = 59 | Sets the percentage of the parent container's remaining space that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: percentage of the parent container's remaining space that is allocated to the component.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: percentage of the parent container's remaining space that is allocated to the component.|
| NODE_FLEX_SHRINK = 60 | Sets the percentage of the parent container's shrink size that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: percentage of the parent container's shrink size that is allocated to the component.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: percentage of the parent container's shrink size that is allocated to the component.|
| NODE_FLEX_BASIS = 61 | Sets the base size of the component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: base size of the component on the main axis of the parent container.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: base size of the component on the main axis of the parent container.|
| NODE_ACCESSIBILITY_GROUP = 62 | Sets the accessibility group. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: Accessibility group. The value **1** means that the component and all its child components form an entire selectable component. In this case, the accessibility service will no longer be available for the content of its child components. The value is **1** or **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Accessibility group. The value **1** means that the component and all its child components form an entire selectable component. In this case, the accessibility service will no longer be available for the content of its child components. The value is **1** or **0**.|
| NODE_ACCESSIBILITY_TEXT = 63 | Sets the accessibility text. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: accessibility text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: accessibility text.|
| NODE_ACCESSIBILITY_MODE = 64 | Defines the accessibility mode. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: accessibility mode. The parameter type is [ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: accessibility mode. The parameter type is [ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode).|
| NODE_ACCESSIBILITY_DESCRIPTION = 65 | Sets the accessibility description. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: accessibility description.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: accessibility description.|
| NODE_FOCUS_STATUS = 66 | Defines the component focus status. This attribute can be set and obtained as required through APIs.<br>Note: Setting the parameter to **0** shifts focus from the currently focused component on the current level of the page to the root container.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The value **1** indicates that the component gains focus and **0** indicates that the component loses focus.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value **1** indicates that the component gains focus and **0** indicates that the component loses focus.|
| NODE_ASPECT_RATIO = 67 | Defines the aspect ratio attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: aspect ratio of the component, in width/height format.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: aspect ratio of the component, in width/height format.|
| NODE_LAYOUT_WEIGHT = 68 | Defines the weight of the component within its row, column, or flex container for proportional distribution of available space within the container. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: weight of the component along the main axis.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: weight of the component along the main axis. |
| NODE_DISPLAY_PRIORITY = 69 | Sets the display priority for the component in the row, column, or flex (single-line) container. When the **displayPriority** value of a child component is greater than 1, a larger value indicates higher priority. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: display priority of the component in the container.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: display priority of the component in the container.|
| NODE_OUTLINE_WIDTH = 70 | Sets the thickness of an element's outline.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: thickness of the left outline.<br> .value[1].f32: thickness of the top outline.<br> .value[2].f32: thickness of the right outline.<br> .value[3].f32: thickness of the bottom outline.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: thickness of the left outline.<br> .value[1].f32: thickness of the top outline.<br> .value[2].f32: thickness of the right outline.<br> .value[3].f32: thickness of the bottom outline.|
| NODE_WIDTH_PERCENT = 71 | Defines the width attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width, in percentage.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width, in percentage.|
| NODE_HEIGHT_PERCENT = 72 | Defines the height attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: height, in percentage. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: height, in percentage. |
| NODE_PADDING_PERCENT = 73 | Defines the padding attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: Specify the same padding for the four directions.<br> .value[0].f32: padding, in percentage. <br> 2: Specify different paddings for different directions.<br> .value[0].f32: top padding, in percentage. <br> .value[1].f32: right padding, in percentage. <br> .value[2].f32: bottom padding, in percentage. <br> .value[3].f32: left padding, in percentage. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: top padding, in percentage. <br> .value[1].f32: right padding, in percentage. <br> .value[2].f32: bottom padding, in percentage. <br> .value[3].f32: left padding, in percentage. |
| NODE_MARGIN_PERCENT = 74 | Defines the margin attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: Specify the same margin for the four directions.<br> .value[0].f32: margin, in percentage.<br> 2: Specify different margins for different directions.<br> .value[0].f32: top margin, in percentage.<br> .value[1].f32: right margin, in percentage.<br> .value[2].f32: bottom margin, in percentage.<br> .value[3].f32: left margin, in percentage.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: top margin, in percentage.<br> .value[1].f32: right margin, in percentage.<br> .value[2].f32: bottom margin, in percentage.<br> .value[3].f32: left margin, in percentage.|
| NODE_GEOMETRY_TRANSITION = 75 | Implements an implicit shared element transition. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: two components bound to the shared element. The parameter type is 1 or 0. By default, the out component does not continue to participate in the shared element animation when not yet deleted, which means that it stays in its original position.<br> .string: ID used to set up a binding relationship. If this attribute is set to an empty string **""**, the binding relationship is cleared. The value can be dynamically changed to refresh the binding relationship. One ID can be bound to only two components, which function as in and out components.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: two components bound to the shared element. The parameter type is 1 or 0. By default, the out component does not continue to participate in the shared element animation when not yet deleted, which means that it stays in its original position.<br> .string: ID used to set up a binding relationship. If this attribute is set to an empty string **""**, the binding relationship is cleared. The value can be dynamically changed to refresh the binding relationship. One ID can be bound to only two components, which function as in and out components.|
| NODE_RELATIVE_LAYOUT_CHAIN_MODE = 76 | Sets the parameters of the chain in which the component is the head. This attribute can be set, reset, and obtained as required through APIs. This attribute has effect only when the parent container is **RelativeContainer**.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: direction of the chain. The value is an enumerated value of [ArkUI_Axis](capi-native-type-h.md#arkui_axis).<br> .value[1].i32: style of the chain. The value is an enumerated value of [ArkUI_RelativeLayoutChainStyle](capi-native-type-h.md#arkui_relativelayoutchainstyle).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].i32: direction of the chain. The value is an enumerated value of [ArkUI_Axis](capi-native-type-h.md#arkui_axis).<br> .value[1].i32: style of the chain. The value is an enumerated value of [ArkUI_RelativeLayoutChainStyle](capi-native-type-h.md#arkui_relativelayoutchainstyle).|
| NODE_RENDER_FIT = 77 | Sets how the final state of the component's content is rendered during its width and height animation process. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: how the final state of the component's content is rendered. The value is an enumerated value of [ArkUI_RenderFit](capi-native-type-h.md#arkui_renderfit).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: how the final state of the component's content is rendered. The value is an enumerated value of [ArkUI_RenderFit](capi-native-type-h.md#arkui_renderfit).|
| NODE_OUTLINE_COLOR = 78 | Defines the border color attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].u32: color of the four borders, in 0xARGB format, for example, **0xFFFF11FF**.<br> 2: .value[0].u32: color of the top border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[1].u32: color of the right border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[2].u32: color of the lower border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[3].u32: color of the left border, in 0xARGB format, for example, **0xFFFF11FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the top border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[1].u32: color of the right border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[2].u32: color of the lower border, in 0xARGB format, for example, **0xFFFF11FF**.<br> .value[3].u32: color of the left border, in 0xARGB format, for example, **0xFFFF11FF**.|
| NODE_SIZE = 79 | Sets the size. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width, in vp.<br> .value[1].f32: height, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width, in vp.<br> .value[1].f32: height, in vp.|
| NODE_RENDER_GROUP = 80 | Sets whether the component and its child components are rendered off the screen and then drawn together with its parent. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the component and its child components are rendered off the screen and then drawn together with its parent. The value **1** means that the component and its child components are rendered off the screen and then drawn together with its parent, and **0** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the component and its child components are rendered off the screen and then drawn together with its parent. The value **1** means that the component and its child components are rendered off the screen and then drawn together with its parent, and **0** means the opposite.|
| NODE_COLOR_BLEND = 81 | Applies a color blend effect to the component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color to blend with the component, in 0xARGB format, for example, **0xFFFF11FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color to blend with the component, in 0xARGB format, for example, **0xFFFF11FF**. |
| NODE_FOREGROUND_BLUR_STYLE = 82 | Applies a foreground blur style to the component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: foreground blur style. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).<br> .value[1]?.i32: color mode used for the foreground blur. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).<br> .value[2]?.i32: adaptive color mode used for the foreground blur. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).<br> .value[3]?.f32: blur degree. The value range is [0.0, 1.0].<br> .value[4]?.i32: brightness of black in the grayscale blur. The value range is [0, 127].<br> .value[5]?.i32: degree of darkening the white color in the grayscale blur. The value range is [0, 127].<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: foreground blur style. The value is an enumerated value of [ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle).<br> .value[1].i32: color mode used for the foreground blur. The value is an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).<br> .value[2].i32: adaptive color mode used for the foreground blur. The value is an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).<br> .value[3].f32: blur degree. The value range is [0.0, 1.0].<br> .value[4].i32: brightness of black in the grayscale blur. The value range is [0, 127].<br> .value[5].i32: degree of darkening the white color in the grayscale blur. The value range is [0, 127].|
| NODE_LAYOUT_RECT = 83 | Defines the component size and position for layout. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: X coordinate of the component, in px. <br> .value[1].i32: Y coordinate of the component, in px. <br> .value[2].i32: width of the component, in px. <br> .value[3].i32: height of the component, in px. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: X coordinate of the component, in px. <br> .value[1].i32: Y coordinate of the component, in px. <br> .value[2].i32: width of the component, in px. <br> .value[3].i32: height of the component, in px. |
| NODE_FOCUS_ON_TOUCH = 84 | Sets whether the component is focusable on touch. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the component is focusable on touch. The value **1** means that the component is focusable on touch, and **0** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the component is focusable on touch. The value **1** means that the component is focusable on touch, and **0** means the opposite.|
| NODE_BORDER_WIDTH_PERCENT = 85 | Defines the border width attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].f32: width of the four borders, in percentage.<br> 2: .value[0].f32: width of the top border, in percentage.<br> .value[1].f32: width of the right border, in percentage.<br> .value[2].f32: width of the bottom border, in percentage.<br> .value[3].f32: width of the left border, in percentage.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width of the top border, in percentage.<br> .value[1].f32: width of the right border, in percentage.<br> .value[2].f32: width of the bottom border, in percentage.<br> .value[3].f32: width of the left border, in percentage. |
| NODE_BORDER_RADIUS_PERCENT = 86 | Defines the border corner radius attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> 1: .value[0].f32: radius of the four corners, in percentage.<br> 2: .value[0].f32: radius of the upper left corner, in percentage.<br> .value[1].f32: radius of the upper right corner, in percentage.<br> .value[2].f32: radius of the lower left corner, in percentage.<br> .value[3].f32: radius of the lower right corner, in percentage.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: radius of the upper left corner, in percentage.<br> .value[1].f32: radius of the upper right corner, in percentage.<br> .value[2].f32: radius of the lower left corner, in percentage.<br> .value[3].f32: radius of the lower right corner, in percentage. |
| NODE_ACCESSIBILITY_ID = 87 | Sets the custom accessibility ID. This attribute can be obtained. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: custom accessibility ID.|
| NODE_ACCESSIBILITY_ACTIONS = 88 | Sets the accessibility action type. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: accessibility action type. The parameter type is [ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: accessibility action type. The parameter type is [ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype).|
| NODE_ACCESSIBILITY_ROLE = 89 | Defines the accessibility component role. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: accessibility component role. The parameter type is [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: accessibility component role. The parameter type is [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype).|
| NODE_ACCESSIBILITY_STATE = 90 | Sets the accessibility state. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: accessibility state. The parameter type is [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: accessibility state. The parameter type is [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md). |
| NODE_ACCESSIBILITY_VALUE = 91 | Sets the accessibility value. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: accessibility value. The parameter type is [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: accessibility value. The parameter type is [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md).|
| NODE_EXPAND_SAFE_AREA = 92 | Sets the safe area to be expanded to. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.u32: types of the expanded safe area, which are enumerated values of [ArkUI_SafeAreaType](capi-native-type-h.md#arkui_safeareatype). Example: ARKUI_SAFE_AREA_TYPE_SYSTEM \| ARKUI_SAFE_AREA_TYPE_CUTOUT.<br> .value[1]?.u32: edges for expanding the safe area, which are enumerated values of [ArkUI_SafeAreaEdge](capi-native-type-h.md#arkui_safeareaedge). Example: ARKUI_SAFE_AREA_EDGE_TOP \| ARKUI_SAFE_AREA_EDGE_BOTTOM.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].u32: expanded safe area.<br>.value[1].u32: edges for expanding the safe area.|
| NODE_VISIBLE_AREA_CHANGE_RATIO = 93 | Defines the visible area ratio (visible area/total area of the component) threshold for invoking the visible area change event of the component. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[...].f32: threshold array. The value ranges from 0 to 1.<br> .object: The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).<br>**Since**: 22<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[...].f32: threshold array.<br>.object: The return type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).<br>**Since**: 22|
| NODE_TRANSITION = 94 | Sets the transition effect when the component is inserted or deleted. This attribute can be set and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: transition effect. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: transition effect. The parameter type is [ArkUI_TransitionEffect](capi-arkui-nativemodule-arkui-transitioneffect.md). |
| NODE_UNIQUE_ID<sup>(deprecated)</sup> &nbsp;= 95 | Defines the component ID. This attribute can be obtained through APIs.<br>The component ID is read-only and unique in a process.<br>This API is sudpported since API version 12 and deprecated since API version 20. You are advised to use [OH_ArkUI_NodeUtils_GetNodeUniqueId](#oh_arkui_nodeutils_getnodeuniqueid) instead.|
| NODE_FOCUS_BOX = 96 | Sets the style of the system focus box for this component.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: distance between the focus box and the edge of the component<br> A positive number indicates the outside, and a negative number indicates the inside.<br> The value cannot be in percentage.<br> .value[1].f32: width of the focus box. Negative numbers and percentages are not supported.<br> .value[2].u32: color of the focus box.|
| NODE_CLICK_DISTANCE = 97 | Defines the moving distance limit for the component-bound tap gesture. This attribute can be set as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: allowed moving distance of a finger, in vp. |
| NODE_TAB_STOP = 98 | Sets whether the focus can be placed on this component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the focus can be placed on the current component. The value **1** means that the focus can be placed on the current component, and **0** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the focus can be placed on the current component. The value **1** means that the focus can be placed on the current component, and **0** means the opposite.<br>**Since**: 14 |
| NODE_BACKDROP_BLUR = 99 | Sets the background blur effect. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: background blur radius. The value range is [0, +∞). The unit is px. The default value is **0.0**.<br> .value[1]?.f32: brightness of black in the grayscale blur. The value range is [0, 127].<br> .value[2]?.f32: degree of darkening the white color in the grayscale blur. The value range is [0, 127].<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: background blur radius. The value range is [0, +∞). The unit is px.<br> .value[1].f32: brightness of black in the grayscale blur. The value range is [0, 127].<br> .value[2].f32: degree of darkening the white color in the grayscale blur. The value range is [0, 127].<br>**Since**: 15|
| NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE = 100 | Sets the resizable attribute of a background image when it is stretched. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: pixel value of the image that remains unchanged when the left side of the image is stretched, in vp.<br> .value[1].f32: pixel value of the image that remains unchanged when the top side of the image is stretched, in vp.<br> .value[2].f32: pixel value of the image that remains unchanged when the right side of the image is stretched, in vp.<br> .value[3].f32: pixel value of the image that remains unchanged when the bottom side of the image is stretched, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: pixel value of the image that remains unchanged when the left side of the image is stretched, in vp.<br> .value[1].f32: pixel value of the image that remains unchanged when the top side of the image is stretched, in vp.<br> .value[2].f32: pixel value of the image that remains unchanged when the right side of the image is stretched, in vp.<br> .value[3].f32: pixel value of the image that remains unchanged when the bottom side of the image is stretched, in vp.<br>**Since**: 19|
| NODE_NEXT_FOCUS = 101 | Sets the next focus node. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: focus movement direction, as defined in [ArkUI_FocusMove](capi-native-type-h.md#arkui_focusmove). .object: next focus node. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).<br>**Since**: 18|
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO = 102 | Sets the threshold ratio for triggering a visible area change event.<br>Note: The visible area change callback is not a real-time callback. The actual callback interval may differ from the expected interval due to system load and other factors. The interval between two visible area change callbacks will not be less than the expected update interval. If the provided expected interval is too short, the actual callback interval will be determined by the system load. By default, the interval threshold of the visible area change callback includes 0. This means that, if the provided threshold is [0.5], the effective threshold will be [0.0, 0.5].<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).<br>**Since**: 17 |
| NODE_TRANSLATE_WITH_PERCENT = 103 | Sets component translation, with support for percentage-based translation parameters. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: translation distance along the x-axis. The default unit is percentage, unless **value[3]** exists and is **0** (then the unit is vp). The default value is **0**.<br> .value[1].f32: translation distance along the y-axis. The default unit is percentage, unless **value[4]** exists and is **0** (then the unit is vp). The default value is **0**.<br> .value[2].f32: translation distance along the z-axis, in vp. The default value is **0**.<br> .value[3]?.i32: whether the x-axis movement distance is in percentage format. Valid values: 0 or 1. The value **1** means percentage format (for example, value[0].f32=0.1 and value[3].i32=1 translates 10% along the x-axis). The default value is **1**.<br> .value[4]?.i32: whether the y-axis movement distance is in percentage. Valid values: 0 or 1. The value **1** means percentage format (for example, value[1].f32=0.1 and value[4].i32=1 translates 10% along the y-axis). The default value is **1**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: translation distance along the X-axis. The unit depends on **value[3]**.<br> .value[1].f32: translation distance along the y-axis. The unit depends on **value[4]**.<br> .value[2].f32: translation distance along the z-axis, in vp.<br> .value[3].i32: whether the unit of x-axis movement distance is percentage. When **value[3].i32** is **0**, the unit of x-axis movement distance is vp; when **value[3].i32** is **1**, the unit is percentage.<br> .value[4].i32: whether the unit of y-axis movement distance is percentage. When **value[4].i32** is **0**, the unit of y-axis movement distance is vp; when **value[4].i32** is **1**, the unit is percentage.<br>**Since**: 20 |
| NODE_ROTATE_ANGLE = 104 | Sets component rotation with multi-axis angle control. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: x-axis rotation angle. The default value is **0**.<br> .value[1].f32: y-axis rotation angle. The default value is **0**.<br> .value[2].f32: z-axis rotation angle. The default value is **0**.<br> .value[3].f32: perspective distance from the viewpoint to the z=0 plane, in vp. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: x-axis rotation angle. The default value is **0**.<br> .value[1].f32: y-axis rotation angle. The default value is **0**.<br> .value[2].f32: z-axis rotation angle. The default value is **0**.<br> .value[3].f32: perspective distance from the viewpoint to the z=0 plane, in vp. The default value is **0**.<br>**Since**: 20 |
|NODE_WIDTH_LAYOUTPOLICY = 105|Sets the width layout policy of a component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: layout policy. The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy).<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].i32: layout policy. The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy).<br>**Since**: 21|
|NODE_HEIGHT_LAYOUTPOLICY = 106|Sets the height layout policy of a component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: layout policy. The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy).<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].i32: layout policy. The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy).<br>**Since**: 21|
|NODE_POSITION_EDGES = 107|Sets the position of a component relative to the boundaries of the container's content area. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: position of the component relative to the boundaries of the container's content area. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: position of the component relative to the boundaries of the container's content area. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).<br>**Since**: 21|
|NODE_ALLOW_FORCE_DARK = 108|Sets whether to enable color inversion of a component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable color inversion. The value can be **0** (no) or **1** (yes).<br>**Since**: 21|
|NODE_PIXEL_ROUND = 109|Sets the pixel rounding policy of a component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.object: pixel rounding policy of the component. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.object: pixel rounding policy of the component. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).<br>**Since**: 21|
|NODE_MOTION_PATH = 111 | Sets the motion path of the component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.object: pointer to the motion path configuration item of the path animation. The parameter type is [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.object: pointer to the motion path configuration item of the path animation. The parameter type is [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).<br>**Since**: 23|
|NODE_HOVER_EFFECT = 112|Defines the hover effect applied when the component is hovered over. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: hover effect applied when the component is hovered over. The parameter type is [ArkUI_HoverEffect](capi-native-type-h.md#arkui_hovereffect). The default value is **ARKUI_HOVER_EFFECT_AUTO**.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].i32: hover effect applied when the component is hovered over. The parameter type is [ArkUI_HoverEffect](capi-native-type-h.md#arkui_hovereffect).<br>**Since**: 23|
|NODE_FOCUS_SCOPE_ID = 113|Configures the container as a focus group with the specified identifier. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.string: focus scope identifier.<br> .value[0].i32: whether the scope is a focus group. The default value is **0**. The value can be **1** or **0**. The value **1** indicates that the component is set as a focus group. The value **0** indicates that the component is not set as a focus group.<br> .value[1].i32: whether arrow keys can move focus from inside the focus group to outside. This setting only takes effect when **isGroup** is **true**. The default value is **1**. The value can be **1** or **0**. The value **1** indicates that arrow keys can move focus from inside the focus group to outside, and the value **0** indicates that arrow keys cannot move focus from inside the focus group to outside.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.string: focus scope identifier.<br> .value[0].i32: whether the scope is a focus group. The default value is **0**. The value can be **1** or **0**. The value **1** indicates that the component is set as a focus group. The value **0** indicates that the component is not set as a focus group.<br> .value[1].i32: whether arrow keys can move focus from inside the focus group to outside. This setting only takes effect when **isGroup** is **true**. The default value is **1**. The value can be **1** or **0**. The value **1** indicates that arrow keys can move focus from inside the focus group to outside, and the value **0** indicates that arrow keys cannot move focus from inside the focus group to outside.<br>**Since**: 23|
|NODE_FOCUS_SCOPE_PRIORITY = 114|Sets the component focus priority within a specific focus scope. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.string: focus scope identifier.<br> .value[0].i32: focus priority within the focus scope. The parameter type is [ArkUI_FocusPriority](capi-native-type-h.md#arkui_focuspriority). The default value is **ARKUI_FOCUS_PRIORITY_AUTO**.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.string: focus scope identifier.<br> .value[0].i32:  focus scope priority. The parameter type is [ArkUI_FocusPriority](capi-native-type-h.md#arkui_focuspriority).<br>**Since**: 23|
|NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD = 115|Sets the distance threshold for click events. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: movement threshold for click events. Value range: (0, +∞) Default value: **+∞**.<br>Unit: vp.<br><br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].f32: movement threshold for click events.<br>**Since**: 23|
| NODE_RESPONSE_REGION_LIST = 116 | Defines the component event response region. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .data[0].i32: event tool type for the response region. The parameter type is [ArkUI_ResponseRegionSupportedTool](capi-native-type-h.md#arkui_responseregionsupportedtool). Default value: **ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL**.<br> .data[1].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.<br> .data[2].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.<br> .data[3].f32: width of the response region, in percentage. The default value is **100.0**.<br> .data[4].f32: height of the response region, in percentage. The default value is **100.0**.<br> .data[5...].f32: additional response regions in the same parameter order.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .data[0].i32: event tool type for the response region. The parameter type is [ArkUI_ResponseRegionSupportedTool](capi-native-type-h.md#arkui_responseregionsupportedtool). Default value: **ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL**.<br> .data[1].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.<br> .data[2].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.<br> .data[3].f32: width of the response region, in percentage. The default value is **100.0**.<br> .data[4].f32: height of the response region, in percentage. The default value is **100.0**.<br> .data[5...].f32: additional response regions in the same parameter order.<br>Note: During configuration, the data array can contain any number of values (all will be accepted), but only 20 values can be retrieved. The order of the retrieved data array may be different from that of the settings.<br>**Since**: 23 |
|NODE_MONOPOLIZE_EVENTS = 117|Defines the event monopolization attribute. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: The value can be **1** or **0**. The value **1** indicates that the component exclusively handles events. The value **0** indicates that the component does not exclusively handle events.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].i32: The value can be **1** or **0**. The value **1** indicates that the component exclusively handles events. The value **0** indicates that the component does not exclusively handle events.<br>**Since**: 23|
|NODE_CHAIN_WEIGHT = 118|Sets the layout location of components that have formed a chain when the parent component is **RelativeContainer**. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: layout weight of the component in the horizontal direction. The default value is **0**.<br> If an invalid value is set, the default value is used.<br> .value[1].f32: layout weight of the component in the vertical direction. The default value is **0**.<br> If an invalid value is set, the default value is used.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: layout weight of the component in the horizontal direction.<br> .value[0].f32: layout weight of the component in the vertical direction.<br>**Since**: 23|
|NODE_IGNORE_LAYOUT_SAFE_AREA = 119|Defines the safe area to be ignored when extending the layout of a component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: type for expanding the safe area. The parameter type is [ArkUI_LayoutSafeAreaType](capi-native-type-h.md#arkui_layoutsafeareatype). The default value is **ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM**.<br> If an invalid value is set, the default value is used.<br> .value[1].u32: edges for expanding the safe area. The parameter type is [ArkUI_LayoutSafeAreaEdge](capi-native-type-h.md#arkui_layoutsafeareaedge). The default value is **ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL**, for example, ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM.<br> If an invalid value is set, the default value is used.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].u32: type for expanding the safe area.<br>.value[1].u32: edges for expanding the safe area.<br>**Since**: 23|
| NODE_DASH_WIDTH  = 120| Sets the length of the dashed line when the border style is set to dashed. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: length of the top border, in vp.<br>.value[1].f32: length of the right border, in vp.<br>.value[2].f32: length of the bottom border, in vp.<br>.value[3].f32: length of the left border, in vp.<br> Value range: [0, +∞).<br> If an abnormal value is set, the default dashed line effect is displayed.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: length of the top border, in vp.<br>.value[1].f32: length of the right border, in vp.<br>.value[2].f32: length of the bottom border, in vp.<br>.value[3].f32: length of the left border, in vp.<br>**Since**: 23|
| NODE_DASH_GAP = 121| Sets the gap between dashes on the dashed line when the border style is set to dashed. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: gap between dashes on the top border, in vp.<br>.value[1].f32: gap between dashes on the right border, in vp.<br>.value[2].f32: gap between dashes on the bottom border, in vp.<br>.value[3].f32: gap between dashes on the left border, in vp.<br> Value range: [0, +∞).<br> If an abnormal value is set, the default dashed line effect is displayed.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: gap between dashes on the top border, in vp.<br>.value[1].f32: gap between dashes on the right border, in vp.<br>.value[2].f32: gap between dashes on the bottom border, in vp.<br>.value[3].f32: gap between dashes on the left border, in vp.<br>**Since**: 23|
|NODE_LAYOUT_GRAVITY = 122|Defines the alignment rule of the child components in the Stack container. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment rules of child components in a **Stack** container. The parameter type is [ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment). The default value is **ARKUI_ALIGNMENT_CENTER**.<br> If an invalid value is set, the default value is used.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment rules of child components in a **Stack** container. The parameter type is [ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment).<br>**Since**: 23|
|NODE_BORDER_RADIUS_TYPE = 123|Sets the mode for drawing rounded corners of a component. This API supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: mode for drawing rounded corners. The parameter type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy). The default value is **ARKUI_RENDERSTRATEGY_FAST**.<br> If an invalid value is set, the default value is used.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: mode for drawing rounded corners. The parameter type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy).<br>**Since**: 23|
| NODE_TEXT_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT = 1000 | Defines the text content attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: text content.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: text content.|
| NODE_FONT_COLOR = 1001 | Defines the font color attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: font color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: font color value, in 0xARGB format.|
| NODE_FONT_SIZE = 1002 | Defines the font size attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: font size, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: font size, in fp.|
| NODE_FONT_STYLE = 1003 | Defines the font style attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).|
| NODE_FONT_WEIGHT = 1004 | Defines the font weight attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|
| NODE_TEXT_LINE_HEIGHT = 1005 | Defines the text line height attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: line height, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: line height, in fp.|
| NODE_TEXT_DECORATION = 1006 | This attribute is used to set the style and color of the text decoration line. It supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype). The default value is **ARKUI_TEXT_DECORATION_TYPE_NONE**.<br> .value[1]?.u32: text decoration color, in 0xARGB format. For example, 0xFFFF0000 indicates red. Optional. <br> .value[2]?.i32: text decoration style [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle).<br> .value[3]?.f32: (optional) thickness ratio of the text decoration line. The default value is 1.0. The value range is [0, +∞). This parameter is supported since API version 22.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype).<br> .value[1].u32: text decoration color, in 0xARGB format.<br> .value[2].i32: text decoration style [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle).<br> .value[3].f32: scale factor of the text decoration thickness. This return value is supported since API version 22.|
| NODE_TEXT_CASE = 1007 | Defines the text case attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text case [ArkUI_TextCase](capi-native-type-h.md#arkui_textcase). The default value is **ARKUI_TEXT_CASE_NORMAL**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text case [ArkUI_TextCase](capi-native-type-h.md#arkui_textcase). |
| NODE_TEXT_LETTER_SPACING = 1008 | Defines the letter spacing attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: letter spacing, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: letter spacing, in fp. |
| NODE_TEXT_MAX_LINES = 1009 | Sets the maximum number of lines in the text. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: maximum number of lines in the text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: maximum number of lines in the text. |
| NODE_TEXT_ALIGN = 1010 | Defines the horizontal alignment mode of the text. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: horizontal alignment mode of the text. The value is an enumerated value of [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment). The default value is **ARKUI_TEXT_ALIGNMENT_START**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: horizontal alignment mode of the text. The value is an enumerated value of [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment).|
| NODE_TEXT_OVERFLOW = 1011 | Defines the text overflow attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: display mode when the text is too long, specified using [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow). The default value is **ARKUI_TEXT_OVERFLOW_NONE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: display mode when the text is too long.[ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow)|
| NODE_FONT_FAMILY = 1012 | Defines the font family attribute, which can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: fonts, separated by commas (,).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: fonts, separated by commas (,).|
| NODE_TEXT_COPY_OPTION = 1013 | Defines the copy option attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: copy option [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions). The default value is **ARKUI_COPY_OPTIONS_NONE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: copy option [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions).|
| NODE_TEXT_BASELINE_OFFSET = 1014 | Defines the text baseline offset attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: baseline offset, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: baseline offset, in fp.|
| NODE_TEXT_TEXT_SHADOW = 1015 | Defines the shadow attribute. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: blur radius of the shadow, in vp.<br> .value[1].i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is **ARKUI_SHADOW_TYPE_COLOR**.<br> .value[2].u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> .value[3].f32: offset of the shadow along the x-axis, in vp.<br> .value[4].f32: offset of the shadow along the y-axis, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: blur radius of the shadow, in vp.<br> .value[1].i32: shadow type [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype).<br> .value[2].u32: shadow color, in 0xARGB format.<br> .value[3].f32: offset of the shadow along the x-axis, in vp.<br> .value[4].f32: offset of the shadow along the y-axis, in vp.|
| NODE_TEXT_MIN_FONT_SIZE = 1016 | Defines the minimum font size attribute, which can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum font size, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum font size, in fp. |
| NODE_TEXT_MAX_FONT_SIZE = 1017 | Defines the maximum font size attribute, which can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum font size, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum font size, in fp. |
| NODE_TEXT_FONT = 1018 | Defines the text style attribute, which can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string?: font family. Optional. Use commas (,) to separate multiple fonts.<br> .value[0].f32: font size, in fp.<br> .value[1]? .i32: font weight. Optional. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.<br> .value[2]?.i32: font style. Optional. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: font family. Use commas (,) to separate multiple fonts.<br> .value[0].f32: font size, in fp.<br> .value[1] .i32: font weight. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.<br> .value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**.|
| NODE_TEXT_HEIGHT_ADAPTIVE_POLICY = 1019 | Defines how the adaptive height is determined for the text. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: how the adaptive height is determined for the text. The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-native-type-h.md#arkui_textheightadaptivepolicy). The default value is **ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: how the adaptive height is determined for the text. The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-native-type-h.md#arkui_textheightadaptivepolicy).|
| NODE_TEXT_INDENT = 1020 | Defines the indentation of the first line. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: indentation of the first line, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: indentation of the first line, in vp.<br>|
| NODE_TEXT_WORD_BREAK = 1021 | Defines the line break rule. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: line break rule. The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak). The default value is **ARKUI_WORD_BREAK_BREAK_WORD**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: line break rule. The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak).|
| NODE_TEXT_ELLIPSIS_MODE = 1022 | Defines the ellipsis position. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode). The default value is **ARKUI_ELLIPSIS_MODE_END**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode). |
| NODE_TEXT_LINE_SPACING = 1023 | Defines the line spacing attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: line spacing, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: line spacing, in fp. |
| NODE_FONT_FEATURE = 1024 | Sets the font feature. **NODE_FONT_FEATURE** provides advanced typographic features in OpenType fonts. These features such as hyphenation and monospace are generally used in custom fonts and require support from the respective fonts. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: string that describes the font feature settings. The value format is normal \|  \<feature-tag-value>.<br>  Syntax for \<feature-tag-value>: <string\>  [ <integer\>  \| on  \| off ], <br>  There can be multiple **\<feature-tag-value>** values, separated by commas (,). For example, for the monospace feature, you can pass in **ss01 on**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: font feature. Multiple font features are separated by commas (,).<br>|
| NODE_TEXT_ENABLE_DATA_DETECTOR = 1025 | Sets whether to enable text recognition.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable text recognition. The default value is **false**. The value **true** means to enable text recognition, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable text recognition.|
| NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG = 1026 | Configures text recognition settings.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0...].i32: array of entity types. The parameter type is [ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0...].i32: array of entity types. The parameter type is [ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype). |
| NODE_TEXT_SELECTED_BACKGROUND_COLOR = 1027 | Defines the background color of the selected text. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format.|
| NODE_TEXT_CONTENT_WITH_STYLED_STRING = 1028 | Sets the string to use in the styled string. This attribute can be set, reset, and obtained as required through APIs. Configuring a custom **OH_Drawing_Typography** object for the **Text** component will skip the layout measurement phase of the component. Note the following:<br> 1. Ensure that the lifecycles of the** OH_ArkUI_StyledString** object and **OH_Drawing_Typography** object are aligned with the lifecycle of the **Text** component. Reset the **OH_ArkUI_StyledString** object when the **Text** component is destroyed; otherwise, it may lead to null pointer crashes in the application.<br> 2. Ensure that the **OH_Drawing_TypographyLayout** API is called prior to the layout measurement of the **Text** component.<br> 3. When the **OH_ArkUI_StyledString** and **OH_Drawing_Typography** objects are released, the **reset** API of the **Text** component must be called synchronously; otherwise, it may cause null pointer crashes in the application.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: string to use in the styled string. The parameter type is [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: string to use in the styled string. The parameter type is [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md).|
| NODE_TEXT_HALF_LEADING = 1029 | Sets whether to center text vertically in the **Text** component.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to center text vertically. The default value is **false**.<br>The value **true** means to center text vertically, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to center text vertically.|
| NODE_IMMUTABLE_FONT_WEIGHT = 1030 | Defines the font weight attribute, which can be set, reset, and obtained as required through APIs. The font weight specified by this API is not affected by any changes in the system font weight settings.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).<br>**Since**: 15 |
| NODE_TEXT_LINE_COUNT = 1031 | Sets the number of lines in the text. This attribute can be obtained through APIs. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of text lines.<br>**Since**: 20 |
| NODE_TEXT_OPTIMIZE_TRAILING_SPACE = 1032 | Sets whether to optimize the trailing spaces at the end of each line during text layout. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to optimize trailing spaces at the end of each line during text layout. The default value is **false**.<br>The value **true** means to optimize trailing spaces at the end of each line during text layout, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to optimize trailing spaces at the end of each line during text layout.<br>**Since**: 20 |
| NODE_TEXT_LINEAR_GRADIENT = 1033 | Sets a linear gradient effect for text. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: start angle of the linear gradient. The setting takes effect only when **direction** is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**. A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is **180**.<br> .value[1].i32: direction of the linear gradient [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection). When a direction other than **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM** is set, the **angle** property is ignored. Default value: **ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM**.<br> .value[2].i32: whether the colors are repeated. The value **true** means that the colors are repeated, and **false** means the opposite. Default value: **false**.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value.<br> **size**: number of colors. If the value is smaller than the length of the **colors** array, only the first **size** colors take effect. Values greater than the **colors** array length, values less than or equal to 0, or invalid values are not recommended.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: start angle of the linear gradient. The set value is used only when **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM** is used. In other cases, the default value **0** is used.<br> .value[1].i32: direction of the linear gradient [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection).<br> .value[2].i32: whether the colors are repeated. The value **1** means that the colors are repeated, and **0** means the opposite. Default value: **0**.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end.<br> **size**: number of effective gradient colors.<br>**Since**: 20|
| NODE_TEXT_RADIAL_GRADIENT = 1034 | Sets a radial gradient effect for text. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: x-coordinate of the radial gradient center relative to the upper left corner of the text box.<br> .value[1]?.f32: y-coordinate of the radial gradient center relative to the upper left corner of the text box. The coordinates of the upper left corner of the text box are [0, 0].<br> .value[2]?.f32: radius of the radial gradient. The default value is **0**.<br> .value[3].i32: whether the colors are repeated. The value **true** means that the colors are repeated, and **false** means the opposite. Default value: **false**.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value.<br> **size**: number of colors. If the value is smaller than the length of the **colors** array, only the first **size** colors take effect. Values greater than the **colors** array length, values less than or equal to 0, or invalid values are not recommended.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0]?.f32: x-coordinate of the radial gradient center relative to the upper left corner of the text box.<br> .value[1]?.f32: y-coordinate of the radial gradient center relative to the upper left corner of the text box. The coordinates of the upper left corner of the text box are [0, 0].<br> .value[2]?.f32: radius of the radial gradient. The default value is **0**.<br> .value[3]?.i32: whether the colors are repeated. The value **1** means that the colors are repeated, and **0** means the opposite. Default value: **0**.<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> **colors**: colors of the color stops, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end.<br> **size**: number of effective gradient colors.<br>**Since**: 20 |
| NODE_TEXT_VERTICAL_ALIGN = 1035 | Sets the vertical alignment of the text content. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: vertical alignment of the text content, specified using the [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment) enum. The default value is **ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: vertical alignment of the text content, specified using the [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment) enum.<br>**Since**: 20  |
| NODE_TEXT_CONTENT_ALIGN = 1036 | Sets the vertical alignment of the text content area. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: vertical alignment of the text content area, specified using the [ArkUI_TextContentAlign](capi-native-type-h.md#arkui_textcontentalign) enum. The default value is **ARKUI_TEXT_CONTENT_ALIGN_CENTER**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: vertical alignment of the text content area, specified using the [ArkUI_TextContentAlign](capi-native-type-h.md#arkui_textcontentalign) enum.<br>**Since**: 21  |
| NODE_TEXT_MIN_LINES = 1037 | Sets the minimum number of lines in the text. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: minimum number of text lines.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: minimum number of text lines.<br>**Since**: 22    |
| NODE_TEXT_ENABLE_SELECTED_DATA_DETECTOR = 1038 | Whether to enable entity recognition for selected text.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable entity recognition for selected text. **true** indicates that entity recognition is enabled, and false indicates that entity recognition is disabled. Default value: **true**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable entity recognition for selected text.<br>**Since**: 22|
| NODE_TEXT_MIN_LINE_HEIGHT = 1040 | Minimum line height. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum line height of the text. The default value is **0**. The unit is fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum line height of the text. The unit is fp.<br>**Since**: 22  |
| NODE_TEXT_MAX_LINE_HEIGHT = 1041 | Maximum line height. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum line height of the text. The default value is **0**, indicating that the maximum line height is not limited. The unit is fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum line height of the text. The unit is fp.<br>**Since**: 22  |
| NODE_TEXT_LINE_HEIGHT_MULTIPLE = 1042 | Multiple value of the multiple line height mode. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: multiple of the line height in the multiple line height mode. The default value is 0, indicating that the default line height is used.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: scale factor of the line height mode.<br>**Since**: 22  |
| NODE_TEXT_LAYOUT_MANAGER = 1043 | Text layout manager, which supports the attribute obtaining API.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: text layout manager object. The parameter type is [ArkUI_LayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md).<br>**Since**: 22|
| NODE_TEXT_EDIT_MENU_OPTIONS = 1044 | Extended item of the text menu, which supports the attribute setting API.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: configuration data of the extended item of the text menu. The parameter type is [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md).<br>**Since**: 22|
| NODE_TEXT_BIND_SELECTION_MENU = 1045 | Customizes the text selection menu and supports the API for setting attributes.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: configuration data of the custom text selection menu. The parameter type is [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md).<br>**Since**: 22|
| NODE_TEXT_TEXT_SELECTION  = 1046 | Sets the text selection area. After the setting, the selected area will be highlighted. This API supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: start position of the selected text.<br> .value[1].i32: end position of the selected text.<br> .object: selection option. The parameter type is [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: start position of the text selection.<br> .value[1].i32: end position of the selected text.<br> .object: selection option. The parameter type is [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md).<br>**Since**: 23  |
| NODE_TEXT_COMPRESS_LEADING_PUNCTUATION = 1048 | Enables or disables the function of compressing punctuations at the beginning of a line. This API supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the function of compressing punctuations at the beginning of a line.<br> The value true indicates that the punctuation compression at the beginning of a line is enabled, and the value false indicates that the punctuation compression at the beginning of a line is disabled. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the punctuation compression at the beginning of a line.<br>**Since**: 23|
| NODE_TEXT_INCLUDE_FONT_PADDING = 1049 | Sets whether to add spacing to the first and last lines to avoid text truncation.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to add spacing to the first and last lines to avoid text truncation. The value true indicates that the spacing is added, and the value false indicates that the spacing is not added. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to add spacing to the first and last lines. The value true indicates that the spacing is added, and the value false indicates that the spacing is not added.<br>**Since**: 23|
| NODE_TEXT_FALLBACK_LINE_SPACING = 1050 | For multi-line text overlay, the line height can be automatically adjusted based on the actual text height. This API takes effect only when the line height is smaller than the actual text height.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to automatically adjust the line height based on the actual text height. The value true indicates that the auto-adaptation is enabled, and the value false indicates that the auto-adaptation is disabled. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the function of automatically adjusting the line height based on the actual text height. The value true indicates that the auto-adaptation is enabled, and the value false indicates that the auto-adaptation is disabled.<br>**Since**: 23|
| NODE_TEXT_MARQUEE_OPTIONS = 1051 | This API is used to configure the text marquee mode, and supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: text marquee mode configuration. The parameter type is [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: text marquee mode configuration. The parameter type is [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md).<br>**Since**: 23  |
| NODE_TEXT_DIRECTION  = 1052 | Text layout direction.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text layout direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). The default value is **ARKUI_TEXT_DIRECTION_DEFAULT**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text layout direction. For details about the values and meanings, see the enumerated values of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).<br>**Since**: 23|
| NODE_TEXT_SELECTED_DRAG_PREVIEW_STYLE = 1053 | Sets the drag preview style when the text is selected.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).<br>**Since**: 23|
| NODE_SPAN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SPAN = 2000 | Defines the text content attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: content of the text span.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: content of the text span. |
| NODE_SPAN_TEXT_BACKGROUND_STYLE = 2001 | Defines the text background style. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the text background, in 0xARGB format, for example, **0xFFFF0000** indicating red.<br> The second parameter is used to set the rounded corner of the text background. The options are as follows:<br> -.value[1].f32: radius of the four corners, in vp.<br> - .value[1].f32: radius of the upper left corner, in vp.<br> .value[2].f32: radius of the upper right corner, in vp.<br> .value[3].f32: radius of the lower left corner, in vp.<br> .value[4].f32: radius of the lower right corner, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the text background, in 0xARGB format.<br> .value[1].f32: radius of the upper left corner, in vp.<br> .value[2].f32: radius of the upper right corner, in vp.<br> .value[3].f32: radius of the lower left corner, in vp.<br> .value[4].f32: radius of the lower right corner, in vp.|
| NODE_SPAN_BASELINE_OFFSET = 2002 | Defines the text baseline offset attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: baseline offset, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: baseline offset, in fp. |
| NODE_IMAGE_SPAN_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_SPAN = 3000 | Defines the image source for an image span. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: image address of the image span.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: image address of the image span.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set.|
| NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT = 3001 | Defines the alignment mode of the image with the text. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode of the image with the text, specified using the [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment) enum.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode of the image with the text, specified using the [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment) enum. |
| NODE_IMAGE_SPAN_ALT = 3002 | Defines the image source for an image span. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: placeholder image address for the image span. GIF images are not supported.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: image source for the image span.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|
| NODE_IMAGE_SPAN_BASELINE_OFFSET = 3003 | Defines the baseline offset attribute of the **ImageSpan** component. This attribute can be set, reset, and obtained as required through APIs. A positive value means an upward offset, while a negative value means a downward offset. The default value is **0**, and the unit is fp.<br><br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: baseline offset, in fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: baseline offset, in fp.<br>**Since**: 13 |
| NODE_IMAGE_SPAN_COLOR_FILTER = 3004 | Defines the color filter of the image. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32 to .value[19].f32: filter matrix array.<br> .size: indicates that the size of the filter array is 5x4.<br> .object: color filter pointer. The parameter type is [OH_Drawing_ColorFilter](../apis-arkgraphics2d/capi-drawing-oh-drawing-colorfilter.md).<br>Either **.object** or **.size** must be set.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32 to .value[19].f32: filter matrix array.<br> .size: indicates that the size of the filter array is 5x4.<br> .object: color filter pointer. The parameter type is [OH_Drawing_ColorFilter](../apis-arkgraphics2d/capi-drawing-oh-drawing-colorfilter.md).<br> **Since**: 22|
| NODE_IMAGE_SPAN_SUPPORT_SVG2 = 3005 | Sets whether to enable the SVG parsing capability, which allows you to set the scope of SVG parsing functionality support. This attribute can be set, reset, and obtained as required through APIs. After the **ImageSpan** component is created, the value of this attribute cannot be dynamically changed.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the new SVG parsing capability. **true**: Enable enhanced SVG tag parsing. **false**: Use original SVG tag parsing.<br>Default value: **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the new SVG parsing capability.<br>**Since**: 22|
| NODE_IMAGE_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE = 4000 | Defines the image source of the **Image** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: image source.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: image address.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|
| NODE_IMAGE_OBJECT_FIT = 4001 | Defines how the image is resized to fit its container. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: how the image is resized to fit its container, specified using the [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit) enum.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: how the image is resized to fit its container, specified using the [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit) enum.|
| NODE_IMAGE_INTERPOLATION = 4002 | Defines the interpolation effect of the image. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: interpolation effect, specified using the [ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation) enum.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: interpolation effect, specified using the [ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation) enum. |
| NODE_IMAGE_OBJECT_REPEAT = 4003 | Defines how the image is repeated. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: how the image is repeated, specified using the [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat) enum.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: how the image is repeated, specified using the [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat) enum. |
| NODE_IMAGE_COLOR_FILTER = 4004 | Defines the color filter of the image. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32 to .value[19].f32: filter matrix array.<br> .size: 5 x 4 filter array size.<br> .object: pointer to the color filter. The parameter type is **OH_Drawing_ColorFilter**.<br>Either **.object** or **.size** must be set.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32 to .value[19].f32: filter matrix array.<br> .size: 5 x 4 filter array size.<br> .object: pointer to the color filter. The parameter type is **OH_Drawing_ColorFilter**. |
| NODE_IMAGE_AUTO_RESIZE = 4005 | Defines the auto resize attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable auto resizing. The default value is **false**. **true**: Enable auto resizing. **false**: Disable auto resizing.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32 : whether to resize the image.|
| NODE_IMAGE_ALT = 4006 | Defines the placeholder image attribute. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: address of the placeholder image.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set. Network images are not supported.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: image source for the image span.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|
| NODE_IMAGE_DRAGGABLE = 4007 | Defines whether the image is draggable. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the image is draggable. The value **true** means that the image is draggable.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the image is draggable.|
| NODE_IMAGE_RENDER_MODE = 4008 | Defines the image rendering mode. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: image rendering mode. The parameter type is [ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: image rendering mode. The parameter type is [ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode).|
| NODE_IMAGE_FIT_ORIGINAL_SIZE = 4009 | Sets whether the display size of an image follows the original size of the image source. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: indicates whether the display size of an image follows the original size of the image source. The value **1** indicates that the display size of an image follows the original size of the image source, and the value **0** indicates the opposite. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value **1** indicates that the display size of an image follows the original size of the image source, and **0** means the opposite.|
| NODE_IMAGE_FILL_COLOR = 4010 | Sets the fill color to be superimposed on the image. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: fill color. The value is in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: fill color. The value is in 0xARGB format.|
| NODE_IMAGE_RESIZABLE = 4011 | Sets the resizable image options.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: fixed distance (unchanged during stretching) from the left edge of the image. The unit is vp.<br> .value[1].f32: fixed distance (unchanged during stretching) from the top edge of the image. The unit is vp.<br> .value[2].f32: fixed distance (unchanged during stretching) from the right edge of the image. The unit is vp.<br> .value[3].f32: fixed distance (unchanged during stretching) from the bottom edge of the image. The unit is vp. When this attribute is used together with **NODE_IMAGE_ANTIALIASED**, the **NODE_IMAGE_ANTIALIASED** attribute setting does not take effect.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: fixed distance (unchanged during stretching) from the left edge of the image. The unit is vp.<br> .value[1].f32: fixed distance (unchanged during stretching) from the top edge of the image. The unit is vp.<br> .value[2].f32: fixed distance (unchanged during stretching) from the right edge of the image. The unit is vp.<br> .value[3].f32: fixed distance (unchanged during stretching) from the bottom edge of the image. The unit is vp.|
| NODE_IMAGE_SYNC_LOAD = 4012 | Defines the synchronous image loading attribute. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to load the image synchronously.. The default value is **false**. **true**: Load the image synchronously. **false**: Load the image asynchronously.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to load the image synchronously.<br>**Since**: 20 |
| NODE_IMAGE_SOURCE_SIZE = 4013 | Sets the decoding size of the image. This attribute works only when the target size is smaller than the source size. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: width for image decoding, in px.<br> .value[1].i32: height for image decoding, in px. If either parameter is set to a value less than or equal to 0, the attribute setting fails, and [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) is returned.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: width for image decoding, in px.<br> .value[1].i32: height for image decoding, in px.<br>**Since**: 21|
| NODE_IMAGE_IMAGE_MATRIX = 4014 | Sets the transformation matrix of the image. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0...15].f32: 4x4 matrix represented by a floating-point array of length 16. If the number of parameters is less than 16, the attribute setting fails, and [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) is returned. If the number of parameters exceeds 16, only the first 16 data entries are used.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0...15].f32: 4x4 matrix represented by a floating-point array of length 16.<br>**Since**: 21|
| NODE_IMAGE_MATCH_TEXT_DIRECTION = 4015 | Specifies whether the image follows the system language direction, displaying a mirrored effect in a right-to-left (RTL) language environments. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the image follows the system language direction. The default value is **false**. **true**: The image follows the system language direction. **false**: The image does not follow the system language direction.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the image follows the system language direction. **true**: The image follows the system language direction. **false**: The image does not follow the system language direction.<br>**Since**: 21|
| NODE_IMAGE_COPY_OPTION = 4016 | Sets the image copy mode. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: image copy mode, specified using the [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions) enum. The default value is **ARKUI_COPY_OPTIONS_NONE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: image copy mode, specified using the [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions) enum.<br>**Since**: 21|
| NODE_IMAGE_ENABLE_ANALYZER = 4017 | Sets whether to enable the AI image analyzer, which supports subject recognition, text recognition, and object lookup. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the AI image analyzer. The default value is **false**. **true**: Enable the AI image analyzer. **false**: Disable the AI image analyzer.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the AI image analyzer. **true**: Enable the AI image analyzer. **false**: Disable the AI image analyzer.<br>**Since**: 21|
| NODE_IMAGE_DYNAMIC_RANGE_MODE = 4018 | Defines the dynamic range attribute for image display, specifying the dynamic range mode for image rendering (for example, SDR/HDR). This attribute can be set, reset, and obtained as required through APIs. It is used to match the capabilities of the display device and ensure accurate presentation of image brightness and colors.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: dynamic range mode, specified using the [ArkUI_DynamicRangeMode](capi-native-type-h.md#arkui_dynamicrangemode) enum. The default value is **ARKUI_DYNAMIC_RANGE_MODE_STANDARD**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: dynamic range mode, specified using the [ArkUI_DynamicRangeMode](capi-native-type-h.md#arkui_dynamicrangemode) enum.<br>**Since**: 21|
| NODE_IMAGE_HDR_BRIGHTNESS = 4019 | Defines the brightness attribute of the image in HDR mode, used to control brightness parameters for high dynamic range display. This attribute can be set, reset, and obtained as required through APIs. It is used to ensure accurate presentation of details in the bright and dark areas of HDR images.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: brightness value. The value range is [0, 1]. Values less than 0 or greater than 1 are clamped to 1. **0**: The image is displayed at SDR brightness. **1**: The image is displayed at the highest allowed HDR brightness.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: brightness value. The value range is [0, 1].<br>**Since**: 21|
| NODE_IMAGE_ORIENTATION = 4020 | Sets the display orientation of the image content. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: expected display orientation of the image content, specified using the [ArkUI_Orientation](capi-native-type-h.md#arkui_imagerotateorientation) enum. The default value is **ARKUI_ORIENTATION_UP**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: expected display orientation of the image content, specified using the [ArkUI_Orientation](capi-native-type-h.md#arkui_imagerotateorientation) enum.<br>**Since**: 21|
| NODE_IMAGE_SUPPORT_SVG2 = 4021 | Sets whether to enable the SVG parsing capability, which allows you to set the scope of SVG parsing functionality support. This attribute can be set, reset, and obtained as required through APIs. After the **Image** component is created, the value of this attribute cannot be dynamically changed.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the new SVG parsing capability.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the new SVG parsing capability.<br>**Since**: 21|
| NODE_IMAGE_CONTENT_TRANSITION = 4022 | Sets the transition effect when the image changes. The APIs for setting, resetting, and obtaining attributes are supported.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: custom transition animation. The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: custom transition animation. The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).<br>**Since**: 21|
| NODE_IMAGE_ALT_PLACEHOLDER  = 4023 | Configures a placeholder image during the loading process. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: placeholder image address during the loading of the image component.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set. Network images are not supported.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: placeholder image address during the loading of the image component.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>**Since**: 22|
| NODE_IMAGE_ALT_ERROR  = 4024 | Configures a placeholder image in the loading failure scenarios. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: placeholder image address in the loading failure scenarios.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set. Network images are not supported.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: placeholder image address in the loading failure scenarios.<br> .object: **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>**Since**: 22|
| NODE_IMAGE_ANTIALIASED = 4025 | Supports the configuration of anti-aliasing at the edges of a bitmap image. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: indicates whether to enable anti-aliasing for the edges of a bitmap image. The default value is false. false indicates that anti-aliasing is disabled, and true indicates that anti-aliasing is enabled. This attribute does not take effect when used together with NODE_IMAGE_RESIZABLE.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: indicates whether to enable anti-aliasing for the edges of a bitmap image. false indicates that anti-aliasing is disabled, and true indicates that anti-aliasing is enabled.<br>**Since**: 23 |
| NODE_TOGGLE_SELECTED_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE = 5000 | Defines the color of the component when it is selected. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format.|
| NODE_TOGGLE_SWITCH_POINT_COLOR = 5001 | Defines the color of the circular thumb for the component of the switch type. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the circular thumb, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the circular thumb, in 0xARGB format.|
| NODE_TOGGLE_VALUE = 5002 | Defines the toggle switch value. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the toggle. The value **true** means to enable the toggle.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the toggle.|
| NODE_TOGGLE_UNSELECTED_COLOR = 5003 | Defines the color of the component when it is deselected. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format.|
| NODE_LOADING_PROGRESS_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LOADING_PROGRESS = 6000 | Defines the foreground color of the loading progress bar. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: foreground color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: foreground color, in 0xARGB format.|
| NODE_LOADING_PROGRESS_ENABLE_LOADING = 6001 | Defines whether to show the loading animation for the **LoadingProgress** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show the loading animation. The value **true** means to show the loading animation, and **false** means the opposite. The default value is true.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show the loading animation. The value **1** means to show the loading animation, and **0** means the opposite.|
| NODE_TEXT_INPUT_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT = 7000 | Defines the default placeholder text of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default placeholder text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default placeholder text.|
| NODE_TEXT_INPUT_TEXT = 7001 | Defines the default text of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default text.|
| NODE_TEXT_INPUT_CARET_COLOR = 7002 | Defines the border color attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: caret color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: caret color, in 0xARGB format. |
| NODE_TEXT_INPUT_CARET_STYLE = 7003 | Defines the caret style attribute. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: caret width, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: caret width, in vp.|
| NODE_TEXT_INPUT_SHOW_UNDERLINE = 7004 | Defines the underline attribute of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show an underline. The value **true** means to show an underline, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value **1** means to show an underline, and **0** means the opposite.|
| NODE_TEXT_INPUT_MAX_LENGTH = 7005 | Defines the maximum number of characters in the text input. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: maximum number of characters in the text input, without a unit.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: maximum number of characters in the text input.|
| NODE_TEXT_INPUT_ENTER_KEY_TYPE = 7006 | Defines the type of the Enter key. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of the Enter key, specified using the [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype) enum. The default value is **ARKUI_ENTER_KEY_TYPE_DONE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of the Enter key, specified using the [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype) enum.|
| NODE_TEXT_INPUT_PLACEHOLDER_COLOR = 7007 | Defines the placeholder text color. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format.|
| NODE_TEXT_INPUT_PLACEHOLDER_FONT = 7008 | Defines the placeholder text font. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: font size, in fp. Optional. The default value is **16.0**.<br> .value[1]?.i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**.<br> .value[2]?.i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.<br> ?.string: font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2".<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: font size, in fp.<br> .value[1].i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).<br> .value[2].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).<br> .string: font family. Multiple font families are separated by commas (,).|
| NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS = 7009 | Defines whether to enable the input method when the component obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the input method when the component obtains focus. The value **true** means to enable the input method, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the input method when the component obtains focus. The value **1** means to enable the input method when the component obtains focus, and **0** means the opposite.|
| NODE_TEXT_INPUT_TYPE = 7010 | Defines the text box type. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text box type, specified using the [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype) enum. The default value is **ARKUI_TEXTINPUT_TYPE_NORMAL**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text box type, specified using the [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype) enum.|
| NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR = 7011 | Defines the background color of the selected text. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format.|
| NODE_TEXT_INPUT_SHOW_PASSWORD_ICON = 7012 | Defines whether to display the password icon at the end of the password text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to display the password icon. **true** to display, **false** otherwise. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: The value **1** means to display the password icon at the end of the password text box, and **0** means the opposite.|
| NODE_TEXT_INPUT_EDITING = 7013 | Defines the editable state for the single-line text box. This attribute can be set as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to remain in the editable state. The value **true** means to remain in the editable state, and **false** means to exit the editable state.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for obtaining the attribute:<br> .value[0].i32: whether to remain in the editable state. The value **true** means to remain in the editable state, and **false** means to exit the editable state. |
| NODE_TEXT_INPUT_CANCEL_BUTTON = 7014 | Defines the style of the cancel button on the right of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: button style [ArkUI_CancelButtonStyle](capi-native-type-h.md#arkui_cancelbuttonstyle). The default value is **ARKUI_CANCELBUTTON_STYLE_INPUT**.<br> .value[1]?.f32: button icon size, in vp.<br> .value[2]?.u32: button icon color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> ?.string: button icon image address. The value is the local address of an image, for example, **/pages/icon.png**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: button style [ArkUI_CancelButtonStyle](capi-native-type-h.md#arkui_cancelbuttonstyle).<br> .value[1].f32: icon size, in vp.<br> .value[2].u32: button icon color, in 0xARGB format.<br> .string: button icon image source.|
| NODE_TEXT_INPUT_TEXT_SELECTION = 7015 | Sets the text selection area, which will be highlighted. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. |
| NODE_TEXT_INPUT_UNDERLINE_COLOR = 7016 | Sets the color of the underline when it is shown. The default underline color configured for the theme is **'0x33182431'**.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the underline applied to the text being typed in. The value is in 0xARGB format. <br> .value[1].u32: color of the underline applied to the text in the normal state. The value is in 0xARGB format. <br> .value[2].u32: color of the underline applied to the text when an error is detected. The value is in 0xARGB format. <br> .value[3].u32: color of the underline applied to the text when it is disabled. The value is in 0xARGB format. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the underline applied to the text being typed in. The value is in 0xARGB format. <br> .value[1].u32: color of the underline applied to the text in the normal state. The value is in 0xARGB format. <br> .value[2].u32: color of the underline applied to the text when an error is detected. The value is in 0xARGB format. <br> .value[3].u32: color of the underline applied to the text when it is disabled. The value is in 0xARGB format. |
| NODE_TEXT_INPUT_ENABLE_AUTO_FILL = 7017 | Sets whether to enable autofill.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable autofill. The default value is **true**.<br>**true**: Enable autofill. **false**: Disable autofill.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable autofill.|
| NODE_TEXT_INPUT_CONTENT_TYPE = 7018 | Sets the autofill type.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype).|
| NODE_TEXT_INPUT_PASSWORD_RULES = 7019 | Defines the rules for generating passwords. When autofill is used, these rules are transparently transmitted to Password Vault for generating a new password.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: rules for generating passwords.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: rules for generating passwords.|
| NODE_TEXT_INPUT_SELECT_ALL = 7020 | Sets whether to select all text in the initial state. This attribute is not available for the inline input style.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to select all text in the initial state. The default value is **false**.<br>**true**: Select all text in the initial state. **false**: Do not select all text in the initial state.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to select all text in the initial state.|
| NODE_TEXT_INPUT_INPUT_FILTER = 7021 | Sets the regular expression for input filtering. Only inputs that comply with the regular expression can be displayed. Other inputs are filtered out. For single-character input scenarios, only single-character matching is supported; for multi-character input scenarios (such as pasting), string matching is supported.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: regular expression.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: regular expression.|
| NODE_TEXT_INPUT_STYLE = 7022 | Sets the text box to the default style or inline input style. The inline input style is only available when [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_NORMAL**.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text input style. The parameter type is [ArkUI_TextInputStyle](capi-native-type-h.md#arkui_textinputstyle). The default value is **ARKUI_TEXTINPUT_STYLE_DEFAULT**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text input style. The parameter type is [ArkUI_TextInputStyle](capi-native-type-h.md#arkui_textinputstyle).|
| NODE_TEXT_INPUT_CARET_OFFSET = 7023 | Sets or obtains the caret position.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> Sets the position of the caret.<br> .value[0].i32: length from the start of the string to the position where the input cursor is located.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> Returns the position information of the caret. If this API is called when the caret position is updated in the current frame, it will not take effect.<br> .value[0].i32: index of the caret position.<br> .value[1].f32: x-coordinate of the caret relative to the text box.<br> .value[2].f32: y-coordinate of the caret relative to the text box.|
| NODE_TEXT_INPUT_CONTENT_RECT = 7024 | Obtains the position of the edited text area relative to the component and its size. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: horizontal coordinate.<br> .value[1].f32: vertical coordinate.<br> .value[2].f32: content width.<br> .value[3].f32: content height.|
| NODE_TEXT_INPUT_CONTENT_LINE_COUNT = 7025 | Obtains the number of lines of the edited text. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: number of lines in the edited text.|
| NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN = 7026 | Sets whether to hide the text selection menu when the text box is long-pressed, double-clicked, or right-clicked. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-clicked, or right-clicked. The default value is **false**.<br>**true**: The system text selection menu is hidden under the following circumstances: clicking the text box cursor, long-pressing the text box, double-tapping the text box, triple-tapping the text box, or right-clicking the text box.<br>**false**: The system text selection menu is displayed under the following circumstances: clicking the text box cursor, long-pressing the text box, double-tapping the text box, triple-tapping the text box, or right-clicking the text box.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-clicked, or right-clicked.|
| NODE_TEXT_INPUT_BLUR_ON_SUBMIT = 7027 | Sets whether the text box loses focus after the **Enter** key is pressed to submit information.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the text box loses focus after the Enter key is pressed to submit information. The default value is **true**.<br>**true**: The text box loses focus. **false**: The text box does not lose focus.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the text box loses focus after the Enter key is pressed to submit information.|
| NODE_TEXT_INPUT_CUSTOM_KEYBOARD = 7028 | Sets a custom keyboard.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).<br> .value[0]?.i32: whether the custom keyboard supports avoidance. The default value is **false**.<br>**true**: The custom keyboard supports avoidance. **false**: The custom keyboard does not support avoidance.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).<br> .value[0].i32: whether the custom keyboard supports avoidance.|
| NODE_TEXT_INPUT_WORD_BREAK = 7029 | Defines the line break rule. This attribute can be set, reset, and obtained as required through APIs. It takes effect only when the component is in the inline input editing state.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: line break rule. The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak). The default value is **ARKUI_WORD_BREAK_BREAK_WORD**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: line break rule. The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak).|
| NODE_TEXT_INPUT_NUMBER_OF_LINES = 7031 | Sets the number of lines in the **TextInput** component, which can be used to work out the height of the component. For example, if **numberOfLines** is set to **3**, the component displays three lines of text by default.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of lines.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of lines.|
| NODE_TEXT_INPUT_LETTER_SPACING = 7032 | Sets the letter spacing of the **TextInput** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: letter spacing. The default unit is fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: letter spacing. The default unit is fp.<br>**Since**: 15  |
| NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT = 7033 | Sets whether to enable preview text for the **TextInput** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable preview text. The default value is **true**.<br>**true**: Enable preview text. **false**: Disable preview text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable preview text.<br>**Since**: 15 |
| NODE_TEXT_INPUT_HALF_LEADING = 7034 | Sets whether to enable half leading.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable half leading. The default value is **false**.<br>Half leading is the leading split in half and applied equally to the top and bottom edges. The value **true** means to enable half leading, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable half leading.<br>**Since**: 18  |
| NODE_TEXT_INPUT_KEYBOARD_APPEARANCE = 7035 | Sets the appearance of the keyboard when the text box is focused.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance). The default value is **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**.<br>**Since**: 15 |
| NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036 | Sets whether to enable the autofill animation.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the autofill animation.<br>**true**: Enable the autofill animation. **false**: Disable the autofill animation.<br>The default value is **true**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the autofill animation. When enabled, the animation only takes effect for text boxes whose [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_PASSWORD**, **ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD**, or **ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD**.<br>**Since**: 20 |
| NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS = 7030 | Sets whether to show the keyboard when the text box obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show the keyboard when the text box obtains focus. **true**: Show the keyboard when the text box obtains focus. **false**: Do not show the keyboard when the text box obtains focus.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show the keyboard when the text box obtains focus.|
| NODE_TEXT_INPUT_LINE_HEIGHT = 7037 | Sets the line height of text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: numeric value for the text line height. Default value: adaptive to the font size. If this parameter is set to **undefined**, the text line height is **5**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: numeric value for the text line height.<br>**Since**: 20  |
| NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR = 7038 | Whether to enable entity recognition for selected text.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable entity recognition for selected text. **true** indicates that entity recognition is enabled, and false indicates that entity recognition is disabled. Default value: **true**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable entity recognition for selected text.<br>**Since**: 22|
| NODE_TEXT_INPUT_SHOW_COUNTER = 7040 | Sets whether to display a counter and its style when the number of input characters exceeds a threshold. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show a character counter. The value true indicates that the counter is enabled, and the value false indicates that the counter is disabled.<br> .value[1]?.f32: percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is displayed. The value range is [1, 100]. If the value is a decimal, it is rounded down. If the value is out of the range, the API attribute setting does not take effect.<br> Whether to highlight the border when the number of entered characters exceeds the maximum. The value true indicates that the border is highlighted, and the value false indicates that the border is not highlighted.<br> .object: counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show a character counter.<br> .value[1].f32: percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is displayed. The value range is [1, 100].<br> .value[2].i32: whether to highlight the border when the number of entered characters exceeds the maximum. The value true indicates that the border is highlighted, and the value false indicates that the border is not highlighted. By default, the border is highlighted.<br> .object: counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).<br>**Since**: 22  |
| NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE = 7041 | Sets or obtains the text input controller.<br>The [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format of the parameter for setting attributes is as follows:<br>.object: basic controller of the text content. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.object: basic controller of the text content. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br>**Since**: 23      |
| NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION  = 7044 | Sets the switch for compressing punctuations at the beginning of an input line. The APIs for setting, resetting, and obtaining attributes are supported.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the function of compressing punctuations at the beginning of a line.<br> The value true indicates that the punctuation compression at the beginning of a line is enabled, and the value false indicates that the punctuation compression at the beginning of a line is disabled. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the punctuation compression at the beginning of a line.<br>**Since**: 23|
| NODE_TEXT_INPUT_INCLUDE_FONT_PADDING = 7045 | Sets whether to add spacing between the first and last lines of text in a single-line text box to avoid text truncation.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to add spacing between the first and last lines of text in a text box to avoid text truncation. The value true indicates that the spacing is enabled, and the value false indicates that the spacing is disabled. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to add spacing to the first and last lines. The value true indicates that the spacing is added, and the value false indicates that the spacing is not added.<br>**Since**: 23|
| NODE_TEXT_INPUT_FALLBACK_LINE_SPACING = 7046 | For multi-line text overlay, the line height can be automatically adjusted based on the actual text height. This API takes effect only when the line height is smaller than the actual text height.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to automatically adjust the line height based on the actual text height. The value true indicates that the auto-adaptation is enabled, and the value false indicates that the auto-adaptation is disabled. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the function of automatically adjusting the line height based on the actual text height. The value true indicates that the auto-adaptation is enabled, and the value false indicates that the auto-adaptation is disabled.<br>**Since**: 23|
| NODE_TEXT_INPUT_DIRECTION = 7047 | Text layout direction of a single-line text box.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text layout direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). The default value is **ARKUI_TEXT_DIRECTION_DEFAULT**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text layout direction. For details about the values and meanings, see the enumerated values of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).<br>**Since**: 23|
| NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE  = 7048 | Sets the drag preview style when the text in the text box is selected.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).<br>**Since**: 23|
| NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA = 8000 | Defines the default placeholder text of the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default placeholder text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default placeholder text.|
| NODE_TEXT_AREA_TEXT = 8001 | Defines the default text content for the multi-line text box. The attribute setting, attribute resetting, and attribute obtaining interfaces are supported.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default text content.|
| NODE_TEXT_AREA_MAX_LENGTH = 8002 | Defines the maximum number of characters in the text input. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: maximum number of characters in the text input.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: maximum number of characters in the text input.|
| NODE_TEXT_AREA_PLACEHOLDER_COLOR = 8003 | Defines the placeholder text color. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format.|
| NODE_TEXT_AREA_PLACEHOLDER_FONT = 8004 | Defines the placeholder text font. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.f32: font size, in fp. Optional. The default value is **16.0**.<br> .value[1]?.i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**.<br> .value[2]?.i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.<br> ?.string: font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2".<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: font size, in fp.<br> .value[1].i32: font style [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).<br> .value[2].i32: font weight [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).<br> .string: font family. Multiple font families are separated by commas (,).|
| NODE_TEXT_AREA_CARET_COLOR = 8005 | Defines the caret color attribute, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format.|
| NODE_TEXT_AREA_EDITING = 8006 | Defines the editable state for the multi-line text box. This attribute can be set and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to remain in the editable state. The value **true** means to remain in the editable state, and **false** means to exit the editable state.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for obtaining the attribute:<br> .value[0].i32: whether to remain in the editable state. The value **true** means to remain in the editable state, and **false** means to exit the editable state.|
| NODE_TEXT_AREA_TYPE = 8007 | Defines the text box type. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text box type, specified using the [ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype) enum. The default value is **ARKUI_TEXTAREA_TYPE_NORMAL**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text box type, specified using the [ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype) enum.|
| NODE_TEXT_AREA_SHOW_COUNTER = 8008 | Sets whether to display a counter and its style when the number of input characters exceeds a threshold. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show a character counter. The value **true** means to show a character counter. The default value is **false**.<br> .value[1]?.f32: percentage of the number of characters that can be entered to the maximum number of characters. When the number of characters exceeds this value, the counter is displayed. The value range is [1, 100]. If the value is a decimal, it is rounded down. If the value is out of the value range, the attribute setting does not take effect.<br> .value[2]?.i32: whether to highlight the border when the number of entered characters reaches the maximum. true indicates that the border is highlighted, and false indicates that the border is not highlighted. The default value is **true**.<br>.object: counter configuration. The configuration attributes are the color of the counter when the number of characters in the text box does not reach the maximum and the color of the counter when the number of characters in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show a character counter. The value **true** means to show a character counter.<br> .value[1].f32: percentage of the number of characters that can be entered to the maximum number of characters. When the number of characters entered exceeds this value, the counter is displayed. The value range is [1, 100].<br> .value[2].i32: whether to highlight the border when the number of entered characters exceeds the maximum. The value is true when the border is highlighted.<br>.object: counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).|
| NODE_TEXT_AREA_SELECTION_MENU_HIDDEN = 8009 | Sets whether to hide the text selection menu when the text box is long-pressed, double-clicked, or right-clicked. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-clicked, or right-clicked. The default value is **false**.<br>**true**: The system text selection menu is hidden under the following circumstances: clicking the text box cursor, long-pressing the text box, double-tapping the text box, triple-tapping the text box, or right-clicking the text box.<br>**false**: The system text selection menu is displayed under the following circumstances: clicking the text box cursor, long-pressing the text box, double-tapping the text box, triple-tapping the text box, or right-clicking the text box.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-clicked, or right-clicked.|
| NODE_TEXT_AREA_BLUR_ON_SUBMIT = 8010 | Sets whether the multi-line text box loses focus after the **Enter** key is pressed to submit information.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the text box loses focus after the Enter key is pressed to submit information. **true**: The text box loses focus. **false**: The text box does not lose focus.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the text box loses focus after the Enter key is pressed to submit information.|
| NODE_TEXT_AREA_INPUT_FILTER = 8011 | Sets the regular expression for input filtering. Only inputs that comply with the regular expression can be displayed. Other inputs are filtered out. For single-character input scenarios, only single-character matching is supported; for multi-character input scenarios (such as pasting), string matching is supported.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: regular expression.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: regular expression.|
| NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR = 8012 | Sets the background color of the selected text. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format.|
| NODE_TEXT_AREA_ENTER_KEY_TYPE = 8013 | Defines the type of the **Enter** key. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of the Enter key, specified using the [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype) enum. The default value is **ARKUI_ENTER_KEY_TYPE_DONE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of the Enter key, specified using the [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype) enum.|
| NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS = 8014 | Sets whether to enable the input method when the multi-line text box obtains focus in a way other than clicking. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the input method when the multi-line text box obtains focus in a way other than clicking. The value **true** means to enable the input method, and **false** means the opposite. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the input method when the component obtains focus. The value **1** means to enable the input method when the component obtains focus, and **0** means the opposite.|
| NODE_TEXT_AREA_CARET_OFFSET = 8015 | Sets or obtains the caret position.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> Sets the position of the caret.<br> .value[0].i32: length from the start of the string to the position where the input cursor is located.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> Returns the position information of the caret. If this API is called when the caret position is updated in the current frame, it will not take effect.<br> .value[0].i32: index of the caret position.<br> .value[1].f32: x-coordinate of the caret relative to the text box.<br> .value[2].f32: y-coordinate of the caret relative to the text box.|
| NODE_TEXT_AREA_CONTENT_RECT = 8016 | Obtains the position of the edited text area relative to the component and its size.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: horizontal coordinate.<br> .value[1].f32: vertical coordinate.<br> .value[2].f32: content width.<br> .value[3].f32: content height.|
| NODE_TEXT_AREA_CONTENT_LINE_COUNT = 8017 | Obtains the number of lines of the edited text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of lines of the edited text.|
| NODE_TEXT_AREA_TEXT_SELECTION = 8018 | Sets the text selection range and highlights the selected text when the component is focused. This API works only when the value of **selectionStart** is less than that of **selectionEnd**.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: start position of the text selection. <br> .value[1].i32: end position of the text selection. |
| NODE_TEXT_AREA_ENABLE_AUTO_FILL = 8019 | Sets whether to enable autofill.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable autofill. The default value is **true**.<br>**true**: Enable autofill. **false**: Disable autofill.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable autofill.|
| NODE_TEXT_AREA_CONTENT_TYPE = 8020 | Sets the autofill type.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype).|
| NODE_TEXT_AREA_NUMBER_OF_LINES = 8022 | Sets the number of lines in the **TextArea** component, which can be used to work out the height of the component.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of lines.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of lines.|
| NODE_TEXT_AREA_LETTER_SPACING = 8023 | Sets the letter spacing of the **TextArea** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: letter spacing. The default unit is fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: letter spacing. The default unit is fp.<br>**Since**: 15 |
| NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024 | Sets whether to enable preview text for the **TextArea** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable preview text. **true**: Enable preview text. **false**: Disable preview text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable preview text.<br>**Since**: 15 |
| NODE_TEXT_AREA_HALF_LEADING = 8025 | Sets whether to enable half leading.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable half leading. The default value is **false**.<br>Half leading is the leading split in half and applied equally to the top and bottom edges. The value **true** means to enable half leading, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable half leading.<br>**Since**: 18 |
| NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026 | Sets the appearance of the keyboard when the text box is focused.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance).<br>**Since**: 15  |
| NODE_TEXT_AREA_MAX_LINES = 8027 | Sets the maximum number of lines that can be displayed with the inline style in the editing state. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: maximum number of lines that can be displayed with the inline style in the editing state. With the inline style, the default value is **3**.<br> With the non-inline style, the default value is +∞, indicating that there is no limit on the maximum number of lines. If this parameter is set to **undefined**, the maximum number of lines is **5**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: maximum number of lines.<br>**Since**: 20  |
| NODE_TEXT_AREA_LINE_SPACING = 8028 | Sets the letter spacing of text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: numeric value for the letter spacing. The default value is **0**, in fp. If this parameter is set to **undefined**, the letter spacing is **5**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: numeric value for the letter spacing, in fp.<br>**Since**: 20  |
| NODE_TEXT_AREA_MIN_LINES = 8029 | Sets the minimum number of lines for the node. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum number of lines.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum number of lines.<br>**Since**: 20 |
| NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL = 8030 | Sets the maximum number of lines for the node when scrolling is enabled. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum number of lines when scrolling is enabled.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum number of lines when scrolling is enabled.<br>**Since**: 20  |
| NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS = 8021 | Sets whether to show the keyboard when the text box obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show the keyboard when the text box obtains focus. The default value is **true**.<br>**true**: Show the keyboard when the text box obtains focus. **false**: Do not show the keyboard when the text box obtains focus.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show the keyboard when the text box obtains focus.|
| NODE_TEXT_AREA_LINE_HEIGHT = 8031 | Sets the line height of text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: numeric value for the text line height. Default value: adaptive to the font size. The unit is fp. If this parameter is set to **undefined**, the text line height is **5**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: numeric value for the text line height, in fp.<br>**Since**: 20 |
| NODE_TEXT_AREA_BAR_STATE = 8032 | Defines the scrollbar status of the text input box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: indicates the scrollbar status of the text. The parameter type is [ArkUI_BarState](capi-native-type-h.md#arkui_barstate). The default value is ARKUI_BAR_STATE_AUTO.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: indicates the scrollbar status of the text. The parameter type is [ArkUI_BarState](capi-native-type-h.md#arkui_barstate).<br>**Since**: 22|
| NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR = 8033 | Whether to enable entity recognition for selected text.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable entity recognition for selected text. **true** indicates that entity recognition is enabled, and false indicates that entity recognition is disabled. Default value: **true**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable entity recognition for selected text.<br>**Since**: 22|
| NODE_TEXT_AREA_SCROLL_BAR_COLOR = 8035 | Sets the scroll bar color of the text box. This API supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value of the scroll bar. 0xargb type. Default value: 0x66182431, which is displayed in gray.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value of the scroll bar.<br>**Since**: 22|
| NODE_TEXT_AREA_CUSTOM_KEYBOARD = 8036 | Sets the custom keyboard of the text box. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).<br> .value[0]?.i32: whether the custom keyboard supports the avoidance function.<br>**true**: The custom keyboard supports avoidance. **false**: The custom keyboard does not support avoidance.<br>Default value: **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).<br> .value[0].i32: whether the custom keyboard supports avoidance.<br>**Since**: 22|
| NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE = 8037 | Sets or obtains the text area controller.<br>The [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format for setting attributes is as follows:<br>.object: basic text content controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br>The [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format for obtaining attributes is as follows:<br>.object: basic text content controller. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).<br>**Since**: 23|
| NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION  = 8040 | Sets the switch for compressing punctuations at the beginning of an input line. This API supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the function of compressing punctuations at the beginning of a line.<br> The value true indicates that the punctuation compression at the beginning of a line is enabled, and the value false indicates that the punctuation compression at the beginning of a line is disabled. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the punctuation compression at the beginning of a line.<br>**Since**: 23|
| NODE_TEXT_AREA_INCLUDE_FONT_PADDING = 8041 | Sets whether to add spacing between the first and last lines of the text in a multi-line text box to avoid text truncation.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to add spacing between the first and last lines of text in a text box to avoid text truncation. The value true indicates that the spacing is enabled, and the value false indicates that the spacing is disabled. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: Indicates whether to add spacing between the first and last lines of the text in the text box. The value true indicates that the spacing is added, and the value false indicates that the spacing is not added.<br>**Since**: 23|
| NODE_TEXT_AREA_FALLBACK_LINE_SPACING = 8042 | For multi-line text overlay, the line height can be automatically adjusted based on the actual text height. This API takes effect only when the line height is smaller than the actual text height.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to automatically adjust the line height based on the actual text height. The value true indicates that the auto-adaptation is enabled, and the value false indicates that the auto-adaptation is disabled. The default value is **false**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the function of automatically adjusting the line height based on the actual text height. The value true indicates that the auto-adaptation is enabled, and the value false indicates that the auto-adaptation is disabled.<br>**Since**: 23|
| NODE_TEXT_AREA_DIRECTION = 8044 | Text layout direction of a multi-line text box.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: text layout direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). The default value is **ARKUI_TEXT_DIRECTION_DEFAULT**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: text layout direction. For details about the values and meanings, see the enumerated values of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).<br>**Since**: 23|
| NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE = 8045 | Sets the drag preview style of the selected text in the multi-line text input box.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).<br>**Since**: 23|
| NODE_BUTTON_LABEL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_BUTTON = 9000 | Defines the button text content. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: default text.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: default text content.|
| NODE_BUTTON_TYPE = 9001 | Sets the button type. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: button style. The parameter type is [ArkUI_ButtonType](capi-native-type-h.md#arkui_buttontype). The default value is **ARKUI_BUTTON_TYPE_CAPSULE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: button style. The parameter type is [ArkUI_ButtonType](capi-native-type-h.md#arkui_buttontype). The default value is **ARKUI_BUTTON_TYPE_CAPSULE**. |
| NODE_BUTTON_MIN_FONT_SCALE = 9002 | Defines the minimum font scale factor for the button. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum font scale factor. The default unit is fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum font scale factor. The default unit is fp.<br>**Since**: 18 |
| NODE_BUTTON_MAX_FONT_SCALE = 9003 | Defines the maximum font scale factor for the button. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum font scale factor. The default unit is fp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum font scale factor. The default unit is fp.<br>**Since**: 18  |
| NODE_PROGRESS_VALUE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PROGRESS = 10000 | Defines the current value of the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: current value of the progress indicator.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current value of the progress indicator.|
| NODE_PROGRESS_TOTAL = 10001 | Defines the total value of the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: total value of the progress indicator.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: total value of the progress indicator.|
| NODE_PROGRESS_COLOR = 10002 | Defines the color for the progress value on the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color value, in 0xARGB format.|
| NODE_PROGRESS_TYPE = 10003 | Defines the type of the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of the progress indicator, specified using the [ArkUI_ProgressType](capi-native-type-h.md#arkui_progresstype) enum. The default value is **ARKUI_PROGRESS_TYPE_LINEAR**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of the progress indicator, specified using the [ArkUI_ProgressType](capi-native-type-h.md#arkui_progresstype) enum.|
| NODE_PROGRESS_LINEAR_STYLE = 10004 | Defines the linear progress indicator style. This attribute can be set, reset, and obtained as required through APIs. Note that the settings are effective only if the progress indicator type is linear.<br>.object: [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) object that defines the component style.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) object that defines the component style.<br>**Since**: 15|
| NODE_CHECKBOX_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX = 11000 | Defines whether the **CheckBox** component is selected. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the component is selected. The value **1** means that the component is selected, and **0** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the component is selected. The value **1** means that the component is selected, and **0** means the opposite.|
| NODE_CHECKBOX_SELECT_COLOR = 11001 | Defines the color of the **CheckBox** component when it is selected. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the check box when it is selected, in 0xARGB format, for example, **0xFF1122FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the check box when it is selected, in 0xARGB format, for example, **0xFF1122FF**. |
| NODE_CHECKBOX_UNSELECT_COLOR = 11002 | Defines the border color of the **CheckBox** component when it is not selected. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: border color, in 0xARGB format, for example, **0xFF1122FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: border color, in 0xARGB format, for example, **0xFF1122FF**.|
| NODE_CHECKBOX_MARK = 11003 | Defines the internal icon style of the **CheckBox** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: border color, in 0xARGB format, for example, **0xFF1122FF**.<br> .value[1]?.f32: size of the internal mark, in vp. Optional.<br> .value[2]?.f32: stroke width of the internal mark, in vp. Optional. The default value is **2**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: border color, in 0xARGB format, for example, **0xFF1122FF**.<br> .value[1].f32: size of the internal mark, in vp. <br> .value[2].f32: stroke width of the internal mark, in vp. The default value is **2**. |
| NODE_CHECKBOX_SHAPE = 11004 | Defines the shape of the **CheckBox** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-native-type-h.md#arkui_checkboxshape).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-native-type-h.md#arkui_checkboxshape).  |
| NODE_CHECKBOX_NAME = 11005 | Defines the name of the **CheckBox** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component name.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component name.<br> **Since**: 15 |
| NODE_CHECKBOX_GROUP = 11006 | Defines the name of the **CheckboxGroup** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component name.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component name.<br>**Since**: 15  |
| NODE_XCOMPONENT_ID = MAX_NODE_SCOPE_NUM * ARKUI_NODE_XCOMPONENT = 12000 | Defines the ID of the **XComponent** component. This attribute can be set and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component ID.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component ID.|
| NODE_XCOMPONENT_TYPE = 12001  | Specifies the type of the **XComponent** component. This attribute is read-only.<br>The type of the **XComponent** component must be explicitly set during creation using **ARKUI_NODE_XCOMPONENT** or **ARKUI_NODE_XCOMPONENT_TEXTURE** in [ArkUI_NodeType](#arkui_nodetype), and cannot be modified afterward.<br>Attempting to change the type through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) will cause rendering exceptions.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: font style [ArkUI_XComponentType](capi-native-type-h.md#arkui_xcomponenttype).|
| NODE_XCOMPONENT_SURFACE_SIZE = 12002  | Specifies the size of the **XComponent** component. This attribute is read-only.<br>Attempting to modify the size through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) will have no effect.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: width, in px. <br> .value[1].u32: height, in px.|
| NODE_XCOMPONENT_SURFACE_RECT = 12003 | Sets the display area of the surface held by the **XComponent** component.This attribute can be set and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: x-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.<br> .value[1].i32: y-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.<br> .value[2].i32: width of the surface display area, in px.<br> .value[3].i32: height of the surface display area, in px.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: x-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.<br> .value[1].i32: y-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.<br> .value[2].i32: width of the surface display area, in px.<br> .value[3].i32: height of the surface display area, in px.<br>**Since**: 18 |
| NODE_XCOMPONENT_ENABLE_ANALYZER = 12004 | Sets whether to enable the AI analyzer for the **XComponent** component. This attribute can be set and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the AI analyzer. **1**: Enable the AI analyzer. **0**: Disable the AI analyzer. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the AI analyzer. **1**: Enable the AI analyzer. **0**: Disable the AI analyzer. The default value is **0**.<br>**Since**: 18 |
| NODE_DATE_PICKER_LUNAR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER = 13000 | Defines whether to display the lunar calendar in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to display the lunar calendar in the date picker. The default value is **false**. **true**: Display the lunar calendar. **false**: Do not display the lunar calendar.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to display the lunar calendar in the date picker.|
| NODE_DATE_PICKER_START = 13001 | Defines the start date of the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The default value is **"1970-1-1"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date.|
| NODE_DATE_PICKER_END = 13002 | Defines the end date of the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The default value is **"2100-12-31"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date.|
| NODE_DATE_PICKER_SELECTED = 13003 | Defines the selected date of the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The default value is **"2024-01-22"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date.|
| NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE = 13004 | Defines the text color, font size, and font weight for the top and bottom items in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are enumerated values: "bold", "normal", "bolder", "lighter", "medium", "regular".<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are **"normal"** and **"italic"**.<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|
| NODE_DATE_PICKER_TEXT_STYLE = 13005 | Defines the text color, font size, and font weight of all items except the top, bottom, and selected items in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are enumerated values: "bold", "normal", "bolder", "lighter", "medium", "regular".<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are **"normal"** and **"italic"**.<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|
| NODE_DATE_PICKER_SELECTED_TEXT_STYLE = 13006 | Defines the text color, font size, and font weight of the selected item in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are enumerated values: "bold", "normal", "bolder", "lighter", "medium", "regular".<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are **"normal"** and **"italic"**.<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|
| NODE_DATE_PICKER_MODE = 13007 | Sets the date columns to be displayed. This attribute can be set, reset, and obtained as required through APIs. **DatePicker** displays different styles of date columns.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of date column to be displayed. The parameter type is [ArkUI_DatePickerMode](capi-native-type-h.md#arkui_datepickermode).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of date column to be displayed. The parameter type is [ArkUI_DatePickerMode](capi-native-type-h.md#arkui_datepickermode).<br>**Since**: 18 |
| NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK = 13008 | Specifies whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: whether to enable haptic feedback. The value **true** means to enable haptic feedback, and **false** means the opposite. The default value is **true**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: whether to enable haptic feedback.<br> **Since**: 18  |
| NODE_DATE_PICKER_CAN_LOOP = 13009 | Defines whether to enable looping for the picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable looping. The value **true** means to enable looping, and **false** means the opposite. Default value: **true**. If an invalid value is provided, the default value is used.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: The value **1** means to enable looping, and **0** means the opposite.<br> Note: When looping is enabled, the year increments or decrements in linkage with the month's cycle, and the month increments or decrements in linkage with the day's cycle.<br> When looping is disabled, scrolling beyond the bounds of the year, month, or day columns is prevented, and cross-column value synchronization (between year, month, and day) is also disabled.<br>     **Since**: 20 |
| NODE_TIME_PICKER_USE_MILITARY_TIME = 14001 | Defines whether the display time is in 24-hour format. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the display time is in 24-hour format. The default value is **false**. **true**: The display time is in 24-hour format. **false**: The display time is in 12-hour format.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the display time is in 24-hour format.|
| NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE = 14002 | Defines the text color, font size, and font weight for the top and bottom items in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are enumerated values: "bold", "normal", "bolder", "lighter", "medium", "regular".<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are **"normal"** and **"italic"**.<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|
| NODE_TIME_PICKER_TEXT_STYLE = 14003 | Defines the text color, font size, and font weight of all items except the top, bottom, and selected items in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are enumerated values: "bold", "normal", "bolder", "lighter", "medium", "regular".<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are **"normal"** and **"italic"**.<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|
| NODE_TIME_PICKER_SELECTED_TEXT_STYLE = 14004 | Defines the text color, font size, and font weight of the selected item in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are enumerated values: "bold", "normal", "bolder", "lighter", "medium", "regular".<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are **"normal"** and **"italic"**.<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|
| NODE_TIME_PICKER_SELECTED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER = 14000 | Sets the selected time for the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: time. Default value: current system time. Format: only hours and minutes are supported (for example, 23:59/23-59).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: time. Default value: current system time. Format: hour, minute, and second (for example, 23,59,1).|
| NODE_TIME_PICKER_START = 14005 | Sets the start time for the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: time. Default value: **"0:0:0"**. Format: only hours and minutes are supported (for example, 12:59/12-59).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: time. Default value: **"0:0:0"**. Format: hour, minute, and second (for example, 12:59:0).<br>**Since**: 18 |
| NODE_TIME_PICKER_END = 14006 | Sets the end time for the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: time. Default value: **"23:59:59"**. Format: only hours and minutes are supported (for example, 23:59/23-59).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: time. Default value: **"23:59:59"**. Format: hour, minute, and second (for example, 23:59:0).<br>**Since**: 18 |
| NODE_TIME_PICKER_ENABLE_CASCADE = 14007 | Sets whether the AM/PM indicator automatically switches based on the hour in 12-hour format. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the AM/PM indicator automatically switches based on the hour in 12-hour format. The default value is **false**. The value **true** means that the AM/PM indicator automatically switches based on the hour in 12-hour format, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the AM/PM indicator automatically switches based on the hour in 12-hour format.<br>**Since**: 18 |
| NODE_TEXT_PICKER_OPTION_RANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER = 15000 | Defines the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: type of the text picker [ArkUI_TextPickerRangeType](capi-native-type-h.md#arkui_textpickerrangetype). The default value is **ARKUI_TEXTPICKER_RANGETYPE_SINGLE**.<br> ?.string: string input, whose format varies by picker type.<br> 1: single-column picker. The input format is a group of strings separated by semicolons (;).<br> 2: multi-column picker. Multiple pairs of plain text strings are supported. The pairs are separated by semicolons (;), and strings within each pair are separated by commas (,).<br> ?.object: object input, whose format varies by picker type.<br> 1: single-column picker with image support. The input struct is [ARKUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md).<br> 2: multi-column cascading picker. The input struct is [ARKUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: type of the text picker [ArkUI_TextPickerRangeType](capi-native-type-h.md#arkui_textpickerrangetype).<br> ?.string: string output, whose format varies by picker type.<br> 1: single-column picker. The output format is a group of strings separated by semicolons (;).<br> 2: multi-column picker. Multiple pairs of plain text strings are supported. The pairs are separated by semicolons (;), and strings within each pair are separated by commas (,).|
| NODE_TEXT_PICKER_OPTION_SELECTED = 15001 | Defines the index of the default selected item in the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: index. If there are multiple index values, add them one by one.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: index. If there are multiple index values, add them one by one.|
| NODE_TEXT_PICKER_OPTION_VALUE = 15002 | Defines the value of the default selected item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: value of the selected item. If there are multiple values, add them one by one and separate them with semicolons (;).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: value of the selected item. If there are multiple values, add them one by one and separate them with semicolons (;).|
| NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE = 15003 | Defines the text color, font size, and font weight for the top and bottom items in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|
| NODE_TEXT_PICKER_TEXT_STYLE = 15004 | Defines the text color, font size, and font weight for all items except the top, bottom, and selected items in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are enumerated values: "bold", "normal", "bolder", "lighter", "medium", "regular".<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are **"normal"** and **"italic"**.<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|
| NODE_TEXT_PICKER_SELECTED_TEXT_STYLE = 15005 | Defines the text color, font size, and font weight of the selected item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: font size, in fp. The value is a number.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: fonts, separated by commas (,).<br>       Parameter 5: font style. Available options are ("normal", "italic").<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: five parameters of the string type, separated by semicolons (;).<br>       Parameter 1: text color, in #ARGB format.<br>       Parameter 2: text size. The value is a number, and the unit is fp.<br>       Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>       Parameter 4: text font list, which is separated by commas (,).<br>       Parameter 5: text style, string enumeration ("normal", "italic")<br>       Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**. |
| NODE_TEXT_PICKER_SELECTED_INDEX = 15006 | Defines the index of the default selected item in the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter:<br> .value[0...].i32: index of the default item in the data selection range. |
| NODE_TEXT_PICKER_CAN_LOOP = 15007 | Defines whether to enable looping for the picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to support scroll looping. The value **true** means to support scroll looping, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: The value **1** means to enable looping, and **0** means the opposite.|
| NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT = 15008 | Defines the height of each item in the picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].f32: item height, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: item height, in vp. |
| NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK = 15010 | Specifies whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: whether to enable haptic feedback. The value **true** means to enable haptic feedback, and **false** means the opposite. The default value is **true**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: whether to enable haptic feedback.<br> **Since**: 18  |
| NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE = 15011 | Sets the background color and border radius of the selected item. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format, for example, **0xFF1122FF**.<br> 1: .value[1].f32: unified radius for all four corners, in vp.<br> 2: .value[1].f32: radius of the upper left corner, in vp.<br> .value[2].f32: radius of the upper right corner, in vp.<br> .value[3].f32: radius of the lower left corner, in vp.<br> .value[4].f32: radius of the lower right corner, in vp.<br> Default values: background color = 0x0C182431; border radius = 24.0.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format, for example, **0xFF1122FF**.<br> .value[1].f32: radius of the upper left corner, in vp.<br> .value[2].f32: radius of the upper right corner, in vp.<br> .value[3].f32: radius of the lower left corner, in vp.<br> .value[4].f32: radius of the lower right corner, in vp.<br>**Since**: 20 |
| NODE_CALENDAR_PICKER_HINT_RADIUS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER = 16000 | Defines the style of the background in the selected state of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: corner radius for the selection state background of the calendar picker. The default value is 16.0, in vp, indicating that the background is a circle. If the value is **0.0**, the background is a right-angled rectangle. If the value is in the (0.0, 16.0) range, the background is a rounded rectangle. If the value is a negative number or greater than 16.0, the default value **16.0** is used, which means the background is a circle.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: corner radius for the selection state background of the calendar picker. The default value is 16.0, in vp, indicating that the background is a circle. The value range is [0.0, 16.0]. If the value is **0.0**, the background is a right-angled rectangle.|
| NODE_CALENDAR_PICKER_SELECTED_DATE = 16001 | Defines the date of the selected item in the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: year of the selected date.<br> .value[1].u32: month of the selected date.<br> .value[2].u32: day of the selected date.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: year of the selected date.<br> .value[1].u32: month of the selected date.<br> .value[2].u32: day of the selected date.|
| NODE_CALENDAR_PICKER_EDGE_ALIGNMENT = 16002 | Defines how the calendar picker is aligned with the entry component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-native-type-h.md#arkui_calendaralignment).<br> .value[1]?.f32: offset of the picker relative to the entry component along the x-axis after alignment based on the specified alignment mode.<br> .value[2]?.f32: offset of the picker relative to the entry component along the y-axis after alignment based on the specified alignment mode.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-native-type-h.md#arkui_calendaralignment).<br> .value[1].f32: offset of the picker relative to the entry component along the x-axis after alignment based on the specified alignment mode.<br> .value[2].f32: offset of the picker relative to the entry component along the y-axis after alignment based on the specified alignment mode.|
| NODE_CALENDAR_PICKER_TEXT_STYLE = 16003 | Defines the text color, font size, and font weight in the entry area of the calendar picker.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.u32: text color of the entry area.<br> .value[1]?.f32: font size of the entry area, in fp.<br> .value[2]?.i32: font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: font color of the entry area.<br> .value[1].f32: font size of the entry area, in fp.<br> .value[2].i32: font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|
| NODE_CALENDAR_PICKER_START = 16004 | Sets the start date for the calendar picker. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The value format is "YYYY-M-D", for example, **"1970-1-1"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date.<br>**Since**: 18 |
| NODE_CALENDAR_PICKER_END = 16005 | Sets the end date for the calendar picker. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: date. The value format is "YYYY-M-D", for example, **"2100-12-31"**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: date.<br>**Since**: 18 |
| NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE = 16006 | Sets the disabled date ranges for the calendar picker. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: string representing the disabled date ranges. The format is "start_date,end_date" for each range, with multiple ranges separated by commas (,).<br> Example: "1910-01-01,1910-12-31,2020-01-01,2020-12-31".<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: string representing the disabled date ranges.<br>**Since**: 19 |
| NODE_CALENDAR_PICKER_MARK_TODAY = 16007 | Sets whether to highlight the current system date in the calendar picker. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> value[0].i32: whether to highlight the current system date in the calendar picker. The default value is **false**. The value **true** means to highlight the current system date in the calendar picker, and **false** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].i32: whether to highlight the current system date in the calendar picker.<br>**Since**: 19  |
| NODE_SLIDER_BLOCK_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER = 17000 | Defines the color of the slider thumb. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the slider thumb, in 0xARGB format, for example, **0xFF1122FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the slider thumb, in 0xARGB format, for example, **0xFF1122FF**.|
| NODE_SLIDER_TRACK_COLOR = 17001 | Defines the background color of the slider. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: background color, in 0xARGB format, for example, **0xFF1122FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: background color, in 0xARGB format, for example, **0xFF1122FF**.  |
| NODE_SLIDER_SELECTED_COLOR = 17002 | Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, **0xFF1122FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the selected part of the slider track, in 0xARGB format, for example, **0xFF1122FF**. |
| NODE_SLIDER_SHOW_STEPS = 17003 | Sets whether to display the step scale value, which can be set, reset, and obtained as required. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to display the step scale value. The value **1** means to display the step scale value, and **0** (default value) means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to display the step scale value. The value **1** means to display the step scale value, and **0** (default value) means the opposite.|
| NODE_SLIDER_BLOCK_STYLE = 17004 | Defines the slider thumb shape, which can be set, reset, and obtained as required. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-native-type-h.md#arkui_sliderblockstyle).<br> .string?: depends on the shape. Optional.<br> ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider thumb. Example: /pages/common/icon.png.<br> **ARKUI_SLIDER_BLOCK_STYLE_SHAPE**: custom shape of the slider thumb. In this case, the width and height values in the defined shape do not represent the actual size of the thumb; they are scaled proportionally to ensure the thumb displays correctly.<br> There are five types:<br> 1. Rectangle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_RECTANGLE**.<br> .value[2].f32: height of the rectangle.<br> .value[3].f32: height of the rectangle.<br> .value[4].f32: height of the rounded corner of the rectangle.<br> .value[5].f32: height of the rounded corner of the rectangle.<br> 2. Circle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_CIRCLE**.<br> .value[2].f32: height of the circle.<br> .value[3].f32: height of the circle.<br> 3. Ellipse:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_ELLIPSE**.<br> .value[2].f32: height of the ellipse.<br> .value[3].f32: height of the ellipse.<br> 4. Path:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_PATH**.<br> .value[2].f32: width of the path.<br> .value[3].f32: height of the path.<br> .string: command for drawing the path.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-native-type-h.md#arkui_sliderblockstyle).<br> .string?: depends on the shape. Optional.<br> ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider thumb. Example: /pages/common/icon.png.<br> ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider thumb.<br> There are five types:<br> 1. Rectangle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_RECTANGLE**.<br> .value[2].f32: height of the rectangle.<br> .value[3].f32: height of the rectangle.<br> .value[4].f32: height of the rounded corner of the rectangle.<br> .value[5].f32: height of the rounded corner of the rectangle.<br> 2. Circle:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_CIRCLE**.<br> .value[2].f32: height of the circle.<br> .value[3].f32: height of the circle.<br> 3. Ellipse:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_ELLIPSE**.<br> .value[2].f32: height of the ellipse.<br> .value[3].f32: height of the ellipse.<br> 4. Path:<br> .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-h.md#arkui_shapetype). The value is **ARKUI_SHAPE_TYPE_PATH**.<br> .value[2].f32: width of the path.<br> .value[3].f32: height of the path.<br> .string: command for drawing the path. |
| NODE_SLIDER_VALUE = 17005 | Defines the current value of the slider. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: current value.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current value. |
| NODE_SLIDER_MIN_VALUE = 17006 | Defines the minimum value of the slider. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum value.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum value. |
| NODE_SLIDER_MAX_VALUE = 17007 | Defines the maximum value of the slider. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum value.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum value. |
| NODE_SLIDER_STEP = 17008 | Defines the step of the slider. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: step. The value range is [0.01, 100].<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: step. The value range is [0.01, 100].|
| NODE_SLIDER_DIRECTION = 17009 | Defines the slider direction. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: display style. The parameter type is [ArkUI_SliderDirection](capi-native-type-h.md#arkui_sliderdirection).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: display style. The parameter type is [ArkUI_SliderDirection](capi-native-type-h.md#arkui_sliderdirection).|
| NODE_SLIDER_REVERSE = 17010 | Defines whether the slider values are reversed. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the slider values are reversed. The value **1** means that the slider values are reversed, and **0** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the slider values are reversed. The value **1** means that the slider values are reversed, and **0** means the opposite. |
| NODE_SLIDER_STYLE = 17011 | Defines the style of the slider thumb and track. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: display style. The parameter type is [ArkUI_SliderStyle](capi-native-type-h.md#arkui_sliderstyle).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: display style. The parameter type is [ArkUI_SliderStyle](capi-native-type-h.md#arkui_sliderstyle).|
| NODE_SLIDER_TRACK_THICKNESS = 17012 | Sets the track thickness of the slider. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: track thickness of the slider, in vp. The default value is 4.0 vp when **NODE_SLIDER_STYLE** is set to **ARKUI_SLIDER_STYLE_OUT_SET** and 20.0 vp when **NODE_SLIDER_STYLE** is set to **ARKUI_SLIDER_STYLE_IN_SET**. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: track thickness of the slider, in vp.  |
| NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013 | Specifies whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: whether to enable haptic feedback. The value **true** means to enable haptic feedback, and **false** means the opposite. The default value is **true**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: whether to enable haptic feedback.<br> To enable haptic feedback, you must add **"name": "ohos.permission.VIBRATE"** under **requestPermissions** in the **module.json5** file of the project.<br>**Since**: 18  |
| NODE_SLIDER_PREFIX = 17014 | Sets a custom prefix component for the start edge of the slider. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: custom prefix component for the start edge. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). The prefix component is typically placed on the left in LTR layouts.<br>**Since**: 20  |
| NODE_SLIDER_SUFFIX = 17015 | Sets a custom suffix component for the end edge of the slider. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: custom suffix component for the end edge. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). The suffix component is typically placed on the right in LTR layouts.<br>**Since**: 20   |
| NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR = 17016 | Defines the color of the slider thumb. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> - **colors**: colors of the color stops.<br> - **stops**: stop positions of the color stops.<br> - **size**: number of colors.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Array of color stops, each of which consists of a color and its stop position.<br> - **colors**: colors of the color stops.<br> - **stops**: stop positions of the color stops.<br> - **size**: number of colors.<br>**Since**: 21   |
| NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR = 17017 | Defines the background color of the slider track. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> - **colors**: colors of the color stops.<br> - **stops**: stop positions of the color stops.<br> - **size**: number of colors.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Array of color stops, each of which consists of a color and its stop position.<br> - **colors**: colors of the color stops.<br> - **stops**: stop positions of the color stops.<br> - **size**: number of colors.<br>**Since**: 21   |
| NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR = 17018 | Defines the color of the selected part of the slider track. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.<br> - **colors**: colors of the color stops.<br> - **stops**: stop positions of the color stops.<br> - **size**: number of colors.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Array of color stops, each of which consists of a color and its stop position.<br> - **colors**: colors of the color stops.<br> - **stops**: stop positions of the color stops.<br> - **size**: number of colors.<br>**Since**: 21   |
| NODE_RADIO_CHECKED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO = 18000 | Sets whether the radio button is selected. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the radio button is selected. The default value is **false**. **true**: The radio button is selected. **false**: The radio button is not selected. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the radio button is selected.|
| NODE_RADIO_STYLE = 18001 | Sets the style of the radio button in selected or deselected state. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.u32: color of the background when the radio button is selected, in 0xARGB format. The default value is **0xFF007DFF**.<br> .value[1]?.u32: color of the border when the radio button is deselected, in 0xARGB format. The default value is **0xFF182431**.<br> .value[2]?.u32: color of the indicator when the radio button is selected, in 0xARGB format. The default value is **0xFFFFFFFF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the background when the radio button is selected, in 0xARGB format. The default value is **0xFF007DFF**.<br> .value[1].u32: color of the border when the radio button is deselected, in 0xARGB format. The default value is **0xFF182431**.<br> .value[2].u32: color of the indicator when the radio button is selected, in 0xARGB format. The default value is **0xFFFFFFF**.|
| NODE_RADIO_VALUE = 18002 | Sets the current value of the radio button. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: value of the radio button.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: value of the radio button.|
| NODE_RADIO_GROUP = 18003 | Sets the name of the group to which the radio button belongs. Only one radio button in a given group can be selected at a time. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: name of the group to which the radio button belongs. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: name of the group to which the radio button belongs. |
| NODE_CHECKBOX_GROUP_NAME = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP = 21000 | Defines the name of the **CheckboxGroup** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: component name.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: component name.<br>**Since**: 15 |
| NODE_CHECKBOX_GROUP_SELECT_ALL = 21001 | Defines whether to select all check boxes in the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to select all check boxes in the **CheckBoxGroup** component. The value **1** means that all check boxes are selected, and **0** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the component is selected. The value **1** means that the component is selected, and **0** means the opposite.<br>**Since**: 15   |
| NODE_CHECKBOX_GROUP_SELECTED_COLOR = 21002 | Defines the color for the selected state of the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the selected state in 0xARGB format, for example, **0xFF1122FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the selected state in 0xARGB format, for example, **0xFF1122FF**.<br>**Since**: 15  |
| NODE_CHECKBOX_GROUP_UNSELECTED_COLOR = 21003 | Defines the border color for the unselected state of the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: border color in 0xARGB format, for example, **0xFF1122FF**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: border color in 0xARGB format, for example, **0xFF1122FF**.<br>**Since**: 15  |
| NODE_CHECKBOX_GROUP_MARK = 21004 | Defines the check mark style of the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: border color in 0xARGB format, for example, **0xFF1122FF**.<br> .value[1]?.f32: size of the check mark, in vp.<br> .value[2]?.f32: stroke width of the check mark, in vp. The default value is **2**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: border color in 0xARGB format, for example, **0xFF1122FF**.<br> .value[1]?.f32: size of the check mark, in vp.<br> .value[2]?.f32: stroke width of the check mark, in vp. The default value is **2**.<br>**Since**: 15 |
| NODE_CHECKBOX_GROUP_SHAPE = 21005 | Defines the shape of the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-native-type-h.md#arkui_checkboxshape).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-native-type-h.md#arkui_checkboxshape).<br>**Since**: 15 |
| NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK = 1000000 | Defines the alignment mode of the child components in the container. This attribute can be set, reset, and obtained as required through APIs. If this attribute and the universal attribute **NODE_ALIGNMENT** are both set, whichever is set later takes effect.<br><br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_CENTER**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment).|
| NODE_SCROLL_BAR_DISPLAY_MODE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SCROLL = 1002000 | Defines the scrollbar display mode. This attribute can be set, reset, and obtained as required through APIs. List, Scroll, and WaterFlow are supported since API version 12. Grid is supported since API version 22.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: scrollbar display mode. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-native-type-h.md#arkui_scrollbardisplaymode). Default value: **ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO** for the **List**, **Grid**, and **Scroll** components; **ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF** for the **WaterFlow** component.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: scrollbar display mode. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-native-type-h.md#arkui_scrollbardisplaymode).|
| NODE_SCROLL_BAR_WIDTH = 1002001 | Defines the width of the scrollbar. This attribute can be set, reset, and obtained as required through APIs. List, Scroll, and WaterFlow are supported since API version 12. Grid is supported since API version 22.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width of the scrollbar, in vp. The default value is **4**.<br>Values less than 0 are treated as the default value. The value **0** means not to show the scrollbar.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: width of the scrollbar, in vp. |
| NODE_SCROLL_BAR_COLOR = 1002002 | Defines the color of the scrollbar. This attribute can be set, reset, and obtained as required through APIs. List, Scroll, and WaterFlow are supported since API version 12. Grid is supported since API version 22.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .data[0].u32: color of the scrollbar, in 0xARGB format. Default value: **0x66182431**.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .data[0].u32: color of the scrollbar, in 0xARGB format. |
| NODE_SCROLL_SCROLL_DIRECTION = 1002003 | Defines the scroll direction. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: scroll direction. The parameter type is [ArkUI_ScrollDirection](capi-native-type-h.md#arkui_scrolldirection). The default value is **ARKUI_SCROLL_DIRECTION_VERTICAL**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: scroll direction. The parameter type is [ArkUI_ScrollDirection](capi-native-type-h.md#arkui_scrolldirection).|
| NODE_SCROLL_EDGE_EFFECT = 1002004 | Defines the effect used at the edges of the component when the boundary of the scrollable content is reached. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect). Default value: **ARKUI_EDGE_EFFECT_NONE** for the **Grid**, **Scroll**, and **WaterFlow** components; **ARKUI_EDGE_EFFECT_SPRING** for the **List** component.<br> .value[1]?.i32: whether to enable the scroll effect when the component content size is smaller than the component itself. The value **1** means to enable the scroll effect, and **0** means the opposite. Default value: **0** for the **List**, **Grid**, and **WaterFlow** components; **1** for the **Scroll** component.<br> .value[2]?.i32: direction where the edge effect takes effect. The parameter type is [ArkUI_EffectEdge](capi-native-type-h.md#arkui_effectedge). The default value is **ARKUI_EFFECT_EDGE_START**.| ARKUI_EFFECT_EDGE_END.<br> This parameter is supported since API version 18.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect).<br> .value[1].i32: whether to enable the scroll effect when the component content size is smaller than the component itself. The value **1** means to enable the scroll effect, and **0** means the opposite.<br> .value[2].i32: direction where the edge effect takes effect. The parameter type is [ArkUI_EffectEdge](capi-native-type-h.md#arkui_effectedge). This parameter is supported since API version 18.|
| NODE_SCROLL_ENABLE_SCROLL_INTERACTION = 1002005 | Sets whether to support scroll gestures. When this attribute is set to **0**, scrolling by finger or mouse is not supported, but the scrolling controller API is not affected.<br>The List, Scroll, and WaterFlow components are supported since API version 12. The Grid component is supported since API version 22.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to support scroll gestures. The default value is **1**. **1**: Scroll gestures are supported. **0**: Scroll gestures are not supported.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to support scroll gestures.|
| NODE_SCROLL_FRICTION = 1002006 | Sets the friction coefficient. It applies only to gestures in the scrolling area, and it affects only indirectly the scroll chaining during the inertial scrolling process.<br>The List, Scroll, and WaterFlow components are supported since API version 12. The Grid component is supported since API version 22.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: friction coefficient. The default value is **0.6** for non-wearable devices and **0.9** for wearable devices. Value range: (0, +∞). If this parameter is set to a value less than or equal to 0, the default value is used.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: friction coefficient.|
| NODE_SCROLL_SNAP = 1002007 | Defines the scroll snapping mode. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: scroll snapping mode. The parameter type is [ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign). The default value is **ARKUI_SCROLL_SNAP_ALIGN_NONE**.<br> .value[1].i32: whether to enable the snap to start feature. When scroll snapping is defined for the **Scroll** component, setting this attribute to **false** enables the component to scroll between the start edge and the first snap point. The default value is **true**. It is valid only when there are multiple snap points.<br> .value[2].i32: Whether to enable the snap to end feature. When scroll snapping is defined for the **Scroll** component, setting this attribute to **false** enables the component to scroll between the end edge and the last snap point. The default value is **true**. It is valid only when there are multiple snap points.<br> .value[3...].f32: snap points for the **Scroll** component. Each snap point defines the offset from an edge to which the **Scroll** component can scroll. One or more snap points are supported.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: scroll snapping mode. The parameter type is [ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign).<br> .value[1].i32: whether to enable the snap to start feature. When scroll snapping is defined for the **Scroll** component, setting this attribute to **false** enables the component to scroll between the start edge and the first snap point.<br> .value[2].i32: Whether to enable the snap to end feature. When scroll snapping is defined for the **Scroll** component, setting this attribute to **false** enables the component to scroll between the end edge and the last snap point.<br> .value[3...].f32: snap points for the **Scroll** component. Each snap point defines the offset from an edge to which the **Scroll** component can scroll.|
| NODE_SCROLL_NESTED_SCROLL = 1002008 | Nested scrolling options, which support attribute setting, resetting, and obtaining. The List, Scroll, and WaterFlow components are supported since API version 12. The Grid component is supported since API version 22.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: nested scrolling behavior when the scrollable component scrolls toward the end edge. The parameter type is [ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode).<br> .value[1].i32: nested scrolling behavior when the scrollable component scrolls toward the start edge. The parameter type is [ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: nested scrolling behavior when the scrollable component scrolls toward the end edge. The parameter type is [ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode).<br> .value[1].i32: nested scrolling behavior when the scrollable component scrolls toward the start edge. The parameter type is [ArkUI_ScrollNestedMode](capi-native-type-h.md#arkui_scrollnestedmode).|
| NODE_SCROLL_OFFSET = 1002009 | Defines the specified position to scroll to. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: horizontal scrolling offset, in vp. Value range: If the value is less than 0, the offset will be 0 for non-animated scrolling. A value greater than 0 triggers an animated scroll to the specified offset. By default, the scroll stops at the target offset. Additional **animation** parameters can be configured to enable a bounce effect when the scroll exceeds the content bounds.<br> .value[1].f32: vertical scrolling offset, in vp. Value range: If the value is less than 0, the offset will be 0 for non-animated scrolling. A value greater than 0 triggers an animated scroll to the specified offset. By default, the scroll stops at the target offset. Additional **animation** parameters can be configured to enable a bounce effect when the scroll exceeds the content bounds.<br> .value[2]?.i32: scrolling duration, in ms. The default value is **1000**.<br> .value[3]?.i32: scrolling curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). The default value is **ARKUI_CURVE_EASE**.<br> .value[4]?.i32: whether to enable the default spring animation. Optional. The default value **0** means not to enable the default spring animation.<br> .value[5]?.i32: whether to convert the scroll animation to an overshoot animation when the boundary is reached. The default value is **0**, meaning not to convert the scroll animation to an overshoot animation when the boundary is reached.<br> .value[6]?.i32: whether the component can stop at an overscrolled position. The default value is **0**, meaning the component cannot stop at an overscrolled position. This parameter is supported since API version 20.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: horizontal scrolling offset, in vp.<br> .value[1].f32: vertical scrolling offset, in vp.|
| NODE_SCROLL_EDGE = 1002010 | Defines the edge position to scroll to. This attribute can be set and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: edge position to scroll to. The parameter type is [ArkUI_ScrollEdge](capi-native-type-h.md#arkui_scrolledge).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the container is at the edge. The value **-1** indicates that the container is not at the edge. If the container is at the edge, the parameter type is [ArkUI_ScrollEdge](capi-native-type-h.md#arkui_scrolledge).|
| NODE_SCROLL_ENABLE_PAGING = 1002011 | Defines whether to enable the swipe-to-turn-pages feature. This attribute can be set, reset, and obtained as required through APIs. If both **enablePaging** and **scrollSnap** are set, **scrollSnap** takes effect, but **enablePaging** does not.<br><br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the swipe-to-turn-pages feature. The default value is **0**. **0**: Disable the swipe-to-turn-pages feature. **1**: Enable the swipe-to-turn-pages feature.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the swipe-to-turn-pages feature.|
| NODE_SCROLL_PAGE = 1002012 | Scrolls to the next or previous page.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to scroll to the next page. The value **0** means to scroll to the next page, and **1** means to scroll to the previous page.<br> .value[1]?.i32: whether to enable the page turning animation. The value **1** means to enable the page turning animation, and **0** means the opposite. Default value: **0**.|
| NODE_SCROLL_BY = 1002013 | Defines the scrolling distance.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: horizontal scrolling distance, in vp by default. <br> .value[1].f32: vertical scrolling distance, in vp by default. |
| NODE_SCROLL_FLING = 1002014 | Performs inertial scrolling based on the initial velocity passed in.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: initial velocity of inertial scrolling. The default unit is vp/s. If the value specified is 0, it is considered as invalid, and the scrolling for this instance will not take effect. If the value is positive, the scroll will move downward; if the value is negative, the scroll will move upward.<br>**Since**: 13 |
| NODE_SCROLL_FADING_EDGE = 1002015 | Sets the edge fade effect for the scrollable component.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the edge fade effect. **0**: Disable the edge fade effect. **1**: Enable the edge fade effect. The default value is **0**.<br> .value[1]?.f32: length of the edge fade effect, in vp. The default value is **32**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the edge fade effect. **0**: Disable the edge fade effect. **1**: Enable the edge fade effect.<br> .value[1].f32: length of the edge fade effect, in vp.<br>**Since**: 14 |
| NODE_SCROLL_SIZE = 1002016 | Obtains the total size of all child components when fully expanded in the scrollable component. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: total width of all child components when fully expanded in the scrollable component. The default unit is vp.<br> .value[1].f32: total height of all child components when fully expanded in the scrollable component. The default unit is vp.<br> When **NODE_PADDING**, **NODE_MARGIN**, **NODE_BORDER_WIDTH** is set, the values are rounded to the nearest pixel when being converted from vp to px. The return values are calculated based on these rounded pixel values.<br>**Since**: 14 |
| NODE_SCROLL_CONTENT_START_OFFSET = 1002017 | Sets the offset from the start of the content of this scrollable component. The **List** component is supported since API version 15, and the **Grid**, **Scroll**, and **WaterFlow** components are supported since API version 22.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: offset from the start of the content, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: offset from the start of the content, in vp.<br>**Since**: 15 |
| NODE_SCROLL_CONTENT_END_OFFSET = 1002018 | Sets the offset from the end of the content of this scrollable component. The **List** component is supported since API version 15, and the **Grid**, **Scroll**, and **WaterFlow** components are supported since API version 22.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: offset from the end of the content, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: offset from the end of the content, in vp.<br>**Since**: 15  |
| NODE_SCROLL_FLING_SPEED_LIMIT = 1002019 | Sets the maximum initial velocity at the start of the fling animation that occurs after gesture-driven scrolling ends. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum initial velocity at the start of the fling animation, in vp/s.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum initial velocity at the start of the fling animation.<br>**Since**: 18 |
| NODE_SCROLL_CLIP_CONTENT = 1002020 | Sets the content clipping area for this scrollable component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: content clipping mode. The parameter type is [ArkUI_ContentClipMode](capi-native-type-h.md#arkui_contentclipmode). Default value: **ARKUI_CONTENT_CLIP_MODE_BOUNDARY** for the **Grid** and **Scroll** components; **ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY** for the **List** and **WaterFlow** components.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: content clipping mode. The parameter type is [ArkUI_ContentClipMode](capi-native-type-h.md#arkui_contentclipmode).<br>**Since**: 18 |
| NODE_SCROLL_BACK_TO_TOP = 1002021 | Sets whether to scroll back to the top when the status bar is clicked. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to scroll back to the top. The value **1** means to scroll back to the top, and **0** means to stay at the current position. Default value:<br>API versions earlier than 18: **0**. API version 18 and later: **0** for the horizontal scroll direction, and **1** for the vertical scroll direction.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to scroll back to the top.<br>**Since**: 15|
| NODE_SCROLL_BAR_MARGIN = 1002022 | Defines the margin of the scrollbar. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: start margin of the scrollbar, in vp. The default value is **0**.<br> .value[1].f32: end margin of the scrollbar, in vp. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: start margin of the scrollbar, in vp.<br> .value[1].f32: end margin of the scrollbar, in vp.<br>**Since**: 20 |
| NODE_SCROLL_MAX_ZOOM_SCALE = 1002023 | Sets the maximum zoom scale for scrollable content.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum zoom scale to set. Default value: **1**.<br>Value range: (0, +∞). If the value is less than or equal to 0, the default value is used.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current maximum zoom scale.<br>**Since**: 20 |
| NODE_SCROLL_MIN_ZOOM_SCALE = 1002024 | Sets the minimum zoom scale for scrollable content.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum zoom scale for scrollable content. The default value is **1**.<br>Value range: (0, NODE_SCROLL_MAX_ZOOM_SCALE]. If the value is less than or equal to 0, the default value **1** is used. If the value is greater than **NODE_SCROLL_MAX_ZOOM_SCALE**, **NODE_SCROLL_MAX_ZOOM_SCALE** is used.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current minimum zoom scale.<br>**Since**: 20|
| NODE_SCROLL_ZOOM_SCALE = 1002025 | Sets the zoom scale for scrollable content.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: zoom scale for scrollable content. The default value is **1**.<br>Value range: (0, +∞). If the value is less than or equal to 0, the default value is used.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: current zoom scale.<br>**Since**: 20 |
| NODE_SCROLL_ENABLE_BOUNCES_ZOOM = 1002026 | Sets whether to enable the zoom bounce effect when the scaling exceeds the limits.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the zoom bounce effect when the scaling exceeds the limits. The value **1** means to enable the effect, and **0** means the opposite. Default value: **1**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the zoom bounce effect when the scaling exceeds the limits. The value **1** means to enable the effect, and **0** means the opposite.<br>**Since**: 20   |
| NODE_LIST_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST = 1003000 | Sets the direction in which the list items are arranged. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: direction in which the list items are arranged. The parameter type is [ArkUI_Axis](capi-native-type-h.md#arkui_axis). The default value is **ARKUI_AXIS_VERTICAL**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: direction in which the list items are arranged. The parameter type is [ArkUI_Axis](capi-native-type-h.md#arkui_axis).|
| NODE_LIST_STICKY = 1003001 | Defines whether to pin the header to the top or the footer to the bottom in the **ListItemGroup** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to pin the header to the top or the footer to the bottom in the **ListItemGroup** component. It is used together with the **ListItemGroup** component. The parameter type is [ArkUI_StickyStyle](capi-native-type-h.md#arkui_stickystyle). The default value is **ARKUI_STICKY_STYLE_NONE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to pin the header to the top or the footer to the bottom in the **ListItemGroup** component. It is used together with the **ListItemGroup** component. The parameter type is [ArkUI_StickyStyle](capi-native-type-h.md#arkui_stickystyle).|
| NODE_LIST_SPACE = 1003002 | Defines the spacing between list items. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: spacing between list items along the main axis. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: spacing between list items along the main axis.|
| NODE_LIST_NODE_ADAPTER = 1003003 | Defines the list adapter. The attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object used as the adapter.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object.|
| NODE_LIST_CACHED_COUNT = 1003004 | Sets the number of cached items in the list adapter. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: used together with the adapter of the list component to set the number of cached items in the adapter.<br> .value[1]?.i32: whether to show cached items. The value **0** means to hide cached items, and **1** means to show cached items. The default value is **0**. This parameter is supported since API version 15.<br> .value[2]?.i32: maximum number of cached items in the list. The default value is the same as that of the first parameter. This parameter is supported since API version 22.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: number of cached items in the list adapter.<br> .value[1].i32: whether to show cached items. The value **0** means to hide cached items, and **1** means to show cached items. This parameter is supported since API version 15.<br> .value[2]?.i32: maximum number of cached items in the list. This parameter is supported since API version 22.|
| NODE_LIST_SCROLL_TO_INDEX = 1003005 | Scrolls to the item with the specified index. When **smooth** is set to **true**, all passed items are loaded and counted in layout calculation. This may result in performance issues if a large number of items are involved.<br><br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: index of the item to be scrolled to in the container.<br> .value[1]?.i32: whether to enable the smooth animation for scrolling to the item with the specified index. The value **1** means to enable the animation, and **0** means the opposite. The default value is **0**.<br> .value[2]?.i32: how the item to scroll to is aligned with the container. The parameter type is [ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment). The default value is **ARKUI_SCROLL_ALIGNMENT_START**.<br> .value[3]?.f32: extra offset, in vp. The default value is **0**. This parameter is supported since API version 15.|
| NODE_LIST_ALIGN_LIST_ITEM = 1003006 | Sets the alignment mode of list items along the cross axis when the cross-axis width of the list is greater than the cross-axis width of list items multiplied by the value of lanes. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode of list items along the cross axis. The parameter type is [ArkUI_ListItemAlign](capi-native-type-h.md#arkui_listitemalignment). Default value: **ARKUI_LIST_ITEM_ALIGNMENT_START**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode of list items along the cross axis. The parameter type is [ArkUI_ListItemAlign](capi-native-type-h.md#arkui_listitemalignment). |
| NODE_LIST_CHILDREN_MAIN_SIZE = 1003007 | Sets the default main axis size of the child components in this list.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> object: [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) object.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> object: [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) object.|
| NODE_LIST_INITIAL_INDEX = 1003008 | Sets the item displayed at the beginning of the viewport when the current list is loaded for the first time. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: item displayed at the beginning of the viewport when the current list is loaded for the first time. Default value: **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: item displayed at the beginning of the viewport when the current list is loaded for the first time.|
| NODE_LIST_DIVIDER = 1003009 | Defines the style of the divider for the list items. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the divider, in 0xARGB format. The default value is **0x08000000**.<br> .value[1].f32: stroke width of the divider, in vp.<br> .value[2].f32: distance between the divider and the start of the list, in vp. The default value is **0**.<br> .value[3].f32: distance between the divider and the end of the list, in vp. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the divider, in 0xARGB format.<br> .value[1].f32: stroke width of the divider.<br> .value[2].f32: distance between the divider and the start of the list, in vp.<br> .value[3].f32: distance between the divider and the end of the list, in vp.|
| NODE_LIST_SCROLL_TO_INDEX_IN_GROUP = 1003010 | Scrolls to the item with the specified index in the specified list item group. When **smooth** is set to **true**, all passed items are loaded and counted in layout calculation. This may result in performance issues if a large number of items are involved.<br><br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: index of the target list item group in the current list.<br> .value[1].i32: index of the target list item in the list item group.<br> .value[2]?.i32: whether to enable the smooth animation for scrolling to the item with the specified index. The value **1** means to enable the animation, and **0** means the opposite. The default value is **0**.<br> .value[3]?.i32: how the item to scroll to is aligned with the container. The parameter type is [ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment). The default value is **ARKUI_SCROLL_ALIGNMENT_START**.<br>**Since**: 15 |
| NODE_LIST_LANES = 1003011 | Sets the number of lanes in the list. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: number of lanes in the list. If the maximum and minimum lane widths are set, setting the number of lanes will not take effect. The default value is **1**. The value range is [1, +∞).<br> .value[1]?.f32: minimum lane width, in vp.<br> .value[2]?.f32: maximum column width, in vp.<br> .value[3]?.f32: lane spacing, in vp. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: number of lanes in the list.<br> .value[1].f32: minimum lane width, in vp.<br> .value[2].f32: maximum lane width, in vp.<br> .value[3].f32: lane spacing, in vp.<br>**Since**: 15 |
| NODE_LIST_SCROLL_SNAP_ALIGN = 1003012 | Sets the scroll snap alignment mode for the **List** component.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: scroll snapping mode. The parameter type is [ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign). The default value is **ARKUI_SCROLL_SNAP_ALIGN_NONE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: scroll snapping mode. The parameter type is [ArkUI_ScrollSnapAlign](capi-native-type-h.md#arkui_scrollsnapalign).<br>**Since**: 15  |
| NODE_LIST_MAINTAIN_VISIBLE_CONTENT_POSITION = 1003013 | Sets whether to maintain the visible content's position when data is inserted or deleted outside the display area of the **List** component.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside the display area of the **List** component. The value **0** means not to maintain the visible content's position, and **1** means the opposite. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside the display area of the **List** component. The value **0** means not to maintain the visible content's position, and **1** means the opposite. The default value is **0**.<br>**Since**: 15  |
| NODE_LIST_STACK_FROM_END = 1003014 | Sets whether the **List** component starts layout from the end.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the **List** component starts layout from the end. The value **0** means layout starts from the top, and **1** means layout starts from the end. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the **List** component starts layout from the end. The value **0** means layout starts from the top, and **1** means layout starts from the end. The default value is **0**.<br>**Since**: 19  |
| NODE_LIST_FOCUS_WRAP_MODE = 1003015 | Defines the focus wrap mode for the **List** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: focus wrap mode of the **List** component. The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode). The default value is **ARKUI_FOCUS_WRAP_MODE_DEFAULT**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: focus wrap mode of the **List** component. The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode).<br>**Since**: 20 |
| NODE_LIST_SYNC_LOAD = 1003016 | Defines whether the **List** component loads child nodes synchronously. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the **List** component synchronously loads child nodes. **0**: frame-by-frame loading. **1**: synchronous loading. Default value: **1**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the **List** component synchronously loads child nodes. **0**: frame-by-frame loading. **1**: synchronous loading.<br>**Since**: 20  |
| NODE_LIST_SCROLL_SNAP_ANIMATION_SPEED = 1003017 | Speed of the snapping animation for the List component. This attribute supports the attribute setting, resetting, and obtaining APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: speed of the snapping animation for the List component. The data type is [ArkUI_ScrollSnapAnimationSpeed](capi-native-type-h.md#arkui_scrollsnapanimationspeed). Default value: ARKUI_SCROLL_SNAP_ANIMATION_NORMAL.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: speed of the snapping animation for the List component. The data type is [ArkUI_ScrollSnapAnimationSpeed](capi-native-type-h.md#arkui_scrollsnapanimationspeed).<br>**Since**: 22  |
| NODE_LIST_LANES_ITEMFILLPOLICY = 1003018 | Responsive column layout policy of the List component. This attribute supports the attribute setting, resetting, and obtaining APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of columns in different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).<br> .value[1]?.f32: column spacing, in vp. Default value: **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of columns in different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).<br> .value[1].f32: column spacing, in vp.<br>**Since**: 22|
| NODE_LIST_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1003019 | Sets whether the current List component supports the generation of empty branch nodes that do not contain any child components using the if/else rendering control syntax in LazyForEach or Repeat.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the List component supports empty branches. 0: no; 1: yes. Default value: **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the List component supports empty branches. 0: no; 1: yes.<br>**Since**: 23  |
| NODE_SWIPER_LOOP = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER = 1001000 | Defines whether to enable loop playback for the swiper. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable loop playback. The value **1** means to enable loop playback, and **0** means the opposite. The default value is **1**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable loop playback. The value **1** means to enable loop playback, and **0** means the opposite. The default value is **1**.  |
| NODE_SWIPER_AUTO_PLAY = 1001001 | Defines whether to enable automatic playback for child component switching in the swiper. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable automatic playback for child component switching. The value **1** means to enable automatic playback, and **0** means the opposite. The default value is **0**.<br> .value[1]?.i32: whether to stop automatic playback when the user touches the screen. The value **0** means to stop automatic playback, and **1** means the opposite. The default value is **0**. This parameter is supported since API version 16.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable automatic playback for child component switching. The value **1** means to enable automatic playback, and **0** means the opposite. The default value is **0**.<br> .value[1].i32: whether to stop automatic playback when the user touches the screen. The value **0** means to stop automatic playback, and **1** means the opposite. This parameter is supported since API version 16. |
| NODE_SWIPER_SHOW_INDICATOR = 1001002 | Defines whether to enable the navigation indicator for the swiper. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to enable the navigation indicator. The value **1** means to enable the navigation indicator, and **0** means the opposite. The default value is **1**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to enable the navigation indicator. The value **1** means to enable the navigation indicator, and **0** means the opposite. The default value is **1**. |
| NODE_SWIPER_INTERVAL = 1001003 | Defines the interval for automatic playback. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: interval for automatic playback, in ms.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: interval for automatic playback, in ms. |
| NODE_SWIPER_VERTICAL = 1001004 | Defines whether vertical swiping is used for the swiper. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether vertical swiping is used. The value **1** means that vertical swiping is used, and **0** means the opposite. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether vertical swiping is used. The value **1** means that vertical swiping is used, and **0** means the opposite. The default value is **0**. |
| NODE_SWIPER_DURATION = 1001005 | Defines the duration of the animation for switching child components. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: duration of the animation for switching child components, in ms. The default value is **400**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: duration of the animation for switching child components, in ms. The default value is **400**. |
| NODE_SWIPER_CURVE = 1001006 | Defines the animation curve for the swiper. This attribute can be set, reset, and obtained as required through APIs. If this attribute is not set or reset, the animation curve is [interpolatingSpring](../../reference/apis-arkui/js-apis-curve.md#curvesinterpolatingspring10)(-1, 1, 328, 34). If an exception occurs when setting this attribute, the default value ARKUI_CURVE_LINEAR is used.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). The default value is **ARKUI_CURVE_LINEAR**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-h.md#arkui_animationcurve). The default value is **ARKUI_CURVE_LINEAR**.|
| NODE_SWIPER_ITEM_SPACE = 1001007 | Defines the spacing between child components in the swiper. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: spacing between child components.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: spacing between child components. |
| NODE_SWIPER_INDEX = 1001008 | Defines the index of the child component currently displayed in the swiper. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of elements to display per page.<br> .value[1]?.i32: switching animation mode. The parameter type is [ArkUI_SwiperAnimationMode](capi-native-type-h.md#arkui_swiperanimationmode). The setting is only effective for the current call.<br> This parameter is supported since API version 15.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of elements to display per page.|
| NODE_SWIPER_DISPLAY_COUNT = 1001009 | Defines the number of elements to display per page. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of elements to display within the viewport.<br> .value[1]?.i32: whether to paginate by group. The value **0** means to paginate by individual child elements, and **1** means to paginate by groups of child elements displayed within the viewport. The default value is **0**.<br> .string?: whether to enable auto-adaptation. This parameter accepts only the value **"auto"**. When this parameter is set to **"auto"**, the **value[]** parameters are ignored.<br> This parameter is supported since API version 19.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of elements to display within the viewport.<br> .value[1].i32: whether to paginate by group. This parameter is supported since API version 19. |
| NODE_SWIPER_DISABLE_SWIPE = 1001010 | Sets whether to disable the swipe-to-switch feature of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to disable the swipe-to-switch feature. The value **1** means to disable the feature, and **0** means the opposite. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to disable the swipe-to-switch feature. The value **1** means to disable the feature, and **0** means the opposite. The default value is **0**. |
| NODE_SWIPER_SHOW_DISPLAY_ARROW = 1001011 | Defines whether to show the arrow when the mouse pointer hovers over the navigation indicator. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow). The default value is **ARKUI_SWIPER_ARROW_HIDE**.<br> .?object: style of the arrow displayed when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrow](capi-native-type-h.md#arkui_swiperarrow).<br> .object: style of the arrow displayed when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.|
| NODE_SWIPER_EDGE_EFFECT_MODE = 1001012 | Defines the effect used at the edges of the swiper when the boundary of the scrollable content is reached. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect).<br> The default value is **ARKUI_EDGE_EFFECT_SPRING**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-native-type-h.md#arkui_edgeeffect). |
| NODE_SWIPER_NODE_ADAPTER = 1001013 | Defines the swiper adapter. The attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object used as the adapter.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object.|
| NODE_SWIPER_CACHED_COUNT = 1001014 | Sets the number of cached items in the swiper adapter. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of cached items in the swiper adapter. <br> .value[1]?.i32: whether to show cached items. The value **0** means to hide cached items, and **1** means to show cached items. The default value is **0**. This parameter is supported since API version 19.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of cached items in the list adapter.<br> .value[1].i32: whether to show cached items. The value **0** means to hide cached items, and **1** means to show cached items. This parameter is supported since API version 19. |
| NODE_SWIPER_PREV_MARGIN = 1001015 | Sets the leading margin of the swiper. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: leading margin, in vp. The default value is **0**.<br> .value[1].i32: whether to ignore blank areas. The value **1** means to ignore blank areas, and **0** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: leading margin, in vp. .value[1].i32: whether to ignore blank areas. The value **1** means to ignore blank areas, and **0** means the opposite.|
| NODE_SWIPER_NEXT_MARGIN = 1001016 | Sets the trailing margin of the swiper. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: trailing margin, in vp. The default value is **0**.<br> .value[1].i32: whether to ignore blank areas. The value **1** means to ignore blank areas, and **0** means the opposite.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: trailing margin, in vp. .value[1].i32: whether to ignore blank areas. The value **1** means to ignore blank areas, and **0** means the opposite. |
| NODE_SWIPER_INDICATOR = 1001017 | Sets the navigation indicator type of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: navigation indicator type. The parameter type is [ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype).<br> .object: additional configuration for the navigation indicator, depending on the type. For **ARKUI_SWIPER_INDICATOR_TYPE_DOT**, the parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md).<br>          For **ARKUI_SWIPER_INDICATOR_TYPE_DIGIT**, the parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md).<br>          The **ArkUI_SwiperDigitIndicator** type is supported since API version 19. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: navigation indicator type. The parameter type is [ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype).<br> .object: additional configuration for the navigation indicator, depending on the type. For **ARKUI_SWIPER_INDICATOR_TYPE_DOT**, the parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md).<br>          For **ARKUI_SWIPER_INDICATOR_TYPE_DIGIT**, the parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md).<br>          The **ArkUI_SwiperDigitIndicator** type is supported since API version 19.  |
| NODE_SWIPER_NESTED_SCROLL = 1001018 | Sets the nested scrolling mode of the **Swiper** component and its parent container.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: nested scrolling mode. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-native-type-h.md#arkui_swipernestedscrollmode).<br> The default value is **ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: nested scrolling mode. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-native-type-h.md#arkui_swipernestedscrollmode).  |
| NODE_SWIPER_SWIPE_TO_INDEX = 1001019 | Sets the swiper to switch to the specified page.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: index of the target page in the swiper.<br> .value[1]?.i32: whether to use an animation for when the target page is reached. The value **1** indicates that the dynamic effect is enabled, and the value **0** indicates that the dynamic effect is disabled. The default value is **0**.|
| NODE_SWIPER_INDICATOR_INTERACTIVE = 1001020 | Sets whether the navigation indicator is interactive.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the navigation indicator is interactive. The default value **true** means that the navigation indicator is interactive.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the navigation indicator is interactive. |
| NODE_SWIPER_PAGE_FLIP_MODE = 1001021 | Sets the page flipping mode using the mouse wheel.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-native-type-h.md#arkui_pageflipmode).<br> Format of the return value [ArkUI_PageFlipMode](capi-native-type-h.md#arkui_pageflipmode):<br> .value[0].i32: page flipping mode using the mouse wheel.<br>**Since**: 15  |
| NODE_SWIPER_AUTO_FILL = 1001022 | Configures the **Swiper** component to automatically adjust the number of elements displayed per page based on the minimum width of the elements. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum width of the elements to be displayed, in vp.<br> .value[1]?.i32: whether to paginate by group. The value **0** means to paginate by individual child elements, and **1** means to paginate by groups of child elements displayed within the viewport. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum width of the elements to be displayed, in vp.<br> .value[1].i32: whether to paginate by group.<br>**Since**: 19 |
| NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023 | Sets whether to maintain the visible content's position when data is inserted or deleted outside the display area of the **Swiper** component.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside the display area of the **Swiper** component. The value **0** means not to maintain the visible content's position, and **1** means the opposite. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside the display area of the **Swiper** component. The value **0** means not to maintain the visible content's position, and **1** means the opposite. The default value is **0**.<br>**Since**: 20  |
| NODE_SWIPER_ITEMFILLPOLICY = 1001024 | This API is used to set, reset, and obtain the responsive column layout policy of the Swiper component.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of columns in different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).<br> .value[1]?.i32: whether to paginate by group. The value **0** means to paginate by individual child elements, and **1** means to paginate by groups of child elements displayed within the viewport. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of columns in different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).<br> .value[1].i32: whether to paginate by group.<br>**Since**: 22  |
| NODE_LIST_ITEM_SWIPE_ACTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM = 1004000 | Sets the swipe action item displayed when the list item is swiped out from the screen edge. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) object.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) object.|
| NODE_LIST_ITEM_GROUP_SET_HEADER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM_GROUP = 1005000 | Defines the header of the list item group. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) object used as the header of the list item group.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) object used as the header of the list item group.|
| NODE_LIST_ITEM_GROUP_SET_FOOTER = 1005001 | Defines the footer of the list item group. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) object used as the footer of the list item group.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) object used as the footer of the list item group.|
| NODE_LIST_ITEM_GROUP_SET_DIVIDER = 1005002 | Defines the style of the divider for the list items. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].u32: color of the divider, in 0xARGB format. The default value is **0x08000000**.<br> .value[1].f32: stroke width of the divider, in vp.<br> .value[2].f32: distance between the divider and the start of the list, in vp. The default value is **0**.<br> .value[3].f32: distance between the divider and the end of the list, in vp. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].u32: color of the divider, in 0xARGB format.<br> .value[1].f32: stroke width of the divider, in vp.<br> .value[2].f32: distance between the divider and the start of the list, in vp.<br> .value[3].f32: distance between the divider and the end of the list, in vp.|
| NODE_LIST_ITEM_GROUP_CHILDREN_MAIN_SIZE = 1005003 | Sets the default main axis size of the **ListItemGroup** child components.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> object: [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) object.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) object.|
| NODE_LIST_ITEM_GROUP_NODE_ADAPTER = 1005004 | Defines the list item group adapter. The attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object used as the adapter.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object.<br>**Since**: 15  |
| NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN = 1006000 | Defines the horizontal alignment mode of child components in the column. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment).<br> Default value: **ARKUI_HORIZONTAL_ALIGNMENT_CENTER**<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment). |
| NODE_COLUMN_JUSTIFY_CONTENT = 1006001 | Defines the vertical alignment mode of child components in the **Column** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment).<br> Default value: **ARKUI_FLEX_ALIGNMENT_START**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment). |
| NODE_LINEAR_LAYOUT_SPACE = 1006002 | Sets the spacing between Column or Row child components. This attribute supports the attribute setting, resetting, and obtaining APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: spacing between child components, in vp. The default value is 0.<br> Value range: [0, +∞).<br> If an invalid value is set, the default value is used.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: spacing between child components, in vp.<br>**Since**: 23 |
| NODE_LINEAR_LAYOUT_REVERSE = 1006003 | Sets whether to reverse the arrangement of child components in the main axis direction in a column or row. This attribute supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to reverse the arrangement of child components in the main axis direction. The default value is false. If the value is true, child components are arranged in reverse order in the vertical direction. If the value is false, child components are arranged in ascending order in the vertical direction.<br> If an invalid value is set, the default value is used.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to reverse the arrangement of child components in the main axis direction.<br>**Since**: 23 |
| NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW = 1007000 | Defines the vertical alignment mode of child components in the **Row** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment).<br> Default value: **ARKUI_VERTICAL_ALIGNMENT_CENTER**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment). |
| NODE_ROW_JUSTIFY_CONTENT = 1007001 | Defines the horizontal alignment mode of child components in the **Row** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment).<br> Default value: **ARKUI_FLEX_ALIGNMENT_START**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment).  |
| NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX = 1008000 | Sets **Flex** attributes, which can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0]?.i32: direction in which child components are arranged within the **Flex** container. The parameter type is [ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection). The default value is **ARKUI_FLEX_DIRECTION_ROW**.<br> .value[1]?.i32: wrapping rule [ArkUI_FlexWrap](capi-native-type-h.md#arkui_flexwrap). The default value is **ARKUI_FLEX_WRAP_NO_WRAP**.<br> .value[2]?.i32: alignment mode along the main axis. The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment). The default value is **ARKUI_FLEX_ALIGNMENT_START**.<br> .value[3]?.i32: alignment mode along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment). The default value is **ARKUI_ITEM_ALIGNMENT_START**.<br> **.value[4]?.i32**: alignment mode for multi-line content when there is extra space in the cross axis. The parameter type is [ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment). The default value is **ARKUI_FLEX_ALIGNMENT_START**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: direction in which child components are arranged within the **Flex** container.<br> .value[1].i32: wrapping rule.<br> .value[2].i32: alignment mode along the main axis.<br> .value[3].i32: alignment mode along the cross axis.<br> .value[4].i32: alignment mode for multi-line content when there is extra space in the cross axis. |
| NODE_FLEX_SPACE = 1008001 | Sets the spacing between child components in a Flex container. This API supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: spacing between child components in the main axis direction of the Flex container, in vp. The default value is 0.<br> Value range: [0, +∞).<br> If an invalid value is set, the default value is used.<br>.value[1].f32: spacing between child components in the cross axis direction of the Flex container, in vp. The default value is 0.<br> Value range: [0, +∞).<br> If an invalid value is set, the default value is used.<br>Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: spacing in the main axis direction of the Flex container, in vp.<br>.value[1].f32: spacing in the cross axis direction of the Flex container, in vp.<br>**Since**: 23 |
| NODE_REFRESH_REFRESHING = MAX_NODE_SCOPE_NUM * ARKUI_NODE_REFRESH = 1009000 | Sets whether the component is being refreshed. This attribute can be set and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the component is being refreshed. **1**: being refreshed. **0**: not being refreshed. The default value is **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the component is being refreshed. **1**: being refreshed. **0**: not being refreshed.|
| NODE_REFRESH_CONTENT = 1009001 | Sets the custom content in the pull-down area. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: custom content. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). |
| NODE_REFRESH_PULL_DOWN_RATIO = 1009002 | Sets the pull-down follow ratio. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: pull-down follow ratio. The value is in the range from 0 to 1.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: pull-down follow ratio. The value is in the range from 0 to 1.  |
| NODE_REFRESH_OFFSET = 1009003 | Sets the pull-down offset that triggers refresh. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: pull-down offset, in vp. The default value is 64 vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: pull-down offset, in vp. The default value is 64 vp.  |
| NODE_REFRESH_PULL_TO_REFRESH = 1009004 | Sets whether to initiate a refresh when the pull-down distance exceeds the value of **refreshOffset**. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether to trigger a refresh. The value can be 0 or 1. The value 1 indicates that the refresh is triggered, and the value 0 indicates that the refresh is not triggered. Default value: **1**<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether to initiate a refresh. The value **1** means to initiate a refresh, and **0** means the opposite.|
| NODE_REFRESH_MAX_PULL_DOWN_DISTANCE = 1009005 | Sets the maximum pull-down distance for refreshing. This attribute can be set, reset, and obtained through the API as required. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: maximum pull-down distance, in vp.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: maximum pull-down distance, in vp.<br>**Since**: 20  |
| NODE_REFRESH_PULL_UP_TO_CANCEL_REFRESH  = 1009006 | Whether to enable the pull-up-to-cancel gesture for refreshing operations. Attribute setting, resetting, and obtaining are supported. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: indicates whether to cancel the refresh when the user swipes up. The value can be 0 or 1. The value 0 indicates that the refresh is not canceled when the user swipes up, and the value 1 indicates that the refresh is canceled when the user swipes up. Default value: **1**<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: indicates whether to cancel the refresh when the user swipes up. The value 0 indicates that the refresh is not canceled when the user swipes up, and the value 1 indicates that the refresh is canceled when the user swipes up.<br>**Since**: 23  |
| NODE_WATER_FLOW_LAYOUT_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_WATER_FLOW = 1010000 | Defines the main axis direction of the **WaterFlow** component layout. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32 main axis direction. The parameter type is [ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection). Default value: **ARKUI_FLEX_DIRECTION_COLUMN**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32 main axis direction. The parameter type is [ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection).|
| NODE_WATER_FLOW_COLUMN_TEMPLATE = 1010001 | Sets the number of columns in the water flow layout. If this parameter is not set, one column is used by default. This attribute can be set, reset, and obtained as required through APIs. For example, **'1fr 1fr 2fr'** indicates three columns, with the first column taking up 1/4 of the parent component's full width, the second column 1/4, and the third column 2/4. You can use **columnsTemplate('repeat(auto-fill,track-size)')** to automatically calculate the number of rows based on the specified row height **track-size**. **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: number of columns in the layout. Default value: **'1fr'**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: number of columns in the layout. |
| NODE_WATER_FLOW_ROW_TEMPLATE = 1010002 | Sets the number of rows in the water flow layout. If this parameter is not set, one row is used by default. This attribute can be set, reset, and obtained as required through APIs. For example, **'1fr 1fr 2fr'** indicates three rows, with the first row taking up 1/4 of the parent component's full height, the second row 1/4, and the third row 2/4. You can use **rowsTemplate('repeat(auto-fill,track-size)')** to automatically calculate the number of rows based on the specified row height **track-size**. **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: number of rows in the layout. Default value: **'1fr'**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: number of rows in the layout. |
| NODE_WATER_FLOW_COLUMN_GAP = 1010003 | Sets the gap between columns. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: gap between columns, in vp. The default value is **0**. Value range: [0, +∞).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: gap between columns, in vp.|
| NODE_WATER_FLOW_ROW_GAP = 1010004 | Sets the gap between rows. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: gap between rows, in vp. The default value is **0**. Value range: [0, +∞).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: gap between rows, in vp.|
| NODE_WATER_FLOW_SECTION_OPTION = 1010005 | Defines the water flow section configuration. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: zero-based index of the water flow item section to update. The value is converted to an integer.<br> .object: [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) object.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) object.|
| NODE_WATER_FLOW_NODE_ADAPTER = 1010006 | Defines the **WaterFlow** component adapter. The attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object used as the adapter.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object. |
| NODE_WATER_FLOW_CACHED_COUNT = 1010007 | Sets the number of cached items in the **WaterFlow** component adapter. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of cached items in the **WaterFlow** component adapter.<br> .value[1]?.i32: whether to show cached items. The value **0** means to hide cached items, and **1** means to show cached items. The default value is **0**. This parameter is supported since API version 16.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: number of cached items in the list adapter.<br> .value[1].i32: whether to show cached items. The value **0** means to hide cached items, and **1** means to show cached items. This parameter is supported since API version 16. |
| NODE_WATER_FLOW_FOOTER = 1010008 | Sets the custom footer for the **WaterFlow** component. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: custom content. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).  |
| NODE_WATER_FLOW_SCROLL_TO_INDEX = 1010009 | Scrolls to the item with the specified index. When **smooth** is set to **true**, all passed items are loaded and counted in layout calculation. This may result in performance issues if a large number of items are involved.<br><br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: index of the item to be scrolled to in the container.<br> .value[1]?.i32: whether to enable the smooth animation for scrolling to the item with the specified index. The value **1** means to enable the animation, and **0** means the opposite. The default value is **0**.<br> .value[2]?.i32: how the item to scroll to is aligned with the container. The parameter type is [ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment). The default value is **ARKUI_SCROLL_ALIGNMENT_START**.<br>.value[3]?.f32: extra offset after the target element is scrolled, in vp. The default value is 0. A positive value offsets the scroll position downward (or toward the end); a negative value offsets it upward (or toward the start). This parameter is supported since API version 23.|
| NODE_WATER_FLOW_ITEM_CONSTRAINT_SIZE = 1010010 | Defines the size constraints to apply to water flow items. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: minimum width. The value **-1** indicates that the minimum width is not set. <br> .value[1].f32: maximum width. The value **-1** indicates that the maximum width is not set. <br> .value[2].f32: minimum height. The value **-1** indicates that the minimum height is not set. <br> .value[3].f32: maximum height. The value **-1** indicates that the maximum height is not set. <br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: minimum width. The value **-1** indicates that the minimum width is not set. <br> .value[1].f32: maximum width. The value **-1** indicates that the maximum width is not set. <br> .value[2].f32: minimum height. The value **-1** indicates that the minimum height is not set. <br> .value[3].f32: maximum height. The value **-1** indicates that the maximum height is not set.  |
| NODE_WATER_FLOW_LAYOUT_MODE = 1010011 | Sets the layout mode for this **WaterFlow** component. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: layout mode. The parameter type is [ArkUI_WaterFlowLayoutMode](capi-native-type-h.md#arkui_waterflowlayoutmode). The default value is **ARKUI_WATER_FLOW_LAYOUT_MODE_ALWAYS_TOP_DOWN**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: layout mode. The parameter type is [ArkUI_WaterFlowLayoutMode](capi-native-type-h.md#arkui_waterflowlayoutmode).<br>**Since**: 18  |
| NODE_WATER_FLOW_SYNC_LOAD = 1010012 | Defines whether the **WaterFlow** component loads child nodes synchronously. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the **WaterFlow** component synchronously loads child nodes. **0**: frame-by-frame loading. **1**: synchronous loading. Default value: **1**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the **WaterFlow** component synchronously loads child nodes. **0**: frame-by-frame loading. **1**: synchronous loading.<br>**Since**: 20  |
| NODE_WATER_FLOW_COLUMN_TEMPLATE_ITEMFILLPOLICY  = 1010013 | Sets the responsive column layout policy for the **WaterFlow** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).<br>**Since**: 22  |
| NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER = 1012000 | Sets the guideline in the **RelativeContainer** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: guideline in the **RelativeContainer** component.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: guideline in the **RelativeContainer** component. |
| NODE_RELATIVE_CONTAINER_BARRIER = 1012001 | Sets the barrier in the **RelativeContainer** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: guideline in the **RelativeContainer** component.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: barrier in the **RelativeContainer** component.  |
| NODE_GRID_COLUMN_TEMPLATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID = 1013000 | Sets the number of columns in the **Grid** component. If this parameter is not set, one column is used by default. This attribute can be set, reset, and obtained as required through APIs. For example, **'1fr 1fr 2fr'** indicates three columns, with the first column taking up 1/4 of the parent component's full width, the second column 1/4, and the third column 2/4. You can use **columnsTemplate('repeat(auto-fill,track-size)')** to automatically calculate the number of rows based on the specified row height **track-size**. **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: number of columns in the layout.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: number of columns in the layout.|
| NODE_GRID_ROW_TEMPLATE = 1013001 | Sets the number of rows or the minimum row height in the **Grid** component. If this parameter is not set, one row is used by default. This attribute can be set, reset, and obtained as required through APIs. For example, **'1fr 1fr 2fr'** indicates three rows, with the first row taking up 1/4 of the parent component's full height, the second row 1/4, and the third row 2/4. You can use **rowsTemplate('repeat(auto-fill,track-size)')** to automatically calculate the number of rows based on the specified row height **track-size**. **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .string: number of rows in the layout.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .string: number of rows in the layout.|
| NODE_GRID_COLUMN_GAP = 1013002 | Sets the gap between columns. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: gap between columns, in vp. The default value is **0**. Value range: [0, +∞).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: gap between columns, in vp.|
| NODE_GRID_ROW_GAP = 1013003 | Sets the gap between rows. This attribute can be set, reset, and obtained as required through APIs. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: gap between rows, in vp. The default value is **0**. Value range: [0, +∞).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].f32: gap between rows, in vp.|
| NODE_GRID_NODE_ADAPTER = 1013004 | Defines the **Grid** component adapter. The attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object used as the adapter.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object.|
| NODE_GRID_CACHED_COUNT = 1013005 | Sets the number of cached items in the **Grid** component adapter. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of cached items in the **Grid** component adapter.|
| NODE_GRID_FOCUS_WRAP_MODE = 1013006 | Defines the focus wrap mode for the **Grid** component. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: focus wrap mode of the **Grid** component. The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode). The default value is **FOCUS_WRAP_MODE_DEFAULT**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: focus wrap mode of the **Grid** component. The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode).<br>**Since**: 20 |
| NODE_GRID_SYNC_LOAD = 1013007 | Defines whether the **Grid** component loads child nodes synchronously. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the **Grid** component synchronously loads child nodes. **0**: frame-by-frame loading. **1**: synchronous loading. Default value: **1**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the **Grid** component synchronously loads child nodes. **0**: frame-by-frame loading. **1**: synchronous loading.<br>**Since**: 20  |
| NODE_GRID_ALIGN_ITEMS = 1013008 | Sets the alignment mode of GridItem in a grid. This API supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: alignment mode of GridItem in a grid. The parameter type is [ArkUI_GridItemAlignment](capi-native-type-h.md#arkui_griditemalignment). The default value is **GRID_ITEM_ALIGNMENT_DEFAULT**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: alignment mode of GridItem in a grid. The parameter type is [ArkUI_GridItemAlignment](capi-native-type-h.md#arkui_griditemalignment).<br>**Since**: 22  |
| NODE_GRID_LAYOUT_OPTIONS = 1013009 | Sets the grid layout options. This API supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: The parameter format is [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .object: The return value format is [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md).<br>**Since**: 22 |
| NODE_GRID_COLUMN_TEMPLATE_ITEMFILLPOLICY = 1013010 | Defines the layout policy of the number of columns in the Grid component. This class supports APIs for setting, resetting, and obtaining attributes.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).<br>**Since**: 22  |
| NODE_GRID_EDIT_MODE = 1013011 | Indicates whether the Grid component enters the editing mode. You can drag a GridItem by using the NODE_GRID_ON_ITEM_DRAG_START event. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the Grid component enters the editing mode. **0**: Disable edit mode. **1**: Enable edit mode. Default value: **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the Grid component enters the editing mode. **0**: Disable edit mode. **1**: Enable edit mode.<br>**Since**: 23  |
| NODE_GRID_DRAG_ANIMATION = 1013012 | Indicates whether to enable the drag animation for GridItems in the Grid component. This attribute can be set, reset, and obtained as required through APIs.<br>The animation is supported only when the scrolling mode is used (only one of NODE_GRID_ROW_TEMPLATE and NODE_GRID_COLUMN_TEMPLATE is set).<br>Drag animations are only supported in grids with fixed size rules; scenarios involving spanning across rows or columns are not supported.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: indicates whether to enable the drag animation of GridItem for the Grid component. **0**: Disable mouse-based multi-selection. **1**: Enable mouse-based multi-selection. Default value: **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: indicates whether to enable the drag animation of GridItem for the Grid component. **0**: Disable mouse-based multi-selection. **1**: Enable mouse-based multi-selection.<br>**Since**: 23  |
| NODE_GRID_MULTI_SELECTABLE = 1013013 | Indicates whether to enable the mouse selection box for the Grid component. This attribute can be set, reset, and obtained as required through APIs.<br>After this function is enabled, the NODE_GRID_ITEM_EVENT_ON_SELECT event of GridItem is triggered when the mouse selection box is used within the Grid component.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: indicates whether to enable the mouse selection box for the Grid component. **0**: Disable mouse-based multi-selection. **1**: Enable mouse-based multi-selection. Default value: **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: indicates whether to enable the mouse selection box for the Grid component. **0**: Disable mouse-based multi-selection. **1**: Enable mouse-based multi-selection.<br>**Since**: 23  |
| NODE_GRID_SCROLL_TO_INDEX = 1013014 | Scrolls to the item with the specified index.<br>When animation is enabled, all passed child components are loaded and counted in layout calculation. This may result in performance issues if a large number of child components are involved.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: index of the item to be scrolled to in the container.<br> .value[1]?.i32: whether to display an animation when scrolling to the target element. 1: yes; 0: no. Default value: **0**.<br> .value[2]?.i32: how the target item to scroll to is aligned with the container. The parameter type is [ArkUI_ScrollAlignment](capi-native-type-h.md#arkui_scrollalignment). The default value is **ARKUI_SCROLL_ALIGNMENT_AUTO**.<br>.value[3]?.f32: extra offset after the target element is scrolled to, in vp. The default value is 0. A positive value offsets the scroll position downward (or toward the end); a negative value offsets it upward (or toward the start).<br>**Since**: 23|
| NODE_GRID_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1013015 | Sets whether the current Grid component supports the use of the if/else rendering control syntax in LazyForEach or Repeat to generate empty branch nodes that do not contain any child components.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: indicates whether the Grid component supports empty branches. 0: no; 1: yes. Default value: **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: indicates whether the Grid component supports empty branches. 0: no; 1: yes.<br>**Since**: 23  |
|  NODE_GRID_ITEM_STYLE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID_ITEM = 1014000 | Sets the GridItem style, and supports attribute setting, resetting, and obtaining.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: GridItem style. The parameter type is [ArkUI_GridItemStyle](capi-native-type-h.md#arkui_griditemstyle). The default value is **GRID_ITEM_STYLE_NONE**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: GridItem style. The parameter type is [ArkUI_GridItemStyle](capi-native-type-h.md#arkui_griditemstyle).<br>**Since**: 22  |
|  NODE_GRID_ITEM_SELECTABLE = 1014001 | Sets whether a GridItem can be selected by the mouse. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: indicates whether a GridItem can be selected by the mouse. **0**: not selectable. **1**: selectable. Default value: **1**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: indicates whether a GridItem can be selected by the mouse. **0**: not selectable. **1**: selectable.<br>**Since**: 23  |
|  NODE_GRID_ITEM_SELECTED = 1014002 | Sets the selection status of a GridItem. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: selection status of a GridItem. **0**: not selected. **1**: selected. Default value: **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: selection status of a GridItem. **0**: not selected. **1**: selected.<br>**Since**: 23  |
| NODE_TEXT_PICKER_COLUMN_WIDTHS = 15009 | Sets the width of columns in the picker. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].f32: width of the first column, specified as a percentage of the total width. By default, all columns have equal widths.<br> .value[1]?.f32: width of the second column, specified as a percentage of the total width. By default, all columns have equal widths.<br> .value[2]?.f32: width of the third column, specified as a percentage of the total width. By default, all columns have equal widths.<br> ...<br> .value[n]?.f32: width of the (n+1)-th column, specified as a percentage of the total width. By default, all columns have equal widths.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> value[0].f32: width of the first column as a percentage of the total width.<br> value[1].f32: width of the second column as a percentage of the total width.<br> value[2].f32: width of the third column as a percentage of the total width.<br> ...<br> value[n].f32: width of the (n+1)-th column as a percentage of the total width.<br>**Since**: 18 |
| NODE_IMAGE_ANIMATOR_IMAGES = ARKUI_NODE_IMAGE_ANIMATOR * MAX_NODE_SCOPE_NUM = 19000 | Sets the image frame information set of the frame animation component. Dynamic update is not supported. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .size: number of image frames.<br> .object: image frame array. The parameter type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .size: number of image frames.<br> .object: image frame array. The parameter type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md). |
| NODE_IMAGE_ANIMATOR_STATE = 19001 | Sets the playback status of the frame-by-frame animation. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: playback state of the frame-by-frame animation. The parameter type is [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus). The default state is initial.<br>     Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: playback state of the frame-by-frame animation. The parameter type is [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus).  |
| NODE_IMAGE_ANIMATOR_DURATION = 19002 | Sets the playback duration of the frame-by-frame animation. This attribute does not take effect when a separate duration is set for any of the image frames. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: playback duration, in ms. The default value is **1000**.<br>     Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: playback duration, in ms. The default value is **1000**. |
| NODE_IMAGE_ANIMATOR_REVERSE = 19003 | Sets the playback direction of the frame-by-frame animation. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: playback direction. The value **0** indicates that images are played from the first one to the last one, and **1** indicates that images are played from the last one to the first one. The default value is **0**.<br>     Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: playback direction. The value **0** indicates that images are played from the first one to the last one, and **1** indicates that images are played from the last one to the first one. |
| NODE_IMAGE_ANIMATOR_FIXED_SIZE = 19004 | Sets whether the image size is fixed at the component size. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: whether the image size is the fixed at the component size. The value **1** indicates that the image size is fixed at the component size. The value **0** indicates that the **width**, **height**, **top**, and **left** attributes of each image must be set separately. The default value is **1**.<br>     Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: whether the image size is the fixed at the component size. The value **1** indicates that the image size is fixed at the component size. The value **0** indicates that the **width**, **height**, **top**, and **left** attributes of each image must be set separately. |
| NODE_IMAGE_ANIMATOR_FILL_MODE = 19005 | Sets the status before and after execution of the frame-by-frame animation in the current playback direction. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: status before and after execution of the frame-by-frame animation in the current playback direction. The parameter type is [ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode). The default value is **ARKUI_ANIMATION_FILL_MODE_FORWARDS**.<br>     Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: status before and after execution of the frame-by-frame animation in the current playback direction. The parameter type is [ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode). |
| NODE_IMAGE_ANIMATOR_ITERATION = 19006 | Sets the number of times that the frame-by-frame animation is played. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .value[0].i32: number of times that the animation is played.<br>     Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br> .value[0].i32: number of times that the animation is played.  |
| NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT = 1016000 | Defines the want used to launch an EmbeddedAbility. This attribute can be set.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: want parameter for the **EmbeddedComponent**. The parameter type is [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md). The default value is **nullptr**.<br>**Since**: 20  |
| NODE_EMBEDDED_COMPONENT_OPTION = 1016001 | Options of **EmbeddedComponent**. This attribute can be set.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br> .object: list of options for the **EmbeddedComponent**. The parameter type is [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md).<br>**Since**: 20  |
| NODE_PICKER_OPTION_SELECTED_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER |Index of the default selected item in the picker's selection range. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.value[0].u32: index value.<br>Default value: **0**.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].u32: index value.<br>**Since**: 23  |
| NODE_PICKER_ENABLE_HAPTIC_FEEDBACK = 1018001 |Defines whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.value[0].i32: whether to enable haptic feedback.<br>- **true**: Enable haptic feedback.<br>- **false**: Disable haptic feedback.<br>The default value is **true**. After this function is enabled, whether haptic feedback is available depends on the hardware support of the system.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].i32: whether to enable feedback.<br>**Since**: 23  |
| NODE_PICKER_CAN_LOOP = 1018002 |Defines whether the picker supports looping. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.value[0].i32: whether to support scrolling cycling.<br>- true: Scrolling cycling is supported.<br>- false: Scrolling cycling is not supported.<br>Default value: **true**.<br>If the number of child components is less than 8, the scrolling cycling is not performed regardless of whether this attribute is set to true or false.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.value[0].i32: whether to support scrolling cycling. The value <b>true</b> indicates that scrolling cycling is supported, and <b>false</b> indicates that scrolling cycling is not supported.<br>**Since**: 23  |
| NODE_PICKER_SELECTION_INDICATOR = 1018003 | Sets the type and parameters of the selection indicator. This attribute can be set, reset, and obtained as required through APIs.<br>Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:<br>.object: The parameter type is [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md).<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):<br>.object: The parameter type is [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md).<br>**Since**: 23  |

### ArkUI_NodeEventType

```c
enum ArkUI_NodeEventType
```

**Description**


Enumerates the event types supported by the **NativeNode** component.

**Since**: 12

<!--Table: 30%; 70%-->
| Value| Description |
| -- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| NODE_TOUCH_EVENT = 0 | Gesture event. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).|
| NODE_EVENT_ON_APPEAR = 1 | Mount event. This event is triggered when the component is mounted and displayed.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.|
| NODE_EVENT_ON_DISAPPEAR = 2 | Unmount event. This event is triggered when the component is unmounted from the component tree and disappears.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.|
| NODE_EVENT_ON_AREA_CHANGE = 3 | Component area change event. This event is triggered when the component area changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> **ArkUI_NodeComponentEvent.data[0].f32**: original width of the target element, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[1].f32**: original height of the target element, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[2].f32**: original x-coordinate of the target element's upper left corner relative to the parent element's, in vp. The value type is number.<br> ArkUI_NodeComponentEvent.data[3].f32: original y-coordinate of the target element's upper left corner relative to the parent element's, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[4].f32**: original x-coordinate of the target element's upper left corner relative to the page's, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[5].f32**: original y-coordinate of the target element's upper left corner relative to the page's, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[6].f32**: new width of the target element, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[7].f32**: new height of the target element, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[8].f32**: new x-coordinate of the target element's upper left corner relative to the parent element's, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[9].f32**: new y-coordinate of the target element's upper left corner relative to the parent element's, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[10].f32**: new x-coordinate of the target element's upper left corner relative to the page's, in vp. The value type is number.<br> **ArkUI_NodeComponentEvent.data[11].f32**: new y-coordinate of the target element's upper left corner relative to the page's, in vp. The value type is number.|
| NODE_ON_FOCUS = 4 | Event of obtaining focus. This event is triggered when the component obtains the focus.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_ON_BLUR = 5 | Event of losing focus. This event is triggered when the component loses the focus.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.|
| NODE_ON_CLICK = 6 | Click event. This event is triggered when the component is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: x-coordinate of the click relative to the upper left corner of the clicked component's original area, in vp.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: y-coordinate of the click relative to the upper left corner of the clicked component's original area, in vp.<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: event timestamp. It is the interval between the time when the event is triggered and the time when the system starts, in microseconds.<br> <b>ArkUI_NodeComponentEvent.data[3].i32</b>: event input device. The value **1** indicates the mouse, **2** indicates the touchscreen, and **4** indicates the key.<br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>: x-coordinate of the click relative to the upper left corner of the application window, in vp.<br> <b>ArkUI_NodeComponentEvent.data[5].f32</b>: y-coordinate of the click relative to the upper left corner of the application window, in vp.<br> <b>ArkUI_NodeComponentEvent.data[6].f32</b>: x-coordinate of the click relative to the upper left corner of the application screen, in vp.<br> <b>ArkUI_NodeComponentEvent.data[7].f32</b>: y-coordinate of the click relative to the upper left corner of the application screen, in vp. |
| NODE_ON_TOUCH_INTERCEPT = 7 | Custom component event interception. This event is triggered when the component is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md). |
| NODE_EVENT_ON_VISIBLE_AREA_CHANGE = 8 | Visible area change event. This event is triggered when the ratio of the component's visible area to its total area is greater than or less than the threshold. Before registering the event, you need to use **NODE_VISIBLE_AREA_CHANGE_RATIO** to configure the threshold.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: whether the component's visible area has increased or decreased relative to its total area since the last update. The value **1** indicates that the visible area has increased, and **0** indicates that the visible area has decreased.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total area when this callback is invoked. |
| NODE_ON_HOVER = 9 | Event triggered when the mouse pointer is moved over or away from the component.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: whether the mouse pointer is hovered over the component. The value **1** indicates that the mouse pointer is hovered over the component, and **0** indicates that the mouse pointer is moved away from the component. |
| NODE_ON_MOUSE = 10 | Click event. This event is triggered when the component is clicked by a mouse device button or when the mouse pointer moves within the component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).|
| NODE_EVENT_ON_ATTACH = 11 | Attach event. This event is triggered when the component is attached to the component tree.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.|
| NODE_EVENT_ON_DETACH = 12 | Detach event. This event is triggered when the component is detached from the component tree.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_ON_ACCESSIBILITY_ACTIONS = 13 | Accessibility-supported action event. This event is triggered when an accessibility action is performed after the corresponding accessibility action type is set.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].u32</b>: action type that triggers the callback. The parameter type is [ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype).  |
| NODE_ON_PRE_DRAG = 14 | Notifies the listener of the interaction state prior to a drop and drop operation. This event is triggered when a component is draggable and when a long press, lift, or drag initiation occurs.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: corresponds to [ArkUI_PreDragStatus](capi-drag-and-drop-h.md#arkui_predragstatus).  |
| NODE_ON_DRAG_START = 15 | Event triggered when the user starts to drag an item. A drag operation is recognized only when the dragged item is moved far enough.<br> When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_DRAG_ENTER = 16 | Event triggered when a dragged item enters the boundaries of the current component. The current component refers to the component that listens for this event.<br> When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.|
| NODE_ON_DRAG_MOVE = 17 | Event triggered when a dragged item moves in the current component. The current component refers to the component that listens for this event.<br> When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.   |
| NODE_ON_DRAG_LEAVE = 18 | Event triggered when a dragged item leaves the boundaries of the current component. The current component refers to the component that listens for this event.<br> When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_DROP = 19 | Event triggered when a dragged item is dropped on the current component. The component can obtain the drag data for processing through the callback. The current component refers to the component that listens for this event.<br> When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_DRAG_END = 20 | Event triggered when a drag operation ends. The drag source can obtain the drag result by registering this callback. A drag operation ends when the dragged item is released. When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. |
| NODE_ON_KEY_EVENT = 21 | Event triggered when a key event occurs. The callback can be triggered during interactions with a focused window using an external keyboard or other input device.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>**Since**: 14 |
| NODE_ON_KEY_PRE_IME = 22 | Event triggered before the input method responds to the key action. If the return value of this callback is **true**, the key event is considered consumed, and subsequent event callbacks (**keyboardShortcut**, input method events, **onKeyEvent**) will be intercepted and no longer triggered. The callback can be triggered during interactions with a focused window using an external keyboard or other input device.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>**Since**: 14    |
| NODE_ON_FOCUS_AXIS = 23 | Event triggered when the bound component receives a focus axis event after gaining focus. The event callback is triggered by interactions with a joystick and a focused component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).<br>**Since**: 15   |
| NODE_DISPATCH_KEY_EVENT = 24 | Component key event re-dispatch event. When a component node receives a key event, this callback is triggered instead of dispatching the event to its child nodes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>**Since**: 15   |
| NODE_ON_AXIS = 25 | Event triggered when the bound component receives an axis event. Defines the event triggered when the bound component receives an axis event.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).<br>**Since**: 17 |
| NODE_ON_HOVER_EVENT = 27 | Event triggered when the mouse pointer moves over or away from the component. This event is triggered when the mouse pointer moves over or away from a component.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).<br>  **Since**: 17 |
| NODE_ON_CLICK_EVENT = 26 | Event triggered when the bound component is clicked. This event is triggered when the bound component is tapped.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).<br>**Since**: 18  |
| NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT = 28 | Sets the callback for the NODE_EVENT_ON_VISIBLE_AREA_CHANGE event, which limits the callback interval. This event is triggered when the ratio of the component's visible area to its total area is greater than or less than the threshold. Before registering the event, you need to use **NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO** to configure the threshold and update interval.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: whether the component's visible area has increased or decreased relative to its total area since the last update. The value **1** indicates that the visible area has increased, and **0** indicates that the visible area has decreased.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total area when this callback is invoked.<br>**Since**: 17 |
| NODE_ON_HOVER_MOVE = 29 | Hover event. This event is triggered when the stylus pointer hovers over the component.<br> When the event callback occurs, the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.<br>**Since**: 15  |
| NODE_ON_SIZE_CHANGE = 30 | Size change event. This event is triggered when the component size changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: width of the component before the size change.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: height of the component before the size change.<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: width of the component after the size change.<br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>: height of the component after the size change.<br>**Since**: 21  |
| NODE_ON_COASTING_AXIS_EVENT = 31 | Defines the coasting axis event. When a user slides two fingers on the touchpad for a certain distance and quickly lifts the fingers, the system continuously constructs events based on the speed at which the fingers are lifted and a certain attenuation curve. You can listen to this type of events to handle the flicking effect after the normal scrolling axis event.<br> When the event callback occurs, you can obtain the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object by calling [OH_ArkUI_NodeEvent_GetInputEvent](#oh_arkui_nodeevent_getinputevent). Then, you can obtain the [ArkUI_CoastingAxisEvent](capi-arkui-nativemodule-arkui-coastingaxisevent.md) object from the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object by calling [OH_ArkUI_UIInputEvent_GetCoastingAxisEvent](capi-ui-input-event-h.md#oh_arkui_uiinputevent_getcoastingaxisevent). You can obtain more information from the object by calling the OH_ArkUI_CoastingAxisEvent_XXX series APIs.<br>**Since**: 22  |
| NODE_ON_CHILD_TOUCH_TEST = 32 | Defines the pre-touch test of a child component. This event is called to specify how to perform a touch test on the child component of the current component. This event is triggered when the component is touched.<br> When the event callback occurs, you can obtain the [ArkUI_TouchTestInfo](./capi-arkui-nativemodule-arkui-touchtestinfo.md) object from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object by calling [OH_ArkUI_NodeEvent_GetTouchTestInfo](#oh_arkui_nodeevent_gettouchtestinfo). and obtain the list of touch test items from the [ArkUI_TouchTestInfo](./capi-arkui-nativemodule-arkui-touchtestinfo.md) object through the [OH_ArkUI_TouchTestInfo_GetTouchTestInfoList](./capi-ui-input-event-h.md#oh_arkui_touchtestinfo_gettouchtestinfolist) API. You can obtain more information by using the [OH_ArkUI_TouchTestInfoItem_GetXXX](./capi-ui-input-event-h.md#oh_arkui_touchtestinfoitem_getx) series APIs. Use [OH_ArkUI_TouchTestInfo_SetTouchResultStrategy](./capi-ui-input-event-h.md#oh_arkui_touchtestinfo_settouchresultstrategy) to set the touch test policy. Use [OH_ArkUI_TouchTestInfo_SetTouchResultId](./capi-ui-input-event-h.md#oh_arkui_touchtestinfo_settouchresultid) to set the subcomponent to be affected during the hit test.<br>**Since**: 22 |
| NODE_TEXT_ON_DETECT_RESULT_UPDATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT = 1000 | Event triggered when text recognition with the configured **TextDataDetectorConfig** settings succeeds. This event is triggered when TextDataDetectorConfig is set and the recognition is successful.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameters:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text recognition result in JSON format. |
| NODE_TEXT_SPAN_ON_LONG_PRESS = 1001 | Long-press event for the span component. This callback is triggered when the component is long-pressed.<br> When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the **ArkUI_UIInputEvent** object.<br>**Since**: 20  |
| NODE_IMAGE_ON_COMPLETE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE = 4000 | Image loading success event. This event is triggered when an image is successfully loaded or decoded.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: loading status. The value **0** indicates that the image is loaded successfully, and **1** indicates that the image is decoded successfully.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: width of the image, in px.<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: height of the image, in px.<br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>: width of the component, in px.<br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>: height of the component, in px.<br> <b>ArkUI_NodeComponentEvent.data[5].f32</b>: offset of the rendered content relative to the component on the x-axis, in px.<br> <b>ArkUI_NodeComponentEvent.data[6].f32</b>: offset of the rendered content relative to the component on the y-axis, in px.<br> <b>ArkUI_NodeComponentEvent.data[7].f32</b>: actual rendered width of the image, in px.<br> <b>ArkUI_NodeComponentEvent.data[8].f32</b>: actual rendered height of the image, in px. |
| NODE_IMAGE_ON_ERROR = 4001 | Image loading failure event. This event is triggered when an error occurs during image loading.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: result code.<br> **401**: The image could not be obtained because the image path is invalid.<br> **103101**: The image format is not supported. |
| NODE_IMAGE_ON_SVG_PLAY_FINISH = 4002 | SVG animation playback completion event. This event is triggered when the animation playback in the loaded SVG image is complete.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_IMAGE_ON_DOWNLOAD_PROGRESS = 4003 | Event triggered during image download. This event is triggered when the page component downloads a web page image.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].u32</b>: number of bytes that have been downloaded.<br> <b>ArkUI_NodeComponentEvent.data[1].u32</b>: total number of bytes of the image to be downloaded. |
| NODE_TOGGLE_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE = 5000 | Event triggered when the toggle status changes. This event is triggered when the switch status changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: toggle status. **1**: on; **0**: off.  |
| NODE_TEXT_INPUT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT = 7000 | Event triggered when the text input content changes in the **TextInput** component.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameters:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text input. |
| NODE_TEXT_INPUT_ON_SUBMIT = 7001 | Event triggered when the **Enter** key on the keyboard is pressed for the **TextInput** component. This event is<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: type of the **Enter** key. |
| NODE_TEXT_INPUT_ON_CUT = 7002 | Event triggered when the cut button on the pasteboard, which displays when the text box is long pressed, is clicked. Condition for triggering this event: You touch and hold the internal area of the text box to display the clipboard and then click the cut button on the clipboard.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameters:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is cut.  |
| NODE_TEXT_INPUT_ON_PASTE = 7003 | Event triggered when the paste button on the pasteboard, which displays when the text box is long pressed, is clicked. Condition for triggering this event: You touch and hold the internal area of the text box to display the clipboard and then click the paste button on the clipboard.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameters:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is pasted.  |
| NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE = 7004 | Event triggered when the text selection position changes. Condition for triggering this event: The selected text position changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: start position of the text selection area.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: end position of the text selection area. |
| NODE_TEXT_INPUT_ON_EDIT_CHANGE = 7005 | Event triggered when the input status changes. This event is triggered when the input status changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: **true** indicates that text input is in progress.  |
| NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR = 7006 | Defines the event triggered when matching with the regular expression specified by **NODE_TEXT_INPUT_INPUT_FILTER** fails. This event is triggered when the regular expression matching fails.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameters:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: content that is filtered out when regular expression matching fails.|
| NODE_TEXT_INPUT_ON_CONTENT_SCROLL = 7007 | Event triggered when the text content is scrolled.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: offset in the x-coordinate of the text in the content area.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: offset in the y-coordinate of the text in the content area. |
| NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE = 7008 | Event triggered when the text input content changes in the **TextInput** component.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: width of the text.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: height of the text. |
| NODE_TEXT_INPUT_ON_WILL_INSERT = 7009 | Event triggered when text is about to be entered. When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).<br> value.f32: position of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br> buffer: string value of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetStringValue**. |
| NODE_TEXT_INPUT_ON_DID_INSERT = 7010 | Event triggered when input is completed. When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).<br> value.f32: position of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br> buffer: string value of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetStringValue**. |
| NODE_TEXT_INPUT_ON_WILL_DELETE = 7011 | Event triggered when text is about to be deleted. When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).<br> value.f32: position of the text deleted, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br> value.i32: direction for deleting the text, with the index of **1**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**. The value **0** indicates backward-delete, and **1** indicates forward-delete.<br> buffer: string value of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetStringValue**.  |
| NODE_TEXT_INPUT_ON_DID_DELETE = 7012 | Event triggered when deletion is completed. When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).<br> value.f32: position of the text deleted, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br> value.i32: direction for deleting the text, with the index of **1**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**. The value **0** indicates backward-delete, and **1** indicates forward-delete.<br> buffer: string value of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetStringValue**. |
| NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT = 7013 | Event triggered when content (including preview text) changes in the **TextInput** component. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md).<br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:<br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the **TextInput** component.<br> <b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the **TextInput** component.<br> <b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the **TextInput** component.<br>**Since**: 15   |
| NODE_TEXT_INPUT_ON_WILL_CHANGE = 7014 | Event triggered when content (including preview text) is about to change in the **TextInput** component. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md).<br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:<br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the **TextInput** component.<br> <b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the **TextInput** component.<br> <b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the **TextInput** component.<br>**Since**: 20  |
| NODE_TEXT_AREA_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA = 8000 | Event triggered when the input in the text box changes.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameters:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: current text input.|
| NODE_TEXT_AREA_ON_PASTE = 8001 | Event triggered when the paste button on the pasteboard, which displays when the text box is long pressed, is clicked. Condition for triggering this event: You touch and hold the internal area of the text box to display the clipboard and then click the paste button on the clipboard.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameters:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: text that is pasted. |
| NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE = 8002 | Event triggered when the text selection position changes. Condition for triggering this event: The selected text position changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: start position of the text selection area.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: end position of the text selection area.|
| NODE_TEXT_AREA_ON_EDIT_CHANGE = 8003 | Event triggered when the input status changes. This event is triggered when the input status changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: **true** indicates that text input is in progress. |
| NODE_TEXT_AREA_ON_SUBMIT = 8004 | Event triggered when the **Enter** key on the keyboard is pressed for the **TextArea** component. This event is not triggered when **keyType** is **ARKUI_ENTER_KEY_TYPE_NEW_LINE**.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: type of the **Enter** key. |
| NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR = 8005 | Defines the event triggered when matching with the regular expression specified by **NODE_TEXT_AREA_INPUT_FILTER** fails. Condition for triggering this event: The regular expression matching fails.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameters:<br> <b>ArkUI_StringAsyncEvent.pStr</b>: content that is filtered out when regular expression matching fails.|
| NODE_TEXT_AREA_ON_CONTENT_SCROLL = 8006 | Event triggered when the text content is scrolled.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: offset in the x-coordinate of the text in the content area.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: offset in the y-coordinate of the text in the content area. |
| NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE = 8007 | Event triggered when the text input content changes in the **TextArea** component.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: width of the text.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: height of the text.|
| NODE_TEXT_AREA_ON_WILL_INSERT = 8008 | Event triggered when text is about to be entered. When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).<br> value.f32: position of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br> buffer: string value of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetStringValue**. |
| NODE_TEXT_AREA_ON_DID_INSERT = 8009 | Event triggered when input is completed. When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).<br> value.f32: position of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br> buffer: string value of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetStringValue**.  |
| NODE_TEXT_AREA_ON_WILL_DELETE = 8010 | Event triggered when text is about to be deleted. When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).<br> value.f32: position of the text deleted, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br> value.i32: direction for deleting the text, with the index of **1**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**. The value **0** indicates backward-delete, and **1** indicates forward-delete.<br> buffer: string value of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetStringValue**. |
| NODE_TEXT_AREA_ON_DID_DELETE = 8011 | Event triggered when deletion is completed. When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).<br> value.f32: position of the text deleted, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br> value.i32: direction for deleting the text, with the index of **1**; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**. The value **0** indicates backward-delete, and **1** indicates forward-delete.<br> buffer: string value of the text, with the index of **0**; obtained using **OH_ArkUI_NodeEvent_GetStringValue**.|
| NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT = 8012 | Event triggered when content (including preview text) changes in the **TextArea** component. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md).<br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:<br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the **TextArea** component.<br> <b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the **TextArea** component.<br> <b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the **TextArea** component.<br>**Since**: 15 |
| NODE_TEXT_AREA_ON_WILL_CHANGE = 8013 | Event triggered when content (including preview text) is about to change in the **TextArea** component. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md).<br> [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:<br> <b>ArkUI_TextChangeEvent.pStr</b>: content in the **TextArea** component.<br> <b>ArkUI_TextChangeEvent.pExtendStr</b>: content of the preview text in the **TextArea** component.<br> <b>ArkUI_TextChangeEvent.number</b>: start position of the preview text in the **TextArea** component.<br>**Since**: 20   |
| NODE_CHECKBOX_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX = 11000 | Event triggered when the selected status of the **ARKUI_NODE_CHECKBOX** component changes. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: **1**: selected. **0**: not selected.  |
| NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER = 13000 | Event triggered when a date is selected in the **ARKUI_NODE_DATE_PICKER** component.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: year of the selected date.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: month of the selected date. Value range: [0-11].<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: day of the selected date.  |
| NODE_TIME_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER = 14000 | Event triggered when a time is selected in the **ARKUI_NODE_TIME_PICKER** component.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: hour of the selected time. Value range: [0-23].<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: minute of the selected time. Value range: [0-59].  |
| NODE_TEXT_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER = 15000 | Event triggered when an item is selected in the **ARKUI_NODE_TEXT_PICKER** component.  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0...11].i32</b>: value of the selected item.|
| NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP = 15001 | Event triggered when an item is selected in the **ARKUI_NODE_TEXT_PICKER** component. This event is triggered when the user stops sliding to select a text item.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0...11].i32</b>: value of the selected item.<br>**Since**: 14|
| NODE_CALENDAR_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER = 16000 | Event triggered when a date is selected in the **NODE_CALENDAR_PICKER** component. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> <b>ArkUI_NodeComponent.data[0].u32</b>: year of the selected date.<br> <b>ArkUI_NodeComponent.data[1].u32</b>: month of the selected date.<br> <b>ArkUI_NodeComponent.data[2].u32</b>: day of the selected date.|
| NODE_SLIDER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER = 17000 | Event triggered when the **ARKUI_NODE_SLIDER** component is dragged or clicked. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: current slider value.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: state triggered by the event. |
| NODE_RADIO_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO = 18000 | Event triggered when the **ARKUI_NODE_RADIO** component is dragged or clicked. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: status of the radio button. |
| NODE_IMAGE_ANIMATOR_EVENT_ON_START = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_ANIMATOR = 19000 | Event triggered when the frame-by-frame animation starts to play.  <br>  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_IMAGE_ANIMATOR_EVENT_ON_PAUSE = 19001 | Event triggered when the frame-by-frame animation playback is paused.  <br>  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.|
| NODE_IMAGE_ANIMATOR_EVENT_ON_REPEAT = 19002 | Event triggered when the frame-by-frame animation playback is repeated.  <br>  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_IMAGE_ANIMATOR_EVENT_ON_CANCEL = 19003 | Event triggered when the frame-by-frame animation playback returns to the initial state.  <br>  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.|
| NODE_IMAGE_ANIMATOR_EVENT_ON_FINISH = 19004 | Event triggered when the frame-by-frame animation playback is complete or stopped.  <br>  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP = 21000 | Event triggered when the selection state of **ARKUI_NODE_CHECKBOX_GROUP** or any check box in the group changes. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br> <b>ArkUI_StringAsyncEvent.pStr</b>Name: name of the selected check box; Status: **0**: All check boxes in the group are selected. **1**: Some check boxes in the group are selected. **2**: No check box in the group is selected.<br>**Since**: 15  |
| NODE_SWIPER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER = 1001000 | Event triggered when the index of the currently displayed element of this **ARKUI_NODE_SWIPER** instance changes. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently displayed element. |
| NODE_SWIPER_EVENT_ON_ANIMATION_START = 1001001 | Event triggered when the switching animation of this **ARKUI_NODE_SWIPER** instance starts. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently displayed element.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: index of the target element to switch to.<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: offset of the currently displayed element relative to the start position of the swiper along the main axis.<br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>: offset of the target element relative to the start position of the swiper along the main axis.<br> <b>ArkUI_NodeComponentEvent.data[4].f32</b>: hands-off velocity. |
| NODE_SWIPER_EVENT_ON_ANIMATION_END = 1001002 | Event triggered when the switching animation of this **ARKUI_NODE_SWIPER** instance ends. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently displayed element.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: offset of the currently displayed element relative to the start position of the swiper along the main axis. |
| NODE_SWIPER_EVENT_ON_GESTURE_SWIPE = 1001003 | Event triggered on a frame-by-frame basis when the page is turned by a swipe. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently displayed element.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: offset of the currently displayed element relative to the start position of the swiper along the main axis.|
| NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL = 1001004 | Event triggered when content in the **ARKUI_NODE_SWIPER** component scrolls. Instructions:<br> 1. This API does not work when **NODE_SWIPER_DISPLAY_COUNT** is set to **'auto'**.<br> 2. This API does not work when **prevMargin** and **nextMargin** are set in such a way that the **Swiper** frontend and backend display the same page during loop playback.<br> 3. During page scrolling, the **ContentDidScrollCallback** callback is invoked for all pages in the viewport on a frame-by-frame basis.<br> For example, when there are two pages whose subscripts are 0 and 1 in the viewport, two callbacks whose indexes are 0 and 1 are invoked in each frame.<br> 4. When the **swipeByGroup** parameter of the **displayCount** attribute is set to **true**, the callback is invoked<br> for all pages in a group if any page in the group is within the viewport.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the **Swiper** component, which is the same as the index in the **onChange** event.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: index of a page in the viewport.<br> * <b>ArkUI_NodeComponentEvent.data[2].f32</b>: position of the page relative to the start position of the **Swiper** component's main axis (start position of the page corresponding to **selectedIndex**).<br> <b>ArkUI_NodeComponentEvent.data[3].f32</b>: length of the page in the main axis direction.  |
| NODE_SWIPER_EVENT_ON_SELECTED = 1001005 | Event triggered when the selection changes in the **ARKUI_NODE_SWIPER** component.  <br> 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meets the threshold for page turning.<br> 2. When the page is changed programmatically using either **NODE_SWIPER_INDEX** or **NODE_SWIPER_SWIPE_TO_INDEX**.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently selected element.<br>**Since**: 18   |
| NODE_SWIPER_EVENT_ON_UNSELECTED = 1001006 | Event triggered when the selection changes in the **ARKUI_NODE_SWIPER** component. This event is triggered when any of the following occurs:<br> 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meets the threshold for page turning.<br> 2. When the page is changed using either **NODE_SWIPER_INDEX** or **NODE_SWIPER_SWIPE_TO_INDEX**.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the item that is about to be hidden.<br>**Since**: 18   |
| NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL = 1001007 | Event for swipe behavior interception in the **ARKUI_NODE_SWIPER** component. Usage: The **ContentWillScrollCallback** callback is triggered before the page is scrolled.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the currently displayed element. The value of this parameter is used as the result of intercepting the event. If this parameter is set to 0, the event is intercepted. If this parameter is set to 1, the event is not intercepted.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: index of the target element to switch to.<br> <b>ArkUI_NodeComponentEvent.data[2].f32</b>: swipe offset per frame. A positive value indicates swiping backward (for example, from index=1 to index=0), and a negative value indicates swiping forward (for example, from index=0 to index=1).<br>**Since**: 15  |
| NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED = 1001008 | **ARKUI_NODE_SWIPER** scroll state change event. This event is triggered under the following scenarios:<br> The **Swiper** transitions between three scroll states: scrolling with the touch, animating after release, and stopped. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: current scroll state. The parameter type is [ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate).<br>**Since**: 20 |
| NODE_SCROLL_EVENT_ON_SCROLL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SCROLL = 1002000 | Event triggered when scrolling occurs. This event is triggered under the following scenarios:<br> 1. Scrolling is started by the scrollable component or other input settings, such as keyboard and mouse operations.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: horizontal scrolling offset.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: vertical scrolling offset. |
| NODE_SCROLL_EVENT_ON_SCROLL_FRAME_BEGIN = 1002001 | Event triggered when each frame scrolling starts in the scrollable component. List, Scroll, and WaterFlow are supported since API version 12. Grid is supported since API version 22.<br>This event is triggered under the following scenarios:<br> 1. This event is triggered when the scrolling component is triggered to scroll, including other input settings that trigger scrolling, such as keyboard and mouse operations.<br> 2. This event is not triggered when the controller API is called.<br> 3. This event is not triggered when the component bounces back out of bounds.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: amount to scroll by.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: current scroll state.<br> <b>::ArkUI_NodeComponentEvent</b> contains one return value: <br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: The event handler can work out the amount by which the component needs to scroll based on the real-world situation and return the result in this parameter.|
| NODE_SCROLL_EVENT_ON_WILL_SCROLL = 1002002 | Event triggered when the container is about to scroll. This event is triggered under the following scenarios:<br> 1. Scrolling is started by the scrollable component or other input settings, such as keyboard and mouse operations.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: scroll offset of each frame, in vp. The offset is positive when the content is scrolled left and negative when the content is scrolled right.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: scroll offset of each frame, in vp. The offset is positive when the content is scrolled up and negative when the content is scrolled down.<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: current scroll state. The parameter type is [ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate).<br> <b>ArkUI_NodeComponentEvent.data[3].i32</b>: current scroll source. The parameter type is [ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource). |
| NODE_SCROLL_EVENT_ON_DID_SCROLL = 1002003 | Event triggered when the container scrolls. This event is triggered under the following scenarios:<br> 1. Scrolling is started by the scrollable component or other input settings, such as keyboard and mouse operations.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: scroll offset of each frame, in vp. The offset is positive when the content is scrolled left and negative when the content is scrolled right.<br> <b>ArkUI_NodeComponentEvent.data[1].f32</b>: scroll offset of each frame, in vp. The offset is positive when the content is scrolled up and negative when the content is scrolled down.<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: current scroll state. The parameter type is [ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate). |
| NODE_SCROLL_EVENT_ON_SCROLL_START = 1002004 | Event triggered when the container starts scrolling. List, Scroll, and WaterFlow are supported since API version 12. Grid is supported since API version 22.<br>This event is triggered under the following scenarios:<br> 1. The scrollable component starts scrolling, supporting various input settings including keyboard and mouse operations.<br> 2. Scrolling is initiated through scroller controller API calls with transition animation effects.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_SCROLL_EVENT_ON_SCROLL_STOP = 1002005 | Event triggered when the container stops scrolling. List, Scroll, and WaterFlow are supported since API version 12. Grid is supported since API version 22.<br>This event is triggered under the following scenarios:<br> 1. The scrollable component stops scrolling, supporting various input settings including keyboard and mouse operations.<br> 2. The scrolling stops after the scrolling controller API is called, with a transition effect.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.  |
| NODE_SCROLL_EVENT_ON_SCROLL_EDGE = 1002006 | Event triggered when the container reaches the scroll boundary. This event is triggered under the following scenarios:<br> 1. This event is triggered when the scrolling component reaches the edge. Other input settings that can trigger scrolling, such as keyboard and mouse operations, are supported.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: edge (top, bottom, left, or right) that the scrolling reaches.|
| NODE_SCROLL_EVENT_ON_REACH_START = 1002007 | Event triggered when the scrollable component reaches the start edge. This event is triggered under the following scenarios:<br> 1. This event is triggered when the component reaches the start position.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.|
| NODE_SCROLL_EVENT_ON_REACH_END = 1002008 | Event triggered when the scrollable component reaches the end edge. This event is triggered under the following scenarios:<br> 1. The component reaches the bottom.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.  |
| NODE_SCROLL_EVENT_ON_WILL_STOP_DRAGGING = 1002009 | Event triggered when the user is about to release the drag on the scrollable component.  <br>  <br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: speed at which the user releases the drag, in vp/s.<br>**Since**: 20 |
| NODE_SCROLL_EVENT_ON_DID_ZOOM = 1002010 | **Scroll** component zoom event, triggered at the end of each frame during zooming.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: current zoom scale.<br>**Since**: 20 |
| NODE_SCROLL_EVENT_ON_ZOOM_START = 1002011 | **Scroll** component's zoom start event, triggered when zooming begins.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.<br>**Since**: 20   |
| NODE_SCROLL_EVENT_ON_ZOOM_STOP = 1002012 | **Scroll** component's zoom end event, triggered when zooming ends.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.<br>**Since**: 20   |
| NODE_SCROLL_EVENT_ON_WILL_START_DRAGGING = 1002013 | Defines the callback to be executed when the drag of a scrollable container component is about to start. This event is triggered when the drag of a scrollable container component is about to start.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.<br>**Since**: 21   |
| NODE_SCROLL_EVENT_ON_DID_STOP_DRAGGING = 1002014 | Defines the callback to be executed when the drag of a scrollable container component ends. This event is triggered when the drag of a scrollable container component ends.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: indicates whether to trigger the sliding animation after the drag ends.<br>**Since**: 21 |
| NODE_SCROLL_EVENT_ON_WILL_START_FLING = 1002015 | Defines the callback that is about to start the sliding animation of the scrollable container component. This event is triggered when the sliding animation of the scrollable container component is about to start.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.<br>**Since**: 21   |
| NODE_SCROLL_EVENT_ON_DID_STOP_FLING = 1002016 | Defines the callback that is triggered when the sliding animation of the scrollable container component ends. This event is triggered when the sliding animation of the scrollable container component ends.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.<br>**Since**: 21   |
| NODE_LIST_ON_SCROLL_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST = 1003000 | Event triggered when a child component enters or leaves the list display area. Note:<br> This event is triggered once when the list is initialized and when the index of the first child component or the next child component in the list display area changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the first child component in the list display area.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: index of the last child component in the list display area.<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: index of the center child component in the list display area.|
| NODE_LIST_ON_WILL_SCROLL = 1003001 | Event triggered when the list is about to scroll. This event is triggered under the following scenarios:<br> 1. Scrolling is started by the scrollable component or other input settings, such as keyboard and mouse operations.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: scroll offset of each frame. The offset is positive when the list is scrolled up and negative when the list is scrolled down.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: current scroll state. The parameter type is [ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate).<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: current scroll source. The parameter type is [ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource).|
| NODE_LIST_ON_DID_SCROLL = 1003002 | Event triggered when the **ARKUI_NODE_LIST** component scrolls. This event is triggered under the following scenarios:<br> 1. Scrolling is started by the scrollable component or other input settings, such as keyboard and mouse operations.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: scroll offset of each frame. The offset is positive when the list is scrolled up and negative when the list is scrolled down.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: current scroll state. |
| NODE_LIST_ON_SCROLL_VISIBLE_CONTENT_CHANGE = 1003003 | Event triggered when the currently displayed content of the **ARKUI_NODE_LIST** component changes. Note:<br> This event is triggered once when the list is initialized and when the index of the first child component or the next child component in the list display area changes. During index calculation, the list item, header of the list item group, and footer of the list item group each are counted as a child component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the first child component in the list display area.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: area in the list item group where the list display area starts. The type is [ArkUI_ListItemGroupArea](capi-native-type-h.md#arkui_listitemgrouparea).<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: index of the list item at the start of the list display area in the list item group. If the start of the list display area is not on a list item, the value is **-1**.<br> <b>ArkUI_NodeComponentEvent.data[3].i32</b>: index of the last child component in the list display area.<br> <b>ArkUI_NodeComponentEvent.data[4].i32</b>: area of the end of the list display area in the ListItemGroup. The type is [ArkUI_ListItemGroupArea](capi-native-type-h.md#arkui_listitemgrouparea).<br> <b>ArkUI_NodeComponentEvent.data[5].i32</b>: index of the last item in the list displayed in the list view. If the last item in the list displayed in the list view is not an item in the list, the value is -1.<br>**Since**: 15    |
| NODE_REFRESH_STATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_REFRESH = 1009000 | Event triggered when the refresh state of the **ARKUI_NODE_REFRESH** object changes. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: refresh state.<br>0: Inactive. This is the default status, indicating that the user has not pulled down the list.<br>1: Drag. The user is pulling down the list, and the distance between the current position and the top of the list is less than the refresh distance. If the user releases the list at this time, the component enters the Inactive state. If the user continues to pull down the list and the distance between the current position and the top of the list exceeds the refresh distance, the component enters the OverDrag state.<br>2: OverDrag. The user is pulling down the list, and the distance between the current position and the top of the list exceeds the refresh distance. If the user releases the list at this time, the component enters the Refresh state. If the user scrolls up the list and the distance between the current position and the top of the list is less than the refresh distance, the component enters the Drag state.<br>3: Refresh. The user has pulled down the list to the refresh distance, and the component is refreshing.<br>4: Done. The refresh is complete, and the component returns to the initial state (the top of the list). |
| NODE_REFRESH_ON_REFRESH = 1009001 | Event triggered when the **ARKUI_NODE_REFRESH** object enters the refresh state. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters. |
| NODE_REFRESH_ON_OFFSET_CHANGE = 1009002 | Event triggered when the pull-down distance of the **ARKUI_NODE_REFRESH** object changes. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: drop-down distance.  |
| NODE_ON_WILL_SCROLL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_WATER_FLOW = 1010000 | Event triggered when the **ARKUI_NODE_WATER_FLOW** component is about to scroll. This event is triggered under the following scenarios:<br> 1. Scrolling is started by the scrollable component or other input settings, such as keyboard and mouse operations.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: scroll offset of each frame. The offset is positive when the content is scrolled up and negative when the content is scrolled down.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: current scroll state. The parameter type is [ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate).<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: current scroll source. The parameter type is [ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource). |
| NODE_WATER_FLOW_ON_DID_SCROLL = 1010001 | Event triggered when the **ARKUI_NODE_WATER_FLOW** component scrolls. This event is triggered under the following scenarios:<br> 1. Scrolling is started by the scrollable component or other input settings, such as keyboard and mouse operations.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: scroll offset of each frame. The offset is positive when the content is scrolled up and negative when the content is scrolled down.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: current scroll state. |
| NODE_WATER_FLOW_ON_SCROLL_INDEX = 1010002 | Event triggered when the first or last item displayed in the water flow container changes.  <br> This event is triggered when the index value of the first or last item in the water flow container changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the first item of the water flow container.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: index of the last item of the water flow container.|
| NODE_GRID_ON_SCROLL_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID = 1013000 | Event triggered when a child component of **ARKUI_NODE_GRID** enters or leaves the grid display area.  <br> This event is triggered once when the grid is initialized and when the index of the first or last child component in the grid display area changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].i32</b>: index of the first child component in the grid display area.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: index of the last child component in the grid display area.<br>**Since**: 22|
| NODE_GRID_ON_WILL_SCROLL = 1013001 | Event triggered when the **ARKUI_NODE_GRID** component is about to scroll. This event is triggered in the following scenarios:<br>  1. Scrolling is started by the scrollable component or other input settings, such as keyboard and mouse operations.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br>   When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: scroll offset of each frame. The offset is positive when the content is scrolled up in the grid and negative when the content is scrolled down.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: current scroll state. The parameter type is [ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate).<br> <b>ArkUI_NodeComponentEvent.data[2].i32</b>: current scroll source. The parameter type is [ArkUI_ScrollSource](capi-native-type-h.md#arkui_scrollsource).<br>**Since**: 22|
| NODE_GRID_ON_DID_SCROLL = 1013002 | Event triggered when the **ARKUI_NODE_GRID** component scrolls. This event is triggered under the following scenarios:<br>  1. Scrolling is started by the scrollable component or other input settings, such as keyboard and mouse operations.<br> 2. Scrolling is initiated by calling the controller API.<br> 3. The out-of-bounds bounce effect is active.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br> <b>ArkUI_NodeComponentEvent.data[0].f32</b>: scroll offset of each frame. The offset is positive when the content is scrolled up in the grid and negative when the content is scrolled down.<br> <b>ArkUI_NodeComponentEvent.data[1].i32</b>: current scroll state. The parameter type is [ArkUI_ScrollState](capi-native-type-h.md#arkui_scrollstate).<br>**Since**: 22|
| NODE_GRID_ON_SCROLL_BAR_UPDATE = 1013003 | Event triggered at the end of each frame layout of the **ARKUI_NODE_GRID** component, which is used to set the position and length of the scrollbar.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). value.i32 at index 0: index of the first item in the currently displayed grid; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br>value.f32 at index 1: offset of the item at the starting position of the currently displayed grid relative to the starting position of the grid display, in vp; obtained using **OH_ArkUI_NodeEvent_GetNumberValue**.<br>**Since**: 22|
| NODE_GRID_ON_ITEM_DRAG_START = 1013004 | **ARKUI_NODE_GRID** component's child drag start event.<br>This event is triggered when the following conditions are met:<br>1. **NODE_GRID_EDIT_MODE** is set to **1**.<br>2. A user long-presses and drags a **Grid** child component with sufficient displacement.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).<br>value.f32 at index 0: X coordinate of the current drag point relative to the **Grid** component, in vp; obtained by calling **OH_ArkUI_NodeEvent_GetNumberValue**.<br>value.f32 at index 1: Y coordinate of the current drag point relative to the **Grid** component, in vp; obtained by calling **OH_ArkUI_NodeEvent_GetNumberValue**.<br>value.i32 at index 2: index of the dragged child component in the **Grid** component; obtained by calling **OH_ArkUI_NodeEvent_GetNumberValue**.<br>You can set the return value using **OH_ArkUI_NodeEvent_SetReturnNumberValue**.<br>value.i32 at index 0 in the return value indicates whether dragging is allowed. **0**: not allowed. **1**: allowed.<br>**Since**: 23|
| NODE_GRID_ON_ITEM_DRAG_ENTER = 1013005 | Event triggered when a dragged child component enters this **Grid** component's area.<br> <br>This event is triggered when a child component is successfully dragged by **NODE_GRID_ON_ITEM_DRAG_START** into the current **Grid** component's area.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br><b>ArkUI_NodeComponentEvent.data[0].f32</b>: X coordinate of the current drag point relative to the **Grid** component, in vp.<br><b>ArkUI_NodeComponentEvent.data[1].f32</b>: Y coordinate of the current drag point relative to the **Grid** component, in vp.<br>**Since**: 23|
| NODE_GRID_ON_ITEM_DRAG_MOVE = 1013006 | Event triggered when a dragged child component moves within this **Grid** component's area.<br> <br>This event is triggered when a child component is successfully dragged by **NODE_GRID_ON_ITEM_DRAG_START** into the current **Grid** component's area.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br><b>ArkUI_NodeComponentEvent.data[0].f32</b>: X coordinate of the current drag point relative to the **Grid** component, in vp.<br><b>ArkUI_NodeComponentEvent.data[1].f32</b>: Y coordinate of the current drag point relative to the **Grid** component, in vp.<br><b>ArkUI_NodeComponentEvent.data[2].i32</b>: index of the dragged child component in the source **Grid** component.<br><b>ArkUI_NodeComponentEvent.data[2].i32</b>: index of the dragged child component in the current **Grid** component.<br>**Since**: 23|
| NODE_GRID_ON_ITEM_DRAG_LEAVE = 1013007 | Event triggered when a dragged child component leaves this **Grid** component's area.<br> <br>This event is triggered when a child component successfully dragged using **NODE_GRID_ON_ITEM_DRAG_START** leaves the current **Grid** component's area.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br><b>ArkUI_NodeComponentEvent.data[0].f32</b>: X coordinate of the current drag point relative to the **Grid** component, in vp.<br><b>ArkUI_NodeComponentEvent.data[1].f32</b>: Y coordinate of the current drag point relative to the **Grid** component, in vp.<br><b>ArkUI_NodeComponentEvent.data[2].i32</b>: index of the dragged child component in the source **Grid** component.<br>**Since**: 23|
| NODE_GRID_ON_ITEM_DROP = 1013008 | Event triggered when a dragged child component is released.<br> <br>This event is triggered when a child component successfully dragged using **NODE_GRID_ON_ITEM_DRAG_START** is released.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br><b>ArkUI_NodeComponentEvent.data[0].f32</b>: X coordinate of the current drag point relative to the **Grid** component, in vp.<br><b>ArkUI_NodeComponentEvent.data[1].f32</b>: Y coordinate of the current drag point relative to the **Grid** component, in vp.<br><b>ArkUI_NodeComponentEvent.data[2].i32</b>: index of the dragged child component in the source **Grid** component.<br><b>ArkUI_NodeComponentEvent.data[2].i32</b>: index of the dragged child component in the current **Grid** component.<br><b>ArkUI_NodeComponentEvent.data[4].i32</b>: whether the dragged child component is successfully released within the **Grid** component's area. **1**: within the **Grid** component's area. **0**: outside the **Grid** component's area.<br>**Since**: 23|
| NODE_GRID_ITEM_ON_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID_ITEM = 1014000 | Selected state change event of the **ARKUI_NODE_GRID_ITEM** component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>: 0 (not selected) or 1 (selected).<br>**Since**: 23|
| NODE_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER | Defines the event triggered when an item is selected in the Picker container component.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>: value of the selected item.<br>**Since**: 23|
| NODE_PICKER_EVENT_ON_SCROLL_STOP = 1018001 | Defines the event triggered when an item is selected in the Picker container and the scrolling stops.<br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br> [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>: value of the selected item.<br>**Since**: 23|

### ArkUI_NodeDirtyFlag

```c
enum ArkUI_NodeDirtyFlag
```

**Description**


Enumerates the flags passed to indicate the need to re-execute measurement, layout, or rendering when a custom component calls the **::markDirty** API.

**Since**: 12

| Value                 | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| NODE_NEED_MEASURE = 1 | Remeasure. When this type of flag is specified, re-layout is triggered by default. |
| NODE_NEED_LAYOUT = 2  | Re-layout.                                                   |
| NODE_NEED_RENDER = 3  | Re-rendering.                                                |

### ArkUI_NodeCustomEventType

```c
enum ArkUI_NodeCustomEventType
```

**Description**


Enumerates the custom component event types.

**Since**: 12

| Value                                               | Description                                               |
| --------------------------------------------------- | --------------------------------------------------------- |
| ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE = 1 << 0         | Custom measurement.                                       |
| ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT = 1 << 1          | Custom layout.                                            |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW = 1 << 2            | Custom content layer drawing.                             |
| ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW = 1 << 3 | Custom foreground drawing.                                |
| ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW = 1 << 4    | Custom overlay drawing.                                   |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT = 1 << 5      | Custom content layer foreground drawing.<br>**Since**: 20 |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND = 1 << 6     | Custom content layer background drawing.<br>**Since**: 20 |

### ArkUI_NodeAdapterEventType

```c
enum ArkUI_NodeAdapterEventType
```

**Description**


Enumerates node adapter events.

**Since**: 12

| Value                                              | Description                                                  |
| -------------------------------------------------- | ------------------------------------------------------------ |
| NODE_ADAPTER_EVENT_WILL_ATTACH_TO_NODE = 1         | This event occurs when the component is attached to the adapter. |
| NODE_ADAPTER_EVENT_WILL_DETACH_FROM_NODE = 2       | This event occurs when the component is detached from the adapter. |
| NODE_ADAPTER_EVENT_ON_GET_NODE_ID = 3              | This event occurs when the adapter obtains the unique ID of the new element to add. |
| NODE_ADAPTER_EVENT_ON_ADD_NODE_TO_ADAPTER = 4      | This event occurs when the adapter obtains the content of the new element to add. |
| NODE_ADAPTER_EVENT_ON_REMOVE_NODE_FROM_ADAPTER = 5 | This event occurs when the adapter removes an element.       |

### ArkUI_NodeContentEventType

```c
enum ArkUI_NodeContentEventType
```

**Description**


Defines the NodeContent event type.

**Since**: 12

| Value                                        | Description   |
| -------------------------------------------- | ------------- |
| NODE_CONTENT_EVENT_ON_ATTACH_TO_WINDOW = 0   | Attach event. |
| NODE_CONTENT_EVENT_ON_DETACH_FROM_WINDOW = 1 | Detach event. |

### ArkUI_InspectorErrorCode

```c
enum ArkUI_InspectorErrorCode
```

**Description**


Enumerates the inspector error codes.

**Since**: 15

| Value                                            | Description           |
| ------------------------------------------------ | --------------------- |
| ARKUI_INSPECTOR_NATIVE_RESULT_SUCCESSFUL = 0     | Operation successful. |
| ARKUI_INSPECTOR_NATIVE_RESULT_BAD_PARAMETER = -1 | Parameter error.      |


## Function Description

### OH_ArkUI_NodeEvent_GetEventType()

```c
ArkUI_NodeEventType OH_ArkUI_NodeEvent_GetEventType(ArkUI_NodeEvent* event)
```

**Description**


Obtains the type of a component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Return value**

| Type                                                         | Description                              |
| ------------------------------------------------------------ | ---------------------------------------- |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) | Returns the type of the component event. |

### OH_ArkUI_NodeEvent_GetTargetId()

```c
int32_t OH_ArkUI_NodeEvent_GetTargetId(ArkUI_NodeEvent* event)
```

**Description**


Obtains the custom ID of a component event. The event ID is passed in as a parameter when the [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function is called and can be applied to the dispatch logic of the same event entry point function [registerNodeEventReceiver](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver).

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Return value**

| Type    | Description                       |
| ------- | --------------------------------- |
| int32_t | Custom ID of the component event. |

### OH_ArkUI_NodeEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeEvent_GetNodeHandle(ArkUI_NodeEvent* event)
```

**Description**


Obtains the component object that triggers an event.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Return value**

| Type                                                        | Description                               |
| ----------------------------------------------------------- | ----------------------------------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Component object that triggers the event. |

### OH_ArkUI_NodeEvent_GetInputEvent()

```c
ArkUI_UIInputEvent* OH_ArkUI_NodeEvent_GetInputEvent(ArkUI_NodeEvent* event)

```

**Description**


Obtains input event (for example, touch event) data for a component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Return value**

| Type                                                         | Description                      |
| ------------------------------------------------------------ | -------------------------------- |
| [ArkUI_UIInputEvent*](capi-arkui-eventmodule-arkui-uiinputevent.md) | Pointer to the input event data. |

### OH_ArkUI_NodeEvent_GetNodeComponentEvent()

```c
ArkUI_NodeComponentEvent* OH_ArkUI_NodeEvent_GetNodeComponentEvent(ArkUI_NodeEvent* event)

```

**Description**


Obtains the numerical data in a component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Return value**

| Type                                                         | Description                    |
| ------------------------------------------------------------ | ------------------------------ |
| [ArkUI_NodeComponentEvent*](capi-arkui-nativemodule-arkui-nodecomponentevent.md) | Pointer to the numerical data. |

### OH_ArkUI_NodeEvent_GetStringAsyncEvent()

```c
ArkUI_StringAsyncEvent* OH_ArkUI_NodeEvent_GetStringAsyncEvent(ArkUI_NodeEvent* event)

```

**Description**


Obtains the string data in a component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Return value**

| Type                                                         | Description                 |
| ------------------------------------------------------------ | --------------------------- |
| [ArkUI_StringAsyncEvent*](capi-arkui-nativemodule-arkui-stringasyncevent.md) | Pointer to the string data. |

### OH_ArkUI_NodeEvent_GetTextChangeEvent()

```c
ArkUI_TextChangeEvent* OH_ArkUI_NodeEvent_GetTextChangeEvent(ArkUI_NodeEvent* event)

```

**Description**


Obtains the **ArkUI_TextChangeEvent** data from the specified component event.

**Since**: 15


**Parameters**

| Name                                                         | Description                                      |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to a component event. It cannot be null. |

**Return value**

| Type                                                         | Description                                      |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [ArkUI_TextChangeEvent*](capi-arkui-nativemodule-arkui-textchangeevent.md) | Pointer to the **ArkUI_TextChangeEvent** object. |

### OH_ArkUI_NodeEvent_GetUserData()

```c
void* OH_ArkUI_NodeEvent_GetUserData(ArkUI_NodeEvent* event)

```

**Description**


Obtains the custom data in a component event. This parameter is passed in [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) and can be applied to the service logic when the event is triggered.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |

**Return value**

| Type  | Description           |
| ----- | --------------------- |
| void* | Pointer to user data. |

### OH_ArkUI_NodeEvent_GetNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_GetNumberValue(ArkUI_NodeEvent* event, int32_t index, ArkUI_NumberValue* value)

```

**Description**


Obtains the numeric-type parameter of a component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |
| int32_t index                                                | Return value index.             |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Return value.                   |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) if the parameter length in the parameter event exceeds the limit.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the data does not exist in the component event. |

### OH_ArkUI_NodeEvent_GetStringValue()

```c
int32_t OH_ArkUI_NodeEvent_GetStringValue(ArkUI_NodeEvent* event, int32_t index, char** string, int32_t* stringSize)

```

**Description**


Obtains the string-type parameter of a component event. The string data is valid only during an event callback. To use it outside an event callback, you are advised to copy the string data.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |
| int32_t index                                                | Return value index.             |
| char** string                                                | Pointer to the string array.    |
| int32_t* stringSize                                          | Length of the string array.     |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) if the parameter length in the parameter event exceeds the limit.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the data does not exist in the component event. |

### OH_ArkUI_NodeEvent_SetReturnNumberValue()

```c
int32_t OH_ArkUI_NodeEvent_SetReturnNumberValue(ArkUI_NodeEvent* event, ArkUI_NumberValue* value, int32_t size)

```

**Description**


Sets the return value for a component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* event | Pointer to the component event. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Event numeric type array.       |
| int32_t size                                                 | Size of the array.              |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the data does not exist in the component event. |

### OH_ArkUI_NodeAdapter_Create()

```c
ArkUI_NodeAdapterHandle OH_ArkUI_NodeAdapter_Create()

```

**Description**


Creates a component adapter.

**Since**: 12

**Return value**

| Type                                                         | Description               |
| ------------------------------------------------------------ | ------------------------- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) | Component adapter object. |

### OH_ArkUI_NodeAdapter_Dispose()

```c
void OH_ArkUI_NodeAdapter_Dispose(ArkUI_NodeAdapterHandle handle)

```

**Description**


Disposes of a component adapter.

**Since**: 12


**Parameters**

| Name                                                         | Description               |
| ------------------------------------------------------------ | ------------------------- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object. |

### OH_ArkUI_NodeAdapter_SetTotalNodeCount()

```c
int32_t OH_ArkUI_NodeAdapter_SetTotalNodeCount(ArkUI_NodeAdapterHandle handle, uint32_t size)

```

**Description**


Sets the total number of elements in the specified adapter.

**Since**: 12


**Parameters**

| Name                                                         | Description               |
| ------------------------------------------------------------ | ------------------------- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object. |
| uint32_t size                                                | Number of elements.       |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_GetTotalNodeCount()

```c
uint32_t OH_ArkUI_NodeAdapter_GetTotalNodeCount(ArkUI_NodeAdapterHandle handle)

```

**Description**


Obtains the total number of elements in the specified adapter.

**Since**: 12


**Parameters**

| Name                                                         | Description               |
| ------------------------------------------------------------ | ------------------------- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object. |

**Return value**

| Type     | Description                              |
| -------- | ---------------------------------------- |
| uint32_t | Total number of elements in the Adapter. |

### OH_ArkUI_NodeAdapter_RegisterEventReceiver()

```c
int32_t OH_ArkUI_NodeAdapter_RegisterEventReceiver(
ArkUI_NodeAdapterHandle handle, void* userData, void (*receiver)(ArkUI_NodeAdapterEvent* event))

```

**Description**


Registers an event callback for the specified adapter. After the callback event is no longer needed, you need to call [OH_ArkUI_NodeAdapter_UnregisterEventReceiver](#oh_arkui_nodeadapter_unregistereventreceiver) to deregister the callback event.

**Since**: 12


**Parameters**

| Name                                                         | Description               |
| ------------------------------------------------------------ | ------------------------- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object. |
| void* userData                                               | Custom data.              |
| receiver                                                     | Event receiving callback. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_UnregisterEventReceiver()

```c
void OH_ArkUI_NodeAdapter_UnregisterEventReceiver(ArkUI_NodeAdapterHandle handle)

```

**Description**


Unregisters an event callback for the specified adapter.

**Since**: 12


**Parameters**

| Name                                                         | Description               |
| ------------------------------------------------------------ | ------------------------- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object. |

### OH_ArkUI_NodeAdapter_ReloadAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadAllItems(ArkUI_NodeAdapterHandle handle)

```

**Description**


Instructs the specified adapter to reload all elements.

**Since**: 12


**Parameters**

| Name                                                         | Description               |
| ------------------------------------------------------------ | ------------------------- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapter_ReloadItem()

```c
int32_t OH_ArkUI_NodeAdapter_ReloadItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)

```

**Description**


Instructs the specified adapter to reload certain elements.

**Since**: 12


**Parameters**

| Name                                                         | Description                          |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object.            |
| uint32_t startPosition                                       | Start position of an element change. |
| uint32_t itemCount                                           | Number of changed elements.          |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns **ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR** if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapter_RemoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_RemoveItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)

```

**Description**


Instructs the specified adapter to remove certain elements.

**Since**: 12


**Parameters**

| Name                                                         | Description                             |
| ------------------------------------------------------------ | --------------------------------------- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object.               |
| uint32_t startPosition                                       | Start position for deleting an element. |
| uint32_t itemCount                                           | Number of deleted elements.             |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns **ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR** if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapter_InsertItem()

```c
int32_t OH_ArkUI_NodeAdapter_InsertItem(
ArkUI_NodeAdapterHandle handle, uint32_t startPosition, uint32_t itemCount)

```

**Description**


Instructs the specified adapter to insert certain elements.

**Since**: 12


**Parameters**

| Name                                                         | Description                              |
| ------------------------------------------------------------ | ---------------------------------------- |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object.                |
| uint32_t startPosition                                       | Start position for inserting an element. |
| uint32_t itemCount                                           | Number of inserted elements.             |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns **ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR** if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapter_MoveItem()

```c
int32_t OH_ArkUI_NodeAdapter_MoveItem(ArkUI_NodeAdapterHandle handle, uint32_t from, uint32_t to)

```

**Description**


Instructs the specified adapter to move certain elements.

**Since**: 12


**Parameters**

| Name                                                         | Description                          |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object.            |
| uint32_t from                                                | Start position of the element shift. |
| uint32_t to                                                  | End position of the element shift.   |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns **ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR** if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapter_GetAllItems()

```c
int32_t OH_ArkUI_NodeAdapter_GetAllItems(ArkUI_NodeAdapterHandle handle, ArkUI_NodeHandle** items, uint32_t* size)

```

**Description**


Obtains all elements stored in the specified adapter. When the API is called, the array object pointer of the element is returned. You must release the memory data to which the pointer points.

**Since**: 12


**Parameters**

| Name                                                         | Description                    |
| ------------------------------------------------------------ | ------------------------------ |
| [ArkUI_NodeAdapterHandle](capi-arkui-nativemodule-arkui-nodeadapter8h.md) handle | Component adapter object.      |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)** items | Array of nodes in the adapter. |
| uint32_t* size                                               | Number of elements.            |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns **ERROR_CODE_NATIVE_IMPL_NODE_ADAPTER_NO_LISTENER_ERROR** if the NodeAdapter requires a listener to be added. |

### OH_ArkUI_NodeAdapterEvent_GetUserData()

```c
void* OH_ArkUI_NodeAdapterEvent_GetUserData(ArkUI_NodeAdapterEvent* event)

```

**Description**


Obtains the custom data passed in during registration of the specified event.

**Since**: 12


**Parameters**

| Name                                                         | Description           |
| ------------------------------------------------------------ | --------------------- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Adapter event object. |

**Return value**

| Type  | Description                         |
| ----- | ----------------------------------- |
| void* | Returns the pointer to custom data. |

### OH_ArkUI_NodeAdapterEvent_GetType()

```c
ArkUI_NodeAdapterEventType OH_ArkUI_NodeAdapterEvent_GetType(ArkUI_NodeAdapterEvent* event)

```

**Description**


Obtains the event type.

**Since**: 12


**Parameters**

| Name                                                         | Description           |
| ------------------------------------------------------------ | --------------------- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Adapter event object. |

**Return value**

| Type                                                         | Description               |
| ------------------------------------------------------------ | ------------------------- |
| [ArkUI_NodeAdapterEventType](capi-native-node-h.md#arkui_nodeadaptereventtype) | Represents an event type. |

### OH_ArkUI_NodeAdapterEvent_GetRemovedNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetRemovedNode(ArkUI_NodeAdapterEvent* event)

```

**Description**


Obtains the element to be removed for the event to be destroyed.

**Since**: 12


**Parameters**

| Name                                                         | Description           |
| ------------------------------------------------------------ | --------------------- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Adapter event object. |

**Return value**

| Type                                                        | Description              |
| ----------------------------------------------------------- | ------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Element to be destroyed. |

### OH_ArkUI_NodeAdapterEvent_GetItemIndex()

```c
uint32_t OH_ArkUI_NodeAdapterEvent_GetItemIndex(ArkUI_NodeAdapterEvent* event)

```

**Description**


Obtains the index of the element to be operated for the specified adapter event.

**Since**: 12


**Parameters**

| Name                                                         | Description           |
| ------------------------------------------------------------ | --------------------- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Adapter event object. |

**Return value**

| Type     | Description                    |
| -------- | ------------------------------ |
| uint32_t | Sequence number of an element. |

### OH_ArkUI_NodeAdapterEvent_GetHostNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeAdapterEvent_GetHostNode(ArkUI_NodeAdapterEvent* event)

```

**Description**


Obtains the scrollable container node that uses the specified adapter.

**Since**: 12


**Parameters**

| Name                                                         | Description           |
| ------------------------------------------------------------ | --------------------- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Adapter event object. |

**Return value**

| Type                                                        | Description                                                  |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Returns the scrollable container node that uses the specified adapter. |

### OH_ArkUI_NodeAdapterEvent_SetItem()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetItem(ArkUI_NodeAdapterEvent* event, ArkUI_NodeHandle node)

```

**Description**


Sets the component to be added to the specified adapter.

**Since**: 12


**Parameters**

| Name                                                         | Description            |
| ------------------------------------------------------------ | ---------------------- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Adapter event object.  |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Component to be added. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeAdapterEvent_SetNodeId()

```c
int32_t OH_ArkUI_NodeAdapterEvent_SetNodeId(ArkUI_NodeAdapterEvent* event, int32_t id)

```

**Description**


Sets the component ID to be generated.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeAdapterEvent](capi-arkui-nativemodule-arkui-nodeadapterevent.md)* event | Adapter event object.           |
| int32_t id                                                   | Sets the returned component ID. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure()

```c
ArkUI_LayoutConstraint* OH_ArkUI_NodeCustomEvent_GetLayoutConstraintInMeasure(ArkUI_NodeCustomEvent* event)

```

**Description**


Obtains the size constraint for measurement through a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Return value**

| Type                    | Description                     |
| ----------------------- | ------------------------------- |
| ArkUI_LayoutConstraint* | Pointer to the constraint size. |

### OH_ArkUI_NodeCustomEvent_GetPositionInLayout()

```c
ArkUI_IntOffset OH_ArkUI_NodeCustomEvent_GetPositionInLayout(ArkUI_NodeCustomEvent* event)

```

**Description**


Obtains the expected position of a component relative to its parent component in the layout phase through a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Return value**

| Type                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | Returns the expected position relative to the parent component. |

### OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw()

```c
ArkUI_DrawContext* OH_ArkUI_NodeCustomEvent_GetDrawContextInDraw(ArkUI_NodeCustomEvent* event)

```

**Description**


Obtains the drawing context through a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Return value**

| Type                                                         | Description      |
| ------------------------------------------------------------ | ---------------- |
| [ArkUI_DrawContext*](capi-arkui-nativemodule-arkui-drawcontext.md) | Drawing context. |

### OH_ArkUI_NodeCustomEvent_GetEventTargetId()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetEventTargetId(ArkUI_NodeCustomEvent* event)

```

**Description**


Obtains the ID of a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Return value**

| Type    | Description                  |
| ------- | ---------------------------- |
| int32_t | Returns the custom event ID. |

### OH_ArkUI_NodeCustomEvent_GetUserData()

```c
void* OH_ArkUI_NodeCustomEvent_GetUserData(ArkUI_NodeCustomEvent* event)

```

**Description**


Obtains custom event parameters through a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Return value**

| Type  | Description                          |
| ----- | ------------------------------------ |
| void* | Returns the custom event parameters. |

### OH_ArkUI_NodeCustomEvent_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_NodeCustomEvent_GetNodeHandle(ArkUI_NodeCustomEvent* event)

```

**Description**


Obtains a component object through a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Return value**

| Type                                                        | Description                            |
| ----------------------------------------------------------- | -------------------------------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Returns the obtained component object. |

### OH_ArkUI_NodeCustomEvent_GetEventType()

```c
ArkUI_NodeCustomEventType OH_ArkUI_NodeCustomEvent_GetEventType(ArkUI_NodeCustomEvent* event)

```

**Description**


Obtains the event type through a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |

**Return value**

| Type                                                         | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [ArkUI_NodeCustomEventType](capi-native-node-h.md#arkui_nodecustomeventtype) | Returns the type of the custom component event. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanMeasureInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMeasureInfo* info)

```

**Description**


Obtains the measurement information of a custom span through a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info | Measurement information to obtain.     |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        A possible cause is that mandatory parameters are left unspecified. |

### OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics()

```c
int32_t OH_ArkUI_NodeCustomEvent_SetCustomSpanMetrics(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanMetrics* metrics)

```

**Description**


Sets the measurement metrics of a custom span through a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Measurement metrics to set.            |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        A possible cause is that mandatory parameters are left unspecified. |

### OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo()

```c
int32_t OH_ArkUI_NodeCustomEvent_GetCustomSpanDrawInfo(ArkUI_NodeCustomEvent* event, ArkUI_CustomSpanDrawInfo* info)

```

**Description**


Obtains the drawing information of a custom span through a custom component event.

**Since**: 12


**Parameters**

| Name                                                         | Description                            |
| ------------------------------------------------------------ | -------------------------------------- |
| [ArkUI_NodeCustomEvent](capi-arkui-nativemodule-arkui-nodecustomevent.md)* event | Pointer to the custom component event. |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Drawing information to obtain.         |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        A possible cause is that mandatory parameters are left unspecified. |

### ArkUI_NodeContentCallback()

```c
typedef void (*ArkUI_NodeContentCallback)(ArkUI_NodeContentEvent* event)

```

**Description**


Defines a callback for the NodeContent event.

**Since**: 12


**Parameters**

| Name                                                         | Description                       |
| ------------------------------------------------------------ | --------------------------------- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Pointer to the NodeContent event. |

### OH_ArkUI_NodeContent_RegisterCallback()

```c
int32_t OH_ArkUI_NodeContent_RegisterCallback(ArkUI_NodeContentHandle content, ArkUI_NodeContentCallback callback)

```

**Description**


Registers an event callback for the **NodeContent**.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | NodeContent object for which an event needs to be registered. |
| [ArkUI_NodeContentCallback](capi-native-node-h.md#arkui_nodecontentcallback) callback | Callback to be executed when the event is triggered.         |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeContentEvent_GetEventType()

```c
ArkUI_NodeContentEventType OH_ArkUI_NodeContentEvent_GetEventType(ArkUI_NodeContentEvent* event)

```

**Description**


Obtains the type of the specified **NodeContent** event.

**Since**: 12


**Parameters**

| Name                                                         | Description                       |
| ------------------------------------------------------------ | --------------------------------- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Pointer to the NodeContent event. |

**Return value**

| Type                                                         | Description             |
| ------------------------------------------------------------ | ----------------------- |
| [ArkUI_NodeContentEventType](capi-native-node-h.md#arkui_nodecontenteventtype) | NodeContent event type. |

### OH_ArkUI_NodeContentEvent_GetNodeContentHandle()

```c
ArkUI_NodeContentHandle OH_ArkUI_NodeContentEvent_GetNodeContentHandle(ArkUI_NodeContentEvent* event)

```

**Description**


Obtains the object that triggers the specified **NodeContent** event.

**Since**: 12


**Parameters**

| Name                                                         | Description                       |
| ------------------------------------------------------------ | --------------------------------- |
| [ArkUI_NodeContentEvent](capi-arkui-nativemodule-arkui-nodecontentevent.md)* event | Pointer to the NodeContent event. |

**Return value**

| Type                                                         | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) | **NodeContent** object that triggers the event. |

### OH_ArkUI_NodeContent_SetUserData()

```c
int32_t OH_ArkUI_NodeContent_SetUserData(ArkUI_NodeContentHandle content, void* userData)

```

**Description**


Saves custom data to the specified **NodeContent** object.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | NodeContent object whose user-defined data needs to be saved. |
| void* userData                                               | User-defined data to be saved.                               |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeContent_GetUserData()

```c
void* OH_ArkUI_NodeContent_GetUserData(ArkUI_NodeContentHandle content)

```

**Description**


Obtains the custom data saved on the specified **NodeContent** object.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | NodeContent object whose user-defined data needs to be saved. |

**Return value**

| Type  | Description  |
| ----- | ------------ |
| void* | Custom data. |

### OH_ArkUI_NodeContent_AddNode()

```c
int32_t OH_ArkUI_NodeContent_AddNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)

```

**Description**


Adds an ArkUI component node to the specified **NodeContent** object.

**Since**: 12


**Parameters**

| Name                                                         | Description                                        |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | NodeContent object to which a node is to be added. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Node to be added.                                  |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>             Returns [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-native-type-h.md#arkui_errorcode) if a child node has been accepted. This specification is supported since API version 22. |

### OH_ArkUI_NodeContent_RemoveNode()

```c
int32_t OH_ArkUI_NodeContent_RemoveNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node)

```

**Description**


Removes an ArkUI component node from the specified **NodeContent** object.

**Since**: 12


**Parameters**

| Name                                                         | Description                                   |
| ------------------------------------------------------------ | --------------------------------------------- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | NodeContent object of the node to be deleted. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Node to be deleted.                           |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeContent_InsertNode()

```c
int32_t OH_ArkUI_NodeContent_InsertNode(ArkUI_NodeContentHandle content, ArkUI_NodeHandle node, int32_t position)

```

**Description**


Inserts an ArkUI component node into a specific position of the specified **NodeContent** object.

**Since**: 12


**Parameters**

| Name                                                         | Description                                    |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontent8h.md) content | NodeContent object of the node to be inserted. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Node to be inserted.                           |
| int32_t position                                             | Start time for an asset to be inserted,        |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>             Returns [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-native-type-h.md#arkui_errorcode) if a child node has been accepted. This specification is supported since API version 22. |

### OH_ArkUI_NodeUtils_GetLayoutSize()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutSize(ArkUI_NodeHandle node, ArkUI_IntSize* size)

```

**Description**


Obtains the layout area size of the component. The size does not count in transformation attributes, such as scale.

**Since**: 12


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer.   |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md)* size | Size of the layout area, in px. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPosition()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPosition(ArkUI_NodeHandle node, ArkUI_IntOffset* localOffset)

```

**Description**


Obtains the position of the component's layout area relative to its parent component. The relative position does not count in transformation attributes, such as translate.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer.                                |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* localOffset | Offset of the component handle relative to the parent component, in px. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)

```

**Description**


Obtains the position of the component's layout area relative to the window. The relative position does not count in transformation attributes, such as translate.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer.                                |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | Offset of the component handle relative to the window, in px. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* screenOffset)

```

**Description**


Obtains the position of the component's layout area relative to the screen. The relative position does not count in transformation attributes, such as translate.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer.                                |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* screenOffset | Offset of the component handle relative to the screen, in px. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay()

```c
int32_t OH_ArkUI_NodeUtils_GetLayoutPositionInGlobalDisplay(ArkUI_NodeHandle node, ArkUI_IntOffset* offset)

```

**Description**


Obtains the offset of the specified component relative to the global display. The relative position does not count in transformation attributes, such as translate.

**Since**: 20


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer.                                |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* offset | Offset of the component handle relative to the screen, in px. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInWindow(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)

```

**Description**


Obtains the position of the component in the window, including the translate attribute.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer.                                |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* translateOffset | Accumulated offset of the component, its parent component, and its ancestor node, in px. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionWithTranslateInScreen(ArkUI_NodeHandle node, ArkUI_IntOffset* translateOffset)

```

**Description**


Obtains the position of the component on the screen, including the translate attribute.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer.                                |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* translateOffset | Accumulated offset of the component, its parent component, and its ancestor node, in px. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_AddCustomProperty()

```c
void OH_ArkUI_NodeUtils_AddCustomProperty(ArkUI_NodeHandle node, const char* name, const char* value)

```

**Description**


Sets a custom property for a component. This API takes effect only in the main thread.

**Since**: 13


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer.                                |
| const char* name                                             | Name of the custom property. A null pointer is not allowed.  |
| const char* value                                            | Value of the custom property. A null pointer is not allowed. |

### OH_ArkUI_NodeUtils_RemoveCustomProperty()

```c
void OH_ArkUI_NodeUtils_RemoveCustomProperty(ArkUI_NodeHandle node, const char* name)

```

**Description**


Removes a custom property that has been set for the specified component.

**Since**: 13


**Parameters**

| Name                                                         | Description                   |
| ------------------------------------------------------------ | ----------------------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer. |
| const char* name                                             | Name of the custom property.  |

### OH_ArkUI_NodeUtils_GetCustomProperty()

```c
int32_t OH_ArkUI_NodeUtils_GetCustomProperty(ArkUI_NodeHandle node, const char* name, ArkUI_CustomProperty** handle)

```

**Description**


Obtains the value of a custom property of the specified component.

**Since**: 14


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ArkUI_NodeHandle** pointer.                                |
| const char* name                                             | Name of the custom property.                                 |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)** handle | Pointer to the struct that receives the custom property corresponding to the key parameter name. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetParentInPageTree()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetParentInPageTree(ArkUI_NodeHandle node)

```

**Description**


Obtains the parent node, which can be a component node created with ArkTS.

**Since**: 14


**Parameters**

| Name                                                         | Description  |
| ------------------------------------------------------------ | ------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node. |

**Return value**

| Type                                                        | Description                                                  |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Pointer to the component if the component exists; returns **NULL** otherwise. |

### OH_ArkUI_NodeUtils_GetActiveChildrenInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetActiveChildrenInfo(ArkUI_NodeHandle head, ArkUI_ActiveChildrenInfo** handle)

```

**Description**


Obtains all active child nodes of the specified node. Spans are not counted as child nodes. In **LazyForEach** scenarios, you are advised to use the [OH_ArkUI_NodeUtils_GetChildWithExpandMode](#oh_arkui_nodeutils_getchildwithexpandmode) API for traversal.

**Since**: 14


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) head | Node for which to obtain the child nodes.                    |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)** handle | Pointer to the struct containing information about the child nodes of the head node. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetCurrentPageRootNode()

```c
ArkUI_NodeHandle OH_ArkUI_NodeUtils_GetCurrentPageRootNode(ArkUI_NodeHandle node)

```

**Description**


Obtains the root node of the current page.

**Since**: 14


**Parameters**

| Name                                                         | Description  |
| ------------------------------------------------------------ | ------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node. |

**Return value**

| Type                                                        | Description                                                  |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Returns the pointer to the root node if the node exists; returns **NULL** otherwise. |

### OH_ArkUI_NodeUtils_IsCreatedByNDK()

```c
bool OH_ArkUI_NodeUtils_IsCreatedByNDK(ArkUI_NodeHandle node)

```

**Description**


Checks whether the specified component is created with C APIs.

**Since**: 14


**Parameters**

| Name                                                         | Description  |
| ------------------------------------------------------------ | ------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node. |

**Return value**

| Type | Description                                                  |
| ---- | ------------------------------------------------------------ |
| bool | Returns whether the node is created with the C API. The value **true** means that the node is created with the C API, and **false** means the opposite. |

### OH_ArkUI_NodeUtils_GetNodeType()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeType(ArkUI_NodeHandle node)

```

**Description**


Obtains the type of the specified node.

**Since**: 14


**Parameters**

| Name                                                         | Description  |
| ------------------------------------------------------------ | ------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Returns the type of the node. Returns **-1** if the type is not supported yet. For details about the available types, see [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype). |

### OH_ArkUI_NodeUtils_GetWindowInfo()

```c
int32_t OH_ArkUI_NodeUtils_GetWindowInfo(ArkUI_NodeHandle node, ArkUI_HostWindowInfo** info)

```

**Description**


Obtains the information about the window to which a node belongs.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.                                                 |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)** info | Pointer to the window information object. The memory allocated for this object must be released using [OH_ArkUI_HostWindowInfo_Destroy](capi-native-type-h.md#oh_arkui_hostwindowinfo_destroy). |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if C API initialization failed.<br>         Returns [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) if the node is not mounted on the main component tree. |

### OH_ArkUI_NodeUtils_MoveTo()

```c
int32_t OH_ArkUI_NodeUtils_MoveTo(ArkUI_NodeHandle node, ArkUI_NodeHandle target_parent, int32_t index)

```

**Description**


Moves a node to a target parent node as a child.

**Since**: 18


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Node to be moved.                                            |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) target_parent | Pointer to the target parent node.                           |
| int32_t index                                                | Index of the node after the movement. If the index is invalid, the node will be added to the end of the target parent node. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if C API initialization failed.<br>             Returns [ARKUI_ERROR_CODE_NODE_IS_ADOPTED](capi-native-type-h.md#arkui_errorcode) if a child node has been accepted. This specification is supported since API version 22. |

### OH_ArkUI_NativeModule_InvalidateAttributes()

```c
int32_t OH_ArkUI_NativeModule_InvalidateAttributes(ArkUI_NodeHandle node)

```

**Description**

Triggers the node attribute update in this frame.

If the attributes of the current node are modified after the build phase, these changes do not take effect immediately but are deferred for batch processing in the next frame.

This API forces immediate node updates within the current frame, ensuring that rendering effects are applied synchronously.

**Since**: 21


**Parameters**

| Name                                                         | Description                              |
| ------------------------------------------------------------ | ---------------------------------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Node whose attributes are to be updated. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>    Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |


### OH_ArkUI_List_CloseAllSwipeActions()

```c
int32_t OH_ArkUI_List_CloseAllSwipeActions(ArkUI_NodeHandle node, void* userData, void (*onFinish)(void* userData))

```

**Description**


Collapses the list items in the expanded state.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Node object for which an event needs to be registered.       |
| void* userData                                               | Custom event parameter, which is passed in the callback when the event is triggered. |
| onFinish                                                     | Callback triggered after the collapse animation is complete. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) if the event is not supported. |

### OH_ArkUI_GetContextByNode()

```c
ArkUI_ContextHandle OH_ArkUI_GetContextByNode(ArkUI_NodeHandle node)

```

**Description**


Obtains the pointer to the UI context object of the specified node.

**Since**: 12


**Parameters**

| Name                                                         | Description     |
| ------------------------------------------------------------ | --------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Specified node. |

**Return value**

| Type                                                         | Description                                   |
| ------------------------------------------------------------ | --------------------------------------------- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) | Returns the pointer to the UI context object. |

### OH_ArkUI_RegisterSystemColorModeChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemColorModeChangeEvent(ArkUI_NodeHandle node,void* userData, void (*onColorModeChange)(ArkUI_SystemColorMode colorMode, void* userData))

```

**Description**


Registers an event listener for system color mode changes. A single component can only register one callback for system color mode changes. For implementation examples, see [Listening for Component Events](../../ui/ndk-listen-to-component-events.md).

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Specified node.                                              |
| void* userData                                               | Custom event parameter, which is passed in the callback when the event is triggered. |
| onColorModeChange                                            | Callback to be executed when the event is triggered. [ArkUI_SystemColorMode](capi-native-type-h.md#arkui_systemcolormode) defines the system color mode (light/dark). |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_UnregisterSystemColorModeChangeEvent()

```c
void OH_ArkUI_UnregisterSystemColorModeChangeEvent(ArkUI_NodeHandle node)

```

**Description**


Unregisters the event listener for system color mode changes.

**Since**: 12


**Parameters**

| Name                                                         | Description     |
| ------------------------------------------------------------ | --------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Specified node. |

### OH_ArkUI_RegisterSystemFontStyleChangeEvent()

```c
int32_t OH_ArkUI_RegisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node,void* userData, void (*onFontStyleChange)(ArkUI_SystemFontStyleEvent* event, void* userData))

```

**Description**


Registers an event listener for system font style changes. A single component can only register one callback for system font style changes.

**Since**: 12


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Specified node.                                              |
| void* userData                                               | Custom event parameter, which is passed in the callback when the event is triggered. |
| onFontStyleChange                                            | Callback to be executed when the event is triggered.         |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_UnregisterSystemFontStyleChangeEvent()

```c
void OH_ArkUI_UnregisterSystemFontStyleChangeEvent(ArkUI_NodeHandle node)

```

**Description**


Unregisters the event listener for system font style changes.

**Since**: 12


**Parameters**

| Name                                                         | Description     |
| ------------------------------------------------------------ | --------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Specified node. |

### OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontSizeScale(const ArkUI_SystemFontStyleEvent* event)

```

**Description**


Obtains the font size from the system font style change event.

**Since**: 12


**Parameters**

| Name                                                         | Description                                            |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| [const ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md)* event | Pointer to the current system font style change event. |

**Return value**

| Type  | Description                                                  |
| ----- | ------------------------------------------------------------ |
| float | Returns the font size scale after the change. Default value: **1.0**. |

### OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale()

```c
float OH_ArkUI_SystemFontStyleEvent_GetFontWeightScale(const ArkUI_SystemFontStyleEvent* event)

```

**Description**


Obtains the font weight from the system font style change event.

**Since**: 12


**Parameters**

| Name                                                         | Description                                            |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| [const ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md)* event | Pointer to the current system font style change event. |

**Return value**

| Type  | Description                                                  |
| ----- | ------------------------------------------------------------ |
| float | Returns the font weight scale after the change. Default value: **1.0**. |

### OH_ArkUI_RegisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node,void* userData, void (*onLayoutCompleted)(void* userData))

```

**Description**


Registers a layout completion callback function for a specific node.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node for which the callback function is to be registered. |
| void* userData                                               | Custom parameter passed to the callback function when it is invoked. |
| onLayoutCompleted                                            | Callback function to be invoked when layout is completed.    |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>          Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_RegisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_RegisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node,void* userData, void (*onDrawCompleted)(void* userData))

```

**Description**


Registers a drawing completion callback function for a specific node.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node for which the callback function is to be registered. |
| void* userData                                               | Custom parameter passed to the callback function when it is invoked. |
| onDrawCompleted                                              | Callback function to be invoked when drawing is completed.   |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>          Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterLayoutCallbackOnNodeHandle(ArkUI_NodeHandle node)

```

**Description**


Unregisters the layout completion callback function for a specific node.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node for which the callback function is to be unregistered. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>          Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_UnregisterDrawCallbackOnNodeHandle()

```c
int32_t OH_ArkUI_UnregisterDrawCallbackOnNodeHandle(ArkUI_NodeHandle node)

```

**Description**


Unregisters the drawing completion callback function for a specific node.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node for which the callback function is to be unregistered. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>          Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetNodeSnapshot()

```c
int32_t OH_ArkUI_GetNodeSnapshot(ArkUI_NodeHandle node, ArkUI_SnapshotOptions* snapshotOptions,OH_PixelmapNative** pixelmap)

```

**Description**


Obtains a snapshot of a given component. If the node is not in the component tree or has not been rendered, the snapshot operation will fail. When the pixelmap is no longer used, you should call [OH_PixelmapNative_Release](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_release) to release it.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node to capture a snapshot.                           |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Snapshot settings. If the value is null, the default settings are used.<br>The screenshot configuration includes the scaling attribute, color space, and dynamic range mode. The color space and dynamic range mode are supported since API version 23.<br>The scaling attribute is a floating point number greater than 0. The default value is 1.0.<br>The color space can be 3 (Display P3 RGB color gamut), 4 (SRGB RGB color gamut), or 27 (Display BT2020 RGB color gamut). The default value is 4.<br> The dynamic range mode can be [ArkUI_DynamicRangeMode](capi-native-type-h.md#arkui_dynamicrangemode). The default value is ARKUI_DYNAMIC_RANGE_MODE_STANDARD. |
| OH_PixelmapNative** pixelmap                                 | Pointer to the Pixelmap created by the system.               |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_INTERNAL_ERROR](capi-native-type-h.md#arkui_errorcode) if the snapshot fails, returning a null pointer.<br>         Returns [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT](capi-native-type-h.md#arkui_errorcode) if the snapshot operation times out.<br>         The [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) does not support the color space or dynamic range mode in the screenshot configuration.<br>         The [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED](capi-native-type-h.md#arkui_errorcode) offscreen node screenshot does not support the setting of the isAuto parameter to true for the color space or dynamic range mode. |

### OH_ArkUI_NodeUtils_GetAttachedNodeHandleById()

```c
int32_t OH_ArkUI_NodeUtils_GetAttachedNodeHandleById(const char* id, ArkUI_NodeHandle* node)

```

**Description**


Obtains the target node based on the provided user ID.

**Since**: 15


**Parameters**

| Name                                                         | Description                 |
| ------------------------------------------------------------ | --------------------------- |
| const char* id                                               | ID of the target node.      |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | Pointer to the target node. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId(const uint32_t uniqueId, ArkUI_NodeHandle* node)

```

**Description**


Obtain a node by its unique ID.

**Since**: 20


**Parameters**

| Name                                                         | Description                   |
| ------------------------------------------------------------ | ----------------------------- |
| const uint32_t uniqueId                                      | Unique ID of the target node. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | Pointer to the target node.   |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if C API initialization failed. |

### OH_ArkUI_NodeUtils_GetNodeUniqueId()

```c
int32_t OH_ArkUI_NodeUtils_GetNodeUniqueId(ArkUI_NodeHandle node, int32_t* uniqueId)

```

**Description**


Obtains the unique ID of the target node.

**Since**: 20


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI node pointer.                                          |
| int32_t* uniqueId                                            | Unique ID of the target node. The component ID is read-only and unique in the process. If the node exists, the unique ID of the node is returned. Otherwise, -1 is returned. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if C API initialization failed. |

### OH_ArkUI_NativeModule_AdoptChild()

```c
int32_t OH_ArkUI_NativeModule_AdoptChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)

```

**Description**

Adopts the target node as an affiliated node. The adopted node must not have an existing parent. This API is not used to add a node as a child node. Instead, it only allows the node to receive lifecycle callbacks of the corresponding child node.

**Since**: 22

**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer, which specifies the parent node of the node to be accepted. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | ArkUI_NodeHandle pointer, which specifies the child node to be accepted. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if C API initialization failed.<br>         [ARKUI_ERROR_CODE_NODE_HAS_PARENT](capi-native-type-h.md#arkui_errorcode) The accepted node already has a parent node.<br>         The [ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED](capi-native-type-h.md#arkui_errorcode) node cannot be accepted as a child node.<br>         The [ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO](capi-native-type-h.md#arkui_errorcode) node cannot accept other child nodes. |

### OH_ArkUI_NativeModule_RemoveAdoptedChild()

```c
int32_t OH_ArkUI_NativeModule_RemoveAdoptedChild(ArkUI_NodeHandle node, ArkUI_NodeHandle child)

```

**Description**

Removes a previously adopted node.

**Since**: 22

**Parameters**

| Name                                                         | Description                                         |
| ------------------------------------------------------------ | --------------------------------------------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI_NodeHandle pointer, parent node.              |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) child | ArkUI_NodeHandle pointer, child node to be removed. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if C API initialization failed.<br>         The [ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN](capi-native-type-h.md#arkui_errorcode) node is not a child node accepted by the target node. |

### OH_ArkUI_NativeModule_IsInRenderState()

```c
int32_t OH_ArkUI_NativeModule_IsInRenderState(ArkUI_NodeHandle node, bool* isInRenderState)

```

**Description**

Obtains whether a node is in the rendering state. If the [RenderNode](./js-apis-arkui-renderNode.md) of a node is in the render tree, the node is in the rendering state.

**Since**: 23

**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ArkUI node pointer.                                          |
| bool*  isInRenderState                                       | Whether the node is in render state. true: The node is in the rendering state. false: The node is not in the rendering state. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>  [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) The method parameter is abnormal.<br>  Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if C API initialization failed. |

### OH_ArkUI_NodeUtils_SetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_SetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)

```

**Description**


Sets the cross-language options for the target node.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the target node.                                  |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | Cross-language configuration option [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md). |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetCrossLanguageOption()

```c
int32_t OH_ArkUI_NodeUtils_GetCrossLanguageOption(ArkUI_NodeHandle node, ArkUI_CrossLanguageOption* option)

```

**Description**


Obtains the cross-language options for the target node.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the target node.                                  |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | Cross-language configuration option [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md). |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)

```

**Description**


Obtains the index of the first child node of the target node in the tree without expanding any nodes.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the target node.                                  |
| uint32_t* index                                              | Pointer to a variable where the index of the first child node is stored. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand()

```c
int32_t OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand(ArkUI_NodeHandle node, uint32_t* index)

```

**Description**


Obtains the index of the last child node of the target node in the tree without expanding any nodes.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the target node.                                  |
| uint32_t* index                                              | Pointer to a variable where the index of the first child node is stored. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetChildWithExpandMode()

```c
int32_t OH_ArkUI_NodeUtils_GetChildWithExpandMode(ArkUI_NodeHandle node, int32_t position,ArkUI_NodeHandle* subnode, uint32_t expandMode)

```

**Description**


Obtains a child node at the specified index using different expansion modes.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the target node.                                  |
| int32_t position                                             | Index of the child node to obtain.                           |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* subnode | Pointer to the obtained child node.                          |
| uint32_t expandMode                                          | Expansion mode for node traversal. For details, see [ArkUI_ExpandMode](capi-native-type-h.md#arkui_expandmode). |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NodeUtils_GetPositionToParent()

```c
int32_t OH_ArkUI_NodeUtils_GetPositionToParent(ArkUI_NodeHandle node, ArkUI_IntOffset* globalOffset)

```

**Description**


Obtains the offset of the target node relative to its parent node, in px.

**Since**: 15


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.                                                 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* globalOffset | Offset of the target node relative to its parent node, in px. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_AddSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_AddSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates,void (statesChangeHandler)(int32_t currentStates, void* userData), bool excludeInner, void* userData)

```

**Description**


Adds the polymorphic style states supported by the component. To handle states efficiently, specify the states of interest and their corresponding handlers. When a state of interest occurs, the handler will be executed. You can adjust the UI style based on the current state within the callback. If this API is called multiple times on the same node, the last set of states and handlers will take precedence. Some component types have default system handling for certain states. For example, the **Button** component has a default style effect for the PRESSED state. When custom state handling is implemented on such components, the default style effect will be applied first, followed by the custom style changes, resulting in a combined effect. To disable the default style effects, set **excludeInner** to **true**, if this is allowed by the system implementation. When this API is called, the provided handler function will be executed immediately. There is no need to explicitly register a listener for the NORMAL state. Once a non-NORMAL state is registered, the system will automatically notify your application when the state changes back to NORMAL.

**Since**: 20


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.                                                 |
| int32_t uiStates                                             | Target UI states to be handled on the node. The combined result of all target UI states can be calculated using the **\|** operator. Example: **targetUIStates = ArkUI_UIState::PRESSED \| ArkUI_UIState::FOCUSED**. |
| void (statesChangeHandler)(int32_t currentStates, void* userData) | Handler for UI state changes. It returns the current UI status. The value is the result of combining all current state enum values using the **\|** operator. You can determine the state using the **&** operator. Example: **if (currentStates & ArkUI_UIState::PRESSED == ArkUI_UIState::PRESSED)**. However, for checking the normal state, use the equality operator directly. Example: **if (currentStates == ArkUI_UIState::NORMAL)**. |
| bool excludeInner                                            | Whether to disable the default state styles. **true**: Disable the default state styles. **false**: Do not disable the default state styles. |
| void* userData                                               | Custom data used in the **onDrawCompleted** callback.        |

**Return value**

| Type                                                     | Description                                                  |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_RemoveSupportedUIStates()

```c
ArkUI_ErrorCode OH_ArkUI_RemoveSupportedUIStates(ArkUI_NodeHandle node, int32_t uiStates)

```

**Description**


Removes registered UI states. When all states registered using **OH_ArkUI_AddSupportedUIStates** are removed, the registered **stateChangeHandler** will no longer be executed.

**Since**: 20


**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.                    |
| int32_t uiStates                                             | Target UI states to be removed. |

**Return value**

| Type                                                     | Description                                                  |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_RunTaskInScope()

```c
int32_t OH_ArkUI_RunTaskInScope(ArkUI_ContextHandle uiContext, void* userData, void(*callback)(void* userData))

```

**Description**


Executes the specified callback in the target UI context. For the implementation example, see [Ensuring Multi-Instance Functionality in the NDK](../../ui/ndk-scope-task.md).

**Since**: 20


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | Pointer to the target UI context.                            |
| void* userData                                               | User-defined data pointer for processing custom data within the callback function. You are responsible for ensuring the validity of the data when the custom function is executed. |
| void(\*callback)(void\* userData)                            | User-defined callback function.                              |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if C API initialization failed.<br>         Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-native-type-h.md#arkui_errorcode) if the **UIContext** object is invalid.<br>         Returns [ARKUI_ERROR_CODE_CALLBACK_INVALID](capi-native-type-h.md#arkui_errorcode) if the callback function is invalid. |

### OH_ArkUI_PostAsyncUITask()

```c
int32_t OH_ArkUI_PostAsyncUITask(ArkUI_ContextHandle context, void* asyncUITaskData,
    void (*asyncUITask)(void* asyncUITaskData), void (*onFinish)(void* asyncUITaskData))

```

**Description**

Submits the **asyncUITask** function to a non-UI thread provided by the ArkUI framework for execution. After **asyncUITask** finishes execution, the **onFinish** function is called in the UI thread.

This is suitable for scenarios involving multi-threaded UI component creation. You can use this API to create UI components in non-UI threads and then mount the created components to the main tree in the UI thread.

**Since**: 22

**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | Pointer to the UI instance object.                           |
| void* asyncUITaskData                                        | Pointer to the user-defined data, which is passed as the input parameter of **asyncUITask** and **onFinish**. A null pointer is allowed. |
| asyncUITask                                                  | Function executed in the non-UI thread.                      |
| onFinish                                                     | Function executed on the UI thread after **asyncUITask** is completed. A null pointer is allowed. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the context object is invalid, or **asyncUITask** is a null pointer. |

### OH_ArkUI_PostUITask()

```c
int32_t OH_ArkUI_PostUITask(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))

```

**Description**

Submits the **task** function to the UI thread for execution.

This is suitable for scenarios involving multi-threaded UI component creation. When you create UI components in a self-built thread, you can use this API to mount the created components to the main tree on the UI thread.

**Since**: 22

**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | Pointer to the UI instance object.                           |
| void* taskData                                               | Pointer to the user-defined data, which is passed as the input parameter of **task**. A null pointer is allowed. |
| task                                                         | Function executed in the UI thread.                          |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the context object is invalid, or **task** is a null pointer. |

### OH_ArkUI_PostUITaskAndWait()

```c
int32_t OH_ArkUI_PostUITaskAndWait(ArkUI_ContextHandle context, void* taskData, void (*task)(void* taskData))

```

**Description**

Submits the **task** function to the UI thread for execution. The thread calling this API will block until the **task** function completes execution. Calling this API from the UI thread is equivalent to synchronously calling the **task** function.

This is suitable for scenarios involving multi-threaded UI component creation. When you need to call functions that are only supported on the UI thread during the multi-threaded component creation process, you can use this API to return to the UI thread to call the function and then resume multi-threaded component creation after the call completes.

When the UI thread is under high load, non-UI threads calling this API may block for extended periods, affecting the performance of multi-threaded UI component creation. Frequent use is not recommended.

**Since**: 22

**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | Pointer to the UI instance object.                           |
| void* taskData                                               | Pointer to the user-defined data, which is passed as the input parameter of **task**. A null pointer is allowed. |
| task                                                         | Function executed in the UI thread.                          |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the context object is invalid, or **task** is a null pointer. |

### OH_ArkUI_NativeModule_RegisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType, void* userData, void (*callback)(ArkUI_NodeEvent* event))

```

**Description**

Registers a basic event callback for the target node.

Currently, the following event types are supported: **NODE_ON_CLICK_EVENT**, **NODE_TOUCH_EVENT**, **NODE_EVENT_ON_APPEAR**, **NODE_EVENT_ON_DISAPPEAR**, **NODE_ON_KEY_EVENT**, **NODE_ON_FOCUS**, **NODE_ON_BLUR**, **NODE_ON_HOVER**, **NODE_ON_MOUSE**, and **NODE_ON_SIZE_CHANGE**. For details, see [ArkUI_NodeEventType](#arkui_nodeeventtype).

**Since**: 21

**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.                                                 |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | Represents an event type.                                    |
| void* userData                                               | User-defined data pointer for processing custom data within the callback function. You are responsible for ensuring the validity of the data when the custom function is executed. |
| callback                                                     | User-defined callback function.                              |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE](capi-native-type-h.md#arkui_errorcode) if the event type is not supported. |

### OH_ArkUI_NativeModule_UnregisterCommonEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonEvent(ArkUI_NodeHandle node, ArkUI_NodeEventType eventType)

```

**Description**

Unregisters the basic event callback for the target node.

For details about the supported event types, see [OH_ArkUI_NativeModule_RegisterCommonEvent](#oh_arkui_nativemodule_registercommonevent).

**Since**: 21

**Parameters**

| Name                                                         | Description               |
| ------------------------------------------------------------ | ------------------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.              |
| [ArkUI_NodeEventType](capi-native-node-h.md#arkui_nodeeventtype) eventType | Represents an event type. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE](capi-native-type-h.md#arkui_errorcode) if the event type is not supported. |

### OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_RegisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node, float* ratios, int32_t size, float expectedUpdateInterval, void* userData, void (*callback)(ArkUI_NodeEvent* event))

```

**Description**

Registers a basic event callback for visible area changes with a constrained callback interval.

**Since**: 21

**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.                                                 |
| float* ratios                                                | Array of threshold ratios, representing the visible area of the component. |
| int32_t size                                                 | Size of the array of threshold ratios.                       |
| float expectedUpdateInterval                                 | Expected calculation interval.                               |
| void* userData                                               | User-defined data pointer for processing custom data within the callback function. You are responsible for ensuring the validity of the data when the custom function is executed. |
| callback                                                     | User-defined callback function.                              |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent()

```c
int32_t OH_ArkUI_NativeModule_UnregisterCommonVisibleAreaApproximateChangeEvent(ArkUI_NodeHandle node)

```

**Description**

Unregisters the basic event callback for visible area changes with a constrained callback interval.

**Since**: 21

**Parameters**

| Name                                                         | Description  |
| ------------------------------------------------------------ | ------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_Swiper_FinishAnimation()

```c
int32_t OH_ArkUI_Swiper_FinishAnimation(ArkUI_NodeHandle node)

```

**Description**


Stops the page flip animation that is being executed on the specified Swiper node.

**Since**: 22


**Parameters**

| Name                                                         | Description     |
| ------------------------------------------------------------ | --------------- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Specified node. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_SetForceDarkConfig()

```c
int32_t OH_ArkUI_SetForceDarkConfig(ArkUI_ContextHandle uiContext, bool forceDark, ArkUI_NodeType nodeType, uint32_t (*colorInvertFunc)(uint32_t color))

```

**Description**


Sets the color inversion algorithm for components and instances. For details, see [Using Color Inversion for Quick Dark Mode Adaptation](../../ui/ui-dark-light-color-adaptation.md#using-color-inversion-for-quick-dark-mode-adaptation).

**Since**: 20


**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | Pointer to the UI instance object.<br>  If the value is null, this function applies to the entire application process. |
| bool forceDark                                               | Whether to use the color inversion capability. The value true indicates that the component uses the color inversion capability, and the value false indicates that the component does not use the color inversion capability. |
| [ArkUI_NodeType](#arkui_nodetype) nodeType                   | Scope of the component where the color inversion capability takes effect.<br>   ARKUI_NODE_UNDEFINED indicates that the setting takes effect for all component types. |
| colorInvertFunc                                              | Customized color inversion algorithm function.<br> If the value is nullptr, the default color inversion algorithm is used for the component, that is, the three primary colors are inverted. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-native-type-h.md#arkui_errorcode) if C API initialization failed.<br> The input parameter of the [ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID](capi-native-type-h.md#arkui_errorcode) color inversion capability is incorrect. |

### OH_ArkUI_NodeEvent_GetTouchTestInfo()

```c
ArkUI_TouchTestInfo* OH_ArkUI_NodeEvent_GetTouchTestInfo(ArkUI_NodeEvent* nodeEvent)

```

**Description**

Obtains the touch test information in a component event.

**Since**: 22

**Parameters**

| Name                                                         | Description                     |
| ------------------------------------------------------------ | ------------------------------- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* nodeEvent | Pointer to the component event. |

**Return value**

| Type                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_TouchTestInfo](./capi-arkui-nativemodule-arkui-touchtestinfo.md)* | Pointer to the [ArkUI_TouchTestInfo](./capi-arkui-nativemodule-arkui-touchtestinfo.md) object. If the input parameter is invalid or is not touch test information, null is returned. |

### OH_ArkUI_NativeModule_ConvertPositionToWindow()

``` c
int32_t OH_ArkUI_NativeModule_ConvertPositionToWindow(ArkUI_NodeHandle currentNode, ArkUI_IntOffset localPosition, ArkUI_IntOffset* windowPosition)

```

**Description**

Converts the coordinates of a point from the coordinate system of a specified node to that of the current window. The coordinate system of a node considers the transformation of the node itself. For example, if node A is translated leftward by 100, the coordinates of the points in its coordinate system will also be translated leftward by 100.

![](./arkui-ts/figures/ConvertToWindow.png)

As shown in the preceding figure, the coordinates (x0, y0) in the coordinate system of the specified node are converted to the coordinates (x1, y1) in the coordinate system of the window.

**Since**: 23

**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) currentNode | Specifies a node.                                            |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) localPosition | Coordinates of the point in the specified node coordinate system. The unit is px. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* windowPosition | Pointer to the converted coordinates (in the current window coordinate system, in px). |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) if the node is not mounted on the main component tree. |

### OH_ArkUI_NativeModule_ConvertPositionFromWindow()

``` c
int32_t OH_ArkUI_NativeModule_ConvertPositionFromWindow(ArkUI_NodeHandle targetNode, ArkUI_IntOffset windowPosition, ArkUI_IntOffset* localPosition)

```

**Description**

Converts the coordinates of a point from the current window coordinate system to the coordinate system of the target node. The node coordinate system considers the transformation of the node itself. For example, if node A is translated 100 pixels to the left, the coordinates of the point in the coordinate system of node A are also translated 100 pixels to the left.

![](./arkui-ts/figures/ConvertFromWindow.png)

As shown in the preceding figure, the coordinates (x1, y1) in the window coordinate system are converted to the coordinates (x0, y0) in the coordinate system of the target node.

**Since**: 23

**Parameters**

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) targetNode | Target node.                                                 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) windowPosition | Coordinates of the point in the current window coordinate system. The unit is px. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md)* localPosition | Pointer to the converted coordinates (in the coordinate system of the target node, in px). |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) if the node is not mounted on the main component tree. |

 
