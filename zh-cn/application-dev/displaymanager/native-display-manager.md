# 使用OH_DisplayManager实现屏幕基础信息查询和状态监听 (C/C++)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 场景介绍

[OH_DisplayManager](../reference/apis-arkui/capi-oh-displaymanager.md)屏幕管理模块用于提供屏幕的信息查询、屏幕状态变化监听、折叠设备的折叠状态变化监听等能力，应用可根据对应的屏幕信息、屏幕状态变化、屏幕折叠状态适配不同的UI界面显示。

- 支持查询的屏幕信息，包括屏幕的分辨率、物理像素密度、逻辑像素密度、刷新率、屏幕尺寸、屏幕旋转方向、屏幕旋转角度等。

- 支持屏幕状态变化的监听，包括屏幕旋转变化，屏幕分辨率变化、屏幕刷新率变化等。

- 支持查询当前设备是否为可折叠设备，同时支持折叠状态（展开/折叠）变化的监听。

## 基本概念

- 屏幕的物理像素密度(densityDPI)：代表每英寸屏幕所拥有的物理像素点数。

- 屏幕的逻辑像素的密度(densityPixels)：代表物理像素与逻辑像素的缩放系数比，计算方法为物理像素密度除以160。

## 接口说明

常用接口如下表所示。更多API说明请参考[OH_DisplayManager](../reference/apis-arkui/capi-oh-displaymanager.md)。

| 接口名 | 描述 |
| -------- | -------- |
| OH_NativeDisplayManager_GetDefaultDisplayRotation(NativeDisplayManager_Rotation *displayRotation) | 获取默认屏幕的旋转角度。 |
| OH_NativeDisplayManager_CreateDefaultDisplayCutoutInfo(NativeDisplayManager_CutoutInfo **cutoutInfo) | 获取挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。 |
| OH_NativeDisplayManager_DestroyDefaultDisplayCutoutInfo(NativeDisplayManager_CutoutInfo *cutoutInfo) |  销毁挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。|
| OH_NativeDisplayManager_IsFoldable()|查询设备是否可折叠。|
| OH_NativeDisplayManager_RegisterDisplayChangeListener( OH_NativeDisplayManager_DisplayChangeCallback displayChangeCallback, uint32_t *listenerIndex)|注册屏幕状态变化监听（如旋转变化、刷新率、DPI、分辨率等）。|
|OH_NativeDisplayManager_UnregisterDisplayChangeListener(uint32_t listenerIndex)|取消屏幕状态变化监听。|
|OH_NativeDisplayManager_RegisterFoldDisplayModeChangeListener( OH_NativeDisplayManager_FoldDisplayModeChangeCallback displayModeChangeCallback, uint32_t *listenerIndex)|注册屏幕展开、折叠状态变化监听。|
|OH_NativeDisplayManager_UnregisterFoldDisplayModeChangeListener(uint32_t listenerIndex)|取消屏幕展开、折叠状态变化监听。|

## 在CMake脚本中链接动态库

```
target_link_libraries(entry PUBLIC libhilog_ndk.z.so)
target_link_libraries(entry PUBLIC libnative_display_manager.so )
```

## 添加头文件

<!-- @[import_display_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample/entry/src/main/cpp/napi_init.cpp) -->

## 获取屏幕状态

1. 可以通过OH_NativeDisplayManager_GetDefaultDisplayRotation获取默认屏幕的旋转角度。

    <!-- @[get_rotation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value GetDefaultDisplayRotation(napi_env env, napi_callback_info info)
    {
        NativeDisplayManager_Rotation displayRotation;
        NativeDisplayManager_ErrorCode errCode = OH_NativeDisplayManager_GetDefaultDisplayRotation(&displayRotation);
        if (errCode == NativeDisplayManager_ErrorCode::DISPLAY_MANAGER_OK) {
            napi_value rotation;
            napi_create_int32(env, displayRotation, &rotation);
            OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "DMSTest", "rotation=%{public}d", displayRotation);
            return rotation;
        } else {
            napi_value errorCode;
            napi_create_int32(env, errCode, &errorCode);
            OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "DMSTest",
                "GetDefaultDisplayRotation errCode=%{public}d", errCode);
            return errorCode;
        }
    }
    ```

2. 可以通过OH_NativeDisplayManager_CreateDefaultDisplayCutoutInfo获取挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。 可通过OH_NativeDisplayManager_DestroyDefaultDisplayCutoutInfo销毁挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。

    <!-- @[get_cutout_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample/entry/src/main/cpp/napi_init.cpp) -->

## 监听屏幕状态变化

可以通过OH_NativeDisplayManager_RegisterDisplayChangeListener接口注册屏幕变化的监听，包括屏幕旋转、分辨率变化、刷新率变化、DPI变化等。 通过OH_NativeDisplayManager_UnregisterDisplayChangeListener接口取消屏幕状态变化的监听。

<!-- @[register_display_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample/entry/src/main/cpp/napi_init.cpp) -->

## 监听折叠设备状态变化

1. 可以通过OH_NativeDisplayManager_IsFoldable接口查询设备是不是折叠设备。

    <!-- @[get_foldable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample/entry/src/main/cpp/napi_init.cpp) -->
 

2. 可以通过OH_NativeDisplayManager_RegisterFoldDisplayModeChangeListener注册屏幕展开/折叠状态变化的监听。 通过OH_NativeDisplayManager_UnregisterFoldDisplayModeChangeListener接口取消屏幕展开/折叠状态变化的监听。

    <!-- @[register_displayMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample/entry/src/main/cpp/napi_init.cpp) -->

## 注册函数

<!-- @[register_napi_display_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample/entry/src/main/cpp/napi_init.cpp) -->

## 注册模块

<!-- @[register_display_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample/entry/src/main/cpp/napi_init.cpp) -->

## 在index.ets文件中调用函数

<!-- @[call_display_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample/entry/src/main/ets/pages/Index.ets) -->
