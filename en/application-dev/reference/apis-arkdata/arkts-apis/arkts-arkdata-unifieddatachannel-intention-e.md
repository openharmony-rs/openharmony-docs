# Intention

```TypeScript
enum Intention
```

Enumerates the data channels supported by UDMF. It is mainly used to identify the different business scenarios targeted by various UDMF data channels.

**Since:** 10

<!--Device-unifiedDataChannel-enum Intention--><!--Device-unifiedDataChannel-enum Intention-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DATA_HUB

```TypeScript
DATA_HUB = 'DataHub'
```

Public data channel.

**Applicable scenario:** Suitable for cross-application data sharing using UDMF in public data sharing scenarios.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Intention-DATA_HUB = 'DataHub'--><!--Device-Intention-DATA_HUB = 'DataHub'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DRAG

```TypeScript
DRAG = 'Drag'
```

Drag-and-drop data channel.

**Applicable scenario:** Suitable for cross-application data sharing using UDMF in drag-and-drop scenarios.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-Intention-DRAG = 'Drag'--><!--Device-Intention-DRAG = 'Drag'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MENU

```TypeScript
MENU = 'Menu'
```

Menu data channel.

**Applicable scenario:** Suitable for cross-application data sharing using UDMF in right-click menu scenarios.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-Intention-MENU = 'Menu'--><!--Device-Intention-MENU = 'Menu'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PICKER

```TypeScript
PICKER = 'Picker'
```

Picker data channel.

**Applicable scenario:** Suitable for cross-application data sharing using UDMF in picker scenarios.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-Intention-PICKER = 'Picker'--><!--Device-Intention-PICKER = 'Picker'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SYSTEM_SHARE

```TypeScript
SYSTEM_SHARE = 'SystemShare'
```

System sharing data channel.

**Applicable scenario:** Suitable for cross-application data sharing using UDMF in system sharing scenarios.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-Intention-SYSTEM_SHARE = 'SystemShare'--><!--Device-Intention-SYSTEM_SHARE = 'SystemShare'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
