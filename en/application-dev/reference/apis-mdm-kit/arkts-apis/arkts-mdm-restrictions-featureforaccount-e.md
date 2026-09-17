# FeatureForAccount

Enumerates the features that can be disabled or enabled for a specified user.

**Since:** 26.0.0

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MULTI_WINDOW

```TypeScript
MULTI_WINDOW = 0
```

System multi-window. Currently, this feature is available only on phones and tablets. Once disabled, the system multi-window feature (split-screen, one-click split-screen, Multi-Window, and floating window) cannot be used. If the feature is currently active, the current usage remains unaffected. However, it cannot be used once closed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DISTRIBUTED_TRANSMISSION

```TypeScript
DISTRIBUTED_TRANSMISSION = 1
```

[Distributed management service](../../../distributedservice/distributedservice-kit-intro.md#working-principles). Once disabled, functions such as discovery, authentication, query, and listening in the distributed device management service cannot be used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SUPER_HUB

```TypeScript
SUPER_HUB = 2
```

SuperHub. Currently, this feature is available only on phones and tablets. Once disabled, the SuperHub feature cannot be used. If SuperHub is currently active, the current usage remains unaffected. However, it cannot be used once closed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## FINGERPRINT

```TypeScript
FINGERPRINT = 3
```

Device fingerprint authentication capability. Currently, this feature is supported only on PCs/2-in-1 devices. The rules for using this capability are as follows:

1. After the device fingerprint authentication capability ([FeatureForDevice.FINGERPRINT](arkts-mdm-restrictions-featurefordevice-e.md))
is disabled, disabling this capability for a specific user will result in a policy conflict.
2. After the device fingerprint authentication capability is disabled or enabled for a specific user, disabling
this capability ([FeatureForDevice.FINGERPRINT](arkts-mdm-restrictions-featurefordevice-e.md)) globally will override the user-specific policy. Subsequently, re-enabling this capability ([FeatureForDevice.FINGERPRINT](arkts-mdm-restrictions-featurefordevice-e.md)) globally will allow all users to use device fingerprint authentication.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## PRINT

```TypeScript
PRINT = 4
```

Device printing capability. If the device printing capability is disabled for a specific user, it remains disabled for that user even if the device printing capability ([FeatureForDevice.PRINTER](arkts-mdm-restrictions-featurefordevice-e.md)) capability is enabled globally.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MTP_CLIENT

```TypeScript
MTP_CLIENT = 5
```

MTP client capability (including read and write capabilities). Currently, it is supported only on PC/2-in-1 devices. MTP allows users to linearly access media files on mobile devices. After the device MTP client capability ([FeatureForDevice.MTP_CLIENT](arkts-mdm-restrictions-featurefordevice-e.md)) is disabled, disabling the MTP client write capability for a specific user will result in a policy conflict.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## USB_STORAGE_DEVICE_WRITE

```TypeScript
USB_STORAGE_DEVICE_WRITE = 6
```

USB storage device write capability. Currently, it is supported only on enterprise PCs/2-in-1 devices.

Disabling the USB storage device write capability for a specific user in any of the following scenarios will result in a policy conflict:

1. The device USB capability ([FeatureForDevice.USB](arkts-mdm-restrictions-featurefordevice-e.md)) has been disabled.
2. USB storage device access policy has been set to read-only or disabled via the
[setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md) API.
3. Storage USB devices have been disabled via the [addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md) API.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DISK_RECOVERY_KEY

```TypeScript
DISK_RECOVERY_KEY = 7
```

[Key export](../../../security/UniversalKeystoreKit/huks-export-key-arkts.md) recovery capability. Currently, it is supported only on PCs/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SUDO

```TypeScript
SUDO = 8
```

superuser do (execution with superuser privileges). Currently, it is supported only on PCs/2-in-1 devices. If this feature is disabled, neither enterprise spaces nor personal spaces can perform operations with superuser privileges.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DISTRIBUTED_TRANSMISSION_OUTGOING

```TypeScript
DISTRIBUTED_TRANSMISSION_OUTGOING = 9
```

Distributed one-way data transmission between devices (only data transmission to other devices is supported). Disabling distributed one-way data transmission capability between devices after the distributed management service ([DISTRIBUTED_TRANSMISSION](arkts-mdm-restrictions-featureforaccount-e.md)) has been disabled will result in a policy conflict.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## OPEN_FILE_BOOST

```TypeScript
OPEN_FILE_BOOST = 10
```

File open acceleration capability, providing applications with the ability to sense the file open acceleration status. By integrating the corresponding APIs, apps can detect the acceleration status of files, and further implement features such as displaying unique UI identifiers for accelerated files, thereby optimizing user experience of file opening. Currently, this feature is supported only on PCs/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
