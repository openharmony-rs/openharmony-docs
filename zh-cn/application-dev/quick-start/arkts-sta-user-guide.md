# ArkTS-Sta用户指导

## 介绍

ArkTS-Sta版本引入了多项重要特性，例如：
- 静态类型系统。
- 对象天然共享特性，不再依赖Sendable特性，无需添加@Sendable装饰器。
- 互操作特性，提供ArkTS-Sta和ArkTS-Dyn以及TS/JS代码的交互能力。

## 前置说明

OpenHarmony应用开发面临着性能优化和架构演进这两方面的具体需求。ArkTS作为OpenHarmony原生应用开发的官方语言，在TypeScript生态的基础上进行了有针对性的扩展与增强，以满足这些核心需求。

### 为什么需要ArkTS静态类型

ArkTS静态类型满足了以下三个核心需求：

**提升应用性能**

ArkTS静态类型通过严格的类型限制和低运行时开销设计，显著提升应用性能：

- **低运行时开销：** 通过新增静态类型特性，减少运行时类型检查和优化开销，实现更高的应用性能。
- **编译时优化：** 静态类型系统使编译器能够在编译阶段进行深度优化，提升代码执行效率。
- **高效并发支持：** 支持共享内存的多线程并发模型，避免序列化开销，实现真正的高性能并行计算。
- **AOT编译优化：** 支持AOT预编译技术，将热点代码预先编译为机器码，进一步提升执行效率。

**增强代码健壮性**

静态类型系统的核心优势在于能够在编译阶段发现潜在问题：

- **类型安全：** 编译时强制类型检查，避免运行时类型错误，大幅降低应用崩溃率。
- **空安全：** 通过严格的空值检查机制，有效防止空指针异常。
- **API契约：** 明确的类型定义作为API契约，使接口使用更加规范和安全。

**支持高效并发编程**

现代应用需要充分利用多核CPU能力，ArkTS静态类型在并发编程方面提供了类型安全和内存共享等支持：

- **共享内存并发模型：** 支持线程间共享内存，避免了序列化开销，实现全场景的高性能并发。
- **类型安全的并发API：** 提供类型安全的并发编程接口，使多线程开发更加简单可靠。

### 目标读者

本文档适用于以下开发者群体：

**对ArkTS静态类型感兴趣，且需要进行并行化改造的应用开发人员**。

- 已具备OpenHarmony应用开发经验。
- 希望了解ArkTS静态类型的新特性和优势。
- 现有应用存在性能瓶颈，希望通过并行化改造提升性能。
- 应用需要处理多个计算密集型任务，需要充分利用多核CPU能力。
- 应用对响应速度有较高要求，希望通过静态类型优化启动时间和运行效率。

### 读者预备知识

为更好地理解相关文档内容，建议读者具备以下知识基础：

- **TypeScript基础：** 熟悉TypeScript或JavaScript语法和类型系统。
- **OpenHarmony应用开发经验：** 至少6个月以上的OpenHarmony应用开发经验。
- **并发编程概念：** 了解线程、进程、锁、竞态条件等基本概念。
- **OpenHarmony应用架构：** 理解Ability、UI框架、数据管理等基础概念。

## 规范指引

