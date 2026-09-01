# 字符串 String
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

`ani_string`是ArkTS字符串在ANI中的引用类型，native侧接收、创建或返回字符串时，通常需要在`std::string`与`ani_string`之间转换。
  
> **注意：**
>
> 在“非VerifyANI”模式下，为了性能不验证编码。调用者有责任确保传入的是合法UTF-8/UTF-16字符。传入非法数据构建的ani_string，ANI不保证转换回c_str时内容的正确性，但不会导致ANI自身崩溃。

## 将`std::string`转换为`ani_string`
```cpp
// str为std::string，通过UTF-8编码创建ani_string。
ani_string result_string {};
ani_status status = env->String_NewUTF8(str.c_str(), str.size(), &result_string);
if (status != ANI_OK) {
    // handle error and return
}
```

## 将`ani_string`转换为`std::string`
```cpp
// 1. 获取UTF-8编码的字节数。
ani_size sz {};
ani_status status = env->String_GetUTF8Size(ani_str, &sz);
if (status != ANI_OK) {
    // handle error and return
}

// 2. 拷贝到缓冲区。
std::string result(sz + 1, 0);
status = env->String_GetUTF8(ani_str, result.data(), result.size(), &sz);
if (status != ANI_OK) {
    // handle error and return
}
result.resize(sz);
```

