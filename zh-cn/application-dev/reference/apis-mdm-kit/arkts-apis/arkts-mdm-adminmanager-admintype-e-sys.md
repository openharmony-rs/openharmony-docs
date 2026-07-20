# AdminType

设备管理应用的类型。

**起始版本：** 15

<!--Device-adminManager-export enum AdminType--><!--Device-adminManager-export enum AdminType-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ADMIN_TYPE_NORMAL

```TypeScript
ADMIN_TYPE_NORMAL = 0x00
```

普通设备管理应用，激活后应用可卸载，其[企业设备管理扩展能力](docroot://mdm/mdm-kit-term.md#企业设备管理扩展能力)组件将开机自启和组件进程死亡后能重新拉起。

**起始版本：** 9

<!--Device-AdminType-ADMIN_TYPE_NORMAL = 0x00--><!--Device-AdminType-ADMIN_TYPE_NORMAL = 0x00-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## ADMIN_TYPE_SUPER

```TypeScript
ADMIN_TYPE_SUPER = 0x01
```

超级设备管理应用，激活后应用不可卸载，其[企业设备管理扩展能力](docroot://mdm/mdm-kit-term.md#企业设备管理扩展能力)组件将开机自启和组件进程死亡后能重新拉起。

**起始版本：** 9

<!--Device-AdminType-ADMIN_TYPE_SUPER = 0x01--><!--Device-AdminType-ADMIN_TYPE_SUPER = 0x01-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

