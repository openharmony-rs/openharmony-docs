# 为Taihe生成的ANI代码开启性能拆解模式
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 性能拆解模式简介

Taihe在ANI场景下提供按需开启的性能拆解模式，该模式旨在拆解分析ArkTS与Native之间单次桥接调用的各阶段耗时。

该模式适合在性能分析、联调和热点定位阶段使用，帮助开发者区分耗时主要发生在参数转换、Native执行还是返回值转换阶段。当运行环境支持HiTrace时，可以在HiTrace结果中查看这些阶段的耗时信息；不支持HiTrace时，则会在控制台输出本地trace日志，便于快速判断瓶颈位置。

该模式默认关闭，开发者在构建承载Taihe ANI生成代码的动态链接库时定义`TH_ANI_ENABLE_PERF_TRACE`后，即可在运行时观察一次桥接调用各阶段的耗时信息。

## 基本概念

性能拆解模式自Taihe编译器工具1.10版本起引入，自该版本后，Taihe会在生成的ANI桥接代码中增加分阶段的trace信息。编译相应文件时如果定义`TH_ANI_ENABLE_PERF_TRACE`宏，则在运行时每次调用都会输出参数转换、Native调用和返回值转换等阶段的耗时信息。

一次调用通常会被拆分为以下几个阶段：

- 参数转换
- Native调用
- 返回值转换

开启性能拆解模式后，如果当前环境支持HiTrace，可以在对应的HiTrace结果中查看这些阶段的耗时信息；如果当前环境不支持HiTrace，则会直接在控制台输出本地trace日志。

## 适用场景

- 需要分析ArkTS和C++之间桥接耗时时。
- 需要判断耗时主要出现在参数处理、Native执行还是返回值回传阶段时。
- 需要在联调阶段快速定位性能热点时。

## 使用方法

以下面的Taihe IDL文件为例：

**idl/math_demo.taihe**

```taihe
function add(a: i32, b: i32): i32;
```

首先使用`taihec`命令生成ANI桥接代码：

```bash
taihec idl/math_demo.taihe -Ogenerated -Gani-bridge -Gcpp-author
```

然后实现相应的作者侧代码：

**author/src/math_demo.impl.cpp**

```cpp
#include "math_demo.impl.hpp"

int32_t add(int32_t a, int32_t b)
{
    return a + b;
}

TH_EXPORT_CPP_API_add(add);
```

**author/ani_constructor.cpp**

```cpp
#include "math_demo.ani.hpp"

ANI_EXPORT ani_status ANI_Constructor(ani_vm *vm, uint32_t *result)
{
    ani_env *env;
    if (ANI_OK != vm->GetEnv(ANI_VERSION_1, &env)) {
        return ANI_ERROR;
    }
    if (ANI_OK != math_demo::ANIRegister(env)) {
        std::cerr << "Error from math_demo::ANIRegister" << std::endl;
        return ANI_ERROR;
    }
    *result = ANI_VERSION_1;
    return ANI_OK;
}
```

当编译上述代码时，在构建承载Taihe ANI生成代码的动态链接库的编译选项中增加`TH_ANI_ENABLE_PERF_TRACE`宏定义，例如：

```cmake
# ...

include_directories(
    ${NATIVERENDER_ROOT_PATH}
    ${NATIVERENDER_ROOT_PATH}/include
    ${TAIHE_RUNTIME_INCLUDE}
    ${TAIHE_GEN_INCLUDE}
)

# 添加如下编译宏定义以开启ANI性能拆解模式
add_compile_definitions(TH_ANI_ENABLE_PERF_TRACE)

add_library(entry SHARED
    ${TAIHE_RUNTIME_SRC}
    ${TAIHE_GEN_SRC}
    math_demo.impl.cpp
    ani_constructor.cpp
)

# 如果需要在运行时输出HiTrace信息，则需要链接libhitrace_ndk.z.so库
target_link_libraries(entry PUBLIC libhitrace_ndk.z.so)
```

修改完成后重新构建动态链接库，即可在运行时启用性能拆解模式。

## 开启后的效果

开启后，在调用上面的函数时，可以看到一次调用在不同阶段的耗时信息。

```typescript
import * as math_demo from "math_demo";

loadLibrary("math_demo");

function main() {
    console.info("1 + 2 = " + math_demo.add(1, 2));
}
```

例如，在不具备系统Trace展示能力的环境中，可能看到类似输出：

```text
// 各参数转换耗时
[TRACE] [math_demo.add::param::a] Start
[TRACE] [math_demo.add::param::a] End, duration = 123ns
[TRACE] [math_demo.add::param::b] Start
[TRACE] [math_demo.add::param::b] End, duration = 234ns

// Native调用耗时
[TRACE] [math_demo.add::call] Start
[TRACE] [math_demo.add::call] End, duration = 567ns

// 返回值转换耗时
[TRACE] [math_demo.add::return] Start
[TRACE] [math_demo.add::return] End, duration = 321ns
```

如果在HiTrace环境中运行，则可以在HiTrace结果中看到类似如下的输出：

```text
$ hitrace --trace_begin app  # 开启trace
$ hitrace --trace_level D  # 设置trace级别为Debug
$ hitrace --trace_dump | grep test_taihe_ani  # 查看trace结果
 .test_taihe_ani-6247    (   6247) [010] .... 474102.425404: tracing_mark_write: B|6247|H:math_demo.add::param::a|D62
 .test_taihe_ani-6247    (   6247) [010] .... 474102.425404: tracing_mark_write: E|6247|D62
 .test_taihe_ani-6247    (   6247) [010] .... 474102.425405: tracing_mark_write: B|6247|H:math_demo.add::param::b|D62
 .test_taihe_ani-6247    (   6247) [010] .... 474102.425405: tracing_mark_write: E|6247|D62
 .test_taihe_ani-6247    (   6247) [010] .... 474102.425406: tracing_mark_write: B|6247|H:math_demo.add::call|D62
 .test_taihe_ani-6247    (   6247) [010] .... 474102.425419: tracing_mark_write: E|6247|D62
 .test_taihe_ani-6247    (   6247) [010] .... 474102.425420: tracing_mark_write: B|6247|H:math_demo.add::return|D62
 .test_taihe_ani-6247    (   6247) [010] .... 474102.425420: tracing_mark_write: E|6247|D62
$ hitrace --trace_finish  # 关闭trace
```

对于以上输出的进一步分析和理解，可以参考[查看HiTraceMeter日志](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/hitracemeter-view)。

通过这些信息，可以快速判断耗时主要集中在参数处理、实际Native执行，还是返回值回传阶段。
