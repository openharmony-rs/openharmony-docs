# 方舟字节码文件格式 (ArkTS-Sta)

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao; @Graceunderpressure-->
<!--Designer: @oatuwwutao-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @HelloCrease-->

本文介绍字节码文件的二进制布局与各结构字段含义，帮助开发者分析、校验与修改 `*.abc` 编译产物。

字节码文件由ArkTS-Sta编译工具链生成，采用Panda二进制容器，并在类型元数据、索引区域等方面针对静态类型场景做了扩展。

本文内容基于版本号 **0.1.0.7**（版本号为方舟编译器内部保留字段，开发者无需关注，仅供准确对照之用）。最低兼容版本为 **0.0.0.6**。

文件头 `version[1]` 为 `1` 时表示当前文档适用的编码（版本形如 `0.1.x.y`）。遗留版本 `0.0.0.6` 的次版本号亦为 `0`，识别时须结合工具链版本与文件结构综合判断。

## 字节码文件数据类型

方舟字节码使用了多种基础和复合数据类型，以下为常见类型的定义和说明。

### 整型

  | **名称** | **说明** |
  | -------- | -------- |
  | `uint8_t` | 8-bit 无符号整数。 |
  | `uint16_t` | 16-bit 无符号整数，采用小端字节序。 |
  | `uint32_t` | 32-bit 无符号整数，采用小端字节序。 |
  | `uleb128` | leb128 编码的无符号整数。 |
  | `sleb128` | leb128 编码的有符号整数。 |

### 字符串

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `utf16_length` | `uleb128` | 值为 `len << 1 \| is_ascii`，其中 `len` 是字符串在 UTF-16 编码中的大小，`is_ascii` 标记该字符串是否仅包含 ASCII 字符。 |
  | `data` | `uint8_t[]` | 以 `'\0'` 结尾的 MUTF-8 编码字符序列。 |

### TaggedValue

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `tag` | `uint8_t` | 表示数据种类的标记。 |
  | `data` | `uint8_t[]` | 根据不同的标记，`data` 是不同类型的数据或者为空。 |

## TypeDescriptor

