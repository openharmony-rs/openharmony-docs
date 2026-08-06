# ListFileOptions

可选项类型，支持listFile接口使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface ListFileOptions--><!--Device-unnamed-export interface ListFileOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## filter

```TypeScript
filter?: Filter
```

文件过滤配置项。 可选，设置过滤条件。

**类型：** Filter

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ListFileOptions-filter?: Filter--><!--Device-ListFileOptions-filter?: Filter-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## listNum

```TypeScript
listNum?: long
```

列出文件名数量。可选，当设置0时，列出所有文件，默认为0。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ListFileOptions-listNum?: long--><!--Device-ListFileOptions-listNum?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## recursion

```TypeScript
recursion?: boolean
```

是否递归子目录下文件名。可选，默认为false。当recursion为false时，返回当前目录下满足过滤要求的文件名及目录名。当recursion为true时，返回此目录下所有满足过滤要求的文件的相对路径（以“/”开头）。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ListFileOptions-recursion?: boolean--><!--Device-ListFileOptions-recursion?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

