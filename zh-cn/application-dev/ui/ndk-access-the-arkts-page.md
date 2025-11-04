# 接入ArkTS页面
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

## 占位组件

使用NDK接口构建UI界面时，需要在ArkTS页面创建用于挂载NDK接口创建组件的占位组件。占位组件类型为[ContentSlot](../reference/apis-arkui/arkui-ts/ts-components-contentSlot.md)，ContentSlot能够绑定一个[NodeContent](../reference/apis-arkui/js-apis-arkui-NodeContent.md)对象，该对象可通过Node-API传递到Native侧挂载显示Native组件。

- NDK配置文件entry/src/main/cpp/types/libentry/oh-package.json5如下。

  <!-- @[Cpp_libentry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/types/libentry/oh-package.json5) --> 
  
  ``` JSON5
  {
    "name": "libentry.so",
    "types": "./Index.d.ts",
    "version": "1.0.0",
    "description": "Please describe the basic information."
  }
  ```

- 占位组件和其他ArkTS系统组件使用方法相同。详细代码请参考[示例](#示例)。

  <!-- @[Main_Index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/ets/pages/Index.ets) -->
  
  ``` TypeScript
  import nativeNode from 'libentry.so';
  import { NodeContent } from '@kit.ArkUI';
  
  @Entry
  @Component
  struct Index {
    // 初始化NodeContent对象。
    private rootSlot:NodeContent = new NodeContent();
    @State @Watch('changeNativeFlag') showNative: boolean = false;
  
    changeNativeFlag(): void {
      if (this.showNative) {
        // 传递NodeContent对象用于Native创建组件的挂载显示
        nativeNode.createNativeRoot(this.rootSlot)
      } else {
        // 销毁NativeModule组件
        nativeNode.destroyNativeRoot()
      }
    }
  
    build() {
      Column() {
        Button(this.showNative ? 'HideNativeUI' : 'ShowNativeUI')
          .onClick(() => {
          this.showNative = !this.showNative
        })
          .id('btn')
        Row() {
          // 将NodeContent和ContentSlot占位组件绑定
          ContentSlot(this.rootSlot)
        }.layoutWeight(1)
      }
      .width('100%')
      .height('100%')
    }
  }
  ```

- 占位组件可以通过相关接口在Native侧转化为挂载对象。
  ```
  ArkUI_NodeContentHandle contentHandle;
  OH_ArkUI_GetNodeContentFromNapiValue(env, args[0], &contentHandle);
  ```

- 挂载对象提供了相关挂载和卸载组件接口。
  ```
  OH_ArkUI_NodeContent_AddNode(handle_, myNativeNode);
  OH_ArkUI_NodeContent_RemoveNode(handle_, myNativeNode);
  ```


## NDK组件模块

NDK提供的UI组件能力如组件创建、树操作、属性设置、事件注册等是通过函数指针结构体（如[ArkUI_NativeNodeAPI_1](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md)）进行暴露，该函数指针结构体可以通过[模块查询接口](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_getmoduleinterface)获取。

> **说明：**
- [模块查询接口](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_getmoduleinterface)带有初始化NDK的逻辑，建议先调用该接口进行全局初始化，再使用NDK进行UI构造。
  ```
  ArkUI_NativeNodeAPI_1* arkUINativeNodeApi = nullptr;
  OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, arkUINativeNodeApi); 
  ```

在获取到函数指针结构体后，可以使用该结构体内的函数实现相关UI组件操作。


- 组件创建和销毁。
  ```
  auto listNode = arkUINativeNodeApi->createNode(ARKUI_NODE_LIST);
  arkUINativeNodeApi->disposeNode(listNode);
  ```

  获取NDK接口支持的组件范围可以通过查询[ArkUI_NodeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodetype)枚举值。

- 组件树操作。
  ```
  auto parent = arkUINativeNodeApi->createNode(ARKUI_NODE_STACK);
  auto child = arkUINativeNodeApi->createNode(ARKUI_NODE_STACK);
  arkUINativeNodeApi->addChild(parent, child);
  arkUINativeNodeApi->removeChild(parent, child);
  ```

- 属性设置。
  ```
  auto stack = arkUINativeNodeApi->createNode(ARKUI_NODE_STACK);
  ArkUI_NumberValue value[] = {{.f32 = 100}};
  ArkUI_AttributeItem item = {value, 1};
  arkUINativeNodeApi->setAttribute(stack, NODE_WIDTH, &item);
  ArkUI_NumberValue value_color[] = {{.u32 = 0xff112233}};
  ArkUI_AttributeItem item_color = {value_color, 1};
  arkUINativeNodeApi->setAttribute(stack, NODE_BACKGROUND_COLOR, &item);
  ```

  获取NDK接口支持的属性范围可以通过查询[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)枚举值。

- 事件注册。
  ```
  auto stack = arkUINativeNodeApi->createNode(ARKUI_NODE_STACK);
  arkUINativeNodeApi->addNodeEventReceiver(stack, [](ArkUI_NodeEvent* event){
      // process event
  });
  arkUINativeNodeApi->registerNodeEvent(stack, NODE_ON_CLICK, 0, nullptr);
  ```

  获取NDK接口支持的事件范围可以通过查询[ArkUI_NodeEventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)枚举值。


## 示例

下面的示例展示了如何使用ContentSlot挂载Native侧的文本列表。

示例代码的目录结构及其文件说明如下：

```
.
|——cpp
|    |——types
|    |	  |——libentry
|    |	  |	   |——index.d.ts 提供Native和ArkTS侧的桥接方法。
|    |——napi_init.cpp 与index.d.ts对应的桥接方法对接Native侧的定义处。
|    |——NativeEntry.cpp 桥接方法的Native侧实现。
|    |——NativeEntry.h 桥接方法的Native侧定义。
|    |——CMakeList.txt C语言库引用文件。
|    |——ArkUIBaseNode.h 节点封装扩展类。
|    |——ArkUINode.h 节点封装扩展类。
|    |——ArkUIListNode.h 节点封装扩展类。
|    |——ArkUIListItemNode.h 节点封装扩展类。
|    |——ArkUITextNode.h 节点封装扩展类。
|    |——NormalTextListExample.h 示例代码文件。
| 
|——ets
|    |——pages
|         |——entry.ets 应用启动页，加载承载Native的容器。
|
```

**图1** Native文本列表

![text_list](figures/text_list.gif)

1. 在ArkTS页面上声明用于Native页面挂载的占位组件，并在页面创建时通知Native侧创建文本列表。

  <!-- @[Main_Index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/ets/pages/Index.ets) -->
  
  ``` TypeScript
  import nativeNode from 'libentry.so';
  import { NodeContent } from '@kit.ArkUI';
  
  @Entry
  @Component
  struct Index {
    // 初始化NodeContent对象。
    private rootSlot:NodeContent = new NodeContent();
    @State @Watch('changeNativeFlag') showNative: boolean = false;
  
    changeNativeFlag(): void {
      if (this.showNative) {
        // 传递NodeContent对象用于Native创建组件的挂载显示
        nativeNode.createNativeRoot(this.rootSlot)
      } else {
        // 销毁NativeModule组件
        nativeNode.destroyNativeRoot()
      }
    }
  
    build() {
      Column() {
        Button(this.showNative ? 'HideNativeUI' : 'ShowNativeUI')
          .onClick(() => {
          this.showNative = !this.showNative
        })
          .id('btn')
        Row() {
          // 将NodeContent和ContentSlot占位组件绑定
          ContentSlot(this.rootSlot)
        }.layoutWeight(1)
      }
      .width('100%')
      .height('100%')
    }
  }
  ```

2. 使用Native模板创建工程，并在Native侧提供Node-API的桥接方法，实现ArkTS侧的NativeNode模块接口。
   接口声明。

  <!-- @[Cpp_indexes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/types/libentry/Index.d.ts) -->
  
  ``` TypeScript
  // entry/src/main/cpp/types/libentry/Index.d.ts
  export const createNativeRoot: (content: Object) => void;
  export const destroyNativeRoot: () => void;
  ```

   Native实现。

  <!-- @[napi_init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/napi_init.cpp) -->
  
  ``` C++
  // entry/src/main/cpp/napi_init.cpp
  #include "napi/native_api.h"
  #include "NativeEntry.h"
  
  EXTERN_C_START
  static napi_value Init(napi_env env, napi_value exports)
  {
      // 绑定Native侧的创建组件和销毁组件。
      napi_property_descriptor desc[] = {
          {"createNativeRoot", nullptr,
           NativeModule::CreateNativeRoot, nullptr, nullptr,
           nullptr, napi_default, nullptr},
          {"destroyNativeRoot", nullptr,
           NativeModule::DestroyNativeRoot, nullptr, nullptr,
           nullptr, napi_default, nullptr}};
      napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
      return exports;
  }
  EXTERN_C_END
  
  static napi_module demoModule = {
      .nm_version = 1,
      .nm_flags = 0,
      .nm_filename = nullptr,
      .nm_register_func = Init,
      .nm_modname = "entry",
      .nm_priv = ((void *)0),
      .reserved = {0},
  };
  
  extern "C" __attribute__((constructor)) void RegisterEntryModule(void) { napi_module_register(&demoModule); }
  ```

3. 在NativeEntry.h文件中创建Native界面。

  <!-- @[Cpp_Native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/NativeEntry.h) -->

   对应实现文件。

  <!-- @[Cpp_NativeEntry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/NativeEntry.cpp) -->
   
   
   使用NDK提供的C接口需要在CMakeLists.txt中增加libace_ndk.z.so的引用，如下所示。其中entry为工程导出的动态库名称，如当前示例使用的是默认的名称libentry.so。新增cpp文件后，同样需要在CMakeLists.txt中添加相应的cpp文件。若未进行此配置，对应的文件将不会被编译。
   
   ```
   add_library(entry SHARED napi_init.cpp NativeEntry.cpp)
   target_link_libraries(entry PUBLIC libace_napi.z.so libace_ndk.z.so)
   ```

4. 由于NDK接口提供的是C接口，为了使用面向对象的方式简化编程和工程管理，这里建议使用C++进行二次封装，下面示例代码展示了示例界面中所需的列表，文本组件封装类。

1）获取ArkUI在NDK接口的入口模块[ArkUI_NativeNodeAPI_1](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md)，该结构体模块提供了一系列组件创建、树构建、属性设置和事件注册等函数指针。
   
  <!-- @[Cpp_NativeModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/NativeModule.h) -->

   2）提供列表，文本组件的基类对象，用于封装通用属性和事件。
   
  <!-- @[Cpp_ArkUIBaseNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/ArkUIBaseNode.h) -->
  <!-- @[Cpp_ArkUINode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/ArkUINode.h) -->

   3）实现列表组件。
   
  <!-- @[Cpp_ArkUIListNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/ArkUIListNode.h) -->

   4）实现列表项组件。
   
  <!-- @[Cpp_ArkUIListItemNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/ArkUIListItemNode.h) -->

   5）实现文本组件。
   
  <!-- @[Cpp_ArkUITextNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/ArkUITextNode.h) -->
   
5. 完善步骤3的CreateTextListExample函数，实现Native文本列表的创建和挂载显示。

  <!-- @[Cpp_NormalTextListExample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/NormalTextListExample.h) -->