# ReadOptions

可选项类型，支持read接口使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface ReadOptions--><!--Device-unnamed-export interface ReadOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## length

```TypeScript
length?: long
```

期望读取数据的长度，单位为Byte。可选，默认缓冲区长度。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ReadOptions-length?: long--><!--Device-ReadOptions-length?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## offset

```TypeScript
offset?: long
```

期望读取文件位置，单位为Byte（基于当前filePointer加上offset的位置）。可选，默认从偏移指针（filePointer）开始读。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ReadOptions-offset?: long--><!--Device-ReadOptions-offset?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

