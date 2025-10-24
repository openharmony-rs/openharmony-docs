# Node-API模块解耦复用实践指导

## 解耦设计在鸿蒙生态中的必要性与优势
在鸿蒙跨语言开发中，ArkTS通过Node-API调用C++模块是常见模式。随着业务复杂度和跨平台需求的增加，对C++模块进行分层解耦成为关键的设计原则。良好的分层设计使Node-API模块在支持ANI时，能复用相同代码逻辑，降低开发工作量。通过将代码明确划分为以下两层：

1. Node-API胶水层：处理ArkTS与C++的类型转换和交互逻辑
2. 核心逻辑层：实现平台无关的业务算法与数据处理

### 分层架构的核心优势

这种分层架构的设计带来了显著的工程价值，主要体现在以下方面：

1. 提升代码可维护性
  - **职责分离**：Node-API 胶水层负责 ArkTS 与 C++ 之间的数据类型转换和接口映射，核心逻辑层独立处理业务计算，降低模块间耦合度。
  - **修改隔离**：当 Node-API 接口或 ArkTS 调用方式调整时，仅需修改胶水层，核心业务逻辑无需变更，减少回归测试范围，提高维护效率。

2. 提高代码可扩展性
  - **灵活适配新场景**：新增语言（如 Java、Python）或平台（如 Windows、Linux）时，只需开发对应胶水层，核心逻辑无缝复用。
  - **渐进式演进**：业务逻辑的优化与语言绑定的升级可并行推进，互不干扰，适应快速迭代的需求。

3. 促进跨平台复用
  - **语言无关性**：核心层采用标准 C++ 编写，不依赖特定运行时，可移植到不同系统，如 Android NDK、Linux，或嵌入其他语言环境，如 Swift、Rust。
  - **减少重复劳动**：同一套算法可在多个平台，多套语言环境中共享，显著降低多端一致性的维护成本。

4. 优化团队协作
  - **专业化分工**： 前端开发者专注 ArkTS/Node-API 胶水层，C++ 工程师专注核心算法，提升开发效率和代码质量。
  - **并行开发**：胶水层与逻辑层可独立开发、测试，缩短项目周期。


## 基于Node-API迁移到ANI的解耦实践

为了更直观地展示分层解耦的价值，我们通过图像处理模块的示例，说明如何将紧耦合的Node-API代码重构为分层架构，并迁移至[ANI（ArkTS Native Interface）](../../ani/ani-usage-scenarios.md)。

### 迁移步骤
1. 分析现有Node-API接口：梳理当前混合了胶水逻辑与业务实现的代码。
2. 分层解耦：
   - **语言无关层**：抽离图像处理算法（如灰度化、滤波）。
   - **胶水层**：仅保留Node-API数据类型转换与接口封装。
3. 适配ANI：基于解耦后的结构，替换Node-API胶水层为ANI实现，核心逻辑无需改动。

### 示例：原有紧耦合的Node-API实现
假设有一个Node-API模块，提供一个GrayScale接口处理图像灰度化功能，在此接口中，解析语言变量参数与灰度化功能逻辑在一个文件或函数中完成。代码如下
```cpp
// 紧耦合示例：Node-API 接口直接混入业务逻辑
napi_value GrayScale(napi_env env, napi_callback_info args) {
    // 1. Node-API 参数解析
    napi_value argv[1];
    size_t argc = 1;
    napi_get_cb_info(env, args, &argc, argv, nullptr, nullptr);

    // 2. 直接处理图像灰度化
    uint8_t* pixels;
    size_t length;
    napi_get_arraybuffer_info(env, argv[0], (void**)&pixels, &length);
    for (int i = 0; i < length; i += 4) {
        uint8_t gray = 0.3 * pixels[i] + 0.59 * pixels[i+1] + 0.11 * pixels[i+2];
        pixels[i] = pixels[i+1] = pixels[i+2] = gray;
    }

    return nullptr;
}

// 在exports模块变量里面导出grayScale接口
static napi_value Init(napi_env env, napi_value exports) {
    napi_property_descriptor desc[] = {
        { "grayScale", nullptr, GrayScale, nullptr, nullptr, nullptr, napi_default, nullptr}
    };
    napi_define_properties(env, exports, sizeof(desc)/sizeof(desc[0]), desc);

    return exports;
}
```
问题：业务逻辑与Node-API接口强耦合，要迁移到别的平台或者接口上，需要对全部的函数进行改造，遇到复杂的模块，复用或迁移成本高。


