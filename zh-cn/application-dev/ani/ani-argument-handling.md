# 参数处理
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

ArkTS参数进入native函数后，C++侧需要按ANI类型接收，并根据声明类型决定是否装箱、拆箱或做运行时类型识别。

## 基本类型参数

- 从语言层面来看，ArkTS 1.2仅包含基本类型的装箱版本。
- 从运行时角度来看，当基本类型被指定为非泛型参数、返回值或字段类型时，会使用基本类型进行优化。

### 装箱类型

| ANI基本类型 | 装箱类 | Mangling  | 绑定/ANI类型 | 说明 |
| ------------------ | ----------- | --------------------- | ---------------- | ------------------- |
|   `ani_boolean`    | `Boolean`   | `C{std.core.Boolean}` | `ani_object`     | Boxed boolean       |
|   `ani_byte`       | `Byte`      | `C{std.core.Byte}`    | `ani_object`     | Boxed byte          |
|   `ani_char`       | `Char`      | `C{std.core.Char}`    | `ani_object`     | Boxed char          |
|   `ani_short`      | `Short`     | `C{std.core.Short}`   | `ani_object`     | Boxed short         |
|   `ani_int`        | `Int`       | `C{std.core.Int}`     | `ani_object`     | Boxed int           |
|   `ani_long`       | `Long`      | `C{std.core.Long}`    | `ani_object`     | Boxed long          |
|   `ani_float`      | `Float`     | `C{std.core.Float}`   | `ani_object`     | Boxed float         |
|   `ani_double`     | `Double`    | `C{std.core.Double}`  | `ani_object`     | Boxed double        |
|         -          | `Void`      | `C{std.core.Void}`    | `ani_object`     | 通常无意义           |


