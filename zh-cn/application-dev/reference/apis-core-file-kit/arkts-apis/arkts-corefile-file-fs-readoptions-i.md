# ReadOptions

可选项类型，支持read接口使用。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-export interface ReadOptions--><!--Device-unnamed-export interface ReadOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## length

```TypeScript
length?: number
```

期望读取数据的长度，单位为Byte。可选，默认缓冲区长度。

**类型：** number

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ReadOptions-length?: number--><!--Device-ReadOptions-length?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## offset

```TypeScript
offset?: number
```

期望读取文件位置，单位为Byte（基于当前filePointer加上offset的位置）。可选，默认从偏移指针（filePointer）开始读。

**类型：** number

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ReadOptions-offset?: number--><!--Device-ReadOptions-offset?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

