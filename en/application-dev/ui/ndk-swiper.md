# Using the Swiper Component
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @jiangdayuan-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

The ArkUI development framework allows you to use the **Swiper** component in NDK APIs to provide the capability of displaying child components in carousel mode. This document describes the development guidelines for NDK APIs. For details about the ArkTS guidelines, see [Creating a Swiper](arkts-layout-development-create-looping.md).

For details about the basic usage of the NDK and how to use the NDK APIs to build UIs, see [Integrating with ArkTS Pages](ndk-access-the-arkts-page.md). After the page is built and [Swiper is created](#creating-a-swiper), you can optimize the page display by [setting common attributes](#setting-common-attributes) and [setting the navigation indicator](#setting-the-navigation-indicator). When the page switches, you can obtain page switching information through [event listening](#listening-for-events).

## Creating a Swiper

In this example, [createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode) is called to create a UI component node of the **ARKUI_NODE_SWIPER** type, which is used for subsequent operations such as setting attributes. In addition, multiple **Text** components are mounted to the **Swiper** component through [addChild](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addchild) to display content.

This example shows only the core function code. For details about the complete example, see <!--RP1-->[NDKSwiperSample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKSwiperSample)<!--RP1End--> project.

<!-- @[swiper_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->

``` C++
ArkUI_NativeNodeAPI_1 *nodeApi = nullptr;
OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, nodeApi);
ArkUI_NodeHandle swiper = nodeApi->createNode(ARKUI_NODE_SWIPER);
AddChild(swiper, nodeApi);
```

## Setting Common Attributes

In this example, the display effect of the page is adjusted by setting the attributes in [ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype). The common attributes are as follows.

| Enum Item| Description|
|---------|----------|
| NODE_HEIGHT_PERCENT  | Height percentage of the component.|
| NODE_WIDTH_PERCENT   | Width percentage of the component.|
| NODE_SWIPER_PREV_MARGIN   | Size of the previous margin, that is, the extent to which the previous child item (before the currently visible item) is displayed within the window.|
| NODE_SWIPER_NEXT_MARGIN   | Size of the next margin, that is, the extent to which the next child item (after the currently visible item) is displayed within the window.|
| NODE_SWIPER_ITEM_SPACE    | Spacing between sub-items.|
| NODE_SWIPER_AUTO_PLAY     | Whether to enable automatic carousel.  |

This example shows only the code for core functions. For details about the complete example, see <!--RP1-->[NDKSwiperSample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKSwiperSample)<!--RP1End-->.

<!-- @[swiper_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->

``` C++
// Set common attributes.
ArkUI_NumberValue value[] = {0};
ArkUI_AttributeItem item = {.value = value, .size = 1};
value[0].f32 = SWIPER_HEIGHT_PERCENT;
nodeApi->setAttribute(swiper, NODE_HEIGHT_PERCENT, &item);
value[0].f32 = SWIPER_WIDTH_PERCENT;
nodeApi->setAttribute(swiper, NODE_WIDTH_PERCENT, &item);

value[0].f32 = PREV_AND_NEXT_MARGIN;
nodeApi->setAttribute(swiper, NODE_SWIPER_PREV_MARGIN, &item);
nodeApi->setAttribute(swiper, NODE_SWIPER_NEXT_MARGIN, &item);
value[0].f32 = ITEM_SPACE;
nodeApi->setAttribute(swiper, NODE_SWIPER_ITEM_SPACE, &item);
value[0].i32 = 1;
nodeApi->setAttribute(swiper, NODE_SWIPER_AUTO_PLAY, &item);
```

## Setting the Navigation Indicator

In this example, [OH_ArkUI_SwiperIndicator_Create](../reference/apis-arkui/capi-native-type-h.md#oh_arkui_swiperindicator_create)(ARKUI_SWIPER_INDICATOR_TYPE_DOT) is used to create a navigation indicator of the dot style, and [OH_ArkUI_SwiperIndicator_SetEndPosition](../reference/apis-arkui/capi-native-type-h.md#oh_arkui_swiperindicator_setendposition) and [OH_ArkUI_SwiperIndicator_SetSelectedColor](../reference/apis-arkui/capi-native-type-h.md#oh_arkui_swiperindicator_setselectedcolor) APIs are used to set the distance between the navigation indicator and the right of the **Swiper** component and the color of the selected dot, respectively.

This example shows only the code of core functions. For details about the complete example, see <!--RP1-->[NDKSwiperSample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKSwiperSample)<!--RP1End-->.

<!-- @[indicator_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->

``` C++
// Set the attributes of the navigation indicator.
ArkUI_SwiperIndicator *swiperIndicatorStyle = OH_ArkUI_SwiperIndicator_Create(ARKUI_SWIPER_INDICATOR_TYPE_DOT);
OH_ArkUI_SwiperIndicator_SetEndPosition(swiperIndicatorStyle, 0);
OH_ArkUI_SwiperIndicator_SetSelectedColor(swiperIndicatorStyle, INDICATOR_COLOR_SELECTED);

ArkUI_NumberValue value[] = {0};
ArkUI_AttributeItem item = {.value = value, .size = 1, .object = swiperIndicatorStyle};
value[0].i32 = ARKUI_SWIPER_INDICATOR_TYPE_DOT;
nodeApi->setAttribute(swiper, NODE_SWIPER_INDICATOR, &item);

OH_ArkUI_SwiperIndicator_Dispose(swiperIndicatorStyle);
```

The following figure shows the display effect.

![swiper_ndk](figures/swiper_ndk.jpg)

## Listening for Events

In this example, the event type [ArkUI_NodeEventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype) supported by the **Swiper** component is registered using [registerNodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent). You can determine the callback type and parse the corresponding callback content in the callback registered using [registerNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver). The involved callbacks are as follows:

| Enum Item| Description|
|---------|----------|
| NODE_SWIPER_EVENT_ON_CHANGE  | Index of the page displayed after the page index is switched.|
| NODE_SWIPER_EVENT_ON_ANIMATION_START   | Index of the currently displayed page at the start of the page switching animation, and index of the page switched to at the end of the animation.|

This example shows only the code of core functions. For details about the complete example, see <!--RP1-->[NDKSwiperSample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKSwiperSample)<!--RP1End-->.

<!-- @[swiper_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->

``` C++
// Register the page switching listener.
nodeApi->registerNodeEvent(swiper, NODE_SWIPER_EVENT_ON_CHANGE, 0, nullptr);
nodeApi->registerNodeEvent(swiper, NODE_SWIPER_EVENT_ON_ANIMATION_START, 1, nullptr);
nodeApi->registerNodeEventReceiver([](ArkUI_NodeEvent *event) {
    ArkUI_NodeEventType eventType = OH_ArkUI_NodeEvent_GetEventType(event);
    if (eventType == NODE_SWIPER_EVENT_ON_CHANGE) {
        auto componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
        if (componentEvent) {
            auto index = componentEvent->data[0].i32;
            OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "NDKSwiper",
                         "NODE_SWIPER_EVENT_ON_CHANGE index = %{public}d", index);
        }
    }
    if (eventType == NODE_SWIPER_EVENT_ON_ANIMATION_START) {
        auto componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
        if (componentEvent) {
            auto currentIndex = componentEvent->data[0].i32;
            auto targetIndex = componentEvent->data[1].i32;
            OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "NDKSwiper",
                         "NODE_SWIPER_EVENT_ON_ANIMATION_START currentIndex = %{public}d, targetIndex = %{public}d",
                         currentIndex, targetIndex);
        }
    }
});
```
