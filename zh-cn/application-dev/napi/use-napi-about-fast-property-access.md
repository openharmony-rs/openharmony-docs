# 使用扩展的Node-API接口加速属性访问

<!--Kit: NDK-->
<!--Subsystem: arkcompiler-->
<!--Owner: @shilei123; @starunvs-->
<!--Designer: @shilei123; @starunvs-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @fang-jinxu-->

从API 24版本开始，OpenHarmony提供了基于调用点缓存的快速属性访问接口。通过为每个调用点创建`napi_callsite_info`句柄，在重复访问相同键名属性时，可以缓存对象的结构信息，从而加速属性访问，显著提升属性访问性能。

> **注意：**
>
> - 每个不同的调用点应创建独立的`napi_callsite_info`句柄，同一句柄可在多次调用中复用。
> - `napi_callsite_info`不支持跨线程使用，每个句柄只能在创建它的线程中使用。
> - 当不再需要时，必须调用`napi_delete_callsite_info`释放`napi_callsite_info`句柄。
> - `napi_get_property_with_callsite_info`和`napi_set_property_with_callsite_info`的info参数可以传入NULL，此时行为等同于普通的`napi_get_property`/`napi_set_property`。
> - `napi_get_property_with_callsite_info`和`napi_set_property_with_callsite_info`支持可为NULL的`hit`输出参数（`bool*`）：true表示命中（快速路径），false表示未命中。

## 场景介绍

当需要对相同的属性键名进行大量重复的属性读写操作时（例如在热点循环中批量处理对象数组），使用调用点缓存可以提升性能。

**性能特征：**

- **缓存命中**（对象具有相同的结构）：性能相比于`napi_get_property`/`napi_set_property`显著提升。
- **缓存失效**：由于额外的检查和回退开销，性能相比普通属性访问接口劣化。
  - 当同一调用点传入对象类型过多时，该调用点对应缓存会溢出并失效，永久回退到慢速路径。
  - **同一`napi_callsite_info`句柄不可同时用于get和set。** Get/Set时缓存的信息不可共用，将用于`napi_get_property_with_callsite_info`的句柄传给`napi_set_property_with_callsite_info`（或反过来），缓存失效，进入慢速路径。

     ```c++
     // 错误示例：同一句柄同时用于 get 和 set，导致缓存失效
     napi_callsite_info shared_info;
     napi_create_callsite_info(env, &shared_info);
     napi_get_property_with_callsite_info(env, obj, key, shared_info, &val, nullptr);
     napi_set_property_with_callsite_info(env, obj, key, new_val, shared_info, nullptr); // 缓存失效！
     napi_delete_callsite_info(env, shared_info);

     // 正确示例：get 和 set 各自使用独立的句柄
     napi_callsite_info get_info, set_info;
     napi_create_callsite_info(env, &get_info);
     napi_create_callsite_info(env, &set_info);
     napi_get_property_with_callsite_info(env, obj, key, get_info, &val, nullptr);
     napi_set_property_with_callsite_info(env, obj, key, new_val, set_info, nullptr); // 正常命中缓存
     napi_delete_callsite_info(env, get_info);
     napi_delete_callsite_info(env, set_info);
     ```
- **缓存未命中**：如果缓存有效但没有命中，由于额外的检查和回退开销，性能相比普通属性访问接口降低10-100%。

**适用场景：**

- 对象结构稳定的批量重复属性访问。
- 对同一键名属性的高频读写。

**不适用场景：**

- 一次性属性访问，缓存初始化开销无法被后续调用摊销。
- 高度多态的对象（同一调用点频繁遇到不同结构的对象），会导致缓存失效，性能会劣化。

## 接口描述

