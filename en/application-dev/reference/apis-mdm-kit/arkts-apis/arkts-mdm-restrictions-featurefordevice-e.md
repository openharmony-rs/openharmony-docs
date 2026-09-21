# FeatureForDevice

```TypeScript
enum FeatureForDevice
```

Enumerates device features.

**Since:** 24

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WIFI_P2P

```TypeScript
WIFI_P2P = 0
```

Wi-Fi P2P (peer-to-peer connection), which allows devices to directly connect to each other without an access point. Once this feature is disallowed, devices cannot be connected through Wi-Fi P2P, affecting application functions that require direct Wi-Fi connections, such as file transfer, online gaming, and screen sharing.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## X_KEY

```TypeScript
X_KEY = 1
```

X key.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## LOCAL_INPUT

```TypeScript
LOCAL_INPUT = 2
```

After local input (including the keyboard, mouse, touchpad, and touchscreen) is disabled, operations cannot be performed through local input. You can restart the device to cancel the disabling. If local input is disabled when the screen is off, the screen cannot be woken up. If the screen automatically turns off after this feature is disabled, the screen also cannot be woken up.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## PACKET_FILTERING

```TypeScript
PACKET_FILTERING = 3
```

Network packet filtering.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SUDO

```TypeScript
SUDO = 4
```

Super user do.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## TRAFFIC_REDIRECTION

```TypeScript
TRAFFIC_REDIRECTION = 5
```

Policy for controlling network traffic redirection. After this capability is disabled, TCP traffic cannot be redirected to other ports. You can cancel the disabling to restore the feature. Currently, this capability is supported only on PCs/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## CORE_DUMP

```TypeScript
CORE_DUMP = 6
```

Create a file dump. After this capability is disabled, file dumps cannot be created through the task manager. Currently, this capability is supported only on PCs/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## RS232

```TypeScript
RS232 = 7
```

RS-232 serial port control policy. If this capability is disabled, data cannot be transmitted via the RS-232 serial port. Currently, this capability is supported only on PCs/2-in-1 devices. (some devices do not support the RS-232 serial port).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DISK_ERASURE

```TypeScript
DISK_ERASURE = 8
```

Disk erasure capability. Once disabled, the "Disk Erasure" entry will be grayed out. Currently, this capability is supported only on PCs/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## BLUETOOTH

```TypeScript
BLUETOOTH = 9
```

Device Bluetooth capability. If a Bluetooth device blocklist or trustlist is configured via [addDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-adddisallowedbluetoothdevices-f.md) or [addAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-addallowedbluetoothdevices-f.md), disabling Bluetooth via this API takes priority. The blocklist or trustlist will only take effect after Bluetooth is re-enabled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MODIFY_DATE_TIME

```TypeScript
MODIFY_DATE_TIME = 10
```

Device capability to modify system time.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## PRINTER

```TypeScript
PRINTER = 11
```

Device printing capability. When the device printing capability has been disabled, enabling printing for a specific user via the [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md) API will not take effect. The printing capability remains disabled for that user.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## HDC

```TypeScript
HDC = 12
```

Capability for other devices to connect to and debug this device via HDC. Disabling this capability prevents external devices from connecting or debugging via HDC.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MICROPHONE

```TypeScript
MICROPHONE = 13
```

Device microphone capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## FINGERPRINT

```TypeScript
FINGERPRINT = 14
```

