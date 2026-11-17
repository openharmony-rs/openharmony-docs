# 回调函数/Lambda函数对象
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

ArkTS函数对象传入native后，可以通过`FunctionalObject_Call`从C++侧回调。这个能力适合native侧需要立即调用ArkTS回调函数或lambda函数对象的场景。

调用ArkTS函数对象的接口签名如下，`argv`为参数数组，`result`接收返回值：

```cpp
ani_status FunctionalObject_Call(ani_env *env, ani_fn_object fn, ani_size argc, ani_ref *argv, ani_ref *result);
```

此函数要求参数以`ani_ref`数组形式传入。

注意：函数对象（`functional object`）始终接受并返回装箱（boxed）的基本类型。这意味着如果参数是基本类型，例如`int`或者`double`，需要先将它们转换为对应的装箱类型（如`Int`,`Double`）,然后将这些对象传入数组中，并将参数数组指针传给`FunctionalObject_Call`。更多装箱说明可参考[装箱](ani-argument-handling.md#装箱)。

**示例：**

```ts
// 场景一：函数对象作为参数直接传入native函数。
native function handleData(sum: (a: double, b: double) => double, val1: double, val2: double): double

// 场景二：函数对象是类的字段，由native侧取出后回调。
native function CallFn(val1: double, val2: double): double

class OptionalClass {
    fn?: (a: double, b: double) => double = (a: double, b: double) => {return a + b}
}

function main() {
    handleData((a: double, b: double) => {return a + b}, 1.0, 2.0);
    CallFn(1.0, 2.0);
}
```

native侧实现`handleData`，通过`FunctionalObject_Call`回调传入的函数对象：

```cpp
// 场景一：函数对象作为参数传入，直接回调。
static ani_double handleData(ani_env *env, ani_fn_object fnObj, ani_double val1, ani_double val2)
{
    // 构造入参数组，基本类型转换为ani_ref需要装箱。
    std::vector<ani_ref> vec;
    ani_object boxedDouble1 {};
    ani_object boxedDouble2 {};
    ani_status status1 = env->Primitive_Box_Double(val1, &boxedDouble1);
    ani_status status2 = env->Primitive_Box_Double(val2, &boxedDouble2);
    if (status1 != ANI_OK || status2 != ANI_OK) {
        // handle error and return
    }
    vec.push_back(static_cast<ani_ref>(boxedDouble1));
    vec.push_back(static_cast<ani_ref>(boxedDouble2));

    ani_ref fnReturnVal;
    ani_status status = env->FunctionalObject_Call(fnObj, vec.size(), vec.data(), &fnReturnVal);
    if (status != ANI_OK) {
        // handle error and return
    }

    // 返回值类型如果要求是基本类型如ani_int、ani_double需要拆箱。
    ani_double sumRs;
    status = env->Primitive_Unbox_Double(static_cast<ani_object>(fnReturnVal), &sumRs);
    if (status != ANI_OK) {
        // handle error and return
    }
    return sumRs;
}

// 场景二：创建OptionalClass实例，取出fn字段转成ani_fn_object后回调。
ani_double CallFn(ani_env *env, ani_double val1, ani_double val2)
{
    ani_object classObj = {};
    static const char *className = "ani_fn_object.OptionalClass";
    ani_class cls;
    ani_status status = env->FindClass(className, &cls);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_method ctor;
    status = env->Class_FindMethod(cls, "<ctor>", nullptr, &ctor);
    if (status != ANI_OK) {
        // handle error and return
    }

    // 创建一个实例
    status = env->Object_New(cls, ctor, &classObj);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_ref fnRef;
    status = env->Object_GetFieldByName_Ref(classObj, "fn", &fnRef);
    if (status != ANI_OK) {
        // handle error and return
    }

    // 构造入参数组，基本类型转换为ani_ref需要装箱。
    std::vector<ani_ref> vec;
    ani_object boxedDouble1 {};
    ani_object boxedDouble2 {};
    ani_status status1 = env->Primitive_Box_Double(val1, &boxedDouble1);
    ani_status status2 = env->Primitive_Box_Double(val2, &boxedDouble2);
    if (status1 != ANI_OK || status2 != ANI_OK) {
        // handle error and return
    }
    vec.push_back(static_cast<ani_ref>(boxedDouble1));
    vec.push_back(static_cast<ani_ref>(boxedDouble2));

    ani_ref fnReturnVal;
    status = env->FunctionalObject_Call(static_cast<ani_fn_object>(fnRef), vec.size(), vec.data(), &fnReturnVal);
    if (status != ANI_OK) {
        // handle error and return
    }

    // 返回值类型如果要求是基本类型如ani_int、ani_double需要拆箱。
    ani_double sumRs;
    status = env->Primitive_Unbox_Double(static_cast<ani_object>(fnReturnVal), &sumRs);
    if (status != ANI_OK) {
        // handle error and return
    }
    return sumRs;
}
```

