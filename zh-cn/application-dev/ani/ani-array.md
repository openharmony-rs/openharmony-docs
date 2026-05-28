# 可变长度数组：Array\<T\>和 T\[\]
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

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
ani_array CreateArray(ani_env *env, const std::vector<ani_double> &numbers)
{
    // Create Array<T>
    ani_ref undefinedRef;
    env->GetUndefined(&undefinedRef);
    ani_array array;
    env->Array_New(numbers.size(), undefinedRef, &array);

    // Populate array
    ani_size index = 0;
    for (auto num : numbers) {
        ani_object boxedNumber;
        env->Primitive_Box_Double(num, &boxedNumber);
        env->Array_Set(array, index, boxedNumber);
        index++;
    }
    return array;
}
```

