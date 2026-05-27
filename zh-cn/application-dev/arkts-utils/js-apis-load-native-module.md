# 同步方式动态加载Native模块
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @HelloCrease-->

[loadNativeModule (同步动态加载系统库接口)](../reference/common/js-apis-common-load-native-module.md)用于同步动态加载Native模块，目的是按需加载所需要的模块。使用该接口会增加加载so文件的时间，开发者需评估其对功能的影响。

## 函数说明

```js
loadNativeModule(moduleName: string): Object;
```

| 参数            | 说明          |
| :------------- | :----------------------------- |
| moduleName            | 加载的模块名。       |

> **说明**
> loadNativeModule加载的模块名是指依赖方oh-package.json5文件的dependencies中的名字。
>
> loadNativeModule必须在UI主线程中调用。
>
> 该接口在加载常量字符串或变量表达式作为参数时，需要配置依赖。

## loadNativeModule支持的场景

| 场景            | 示例           | 
| :------------- | :----------------------------- | 
| 系统库模块        | 加载@ohos.或@system.        | 
| 应用内Native模块  | 加载libNativeLibrary.so |

## 使用示例

- **HAP加载系统库模块**

<!-- @[hap_load_system_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/src/main/ets/pages/Index.ets) --> 

``` TypeScript
// HAP加载系统库模块
let hilog: ESObject = loadNativeModule('@ohos.hilog');
hilog.info(0, 'testTag', 'loadNativeModule ohos.hilog success');
```

- **HAP加载Native库**

libentry.so的index.d.ts文件如下：

<!-- @[hap_load_native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/src/main/cpp/types/libentry/index.d.ts) -->

``` TypeScript
export const add: (a: number, b: number) => number;
```

1.加载本地so库时，需要在oh-package.json5文件中配置dependencies项。

<!-- @[hap_load_native_dependence](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/oh-package.json5) -->

``` JSON5
"dependencies": {
  "libentry.so": "file:./src/main/cpp/types/libentry"
},
```

2.在build-profile.json5中进行配置。

<!-- @[hap_load_native_dependence_01](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/build-profile.json5) -->

``` JSON5
"buildOption": {
  "arkOptions": {
    "runtimeOnly": {
      "packages": [
        "libentry.so"
      ]
    }
  },
  // ...
},
```

3.使用loadNativeModule加载libentry.so，并调用add函数。

<!-- @[load_native_module_libentry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
//HAP加载Native库
let module: ESObject = loadNativeModule('libentry.so');
let sum: number = module.add(1, 2);
```
