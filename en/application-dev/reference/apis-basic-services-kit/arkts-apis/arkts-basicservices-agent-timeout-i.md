# Timeout

Defines the timeout configuration of a task. The task waiting duration is not counted. For details about the waiting reasons, see [WaitingReason&lt;sup&gt;20+&lt;/sup&gt;](arkts-basicservices-agent-waitingreason-e.md).

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## connectionTimeout

```TypeScript
connectionTimeout?: number
```

Task connection timeout interval, in seconds. The connection timeout interval indicates the maximum time required for establishing a connection between the client and server. If this parameter is not set, the default value **60** is used. The minimum value is **1**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## totalTimeout

```TypeScript
totalTimeout?: number
```

Total timeout interval of a task, in seconds. The total timeout interval includes the time required for establishing a connection, sending a request, and receiving a response. If this parameter is not set, the default value **604800** is used. The minimum value is **1**, and the maximum value is **604800** (that is, one week).

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent
