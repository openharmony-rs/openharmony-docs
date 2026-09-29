# DisposedRule (System API)

```TypeScript
export interface DisposedRule
```

Defines a disposed rule.

**Since:** 11

<!--Device-appControl-export interface DisposedRule--><!--Device-appControl-export interface DisposedRule-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## componentType

```TypeScript
componentType: ComponentType
```

Type of application component that functions as the displayed page.

**Type:** [ComponentType](arkts-ability-appcontrol-componenttype-e-sys.md)

**Since:** 11

<!--Device-DisposedRule-componentType: ComponentType--><!--Device-DisposedRule-componentType: ComponentType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## controlType

```TypeScript
controlType: ControlType
```

Control type of application disposal.

**Type:** [ControlType](arkts-ability-appcontrol-controltype-e-sys.md)

**Since:** 11

<!--Device-DisposedRule-controlType: ControlType--><!--Device-DisposedRule-controlType: ControlType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## disposedType

```TypeScript
disposedType: DisposedType
```

Type of application disposal.

**Type:** [DisposedType](arkts-ability-appcontrol-disposedtype-e-sys.md)

**Since:** 11

<!--Device-DisposedRule-disposedType: DisposedType--><!--Device-DisposedRule-disposedType: DisposedType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## elementList

```TypeScript
elementList: Array<ElementName>
```

List of application components to be disposed of or exempted.

**Type:** Array&lt;[ElementName](arkts-ability-elementname-i.md)&gt;

**Since:** 11

<!--Device-DisposedRule-elementList: Array<ElementName>--><!--Device-DisposedRule-elementList: Array<ElementName>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## pageJump

```TypeScript
pageJump?: PageJumpMode
```

Specifies whether to jump to another page when the target application is blocked. The default value is [PAGE_JUMP_WINDOW_SHOW](arkts-ability-appcontrol-pagejumpmode-e-sys.md#page_jump_window_show).

**Type:** [PageJumpMode](arkts-ability-appcontrol-pagejumpmode-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DisposedRule-pageJump?: PageJumpMode--><!--Device-DisposedRule-pageJump?: PageJumpMode-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## priority

```TypeScript
priority: number
```

Priority of the disposed rule, which is used to sort the query results of the rule list. The value is an integer. A smaller value indicates a higher priority.

**Type:** number

**Since:** 11

<!--Device-DisposedRule-priority: int--><!--Device-DisposedRule-priority: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## want

```TypeScript
want: Want
```

Page displayed when the application is disposed of.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 11

<!--Device-DisposedRule-want: Want--><!--Device-DisposedRule-want: Want-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.
