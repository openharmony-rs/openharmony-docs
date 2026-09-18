# CallAbilityParam

@typedef CallAbilityParam

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## abilityName

```TypeScript
abilityName: string
```

Ability name, which is case sensitive and must be the same as that on the AA side.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## abilityType

```TypeScript
abilityType: number
```

Ability type. Different types of abilities have different implementation on the AA side. 0: Ability, which has an independent lifecycle. The FA starts and requests an AA through an RPC. Such type of abilities are used to provide basic services for multiple FAs to call or are used when the abilities should run in the background. 1: Internal ability, which shares the same process with the FA and communicates with it by calling internal functions. Such type of abilities are used in scenarios that require low response latency and cannot be called by other FAs.

**Type:** number

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## bundleName

```TypeScript
bundleName: string
```

Name of the bundle where the ability has been located. The name is case sensitive and must be the same as that on the AA side.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## data

```TypeScript
data?: object
```

Data sent to the ability. The data to carry differs depending on the service to be processed and its field name must be consistent with the AA side.

**Type:** object

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## messageCode

```TypeScript
messageCode: number
```

Ability operation code, which defines the service function of an AA and must be consistent with the AA side.

**Type:** number

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## syncOption

```TypeScript
syncOption?: number
```

Whether the request is synchronous or asynchronous. The synchronous mode is used by default. Currently, the asynchronous mode is available only for internal abilities. 0: Synchronous mode (default value) 1: Asynchronous mode

**Type:** number

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
