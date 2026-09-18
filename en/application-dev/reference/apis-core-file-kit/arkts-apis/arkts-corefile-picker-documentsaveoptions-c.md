# DocumentSaveOptions

Defines the options for saving documents.

**Since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

## Modules to Import

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## autoCreateEmptyFile

```TypeScript
autoCreateEmptyFile?: boolean
```

A Boolean value indicates whether to pre-create empty files when saving files. The default value is **true**, in which case the Picker pre-creates empty files and returns an array of the file URIs. If it is set to **false**, no empty files are pre-created, and only an array of the file URIs is returned.

**Type:** boolean

**Default:** true

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

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

## fileSuffixChoices

```TypeScript
fileSuffixChoices?: Array<string>
```

Document suffix of the document to save.

The value is a string array. Each element specifies an option, which includes at most two parts with a vertical bar (|) in between. The first part is the description, and the second part is the document suffix. If there is no "|", the option does not have the description. By default, all documents are saved.

**Type:** Array&lt;string&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

## newFileNames

```TypeScript
newFileNames?: Array<string>
```

Name of the document to save. If this parameter is not specified, the user needs to enter the file name.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

## pickerMode

```TypeScript
pickerMode?: DocumentPickerMode
```

Mode for starting Picker.

Default value: **DEFAULT**. If **pickerMode** is **DOWNLOAD**, the settings of **newFileNames**, **defaultFilePathUri**, and **fileSuffixChoices** do not take effect.

**Type:** [DocumentPickerMode](arkts-corefile-picker-documentpickermode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService
