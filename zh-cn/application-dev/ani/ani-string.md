# 字符串 String
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

`ani_string`是ArkTS字符串在ANI中的引用类型，native侧接收、创建或返回字符串时，通常需要在`std::string`与`ani_string`之间转换。
  
> **注意：**
>
> 在“非VerifyANI”模式下，为了性能不验证编码。调用者有责任确保传入的是合法UTF-8/UTF-16字符。传入非法数据构建的ani_string，ANI不保证转换回c_str时内容的正确性，但不会导致ANI自身崩溃。

## 将`std::string`转换为`ani_string`
```cpp
std::optional<ani_string> ANIUtils_StdStringToANIString(ani_env *env, std::string str)
{
    ani_string result_string {};
    if (env->String_NewUTF8(str.c_str(), str.size(), &result_string) != ANI_OK) {
        return {};
    }
    return result_string;
}
```

## 将`ani_string`转换为`std::string`
```cpp
std::string ANIUtils_ANIStringToStdString(ani_env *env, ani_string ani_str)
{
    ani_size sz {};
    env->String_GetUTF8Size(ani_str, &sz);

    std::string result(sz + 1, 0);
    env->String_GetUTF8(ani_str, result.data(), result.size(), &sz);
    result.resize(sz);
    return result;
}
```