### 解耦后的分层实现
了解了Node-API模块的实现以后，接下来对上述功能进行分层解耦。

1. 提取语言无关的逻辑层（C++）

根据上述代码提供的GrayScale功能主要是根据图像数据进行灰度计算，这部分功能可以提取一个image_processor.cpp文件，此文件提供一个纯c++函数ApplyGrayScale，接收pixelmap的数据，进行灰度计算，在这个函数中不能使用任何Node-API相关的类型与函数。

语言无关核心层（image_processor.cpp）
```cpp
// 纯 C++ 实现，无 Node-API 依赖
void ApplyGrayScale(uint8_t* pixels, size_t length) {
    for (int i = 0; i < length; i += 4) {
        uint8_t gray = 0.3 * pixels[i] + 0.59 * pixels[i+1] + 0.11 * pixels[i+2];
        pixels[i] = pixels[i+1] = pixels[i+2] = gray;
    }
}
```

2. 重构提取Node-API胶水层（NAPI_Glue.cpp）
从原始文件中去掉业务逻辑部分代码，替换成调用image_processor.cpp文件中封装的接口；提取这部分代码到Node-API胶水层NAPI_Glue.cpp中。
```cpp
napi_value GrayScale(napi_env env, napi_callback_info args) {
    // 1. Node-API参数解析
    napi_value argv[1];
    size_t argc = 1;
    napi_get_cb_info(env, args, &argc, argv, nullptr, nullptr);

    // 仅处理数据转换
    uint8_t* pixels;
    size_t length;
    napi_get_arraybuffer_info(env, argv[0], (void**)&pixels, &length);

    // 调用核心逻辑
    ApplyGrayScale(pixels, length);
    return nullptr;
}

// 在exports模块变量里面导出grayScale接口
static napi_value Init(napi_env env, napi_value exports) {
    napi_property_descriptor desc[] = {
        { "grayScale", nullptr, GrayScale, nullptr, nullptr, nullptr, napi_default, nullptr}
    };
    napi_define_properties(env, exports, sizeof(desc)/sizeof(desc[0]), desc);

    return exports;
}
```

### 适配ANI胶水层（ANI_Glue.cpp）
完成上述的接口分层后，要使Native模块能够在ArkTS-ST模式中运行，只需将胶水层从Node-API接口迁移到ANI接口，而业务逻辑层在两种环境中均可复用。

Node-API与ANI的模块注册机制不同。Node-API可以在Native侧完整注册模块，而ANI需在ArkTS侧声明模块，并在函数前添加native关键字，表明函数实现在Native侧。
image_processor.ets文件
```typescript
native function grayScale(data: ArrayBuffer): void;
```
ANI_Glue.cpp文件
```cpp
// ANI 的接口适配（与 Node-API 类似，但接口名不同）
void ANI_GrayScale(ani_env env, ani_arraybuffer data) {
    uint8_t* pixels;
    size_t length;
    if (ANI_OK != env->ArrayBuffer_GetInfo(data, &pixels, &length)) {
        return;
    }

    // 复用同一核心逻辑
    ApplyGrayScale(pixels, length);
}

// 绑定native的grayScale函数
ani_status ANI_Constructor(ani_vm *vm, uint32_t *result)
{
    ...
    static const char *className = "Limage_processor/ETSGLOBAL;";
    ani_class cls;

    if (ANI_OK != env->FindClass(className, &cls)) {
        return ANI_ERROR;
    }
    std::array methods = {
        ani_native_function {"grayScale", "Lstd/core/ArrayBuffer;:v", reinterpret_cast<void*>(ANI_GrayScale)},
    }

    ani_status ret = env->Class_BindNativeMethods(cls, methods.data(), methods.size());
    if (ANI_OK != ret) {
        return ANI_ERROR;
    }
    ...
}
```

通过上述的解耦，重构，ArkTS-DT与ArkTS-ST两种接口可以复用逻辑业务，降低工作量，当中的胶水层后续可以通过工具自动生成。


## 总结
通过上述分层解耦，代码的可维护性、扩展性和复用性全面提升，同时为接口未来迁移到不同语言提供平滑过渡。此模式特别适合长期维护的中大型跨平台项目。

