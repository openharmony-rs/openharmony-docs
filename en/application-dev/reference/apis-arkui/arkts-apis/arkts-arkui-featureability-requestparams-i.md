# RequestParams

@typedef RequestParams

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## abilityName

```TypeScript
abilityName?: string
```

Ability name, which is case sensitive.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## action

```TypeScript
action?: string
```

Without specifying the bundle name and ability name, you can start the application according to other properties with action.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## bundleName

```TypeScript
bundleName?: string
```

The name of the bundle to start. It should be used with abilityname and case sensitive.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## data

```TypeScript
data?: object
```

Data sent to the ability which need to be serializable.

**Type:** object

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## deviceType

```TypeScript
deviceType?: number
```

If more than one FA meets the conditions, the user can select the device from the popup. 0: Default. Select the FA to start from the local and remote devices. 1: start FA from the local device.

**Type:** number

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## entities

```TypeScript
entities?: Array<string>
```

The list of entities to which the FA to be called. If it is not filled in, all entity lists will be found by default. It should be used with action.

**Type:** Array&lt;string&gt;

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## flag

```TypeScript
flag?: number
```

Configuration switch when start FA.

**Type:** number

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## url

```TypeScript
url?: string
```

Specify the url of the page which the FA to be called. Use home page directly by default.

**Type:** string

**Since:** 5

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