详细的规范文档请参考：[ArkTS-Sta规范](https://gitee.com/openharmony/arkcompiler_runtime_core/releases)

## ArkTS 迁移指南

为帮助开发者顺利迁移到ArkTS-Sta，特提供以下迁移指南。

- 了解ArkTS-Sta的基础语法和规则变更：[ArkTS基础规则变更](./arkts-dyn-to-sta-syntax-rules.md)。
- 了解新的并发特性和使用方法：[并发特性变更](./arkts-dyn-to-sta-concurrency-rules.md)。
- 了解与其他系统交互的规则变更：[ArkTS互操作规则变更](./arkts-dyn-to-sta-interop-rules.md)。
- 了解builtin的语法和规则变更：[builtin规则变更](./arkts-dyn-to-sta-builtin-rules.md)。
- 了解ArkUI的语法和接口变更：[从ArkTS-Dyn到ArkTS-Sta的UI语法规则适配](../ui/arkts-dyn-sta-ui-rules.md)。
- 了解SDK的语法和规则变更：[SDK规则变更](./arkts-dyn-to-sta-sdk-rules.md)。
- 了解ArkTS-Sta的应用迁移改造：[ArkTS新增静态类型及应用迁移改造概述](./arkts-sta-additions-application-migration.md)。 
- 了解ArkTS-Sta的类型改造示例：[ArkTS静态类型改造案例](./arkts-sta-transformation-case.md)。
- 了解ArkTS-Sta的应用改造示例：[ArkTS静态类型迁移改造案例](./arkts-sta-migration-case.md)。

## ArkTS-Sta与ArkTS-Dyn文件区分方式

ArkTS-Sta包含已有的ArkTS-Dyn特性和新引入的静态类型模式，使用静态类型特性的代码文件通过在文件头增加"use static"导语进行说明。ArkTS语言版本号与"use static"导语是两个维度的配置。"use static"表示静态模式，后续ArkTS版本升级会一直带静态类型特性，文件内"use static"导语可保持不变，无需修改适配。

### 约束限制

- ArkTS-Sta静态类型源码和声明文件均需在首行增加"use static"，否则默认为ArkTS-Dyn文件。
- "use static"必须位于文件首行，即使存在import语句、文件注释等，也一样位于这些语句之前的文件首行。
- "use static"是一个字面量表达式，所以字母大小写敏感，建议与"use strict"一致使用双引号形式。
```typescript
"use static"; // 位于首行，import语句前
import { hilog } from '@kit.PerformanceAnalysisKit';
```
```typescript
"use static"; // 位于首行，文件注释前
// 这是一行注释
import { hilog } from '@kit.PerformanceAnalysisKit';
```

- **版本演进性：** ArkTS静态类型处于持续演进中，本文档基于当前版本编写，类型系统和语法特性可能在后续版本中调整。
API范围说明：本文档描述静态类型SDK和应用框架API范围为研发中的API，后续版本将扩展。

## ArkTS静态类型全景概述

### 静态类型改造场景

**核心价值**

1. 性能提升

- **启动加速：** AOT预编译和关键模块的并行化。
- **执行效率：** 直接执行机器码，提升运行性能。
- **内存优化：** 无需JIT运行时，降低内存占用。

2. 并发能力
 
- **内存共享：** EAWorker支持线程间内存共享，突破消息传递限制。
- **零拷贝传输：** 直接共享对象，无需序列化开销。
- **并行处理：** 多线程并行执行，释放主线程资源。

### 典型应用场景

| 场景类型 | 典型特征 |
|:---------|:---------|
| **计算密集型** | 数据加密/解密、图像处理、压缩算法。 |
| **启动瓶颈型** | 应用启动慢、初始化耗时长。 |
| **高并发需求** | 需要多线程并行处理的任务。 |
| **性能敏感型** | 用户明显感知的卡顿、延迟。 |


### 静态类型知识全景概述

| 分类           | 子类                          | 资料名                                     | 状态 |
| :------------- | :--------------------------- | :---------------------------------------- |:--------------- |
| 快速入门 | 开发准备 | DevEco Studio、SDK、ROM镜像 |已完成
| 快速入门 | 构建第一个ArkTS静态类型的应用 | DevEco Studio创建支持ArkTS静态类型HelloWorld工程 |准备中
| 学习ArkTS语言  | 初识ArkTS静态类型             | ArkTS语言演进介绍                          |准备中
| 学习ArkTS语言   | 初识ArkTS静态类型             | [ArkTS静态类型Playground](https://arkts-play.cn.bz-openlab.ru:10443)                    |已完成
| 学习ArkTS语言   | ArkTS静态类型编程规范         | [ArkTS静态类型语言Specification](https://gitcode.com/openharmony/arkcompiler_runtime_core/releases/)             |已完成
| ArkTS          | ArkTS静态类型                 |  [ArkTS动态类型到静态类型迁移工具使用指导](../quick-start/arkts-easytrans-userguide.md)      |已完成
| ArkTS        |    ArkTS静态类型                 | [ArkTS动静态上下文互操作指导](../quick-start/arkts-dyn-to-sta-interop-rules.md)                |已完成
| ArkTS       |      ArkTS静态类型              | [ArkTS动静态类型语法差异](../quick-start/arkts-dyn-to-sta-syntax-rules.md)                    |已完成
| ArkTS          |     ArkTS静态类型                 | [ArkTS静态类型并发特性](../quick-start/arkts-dyn-to-sta-concurrency-rules.md)                      |已完成
| ArkTS         |       ArkTS静态类型             | ArkTS静态类型注解、AOP                     |准备中
|ArkTS | ArkTS静态类型 | ArkTS静态类型混淆 |准备中
| SDK            | 静态类型SDK                   | [静态类型API范围](https://gitcode.com/openharmony/docs/tree/OpenHarmony_feature_20250702/zh-cn/application-dev/reference)                      |已完成
| 应用框架       | ArkUI                         | [ArkUI静态类型API相比动态差异](../reference/apis-arkui/Readme-CN.md)                  |已完成
|  应用框架    |    ArkUI                   | [ArkUI静态类型状态管理相比动态差异](../reference/apis-arkui/Readme-CN.md)          |已完成
| 应用框架 | ArkUI | [ArkUI动态到静态迁移适配指导](../ui/Readme-CN.md) |已完成
| 应用框架 | ArkUI | [ArkUI动静态互操作指导](../ui/Readme-CN.md) | 已完成
| 应用框架 | ArkUI | [ArkUI静态类型并发特性](../reference/apis-arkui/js-apis-arkui-Parallelize.md) |已完成
| Sample应用     | Sample应用                    | [Sample代码仓库说明](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/ArkTS-Sta)                         |已完成
| CodeLabs       | CodeLabs                      | CodeLabs说明                               |准备中
| 构建应用       | 编译构建                      | 构建任务说明                              |准备中
| 编写与调试应用 | 应用调试                      | UI布局分析          |准备中
| 优化应用性能   | 卡顿丢帧分析                  | Frame分析  |准备中
| 应用测试       | 应用测试                      | 单元测试框架 |准备中
|  应用测试        |  应用测试                   | UI测试框架  |准备中
