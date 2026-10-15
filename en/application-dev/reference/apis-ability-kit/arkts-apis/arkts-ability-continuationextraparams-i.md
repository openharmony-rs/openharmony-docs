# ContinuationExtraParams

```TypeScript
export interface ContinuationExtraParams
```

The ContinuationExtraParams module provides the filter parameters required by the device selection module in the continuation management entry. These filter parameters can be used as an input parameter of [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md#startcontinuationdevicemanager1).

**Since:** 8

**Deprecated since:** 22

<!--Device-unnamed-export interface ContinuationExtraParams--><!--Device-unnamed-export interface ContinuationExtraParams-End-->

**System capability:** SystemCapability.Ability.DistributedAbilityManager

## authInfo

```TypeScript
authInfo?: Record<string, Object>
```

Authentication information.

**Type:** Record&lt;string, Object&gt;

**Since:** 8

**Deprecated since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ContinuationExtraParams-authInfo?: Record<string, Object>--><!--Device-ContinuationExtraParams-authInfo?: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.DistributedAbilityManager

## continuationMode

```TypeScript
continuationMode?: continuationManager.ContinuationMode
```

Continuation mode.

**Type:** [continuationManager.ContinuationMode](arkts-ability-continuationmanager-continuationmode-e.md)

**Since:** 8

**Deprecated since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ContinuationExtraParams-continuationMode?: continuationManager.ContinuationMode--><!--Device-ContinuationExtraParams-continuationMode?: continuationManager.ContinuationMode-End-->

**System capability:** SystemCapability.Ability.DistributedAbilityManager

## description

```TypeScript
description?: string
```

Device filtering description.

**Type:** string

**Since:** 8

**Deprecated since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ContinuationExtraParams-description?: string--><!--Device-ContinuationExtraParams-description?: string-End-->

**System capability:** SystemCapability.Ability.DistributedAbilityManager

## deviceType

```TypeScript
deviceType?: Array<string>
```

Device type.

**Type:** Array&lt;string&gt;

**Since:** 8

**Deprecated since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ContinuationExtraParams-deviceType?: Array<string>--><!--Device-ContinuationExtraParams-deviceType?: Array<string>-End-->

**System capability:** SystemCapability.Ability.DistributedAbilityManager

## filter

```TypeScript
filter?: any
```

Device filtering parameter.

**Type:** any

**Since:** 8

**Deprecated since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ContinuationExtraParams-filter?: any--><!--Device-ContinuationExtraParams-filter?: any-End-->

**System capability:** SystemCapability.Ability.DistributedAbilityManager

## targetBundle

```TypeScript
targetBundle?: string
```

Name of the target bundle.

**Type:** string

**Since:** 8

**Deprecated since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ContinuationExtraParams-targetBundle?: string--><!--Device-ContinuationExtraParams-targetBundle?: string-End-->

**System capability:** SystemCapability.Ability.DistributedAbilityManager
