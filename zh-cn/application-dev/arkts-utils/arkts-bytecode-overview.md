# 方舟字节码概述

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu; @zmw1-->
<!--Designer: @huyunhui1; @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @HelloCrease-->

方舟字节码是ArkTS/TS/JS源码经编译工具链生成的二进制执行载体，以 `*.abc` 文件形式由方舟运行时在设备侧加载、校验并执行。与仅关注源码层语法不同，字节码层保留了类型、方法、字段及指令序列等编译期决策结果，是连接编译器、运行时与诊断工具的关键接口。

开发者如需分析编译产物、定位运行时问题或开展指令级特性开发，须理解字节码的文件结构与指令语义。本专题介绍方舟字节码的文件格式、指令集与执行模型，并提供编译期改写、反汇编等配套能力说明，适用于反汇编与故障定位、编译产物结构审计、特性开发与测试、编译器输出验证，以及与运行时协同排查语义差异等场景。

按编译模式，方舟字节码分为 [方舟字节码 (ArkTS-Dyn)](arkts-bytecode-fundamentals.md) 与 [方舟字节码 (ArkTS-Sta)](arkts-static-bytecode-fundamentals.md)。二者共享 Panda 二进制容器与寄存器型虚拟机基础，但在类型元数据、索引布局、指令编码及调用约定等方面存在显著差异，须按对应文档分别解析，不可混用。

## 约束与限制

- 方舟字节码文件头 `version` 字段为 4 字节数组，次版本号 `version[1]` 用于区分编码体系：`1` 表示方舟字节码 (ArkTS-Sta)（版本形如 `0.1.x.y`），`0` 表示方舟字节码 (ArkTS-Dyn)（版本形如 `12.0.x.y` 等）。遗留方舟字节码 (ArkTS-Sta) 版本 `0.0.0.6` 的次版本号亦为 `0`，识别时须结合工具链与文件整体结构判断。
- 各子文档仅描述对应编码体系；解析、校验、反汇编及改写工具须与目标文件版本和编码类型匹配。
- 版本号为方舟编译器内部保留字段，文档中给出的版本号仅供对照，开发者通常无需手工构造版本字段。
- 字节码文件采用小端字节序；除各结构章节另有说明外，偏移量从文件起始位置（偏移 0）计算。

## 架构与实现原理

方舟字节码文件以固定魔数的文件头起始，通过偏移量与区域索引组织类、方法、字段、常量池及调试信息等结构。方法体由定长或变长编码的指令流组成，运行时以**虚拟寄存器 + 累加器（acc）**模型解释执行：多数指令隐式以 acc 为源或目标操作数，以降低编码体积。

