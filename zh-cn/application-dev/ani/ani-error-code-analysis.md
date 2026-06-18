# 错误码分析
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

每个ANI接口调用都会返回对应的状态码，用于判断接口调用是否成功、存在什么问题。

```cpp
typedef enum {
    ANI_OK,
    ANI_ERROR,
    ANI_INVALID_ARGS,
    ANI_INVALID_TYPE,
    ANI_INVALID_DESCRIPTOR,
    ANI_INCORRECT_REF,
    ANI_PENDING_ERROR,
    ANI_NOT_FOUND,
    ANI_ALREADY_BINDED,
    ANI_OUT_OF_REF,
    ANI_OUT_OF_MEMORY,
    ANI_OUT_OF_RANGE,
    ANI_BUFFER_TO_SMALL,
    ANI_INVALID_VERSION,
    ANI_AMBIGUOUS,
} ani_status;
```

| 枚举 | 值 | 描述 | 注意事项 |
| ------------------------ | ----- | -------------------------- | ------------------------- |
| `ANI_OK`                 | 0     | 成功                       | -                         |
| `ANI_ERROR`              | 1     | 通用Error                  | 需要进一步调查             |
| `ANI_INVALID_ARGS`       | 2     | 无效参数                   | 参数中可能存在空指针       |
| `ANI_INVALID_TYPE`       | 3     | 类型无效                   |  返回值不匹配              |
| `ANI_INVALID_DESCRIPTOR` | 4     | 描述符无效                 | Mangling问题               |
| `ANI_INCORRECT_REF`      | 5     | 引用不正确                 | -                          |
| `ANI_PENDING_ERROR`      | 6     | ArkTS中抛出异常            | ArkTS-level error          |
| `ANI_NOT_FOUND`          | 7     | 未找到                     | FindXXX failed             |
| `ANI_ALREADY_BINDED`     | 8     | 已绑定                     | 重复的native绑定            |
| `ANI_OUT_OF_REF`         | 9     | 引用超出范围               | 数组越界                    |
| `ANI_OUT_OF_MEMORY`      | 10    | 内存不足                   | -                          |
| `ANI_OUT_OF_RANGE`       | 11    | 超出范围                   | -                          |
| `ANI_BUFFER_TO_SMALL`    | 12    |  缓冲区过小                | -                          |
| `ANI_INVALID_VERSION`    | 13    | 版本无效                   | 常见于VM创建时              |
| `ANI_AMBIGUOUS`          | 14    | 存在歧义                   | 避免在签名中使用nullptr     |


建议开发者对于每个ANI接口调用都要校验接口返回的状态码是否为`ANI_OK`，如果不是，需要把对应的状态码打印出来以便问题定位。

```cpp
ani_class cls;
ani_status status = env->FindClass("std.core.String", &cls);
if (status != ANI_OK) {
    std::cerr << "FindClass 'std.core.String' Failed, status: " << status << std::endl;
    return;
}
```

## 错误码2：`ANI_INVALID_ARGS`
这表明某个参数是非法的`nullptr`。

示例：

```cpp
Object_CallMethodByName_Boolean(nullptr, ...);
```

## 错误码6：`ANI_PENDING_ERROR`
该错误码表示在执行当前的ANI操作期间，ArkTS运行时（VM）内部抛出了一个异常，且该异常尚未被C++侧/ArkTS侧捕获或处理。这通常对应于ArkTS代码中的`throw new Error(...)`，或者运行时错误（如类型不匹配、访问未定义属性等）。

当`ANI_PENDING_ERROR`发生时，该`ani_env`处于“异常挂起”状态。在此状态被清除之前，绝大多数后续的ANI函数调用都会直接失败（通常也返回`ANI_PENDING_ERROR`），而不会执行任何实际操作。

> **注意：**
>
> 必须先清除异常，才能继续调用其他ANI接口。可使用以下代码捕获并描述该异常：

```cpp
// Code that causes error...
ani_boolean errorExists;
env->ExistUnhandledError(&errorExists);
// Log `errorExists`: true or false

std::ostringstream buffer;
std::streambuf *oldStderr = std::cerr.rdbuf(buffer.rdbuf());
ani_status status = env->DescribeError();
std::cerr.rdbuf(oldStderr);
std::string output = buffer.str();
// Log captured `output`
```
该异常同样可以在ArkTS侧被捕获

```typescript
// ArkTS代码
try {
    // 调用可能存在出现未处理异常的函数
    nativeLib.triggerException();
} catch (e) {
    // 这里会捕获到Error传递的消息
    console.error("Caught an exception from Native side!");
    console.error("Error Message: " + e.message);
}
```

## 错误码7：`ANI_NOT_FOUND`
要确保`.d.ets`和`.ets`文件完全一致。否则，native方法在设备上可能总是失败。
```ts
// .d.ets文件
class A {
    foo(i: int): void // 不匹配
}

// .ets文件
class A {
    foo(): void // 不匹配
}
```

## 错误码14：`ANI_AMBIGUOUS`

当存在重载且在mangling中使用`nullptr`时会出现此错误：

```cpp
// .ets文件
function foo(i: int): void;
function foo(d: number): void;

// .cpp文件
FindMethod(cls, "foo", nullptr, &method); // 错误
FindMethod(cls, "foo", "d:", &method);   // 正确
```

