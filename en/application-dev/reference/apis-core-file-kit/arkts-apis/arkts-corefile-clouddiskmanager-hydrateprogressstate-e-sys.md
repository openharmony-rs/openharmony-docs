# HydrateProgressState (System API)

```TypeScript
enum HydrateProgressState
```

Enumerates the states of the hydrate progress.

**Since:** 26.0.1

<!--Device-cloudDiskManager-enum HydrateProgressState--><!--Device-cloudDiskManager-enum HydrateProgressState-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## CANCELLED

```TypeScript
CANCELLED = 3
```

The hydrate is cancelled by the user, a crash, or the application giving up.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-HydrateProgressState-CANCELLED = 3--><!--Device-HydrateProgressState-CANCELLED = 3-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## COMPLETED

```TypeScript
COMPLETED = 2
```

The hydrate is completed.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-HydrateProgressState-COMPLETED = 2--><!--Device-HydrateProgressState-COMPLETED = 2-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## IN_PROGRESS

```TypeScript
IN_PROGRESS = 1
```

The hydrate is in progress.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-HydrateProgressState-IN_PROGRESS = 1--><!--Device-HydrateProgressState-IN_PROGRESS = 1-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## PENDING

```TypeScript
PENDING = 0
```

The hydrate task has been created, but the FFRT worker has not been dispatched yet.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-HydrateProgressState-PENDING = 0--><!--Device-HydrateProgressState-PENDING = 0-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.
