# Using Navigation Components
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @jiangdayuan-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

The NDK provides a series of status query interfaces for [Navigation](./arkts-navigation-architecture.md#overall-architecture) and page routing. You can use functions such as [OH_ArkUI_GetNavDestinationName](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnavdestinationname), [OH_ArkUI_GetNavDestinationParam](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnavdestinationparam), [OH_ArkUI_GetNavDestinationState](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnavdestinationstate), [OH_ArkUI_GetNavigationId](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnavigationid), and [OH_ArkUI_GetNavDestinationIndex](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnavdestinationindex) to query a page's status, index, name, and other information, and then perform corresponding operations based on the query results, such as displaying different page information.

This document provides development guidance for page status query. Before the query, you need to access the ArkTS pages. For details, see [Integrating with ArkTS Pages](./ndk-access-the-arkts-page.md).

## Querying Page Information

Before querying page information, ensure that the target node has been mounted to the page as a child node. If the node is not mounted, the operation will fail. For example, the corresponding information cannot be found in the [aboutToAppear](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear) lifecycle. For details about the page lifecycle and component mounting lifecycle, see [Page Lifecycle](./arkts-navigation-navdestination.md#page-lifecycle). You can load different page components based on the queried page information.

This example demonstrates only the core function code. For details about the complete sample, see <!--RP1-->[NDK Page Query API Example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKNavigation)<!--RP1End-->.

1. Query the name of the current page.

   Use [OH_ArkUI_GetNavDestinationName](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnavdestinationname) to query the name of the **NavDestination** page. You can use the [OH_ArkUI_GetRouterPageName](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getrouterpagename) API to query the router page name.

   <!-- @[get_page_name](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKNavigation/entry/src/main/cpp/QueryNavigation.h) -->
   
   ``` C
   // Obtain the page name.
   char pageName[NUM_50];
   int32_t bufferLen = 0;
   OH_ArkUI_GetNavDestinationName(node, pageName, NUM_50, &bufferLen);
   ```

2. Query page redirection parameters.

   You can use [OH_ArkUI_GetNavDestinationParam](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnavdestinationparam) to query [NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) page redirection parameters.

   <!-- @[get_page_param](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKNavigation/entry/src/main/cpp/QueryNavigation.h) -->
   
   ``` C
   // Obtain the page redirection parameters.
   napi_value param = OH_ArkUI_GetNavDestinationParam(node);
   napi_value nameVal = nullptr;
   napi_get_named_property(env, param, "name", &nameVal);
   size_t len = 0;
   napi_get_value_string_utf8(env, nameVal, nullptr, 0, &len);
   std::unique_ptr<char[]> viewName = std::make_unique<char[]>(len + 1);
   napi_get_value_string_utf8(env, nameVal, viewName.get(), len + 1, &len);
   ArkUI_NodeHandle targetNode = nullptr;
   std::string view = viewName.get();
   if (view == "QueryNavigation") {
       InitNavigationNode(column, pageName);
   } else if (view == "QueryRouter") {
       InitRouterNode(column);
   }
   nativeApi->addChild(node, column);
   ```

## Querying the Page Status

You can use [OH_ArkUI_GetNavDestinationState](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnavdestinationstate) to query the status of the **NavDestination** page to which the current placeholder component belongs. You can use the [OH_ArkUI_GetRouterPageState](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getrouterpagestate) API to query the router page and perform adaptation based on the query result, for example, setting the **visible** attribute of the component and the video playback state.

This example demonstrates only the core function code. For details about the complete sample, see <!--RP1-->[NDK Page Query API Example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKNavigation)<!--RP1End-->.

<!-- @[get_page_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKNavigation/entry/src/main/cpp/EntryModule.cpp) -->

``` C++
ArkUI_NodeHandle targetNode = nullptr;
OH_ArkUI_NodeUtils_GetAttachedNodeHandleById("navDestinationState", &targetNode);
auto entry = NativeEntry::GetInstance();
entry->ReportError(targetNode, "event clicked");
ArkUI_NavDestinationState state;
OH_ArkUI_GetNavDestinationState(targetNode, &state);
if (state == NUM_8) {
    entry->SetColor(targetNode, 0x80808080);
} else if (state == NUM_9) {
    entry->SetColor(targetNode, 0xFF000000);
}
```

## Querying Page Information

You can use [OH_ArkUI_GetNavDestinationIndex](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnavdestinationindex) to query the position of **NavDestination** to which the current placeholder component belongs in the stack. You can use the [OH_ArkUI_GetRouterPageIndex](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getrouterpageindex) API to query the router page name. Based on the returned page stack information, you can implement DFX functions during application development, such as collecting parameters for performance monitoring and user behavior analysis, which are used for data reporting and analysis.

This example demonstrates only the core function code. For details about the complete sample, see <!--RP1-->[NDK Page Query API Example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKNavigation)<!--RP1End-->.

<!-- @[get_stack_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKNavigation/entry/src/main/cpp/EntryModule.cpp) -->

``` C++
char navigationId[NUM_50];
int32_t bufferLen = 0;
OH_ArkUI_GetNavigationId(handle, navigationId, NUM_50, &bufferLen);
    
char name[NUM_50];
int32_t nameLen = OH_ArkUI_GetNavDestinationName(handle, name, NUM_50, &nameLen);
    
int32_t index = -1;
OH_ArkUI_GetNavDestinationIndex(handle, &index);
OH_LOG_Print(LOG_APP, LOG_ERROR, 0xFF00, "NAPI",
             "navigation id: %{public}s, name: %{public}s, index: %{public}d, error: %{public}s",
             navigationId, name, index, info.c_str());
```