`TypeDescriptor` 是类（[Class](#class)）名称的格式，语法如下：

```text
TypeDescriptor -> PrimitiveType | ArrayType | RefType
PrimitiveType -> 'Z' | 'B' | 'H' | 'S' | 'C' | 'I' | 'U' | 'J' | 'Q' | 'F' | 'D' | 'A'
ArrayType -> '[' TypeDescriptor
RefType -> 'L' ClassName ';'
```

其中 `ClassName` 是类的全名，名称中的 `'.'` 会被替换为 `'/'`。

基本类型编码如下：

  | **类型** | **编码** |
  | -------- | -------- |
  | `u1` | `Z` |
  | `i8` | `B` |
  | `u8` | `H` |
  | `i16` | `S` |
  | `u16` | `C` |
  | `i32` | `I` |
  | `u32` | `U` |
  | `f32` | `F` |
  | `f64` | `D` |
  | `i64` | `J` |
  | `u64` | `Q` |
  | `any` | `A` |

## 字节码文件布局

字节码文件起始于 [Header](#header) 结构。文件中的所有结构均可以从 `Header` 出发，直接或间接地访问到。字节码文件中结构的引用方式包括偏移量和索引。偏移量是一个 32 位长度的值，表示当前结构的起始位置在字节码文件中相对于文件头的字节偏移量，从 0 开始计算。索引是一个 16 位长度的值，表示当前结构在索引区域中的位置，此机制将在 [IndexSection](#indexsection) 章节描述。

字节码文件中所有多字节数值类型（如 `u16`、`u32` 和 `i32` 等）均采用小端字节序（Little-endian）存储。

除非另有说明，所有偏移量均从文件起始位置（偏移 0）开始计算。偏移量通常不得落在 `[0, 32)` 范围内（文件头占用该区间）。

### Header

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `magic` | `uint8_t[8]` | 文件头魔数，值必须是 `'P' 'A' 'N' 'D' 'A' '\0' '\0' '\0'`。 |
  | `checksum` | `uint32_t` | 字节码文件除文件头魔数和本校验字段之外的内容的 adler32 校验和。 |
  | `version` | `uint8_t[4]` | 字节码文件的版本号（[Version](#version)）。 |
  | `file_size` | `uint32_t` | 字节码文件的大小，以字节为单位。 |
  | `foreign_off` | `uint32_t` | 偏移量，指向外部区域。外部区域中仅包含类型为 [ForeignClass](#foreignclass)、[ForeignMethod](#foreignmethod) 或 [ForeignField](#foreignfield) 的元素。 |
  | `foreign_size` | `uint32_t` | 外部区域的大小，以字节为单位。 |
  | `quickened_flag` | `uint32_t` | 快速化标记。非零表示文件已经过快速化处理，运行时不再接受二次快速化。 |
  | `num_classes` | `uint32_t` | [ClassIndex](#classindex) 结构中元素的数量，即文件中定义的 [Class](#class) 的数量。 |
  | `class_idx_off` | `uint32_t` | 偏移量，指向 [ClassIndex](#classindex)。 |
  | `num_export_table` | `uint32_t` | 导出表中的类数量，可为 0。 |
  | `export_table_off` | `uint32_t` | 偏移量，指向导出类索引结构（[ClassIndex](#classindex) 格式）。 |
  | `num_lnps` | `uint32_t` | [LineNumberProgramIndex](#linenumberprogramindex) 结构中元素的数量。 |
  | `lnp_idx_off` | `uint32_t` | 偏移量，指向 [LineNumberProgramIndex](#linenumberprogramindex)。 |
  | `num_literalarrays` | `uint32_t` | [LiteralArrayIndex](#literalarrayindex) 结构中元素的数量。 |
  | `literalarray_idx_off` | `uint32_t` | 偏移量，指向 [LiteralArrayIndex](#literalarrayindex)。 |
  | `num_index_regions` | `uint32_t` | [IndexSection](#indexsection) 结构中元素的数量，即文件中 [RegionHeader](#regionheader) 的数量。 |
  | `index_section_off` | `uint32_t` | 偏移量，指向 [IndexSection](#indexsection)。 |

> **说明：**
>
> - 文件头含 `quickened_flag` 快速化标记，非零表示文件已经过快速化处理。
> - 文件头含 `export_table` 导出表与 `literalarray_idx` 字面量数组索引，用于模块导出与字面量数组的快速定位。
> - [RegionHeader](#regionheader) 将类、方法、字段与原型（Proto）索引拆分为独立区域管理。

### Version

字节码版本号由 4 个部分组成，格式为：`主版本号.次版本号.特性版本号.编译版本号`。

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | 主版本号 | `uint8_t` | 标识整体架构调整引入的字节码文件格式变更。 |
  | 次版本号 | `uint8_t` | 标识字节码编码类型：`1` 表示当前文档适用的 ArkTS-Sta 编码；遗留版本 `0.0.0.6` 的次版本号为 `0`。 |
  | 特性版本号 | `uint8_t` | 标识中小特性引入的字节码文件格式变更。 |
  | 编译版本号 | `uint8_t` | 标识缺陷修复引入的字节码文件格式变更。 |

### ForeignClass

描述字节码文件中的外部类。外部类在其他文件中声明，并在当前字节码文件中被引用。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `name` | `String` | 外部类的名称，命名遵循 [TypeDescriptor](#typedescriptor) 语法。 |

### ForeignField

描述字节码文件中的外部字段。外部字段在其他文件中声明，并在当前字节码文件中被引用。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `class_idx` | `uint16_t` | 指向该字段所从属类的索引，位于 [ClassRegionIndex](#classregionindex) 中。 |
  | `type_idx` | `uint16_t` | 指向字段类型的索引，位于 [ClassRegionIndex](#classregionindex) 中，值为 [FieldType](#fieldtype) 类型。 |
  | `name_off` | `uint32_t` | 偏移量，指向 [字符串](#字符串)，表示字段名称。 |
  | `access_flags` | `uleb128` | 字段的访问标志（[FieldAccessFlag](#fieldaccessflag) 的组合）。对于外部字段，仅 `ACC_STATIC` 有效。 |

### ForeignMethod

描述字节码文件中的外部方法。外部方法在其他文件中声明，并在当前字节码文件中被引用。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `class_idx` | `uint16_t` | 指向该方法所从属类的索引，位于 [ClassRegionIndex](#classregionindex) 中。 |
  | `proto_idx` | `uint16_t` | 指向方法原型的索引，位于 [ProtoRegionIndex](#protoregionindex) 中。 |
  | `name_off` | `uint32_t` | 偏移量，指向 [字符串](#字符串)，表示方法名称。 |
  | `access_flags` | `uleb128` | 方法的访问标志（[MethodAccessFlag](#methodaccessflag) 的组合）。对于外部方法，仅 `ACC_STATIC` 有效。 |

> **说明：**
>
> 通过 ForeignField 或 ForeignMethod 的偏移量，可以找到偏移量所在的 RegionHeader 以解析 `class_idx`、`type_idx` 和 `proto_idx`。

### ClassIndex

`ClassIndex` 结构能通过名称快速定位到 Class 的定义。

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `offsets` | `uint32_t[]` | 数组中每个元素的值是一个指向 [Class](#class) 或 [ForeignClass](#foreignclass) 的偏移量。数组中的元素根据类的名称进行排序，名称遵循 [TypeDescriptor](#typedescriptor) 语法。数组长度由 [Header](#header) 中的 `num_classes` 指定。 |

### Class

在字节码文件中，一个类可以表示一个源代码文件、一个类型定义或一种内置的 [Annotation](#annotation)。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `name` | `String` | Class 的名称，命名遵循 [TypeDescriptor](#typedescriptor) 语法。 |
  | `super_class_off` | `uint32_t` | 偏移量，指向父类（[Class](#class) 或 [ForeignClass](#foreignclass)）。根类（如 `panda.Object`）取值为 `0`。 |
  | `access_flags` | `uleb128` | Class 的访问标志（[ClassAccessFlag](#classaccessflag) 的组合）。 |
  | `num_fields` | `uleb128` | Class 的字段的数量。 |
  | `num_methods` | `uleb128` | Class 的方法的数量。 |
  | `class_data` | `TaggedValue[]` | 不定长度的数组，数组中每个元素都是 [TaggedValue](#taggedvalue) 类型，元素的标记是 [ClassTag](#classtag) 类型，数组中的元素按照标记递增排序（`0x00` 标记除外）。 |
  | `fields` | `Field[]` | Class 的字段的数组，数组长度由 `num_fields` 指定。 |
  | `methods` | `Method[]` | Class 的方法的数组，数组长度由 `num_methods` 指定。 |

### ClassAccessFlag

  | **名称** | **值** | **说明** |
  | -------- | ------ | -------- |
  | `ACC_PUBLIC` | `0x0001` | 声明为 public。 |
  | `ACC_FINAL` | `0x0010` | 声明为 final，不允许子类化。 |
  | `ACC_SUPER` | `0x0020` | 保留标志，用于兼容性。 |
  | `ACC_INTERFACE` | `0x0200` | 声明为接口。 |
  | `ACC_ABSTRACT` | `0x0400` | 声明为 abstract。 |
  | `ACC_SYNTHETIC` | `0x1000` | 编译器合成的类，源代码中不存在。 |
  | `ACC_ANNOTATION` | `0x2000` | 声明为注解类型。 |
  | `ACC_ENUM` | `0x4000` | 声明为枚举类型。 |

### ClassTag

  | **名称** | **值** | **数量** | **格式** | **说明** |
  | -------- | ---- | -------- | -------- | -------- |
  | `NOTHING` | `0x00` | `1` | `none` | 拥有此标记的 [TaggedValue](#taggedvalue)，是其所在 `class_data` 的最后一项。 |
  | `INTERFACES` | `0x01` | `0-1` | `uleb128 uint16_t[]` | 实现的接口列表。`data` 以 `uleb128` 编码接口数量，后接对应数量的 `uint16_t` 索引。 |
  | `SOURCE_LANG` | `0x02` | `0-1` | `uint8_t` | 源码语言标识。`0x01` 表示 Panda Assembly。 |
  | `RUNTIME_ANNOTATION` | `0x03` | `>=0` | `uint32_t` | 运行时可见注解的偏移量。 |
  | `ANNOTATION` | `0x04` | `>=0` | `uint32_t` | 运行时不可见注解的偏移量。 |
  | `RUNTIME_TYPE_ANNOTATION` | `0x05` | `>=0` | `uint32_t` | 运行时可见类型注解的偏移量。 |
  | `TYPE_ANNOTATION` | `0x06` | `>=0` | `uint32_t` | 运行时不可见类型注解的偏移量。 |
  | `SOURCE_FILE` | `0x07` | `0-1` | `uint32_t` | 源文件名称字符串的偏移量。 |

### Field

描述字节码文件中的字段。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `class_idx` | `uint16_t` | 指向该字段从属类的索引，位于 [ClassRegionIndex](#classregionindex) 中。 |
  | `type_idx` | `uint16_t` | 指向字段类型的索引，位于 [ClassRegionIndex](#classregionindex) 中，值为 [FieldType](#fieldtype) 类型。 |
  | `name_off` | `uint32_t` | 偏移量，指向 [字符串](#字符串)，表示字段的名称。 |
  | `access_flags` | `uleb128` | 字段的访问标志（[FieldAccessFlag](#fieldaccessflag) 的组合）。 |
  | `field_data` | `TaggedValue[]` | 不定长度的数组，元素的标记是 [FieldTag](#fieldtag) 类型，按标记递增排序（`0x00` 除外）。 |

### FieldAccessFlag

  | **名称** | **值** | **说明** |
  | -------- | ------ | -------- |
  | `ACC_PUBLIC` | `0x0001` | 声明为 public。 |
  | `ACC_PRIVATE` | `0x0002` | 声明为 private。 |
  | `ACC_PROTECTED` | `0x0004` | 声明为 protected。 |
  | `ACC_STATIC` | `0x0008` | 声明为 static。 |
  | `ACC_FINAL` | `0x0010` | 声明为 final。 |
  | `ACC_READONLY` | `0x0020` | 声明为 readonly，对象构造期间仅赋值一次。 |
  | `ACC_VOLATILE` | `0x0040` | 声明为 volatile。 |
  | `ACC_TRANSIENT` | `0x0080` | 声明为 transient。 |
  | `ACC_SYNTHETIC` | `0x1000` | 编译器合成的字段。 |
  | `ACC_ENUM` | `0x4000` | 声明为枚举元素。 |

### FieldTag

  | **名称** | **值** | **数量** | **格式** | **说明** |
  | -------- | ---- | -------- | -------- | -------- |
  | `NOTHING` | `0x00` | `1` | `none` | `field_data` 的最后一项。 |
  | `INT_VALUE` | `0x01` | `0-1` | `sleb128` | 整型常量值，适用于 `boolean`、`byte`、`char`、`short` 或 `int` 类型字段。 |
  | `VALUE` | `0x02` | `0-1` | `uint32_t` | [Value formats](#value-formats) 中的 `FLOAT` 或 `ID` 类型值。 |
  | `RUNTIME_ANNOTATIONS` | `0x03` | `>=0` | `uint32_t` | 运行时可见字段注解的偏移量。 |
  | `ANNOTATIONS` | `0x04` | `>=0` | `uint32_t` | 运行时不可见字段注解的偏移量。 |
  | `RUNTIME_TYPE_ANNOTATION` | `0x05` | `>=0` | `uint32_t` | 运行时可见类型注解的偏移量。 |
  | `TYPE_ANNOTATION` | `0x06` | `>=0` | `uint32_t` | 运行时不可见类型注解的偏移量。 |

### FieldType

`FieldType` 是一个 32 位值，表示基本类型编码或指向 [Class](#class) / [ForeignClass](#foreignclass) 的偏移量。由于文件头长度大于 16 字节，偏移量落在 `[0, sizeof(Header))` 范围内的值被用于编码基本类型（低 4 位）：

  | **类型** | **编码** |
  | -------- | -------- |
  | `u1` | `0x00` |
  | `i8` | `0x01` |
  | `u8` | `0x02` |
  | `i16` | `0x03` |
  | `u16` | `0x04` |
  | `i32` | `0x05` |
  | `u32` | `0x06` |
  | `f32` | `0x07` |
  | `f64` | `0x08` |
  | `i64` | `0x09` |
  | `u64` | `0x0a` |
  | `any` | `0x0b` |

### Method

描述字节码文件中的方法。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `class_idx` | `uint16_t` | 指向该方法所从属类的索引，位于 [ClassRegionIndex](#classregionindex) 中。 |
  | `proto_idx` | `uint16_t` | 指向方法原型的索引，位于 [ProtoRegionIndex](#protoregionindex) 中。 |
  | `name_off` | `uint32_t` | 偏移量，指向 [字符串](#字符串)，表示方法名称。 |
  | `access_flags` | `uleb128` | 方法的访问标志（[MethodAccessFlag](#methodaccessflag) 的组合）。 |
  | `method_data` | `TaggedValue[]` | 不定长度的数组，元素的标记是 [MethodTag](#methodtag) 类型，按标记递增排序（`0x00` 除外）。 |

> **说明：**
>
> 方法通过 `proto_idx` 引用 [Proto](#proto) 结构描述方法签名。方法体引用的类型、字段、方法等常量池条目，由指令编码中的各类 `id` 操作数（`type_id`、`method_id`、`field_id` 等）结合所在区域的索引表解析。

### MethodAccessFlag

  | **名称** | **值** | **说明** |
  | -------- | ------ | -------- |
  | `ACC_PUBLIC` | `0x0001` | 声明为 public。 |
  | `ACC_PRIVATE` | `0x0002` | 声明为 private。 |
  | `ACC_PROTECTED` | `0x0004` | 声明为 protected。 |
  | `ACC_STATIC` | `0x0008` | 声明为 static。 |
  | `ACC_FINAL` | `0x0010` | 声明为 final。 |
  | `ACC_SYNCHRONIZED` | `0x0020` | 声明为 synchronized。 |
  | `ACC_BRIDGE` | `0x0040` | 桥接方法，由编译器生成。 |
  | `ACC_VARARGS` | `0x0080` | 声明为可变参数方法。 |
  | `ACC_NATIVE` | `0x0100` | 声明为 native 方法。 |
  | `ACC_ABSTRACT` | `0x0400` | 声明为 abstract。 |
  | `ACC_STRICT` | `0x0800` | 声明为 strictfp。 |
  | `ACC_SYNTHETIC` | `0x1000` | 编译器合成的方法。 |

### MethodTag

  | **名称** | **值** | **数量** | **格式** | **说明** |
  | -------- | ---- | -------- | -------- | -------- |
  | `NOTHING` | `0x00` | `1` | `none` | `method_data` 的最后一项。 |
  | `CODE` | `0x01` | `0-1` | `uint32_t` | 指向 [Code](#code) 的偏移量，表示方法的代码段。 |
  | `SOURCE_LANG` | `0x02` | `0-1` | `uint8_t` | 源码语言标识。 |
  | `RUNTIME_ANNOTATION` | `0x03` | `>=0` | `uint32_t` | 运行时可见方法注解的偏移量。 |
  | `RUNTIME_PARAM_ANNOTATION` | `0x04` | `0-1` | `uint32_t` | 运行时可见参数注解的偏移量，指向 [ParamAnnotations](#paramannotations)。 |
  | `DEBUG_INFO` | `0x05` | `0-1` | `uint32_t` | 指向 [DebugInfo](#debuginfo) 的偏移量。 |
  | `ANNOTATION` | `0x06` | `>=0` | `uint32_t` | 运行时不可见方法注解的偏移量。 |
  | `PARAM_ANNOTATION` | `0x07` | `0-1` | `uint32_t` | 运行时不可见参数注解的偏移量。 |
  | `TYPE_ANNOTATION` | `0x08` | `>=0` | `uint32_t` | 运行时不可见类型注解的偏移量。 |
  | `RUNTIME_TYPE_ANNOTATION` | `0x09` | `>=0` | `uint32_t` | 运行时可见类型注解的偏移量。 |
  | `PROFILE_INFO` | `0x0a` | `>=0` | `uint8_t[]` | 性能剖析信息，格式由语言插件定义。 |

### Proto

`Proto` 描述方法的签名（返回值类型与参数类型列表），是静态类型元数据的核心结构。

- 对齐方式：2 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `shorty` | `uint16_t[]` | 方法签名的简短表示，编码规则见 [Shorty](#shorty)。 |
  | `reference_types` | `uint16_t[]` | 签名中所有引用类型（非基本类型）在 [ClassRegionIndex](#classregionindex) 中的索引数组。数组长度等于 `shorty` 中引用类型的数量。 |

### Shorty

`Shorty` 是方法签名的紧凑编码，由返回类型、参数类型列表和结束标记 `0x0` 组成。每 4 个类型元素编码为一个 `uint16_t`，每个类型占 4 位：

  | **类型** | **值** |
  | -------- | ------ |
  | `void` | `0x01` |
  | `u1` | `0x02` |
  | `i8` | `0x03` |
  | `u8` | `0x04` |
  | `i16` | `0x05` |
  | `u16` | `0x06` |
  | `i32` | `0x07` |
  | `u32` | `0x08` |
  | `f32` | `0x09` |
  | `f64` | `0x0a` |
  | `i64` | `0x0b` |
  | `u64` | `0x0c` |
  | `ref` | `0x0d` |
  | `any` | `0x0e` |

### Code

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `num_vregs` | `uleb128` | 虚拟寄存器的数量，不包括存放参数的寄存器。 |
  | `num_args` | `uleb128` | 方法参数的数量。 |
  | `code_size` | `uleb128` | 所有指令的总大小，以字节为单位。 |
  | `tries_size` | `uleb128` | `try_blocks` 数组的长度。 |
  | `instructions` | `uint8_t[]` | 所有指令的数组。 |
  | `try_blocks` | `TryBlock[]` | Try 块数组。 |

### TryBlock

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `start_pc` | `uleb128` | Try 块的第一条指令距离其所在 [Code](#code) 的 `instructions` 起始位置的偏移量。 |
  | `length` | `uleb128` | Try 块覆盖的指令范围大小，以字节为单位。 |
  | `num_catches` | `uleb128` | 关联的 [CatchBlock](#catchblock) 数量。 |
  | `catch_blocks` | `CatchBlock[]` | Catch 块数组，按运行时检查异常类型的顺序排列；`catch all` 块（若存在）必须位于最后。 |

### CatchBlock

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `type_idx` | `uleb128` | 捕获的异常类型在 [ClassRegionIndex](#classregionindex) 中的索引加 1；值为 `0` 表示捕获所有类型的异常。 |
  | `handler_pc` | `uleb128` | 异常处理逻辑的第一条指令的程序计数器。 |
  | `code_size` | `uleb128` | 此 Catch 块处理逻辑的大小，以字节为单位。 |

> **说明：**
>
> `CatchBlock` 支持按异常类型分派的多路 catch；`type_idx` 为 `0` 时表示捕获所有类型的异常。

### Annotation

描述一个注解结构。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `class_idx` | `uint16_t` | 注解类在 [ClassRegionIndex](#classregionindex) 中的索引。 |
  | `count` | `uint16_t` | `elements` 数组的长度。 |
  | `elements` | `AnnotationElement[]` | 注解元素数组。 |
  | `element_types` | `uint8_t[]` | 与 `elements` 一一对应的元素类型标记数组。 |

### AnnotationElementTag

  | **名称** | **标记** |
  | -------- | -------- |
  | `u1` | `'1'` |
  | `i8` | `'2'` |
  | `u8` | `'3'` |
  | `i16` | `'4'` |
  | `u16` | `'5'` |
  | `i32` | `'6'` |
  | `u32` | `'7'` |
  | `i64` | `'8'` |
  | `u64` | `'9'` |
  | `f32` | `'A'` |
  | `f64` | `'B'` |
  | `string` | `'C'` |
  | `record` | `'D'` |
  | `method` | `'E'` |
  | `enum` | `'F'` |
  | `annotation` | `'G'` |
  | `array` | `'H'` |
  | `method_handle` | `'J'` |
  | `nullptr_string` | `'*'` |

### AnnotationElement

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `name_off` | `uint32_t` | 元素名称字符串的偏移量。 |
  | `value` | `uint32_t` | 元素值。宽度不超过 32 位时内联存储，否则存储指向 [Value formats](#value-formats) 的偏移量。 |

### ParamAnnotations

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `count` | `uint32_t` | 方法参数数量（含合成参数与 mandated 参数）。 |
  | `annotations` | `AnnotationArray[]` | 每个参数对应的注解列表。 |

### Value formats

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `INTEGER` | `uint32_t` | 有符号四字节整数值。 |
  | `LONG` | `uint64_t` | 有符号八字节整数值。 |
  | `FLOAT` | `uint32_t` | 四字节位模式，解译为 IEEE754 32 位浮点值。 |
  | `DOUBLE` | `uint64_t` | 八字节位模式，解译为 IEEE754 64 位浮点值。 |
  | `ID` | `uint32_t` | 四字节位模式，表示文件中某个结构的偏移量。 |

### MethodHandle

描述方法句柄，用于支持 `invokedynamic` 等高级调用场景。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `type` | `uint8_t` | 句柄类型，见下表。 |
  | `offset` | `uleb128` | 指向对应实体的偏移量。 |

  | **名称** | **值** | **说明** |
  | -------- | ------ | -------- |
  | `PUT_STATIC` | `0x00` | 静态字段 setter，偏移指向 [Field](#field) 或 [ForeignField](#foreignfield)。 |
  | `GET_STATIC` | `0x01` | 静态字段 getter。 |
  | `PUT_INSTANCE` | `0x02` | 实例字段 setter。 |
  | `GET_INSTANCE` | `0x03` | 实例字段 getter。 |
  | `INVOKE_STATIC` | `0x04` | 静态方法调用。 |
  | `INVOKE_INSTANCE` | `0x05` | 实例方法调用。 |
  | `INVOKE_CONSTRUCTOR` | `0x06` | 构造函数调用。 |
  | `INVOKE_DIRECT` | `0x07` | 直接方法调用。 |
  | `INVOKE_INTERFACE` | `0x08` | 接口方法调用。 |

### LiteralArray

描述字节码文件中的字面量数组。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `num_literals` | `uint32_t` | `literals` 数组的长度。 |
  | `literals` | `Literal[]` | 字面量数组。 |

### Literal

根据字面量值的字节数，有四种编码格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | 单字节编码 | `uint8_t` | 单字节对齐，存储简单类型字面量（如 `BOOL`）。 |
  | 双字节编码 | `uint16_t` | 2 字节对齐，存储 16 位整型字面量。 |
  | 四字节编码 | `uint32_t` | 4 字节对齐，存储 32 位数值字面量。 |
  | 八字节编码 | `uint64_t` | 8 字节对齐，存储 64 位数值字面量。 |

### LineNumberProgramIndex

行号程序索引的结构是一个数组，便于使用更紧凑的索引访问行号程序。

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `offsets` | `uint32_t[]` | 数组中每个元素的值是一个偏移量，指向一个行号程序。数组长度由 [Header](#header) 中的 `num_lnps` 指定。 |

### LiteralArrayIndex

字面量数组索引，便于通过索引快速定位 [LiteralArray](#literalarray)。

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `offsets` | `uint32_t[]` | 指向 [LiteralArray](#literalarray) 的偏移量数组。数组长度由 [Header](#header) 中的 `num_literalarrays` 指定。 |

### DebugInfo

调试信息包含方法的程序计数器与源代码行列号之间的映射以及局部变量信息。格式由 [DWARF 调试信息格式第 3 版](https://dwarfstd.org/dwarf3std.html)（见第 6.2 项）演变形成，并额外支持 `RESTART_LOCAL`、`SET_PROLOGUE_END`、`SET_EPILOGUE_BEGIN` 等操作码。

- 对齐方式：单字节对齐。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `line_start` | `uleb128` | 状态机行号寄存器的初始值。 |
  | `num_parameters` | `uleb128` | 方法参数的总数量。 |
  | `parameters` | `uleb128[]` | 参数名称偏移量数组，长度为 `num_parameters`；`0` 表示无名称。 |
  | `constant_pool_size` | `uleb128` | 常量池的大小，以字节为单位。 |
  | `constant_pool` | `uleb128[]` | 常量池数据。 |
  | `line_number_program_idx` | `uleb128` | 指向 [LineNumberProgramIndex](#linenumberprogramindex) 中某个行号程序的索引。 |

行号程序的操作码、状态机寄存器及特殊操作码计算规则见各操作码定义，此处不再赘述。

### IndexSection

字节码文件被分割为多个索引区域（Index region），每个索引区域内的结构使用 16 位索引。`IndexSection` 结构描述了索引区域的集合。

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `headers` | `RegionHeader[]` | 数组中每个元素是 [RegionHeader](#regionheader) 类型，按区域起始偏移量排序。数组长度由 [Header](#header) 中的 `num_index_regions` 指定。 |

### RegionHeader

每个 `RegionHeader` 描述一个索引区域，将类、方法、字段和原型索引拆分为四个独立区域。

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `start_off` | `uint32_t` | 该区域的起始偏移量。 |
  | `end_off` | `uint32_t` | 该区域的结束偏移量。 |
  | `class_region_idx_size` | `uint32_t` | [ClassRegionIndex](#classregionindex) 中元素的数量，最大值为 65536。 |
  | `class_region_idx_off` | `uint32_t` | 偏移量，指向 [ClassRegionIndex](#classregionindex)。 |
  | `method_region_idx_size` | `uint32_t` | [MethodRegionIndex](#methodregionindex) 中元素的数量，最大值为 65536。 |
  | `method_region_idx_off` | `uint32_t` | 偏移量，指向 [MethodRegionIndex](#methodregionindex)。 |
  | `field_region_idx_size` | `uint32_t` | [FieldRegionIndex](#fieldregionindex) 中元素的数量，最大值为 65536。 |
  | `field_region_idx_off` | `uint32_t` | 偏移量，指向 [FieldRegionIndex](#fieldregionindex)。 |
  | `proto_region_idx_size` | `uint32_t` | [ProtoRegionIndex](#protoregionindex) 中元素的数量，最大值为 65536。 |
  | `proto_region_idx_off` | `uint32_t` | 偏移量，指向 [ProtoRegionIndex](#protoregionindex)。 |

### ClassRegionIndex

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `types` | `FieldType[]` | [FieldType](#fieldtype) 数组。 |

### MethodRegionIndex

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `offsets` | `uint32_t[]` | 指向 [Method](#method) 或 [ForeignMethod](#foreignmethod) 的偏移量数组。 |

### FieldRegionIndex

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `offsets` | `uint32_t[]` | 指向 [Field](#field) 或 [ForeignField](#foreignfield) 的偏移量数组。 |

### ProtoRegionIndex

- 对齐方式：4 个字节。
- 格式：

  | **名称** | **格式** | **说明** |
  | -------- | -------- | -------- |
  | `offsets` | `uint32_t[]` | 指向 [Proto](#proto) 的偏移量数组。 |

## 外部实体与本地实体

字节码文件中的类、字段和方法分为**外部（Foreign）**和**本地（Local）**两类：

- **外部实体**：在其他文件中声明，在当前文件中被引用。其偏移量落在 `[foreign_off, foreign_off + foreign_size)` 区间内。
- **本地实体**：在当前文件中定义。偏移量落在上述区间之外。

运行时通过检查偏移量是否位于外部区域来判断实体类型，并据此决定是跨文件解析还是直接实例化本地定义。
