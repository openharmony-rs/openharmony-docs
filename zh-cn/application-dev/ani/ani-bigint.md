# 大整数 BigInt
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

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
    env->FindClass(className, &bigIntCls);
    ani_method getLongMethod;
    env->Class_FindMethod(bigIntCls, "getLong", ":l", &getLongMethod);

    ani_long longnum;
    env->Object_CallMethod_Long(num, getLongMethod, &longnum);

    std::cout << "num value is: '" << longnum << "'" << std::endl;
}

ANI_EXPORT ani_status ANI_Constructor(ani_vm *vm, uint32_t *result) {
    ani_env *env;
    vm->GetEnv(ANI_VERSION_1, &env);

    ani_module mod;
    env->FindModule("example", &mod);

    ani_native_function fn {"testBigInt", "C{std.core.BigInt}:", reinterpret_cast<void *>(TestBigIntImpl)};
    env->Module_BindNativeFunctions(mod, &fn, 1);
    *result = ANI_VERSION_1;
    return ANI_OK;
}
```