| 接口 | 描述 |
| -------- | -------- |
| [napi_create_callsite_info](../reference/native-lib/napi.md#napi_create_callsite_info) | 创建调用点信息句柄，用于缓存属性访问信息。 |
| [napi_delete_callsite_info](../reference/native-lib/napi.md#napi_delete_callsite_info) | 删除调用点信息句柄，释放关联的缓存资源。 |
| [napi_get_property_with_callsite_info](../reference/native-lib/napi.md#napi_get_property_with_callsite_info) | 使用调用点信息快速获取对象属性值。 |
| [napi_set_property_with_callsite_info](../reference/native-lib/napi.md#napi_set_property_with_callsite_info) | 使用调用点信息快速设置对象属性值。 |

## 示例代码

- 模块注册

   ```c++
   // napi_init.cpp
   #include "napi/native_api.h"
   #include <vector>

   // 使用C++的RAII机制管理napi_callsite_info的生命周期，避免遗漏释放
   // 仅用作示例，也可以通过其他方式进行封装，或直接使用原始接口
   class MyCallsiteInfo
   {
      napi_env env_{};
      napi_callsite_info info_{};

   public:
      explicit MyCallsiteInfo(napi_env env) : env_(env)
      {
         if (napi_create_callsite_info(env, &info_) != napi_ok)
         {
             info_ = nullptr;
             // logging
         }
      }
      ~MyCallsiteInfo()
      {
         if (info_ != nullptr) {
               napi_delete_callsite_info(env_, info_);
         }
      }
      napi_callsite_info get() const { return info_; }
   };

   // 示例：批量读取对象数组中指定属性名的值
   // 注意：此处的 csInfo 仅用于 get，不可同时用于 set（需另建句柄）
   static napi_value NAPI_Global_batchGetProperty(napi_env env, napi_callback_info info)
   {
      napi_value args[2]{};
      size_t argc = 2;
      napi_get_cb_info(env, info, &argc, args, /* thisVar */ nullptr, /* data */ nullptr);
      if (argc < 2) {
         return nullptr;
      }

      // args[0]为对象数组，args[1]为属性键名
      uint32_t length = 0;
      napi_get_array_length(env, args[0], &length);

      // 创建调用点信息，缓存对象结构以加速后续访问
      MyCallsiteInfo csInfo(env);

      napi_value result;
      napi_create_array_with_length(env, length, &result);

      for (uint32_t i = 0; i < length; i++) {
         napi_value element;
         napi_get_element(env, args[0], i, &element);

         napi_value val;
         napi_get_property_with_callsite_info(env, element, args[1], csInfo.get(), &val, nullptr);

         napi_set_element(env, result, i, val);
      }

      return result;
   }

   // 示例：批量设置对象数组中指定属性名的值
   static napi_value NAPI_Global_batchSetProperty(napi_env env, napi_callback_info info)
   {
      napi_value args[3]{};
      size_t argc = 3;
      napi_get_cb_info(env, info, &argc, args, /* thisVar */ nullptr, /* data */ nullptr);
      if (argc < 3) {
         return nullptr;
      }

      // args[0]为对象数组，args[1]为属性键名，args[2]为要设置的值
      uint32_t length = 0;
      napi_get_array_length(env, args[0], &length);

      MyCallsiteInfo csInfo(env);

      for (uint32_t i = 0; i < length; i++) {
         napi_value element;
         napi_get_element(env, args[0], i, &element);

         napi_set_property_with_callsite_info(env, element, args[1], args[2], csInfo.get(), nullptr);
      }

      napi_value undefined;
      napi_get_undefined(env, &undefined);
      return undefined;
   }

   // 模块注册
   EXTERN_C_START
   static napi_value Init(napi_env env, napi_value exports)
   {
      std::vector<napi_property_descriptor> desc{
         {"batchGetProperty", nullptr, NAPI_Global_batchGetProperty, nullptr, nullptr, nullptr, napi_default, nullptr},
         {"batchSetProperty", nullptr, NAPI_Global_batchSetProperty, nullptr, nullptr, nullptr, napi_default, nullptr},
      };
      napi_define_properties(env, exports, desc.size(), desc.data());
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

   extern "C" __attribute__((constructor)) void RegisterEntryModule(void)
   {
      napi_module_register(&demoModule);
   }
   ```

- 接口声明

   ```ts
   // index.d.ts
   export const batchGetProperty: (objects: object[], key: string) => (string | number | boolean | undefined | null)[];
   export const batchSetProperty: (objects: object[], key: string, value: string | number | boolean) => void;
   ```

- ArkTS代码示例：

   ```ts
   // index.ets
   import testNapi from "libentry.so"

   class Item {
      name: string = '';
      value: string = '';

      constructor(name: string, value: string) {
         this.name = name;
         this.value = value;
      }
   }

   @Entry
   @Component
   struct Index {
      @State message: string = '点击运行示例';

      build() {
         Row() {
            Column() {
               Text(this.message)
                  .fontSize(20)
                  .fontWeight(FontWeight.Bold)
                  .onClick(() => {
                     // 构造一批具有相同结构的对象
                     const objects: Item[] = [];
                     for (let i = 0; i < 3; i++) {
                        objects.push(new Item(`item_${i}`, `val_${i}`));
                     }

                     // 使用napi_get_property_with_callsite_info批量读取属性
                     const names = testNapi.batchGetProperty(objects, "name");
                     // 预期结果: ["item_0","item_1","item_2"]

                     // 使用napi_set_property_with_callsite_info批量设置属性
                     testNapi.batchSetProperty(objects, "value", "updated");
                     const values = testNapi.batchGetProperty(objects, "value");
                     // 预期结果: ["updated","updated","updated"]

                     this.message = `get "name": ${JSON.stringify(names)}\nget "value" after set: ${JSON.stringify(values)}`;
                  })
            }
            .width('100%')
         }
         .height('100%')
      }
   }
   ```
