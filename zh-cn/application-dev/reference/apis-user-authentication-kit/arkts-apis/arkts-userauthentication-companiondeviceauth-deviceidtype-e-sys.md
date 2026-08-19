# DeviceIdType（系统接口）

设备ID类型枚举。用于定义设备业务标识的类型，支持系统预设类型和厂商自定义扩展类型。

**起始版本：** 23

<!--Device-companionDeviceAuth-enum DeviceIdType--><!--Device-companionDeviceAuth-enum DeviceIdType-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## UNIFIED_DEVICE_ID

```TypeScript
UNIFIED_DEVICE_ID = 1
```

统一设备ID。系统预设的设备业务标识类型，用于跨设备的统一设备识别。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceIdType-UNIFIED_DEVICE_ID = 1--><!--Device-DeviceIdType-UNIFIED_DEVICE_ID = 1-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## VENDOR_BEGIN

```TypeScript
VENDOR_BEGIN = 10000
```

厂商自定义设备ID类型取值起点。厂商可在此值基础上自定义扩展设备ID类型，实际取值需大于等于10000，避免与系统保留值[1-9999]冲突。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceIdType-VENDOR_BEGIN = 10000--><!--Device-DeviceIdType-VENDOR_BEGIN = 10000-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

