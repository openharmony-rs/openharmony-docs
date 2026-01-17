# 自定义Native Sendable对象的多线程操作场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS支持开发者自定义Native Sendable对象，Sendable对象提供了并发实例间高效的通信能力，即引用传递，适用于开发者自定义大对象需要线程间通信的场景，例如子线程读取数据库数据并返回给宿主线程。

本示例将详细说明如何使用自定义Native Sendable对象实现并发实例间数据共享。

1. 接口声明中自定义Sendable类。

   <!-- @[export_myObject](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCaseSendable/entry/src/main/cpp/types/libentry/Index.d.ets) -->  

2. 编译配置。

    ```cmake
    # CMakeLists.txt
    # the minimum version of CMake.
    cmake_minimum_required(VERSION 3.5.0)
    project(napi_wrap_sendable_demo)

    set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})

    if(DEFINED PACKAGE_FIND_FILE)
        include(${PACKAGE_FIND_FILE})
    endif()

    include_directories(${NATIVERENDER_ROOT_PATH}
                        ${NATIVERENDER_ROOT_PATH}/include)

    add_definitions("-DLOG_DOMAIN=0x0000")
    add_definitions("-DLOG_TAG=\"testTag\"")

    add_library(entry SHARED napi_init.cpp)
    target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so)
    ```

3. Native实现各项接口功能，例如取值、设置值或者给Native对象的值加1等功能。

   <!-- @[init_sendable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCaseSendable/entry/src/main/cpp/napi_init.cpp) -->  

4. ArkTS侧在UI主线程中定义Sendable实例对象并传递给TaskPool子线程，子线程处理完数据后返回UI主线程，UI主线程可以继续访问该Sendable实例对象。

   <!-- @[load_nativeSendable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCaseSendable/entry/src/main/ets/pages/Indx.ets) -->    

5. 修改与Index.d.ets同目录下的配置文件oh-package.json5，配置如下：

   <!-- @[define_libentry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCaseSendable/entry/src/main/cpp/types/libentry/oh-package.json5) -->    

