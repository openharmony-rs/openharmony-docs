# FileResponse

文件返回。包含文件的信息。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export interface FileResponse--><!--Device-unnamed-export interface FileResponse-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## lastModifiedTime

```TypeScript
lastModifiedTime: number
```

文件保存时的时间戳，从1970/01/01?00:00:00到当前时间的毫秒数。

**类型：** number

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileResponse-lastModifiedTime: number--><!--Device-FileResponse-lastModifiedTime: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## length

```TypeScript
length: number
```

文件长度，单位为Byte。

**类型：** number

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileResponse-length: number--><!--Device-FileResponse-length: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## subFiles

```TypeScript
subFiles?: Array<FileResponse>
```

文件列表。

**类型：** Array&lt;FileResponse&gt;

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileResponse-subFiles?: Array<FileResponse>--><!--Device-FileResponse-subFiles?: Array<FileResponse>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## type

```TypeScript
type: 'dir' | 'file'
```

文件类型，可选值为：  
-dir：目录；  
-file：文件。

**类型：** 'dir' \| 'file'

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileResponse-type: 'dir' | 'file'--><!--Device-FileResponse-type: 'dir' | 'file'-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## uri

```TypeScript
uri: string
```

文件的URI。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileResponse-uri: string--><!--Device-FileResponse-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

