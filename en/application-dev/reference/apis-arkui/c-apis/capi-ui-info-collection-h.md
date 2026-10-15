# ui_info_collection.h

## Overview

Declares the APIs used by in-app intelligent agents and UI automation to observe UI interaction events and hit nodes.<br> Status-returning functions report errors through ArkUI_ErrorCode. Asynchronous execution results are reported through the documented completion callback. errno is not an error-reporting channel for these APIs; its value after a call is unspecified and must not be used to determine success or failure.

**Include**: <arkui/ui_info_collection.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) | OH_ArkUI_NativeModule_UIAgentTreeRequest | Declare a UI tree collection request structure. |
| [OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md) | OH_ArkUI_NativeModule_UIContentChangeEvent | Declare the ArkUI content change event structure. |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md) | OH_ArkUI_NativeModule_ImageCollection | ArkUI image acquisition result structure declaration |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType](#oh_arkui_nativemodule_uiinfocollection_interactioneventtype) | OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType | Enumerates the observable UI interaction event types.<br> The values are bit flags. They are used to build the eventMask passed to [OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver). |
| [OH_ArkUI_NativeModule_UIAgentTreeType](#oh_arkui_nativemodule_uiagenttreetype) | OH_ArkUI_NativeModule_UIAgentTreeType | Enumeration of the collection type of the UI tree. |
| [OH_ArkUI_NativeModule_UIContentChangeEventCategory](#oh_arkui_nativemodule_uicontentchangeeventcategory) | OH_ArkUI_NativeModule_UIContentChangeEventCategory | UI Content Change Event Type Enumeration |
| [OH_ArkUI_NativeModule_UIContentChangeIgnoreType](#oh_arkui_nativemodule_uicontentchangeignoretype) | OH_ArkUI_NativeModule_UIContentChangeIgnoreType | UI Content Change Event Ignore Enumeration |
| [OH_ArkUI_NativeModule_UIContentChangeEventType](#oh_arkui_nativemodule_uicontentchangeeventtype) | OH_ArkUI_NativeModule_UIContentChangeEventType | Enumerates ArkUI state change event types. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback)(const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)](#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback) | OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback | Callback type for receiving a sensed interaction event.<br> The callback carries a borrowed [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) object that holds the event payload. The object is valid only within the callback invocation; the callback must not retain or destroy it. All positional coordinates in the payload are relative to the screen (display), in physical pixels (px). The payload always includes a top-level schemaVersion field. Its top-level structure is { "schemaVersion": 1, "type": "<event type>", ... }.<br> The event-specific fields are listed below. - Tap or click: id, point, count, fingers. - Long press: id, point, actualDuration (milliseconds), action ("end"). - Pan: id, point, direction, action ("start" \| "end" \| "cancel"). - Pinch: id, point (array of [x, y]), fingers, action ("start" \| "end" \| "cancel"); scale is present only on "end". - Rotation: id, point (array of [x, y]), fingers, action ("start" \| "end" \| "cancel"); angle (degrees) is present only on "end". - Swipe: id, downPoint (array of [x, y]), upPoint (array of [x, y]), direction, speed, actualSpeed. - Drag: action ("start" \| "end"); "start" carries id, point, hostName, actualDuration; "end" carries point, dropResult ("success" \| "fail"), id (target, present only on success), hostName. - Touch: action ("down" \| "up"), fingerId, point; "down" also carries id (hit node ID). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver(ArkUI_ContextHandle uiContext, uint32_t eventMask, uint32_t *registerID, OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback callback, void *userData)](#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver) | - | Registers an observer for UI interaction events.<br> The observer receives callbacks only for the event types included in eventMask. Multiple observers can be registered for the same UI instance. Registering the same callback and userData pair again creates an additional independent observer with a new registration ID.<br> Remember to unregister the callback by [OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver) when it's not used anymore. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver(uint32_t registerID)](#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver) | - | Unregisters an interaction observer.<br> After this call completes, the associated callback is no longer invoked.<br> This function is thread-safe, can be called from any thread, does not block the caller, and is not async-signal-safe. |
| [typedef void (\*OH_ArkUI_NativeModule_UIAgentJsonCallback)(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)](#oh_arkui_nativemodule_uiagentjsoncallback) | OH_ArkUI_NativeModule_UIAgentJsonCallback | Defines the callback invoked after an asynchronous JSON tree request completes.<br> The callback is invoked exactly once on the UI thread for each accepted request. The callback receives ownership of a non-NULL JSON object only when errorCode is ARKUI_ERROR_CODE_NO_ERROR. The caller must release the object by calling OH_ArkUI_NativeModule_UIJsonWrapperDestroy. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestCreate(OH_ArkUI_NativeModule_UIAgentTreeType treeType, OH_ArkUI_NativeModule_UIAgentTreeRequest **request)](#oh_arkui_nativemodule_uiagenttreerequestcreate) | - | Create a UI tree collection request. |
| [void OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy(OH_ArkUI_NativeModule_UIAgentTreeRequest *request)](#oh_arkui_nativemodule_uiagenttreerequestdestroy) | - | Destroys the UI tree collection request object.<br> Passing NULL has no effect. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetfilterpurelayoutnodes) | - | Sets whether pure layout nodes are filtered from the returned tree.<br> Filtering is disabled by default. When enabled, retained descendants of a filtered node are attached to the nearest retained ancestor while preserving their relative order. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes) | - | Sets whether fully occluded nodes are filtered from the returned tree.<br> Filtering is disabled by default and can be enabled only for visible-tree requests. Enabling occlusion filtering may add substantial computational overhead to collection. Use this option judiciously based on the complexity of the UI. Disabling this option does not disable visibility, clipping, off-screen, or fully transparent node filtering.<br> The occluder opacity threshold is configured separately by [OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold). Changing this option does not change that threshold. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, float threshold)](#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold) | - | Sets the minimum final opacity for a node to participate as an occluder.<br> The default value is 1.0. The option is supported only for visible-tree requests. A target node is removed only when the union of qualifying occluder regions fully covers its effective visible region.<br> This threshold will not work if the filter option is not enabled by [OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetinteractioninfo) | - | Sets whether additional interaction information is collected.<br> Collection is disabled by default. When enabled, the result includes supported interaction information, such as whether a node is clickable, focusable, or editable. This option does not register event observers or change the interaction behavior of any node.<br> Disabling this option does not remove fields included in the default simplified result. Advanced property collection does not implicitly enable this option or collect fields reserved for this option. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetaccessibilityinfo) | - | Sets whether additional accessibility information is collected.<br> Collection is disabled by default. When enabled, the result includes supported accessibility information, such as accessibility content. This option does not enable accessibility services or change node behavior.<br> Disabling this option does not remove fields included in the default simplified result. Advanced property collection does not implicitly enable this option or collect fields reserved for this option. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetcollectvisualproperties) | - | Sets whether advanced visual properties are collected.<br> Collection is disabled by default. When enabled, the result additionally includes supported properties describing directly perceivable appearance, such as visual styles and displayed states.<br> Properties already included in the default simplified result are not duplicated. Fields reserved for interaction or accessibility collection are excluded from this property group, regardless of those options. Internal diagnostic properties are never included.<br> This option is independent of advanced functional property collection and does not change which nodes are retained in the tree. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetcollectfunctionalproperties) | - | Sets whether advanced functional properties are collected.<br> Collection is disabled by default. When enabled, the result additionally includes supported properties describing developer-configured component behavior and functional capabilities.<br> Properties already included in the default simplified result are not duplicated. Fields reserved for interaction or accessibility collection are excluded from this property group, regardless of those options. Internal diagnostic properties are never included.<br> This option is independent of advanced visual property collection and does not change which nodes are retained in the tree. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJson(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIJsonWrapper **json)](#oh_arkui_nativemodule_uiagentgettreejson) | - | Collects a UI tree synchronously and returns it as JSON.<br> This function must be called on the UI thread. The result contains at most 5000 nodes and must not exceed 5 MiB. The size limit is measured using canonical compact JSON. If pretty output itself exceeds 5 MiB, the request also fails. No partial JSON is returned. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIAgentJsonCallback callback, void *userData, uint64_t *requestId)](#oh_arkui_nativemodule_uiagentgettreejsonasync) | - | Initiate an asynchronous UI tree collection request. Receive the collection through asynchronous callback. This function must be called on the UI thread. function copies the request and format before returning, so The caller can destroy or reuse the request immediately after the call. Each accepted request is completed only once On the UI thread. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetPageText(ArkUI_ContextHandle uiContext, OH_ArkUI_NativeModule_UIJsonWrapper** pageText)](#oh_arkui_nativemodule_uiagentgetpagetext) | - | Synchronously collects the text on the current ArkUI page and outputs the text in JSON format. Each JSON item contains an integer "id". Recognize the control, the rectangular "rect" relative to the target window, and the text content The string "content". After using the result, use OH_ArkUI_NativeModule_UIJsonWrapperDestroy to free up the result memory. The function must be called on the UI thread. The output format is as follows: |
| [typedef void (\*OH_ArkUI_NativeModule_UIContentChangeEventCallback)(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData)](#oh_arkui_nativemodule_uicontentchangeeventcallback) | OH_ArkUI_NativeModule_UIContentChangeEventCallback | Defines the callback invoked for a registered ArkUI state change event.<br> The callback runs on the user interface thread associated with the registered context. The event snapshot is immutable and valid only until this callback returns. ArkUI borrows but does not access or release userData. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_RegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, bool withStart, uint32_t eventMask, uint32_t ignoreMask, void* userData, OH_ArkUI_NativeModule_UIContentChangeEventCallback callback, uint64_t* subscriptionId)](#oh_arkui_nativemodule_registeruicontentchangeevent) | - | Registers to the selected ArkUI state change event categories for a user interface context.<br> Each successful call creates an independent subscription. The returned ID is nonzero and unique within the context. The callback is invoked synchronously on the context's user interface thread. ArkUI borrows uiContext and userData and does not release either value. If the operation fails, subscriptionId is not modified. This function must be called on the UI thread; calling it from a non-UI thread will abort the process. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, uint64_t subscriptionId)](#oh_arkui_nativemodule_unregisteruicontentchangeevent) | - | Unregisters an active ArkUI state change event subscription from a user interface context.<br> After this function returns successfully, no later event invokes the removed subscription. The caller can then release its userData. Unsubscribing from a callback does not change the callback batch currently being dispatched. This function must be called on the UI thread; calling it from a non-UI thread will abort the process. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetType(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, OH_ArkUI_NativeModule_UIContentChangeEventType* type)](#oh_arkui_nativemodule_uicontentchangeeventgettype) | - | Obtains the event type from an ArkUI state change event snapshot. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, uint64_t* nanoTimestamp)](#oh_arkui_nativemodule_uicontentchangeeventgettimestamp) | - | Obtains the monotonic timestamp of an ArkUI state change event snapshot.<br> The timestamp is captured at the event completion point, is expressed in nanoseconds, and is not wall-clock time. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContext(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, ArkUI_ContextHandle* uiContext)](#oh_arkui_nativemodule_uicontentchangeeventgetcontext) | - | Obtains the user interface context associated with an ArkUI state change event snapshot.<br> The returned handle is borrowed, and the caller must not release it or use it after the callback returns. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, const OH_ArkUI_NativeModule_UIJsonWrapper** json)](#oh_arkui_nativemodule_uicontentchangeeventgetcontentchangeeventjson) | - | Obtains the content change event details as a JSON wrapper from an ArkUI state change event snapshot.<br> The JSON output includes a top-level schemaVersion field, the content change type, trigger node, target node, overlay type, and an optional sub-tree dump depending on the event category:<br> Page events identify the target page. Scroll events identify the scrolling node. Overlay events identify overlay node and provide the overlay type (such as "dialog"). The trigger node is the node that initiated the content change; it is available for overlay events and general start/end scenarios, and is NULL for page and scroll events when no trigger node can be exposed. The operation succeeds when no target node can be exposed; the returned JSON still contains schemaVersion. The handles referenced in the JSON wrapper are borrowed and must not be released or used after the callback returns. |
| [typedef void (\*OH_ArkUI_NativeModule_ImageCollectionCallback)(ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData)](#oh_arkui_nativemodule_imagecollectioncallback) | OH_ArkUI_NativeModule_ImageCollectionCallback | Defines the callback used to return the result of collecting images of ArkUI nodes.<br> The framework invokes this callback exactly once on the UI thread for each accepted request. When <b>errorCode</b> is ARKUI_ERROR_CODE_NO_ERROR, the framework transfers ownership of the non-<b>NULL</b> <b>collection</b> to the caller. When <b>errorCode</b> is ARKUI_ERROR_CODE_INTERNAL_ERROR or ARKUI_ERROR_CODE_UI_CONTEXT_INVALID, <b>collection</b> is <b>NULL</b>.<br> The framework returns <b>userData</b> unchanged without dereferencing, copying, or releasing the object it points to. The caller must keep that object valid until the callback has finished using it. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetImagesByNodeIdAsync(ArkUI_ContextHandle context, const int32_t* nodeIds, uint32_t count, OH_ArkUI_NativeModule_ImageCollectionCallback callback, void* userData)](#oh_arkui_nativemodule_getimagesbynodeidasync) | - | Asynchronously collects images for specified ArkUI node IDs.<br> The framework accepts from <b>1</b> to <b>20</b> unique node IDs in one request and copies the <b>nodeIds</b> array before this function returns. If <b>count</b> is <b>0</b> or greater than <b>20</b>, this function returns ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE.<br> Each accepted node ID has one result in the collection, including a result for a node ID that cannot be found or whose image cannot be captured. An <b>Image</b> node returns its complete source <b>PixelMap</b> when available and otherwise falls back to capturing the rendered content within the node bounds. A non-<b>Image</b> node uses the same node-bounds capture behavior. A node does not need to be visible.<br> If the ArkUI node corresponding to a requested node ID cannot be found, the corresponding collection item reports <b>ARKUI_ERROR_CODE_NODE_NOT_FOUND</b>; the caller should check the node ID. A capture timeout reports <b>ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT</b>; the caller can retry the request. Another internal capture failure reports <b>ARKUI_ERROR_CODE_INTERNAL_ERROR</b> for that item; the caller can retry the request after handling the failure. An item failure does not change the overall successful request result.<br> The caller can call this function from any thread. For each accepted request, the framework invokes <b>callback</b> exactly once on the UI thread associated with <b>context</b>. If the previous request has not finished, this function returns ARKUI_ERROR_CODE_COMMAND_UNFINISHED. The caller must wait for that request to complete before submitting another request. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId(OH_ArkUI_NativeModule_ImageCollection* collection, int32_t nodeId, OH_PixelmapNative** outPixelmap, ArkUI_ErrorCode* outItemError)](#oh_arkui_nativemodule_imagecollectiontakeitembynodeid) | - | Consumes the result for a specified node ID.<br> For a successful image result, this function transfers ownership of the <b>PixelMap</b> to the caller. The caller must release it by calling <b>OH_PixelmapNative_Destroy</b>. This function also consumes a failed image result. In that case, it sets <b>*outPixelmap</b> to <b>NULL</b> and writes the item error to <b>*outItemError</b>. Each node ID in a collection can be consumed only once.<br> Destroying the collection releases only <b>PixelMap</b> instances that the caller has not taken and does not invalidate a transferred <b>PixelMap</b>.<br> The caller must not call this function concurrently with another collection API for the same collection. |
| [void OH_ArkUI_NativeModule_ImageCollectionDestroy(OH_ArkUI_NativeModule_ImageCollection* collection)](#oh_arkui_nativemodule_imagecollectiondestroy) | - | Destroys an image collection and releases <b>PixelMap</b> instances that have not been consumed.<br> The caller must destroy every non-<b>NULL</b> collection returned through the callback, even after all its items have been consumed. This function does not release or invalidate <b>PixelMap</b> instances that the caller obtained through <b>OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId</b>.<br> The caller must not call this function concurrently with another collection API for the same collection. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback)( const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData) | Callback type for receiving a sensed interaction event.<br> The callback carries a borrowed [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) object that holds the event payload. The object is valid only within the callback invocation; the callback must not retain or destroy it. All positional coordinates in the payload are relative to the screen (display), in physical pixels (px). The payload always includes a top-level schemaVersion field. Its top-level structure is { "schemaVersion": 1, "type": "<event type>", ... }.<br> The event-specific fields are listed below. - Tap or click: id, point, count, fingers. - Long press: id, point, actualDuration (milliseconds), action ("end"). - Pan: id, point, direction, action ("start" \| "end" \| "cancel"). - Pinch: id, point (array of [x, y]), fingers, action ("start" \| "end" \| "cancel"); scale is present only on "end". - Rotation: id, point (array of [x, y]), fingers, action ("start" \| "end" \| "cancel"); angle (degrees) is present only on "end". - Swipe: id, downPoint (array of [x, y]), upPoint (array of [x, y]), direction, speed, actualSpeed. - Drag: action ("start" \| "end"); "start" carries id, point, hostName, actualDuration; "end" carries point, dropResult ("success" \| "fail"), id (target, present only on success), hostName. - Touch: action ("down" \| "up"), fingerId, point; "down" also carries id (hit node ID).<br>**Since**: 26.2.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| void (*OH_ArkUI_NativeModule_UIAgentJsonCallback)(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData) | Defines the callback invoked after an asynchronous JSON tree request completes.<br> The callback is invoked exactly once on the UI thread for each accepted request. The callback receives ownership of a non-NULL JSON object only when errorCode is ARKUI_ERROR_CODE_NO_ERROR. The caller must release the object by calling OH_ArkUI_NativeModule_UIJsonWrapperDestroy.<br>**Since**: 26.2.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| void (*OH_ArkUI_NativeModule_UIContentChangeEventCallback)( const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData) | Defines the callback invoked for a registered ArkUI state change event.<br> The callback runs on the user interface thread associated with the registered context. The event snapshot is immutable and valid only until this callback returns. ArkUI borrows but does not access or release userData.<br>**Since**: 26.2.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| void (*OH_ArkUI_NativeModule_ImageCollectionCallback)(ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData) | Defines the callback used to return the result of collecting images of ArkUI nodes.<br> The framework invokes this callback exactly once on the UI thread for each accepted request. When <b>errorCode</b> is ARKUI_ERROR_CODE_NO_ERROR, the framework transfers ownership of the non-<b>NULL</b> <b>collection</b> to the caller. When <b>errorCode</b> is ARKUI_ERROR_CODE_INTERNAL_ERROR or ARKUI_ERROR_CODE_UI_CONTEXT_INVALID, <b>collection</b> is <b>NULL</b>.<br> The framework returns <b>userData</b> unchanged without dereferencing, copying, or releasing the object it points to. The caller must keep that object valid until the callback has finished using it.<br>**Since**: 26.2.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

## Enum type description

### OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType

```c
enum OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType
```

**Description**

Enumerates the observable UI interaction event types.<br> The values are bit flags. They are used to build the eventMask passed to [OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_NONE = 0 | No event.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TAP = 1 << 0 | Tap gesture.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_CLICK = 1 << 1 | Click.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_LONG_PRESS = 1 << 2 | Long press gesture.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PAN = 1 << 3 | Pan gesture.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PINCH = 1 << 4 | Pinch gesture.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_ROTATION = 1 << 5 | Rotation gesture.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_SWIPE = 1 << 6 | Swipe gesture.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_DRAG = 1 << 7 | Unified drag and drop.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TOUCH = 1 << 8 | Raw touch down or up.<br>**Since**: 26.2.0 |

### OH_ArkUI_NativeModule_UIAgentTreeType

```c
enum OH_ArkUI_NativeModule_UIAgentTreeType
```

**Description**

Enumeration of the collection type of the UI tree.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_AGENT_TREE_FULL = 0 | Collects the full UI tree, including invisible, transparent, off-screen, and blocked nodes.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVE_MODULE_UI_AGENT_TREE_VISIBLE = 1 | Collects the visible tree after visibility, clipping, off-screen, and occlusion filtering.<br>**Since**: 26.2.0 |

### OH_ArkUI_NativeModule_UIContentChangeEventCategory

```c
enum OH_ArkUI_NativeModule_UIContentChangeEventCategory
```

**Description**

UI Content Change Event Type Enumeration

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_PAGE = 1U << 0 | Page switch events, including Navigation, Router, Swiper, and Tabs switchover events.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_SCROLL = 1U << 1 | Scroll events.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_OVERLAY = 1U << 2 | Overlay events, such as events for modals, menus, or popups.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_ALL = ~0U | All supported event categories.<br>**Since**: 26.2.0 |

### OH_ArkUI_NativeModule_UIContentChangeIgnoreType

```c
enum OH_ArkUI_NativeModule_UIContentChangeIgnoreType
```

**Description**

UI Content Change Event Ignore Enumeration

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLBY = 1U << 0 | Scroll by events.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLTO = 1U << 1 | Scroll to events.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_TOAST = 1U << 2 | Toast events.<br>**Since**: 26.2.0 |

### OH_ArkUI_NativeModule_UIContentChangeEventType

```c
enum OH_ArkUI_NativeModule_UIContentChangeEventType
```

**Description**

Enumerates ArkUI state change event types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_START = 0 | Start of page change.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_END = 1 | End of page change<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_START = 2 | Start of scrolling events<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_END = 3 | A scroll interaction and any following inertial scrolling have ended.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_SHOW = 4 | An overlay has finished appearing.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_HIDE = 5 | An overlay has finished disappearing.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_START = 6 | A Swiper transition has started.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_END = 7 | A Swiper transition has completed, including its transition animation, if any.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_CANCEL = 8 | The Swiper transition is interrupted, and Swiper springs back to the starting index.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_START = 9 | Tabs Start Event<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_END = 10 | Tabs End Event<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_CANCEL = 11 | Cancel the event after the Tabs switch starts. Rebound to the index after the start<br>**Since**: 26.2.0 |


## Function description

### OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback)(const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)
```

**Description**

Callback type for receiving a sensed interaction event.<br> The callback carries a borrowed [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) object that holds the event payload. The object is valid only within the callback invocation; the callback must not retain or destroy it. All positional coordinates in the payload are relative to the screen (display), in physical pixels (px). The payload always includes a top-level schemaVersion field. Its top-level structure is { "schemaVersion": 1, "type": "<event type>", ... }.<br> The event-specific fields are listed below. - Tap or click: id, point, count, fingers. - Long press: id, point, actualDuration (milliseconds), action ("end"). - Pan: id, point, direction, action ("start" \| "end" \| "cancel"). - Pinch: id, point (array of [x, y]), fingers, action ("start" \| "end" \| "cancel"); scale is present only on "end". - Rotation: id, point (array of [x, y]), fingers, action ("start" \| "end" \| "cancel"); angle (degrees) is present only on "end". - Swipe: id, downPoint (array of [x, y]), upPoint (array of [x, y]), direction, speed, actualSpeed. - Drag: action ("start" \| "end"); "start" carries id, point, hostName, actualDuration; "end" carries point, dropResult ("success" \| "fail"), id (target, present only on success), hostName. - Touch: action ("down" \| "up"), fingerId, point; "down" also carries id (hit node ID).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [in] Borrowed JSON object. Valid only during the callback invocation. |
| void *userData | [in] Custom user data passed during registration. It can be NULL. The framework does not own, dereference, or free it. |

### OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver(ArkUI_ContextHandle uiContext, uint32_t eventMask, uint32_t *registerID, OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback callback, void *userData)
```

**Description**

Registers an observer for UI interaction events.<br> The observer receives callbacks only for the event types included in eventMask. Multiple observers can be registered for the same UI instance. Registering the same callback and userData pair again creates an additional independent observer with a new registration ID.<br> Remember to unregister the callback by [OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver) when it's not used anymore.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] Pointer to a UI instance. It must not be NULL. |
| uint32_t eventMask | [in] Bitmask of [OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollection_interactioneventtype) values to observe, combined with the bitwise OR operator. The supported bits are OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TAP through OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TOUCH. Bits outside this range are ignored. If no supported bit is set, ARKUI_ERROR_CODE_PARAM_INVALID is returned. |
| uint32_t *registerID | [out] Receives the observer registration ID on success. It must not be NULL, requires no initialization, and on failure is set to 0. |
| [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback) callback | [in] Callback invoked when a matching event occurs. It must not be NULL. |
| void *userData | [in] Custom user data passed to the callback. It can be NULL. The framework does not take ownership of it; the caller must keep it valid until the observer is unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a required pointer is NULL or eventMask contains no supported bit.</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if the UI context is invalid.</li> </ul> |

### OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver(uint32_t registerID)
```

**Description**

Unregisters an interaction observer.<br> After this call completes, the associated callback is no longer invoked.<br> This function is thread-safe, can be called from any thread, does not block the caller, and is not async-signal-safe.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t registerID | [in] Registration ID returned by a successful registration. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if the registration ID is invalid.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentJsonCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIAgentJsonCallback)(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)
```

**Description**

Defines the callback invoked after an asynchronous JSON tree request completes.<br> The callback is invoked exactly once on the UI thread for each accepted request. The callback receives ownership of a non-NULL JSON object only when errorCode is ARKUI_ERROR_CODE_NO_ERROR. The caller must release the object by calling OH_ArkUI_NativeModule_UIJsonWrapperDestroy.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Resource release**: ui_json_wrapper/OH_ArkUI_NativeModule_UIJsonWrapperDestroy {json}.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | [in] The UI context used to start the request. |
| uint64_t requestId | [in] The identifier assigned to the accepted request. |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) errorCode | [in] The request result. |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [in] Immutable JSON result. If the request fails, the value is NULL. Otherwise, the control tree is in the JSON structure, which includes a top-level schemaVersion field. This object needs to be released by the developer after being used. |
| void *userData | [in] The caller-provided data passed to OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync. NULL is allowed and indicates that no custom context was provided. The pointer is passed through unchanged. The framework does not dereference or free the pointed-to data. The data remains owned by the caller and must remain valid until this callback returns. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestCreate()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestCreate(OH_ArkUI_NativeModule_UIAgentTreeType treeType, OH_ArkUI_NativeModule_UIAgentTreeRequest **request)
```

**Description**

Create a UI tree collection request.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Resource release**: OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy {request}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreetype) treeType | [in] The tree type. The value must be a member of OH_ArkUI_NativeModule_UIAgentTreeType. |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) **request | [out] The output request object. The caller must release it by calling OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the request is created successfully.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if an input or output parameter is invalid.</li> <li>ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED if allocation fails.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy()

```c
void OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy(OH_ArkUI_NativeModule_UIAgentTreeRequest *request)
```

**Description**

Destroys the UI tree collection request object.<br> Passing NULL has no effect.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] The request to destroy. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether pure layout nodes are filtered from the returned tree.<br> Filtering is disabled by default. When enabled, retained descendants of a filtered node are attached to the nearest retained ancestor while preserving their relative order.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] The request to configure. |
| bool enabled | [in] Whether pure layout nodes are filtered. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li> ARKUI_ERROR_CODE_NO_ERROR if the option is set successfully.</li> <li> ARKUI_ERROR_CODE_PARAM_INVALID if the request is NULL.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether fully occluded nodes are filtered from the returned tree.<br> Filtering is disabled by default and can be enabled only for visible-tree requests. Enabling occlusion filtering may add substantial computational overhead to collection. Use this option judiciously based on the complexity of the UI. Disabling this option does not disable visibility, clipping, off-screen, or fully transparent node filtering.<br> The occluder opacity threshold is configured separately by [OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold). Changing this option does not change that threshold.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] The request to configure. It must not be NULL. |
| bool enabled | [in] true to enable occlusion filtering; false to disable it. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the option is set successfully. Setting false for a full-tree request also succeeds.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if request is NULL.</li> <li>ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED if enabled is true for a full-tree request. The request remains unchanged. Use a visible-tree request to enable this option.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, float threshold)
```

**Description**

Sets the minimum final opacity for a node to participate as an occluder.<br> The default value is 1.0. The option is supported only for visible-tree requests. A target node is removed only when the union of qualifying occluder regions fully covers its effective visible region.<br> This threshold will not work if the filter option is not enabled by [OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] UI tree collection request. |
| float threshold | [in] The opacity threshold in the range [0.0, 1.0]. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the threshold is set successfully.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if the request is NULL.</li> <li>ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE if the threshold is outside the valid range.</li> <li>ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED if the request is for a full tree.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether additional interaction information is collected.<br> Collection is disabled by default. When enabled, the result includes supported interaction information, such as whether a node is clickable, focusable, or editable. This option does not register event observers or change the interaction behavior of any node.<br> Disabling this option does not remove fields included in the default simplified result. Advanced property collection does not implicitly enable this option or collect fields reserved for this option.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] The request to configure. It must not be NULL. |
| bool enabled | [in] true to collect interaction information; false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the option is set successfully.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if request is NULL.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether additional accessibility information is collected.<br> Collection is disabled by default. When enabled, the result includes supported accessibility information, such as accessibility content. This option does not enable accessibility services or change node behavior.<br> Disabling this option does not remove fields included in the default simplified result. Advanced property collection does not implicitly enable this option or collect fields reserved for this option.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] The request to configure. It must not be NULL. |
| bool enabled | [in] true to collect accessibility information; false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the option is set successfully.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if request is NULL.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether advanced visual properties are collected.<br> Collection is disabled by default. When enabled, the result additionally includes supported properties describing directly perceivable appearance, such as visual styles and displayed states.<br> Properties already included in the default simplified result are not duplicated. Fields reserved for interaction or accessibility collection are excluded from this property group, regardless of those options. Internal diagnostic properties are never included.<br> This option is independent of advanced functional property collection and does not change which nodes are retained in the tree.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] The request to configure. It must not be NULL. |
| bool enabled | [in] true to collect advanced visual properties; false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the option is set successfully.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if request is NULL.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether advanced functional properties are collected.<br> Collection is disabled by default. When enabled, the result additionally includes supported properties describing developer-configured component behavior and functional capabilities.<br> Properties already included in the default simplified result are not duplicated. Fields reserved for interaction or accessibility collection are excluded from this property group, regardless of those options. Internal diagnostic properties are never included.<br> This option is independent of advanced visual property collection and does not change which nodes are retained in the tree.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] The request to configure. It must not be NULL. |
| bool enabled | [in] true to collect advanced functional properties; false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the option is set successfully.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if request is NULL.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentGetTreeJson()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJson(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIJsonWrapper **json)
```

**Description**

Collects a UI tree synchronously and returns it as JSON.<br> This function must be called on the UI thread. The result contains at most 5000 nodes and must not exceed 5 MiB. The size limit is measured using canonical compact JSON. If pretty output itself exceeds 5 MiB, the request also fails. No partial JSON is returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Resource release**: ui_json_wrapper/OH_ArkUI_NativeModule_UIJsonWrapperDestroy {json}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | [in] The UI context whose tree is collected. |
| [const OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] The collection request. |
| [OH_ArkUI_NativeModule_UIJsonFormat](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonformat) format | [in] The JSON output format. |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) **json | [out] Receives the immutable JSON result object. The pointer must not be NULL and must point to writable storage valid for the duration of the call. The caller does not need to initialize *json. On success, *json is non-NULL and the result includes a top-level schemaVersion field. The caller owns the result and must release it with [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy). On any failure, *json is set to NULL if json points to valid writable storage; no result needs to be released. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if collection succeeds.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter or format is invalid.</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if the context is invalid.</li> <li>ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD if called outside the UI thread.</li> <li>ARKUI_ERROR_CODE_RESULT_TOO_LARGE if a result limit is exceeded.</li> <li>ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED if allocation fails.</li> <li>ARKUI_ERROR_CODE_INTERNAL_ERROR if another internal failure occurs.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIAgentJsonCallback callback, void *userData, uint64_t *requestId)
```

**Description**

Initiate an asynchronous UI tree collection request. Receive the collection through asynchronous callback. This function must be called on the UI thread. function copies the request and format before returning, so The caller can destroy or reuse the request immediately after the call. Each accepted request is completed only once On the UI thread.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | [in] The UI context whose tree is collected. |
| [const OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [in] The collection request. |
| [OH_ArkUI_NativeModule_UIJsonFormat](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonformat) format | [in] The JSON output format. |
| [OH_ArkUI_NativeModule_UIAgentJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentjsoncallback) callback | [in] The completion callback. On success, the callback receives ownership of the JSON object and must release it by calling OH_ArkUI_NativeModule_UIJsonWrapperDestroy. The JSON object includes a top-level schemaVersion field. |
| void *userData | [in] The caller-provided data passed to the callback. NULL is allowed and indicates no custom context. The framework retains only the pointer value until completion and passes it through unchanged; it does not copy, dereference, or free the pointed-to data. The caller owns the data and must keep it valid until the completion callback returns. If the request is rejected synchronously, it is not retained. |
| uint64_t *requestId | [out] The output identifier for the accepted request. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the request is accepted.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter or format is invalid.</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if the context is invalid.</li> <li>ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD if called outside the UI thread.</li> <li>ARKUI_ERROR_CODE_COMMAND_UNFINISHED if last request unfinished.</li> </ul> |

### OH_ArkUI_NativeModule_UIAgentGetPageText()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetPageText(ArkUI_ContextHandle uiContext, OH_ArkUI_NativeModule_UIJsonWrapper** pageText)
```

**Description**

Synchronously collects the text on the current ArkUI page and outputs the text in JSON format. Each JSON item contains an integer "id". Recognize the control, the rectangular "rect" relative to the target window, and the text content The string "content". After using the result, use OH_ArkUI_NativeModule_UIJsonWrapperDestroy to free up the result memory. The function must be called on the UI thread. The output format is as follows:

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Resource release**: ui_json_wrapper/OH_ArkUI_NativeModule_UIJsonWrapperDestroy {pageText}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] Context of the target UI instance for text collection |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)** pageText | [out] output slot, initialized to NULL by the caller. On success, the caller owns the returned object and must release it with [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) when it is no longer needed. A valid slot is set to NULL on failure. On success, the returned JSON object includes a top-level schemaVersion field, even when the page is empty. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR on success.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if pageText is NULL.</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if uiContext is NULL or no longer valid.</li> <li>ARKUI_ERROR_CODE_CAPI_INIT_ERROR if the native implementation is unavailable.</li> <li>ARKUI_ERROR_CODE_INTERNAL_ERROR if no current page exists, the JSON payload cannot be represented by uint32_t size, or collection/serialization fails.</li> </ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIContentChangeEventCallback)(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData)
```

**Description**

Defines the callback invoked for a registered ArkUI state change event.<br> The callback runs on the user interface thread associated with the registered context. The event snapshot is immutable and valid only until this callback returns. ArkUI borrows but does not access or release userData.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] Pointer to the immutable event snapshot. |
| void* userData | [in] Pointer supplied when the callback was registered. The pointer can be NULL. |

### OH_ArkUI_NativeModule_RegisterUIContentChangeEvent()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_RegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, bool withStart, uint32_t eventMask, uint32_t ignoreMask, void* userData, OH_ArkUI_NativeModule_UIContentChangeEventCallback callback, uint64_t* subscriptionId)
```

**Description**

Registers to the selected ArkUI state change event categories for a user interface context.<br> Each successful call creates an independent subscription. The returned ID is nonzero and unique within the context. The callback is invoked synchronously on the context's user interface thread. ArkUI borrows uiContext and userData and does not release either value. If the operation fails, subscriptionId is not modified. This function must be called on the UI thread; calling it from a non-UI thread will abort the process.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] User interface context to observe. The handle must remain valid for the subscription. |
| bool withStart | [in] Whether to report start events. When set to true, start events (such as page change start and scroll start) are reported; when set to false, only end events are reported. |
| uint32_t eventMask | [in] Bitwise OR combination of [OH_ArkUI_NativeModule_UIContentChangeEventCategory](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcategory) values. Must not be zero. The [OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_SCROLL](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcategory) category does not differentiate between scroll sub-types. Set the corresponding [OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLTO](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype) or [OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLBY](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype) bit in ignoreMask to ignore those events. |
| uint32_t ignoreMask | [in] Bitwise OR combination of [OH_ArkUI_NativeModule_UIContentChangeIgnoreType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype) values. |
| void* userData | [in] User-defined data passed to the callback. The pointer can be NULL and owned by the caller. |
| [OH_ArkUI_NativeModule_UIContentChangeEventCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcallback) callback | [in] Callback invoked for matching events. The callback must not be NULL. |
| uint64_t* subscriptionId | [out] Pointer to the nonzero subscription ID written when the operation succeeds. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if uiContext is NULL or no longer active.</li> <li>ARKUI_ERROR_CODE_CALLBACK_INVALID if callback is NULL.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if eventMask or subscriptionId is invalid.</li> <li>ARKUI_ERROR_CODE_CAPI_INIT_ERROR if the native module is not initialized.</li></ul> |

### OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, uint64_t subscriptionId)
```

**Description**

Unregisters an active ArkUI state change event subscription from a user interface context.<br> After this function returns successfully, no later event invokes the removed subscription. The caller can then release its userData. Unsubscribing from a callback does not change the callback batch currently being dispatched. This function must be called on the UI thread; calling it from a non-UI thread will abort the process.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] User interface context that owns the subscription. |
| uint64_t subscriptionId | [in] Nonzero ID of an active subscription owned by uiContext. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID if uiContext is NULL or no longer active.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if subscriptionId is zero, unknown, already removed.</li> <li>ARKUI_ERROR_CODE_CAPI_INIT_ERROR if the native C API is not initialized.</li> </ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventGetType()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetType(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, OH_ArkUI_NativeModule_UIContentChangeEventType* type)
```

**Description**

Obtains the event type from an ArkUI state change event snapshot.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] Pointer to the event snapshot. The pointer is valid only while the callback is running. |
| [OH_ArkUI_NativeModule_UIContentChangeEventType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventtype)* type | [out] Pointer to the event type written when the operation succeeds. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if event or type is NULL.</li></ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, uint64_t* nanoTimestamp)
```

**Description**

Obtains the monotonic timestamp of an ArkUI state change event snapshot.<br> The timestamp is captured at the event completion point, is expressed in nanoseconds, and is not wall-clock time.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] Pointer to the event snapshot. The pointer is valid only while the callback is running. |
| uint64_t* nanoTimestamp | [out] Pointer to the monotonic timestamp in nanoseconds written when the operation succeeds. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if event or nanoTimestamp is NULL.</li></ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventGetContext()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContext(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, ArkUI_ContextHandle* uiContext)
```

**Description**

Obtains the user interface context associated with an ArkUI state change event snapshot.<br> The returned handle is borrowed, and the caller must not release it or use it after the callback returns.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] Pointer to the event snapshot. The pointer is valid only while the callback is running. |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md)* uiContext | [out] Pointer to the borrowed user interface context handle written when the operation succeeds. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if event or uiContext is NULL.</li></ul> |

### OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, const OH_ArkUI_NativeModule_UIJsonWrapper** json)
```

**Description**

Obtains the content change event details as a JSON wrapper from an ArkUI state change event snapshot.<br> The JSON output includes a top-level schemaVersion field, the content change type, trigger node, target node, overlay type, and an optional sub-tree dump depending on the event category:<br> Page events identify the target page. Scroll events identify the scrolling node. Overlay events identify overlay node and provide the overlay type (such as "dialog"). The trigger node is the node that initiated the content change; it is available for overlay events and general start/end scenarios, and is NULL for page and scroll events when no trigger node can be exposed. The operation succeeds when no target node can be exposed; the returned JSON still contains schemaVersion. The handles referenced in the JSON wrapper are borrowed and must not be released or used after the callback returns.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [in] Pointer to the event snapshot. The pointer is valid only while the callback is running. |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)** json | [out] Pointer to the [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) that receives the content change event details. The caller must not release the wrapper or use it after the callback returns. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if event or json is NULL.</li></ul> |

### OH_ArkUI_NativeModule_ImageCollectionCallback()

```c
typedef void (*OH_ArkUI_NativeModule_ImageCollectionCallback)(ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData)
```

**Description**

Defines the callback used to return the result of collecting images of ArkUI nodes.<br> The framework invokes this callback exactly once on the UI thread for each accepted request. When <b>errorCode</b> is ARKUI_ERROR_CODE_NO_ERROR, the framework transfers ownership of the non-<b>NULL</b> <b>collection</b> to the caller. When <b>errorCode</b> is ARKUI_ERROR_CODE_INTERNAL_ERROR or ARKUI_ERROR_CODE_UI_CONTEXT_INVALID, <b>collection</b> is <b>NULL</b>.<br> The framework returns <b>userData</b> unchanged without dereferencing, copying, or releasing the object it points to. The caller must keep that object valid until the callback has finished using it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Resource release**: OH_ArkUI_NativeModule_ImageCollectionDestroy {collection}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) errorCode | [in] Indicates the overall request result. <ul<li>>ARKUI_ERROR_CODE_NO_ERROR indicates successful collection.</li> <li>ARKUI_ERROR_CODE_INTERNAL_ERROR indicates an internal collection failure.</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID context became invalid after the request was accepted.</li></ul> |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)* collection | [in] Indicates the result collection. The value is non-<b>NULL</b> for overall success and <b>NULL</b> for an overall error. |
| void* userData | [in] Indicates the caller-defined context pointer. The value can be <b>NULL</b>. |

### OH_ArkUI_NativeModule_GetImagesByNodeIdAsync()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetImagesByNodeIdAsync(ArkUI_ContextHandle context, const int32_t* nodeIds, uint32_t count, OH_ArkUI_NativeModule_ImageCollectionCallback callback, void* userData)
```

**Description**

Asynchronously collects images for specified ArkUI node IDs.<br> The framework accepts from <b>1</b> to <b>20</b> unique node IDs in one request and copies the <b>nodeIds</b> array before this function returns. If <b>count</b> is <b>0</b> or greater than <b>20</b>, this function returns ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE.<br> Each accepted node ID has one result in the collection, including a result for a node ID that cannot be found or whose image cannot be captured. An <b>Image</b> node returns its complete source <b>PixelMap</b> when available and otherwise falls back to capturing the rendered content within the node bounds. A non-<b>Image</b> node uses the same node-bounds capture behavior. A node does not need to be visible.<br> If the ArkUI node corresponding to a requested node ID cannot be found, the corresponding collection item reports <b>ARKUI_ERROR_CODE_NODE_NOT_FOUND</b>; the caller should check the node ID. A capture timeout reports <b>ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT</b>; the caller can retry the request. Another internal capture failure reports <b>ARKUI_ERROR_CODE_INTERNAL_ERROR</b> for that item; the caller can retry the request after handling the failure. An item failure does not change the overall successful request result.<br> The caller can call this function from any thread. For each accepted request, the framework invokes <b>callback</b> exactly once on the UI thread associated with <b>context</b>. If the previous request has not finished, this function returns ARKUI_ERROR_CODE_COMMAND_UNFINISHED. The caller must wait for that request to complete before submitting another request.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) context | [in] Indicates the ArkUI context used to process the request. The parameter must not be <b>NULL</b>. |
| const int32_t* nodeIds | [in] Indicates the first element of an array containing <b>count</b> unique ArkUI node IDs. The parameter must not be NULL. |
| uint32_t count | [in] Indicates the number of node IDs. The valid range is (0, 20]. |
| [OH_ArkUI_NativeModule_ImageCollectionCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_imagecollectioncallback) callback | [in] Indicates the callback used to receive the result. The parameter must not be <b>NULL</b>. |
| void* userData | [in] Indicates the caller-defined context pointer passed unchanged to the callback. The value can be <b>NULL</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the framework accepts the request. </li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if context, nodeIds, or callback is NULL.</li> <li>ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE if count is 0 or greater than 20.</li> <li>ARKUI_ERROR_CODE_COMMAND_UNFINISHED if the previous request has not finished.</li></ul> |

### OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId(OH_ArkUI_NativeModule_ImageCollection* collection, int32_t nodeId, OH_PixelmapNative** outPixelmap, ArkUI_ErrorCode* outItemError)
```

**Description**

Consumes the result for a specified node ID.<br> For a successful image result, this function transfers ownership of the <b>PixelMap</b> to the caller. The caller must release it by calling <b>OH_PixelmapNative_Destroy</b>. This function also consumes a failed image result. In that case, it sets <b>*outPixelmap</b> to <b>NULL</b> and writes the item error to <b>*outItemError</b>. Each node ID in a collection can be consumed only once.<br> Destroying the collection releases only <b>PixelMap</b> instances that the caller has not taken and does not invalidate a transferred <b>PixelMap</b>.<br> The caller must not call this function concurrently with another collection API for the same collection.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Resource release**: multimedia/image_framework/image/OH_PixelmapNative_Destroy {outPixelmap}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)* collection | [in] Indicates the image collection whose item is consumed. The parameter must not be NULL. |
| int32_t nodeId | [in] Indicates the ArkUI node ID of the item to consume. |
| [OH_PixelmapNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-pixelmapnative.md)** outPixelmap | [out] Indicates the output pointer that receives the transferred PixelMap. The parameter must not be NULL. For a failed item, the function sets outPixelmap to NULL. |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode)* outItemError | [out] Indicates the output pointer to the result code for the item. The parameter must not be NULL. The function writes ARKUI_ERROR_CODE_NO_ERROR for a successful item, ARKUI_ERROR_CODE_NODE_NOT_FOUND if the ArkUI node corresponding to the requested node ID could not be found while collecting its image, ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT for a capture timeout, or ARKUI_ERROR_CODE_INTERNAL_ERROR for another capture failure, the caller can retry the request. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if this function consumes the item, including a failed image result.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a required pointer is NULL, nodeId does not identify an item in collection, or the caller has already consumed that item. To resolve the error, provide all required pointers and use a nodeId that identifies an unconsumed item in collection.</li></ul> |

### OH_ArkUI_NativeModule_ImageCollectionDestroy()

```c
void OH_ArkUI_NativeModule_ImageCollectionDestroy(OH_ArkUI_NativeModule_ImageCollection* collection)
```

**Description**

Destroys an image collection and releases <b>PixelMap</b> instances that have not been consumed.<br> The caller must destroy every non-<b>NULL</b> collection returned through the callback, even after all its items have been consumed. This function does not release or invalidate <b>PixelMap</b> instances that the caller obtained through <b>OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId</b>.<br> The caller must not call this function concurrently with another collection API for the same collection.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)* collection | [in] Indicates the image collection to destroy. The parameter can be <b>NULL</b>. If <b>collection</b> is <b>NULL</b>, this function does nothing. |


