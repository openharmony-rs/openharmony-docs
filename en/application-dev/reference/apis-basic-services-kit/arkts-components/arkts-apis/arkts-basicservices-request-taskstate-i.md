# TaskState

Upload task information, which is the callback parameter of the on('complete' | 'fail') and off('complete' | 'fail') APIs.

**Since:** 9

**System capability:** SystemCapability.MiscServices.Upload

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## message

```TypeScript
message: string
```

Description of the upload task result.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.MiscServices.Upload

## path

```TypeScript
path: string
```

File path.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.MiscServices.Upload

## responseCode

```TypeScript
responseCode: number
```

Return value of an upload task. The value **0** means that the task is successful, and other values means that the task fails. For details about the task result, see **message**.

You are advised to create an upload task by using [request.agent.create](arkts-basicservices-agent-create-f.md)and handle exceptions based on standard error codes.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Upload
