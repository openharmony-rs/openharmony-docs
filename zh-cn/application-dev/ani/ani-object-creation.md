# 对象创建
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

在native侧主动构造ArkTS对象时，需要先查找类，再按精确签名找到构造函数或方法。这个流程适用于C++侧创建ArkTS标准库对象或业务类对象的场景。

## 查询标准类的方法

在 [stdlib](https://gitcode.com/openharmony/arkcompiler_runtime_core/blob/master/static_core/plugins/ets/stdlib/) 路径下查找所需的标准库函数。如果不确定要查询哪个类，可以反汇编`etsstdlib.abc`文件来确认类名和编译后的签名。

在 [ArrayBuffer.ets](https://gitcode.com/openharmony/arkcompiler_runtime_core/tree/master/static_core/plugins/ets/stdlib/std/core/ArrayBuffer.ets) 中找到`class ArrayBuffer`与对应的`constructor`。

代码片段：
```ts
export class ArrayBuffer extends Buffer
{
    public constructor(length: int, maxByteLength?: int)
    public constructor(length: number, maxByteLength?: number)
    public static isView(obj: Object): boolean
    get byteLength(): number
}
```

从上述代码片段中，可以发现：
1. 有两个构造函数。ANI识别的构造函数名为`<ctor>`。第一个构造函数的mangling可以写成`iC{std.core.Int}:`。**切勿使用`nullptr`代替构造函数签名** - 重载的methods需要通过函数签名进行区分。
2. 名为`isView`的方法，参数为`Object`，返回类型为`boolean`。它的mangling是`C{std.core.Object}:z`。
3. 一个`byteLength`属性。


## 查询非标准类的方法
一个典型的例子是枚举（enum）。ArkTS前端在编译过程中会为枚举生成特殊的类来支持其功能。

这些枚举类中生成的方法和字段属于实现细节（implementation-defined），因此不可以直接访问它们，以避免因版本变化或内部结构调整导致程序出错。

相反，ArkTS提供了专门的ANI接口来安全地操作枚举，例如[枚举](ani-enum.md)：

- `Enum_GetEnumItemByName`：通过名称获取枚举
- `EnumItem_GetValue_String`：获取枚举项的字符串值

## 创建类实例
1. 使用`FindClass`定位类。
2. 使用`Class_FindMethod`，通过正确的mangling查找所需的构造函数。
3. 使用`Object_New`创建对象。

### 示例

```ts
// 文件名: example.ets
// 模块名: example
// 默认情况下，模块名等于文件名

class Point {
    x: int
    y: int
    constructor(x: int, y: int) {
        this.x = x; this.y = y;
    }
    constructor(x: number, y: number) {
        this.x = x as int; this.y = y as int;
    }
}
```

1. FindClass：

   ```cpp
   ani_class cls {};
   env->FindClass("example.Point", &cls);
   ```

2. Class_FindMethod：

   ```cpp
   ani_method ctor1 {};
   env->Class_FindMethod(cls, "<ctor>", "ii:", &ctor1);
   ani_method ctor2 {};
   env->Class_FindMethod(cls, "<ctor>", "dd:", &ctor2);
   ```

   - mangling `ii:`与`constructor(x: int, y: int)`匹配；
   - mangling `dd:`与`constructor(x: double, y: double)`匹配。

   **永远不要使用nullptr代替构造函数签名**。这样做会使native代码容易出错，因为如果在托管代码中添加新的重载，原本依赖特定签名的native调用可能会意外失效或行为异常。

3. Object_New：

   ```cpp
   ani_object obj1 {};
   env->Object_New(cls, ctor1, &obj1, static_cast<ani_int>(1), static_cast<ani_int>(2));
   ani_object obj2 {};
   env->Object_New(cls, ctor2, &obj2, static_cast<ani_double>(1), static_cast<ani_double>(2));
   ```

   在这里：
   - `obj1`是使用`constructor(x: int, y: int)`创建的。
   - `obj2`是使用`constructor(x: double, y: double)`创建的。

### 创建ArkTS标准库类的实例
1. `FindClass`：在`arkcompiler/runtime_core/static_core/plugins/ets/stdlib`下定位类。文件会声明包名，通常是`std.core`或`escompat`，mangling将是`std.core.<ClassName>`或`escompat.<ClassName>`。
2. `Class_FindMethod`：通过mangling识别目标构造函数。
3. `Object_New`：调用此函数创建实例。

> **注意：**<br>
> 在ANI中，以下类型**不能**使用`Object_New`创建：
>
> - 接口类型
> - 抽象类
> - 字符串（`ani_string`）—— 必须使用专门的ANI创建函数
> - `FixedArray<T>`类型 —— 必须使用专门的ANI数组创建函数

