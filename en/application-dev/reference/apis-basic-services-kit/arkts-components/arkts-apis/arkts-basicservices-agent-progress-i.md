# Progress

Describes the data structure of the task progress.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## extras

```TypeScript
readonly extras?: object
```

Extra information of the task, for example, the header and body of the response from the server. The default value is empty.

**Type:** object

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## index

```TypeScript
readonly index: number
```

Index of the file that is being processed in the task.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## processed

```TypeScript
readonly processed: number
```

Size of processed data in the current file in the task, in bytes.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## sizes

```TypeScript
readonly sizes: Array<number>
```

Size of a file in a task, in bytes. If the server uses the chunk mode for data transmission and the total file size cannot be obtained from the request header, the value of **sizes** is treated as **-1**.

**Type:** Array&lt;number&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## state

```TypeScript
readonly state: State
```

Current task status.

**Type:** [State](arkts-basicservices-agent-state-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent
