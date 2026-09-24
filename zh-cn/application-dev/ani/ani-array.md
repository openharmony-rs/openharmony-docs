# 可变长度数组：Array\<T\>和 T\[\]
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

`Array<T>`和`T[]`在ArkTS中是相同类型，它们在编译后都对应为标准库中的`std.core.Array`类。这些数组对象可以像普通对象一样通过类实例化、方法调用进行管理。

同时也可以使用ANI层提供的专用函数进行操作：

```cpp
// 获取数组长度。
ani_status Array_GetLength(ani_env *env, ani_array array, ani_size *result);

// 创建指定长度的数组，并使用initial_element初始化元素。
ani_status Array_New(ani_env *env, ani_size length, ani_ref initial_element, ani_array *result);

// 设置指定下标的数组元素。
ani_status Array_Set(ani_env *env, ani_array array, ani_size index, ani_ref ref);

// 获取指定下标的数组元素。
ani_status Array_Get(ani_env *env, ani_array array, ani_size index, ani_ref *result);

// 向数组末尾追加元素。
ani_status Array_Push(ani_env *env, ani_array array, ani_ref ref);

// 弹出并返回数组末尾元素。
ani_status Array_Pop(ani_env *env, ani_array array, ani_ref *result);
```

注意：泛型参数会在编译后被擦除，所以在ani层，所有的泛型数组都是统一的`ani_array`类型。

**示例：**

```cpp
// 创建长度为3的数组，元素初始化为undefined。
ani_size length = 3;
ani_ref undefinedRef;
ani_status status = env->GetUndefined(&undefinedRef);
if (status != ANI_OK) {
    // handle error and return
}
ani_array array;
status = env->Array_New(length, undefinedRef, &array);
if (status != ANI_OK) {
    // handle error and return
}

// 设置下标0的元素。注意泛型被擦除，元素以ani_ref传入，基本类型需要装箱。
ani_size index = 0;
ani_double value = 1.0;
ani_object boxedDouble;
status = env->Primitive_Box_Double(value, &boxedDouble);
if (status != ANI_OK) {
    // handle error and return
}
status = env->Array_Set(array, index, boxedDouble);
if (status != ANI_OK) {
    // handle error and return
}
```

