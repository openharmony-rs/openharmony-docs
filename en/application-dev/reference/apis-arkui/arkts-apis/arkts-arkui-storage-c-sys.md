# Storage (System API)

```TypeScript
declare class Storage
```

Defines the base class of storage.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## clear

```TypeScript
clear(): void
```

Called when data is cleared.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## constructor

```TypeScript
constructor(needCrossThread?: boolean, file?: string)
```

Constructor parameters.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| needCrossThread | boolean | No |  |
| file | string | No |  |

## delete

```TypeScript
delete(key: string): void
```

Called when data is deleted.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes |  |

## get

```TypeScript
get(key: string): string | undefined
```

Called when data is obtained.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; undefined |  |

## set

```TypeScript
set(key: string, val: any): void
```

Called when setting.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes |  |
| val | any | Yes |  |
