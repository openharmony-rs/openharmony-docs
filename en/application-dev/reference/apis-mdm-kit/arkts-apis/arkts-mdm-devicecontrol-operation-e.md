# Operation

Defines the device operation.

**Since:** 26.0.0

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DISK_ERASURE

```TypeScript
DISK_ERASURE = 0
```

Disk erasure. After this API is called, the device immediately performs a disk erasure operation. Once completed, all data on the device will be erased and cannot be recovered. To protect against data loss caused by potential application attacks, enterprises should implement robust security measures for their applications. It is support only on PCs/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## RESET_FACTORY

```TypeScript
RESET_FACTORY = 1
```

Restore device factory settings..

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## REBOOT

```TypeScript
REBOOT = 2
```

Restart devices.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SHUT_DOWN

```TypeScript
SHUT_DOWN = 3
```

Shut down devices.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## LOCK_SCREEN

```TypeScript
LOCK_SCREEN = 4
```

Lock device screens.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## LOCK_DEVICE

```TypeScript
LOCK_DEVICE = 5
```

Lock devices.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## UNLOCK_DEVICE

```TypeScript
UNLOCK_DEVICE = 6
```

Unlock devices.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
