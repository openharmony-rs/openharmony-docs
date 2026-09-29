# RouterPageInfo

```TypeScript
export class RouterPageInfo
```

Provides the information contained in **RouterPageInfo**, returned by the system to developers.

**Since:** 11

<!--Device-uiObserver-export class RouterPageInfo--><!--Device-uiObserver-export class RouterPageInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## context

```TypeScript
context: UIAbilityContext | UIContext
```

Context of the router page that invokes the lifecycle callback.

**Type:** [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) &#124; UIContext

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RouterPageInfo-context: UIAbilityContext | UIContext--><!--Device-RouterPageInfo-context: UIAbilityContext | UIContext-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Position of the router page that invokes the lifecycle callback, in the navigation stack.

Value range: [0, +∞)

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RouterPageInfo-index: number--><!--Device-RouterPageInfo-index: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

Name of the page that invokes the lifecycle callback.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RouterPageInfo-name: string--><!--Device-RouterPageInfo-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pageId

```TypeScript
pageId: string
```

Unique ID of the router page that invokes the lifecycle callback.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RouterPageInfo-pageId: string--><!--Device-RouterPageInfo-pageId: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

Path of the page that invokes the lifecycle callback.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RouterPageInfo-path: string--><!--Device-RouterPageInfo-path: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Size
```

Size of the router page, in vp.

**Type:** Size

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-RouterPageInfo-size?: Size--><!--Device-RouterPageInfo-size?: Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state: RouterPageState
```

State of the router page that invokes the lifecycle callback.

**Type:** [RouterPageState](arkts-arkui-uiobserver-routerpagestate-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RouterPageInfo-state: RouterPageState--><!--Device-RouterPageInfo-state: RouterPageState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
