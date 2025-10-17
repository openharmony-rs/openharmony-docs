# NativeBundle开发指导
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

## 场景介绍

开发者可以通过本指导了解在OpenHarmony应用中，如何使用Native Bundle接口获取应用自身相关信息。

## 接口说明

常用接口如下表所示，具体API说明详见[Native_Bundle](../reference/apis-ability-kit/capi-native-bundle.md)。

| 接口名                                                       | 描述                                     |
| :----------------------------------------------------------- | :--------------------------------------- |
| [OH_NativeBundle_GetCurrentApplicationInfo](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_getcurrentapplicationinfo) | 获取应用自身相关信息。          |
| [OH_NativeBundle_GetAppId](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_getappid) | 获取自身应用的appId信息。 |
| [OH_NativeBundle_GetAppIdentifier](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_getappidentifier) | 获取自身应用的appIdentifier信息。 |
| [OH_NativeBundle_GetMainElementName](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_getmainelementname) | 获取自身应用入口的信息。 |
| [OH_NativeBundle_GetCompatibleDeviceType](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_getcompatibledevicetype) | 获取自身应用适用的设备类型。 |
| [OH_NativeBundle_IsDebugMode](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_isdebugmode) | 查询当前应用的调试模式。从API version 20开始支持。|
| [OH_NativeBundle_GetModuleMetadata](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_getmodulemetadata) | 获取当前应用的元数据信息。从API version 20开始支持。 |
| [OH_NativeBundle_GetAbilityResourceInfo](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_getabilityresourceinfo) | 获取支持打开特定文件类型的组件资源信息列表。从API version 21开始支持。 |


## 开发步骤

**1. 创建工程**

![native](figures/rawfile1.png)


**2. 添加依赖**

创建完成后，DevEco Studio会在工程生成cpp目录，目录有types/libentry/index.d.ts、napi_init.cpp、CMakeLists.txt等文件。

1. 打开src/main/cpp/CMakeLists.txt，在target_link_libraries依赖中添加包管理的libbundle_ndk.z.so。

    ```c++
    target_link_libraries(entry PUBLIC libace_napi.z.so libbundle_ndk.z.so)
    ```

2. 打开src/main/cpp/napi_init.cpp文件，添加头文件。

    <!-- @[native-bundle-guidelines_002](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/cpp/napi_init.cpp) -->

**3. 修改源文件**

1. 打开src/main/cpp/napi_init.cpp文件，文件Init会对当前方法进行初始化映射，这里定义对外的接口。

    <!-- @[native-bundle-guidelines_004](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/cpp/napi_init.cpp) -->

2. 在src/main/cpp/napi_init.cpp文件中获取Native的包信息对象，并转为js的包信息对象，即可在js侧获取应用的信息：

    <!-- @[native-bundle-guidelines_003](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/cpp/napi_init.cpp) -->

    <!-- @[native-bundle-guidelines_006](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/cpp/napi_init.cpp) -->


**4. 接口暴露**

在src/main/cpp/types/libentry/Index.d.ts文件中，声明暴露接口。

<!-- @[native-bundle-guidelines_001](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/cpp/types/libentry/Index.d.ts) -->

**5. js侧调用**

1. 打开src\main\ets\pages\index.ets, 导入"libentry.so"。


2. 调用Native接口打印出获取的信息内容。示例如下：

    <!-- @[native-bundle-guidelines_005](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/ets/pages/Index.ets) -->

关于包管理NDK接口说明，可参考[Native_Bundle模块介绍](../reference/apis-ability-kit/capi-native-bundle.md)。
