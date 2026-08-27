# ANI支持的接口
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

> 本文基于 [`ani.h`](https://gitcode.com/openharmony/arkcompiler_runtime_core/blob/master/static_core/plugins/ets/runtime/ani/ani.h) 头文件，对 ANI（Ark Native Interface）所支持的接口进行分组说明。接口实现主要位于 `ani_interaction_api.cpp` 和 `ani_vm_api.cpp`（VM 与线程相关接口见后者）。
>
> 如需了解 ANI 的总体设计、使用场景与迁移实践，请先阅读 [ANI入门与开发调试](ani-introduction.md)。

## VM与环境相关

| 接口 | 功能说明 |
| ---- | -------- |
| ANI_CreateVM | 创建虚拟机实例。`ani_options` 为 VM 初始化配置入口（如 `--verify:ani`、`--ext:boot-panda-files=...`、`--logger` 等）。 |
| ANI_GetCreatedVMs | 获取当前进程已创建的 VM 列表。 |
| ANI_Constructor | native 库入口函数。通过 `loadLibrary` 加载 .so 时自动调用，通常在其中完成 native 方法/函数绑定。 |
| ANI_Destructor | native 库析构入口函数。 |
| GetVM | 从当前 `ani_env` 获取关联的 `ani_vm`。 |
| GetEnv | 从 `ani_vm` 获取当前线程已附加的 `ani_env`（要求线程已附加）。 |
| AttachCurrentThread | 将当前 native 线程附加到 VM，获得 `ani_env`；使用后必须 `DetachCurrentThread`。`ani_options` 用于控制是否启用 interop。 |
| DetachCurrentThread | 分离当前线程与 VM，释放该线程相关资源。仅可分离由 `AttachCurrentThread` 附加的线程。 |
| DestroyVM | 销毁 VM 实例。 |
| GetVersion | 获取 ANI 运行时版本信息。 |

## 查找相关

按描述符定位模块、命名空间、类与枚举。`FindClass` 返回 `ANI_PENDING_ERROR` 表示查找过程中产生了未处理异常，可通过 `GetUnhandledError` 获取具体异常。

| 接口 | 功能说明 |
| ---- | -------- |
| FindModule | 按模块描述符（如 `"example"`）查找模块。绑定模块级 native 函数前必须先找到对应 module。 |
| FindNamespace | 按命名空间描述符查找命名空间。 |
| FindClass | 按类描述符（如 `"example.Point"`、`"std.core.String"`、`"A{i}"`）查找类。 |
| FindEnum | 按枚举描述符（如 `E{example.COLOR}`）查找枚举。 |

## 模块/命名空间相关

| 接口 | 功能说明 |
| ---- | -------- |
| Module_FindFunction | 在模块中按名称与 Mangling 签名查找函数。 |
| Module_FindVariable | 在模块中按名称查找变量。 |
| Module_BindNativeFunctions | 将一组 `ani_native_function` 绑定到模块。native 函数签名仅需前置 `ani_env*`，无需额外对象参数。 |
| Namespace_FindFunction | 在命名空间中按名称与签名查找函数。 |
| Namespace_FindVariable | 在命名空间中按名称查找变量。 |
| Namespace_BindNativeFunctions | 将一组 native 函数绑定到命名空间。 |

## 类成员查找与绑定相关

| 接口 | 功能说明 |
| ---- | -------- |
| Class_BindNativeMethods | 将一组 native 实例方法绑定到类。C++ 实现前置参数为 `ani_env*`、`ani_object`。 |
| Class_BindStaticNativeMethods | 将一组 native 静态方法绑定到类。C++ 实现前置参数为 `ani_env*`、`ani_class`。 |
| Class_FindMethod | 按名称与签名查找实例方法（构造函数名为 `"<ctor>"`）。**重载时不要用 `nullptr` 代替签名**。 |
| Class_FindStaticMethod | 按名称与签名查找静态方法。 |
| Class_FindField | 按名称查找实例字段句柄。用于字段读写（不可用于属性）。 |
| Class_FindStaticField | 按名称查找静态字段句柄。 |
| Class_FindGetter | 按名称查找属性 getter 方法。 |
| Class_FindSetter | 按名称查找属性 setter 方法。 |
| Class_FindIndexableGetter | 按签名查找可索引 getter（如 `Record` 的 `$_get`）。 |
| Class_FindIndexableSetter | 按签名查找可索引 setter（如 `Record` 的 `$_set`）。 |
| Class_FindIterator | 查找类的迭代器方法。 |

## 对象相关

| 接口 | 功能说明 |
| ---- | -------- |
| Object_New | 通过类与构造方法创建对象，以变参传参。不能用于接口、抽象类、`ani_string`、`FixedArray<T>`。 |
| Object_New_A | 同上，以 `const ani_value *args` 数组传参。 |
| Object_New_V | 同上，以 `va_list args` 传参。 |
| Object_GetType | 获取对象对应的 `ani_type`。 |
| Object_InstanceOf | 判断对象是否为指定 `ani_type` 的实例。联合类型参数的实际类型识别依赖此接口。 |
| Type_GetSuperClass | 获取指定 `ani_type` 的父类。 |
| Type_IsAssignableFrom | 判断一个类型是否可由另一个类型赋值。 |

## 属性访问相关

属性（property）带有 getter/setter；接口中的字段默认为属性。ANI 仅提供按名称访问的属性接口；若需通过句柄访问，先用 `Class_FindGetter`/`Class_FindSetter` 取得方法句柄，再用 `Object_CallMethod_*` 调用。`<Type>` 取值含 `Boolean`、`Char`、`Byte`、`Short`、`Int`、`Long`、`Float`、`Double`、`Ref`（不含 `Void`）。

| 接口 | 功能说明 |
| ---- | -------- |
| Object_GetPropertyByName_\<Type\> | 按名称以对应类型读取对象属性。 |
| Object_SetPropertyByName_\<Type\> | 按名称以对应类型设置对象属性。 |

## 字段访问相关

字段（field）无 getter/setter，直接读写实例数据。`<Type>` 取值含 `Boolean`、`Char`、`Byte`、`Short`、`Int`、`Long`、`Float`、`Double`、`Ref`（不含 `Void`）。

| 接口 | 功能说明 |
| ---- | -------- |
| Object_GetFieldByName_\<Type\> | 按名称以对应类型读取实例字段。 |
| Object_SetFieldByName_\<Type\> | 按名称以对应类型设置实例字段。 |
| Object_GetField_\<Type\> | 通过字段句柄读取实例字段。 |
| Object_SetField_\<Type\> | 通过字段句柄设置实例字段。 |

## 静态字段访问相关

`<Type>` 的取值与[字段访问相关](#字段访问相关)相同：`Boolean`、`Char`、`Byte`、`Short`、`Int`、`Long`、`Float`、`Double`、`Ref`（不含 `Void`）。

| 接口 | 功能说明 |
| ---- | -------- |
| Class_GetStaticField_\<Type\> | 通过静态字段句柄读取静态字段值。 |
| Class_SetStaticField_\<Type\> | 通过静态字段句柄设置静态字段值。 |
| Class_GetStaticFieldByName_\<Type\> | 按名称读取静态字段值。 |
| Class_SetStaticFieldByName_\<Type\> | 按名称设置静态字段值。 |

## 实例方法调用相关

调用实例方法，按返回类型选择接口；同一返回类型提供三种传参变体：默认变体（变参 `...`，形如 `Object_CallMethod_<Type>`）、数组传参变体 `_A`（以 `const ani_value *args` 传入）、`va_list` 传参变体 `_V`（以 `va_list args` 传入）。`<Type>` 取值含 `Boolean`、`Char`、`Byte`、`Short`、`Int`、`Long`、`Float`、`Double`、`Ref`、`Void`。

| 接口 | 功能说明 |
| ---- | -------- |
| Object_CallMethod_\<Type\> | 通过方法句柄调用实例方法并返回对应类型的结果（变参传参）。`_Void` 表示无返回值。 |
| Object_CallMethod_\<Type\>_A | 同上，以 `const ani_value *args` 数组传参。 |
| Object_CallMethod_\<Type\>_V | 同上，以 `va_list args` 传参。 |
| Object_CallMethodByName_\<Type\> | 按方法名与签名调用实例方法并返回对应类型的结果（变参传参）。 |
| Object_CallMethodByName_\<Type\>_A | 同上，以数组传参。 |
| Object_CallMethodByName_\<Type\>_V | 同上，以 `va_list` 传参。 |

## 静态方法调用相关

调用类的静态方法，按返回类型与传参方式选择接口。

| 接口 | 功能说明 |
| ---- | -------- |
| Class_CallStaticMethod_\<Type\> | 通过静态方法句柄调用静态方法并返回对应类型的结果（变参传参）。`_Void` 表示无返回值。 |
| Class_CallStaticMethod_\<Type\>_A | 同上，以数组传参。 |
| Class_CallStaticMethod_\<Type\>_V | 同上，以 `va_list` 传参。 |
| Class_CallStaticMethodByName_\<Type\> | 按名称与签名调用静态方法并返回对应类型的结果（变参传参）。 |
| Class_CallStaticMethodByName_\<Type\>_A | 同上，以数组传参。 |
| Class_CallStaticMethodByName_\<Type\>_V | 同上，以 `va_list` 传参。 |

## 函数调用相关

调用模块/命名空间级函数，按返回类型与传参方式选择接口。

| 接口 | 功能说明 |
| ---- | -------- |
| Function_Call_\<Type\> | 通过 `ani_function` 句柄调用函数并返回对应类型的结果（变参传参）。`_Void` 表示无返回值。 |
| Function_Call_\<Type\>_A | 同上，以 `const ani_value *args` 数组传参。 |
| Function_Call_\<Type\>_V | 同上，以 `va_list args` 传参。 |

## 函数对象调用

| 接口 | 功能说明 |
| ---- | -------- |
| FunctionalObject_Call | `FunctionalObject_Call` 的参数和返回值统一以 `ani_ref` 表示。引用类型可直接传递；基本类型由于不能直接表示为 `ani_ref`，需要先装箱，基本类型返回结果需要按需拆箱。 |

## 变量读写相关

读取或设置模块/命名空间级变量，按对应类型选择接口。`<Type>` 取值含 `Boolean`、`Char`、`Byte`、`Short`、`Int`、`Long`、`Float`、`Double`、`Ref`（不含 `Void`）。

| 接口 | 功能说明 |
| ---- | -------- |
| Variable_SetValue_\<Type\> | 以对应类型设置变量值。 |
| Variable_GetValue_\<Type\> | 读取变量的对应类型值。 |

## 装箱与拆箱相关

将基本类型值装箱为对应的包装类对象（如 `Double`），或从包装对象中拆箱取出基本值。

| 接口 | 功能说明 |
| ---- | -------- |
| Primitive_Box_\<Type\> | 将 ANI 基本类型装箱为对应包装类对象（`ani_object`）。`<Type>` 不含 `Ref`。 |
| Primitive_Unbox_\<Type\> | 从包装类对象中拆箱取出基本类型值。`<Type>` 不含 `Ref`。 |

> 装箱/拆箱对应关系（`ani_int` ↔ `Int` ↔ `C{std.core.Int}`）详见 [ANI应用实践手册 - 装箱类型](ani-argument-handling.md#装箱类型)。

## 枚举相关

ArkTS 枚举在编译期生成特殊类，其内部成员属于实现细节，不可直接访问，必须使用下列专用接口操作。

| 接口 | 功能说明 |
| ---- | -------- |
| Enum_GetEnumItemByName | 按名称获取枚举项（`ani_enum_item`）。 |
| Enum_GetEnumItemByIndex | 按索引获取枚举项。 |
| EnumItem_GetEnum | 获取枚举项所属的枚举（`ani_enum`）。 |
| EnumItem_GetValue_Int | 获取枚举项的整型值（仅整型枚举）。 |
| EnumItem_GetValue_String | 获取枚举项的字符串值（仅字符串枚举）。 |
| EnumItem_GetName | 获取枚举项的名称（`ani_string`）。 |
| EnumItem_GetIndex | 获取枚举项在其枚举中的索引。 |

## 字符串相关

> 在非 VerifyANI 模式下不校验编码，调用方需保证传入合法 UTF-8/UTF-16 数据。

| 接口 | 功能说明 |
| ---- | -------- |
| String_NewUTF8 | 以 UTF-8 数据与字节长度创建 `ani_string`。 |
| String_NewUTF16 | 以 UTF-16 数据与码元长度创建 `ani_string`。 |
| String_GetUTF8Size | 获取字符串的 UTF-8 字节长度。 |
| String_GetUTF16Size | 获取字符串的 UTF-16 码元长度。 |
| String_GetUTF8 | 将字符串的 UTF-8 数据拷入缓冲区，返回写入字节数。 |
| String_GetUTF16 | 将字符串的 UTF-16 数据拷入缓冲区，返回写入码元数。 |
| String_GetUTF8SubString | 获取字符串指定偏移与字节长度子串的 UTF-8 数据。字节范围未覆盖完整字符时会被截断。 |
| String_GetUTF16SubString | 获取字符串指定偏移与码元长度子串的 UTF-16 数据。 |

## 可变数组相关

`Array<T>` 与 `T[]` 在底层均为 `std.core.Array`，泛型参数被擦除，运行时统一为 `ani_array`。

| 接口 | 功能说明 |
| ---- | -------- |
| Array_New | 创建指定长度的 `ani_array`，以初始元素引用填充。 |
| Array_GetLength | 获取数组长度（考虑可能被覆写的 `length` 托管方法）。 |
| Array_Get | 按下标获取数组元素引用。 |
| Array_Set | 按下标设置数组元素。 |
| Array_Push | 向数组末尾追加一个元素。 |
| Array_Pop | 取出并删除数组末尾元素。 |

## 定长数组相关

`FixedArray<T>` 的元素类型在编译期不被擦除，不同元素类型互不兼容，需使用与之匹配的接口。本组为引用型 `FixedArray` 的通用接口。

| 接口 | 功能说明 |
| ---- | -------- |
| FixedArray_New | 按 `ani_type` 与长度创建引用型 `FixedArray`。长度非零时必须提供初始元素引用，传 C/C++ `nullptr` 会返回 `ANI_INVALID_ARGS`；无需实际初始值时可传入 `GetUndefined` 获得的引用跳过填充。 |
| FixedArray_GetLength | 获取 `FixedArray` 长度。 |
| FixedArray_Set | 按下标设置 `FixedArray` 中的引用。 |
| FixedArray_Get | 按下标获取 `FixedArray` 中的引用。 |

## 值数组相关

`ValueArray` 是基本类型定长数组，按元素类型提供专用创建与区域读写接口。`<Type>` 为基本类型后缀（不含 `Ref`）。

| 接口 | 功能说明 |
| ---- | -------- |
| ValueArray_New_\<Type\> | 创建指定长度的基本类型值数组。 |
| ValueArray_GetLength | 获取值数组长度。 |
| ValueArray_GetRegion_\<Type\> | 将值数组指定偏移与长度的区域拷贝到 native 缓冲区。 |
| ValueArray_SetRegion_\<Type\> | 将 native 缓冲区数据写入值数组指定区域。 |

## ArrayBuffer相关

| 接口 | 功能说明 |
| ---- | -------- |
| CreateArrayBuffer | 创建指定字节数的 `ArrayBuffer`，并返回底层数据指针。 |
| ArrayBuffer_GetInfo | 获取 `ArrayBuffer` 的底层数据指针与字节长度。 |

## 元组相关

`<Type>` 取值含 `Boolean`、`Char`、`Byte`、`Short`、`Int`、`Long`、`Float`、`Double`、`Ref`（不含 `Void`）。

| 接口 | 功能说明 |
| ---- | -------- |
| TupleValue_GetNumberOfItems | 获取元组的元素个数。 |
| TupleValue_GetItem_\<Type\> | 按下标获取元组元素的对应类型值。 |
| TupleValue_SetItem_\<Type\> | 按下标设置元组元素的对应类型值。 |

## Promise相关

用于在 native 层创建并管理 Promise，配合 resolver 完成 resolve/reject。

| 接口 | 功能说明 |
| ---- | -------- |
| Promise_New | 创建 Promise 对象，同时返回 `ani_resolver` 用于后续 resolve/reject。 |
| PromiseResolver_Resolve | 以引用值 resolve 关联的 resolver。成功后 `resolver` 被释放，不可再次使用。 |
| PromiseResolver_Reject | 以 `ani_error` reject 关联的 resolver。成功后 `resolver` 被释放，不可再次使用。 |

> ANI 推荐将异步编排放在 ArkTS 层（借助 `taskpool`/`Promise`），native 仅实现同步耗时操作。详见 [ANI应用实践手册 - 异步编程](ani-asynchronous-programming.md)。

## 引用与作用域相关

native 侧创建的引用默认为局部引用，仅在当前调用上下文有效。需要跨调用持久化时使用全局/弱引用；在纯 native 线程回调中应使用 LocalScope 管理引用生命周期。

| 接口 | 功能说明 |
| ---- | -------- |
| EnsureEnoughReferences | 确保当前作用域可容纳指定数量的局部引用。 |
| CreateLocalScope | 创建局部作用域，限制其中引用数量上限为 `nr_refs`。 |
| DestroyLocalScope | 销毁当前局部作用域，一次性释放其中所有局部引用。 |
| CreateEscapeLocalScope | 创建可逃逸的局部作用域。 |
| DestroyEscapeLocalScope | 销毁可逃逸作用域，并将指定引用逃逸到外层作用域。 |
| Reference_Delete | 删除指定局部引用以立即释放资源。 |
| GlobalReference_Create | 将局部引用提升为全局引用，跨多次 native 调用持久有效。 |
| GlobalReference_Delete | 删除全局引用，避免内存耗尽。 |
| WeakReference_Create | 为引用创建弱引用（`ani_wref`），不阻止目标被 GC 回收。 |
| WeakReference_Delete | 删除弱引用。 |
| WeakReference_GetReference | 尝试从弱引用取出强引用，并返回目标是否已被释放。 |

## 特殊值与引用比较相关

| 接口 | 功能说明 |
| ---- | -------- |
| GetNull | 获取 `null` 引用。 |
| GetUndefined | 获取 `undefined` 引用。 |
| Reference_IsNull | 判断引用是否为 `null`。 |
| Reference_IsUndefined | 判断引用是否为 `undefined`。 |
| Reference_IsNullishValue | 判断引用是否为 nullish（`null` 或 `undefined`）。 |
| Reference_Equals | 判断两个引用是否相等（包装类按内容比较，自定义类按地址比较）。 |
| Reference_StrictEquals | 判断两个引用是否严格相等。 |

## 异常与错误相关

`ANI_PENDING_ERROR` 发生后，`ani_env` 进入异常挂起状态，需先清除异常才能继续调用其他 ANI 接口。

| 接口 | 功能说明 |
| ---- | -------- |
| ThrowError | 抛出指定的 `ani_error`。自定义错误需继承 `escompat.Error`。 |
| ExistUnhandledError | 判断当前环境是否存在未处理的异常。 |
| GetUnhandledError | 获取当前未处理的异常对象。 |
| ResetError | 清除当前错误/异常状态。 |
| DescribeError | 通过 `console.error` 输出当前异常的堆栈等调试信息。 |
| Abort | 以指定消息立即终止进程，不返回。 |