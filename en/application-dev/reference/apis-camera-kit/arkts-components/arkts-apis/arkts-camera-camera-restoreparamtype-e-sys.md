# RestoreParamType (System API)

Enumerates the types of the parameters used for prelaunch.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## NO_NEED_RESTORE_PARAM

```TypeScript
NO_NEED_RESTORE_PARAM = 0
```

The parameter used for prelaunch is not required.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## PRESISTENT_DEFAULT_PARAM

```TypeScript
PRESISTENT_DEFAULT_PARAM = 1
```

Persistent parameter type. This parameter is used to restore stream information with the specified time point.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## TRANSIENT_ACTIVE_PARAM

```TypeScript
TRANSIENT_ACTIVE_PARAM = 2
```

Temporary parameter type. This parameter is used to restore stream information only within a period of time after the camera application is closed. Its priority is higher than that of the persistent parameter.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
