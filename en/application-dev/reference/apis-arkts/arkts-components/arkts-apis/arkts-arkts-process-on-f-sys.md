# on (System API)

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## on

```TypeScript
function on(type: string, listener: EventListener): void
```

Register for an event

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Indicates the type of event registered. |
| listener | [EventListener](arkts-arkts-process-eventlistener-t.md) | Yes | Represents the registered event function |
