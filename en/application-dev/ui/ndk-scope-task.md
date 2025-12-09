# Ensuring Multi-Instance Functionality in the NDK
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

Since API version 20, the ArkUI development framework provides the [OH_ArkUI_RunTaskInScope](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_runtaskinscope) API to address component operation challenges in multi-instance scenarios on the native side. This feature dynamically switches execution contexts to ensure the validity of component attribute settings across instances, preventing API call exceptions caused by instance context mismatches.

In NDK multi-window development scenarios requiring cross-instance attribute configuration, this capability maintains proper context integrity during cross-instance operations, thereby avoiding cross-instance API call failures.

> **NOTE**
> - This feature is designed for interaction scenarios between different UI instances in NDK multi-window development, such as modifying attributes of components created on page A or handling logic for components not mounted to the UI tree on page B.
>
> - You can pass custom data structures (such as component pointers or service parameters) through the **userData** parameter to precisely locate target components within callback tasks.
>
> - This feature complements APIs like [OH_ArkUI_NodeUtils_GetAttachedNodeHandleById](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getattachednodehandlebyid) to prevent null pointer or permission exceptions resulting from cross-instance access.


This example demonstrates the basic usage of the **OH_ArkUI_RunTaskInScope** API, using **OH_ArkUI_NodeUtils_GetAttachedNodeHandleById** to retrieve components from previous pages. For details, see [OH_ArkUI_NodeUtils_GetAttachedNodeHandleById](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getattachednodehandlebyid). The **userData** parameter passes a component pointer for setting corresponding component attributes.


<!-- @[runtaskinscopethree_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkScopeTask/entry/src/main/cpp/napi_init.cpp) -->

``` C++
const uint32_t VALUE_2 = 250;
const uint32_t VALUE_3 = 480;
```

<!-- @[runtaskinscopeone_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkScopeTask/entry/src/main/cpp/napi_init.cpp) -->

``` C++
//page1
ArkUI_NodeHandle button = nodeAPI->createNode(ARKUI_NODE_BUTTON);
ArkUI_AttributeItem LABEL_Item = {.string = "pageOneButton"};
// Set the ID for component retrieval using APIs on the second page.
ArkUI_AttributeItem id = {.string = "pageOneButton"};
nodeAPI->setAttribute(button, NODE_ID, &id);
nodeAPI->setAttribute(button, NODE_BUTTON_LABEL, &LABEL_Item);
nodeAPI->addChild(textContainer, button);
```

<!-- @[runtaskinscopetwo_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkScopeTask/entry/src/main/cpp/napi_init.cpp) -->

``` C++
//page2
// Retrieve pageOneButton created on the previous page using OH_ArkUI_NodeUtils_GetAttachedNodeHandleById.
ArkUI_NodeHandle pageOneButton = nullptr;
auto errorCode = OH_ArkUI_NodeUtils_GetAttachedNodeHandleById("pageOneButton", &pageOneButton);
if (errorCode != ARKUI_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "test Failed to get pageOneButton handle, error code: %{public}d", errorCode);
    return nullptr;
}
auto uiContext = OH_ArkUI_GetContextByNode(pageOneButton);
if (uiContext == nullptr) {
    OH_LOG_ERROR(LOG_APP, "test Failed to get UI context for pageOneButton");
    return nullptr;
}
OH_ArkUI_RunTaskInScope(uiContext, pageOneButton, [](void *userData) {
    auto *nodeAPI = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
        OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
    auto pageOneButton = (ArkUI_NodeHandle)userData;
    ArkUI_NumberValue value[] = {VALUE_3};
    ArkUI_AttributeItem LABEL_Item = {.string = "success"};
    value[0].f32 = VALUE_2;
    ArkUI_AttributeItem button_Item = {value, sizeof(value) / sizeof(ArkUI_NumberValue)};
    nodeAPI->setAttribute(pageOneButton, NODE_BUTTON_LABEL, &LABEL_Item);
    nodeAPI->setAttribute(pageOneButton, NODE_WIDTH, &button_Item);
});
```