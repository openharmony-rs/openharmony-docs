# ANI简介
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

## 什么是ANI？

**ANI**（ArkTS Native Interface）是ArkTS虚拟机（ArkRuntime）的核心组成部分，它为ArkTS 1.2代码与native代码（如C, C++）之间的双向交互提供了一套标准的接口规范。

与ArkTS 1.0（基于JavaScript）所使用的NAPI（Node-API）不同，ANI是为静态类型的ArkTS 1.2全新设计的。强调在编译期确定类型信息，提供更高效，类型更安全的互操作能力。

## 开发调试：VerifyANI

**VerifyANI**是ANI的验证模式：在调用进入Release实现之前，对`ani_env` / `ani_vm`的入参、引用合法性、调用上下文等做额外校验，并输出结构化诊断信息，帮助在开发阶段尽早发现误用ANI API的问题（例如空指针、非法引用、跨线程使用`ani_env`等）。实现上通过替换`c_api`函数表，在常规实现与验证实现之间透明切换；公开API签名与语义不变。

> **注意：**
>
> VerifyANI会带来一定性能开销，仅建议在开发、调试、CI或专项测试中启用，**不要**在正式发布版本中默认开启。

### VerifyANI的启用方式

| 场景                       | 启用方式                              | 生效时机    |
| -------------------------- | ------------------------------------ | ---------- |
| OpenHarmony应用进程        | 系统参数`debug.verifyANI.enable=true` | 应用启动时  |
| 自管VM的原生程序/单元测试   | `ANI_CreateVM`传入`--verify:ani`      | 创建VM时    |
| 使用Ark运行时命令行启动ETS  | 运行时选项`--verify-ani`              | VM初始化时  |

**方式一：通过OpenHarmony系统参数（应用进程，推荐）**

+ 在OpenHarmony系统中，针对应用进程启用VerifyANI最常用的方式是通过设置系统参数。应用VM多在appspawn预建、通常不带`--verify:ani`，通过系统参数在**应用Postfork后**启用VerifyANI；修改参数后需重启应用。

+ 在设备上执行命令来启用或禁用VerifyANI：
    + 启用：`hdc shell param set debug.verifyANI.enable true`
    + 禁用：`hdc shell param set debug.verifyANI.enable false`

**方式二：通过`ANI_CreateVM`启动选项**

+ 对于自管的VM原生程序或单元测试，可以在创建VM时通过`ANI_CreateVM`传入`--verify:ani`选项来启用VerifyANI。
+ 示例代码片段：

    ```cpp
    std::array vmOptions {
        ani_option {"--ext:boot-panda-files=/path/to/etsstdlib.abc", nullptr},
        ani_option {"--verify:ani", nullptr},
    };

    ani_options createVmArgs {vmOptions.size(), vmOptions.data()};
    ani_vm *vm = nullptr;
    ani_status status = ANI_CreateVM(&createVmArgs, ANI_VERSION_1, &vm);
    ```

+ 通过这种方式，可以在VM创建时立即启用VerifyANI。

**方式三：通过Ark CLI选项**

+ 若通过Ark ETS运行时（如`ark`/相关测试启动器）以命令行创建VM，可在运行时参数中增加`--verify-ani`。

+ 示例命令行（具体可执行文件名以本地构建产物为准）：

    ```bash
    # 在已有panda/ark启动命令后追加
    ./ark --boot-panda-files=$ENV{PANDA_HOME}/plugins/ets/etsstdlib.abc --load-runtimes=ets --verify-ani ${target_name}.abc ${target_name}.ETSGLOBAL::main
    ```

+ 这种方式适用于通过命令行工具启动的应用或测试场景，在VM初始化时即启用VerifyANI来执行验证。

## 参考资源

| 名称 | 资源链接 | 主要用途 | 定位 |
| ---- | ---- | ---- | ---- |
| ANI接口测试套件 | **[ani/tests测试文件夹](https://gitcode.com/openharmony/arkcompiler_runtime_core/tree/master/static_core/plugins/ets/tests/ani/tests)** | 验证ANI函数及其正确性；始终保持功能可用 | API用法参考 |
| ani.h头文件 | **[ani.h](https://gitcode.com/openharmony/arkcompiler_runtime_core/blob/master/static_core/plugins/ets/runtime/ani/ani.h)** | 核心定义文件，包括函数声明、类型和继承关系 | 所有定义的来源 |
| ArkTS语言规范 | **[下载地址](https://gitcode.com/openharmony/arkcompiler_runtime_core/releases/OpenHarmony-v6.0-Release)** | 提供ArkTS语言的各种规范文档下载 | ArkTS语言规范参考资料 |

