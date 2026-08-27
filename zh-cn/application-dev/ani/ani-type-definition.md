# 类型定义
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

ANI类型体系由基本类型和扩展对象类型组成，native函数签名、装箱判断和类型转换都依赖这套对应关系。编写native代码时，需要先确认ArkTS侧声明的参数类型，再结合[Mangling规则](ani-name-mangling.md)确定签名，并判断是否需要在`ani_ref`、`ani_object`和具体对象类型之间转换。

## 原生（native）类型/基本类型

```cpp
// ETS基本类型的运行时类型
typedef uint8_t  ani_boolean;  // 布尔型（1字节） ETS声明：boolean
typedef uint16_t ani_char;     // 字符型（2字节） ETS声明：char
typedef int8_t   ani_byte;     // 字节型（1字节） ETS声明：byte
typedef int16_t  ani_short;    // 短整型（2字节） ETS声明：short
typedef int32_t  ani_int;      // 整型（4字节）   ETS声明：int
typedef int64_t  ani_long;     // 长整型（8字节） ETS声明：long
typedef float    ani_float;    // 单精度浮点型    ETS声明：float
typedef double   ani_double;   // 双精度浮点型    ETS声明：double/number
```

`number`是`double`类型的别名。

> 由于`ani_boolean`是`uint8_t`而非`bool`，所以不能直接使用`cout`或别的C++流API进行打印。在输出之前，需要将其转换为`int`类型。

## 扩展类型

| 类型定义 | 描述 | 补充说明 |
| ------------------- | ------------------------- | ------------------------------------------------- |
| `ani_ref`           | 所有引用类型的基类型       | -                                                 |
| `ani_object`        | 任何非基本类型             | 不包括像`ani_int`这样的基本类型                    |
| `ani_error`         | `Error`                   | -                                                 |
| `ani_fn_object`     | `Function/() => void`       | -                                                 |
| `ani_enum_item`     | 枚举项                    | -                                                 |
| `ani_tuple_value`   | 元组值                    | -                                                 |
| `ani_arraybuffer`   | `ArrayBuffer`             | -                                                 |
| `ani_string`        | `string`                  | -                                                 |
| `ani_type`          | 类型对象的基类型           | `ani_class`的基类型                               |
| `ani_class`         | 类类型                    | `ani_module`、`ani_namespace`、`ani_enum`的基类型  |
| `ani_module`        | 模块类型                  | -                                                 |
| `ani_namespace`     | 命名空间类型              | -                                                 |
| `ani_enum`          | 枚举类型                  | -                                                 |
| `ani_fixedarray`    | `FixedArray<T>`           | 引用元素定长数组类型                              |
| `ani_valuearray`    | `ValueArray<T>`           | 基本类型元素定长数组的基类型                      |
| `ani_array`         | `T[]`                     | 等价于`Array<T>`                                  |


如果函数参数期望的是`ani_ref`或`ani_object`，需要传递一个`ani_int`类型的值，则需要将其装箱为`ani_ref`。请参阅[装箱类型](ani-argument-handling.md#装箱类型)。

## 类型转换

如果以下继承链上的类型存在父子关系，则可以使用`static_cast`进行转换。此链之外的类型不能转换为`ani_ref`或`ani_object`，一个典型的例子是`ani_method`。

然而，这种转换必须确保该类型在ETS运行时层是可用的。例如，将一个`ani_string`转换为`ani_ref`后，再尝试将其当作`ani_array`使用，将会导致运行时崩溃。

```text
ani_ref
├── ani_object
│   ├── ani_fn_object
│   ├── ani_enum_item
│   ├── ani_error
│   ├── ani_tuple_value
│   ├── ani_arraybuffer
│   ├── ani_string
│   ├── ani_type
│   │   └── ani_class
│   │       ├── ani_module
│   │       ├── ani_namespace
│   │       └── ani_enum
│   ├── ani_array
│   ├── ani_fixedarray
│   └── ani_valuearray
│       ├── ani_valuearray_boolean
│       ├── ani_valuearray_char
│       ├── ani_valuearray_byte
│       ├── ani_valuearray_short
│       ├── ani_valuearray_int
│       ├── ani_valuearray_long
│       ├── ani_valuearray_float
│       └── ani_valuearray_double
```
例如`auto str = static_cast<ani_string>(string_ref);`

- 如何将`ani_int` / `ani_double`等基本类型转换为`ani_ref`？

    请参考[装箱类型](ani-argument-handling.md#装箱类型)中的“装箱”过程。

## 类型识别：Object_InstanceOf

参数中的`ani_object`代表所有非基本对象类型。如果存在像`A | B`这样的联合类型参数，则必须使用`Object_InstanceOf`来识别实际类型。

```ts
type DataType = string | ArrayBuffer | ValueArray<int> | FixedArray<string>
native function handleData(data: DataType): void

function main(){
    loadLibrary("libraryName")
    handleData("hello")                 // 将会输出 "Object is String; content: hello"
    handleData(new ArrayBuffer(1024))   // 将会输出 "Object is ArrayBuffer; length: 1024"
    handleData(new ValueArray<int>())      // 将会输出 "Object is ValueArray"
    handleData(new FixedArray<string>())   // 将会输出 "Object is FixedArray"
}
```

```cpp
static void handleData_union(ani_env *env, ani_object union_obj) {
    // 注意：在生产代码中，通过`GlobalReference_Create`将FindClass找到的类缓存会大大提高效率
    ani_class stringClass {};
    ani_status status = env->FindClass("std.core.String", &stringClass);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_class arrayBufferClass {};
    status = env->FindClass("std.core.ArrayBuffer", &arrayBufferClass);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_class valueArrayIntClass {};
    status = env->FindClass("A{i}", &valueArrayIntClass);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_class fixedArrayStringClass {};
    status = env->FindClass("A{C{std.core.String}}", &fixedArrayStringClass);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_boolean isString = ANI_FALSE;
    status = env->Object_InstanceOf(union_obj, stringClass, &isString);
    if (status != ANI_OK) {
        // handle error and return
    }
    if (isString) {
        ani_size sz {};
        env->String_GetUTF8Size(static_cast<ani_string>(union_obj), &sz);
        std::string result(sz + 1, 0);
        env->String_GetUTF8(static_cast<ani_string>(union_obj), result.data(), result.size(), &sz);
        result.resize(sz);
        std::cout << "Object is String; content: " << result.c_str() << std::endl;
        return;
    }

    ani_boolean isArrayBuffer = ANI_FALSE;
    status = env->Object_InstanceOf(union_obj, arrayBufferClass, &isArrayBuffer);
    if (status != ANI_OK) {
        // handle error and return
    }
    if (isArrayBuffer) {
        ani_int length;
        status = env->Object_CallMethodByName_Int(union_obj, "getByteLength", nullptr, &length);
        if (status != ANI_OK) {
            // handle error and return
        }
        std::cout << "Object is ArrayBuffer; length: " << length << std::endl;
        return;
    }

    ani_boolean isIntValueArray = ANI_FALSE;
    status = env->Object_InstanceOf(union_obj, valueArrayIntClass, &isIntValueArray);
    if (status != ANI_OK) {
        // handle error and return
    }
    if (isIntValueArray) {
        std::cout << "Object is ValueArray"<< std::endl;
        return;
    }

    ani_boolean isStringFixedArray = ANI_FALSE;
    status = env->Object_InstanceOf(union_obj, fixedArrayStringClass, &isStringFixedArray);
    if (status != ANI_OK) {
        // handle error and return
    }
    if (isStringFixedArray) {
        std::cout << "Object is FixedArray"<< std::endl;
    }
    return;
}
```

