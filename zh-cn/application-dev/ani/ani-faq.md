# 常见问题解答（FAQ）
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

- **BusinessError无法创建或行为异常**：检查是否存在`BusinessError$partial`。系统可能包含内置的`BusinessError`，这会在ABC文件中引发冲突。请联系前端和标准库的维护人员。
- **`Object_New`后程序崩溃**：通常是由于参数类型不匹配。在查找构造函数时，绝不要使用`nullptr`作为签名。
- **声明和实现不匹配**：`.d.ets`和`.ets`文件之间的不一致会导致字段或方法无法识别。
- **`ani_boolean`无法正确打印**：它被定义为`uint8_t`，而不是`bool`。在输出前需要将其转换为`int`。
- **如何将`ani_int`/`ani_double`转换为`ani_ref`？**：先将它们装箱为`ani_object`，然后再转换为`ani_ref`。详见[类型转换](ani-type-definition.md#类型转换)。
- **如何在ETS垃圾回收（GC）时为native清理注册析构函数？**：目前不支持自动注册。必须在ETS中通过垃圾回收手动触发。
- **为什么ETS中的两个不同函数在native中具有相同的地址？**：native函数参数在内部使用固定指针槽。它们的地址会被复用。
- **如何在native中比较两个ETS函数参数？**：使用`GlobalReference_Create`保留`ani_ref`，并通过`Reference_StrictEquals`进行比较。
- **`Reference_StrictEquals`对不同实例返回`true`？**：对于像`String`这样的基本类型包装器，比较是基于内容的。对于自定义类，则是基于地址进行比较。
- **`String_GetUTF8SubString`在长度不足时会截断字符吗？**：会的。如果字节范围未覆盖完整字符，UTF-8子字符串将被截断。
- **为什么`Object_New`返回`ANI_INVALID_TYPE`？**：确保精确匹配构造函数的参数类型（例如，对于`long`类型的参数，使用`ani_long`）。
- **如何为`Promise<void>`函数编写`resolve`和`reject`？**：不支持这种操作。请更改为有返回类型的版本。
- **如何在设备上执行`.abc`文件并测试API？**：通过GN构建运行时，然后通过以下命令执行：
    ```bash
    export LD_LIBRARY_PATH=.;
    /path/to/ark --boot-panda-files=etsstdlib.abc --load-runtimes=ets run.abc run.ETSGLOBAL::main
    ```
- **构造函数支持可选参数吗？**：支持，通过重载实现。将每个重载绑定为一个单独的native构造函数。
- **为什么无法在命名空间方法中检索可选参数？**：使用`Namespace_BindNativeFunctions`时，不要将类对象作为第二个参数传递。
- **在命名空间绑定的native代码中访问联合类型时出现问题**：同样，在`Namespace_BindNativeFunctions`中，不要将类对象作为第二个参数传递。
- **声明并传递的参数在native中仍然为`nullptr`**：请检查[native绑定](load-library.md#native绑定)是否有误。
- **调用`Record.keys()`导致错误码14**：添加正确的签名`:C{std.core.IterableIterator}`以解决歧义。

