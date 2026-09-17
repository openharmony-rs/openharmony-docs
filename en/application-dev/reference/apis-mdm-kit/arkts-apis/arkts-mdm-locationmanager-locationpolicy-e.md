# LocationPolicy

Enumerates the location service policies.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DEFAULT_LOCATION_SERVICE

```TypeScript
DEFAULT_LOCATION_SERVICE = 0
```

Default policy. The location service is not restricted and can be controlled by the user.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DISALLOW_LOCATION_SERVICE

```TypeScript
DISALLOW_LOCATION_SERVICE = 1
```

The location service is disabled. This policy applies to scenarios where the location service needs to be disabled, such as confidential areas and conference rooms.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## FORCE_OPEN_LOCATION_SERVICE

```TypeScript
FORCE_OPEN_LOCATION_SERVICE = 2
```

The location service is forcibly enabled. This policy applies to scenarios where the location service needs to be available, such as logistics tracking and field management.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
