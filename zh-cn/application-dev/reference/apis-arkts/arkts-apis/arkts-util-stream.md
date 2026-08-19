# @ohos.util.stream

本模块提供基本流类型的处理能力，支持数据分块读取或写入，避免一次性加载整个数据到内存。 包括可写流（[Writable](arkts-arkts-stream-writable-c.md)）、可读流（[Readable](arkts-arkts-stream-readable-c.md)）、双工流（[Duplex](arkts-arkts-stream-duplex-c.md)）和转换流（[Transform](arkts-arkts-stream-transform-c.md)）。

**起始版本：** 23

<!--Device-unnamed-declare namespace stream--><!--Device-unnamed-declare namespace stream-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { stream } from '@kit.ArkTS';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Duplex](arkts-arkts-stream-duplex-c.md) | 既可读又可写的流。双工流允许数据双向传输，即可读可写。 **Duplex**类继承自[Readable](arkts-arkts-stream-readable-c.md)，支持**Readable**中的所有API。 |
| [Readable](arkts-arkts-stream-readable-c.md) | 可从中读取数据的流。可读流用于从源（如文件或网络套接字）读取数据。 |
| [Transform](arkts-arkts-stream-transform-c.md) | 一种特殊的双工流，支持数据转换和结果输出。**Transform**类继承自[Duplex](arkts-arkts-stream-duplex-c.md)，支持**Duplex**中的所有API。 |
| [Writable](arkts-arkts-stream-writable-c.md) | 可写入数据的流。可写流允许将数据写入到目标中，这个目标可以是文件、HTTP响应、标准输出、另一个流等。可写流采用缓冲区机制：数据通过write()写入缓冲区，缓冲区数据通过doWrite()自动写出到目标，开发者需实现doWrite以定义数据写出的具体行为。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ReadableOptions](arkts-arkts-stream-readableoptions-i.md) | 描述**Readable**构造函数中使用的选项。 |

