# Accessibility

枚举，关键资产基于锁屏状态的访问控制类型。

**起始版本：** 11

<!--Device-asset-enum Accessibility--><!--Device-asset-enum Accessibility-End-->

**系统能力：** SystemCapability.Security.Asset

## DEVICE_POWERED_ON

```TypeScript
DEVICE_POWERED_ON = 0
```

开机后可访问。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Accessibility-DEVICE_POWERED_ON = 0--><!--Device-Accessibility-DEVICE_POWERED_ON = 0-End-->

**系统能力：** SystemCapability.Security.Asset

## DEVICE_FIRST_UNLOCKED

```TypeScript
DEVICE_FIRST_UNLOCKED = 1
```

首次解锁后可访问

**说明：** 未设置锁屏密码时，等同于开机后可访问。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Accessibility-DEVICE_FIRST_UNLOCKED = 1--><!--Device-Accessibility-DEVICE_FIRST_UNLOCKED = 1-End-->

**系统能力：** SystemCapability.Security.Asset

## DEVICE_UNLOCKED

```TypeScript
DEVICE_UNLOCKED = 2
```

解锁状态时可访问

**说明：** 未设置锁屏密码时，等同于开机后可访问。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Accessibility-DEVICE_UNLOCKED = 2--><!--Device-Accessibility-DEVICE_UNLOCKED = 2-End-->

**系统能力：** SystemCapability.Security.Asset

