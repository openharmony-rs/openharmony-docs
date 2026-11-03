# RestoreParamType（系统接口）

```TypeScript
enum RestoreParamType
```

枚举，预启动使用的参数类型。

**起始版本：** 11

<!--Device-camera-enum RestoreParamType--><!--Device-camera-enum RestoreParamType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## NO_NEED_RESTORE_PARAM

```TypeScript
NO_NEED_RESTORE_PARAM = 0
```

无需预启动参数。

**起始版本：** 11

<!--Device-RestoreParamType-NO_NEED_RESTORE_PARAM = 0--><!--Device-RestoreParamType-NO_NEED_RESTORE_PARAM = 0-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## PRESISTENT_DEFAULT_PARAM

```TypeScript
PRESISTENT_DEFAULT_PARAM = 1
```

持久化参数类型。该参数用于按指定时间点恢复流信息。

**起始版本：** 11

<!--Device-RestoreParamType-PRESISTENT_DEFAULT_PARAM = 1--><!--Device-RestoreParamType-PRESISTENT_DEFAULT_PARAM = 1-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## TRANSIENT_ACTIVE_PARAM

```TypeScript
TRANSIENT_ACTIVE_PARAM = 2
```

临时参数类型。该参数仅用于在相机应用关闭后的一段时间内恢复流信息。其优先级高于持久化参数。

**起始版本：** 11

<!--Device-RestoreParamType-TRANSIENT_ACTIVE_PARAM = 2--><!--Device-RestoreParamType-TRANSIENT_ACTIVE_PARAM = 2-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
