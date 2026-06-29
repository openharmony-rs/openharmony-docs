# 回调函数/Lambda函数对象
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

ArkTS函数对象传入native后，可以通过`FunctionalObject_Call`从C++侧回调。这个能力适合native侧需要立即调用ArkTS回调函数或lambda函数对象的场景。

函数对象和回调示例：[ani_fn_object/ani_fn_object.ets · LeechyLiang/ani_cookbook](https://gitcode.com/LeechyLiang/ani_cookbook/blob/master/ani_fn_object/ani_fn_object.ets)

```cpp
// 调用ArkTS函数对象，argv为参数数组，result接收返回值。
ani_status FunctionalObject_Call(ani_env *env, ani_fn_object fn, ani_size argc, ani_ref *argv, ani_ref *result);
```

此函数要求参数以`ani_ref`数组形式传入。

注意：函数对象（`functional object`）始终接受并返回装箱（boxed）的基本类型。这意味着如果参数是基本类型，例如`int`或者`double`，需要先将它们转换为对应的装箱类型（如`Int`,`Double`）,然后将这些对象传入数组中，并将参数数组指针传给`FunctionalObject_Call`。

**示例：**

创建`Double`实例的方式可参考[装箱](ani-argument-handling.md#装箱)。

```cpp
ani_object createDouble(ani_double doubleVal) { ... } // 返回一个Double实例
```

```cpp
std::vector<ani_ref> vec;
vec.push_back(createDouble(ani_double(2)));
vec.push_back(createDouble(ani_double(4)));

ani_ref result {};
env->FunctionalObject_Call(show_every, ani_size(2), vec.data(), &result);
```

