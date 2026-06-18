# 枚举
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

ArkTS枚举在ANI中有专门的枚举和枚举项类型。ArkTS枚举作为native参数传入，或native侧需要按名称获取枚举项时，可以使用ANI提供的Enum相关接口。

ANI中操作枚举的接口：
```cpp
// 根据枚举描述符查找枚举类型。
ani_status FindEnum(ani_env *env, const char *enum_descriptor, ani_enum *result);

// 根据枚举项名称获取枚举项。
ani_status Enum_GetEnumItemByName(ani_env *env, ani_enum enm, const char *name, ani_enum_item *result);

// 根据枚举项下标获取枚举项。
ani_status Enum_GetEnumItemByIndex(ani_env *env, ani_enum enm, ani_size index, ani_enum_item *result);

// 获取枚举项所属的枚举类型。
ani_status EnumItem_GetEnum(ani_env *env, ani_enum_item enum_item, ani_enum *result);

// 获取整型枚举项的值。
ani_status EnumItem_GetValue_Int(ani_env *env, ani_enum_item enum_item, ani_int *result);

// 获取字符串枚举项的值。
ani_status EnumItem_GetValue_String(ani_env *env, ani_enum_item enum_item, ani_string *result);

// 获取枚举项名称。
ani_status EnumItem_GetName(ani_env *env, ani_enum_item enum_item, ani_string *result);

// 获取枚举项在枚举声明中的下标。
ani_status EnumItem_GetIndex(ani_env *env, ani_enum_item enum_item, ani_size *result);
```

| 标识符 | ANI类型 | Mangling  |
| ------------- | -------------- | --------------------- |
| `COLOR`       | `ani_enum`     | `E{moduleName.COLOR}` |
| `COLOR.Blue`  | `ani_enum_item`| `C{std.core.Object}`  |

示例：[ani_enum.cpp](https://gitee.com/LeechyLiang/ani_cookbook/blob/master/ani_enum/ani_enum.cpp)

