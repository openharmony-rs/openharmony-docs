# FileFilter

文件名过滤器接口，可通过该接口自定义文件名过滤规则。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export interface FileFilter--><!--Device-unnamed-export interface FileFilter-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## filter

```TypeScript
filter(name: string): boolean
```

用于[listFileExt]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或[listFileExtSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口的文件过滤， 判断指定文件名是否应包含在返回的文件列表中。 > **说明**： > > 该函数调用频率较高，请避免执行耗时操作，如文件I/O、网络请求等。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileFilter-filter(name: string): boolean--><!--Device-FileFilter-filter(name: string): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 待过滤的文件名或文件相对路径。递归模式下为文件的相对路径，相对路径以“/”开头。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否包含在返回的文件列表中。true：包含该文件；false：不包含该文件。 |

