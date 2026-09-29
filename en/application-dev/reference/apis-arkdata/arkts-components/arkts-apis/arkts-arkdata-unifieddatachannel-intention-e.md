# Intention

```TypeScript
enum Intention
```

Enumerates the data channel types supported by the UDMF. It is used to identify different service scenarios, to which the UDMF data channels apply.

**Since:** 10

<!--Device-unifiedDataChannel-enum Intention--><!--Device-unifiedDataChannel-enum Intention-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DATA_HUB

```TypeScript
DATA_HUB = 'DataHub'
```

Public data channel.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Intention-DATA_HUB = 'DataHub'--><!--Device-Intention-DATA_HUB = 'DataHub'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DRAG

```TypeScript
DRAG = 'Drag'
```

Channel in which data can be dragged and dropped.

**Use scenario**: This API is used to share data across applications in drag-and-drop scenarios.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-Intention-DRAG = 'Drag'--><!--Device-Intention-DRAG = 'Drag'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SYSTEM_SHARE

```TypeScript
SYSTEM_SHARE = 'SystemShare'
```

Data channel of the system sharing type.

**Use scenario**: This API is used to share data across applications in system sharing scenarios.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-Intention-SYSTEM_SHARE = 'SystemShare'--><!--Device-Intention-SYSTEM_SHARE = 'SystemShare'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PICKER

```TypeScript
PICKER = 'Picker'
```

Data channel of the picker type.

**Use scenario**: This API is used to share data across applications in the scenarios where a picker is used.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-Intention-PICKER = 'Picker'--><!--Device-Intention-PICKER = 'Picker'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MENU

```TypeScript
MENU = 'Menu'
```

Data channel of the menu type.

**Use scenario**: This API is used to share data across applications in the shortcut menu.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-Intention-MENU = 'Menu'--><!--Device-Intention-MENU = 'Menu'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
