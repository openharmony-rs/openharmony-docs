# SendMessageOptions

@typedef SendMessageOptions

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## complete

```TypeScript
complete?: () => void
```

Called when the execution is completed.

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when the messages fail to be sent.

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: () => void
```

Called when the messages are sent successfully.

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## abilityName

```TypeScript
abilityName: string
```

Destination ability name, which is case sensitive.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## bundleName

```TypeScript
bundleName: string
```

Name of the destination bundle where the ability has been located. The name is case sensitive.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## deviceId

```TypeScript
deviceId: string
```

Destination device ID.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## message

```TypeScript
message?: string
```

Messages sent to the destination device. A maximum of 1 KB of data can be transmitted at a time. If more than 1 KB of data needs to be transmitted, split the messages into multiple parts to transmit.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
