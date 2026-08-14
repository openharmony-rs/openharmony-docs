# Using the Arc Swiper Container (ArcSwiper)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @Hu_ZeQi-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=12affbed96c04ca63a8278f9eaa693d54cc02401 translatedAt=2026-08-05T01:27:53.147Z pushedAt=2026-08-05T06:14:48.668Z -->

## Overview

The ArkUI development framework supports using the arc swiper container **ArcSwiper** through NDK APIs, providing the ability to display child components in a swipe carousel, suitable for circular screen scenarios such as wearable devices. This document introduces the development guide for NDK APIs. For the ArkTS guide, see [Creating an Arc Swiper (ArcSwiper)](arkts-layout-development-arcswiper.md).

For building UIs using NDK APIs and basic NDK usage, refer to [Integrating with ArkTS Pages](ndk-access-the-arkts-page.md). After the page is built and the [Creating an ArcSwiper](#creating-an-arcswiper), you can optimize the page display by [Setting Common Attributes](#setting-common-attributes) and [Setting the Arc Navigation Point Indicator](#setting-the-arc-navigation-point-indicator). When pages switch, you can obtain page switching information by [Listening for Events](#listening-for-events).

## Creating an ArcSwiper

In this example, a UI component node of the **ARKUI_NODE_ARC_SWIPER** type is created by calling [createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode) for subsequent operations such as setting attributes. Multiple **Text** components are mounted under the **ArcSwiper** component as carousel page content through [addChild](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addchild).

This example only shows the core function code. For the complete example, see the project <!--RP1-->[NDKArcSwiperSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKArcSwiperSample)<!--RP1End-->.

<!-- @[arc_swiper_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKArcSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->

``` C++
ArkUI_NativeNodeAPI_1 *nodeApi = nullptr;
OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, nodeApi);
ArkUI_NodeHandle arcSwiper = nodeApi->createNode(ARKUI_NODE_ARC_SWIPER);
AddChild(arcSwiper, nodeApi);
```

## Setting Common Attributes

This example adjusts the ArcSwiper page display and interaction effects by setting attributes in [ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype). The common attributes are as follows:

| Enum Item | Description |
|---------|----------|
| NODE_WIDTH_PERCENT | Component width percentage. |
| NODE_HEIGHT_PERCENT | Component height percentage. |
| NODE_ARC_SWIPER_INDEX | Index of the currently displayed child component. |
| NODE_ARC_SWIPER_DURATION | Animation duration for child component switching, in milliseconds. |
| NODE_ARC_SWIPER_VERTICAL | Whether to swipe vertically. |
| NODE_ARC_SWIPER_DISABLE_SWIPE | Whether to disable the swipe switching feature. |
| NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY | Sensitivity of the rotating crown. The parameter type is [ArkUI_CrownSensitivity](../reference/apis-arkui/capi-native-type-h.md#arkui_crownsensitivity). |
| NODE_ARC_SWIPER_EFFECT_MODE | Edge swipe effect when swiping to the boundary of scrollable content. The parameter type is [ArkUI_EdgeEffect](../reference/apis-arkui/capi-scroll-h.md#arkui_edgeeffect). |
| NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION | Whether to disable the transition animation. |

This example only shows the core function code. For the complete example, see the project <!--RP1-->[NDKArcSwiperSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKArcSwiperSample)<!--RP1End-->.

<!-- @[arc_swiper_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKArcSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->

``` C++
ArkUI_NumberValue value[] = {0};
ArkUI_AttributeItem item = {.value = value, .size = 1};

value[0].f32 = ARC_SWIPER_HEIGHT_PERCENT;
nodeApi->setAttribute(arcSwiper, NODE_HEIGHT_PERCENT, &item);
value[0].f32 = ARC_SWIPER_WIDTH_PERCENT;
nodeApi->setAttribute(arcSwiper, NODE_WIDTH_PERCENT, &item);

value[0].i32 = 0;
nodeApi->setAttribute(arcSwiper, NODE_ARC_SWIPER_INDEX, &item);
value[0].i32 = ARC_SWIPER_DURATION;
nodeApi->setAttribute(arcSwiper, NODE_ARC_SWIPER_DURATION, &item);
value[0].i32 = 0;
nodeApi->setAttribute(arcSwiper, NODE_ARC_SWIPER_VERTICAL, &item);
nodeApi->setAttribute(arcSwiper, NODE_ARC_SWIPER_DISABLE_SWIPE, &item);
nodeApi->setAttribute(arcSwiper, NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION, &item);
value[0].i32 = ARKUI_CROWN_SENSITIVITY_MEDIUM;
nodeApi->setAttribute(arcSwiper, NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY, &item);
value[0].i32 = ARKUI_EDGE_EFFECT_SPRING;
nodeApi->setAttribute(arcSwiper, NODE_ARC_SWIPER_EFFECT_MODE, &item);

ArkUI_NumberValue indicatorValue[] = {
    {.i32 = 1},
    {.i32 = OH_ARKUI_ARCDIRECTION_SIX_CLOCK_DIRECTION},
    {.u32 = INDICATOR_COLOR},
    {.u32 = INDICATOR_SELECTED_COLOR},
    {.u32 = INDICATOR_BACKGROUND_COLOR},
};
ArkUI_AttributeItem indicatorItem = {.value = indicatorValue, .size = 5};
nodeApi->setAttribute(arcSwiper, NODE_ARC_SWIPER_INDICATOR, &indicatorItem);
```

## Setting the Arc Navigation Point Indicator

This example controls the display state, direction, unselected color, selected color, and long-press background color of the arc navigation point indicator by setting the **NODE_ARC_SWIPER_INDICATOR** attribute. The navigation point direction uses the **OH_ArkUI_ArcDirection** enumeration, which supports the 3 o'clock, 6 o'clock, and 9 o'clock directions.

| Enum Item | Description |
|---------|----------|
| OH_ARKUI_ARCDIRECTION_THREE_CLOCK_DIRECTION | 3 o'clock direction. |
| OH_ARKUI_ARCDIRECTION_SIX_CLOCK_DIRECTION | 6 o'clock direction. |
| OH_ARKUI_ARCDIRECTION_NINE_CLOCK_DIRECTION | 9 o'clock direction. |

For the related code, refer to the **arc_swiper_attribute** code snippet in [Setting Common Attributes](#setting-common-attributes). To set the navigation point mask gradient color, pass the [ArkUI_ColorStop](../reference/apis-arkui/capi-arkui-nativemodule-arkui-colorstop.md) object through the **object** field of **ArkUI_AttributeItem**.

## Listening for Events

In this example, the event types [ArkUI_NodeEventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype) supported by the **ArcSwiper** component are registered through [registerNodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent). In the listener callback registered through [registerNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver), you can determine the callback type and parse the corresponding callback content. The callbacks involved are as follows:

| Enum Item | Description |
|---------|----------|
| NODE_ARC_SWIPER_EVENT_ON_CHANGE | Index of the page displayed after the page index switches. |
| NODE_ARC_SWIPER_EVENT_ON_ANIMATION_START | Index of the currently displayed page, target page index, current page offset, target page offset, and the swipe velocity when the page switching animation starts. |
| NODE_ARC_SWIPER_EVENT_ON_ANIMATION_END | Index of the currently displayed page and current page offset when the page switching animation ends. |
| NODE_ARC_SWIPER_EVENT_ON_GESTURE_SWIPE | Index of the currently displayed page and the current page offset. This item is triggered frame by frame during finger-following page swiping. |

This example only shows the core function code. For the complete example, see the project <!--RP1-->[NDKArcSwiperSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKArcSwiperSample)<!--RP1End-->.

<!-- @[arc_swiper_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKArcSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->

``` C++
nodeApi->registerNodeEvent(arcSwiper, NODE_ARC_SWIPER_EVENT_ON_CHANGE, 0, nullptr);  // 0: onChange event ID.
nodeApi->registerNodeEvent(arcSwiper, NODE_ARC_SWIPER_EVENT_ON_ANIMATION_START, 1, nullptr);  // 1: Animation start event ID.
nodeApi->registerNodeEvent(arcSwiper, NODE_ARC_SWIPER_EVENT_ON_ANIMATION_END, 2, nullptr);  // 2: Animation end event ID.
nodeApi->registerNodeEvent(arcSwiper, NODE_ARC_SWIPER_EVENT_ON_GESTURE_SWIPE, 3, nullptr);  // 3: gesture swipe event ID.
nodeApi->registerNodeEventReceiver([](ArkUI_NodeEvent *event) {
    ArkUI_NodeEventType eventType = OH_ArkUI_NodeEvent_GetEventType(event);
    auto componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
    if (!componentEvent) {
        return;
    }

    if (eventType == NODE_ARC_SWIPER_EVENT_ON_CHANGE) {
        auto index = componentEvent->data[0].i32;
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "ArcSwiper",
                     "NODE_ARC_SWIPER_EVENT_ON_CHANGE index = %{public}d", index);
    }
    if (eventType == NODE_ARC_SWIPER_EVENT_ON_ANIMATION_START) {
        auto currentIndex = componentEvent->data[0].i32;
        auto targetIndex = componentEvent->data[1].i32;
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "ArcSwiper",
                     "NODE_ARC_SWIPER_EVENT_ON_ANIMATION_START currentIndex = %{public}d, "
                     "targetIndex = %{public}d",
                     currentIndex, targetIndex);
    }
    if (eventType == NODE_ARC_SWIPER_EVENT_ON_ANIMATION_END) {
        auto index = componentEvent->data[0].i32;
        auto offset = componentEvent->data[1].f32;
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "ArcSwiper",
                     "NODE_ARC_SWIPER_EVENT_ON_ANIMATION_END index = %{public}d, offset = %{public}f",
                     index, offset);
    }
    if (eventType == NODE_ARC_SWIPER_EVENT_ON_GESTURE_SWIPE) {
        auto index = componentEvent->data[0].i32;
        auto offset = componentEvent->data[1].f32;
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "ArcSwiper",
                     "NODE_ARC_SWIPER_EVENT_ON_GESTURE_SWIPE index = %{public}d, offset = %{public}f",
                     index, offset);
    }
});
```