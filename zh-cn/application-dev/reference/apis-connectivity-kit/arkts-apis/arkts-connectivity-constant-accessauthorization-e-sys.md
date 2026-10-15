# AccessAuthorization（系统接口）

```TypeScript
export enum AccessAuthorization
```

枚举，蓝牙访问授权状态。表示对端蓝牙设备访问本端蓝牙Profile（如电话簿、消息等）的授权状态，用于蓝牙数据访问授权场景。

**起始版本：** 11

<!--Device-constant-export enum AccessAuthorization--><!--Device-constant-export enum AccessAuthorization-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## ALLOWED

```TypeScript
ALLOWED = 1
```

允许。

**起始版本：** 11

<!--Device-AccessAuthorization-ALLOWED = 1--><!--Device-AccessAuthorization-ALLOWED = 1-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## REJECTED

```TypeScript
REJECTED = 2
```

拒绝。

**起始版本：** 11

<!--Device-AccessAuthorization-REJECTED = 2--><!--Device-AccessAuthorization-REJECTED = 2-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

未知。

**起始版本：** 11

<!--Device-AccessAuthorization-UNKNOWN = 0--><!--Device-AccessAuthorization-UNKNOWN = 0-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
