# 使用弧形滑块视图容器 (ArcSwiper)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @Hu_ZeQi-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

ArkUI开发框架支持在NDK接口使用弧形滑块视图容器ArcSwiper，提供子组件滑动轮播显示的能力，适用于可穿戴设备等圆形屏幕场景。本文介绍NDK接口的开发指导，ArkTS指南请参考[创建弧形轮播 (ArcSwiper)](arkts-layout-development-arcswiper.md)。

使用NDK接口构建UI界面以及NDK基本使用，可以参考[接入ArkTS页面](ndk-access-the-arkts-page.md)。页面构建完成[创建ArcSwiper](#创建arcswiper)后，可以通过[设置常用属性](#设置常用属性)和[设置弧形导航点指示器](#设置弧形导航点指示器)优化页面显示效果，页面切换时可以通过[监听事件](#监听事件)获取页面切换信息。

## 创建ArcSwiper

本示例通过调用[createNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode)创建ARKUI_NODE_ARC_SWIPER类型的UI组件节点，用于后续设置属性等操作。并通过[addChild](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addchild)在ArcSwiper组件下挂载多个Text文本组件，作为轮播页面内容。

本示例仅展示核心功能代码，完整示例请参考工程<!--RP1-->[NDKArcSwiperSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKArcSwiperSample)<!--RP1End-->。

<!-- @[arc_swiper_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKArcSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->

## 设置常用属性

本示例通过设置[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)中的属性调整ArcSwiper页面显示和交互效果，常见的属性如下：

| 枚举项 | 描述 |
|---------|----------|
| NODE_WIDTH_PERCENT | 组件宽度百分比。 |
| NODE_HEIGHT_PERCENT | 组件高度百分比。 |
| NODE_ARC_SWIPER_INDEX | 当前显示的子组件索引。 |
| NODE_ARC_SWIPER_DURATION | 子组件切换的动画时长，单位为毫秒。 |
| NODE_ARC_SWIPER_VERTICAL | 是否为纵向滑动。 |
| NODE_ARC_SWIPER_DISABLE_SWIPE | 是否禁用滑动切换功能。 |
| NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY | 转动表冠的灵敏度，参数类型为[ArkUI_CrownSensitivity](../reference/apis-arkui/capi-native-type-h.md#arkui_crownsensitivity)。 |
| NODE_ARC_SWIPER_EFFECT_MODE | 滑动到可滚动内容边界时的边缘滑动效果，参数类型为[ArkUI_EdgeEffect](../reference/apis-arkui/capi-scroll-h.md#arkui_edgeeffect)。 |
| NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION | 是否禁用转场动画。 |

本示例仅展示核心功能代码，完整示例请参考工程<!--RP1-->[NDKArcSwiperSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKArcSwiperSample)<!--RP1End-->。

<!-- @[arc_swiper_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKArcSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->

## 设置弧形导航点指示器

本示例通过设置NODE_ARC_SWIPER_INDICATOR属性控制弧形导航点指示器的显示状态、方向、未选中颜色、选中颜色和长按后的背景颜色。其中，导航点方向使用OH_ArkUI_ArcDirection枚举，支持3点钟、6点钟和9点钟方向。

| 枚举项 | 描述 |
|---------|----------|
| OH_ARKUI_ARCDIRECTION_THREE_CLOCK_DIRECTION | 3点钟方向。 |
| OH_ARKUI_ARCDIRECTION_SIX_CLOCK_DIRECTION | 6点钟方向。 |
| OH_ARKUI_ARCDIRECTION_NINE_CLOCK_DIRECTION | 9点钟方向。 |

相关代码请参考[设置常用属性](#设置常用属性)中的arc_swiper_attribute代码片段。如需设置导航点遮罩渐变颜色，可将[ArkUI_ColorStop](../reference/apis-arkui/capi-arkui-nativemodule-arkui-colorstop.md)对象通过ArkUI_AttributeItem的object字段传入。

## 监听事件

本示例通过[registerNodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)注册ArcSwiper组件支持的事件类型[ArkUI_NodeEventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)，开发者可以在[registerNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver)注册的监听回调中，判断回调类型并解析对应的回调内容。涉及的回调如下：

| 枚举项 | 描述 |
|---------|----------|
| NODE_ARC_SWIPER_EVENT_ON_CHANGE | 页面索引切换后显示的页面索引。 |
| NODE_ARC_SWIPER_EVENT_ON_ANIMATION_START | 页面切换动画开始时，当前显示页面的索引、目标页面索引、当前页面位移、目标页面位移和离手速度。 |
| NODE_ARC_SWIPER_EVENT_ON_ANIMATION_END | 页面切换动画结束时，当前显示页面的索引和当前页面位移。 |
| NODE_ARC_SWIPER_EVENT_ON_GESTURE_SWIPE | 页面跟手滑动过程中逐帧触发，返回当前显示页面的索引和当前页面位移。 |

本示例仅展示核心功能代码，完整示例请参考工程<!--RP1-->[NDKArcSwiperSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKArcSwiperSample)<!--RP1End-->。

<!-- @[arc_swiper_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKArcSwiperSample/entry/src/main/cpp/NativeEntry.cpp) -->
