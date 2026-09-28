# 枚举
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

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

示例：

ArkTS侧声明枚举和native函数：

```ts
enum COLORINT {
    REDINT = 5,
    GREENINT = 77,
    BLUEINT = 9999
}

enum COLORSTRING {
    REDSTR = "str_red",
    GREENSTR = "str_green",
    BLUESTR = "str_blue"
}

native function getBlue(): COLORINT;
native function processEnumInt(color: COLORINT): COLORINT;
native function processEnumIntReturnNext(color: COLORINT): COLORINT;
native function getCOLORSTRING(enumIndex: int): COLORSTRING;

function main() {
    processEnumInt(COLORINT.REDINT);
    let blue = getBlue();
    console.info(blue);
    let nextColor = processEnumIntReturnNext(COLORINT.GREENINT);
    console.info(nextColor);
    getCOLORSTRING(0);
}
```

native侧实现：

```cpp
// native函数：根据下标获取枚举项。
static ani_enum_item getBlue(ani_env *env)
{
    ani_enum enumType;
    ani_status status = env->FindEnum("ani_enum.COLORINT", &enumType);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_enum_item enumItem;
    ani_size index = 2;
    // 等效方法：env->Enum_GetEnumItemByName(enumType, "BLUEINT", &enumItem);
    status = env->Enum_GetEnumItemByIndex(enumType, index, &enumItem);
    if (status != ANI_OK) {
        // handle error and return
    }
    return enumItem;
}

// native函数：按名称获取枚举项，再读取枚举项名称验证。
static ani_enum_item processEnumInt(ani_env *env, ani_enum_item enumObj)
{
    ani_string inputEnumName;
    // 通过enum实例获取enum属性的ani_string
    ani_status status = env->EnumItem_GetName(enumObj, &inputEnumName);
    if (status != ANI_OK) {
        // handle error and return
    }

    // 将ani_string转换为std::string后打印
    ani_size strSize;
    status = env->String_GetUTF8Size(inputEnumName, &strSize);
    if (status != ANI_OK) {
        // handle error and return
    }
    std::vector<char> buffer(strSize + 1);
    ani_size bytesWritten = 0;
    status = env->String_GetUTF8(inputEnumName, buffer.data(), strSize + 1, &bytesWritten);
    if (status != ANI_OK) {
        // handle error and return
    }
    std::cout << "inputEnumName: " << buffer.data() << std::endl;

    ani_enum enumType;
    status = env->FindEnum("ani_enum.COLORINT", &enumType);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_enum_item enumItem;
    // 通过enum属性的字符串获取enum实例
    status = env->Enum_GetEnumItemByName(enumType, "GREENINT", &enumItem);
    if (status != ANI_OK) {
        // handle error and return
    }
    return enumItem;
}

// native函数：获取枚举项的序号和值，并返回下一个枚举项。
static ani_enum_item processEnumIntReturnNext(ani_env *env, ani_enum_item enumObj)
{
    ani_size enumIndex;
    // 通过enum的实例获取其属性在enum中对应的序号
    ani_status status = env->EnumItem_GetIndex(enumObj, &enumIndex);
    if (status != ANI_OK) {
        // handle error and return
    }
    std::cout << "inputEnumIndex: " << enumIndex << std::endl;

    ani_int enumValue;
    // 通过enum的实例获取其属性的值
    status = env->EnumItem_GetValue_Int(enumObj, &enumValue);
    if (status != ANI_OK) {
        // handle error and return
    }
    std::cout << "inputEnumValue: " << enumValue << std::endl;

    ani_enum enumType;
    status = env->FindEnum("ani_enum.COLORINT", &enumType);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_enum_item enumItem;
    // Enum_GetEnumItemByIndex和Enum_GetEnumItemByName相当于Enum的Object_New
    status = env->Enum_GetEnumItemByIndex(enumType, enumIndex + 1, &enumItem);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_string nextEnumName;
    status = env->EnumItem_GetName(enumItem, &nextEnumName);
    if (status != ANI_OK) {
        // handle error and return
    }
    ani_size strSize;
    status = env->String_GetUTF8Size(nextEnumName, &strSize);
    if (status != ANI_OK) {
        // handle error and return
    }
    std::vector<char> buffer(strSize + 1);
    ani_size bytesWritten = 0;
    status = env->String_GetUTF8(nextEnumName, buffer.data(), strSize + 1, &bytesWritten);
    if (status != ANI_OK) {
        // handle error and return
    }
    std::cout << "nextEnumName: " << buffer.data() << std::endl;

    return enumItem;
}

// native函数：读取字符串枚举项的值。
static ani_enum_item getCOLORSTRING(ani_env *env, ani_int enumIndex)
{
    ani_enum enumType;
    ani_status status = env->FindEnum("ani_enum.COLORSTRING", &enumType);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_enum_item enumItem;
    status = env->Enum_GetEnumItemByIndex(enumType, enumIndex, &enumItem);
    if (status != ANI_OK) {
        // handle error and return
    }

    {
        ani_enum ownerEnum;
        // 从enumItem获取到enumType
        status = env->EnumItem_GetEnum(enumItem, &ownerEnum);
        if (status != ANI_OK) {
            // handle error and return
        }
    }

    ani_string stringValue;
    status = env->EnumItem_GetValue_String(enumItem, &stringValue);
    if (status != ANI_OK) {
        // handle error and return
    }
    ani_size strSize;
    status = env->String_GetUTF8Size(stringValue, &strSize);
    if (status != ANI_OK) {
        // handle error and return
    }
    std::vector<char> buffer(strSize + 1);
    ani_size bytesWritten = 0;
    status = env->String_GetUTF8(stringValue, buffer.data(), strSize + 1, &bytesWritten);
    if (status != ANI_OK) {
        // handle error and return
    }
    std::cout << "Enum Value: " << buffer.data() << std::endl;

    return enumItem;
}
```

此示例演示了枚举操作的常用模式：

- `getBlue`：`Enum_GetEnumItemByIndex`按下标获取枚举项，等效于`Enum_GetEnumItemByName`按名称获取；
- `processEnumInt`：byName处理版本，通过`EnumItem_GetName`读出名称再反查，不要求C++侧存储对应枚举值；
- `processEnumIntReturnNext`：综合使用`EnumItem_GetIndex`、`EnumItem_GetValue_Int`读取枚举项信息，再获取下一个枚举项。

