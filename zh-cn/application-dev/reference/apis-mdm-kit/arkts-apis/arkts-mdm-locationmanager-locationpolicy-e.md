# LocationPolicy

位置服务策略值。

**起始版本：** 12

<!--Device-locationManager-export enum LocationPolicy--><!--Device-locationManager-export enum LocationPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DEFAULT_LOCATION_SERVICE

```TypeScript
DEFAULT_LOCATION_SERVICE = 0
```

默认策略，不限制位置服务开关，允许用户自行控制。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocationPolicy-DEFAULT_LOCATION_SERVICE = 0--><!--Device-LocationPolicy-DEFAULT_LOCATION_SERVICE = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DISALLOW_LOCATION_SERVICE

```TypeScript
DISALLOW_LOCATION_SERVICE = 1
```

禁用位置服务策略。适用于涉密区域、保密会议室等需要禁止位置服务的场景。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocationPolicy-DISALLOW_LOCATION_SERVICE = 1--><!--Device-LocationPolicy-DISALLOW_LOCATION_SERVICE = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## FORCE_OPEN_LOCATION_SERVICE

```TypeScript
FORCE_OPEN_LOCATION_SERVICE = 2
```

强制开启位置服务策略。适用于物流追踪、外勤管理等需要确保位置服务可用的场景。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocationPolicy-FORCE_OPEN_LOCATION_SERVICE = 2--><!--Device-LocationPolicy-FORCE_OPEN_LOCATION_SERVICE = 2-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

