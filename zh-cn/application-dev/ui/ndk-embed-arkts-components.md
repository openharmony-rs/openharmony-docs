# 嵌入ArkTS组件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

ArkUI在Native侧提供的能力作为ArkTS的子集，部分能力不会在Native侧提供，如声明式UI语法，自定义struct组件，UI高级组件。


针对需要使用ArkTS侧独立能力的场景，ArkUI开发框架提供了Native侧嵌入ArkTS组件的能力，该能力依赖[ComponentContent](../reference/apis-arkui/js-apis-arkui-ComponentContent.md)机制，通过ComponentContent完成对ArkTS组件的封装，然后将封装对象转递到Native侧，通过Native侧的[OH_ArkUI_GetNodeHandleFromNapiValue](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnodehandlefromnapivalue)接口转化为ArkUI_NodeHandle对象用于Native侧组件挂载使用。


> **说明：**
>
> - 通过OH_ArkUI_GetNodeHandleFromNapiValue接口获得的ArkUI_NodeHandle对象只能作为子组件参数使用，如[addChild](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addchild)接口的第二个参数，将该对象使用在其他场景下，如[setAttribute](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)设置属性将不生效并返回错误码。
> 
> - 针对Native侧修改ArkTS组件的场景，需要在Native侧通过Node-API方式构建ArkTS侧的更新数据，再通过ComponentContent的[update](../reference/apis-arkui/js-apis-arkui-ComponentContent.md#update)接口更新。
> 
> - [构建自定义组件](ndk-build-custom-components.md)时，相关函数如measureNode等无法对ArkTS模块内部的组件进行调用。


以下示例代码在[接入ArkTS页面](ndk-access-the-arkts-page.md)章节基础上引入ArkTS的Refresh组件。


**图1** Refresh组件挂载文本列表

![refresh_text_list](figures/refresh_text_list.gif)


1. 注册ArkTS组件创建函数给Native侧，以便Native侧调用，创建函数使用ComponentContent能力进行封装。
   <!-- @[mixed_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkEmbedArktsComponents/entry/src/main/ets/pages/MixedModule.ets) -->

2. 将创建和更新函数注册给Native侧。
   <!-- @[page_index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkEmbedArktsComponents/entry/src/main/ets/pages/Index.ets) -->

   <!-- @[native_init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkEmbedArktsComponents/entry/src/main/cpp/NapiInit.cpp) -->

3. Native侧通过Node-API保存创建和更新函数，用于后续调用。
   ```c
   // ArkUIMixedRefresh.h
   // 混合模式交互类。
   
   #ifndef MYAPPLICATION_ARKUIMIXEDREFRESH_H
   #define MYAPPLICATION_ARKUIMIXEDREFRESH_H
   
   #include "ArkUIMixedNode.h"
   
   #include <optional>
   
   #include <arkui/native_node_napi.h>
   #include <js_native_api_types.h>
   
   namespace NativeModule {
   
   class ArkUIMixedRefresh : public ArkUIMixedNode {
   public:
       static napi_value RegisterCreateAndUpdateRefresh(napi_env env, napi_callback_info info);
   };
   
   } // namespace NativeModule
   
   #endif // MYAPPLICATION_ARKUIMIXEDREFRESH_H
   ```

   ```cpp
   // ArkUIMixedRefresh.cpp
   // 混合模式交互类。
   
   #include "ArkUIMixedRefresh.h"
   
   namespace NativeModule {
   namespace {
   napi_env g_env;
   napi_ref g_createRefresh;
   napi_ref g_updateRefresh;
   } // namespace
   
   napi_value ArkUIMixedRefresh::RegisterCreateAndUpdateRefresh(napi_env env, napi_callback_info info) {
       size_t argc = 1;
       napi_value args[1] = {nullptr};
   
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       g_env = env;
       napi_ref refer;
       // 创建引用之后保存，防止释放。
       napi_create_reference(env, args[0], 1, &refer);
   
       g_createRefresh = refer;
       return nullptr;
   }
   
   } // namespace NativeModule
   ```

   ```cpp
     # CMakeLists.txt
 
     # the minimum version of CMake.
     cmake_minimum_required(VERSION 3.4.1)
     project(testndk)
     
     # optional依赖C++17
     set(CMAKE_CXX_STANDARD 17)
     set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})
     
     include_directories(${NATIVERENDER_ROOT_PATH}
                          ${NATIVERENDER_ROOT_PATH}/include)
     
     add_library(entry SHARED NativeEntry.cpp ArkUIMixedRefresh.cpp napi_init.cpp)
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

4. 抽象混合模式下组件的基类，用于通用逻辑管理。
   <!-- @[arkui_mixed_node](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkEmbedArktsComponents/entry/src/main/cpp/ArkUIMixedNode.h) -->

5. 实现Refresh组件的混合模式封装对象。
   <!-- @[arkui_mixed_refresh](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkEmbedArktsComponents/entry/src/main/cpp/ArkUIMixedRefresh.h) -->

   相关实现类说明：

   ```c
   // ArkUIMixedRefresh.cpp

   #include "ArkUIMixedRefresh.h"
   #include <hilog/log.h>
   
   namespace NativeModule {
   namespace {
   napi_env g_env;
   napi_ref g_createRefresh;
   napi_ref g_updateRefresh;
   } // namespace
   
   // 使用Napi接口创建与ArkTS侧交互的数据结构，用于Refresh组件的创建和更新。
   napi_value ArkUIMixedRefresh::CreateRefreshAttribute(const NativeRefreshAttribute &attribute, void *userData) {
       napi_property_descriptor desc[] = {
           {"width", nullptr, nullptr, nullptr, nullptr, nullptr, napi_default, userData},
           {"height", nullptr, nullptr, nullptr, nullptr, nullptr, napi_default, userData},
           {"backgroundColor", nullptr, nullptr, nullptr, nullptr, nullptr, napi_default, userData},
           {"pullToRefresh", nullptr, nullptr, nullptr, nullptr, nullptr, napi_default, userData},
           {"isRefreshing", nullptr, nullptr, nullptr, nullptr, nullptr, napi_default, userData},
           {"refreshOffset", nullptr, nullptr, nullptr, nullptr, nullptr, napi_default, userData},
           {"onRefreshing", nullptr, nullptr, nullptr, nullptr, nullptr, napi_default, userData},
           {"onOffsetChange", nullptr, nullptr, nullptr, nullptr, nullptr, napi_default, userData},
       };
       if (attribute.width) {
           napi_value width;
           napi_create_double(g_env, attribute.width.value(), &width);
           desc[0].value = width;
       }
       if (attribute.height) {
           napi_value height;
           napi_create_double(g_env, attribute.height.value(), &height);
           desc[1].value = height;
       }
       if (attribute.backgroundColor) {
           napi_value backgroundColor;
           napi_create_uint32(g_env, attribute.backgroundColor.value(), &backgroundColor);
           desc[2].value = backgroundColor;
       }
       if (attribute.pullToRefresh) {
           napi_value pullToRefresh;
           napi_create_int32(g_env, attribute.pullToRefresh.value(), &pullToRefresh);
           desc[3].value = pullToRefresh;
       }
       if (attribute.isRefreshing) {
           napi_value isRefreshing;
           napi_create_int32(g_env, attribute.isRefreshing.value(), &isRefreshing);
           desc[4].value = isRefreshing;
       }
       if (attribute.refreshOffset) {
           napi_value refreshOffset;
           napi_create_double(g_env, attribute.refreshOffset.value(), &refreshOffset);
           desc[5].value = refreshOffset;
       }
       if (attribute.onRefreshing) {
           OH_LOG_INFO(LOG_APP, "onRefreshing start");
           desc[6].method = [](napi_env env, napi_callback_info info) -> napi_value {
               OH_LOG_INFO(LOG_APP, "onRefreshing callback");
               size_t argc = 0;
               napi_value args[0];
               void *data;
               napi_get_cb_info(env, info, &argc, args, nullptr, &data);
               auto refresh = reinterpret_cast<ArkUIMixedRefresh *>(data);
               if (refresh && refresh->attribute_.onRefreshing) {
                   refresh->attribute_.onRefreshing();
               }
               return nullptr;
           };
       }
       if (attribute.onOffsetChange) {
           OH_LOG_INFO(LOG_APP, "onOffsetChange start");
           desc[7].method = [](napi_env env, napi_callback_info info) -> napi_value {
               OH_LOG_INFO(LOG_APP, "onOffsetChange callback");
               size_t argc = 1;
               napi_value args[1] = {nullptr};
               void *data;
               napi_get_cb_info(env, info, &argc, args, nullptr, &data);
               double offset = 0.0;
               napi_get_value_double(env, args[0], &offset);
               auto refresh = reinterpret_cast<ArkUIMixedRefresh *>(data);
               if (refresh && refresh->attribute_.onOffsetChange) {
                   refresh->attribute_.onOffsetChange(offset);
               }
               return nullptr;
           };
       }
       napi_value refreshAttribute = nullptr;
       auto result = napi_create_object_with_properties(g_env, &refreshAttribute, sizeof(desc) / sizeof(desc[0]), desc);
       if (result != napi_ok) {
           return nullptr;
       }
       return refreshAttribute;
   }
   
   // 创建ArkTS侧的组件并保存在Native侧的封装对象中。
   const std::shared_ptr<ArkUIMixedRefresh> ArkUIMixedRefresh::Create(const NativeRefreshAttribute &attribute) {
       napi_handle_scope scope;
       napi_open_handle_scope(g_env, &scope);
       auto refresh = std::make_shared<ArkUIMixedRefresh>();
       auto refreshAttribute = CreateRefreshAttribute(attribute, refresh.get());
       if (refreshAttribute == nullptr) {
           napi_close_handle_scope(g_env, scope);
           return nullptr;
       }
       napi_value result = nullptr;
       napi_value argv[1] = {refreshAttribute};
       napi_value createRefresh = nullptr;
       napi_get_reference_value(g_env, g_createRefresh, &createRefresh);
       // 调用ArkTS的Create函数创建ArkTS的ComponentContent。
       napi_call_function(g_env, nullptr, createRefresh, 1, argv, &result);
   
       // 获取ArkTS的Refresh组件。
       napi_value componentContent = nullptr;
       napi_get_named_property(g_env, result, "content", &componentContent);
       ArkUI_NodeHandle handle;
       OH_ArkUI_GetNodeHandleFromNapiValue(g_env, componentContent, &handle);
       assert(handle);
       // 获取ArkTS的Refresh组件的子组件插槽。
       napi_value nodeContent = nullptr;
       napi_get_named_property(g_env, result, "childSlot", &nodeContent);
       ArkUI_NodeContentHandle contentHandle;
       OH_ArkUI_GetNodeContentFromNapiValue(g_env, nodeContent, &contentHandle);
       assert(contentHandle);
       // 保存ArkTS的ComponentContent用于防止ArkTS侧对象释放以及后续的更新。
       napi_ref componentContentRef;
       napi_create_reference(g_env, componentContent, 1, &componentContentRef);
       // 保存ArkTS的NodeContent用于防止ArkTS侧对象释放以及后续的更新。
       napi_ref nodeContentRef;
       napi_create_reference(g_env, nodeContent, 1, &nodeContentRef);
       // 更新Refresh组件相关参数。
       refresh->handle_ = handle;
       refresh->env_ = g_env;
       refresh->componentContent_ = componentContentRef;
       refresh->nodeContent_ = nodeContentRef;
       refresh->contentHandle_ = contentHandle;
       refresh->attribute_ = attribute;
       return refresh;
   }
   // 更新函数实现。
   void ArkUIMixedRefresh::FlushMixedModeCmd() {
       napi_handle_scope scope;
       napi_open_handle_scope(g_env, &scope);
       // 创建调用ArkTS接口入参。
       auto refreshAttribute = CreateRefreshAttribute(attribute_, this);
       if (refreshAttribute == nullptr) {
           napi_close_handle_scope(g_env, scope);
           return;
       }
       // 获取更新接口的剩余两个接口参数。
       napi_value componentContent = nullptr;
       napi_get_reference_value(g_env, componentContent_, &componentContent);
       napi_value nodeContent = nullptr;
       napi_get_reference_value(g_env, nodeContent_, &nodeContent);
   
       napi_value argv[3] = {componentContent, nodeContent, refreshAttribute};
       napi_value updateRefresh = nullptr;
       napi_get_reference_value(g_env, g_updateRefresh, &updateRefresh);
       // 调用ArkTS的Update函数进行更新。
       napi_value result = nullptr;
       napi_call_function(g_env, nullptr, updateRefresh, 3, argv, &result);
   }

   napi_value ArkUIMixedRefresh::RegisterCreateRefresh(napi_env env, napi_callback_info info) {
        size_t argc = 1;
        napi_value args[1] = {nullptr};

        napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

        g_env = env;
        napi_ref refer;
        napi_create_reference(env, args[0], 1, &refer);

        g_createRefresh = refer;
        return nullptr;
    }
   
   napi_value ArkUIMixedRefresh::RegisterUpdateRefresh(napi_env env, napi_callback_info info) {
       size_t argc = 1;
       napi_value args[1] = {nullptr};

       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

       g_env = env;
       napi_ref refer;
       napi_create_reference(env, args[0], 1, &refer);

       g_updateRefresh = refer;
       return nullptr;
   }
   
   } // namespace NativeModule
   
   ```

6. 定时器模块相关简单实现。
   <!-- @[ui_timer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkEmbedArktsComponents/entry/src/main/cpp/UITimer.h) -->

7. 使用[接入ArkTS页面](ndk-access-the-arkts-page.md)章节的页面结构，并沿用[定时器模块相关简单实现](ndk-embed-arkts-components.md)，将Refresh组件作为文本列表的父组件。
   <!-- @[mixed_refresh_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkEmbedArktsComponents/entry/src/main/cpp/MixedRefreshExample.h) -->

   替换入口组件创建为下拉刷新文本列表。

   <!-- @[native_entry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkEmbedArktsComponents/entry/src/main/cpp/NativeEntry.cpp) -->

8. 在Native侧提供Node-API的桥接方法，实现ArkTS侧的NativeNode模块接口。 
   <!-- @[bridge_index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkEmbedArktsComponents/entry/src/main/cpp/types/libentry/Index.d.ts) -->
