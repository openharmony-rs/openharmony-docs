# RandomAccessFileOptions

可选项类型，支持 createRandomAccessFile 接口使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface RandomAccessFileOptions--><!--Device-unnamed-export interface RandomAccessFileOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
```

## end

```TypeScript
end?: long
```

表示期望读取结束的位置，单位为Byte。可选，默认文件末尾。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-RandomAccessFileOptions-end?: long--><!--Device-RandomAccessFileOptions-end?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## start

```TypeScript
start?: long
```

表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-RandomAccessFileOptions-start?: long--><!--Device-RandomAccessFileOptions-start?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

