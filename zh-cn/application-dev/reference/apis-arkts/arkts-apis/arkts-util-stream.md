# @ohos.util.stream

stream模块提供了处理基本流类型的API。通过流，数据可按块读取或写入，而不是一次性加载到内存中。
有四种基本流类型：可写流（[Writable](arkts-arkts-writable-c.md)）、可读流（[Readable](arkts-arkts-readableoptions-i.md)）、双工流（[Duplex](arkts-arkts-duplex-c.md)）和转换流（[Transform](arkts-arkts-transform-c.md)）。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Duplex](arkts-arkts-duplex-c.md) | 既可读又可写的流。双工流允许数据双向传输，即可读可写。**Duplex**类继承自[Readable](arkts-arkts-readableoptions-i.md)，支持**Readable**中的所有API。 |
| [Readable](arkts-arkts-readable-c.md) | 可从中读取数据的流。可读流用于从源（如文件或网络套接字）读取数据。 |
| [Transform](arkts-arkts-transform-c.md) | 一种特殊的双工流，支持数据转换和结果输出。**Transform**类继承自[Duplex](arkts-arkts-duplex-c.md)，支持**Duplex**中的所有API。 |
| [Writable](arkts-arkts-writable-c.md) | 可写入数据的流。可写流允许将数据写入目标，目标可以是文件、HTTP响应、标准输出、另一个流等。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ReadableOptions](arkts-arkts-readableoptions-i.md) | 描述**Readable**构造函数中使用的选项。 |