可以参考[查询标准类的方法](ani-object-creation.md#查询标准类的方法)来查询这些装箱类型及其对应模块的方法。

如果函数参数的名称修饰（mangling）是`C{std.core.Object}`，则它只接受类实例。例如，`Array<T>`方法`$_set(i: int, val: T): void`的Mangling为`iC{std.core.Object}:`，其中第二个参数必须是类实例。

在这种情况下，基本类型的值（如`int`或`double`）需要进行装箱（转换为`Int`或`Double`）。根据[类型转换](ani-type-definition.md#类型转换)，得到的`ani_object`也可以转换为`ani_ref`以满足函数要求。

同样，`A{C{std.core.Object}}`表示类实例的定长数组。

### 装箱

目的：
1. 满足函数参数类型要求。
2. 将基本类型的值转换为类实例（例如，将`ani_int`转换为`ani_object`）。

在托管代码中，对于可选参数，装箱操作会自动进行。省略可选基本类型的值默认为`undefined`。在原生（native）代码中，必须显式传递参数。

**快速装箱接口：**

| 函数名 | 描述 |
| ---------------------- | --------------------------------- |
| `Primitive_Box_<Type>` | 将ANI基本数据类型装箱为对应的类对象 |

其中`<Type>`为待装箱的数据类型。

代码示例：

```cpp
ani_object createDouble(ani_env *env)
{
    ani_object doubleObj {};
    if (env->Primitive_Box_Double(static_cast<ani_double>(2.0), &doubleObj) != ANI_OK) {
        std::cerr << "Failed to allocate Double!" << std::endl;
        ani_ref undefinedRef;
        env->GetUndefined(&undefinedRef);
        return static_cast<ani_object>(undefinedRef);
    }
    return doubleObj;
}
```

**传统装箱方式：**

通过`Object_New`接口创建`std.core.<Type>`的类对象。

代码示例：

```cpp
ani_object createDouble(ani_env *env)
{
    // 注意：在生产代码中，通过`GlobalReference_Create`将FindClass找到的类缓存会大大提高效率
    static constexpr const char *className = "std.core.Double";
    ani_class doubleCls {};
    env->FindClass(className, &doubleCls);
    ani_method ctor {};
    env->Class_FindMethod(doubleCls, "<ctor>", "d:", &ctor);
    ani_object doubleObj {};
    if (env->Object_New(doubleCls, ctor, &doubleObj, static_cast<ani_double>(2.0)) != ANI_OK) {
        std::cerr << "Failed to allocate Double!" << std::endl;
        ani_ref undefinedRef;
        env->GetUndefined(&undefinedRef);
        return static_cast<ani_object>(undefinedRef);
    }
    return doubleObj;
}
```

可以通过`Class_FindMethod`的`signature`参数来选择所需的构造函数重载版本。

### 拆箱

**快速拆箱接口：**

| 函数名 | 描述 |
| ------------------------ | ---------------------------- |
| `Primitive_Unbox_<Type>` | 提取装箱对象对应的基本类型的值 |

其中`<Type>`为待拆箱的对象类型。

代码示例：

```cpp
ani_double doubleVal {};
env->Primitive_Unbox_Double(doubleObj, &doubleVal);
```
开发者需要保证传入的装箱对象类型与调用的拆箱接口类型一致，如传入`Double`类型装箱对象则调用`Primitive_Unbox_Double`接口。

**传统拆箱方式：**

使用`to<Type>`方法来提取基本类型的值，其中`<Type>`为对应的数据类型：

```cpp
Object_CallMethodByName_Double(boxed_double_obj, "toDouble", ":d", &unboxed_value)
```

`Double`由装箱对象的返回类型决定。Mangling `:d`表示返回一个`double`类型的值。

代码示例：
```ts
function handleData(param: Double): void
```

```cpp
void HandleDataImpl(ani_env *env, ani_object param)
{
    ani_double value = 0;
    env->Object_CallMethodByName_Double(param, "toDouble", ":d", &value);
    std::cout << "value: " << value << std::endl;
}
```

## 泛型参数

- 除了`FixedArray`外，所有泛型类型在运行时都会被擦除。
- 在字节码中，类型参数会被编译为其类型约束。
- 默认的类型约束是`Object | null | undefined`。
- 基本类型作为类型参数使用时总是会被装箱。

| ArkTS类型 | 示例 | Mangling | 绑定/ANI类型 | 补充说明 |
| -------------------- | ----------------- | --------------------------------------- | -------------------- | ------------------------ |
| `(a: T, b: R): void` | `f(1, "str")`     | `C{std.core.Object}C{std.core.Object}:` | `ani_object`         | -                        |
| `Array<T>`           | `Array<int>`      | `C{std.core.Array}`                     | `ani_object`         | -                        |
| `FixedArray<T>`      | `FixedArray<int>` | `A{i}`                                  | `ani_fixedarray_int` | Reified（非擦除）类型参数 |

## 联合类型

联合类型会被编译为组件的 _最小上界_，在ANI中对应`ani_object`。最常见的情况是该类型为`C{std.core.Object}`，但并非总是如此：如公共Interface为最小上界，类型为`C{some_module.I}`

```ts
interface I {}
class C implements I {}
function foo(arg: C | I): void  // Mangling: "X{C{some_module.I}C{some_module.C}}:"
```

> 可选参数`arg?: T`始终等同于`arg: T | undefined`，可以在[ArkTS语言规范](ani-introduction.md#参考资源)`第4.8.4 Optional Parameters`中查看

由于联合类型用引用表示，基本类型的值必须装箱后才能作为联合类型的一部分使用。

| ETS类型 | Mangling | 绑定/ANI类型 | 补充说明 |
| --------------------- | ----------------------------------------- | ---------------- | ---------------- |
| `a: double \| string` | `X{C{std.core.Double}C{std.core.String}}` | `ani_object`     | 基本类型需要装箱  |

**参数处理**：

使用`Object_InstanceOf`来确定参数的实际类型并进行相应处理。请参阅[类型识别：Object_InstanceOf](ani-type-definition.md#类型识别object_instanceof)

## 可选参数

**Mangling**：
1. 像`int`、`double`这样的基本类型会被装箱为`Int`、`Double`等。
2. 非基本类型保留其原始的Mangling。
3. 所有可选参数都被视为包含`undefined`的联合类型（请参阅[ArkTS语言规范](ani-introduction.md#参考资源) `第4.8.4可选参数`）。
4. 对于带有可选参数的构造函数，`.abc`文件中存在重载构造函数。

| ETS类型 | Mangling | 绑定/ANI类型 | 补充说明 |
| ------------------- | ---------------------- | ------------------ | ---------- |
| `a: int`            | `i`                    | `ani_int`          | -          |
| `a?: int`           | `C{std.core.Int}`      | `ani_object`       | 装箱       |
| `a: Int`            | `C{std.core.Int}`      | `ani_object`       | -          |
| `a?: Int`           | `C{std.core.Int}`      | `ani_object`       | -          |
| `a?: customCls`     | `C{example.CustomCls}` | `ani_object`       | -          |
| `a?: string \| int` | `C{std.core.Object}`   | `ani_object`       | 联合类型   |

**参数处理**：

在托管代码中，可选参数可以省略；例如对`foo(arg?: T)`的调用`foo()`，编译器会按等价于调用`foo(undefined)`的语义处理。

但在原生（native）代码中调用带有可选参数的函数或方法时，必须显式传递对应位置的参数；如果希望表达“该可选参数未传值”，需要显式传递`undefined`。

使用示例：

```ts
class C {
    checkOptionalString(z?: string): int {
        if (z == undefined) {
            return 5;
        }
        return 4;
    }
}
```

```cpp
ani_method method {};
env->Class_FindMethod(cls, "checkOptionalString", "C{std.core.String}:i", &method);

// 1. 显式传undefined，等价于托管代码中“省略该可选参数”
ani_ref undef {};
env->GetUndefined(&undef);

ani_int result {};
env->Object_CallMethod_Int(obj, method, &result, undef); // obj是C的实例对象

// 2. 显式传实际值
ani_string str {};
env->String_NewUTF8("hello", 5, &str);
env->Object_CallMethod_Int(obj, method, &result, str);
```

如果参数是包含`undefined`类型的联合类型，在原生（native）代码中访问该参数之前，必须使用`Reference_IsUndefined`接口检查它是否为`undefined`：


```cpp
static void CallMeWithOptionalDouble(ani_env *env, ani_object doubleObject)
{
    ani_boolean isUndefined;
    env->Reference_IsUndefined(doubleObject, &isUndefined);
    if (isUndefined) {
        std::cout << "CallMeWithOptionalDouble NOT passed value " << std::endl;
    } else {
        ani_double result;
        env->Object_CallMethodByName_Double(doubleObject, "toDouble", ":d", &result);
        std::cout << "CallMeWithOptionalDouble passed value: " <<  result << std::endl;
    }
}
```

## 默认参数

与可选参数的情况类似：
1. 基本类型会自动装箱。
2. 非基本类型保留原始的Mangling。

```ts
// mangling: "zC{std.core.Boolean}:"
function foo(a: boolean, b: boolean = false): void {}
```

## 可变/剩余参数

可变参数`...args: T[]`是ArkTS中的语法糖，用于接收不定数量的实参，ArkTS会将这些参数收集到一个数组中。

```ts
// mangling: "iC{std.core.Array}:"
function foo(a: int, ...b: int[]): void
```

