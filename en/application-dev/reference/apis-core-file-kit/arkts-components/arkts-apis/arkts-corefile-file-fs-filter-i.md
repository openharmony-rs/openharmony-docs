# Filter

Defines the file filtering configuration used by **listFile()**.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## displayName

```TypeScript
displayName?: Array<string>
```

Locate files that fuzzy match the specified file names, which are of the OR relationship. Currently, only the wildcard * is supported.

**Type:** Array&lt;string&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

## excludeMedia

```TypeScript
excludeMedia?: boolean
```

Whether to exclude the files already in **Media**.

The value **true** means to exclude the files already in **Media**; the value **false** means not to exclude the files already in **Media**.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

## fileSizeOver

```TypeScript
fileSizeOver?: number
```

Locate files that are greater than the specified size, in bytes.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

## lastModifiedAfter

```TypeScript
lastModifiedAfter?: number
```

Locate files whose last modification time is the same or later than the specified time.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

## mimeType

```TypeScript
mimeType?: Array<string>
```

Locate files that fully match the specified MIME types, which are of the OR relationship. This parameter is reserved.

**Type:** Array&lt;string&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

## suffix

```TypeScript
suffix?: Array<string>
```

Locate files that fully match the specified file name extensions, which are of the OR relationship.

**Type:** Array&lt;string&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO
