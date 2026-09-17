# TaskInfo

Defines the data structure of the task information for query. The fields available vary depending on the query type.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## bundle

```TypeScript
readonly bundle?: string
```

The bundle name. For system query only.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

**System API:** This is a system API.

## uid

```TypeScript
readonly uid?: string
```

The UID of an application. For system query only.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

**System API:** This is a system API.
