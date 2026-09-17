# AdminType

Enumerates the types of device administrator applications.

**Since:** 15

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ADMIN_TYPE_NORMAL

```TypeScript
ADMIN_TYPE_NORMAL = 0x00
```

After a common device administrator application is enabled, it can be uninstalled. Its [EnterpriseAdminExtensionAbility](../../../mdm/mdm-kit-term.md#enterpriseadminextensionability) component will automatically start upon device startup and can be restarted after the component process dies.

**Since:** 9

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## ADMIN_TYPE_SUPER

```TypeScript
ADMIN_TYPE_SUPER = 0x01
```

After a super device administrator application is enabled, it cannot be uninstalled. Its [EnterpriseAdminExtensionAbility](../../../mdm/mdm-kit-term.md#enterpriseadminextensionability) component will automatically start upon device startup and can be restarted after the component process dies.

**Since:** 9

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.
