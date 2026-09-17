# DocumentSelectOptions

Defines the options for selecting documents.

**Since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

## Modules to Import

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## allowsMulFolderSelection

```TypeScript
allowsMulFolderSelection?: boolean
```

Whether to support for selecting folders, Only 2-in-1 devices are supported. The value false (default) means not support folder selection;

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.UserFileService.FolderSelection

## authMode

```TypeScript
authMode?: boolean
```

Whether to start Picker.

Default value: **false**. If **authMode** is **true**, **defaultFilePathUri** is mandatory, which specifies the URI of the file allowed to access.

This parameter can be used on 2-in-1 devices but has no effect on other devices.

This API can be used in atomic services since API version 12.

SystemCapability.FileManagement.UserFileService.FolderSelection

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService.FolderSelection

## defaultFilePathUri

```TypeScript
defaultFilePathUri?: string
```

URI of the file or directory that can be selected. It is empty by default (the recently opened page is displayed).

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

## fileSuffixFilters

```TypeScript
fileSuffixFilters?: Array<string>
```

Suffix of the document to select.

The value is a string array. Each element specifies an option, which includes at most two parts with a vertical bar (|) in between. The first part is the description, and the second part is the document suffix. If there is no "|", the option does not have the description. Each filter suffix can contain multiple suffixes, separated by a comma (,). The length of the input array cannot exceed 100 characters, for example, ['Images (.png,jpg)|.png,jpg', 'Documents|.txt', 'Videos|.mp4', '.pdf'].

By default, no filtering is performed, that is, all documents are selected. The wildcard ['All files (*.*)|.*'] can be used on 2-in-1 devices to display all files. (Mobile phones can support this configuration since API version 17.)

This parameter is available only to the devices that have the required system capability.

**Type:** Array&lt;string&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

## isEncryptionSupported

```TypeScript
isEncryptionSupported?: boolean
```

Whether to support encryption (only files are supported). The default value is **false**. If this parameter is set to **true**, files can be encrypted on the Picker page.

**Type:** boolean

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.FileManagement.UserFileService

## maxSelectNumber

```TypeScript
maxSelectNumber?: number
```

Maximum number of files that can be selected.

In API version 20 and earlier versions, a maximum of 500 files can be selected at a time. The default value is 500. Directories can be selected only on devices that have the system capability. A maximum of one directory can be selected at a time.

In API version 21 and later versions, the maximum number of files that can be selected at a time is not limited. Due to system capability restrictions, if too many files are selected at a time, the functionality may be abnormal or the processing performance may be poor. It is recommended that a maximum of 10,000 files be selected at a time.

In API version 23 and later versions, the maximum number of files that can be selected at a time is not limited.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

## mergeMode

```TypeScript
mergeMode?: MergeTypeMode
```

Whether to enable the aggregation view mode for a file management application. The default value is **DEFAULT**, indicating that this parameter does not take effect and the aggregation view is disabled. If this parameter is set to a value other than **DEFAULT**, other parameters do not take effect.

This parameter can be used on smartphones but has no effect on other devices.

**Type:** [MergeTypeMode](arkts-corefile-picker-mergetypemode-e.md)

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.FileManagement.UserFileService

## multiAuthMode

```TypeScript
multiAuthMode?: boolean
```

Whether to enable the batch authorization mode.

The value **false** (default) means to disable the batch authorization mode; the value **true** means to enable the batch authorization mode. The **multiUriArray** parameter only takes effect when **multiAuthMode** is set to **true**.

This parameter can be used on smartphones but has no effect on other devices.

**Type:** boolean

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.FileManagement.UserFileService

## multiUriArray

```TypeScript
multiUriArray?: Array<string>
```

Whether to pass the URIs for batch authorization (only files are supported). This parameter is used together with **multiAuthMode** and does not take effect when **multiAuthMode** is set to **false**. By default, this parameter is left empty. (The files displayed on the batch authorization page are empty.)

This parameter can be used on smartphones but has no effect on other devices.

**Type:** Array&lt;string&gt;

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.FileManagement.UserFileService

## selectMode

```TypeScript
selectMode?: DocumentSelectMode
```

Type of the document selected by Picker. The default value is **FILE** (file type).

**Type:** [DocumentSelectMode](arkts-corefile-picker-documentselectmode-e.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService.FolderSelection
