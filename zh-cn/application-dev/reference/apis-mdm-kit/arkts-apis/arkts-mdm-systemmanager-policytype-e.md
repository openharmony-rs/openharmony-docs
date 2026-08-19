# PolicyType

升级策略类型枚举。

**起始版本：** 12

<!--Device-systemManager-enum PolicyType--><!--Device-systemManager-enum PolicyType-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认升级策略。周期提示用户，用户确认后升级。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolicyType-DEFAULT = 0--><!--Device-PolicyType-DEFAULT = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## PROHIBIT

```TypeScript
PROHIBIT = 1
```

禁止升级策略。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolicyType-PROHIBIT = 1--><!--Device-PolicyType-PROHIBIT = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## UPDATE_TO_SPECIFIC_VERSION

```TypeScript
UPDATE_TO_SPECIFIC_VERSION = 2
```

强制升级策略。需指定最晚升级时间（latestUpdateTime）参数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolicyType-UPDATE_TO_SPECIFIC_VERSION = 2--><!--Device-PolicyType-UPDATE_TO_SPECIFIC_VERSION = 2-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## WINDOWS

```TypeScript
WINDOWS = 3
```

指定时间窗口升级策略。需指定时间窗口参数（installStartTime、installEndTime）。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolicyType-WINDOWS = 3--><!--Device-PolicyType-WINDOWS = 3-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## POSTPONE

```TypeScript
POSTPONE = 4
```

延迟升级策略。延迟指定时间（delayUpdateTime）后进入DEFAULT模式，周期提示用户升级。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolicyType-POSTPONE = 4--><!--Device-PolicyType-POSTPONE = 4-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

