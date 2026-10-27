# AdminType

```TypeScript
export enum AdminType
```

Enumerates the types of device administrator applications.

**Since:** 15

<!--Device-adminManager-export enum AdminType--><!--Device-adminManager-export enum AdminType-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ADMIN_TYPE_BYOD

```TypeScript
ADMIN_TYPE_BYOD = 0x02
```

BYOD device administrator application.

**Since:** 15

<!--Device-AdminType-ADMIN_TYPE_BYOD = 0x02--><!--Device-AdminType-ADMIN_TYPE_BYOD = 0x02-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ADMIN_TYPE_NORMAL

```TypeScript
ADMIN_TYPE_NORMAL = 0x00
```

After a common device administrator application is enabled, it can be uninstalled. Its [EnterpriseAdminExtensionAbility](../../../mdm/mdm-kit-term.md#enterpriseadminextensionability) component will automatically start upon device startup and can be restarted after the component process dies.

**Since:** 26.0.1

<!--Device-AdminType-ADMIN_TYPE_NORMAL = 0x00--><!--Device-AdminType-ADMIN_TYPE_NORMAL = 0x00-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ADMIN_TYPE_SUPER

```TypeScript
ADMIN_TYPE_SUPER = 0x01
```

After a super device administrator application is enabled, it cannot be uninstalled. Its [EnterpriseAdminExtensionAbility](../../../mdm/mdm-kit-term.md#enterpriseadminextensionability) component will automatically start upon device startup and can be restarted after the component process dies.

**Since:** 26.0.1

<!--Device-AdminType-ADMIN_TYPE_SUPER = 0x01--><!--Device-AdminType-ADMIN_TYPE_SUPER = 0x01-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
