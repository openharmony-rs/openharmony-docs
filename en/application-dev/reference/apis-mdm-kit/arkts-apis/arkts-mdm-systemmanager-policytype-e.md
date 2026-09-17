# PolicyType

Enumerates the update policy types.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default update policy, which periodically notifies the user of the update and starts the update after user confirmation.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## PROHIBIT

```TypeScript
PROHIBIT = 1
```

Prohibit updates.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## UPDATE_TO_SPECIFIC_VERSION

```TypeScript
UPDATE_TO_SPECIFIC_VERSION = 2
```

Enforce updates. In this case, **latestUpdateTime** must be specified.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WINDOWS

```TypeScript
WINDOWS = 3
```

Update at the specified time window. In this case, **installStartTime** and **installEndTime** must be specified.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## POSTPONE

```TypeScript
POSTPONE = 4
```

Postpone updates. After the time specified by **delayUpdateTime** is over, the default update policy is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
