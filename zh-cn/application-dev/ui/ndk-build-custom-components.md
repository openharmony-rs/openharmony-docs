# 构建自定义组件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

ArkUI开发框架在NDK接口提供了自定义UI组件的能力，这些能力包括自定义测算，自定义布局和自定义绘制。开发者通过注册相关自定义回调事件接入ArkUI开发框架的布局渲染流程，这些事件需要使用[registerNodeCustomEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodecustomevent)来进行声明，并通过[addNodeCustomEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodecustomeventreceiver)函数添加组件自定义事件的监听器，在该监听器的回调函数中处理相关自定义测算，自定义布局和自定义绘制逻辑。


> **说明：**
>
> - 自定义组件事件注册需要[addNodeCustomEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodecustomeventreceiver)声明监听器注册和[registerNodeCustomEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodecustomevent)声明需要的自定义事件类型，监听器只能监听已声明的事件。
> 
> - 需要关注事件的反注册逻辑，如在组件销毁前调用[removeNodeCustomEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#removenodecustomeventreceiver)移除事件监听器，[unregisterNodeCustomEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#unregisternodecustomevent)通知ArkUI框架已监听的自定义组件事件不再需要监听。
> 
> - [addNodeCustomEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodecustomeventreceiver)可以添加多个函数指针，每个函数指针都会在对应事件触发时触发，对应的[removeNodeCustomEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#removenodecustomeventreceiver)需要传递对应的函数指针用于移除监听。
> 
> - [registerNodeCustomEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodecustomeventreceiver)是全局监听函数，不同于[addNodeCustomEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodecustomeventreceiver)，[registerNodeCustomEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodecustomeventreceiver)能够监听所有Native组件的自定义事件触发，但只能传递一个函数指针，多次调用使用最后一次的函数指针进行回调，释放时使用unregisterNodeCustomEventReceiver进行反注册。
> 
> - 自定义组件相关接口（[measureNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#measurenode)、[layoutNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#layoutnode)、[setMeasuredSize](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setmeasuredsize)、[setLayoutPosition](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlayoutposition)）仅允许在对应的自定义事件（[ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE、ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT](../reference/apis-arkui/capi-native-node-h.md#arkui_nodecustomeventtype)）回调中使用。


## 自定义布局容器

以下示例创建了一个自定义容器，该容器将子组件最大值加上额外边距作为自身大小，同时对子组件进行居中排布。

**图1** 自定义容器组件

![customContainer](figures/customContainer.png)

1. 按照[接入ArkTS页面](ndk-access-the-arkts-page.md)创建前置工程。

2. 创建自定义容器组件封装对象。
   <!-- @[custom-components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomContainerSample/entry/src/main/cpp/ArkUICustomContainerNode.h) -->

3. 使用自定义容器创建带文本的示例界面，并沿用[定时器模块相关简单实现](ndk-embed-arkts-components.md)。
   <!-- @[entrance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomContainerSample/entry/src/main/cpp/NativeEntry.cpp) -->

4. 修改CMakeList.txt，添加链接库。
   ```cpp
     # CMakeLists.txt

     # the minimum version of CMake.
     cmake_minimum_required(VERSION 3.4.1)
     project(testndk)

     set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})

     include_directories(${NATIVERENDER_ROOT_PATH}
                          ${NATIVERENDER_ROOT_PATH}/include)

     add_library(entry SHARED NativeEntry.cpp napi_init.cpp)
     # target_link_libraries(entry PUBLIC libace_napi.z.so, libace_ndk.z.so, libhilog_ndk.z.so)

     find_library(
          # Sets the name of the path variable.
          hilog-lib
          # Specifies the name of the NDK library that
          # you want CMake to locate.
          hilog_ndk.z
      )

     find_library(
          # Sets the name of the path variable.
          libace-lib
          # Specifies the name of the NDK library that
          # you want CMake to locate.
          ace_ndk.z
      )

     find_library(
          # Sets the name of the path variable.
          libnapi-lib
          # Specifies the name of the NDK library that
          # you want CMake to locate.
          ace_napi.z
      )

      find_library(
           # Sets the name of the path variable.
           libuv-lib
           uv
       )

     target_link_libraries(entry PUBLIC
          ${hilog-lib} ${libace-lib} ${libnapi-lib} ${libuv-lib} )
   ```

## 自定义绘制组件

以下示例创建了一个自定义绘制组件，该绘制组件能够绘制自定义矩形，并使用上述自定义容器进行布局排布。

**图2** 自定义绘制组件
 
![customNode](figures/customNode.png)

1. 按照[自定义布局容器](#自定义布局容器)章节准备前置工程。

2. 创建自定义绘制组件封装对象。
   <!-- @[custom-draw](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomDrawSample/entry/src/main/cpp/ArkUICustomNode.h) -->

3. 使用自定义绘制组件和自定义容器创建示例界面，并沿用[定时器模块相关简单实现](ndk-embed-arkts-components.md)。
   <!-- @[entrance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomDrawSample/entry/src/main/cpp/NativeEntry.cpp) -->

4. 修改CMakeList.txt，添加链接库。
   ```cpp
     # CMakeLists.txt

     # the minimum version of CMake.
     cmake_minimum_required(VERSION 3.4.1)
     project(testndk)

     set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})

     include_directories(${NATIVERENDER_ROOT_PATH}
                          ${NATIVERENDER_ROOT_PATH}/include)

     add_library(entry SHARED NativeEntry.cpp napi_init.cpp)
     # target_link_libraries(entry PUBLIC libace_napi.z.so, libace_ndk.z.so, libhilog_ndk.z.so)

     find_library(
          # Sets the name of the path variable.
          hilog-lib
          # Specifies the name of the NDK library that
          # you want CMake to locate.
          hilog_ndk.z
      )

     find_library(
          # Sets the name of the path variable.
          libace-lib
          # Specifies the name of the NDK library that
          # you want CMake to locate.
          ace_ndk.z
      )

     find_library(
          # Sets the name of the path variable.
          libnapi-lib
          # Specifies the name of the NDK library that
          # you want CMake to locate.
          ace_napi.z
      )

      find_library(
           # Sets the name of the path variable.
           libuv-lib
           uv
       )

     target_link_libraries(entry PUBLIC
          ${hilog-lib} ${libace-lib} ${libnapi-lib} ${libuv-lib} libnative_drawing.so)
   ```