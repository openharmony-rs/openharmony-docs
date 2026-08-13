# ListFileExtOptions

可选项类型，支持listFileExt接口使用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export interface ListFileExtOptions--><!--Device-unnamed-export interface ListFileExtOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## fileFilter

```TypeScript
fileFilter?: FileFilter
```

自定义文件名过滤的规则，默认为空，表示不进行过滤。

**类型：** [FileFilter](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-filefilter-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListFileExtOptions-fileFilter?: FileFilter--><!--Device-ListFileExtOptions-fileFilter?: FileFilter-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## listNum

```TypeScript
listNum?: long
```

列出文件名数量，默认为0，表示列出所有文件。

**类型：** long

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListFileExtOptions-listNum?: long--><!--Device-ListFileExtOptions-listNum?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## recursion

```TypeScript
recursion?: boolean
```

是否递归子目录下的文件名，默认为false。 false：返回当前目录下满足过滤要求的文件名及目录名。 true：返回该目录下所有符合过滤条件的文件的相对路径，相对路径以“/”开头。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListFileExtOptions-recursion?: boolean--><!--Device-ListFileExtOptions-recursion?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

