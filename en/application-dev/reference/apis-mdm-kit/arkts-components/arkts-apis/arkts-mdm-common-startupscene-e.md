# StartupScene

Startup wizard completion scenario. When the initial switch to a sub-user (only on PCs), OTA upgrade, and first- time startup wizard are complete, the device system calls the [onStartupGuideCompleted](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onstartupguidecompleted) API to notify the device administrator application.

**Since:** 24

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## USER_SETUP

```TypeScript
USER_SETUP = 0
```

A sub-user is switched to for the first time and the startup wizard for the sub-user is complete (only on PCs). The callback will not be triggered when the sub-user is switched again.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## OTA

```TypeScript
OTA = 1
```

The OTA upgrade is complete.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DEVICE_PROVISION

```TypeScript
DEVICE_PROVISION = 2
```

The initial startup wizard is complete.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
