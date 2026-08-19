# RestoreParamType（系统接口）

Enumerates the types of the parameters used for prelaunch.

**起始版本：** 23

<!--Device-camera-enum RestoreParamType--><!--Device-camera-enum RestoreParamType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## NO_NEED_RESTORE_PARAM

```TypeScript
NO_NEED_RESTORE_PARAM = 0
```

The parameter used for prelaunch is not required.

**起始版本：** 23

<!--Device-RestoreParamType-NO_NEED_RESTORE_PARAM = 0--><!--Device-RestoreParamType-NO_NEED_RESTORE_PARAM = 0-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## PRESISTENT_DEFAULT_PARAM

```TypeScript
PRESISTENT_DEFAULT_PARAM = 1
```

Persistent parameter type. This parameter is used to restore stream information with the specified time point.

**起始版本：** 23

<!--Device-RestoreParamType-PRESISTENT_DEFAULT_PARAM = 1--><!--Device-RestoreParamType-PRESISTENT_DEFAULT_PARAM = 1-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## TRANSIENT_ACTIVE_PARAM

```TypeScript
TRANSIENT_ACTIVE_PARAM = 2
```

Temporary parameter type. This parameter is used to restore stream information only within a period of time after the camera application is closed. Its priority is higher than that of the persistent parameter.

**起始版本：** 23

<!--Device-RestoreParamType-TRANSIENT_ACTIVE_PARAM = 2--><!--Device-RestoreParamType-TRANSIENT_ACTIVE_PARAM = 2-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

