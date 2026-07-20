# DocumentSelectOptions

文档选择选项。

**起始版本：** 9

<!--Device-picker-class DocumentSelectOptions--><!--Device-picker-class DocumentSelectOptions-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## 导入模块

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## allowsMulFolderSelection

```TypeScript
allowsMulFolderSelection?: boolean
```

是否支持多选文件夹。true表示支持，false表示不支持，默认值为false。该参数需要与selectMode配合使用，当selectMode为FOLDER或者MIXED，并且allowsMulFolderSelection为true，多选文件夹功能生效。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-allowsMulFolderSelection?: boolean--><!--Device-DocumentSelectOptions-allowsMulFolderSelection?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService.FolderSelection

## authMode

```TypeScript
authMode?: boolean
```

拉起授权Picker，默认为false（非授权模式）。当authMode为true时为授权模式，defaultFilePathUri必填，表明待授权URI。

该参数在2in1设备中可正常使用，在其他设备中无效果。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-authMode?: boolean--><!--Device-DocumentSelectOptions-authMode?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService.FolderSelection

## defaultFilePathUri

```TypeScript
defaultFilePathUri?: string
```

指定选择的文件或者目录的URI。默认为空（效果为拉起最近打开页）。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-defaultFilePathUri?: string--><!--Device-DocumentSelectOptions-defaultFilePathUri?: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## fileSuffixFilters

```TypeScript
fileSuffixFilters?: Array<string>
```

选择文件的后缀类型。传入字符串数组，每一项代表一个后缀选项，每一项内部用"|"分为两部分，第一部分为描述，第二部分为过滤后缀。没有"|"则没有描述，该项整体是一个过滤后缀。每项过滤后缀可以存在多个后缀名，则每一个后缀名之间用英文逗号进行分隔，传入数组长度不能超过100，例如：['图片(.png, .jpg)|.png,.jpg', '文档|.txt', '视频|.mp4', '.pdf']。

默认不过滤，即显示所有文件。此外2in1设备支持通配符方式['所有文件(*.*)|.*']（说明：从API version 17开始，手机支持该配置），表示为显示所有文件。

仅对具有该系统能力的设备开放。

**类型：** Array&lt;string&gt;

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-fileSuffixFilters?: Array<string>--><!--Device-DocumentSelectOptions-fileSuffixFilters?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## isEncryptionSupported

```TypeScript
isEncryptionSupported?: boolean
```

是否支持加密（仅支持文件，文件夹不生效），默认为false。该参数为true时，在Picker界面可以选择对文件进行加密。

**类型：** boolean

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-isEncryptionSupported?: boolean--><!--Device-DocumentSelectOptions-isEncryptionSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## maxSelectNumber

```TypeScript
maxSelectNumber?: number
```

选择文件最大个数。

API version 20及之前的版本，单次文件选择的最大数量上限为500个，默认值也为500。目录选择功能仅对具备该系统能力的设备开放，且单次最多可选择1个目录。

API version 21及之后的版本取消文件选择数量的限制。受系统能力限制，选择文件数量过大可能会出现功能异常或处理性能较差等情况，建议单次选择文件个数不超过1万个。

API version 23及之后的版本取消目录选择数量的限制。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-maxSelectNumber?: number--><!--Device-DocumentSelectOptions-maxSelectNumber?: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## mergeMode

```TypeScript
mergeMode?: MergeTypeMode
```

开启聚合视图模式，支持拉起文件管理应用的聚合视图。默认为DEFAULT，表示该参数不生效，非聚合视图。当该参数置为非DEFAULT时，其他参数不生效。

该参数在Phone设备中可正常使用，在其他设备中无效果。

**类型：** MergeTypeMode

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-mergeMode?: MergeTypeMode--><!--Device-DocumentSelectOptions-mergeMode?: MergeTypeMode-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## multiAuthMode

```TypeScript
multiAuthMode?: boolean
```

支持批量授权模式，默认为false（非批量授权模式）。当multiAuthMode为true时为批量授权模式。当multiAuthMode为true时，只有multiUriArray参数生效，其他参数不生效。

该参数在Phone设备中可正常使用，在其他设备中无效果。

**类型：** boolean

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-multiAuthMode?: boolean--><!--Device-DocumentSelectOptions-multiAuthMode?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## multiUriArray

```TypeScript
multiUriArray?: Array<string>
```

传入需要批量授权的URI数组（仅支持文件，文件夹不生效）。配合multiAuthMode使用。当multiAuthMode为false时，配置该参数不生效。默认为空（效果为拉起批量授权页面后展示的文件为空）。

该参数在Phone设备中可正常使用，在其他设备中无效果。

**类型：** Array&lt;string&gt;

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-multiUriArray?: Array<string>--><!--Device-DocumentSelectOptions-multiUriArray?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## selectMode

```TypeScript
selectMode?: DocumentSelectMode
```

Picker选择的文档类型，默认值是FILE(文件类型)。

**类型：** DocumentSelectMode

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DocumentSelectOptions-selectMode?: DocumentSelectMode--><!--Device-DocumentSelectOptions-selectMode?: DocumentSelectMode-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService.FolderSelection

