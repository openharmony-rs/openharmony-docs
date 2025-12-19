# NativeDisplaySoloist开发指导 (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hudi33-->
<!--Designer: @hudi33-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

如果开发者想在独立线程中实现帧率控制的Native侧业务，可以通过DisplaySoloist来实现，如游戏、自绘制UI框架对接等场景。
开发者可以选择多个DisplaySoloist实例共享一个线程，也可以选择每个DisplaySoloist实例独占一个线程。

## 接口说明

| 函数名称                                                     | 说明                                                  |
| ------------------------------------------------------------ | ----------------------------------------------------- |
| OH_DisplaySoloist* OH_DisplaySoloist_Create (bool useExclusiveThread) | 创建一个OH_DisplaySoloist实例。                       |
| OH_DisplaySoloist_Destroy (OH_DisplaySoloist * displaySoloist) | 销毁一个OH_DisplaySoloist实例。                       |
| OH_DisplaySoloist_Start (OH_DisplaySoloist * displaySoloist, OH_DisplaySoloist_FrameCallback callback, void * data ) | 设置每帧回调函数，每次VSync信号到来时启动每帧回调。   |
| OH_DisplaySoloist_Stop (OH_DisplaySoloist * displaySoloist)  | 停止请求下一次VSync信号，并停止调用回调函数callback。 |
| OH_DisplaySoloist_SetExpectedFrameRateRange (OH_DisplaySoloist* displaySoloist, DisplaySoloist_ExpectedRateRange* range) | 设置期望帧率范围。                                    |

详细的接口说明请参考[NativeDisplaySoloist](../reference/apis-arkgraphics2d/capi-nativedisplaysoloist.md)。

## 开发示例

   本范例是通过Drawing在Native侧实现图形的绘制，通过异步线程设置期望的帧率，再根据帧率进行图形的绘制并将其呈现在NativeWindow上，图形绘制部分可参考[使用Drawing实现图形绘制与显示](graphic-drawing-overview.md)。

### 添加开发依赖

**添加动态链接库**

CMakeLists.txt中添加以下lib。
<!-- @[display_soloist_add_lib](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/cpp/CMakeLists.txt) -->

``` Text
target_link_libraries(entry PUBLIC libace_napi.z.so libnative_drawing.so libnative_window.so libace_ndk.z.so libnative_display_soloist.so)
```

**头文件**
<!-- @[display_soloist_import_module_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/cpp/samples/sample_xcomponent.h) -->

``` C
#include <ace/xcomponent/native_interface_xcomponent.h>
#include <arpa/nameser.h>
#include <bits/alltypes.h>
#include <native_window/external_window.h>
#include <native_drawing/drawing_bitmap.h>
#include <native_drawing/drawing_color.h>
#include <native_drawing/drawing_canvas.h>
#include <native_drawing/drawing_pen.h>
#include <native_drawing/drawing_brush.h>
#include <native_drawing/drawing_path.h>
#include <cstdint>
#include <map>
#include <sys/mman.h>
#include <string>
#include "napi/native_api.h"
```
<!-- @[display_soloist_import_module_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/cpp/samples/sample_xcomponent.cpp) -->

``` C++
#include <native_display_soloist/native_display_soloist.h>
```

### 开发步骤

1. 定义ArkTS接口文件XComponentContext.ts，用来对接Native层。
   <!-- @[display_soloist_export_interface_xcomponent_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/ets/interface/XComponentContext.ts) -->

2. 定义演示页面，包含两个XComponent组件。
   <!-- @[display_soloist_create_xcomponent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/ets/pages/Index.ets) -->

3. 在 Native C++层获取NativeXComponent。建议使用单例模式保存XComponent。此步骤需要在napi_init的过程中处理。

    创建一个PluginManger单例类，用于管理NativeXComponent。
   <!-- @[display_soloist_create_plugin_manager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/cpp/plugin/plugin_manager.h) -->

   SampleXComponent类会在后面的绘制图形中创建。
   <!-- @[display_soloist_export_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/cpp/plugin/plugin_manager.cpp) -->

4. Native层配置帧率和注册回调函数。

   定义每帧回调函数内容。
   <!-- @[display_soloist_frame_rate_setting_and_subscription_function_registration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/cpp/samples/sample_xcomponent.cpp) -->

   使用DisplaySoloist接口配置帧率和注册每帧回调函数。如果使用OH_DisplaySoloist_Create创建DisplaySoloist实例时传入的参数useExclusiveThread为true，则OH_DisplaySoloist_FrameCallback以独占线程方式执行，否则OH_DisplaySoloist_FrameCallback以共享线程方式执行。

   > **说明：**
   >
   > - 实例在调用NapiRegister后，在不需要进行帧率控制时，应进行NapiUnregister操作，避免内存泄漏问题。
   > - 在页面跳转时，应进行NapiUnregister和NapiDestroy操作，避免内存泄漏问题。
   <!-- @[display_soloist_napi_register_and_unregister](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/cpp/samples/sample_xcomponent.cpp) -->

5. TS层注册和取消注册每帧回调，销毁OH_DisplaySoloist实例。
   <!-- @[display_soloist_disappear](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySoloist/entry/src/main/ets/pages/Index.ets) -->

<!--RP1-->
## 相关实例

针对可变帧率的开发，有以下相关实例可供参考：

- [DisplaySoloist分级管控 (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/DisplaySoloist)
<!--RP1End-->