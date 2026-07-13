# StartupScene

开机向导完成场景。端侧系统在首次切换子用户完成（仅限PC）、OTA升级完成、首次开机完成开机向导时会通过
[onStartupGuideCompleted](arkts-mdm-enterpriseadminextensionability-c.md#onstartupguidecompleted-1)
回调接口通知设备管理应用。

**起始版本：** 24

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## USER_SETUP

```TypeScript
USER_SETUP = 0
```

子用户被首次切换并完成其开机向导场景（仅限PC）。后续再次切换该子用户不会触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## OTA

```TypeScript
OTA = 1
```

OTA升级完成场景。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DEVICE_PROVISION

```TypeScript
DEVICE_PROVISION = 2
```

首次开机完成开机向导场景。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

