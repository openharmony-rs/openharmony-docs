# 错误处理 Exception
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

native实现检测到业务错误时，可以构造ArkTS异常并抛回调用侧，由ArkTS侧按普通异常流程捕获。这个流程适合需要中断当前ArkTS调用链的错误场景。

## 抛出异常
基类：`Error` Mangling：`C{escompat.Error}`

若要抛出自定义错误，需继承该基类。

> **注意：**
>
> 系统声明的`BusinessError`可能会与native构造函数产生绑定冲突。

**示例：**

```cpp
// 1. 查找Error类及其构造函数。
static constexpr std::string_view message = "This will show message!";

ani_class errCls;
const char* className = "escompat.Error";
ani_status status = env->FindClass(className, &errCls);
if (status != ANI_OK) {
    // handle error and return
}
ani_method errCtor {};
status = env->Class_FindMethod(errCls, "<ctor>", "C{std.core.String}C{escompat.ErrorOptions}:", &errCtor);
if (status != ANI_OK) {
    // handle error and return
}

// 2. 构造message字符串。
ani_string resultString {};
status = env->String_NewUTF8(message.data(), message.size(), &resultString);
if (status != ANI_OK) {
    // handle error and return
}

// 3. 创建Error实例并抛出。ErrorOptions为可选参数，省略时需显式传入undefined。
ani_ref undefinedRef {};
status = env->GetUndefined(&undefinedRef);
if (status != ANI_OK) {
    // handle error and return
}
ani_object errObj {};
status = env->Object_New(errCls, errCtor, &errObj, resultString, undefinedRef);
if (status != ANI_OK) {
    // handle error and return
}
status = env->ThrowError(static_cast<ani_error>(errObj));
if (status != ANI_OK) {
    // handle error and return
}
```

## 捕获异常

1. 同步情况：

   ```ts
   try {
     nativeThrowError();
   } catch (e: Error) {
     console.info(e.message);
   }
   ```

2. 异步情况：使用`.catch()`

