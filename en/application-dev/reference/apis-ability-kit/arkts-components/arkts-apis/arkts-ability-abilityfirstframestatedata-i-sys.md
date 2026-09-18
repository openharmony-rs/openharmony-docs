# AbilityFirstFrameStateData (System API)

The module defines the struct reported by the callback when the first frame of an ability is rendered. After registering the first frame rendering completion event of an ability by using [on](arkts-ability-appmanager-on-f-sys.md#onabilityfirstframestate), you can obtain the reported struct through the [onAbilityFirstFrameDrawn](arkts-ability-abilityfirstframestateobserver-i-sys.md#onabilityfirstframedrawn) callback of [AbilityFirstFrameStateObserver](arkts-ability-abilityfirstframestateobserver-i-sys.md).

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## abilityName

```TypeScript
abilityName: string
```

The ability name.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## appIndex

```TypeScript
appIndex: number
```

The index of DLP sandbox.

**Type:** number

**Default:** 0

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

The bundle name.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## isColdStart

```TypeScript
isColdStart: boolean
```

The entry ability of application is cold-start return true, others false.

**Type:** boolean

**Default:** false

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## moduleName

```TypeScript
moduleName: string
```

The module name.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
