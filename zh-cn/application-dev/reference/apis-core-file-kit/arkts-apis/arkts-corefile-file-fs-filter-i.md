# Filter

文件过滤配置项，支持listFile接口使用。

**起始版本：** 10

<!--Device-unnamed-export interface Filter--><!--Device-unnamed-export interface Filter-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## displayName

```TypeScript
displayName?: Array<string>
```

文件名模糊匹配，各个关键词OR关系。当前仅支持通配符*。

**类型：** Array<string>

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-displayName?: Array<string>--><!--Device-Filter-displayName?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## excludeMedia

```TypeScript
excludeMedia?: boolean
```

是否排除Media中已有的文件。true：排除Media中已有的文件；false：不排除Media中已有的文件。

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-excludeMedia?: boolean--><!--Device-Filter-excludeMedia?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## fileSizeOver

```TypeScript
fileSizeOver?: number
```

文件大小匹配，大于指定大小的文件，单位为Byte。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-fileSizeOver?: number--><!--Device-Filter-fileSizeOver?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## lastModifiedAfter

```TypeScript
lastModifiedAfter?: number
```

文件最近修改时间匹配，在指定时间点及之后的文件。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-lastModifiedAfter?: number--><!--Device-Filter-lastModifiedAfter?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## mimeType

```TypeScript
mimeType?: Array<string>
```

mime类型完全匹配，各个关键词OR关系。预留字段，暂不支持使用。

**类型：** Array<string>

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-mimeType?: Array<string>--><!--Device-Filter-mimeType?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## suffix

```TypeScript
suffix?: Array<string>
```

文件后缀名完全匹配，各个关键词OR关系。

**类型：** Array<string>

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-suffix?: Array<string>--><!--Device-Filter-suffix?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

