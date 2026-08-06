# AdminType

设备管理应用的类型。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

<!--Device-adminManager-export enum AdminType--><!--Device-adminManager-export enum AdminType-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ADMIN_TYPE_NORMAL

```TypeScript
ADMIN_TYPE_NORMAL = 0x00
```

普通设备管理应用，激活后应用可卸载，其\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_组件将开机自启和组 件进程死亡后能重新拉起。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-AdminType-ADMIN_TYPE_NORMAL = 0x00--><!--Device-AdminType-ADMIN_TYPE_NORMAL = 0x00-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ADMIN_TYPE_SUPER

```TypeScript
ADMIN_TYPE_SUPER = 0x01
```

超级设备管理应用，激活后应用不可卸载，其\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_组件将开机自启和 组件进程死亡后能重新拉起。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-AdminType-ADMIN_TYPE_SUPER = 0x01--><!--Device-AdminType-ADMIN_TYPE_SUPER = 0x01-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ADMIN_TYPE_BYOD

```TypeScript
ADMIN_TYPE_BYOD = 0x02
```

BYOD设备管理应用。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

<!--Device-AdminType-ADMIN_TYPE_BYOD = 0x02--><!--Device-AdminType-ADMIN_TYPE_BYOD = 0x02-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

