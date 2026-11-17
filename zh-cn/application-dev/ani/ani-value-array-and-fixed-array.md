# 定长数组：FixedArray\<T\>和ValueArray\<T\>
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

定长数组是一种长度不可变的数组类型。根据元素类型的不同，它在语言层有不同的表述：基本类型元素（boolean、char、byte、short、int、long、float、double）的定长数组为`ValueArray<T>`（如`ValueArray<int>`），引用类型元素（类实例、字符串等）的定长数组为`FixedArray<T>`（如`FixedArray<string>`）。

与普通泛型不同，定长数组的元素类型在编译阶段不会被擦除，`ValueArray<int>`、`ValueArray<double>`和`FixedArray<string>`等不同元素类型的定长数组在字节码和语言层面互不兼容。编译器会为不同的元素生成不同的底层结构，因此在native层需要使用**类型匹配的API进行操作**：

- 基本类型元素使用`ValueArray_*`系列API；
- 引用类型元素使用`FixedArray_*`系列API。

基本类型元素定长数组的创建和访问，使用`ValueArray_*`系列API：

```cpp
// 获取基本类型元素定长数组的长度。
ani_status ValueArray_GetLength(ani_env *env, ani_valuearray array, ani_size *result);

// 创建double元素类型的定长数组。
ani_status ValueArray_New_Double(ani_env *env, ani_size length, ani_valuearray_double *result);

// 批量读取double定长数组中的一段元素。
ani_status ValueArray_GetRegion_Double(ani_env *env, ani_valuearray_double array, ani_size offset, ani_size length, ani_double *native_buffer);

// 批量写入double定长数组中的一段元素。
ani_status ValueArray_SetRegion_Double(ani_env *env, ani_valuearray_double array, ani_size offset, ani_size length, const ani_double *native_buffer);
```

引用类型元素定长数组的创建和访问，使用`FixedArray_*`系列API：

```cpp
// 获取引用元素定长数组的长度。
ani_status FixedArray_GetLength(ani_env *env, ani_fixedarray array, ani_size *result);

// 创建引用元素类型的定长数组，initial_element用于初始化所有元素，可以为nullptr。
ani_status FixedArray_New(ani_env *env, ani_type type, ani_size length, ani_ref initial_element, ani_fixedarray *result);

// 读取定长数组中指定下标的引用元素。
ani_status FixedArray_Get(ani_env *env, ani_fixedarray array, ani_size index, ani_ref *result);

// 写入定长数组中指定下标的引用元素。
ani_status FixedArray_Set(ani_env *env, ani_fixedarray array, ani_size index, ani_ref ref);
```

**示例：**

```cpp
// 创建长度为3的double定长数组。
ani_size length = 3;
ani_valuearray_double array;
ani_status status = env->ValueArray_New_Double(length, &array);
if (status != ANI_OK) {
    // handle error and return
}

// 批量写入元素，从下标0开始。
ani_size offset = 0;
ani_double numbers[] = {1.0, 2.0, 3.0};
status = env->ValueArray_SetRegion_Double(array, offset, length, numbers);
if (status != ANI_OK) {
    // handle error and return
}
```

