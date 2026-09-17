# FileResponse

Returns a file, including the file information.

**Since:** 3

**Deprecated since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## Modules to Import

```TypeScript
```

## lastModifiedTime

```TypeScript
lastModifiedTime: number
```

Timestamp when the file is stored the last time, which is the number of milliseconds elapsed since 1970/01/01 00:00:00 GMT. For lite wearables, the value is fixed to 0, because this parameter is restricted by the underlying file system.

**Type:** number

**Since:** 3

**Deprecated since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## length

```TypeScript
length: number
```

File length, in bytes.

**Type:** number

**Since:** 3

**Deprecated since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## subFiles

```TypeScript
subFiles?: Array<FileResponse>
```

List of files. When the recursive value is true and the type is dir, the file information under the subdirectory will be returned. Otherwise, no value will be returned.

**Type:** Array&lt;[FileResponse](arkts-corefile-system-file-fileresponse-depr-i.md)&gt;

**Since:** 3

**Deprecated since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## type

```TypeScript
type: 'dir' | 'file'
```

File type. Available values are as follows: **dir**: directory **file**: file

**Type:** 'dir' &#124; 'file'

**Since:** 3

**Deprecated since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite

## uri

```TypeScript
uri: string
```

URI of the file.

**Type:** string

**Since:** 3

**Deprecated since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO.Lite
