# @ohos.file.fileuri

提供文件URI相关接口，可用于URI与应用沙箱路径之间的转换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace fileUri--><!--Device-unnamed-declare namespace fileUri-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getUriFromPath](arkts-corefile-fileuri-geturifrompath-f.md#getUriFromPath) | 通过应用沙箱内的文件路径生成URI。路径中的中文及非数字字母的特殊字符会进行百分号编码。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [FileUri](arkts-corefile-fileuri-fileuri-c.md) | FileUri表示文件的URI，继承自uri.URI。 |

