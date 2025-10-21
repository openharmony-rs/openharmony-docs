# 事件拦截开发指导（C/C++）

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## 功能介绍

从API version 12开始，多模为应用提供了创建和删除按键、输入事件（鼠标、触摸和轴事件）拦截的能力。使用场景例如：云桌面应用需要拦截按键、鼠标、触摸和轴事件。

## 接口说明

创建和删除事件拦截相关接口如下表所示，接口详细介绍请参考[Input文档](../../reference/apis-input-kit/capi-input.md)。

| 接口名称  | 描述 |
| ------------------------------------------------------------ | -------------------------- |
| Input_Result OH_Input_AddKeyEventInterceptor(Input_KeyEventCallback callback, Input_InterceptorOptions *option) |创建按键事件拦截。  |
| Input_Result OH_Input_AddInputEventInterceptor(Input_InterceptorEventCallback *callback, Input_InterceptorOptions *option) |创建输入事件拦截，包含鼠标、触摸和轴事件。  |
| Input_Result OH_Input_RemoveKeyEventInterceptor() |删除按键事件拦截。  |
| Input_Result OH_Input_RemoveInputEventInterceptor() |删除输入事件拦截，包含鼠标、触摸和轴事件。  |

## 开发步骤

### 链接动态库

调用创建和删除事件拦截前，需链接相关动态库。链接动态库的方法是，在CMakeList.txt文件中做下面例子所示的配置：

```txt
target_link_libraries(entry PUBLIC libohinput.so)
```

### 申请所需权限

应用需要在module.json5中添加下面权限的配置，详细的配置方法参考[声明权限文档](../../security/AccessToken/declare-permissions.md)。

```json
"requestPermissions": [
    {
        "name": "ohos.permission.INTERCEPT_INPUT_EVENT"
    }
]
```

### 创建事件拦截

- **按键事件**

<!-- @[key_event_interceptor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/NDKInputEventInterceptor/entry/src/main/cpp/napi_init.cpp) -->

- **输入拦截（鼠标、触摸和轴事件）**

<!-- @[input_event_interceptor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/NDKInputEventInterceptor/entry/src/main/cpp/napi_init.cpp) -->
