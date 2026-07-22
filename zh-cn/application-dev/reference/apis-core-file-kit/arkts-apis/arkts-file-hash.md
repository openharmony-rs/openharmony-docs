# @ohos.file.hash

该模块提供文件哈希处理能力，对文件内容进行哈希处理。

**起始版本：** 9

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
| [createHash](arkts-corefile-hash-createhash-f.md#createhash) | 创建并返回 HashStream 对象，该对象可用于使用给定的 algorithm 生成哈希摘要。 |
| [hash](arkts-corefile-hash-f.md#hash) | 计算文件的哈希值，使用Promise异步回调。 |
| [hash](arkts-corefile-hash-f.md#hash-1) | 计算文件的哈希值，使用callback异步回调。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [HashStream](arkts-corefile-hash-hashstream-c.md) | HashStream 类是用于创建数据的哈希摘要的实用工具。由 [createHash](arkts-corefile-hash-createhash-f.md#createhash) 接口获得。 |

