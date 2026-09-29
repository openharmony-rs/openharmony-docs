# EntryOptions

```TypeScript
declare interface EntryOptions
```

Page entry configuration options, used to configure parameters such as the route name, state storage, and shared storage when decorating a page with @Entry.

**Since:** 10

<!--Device-unnamed-declare interface EntryOptions--><!--Device-unnamed-declare interface EntryOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## routeName

```TypeScript
routeName? : string
```

Name of the page as a named route. When the page needs to be navigated to through a named route, set this parameter as the route name. If this parameter is not passed, the page is not registered as a named route page and cannot be accessed through named route navigation; it is loaded only as the default entry page.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-EntryOptions-routeName? : string--><!--Device-EntryOptions-routeName? : string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## storage

```TypeScript
storage? : LocalStorage
```

Page-level UI state storage. Pass this parameter when you need to create and manage UI state outside the page in advance, or when you need to bind an existing LocalStorage instance to this page for state sharing. If this parameter is not passed, the framework creates a new LocalStorage instance as the default value. When useSharedStorage is set to true and storage is assigned, the value of useSharedStorage takes precedence.

**Type:** [LocalStorage](../arkts-apis/arkts-arkui-localstorage-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-EntryOptions-storage? : LocalStorage--><!--Device-EntryOptions-storage? : LocalStorage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## useSharedStorage

```TypeScript
useSharedStorage? : boolean
```

Whether to use the LocalStorage instance passed in by loadContent. The default value is false. true: uses the shared LocalStorage instance (prerequisite: ensure that the loadContent API has passed in a LocalStorage instance; if not, a new LocalStorage instance is created). false: does not use the shared LocalStorage instance. When useSharedStorage is set to true and storage is assigned, the value of useSharedStorage takes precedence.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-EntryOptions-useSharedStorage? : boolean--><!--Device-EntryOptions-useSharedStorage? : boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
