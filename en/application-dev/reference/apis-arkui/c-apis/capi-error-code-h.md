# error_code.h

## Overview

Defines the error code for the native module.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ErrorCode](#arkui_errorcode) | ArkUI_ErrorCode | Enumerates error codes of ArkUI native APIs, which are used to indicate the results or failure causes of API calls. |

## Enum type description

### ArkUI_ErrorCode

```c
enum ArkUI_ErrorCode
```

**Description**

Enumerates error codes of ArkUI native APIs, which are used to indicate the results or failure causes of API calls.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ERROR_CODE_NO_ERROR = 0 | No error.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_PARAM_INVALID = 401 | Parameter error.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR = 500 | API initialization error.<br>**Since**: 18 |
| ARKUI_ERROR_CODE_INTERNAL_ERROR = 100001 | Internal error, such as API call failure due to abnormal running environment or operation failure caused by API internal execution errors.<br>**Since**: 15 |
| ARKUI_ERROR_CODE_PARAM_ERROR = 100023 | Parameter error. For details about the error code, see 100023 Parameter Error.<br>**Since**: 21 |
| ARKUI_ERROR_CODE_XCOMPONENT_STATE_INVALID = 103501 | The **XComponent** is in an invalid or unsupported state. For details about the error code, see XComponent Error Codes.<br>**Since**: 18 |
| ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED = 106102 | The component does not support specific attributes or events. For details, see Interaction Event Error Codes.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED = 106103 | The corresponding operations cannot be performed on the node created by ArkTS. For details about the error code, see 106103 Operation Not Allowed on Nodes Created by ArkTS.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_ADAPTER_NOT_BOUND = 106104 | The adapter for lazy loading is not bound to the component. For details about the error code, see 106104 Adapter Not Bound.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_ADAPTER_EXIST = 106105 | The adapter already exists. For details about the error code, see 106105 Adapter Already Exists.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_CHILD_NODE_EXIST = 106106 | Failed to add the adapter because the corresponding node already has a child node. For details about the error code, see 106106 Child Node Exists.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE = 106107 | The index parameter in the component event exceeds the array length limit. For details about the error code, see 106107 Index Out of Range.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID = 106108 | The data requested by the caller does not exist in the component event. For details about the error code, see 106108 Data Not Found.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN = 106109 | The component event does not support return values. For details about the error code, see 106109 Return Value Not Supported.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE = 106110 | The event type is not supported. For details about the error code, see 106110 Unsupported Event Type.<br>**Since**: 21 |
| ARKUI_ERROR_CODE_NODE_INDEX_INVALID = 106200 | Invalid index.<br>For details about the error code, see 106200 Invalid Index Value.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_GET_INFO_FAILED = 106201 | Failed to obtain the route navigation information.<br>For details about the error code, see 106201 Failed to Obtain Route Navigation Information.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR = 106202 | The buffer size passed is insufficient to accommodate the target data.<br>For details about the error code, see 106202 Invalid Buffer Size.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE = 106203 | The passed node is not mounted to the component tree. For details about the error code, see 106203 Passed Node Not Mounted to Component Tree.<br>**Since**: 15 |
| ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD = 106204 | Operations on the provided node are not supported on non-UI threads. For details about the error code. See 106204 Operations on the Provided Node Not Supported on Non-UI Threads.<br>**Since**: 22 |
| ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID = 106205 | The input parameter for the color inversion capability is incorrect. For details about the error code, see 106205 Color Inversion Capability Configuration Error.<br>**Since**: 20 |
| ARKUI_ERROR_CODE_NODE_IS_ADOPTED = 106206 | The node has been accepted as an auxiliary node. For details about the error code, see 106206 The Node Has Been Accepted as an Auxiliary Node.<br>**Since**: 22 |
| ARKUI_ERROR_CODE_NODE_HAS_PARENT = 106207 | The accepted node already has a parent node. For details about the error code, see 106207 The Auxiliary Node to Accept Has a Parent Node.<br>**Since**: 22 |
| ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED = 106208 | The node cannot be accepted as an auxiliary node. For details about the error code, see 106208 The Node Cannot Be Accepted as an Auxiliary Node.<br>**Since**: 22 |
| ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO = 106209 | The node cannot accept other nodes. For details about the error code, see 106209 The Node Cannot Accept Other Nodes.<br>**Since**: 22 |
| ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN = 106210 | The node is not an auxiliary node accepted by the target node. For details about the error code, see 106210 The Node Is Not an Affiliated Node Accepted by the Target Node.<br>**Since**: 22 |
| ARKUI_ERROR_CODE_NO_ATTRIBUTE_FOUND = 106211 | Can not get attribute because it is not set before.<br>**Since**: 26.0.1 |
| ARKUI_ERROR_CODE_SUB_ANIMATION_INVALID = 106212 | The parameters of sub animation are invalid.<br>**Since**: 26.0.1 |
| ARKUI_ERROR_CODE_ANIMATION_GROUP_NOT_FOUND = 106213 | The animation group is not found on the UIContext.<br>**Since**: 26.0.1 |
| ARKUI_ERROR_CODE_ANIMATION_GROUP_REENTRANT_CALL = 106214 | A re-entrant call to the animation group API is detected on the same thread.<br>**Since**: 26.0.1 |
| ARKUI_ERROR_CODE_ANIMATION_GROUP_INVALID_STATE = 106215 | The animation group is not in the state required by the operation.<br>**Since**: 26.0.1 |
| ARKUI_ERROR_CODE_TARGET_NODE_NOT_IN_SAME_CONTEXT = 106216 | The resolved target node does not belong to the same UIContext as the context parameter.<br>**Since**: 26.0.1 |
| ARKUI_ERROR_CODE_NOT_CUSTOM_NODE = 106401 | The current node is not a custom node. For details, see Render Node Error Codes.<br>**Since**: 20 |
| ARKUI_ERROR_CODE_CHILD_EXISTED = 106402 | The current node already has child nodes. For details, see Render Node Error Codes.<br>**Since**: 20 |
| ARKUI_ERROR_CODE_RENDER_PARENT_EXISTED = 106403 | The current render node has a parent component. For details, see Render Node Error Codes.<br>**Since**: 20 |
| ARKUI_ERROR_CODE_RENDER_CHILD_NOT_EXIST = 106404 | Corresponding render child node not found. For details, see Render Node Error Codes.<br>**Since**: 20 |
| ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE = 106405 | The parameter value is out of range. For details, see Render Node Error Codes.<br>**Since**: 20 |
| ARKUI_ERROR_CODE_RENDER_IS_FROM_FRAME_NODE = 106406 | The current render node is obtained from a FrameNode. For details about the error code, see 106406 Current Render Node Is Obtained from FrameNode.<br>**Since**: 22 |
| ARKUI_ERROR_CODE_RENDER_HAS_INVALID_FRAME_NODE = 106407 | The current render node is obtained from a FrameNode and the FrameNode has not been adopted as an affiliated node or has been disposed of. For details about the error code, see 106407 Current Render Node Is Obtained from FrameNode and the FrameNode Is Disposed or No Longer Adopted.<br>**Since**: 22 |
| ARKUI_ERROR_CODE_RENDER_NOT_ADOPTED_NODE = 106408 | The current node is not in the adopted state. For details about the error code, see 106408 Current Node Is Not in Adopted State.<br>**Since**: 22 |
| ARKUI_ERROR_CODE_COMMAND_UNFINISHED = 106409 | The last command was not finished.<br>**Since**: 26.1.0 |
| ARKUI_ERROR_CODE_NODE_NOT_FOUND = 106410 | The target node was not found.<br>**Since**: 26.1.0 |
| ARKUI_ERROR_CODE_RESULT_TOO_LARGE = 106411 | Result too large.<br>**Since**: 26.1.0 |
| ARKUI_ERROR_CODE_RESOURCE_EXHAUSTED = 106412 | Resource exhausted.<br>**Since**: 26.1.0 |
| ARKUI_ERROR_CODE_DUPLICATE_NODE_ID = 106413 | The node ID is duplicated.<br>**Since**: 26.1.0 |
| ARKUI_ERROR_CODE_COLLECTION_PARTIAL_FAILED = 106414 | Some collection items failed.<br>**Since**: 26.1.0 |
| ARKUI_ERROR_CODE_COLLECTION_ITEM_NOT_FOUND = 106415 | The collection item is not found.<br>**Since**: 26.1.0 |
| ARKUI_ERROR_CODE_COLLECTION_ITEM_ALREADY_TAKEN = 106416 | The collection item has already been taken.<br>**Since**: 26.1.0 |
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE = 150001 | The current node is not focusable. For details about the error code, see 150001 Component Not Focusable.<br>**Since**: 15 |
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR = 150002 | An ancestor of the current node is not focusable. For details about the error code, see 150002 Ancestor Component Not Focusable.<br>**Since**: 15 |
| ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT = 150003 | The current node does not exist. For details about the error code, see 150003 Component Does Not Exist.<br>**Since**: 15 |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT = 160002 | Snapshot timed out. For details, see Snapshot Error Codes.<br>**Since**: 15 |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED = 160003 | The color space or dynamic range mode set in the screenshot options is not supported. For details, see Snapshot Error Codes.<br>**Since**: 23 |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED = 160004 | The **isAuto** parameter corresponding to the color space or dynamic range mode cannot be set to **true**<br>for offscreen node screenshots. For details, see Snapshot Error Codes.<br>**Since**: 23 |
| ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER = 180001 | The component is not a scrollable container. For details, see Interaction Event Error Codes.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH = 180002 | Buffer is not large enough. For details, see Interaction Event Error Codes.<br>**Since**: 12 |
| ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT = 180003 | The event is not a cloned event. For details, see Interaction Event Error Codes.<br>**Since**: 15 |
| ARKUI_ERROR_CODE_POST_CLONED_COMPONENT_STATUS_ABNORMAL = 180004 | The component status is abnormal. For details, see Interaction Event Error Codes.<br>**Since**: 15 |
| ARKUI_ERROR_CODE_POST_CLONED_NO_COMPONENT_HIT_TO_RESPOND_TO_THE_EVENT = 180005 | No component hit to respond to the event. For details, see Interaction Event Error Codes.<br>**Since**: 15 |
| ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED = 180006 | The API does not support this input event type. For details about the error code, see Interaction Event Error Codes.<br>**Since**: 20 |
| ARKUI_ERROR_CODE_INVALID_STYLED_STRING = 180101 | Invalid styled string. For details, see Styled String Error Codes.<br>**Since**: 14 |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID = 190001 | Invalid UIContext object. For details, see UI Context Error Codes.<br>**Since**: 18 |
| ARKUI_ERROR_CODE_CALLBACK_INVALID = 190002 | Invalid callback function. For details, see UI Context Error Codes.<br>**Since**: 18 |
| ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED = 180102 | The gesture recognizer type is not supported. For details, see Interaction Event Error Codes.<br>**Since**: 18 |
| ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED = 190004 | The requested operation is not allowed in the current drag and drop event processing phase. For details, see Drag Event Error Codes.<br>**Since**: 19 |
| ARKUI_ERROR_CODE_DIALOG_NODE_MOUNT_FAILURE = 103306 | The dialog box cannot be opened because the node fails to be mounted. For details, see Popup Window Error Codes.<br>**Since**: 26.0.1 |
| ARKUI_ERROR_CODE_DIALOG_SUBWINDOW_CREATE_FAILURE = 103308 | The dialog box cannot be opened because the subwindow fails to be created. For details, see Popup Window Error Codes.<br>**Since**: 26.0.1 |


