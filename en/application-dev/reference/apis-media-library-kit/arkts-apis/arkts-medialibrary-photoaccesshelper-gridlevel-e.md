# GridLevel

```TypeScript
export enum GridLevel
```

Enumerates the levels of grid columns after Picker is started.

**Since:** 23

<!--Device-photoAccessHelper-export enum GridLevel--><!--Device-photoAccessHelper-export enum GridLevel-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SPACIOUS

```TypeScript
SPACIOUS = 0
```

Spacious grid level. This level is the number of standard grid columns minus 1.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-GridLevel-SPACIOUS = 0--><!--Device-GridLevel-SPACIOUS = 0-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## STANDARD

```TypeScript
STANDARD = 1
```

Standard grid level. The number of standard grid columns varies with the device size. If no number of standard grid columns is configured, the system uses the default number of columns.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-GridLevel-STANDARD = 1--><!--Device-GridLevel-STANDARD = 1-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## COMPACT

```TypeScript
COMPACT = 2
```

Compact grid level. This level is the number of standard grid columns plus 1.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-GridLevel-COMPACT = 2--><!--Device-GridLevel-COMPACT = 2-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
