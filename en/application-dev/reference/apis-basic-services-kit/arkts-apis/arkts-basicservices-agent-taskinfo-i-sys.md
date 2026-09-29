# TaskInfo

```TypeScript
interface TaskInfo
```

Defines the data structure of the task information for query. The fields available vary depending on the query type.

**Since:** 10

<!--Device-agent-interface TaskInfo--><!--Device-agent-interface TaskInfo-End-->

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

<!--Device-TaskInfo-readonly bundle?: string--><!--Device-TaskInfo-readonly bundle?: string-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

**System API:** This is a system API.

## uid

```TypeScript
readonly uid?: string
```

The UID of an application. For system query only.

**Type:** string

**Since:** 10

<!--Device-TaskInfo-readonly uid?: string--><!--Device-TaskInfo-readonly uid?: string-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

**System API:** This is a system API.
