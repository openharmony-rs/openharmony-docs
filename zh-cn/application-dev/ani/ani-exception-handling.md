# 错误处理 Exception
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

native实现检测到业务错误时，可以构造ArkTS异常并抛回调用侧，由ArkTS侧按普通异常流程捕获。这个流程适合需要中断当前ArkTS调用链的错误场景。

## 抛出异常
基类：`Error` Mangling：`C{std.core.Error}`

若要抛出自定义错误，需继承该基类。

> **注意：**
>
> 系统声明的`BusinessError`可能会与native构造函数产生绑定冲突。

**示例：**

```cpp
void ThrowError(ani_env *env)
{
    static constexpr std::string_view message = "This will show message!";

    ani_class errCls;
    const char* className = "std.core.Error";
    env->FindClass(className, &errCls);
    ani_method errCtor {};
    env->Class_FindMethod(errCls, "<ctor>", "C{std.core.String}C{std.core.ErrorOptions}:", &errCtor);

    ani_string resultString {};
    env->String_NewUTF8(message.data(), message.size(), &resultString);
    ani_ref undefinedRef {};
    env->GetUndefined(&undefinedRef);

    ani_object errObj {};
    env->Object_New(errCls, errCtor, &errObj, resultString, undefinedRef);
    env->ThrowError(static_cast<ani_error>(errObj));
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

