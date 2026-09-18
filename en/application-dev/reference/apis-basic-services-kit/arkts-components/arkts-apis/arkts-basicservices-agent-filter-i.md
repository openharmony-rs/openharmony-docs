# Filter

Defines the filter criteria.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## action

```TypeScript
action?: Action
```

Task action.

- **UPLOAD**: Upload tasks.  
- **DOWNLOAD**: Download tasks.  
- If this parameter is not set, all tasks are queried.

**Type:** [Action](arkts-basicservices-agent-action-e.md)

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## after

```TypeScript
after?: number
```

Unix timestamp of the start time, in milliseconds. The default value is the invoking time minus 24 hours.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## before

```TypeScript
before?: number
```

Unix timestamp of the end time, in milliseconds. The default value is the invoking time.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## mode

```TypeScript
mode?: Mode
```

Task mode.

- **FOREGROUND**: foreground task.  
- **BACKGROUND**: background task.  
- If this parameter is not set, all tasks are queried.

**Type:** [Mode](arkts-basicservices-agent-mode-e.md)

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## state

```TypeScript
state?: State
```

Task state. If this parameter is not set, all tasks are queried.

**Type:** [State](arkts-basicservices-agent-state-e.md)

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent
