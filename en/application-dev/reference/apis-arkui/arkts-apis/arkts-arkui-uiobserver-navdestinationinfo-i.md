# NavDestinationInfo

```TypeScript
export interface NavDestinationInfo
```

Provides information about the **NavDestination** component, returned by the system to developers.

**Since:** 11

<!--Device-uiObserver-export interface NavDestinationInfo--><!--Device-uiObserver-export interface NavDestinationInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## index

```TypeScript
index: number
```

Index of the **NavDestination** component in the navigation stack.

Value range: [0, +∞)

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationInfo-index: number--><!--Device-NavDestinationInfo-index: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: NavDestinationMode
```

Mode of the **NavDestination** component.

**Type:** [NavDestinationMode](../arkts-components/arkts-arkui-navdestination-comp-navdestinationmode-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-NavDestinationInfo-mode?: NavDestinationMode--><!--Device-NavDestinationInfo-mode?: NavDestinationMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: ResourceStr
```

Name of the **NavDestination** component.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationInfo-name: ResourceStr--><!--Device-NavDestinationInfo-name: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId: string
```

Unique ID of the **NavDestination** component.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationInfo-navDestinationId: string--><!--Device-NavDestinationInfo-navDestinationId: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## navigationId

```TypeScript
navigationId: ResourceStr
```

ID of the **Navigation** component that contains the target **NavDestination** component.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationInfo-navigationId: ResourceStr--><!--Device-NavDestinationInfo-navigationId: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## param

```TypeScript
param?: Object
```

Parameters of the **NavDestination** component.

**Type:** Object

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationInfo-param?: Object--><!--Device-NavDestinationInfo-param?: Object-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Size
```

Size of the **NavDestination** component, in vp.

**Type:** Size

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-NavDestinationInfo-size?: Size--><!--Device-NavDestinationInfo-size?: Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state: NavDestinationState
```

State of the **NavDestination** component.

**Type:** [NavDestinationState](arkts-arkui-uiobserver-navdestinationstate-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationInfo-state: NavDestinationState--><!--Device-NavDestinationInfo-state: NavDestinationState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId?: number
```

Unique ID of the **NavDestination** component.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-NavDestinationInfo-uniqueId?: number--><!--Device-NavDestinationInfo-uniqueId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
