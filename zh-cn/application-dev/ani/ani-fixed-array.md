# 定长数组
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

定长数组是一种特殊类型，其元素类型在编译阶段不会被擦除，这意味着`FixedArray<int>`和`FixedArray<double>`在字节码和语言层面是不兼容的。编译器会为不同的元素生成不同的底层结构，因此在native层需要使用**类型匹配的API进行操作**。

如`FixedArray_*`系列API：

```cpp
// 获取定长数组长度。
ani_status FixedArray_GetLength(ani_env *env, ani_fixedarray array, ani_size *result);

// 创建double元素类型的定长数组。
ani_status FixedArray_New_Double(ani_env *env, ani_size length, ani_fixedarray_double *result);

// 批量读取double定长数组中的一段元素。
ani_status FixedArray_GetRegion_Double(ani_env *env, ani_fixedarray_double array, ani_size offset, ani_size length, ani_double *native_buffer);

// 批量写入double定长数组中的一段元素。
ani_status FixedArray_SetRegion_Double(ani_env *env, ani_fixedarray_double array, ani_size offset, ani_size length, const ani_double *native_buffer);
```
**示例：**

```cpp
ani_fixedarray_double CreateFixedArray(ani_env *env, const std::vector<ani_double> &numbers)
{
    // Create Array<T>
    ani_fixedarray_double array;
    env->FixedArray_New_Double(numbers.size(), &array);
    // Populate array
    env->FixedArray_SetRegion_Double(array, 0, numbers.size(), numbers.data());
    return array;
}
```

