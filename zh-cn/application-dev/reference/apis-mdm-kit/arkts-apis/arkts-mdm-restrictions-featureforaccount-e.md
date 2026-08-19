# FeatureForAccount

可为指定用户设置禁用/启用的特性的枚举。

**起始版本：** 26.0.0

<!--Device-restrictions-enum FeatureForAccount--><!--Device-restrictions-enum FeatureForAccount-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MULTI_WINDOW

```TypeScript
MULTI_WINDOW = 0
```

系统多窗口。当前仅支持手机、平板设备使用，禁用后无法使用系统多窗口功能（分屏、一键分屏、智慧多窗、悬浮窗口）。若系统多窗口功能已开启，本次使用不受影响，但关闭后将无法再次使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-MULTI_WINDOW = 0--><!--Device-FeatureForAccount-MULTI_WINDOW = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DISTRIBUTED_TRANSMISSION

```TypeScript
DISTRIBUTED_TRANSMISSION = 1
```

[分布式管理服务](../../../distributedservice/distributedservice-kit-intro.md#运作机制)。禁用后无法使用设备分布式管理服务中的发现、认证、查询、监听等功能。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-DISTRIBUTED_TRANSMISSION = 1--><!--Device-FeatureForAccount-DISTRIBUTED_TRANSMISSION = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SUPER_HUB

```TypeScript
SUPER_HUB = 2
```

中转站。当前仅支持手机、平板设备使用，禁用后无法使用中转站功能。若中转站已开启，本次使用不受影响，但关闭后将无法再次使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-SUPER_HUB = 2--><!--Device-FeatureForAccount-SUPER_HUB = 2-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## FINGERPRINT

```TypeScript
FINGERPRINT = 3
```

设备指纹认证能力，当前仅支持PC/2in1设备使用。使用时有以下规则： 1. 禁用设备指纹认证能力（[FeatureForDevice.FINGERPRINT](arkts-mdm-restrictions-featurefordevice-e.md)）后，再禁用某用户的设备指纹认证能力，会报策略冲突。 2. 禁用/启用指定用户的设备指纹认证能力后，再禁用设备指纹认证能力（[FeatureForDevice.FINGERPRINT](arkts-mdm-restrictions-featurefordevice-e.md)）时，后者会覆盖前者的策略。 此后再启用设备指纹认证能力（[FeatureForDevice.FINGERPRINT](arkts-mdm-restrictions-featurefordevice-e.md)），则所有用户都允许使用设备指纹认证能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-FINGERPRINT = 3--><!--Device-FeatureForAccount-FINGERPRINT = 3-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## PRINT

```TypeScript
PRINT = 4
```

设备打印能力。如果禁用了指定用户的设备打印能力，再启用设备打印能力（[FeatureForDevice.PRINTER](arkts-mdm-restrictions-featurefordevice-e.md)），该用户下的设备打印能力仍然被 禁用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-PRINT = 4--><!--Device-FeatureForAccount-PRINT = 4-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MTP_CLIENT

```TypeScript
MTP_CLIENT = 5
```

MTP客户端能力（仅包含写入），当前仅支持PC/2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。当已禁用设备MTP客户端能力（ [FeatureForDevice.MTP_CLIENT](arkts-mdm-restrictions-featurefordevice-e.md)）时，再禁用某用户MTP客户端写入能力，会报策略冲突。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-MTP_CLIENT = 5--><!--Device-FeatureForAccount-MTP_CLIENT = 5-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## USB_STORAGE_DEVICE_WRITE

```TypeScript
USB_STORAGE_DEVICE_WRITE = 6
```

USB存储设备写入能力，当前仅支持PC/2in1企业设备使用。 以下三种情况再禁用某用户USB存储设备写入能力，会报策略冲突。 1）已禁用设备USB能力（[FeatureForDevice.USB](arkts-mdm-restrictions-featurefordevice-e.md)）。 2）通过 [setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md)接口 设置了USB存储设备访问策略为只读/禁用。 3）通过[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md)接口添加了存储类型的USB设 备禁用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-USB_STORAGE_DEVICE_WRITE = 6--><!--Device-FeatureForAccount-USB_STORAGE_DEVICE_WRITE = 6-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DISK_RECOVERY_KEY

```TypeScript
DISK_RECOVERY_KEY = 7
```

恢复[密钥导出](../../../security/UniversalKeystoreKit/huks-export-key-arkts.md)能力，当前仅支持PC/2in1设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-DISK_RECOVERY_KEY = 7--><!--Device-FeatureForAccount-DISK_RECOVERY_KEY = 7-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SUDO

```TypeScript
SUDO = 8
```

superuser do，表示以超级用户执行，当前仅支持PC/2in1设备使用。禁用后企业空间或个人空间不能以超级用户执行。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-SUDO = 8--><!--Device-FeatureForAccount-SUDO = 8-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DISTRIBUTED_TRANSMISSION_OUTGOING

```TypeScript
DISTRIBUTED_TRANSMISSION_OUTGOING = 9
```

设备间分布式单向传输数据的能力（仅包含向其他设备传输数据）。当已禁用分布式管理服务（[DISTRIBUTED_TRANSMISSION](#featureforaccount)），再禁用设备 间分布式单向传输数据的能力，会报策略冲突。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-DISTRIBUTED_TRANSMISSION_OUTGOING = 9--><!--Device-FeatureForAccount-DISTRIBUTED_TRANSMISSION_OUTGOING = 9-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## OPEN_FILE_BOOST

```TypeScript
OPEN_FILE_BOOST = 10
```

文件打开加速能力，为应用提供文件打开加速状态感知能力。应用可以通过接入对应API，感知文件的加速状态，进而应用可以实现对已加速文件给出独特的UI（user interface）标识等功能，优化用户文件打开体验，当前仅支持PC/2in1设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-OPEN_FILE_BOOST = 10--><!--Device-FeatureForAccount-OPEN_FILE_BOOST = 10-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

