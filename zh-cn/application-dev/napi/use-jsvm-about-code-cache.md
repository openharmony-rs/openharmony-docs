# 使用code cache加速编译
<!--Kit: NDK Development-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

##code cache简介

JSVM提供了生成并使用code cache加速编译过程的方法，其获取和使用分为下面几个部分：

- 首先使用compile系列接口编译得到JSVM_Script
- 使用OH_JSVM_CreateCodeCache接口，传递编译完成后生成的JSVM_Script
- 将OH_JSVM_CreateCodeCache生成的code cache保存，等待下一次编译时，作为参数传入compile系列接口

通过上述流程，将会在使用code cache的那次编译中，极大减少编译时间，其原理为将编译完成的script序列化，然后使用code cache编译时就不再需要重新解析/编译已经被序列化的函数，只需要进行一次反序列化即可，这样编译就简化为了一次数据读取。

##code cache校验规格说明
| 规格       | 规格说明                                            |
| ---------- | -------------------------------------------------- |
| 完整性校验  | 校验cache实际长度，是否与生成时一致                 |
| 兼容性校验  | 校验生成cache的JSVM版本与编译选项是否与当前一致    |
| 一致性校验  | 校验生成cache的js源码，是否与当前输入源码长度一致  |

## 场景示例

下面的伪代码是一个典型的使用方法，其中第二次编译，如果cacheRejected为true，那么说明code cache被拒绝无法生效，运行时间会与无code cache时间相同；为false则这次运行将会极大加快。

其中使用到的JSVM-API可以参考 [JSVM数据类型与接口说明](./jsvm-data-types-interfaces.md)，这里仅展示调用的步骤。
外层跨语言交互的部分可以参考 [使用JSVM-API实现JS与C/C++语言交互开发流程](./use-jsvm-process.md)。

```c++
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
#include <string>

JSVM_Value UseCodeCache(JSVM_Env env, JSVM_CallbackInfo info) {
    // 编译参数准备
    JSVM_Value jsSrc;
    JSVM_Script script;
    JSVM_Value result;
    size_t length = 0;
    const uint8_t* dataPtr = nullptr;
    bool cacheRejected = true;
    static std::string src = R"JS(
        a = 65536;
        b = 32768;
        c = a + b;
    )JS";

    // 生成code cache
    {
        JSVM_HandleScope handleScope;
        OH_JSVM_OpenHandleScope(env, &handleScope);

        // 源码字符串转换为js字符串
        OH_JSVM_CreateStringUtf8(env, src.c_str(), src.size(), &jsSrc);

        // 编译js代码
        OH_JSVM_CompileScript(env, jsSrc, nullptr, 0, true, nullptr, &script);

        // 执行js代码
        OH_JSVM_RunScript(env, script, &result);
        int value = 0;
        OH_JSVM_GetValueInt32(env, result, &value);
        OH_LOG_INFO(LOG_APP, "first run result: %{public}d\n", value);

        if (dataPtr == nullptr) {
            // 将js源码编译出的脚本保存到cache, 可以避免重复编译, 带来性能提升
            OH_JSVM_CreateCodeCache(env, script, &dataPtr, &length);
        }

        OH_JSVM_CloseHandleScope(env, handleScope);
    }

    // 使用code cache
    {
        JSVM_HandleScope handleScope;
        OH_JSVM_OpenHandleScope(env, &handleScope);

        // 源码字符串转换为js字符串
        OH_JSVM_CreateStringUtf8(env, src.c_str(), src.size(), &jsSrc);

        // 使用code cache编译js代码
        OH_JSVM_CompileScript(env, jsSrc, dataPtr, length, true, &cacheRejected, &script);

        // 执行js代码
        OH_JSVM_RunScript(env, script, &result);
        int value = 0;
        OH_JSVM_GetValueInt32(env, result, &value);
        OH_LOG_INFO(LOG_APP, "second run result: %{public}d\n", value);

        OH_JSVM_CloseHandleScope(env, handleScope);
    }
    OH_LOG_INFO(LOG_APP, "cache rejected: %{public}d\n", cacheRejected);
    return result;
}

// Register a callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = UseCodeCache}
};
static JSVM_CallbackStruct *method = param;
// Register the C++ callback as a JSVM globalThis.UseCodeCache property for the JS to call.
static JSVM_PropertyDescriptor descriptor[] = {
    {"UseCodeCache", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};

// 样例测试js
const char* srcCallNative = R"JS(globalThis.UseCodeCache())JS";
```
<!-- @[jsvm_code_cache](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/JSVMAPI/JsvmDebug/aboutcodecache/src/main/cpp/hello.cpp) -->

预期的输出结果如下：
```
first run result: 98304
second run result: 98304
cache rejected: 0
```

## 注意事项

上述代码中使用了code cache进行编译：`OH_JSVM_CompileScript(env, jsSrc, dataPtr, length, true, &cacheRejected, &script);`
这个接口的传入参数中包含cacheRejected，用于接收实际编译过程中code cache是否被拒绝的状态，具体包括多种情况：

-code cache校验失败
-code cache校验成功
- 内存中存在编译缓存，code cache没有被校验

对于第一种情况，这个参数会被设置为true，而后两种情况都是false，因此需要注意即使reject为false，也不能说明code cache被接收了。
