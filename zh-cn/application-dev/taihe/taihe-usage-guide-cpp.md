# Taihe C++用户文档

本文档旨在帮助用户了解如何使用Taihe根据IDL文件自动生成的C++代码，及Taihe C++运行时提供的功能（如泛型容器等）。

# 1. 生成的文件结构

在使用模块前，需要导入对应的头文件。头文件名与IDL文件的包名相关，例如，假设IDL文件名为`rgb.base.ohidl`，则`generated/include`目录下可能生成以下头文件：

```
generated/include/rgb.base.proj.hpp
generated/include/rgb.base.user.hpp
generated/include/rgb.base.impl.hpp
```

这些文件对于使用者的意义如下：

- 对于接口的作者（发布方），需要关注的是`proj.hpp`和`impl.hpp`，其中`proj.hpp`包含了当前包下定义的所有类型（包括枚举类、结构体、联合体、接口等，使用方式见后文）的C++声明和定义，而`impl.hpp`则提供了用于[导出全局函数](#71-导出函数接口发布方)的宏定义。
- 对于接口的用户（消费方），只需要关注`user.hpp`，该文件包含了`proj.hpp`中的所有内容，此外还允许用户直接[调用全局函数](#72-调用函数接口消费方)。

> **⚠️ 特别注意**
>
> 除这些文件之外，`generated/include`目录下还可能包含其他头文件，这些文件通常对应于IDL文件中定义的特定类型，例如`rgb.base.IShowable.{0,1,2}.hpp`等，这些文件是Taihe的内部实现文件，用户通常**_不应该_**直接使用它们，并且我们也**_不保证_**这些文件的稳定性，它们可能会在未来的版本中发生变化。

# 2. 枚举类

假设在IDL文件中定义了一个枚举类`Color`，其定义如下：

```rust
enum Color: String {
    BLACK = "black",
    RED = "red",
    GREEN = "green",
    YELLOW = "yellow",
    BLUE = "blue",
    MAGENTA = "magenta",
    CYAN = "cyan",
    WHITE = "white",
}
```

## 2.1 构造

### 2.1.1 通过Key初始化对象

可以通过如下方式，直接根据枚举值来创建枚举类对象：

```cpp
rgb::base::Color yellow = rgb::base::Color::key_t::YELLOW;
```

### 2.1.2 通过Value初始化对象

也可以通过值初始化枚举类对象：

```cpp
auto yellow = rgb::base::Color::from_value("yellow");
```

如果指定的值不在枚举类定义的范围内，则会创建一个无效的枚举对象。可以通过`is_valid()`方法[检查对象](#223-判断枚举值是否有效)是否有效。假如有多个枚举项的值相同，会默认返回第一个匹配的枚举项。

## 2.2 枚举类的成员函数

### 2.2.1 获取枚举值

可以使用`get_value()`方法获取枚举值：

```cpp
char const* value = yellow.get_value();  // "yellow"
```

### 2.2.2 获取对象的Key

可以使用`get_key()`方法获取枚举类对象的Key：

```cpp
rgb::base::Color::key_t key = yellow.get_key();

switch (key) {
    case rgb::base::Color::key_t::BLACK:   /* Process */ break;
    case rgb::base::Color::key_t::RED:     /* Process */ break;
    case rgb::base::Color::key_t::GREEN:   /* Process */ break;
    case rgb::base::Color::key_t::YELLOW:  /* Process */ break;
    case rgb::base::Color::key_t::BLUE:    /* Process */ break;
    case rgb::base::Color::key_t::MAGENTA: /* Process */ break;
    case rgb::base::Color::key_t::CYAN:    /* Process */ break;
    case rgb::base::Color::key_t::WHITE:   /* Process */ break;
}
```

> **💡 提示：Key与Value的区别**
>
> - **Key**
>   枚举项的名称，例如`Color::key_t::YELLOW`。它是一个强类型，可以安全地用于`switch`语句。
> - **Value**
>   枚举项关联的值，例如`"yellow"`。
>
> 特别注意：对于整数类型的枚举，将Key强制转换为整数得到的是**索引（index）**，而非其**值（value）**。
>
> 例如，假设有以下枚举定义：
>
> ```rust
> enum IntEnum: i32 {
>     FOO = 12, // index 0
>     BAR = 34, // index 1
> }
> ```
>
> 在C++中使用时：
>
> ```cpp
> // 从IntEnum::key_t转换为枚举值
> auto key = IntEnum::key_t::FOO;
> int index = static_cast<int>(key); // 结果是0而非12
> int value = IntEnum(key).get_value(); // 结果是12
>
> // 从整型枚举值转换为Taihe枚举对象
> IntEnum fooA = static_cast<IntEnum::key_t>(12); // 不正确！因为12不是IntEnum的有效Key
> IntEnum fooB = IntEnum::from_value(12); // 正确，fooB.get_key()返回IntEnum::key_t::FOO
> ```

> **💡 枚举对象的相等性**
>
> 枚举类对象的相等性比较是基于其Key而非Value的。即使两个枚举对象的Value相同，但Key不同，它们也被视为不同的枚举对象。
>
> 例如，假设有以下枚举定义：
>
> ```rust
> enum DuplicateEnum: i32 {
>     FOO = 1,
>     BAR = 1,
> }
> ```
>
> 在上例中，`FOO`和`BAR`是不同的枚举对象，即使它们的Value都是1。
>
> ```cpp
> DuplicateEnum foo = DuplicateEnum::key_t::FOO;
> DuplicateEnum bar = DuplicateEnum::key_t::BAR;
> bool is_equal = (foo == bar);  // false
> bool value_is_equal = (foo.get_value() == bar.get_value());  // true
> ```

### 2.2.3 判断枚举值是否有效

可以使用`is_valid()`方法判断一个枚举对象是否有效，在返回`false`的情况下，调用`get_value()`等方法可能导致未定义行为（UB）。

```cpp
auto yellow = rgb::base::Color::from_value("yellow");
bool yellow_is_valid = yellow.is_valid();  // true
char const* yellow_value = yellow.get_value();  // "yellow"

auto purple = rgb::base::Color::from_value("purple");
bool purple_is_valid = purple.is_valid();  // false
char const* purple_value = purple.get_value();  // UB

rgb::base::Color color_7 = static_cast<rgb::base::Color::key_t>(7);
bool color_7_is_valid = color_7.is_valid();  // true
char const* color_7_value = color_7.get_value();  // "white"

rgb::base::Color color_8 = static_cast<rgb::base::Color::key_t>(8);
bool color_8_is_valid = color_8.is_valid();  // false
char const* color_8_value = color_8.get_value();  // UB
```

# 3. 结构体

使用IDL文件中定义的结构体时，应使用对应命名空间下的结构体名称`package::name::StructName`。你可以像使用C++原生结构体那样使用它们。初始化结构体成员时使用花括号（`{}`）语法。

以下是一个示例，假设结构体在IDL中的定义如下：

```rust
struct RGB {
    red: u8;
    green: u8;
    blue: u8;
}
```

可以在C++中这样创建和初始化结构体对象：

```cpp
rgb::base::RGB color_rgb = rgb::base::RGB{0x39, 0xC5, 0xBB};

// 或者使用命名初始化
rgb::base::RGB color_rgb = rgb::base::RGB{
    .red = 0x39,
    .green = 0xC5,
    .blue = 0xBB,
};
```

> **💡 结构体的默认构造函数**
>
> 一个结构体是否支持默认构造函数取决于其成员类型。如果所有成员类型都支持默认构造函数，则结构体也支持默认构造。

# 4. 联合体

本节介绍如何在C++中使用Taihe中定义的联合体（Union）。以下面的IDL文件中的联合体定义为例：

```rust
union RGBOrColorOrName {
    rgb: RGB;
    color: Color;
    name: String;
    unknown;
}
```

## 4.1 构造联合体对象

### 4.1.1 使用工厂方法创建对象

可以通过类提供的静态工厂方法`package::name::EnumName::make_variantName(...)`构造对应变体的对象。例如：

```cpp
auto color_114514 = rgb::base::RGBOrColorOrName::make_rgb(RGB{0x11, 0x45, 0x14});
auto color_yellow = rgb::base::RGBOrColorOrName::make_color(rgb::base::Color::key_t::YELLOW);
auto color_miku = rgb::base::RGBOrColorOrName::make_name("Miku");
auto color_unknown = rgb::base::RGBOrColorOrName::make_unknown();  // 构造taihe::unit类型时不需要参数
```

### 4.1.2 使用就地构造函数

也可以直接使用构造函数进行就地初始化。该方法的形式为：

```cpp
package::name::EnumName(taihe::static_tag<package::name::EnumName::tag_t::variantName>, item_init_args, ...);
```

例如：

```cpp
auto color_miku =
    rgb::base::RGBOrColorOrName(taihe::static_tag<rgb::base::RGBOrColorOrName::tag_t::name>, "Miku");
```

## 4.2 修改枚举类/联合体对象

已创建的对象可以通过`emplace_variantName(...)`方法修改为其他变体。例如：

```cpp
color_miku.emplace_rgb(RGB{0x39, 0xC5, 0xBB});
```

## 4.3 检查对象当前的变体类型

可以使用`holds_variantName()`方法判断当前对象是否为指定变体。该方法返回一个`bool`类型的值。例如：

```cpp
bool is_name = color_miku.holds_name();
```

## 4.4 获取对象中的数据

### 4.4.1 安全获取数据指针

`get_variantName_ptr()`方法用于安全获取数据指针。如果当前对象是指定变体，该方法返回指向其数据的指针；否则返回空指针。例如：

```cpp
rgb::base::RGB* rgb_ptr = color_114515.get_rgb_ptr();
if (rgb_ptr != nullptr) {
    // 使用rgb_ptr ...
}
```

### 4.4.2 不安全获取数据指针

使用`get_variantName_ref()`方法可以直接获取成员数据的引用，但不会检查变体类型是否正确。如果当前对象不是指定变体类型，可能会导致程序崩溃。因此，使用时应确保对象确实是该变体类型。例如：

```cpp
if (color_114515.holds_rgb()) {
    rgb::base::RGB& rgb_ref = color_114515.get_rgb_ref();
    // 使用rgb_ref ...
}
```

## 4.5 获取当前变体的标记（Tag）

使用`get_tag()`方法可以获取当前对象的变体标记，返回值类型为`package::name::EnumName::tag_t`。例如：

```cpp
rgb::base::RGBOrColorOrName::tag_t tag = color_miku.get_tag();
```

## 4.6 模板方法

上述方法均有等效的模板函数版本，形式如下：

```cpp
using ColorVariant = rgb::base::RGBOrColorOrName;
using Tag = ColorVariant::tag_t;

// 等效于ColorVariant::make_rgb(RGB{0x11, 0x45, 0x14})
ColorVariant color = ColorVariant::make<Tag::rgb>(RGB{0x11, 0x45, 0x14});

// 等效于color.emplace_name("Miku")
color.emplace<Tag::name>("Miku");

// 等效于color.holds_name()
bool is_name = color.holds<Tag::name>();

// 等效于color.get_name_ptr()
auto* ptr = color.get_ptr<Tag::name>();

// 等效于color.get_name_ref()
auto& ref = color.get_ref<Tag::name>();
```

## 4.7 进阶：使用访问者模式处理不同变体

联合体还提供了`match`方法，允许用户通过访问者模式（Visitor Pattern）来处理不同的变体。以下是一个示例，假设我们要将`RGBOrColorOrName`的不同变体转换为字符串表示，可以定义一个访问者类：

```cpp
class ColorVariantVisitor {
public:
    std::string case_rgb(rgb::base::RGB const& rgb) {
        return std::format("#{:02X}{:02X}{:02X}", rgb.red, rgb.green, rgb.blue);
    }

    std::string case_name(taihe::string const& name) {
        return std::format("Name: {}", name.c_str());
    }

    std::string case_color(rgb::base::Color const& color) {
        return std::format("Color: {}", color.get_value());
    }

    std::string case_unknown(taihe::unit) {
        return "Unknown";
    }
};
```

然后可以使用`match`方法来处理联合体对象：

```cpp
auto result = rgb::base::RGBOrColorOrName::make_rgb(RGB{0x39, 0xC5, 0xBB})
    .match<std::string>(ColorVariantVisitor{});  // result将包含"#39C5BB"
```

此外，`match`方法还有模板版本`visit`，区别在于`match`通过方法名（`case_variantName`）进行匹配，而`visit`通过重载`operator()`和标记类型`static_tag_t<package::name::EnumName::tag_t::variantName>`进行匹配：

```cpp
class ColorVariantFunctionVisitor {
public:
    std::string operator()(taihe::static_tag_t<Tag::rgb>, rgb::base::RGB const& rgb) {
        return std::format("#{:02X}{:02X}{:02X}", rgb.red, rgb.green, rgb.blue);
    }

    std::string operator()(taihe::static_tag_t<Tag::name>, taihe::string const& name) {
        return std::format("Name: {}", name.c_str());
    }

    std::string operator()(taihe::static_tag_t<Tag::color>, rgb::base::Color const& color) {
        return std::format("Color: {}", color.get_value());
    }

    std::string operator()(taihe::static_tag_t<Tag::unknown>, taihe::unit) {
        return "Unknown";
    }
};

auto result = rgb::base::RGBOrColorOrName::make_rgb(RGB{0x39, 0xC5, 0xBB})
    .visit<std::string>(ColorVariantFunctionVisitor{});
```

# 5. 接口

本节介绍Taihe文件中定义的接口在C++中的使用方法。以下是一个示例，假定IDL文件中定义了一个接口`IShowable`，其定义如下：

```rust
interface IHasColor {
    getColor(): RGBOrColorOrName;
    setColor(color: RGBOrColorOrName);
}

interface IShape {
    getId(): String;
    calculateArea(): f32;
}

interface IShowable: IHasColor, IShape {
    show();
}
```

## 5.1 接口的实现

用户可以通过实现IDL文件中定义的接口来自定义类。接口的实例化可以通过`taihe::make_holder<ImplClass, InterfaceA, InterfaceB, ...>(...)`方法实现，其中`InterfaceA`, `InterfaceB`等为IDL中定义的接口，`ImplClass`为用户自定义的类，该类需要实现所有接口中定义的方法。

在C++中定义一个实现了`IShowable`接口的C++实现类`ColoredCircle`如下：

```cpp
class ColoredCircle {
public:
    // 任意的构造函数
    ColoredCircle(taihe:core::string_view id, float r, rgb::show::RGBOrColorOrName const& color);

    // 析构函数
    ~ColoredCircle();

    // 实现在IDL中定义的接口方法
    taihe::string getId();
    float calculateArea();
    rgb::show::RGBOrColorOrName getColor();
    void setColor(rgb::show::RGBOrColorOrName const& color);
    void show();

private:
    // 其他内部实现细节 ...
};
```

一旦实现了接口，就可以通过`taihe::make_holder`创建一个持有该接口的类智能指针对象。以下是使用`ColoredCircle`类创建一个`IShowable`接口对象的示例：

```cpp
// 创建接口对象
rgb::show::IShowable circle =
    taihe::make_holder<ColoredCircle, rgb::show::IShowable>("myCircle", 10, color_114514);
```

> **💡 Taihe interface和C++实现类之间的关系**
>
> 事实上，`ColoredCircle`类本身完全是独立的，与IDL文件中声明的`IShowable`接口并没有耦合。只要在该类中实现了`IShowable`接口定义的所有方法，就可以通过Taihe的接口机制将其与IDL文件中的接口关联起来。反过来，接口`IShowable`本身也并不会与`ColoredCircle`类绑定，你完全可以定义多个类都实现了同一个接口。

## 5.2 接口的转换

接口支持以下两种转换方式：

- **静态转换**：子接口到父接口间的转换是隐式、静态的。例如：

  ```cpp
  // 子接口
  my::package::IDerived d0;
  // 父接口
  my::package::IBase b0 = d0; // OK
  my::package::weak::IBase b0 = d0; // OK
  ```

- **动态转换**：除子接口向父接口的转换外，其他接口间的类型转换是动态的，需要显式写出，并需要在运行时检查转换后得到的对象是否有效。

  ```cpp
  // 父接口
  my::package::IBase b1;
  // 子接口
  my::package::weak::IDerived d1 = b1; // Error: 无法隐式从父接口转换为子接口
  auto d2 = my::package::weak::IDerived(b1); // OK
  if (!d2.is_error()) {  // 通过is_error()检查转换是否成功
      // 转换成功，可以使用d2
      std::cout << "Conversion succeeded!" << std::endl;
  } else {
      // 转换失败，b1不是IDerived的实例
      std::cerr << "Conversion failed!" << std::endl;
  }
  ```

> **💡 扩展：Taihe实现静态转换和动态转换的原理**
>
> Taihe的接口动态转换基于胖指针（fat pointer）实现。每个接口对象都包含一个指向实际对象数据的指针和一个接口虚表（vtable）的指针。虚表则由若干函数表（function table）组成，每个函数表对应于一个接口，里面存储了该接口的所有方法的指针。且虚表内的函数表排布顺序由IDL中声明的接口的继承关系确定，因此，可以通过子接口的虚表指针静态计算出其父接口的虚表指针，从而实现静态转换。
>
> 动态转换则需要在运行时检查实际对象是否实现了目标接口。每个Taihe接口在二进制中都对应一个接口ID（IID），当通过`taihe::make_holder`创建对象时，对象数据内存的前面会被插入一个指向运行时类型信息（RTTI）的指针，而在RTTI中，则包含从该对象实现的所有接口所对应IID到相应虚表的映射关系。进行动态转换时，会尝试查询此映射表找到对应虚表指针。

## 5.3 接口方法的调用

通过`->`运算符调用接口自己的方法。例如：

```cpp
rgb::show::IShowable circle =
    taihe::make_holder<ColoredCircle, rgb::show::IShowable>("myCircle", 10, color_114514);
circle->show();
```

> **💡 调用父接口的方法**
>
> 您不能直接在子接口上调用父接口的方法。必须先将接口转换为父接口类型，然后再调用。
>
> ```cpp
> // 错误
> circle->calculateArea();
>
> // 正确
> rgb::show::weak::IShape shape = circle; // 静态转换为父接口
> float area = shape->calculateArea();
> ```

## 5.4 接口的生命周期管理

接口对象的生命周期通过引用计数进行管理，对于每个在IDL文件中定义的接口，Taihe会生成两种对应的类型：

- **强引用**：`package::name::interfaceName`，类似于`std::shared_ptr`。
- **弱引用**：`package::name::weak::interfaceName`，类似于`std::weak_ptr`。

在参数传递时，为避免增加引用计数，可使用弱引用。例如：

```cpp
void copyColorImpl(rgb::base::weak::IColorable dst, rgb::base::weak::IColorable src) {
    dst->setColor(src->getColor());
}
```

强引用类型和弱引用类型之间可以相互转换：

- 强引用转换为弱引用

  ```cpp
  rgb::base::IColorable colorable = taihe::make_holder<ColoredCircle, rgb::base::IColorable>("myCircle", 10, color_114514);
  rgb::base::weak::IColorable weakColorable = colorable;
  ```

- 弱引用转换为强引用

  ```cpp
  class MyClass {
      rgb::base::IColorable colorable_;

  public:
      MyClass(rgb::base::weak::IColorable weakColorable) {
          colorable_ = weakColorable;
      }
  };
  ```

当对象的引用计数为0时，对象会被自动销毁。销毁时，除释放内存外，具体实现类的析构函数也会被自动调用。

## 5.5 进阶：`taihe::impl_holder`和`taihe::impl_view`

如[5.1](#51-接口的实现)所述，Taihe接口和C++实现类之间的关系是松耦合的。当一个C++对象被转换为Taihe接口类型后，将只保留和Taihe接口对应的能力（如调用你在Taihe接口里声明的方法、进行接口间的静态/动态转换等），而其他与原C++类相关的信息都会被“丢掉”。这意味着，假如你在IDL文件中定义了一个接口`IFoo`：

```rust
// my.package.ohidl
interface IFoo {
    doSomething();
}
```

而在C++中定义了一个类`FooImpl`来实现这个接口：

```cpp
class FooImpl {
public:
    void doSomething() { /* 实现 */ }
    void doSomethingElse() { /* 实现 */ }
};
```

那么当你将`FooImpl`类的实例创建为`IFoo`接口对象后，则无法再调用`doSomethingElse()`方法，因为`IFoo`接口并没有定义这个方法。

```cpp
my::package::IFoo foo = taihe::make_holder<FooImpl, my::package::IFoo>();
foo->doSomething(); // OK
foo->doSomethingElse(); // Error: IFoo没有doSomethingElse方法
```

但是，下面的写法却是可以的：

```cpp
auto fooImpl = taihe::make_holder<FooImpl, my::package::IFoo>();
fooImpl->doSomething(); // OK
fooImpl->doSomethingElse(); // Also OK
```

事实上，调用`taihe::make_holder<FooImpl, my::package::IFoo>`直接创建的`fooImpl`的实际类型为`taihe::impl_holder<FooImpl, my::package::IFoo>`而非`my::package::IFoo`，它相当于一个持有`FooImpl`类实例，并可以隐式静态转换为`my::package::IFoo`接口的智能指针。因此可以访问`FooImpl`类的所有方法。而在之前的例子中，`foo`在创建后就被转换为`my::package::IFoo`接口类型，丢失了对`FooImpl`类的引用。

## 5.6 进阶：同时实现多个接口

如果在`file.ohidl`中定义了`IReadable`和`IWritable`两个接口：

```rust
interface IReadable {
    read(): String;
}
interface IWritable {
    write(data: String);
}
```

在C++中可以实现一个类同时实现这两个接口的方法：

```cpp
class FileHandler {
public:
    FileHandler(taihe::string_view filename);
    taihe::string read();
    void write(taihe::string_view data);
};
```

然后使用`taihe::make_holder`创建一个同时实现这两个接口的对象：

```cpp
auto fileHandler = taihe::make_holder<FileHandler, rgb::show::IReadable, rgb::show::IWritable>("file.txt");

rgb::show::IReadable readable = fileHandler;  // OK
rgb::show::IWritable writable = fileHandler;  // OK

// 调用接口方法
writable->write("Hello, Taihe!");
taihe::string content = readable->read();

// 它们本质上指向同一个对象，可以动态转换
auto readableAsWritable = rgb::show::weak::IWritable(readable);
bool isWritable = not readableAsWritable.is_error();  // true
auto writableAsReadable = rgb::show::weak::IReadable(writable);
bool isReadable = not writableAsReadable.is_error();  // true
```

## 5.7 进阶：自定义对象的比较和哈希

比较和哈希是对象的重要特性，特别是在使用容器（如`set`、`map`等）时。因此，它们被作为所有Taihe对象的内置属性，而非单独的接口。在C++中，可以通过特化`taihe::same_impl_t`和`taihe::hash_impl_t`模板类来实现自定义的比较和哈希方法。

例如，假设我们有一个类`MyComparableObject`，它实现了上面的`IShape`接口，并且我们希望在使用Taihe时能够根据对象的`id`属性进行比较和哈希，就可以按照以下方式进行特化：

```cpp
struct MyComparableObject {
  string id_;

  MyComparableObject(string_view id) : id_(id) {}

  string getId() const {
    return id_;
  }

  // 其他方法 ...
};

// 针对MyComparableObject类特化模板类taihe::same_impl_t来实现其比较方法
template<>
struct taihe::same_impl_t<MyComparableObject> {
  // data_view和data_holder表示任意Taihe interface对象
  // 其中data_view是弱引用，data_holder是强引用
  bool operator()(data_view lhs, data_view rhs) const {
    // 尝试将data_view转换为IShape接口
    auto lhs_with_id = weak::IShape(lhs);
    auto rhs_with_id = weak::IShape(rhs);
    if (lhs_with_id.is_error() || rhs_with_id.is_error()) {
      // 如果对象不是IShape接口的实例，则回退到默认比较方法
      return same_impl_t<void>{}(lhs, rhs);
    }
    return lhs_with_id->getId() == rhs_with_id->getId();
  }
};

// 同上，针对MyComparableObject类特化模板类taihe::hash_impl_t来实现其哈希方法
template<>
struct taihe::hash_impl_t<MyComparableObject> {
  std::size_t operator()(data_view val) const {
    auto val_with_id = weak::IShape(val);
    if (val_with_id.is_error()) {
      return hash_impl_t<void>{}(val);
    }
    return std::hash<std::string_view>{}(val_with_id->getId());
  }
};
```

对于未特化`taihe::same_impl_t`和`taihe::hash_impl_t`的类型，Taihe会采用默认实现，这些默认实现会使用对象的内存地址进行比较和哈希。这意味着如果两个对象的内存地址相同，则被认为是相同的对象；如果不同，则被认为是不同的对象。

```cpp
template<typename Impl, typename Enabled = void>
struct hash_impl_t {
  std::size_t operator()(data_view val) const {
    return reinterpret_cast<std::size_t>(val.data_ptr);
  }
};

template<typename Impl, typename Enabled = void>
struct same_impl_t {
  bool operator()(data_view lhs, data_view rhs) const {
    return lhs.data_ptr == rhs.data_ptr;
  }
};
```

使用示例：

```cpp
// 使用自定义的比较和哈希函数
IShape obj_0 = taihe::make_holder<MyComparableObject, weak::IShape>("foo");
IShape obj_1 = taihe::make_holder<MyComparableObject, weak::IShape>("foo");
IShape obj_2 = taihe::make_holder<MyComparableObject, weak::IShape>("bar");
IColorable obj_3 = taihe::make_holder<MyComparableObject, weak::IColorable>("foo");

assert(obj_0 == obj_1);
// 调用对obj_0所对应类特化的比较方法，比较obj_0和obj_1的id，结果相等
assert(obj_0 != obj_2);
// 调用对obj_0所对应类特化的比较方法，比较obj_0和obj_2的id，结果不等
assert(obj_0 != obj_3);
// 在调用对obj_0所对应类特化的比较方法进行比较时，由于obj_3没有实现IShape接口，会回退到默认比较方法，
// 进而比较obj_0和obj_3的内存地址，结果不等

assert(std::hash<IShape>{}(obj_0) == std::hash<std::string_view>{}(obj_0->getId()));
// 调用对obj_0所对应类特化的哈希方法
```

# 6. 容器类型

Taihe提供了丰富的容器类型来满足不同的数据存储需求。这些容器类型分为两类：

- **值语义容器**：`Array<T>`和`Optional<T>`，拷贝时会复制内部数据
- **引用语义容器**：`String`、`Vector<T>`、`Map<K,V>`、`Set<T>`和函数闭包，通过引用计数管理生命周期

每种容器都有两种对应的C++类型：

- **持有者类型**（如`taihe::string`）：拥有数据的所有权，类似于`std::shared_ptr`
- **视图类型**（如`taihe::string_view`）：不拥有数据，但同样支持访问数据的一般方法，可用于参数传递等场景，避免引用计数的开销

## 6.1 字符串（String）

字符串是Taihe中最常用的容器类型之一，通过引用计数进行管理。

- **持有者类型**：`taihe::string`
- **视图类型**：`taihe::string_view`

### 6.1.1 创建字符串

`taihe::string`可以从C字符串、`std::string`或`std::string_view`创建，以下是一些示例：

```cpp
#include <taihe/string.hpp>

// 从C字符串创建
taihe::string str1 = "Hello, Taihe!";

// 从std::string创建
std::string std_str = "Hello";
taihe::string str2 = std_str;

// 从std::string_view创建
std::string_view std_sv = "World";
taihe::string str3 = std_sv;

// 指定长度创建
taihe::string str4("Hello", 5);
```

### 6.1.2 字符串操作

以下是一些常用的字符串操作示例：

```cpp
// 字符串连接
taihe::string hello = "Hello";
taihe::string world = "World";
taihe::string greeting = hello + ", " + world + "!";

// 使用concat函数连接多个字符串
taihe::string result = taihe::concat({hello, ", ", world, "!"});

// 获取子串
taihe::string sub = greeting.substr(0, 5);  // "Hello"

// 访问字符
char first = greeting[0];  // 'H'
char last = greeting.back();  // '!'

// 获取长度和判空
size_t len = greeting.size();
bool is_empty = greeting.empty();

// 转换为std::string_view
std::string_view view = greeting;  // 隐式转换

// 获取C字符串指针
const char* c_str = greeting.c_str();
```

### 6.1.3 字符串视图

在函数参数中建议使用`taihe::string_view`以避免引用计数的开销：

```cpp
void process_string(taihe::string_view sv) {
    std::cout << "Processing: " << sv << std::endl;
}

// 调用时可以传入string或string_view
taihe::string str = "Hello";
process_string(str);  // 自动转换为string_view
process_string("World");  // 直接从C字符串创建string_view

// 也可以传入std::string或std::string_view
std::string std_str = "Taihe";
process_string(std_str);
std::string_view std_sv = "Taihe";
process_string(std_sv);
```

## 6.2 数组（Array）

定长数组，在创建后大小不可改变，且为值语义，没有引用计数，拷贝时会复制内部所有元素。

- **持有者类型**：`taihe::array<T>`
- **视图类型**：`taihe::array_view<T>`

### 6.2.1 创建数组

`taihe::array<T>`可以通过指定大小或使用初始化列表创建，以下是一些示例：

```cpp
#include <taihe/array.hpp>

// 1. 创建指定大小的数组（元素默认初始化）
taihe::array<int> arr1(5);

// 2. 创建并用特定值填充
taihe::array<int> arr2(5, 42);  // 5个元素，都是42

// 3. 从初始化列表创建
taihe::array<int> arr3 = {1, 2, 3, 4, 5};

// 4. 从std::vector创建
std::vector<int> vec = {6, 7, 8};
taihe::array<int> arr4(taihe::copy_data, vec.begin(), vec.size());

// 5. 从C数组创建
int c_arr[] = {9, 10, 11};
taihe::array<int> arr5(taihe::copy_data, c_arr, 3);
```

对于4和5的创建方式，你也可以使用`taihe::move_data`代替`taihe::copy_data`作为第一个参数来表示从源容器中移动逐个数据，而不是复制它们。

### 6.2.2 访问和遍历

Taihe的数组提供了多种访问和遍历方式，以下是一些常用操作：

```cpp
// 下标访问
int first = arr3[0];
int last = arr3[arr3.size() - 1];

// 安全访问（会检查边界）
try {
    int value = arr3.at(10);  // 抛出std::out_of_range
} catch (const std::out_of_range& e) {
    // 处理越界
}

// 获取首尾元素
int front = arr3.front();
int back = arr3.back();

// 遍历数组
for (int value : arr3) {
    std::cout << value << " ";
}

// 使用迭代器
for (auto it = arr3.begin(); it != arr3.end(); ++it) {
    std::cout << *it << " ";
}

// 获取原始指针和大小
int* data = arr3.data();
size_t size = arr3.size();
```

### 6.2.3 数组视图

`taihe::array_view`用于函数参数传递：

```cpp
void process_array(taihe::array_view<int> view) {
    for (int value : view) {
        // 处理元素
    }
}

// 可以传入array、vector、C数组等
taihe::array<int> arr = {1, 2, 3};
std::vector<int> vec = {4, 5, 6};
int c_arr[] = {7, 8, 9};

process_array(arr);
process_array(vec);
process_array(c_arr);
```

## 6.3 可选类型（Optional）

表示可能不存在的值。和数组一样，可选类型也是值语义，没有引用计数，拷贝时会复制内部的数据。

- **持有者类型**：`taihe::optional<T>`
- **视图类型**：`taihe::optional_view<T>`

### 6.3.1 创建可选类型

通过`std::in_place`或`std::nullopt`创建可选类型：

```cpp
#include <taihe/optional.hpp>

// 创建空的optional
taihe::optional<int> opt1;
taihe::optional<int> opt2 = std::nullopt;

// 创建包含值的optional
taihe::optional<int> opt3(std::in_place, 42);
auto opt4 = taihe::optional<taihe::string>(std::in_place, "Hello");
```

### 6.3.2 检查和访问值

Taihe的可选类型提供了和C++标准库类似的接口来检查和访问值：

```cpp
// 检查是否有值，也可以直接写成if (opt3) { ... }
if (opt3.has_value()) {
    int value = opt3.value();  // 获取值
}

// 使用value_or提供默认值
int value = opt1.value_or(0);  // 如果为空返回0

// 使用指针语法访问
if (opt4) {
    std::cout << opt4->length() << std::endl;  // 调用string的方法
    std::cout << *opt4 << std::endl;  // 解引用获取值
}
```

## 6.4 动态数组（Vector）

可动态增长的数组，通过引用计数进行管理。

- **持有者类型**：`taihe::vector<T>`
- **视图类型**：`taihe::vector_view<T>`

### 6.4.1 创建和基本操作

```cpp
#include <taihe/vector.hpp>

// 创建空vector
taihe::vector<int> vec1;

// 添加元素
vec1.push_back(42);
vec1.push_back(100);

// 就地构造元素
vec1.emplace_back(200);

// 访问元素
int first = vec1[0];

// 删除最后一个元素
vec1.pop_back();
```

### 6.4.2 容量管理

```cpp
// 预留容量
vec1.reserve(100);  // 预分配空间，避免频繁重新分配

// 获取当前容量
size_t capacity = vec1.capacity();
```

### 6.4.3 获取大小、遍历和清空

```cpp
// 获取大小
size_t size = vec1.size();

// 范围for循环
for (const auto& value : vec1) {
    std::cout << value << " ";
}

// 使用迭代器
for (auto it = vec1.begin(); it != vec1.end(); ++it) {
    *it *= 2;  // 可以修改元素
}

// 清空所有元素
vec1.clear();

// 判断是否为空
bool is_empty = vec1.empty();
```

## 6.5 映射（Map）

用于表示键值对映射集合，通过引用计数管理。它基于哈希表实现，故键值对的顺序并不保证。

- **持有者类型**：`taihe::map<K, V>`
- **视图类型**：`taihe::map_view<K, V>`

### 6.5.1 创建和插入

```cpp
#include <taihe/map.hpp>

// 创建空map
taihe::map<taihe::string, int> map1;

map1.reserve(10);  // 支持预分配空间，避免频繁重新分配

size_t capacity = map1.capacity();  // 获取当前容量
```

### 6.5.2 插入、查找和删除

```cpp
// 插入键值对
auto [it1, success1] = map1.emplace("apple", 5);
auto [it2, success2] = map1.emplace("banana", 3);

// 如果键已存在，emplace不会覆盖
auto [it3, success3] = map1.emplace("apple", 10);  // success3为false

// 使用emplace<true> 强制覆盖
auto [it4, success4] = map1.emplace<true>("apple", 10);  // 覆盖原值

// 查找键值对
auto it = map1.find_item("banana");
if (it != map1.end()) {
    std::cout << it->first << ": " << it->second << std::endl;
}

// 删除键值对
bool erased = map1.erase("apple");
```

**_⚠️ 特别注意：当前请不要使用`map`对象的`find`方法，当前该方法的返回值类型为`V*`而不是迭代器。这将在未来的版本中被修正，届时将导致之前使用`find`处产生不兼容，请使用`find_item`方法代替。_**

### 6.5.3 获取大小、遍历和清空

```cpp
// 获取大小
size_t size = map1.size();

// 遍历map
for (const auto& [key, value] : map1) {
    std::cout << key << " => " << value << std::endl;
}

// 清空所有元素
map1.clear();

// 判断是否为空
bool is_empty = map1.empty();
```

## 6.6 集合（Set）

用于表示不重复元素的集合，通过引用计数管理。和映射类似，集合基于哈希表实现，元素的顺序并不保证。

- **持有者类型**：`taihe::set<T>`
- **视图类型**：`taihe::set_view<T>`

### 6.6.1 创建和插入

```cpp
#include <taihe/set.hpp>

// 创建空set
taihe::set<int> set1;

set1.reserve(10);  // 预分配空间，避免频繁重新分配

size_t capacity = set1.capacity();  // 获取当前容量
```

### 6.6.2 插入、查找和删除

```cpp
// 插入元素
auto [it1, success1] = set1.emplace(42);
auto [it2, success2] = set1.emplace(100);
auto [it3, success3] = set1.emplace(42);  // 重复插入，success3为false

// 查找元素
auto it = set1.find_item(42);
if (it != set1.end()) {
    std::cout << "Found: " << *it << std::endl;
}

// 删除元素
bool erased = set1.erase(42);
```

**_⚠️ 特别注意：当前请不要使用`set`对象的`find`方法，当前该方法的返回值类型为`bool`而不是迭代器。这将在未来的版本中被修正，届时将导致之前使用`find`处产生不兼容，请使用`find_item`方法代替。_**

### 6.6.3 获取大小、遍历和清空

```cpp
// 获取大小
size_t size = set1.size();

// 范围for循环
for (const auto& value : set1) {
    std::cout << value << " ";
}

// 清空所有元素
set1.clear();

// 判断是否为空
bool is_empty = set1.empty();
```

## 6.7 函数闭包（Callback）

用于存储可调用对象。

- **持有者类型**：`taihe::callback<R(Args...)>`
- **视图类型**：`taihe::callback_view<R(Args...)>`

### 6.7.1 创建回调

回调的创建方式和[接口](#51-接口的实现)非常类似，使用`taihe::make_holder`创建一个持有回调的对象。以下是一个示例，假设我们需要创建一个回调来处理字符串输入并返回处理结果：

```cpp
#include <taihe/callback.hpp>

struct MyProcessor {
    taihe::string prefix;

    MyProcessor(taihe::string_view p) : prefix(p) {}

    taihe::string operator()(taihe::string_view input) {
        return prefix + ": " + input;
    }
};

taihe::callback<taihe::string(taihe::string_view)> callback = \
    taihe::make_holder<
        MyProcessor,
        taihe::callback<taihe::string(taihe::string_view)>
    >("Result");
```

> **💡 注意：**
>
> `taihe::callback`的参数和返回值类型都必须是Taihe支持的C++投影类型，例如参数类型可以是`taihe::string_view`, `taihe::vector_view<T>`, `int32_t`等，返回值类型可以是`taihe::string`, `float`等等，但不能是其他C++的原生类型（如`std::string`、`std::vector`）。这是因为Taihe的回调中需要储存ABI稳定的函数指针，而C++的原生类型作为函数参数或返回值时，调用约定（Calling convention）不能被保证，因此无法在不同编译器或不同版本的编译器之间保持ABI兼容。

### 6.7.2 调用回调

回调可以像普通函数一样调用，可使用`operator()`或直接调用：

```cpp
// 直接调用
taihe::string result = callback("Hello");
```

### 6.7.3 进阶：函数闭包和接口的关系

事实上，Taihe函数闭包和Taihe接口的底层结构和实现原理几乎是相同的，它们的ABI结构都是一个数据指针外加一个虚函数指针/虚表指针。你甚至可以认为函数闭包实际上只是一种特殊的接口类型。它具备大多数接口的特性，例如，你可以将一个C++类同时实现为一个接口和一个函数闭包：

```cpp
class CallableImpl {
public:
    // 实现函数调用运算符
    taihe::string operator()(taihe::string_view input);

    // 实现接口方法
    taihe::string getId() const;
    double calculateArea() const;

    // 其他方法
    void myOtherMethod();
};

auto callableImpl =
    taihe::make_holder<
        CallableImpl,
        taihe::callback<taihe::string(taihe::string_view)>,
        taihe::weak::IShape
    >("CallableImpl");

callableImpl->getId();  // 调用接口方法
callableImpl->calculateArea();  // 调用接口方法

callableImpl->myOtherMethod();  // 调用其他方法，这也是合法的，因为callableImpl的实际类型为
                            // taihe::impl_holder<
                            //     CallableImpl,
                            //     taihe::callback<taihe::string(taihe::string_view)>,
                            //     taihe::weak::IShape
                            // >

callableImpl("Hello");  // 当作函数闭包调用，taihe::impl_holder重载了operator()方法

taihe::callback<taihe::string(taihe::string_view)> cb = callableImpl;  // 转换为函数闭包
taihe::weak::IShape shape = callableImpl;  // 转换为接口
```

并且你可以尝试将函数闭包动态转换为接口：

```cpp
auto cb_as_shape = taihe::weak::IShape(cb);  // 尝试将函数闭包转换为接口
assert(not cb_as_shape.is_error());
```

但是，由于函数闭包类型不具备IID，因此你并不能反过来从其他接口转换为函数闭包。

```cpp
auto shape_as_cb = taihe::callback_view<taihe::string(taihe::string_view)>(cb_as_shape);  // 错误：无法从接口转换为函数闭包
```

## 6.8 内存管理最佳实践

- **参数传递**：始终使用视图类型（如`taihe::string_view`、`taihe::vector_view`）作为函数参数，避免不必要的引用计数操作。
- **返回值**：返回持有者类型（如`taihe::string`、`taihe::vector`）以确保正确的生命周期管理。
- **存储**：在类成员中存储持有者类型以保持数据的所有权。

以`taihe::string`和`taihe::string_view`为例，以下是一个类的示例，展示了如何使用持有者类型和视图类型：

```cpp
class MyClass {
    taihe::string name_;  // 持有者类型作为成员

public:
    // 视图类型作为参数
    void set_name(taihe::string_view name) {
        name_ = name;
    }

    // 返回持有者类型
    taihe::string get_name() const {
        return name_;
    }
};
```

# 7. 使用全局函数

## 7.1 导出函数（接口发布方）

如果你是接口的作者（发布方），需要将函数导出以供用户调用。可以使用`package.name.impl.hpp`中定义的宏`TH_EXPORT_CPP_API_funcName(func)`来导出函数，其中`func`是你实现的函数名。

例如，假设你在IDL文件中定义了一个函数`divmod_i32`：

```rust
struct DivModResult {
    quo: i32;
    rem: i32;
}
function divmod_i32(a: i32, b: i32): DivModResult;
```

你可以在C++实现文件中这样导出该函数：

```cpp
#include <integer.arithmetic.proj.hpp>
#include <integer.arithmetic.impl.hpp>

integer::arithmetic::DivModResult ohos_int_divmod(int32_t a, int32_t b) {
    return { a / b, a % b };
}

TH_EXPORT_CPP_API_divmod_i32(ohos_int_divmod)
```

## 7.2 调用函数（接口消费方）

接口的使用方可以导入头文件`package.name.user.hpp`，并根据IDL文件中定义的函数名称和其所在的命名空间来调用函数。如`package::name::funcName()`。例如，假设你要调用上文中定义的`divmod_i32`函数，可以这样写：

```cpp
#include <integer.arithmetic.user.hpp>

#include <iostream>

int main() {
    int32_t a = 10;
    int32_t b = 3;

    integer::arithmetic::DivModResult result = integer::arithmetic::divmod_i32(a, b);

    std::cout << "Quotient = " << result.quo << std::endl;
    std::cout << "Remainder = " << result.rem << std::endl;

    return 0;
}
```

# 8. 异常和错误

在使用Taihe生成Napi桥接代码时，在生成的C++ 函数中，返回值类型为`taihe::expected<T, E>`，其中`T`为用户在IDL中定义的返回值类型，E默认为`taihe::error`类型，注意，此处提到的`taihe::expected<T, E>`和`taihe::error`不同于其他类型，是专用于异常处理的类型，无法在IDL中表示。

## 8.1 Error类

### 8.1.1 构造Error对象

```cpp
// 只包含错误信息
taihe::error err1("File not found");

// 包含错误信息和错误码
taihe::error err2("Permission denied", 13);

// 复制构造
taihe::error err3 = err1;

// 移动构造
taihe::error err4 = std::move(err2);
```

### 8.1.2 访问Error信息

```cpp
taihe::error err("Network timeout", 110);

// 获取错误信息
taihe::string msg = err.message();

// 检查是否有错误码
bool hasCode = err.has_code();  // 返回true

// 获取错误码
int32_t code = err.code();  // 返回110

// 获取错误码或默认值
int32_t codeOrDefault = err.code_or(-1);  // 有错误码时返回110，否则返回 -1
```

### 8.1.3比较Error对象

```cpp
taihe::error err1("Error 1", 1);
taihe::error err2("Error 2", 2);
taihe::error err3("Error 1", 1);

bool equal1 = (err1 == err2);  // false
bool equal2 = (err1 == err3);  // true
```

## 8.2 Expected类

### 8.2.1 构造Expected对象
```cpp
// 包含成功值
taihe::expected<int, taihe::error> success1 = 42;
taihe::expected<std::string, taihe::error> success2 = "Hello World";

// 使用std::in_place就地构造
taihe::expected<std::vector<int>, taihe::error> success3(std::in_place, {1, 2, 3, 4, 5});

// T = void且成功情况下，使用expected<void, E>
taihe::expected<void, taihe::error> success4 = {};

// 使用unexpected封装错误
taihe::expected<int, taihe::error> failure1 = taihe::unexpected(taihe::error("Failed"));
taihe::expected<void, taihe::error> failure2 = taihe::unexpected(taihe::error("Failed"));

// 直接使用错误信息或错误码构造
taihe::expected<int, taihe::error> failure3(taihe::unexpect, "Failed", 1);
taihe::expected<void, taihe::error> failure4(taihe::unexpect, "Failed", 1);

// 使用unexpected对象
taihe::unexpected<taihe::error> unex(taihe::error("Error", 100));
taihe::expected<int, taihe::error> failure5 = unex;
taihe::expected<void, taihe::error> failure6 = unex;
```

### 8.2.2 检查Expected状态
```cpp
taihe::expected<int, taihe::error> result = some_function();

// 检查是否包含值
if (result.has_value()) {
    // 处理成功情况
}

// 转换为bool（与has_value() 相同）
if (result) {
    // 处理成功情况
}
```

### 8.2.3 访问Expected中的值

```cpp
// 安全访问
taihe::expected<int, taihe::error> result = some_function();

// 访问值（如果不包含值会抛出bad_expected_access异常）
try {
    int value = result.value();
    // 使用value
} catch (taihe::bad_expected_access& e) {
    std::cerr << "Error: " << e.what() << std::endl;
}

// 访问错误（如果包含值会抛出异常）
try {
    taihe::error err = result.error();
} catch (taihe::bad_expected_access& e) {
    std::cerr << "Has value: " << e.what() << std::endl;
}

// 获取指针访问
taihe::expected<Data, taihe::error> result = load_data();

if (result.has_value()) {
    // 获取值的引用
    Data& data = result.value();
    
    // 获取值的指针
    Data* data_ptr = &result.value();
}

// 修改Expected对象
taihe::expected<int, taihe::error> result = 42;

// 重新赋值（成功值）
result = 100;

// 重新赋值（错误值）
result = taihe::unexpected(taihe::error("New error"));

// 移动赋值
taihe::expected<int, taihe::error> other = 200;
result = std::move(other);
```

# 附录

## A. 常见的编译/链接错误

- 链接错误：`` undefined reference to `package_name_InterfaceName_funcName_f' ``

  这类错误通常是因为在IDL文件中定义的函数没有被正确导出。请确保在实现文件中使用了`TH_EXPORT_CPP_API_funcName(func)`宏来导出函数。

- 链接错误：`` undefined reference to `package_name_InterfaceName_i' ``

  类似`package_name_InterfaceName_i`这样的是Taihe接口的ID符号，其定义通常在自动生成的`package.name.abi.c`中，请确保你在构建时将该文件包含在内。

- 编译错误：

  ```
  error: no member named 'methodName' in 'ClassName'
   xx |         return ::taihe::into_abi<...>(::taihe::cast_data_ptr<Impl>(tobj.data_ptr)->methodName(...));
      |                                       ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  ^
  ```

  这意味着在你的C++类`ClassName`中没有实现IDL文件中定义的`methodName`方法。请检查你的类实现，确保所有所需的接口方法都已正确实现，并注意方法名的大小写和参数类型是否与IDL文件中的定义一致。

- 编译错误：

  ```
  error: no matching function for call to 'into_abi'
   xx |         return ::taihe::into_abi<...>(::taihe::cast_data_ptr<Impl>(tobj.data_ptr)->methodName(...));
      |                ^~~~~~~~~~~~~~~~~~~~~~
  ```

  `methodName`方法的C++实现中的返回类型和在Taihe IDL文件中声明的返回值类型所对应的C++投影类型不匹配。

  ```
  error: no viable conversion from 'const ::my::package::MyStruct' to 'const std::string'
   xx |         return ::taihe::cast_data_ptr<Impl>(tobj.data_ptr)->methodName(::taihe::from_abi<::my::package::MyStruct const&>(c));
      |                                                                      ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ```

  `methodName`方法的C++实现中的参数类型和在Taihe IDL文件中声明的参数类型所对应的C++投影类型不匹配。

- 编译错误：`error: no member named 'methodName' in 'package::name::weak::InterfaceName::virtual_type'`

  这可能说明你没有在IDL的接口`InterfaceName`中声明`methodName`方法，详见[5.5](#55-进阶taiheimpl_holder和taiheimpl_view)。另外，请注意，当要在子接口对象上调用父接口的方法时，必须先将子接口转换为父接口类型，详见[5.3](#53-接口方法的调用)。

- 编译错误：`error: implicit instantiation of undefined template 'taihe::as_abi<...>'`

  见[6.7.1](#671-创建回调)，这种错误通常是因为你在函数闭包的参数或返回值中使用了Taihe不支持的C++类型。请确保你使用的类型都是Taihe支持的C++投影类型。

---

以上是使用IDL文件生成代码的主要方法和注意事项。如需更多帮助，请参考具体模块的文档或示例代码。
