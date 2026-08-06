# Operation

设备操作。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-deviceControl-enum Operation--><!--Device-deviceControl-enum Operation-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DISK_ERASURE

```TypeScript
DISK_ERASURE = 0
```

磁盘擦除。接口调用后，设备将立即执行磁盘擦除操作。磁盘擦除完成后，整机设备数据将全部被擦除且无法恢复。企业需要做好应用的安全设计，防止应用被攻击导致企业数据丢失。仅支持PC/2in1设备。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Operation-DISK_ERASURE = 0--><!--Device-Operation-DISK_ERASURE = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## RESET_FACTORY

```TypeScript
RESET_FACTORY = 1
```

设备恢复出厂设置。接口调用后，设备将立即恢复出厂设置。恢复完成后，整机设备数据将全部被擦除且无法恢复。企业需要做好应用的安全设计，防止应用被攻击导致企业数据丢失。 已经通过restrictions.setDisallowedPolicy接口禁用了恢复出厂，需要先解除禁用。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Operation-RESET_FACTORY = 1--><!--Device-Operation-RESET_FACTORY = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## REBOOT

```TypeScript
REBOOT = 2
```

设备重启。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Operation-REBOOT = 2--><!--Device-Operation-REBOOT = 2-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SHUT_DOWN

```TypeScript
SHUT_DOWN = 3
```

设备关机。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Operation-SHUT_DOWN = 3--><!--Device-Operation-SHUT_DOWN = 3-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## LOCK_SCREEN

```TypeScript
LOCK_SCREEN = 4
```

设备锁屏。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Operation-LOCK_SCREEN = 4--><!--Device-Operation-LOCK_SCREEN = 4-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## LOCK_DEVICE

```TypeScript
LOCK_DEVICE = 5
```

设备锁定。该能力使用后设备屏幕无法使用，按键无响应，仅支持锁屏文案定制，不支持在锁屏界面定制交互功能。在开发过程中，下发设备锁定策略前一定要预留逃生通道，并且确保逃生通道正常。 建议开发时保留hdc能力与远程通信能力，通过hdc命令或者远程push能力能触发设备解锁定功能。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_如果需要实现在屏幕锁定的情况下支持自定义行为的能力， 使用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_)接口进入Kiosk模式。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Operation-LOCK_DEVICE = 5--><!--Device-Operation-LOCK_DEVICE = 5-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## UNLOCK_DEVICE

```TypeScript
UNLOCK_DEVICE = 6
```

设备解锁定。接口调用后，设备将被解锁，用户可正常操作设备。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Operation-UNLOCK_DEVICE = 6--><!--Device-Operation-UNLOCK_DEVICE = 6-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

