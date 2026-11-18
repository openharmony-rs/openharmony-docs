# ui_info_collection.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202 -->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=4b782a4c62ca52bc00a7b866ba50125e07e60908 translatedAt=2026-11-03T08:45:20.968Z pushedAt=2026-11-04T06:55:00.450Z nl=1 -->

## Overview

Declares the APIs for in-application agents and UI automation, used to listen for UI interaction events and obtain the hit nodes.<br>APIs that return a status code report errors through [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode). After the execution of an API completes, the execution result is returned asynchronously through a callback function. These APIs do not report errors through the **errno** variable. After the APIs are called, the value of this variable is unspecified and must not be used to determine whether the call succeeds.

**File to include:** <arkui/ui_info_collection.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 26.1.0

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) | OH_ArkUI_NativeModule_UIAgentTreeRequest | Declares the UI tree collection request. |
| [OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md) | OH_ArkUI_NativeModule_UIContentChangeEvent | Declares the ArkUI content change event. |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md) | OH_ArkUI_NativeModule_ImageCollection | Declares the ArkUI image collection result. |

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType](#oh_arkui_nativemodule_uiinfocollection_interactioneventtype) | OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType | Enumerates the UI interaction event types that can be listened for.<br>Each enumerated value is a bit flag, used to construct **eventMask** passed to [OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver()](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver). |
| [OH_ArkUI_NativeModule_UIAgentTreeType](#oh_arkui_nativemodule_uiagenttreetype) | OH_ArkUI_NativeModule_UIAgentTreeType | Enumerates the UI tree collection types. |
| [OH_ArkUI_NativeModule_UIContentChangeEventCategory](#oh_arkui_nativemodule_uicontentchangeeventcategory) | OH_ArkUI_NativeModule_UIContentChangeEventCategory | Enumerates the UI content change event categories. |
| [OH_ArkUI_NativeModule_UIContentChangeIgnoreType](#oh_arkui_nativemodule_uicontentchangeignoretype) | OH_ArkUI_NativeModule_UIContentChangeIgnoreType | Enumerates the UI content change event types that can be ignored. |
| [OH_ArkUI_NativeModule_UIContentChangeEventType](#oh_arkui_nativemodule_uicontentchangeeventtype) | OH_ArkUI_NativeModule_UIContentChangeEventType | Enumerates the ArkUI content change event types. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback)(const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)](#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback) | OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback | Defines the callback function for receiving perceived interaction events.<br>The callback receives event data through a borrowed [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) object and does not obtain the object's ownership. The object is valid only during the execution of this callback. The callback must not retain or destroy the object. All position coordinates in the event data are relative to the screen (display), and the unit is physical pixels (px). The top level of the event data always contains the **schemaVersion** field. The top-level structure is { "schemaVersion": 1, "type": "<event type>", ... }.<br>For the fields corresponding to each event type, see [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback()](#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver(ArkUI_ContextHandle uiContext, uint32_t eventMask, uint32_t *registerID, OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback callback, void *userData)](#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver) | - | Registers a UI interaction event observer.<br>The observer receives event callbacks only for the types specified by **eventMask**. Multiple observers can be registered for the same UI instance. Registering repeatedly with the same callback and **userData** combination creates a new independent observer and assigns a new registration ID.<br>When the observer is no longer used, [OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver()](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver) must be called to unregister the callback. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver(uint32_t registerID)](#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver) | - | Unregisters a UI interaction event observer.<br>After this call completes, the corresponding callback function is no longer invoked.<br>This API is not thread-safe and must not be called from a non-UI thread. |
| [typedef void (\*OH_ArkUI_NativeModule_UIAgentJsonCallback)(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)](#oh_arkui_nativemodule_uiagentjsoncallback) | OH_ArkUI_NativeModule_UIAgentJsonCallback | Defines the callback function called when an asynchronous JSON tree collection request completes.<br>Each accepted request triggers the callback on the UI thread and only once. Only when **errorCode** is [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) does the callback receive a non-**NULL** JSON object and obtain its ownership. The caller must call [OH_ArkUI_NativeModule_UIJsonWrapperDestroy()](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) to release the object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestCreate(OH_ArkUI_NativeModule_UIAgentTreeType treeType, OH_ArkUI_NativeModule_UIAgentTreeRequest **request)](#oh_arkui_nativemodule_uiagenttreerequestcreate) | - | Creates a UI tree collection request. |
| [void OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy(OH_ArkUI_NativeModule_UIAgentTreeRequest *request)](#oh_arkui_nativemodule_uiagenttreerequestdestroy) | - | Destroys a UI tree collection request object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetfilterpurelayoutnodes) | - | Sets whether to filter pure layout nodes from the returned UI tree.<br>Filtering is disabled by default. When enabled, descendant nodes that still need to be retained under a filtered node are attached to the nearest retained ancestor node, preserving their original relative order. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes) | - | Sets whether to filter fully occluded nodes from the returned UI tree.<br>Filtering is disabled by default, and it can be enabled only for visible tree collection requests. Enabling occlusion filtering may introduce significant additional computation to collection. Use it as appropriate based on the complexity of the UI. Disabling this option does not disable visibility filtering, clipping filtering, off-screen node filtering, or fully transparent node filtering.<br>The opacity threshold that a node acting as an occluder must meet is configured separately by [OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold()](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold). Modifying this option does not change that threshold. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, float threshold)](#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold) | - | Sets the minimum final opacity that a node must reach to participate in occlusion determination as an occluder.<br>The default value is **1.0**, and this option is supported only for visible tree collection requests. A target node is removed only when the union of the regions of the occluding nodes that meet the threshold condition completely covers the effective visible region of the target node.<br>If occlusion filtering is not enabled through [OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes()](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes), this threshold does not take effect. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetinteractioninfo) | - | Sets whether to collect additional interaction information.<br>Collection is disabled by default. When enabled, the result includes supported interaction information, such as whether a node is clickable, focusable, or editable. This option does not register an event observer and does not change the interaction behavior of any node.<br>Disabling this option does not remove fields already present in the default compact result. Advanced property collection does not implicitly enable this option, nor does it collect fields exclusive to this option. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetaccessibilityinfo) | - | Sets whether to collect additional accessibility information.<br>Collection is disabled by default. When enabled, the result includes supported accessibility information, such as accessibility content. This option does not enable accessibility services and does not change node behavior.<br>Disabling this option does not remove fields already present in the default compact result. Advanced property collection does not implicitly enable this option, nor does it collect fields exclusive to this option. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetcollectvisualproperties) | - | Sets whether to collect advanced visual properties.<br>Collection is disabled by default. When enabled, the result additionally includes supported properties that describe directly perceivable appearance, such as visual style and display state.<br>Properties already present in the default compact result are not collected again. Regardless of whether the interaction information and accessibility information collection options are enabled, the fields exclusive to these two categories do not belong to this group of properties. Internal diagnostic properties are never included.<br>This option is independent of the advanced functional property collection option and does not change the nodes retained in the UI tree. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)](#oh_arkui_nativemodule_uiagenttreerequestsetcollectfunctionalproperties) | - | Sets whether to collect advanced functional properties.<br>Collection is disabled by default. When enabled, the result additionally includes supported properties that describe the component behavior and functional capabilities you configure.<br>Properties already present in the default compact result are not collected again. Regardless of whether the interaction information and accessibility information collection options are enabled, the fields exclusive to these two categories do not belong to this group of properties. Internal diagnostic properties are never included.<br>This option is independent of the advanced visual property collection option and does not change the nodes retained in the UI tree. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJson(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIJsonWrapper **json)](#oh_arkui_nativemodule_uiagentgettreejson) | - | Synchronously collects the UI tree and returns it in JSON format.<br>This API must be called on the UI thread. The result contains at most 5,000 nodes and must not exceed 5 MiB in size. The size limit is based on the canonical compact JSON format; if the formatted output with indentation and line breaks itself exceeds 5 MiB, the request also fails. Partial JSON data is not returned. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIAgentJsonCallback callback, void *userData, uint64_t *requestId)](#oh_arkui_nativemodule_uiagentgettreejsonasync) | - | Initiates an asynchronous UI tree collection request and receives the collection result through an asynchronous callback.<br>This API must be called on the UI thread. The request and format are copied before the API returns, so the caller can destroy or reuse the request object immediately after the call returns. Each accepted request completes on the UI thread and only once. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetPageText(ArkUI_ContextHandle uiContext, OH_ArkUI_NativeModule_UIJsonWrapper** pageText)](#oh_arkui_nativemodule_uiagentgetpagetext) | - | Synchronously collects the text of the current ArkUI page and outputs it in JSON format.<br>Each JSON item contains an integer "id" used to identify the control, a rectangular region "rect" relative to the target window, and a string "content" representing the text content. After use, [OH_ArkUI_NativeModule_UIJsonWrapperDestroy()](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) must be called to release the memory occupied by the result. This API must be called on the UI thread. |
| [typedef void (\*OH_ArkUI_NativeModule_UIContentChangeEventCallback)(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData)](#oh_arkui_nativemodule_uicontentchangeeventcallback) | OH_ArkUI_NativeModule_UIContentChangeEventCallback | Defines the callback function invoked when a registered ArkUI content change event is triggered.<br>The callback is executed on the UI thread associated with the UI context specified at registration. The event snapshot is immutable and is valid only until this callback returns. ArkUI only borrows **userData**, does not obtain its ownership, and does not access or release the data it points to. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_RegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, bool withStart, uint32_t eventMask, uint32_t ignoreMask, void* userData, OH_ArkUI_NativeModule_UIContentChangeEventCallback callback, uint64_t* subscriptionId)](#oh_arkui_nativemodule_registeruicontentchangeevent) | - | Registers a subscription for ArkUI content change events of the selected categories for the specified UI context.<br>Each successful call creates an independent subscription. The returned subscription ID is non-zero and unique within that UI context. The callback is executed synchronously on the UI thread associated with that UI context. ArkUI only borrows **uiContext** and **userData** and does not release either. On failure, the value pointed to by **subscriptionId** is not modified. This API must be called on the UI thread; calling it from a non-UI thread causes process termination. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, uint64_t subscriptionId)](#oh_arkui_nativemodule_unregisteruicontentchangeevent) | - | Unregisters a still-valid ArkUI content change event subscription in the specified UI context.<br>After this API returns successfully, subsequent events no longer trigger the callback of the removed subscription, and the caller can then release its **userData**. Unsubscribing within a callback does not change the batch of callbacks currently being dispatched. This API must be called on the UI thread; calling it from a non-UI thread causes process termination. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetType(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, OH_ArkUI_NativeModule_UIContentChangeEventType* type)](#oh_arkui_nativemodule_uicontentchangeeventgettype) | - | Obtains the event type from an ArkUI content change event snapshot. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, uint64_t* nanoTimestamp)](#oh_arkui_nativemodule_uicontentchangeeventgettimestamp) | - | Obtains the monotonic timestamp of an ArkUI content change event snapshot.<br>The timestamp is recorded when the event completes, in nanoseconds, using a monotonic clock, and does not represent calendar time. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContext(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, ArkUI_ContextHandle* uiContext)](#oh_arkui_nativemodule_uicontentchangeeventgetcontext) | - | Obtains the UI context associated with an ArkUI content change event snapshot.<br>The returned handle is a borrowed handle. The caller does not own it, must not release it, and must not use it after the callback returns. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, const OH_ArkUI_NativeModule_UIJsonWrapper** json)](#oh_arkui_nativemodule_uicontentchangeeventgetcontentchangeeventjson) | - | Obtains the content change event details from an ArkUI content change event snapshot and returns them as a JSON wrapper object.<br>The top level of the JSON output contains the **schemaVersion** field, and includes the content change type, trigger node, target node, overlay type, and subtree dump information whose inclusion depends on the event category.<br>A page event identifies the target page, a scroll event identifies the node where scrolling occurs, and an overlay event identifies the overlay node and provides the overlay type, such as "dialog". The trigger node is the node that causes the content change, and is available in overlay events and general start and end scenarios. For page events and scroll events, if the trigger node cannot be provided, the node is **NULL**. If the target node cannot be provided, the operation still succeeds, and the returned JSON still contains the **schemaVersion** field. The handles referenced in the JSON wrapper object are all borrowed handles and must not be released or used after the callback returns. |
| [typedef void (\*OH_ArkUI_NativeModule_ImageCollectionCallback)(ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData)](#oh_arkui_nativemodule_imagecollectioncallback) | OH_ArkUI_NativeModule_ImageCollectionCallback | Defines the callback function used to return the ArkUI node image collection result.<br>For each accepted request, the framework invokes this callback on the UI thread and only once. Each non-**NULL** collection is transferred to the caller. A collection is returned even if some result items fail. The caller must call [OH_ArkUI_NativeModule_ImageCollectionDestroy()](#oh_arkui_nativemodule_imagecollectiondestroy) to release each non-**NULL** collection.<br>The framework passes **userData** back as is, does not dereference the pointer, and does not copy or release the object it points to. The caller must ensure that the object remains valid until the callback finishes using it. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_GetImagesByNodeIdAsync(ArkUI_ContextHandle context, const int32_t* nodeIds, uint32_t count, OH_ArkUI_NativeModule_ImageCollectionCallback callback, void* userData)](#oh_arkui_nativemodule_getimagesbynodeidasync) | - | Asynchronously collects the images corresponding to the specified ArkUI node IDs.<br>A single request can contain 1 to 20 non-duplicate node IDs. The framework copies the **nodeIds** array before this API returns. If the value of **count** is less than or equal to 0 or greater than 20, this API returns [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode).<br>Each accepted node ID has a corresponding result item in the result collection, even if the node is not found or its image cannot be captured. For an **Image** node, if its source PixelMap can be obtained, the complete source PixelMap is returned; otherwise, a snapshot of the rendered content within the node boundary is taken. For a non-**Image** node, a snapshot of the rendered content within the node boundary is also taken. The node does not need to be visible.<br>If the ArkUI node corresponding to a requested node ID is not found, the corresponding result item reports [ARKUI_ERROR_CODE_NODE_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode), and the caller should check the node ID. When the snapshot times out, the corresponding result item reports [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode), and the caller can retry the request. When a result item is consumed in the collection, the error code of that result item can be obtained. When any result item fails, the callback reports [ARKUI_ERROR_CODE_COLLECTION_PARTIAL_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode), but the collection is still returned.<br>The caller can call this API from any thread. For each accepted request, the framework invokes the callback exactly once on the UI thread associated with the context. If the previous request has not completed, this API returns [ARKUI_ERROR_CODE_COMMAND_UNFINISHED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode). The caller must wait for that request to complete before submitting the next request. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId(OH_ArkUI_NativeModule_ImageCollection* collection, int32_t nodeId, OH_PixelmapNative** outPixelmap, ArkUI_ErrorCode* outItemError)](#oh_arkui_nativemodule_imagecollectiontakeitembynodeid) | - | Takes out the result corresponding to the specified node ID.<br>For a result item whose image collection succeeds, this API transfers the ownership of the PixelMap to the caller. The caller must call [OH_PixelmapNative_Destroy()](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to release the object. This API can also take out a result item whose image collection fails, in which case **\*outPixelmap** is set to **NULL** and the error code of that result item is written to **\*outItemError**. The result corresponding to each node ID in the collection can be taken out only once.<br>When the collection is destroyed, only the PixelMap instances that the caller has not taken out are released. The PixelMap instances already transferred to the caller are not invalidated by this.<br>The caller must not call this API concurrently with other collection operation APIs on the same collection. |
| [void OH_ArkUI_NativeModule_ImageCollectionDestroy(OH_ArkUI_NativeModule_ImageCollection* collection)](#oh_arkui_nativemodule_imagecollectiondestroy) | - | Destroys the image collection and releases the PixelMap instances that have not been taken out.<br>The caller must destroy every non-**NULL** collection returned by the callback, even if all result items in it have been taken out. This API does not release the PixelMap instances obtained through [OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId()](#oh_arkui_nativemodule_imagecollectiontakeitembynodeid), nor does it invalidate these instances.<br>The caller must not call this API concurrently with other collection operation APIs on the same collection. |

### Variables

| Name | Description |
| -- | -- |
| void (*OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback)( const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData) | Defines the callback function for receiving perceived interaction events.<br>The callback receives event data through a borrowed [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) object and does not obtain the ownership of the object. The object is valid only during the execution of this callback, and the callback must not retain or destroy the object. All position coordinates in the event data are relative to the screen (display), and the unit is physical pixels (px). The top level of the event data always contains the **schemaVersion** field. The top-level structure is { "schemaVersion": 1, "type": "<event type>", ... }.<br>For the fields corresponding to each event type, see [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback()](#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback). |
| void (*OH_ArkUI_NativeModule_UIAgentJsonCallback)(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData) | Defines the callback function invoked when an asynchronous JSON tree collection request completes.<br>Each accepted request is triggered on the UI thread and only triggers the callback once. Only when **errorCode** is [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) does the callback receive a non-**NULL** JSON object and obtain its ownership. The caller must call [OH_ArkUI_NativeModule_UIJsonWrapperDestroy()](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) to release the object. |
| void (*OH_ArkUI_NativeModule_UIContentChangeEventCallback)( const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData)| Defines the callback function invoked when a registered ArkUI content change event is triggered.<br>The callback is executed on the UI thread associated with the UI context specified at registration. The event snapshot is immutable and is valid only before this callback returns. ArkUI only borrows **userData**, does not obtain its ownership, and does not access or release the data it points to. |
| void (*OH_ArkUI_NativeModule_ImageCollectionCallback)(ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData) | Defines the callback function used to return the result of ArkUI node image collection.<br>For each accepted request, the framework invokes this callback exactly once on the UI thread. Each non-**NULL** collection is transferred to the caller. Even if some result items fail, the collection is still returned. The caller must call [OH_ArkUI_NativeModule_ImageCollectionDestroy()](#oh_arkui_nativemodule_imagecollectiondestroy) to release each non-**NULL** collection.<br>The framework passes **userData** back as is, without dereferencing the pointer, and without copying or releasing the object it points to. The caller must ensure that the object remains valid until the callback finishes using it. |

## Enum Description

### OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType

```c
enum OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType
```

**Description**

Enumerates the UI interaction event types that can be listened for.<br>Each enumerated value is a bit flag, used to construct **eventMask** passed to [OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver()](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionregisterinteractionobserver).

**Since:** 26.1.0

| Value | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_NONE = 0 | No event. |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TAP = 1 << 0 | Tap gesture. |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_CLICK = 1 << 1 | Click event. |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_LONG_PRESS = 1 << 2 | Long press gesture. |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PAN = 1 << 3 | Pan gesture. |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_PINCH = 1 << 4 | Pinch gesture. |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_ROTATION = 1 << 5 | Rotation gesture. |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_SWIPE = 1 << 6 | Swipe gesture. |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_DRAG = 1 << 7 | Unified drag event. |
| OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TOUCH = 1 << 8 | Raw touch press or lift event. |

### OH_ArkUI_NativeModule_UIAgentTreeType

```c
enum OH_ArkUI_NativeModule_UIAgentTreeType
```

**Description**

Enumerates the UI tree collection types.

**Since:** 26.1.0

| Value | Description |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_AGENT_TREE_FULL = 0 | Collects the complete UI tree, including invisible, transparent, off-screen, and occluded nodes. |
| OH_ARKUI_NATIVE_MODULE_UI_AGENT_TREE_VISIBLE = 1 | Collects the visible UI tree after visibility, clipping, off-screen, and occlusion filtering. |

### OH_ArkUI_NativeModule_UIContentChangeEventCategory

```c
enum OH_ArkUI_NativeModule_UIContentChangeEventCategory
```

**Description**

Enumerates the UI content change event categories.

**Since:** 26.1.0

| Value | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_PAGE = 1U << 0 | Page switch event, including the switch events of **Navigation**, **Router**, **Swiper**, and **Tabs**. |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_SCROLL = 1U << 1 | Scroll event. |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_OVERLAY = 1U << 2 | Overlay event, for example, a modal, menu, or popup event. |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_ALL = ~0U | All supported event categories. |

### OH_ArkUI_NativeModule_UIContentChangeIgnoreType

```c
enum OH_ArkUI_NativeModule_UIContentChangeIgnoreType
```

**Description**

Enumerates the UI content change event types that can be ignored.

**Since:** 26.1.0

| Value | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLBY = 1U << 0 | Event of scrolling by a specified offset ([scrollBy](arkui-ts/ts-container-scroll.md#scrollby9)). |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLTO = 1U << 1 | Event of scrolling to a specified position ([scrollTo](arkui-ts/ts-container-scroll.md#scrollto)). |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_TOAST = 1U << 2 | Toast event. |

### OH_ArkUI_NativeModule_UIContentChangeEventType

```c
enum OH_ArkUI_NativeModule_UIContentChangeEventType
```

**Description**

Enumerates the ArkUI content change event types.

**Since:** 26.1.0

| Value | Description |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_START = 0 | Page switch starts. |
| OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_END = 1 | Page switch ends. |
| OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_START = 2 | Scrolling starts. |
| OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_END = 3 | The scroll interaction and its subsequent inertial scrolling have both ended. |
| OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_SHOW = 4 | The overlay is shown. |
| OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_HIDE = 5 | The overlay is hidden. |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_START = 6 | Swiper switch starts. |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_END = 7 | Swiper switch is complete; if a transition animation exists, the animation is also complete. |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_CANCEL = 8 | Swiper switch is interrupted and bounces back to the start index. |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_START = 9 | Tabs switch starts. |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_END = 10 | Tabs switch ends. |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_CANCEL = 11 | Tabs switch is canceled after it starts and bounces back to the index at the start of the switch. |


## Function Description

### OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback)(const OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)
```

**Description**

Defines the callback function for receiving perceived interaction events.

The callback receives event data through a borrowed [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) object and does not obtain the ownership of the object. The object is valid only during the execution of this callback, and the callback must not retain or destroy the object. All position coordinates in the event data are relative to the screen (display), and the unit is physical pixels (px). The top level of the event data always contains the **schemaVersion** field. The top-level structure is { "schemaVersion": 1, "type": "<event type>", ... }.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [Input parameter] Pointer to the borrowed JSON object, valid only during the execution of this callback. |
| void *userData | [Input parameter] Pointer to the custom user data passed in during registration, which can be **NULL**. The framework does not obtain its ownership, nor does it dereference or release the pointer. |

### OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionRegisterInteractionObserver(ArkUI_ContextHandle uiContext, uint32_t eventMask, uint32_t *registerID, OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback callback, void *userData)
```

**Description**

Registers a UI interaction event observer.<br>The observer receives event callbacks only for the types specified by **eventMask**. Multiple observers can be registered for the same UI instance. Registering repeatedly with the same callback and **userData** combination creates a new independent observer and assigns a new registration ID.<br>When the observer is no longer used, [OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver()](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectionunregisterinteractionobserver) must be called to unregister the callback.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | [Input parameter] Pointer to the UI instance, which cannot be **NULL**. |
| uint32_t eventMask | [Input parameter] Bit mask of the event types to listen for, formed by the bitwise OR of the enumerated values of [OH_ArkUI_NativeModule_UIInfoCollection_InteractionEventType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollection_interactioneventtype). The supported flag range is from **OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TAP** to **OH_ARKUI_NATIVEMODULE_UIINFOCOLLECTION_INTERACTION_EVENT_TOUCH**; bits outside this range are ignored. If no supported flag is set, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| uint32_t *registerID | [Out parameter] Pointer to the observer registration ID, which cannot be **NULL**. The value it points to does not need to be initialized; the registration ID is written on success, and set to **0** on failure. |
| [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback) callback | [Input parameter] Callback function invoked when a matching event occurs, which cannot be **NULL**. |
| void *userData | [Input parameter] Pointer to the custom user data passed to the callback, which can be **NULL**. The framework does not take ownership of it; the caller must ensure that the data remains valid until the observer is unregistered. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a required pointer parameter is **NULL**, or **eventMask** does not contain any supported flag.<br>Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the UI context is invalid. |

### OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIInfoCollectionUnregisterInteractionObserver(uint32_t registerID)
```

**Description**

Unregisters a UI interaction event observer.<br>After this call completes, the corresponding callback function is no longer invoked.<br>This API is not thread-safe and must not be called from a non-UI thread.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| uint32_t registerID | [Input parameter] Registration ID returned upon successful registration. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the registration ID is invalid. |

### OH_ArkUI_NativeModule_UIAgentJsonCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIAgentJsonCallback)(ArkUI_ContextHandle context, uint64_t requestId, ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_UIJsonWrapper *json, void *userData)
```

**Description**

Defines the callback function called when an asynchronous JSON tree collection request completes.<br>Each accepted request triggers the callback on the UI thread and only once. Only when **errorCode** is [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) does the callback receive a non-**NULL** JSON object and obtain its ownership. The caller must call [OH_ArkUI_NativeModule_UIJsonWrapperDestroy()](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) to release the object.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] UI context used when initiating the request. |
| uint64_t requestId | [Input parameter] ID assigned to the accepted request. |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) errorCode | [Input parameter] Processing result of the request. |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [Input parameter] Pointer to the immutable JSON result. It is **NULL** when the request fails, and contains the UI tree represented as a JSON structure when the request succeeds. The top level of the JSON object contains the **schemaVersion** field. You must release this object after use. |
| void *userData | [Input parameter] Pointer to the data passed by the caller to [OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync()](#oh_arkui_nativemodule_uiagentgettreejsonasync). It can be **NULL**, indicating that no custom context is provided. This pointer is passed back as is, and the framework does not dereference or release the data it points to. The ownership of the data remains with the caller, and the caller must ensure that the data remains valid until this callback returns. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestCreate()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestCreate(OH_ArkUI_NativeModule_UIAgentTreeType treeType, OH_ArkUI_NativeModule_UIAgentTreeRequest **request)
```

**Description**

Creates a UI tree collection request.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreetype) treeType | [Input parameter] UI tree type, which must be an enumerated value of **OH_ArkUI_NativeModule_UIAgentTreeType**. |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) **request | [Output parameter] Pointer to the output parameter used to receive the created request object. The caller must call [OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy()](#oh_arkui_nativemodule_uiagenttreerequestdestroy) to release the object. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the request is created successfully.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input or output parameter is invalid.<br>Returns [ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the memory allocation fails. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy()

```c
void OH_ArkUI_NativeModule_UIAgentTreeRequestDestroy(OH_ArkUI_NativeModule_UIAgentTreeRequest *request)
```

**Description**

Destroys a UI tree collection request object.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the request object to destroy. It can be **NULL**; no operation is performed when **NULL** is passed in. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterPureLayoutNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether to filter pure layout nodes from the returned UI tree.<br>Filtering is disabled by default. When enabled, descendant nodes that still need to be retained under a filtered node are attached to the nearest retained ancestor node, preserving their original relative order.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the request object to configure. |
| bool enabled | [Input parameter] Whether to filter pure layout nodes. The value **true** means to filter pure layout nodes, and **false** means the opposite. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the option is set successfully.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **request** is **NULL**. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether to filter fully occluded nodes from the returned UI tree.<br>Filtering is disabled by default, and it can be enabled only for visible tree collection requests. Enabling occlusion filtering may introduce significant additional computation to collection. Use it as appropriate based on the complexity of the UI. Disabling this option does not disable visibility filtering, clipping filtering, off-screen node filtering, or fully transparent node filtering.<br>The opacity threshold that a node acting as an occluder must meet is configured separately by [OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold()](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetocclusionopacitythreshold). Modifying this option does not change that threshold.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the request object to configure. It cannot be **NULL**. |
| bool enabled | [Input parameter] Whether to enable occlusion filtering. The value **true** means to enable, and **false** means the opposite. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the option is set successfully. Setting **false** for a full tree collection request also succeeds.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **request** is **NULL**.<br>Returns [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **enabled** is set to **true** for a full tree collection request. In this case, the request object remains unchanged. To enable this option, use a visible tree collection request. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetOcclusionOpacityThreshold(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, float threshold)
```

**Description**

Sets the minimum final opacity that a node must reach to participate in occlusion determination as an occluder.<br>The default value is **1.0**, and this option is supported only for visible tree collection requests. A target node is removed only when the union of the regions of the occluding nodes that meet the threshold condition completely covers the effective visible region of the target node.<br>If occlusion filtering is not enabled through [OH_ArkUI_NativeModule_UIAgentTreeRequestSetFilterOccludedNodes()](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetfilteroccludednodes), this threshold does not take effect.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the UI tree collection request. |
| float threshold | [Input parameter] Opacity threshold. The value range is [0.0, 1.0]. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the threshold is set successfully.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if  **request** is **NULL**.<br>Returns [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the threshold is out of the valid range.<br>Returns [ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if  request is a full tree collection request. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether to collect additional interaction information.<br>Collection is disabled by default. When enabled, the result includes supported interaction information, such as whether a node is clickable, focusable, or editable. This option does not register an event observer and does not change the interaction behavior of any node.<br>Disabling this option does not remove fields already present in the default compact result. Advanced property collection does not implicitly enable this option, nor does it collect fields exclusive to this option.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the request object to configure, which cannot be **NULL**. |
| bool enabled | [Input parameter] Whether to collect interaction information. The value **true** means to collect, and **false** means the opposite. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the option is set successfully.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **request** is **NULL**. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether to collect additional accessibility information.<br>Collection is disabled by default. When enabled, the result includes supported accessibility information, such as accessibility content. This option does not enable accessibility services and does not change node behavior.<br>Disabling this option does not remove fields already present in the default compact result. Advanced property collection does not implicitly enable this option, nor does it collect fields exclusive to this option.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the request object to configure, which cannot be **NULL**. |
| bool enabled | [Input parameter] Whether to collect accessibility information. The value **true** means to collect, and **false** means the opposite. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the option is set successfully.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **request** is NULL. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether to collect advanced visual properties.<br>Collection is disabled by default. When enabled, the result additionally includes supported properties that describe directly perceivable appearance, such as visual style and display state.<br>Properties already present in the default compact result are not collected again. Regardless of whether the interaction information and accessibility information collection options are enabled, the fields exclusive to these two categories do not belong to this group of properties. Internal diagnostic properties are never included.<br>This option is independent of the advanced functional property collection option and does not change the nodes retained in the UI tree.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the request object to configure, which cannot be **NULL**. |
| bool enabled | [Input parameter] Whether to collect advanced visual properties. The value **true** means to collect, and **false** means the opposite. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the option is set successfully.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if  **request** is **NULL**. |

### OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties(OH_ArkUI_NativeModule_UIAgentTreeRequest *request, bool enabled)
```

**Description**

Sets whether to collect advanced functional properties.<br>Collection is disabled by default. When enabled, the result additionally includes supported properties that describe the component behavior and functional capabilities you configure.<br>Properties already present in the default compact result are not collected again. Regardless of whether the interaction information and accessibility information collection options are enabled, the fields exclusive to these two categories do not belong to this group of properties. Internal diagnostic properties are never included.<br>This option is independent of the advanced visual property collection option and does not change the nodes retained in the UI tree.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the request object to configure, which cannot be **NULL**. |
| bool enabled | [Input parameter] Whether to collect advanced functional properties. The value **true** means to collect, and **false** means the opposite. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the option is set successfully.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **request** is **NULL**. |

### OH_ArkUI_NativeModule_UIAgentGetTreeJson()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJson(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIJsonWrapper **json)
```

**Description**

Synchronously collects the UI tree and returns it in JSON format.<br>This API must be called on the UI thread. The result contains at most 5,000 nodes and must not exceed 5 MiB in size. The size limit is based on the canonical compact JSON format; if the formatted output with indentation and line breaks itself exceeds 5 MiB, the request also fails. Partial JSON data is not returned.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] UI context to which the UI tree to be collected belongs. |
| [const OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the collection request. |
| [OH_ArkUI_NativeModule_UIJsonFormat](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonformat) format | [Input parameter] JSON output format. |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) **json | [Output parameter] Pointer to the output parameter used to receive the immutable JSON result object. It cannot be **NULL** and must point to writable storage that remains valid throughout the call. The caller does not need to initialize **\*json** in advance. On success, **\*json** is non-NULL, and the top level of the result object contains the **schemaVersion** field. The caller owns the result object and must call [OH_ArkUI_NativeModule_UIJsonWrapperDestroy()](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) to release the object. On any failure, as long as **json** points to valid writable storage, **\*json** is set to **NULL**, and the caller does not need to release the result object. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the collection is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the parameter or output format is invalid.<br>Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the UI context is invalid.<br>Returns [ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the API is called on a non-UI thread.<br>Returns [ARKUI_ERROR_CODE_RESULT_TOO_LARGE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the result exceeds the node count or size limit.<br>Returns [ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the memory allocation fails.<br>Returns [ARKUI_ERROR_CODE_INTERNAL_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if another internal error occurs. |

### OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetTreeJsonAsync(ArkUI_ContextHandle context, const OH_ArkUI_NativeModule_UIAgentTreeRequest *request, OH_ArkUI_NativeModule_UIJsonFormat format, OH_ArkUI_NativeModule_UIAgentJsonCallback callback, void *userData, uint64_t *requestId)
```

**Description**

Initiates an asynchronous UI tree collection request and receives the collection result through an asynchronous callback.<br>This API must be called on the UI thread. The request and format are copied before the API returns, so the caller can destroy or reuse the request object immediately after the call returns. Each accepted request completes on the UI thread and only once.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] UI context to which the UI tree to be collected belongs. |
| [const OH_ArkUI_NativeModule_UIAgentTreeRequest](capi-arkui-nativemodule-oh-arkui-nativemodule-uiagenttreerequest.md) *request | [Input parameter] Pointer to the collection request. |
| [OH_ArkUI_NativeModule_UIJsonFormat](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonformat) format | [Input parameter] JSON output format. |
| [OH_ArkUI_NativeModule_UIAgentJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagentjsoncallback) callback | [Input parameter] Callback invoked when the request completes. On success, the callback obtains ownership of the JSON object and must call [OH_ArkUI_NativeModule_UIJsonWrapperDestroy()](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) to release the object. The top-level structure of the JSON object contains the **schemaVersion** field. |
| void *userData | [Input parameter] Pointer to the data provided by the caller and passed to the callback. It can be **NULL**, indicating that no custom context is provided. The framework only saves the pointer value until the request completes and passes it back as is, without copying, dereferencing, or releasing the data pointed to. The data is owned by the caller, and the caller must ensure that the data remains valid until the completion callback returns. The pointer is not retained when the request is synchronously rejected. |
| uint64_t *requestId | [Output parameter] Pointer to the output parameter used to receive the ID of the accepted request. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the request has been accepted.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the parameter or output format is invalid.<br>Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the UI context is invalid.<br>Returns [ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the API is called on a non-UI thread.<br>Returns [ARKUI_ERROR_CODE_COMMAND_UNFINISHED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the previous request has not been completed. |

### OH_ArkUI_NativeModule_UIAgentGetPageText()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIAgentGetPageText(ArkUI_ContextHandle uiContext, OH_ArkUI_NativeModule_UIJsonWrapper** pageText)
```

**Description**

Synchronously collects the text of the current ArkUI page and outputs it in JSON format.<br>Each JSON item contains an integer "id" used to identify the control, a rectangular region "rect" relative to the target window, and a string "content" representing the text content. After use, [OH_ArkUI_NativeModule_UIJsonWrapperDestroy()](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) must be called to release the memory occupied by the result. This API must be called on the UI thread.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | [Input parameter] Context of the target UI instance whose text is to be collected. |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)** pageText | [Output parameter] Double pointer to the output parameter used to receive the result object. The caller should initialize the object pointer it points to to **NULL**. On success, the caller owns the returned object and must call [OH_ArkUI_NativeModule_UIJsonWrapperDestroy()](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) to release the object when it is no longer used. On failure, if the output parameter is valid, the object pointer it points to is set to **NULL**. On success, the top level of the returned JSON object contains the **schemaVersion** field, which must be carried even if the page is empty. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **pageText** is **NULL**.<br>Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **uiContext** is **NULL** or has become invalid.<br>Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the native implementation is unavailable.<br>Returns [ARKUI_ERROR_CODE_INTERNAL_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the current page does not exist, the size of the JSON data cannot be represented by uint32_t, or collection or serialization fails. |

### OH_ArkUI_NativeModule_UIContentChangeEventCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIContentChangeEventCallback)(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData)
```

**Description**

Defines the callback function invoked when a registered ArkUI content change event is triggered.<br>The callback is executed on the UI thread associated with the UI context specified at registration. The event snapshot is immutable and is valid only until this callback returns. ArkUI only borrows **userData**, does not obtain its ownership, and does not access or release the data it points to.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [Input parameter] Pointer to the immutable event snapshot. |
| void* userData | [Input parameter] Pointer passed in when the callback is registered. It can be **NULL**. |

### OH_ArkUI_NativeModule_RegisterUIContentChangeEvent()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_RegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, bool withStart, uint32_t eventMask, uint32_t ignoreMask, void* userData, OH_ArkUI_NativeModule_UIContentChangeEventCallback callback, uint64_t* subscriptionId)
```

**Description**

Registers a subscription for ArkUI content change events of the selected categories for the specified UI context.<br>Each successful call creates an independent subscription. The returned subscription ID is non-zero and unique within that UI context. The callback is executed synchronously on the UI thread associated with that UI context. ArkUI only borrows **uiContext** and **userData** and does not release either. On failure, the value pointed to by **subscriptionId** is not modified. This API must be called on the UI thread; calling it from a non-UI thread causes process termination.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | [Input parameter] UI context to listen for. This handle must remain valid for the lifetime of the subscription. |
| bool withStart | [Input parameter] Whether to report start events. The value **true** indicates to report start events, for example, page switching start and scrolling start; **false** indicates to report only end events. |
| uint32_t eventMask | [Input parameter] Event categories to subscribe to, formed by the bitwise OR of the enumerated values of [OH_ArkUI_NativeModule_UIContentChangeEventCategory](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcategory). It cannot be **0**. The [OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_SCROLL](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcategory) category does not distinguish scroll subtypes. To ignore specific scroll events, set the corresponding flag of [OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLTO](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype) or [OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLBY](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype) in **ignoreMask**. |
| uint32_t ignoreMask | [Input parameter] Event types to ignore, formed by the bitwise OR of the enumerated values of [OH_ArkUI_NativeModule_UIContentChangeIgnoreType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype). |
| void* userData | [Input parameter] Pointer to the user-defined data passed to the callback. This pointer can be **NULL**, and the ownership of the data belongs to the caller. |
| [OH_ArkUI_NativeModule_UIContentChangeEventCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcallback) callback | [Input parameter] Callback function invoked when a matching event occurs. It cannot be **NULL**. |
| uint64_t* subscriptionId | [Output parameter] Pointer used to receive the subscription ID. A non-zero subscription ID is written when the operation succeeds. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation succeeds.<br>Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **uiContext** is **NULL** or no longer active.<br>Returns [ARKUI_ERROR_CODE_CALLBACK_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **callback** is **NULL**.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **eventMask** or **subscriptionId** is invalid.<br>Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the native module has not been initialized. |

### OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent(ArkUI_ContextHandle uiContext, uint64_t subscriptionId)
```

**Description**

Unregisters a still-valid ArkUI content change event subscription in the specified UI context.<br>After this API returns successfully, subsequent events no longer trigger the callback of the removed subscription, and the caller can then release its **userData**. Unsubscribing within a callback does not change the batch of callbacks currently being dispatched. This API must be called on the UI thread; calling it from a non-UI thread causes process termination.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | [Input parameter] UI context to which the subscription belongs. |
| uint64_t subscriptionId | [Input parameter] Subscription ID that belongs to **uiContext** and is still valid. It must be a non-zero value. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **uiContext** is **NULL** or is no longer active.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **subscriptionId** is set to **0**, cannot be identified, or the corresponding subscription has already been removed.<br>Returns [ARKUI_ERROR_CODE_CAPI_INIT_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the native C API has not been initialized. |

### OH_ArkUI_NativeModule_UIContentChangeEventGetType()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetType(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, OH_ArkUI_NativeModule_UIContentChangeEventType* type)
```

**Description**

Obtains the event type from an ArkUI content change event snapshot.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [Input parameter] Pointer to the event snapshot, which is valid only during callback execution. |
| [OH_ArkUI_NativeModule_UIContentChangeEventType](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventtype)* type | [Output parameter] Pointer to the event type, which is written when the operation is successful. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **event** or **type** is **NULL**. |

### OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, uint64_t* nanoTimestamp)
```

**Description**

Obtains the monotonic timestamp of an ArkUI content change event snapshot.<br>The timestamp is recorded when the event completes, in nanoseconds, using a monotonic clock, and does not represent calendar time.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [Input parameter] Pointer to the event snapshot, valid only during callback execution. |
| uint64_t* nanoTimestamp | [Output parameter] Pointer to the monotonic timestamp, in nanoseconds. It is written on success. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **event** or **nanoTimestamp** is **NULL**. |

### OH_ArkUI_NativeModule_UIContentChangeEventGetContext()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContext(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, ArkUI_ContextHandle* uiContext)
```

**Description**

Obtains the UI context associated with an ArkUI content change event snapshot.<br>The returned handle is a borrowed handle. The caller does not own it, must not release it, and must not use it after the callback returns.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [Input parameter] Pointer to the event snapshot, valid only during callback execution. |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md)* uiContext | [Output parameter] Pointer to the borrowed UI context handle, which is written on success. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **event** or **uiContext** is **NULL**. |

### OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, const OH_ArkUI_NativeModule_UIJsonWrapper** json)
```

**Description**

Obtains the content change event details from an ArkUI content change event snapshot and returns them as a JSON wrapper object.<br>The top level of the JSON output contains the **schemaVersion** field, and includes the content change type, trigger node, target node, overlay type, and subtree dump information whose inclusion depends on the event category.<br>A page event identifies the target page, a scroll event identifies the node where scrolling occurs, and an overlay event identifies the overlay node and provides the overlay type, such as "dialog". The trigger node is the node that causes the content change, and is available in overlay events and general start and end scenarios. For page events and scroll events, if the trigger node cannot be provided, the node is **NULL**. If the target node cannot be provided, the operation still succeeds, and the returned JSON still contains the **schemaVersion** field. The handles referenced in the JSON wrapper object are all borrowed handles and must not be released or used after the callback returns.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIContentChangeEvent](capi-arkui-nativemodule-oh-arkui-nativemodule-uicontentchangeevent.md)* event | [Input parameter] Pointer to the event snapshot, valid only during callback execution. |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)** json | [Output parameter] Double pointer to the output parameter used to receive the [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) object that contains the content change event details. The caller must not release the wrapper object and must not use the object after the callback returns. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **event** or **json** is **NULL**. |

### OH_ArkUI_NativeModule_ImageCollectionCallback()

```c
typedef void (*OH_ArkUI_NativeModule_ImageCollectionCallback)(ArkUI_ErrorCode errorCode, OH_ArkUI_NativeModule_ImageCollection* collection, void* userData)
```

**Description**

Defines the callback function used to return the ArkUI node image collection result.<br>For each accepted request, the framework invokes this callback on the UI thread and only once. Each non-**NULL** collection is transferred to the caller. A collection is returned even if some result items fail. The caller must call [OH_ArkUI_NativeModule_ImageCollectionDestroy()](#oh_arkui_nativemodule_imagecollectiondestroy) to release each non-**NULL** collection.<br>The framework passes **userData** back as is, does not dereference the pointer, and does not copy or release the object it points to. The caller must ensure that the object remains valid until the callback finishes using it.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) errorCode | [Input parameter] Overall processing result of the request.<br>[ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) indicates that all result items are successful.<br>[ARKUI_ERROR_CODE_COLLECTION_PARTIAL_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) indicates that some result items fail to be collected.<br>[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) indicates that the associated UI context becomes invalid after the request is accepted.<br>[ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) indicates that collection allocation fails. |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)* collection | [Input parameter] Pointer to the result collection. It is a non-**NULL** value when all result items are successful or some result items fail; it is **NULL** when the UI context becomes invalid or collection allocation fails. |
| void* userData | [Input parameter] Pointer to the caller-defined context, which can be **NULL**. |

### OH_ArkUI_NativeModule_GetImagesByNodeIdAsync()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_GetImagesByNodeIdAsync(ArkUI_ContextHandle context, const int32_t* nodeIds, uint32_t count, OH_ArkUI_NativeModule_ImageCollectionCallback callback, void* userData)
```

**Description**

Asynchronously collects the images corresponding to the specified ArkUI node IDs.<br>A single request can contain 1 to 20 non-duplicate node IDs. The framework copies the **nodeIds** array before this API returns. If the value of **count** is less than or equal to 0 or greater than 20, this API returns [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode).<br>Each accepted node ID has a corresponding result item in the result collection, even if the node is not found or its image cannot be captured. For an **Image** node, if its source PixelMap can be obtained, the complete source PixelMap is returned; otherwise, a snapshot of the rendered content within the node boundary is taken. For a non-**Image** node, a snapshot of the rendered content within the node boundary is also taken. The node does not need to be visible.<br>If the ArkUI node corresponding to a requested node ID is not found, the corresponding result item reports [ARKUI_ERROR_CODE_NODE_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode), and the caller should check the node ID. When the snapshot times out, the corresponding result item reports [ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode), and the caller can retry the request. When a result item is consumed in the collection, the error code of that result item can be obtained. When any result item fails, the callback reports [ARKUI_ERROR_CODE_COLLECTION_PARTIAL_FAILED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode), but the collection is still returned.<br>The caller can call this API from any thread. For each accepted request, the framework invokes the callback exactly once on the UI thread associated with the context. If the previous request has not completed, this API returns [ARKUI_ERROR_CODE_COMMAND_UNFINISHED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode). The caller must wait for that request to complete before submitting the next request.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | [Input parameter] ArkUI context used to process the request. It cannot be **NULL**. |
| const int32_t* nodeIds | [Input parameter] Pointer to the first element of the node ID array. The array contains **count** non-duplicate ArkUI node IDs. The pointer cannot be **NULL**. |
| uint32_t count | [Input parameter] Number of node IDs. The valid range is (0, 20]. |
| [OH_ArkUI_NativeModule_ImageCollectionCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_imagecollectioncallback) callback | [Input parameter] Callback used to receive the result. It cannot be **NULL**. |
| void* userData | [Input parameter] Pointer to the caller-defined context, which is passed to the callback as is. It can be **NULL**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the framework has accepted the request.<br>Returns [ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **context** is **NULL** or invalid.<br>Returns [ARKUI_ERROR_CODE_CALLBACK_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **callback** is **NULL**.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **nodeIds** is **NULL**.<br>Returns [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the value of **count** is less than or equal to 0 or greater than 20.<br>Returns [ARKUI_ERROR_CODE_DUPLICATE_NODE_ID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if there is a duplicate node ID.<br>Returns [ARKUI_ERROR_CODE_COMMAND_UNFINISHED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the previous request has not completed. |

### OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId(OH_ArkUI_NativeModule_ImageCollection* collection, int32_t nodeId, OH_PixelmapNative** outPixelmap, ArkUI_ErrorCode* outItemError)
```

**Description**

Takes out the result corresponding to the specified node ID.<br>For a result item whose image collection succeeds, this API transfers the ownership of the PixelMap to the caller. The caller must call [OH_PixelmapNative_Destroy()](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to release the object. This API can also take out a result item whose image collection fails, in which case **\*outPixelmap** is set to **NULL** and the error code of that result item is written to **\*outItemError**. The result corresponding to each node ID in the collection can be taken out only once.<br>When the collection is destroyed, only the PixelMap instances that the caller has not taken out are released. The PixelMap instances already transferred to the caller are not invalidated by this.<br>The caller must not call this API concurrently with other collection operation APIs on the same collection.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)* collection | [Input parameter] Pointer to the image collection from which the result item is to be taken out. It cannot be **NULL**. |
| int32_t nodeId | [Input parameter] ArkUI node ID corresponding to the result item to be taken out. |
| [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)** outPixelmap | [Output parameter] Double pointer to the output parameter used to receive the PixelMap whose ownership has been transferred. It cannot be **NULL**. For a failed result item, the PixelMap pointer it points to is set to **NULL**. |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)* outItemError | [Output parameter] Pointer to the output parameter used to receive the error code of the result item. It cannot be **NULL**.<br>[ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) indicates that the result item is collected successfully.<br>[ARKUI_ERROR_CODE_NODE_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) indicates that the ArkUI node corresponding to the requested node ID is not found when the image is collected.<br>[ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) indicates that memory allocation required to generate the image result fails.<br>[ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) indicates that the snapshot times out. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the result item is taken out successfully, including a result item whose image collection fails.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a mandatory pointer parameter is **NULL**.<br>Returns [ARKUI_ERROR_CODE_COLLECTION_ITEM_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **nodeId** has no corresponding result item in **collection**.<br>Returns [ARKUI_ERROR_CODE_COLLECTION_ITEM_ALREADY_TAKEN](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the result item has already been taken out. |

### OH_ArkUI_NativeModule_ImageCollectionDestroy()

```c
void OH_ArkUI_NativeModule_ImageCollectionDestroy(OH_ArkUI_NativeModule_ImageCollection* collection)
```

**Description**

Destroys the image collection and releases the PixelMap instances that have not been taken out.<br>The caller must destroy every non-**NULL** collection returned by the callback, even if all result items in it have been taken out. This API does not release the PixelMap instances obtained through [OH_ArkUI_NativeModule_ImageCollectionTakeItemByNodeId()](#oh_arkui_nativemodule_imagecollectiontakeitembynodeid), nor does it invalidate these instances.<br>The caller must not call this API concurrently with other collection operation APIs on the same collection.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_ImageCollection](capi-arkui-nativemodule-oh-arkui-nativemodule-imagecollection.md)* collection | [Input parameter] Pointer to the image collection to destroy. It can be **NULL**. If **collection** is **NULL**, no operation is performed. |
