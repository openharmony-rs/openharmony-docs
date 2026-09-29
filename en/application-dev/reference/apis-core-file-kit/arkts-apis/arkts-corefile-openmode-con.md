# Constants

## APPEND

```TypeScript
const APPEND = 0o2000
```

Open the file in append mode. New data will be written to the end of the file.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-OpenMode-const APPEND = 0o2000--><!--Device-OpenMode-const APPEND = 0o2000-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## CREATE

```TypeScript
const CREATE = 0o100
```

Create a file if the specified file does not exist.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-OpenMode-const CREATE = 0o100--><!--Device-OpenMode-const CREATE = 0o100-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## DIR

```TypeScript
const DIR = 0o200000
```

If **path** does not point to a directory, throw an exception.

**Since:** 9

<!--Device-OpenMode-const DIR = 0o200000--><!--Device-OpenMode-const DIR = 0o200000-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## NOFOLLOW

```TypeScript
const NOFOLLOW = 0o400000
```

If **path** points to a symbolic link, throw an exception.

**Since:** 9

<!--Device-OpenMode-const NOFOLLOW = 0o400000--><!--Device-OpenMode-const NOFOLLOW = 0o400000-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## NONBLOCK

```TypeScript
const NONBLOCK = 0o4000
```

If **path** points to a named pipe (FIFO), block special file, or character special file, perform non-blocking operations on the open file and in subsequent I/Os.

**Since:** 9

<!--Device-OpenMode-const NONBLOCK = 0o4000--><!--Device-OpenMode-const NONBLOCK = 0o4000-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## READ_ONLY

```TypeScript
const READ_ONLY = 0o0
```

Open the file in read-only mode.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-OpenMode-const READ_ONLY = 0o0--><!--Device-OpenMode-const READ_ONLY = 0o0-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## READ_WRITE

```TypeScript
const READ_WRITE = 0o2
```

Open the file in read/write mode.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-OpenMode-const READ_WRITE = 0o2--><!--Device-OpenMode-const READ_WRITE = 0o2-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## SYNC

```TypeScript
const SYNC = 0o4010000
```

Open the file in synchronous I/O mode.

**Since:** 9

<!--Device-OpenMode-const SYNC = 0o4010000--><!--Device-OpenMode-const SYNC = 0o4010000-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## TRUNC

```TypeScript
const TRUNC = 0o1000
```

If the file exists and is opened in write-only or read/write mode, truncate the file length to 0.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-OpenMode-const TRUNC = 0o1000--><!--Device-OpenMode-const TRUNC = 0o1000-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## UNCACHE

```TypeScript
const UNCACHE = 0o10000000000
```

UNCACHE IO.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OpenMode-const UNCACHE = 0o10000000000--><!--Device-OpenMode-const UNCACHE = 0o10000000000-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## WRITE_ONLY

```TypeScript
const WRITE_ONLY = 0o1
```

Open the file in write-only mode.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-OpenMode-const WRITE_ONLY = 0o1--><!--Device-OpenMode-const WRITE_ONLY = 0o1-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO
