# ReadStreamOptions

可选项类型，支持 createReadStream 接口使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface ReadStreamOptions--><!--Device-unnamed-export interface ReadStreamOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## end

```TypeScript
end?: long
```

表示期望读取结束的位置，单位为Byte。可选，默认文件末尾。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ReadStreamOptions-end?: long--><!--Device-ReadStreamOptions-end?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## start

```TypeScript
start?: long
```

表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ReadStreamOptions-start?: long--><!--Device-ReadStreamOptions-start?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

