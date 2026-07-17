# DocumentSaveOptions

文档保存选项。

**起始版本：** 9

<!--Device-picker-class DocumentSaveOptions--><!--Device-picker-class DocumentSaveOptions-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## 导入模块

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## autoCreateEmptyFile

```TypeScript
autoCreateEmptyFile?: boolean
```

保存文件时，由应用决定是否预置空文件。默认为true，Picker会预置空文件并且返回文件的URI数组。false不预置空文件，只会返回文件的URI数组。

**类型：** boolean

**默认值：** true

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DocumentSaveOptions-autoCreateEmptyFile?: boolean--><!--Device-DocumentSaveOptions-autoCreateEmptyFile?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService.FolderSelection

## defaultFilePathUri

```TypeScript
defaultFilePathUri?: string
```

指定选择的文件或者目录的URI。默认为空（效果为拉起最近打开页）。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSaveOptions-defaultFilePathUri?: string--><!--Device-DocumentSaveOptions-defaultFilePathUri?: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## fileSuffixChoices

```TypeScript
fileSuffixChoices?: Array<string>
```

保存文件的后缀类型。传入字符串数组，每一项代表一个后缀选项，每一项内部用"|"分为两部分，第一部分为描述，第二部分为要保存的后缀。没有"|"则没有描述，该项整体是一个保存的后缀。默认没有后缀类型。

**类型：** Array<string>

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSaveOptions-fileSuffixChoices?: Array<string>--><!--Device-DocumentSaveOptions-fileSuffixChoices?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## newFileNames

```TypeScript
newFileNames?: Array<string>
```

拉起documentPicker进行保存的文件名。若无此参数，则默认需要用户自行输入。

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSaveOptions-newFileNames?: Array<string>--><!--Device-DocumentSaveOptions-newFileNames?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## pickerMode

```TypeScript
pickerMode?: DocumentPickerMode
```

拉起picker的类型, 默认为DEFAULT。当pickerMode设置为DOWNLOAD时，用户配置的参数newFileNames、defaultFilePathUri和fileSuffixChoices将不会生效。

**类型：** DocumentPickerMode

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSaveOptions-pickerMode?: DocumentPickerMode--><!--Device-DocumentSaveOptions-pickerMode?: DocumentPickerMode-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