方舟字节码 (ArkTS-Dyn) 面向 ECMAScript 动态语义，方法元数据与调用指令中编码实参个数与函数种类，属性访问多采用名称或运行时索引解析。方舟字节码 (ArkTS-Sta) 在编译期完成类型检查，以 [Proto](arkts-static-bytecode-file-format.md#proto)、`shorty` 等结构固化方法签名，指令通过 `type_id`、`method_id`、`field_id` 等强类型索引直接引用目标实体，并扩展四路索引区域、按类型分派异常处理等能力。

## 方舟字节码 (ArkTS-Dyn)

方舟字节码 (ArkTS-Dyn) 由ArkTS/TS/JS动态编译工具链生成，承载动态类型、词法环境、模块与补丁变量等ECMAScript语义。适用于动态应用编译产物分析、动态运行时问题定位及动态指令级特性开发。

- [方舟字节码文件格式 (ArkTS-Dyn)](arkts-bytecode-file-format.md)：说明文件头、类与方法索引、常量池及调试信息等二进制布局。
- [方舟字节码基本原理 (ArkTS-Dyn)](arkts-bytecode-fundamentals.md)：说明寄存器与累加器、词法环境、指令格式及完整指令语义。
- [方舟字节码函数命名规则 (ArkTS-Dyn)](arkts-bytecode-function-name.md)：说明函数字符串在字节码文件中的命名约定。

## 方舟字节码 (ArkTS-Sta)

方舟字节码 (ArkTS-Sta) 由ArkTS-Sta编译工具链生成，面向静态类型语言语义，被ArkTS-Sta方舟运行时解释执行或AOT编译。适用于静态编译产物结构分析、静态 VM 行为核对及静态指令级特性开发。

- [方舟字节码文件格式 (ArkTS-Sta)](arkts-static-bytecode-file-format.md)：说明Proto签名、四路索引区域、外部字段等静态类型元数据布局。
- [方舟字节码基本原理 (ArkTS-Sta)](arkts-static-bytecode-fundamentals.md)：说明前缀体系、调用约定、对象创建及完整指令集。

## 方舟字节码 (ArkTS-Dyn) 与方舟字节码 (ArkTS-Sta) 差异对照

下表汇总两套字节码在文件格式与指令层面的主要差异，便于对照分析时快速定位。详细字段与指令说明请参阅各自子文档。

### 文件格式差异

  | **对比项** | **方舟字节码 (ArkTS-Sta)** | **方舟字节码 (ArkTS-Dyn)** |
  | ---------- | -------------------------- | -------------------------- |
  | 版本标识 | `version[1] == 1`（`0.1.x.y`）；遗留 `0.0.0.6` 的次版本号为 `0` | `version[1] == 0`（如 `12.0.x.y`） |
  | 方法签名 | [Proto](arkts-static-bytecode-file-format.md#proto) + `shorty` 描述返回类型与参数类型 | 无 Proto；实参个数由调用指令编码（如 `callargN`、`callrange` 的 `+AA`） |
  | 方法元数据 | `proto_idx` + `access_flags` | `index_data`（含 `header_index` 和 `function_kind`） |
  | 字段元数据 | 含完整 `access_flags` | 含 `reserved` 字段 |
  | 外部字段 | 独立的 [ForeignField](arkts-static-bytecode-file-format.md#foreignfield) | 无 |
  | 类定义 | 含 `super_class_off`、接口列表 | 无父类偏移 |
  | 索引区域 | 类 / 方法 / 字段 / 原型四路索引 | 类索引 + 方法/字符串/字面量合并索引 |
  | 异常处理 | 支持按类型分派的多路 catch | 仅 catch-all |
  | 文件头 | `quickened_flag`、导出表、字面量数组索引 | `reserved` 字段 |

### 指令与执行模型差异

  | **对比项** | **方舟字节码 (ArkTS-Sta)** | **方舟字节码 (ArkTS-Dyn)** |
  | ---------- | -------------------------- | -------------------------- |
  | 类型系统 | 编译期静态类型，Proto 描述签名 | 运行时动态类型 |
  | 值存储 | 静态字段 / 实例字段 / 寄存器 | 全局变量 / 模块变量 / 词法环境 / 补丁变量 |
  | 方法调用 | `call` / `call.virt`（静态分派 + 虚分派） | `callarg0` / `callthis1` 等（this 绑定语义） |
  | 对象创建 | `newobj` + `call`，或 `initobj` 指令族 | `newobjrange` / `defineclasswithbuffer` |
  | 属性访问 | `ldobj` / `stobj` + `field_id` | `ldobjbyname` / `stobjbyname` + `string_id` |
  | 前缀体系 | `bit` / `unsigned` / `cast` / `f32` / `any` | `throw` / `wide` / `deprecated` / `callruntime` |
  | 寄存器宽度 | 4 / 8 / 16 位可变 | 固定 8 位 |
  | 异常处理 | 按类型多路 catch | 仅 catch-all |
  | 函数类型 | 无 FunctionKind 区分 | 区分普通函数 / 箭头函数 / 生成器 / 异步等 |

## 编译工具链通用能力

[编译期自定义修改方舟字节码](customize-bytecode-during-compilation.md)介绍如何在编译流程中插入或改写字节码内容，适用于需要在构建阶段注入探针、调整指令序列等场景。该能力对两套字节码均可能涉及，具体约束以该文档及目标编码类型为准。
