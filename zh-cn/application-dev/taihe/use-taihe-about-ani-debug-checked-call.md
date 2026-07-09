# 为Taihe生成的ANI代码开启Debug模式
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## Debug模式简介

Taihe在ANI场景下提供按需开启的Debug模式，用于在桥接调用过程中对关键ANI调用结果执行额外校验。

该模式适合在开发、调试和联调阶段使用，帮助开发者尽早发现ANI桥接代码中的类名错误、方法签名不匹配、对象访问异常或线程环境不正确等问题。当某次ANI调用返回异常状态时，程序会立即输出错误信息并终止执行，避免错误延后暴露而增加定位成本。

该模式默认关闭，开发者在构建承载Taihe ANI生成代码的动态链接库时定义`TH_ANI_ENABLE_CHECKED_CALL`后，即可在运行时对调用失败进行即时检测。

## 基本概念

开启`TH_ANI_ENABLE_CHECKED_CALL`后，Taihe会对ANI调用结果做额外检查。

如果某次ANI调用返回异常状态，程序会立即输出错误信息并终止执行，这样可以更早暴露类名、方法签名、对象访问或线程环境等问题，而不是把错误延后到更难定位的位置。

## 适用场景和限制

Debug模式自Taihe编译器工具1.14版本起引入，该Debug模式主要用于Taihe生成的ANI桥接代码中，适用于所有通过Taihe IDL定义并生成ANI代码的接口调用。

可以通过开启Debug模式暴露出的错误场景包括：

- 反向调用的方法或函数对象在Taihe IDL中被声明为`@noexcept`或开启了`-Cnoexcept-all`，但实际调用时在ArkTS侧抛出了异常。
  ```text
  [FATAL] Assertion failed: (() => void) failed with status 6
  ```
- ArkTS对象被转换为Taihe C++对象时失败。例如ArkTS侧传递了一个不合法的联合类型值等。
  ```text
  [FATAL] Assertion failed: Invalid ANI value for type NumberOrString
  ```
- Taihe C++对象被转换为ArkTS对象时失败。例如C++侧传递了一个不合法的枚举值等。
  ```text
  [FATAL] Assertion failed: ANI call Enum_GetEnumItemByIndex failed with status 7
  ```
- Taihe未能获取到ANI VM（ANI虚拟机对象的指针），这通常需要排查在调用Taihe ANI相关接口时，所在动态链接库中的ANIRegister（即Taihe工具生成的ANI接口的注册函数）是否已被调用过。
  ```text
  [ERROR] ANI VM is not set
  ```

以下ANI接口调用错误通常情况下不会发生，只会出现在环境配置错误、虚拟机版本不匹配等情况下，但作为防御性检查也会被Debug模式捕获并暴露：

- 导入so时，ArkTS native函数/方法绑定失败。
- 查找了不存在的类型。
- 查找了某个类型中不存在的方法或字段。
- 其他内部ANI接口调用错误，如抛出/捕获异常失败、无法获取/释放当前线程环境等。

除此之外，Debug模式不会对业务逻辑错误以及其他非ANI调用过程中的错误进行捕获和暴露。

## 使用方法

此处以CMake为例，说明如何在构建承载Taihe ANI生成代码的动态链接库时定义`TH_ANI_ENABLE_CHECKED_CALL`。

```cmake
# ...

include_directories(
    ${NATIVERENDER_ROOT_PATH}
    ${NATIVERENDER_ROOT_PATH}/include
    ${TAIHE_RUNTIME_INCLUDE}
    ${TAIHE_GEN_INCLUDE}
)

# 添加如下编译宏定义以开启ANI Debug模式
add_compile_definitions(TH_ANI_ENABLE_CHECKED_CALL)

add_library(entry SHARED
    ${TAIHE_RUNTIME_SRC}
    ${TAIHE_GEN_SRC}
    demo.impl.cpp
    ani_constructor.cpp
)

# 如果需要使用HiLog输出日志，则需要链接libhilog_ndk.z.so库
target_link_libraries(entry PUBLIC libhilog_ndk.z.so)
```

修改完成后重新构建动态链接库，即可在运行时启用Debug模式。

## 使用示例

假设在Taihe IDL中有如下接口定义：

**demo.taihe**

```rust
function testInvalidThrow(callback: @noexcept () => void): void;
```

在C++侧的实现如下：

**demo.impl.cpp**

```cpp
#include "demo.impl.hpp"

void testInvalidThrow(std::function<void()> callback) {
    callback();
}

TH_EXPORT_CPP_API_testInvalidThrow(testInvalidThrow);
```

如果在ArkTS侧调用`testInvalidThrow`时传入了一个会抛出异常的函数对象，例如：

**main.ets**

```typescript
import { testInvalidThrow } from 'demo';

loadLibrary("demo");

function main() {
  testInvalidThrow(() => {
      throw new Error("This is an invalid throw");
  });
}
```

当开启`TH_ANI_ENABLE_CHECKED_CALL`后，运行时会立即捕获到这个异常，并输出如下错误信息：

```text
[FATAL] Assertion failed: (() => void) failed with status 6
```

此外，可以同时开启性能拆解模式（参考[为Taihe生成的ANI代码开启性能拆解模式](use-taihe-about-ani-perf-trace.md)）看到Trace信息，帮助进一步定位是参数转换、Native调用还是返回值转换过程中发生了异常：

```text
[TRACE] [demo.testInvalidThrow::param::callback] Start
[TRACE] [demo.testInvalidThrow::param::callback] End, duration = 123ns
[TRACE] [demo.testInvalidThrow::call] Start
[FATAL] Assertion failed: (() => void) failed with status 6
```

如上所示，异常发生在`demo.testInvalidThrow`的Native调用阶段，且参数转换阶段已经成功完成。
