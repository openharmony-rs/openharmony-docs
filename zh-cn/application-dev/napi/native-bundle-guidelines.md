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

``` C++
// napi依赖头文件
#include "napi/native_api.h"
// native接口依赖头文件
#include "bundle/ability_resource_info.h"
#include "bundle/native_interface_bundle.h"
// free()函数依赖的基础库
#include <cstdlib>
```


**3. 修改源文件**

1. 打开src/main/cpp/napi_init.cpp文件，文件Init会对当前方法进行初始化映射，这里定义对外的接口。

    <!-- @[native-bundle-guidelines_004](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/cpp/napi_init.cpp) -->

``` C++
EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        { "add", nullptr, Add, nullptr, nullptr, nullptr, napi_default, nullptr },
        // 新增方法getCurrentApplicationInfo
        { "getCurrentApplicationInfo", nullptr, GetCurrentApplicationInfo, nullptr,
            nullptr, nullptr, napi_default, nullptr},
        // 新增方法getAppId
        { "getAppId", nullptr, GetAppId, nullptr, nullptr, nullptr, napi_default, nullptr},
        // 新增方法getAppIdentifier
        { "getAppIdentifier", nullptr, GetAppIdentifier, nullptr, nullptr, nullptr, napi_default, nullptr},
        // 新增方法getMainElementName
        { "getMainElementName", nullptr, GetMainElementName, nullptr, nullptr, nullptr, napi_default, nullptr},
        // 新增方法getCompatibleDeviceType
        { "getCompatibleDeviceType", nullptr, GetCompatibleDeviceType, nullptr,
            nullptr, nullptr, napi_default, nullptr},
        // 新增方法isDebugMode
        { "isDebugMode", nullptr, IsDebugMode, nullptr, nullptr, nullptr, napi_default, nullptr},
        // 新增方法getModuleMetadata
        { "getModuleMetadata", nullptr, GetModuleMetadata, nullptr, nullptr, nullptr, napi_default, nullptr},
        // 新增方法getAbilityResourceInfo
        { "getAbilityResourceInfo", nullptr, GetAbilityResourceInfo, nullptr, nullptr, nullptr, napi_default, nullptr}
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END
```


2. 在src/main/cpp/napi_init.cpp文件中获取Native的包信息对象，并转为js的包信息对象，即可在js侧获取应用的信息：

<!-- @[native-bundle-guidelines_003](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/cpp/napi_init.cpp) -->


<!-- @[native-bundle-guidelines_006](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/cpp/napi_init.cpp) -->


**4. 接口暴露**

在src/main/cpp/types/libentry/Index.d.ts文件中，声明暴露接口。

<!-- @[native-bundle-guidelines_001](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const add: (a: number, b: number) => number;
export const getCurrentApplicationInfo: () => object;   // 新增暴露方法 getCurrentApplicationInfo
export const getAppId: () => string;                    // 新增暴露方法 getAppId
export const getAppIdentifier: () => string;            // 新增暴露方法 getAppIdentifier
export const getMainElementName: () => object;          // 新增暴露方法 getMainElementName
export const getCompatibleDeviceType: () => string;     // 新增暴露方法 getCompatibleDeviceType
export const isDebugMode: () => string;                 // 新增暴露方法 isDebugMode
export const getModuleMetadata: () => object;           // 新增暴露方法 getModuleMetadata
export const getAbilityResourceInfo: (fileType: string) => object;      // 新增暴露方法 getAbilityResourceInfo
```


**5. js侧调用**

1. 打开src\main\ets\pages\index.ets, 导入"libentry.so"。


2. 调用Native接口打印出获取的信息内容。示例如下：

    <!-- @[native-bundle-guidelines_005](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/NativeBundleGuidelines/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';

const DOMAIN = 0x0000;

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize($r('app.float.page_text_font_size'))
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            this.message = 'Welcome';
            hilog.info(DOMAIN, 'testTag', 'Test NAPI 2 + 3 = %{public}d', testNapi.add(2, 3));
            let appInfo = testNapi.getCurrentApplicationInfo();
            console.info("bundleNative getCurrentApplicationInfo success, data is " + JSON.stringify(appInfo));
            let appId = testNapi.getAppId();
            console.info("bundleNative getAppId success, appId is " + appId);
            let appIdentifier = testNapi.getAppIdentifier();
            console.info("bundleNative getAppIdentifier success, appIdentifier is " + appIdentifier);
            let mainElement = testNapi.getMainElementName();
            console.info("bundleNative getMainElementName success, data is " + JSON.stringify(mainElement));
            let deviceType = testNapi.getCompatibleDeviceType();
            console.info("bundleNative getCompatibleDeviceType success, deviceType is " + deviceType);
            let isDebugMode = testNapi.isDebugMode();
            console.info("bundleNative isDebugMode success, isDebugMode is " + isDebugMode);
            let moduleMetadata = testNapi.getModuleMetadata();
            console.info("bundleNative getModuleMetadata success, data is " + JSON.stringify(moduleMetadata));
            let fileType: string = '.png';
            let abilityResourceInfo = testNapi.getAbilityResourceInfo(fileType);
            console.info("bundleNative getAbilityResourceInfo success, data is " + JSON.stringify(abilityResourceInfo));
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```


关于包管理NDK接口说明，可参考[Native_Bundle模块介绍](../reference/apis-ability-kit/capi-native-bundle.md)。
