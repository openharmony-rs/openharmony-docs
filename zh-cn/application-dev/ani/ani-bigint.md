# 大整数 BigInt
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @k1ngqaquuu-->

ArkTS侧的`bigint`传入native函数后，在C++侧表现为`std.core.BigInt`对象，而不是ANI基本整数类型。native侧需要读取BigInt值时，可以调用`std.core.BigInt`提供的`getLong(): long`方法获取对应值。

```ts
// example.ets
native function testBigInt(num: bigint): void;

function main() {
    loadLibrary("libraryName");
    let n: bigint = 11223344n;
    testBigInt(n);
}
```

```cpp
static void TestBigIntImpl(ani_env *env, ani_object num) {
    static constexpr const char* className = "std.core.BigInt";
    ani_class bigIntCls;
    ani_status status = env->FindClass(className, &bigIntCls);
    if (status != ANI_OK) {
        // handle error and return
    }
    ani_method getLongMethod;
    status = env->Class_FindMethod(bigIntCls, "getLong", ":l", &getLongMethod);
    if (status != ANI_OK) {
        // handle error and return
    }

    ani_long longnum;
    status = env->Object_CallMethod_Long(num, getLongMethod, &longnum);
    if (status != ANI_OK) {
        // handle error and return
    }

    std::cout << "num value is: '" << longnum << "'" << std::endl;
}
```

