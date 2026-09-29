# NavDestinationSwitchInfo

```TypeScript
export interface NavDestinationSwitchInfo
```

Provides the information about page switching of the **Navigation** component.

**Since:** 12

<!--Device-uiObserver-export interface NavDestinationSwitchInfo--><!--Device-uiObserver-export interface NavDestinationSwitchInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## context

```TypeScript
context: UIAbilityContext | UIContext
```

Context information corresponding to **Navigation** component that triggers page switching.

**Type:** [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) &#124; UIContext

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationSwitchInfo-context: UIAbilityContext | UIContext--><!--Device-NavDestinationSwitchInfo-context: UIAbilityContext | UIContext-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from: NavDestinationInfo | NavBar
```

Source page for page switching.

**Type:** [NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md) &#124; NavBar

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationSwitchInfo-from: NavDestinationInfo | NavBar--><!--Device-NavDestinationSwitchInfo-from: NavDestinationInfo | NavBar-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operation

```TypeScript
operation: NavigationOperation
```

Page switching operation type.

**Type:** NavigationOperation

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationSwitchInfo-operation: NavigationOperation--><!--Device-NavDestinationSwitchInfo-operation: NavigationOperation-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: NavDestinationInfo | NavBar
```

Destination page for page switching.

**Type:** [NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md) &#124; NavBar

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavDestinationSwitchInfo-to: NavDestinationInfo | NavBar--><!--Device-NavDestinationSwitchInfo-to: NavDestinationInfo | NavBar-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
