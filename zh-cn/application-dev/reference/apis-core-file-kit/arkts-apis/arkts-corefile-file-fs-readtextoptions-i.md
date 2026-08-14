# ReadTextOptions

可选项类型，支持readText接口使用，ReadTextOptions继承至[ReadOptions](arkts-corefile-file-fs-readoptions-i.md#ReadOptions)。

**继承/实现关系：** ReadTextOptions extends [ReadOptions](arkts-corefile-file-fs-readoptions-i.md#ReadOptions)

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-export interface ReadTextOptions--><!--Device-unnamed-export interface ReadTextOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## encoding

```TypeScript
encoding?: string
```

当数据是 string 类型时有效，表示数据的编码方式，默认 'utf-8'，仅支持 'utf-8'。

**类型：** string

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ReadTextOptions-encoding?: string--><!--Device-ReadTextOptions-encoding?: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

