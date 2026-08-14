# drag_and_drop.h

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=66d449f865d808c2ab2228de4384c97bf7b4883d translatedAt=2026-08-04T11:03:35.765Z pushedAt=2026-08-05T04:07:24.075Z -->

## Overview

Declares the APIs of **NativeDrag**, supporting obtaining drag events, setting and obtaining drag data, configuring drag previews, initiating drag operations, and listening for drag states. It is suitable for scenarios where applications need to implement native drag interactions, data drag-in and drag-out, and custom drag effects. This module supports cross-device drag interactions, provides an asynchronous data loading mechanism to improve the efficiency of dragging large amounts of data, and supports fine-grained drag behavior control and state listening.

**File to include**: <arkui/drag_and_drop.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[NativeDragDrop](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeDragDrop)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) | ArkUI_NodeEvent | Defines a component event. This is a general struct. |
| [ArkUI_Context](capi-arkui-nativemodule-arkui-context.md) | ArkUI_Context | Defines an ArkUI native UI context instance object, used to represent the UIContext of the page where the component is located. Its pointer type is [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md). You can obtain the corresponding context through [OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode) and use it as the context input parameter of the APIs for drag operations, animations, and UI task scheduling. |
| [ArkUI_Context*](capi-arkui-nativemodule-arkui-context8h.md) | ArkUI_ContextHandle | Defines a pointer to the ArkUI context instance object on the native side, used to represent the UIContext of the page where the component is located. You can obtain this pointer through [OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode) or [OH_ArkUI_GetContextFromNapiValue](capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue) and use it as the context input parameter of APIs for UI task scheduling, animations, and focus control. |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) | ArkUI_DragEvent | Defines a drag event, used to represent the event information during the drag process of an ArkUI component. You can obtain the drag status and event data through the drag event APIs in the following header file. For details about the drag event binding process, see [Binding Drag Events](../../ui/ndk-drag-event.md). |
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md) | ArkUI_DragPreviewOption | Defines custom drag preview options (such as shadow and corner radius effects), used to customize the preview display effect in drag scenarios and help applications provide a drag interaction experience that better meets service requirements. |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md) | ArkUI_DragAction | Defines a drag action handle, used to proactively initiate a drag operation, that is, you proactively call APIs to start dragging, as opposed to passively responding to drag events. This handle supports creating, configuring, executing, and destroying drag actions, and can set drag data and proactively start dragging. The usage process of ArkUI_DragAction is as follows: 1. Create an object through [OH_ArkUI_CreateDragActionWithNode](capi-drag-and-drop-h.md#oh_arkui_createdragactionwithnode) or [OH_ArkUI_CreateDragActionWithContext](capi-drag-and-drop-h.md#oh_arkui_createdragactionwithcontext). 2. Call APIs such as **OH_ArkUI_DragAction_SetData** to configure drag parameters. 3. Call [OH_ArkUI_StartDrag](capi-drag-and-drop-h.md#oh_arkui_startdrag) to start dragging. 4. When the object is no longer needed, call [OH_ArkUI_DragAction_Dispose](capi-drag-and-drop-h.md#oh_arkui_dragaction_dispose) to destroy it and release resources. For details about the creation, configuration, and execution mechanism, see [Binding Drag Events](../../ui/ndk-drag-event.md). |
| [ArkUI_DragAndDropInfo](capi-arkui-nativemodule-arkui-draganddropinfo.md) | ArkUI_DragAndDropInfo | Defines drag and drop information returned through a drag status listener after the drag is proactively initiated. You can obtain the drag start or end status from this struct, as well as the drag event data when the drag ends, and perform subsequent processing based on the status. For details about how to register the drag callback, see [drag_and_drop.h](capi-drag-and-drop-h.md). |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_DragResult](#arkui_dragresult) | ArkUI_DragResult | Enumerates drag results, which are set by the data receiver and transferred by the system to the drag source so that the drag source is aware of the data processing result of the receiver.|
| [ArkUI_DropOperation](#arkui_dropoperation) | ArkUI_DropOperation | Enumerates data processing modes used when data is dropped, which affects the display of the badge. When copying behavior is set, the badge shows a plus sign; when cutting behavior is set, the badge does not show a plus sign. |
| [ArkUI_PreDragStatus](#arkui_predragstatus) | ArkUI_PreDragStatus | Enumerates interaction states prior to a drop and drop operation.|
| [ArkUI_DragPreviewScaleMode](#arkui_dragpreviewscalemode) | ArkUI_DragPreviewScaleMode | Enumerates drag preview scale modes.|
| [ArkUI_DragStatus](#arkui_dragstatus) | ArkUI_DragStatus | Enumerates drag operation states.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent* OH_ArkUI_NodeEvent_GetDragEvent(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_getdragevent) | Obtains a **DragEvent** object from the specified **NodeEvent** object.|
| [ArkUI_PreDragStatus OH_ArkUI_NodeEvent_GetPreDragStatus(ArkUI_NodeEvent* nodeEvent)](#oh_arkui_nodeevent_getpredragstatus) | Obtains the state prior to a drop and drop operation.|
| [int32_t OH_ArkUI_DragEvent_DisableDefaultDropAnimation(ArkUI_DragEvent* event, bool disable)](#oh_arkui_dragevent_disabledefaultdropanimation) | Sets whether to disable the default drop animation, which is enabled by default. Use this API to apply a custom drop animation.|
| [int32_t OH_ArkUI_DragEvent_SetSuggestedDropOperation(ArkUI_DragEvent* event, ArkUI_DropOperation dropOperation)](#oh_arkui_dragevent_setsuggesteddropoperation) | Sets the data processing mode, which affects how the badge is displayed during dragging. This is suitable for scenarios where you need to suggest data processing behavior to the system when data is dropped. For example, when copyable text or image content is dragged, it is recommended to set the copying behavior (**ARKUI_DROP_OPERATION_COPY**); when dragging content needs to be removed from the source location, it is recommended to set the cutting behavior (**ARKUI_DROP_OPERATION_MOVE**). This API has the same functionality as [OH_ArkUI_NotifySuggestedDropOperation](#oh_arkui_notifysuggesteddropoperation), with the following difference: this API sets the data processing mode directly in a synchronous drag event callback, which is suitable for scenarios where delayed processing of the drag end event is not required; **OH_ArkUI_NotifySuggestedDropOperation** sends the data processing mode notification in the asynchronous **RequestDragEndPending** flow, which is suitable for scenarios where [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending) has been called to delay processing of the drag end event. |
| [int32_t OH_ArkUI_DragEvent_SetDragResult(ArkUI_DragEvent* event, ArkUI_DragResult result)](#oh_arkui_dragevent_setdragresult) | Sets the result for a drag event. As the data receiver, this API sets the processing result of the drag event in the drop callback so that the drag initiator can perceive the data receiving and processing status. This API has the same functionality as [OH_ArkUI_NotifyDragResult](#oh_arkui_notifydragresult), with the following difference: this API sets the drag result directly in a synchronous drag event callback, which is suitable for scenarios where delayed processing of the drag end event is not required; **OH_ArkUI_NotifyDragResult** sends the result notification in the asynchronous **RequestDragEndPending** flow, which is suitable for scenarios where [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending) has been called to delay processing of the drag end event. |
| [int32_t OH_ArkUI_DragEvent_SetData(ArkUI_DragEvent* event, OH_UdmfData* data)](#oh_arkui_dragevent_setdata) | Sets drag data for a drag event.|
| [ArkUI_ErrorCode OH_ArkUI_DragEvent_SetDataLoadParams(ArkUI_DragEvent* event, OH_UdmfDataLoadParams* dataLoadParams)](#oh_arkui_dragevent_setdataloadparams) | Provides data loading parameters to the system instead of directly providing a complete data object. When the user drops data on the target application, the system will use **dataLoadParams** to request data. This can greatly improve the efficiency of dragging large amounts of data and the efficiency of processing dropped data in the target application. This API must always be used in preference to [OH_ArkUI_DragEvent_SetData](#oh_arkui_dragevent_setdata). For details about how to create and prepare data loading parameters, see [OH_UdmfDataLoadParams_Create](../apis-arkdata/capi-udmf-h.md#oh_udmfdataloadparams_create) in **udmf.h**. If this API conflicts with [OH_ArkUI_DragEvent_SetData](#oh_arkui_dragevent_setdata), the system always uses the last called API. |
| [int32_t OH_ArkUI_DragEvent_GetUdmfData(ArkUI_DragEvent* event, OH_UdmfData *data)](#oh_arkui_dragevent_getudmfdata) | Obtains the drag data from **ArkUI_DragEvent**. |
| [int32_t OH_ArkUI_DragEvent_GetDataTypeCount(ArkUI_DragEvent* event, int32_t* count)](#oh_arkui_dragevent_getdatatypecount) | Obtains the number of drag data types from a drag event.|
| [int32_t OH_ArkUI_DragEvent_GetDataTypes(ArkUI_DragEvent *event, char *eventTypeArray[], int32_t length, int32_t maxStrLen)](#oh_arkui_dragevent_getdatatypes) | Obtains the type list of drag data types from a drag event.|
| [int32_t OH_ArkUI_DragEvent_GetDragResult(ArkUI_DragEvent* event, ArkUI_DragResult* result)](#oh_arkui_dragevent_getdragresult) | Obtains the drag and drop result from the drag event.|
| [int32_t OH_ArkUI_DragEvent_GetDropOperation(ArkUI_DragEvent* event, ArkUI_DropOperation* operation)](#oh_arkui_dragevent_getdropoperation) | Obtains the data handling method from the drag event.|
| [float OH_ArkUI_DragEvent_GetPreviewTouchPointX(ArkUI_DragEvent* event)](#oh_arkui_dragevent_getpreviewtouchpointx) | Obtains the x-coordinate of the touch point for a drag preview from a drag event.|
| [float OH_ArkUI_DragEvent_GetPreviewTouchPointY(ArkUI_DragEvent* event)](#oh_arkui_dragevent_getpreviewtouchpointy) | Obtains the y-coordinate of the touch point on the preview image from a drag event.|
| [float OH_ArkUI_DragEvent_GetPreviewRectWidth(ArkUI_DragEvent* event)](#oh_arkui_dragevent_getpreviewrectwidth) | Obtains the width of a drag preview from a drag event.|
| [float OH_ArkUI_DragEvent_GetPreviewRectHeight(ArkUI_DragEvent* event)](#oh_arkui_dragevent_getpreviewrectheight) | Obtains the height of a drag preview from a drag event.|
| [float OH_ArkUI_DragEvent_GetTouchPointXToWindow(ArkUI_DragEvent* event)](#oh_arkui_dragevent_gettouchpointxtowindow) | Obtains the x-coordinate of the touch point relative to the window from a drag event.|
| [float OH_ArkUI_DragEvent_GetTouchPointYToWindow(ArkUI_DragEvent* event)](#oh_arkui_dragevent_gettouchpointytowindow) | Obtains the y-coordinate of the touch point relative to the window from a drag event.|
| [float OH_ArkUI_DragEvent_GetTouchPointXToDisplay(ArkUI_DragEvent* event)](#oh_arkui_dragevent_gettouchpointxtodisplay) | Obtains the x-coordinate of the touch point relative to the display from a drag event.|
| [float OH_ArkUI_DragEvent_GetTouchPointYToDisplay(ArkUI_DragEvent* event)](#oh_arkui_dragevent_gettouchpointytodisplay) | Obtains the y-coordinate of the touch point relative to the display from a drag event.|
| [float OH_ArkUI_DragEvent_GetVelocityX(ArkUI_DragEvent* event)](#oh_arkui_dragevent_getvelocityx) | Obtains the dragging velocity along the x-axis.|
| [float OH_ArkUI_DragEvent_GetVelocityY(ArkUI_DragEvent* event)](#oh_arkui_dragevent_getvelocityy) | Obtains the dragging velocity along the y-axis.|
| [float OH_ArkUI_DragEvent_GetVelocity(ArkUI_DragEvent* event)](#oh_arkui_dragevent_getvelocity) | Obtains the dragging velocity along the main axis.|
| [int32_t OH_ArkUI_DragEvent_GetModifierKeyStates(ArkUI_DragEvent* event, uint64_t* keys)](#oh_arkui_dragevent_getmodifierkeystates) | Obtains the pressed states of modifier keys. |
| [int32_t OH_ArkUI_DragEvent_StartDataLoading(ArkUI_DragEvent* event, OH_UdmfGetDataParams* options, char* key, unsigned int keyLen)](#oh_arkui_dragevent_startdataloading) | Starts data synchronization using the specified synchronization parameters.|
| [int32_t OH_ArkUI_CancelDataLoading(ArkUI_ContextHandle uiContext, const char* key)](#oh_arkui_canceldataloading) | Cancels the ongoing data synchronization.|
| [int32_t OH_ArkUI_DisableDropDataPrefetchOnNode(ArkUI_NodeHandle node, bool disabled)](#oh_arkui_disabledropdataprefetchonnode) | Sets whether to disable the data prefetch process before executing [NODE_ON_DROP](./capi-native-node-h.md#arkui_nodeeventtype). The system will retry data fetching until the maximum time limit (currently 2.4 seconds) is reached. This is useful for cross-device drag operations because it helps stabilize system communication. However, this feature is redundant for the [OH_ArkUI_DragEvent_StartDataLoading](#oh_arkui_dragevent_startdataloading) API. Since this API uses an asynchronous mechanism to fetch data, when [OH_ArkUI_DragEvent_StartDataLoading](#oh_arkui_dragevent_startdataloading) is used in **NODE_ON_DROP**, this parameter must be set to **true** to prevent accidental data fetching before **NODE_ON_DROP** is executed. |
| [int32_t OH_ArkUI_SetDragEventStrictReportWithNode(ArkUI_NodeHandle node, bool enabled)](#oh_arkui_setdrageventstrictreportwithnode) | Sets whether to enable strict reporting on drag events. This feature is disabled by default, and you are advised to enable it. If this feature is disabled, the parent component is not notified when an item in it is dragged over its child component. If this feature is enabled, the component is notified of the dragged item's leaving, and the child component to which the dragged item is dropped is notified of the item's entering. This configuration is related to a specific UI instance. You can pass in a specific component node on the current UI instance for association. |
| [int32_t OH_ArkUI_SetDragEventStrictReportWithContext(ArkUI_ContextHandle uiContext, bool enabled)](#oh_arkui_setdrageventstrictreportwithcontext) | Sets whether to enable strict reporting on drag events. This feature is disabled by default, and you are advised to enable it. If this feature is disabled, the parent component is not notified when an item in it is dragged over its child component. If this feature is enabled, the component is notified of the dragged item's leaving, and the child component to which the dragged item is dropped is notified of the item's entering. This configuration is related to a specific UI instance. You can pass in a specific UI instance for association. |
| [int32_t OH_ArkUI_SetNodeAllowedDropDataTypes(ArkUI_NodeHandle node, const char* typesArray[], int32_t count)](#oh_arkui_setnodealloweddropdatatypes) | Sets the types of data that can be dropped to the specified component. This API resets the settings configured through [OH_ArkUI_DisallowNodeAnyDropDataTypes](#oh_arkui_disallownodeanydropdatatypes) or [OH_ArkUI_AllowNodeAllDropDataTypes](#oh_arkui_allownodealldropdatatypes). |
| [int32_t OH_ArkUI_DisallowNodeAnyDropDataTypes(ArkUI_NodeHandle node)](#oh_arkui_disallownodeanydropdatatypes) | Configures the specified component to disallow any data types. This API resets the settings configured through [OH_ArkUI_SetNodeAllowedDropDataTypes](capi-drag-and-drop-h.md#oh_arkui_setnodealloweddropdatatypes). Note: Calling **OH_ArkUI_SetNodeAllowedDropDataTypes** also resets the configuration made by this API. |
| [int32_t OH_ArkUI_AllowNodeAllDropDataTypes(ArkUI_NodeHandle node)](#oh_arkui_allownodealldropdatatypes) | Configures the specified component to allow any data types. This API resets the settings configured through [OH_ArkUI_SetNodeAllowedDropDataTypes](capi-drag-and-drop-h.md#oh_arkui_setnodealloweddropdatatypes). Note: Calling  **OH_ArkUI_SetNodeAllowedDropDataTypes** also resets the configuration made by this API. |
| [int32_t OH_ArkUI_SetNodeDraggable(ArkUI_NodeHandle node, bool enabled)](#oh_arkui_setnodedraggable) | Sets whether the component is draggable.|
| [int32_t OH_ArkUI_SetNodeDragPreview(ArkUI_NodeHandle node, OH_PixelmapNative* preview)](#oh_arkui_setnodedragpreview) | Sets a custom drag preview for the specified component.|
| [ArkUI_DragPreviewOption* OH_ArkUI_CreateDragPreviewOption(void)](#oh_arkui_createdragpreviewoption) | Creates an **ArkUI_DragPreviewOption** object.|
| [void OH_ArkUI_DragPreviewOption_Dispose(ArkUI_DragPreviewOption* option)](#oh_arkui_dragpreviewoption_dispose) | Disposes of an **ArkUI_DragPreviewOption** object.|
| [int32_t OH_ArkUI_DragPreviewOption_SetScaleMode(ArkUI_DragPreviewOption* option, ArkUI_DragPreviewScaleMode scaleMode)](#oh_arkui_dragpreviewoption_setscalemode) | Sets the scale mode for an **ArkUI_DragPreviewOption** object.|
| [int32_t OH_ArkUI_DragPreviewOption_SetDefaultShadowEnabled(ArkUI_DragPreviewOption* option, bool enabled)](#oh_arkui_dragpreviewoption_setdefaultshadowenabled) | Sets whether to enable the default shadow effect for an **ArkUI_DragPreviewOption** object. The effect is disabled by default.|
| [int32_t OH_ArkUI_DragPreviewOption_SetDefaultRadiusEnabled(ArkUI_DragPreviewOption* option, bool enabled)](#oh_arkui_dragpreviewoption_setdefaultradiusenabled) | Sets whether to enable the default corner radius effect for an **ArkUI_DragPreviewOption** object. The rounded corner radius is 12.0 vp by default. The effect is disabled by default.|
| [int32_t OH_ArkUI_DragPreviewOption_SetNumberBadgeEnabled(ArkUI_DragPreviewOption* option, bool enabled)](#oh_arkui_dragpreviewoption_setnumberbadgeenabled) | Sets whether to enable the badge for the drag preview. If this feature is enabled, a badge that contains the number of dragged items is displayed. Note: Calling [OH_ArkUI_DragPreviewOption_SetBadgeNumber](#oh_arkui_dragpreviewoption_setbadgenumber) overrides the value set by this API. |
| [int32_t OH_ArkUI_DragPreviewOption_SetBadgeNumber(ArkUI_DragPreviewOption* option, uint32_t forcedNumber)](#oh_arkui_dragpreviewoption_setbadgenumber) | Sets the count on the badge. The settings will overwrite the value in [OH_ArkUI_DragPreviewOption_SetNumberBadgeEnabled](#oh_arkui_dragpreviewoption_setnumberbadgeenabled).|
| [int32_t OH_ArkUI_DragPreviewOption_SetDefaultAnimationBeforeLiftingEnabled(ArkUI_DragPreviewOption* option, bool enabled)](#oh_arkui_dragpreviewoption_setdefaultanimationbeforeliftingenabled) | Sets whether to enable the default animation on a click or touch. This is suitable for scenarios where a press visual feedback is needed before the drag preview lifts. |
| [int32_t OH_ArkUI_SetNodeDragPreviewOption(ArkUI_NodeHandle node, ArkUI_DragPreviewOption* option)](#oh_arkui_setnodedragpreviewoption) | Sets an **ArkUI_DragPreviewOption** object for the specified component.|
| [ArkUI_DragAction* OH_ArkUI_CreateDragActionWithNode(ArkUI_NodeHandle node)](#oh_arkui_createdragactionwithnode) | Creates a drag action object. The object needs to be associated with a UI instance, which can be specified by passing in a component node of the current UI instance.|
| [ArkUI_DragAction* OH_ArkUI_CreateDragActionWithContext(ArkUI_ContextHandle uiContext)](#oh_arkui_createdragactionwithcontext) | Creates a drag action object for the specified UI instance.|
| [void OH_ArkUI_DragAction_Dispose(ArkUI_DragAction* dragAction)](#oh_arkui_dragaction_dispose) | Disposes of an **ArkUI_DragAction** object.|
| [int32_t OH_ArkUI_DragAction_SetPointerId(ArkUI_DragAction* dragAction, int32_t pointer)](#oh_arkui_dragaction_setpointerid) | Sets the pointer ID. If only one finger is used on the screen, the finger ID is 0. Generally, you can set this parameter to **0**.|
| [int32_t OH_ArkUI_DragAction_SetPixelMaps(ArkUI_DragAction* dragAction, OH_PixelmapNative* pixelmapArray[], int32_t size)](#oh_arkui_dragaction_setpixelmaps) | Sets the drag previews for a drag action. Only pixel map objects are supported.|
| [int32_t OH_ArkUI_DragAction_SetTouchPointX(ArkUI_DragAction* dragAction, float x)](#oh_arkui_dragaction_settouchpointx) | Sets the touch point relative to the upper left corner of the first drag preview (pixel map).|
| [int32_t OH_ArkUI_DragAction_SetTouchPointY(ArkUI_DragAction* dragAction, float y)](#oh_arkui_dragaction_settouchpointy) | Sets the touch point relative to the upper left corner of the first drag preview (pixel map).|
| [int32_t OH_ArkUI_DragAction_SetData(ArkUI_DragAction* dragAction, OH_UdmfData* data)](#oh_arkui_dragaction_setdata) | Sets the drag data.|
| [ArkUI_ErrorCode OH_ArkUI_DragAction_SetDataLoadParams(ArkUI_DragAction* dragAction,OH_UdmfDataLoadParams* dataLoadParams)](#oh_arkui_dragaction_setdataloadparams) | Provides data loading parameters to the system instead of directly providing a complete data object. When the user drops data on the target application, the system will use **dataLoadParams** to request data. This can significantly improve the efficiency of dragging large volumes of data and the efficiency of processing the dropped data in the target application. This API must always be used in preference to [OH_ArkUI_DragAction_SetData](#oh_arkui_dragaction_setdata). For details about how to create and prepare data loading parameters, see [OH_UdmfDataLoadParams_Create](../apis-arkdata/capi-udmf-h.md#oh_udmfdataloadparams_create) in **udmf.h**. If this API conflicts with [OH_ArkUI_DragAction_SetData](#oh_arkui_dragaction_setdata), the system always uses the last called API. |
| [int32_t OH_ArkUI_DragAction_SetDragPreviewOption(ArkUI_DragAction* dragAction, ArkUI_DragPreviewOption* option)](#oh_arkui_dragaction_setdragpreviewoption) | Sets an **ArkUI_DragPreviewOption** object for the specified drag action object.|
| [int32_t OH_ArkUI_DragAction_RegisterStatusListener(ArkUI_DragAction* dragAction, void* userData,void(\*listener)(ArkUI_DragAndDropInfo* dragAndDropInfo, void* userData))](#oh_arkui_dragaction_registerstatuslistener) | Registers a drag status listener. This listener can be used to check whether the data is successfully received and processed.|
| [ArkUI_ErrorCode OH_ArkUI_DragEvent_GetDisplayId(ArkUI_DragEvent* event, int32_t* displayId)](#oh_arkui_dragevent_getdisplayid) | Obtains the ID of the display where this drag event occurs. This API is suitable for multi-display device scenarios where you need to determine which display the drag operation occurs on, such as performing differentiated processing based on the display ID during cross-display dragging. This API is not supported when **eventType** is set to **NODE_ON_DRAG_END**. |
| [void OH_ArkUI_DragAction_UnregisterStatusListener(ArkUI_DragAction* dragAction)](#oh_arkui_dragaction_unregisterstatuslistener) | Unregisters a drag status listener.|
| [ArkUI_DragStatus OH_ArkUI_DragAndDropInfo_GetDragStatus(ArkUI_DragAndDropInfo* dragAndDropInfo)](#oh_arkui_draganddropinfo_getdragstatus) | Obtains the drag status of the [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md). **ArkUI_DRAG_STATUS_UNKNOWN** is returned if the acquisition fails.|
| [ArkUI_DragEvent* OH_ArkUI_DragAndDropInfo_GetDragEvent(ArkUI_DragAndDropInfo* dragAndDropInfo)](#oh_arkui_draganddropinfo_getdragevent) | Obtains a drag event based on the specified drag and drop information. The drag event can then be used to obtain the drag result.|
| [int32_t OH_ArkUI_StartDrag(ArkUI_DragAction* dragAction)](#oh_arkui_startdrag) | Initiates a drag action through the specified **DragAction** object.|
| [int32_t OH_ArkUI_DragEvent_RequestDragEndPending(ArkUI_DragEvent* event, int32_t* requestIdentify)](#oh_arkui_dragevent_requestdragendpending) | Requests deferred processing of the drag end event, allowing the application to confirm the operation result. The application must pass the final result back to the system via the [OH_ArkUI_NotifyDragResult](#oh_arkui_notifydragresult) API, and call [OH_ArkUI_NotifyDragEndPendingDone](#oh_arkui_notifydragendpendingdone) after all processing is complete. The maximum waiting time is 2 seconds. |
| [int32_t OH_ArkUI_NotifyDragResult(int32_t requestIdentify, ArkUI_DragResult result)](#oh_arkui_notifydragresult) | Notifies the system of the final drag result. The system will verify whether the request identifier matches that returned by [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending). If they do not match, this call will be ignored. |
| [int32_t OH_ArkUI_NotifySuggestedDropOperation(int32_t requestIdentity, ArkUI_DropOperation operation)](#oh_arkui_notifysuggesteddropoperation) | Notifies the drag initiator of the operation type of the current drop. This API must be called during the drop phase. The drag initiator can call [OH_ArkUI_DragEvent_GetDropOperation](#oh_arkui_dragevent_getdropoperation) in the drag end callback to obtain the operation type of the current drop and perform custom processing. The drag initiator can also ignore the notification. When the drag operation fails, the operation type of the current drop is unreliable. In this case, the operation type obtained by calling [OH_ArkUI_DragEvent_GetDropOperation](#oh_arkui_dragevent_getdropoperation) is always **ARKUI_DROP_OPERATION_COPY**. The system will verify whether the value of **requestIdentity** is the same as that returned by [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending). If they are different, this API call does not take effect. |
| [int32_t OH_ArkUI_NotifyDisableDefaultDropAnimation(int32_t requestIdentity, bool disable)](#oh_arkui_notifydisabledefaultdropanimation) | Notifies the system whether to disable the default drop animation. This API must be called during the drop phase. If the drag fails, the default drop animation is diffusion. If the drag succeeds, the default drop animation is shrinking and fading. Calling this API can disable the default animation and implement a custom drop animation as required. The system will verify whether the value of **requestIdentity** is the same as that returned by [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending). If they are different, this API call does not take effect. |
| [int32_t OH_ArkUI_NotifyDragEndPendingDone(int32_t requestIdentify)](#oh_arkui_notifydragendpendingdone) | Notifies the system that all asynchronous processing has been completed and the drag end pending state can be terminated.|
| [ArkUI_ErrorCode OH_ArkUI_EnableDropDisallowedBadge(ArkUI_ContextHandle uiContext, bool enabled)](#oh_arkui_enabledropdisallowedbadge) | Sets whether the drop-disallowed badge can be displayed.|
| [float OH_ArkUI_DragEvent_GetTouchPointXToGlobalDisplay(ArkUI_DragEvent* event)](#oh_arkui_dragevent_gettouchpointxtoglobaldisplay) | Obtains the x-coordinate of the drag touch point relative to the global display from the specified **ArkUI_DragEvent** object.|
| [float OH_ArkUI_DragEvent_GetTouchPointYToGlobalDisplay(ArkUI_DragEvent* event)](#oh_arkui_dragevent_gettouchpointytoglobaldisplay) | Obtains the y-coordinate of the drag touch point relative to the global display from the specified **ArkUI_DragEvent** object.|
| [ArkUI_ErrorCode OH_ArkUI_DragEvent_GetDragSource(ArkUI_DragEvent* event, char *bundleName, int32_t length)](#oh_arkui_dragevent_getdragsource) | Obtains the bundle name of the drag source application. This API can be used to identify the drag source application, perform verification by source, or execute differentiated processing. When calling this API, you need to pass a character array to receive the bundle name string and explicitly specify the array length. The array length must be no less than 128 characters. |
| [ArkUI_ErrorCode OH_ArkUI_DragEvent_IsRemote(ArkUI_DragEvent* event, bool* isRemote)](#oh_arkui_dragevent_isremote) | Checks whether the current drag operation is a cross-device drag. This API is suitable for scenarios where you need to distinguish between local drag and cross-device drag. For example, cross-device drag may require additional data transmission verification or display different UI prompts, while local drag can process data directly. |

## Enum Description

### ArkUI_DragResult

```c
enum ArkUI_DragResult
```

**Description**

Enumerates drag results, which are set by the data receiver and transferred by the system to the drag source so that the drag source is aware of the data processing result of the receiver.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_DRAG_RESULT_SUCCESSFUL = 0 | The drag and drop operation succeeded.|
| ARKUI_DRAG_RESULT_FAILED = 1 | The drag and drop operation failed.|
| ARKUI_DRAG_RESULT_CANCELED = 2 | The drag and drop operation was canceled.|

### ArkUI_DropOperation

```c
enum ArkUI_DropOperation
```

**Description**

Enumerates data processing modes used when data is dropped, which affects the display of the badge. When the copy operation is set, the badge displays a plus sign (+). When the cut operation is set, the badge does not display a plus sign (+).

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_DROP_OPERATION_COPY = 0 | Copy.|
| ARKUI_DROP_OPERATION_MOVE = 1 | Cut.|

### ArkUI_PreDragStatus

```c
enum ArkUI_PreDragStatus
```

**Description**

Enumerates interaction states prior to a drop and drop operation.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_PRE_DRAG_STATUS_UNKNOWN = -1 | Failed to obtain the status before drag is initiated. |
| ARKUI_PRE_DRAG_STATUS_ACTION_DETECTING = 0 | A drag gesture is being detected.|
| ARKUI_PRE_DRAG_STATUS_READY_TO_TRIGGER_DRAG = 1 | The component is ready to be dragged.|
| ARKUI_PRE_DRAG_STATUS_PREVIEW_LIFT_STARTED = 2 | A lift animation is started.|
| ARKUI_PRE_DRAG_STATUS_PREVIEW_LIFT_FINISHED = 3 | A lift animation is finished.|
| ARKUI_PRE_DRAG_STATUS_PREVIEW_LANDING_STARTED = 4 | A drop animation is started.|
| ARKUI_PRE_DRAG_STATUS_PREVIEW_LANDING_FINISHED = 5 | A drop animation is finished.|
| ARKUI_PRE_DRAG_STATUS_CANCELED_BEFORE_DRAG = 6 | A drop animation is canceled.|

### ArkUI_DragPreviewScaleMode

```c
enum ArkUI_DragPreviewScaleMode
```

**Description**

Enumerates drag preview scale modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_DRAG_PREVIEW_SCALE_AUTO = 0 | Enables the system to automatically change the position of the dragged point based on the scenario and apply scaling transformations to the drag preview based on set rules. |
| ARKUI_DRAG_PREVIEW_SCALE_DISABLED = 1 | Disables the system's scaling behavior for the drag preview.|

### ArkUI_DragStatus

```c
enum ArkUI_DragStatus
```

**Description**

Enumerates drag operation states.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_DRAG_STATUS_UNKNOWN = -1 | Unknown drag state.|
| ARKUI_DRAG_STATUS_STARTED = 0 | The drag operation has started.|
| ARKUI_DRAG_STATUS_ENDED = 1 | The drag operation has ended.|

## Function Description

### OH_ArkUI_NodeEvent_GetDragEvent()

```c
ArkUI_DragEvent* OH_ArkUI_NodeEvent_GetDragEvent(ArkUI_NodeEvent* nodeEvent)
```

**Description**

Obtains a **DragEvent** object from the specified **NodeEvent** object.

**Since**: 12

**Parameters**

| Name                           | Description|
|--------------------------------| -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* nodeEvent | Pointer to the target **ArkUI_NodeEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* | Returns the pointer to an **ArkUI_DragEvent** object; returns null if the parameter passed in is invalid or is not a drag-related event.|

### OH_ArkUI_NodeEvent_GetPreDragStatus()

```c
ArkUI_PreDragStatus OH_ArkUI_NodeEvent_GetPreDragStatus(ArkUI_NodeEvent* nodeEvent)
```

**Description**

Obtains the state prior to a drop and drop operation.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)* nodeEvent | Pointer to the target **ArkUI_NodeEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_PreDragStatus](#arkui_predragstatus) | Interaction status before drag is initiated. |

### OH_ArkUI_DragEvent_DisableDefaultDropAnimation()

```c
int32_t OH_ArkUI_DragEvent_DisableDefaultDropAnimation(ArkUI_DragEvent* event, bool disable)
```

**Description**

Sets whether to disable the default drop animation, which is enabled by default. Use this API to apply a custom drop animation. It has the same functionality as [OH_ArkUI_NotifyDisableDefaultDropAnimation](#oh_arkui_notifydisabledefaultdropanimation), with the following difference: this API sets the configuration directly in a synchronous drag event callback, making it suitable for scenarios where deferred processing of the drag end event is not required; **OH_ArkUI_NotifyDisableDefaultDropAnimation** notifies the configuration in the asynchronous **RequestDragEndPending** flow, making it suitable for scenarios where [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending) has been called to defer processing of the drag end event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| bool disable | Whether to disable the default drop animation. The value **true** means to disable the default drop animation, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_SetSuggestedDropOperation()

```c
int32_t OH_ArkUI_DragEvent_SetSuggestedDropOperation(ArkUI_DragEvent* event, ArkUI_DropOperation dropOperation)
```

**Description**

Sets the data processing mode, which affects how the badge is displayed during dragging. This is suitable for scenarios where you need to suggest data processing behavior to the system when data is dropped. For example, when copyable text or image content is dragged, it is recommended to set the copying behavior (**ARKUI_DROP_OPERATION_COPY**); when dragging content needs to be removed from the source location, it is recommended to set the cutting behavior (**ARKUI_DROP_OPERATION_MOVE**). This API has the same functionality as [OH_ArkUI_NotifySuggestedDropOperation](#oh_arkui_notifysuggesteddropoperation), with the following difference: this API sets the data processing mode directly in a synchronous drag event callback, which is suitable for scenarios where delayed processing of the drag end event is not required; **OH_ArkUI_NotifySuggestedDropOperation** sends the data processing mode notification in the asynchronous **RequestDragEndPending** flow, which is suitable for scenarios where [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending) has been called to delay processing of the drag end event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| [ArkUI_DropOperation](#arkui_dropoperation) dropOperation | Data processing mode, used to set the operation type upon drop. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_SetDragResult()

```c
int32_t OH_ArkUI_DragEvent_SetDragResult(ArkUI_DragEvent* event, ArkUI_DragResult result)
```

**Description**

Sets the result for a drag event. As the data receiver, this API sets the processing result of the drag event in the drop callback so that the drag initiator can perceive the data receiving and processing status. This API has the same functionality as [OH_ArkUI_NotifyDragResult](#oh_arkui_notifydragresult), with the following difference: this API sets the drag result directly in a synchronous drag event callback, which is suitable for scenarios where delayed processing of the drag end event is not required; **OH_ArkUI_NotifyDragResult** sends the result notification in the asynchronous **RequestDragEndPending** flow, which is suitable for scenarios where [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending) has been called to delay processing of the drag end event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| [ArkUI_DragResult](#arkui_dragresult) result | Drag data processing result. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_SetData()

```c
int32_t OH_ArkUI_DragEvent_SetData(ArkUI_DragEvent* event, OH_UdmfData* data)
```

**Description**

Sets drag data for **ArkUI_DragEvent**. [OH_ArkUI_DragEvent_SetDataLoadParams](capi-drag-and-drop-h.md#oh_arkui_dragevent_setdataloadparams) should be used preferentially to provide data loading parameters, so as to improve the efficiency of dragging large amounts of data and the efficiency of processing dropped data in the target application. If this API conflicts with [OH_ArkUI_DragEvent_SetDataLoadParams](capi-drag-and-drop-h.md#oh_arkui_dragevent_setdataloadparams), the system always uses the last called API.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| [OH_UdmfData](../apis-arkdata/capi-udmf-oh-udmfdata.md)* data | Pointer to the drag data object to set. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_SetDataLoadParams()

```c
ArkUI_ErrorCode OH_ArkUI_DragEvent_SetDataLoadParams(ArkUI_DragEvent* event, OH_UdmfDataLoadParams* dataLoadParams)
```

**Description**

Provides data loading parameters to the system instead of directly providing a complete data object. When the user drops data on the target application, the system will use **dataLoadParams** to request data. This can significantly improve the efficiency of dragging large volumes of data and the efficiency of processing the dropped data in the target application. This API must always be used in preference to [OH_ArkUI_DragEvent_SetData](#oh_arkui_dragevent_setdata). For details about how to create and prepare data loading parameters, see [OH_UdmfDataLoadParams_Create](../apis-arkdata/capi-udmf-h.md#oh_udmfdataloadparams_create) in **udmf.h**. If this API conflicts with [OH_ArkUI_DragEvent_SetData](#oh_arkui_dragevent_setdata), the system always uses the last called API.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| [OH_UdmfDataLoadParams](../apis-arkdata/capi-udmf-oh-udmfdataloadparams.md)* dataLoadParams | Data loading parameters used during a drop operation.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_GetUdmfData()

```c
int32_t OH_ArkUI_DragEvent_GetUdmfData(ArkUI_DragEvent* event, OH_UdmfData *data)
```

**Description**

Obtains the drag data from **ArkUI_DragEvent**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| [OH_UdmfData](../apis-arkdata/capi-udmf-oh-udmfdata.md) *data | Pointer to an **OH_UdmfData** object. The application needs to create a pointer for receiving data by using the [OH_UdmfData_Create](../apis-arkdata/capi-udmf-h.md#oh_udmfdata_create) API.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_GetDataTypeCount()

```c
int32_t OH_ArkUI_DragEvent_GetDataTypeCount(ArkUI_DragEvent* event, int32_t* count)
```

**Description**

Obtains the number of drag data types from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| int32_t* count | Number of drag data types returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_GetDataTypes()

```c
int32_t OH_ArkUI_DragEvent_GetDataTypes(ArkUI_DragEvent *event, char *eventTypeArray[], int32_t length, int32_t maxStrLen)
```

**Description**

Obtains the type list of drag data types from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) *event | Pointer to the target **ArkUI_DragEvent** object.|
| char *eventTypeArray[] | Pointer to the list of the drag data types. You need to create a string array first.|
| int32_t length | Total length of the array, which cannot be less than the number obtained using [OH_ArkUI_DragEvent_GetDataTypeCount](#oh_arkui_dragevent_getdatatypecount).|
| int32_t maxStrLen | Maximum string length of the drag data type, used to limit the buffer size of each data type string. Recommended value: no less than 128 characters to ensure that all standard UDMF data type strings can be fully received. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input buffer size is abnormal.|

### OH_ArkUI_DragEvent_GetDragResult()

```c
int32_t OH_ArkUI_DragEvent_GetDragResult(ArkUI_DragEvent* event, ArkUI_DragResult* result)
```

**Description**

Obtains the drag and drop result from the drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| [ArkUI_DragResult](capi-drag-and-drop-h.md#arkui_dragresult)* result | Drag result returned.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_GetDropOperation()

```c
int32_t OH_ArkUI_DragEvent_GetDropOperation(ArkUI_DragEvent* event, ArkUI_DropOperation* operation)
```

**Description**

Obtains the data processing method from **ArkUI_DragEvent**. When the drag fails, the operation type of the current drop is unreliable, and the operation type obtained is always **ARKUI_DROP_OPERATION_COPY**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| [ArkUI_DropOperation](capi-drag-and-drop-h.md#arkui_dropoperation)* operation | Pointer to the data processing mode of the drag event. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>                Possible cause: 1. Parameters are null or the event is not a valid **DragEvent**. |

### OH_ArkUI_DragEvent_GetPreviewTouchPointX()

```c
float OH_ArkUI_DragEvent_GetPreviewTouchPointX(ArkUI_DragEvent* event)
```

**Description**

Obtains the x-coordinate of the touch point for a drag preview from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the touch point, in px, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetPreviewTouchPointY()

```c
float OH_ArkUI_DragEvent_GetPreviewTouchPointY(ArkUI_DragEvent* event)
```

**Description**

Obtains the y-coordinate of the touch point on the preview image from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the touch point, in px. The default value **0** is returned when the input parameter is invalid. |

### OH_ArkUI_DragEvent_GetPreviewRectWidth()

```c
float OH_ArkUI_DragEvent_GetPreviewRectWidth(ArkUI_DragEvent* event)
```

**Description**

Obtains the width of a drag preview from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Width of the drag preview, in px, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetPreviewRectHeight()

```c
float OH_ArkUI_DragEvent_GetPreviewRectHeight(ArkUI_DragEvent* event)
```

**Description**

Obtains the height of a drag preview from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Height of the drag preview, in px, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetTouchPointXToWindow()

```c
float OH_ArkUI_DragEvent_GetTouchPointXToWindow(ArkUI_DragEvent* event)
```

**Description**

Obtains the x-coordinate of the touch point relative to the window from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the touch point relative to the window, in px, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetTouchPointYToWindow()

```c
float OH_ArkUI_DragEvent_GetTouchPointYToWindow(ArkUI_DragEvent* event)
```

**Description**

Obtains the y-coordinate of the touch point relative to the window from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the touch point relative to the window, in px, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetTouchPointXToDisplay()

```c
float OH_ArkUI_DragEvent_GetTouchPointXToDisplay(ArkUI_DragEvent* event)
```

**Description**

Obtains the x-coordinate of the touch point relative to the display from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the touch point relative to the display, in px, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetTouchPointYToDisplay()

```c
float OH_ArkUI_DragEvent_GetTouchPointYToDisplay(ArkUI_DragEvent* event)
```

**Description**

Obtains the y-coordinate of the touch point relative to the display from a drag event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the touch point relative to the display, in px, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetVelocityX()

```c
float OH_ArkUI_DragEvent_GetVelocityX(ArkUI_DragEvent* event)
```

**Description**

Obtains the dragging velocity along the x-axis.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Dragging velocity along the x-axis, in px/s, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetVelocityY()

```c
float OH_ArkUI_DragEvent_GetVelocityY(ArkUI_DragEvent* event)
```

**Description**

Obtains the dragging velocity along the y-axis.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Dragging velocity along the y-axis, in px/s, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetVelocity()

```c
float OH_ArkUI_DragEvent_GetVelocity(ArkUI_DragEvent* event)
```

**Description**

Obtains the dragging velocity along the main axis.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Dragging velocity along the main axis, in px/s, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetModifierKeyStates()

```c
int32_t OH_ArkUI_DragEvent_GetModifierKeyStates(ArkUI_DragEvent* event, uint64_t* keys)
```

**Description**

Obtains the pressed status of modifier keys.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| uint64_t* keys | Pointer to the combination of pressed modifier keys. The value is a bitwise OR of the masks corresponding to each modifier key: the **Ctrl** key corresponds to bit 0 (mask value 0x1), the **Shift** key corresponds to bit 1 (mask value 0x2), and the **Alt** key corresponds to bit 2 (mask value 0x4). The application can use bitwise operations to determine which keys are pressed, for example, using **(*keys & 0x1)** to check whether the **Ctrl** key is pressed. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_StartDataLoading()

```c
int32_t OH_ArkUI_DragEvent_StartDataLoading(ArkUI_DragEvent* event, OH_UdmfGetDataParams* options, char* key, unsigned int keyLen)
```

**Description**

Starts data synchronization using the specified synchronization parameters. When this API is used in **NODE_ON_DROP**, to avoid accidentally obtaining data before **NODE_ON_DROP** is executed, data prefetching must first be disabled through [OH_ArkUI_DisableDropDataPrefetchOnNode](capi-drag-and-drop-h.md#oh_arkui_disabledropdataprefetchonnode).

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| [OH_UdmfGetDataParams](../apis-arkdata/capi-udmf-oh-udmfgetdataparams.md)* options | Pointer to the option array for data obtaining, used to configure data request options during this drag data synchronization. |
| char* key | Pointer to the key value allocated after data loading is successfully started. The length of the character array used to receive the key must be no less than that specified by [UDMF_KEY_BUFFER_LEN](../apis-arkdata/capi-udmf-h.md#udmf_key_buffer_len). |
| unsigned int keyLen | Length of the key string. It must be no less than the length defined by [UDMF_KEY_BUFFER_LEN](../apis-arkdata/capi-udmf-h.md#udmf_key_buffer_len), which is used to ensure that the key can be completely received. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CancelDataLoading()

```c
int32_t OH_ArkUI_CancelDataLoading(ArkUI_ContextHandle uiContext, const char* key)
```

**Description**

Cancels the ongoing data synchronization.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | Pointer to the UI instance.|
| const char* key | Pointer to the data key returned by [OH_ArkUI_DragEvent_StartDataLoading](capi-drag-and-drop-h.md#oh_arkui_dragevent_startdataloading). |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DisableDropDataPrefetchOnNode()

```c
int32_t OH_ArkUI_DisableDropDataPrefetchOnNode(ArkUI_NodeHandle node, bool disabled)
```

**Description**

Sets whether to disable the data prefetch process before executing [NODE_ON_DROP](./capi-native-node-h.md#arkui_nodeeventtype). The system will retry data fetching until the maximum time limit (currently 2.4 seconds) is reached, which is useful for cross-device drag and drop operations as it helps stabilize system communication. However, this feature is redundant for the [OH_ArkUI_DragEvent_StartDataLoading](capi-drag-and-drop-h.md#oh_arkui_dragevent_startdataloading) API. Since this API uses an asynchronous mechanism to fetch data, when [OH_ArkUI_DragEvent_StartDataLoading](capi-drag-and-drop-h.md#oh_arkui_dragevent_startdataloading) is used in **NODE_ON_DROP**, this field must be set to **true** to prevent accidental data fetching before **NODE_ON_DROP** is executed.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|
| bool disabled | Whether to disable data prefetching. The value **true** means to disable it, and **false** means the opposite. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SetDragEventStrictReportWithNode()

```c
int32_t OH_ArkUI_SetDragEventStrictReportWithNode(ArkUI_NodeHandle node, bool enabled)
```

**Description**

Sets whether to enable strict reporting on drag events. This feature is disabled by default, and you are advised to enable it. If this feature is disabled, the parent component is not notified when an item in it is dragged over its child component. If this feature is enabled, the component is notified of the dragged item's leaving, and the child component to which the dragged item is dropped is notified of the item's entering. This configuration is related to a specific UI instance. You can pass in a specific component node on the current UI instance for association.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|
| bool enabled | Whether to enable strict reporting on drag events. The value **true** means to enable strict reporting on drag events, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SetDragEventStrictReportWithContext()

```c
int32_t OH_ArkUI_SetDragEventStrictReportWithContext(ArkUI_ContextHandle uiContext, bool enabled)
```

**Description**

Sets whether to enable strict reporting on drag events. This feature is disabled by default, and you are advised to enable it. If this feature is disabled, the parent component is not notified when an item in it is dragged over its child component. If this feature is enabled, the component is notified of the dragged item's leaving, and the child component to which the dragged item is dropped is notified of the item's entering. This configuration is related to a specific UI instance. You can pass in a specific UI instance for association.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | Pointer to the UI instance.|
| bool enabled | Whether to enable strict reporting on drag events. The value **true** means to enable strict reporting on drag events, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SetNodeAllowedDropDataTypes()

```c
int32_t OH_ArkUI_SetNodeAllowedDropDataTypes(ArkUI_NodeHandle node, const char* typesArray[], int32_t count)
```

**Description**

Sets the types of data that can be dropped to the specified component. This API resets the settings configured through [OH_ArkUI_DisallowNodeAnyDropDataTypes](capi-drag-and-drop-h.md#oh_arkui_disallownodeanydropdatatypes) or [OH_ArkUI_AllowNodeAllDropDataTypes](capi-drag-and-drop-h.md#oh_arkui_allownodealldropdatatypes).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|
| const char* typesArray[] | Pointer to the array of types of data that can be dropped. The array elements are strings of unified data type identifiers defined by UDMF. |
| int32_t count | Length of the array, indicating the number of data type strings in **typesArray**. The number must be consistent with the actual number of elements in **typesArray**. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DisallowNodeAnyDropDataTypes()

```c
int32_t OH_ArkUI_DisallowNodeAnyDropDataTypes(ArkUI_NodeHandle node)
```

**Description**

Configures the specified component to disallow any data types. This API resets the settings configured through [OH_ArkUI_SetNodeAllowedDropDataTypes](capi-drag-and-drop-h.md#oh_arkui_setnodealloweddropdatatypes). Note: Calling **OH_ArkUI_SetNodeAllowedDropDataTypes** also resets the configuration made by this API.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AllowNodeAllDropDataTypes()

```c
int32_t OH_ArkUI_AllowNodeAllDropDataTypes(ArkUI_NodeHandle node)
```

**Description**

Configures the specified component to allow any data types. This API resets the settings configured through [OH_ArkUI_SetNodeAllowedDropDataTypes](capi-drag-and-drop-h.md#oh_arkui_setnodealloweddropdatatypes). Note: Calling **OH_ArkUI_SetNodeAllowedDropDataTypes** also resets the configuration made by this API.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SetNodeDraggable()

```c
int32_t OH_ArkUI_SetNodeDraggable(ArkUI_NodeHandle node, bool enabled)
```

**Description**

Sets whether the component is draggable.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|
| bool enabled | Whether the component is draggable. The value **true** means that the component is draggable, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SetNodeDragPreview()

```c
int32_t OH_ArkUI_SetNodeDragPreview(ArkUI_NodeHandle node, OH_PixelmapNative* preview)
```

**Description**

Sets a custom drag preview for the specified component.

**Since**: 12

**Parameters**

| Name                                                             | Description|
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|
| [OH_PixelmapNative](capi-arkui-nativemodule-oh-pixelmapnative8h.md)* preview                                   | Custom drag preview, which is a pixel map.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CreateDragPreviewOption()

```c
ArkUI_DragPreviewOption* OH_ArkUI_CreateDragPreviewOption(void)
```

**Description**

Creates an **ArkUI_DragPreviewOption** object. When the object is no longer needed, you can call [OH_ArkUI_DragPreviewOption_Dispose](#oh_arkui_dragpreviewoption_dispose) to dispose of it to prevent resource leaks.

**Since**: 12

**Return value**

| Type                          | Description|
|------------------------------| -- |
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* | Pointer to the **ArkUI_DragPreviewOption** object, which is used to configure custom parameters for the drag preview. |

### OH_ArkUI_DragPreviewOption_Dispose()

```c
void OH_ArkUI_DragPreviewOption_Dispose(ArkUI_DragPreviewOption* option)
```

**Description**

Disposes of an **ArkUI_DragPreviewOption** object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* option | Pointer to the custom drag preview parameter object to dispose of. |

### OH_ArkUI_DragPreviewOption_SetScaleMode()

```c
int32_t OH_ArkUI_DragPreviewOption_SetScaleMode(ArkUI_DragPreviewOption* option, ArkUI_DragPreviewScaleMode scaleMode)
```

**Description**

Sets whether the drag preview is automatically scaled according to the system definition. This API is suitable for scenarios where the drag preview size needs to be adjusted according to system rules during dragging, or where the original size of the custom drag preview needs to be maintained.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* option | Pointer to the custom drag preview parameter object, which is used to set the scale mode of the drag preview. |
| [ArkUI_DragPreviewScaleMode](capi-drag-and-drop-h.md#arkui_dragpreviewscalemode) scaleMode | Scale mode to set.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragPreviewOption_SetDefaultShadowEnabled()

```c
int32_t OH_ArkUI_DragPreviewOption_SetDefaultShadowEnabled(ArkUI_DragPreviewOption* option, bool enabled)
```

**Description**

Sets whether to enable the default shadow effect for an **ArkUI_DragPreviewOption** object. The effect is disabled by default.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* option | Pointer to the custom drag preview parameter object, which is used to set the default projection effect of the drag preview. |
| bool enabled | Whether to enable the default shadow effect. The value **true** means to enable the default shadow effect, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragPreviewOption_SetDefaultRadiusEnabled()

```c
int32_t OH_ArkUI_DragPreviewOption_SetDefaultRadiusEnabled(ArkUI_DragPreviewOption* option, bool enabled)
```

**Description**

Sets whether to enable the default corner radius effect for an **ArkUI_DragPreviewOption** object. The rounded corner radius is 12.0 vp by default. The effect is disabled by default.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* option | Pointer to the custom drag preview parameter object, which is used to set the default corner radius effect of the drag preview. |
| bool enabled | Whether to enable the default corner radius effect. The value **true** means to enable the default corner radius effect, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragPreviewOption_SetNumberBadgeEnabled()

```c
int32_t OH_ArkUI_DragPreviewOption_SetNumberBadgeEnabled(ArkUI_DragPreviewOption* option, bool enabled)
```

**Description**

Sets whether to enable the badge for an **ArkUI_DragPreviewOption** object. If this feature is enabled, a badge that contains the number of dragged items is displayed. Note: Calling [OH_ArkUI_DragPreviewOption_SetBadgeNumber](#oh_arkui_dragpreviewoption_setbadgenumber) overrides the value set by this API.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* option | Pointer to the custom drag preview parameter object, which is used to set whether to display the count badge on the drag preview. |
| bool enabled | Whether to enable the badge. The value **true** means to enable the badge, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragPreviewOption_SetBadgeNumber()

```c
int32_t OH_ArkUI_DragPreviewOption_SetBadgeNumber(ArkUI_DragPreviewOption* option, uint32_t forcedNumber)
```

**Description**

Sets the count on the badge. The settings will overwrite the value in [OH_ArkUI_DragPreviewOption_SetNumberBadgeEnabled](#oh_arkui_dragpreviewoption_setnumberbadgeenabled).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* option | Pointer to the custom drag preview parameter object, which is used to set the count that is forcibly displayed on the badge. |
| uint32_t forcedNumber | Count on the badge. The value is a positive integer used to forcibly specify the count displayed on the badge. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragPreviewOption_SetDefaultAnimationBeforeLiftingEnabled()

```c
int32_t OH_ArkUI_DragPreviewOption_SetDefaultAnimationBeforeLiftingEnabled(ArkUI_DragPreviewOption* option, bool enabled)
```

**Description**

Sets whether to enable the default animation on a click or touch. This API is suitable for scenarios where press visual feedback is needed before the drag preview lifts.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* option | Pointer to the custom drag preview parameter object. |
| bool enabled | Whether to enable the default animation on a click or touch. The value **true** means to enable the default animation on a click or touch, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SetNodeDragPreviewOption()

```c
int32_t OH_ArkUI_SetNodeDragPreviewOption(ArkUI_NodeHandle node, ArkUI_DragPreviewOption* option)
```

**Description**

Sets an **ArkUI_DragPreviewOption** object for the specified component.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* option | Pointer to the custom drag preview parameter object to be set on the target component. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CreateDragActionWithNode()

```c
ArkUI_DragAction* OH_ArkUI_CreateDragActionWithNode(ArkUI_NodeHandle node)
```

**Description**

Creates a drag operation object, which must be associated with a UI instance. This can be specified by passing in a component node of the current UI instance. After the object is used, you need to call [OH_ArkUI_DragAction_Dispose](#oh_arkui_dragaction_dispose) to dispose of it to prevent resource leaks.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the component node.|

**Return value**

| Type                   | Description|
|-----------------------| -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* | Pointer to the **ArkUI_DragAction** object, which is used to configure and initiate a drag operation. If creation fails, null is returned. |

### OH_ArkUI_CreateDragActionWithContext()

```c
ArkUI_DragAction* OH_ArkUI_CreateDragActionWithContext(ArkUI_ContextHandle uiContext)
```

**Description**

Creates a drag operation object, which must be associated with a UI instance. This can be associated by passing in a UI instance pointer. After the object is used, you need to call [OH_ArkUI_DragAction_Dispose](#oh_arkui_dragaction_dispose) to dispose of it to prevent resource leaks.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | Pointer to the UI instance.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* | Pointer to the **ArkUI_DragAction** object, which is used to configure and initiate a drag operation. If creation fails, null is returned. |

### OH_ArkUI_DragAction_Dispose()

```c
void OH_ArkUI_DragAction_Dispose(ArkUI_DragAction* dragAction)
```

**Description**

Disposes of an **ArkUI_DragAction** object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Pointer to the target drag action object.|

### OH_ArkUI_DragAction_SetPointerId()

```c
int32_t OH_ArkUI_DragAction_SetPointerId(ArkUI_DragAction* dragAction, int32_t pointer)
```

**Description**

Sets the pointer ID. If only one finger is used on the screen, the finger ID is 0. Generally, you can set this parameter to **0**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Pointer to the target drag action object.|
| int32_t pointer | Pointer ID. The value ranges from 0 to 9. If the value is out of the range, **-1** is used by default.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragAction_SetPixelMaps()

```c
int32_t OH_ArkUI_DragAction_SetPixelMaps(ArkUI_DragAction* dragAction, OH_PixelmapNative* pixelmapArray[], int32_t size)
```

**Description**

Sets the drag previews for a drag action. Only pixel map objects are supported.

**Since**: 12

**Parameters**

| Name                                                                                 | Description|
|--------------------------------------------------------------------------------------| -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction          | Pointer to the target drag action object.|
| [OH_PixelmapNative](capi-arkui-nativemodule-oh-pixelmapnative8h.md)* pixelmapArray[] | Array of the drag previews to set, which must be pixel maps.<br>Note: This parameter must be an object allocated on the heap. You need to manually manage the lifecycle of the object.|
| int32_t size | Number of drag previews. The value must be a positive integer and must match the actual number of elements in **pixelmapArray**. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragAction_SetTouchPointX()

```c
int32_t OH_ArkUI_DragAction_SetTouchPointX(ArkUI_DragAction* dragAction, float x)
```

**Description**

Sets the touch point relative to the upper left corner of the first drag preview (pixel map).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Pointer to the target drag action object.|
| float x | X-coordinate of the touch point, in px.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragAction_SetTouchPointY()

```c
int32_t OH_ArkUI_DragAction_SetTouchPointY(ArkUI_DragAction* dragAction, float y)
```

**Description**

Sets the touch point relative to the upper left corner of the first drag preview (pixel map).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Pointer to the target drag action object.|
| float y | Y-coordinate of the touch point, in px.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragAction_SetData()

```c
int32_t OH_ArkUI_DragAction_SetData(ArkUI_DragAction* dragAction, OH_UdmfData* data)
```

**Description**

Sets drag data. [OH_ArkUI_DragAction_SetDataLoadParams](capi-drag-and-drop-h.md#oh_arkui_dragaction_setdataloadparams) should be used preferentially to provide data loading parameters, so as to improve the efficiency of dragging large amounts of data and the efficiency of processing dropped data in the target application. If this API conflicts with [OH_ArkUI_DragAction_SetDataLoadParams](capi-drag-and-drop-h.md#oh_arkui_dragaction_setdataloadparams), the system always uses the last called API.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Pointer to the target drag action object.|
| [OH_UdmfData](../apis-arkdata/capi-udmf-oh-udmfdata.md)* data | Pointer to the drag data object to set. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragAction_SetDataLoadParams()

```c
ArkUI_ErrorCode OH_ArkUI_DragAction_SetDataLoadParams(ArkUI_DragAction* dragAction, OH_UdmfDataLoadParams* dataLoadParams)
```

**Description**

Provides data loading parameters to the system instead of directly providing a complete data object. When the user drops data on the target application, the system will use **dataLoadParams** to request data. This can significantly improve the efficiency of dragging large volumes of data and the efficiency of processing the dropped data in the target application. This API must always be used in preference to [OH_ArkUI_DragAction_SetData](#oh_arkui_dragaction_setdata). For details about how to create and prepare data loading parameters, see [OH_UdmfDataLoadParams_Create](../apis-arkdata/capi-udmf-h.md#oh_udmfdataloadparams_create) in **udmf.h**. If this API conflicts with [OH_ArkUI_DragAction_SetData](#oh_arkui_dragaction_setdata), the system always uses the last called API.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Pointer to the target drag action object.|
| [OH_UdmfDataLoadParams](../apis-arkdata/capi-udmf-oh-udmfdataloadparams.md)* dataLoadParams | Data loading parameters used during a drop operation.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragAction_SetDragPreviewOption()

```c
int32_t OH_ArkUI_DragAction_SetDragPreviewOption(ArkUI_DragAction* dragAction, ArkUI_DragPreviewOption* option)
```

**Description**

Sets an **ArkUI_DragPreviewOption** object for the specified drag action object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Pointer to the target drag action object.|
| [ArkUI_DragPreviewOption](capi-arkui-nativemodule-arkui-dragpreviewoption.md)* option | Pointer to the custom drag preview parameter object to be set on **ArkUI_DragAction**. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragAction_RegisterStatusListener()

```c
int32_t OH_ArkUI_DragAction_RegisterStatusListener(ArkUI_DragAction* dragAction, void* userData, void(*listener)(ArkUI_DragAndDropInfo* dragAndDropInfo, void* userData))
```

**Description**

Registers a drag status listener, which can perceive the status of the drag having been initiated or the user having released to end. Through this listener, you can obtain whether the data receiving and processing by the drop target is successful. When the drag status no longer needs to be listened for, you need to call [OH_ArkUI_DragAction_UnregisterStatusListener](#oh_arkui_dragaction_unregisterstatuslistener) to unregister the listener.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Pointer to the target drag action object.|
| void* userData | Pointer to the user-defined data. After the status listener is registered, the data will be passed back through the **userData** parameter of the listener when the callback is triggered. |
| listener | Status listener callback. The signature is **void(*listener)(ArkUI_DragAndDropInfo* dragAndDropInfo, void* userData)**. **dragAndDropInfo** indicates the pointer to the drag status object returned by the system. This pointer will be destroyed after the callback execution is complete, and the application should no longer hold it. **userData** indicates the user-defined data passed in during registration. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_GetDisplayId()

```c
ArkUI_ErrorCode OH_ArkUI_DragEvent_GetDisplayId(ArkUI_DragEvent* event, int32_t* displayId)
```

**Description**

Obtains the ID of the display where this drag event occurs. This is suitable for multi-display device scenarios where it is necessary to determine which display the drag operation occurs on, such as performing differentiated processing based on the display ID during cross-screen dragging. This API is not supported when **eventType** is set to **NODE_ON_DRAG_END**.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| int32_t* displayId | Pointer to the ID of the display where the current drag event occurs.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragAction_UnregisterStatusListener()

```c
void OH_ArkUI_DragAction_UnregisterStatusListener(ArkUI_DragAction* dragAction)
```

**Description**

Unregisters a drag status listener.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Pointer to the target drag action object.|

### OH_ArkUI_DragAndDropInfo_GetDragStatus()

```c
ArkUI_DragStatus OH_ArkUI_DragAndDropInfo_GetDragStatus(ArkUI_DragAndDropInfo* dragAndDropInfo)
```

**Description**

Obtains the drag status of the [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md). **ArkUI_DRAG_STATUS_UNKNOWN** is returned if the acquisition fails.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAndDropInfo](capi-arkui-nativemodule-arkui-draganddropinfo.md)* dragAndDropInfo | Drag and drop information returned by the drag status listener.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_DragStatus](capi-drag-and-drop-h.md#arkui_dragstatus) | Drag status. If the status fails to be obtained, the default value **ArkUI_DRAG_STATUS_UNKNOWN** is returned. |

### OH_ArkUI_DragAndDropInfo_GetDragEvent()

```c
ArkUI_DragEvent* OH_ArkUI_DragAndDropInfo_GetDragEvent(ArkUI_DragAndDropInfo* dragAndDropInfo)
```

**Description**

Obtains **DragEvent** through **dragAndDropInfo**. **DragEvent** can be used to obtain the drop result.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAndDropInfo](capi-arkui-nativemodule-arkui-draganddropinfo.md)* dragAndDropInfo | Drag and drop information returned by the drag status listener.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* | Pointer to the drag event object. If the obtaining fails, null is returned. |

### OH_ArkUI_StartDrag()

```c
int32_t OH_ArkUI_StartDrag(ArkUI_DragAction* dragAction)
```

**Description**

Initiates a drag action through the specified **DragAction** object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragAction](capi-arkui-nativemodule-arkui-dragaction.md)* dragAction | Drag action object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_RequestDragEndPending()

```c
int32_t OH_ArkUI_DragEvent_RequestDragEndPending(ArkUI_DragEvent* event, int32_t* requestIdentify)
```

**Description**

Requests deferred processing of the drag end event, allowing the application to confirm the operation result. The application must pass the final result back to the system via the [OH_ArkUI_NotifyDragResult](#oh_arkui_notifydragresult) API, and call [OH_ArkUI_NotifyDragEndPendingDone](#oh_arkui_notifydragendpendingdone) after all processing is complete. The maximum waiting time is 2 seconds.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| int32_t* requestIdentify | System-generated request identifier, which is an output parameter and must point to a valid address.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the request operation is not allowed in the current drag-and-drop event processing phase. |

### OH_ArkUI_NotifyDragResult()

```c
int32_t OH_ArkUI_NotifyDragResult(int32_t requestIdentify, ArkUI_DragResult result)
```

**Description**

Notifies the system of the final drag result. The system will verify whether the request identifier matches that returned by [OH_ArkUI_DragEvent_RequestDragEndPending](capi-drag-and-drop-h.md#oh_arkui_dragevent_requestdragendpending). If they do not match, this call will be ignored.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| int32_t requestIdentify | Identifier returned by [OH_ArkUI_DragEvent_RequestDragEndPending](capi-drag-and-drop-h.md#oh_arkui_dragevent_requestdragendpending).|
| [ArkUI_DragResult](capi-drag-and-drop-h.md#arkui_dragresult) result | Enumerated value of the drag result (of the [ArkUI_DragResult](capi-drag-and-drop-h.md#arkui_dragresult) type).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the request operation is not allowed in the current drag-and-drop event processing phase. |

### OH_ArkUI_NotifySuggestedDropOperation()

```c
int32_t OH_ArkUI_NotifySuggestedDropOperation(int32_t requestIdentify, ArkUI_DropOperation operation)
```

**Description**

Notifies the drag initiator of the operation type of the current drop. This API must be called during the drop phase. The drag initiator can call [OH_ArkUI_DragEvent_GetDropOperation](#oh_arkui_dragevent_getdropoperation) in the drag end callback to obtain the operation type of the current drop and perform custom processing. The drag initiator can also ignore the notification. If the drag operation fails, the operation type of the current drop is unreliable. In this case, the operation type obtained by calling [OH_ArkUI_DragEvent_GetDropOperation](#oh_arkui_dragevent_getdropoperation) is always **ARKUI_DROP_OPERATION_COPY**. The system will verify whether the value of **requestIdentity** is the same as that returned by [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending). If they are different, this API call does not take effect.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| int32_t requestIdentify | Identifier returned by [OH_ArkUI_DragEvent_RequestDragEndPending](capi-drag-and-drop-h.md#oh_arkui_dragevent_requestdragendpending), which is used to identify the drag event.|
| [ArkUI_DropOperation](capi-drag-and-drop-h.md#arkui_dropoperation) operation | Operation type of the current drop.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the API is not called in the drop phase.|

### OH_ArkUI_NotifyDisableDefaultDropAnimation()

```c
int32_t OH_ArkUI_NotifyDisableDefaultDropAnimation(int32_t requestIdentity, bool disable)
```

**Description**

Notifies the system whether to disable the default drop animation. This API must be called during the drop phase. If the drag fails, the default drop animation is diffusion. If the drag succeeds, the default drop animation is shrinking and fading. Calling this API can disable the default animation and implement a custom drop animation as required. The system will verify whether the value of **requestIdentity** is the same as that returned by [OH_ArkUI_DragEvent_RequestDragEndPending](#oh_arkui_dragevent_requestdragendpending). If they are different, this API call does not take effect.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| int32_t requestIdentify | Identifier returned by [OH_ArkUI_DragEvent_RequestDragEndPending](capi-drag-and-drop-h.md#oh_arkui_dragevent_requestdragendpending), which is used to identify the drag event.|
| bool disable | Whether to disable the default drop animation. **true** if disable; **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the API is not called in the drop phase.|

### OH_ArkUI_NotifyDragEndPendingDone()

```c
int32_t OH_ArkUI_NotifyDragEndPendingDone(int32_t requestIdentify)
```

**Description**

Notifies the system that all asynchronous processing is complete and the drag end pending state can be ended. The system will verify whether the value of **requestIdentify** matches the identifier returned by [OH_ArkUI_DragEvent_RequestDragEndPending](capi-drag-and-drop-h.md#oh_arkui_dragevent_requestdragendpending). If they do not match or the current state is not in the drop phase, this call does not take effect.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| int32_t requestIdentify | Identifier returned by [OH_ArkUI_DragEvent_RequestDragEndPending](capi-drag-and-drop-h.md#oh_arkui_dragevent_requestdragendpending).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the request operation is not allowed in the current drag-and-drop event processing phase. |

### OH_ArkUI_EnableDropDisallowedBadge()

```c
ArkUI_ErrorCode OH_ArkUI_EnableDropDisallowedBadge(ArkUI_ContextHandle uiContext, bool enabled)
```

**Description**

Sets whether the drop-disallowed badge can be displayed. This API is suitable for scenarios where a drop-disallowed badge is needed to prompt the user when data is dragged to a target area that does not allow dropping or does not support receiving the current data type.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | Pointer to the UI instance.|
| bool enabled | Whether the drop-disallowed badge can be displayed. The value **true** means that the drop-disallowed badge can be displayed, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_GetTouchPointXToGlobalDisplay()

```c
float OH_ArkUI_DragEvent_GetTouchPointXToGlobalDisplay(ArkUI_DragEvent* event)
```

**Description**

Obtains the x-coordinate of the drag touch point relative to the global display from the specified **ArkUI_DragEvent** object.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the touch point relative to the global display, in px, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetTouchPointYToGlobalDisplay()

```c
float OH_ArkUI_DragEvent_GetTouchPointYToGlobalDisplay(ArkUI_DragEvent* event)
```

**Description**

Obtains the y-coordinate of the drag touch point relative to the global display from the specified **ArkUI_DragEvent** object.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the touch point relative to the global display, in px, or the default value **0** if the input parameter is invalid.|

### OH_ArkUI_DragEvent_GetDragSource()

```c
ArkUI_ErrorCode OH_ArkUI_DragEvent_GetDragSource(ArkUI_DragEvent* event, char *bundleName, int32_t length)
```

**Description**

Obtains the bundle name of the drag source application. This API can be used to identify the drag source application, perform verification based on the source, or execute differentiated processing. When calling, a character array must be passed to receive the bundle name string, and the array length must be explicitly specified, with a length of no less than 128 characters.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| char *bundleName | Character array to store the bundle name string, with a length of at least 128 characters.|
| int32_t length | Length of the character array to store the bundle name string. The minimum length is 128 characters.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_DragEvent_IsRemote()

```c
ArkUI_ErrorCode OH_ArkUI_DragEvent_IsRemote(ArkUI_DragEvent* event, bool* isRemote)
```

**Description**

Checks whether the current drag operation is a cross-device drag. This API is suitable for scenarios where it is necessary to distinguish between local drag and cross-device drag. For example, cross-device dragging may require additional verification of data transmission or display different UI prompts, while local dragging can process data directly.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md)* event | Pointer to the target **ArkUI_DragEvent** object.|
| bool* isRemote | Pointer to a boolean variable to store the result. The value **true** means that the current drag operation is a cross-device drag, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|