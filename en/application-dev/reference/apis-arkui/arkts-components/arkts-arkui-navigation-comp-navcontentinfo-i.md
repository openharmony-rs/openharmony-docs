# NavContentInfo

```TypeScript
declare interface NavContentInfo
```

Provides the destination information.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the navigation destination in the routing stack. If the view is a root view (**NavBar**), the return value is **-1**.

Value range: [-1, +��)

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: NavDestinationMode
```

Mode of the navigation destination. If the view is a root view (**NavBar**), the return value is **undefined**.

**Type:** [NavDestinationMode](arkts-arkui-navdestination-comp-navdestinationmode-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name?: string
```

Name of the navigation destination. If the view is a root view (**NavBar**), the return value is **undefined**.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId?: string
```

Unique identifier of the navigation destination page.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## param

```TypeScript
param?: Object
```

Parameters loaded on the navigation destination page.

**Type:** Object

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
