# PersistPropsOptions

Defines a key-value pair object used to specify persistent properties and their default values, passed as a parameter to [persistProps](arkts-arkui-persistentstorage-c.md#persistprops).

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultValue

```TypeScript
defaultValue: number | string | boolean | Object
```

Default value used for initialization if the specified **key** is not found in PersistentStorage and AppStorage. Since API version 12, **defaultValue** can be set to **null** or **undefined**.

**Type:** number &#124; string &#124; boolean &#124; Object

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key: string
```

Property name.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