Device fingerprint authentication capability. Enable device fingerprint authentication will trigger a policy conflict if fingerprint authentication has already been disabled for a user via [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## USB

```TypeScript
USB = 15
```

Device USB capability. Disabling this capability prohibits the use of external USB devices (the device cannot act as a USB host to connect external devices).

If the device USB capability is disabled in any of the following scenarios, a policy conflict will be reported:

1. A list of allowed USB devices has been configured via the
[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md) API.
2. USB storage device access policy has been set to read-only or disabled via the
[setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md) API.
3. Specific USB device types have been blocked via the
[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md) API.
4. USB storage write has been disabled for specific users via the [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md) API.
5. USB-to-serial conversion ([USB_SERIAL](arkts-mdm-restrictions-featurefordevice-e.md)) is disabled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WIFI

```TypeScript
WIFI = 16
```

Device Wi-Fi capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## TETHERING

```TypeScript
TETHERING = 17
```

Network tethering capability (the ability to share the device's internet connection with other devices, that is, hotspot sharing).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## INACTIVE_USER_FREEZE

```TypeScript
INACTIVE_USER_FREEZE = 18
```

Capability of freezing inactive users. When this capability is disabled, non-**UIAbility** processes will generally not be frozen, and background tasks requested by **UIAbility** (such as transient tasks, continuous tasks, deferred tasks, or energy efficiency resources) will also not be frozen. Currently, this capability is supported only on PCs/2-in-1 devices. When the system switches to the enterprise space user, the personal space users are inactive users.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## CAMERA

```TypeScript
CAMERA = 19
```

Device camera capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MTP_CLIENT

```TypeScript
MTP_CLIENT = 20
```

Media Transfer Protocol (MTP) client capability (including read and write capabilities), currently supported only on PC/2-in-1 devices. MTP allows users to linearly access media files on mobile devices. A policy conflict occurs when you disable the MTP client capability after MTP client write has been disabled for specific users via [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MTP_SERVER

```TypeScript
MTP_SERVER = 21
```

MTP server capability, currently supported only on phone and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SAMBA_CLIENT

```TypeScript
SAMBA_CLIENT = 22
```

Samba client capability, currently supported only on PC/2-in-1 devices.

Samba is a free software that implements the SMB protocol on Linux and UNIX systems, consisting of both server and client programs. Server Message Block (SMB) is a communication protocol for sharing files and printers over the local area network (LAN). It provides resource-sharing services, such as files and printers, among different computers within the LAN. As a client/server protocol, SMB allows clients to access shared resources hosted on servers.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SAMBA_SERVER

```TypeScript
SAMBA_SERVER = 23
```

Samba server capability, currently supported only on PC/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## BACKUP_AND_RESTORE

```TypeScript
BACKUP_AND_RESTORE = 24
```

Backup and restore capability. If this feature is disabled, the **Settings**  
> **System**
> **Backup & Restore** and **Settings**
> **Cloud** options will be dimmed. Currently, this feature is supported only on phones and tablets. To completely disable the backup and restore capability, you are advised to call [applicationManager.addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md) to disable applications with this feature, such as Backup & Restore, HiSuite, and Cloud.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MAINTENANCE_MODE

```TypeScript
MAINTENANCE_MODE = 25
```

Device maintenance mode capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MMS

```TypeScript
MMS = 26
```

Multimedia Messaging Service (MMS) capability to receive and send multimedia messages. Currently, this feature is supported only on smartphones and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SMS

```TypeScript
SMS = 27
```

Short Messaging Service (SMS) capability to receive and send SMS messages. Currently, this feature is supported only on smartphones and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## MOBILE_DATA

```TypeScript
MOBILE_DATA = 28
```

Cellular data capability, which is supported only on smartphones and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## AIRPLANE_MODE

```TypeScript
AIRPLANE_MODE = 29
```

Airplane mode capability, which is supported only on smartphones and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## VPN

```TypeScript
VPN = 30
```

Virtual Private Network (VPN) capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## NOTIFICATION

```TypeScript
NOTIFICATION = 31
```

Device notification capability. After this capability is disabled, notifications sent by system applications and third-party applications will not be displayed. However, notification capabilities for system services are not affected. If you disable the device-level notification capability after an allowed notification bundle has already been set via [addAllowedNotificationBundles](arkts-mdm-applicationmanager-addallowednotificationbundles-f.md), error code 9200010 will be reported.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## NFC

```TypeScript
NFC = 32
```

Near Field Communication (NFC) capability, which is supported only on phones and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## PRIVATE_SPACE

```TypeScript
PRIVATE_SPACE = 33
```

Privacy space creation capability, which is supported only on smartphones and tablets. This setting does not affect existing private spaces.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## TELEPHONE_CALL

```TypeScript
TELEPHONE_CALL = 34
```

Call capability. Disabling this feature blocks incoming or outgoing calls. Currently, this feature is supported only on smartphones and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## APP_CLONE

```TypeScript
APP_CLONE = 35
```

[Application clone capability](../../../quick-start/app-clone.md). When this feature is disabled, new application clones cannot be created. This feature is invalid for the application clone that has been created.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EXTERNAL_STORAGE_CARD

```TypeScript
EXTERNAL_STORAGE_CARD = 36
```

External storage capability. Disabling this feature prohibits the use of external storage and unmounts currently connected external storage. If files are in use during unmounting, unmounting may fail with error code 9200013.

After external storage is disabled and then enabled again, you need to manually reconnect the external storage.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## RANDOM_MAC

```TypeScript
RANDOM_MAC = 37
```

Random MAC address capability for Wi-Fi connections. When this feature is disabled, only the device's physical MAC address can be used for Wi-Fi connections.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## UNMUTE_DEVICE

```TypeScript
UNMUTE_DEVICE = 38
```

Device audio playback capability. When this feature is disabled, media playback will be muted, while [cellular calls](../../../media/audio/audio-call-overview.md) remain unaffected.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## HDC_REMOTE

```TypeScript
HDC_REMOTE = 39
```

Capability of the device to debug other devices through HDC. Currently, this feature can be set only for PCs/2-in -1 devices. Disabling this capability prevents debugging smartphones, tablets, PCs, smart watches, and other devices via HDC.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## VIRTUAL_SERVICE

```TypeScript
VIRTUAL_SERVICE = 40
```

Device virtualization service capability, which refers to the system capability of running other operating system platforms (such as Linux and Windows) through virtualization technology by leveraging the redundancy of the device's hardware resources. If this capability is disabled, it is advised to uninstall all applications related to the virtualization service and prohibit their reinstallation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## USB_SERIAL

```TypeScript
USB_SERIAL = 41
```

Device USB-to-serial port capability. After the capability is disabled, external USB-to-serial port devices will be unavailable. Disabling the USB-to-Serial capability in any of the following scenario will trigger a policy conflict:

1. A list of allowed USB devices has been configured via the
[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md) API.
2. The device ([USB](arkts-mdm-restrictions-featurefordevice-e.md)) capability has been disabled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SCREEN_SHOT

```TypeScript
SCREEN_SHOT = 42
```

Screenshot capability. After this capability is disabled, screenshots cannot be taken.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SCREEN_RECORD

```TypeScript
SCREEN_RECORD = 43
```

Screen recording capability. After this capability is disabled, screen recording cannot be performed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DISK_RECOVERY_KEY

```TypeScript
DISK_RECOVERY_KEY = 44
```

[Key export](../../../security/UniversalKeystoreKit/huks-export-key-arkts.md) recovery capability. Currently, it is supported only on PCs/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## NEAR_LINK

```TypeScript
NEAR_LINK = 45
```

NearLink capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DEVELOPER_MODE

```TypeScript
DEVELOPER_MODE = 46
```

Developer mode. Disabling this feature takes effect after the device is restarted.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## RESET_FACTORY

```TypeScript
RESET_FACTORY = 47
```

Factory reset capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## REMOTE_DESK

```TypeScript
REMOTE_DESK = 48
```

Remote desktop capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## REMOTE_DIAGNOSIS

```TypeScript
REMOTE_DIAGNOSIS = 49
```

Remote diagnosis capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## OTA_UPDATE

```TypeScript
OTA_UPDATE = 50
```

Public network system upgrade capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SYSTEM_ROLLBACK

```TypeScript
SYSTEM_ROLLBACK = 51
```

System rollback capability.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
