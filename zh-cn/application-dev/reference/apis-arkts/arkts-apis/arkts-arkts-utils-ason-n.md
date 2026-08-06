# ASON

为支持将JSON字符串解析为共享数据，即Sendable支持的数据类型，ArkTS语言基础库新增了ASON工具。ASON工具支持解析JSON字符串并生成共享数据，用于跨并发实例引用传递，同时也支持将共享数据转换为JSON字符串。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-utils-namespace ASON--><!--Device-utils-namespace ASON-End-->

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [parse](arkts-arkts-ason-parse-f.md#parse) | 用于解析JSON字符串生成ISendable数据或null。 |
| [stringify](arkts-arkts-ason-stringify-f.md#stringify) | 该方法将ArkTS对象数据转换为JSON字符串，额外支持Map和Set相关类型。 从API 18开始参数修改为Object类型，API 18之前参数只支持ISendable类型 （除Int8Array、Uint8Array、Int16Array、Uint16Array、Int32Array、Uint32Array、Uint8ClampedArray、Float32Array外）。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ParseOptions](arkts-arkts-ason-parseoptions-i.md) | 解析的选项，可定义处理BigInt的模式和解析结果的返回类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BigIntMode](arkts-arkts-ason-bigintmode-e.md) | 定义处理BigInt的模式。 |
| [ParseReturnType](arkts-arkts-ason-parsereturntype-e.md) | 定义解析结果的返回类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ISendable](arkts-arkts-ason-isendable-t.md) | ISendable是所有Sendable类型（除null和undefined）的父类型。自身没有任何必要的方法和属性。 |
| [Transformer](arkts-arkts-ason-transformer-t.md) | 用于转换结果函数的类型。 |

