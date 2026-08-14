# WriteOptions

可选项类型，支持write接口使用，WriteOptions继承自[Options](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-options-i.md#Options)。

**继承/实现关系：** WriteOptions extends [Options](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-options-i.md#Options)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface WriteOptions--><!--Device-unnamed-export interface WriteOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## length

```TypeScript
length?: long
```

期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WriteOptions-length?: long--><!--Device-WriteOptions-length?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## offset

```TypeScript
offset?: long
```

期望写入文件位置，单位为Byte（基于当前filePointer加上offset的位置）。可选，默认从偏移指针（filePointer）开始写。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WriteOptions-offset?: long--><!--Device-WriteOptions-offset?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

