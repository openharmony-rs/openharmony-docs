# ManagedEvent

Enumerates the system management events that can be subscribed to.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_BUNDLE_ADDED

```TypeScript
MANAGED_EVENT_BUNDLE_ADDED = 0
```

An application is installed.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_BUNDLE_REMOVED

```TypeScript
MANAGED_EVENT_BUNDLE_REMOVED = 1
```

An application is uninstalled.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_APP_START

```TypeScript
MANAGED_EVENT_APP_START = 2
```

An application is started.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_APP_STOP

```TypeScript
MANAGED_EVENT_APP_STOP = 3
```

An application is stopped.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_SYSTEM_UPDATE

```TypeScript
MANAGED_EVENT_SYSTEM_UPDATE = 4
```

The system is updated.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_ACCOUNT_ADDED

```TypeScript
MANAGED_EVENT_ACCOUNT_ADDED = 5
```

An account is created.

**Since:** 18

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_ACCOUNT_SWITCHED

```TypeScript
MANAGED_EVENT_ACCOUNT_SWITCHED = 6
```

An account is switched.

**Since:** 18

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_ACCOUNT_REMOVED

```TypeScript
MANAGED_EVENT_ACCOUNT_REMOVED = 7
```

An account is removed.

**Since:** 18

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_STARTUP_GUIDE_COMPLETED

```TypeScript
MANAGED_EVENT_STARTUP_GUIDE_COMPLETED = 8
```

The startup wizard is complete.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_BOOT_COMPLETED

```TypeScript
MANAGED_EVENT_BOOT_COMPLETED = 9
```

Device startup is complete.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_BUNDLE_UPDATED

```TypeScript
MANAGED_EVENT_BUNDLE_UPDATED = 10
```

Application update event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MANAGED_EVENT_POLICIES_CHANGED

```TypeScript
MANAGED_EVENT_POLICIES_CHANGED = 11
```

Policy change event. Only super device administrator applications can subscribe to this event. If other types of device administrator applications attempt to subscribe, error code 9200002 is returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
