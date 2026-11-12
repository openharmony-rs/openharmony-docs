# 设置自定义节点跨语言属性
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

ArkUI支持在前端使用ArkTS语言创建命令式节点，即[FrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md)节点，也可以在Native侧使用C语言创建命令式节点，并且可以混合使用两类节点构建页面。

针对上述场景，ArkUI提供命令式节点跨语言属性设置功能，即使用ArkTS语言创建的命令式节点，可以在Native侧进行属性设置。使用C语言创建的节点，可以在ArkTS侧进行属性设置。

> **说明：**
>
> 下述示例中，需要先进行Native侧配置，请参考[接入ArkTS页面](./ndk-access-the-arkts-page.md)完成。

## 设置和获取跨语言配置

跨语言指的是跨越ArkTS语言和C语言。跨语言配置指的是命令式节点上对于跨语言操作的权限配置。

可以通过[setCrossLanguageOptions](../reference/apis-arkui/js-apis-arkui-frameNode.md#setcrosslanguageoptions15)与[OH_ArkUI_NodeUtils_SetCrossLanguageOption](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_setcrosslanguageoption)接口设置当前节点的跨语言配置。如果当前节点无法修改或设置跨语言配置，则会抛出异常信息。

可以使用[getCrossLanguageOptions](../reference/apis-arkui/js-apis-arkui-frameNode.md#getcrosslanguageoptions15)与[OH_ArkUI_NodeUtils_GetCrossLanguageOption](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getcrosslanguageoption)接口获取当前节点的跨语言配置。

以下示例描述了如何设置和获取ArkTS命令式节点的跨语言配置。

```ts
// Index.ets
import { NodeController, UIContext, FrameNode, typeNode, BuilderNode } from '@kit.ArkUI';

@Builder
function insideScroll() {
  Column() {
    ForEach([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], (item: number) => {
      Text(item.toString())
        .width("75%")
        .height(50)
        .backgroundColor(0xFFFFFF)
        .borderRadius(15)
        .fontSize(30)
        .textAlign(TextAlign.Center)
        .margin({ top: 10 })
    }, (item: number) => item.toString())
  }
  .width("100%")
}

class MyNodeController extends NodeController {
  uiContext: UIContext | null = null;
  rootNode: FrameNode | null = null;
  scrollNode: FrameNode | null = null;
  scroller: Scroller = new Scroller();

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    this.rootNode.commonAttribute.width("80%").height("50%").borderWidth(2).margin(15);
    const scroll = typeNode.createNode(uiContext, 'Scroll');
    scroll.initialize(this.scroller).id("scroll");
    this.scrollNode = scroll;
    this.rootNode.appendChild(this.scrollNode);
    const builderNode = new BuilderNode(uiContext);
    builderNode.build(wrapBuilder(insideScroll));
    this.scrollNode?.appendChild(builderNode.getFrameNode());
    return this.rootNode;
  }
}

@Entry
@Component
struct CrossLanguage {
  myNodeController: MyNodeController = new MyNodeController()
  @State attributeSetting: boolean = false;
  @State getCrossLanguageOptions: string = '{"attributeSetting": false}';

  build() {
    Scroll() {
      Column({ space: 15 }) {
        Column() {
          Scroll() {
            Column() {
              NodeContainer(this.myNodeController)
              Button("setCrossLanguageOptions").margin({ bottom: 15})
                .onClick(() => {
                  this.attributeSetting = !this.attributeSetting;
                  this.myNodeController.scrollNode?.setCrossLanguageOptions({
                    attributeSetting: this.attributeSetting
                  });
                  // 若attributeSetting为true，表示scrollNode支持通过非ArkTS语言进行属性设置，否则为不支持
                  this.getCrossLanguageOptions = JSON.stringify(this.myNodeController.scrollNode?.getCrossLanguageOptions());
                })
              Text("CrossLanguageOptions: " + this.getCrossLanguageOptions)
            }
          }.scrollBarColor(Color.Transparent)
        }
        .width('100%')
        .height(350)
        .backgroundColor(0xeeeeee)
        .id('Part_TS')
      }
      .width('100%')
    }.scrollBarColor(Color.Transparent)
  }
}
```

## 跨语言设置节点属性

获取节点后，若节点的跨语言配置设置为允许属性设置，ArkTS侧可利用getAttribute接口获取修改Native节点属性的对象，Native侧可利用[setAttribute](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)接口修改ArkTS节点属性。

以下示例创建了ArkTS的[Scroll](../reference/apis-arkui/js-apis-arkui-frameNode.md#scroll12)类型节点，并在Native侧修改了Scroll的属性。

1. 在ArkTS侧创建组件类型为Scroll的命令式节点。新建`CrossLanguage.ets`页面文件，在页面创建时调用createCrossLanguageRoot方法通知Native侧创建跨语言示例组件，在页面销毁时调用destroyNativeRoot方法释放Native侧组件。此外，需要在`entry/src/main/resources/base/profile/main_pages.json`中注册`pages/CrossLanguage`页面，并在主页面中添加跳转至该页面的路由。

   <!-- @[cross_language_index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/ets/pages/CrossLanguage.ets) -->  
   
   ``` TypeScript
   import nativeNode from 'libentry.so';
   import { NodeController, UIContext, FrameNode, typeNode, BuilderNode, NodeContent } from '@kit.ArkUI';
   
   @Builder
   function insideScroll() {
     Column() {
       ForEach([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], (item: number) => {
         Text(item.toString())
           .width('75%')
           .height(50)
           .backgroundColor(0xFFFFFF)
           .borderRadius(15)
           .fontSize(30)
           .textAlign(TextAlign.Center)
           .margin({ top: 10 })
       }, (item: number) => item.toString())
     }
     .width('100%')
   }
   
   class MyNodeController extends NodeController {
     private uiContext: UIContext | null = null;
     private rootNode: FrameNode | null = null;
     public scrollNode: FrameNode | null = null;
     private scroller: Scroller = new Scroller();
   
     makeNode(uiContext: UIContext): FrameNode | null {
       this.uiContext = uiContext;
       this.rootNode = new FrameNode(uiContext);
       this.rootNode.commonAttribute.width('80%').height('50%').borderWidth(2).margin(15);
       const scroll = typeNode.createNode(uiContext, 'Scroll');
       scroll.initialize(this.scroller).id('scroll');
       this.scrollNode = scroll;
       this.rootNode.appendChild(this.scrollNode);
       const builderNode = new BuilderNode(uiContext);
       builderNode.build(wrapBuilder(insideScroll));
       this.scrollNode?.appendChild(builderNode.getFrameNode());
       return this.rootNode;
     }
   }
   
   @Entry
   @Component
   struct CrossLanguage {
     private myNodeController: MyNodeController = new MyNodeController();
     @State attributeSetting: boolean = false;
     @State getCrossLanguageOptions: string = '{"attributeSetting": false}';
     private rootSlot = new NodeContent();
   
     aboutToAppear(): void {
       // 传递NodeContent对象用于Native创建跨语言示例组件的挂载显示。
       nativeNode.createCrossLanguageRoot(this.rootSlot);
     }
   
     aboutToDisappear(): void {
       // 页面销毁时释放Native侧组件。
       nativeNode.destroyNativeRoot();
     }
   
     build() {
       Scroll() {
         Column({ space: 15 }) {
           Column() {
             Scroll() {
               Column() {
                 NodeContainer(this.myNodeController)
                 Button('setCrossLanguageOptions').margin({ bottom: 15})
                   .onClick(() => {
                     this.attributeSetting = !this.attributeSetting;
                     this.myNodeController.scrollNode?.setCrossLanguageOptions({
                       attributeSetting: this.attributeSetting
                     });
                     // 若attributeSetting为true，表示scrollNode支持通过非ArkTS语言进行属性设置，否则为不支持
                     this.getCrossLanguageOptions =
                       JSON.stringify(this.myNodeController.scrollNode?.getCrossLanguageOptions());
                   })
                 Text('CrossLanguageOptions: ' + this.getCrossLanguageOptions)
               }
             }.scrollBarColor(Color.Transparent)
           }
           .width('100%')
           .height(350)
           .backgroundColor(0xeeeeee)
           .id('Part_TS')
   
           Column() {
             ContentSlot(this.rootSlot)
           }
           .width(500)
           .height(400)
           .id('Part_C')
         }
         .width('100%')
       }.scrollBarColor(Color.Transparent)
     }
   }
   ```

2. 提供ArkTS侧引用Native桥接方法的接口声明与注册，使步骤1中通过`import nativeNode from 'libentry.so'`引用的createCrossLanguageRoot和destroyNativeRoot方法生效。

   其中，`entry/src/main/cpp/types/libentry/oh-package.json5`文件用于将`libentry.so`与接口声明文件`Index.d.ts`关联。

   <!-- @[Cpp_libentry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/types/libentry/oh-package.json5) -->  
   
   ``` JSON5
   {
     "name": "libentry.so",
     "types": "./Index.d.ts",
     "version": "1.0.0",
     "description": "Please describe the basic information."
   }
   ```

   接口声明。

   <!-- @[Cpp_indexes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/types/libentry/Index.d.ts) -->  
   
   ``` TypeScript
   // entry/src/main/cpp/types/libentry/Index.d.ts
   export const createNativeRoot: (content: Object) => void;
   export const createCrossLanguageRoot: (content: Object) => void;
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
           {"createCrossLanguageRoot", nullptr,
            NativeModule::CreateCrossLanguageRoot, nullptr, nullptr,
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

3. 本示例使用C++对NDK的C接口进行二次封装，需要提供获取NDK接口入口的封装接口`NativeModule.h`、组件树操作基类`ArkUIBaseNode.h`以及通用属性和事件的封装类`ArkUINode.h`。若已完成[接入ArkTS页面](./ndk-access-the-arkts-page.md)中的Native侧配置，可直接复用对应文件。

   <!-- @[Cpp_NativeModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/NativeModule.h) -->  
   
   ``` C
   // NativeModule.h
   // 提供获取ArkUI在Native侧模块的封装接口
   
   #ifndef MYAPPLICATION_NATIVEMODULE_H
   #define MYAPPLICATION_NATIVEMODULE_H
   
   #include <arkui/native_node.h>
   #include <cassert>
   
   #include <arkui/native_interface.h>
   
   namespace NativeModule {
   
   class NativeModuleInstance {
   public:
       static NativeModuleInstance *GetInstance()
       {
           static NativeModuleInstance instance;
           return &instance;
       }
       NativeModuleInstance()
       {
           OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, arkUINativeNodeApi_);
       }
       // 暴露给其他模块使用。
       ArkUI_NativeNodeAPI_1 *GetNativeNodeAPI() { return arkUINativeNodeApi_; }
   
   private:
       ArkUI_NativeNodeAPI_1 *arkUINativeNodeApi_ = nullptr;
   };
   
   } // namespace NativeModule
   
   #endif // MYAPPLICATION_NATIVEMODULE_H
   ```

   <!-- @[Cpp_ArkUIBaseNode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/ArkUIBaseNode.h) -->  
   
   ``` C
   // ArkUIBaseNode.h
   // 提供组件树操作的基类。
   #ifndef MYAPPLICATION_ARKUIBASENODE_H
   #define MYAPPLICATION_ARKUIBASENODE_H
   
   #include <arkui/native_type.h>
   #include <list>
   #include <memory>
   
   #include "NativeModule.h"
   
   namespace NativeModule {
   
   class ArkUIBaseNode {
   public:
       explicit ArkUIBaseNode(ArkUI_NodeHandle handle)
           : handle_(handle), nativeModule_(NativeModuleInstance::GetInstance()->GetNativeNodeAPI()) {}
   
       virtual ~ArkUIBaseNode()
       {
           // 封装析构函数，实现子节点移除功能。
           if (!children_.empty()) {
               for (const auto& child : children_) {
                   nativeModule_->removeChild(handle_, child->GetHandle());
               }
               children_.clear();
           }
           // 封装析构函数，统一回收节点资源。
           nativeModule_->disposeNode(handle_);
       }
   
       void AddChild(const std::shared_ptr<ArkUIBaseNode> &child)
       {
           children_.emplace_back(child);
           OnAddChild(child);
       }
   
       void RemoveChild(const std::shared_ptr<ArkUIBaseNode> &child)
       {
           children_.remove(child);
           OnRemoveChild(child);
       }
   
       void InsertChild(const std::shared_ptr<ArkUIBaseNode> &child, int32_t index)
       {
           if (index >= children_.size()) {
               AddChild(child);
           } else {
               auto iter = children_.begin();
               std::advance(iter, index);
               children_.insert(iter, child);
               OnInsertChild(child, index);
           }
       }
   
       ArkUI_NodeHandle GetHandle() const { return handle_; }
   
   protected:
       // 针对父容器子类需要重载下面的函数，实现组件挂载和卸载。
       virtual void OnAddChild(const std::shared_ptr<ArkUIBaseNode> &child) {}
       virtual void OnRemoveChild(const std::shared_ptr<ArkUIBaseNode> &child) {}
       virtual void OnInsertChild(const std::shared_ptr<ArkUIBaseNode> &child, int32_t index) {}
   
       ArkUI_NodeHandle handle_;
       ArkUI_NativeNodeAPI_1 *nativeModule_ = nullptr;
   
   private:
       std::list<std::shared_ptr<ArkUIBaseNode>> children_;
   };
   } // namespace NativeModule
   
   #endif // MYAPPLICATION_ARKUIBASENODE_H
   ```

   <!-- @[Cpp_ArkUINode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/ArkUINode.h) -->  
   
   ``` C
   // ArkUINode.h
   // 提供通用属性和事件的封装。
   #ifndef MYAPPLICATION_ARKUINODE_H
   #define MYAPPLICATION_ARKUINODE_H
   
   #include "ArkUIBaseNode.h"
   #include "NativeModule.h"
   #include <arkui/native_node.h>
   #include <arkui/native_type.h>
   
   namespace NativeModule {
   
   class ArkUINode : public ArkUIBaseNode {
   public:
       explicit ArkUINode(ArkUI_NodeHandle handle) : ArkUIBaseNode(handle) {}
   
       ~ArkUINode() override {}
       
       void SetWidth(float width)
       {
           ArkUI_NumberValue value[] = {{.f32 = width}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_WIDTH, &item);
       }
       void SetPercentWidth(float percent)
       {
           ArkUI_NumberValue value[] = {{.f32 = percent}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_WIDTH_PERCENT, &item);
       }
       void SetHeight(float height)
       {
           ArkUI_NumberValue value[] = {{.f32 = height}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_HEIGHT, &item);
       }
       void SetPercentHeight(float percent)
       {
           ArkUI_NumberValue value[] = {{.f32 = percent}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_HEIGHT_PERCENT, &item);
       }
       void SetBackgroundColor(uint32_t color)
       {
           ArkUI_NumberValue value[] = {{.u32 = color}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_BACKGROUND_COLOR, &item);
       }
   
   protected:
       // 组件树操作的实现类对接。
       void OnAddChild(const std::shared_ptr<ArkUIBaseNode> &child) override
       {
           nativeModule_->addChild(handle_, child->GetHandle());
       }
       void OnRemoveChild(const std::shared_ptr<ArkUIBaseNode> &child) override
       {
           nativeModule_->removeChild(handle_, child->GetHandle());
       }
       void OnInsertChild(const std::shared_ptr<ArkUIBaseNode> &child, int32_t index) override
       {
           nativeModule_->insertChildAt(handle_, child->GetHandle(), index);
       }
   };
   } // namespace NativeModule
   
   #endif // MYAPPLICATION_ARKUINODE_H
   ```

4. 在`NativeEntry.h`中声明CreateCrossLanguageRoot等桥接方法，并管理Native组件的生命周期和内存。

   <!-- @[Cpp_Native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/NativeEntry.h) -->  
   
   ``` C
   // NativeEntry.h
   
   #ifndef MYAPPLICATION_NATIVEENTRY_H
   #define MYAPPLICATION_NATIVEENTRY_H
   
   #include <ArkUIBaseNode.h>
   #include <arkui/native_type.h>
   #include <js_native_api_types.h>
   
   namespace NativeModule {
   
   napi_value CreateNativeRoot(napi_env env, napi_callback_info info);
   
   napi_value CreateCrossLanguageRoot(napi_env env, napi_callback_info info);
   
   napi_value DestroyNativeRoot(napi_env env, napi_callback_info info);
   
   // 管理Native组件的生命周期和内存。
   class NativeEntry {
   public:
       static NativeEntry *GetInstance()
       {
           static NativeEntry nativeEntry;
           return &nativeEntry;
       }
   
       void SetContentHandle(ArkUI_NodeContentHandle handle)
       {
           handle_ = handle;
       }
   
       void SetRootNode(const std::shared_ptr<ArkUIBaseNode> &baseNode)
       {
           root_ = baseNode;
           // 添加Native组件到NodeContent上用于挂载显示。
           OH_ArkUI_NodeContent_AddNode(handle_, root_->GetHandle());
       }
       void DisposeRootNode()
       {
           // 从NodeContent上卸载组件并销毁Native组件。
           OH_ArkUI_NodeContent_RemoveNode(handle_, root_->GetHandle());
           root_.reset();
       }
   
   private:
       std::shared_ptr<ArkUIBaseNode> root_;
       ArkUI_NodeContentHandle handle_;
   };
   
   } // namespace NativeModule
   
   #endif  // MYAPPLICATION_NATIVEENTRY_H
   ```

5. 在`NativeEntry.cpp`中实现CreateCrossLanguageRoot方法，创建跨语言示例组件并挂载显示。其中CreateNativeRoot为[接入ArkTS页面](./ndk-access-the-arkts-page.md)示例中挂载Native文本列表的方法。

   <!-- @[Cpp_NativeEntry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/NativeEntry.cpp) -->  
   
   ``` C++
   // NativeEntry.cpp
   
   #include <arkui/native_node_napi.h>
   #include <js_native_api.h>
   #include "NativeEntry.h"
   #include "CrossLanguageExample.h"
   #include "NormalTextListExample.h"
   
   namespace NativeModule {
   
   napi_value CreateNativeRoot(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value args[1] = {nullptr};
   
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       // 获取NodeContent
       ArkUI_NodeContentHandle contentHandle;
       OH_ArkUI_GetNodeContentFromNapiValue(env, args[0], &contentHandle);
       NativeEntry::GetInstance()->SetContentHandle(contentHandle);
   
       // 创建文本列表
       auto list = CreateTextListExample();
   
       // 保持Native侧对象到管理类中，维护生命周期。
       NativeEntry::GetInstance()->SetRootNode(list);
       return nullptr;
   }
   
   napi_value CreateCrossLanguageRoot(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value args[1] = {nullptr};
   
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       // 获取NodeContent
       ArkUI_NodeContentHandle contentHandle;
       OH_ArkUI_GetNodeContentFromNapiValue(env, args[0], &contentHandle);
       NativeEntry::GetInstance()->SetContentHandle(contentHandle);
   
       // 创建跨语言属性设置示例
       auto node = CreateCrossLanguageExample();
   
       // 保持Native侧对象到管理类中，维护生命周期。
       NativeEntry::GetInstance()->SetRootNode(node);
       return nullptr;
   }
   
   napi_value DestroyNativeRoot(napi_env env, napi_callback_info info)
   {
       // 从管理类中释放Native侧对象。
       NativeEntry::GetInstance()->DisposeRootNode();
       return nullptr;
   }
   } // namespace NativeModule
   ```

6. 新建`CrossLanguageExample.h`文件，在其中创建Native侧组件树，并通过OH_ArkUI_NodeUtils_GetAttachedNodeHandleById获取ArkTS侧创建的目标节点，设置其属性。

   <!-- @[cpp_cross_language_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonList/entry/src/main/cpp/CrossLanguageExample.h) -->  
   
   ``` C
   // CrossLanguageExample.h
   // 提供跨语言属性设置示例中Native侧组件的创建。
   
   #ifndef MYAPPLICATION_CROSSLANGUAGEEXAMPLE_H
   #define MYAPPLICATION_CROSSLANGUAGEEXAMPLE_H
   
   #include "ArkUINode.h"
   #include <hilog/log.h>
   #include <memory>
   
   namespace NativeModule {
   
   // 事件回调：在Native侧跨语言修改ArkTS侧创建的Scroll节点属性。
   void HandleCrossLanguageClick(ArkUI_NodeEvent *event)
   {
       auto nodeAPI = NativeModuleInstance::GetInstance()->GetNativeNodeAPI();
   
       if (OH_ArkUI_NodeEvent_GetTargetId(event) == 0) { // 修改滚动条颜色。
           ArkUI_NodeHandle node_ptr = nullptr;
           // 通过id获取ArkTS侧创建的节点。
           auto ret = OH_ArkUI_NodeUtils_GetAttachedNodeHandleById("scroll", &node_ptr);
           if (ret != ARKUI_ERROR_CODE_NO_ERROR || node_ptr == nullptr) {
               OH_LOG_Print(LOG_APP, LOG_ERROR, 0xFF00, "CrossLanguageExample",
                   "OH_ArkUI_NodeUtils_GetAttachedNodeHandleById failed, error code: %{public}d", ret);
               return;
           }
           ArkUI_NumberValue scroll_color_value[] = {{.u32 = 0xff00ff00}};
           ArkUI_AttributeItem scroll_color_item = {scroll_color_value,
               sizeof(scroll_color_value) / sizeof(ArkUI_NumberValue)};
           // 若ArkTS侧未开启跨语言属性设置，此处设置失败并返回错误码。
           auto errCode = nodeAPI->setAttribute(node_ptr, NODE_SCROLL_BAR_COLOR, &scroll_color_item);
           if (errCode != ARKUI_ERROR_CODE_NO_ERROR) {
               OH_LOG_Print(LOG_APP, LOG_ERROR, 0xFF00, "CrossLanguageExample",
                   "crossLanguage setAttribute scroll bar color failed, error code: %{public}d", errCode);
           }
       }
   
       if (OH_ArkUI_NodeEvent_GetTargetId(event) == 1) { // 修改滚动条宽度。
           ArkUI_NodeHandle node_ptr = nullptr;
           auto ret = OH_ArkUI_NodeUtils_GetAttachedNodeHandleById("scroll", &node_ptr);
           if (ret != ARKUI_ERROR_CODE_NO_ERROR || node_ptr == nullptr) {
               OH_LOG_Print(LOG_APP, LOG_ERROR, 0xFF00, "CrossLanguageExample",
                   "OH_ArkUI_NodeUtils_GetAttachedNodeHandleById failed, error code: %{public}d", ret);
               return;
           }
           ArkUI_NumberValue scroll_width_value[] = {{.f32 = 20}};
           ArkUI_AttributeItem scroll_width_item = {scroll_width_value,
               sizeof(scroll_width_value) / sizeof(ArkUI_NumberValue)};
           auto errCode = nodeAPI->setAttribute(node_ptr, NODE_SCROLL_BAR_WIDTH, &scroll_width_item);
           if (errCode != ARKUI_ERROR_CODE_NO_ERROR) {
               OH_LOG_Print(LOG_APP, LOG_ERROR, 0xFF00, "CrossLanguageExample",
                   "crossLanguage setAttribute scroll bar width failed, error code: %{public}d", errCode);
           }
       }
   }
   
   // 创建根节点Scroll。
   ArkUI_NodeHandle CreateScrollNode(ArkUI_NativeNodeAPI_1 *nodeAPI)
   {
       ArkUI_NodeHandle scroll = nodeAPI->createNode(ARKUI_NODE_SCROLL);
       ArkUI_NumberValue length_value[] = {{.f32 = 480}};
       ArkUI_AttributeItem length_item = {length_value, sizeof(length_value) / sizeof(ArkUI_NumberValue)};
       nodeAPI->setAttribute(scroll, NODE_WIDTH, &length_item);
       ArkUI_NumberValue length_value1[] = {{.f32 = 650}};
       ArkUI_AttributeItem length_item1 = {length_value1, sizeof(length_value1) / sizeof(ArkUI_NumberValue)};
       nodeAPI->setAttribute(scroll, NODE_HEIGHT, &length_item1);
       ArkUI_AttributeItem scroll_id = {.string = "Scroll_CAPI"};
       nodeAPI->setAttribute(scroll, NODE_ID, &scroll_id);
       return scroll;
   }
   
   // 创建Column。
   ArkUI_NodeHandle CreateColumnNode(ArkUI_NativeNodeAPI_1 *nodeAPI)
   {
       ArkUI_NodeHandle column = nodeAPI->createNode(ARKUI_NODE_COLUMN);
       ArkUI_NumberValue value[] = {{.f32 = 480}};
       ArkUI_AttributeItem item = {value, sizeof(value) / sizeof(ArkUI_NumberValue)};
       nodeAPI->setAttribute(column, NODE_WIDTH, &item);
       ArkUI_NumberValue column_bc[] = {{.u32 = 0xFFF00BB}};
       ArkUI_AttributeItem column_item = {column_bc, 1};
       nodeAPI->setAttribute(column, NODE_BACKGROUND_COLOR, &column_item);
       ArkUI_AttributeItem column_id = {.string = "Column_CAPI"};
       nodeAPI->setAttribute(column, NODE_ID, &column_id);
       return column;
   }
   
   // 创建Text。
   ArkUI_NodeHandle CreateTextNode(ArkUI_NativeNodeAPI_1 *nodeAPI)
   {
       ArkUI_NodeHandle text0 = nodeAPI->createNode(ARKUI_NODE_TEXT);
       ArkUI_NumberValue text_width[] = {{.f32 = 300}};
       ArkUI_AttributeItem text_item0 = {text_width, sizeof(text_width) / sizeof(ArkUI_NumberValue)};
       nodeAPI->setAttribute(text0, NODE_WIDTH, &text_item0);
       ArkUI_NumberValue text_height[] = {{.f32 = 50}};
       ArkUI_AttributeItem text_item1 = {text_height, sizeof(text_height) / sizeof(ArkUI_NumberValue)};
       nodeAPI->setAttribute(text0, NODE_HEIGHT, &text_item1);
       ArkUI_AttributeItem text_item = {.string = "C设置TS创建的节点属性"};
       nodeAPI->setAttribute(text0, NODE_TEXT_CONTENT, &text_item);
       ArkUI_NumberValue margin[] = {{.f32 = 10}};
       ArkUI_AttributeItem item_margin = {margin, sizeof(margin) / sizeof(ArkUI_NumberValue)};
       nodeAPI->setAttribute(text0, NODE_MARGIN, &item_margin);
       return text0;
   }
   
   // 创建Row。
   ArkUI_NodeHandle CreateRowNode(ArkUI_NativeNodeAPI_1 *nodeAPI)
   {
       ArkUI_NodeHandle row0 = nodeAPI->createNode(ARKUI_NODE_ROW);
       ArkUI_NumberValue width_value[] = {{.f32 = 330}};
       ArkUI_AttributeItem width_item = {width_value, sizeof(width_value) / sizeof(ArkUI_NumberValue)};
       nodeAPI->setAttribute(row0, NODE_WIDTH, &width_item);
       ArkUI_NumberValue height_value[] = {{.f32 = 50}};
       ArkUI_AttributeItem height_item = {height_value, sizeof(height_value) / sizeof(ArkUI_NumberValue)};
       nodeAPI->setAttribute(row0, NODE_HEIGHT, &height_item);
       ArkUI_NumberValue margin[] = {{.f32 = 10}};
       ArkUI_AttributeItem item_margin = {margin, sizeof(margin) / sizeof(ArkUI_NumberValue)};
       nodeAPI->setAttribute(row0, NODE_MARGIN, &item_margin);
       return row0;
   }
   
   // 创建Button，用于触发Native侧跨语言属性设置。
   void CreateButtonNodes(ArkUI_NativeNodeAPI_1 *nodeAPI, ArkUI_NodeHandle row0)
   {
       ArkUI_NumberValue btn_width[] = {{.f32 = 150}};
       ArkUI_AttributeItem btn_item0 = {btn_width, sizeof(btn_width) / sizeof(ArkUI_NumberValue)};
       ArkUI_NumberValue height_value[] = {{.f32 = 50}};
       ArkUI_AttributeItem height_item = {height_value, sizeof(height_value) / sizeof(ArkUI_NumberValue)};
       ArkUI_NumberValue margin[] = {{.f32 = 10}};
       ArkUI_AttributeItem item_margin = {margin, sizeof(margin) / sizeof(ArkUI_NumberValue)};
   
       ArkUI_NodeHandle bt0 = nodeAPI->createNode(ARKUI_NODE_BUTTON);
       nodeAPI->setAttribute(bt0, NODE_WIDTH, &btn_item0);
       nodeAPI->setAttribute(bt0, NODE_HEIGHT, &height_item);
       nodeAPI->setAttribute(bt0, NODE_MARGIN, &item_margin);
       ArkUI_AttributeItem bt0_item = {.string = "scrollBarColor"};
       nodeAPI->setAttribute(bt0, NODE_BUTTON_LABEL, &bt0_item);
       nodeAPI->registerNodeEvent(bt0, NODE_ON_CLICK, 0, nullptr);
   
       ArkUI_NodeHandle bt1 = nodeAPI->createNode(ARKUI_NODE_BUTTON);
       nodeAPI->setAttribute(bt1, NODE_WIDTH, &btn_item0);
       nodeAPI->setAttribute(bt1, NODE_HEIGHT, &height_item);
       nodeAPI->setAttribute(bt1, NODE_MARGIN, &item_margin);
       ArkUI_AttributeItem bt1_item = {.string = "scrollBarWidth"};
       nodeAPI->setAttribute(bt1, NODE_BUTTON_LABEL, &bt1_item);
       nodeAPI->registerNodeEvent(bt1, NODE_ON_CLICK, 1, nullptr);
   
       nodeAPI->addChild(row0, bt0);
       nodeAPI->addChild(row0, bt1);
   }
   
   std::shared_ptr<ArkUIBaseNode> CreateCrossLanguageExample()
   {
       auto nodeAPI = NativeModuleInstance::GetInstance()->GetNativeNodeAPI();
   
       // 创建根节点Scroll。
       ArkUI_NodeHandle scroll = CreateScrollNode(nodeAPI);
   
       // 创建Column。
       ArkUI_NodeHandle column = CreateColumnNode(nodeAPI);
   
       // 创建Text。
       ArkUI_NodeHandle text0 = CreateTextNode(nodeAPI);
   
       // 创建Row。
       ArkUI_NodeHandle row0 = CreateRowNode(nodeAPI);
   
       // 创建Button，用于触发Native侧跨语言属性设置。
       CreateButtonNodes(nodeAPI, row0);
   
       // 注册事件回调，在Native侧跨语言修改ArkTS侧创建的Scroll节点属性。
       nodeAPI->registerNodeEventReceiver(HandleCrossLanguageClick);
   
       // 节点添加，构建组件树。
       nodeAPI->addChild(scroll, column);
       nodeAPI->addChild(column, text0);
       nodeAPI->addChild(column, row0);
   
       return std::make_shared<ArkUINode>(scroll);
   }
   } // namespace NativeModule
   
   #endif // MYAPPLICATION_CROSSLANGUAGEEXAMPLE_H
   ```

7. 修改CMakeLists.txt，添加链接库。
   ```c
   # CMakeLists.txt
   # the minimum version of CMake.
   cmake_minimum_required(VERSION 3.5.0)
   project(CAPI_DEMO)
 
   set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})
 
   if(DEFINED PACKAGE_FIND_FILE)
       include(${PACKAGE_FIND_FILE})
   endif()
 
   include_directories(${NATIVERENDER_ROOT_PATH}
                     ${NATIVERENDER_ROOT_PATH}/include)
 
   add_library(entry SHARED napi_init.cpp NativeEntry.cpp)
   target_link_libraries(entry PUBLIC libace_napi.z.so libace_ndk.z.so hilog_ndk.z.so)
   ```

8. 运行程序，在示例主页面点击CrossLanguage按钮进入跨语言属性设置页面，在ArkTS侧点击setCrossLanguageOptions按钮，设置当前attributeSetting为true，在Native侧点击按钮，设置ArkTS侧Scroll组件滚动条的颜色和粗细属性。

    ![crossLanguageDemo](figures/crossLanguageDemo.gif)

## 支持跨语言设置属性的节点类型

仅以下节点类型支持跨语言设置节点属性。Native侧需要使用[OH_ArkUI_NodeUtils_GetAttachedNodeHandleById](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getattachednodehandlebyid)获取待修改属性的节点，不支持对[OH_ArkUI_GetNodeHandleFromNapiValue](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnodehandlefromnapivalue)获取的目标节点跨语言设置属性。

> **说明：**
>
> 通过C API创建的Scroll、WaterFlow、Grid和List节点支持在ArkTS侧使用bindController绑定滚动控制器[Scroller](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scroller)。从API版本26.0.0开始，调用如上四个组件的对应接口无需开启跨语言属性设置。

| ArkTS侧[TypedFrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#typedframenode12)类型 | Native侧[ArkUI_NodeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodetype)类型 | ArkTS属性获取接口 | ArkTS控制器获取/绑定接口 |
| -------- | -------- | -------- | -------- |
| [Button](../reference/apis-arkui/js-apis-arkui-frameNode.md#button12) | ARKUI_NODE_BUTTON | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributebutton20) | NA |
| [Checkbox](../reference/apis-arkui/js-apis-arkui-frameNode.md#checkbox18) | ARKUI_NODE_CHECKBOX | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributecheckbox20) | NA |
| [Radio](../reference/apis-arkui/js-apis-arkui-frameNode.md#radio18) | ARKUI_NODE_RADIO | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributeradio20) | NA |
| [Slider](../reference/apis-arkui/js-apis-arkui-frameNode.md#slider18) | ARKUI_NODE_SLIDER | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributeslider20) | NA |
| [Toggle](../reference/apis-arkui/js-apis-arkui-frameNode.md#toggle18) | ARKUI_NODE_TOGGLE | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributetoggle20) | NA |
| [Progress](../reference/apis-arkui/js-apis-arkui-frameNode.md#progress12) | ARKUI_NODE_PROGRESS | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributeprogress20) | NA |
| [LoadingProgress](../reference/apis-arkui/js-apis-arkui-frameNode.md#loadingprogress12) | ARKUI_NODE_LOADING_PROGRESS | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributeloadingprogress20) | NA |
| [Image](../reference/apis-arkui/js-apis-arkui-frameNode.md#image12) | ARKUI_NODE_IMAGE | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributeimage20) | NA |
| [XComponent](../reference/apis-arkui/js-apis-arkui-frameNode.md#xcomponent12) | ARKUI_NODE_XCOMPONENT | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributexcomponent20) | getController |
| [Column](../reference/apis-arkui/js-apis-arkui-frameNode.md#column12) | ARKUI_NODE_COLUMN | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributecolumn20) | NA |
| [Row](../reference/apis-arkui/js-apis-arkui-frameNode.md#row12) | ARKUI_NODE_ROW | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributerow20) | NA |
| [Stack](../reference/apis-arkui/js-apis-arkui-frameNode.md#stack12) | ARKUI_NODE_STACK | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributestack20) | NA |
| [Flex](../reference/apis-arkui/js-apis-arkui-frameNode.md#flex12) | ARKUI_NODE_FLEX | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributeflex20) | NA |
| [RelativeContainer](../reference/apis-arkui/js-apis-arkui-frameNode.md#relativecontainer12) | ARKUI_NODE_RELATIVE_CONTAINER | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributerelativecontainer20) | NA |
| [Swiper](../reference/apis-arkui/js-apis-arkui-frameNode.md#swiper12) | ARKUI_NODE_SWIPER | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributeswiper20) | [bindController](../reference/apis-arkui/js-apis-arkui-frameNode.md#bindcontrollerswiper20) |
| [Scroll](../reference/apis-arkui/js-apis-arkui-frameNode.md#scroll12) | ARKUI_NODE_SCROLL | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributescroll15) | [bindController](../reference/apis-arkui/js-apis-arkui-frameNode.md#bindcontrollerscroll15) |
| [List](../reference/apis-arkui/js-apis-arkui-frameNode.md#list12) | ARKUI_NODE_LIST | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributelist20) | [bindController](../reference/apis-arkui/js-apis-arkui-frameNode.md#bindcontrollerlist20) |
| [ListItem](../reference/apis-arkui/js-apis-arkui-frameNode.md#listitem12) | ARKUI_NODE_LIST_ITEM | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributelistitem20) | NA |
| [ListItemGroup](../reference/apis-arkui/js-apis-arkui-frameNode.md#listitemgroup12) | ARKUI_NODE_LIST_ITEM_GROUP | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributelistitemgroup20) | NA |
| [WaterFlow](../reference/apis-arkui/js-apis-arkui-frameNode.md#waterflow12) | ARKUI_NODE_WATER_FLOW | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributewaterflow20) | [bindController](../reference/apis-arkui/js-apis-arkui-frameNode.md#bindcontrollerwaterflow20) |
| [FlowItem](../reference/apis-arkui/js-apis-arkui-frameNode.md#flowitem12) | ARKUI_NODE_FLOW_ITEM | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributeflowitem20) | NA |
| [Grid](../reference/apis-arkui/js-apis-arkui-frameNode.md#grid14) | ARKUI_NODE_GRID | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributegrid20) | [bindController](../reference/apis-arkui/js-apis-arkui-frameNode.md#bindcontrollergrid20) |
| [GridItem](../reference/apis-arkui/js-apis-arkui-frameNode.md#griditem14) | ARKUI_NODE_GRID_ITEM | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributegriditem20) | NA |
| [Text](../reference/apis-arkui/js-apis-arkui-frameNode.md#text12) | ARKUI_NODE_TEXT | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributetext20) | [bindController](../reference/apis-arkui/js-apis-arkui-frameNode.md#bindcontrollertext20) |
| [TextInput](../reference/apis-arkui/js-apis-arkui-frameNode.md#textinput12) | ARKUI_NODE_TEXT_INPUT | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributetextinput20) | [bindController](../reference/apis-arkui/js-apis-arkui-frameNode.md#bindcontrollertextinput20) |
| [TextArea](../reference/apis-arkui/js-apis-arkui-frameNode.md#textarea14) | ARKUI_NODE_TEXT_AREA | [getAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#getattributetextarea20) | [bindController](../reference/apis-arkui/js-apis-arkui-frameNode.md#bindcontrollertextarea20) |
