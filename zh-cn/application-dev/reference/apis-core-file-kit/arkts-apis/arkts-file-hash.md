# @ohos.file.hash

该模块提供文件哈希处理能力，对文件内容进行哈希处理，适用于数据完整性校验、版本比对与内容去重等场景，可确保计算结果的不可变性与一致性，并支持流式处理大文件。 > **使用说明：** 使用该功能模块对文件/目录进行操作前，需要先获取其应用沙箱路径，获取沙箱路径的方式及其接口用法可参考： [应用上下文Context-获取应用文件路径](../../../application-models/application-context-stage.md#获取应用文件路径)。

**起始版本：** 23

<!--Device-unnamed-declare namespace hash--><!--Device-unnamed-declare namespace hash-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { hash } from '@kit.CoreFileKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createHash](arkts-corefile-hash-createhash-f.md) | 创建并返回HashStream对象，用于生成哈希摘要。可以指定哈希计算采用的算法。HashStream采用流式处理机制，支持分批次更新数据，适用于大文件或数据流的哈希计算，避免一次性加载大文件到内存。 |
| [hash](arkts-corefile-hash-f.md) | 计算文件的哈希值，基于指定算法对文件完整内容进行哈希摘要计算。使用Promise异步回调。 |
| [hash](arkts-corefile-hash-f.md) | 计算文件的哈希值，基于指定算法对文件完整内容进行哈希摘要计算。使用callback异步回调。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [HashStream](arkts-corefile-hash-hashstream-c.md) | HashStream类是用于创建数据的哈希摘要的实用工具。由 [createHash](arkts-corefile-hash-createhash-f.md) 接口获得。该类采用增量式哈希计算设计，通过update方法多次添加数据块， 最后通过digest方法计算最终哈希值，适用于处理大文件或持续产生的数据流。 |

