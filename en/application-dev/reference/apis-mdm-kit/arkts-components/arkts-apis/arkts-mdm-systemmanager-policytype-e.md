# PolicyType

```TypeScript
enum PolicyType
```

Enumerates the update policy types.

**Since:** 12

<!--Device-systemManager-enum PolicyType--><!--Device-systemManager-enum PolicyType-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default update policy, which periodically notifies the user of the update and starts the update after user confirmation.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PolicyType-DEFAULT = 0--><!--Device-PolicyType-DEFAULT = 0-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## PROHIBIT

```TypeScript
PROHIBIT = 1
```

Prohibit updates.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PolicyType-PROHIBIT = 1--><!--Device-PolicyType-PROHIBIT = 1-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## UPDATE_TO_SPECIFIC_VERSION

```TypeScript
UPDATE_TO_SPECIFIC_VERSION = 2
```

Enforce updates. In this case, **latestUpdateTime** must be specified.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PolicyType-UPDATE_TO_SPECIFIC_VERSION = 2--><!--Device-PolicyType-UPDATE_TO_SPECIFIC_VERSION = 2-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WINDOWS

```TypeScript
WINDOWS = 3
```

Update at the specified time window. In this case, **installStartTime** and **installEndTime** must be specified.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PolicyType-WINDOWS = 3--><!--Device-PolicyType-WINDOWS = 3-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## POSTPONE

```TypeScript
POSTPONE = 4
```

Postpone updates. After the time specified by **delayUpdateTime** is over, the default update policy is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PolicyType-POSTPONE = 4--><!--Device-PolicyType-POSTPONE = 4-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
