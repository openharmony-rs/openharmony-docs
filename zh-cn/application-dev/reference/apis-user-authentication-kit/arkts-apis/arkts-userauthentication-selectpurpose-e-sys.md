# SelectPurpose（系统接口）

选择伴随设备的目的。

**起始版本：** 23

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## SELECT_ADD_DEVICE

```TypeScript
SELECT_ADD_DEVICE = 1
```

选择添加模板的伴随设备。表示当前操作目的是选择一个设备用于添加新的认证模板，系统应返回适合添加模板的设备列表。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## SELECT_AUTH_DEVICE

```TypeScript
SELECT_AUTH_DEVICE = 2
```

选择提供认证能力的伴随设备。表示当前操作目的是选择一个已注册模板的设备用于执行身份认证，系统应返回具备认证能力的设备列表。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## VENDOR_BEGIN

```TypeScript
VENDOR_BEGIN = 10000
```

厂商自定义选择目的取值起点。厂商可在此值基础上自定义扩展选择目的，实际取值需大于等于10000，避免与系统保留值[0-9999]冲突。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

