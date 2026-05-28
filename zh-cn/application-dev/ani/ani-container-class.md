# 其余容器类的使用
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

Record、Tuple等容器类型传入native后，本质上仍按对象或专用ANI类型访问。ArkTS侧把`Record<K, V>`或元组传给native函数时，C++侧通常需要读取键值、按下标读取元素，或调用容器内置方法。

1. 运用`FindClass`依据名称定位目标容器类。
2. 借助`Class_FindMethod` + `Object_CallMethod`或者`Object_CallMethodByName`来调用内置方法。
3. 按需转换参数和返回值类型。对于复杂类型，可通过方法调用提取基本类型。

## Record：`std.core.Record`

Record在标准库中继承自`Map`，并提供`$_get`、`$_set`形式的索引访问方法。Record索引访问常用以下ANI接口查找`getter/setter`：

```cpp
// 查找Record等类型的索引getter方法。
ani_status Class_FindIndexableGetter(ani_env *env, ani_class cls, const char *signature, ani_method *result);

// 查找Record等类型的索引setter方法。
ani_status Class_FindIndexableSetter(ani_env *env, ani_class cls, const char *signature, ani_method *result);
```

| 函数 | 签名 | 描述 |
|--------------| ----------------------------------------|--------------------|
| `<ctor>`     | `C{std.core.Object}:`                   | Constructor        |
| `$_get`      | `C{std.core.Object}:C{std.core.Object}` | Get value by key   |
| `$_set`      | `C{std.core.Object}:`                   | Set key-value pair |
| `keys`       | `C{std.core.IterableIterator}`          | List keys          |

**示例：**
```ts
class PersonInfo {
    name: string = "";
    age: number = 0;
}

native callWithRecord(entry: Record<string, PersonInfo>): void;
```

```cpp
void CallWithRecordImpl(ani_env *env, ani_object record) {
    ani_class recordCls;
    env->FindClass("std.core.Record", &recordCls);
    ani_method getter;
    // Signature can be omitted if there are not overloads
    env->Class_FindIndexableGetter(recordCls, nullptr, &getter);

    static constexpr std::string_view name = "Chloe";
    ani_string aniName;
    env->String_NewUTF8(name.data(), name.length(), &aniName);
    ani_ref person;
    env->Object_CallMethod_Ref(record, getter, &person, aniName);

    ani_ref personName;
    env->Object_GetFieldByName_Ref(static_cast<ani_object>(person), "name", &personName);
    ani_double personAge;
    env->Object_GetFieldByName_Double(static_cast<ani_object>(person), "age", &personAge);
}
```


## 元组（Tuple）

ANI侧提供以下`TupleValue_*`系列接口：

| 函数名 | 操作 | 描述 |
| ----------------------------- | ---- | --------------------- |
| `TupleValue_GetNumberOfItems` | 获取 | 获取元组元素数量       |
| `TupleValue_GetItem_<Type>`   | 读取 | 读取指定类型的元组元素 |
| `TupleValue_SetItem_<Type>`   | 写入 | 写入指定类型的元组元素 |

其中`<Type>`为元素类型。

**示例：**
```ts
let a = [3.14, 2.71, 1.61, 0.59, 10.0];

native callWithTuple(tuple:[double, double, double, double, double]):void;
```

```cpp
void callWithTupleImpl(ani_env *env, ani_tuple_value tuple) {
    ani_double result = 0.0;
    env->TupleValue_GetItem_Double(tuple, 0U, &result);  // result = 3.14
}
```
上述元组示例，通过传入元组对象和序号参数，获取对应元组序号位置的值。

