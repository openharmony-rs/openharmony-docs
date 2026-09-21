# EntryOptions

```TypeScript
declare interface EntryOptions
```

Defines the options of Entry ClassDecorator.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## routeName

```TypeScript
routeName? : string
```

Named route name.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## storage

```TypeScript
storage? : LocalStorage
```

LocalStorage to be passed.

**Type:** [LocalStorage](../arkts-apis/arkts-arkui-localstorage-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## useSharedStorage

```TypeScript
useSharedStorage? : boolean
```

Determines whether to use the LocalStorage instance object returned by the LocalStorage.getShared() interface.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
