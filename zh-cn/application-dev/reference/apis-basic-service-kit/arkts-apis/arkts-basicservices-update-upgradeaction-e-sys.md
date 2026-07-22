# UpgradeAction（系统接口）

升级方式。

**起始版本：** 9

<!--Device-update-export enum UpgradeAction--><!--Device-update-export enum UpgradeAction-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## UPGRADE

```TypeScript
UPGRADE = 'upgrade'
```

差分包，仅包含与当前版本的差异部分，适用于已安装基础版本的增量升级场景。详见[术语](../../../basic-services/update/update-kit-term.md)。

**起始版本：** 9

<!--Device-UpgradeAction-UPGRADE = 'upgrade'--><!--Device-UpgradeAction-UPGRADE = 'upgrade'-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## RECOVERY

```TypeScript
RECOVERY = 'recovery'
```

修复包，用于修复系统异常或恢复系统功能的特殊升级包，适用于系统故障修复场景。详见[术语](../../../basic-services/update/update-kit-term.md)。

**起始版本：** 9

<!--Device-UpgradeAction-RECOVERY = 'recovery'--><!--Device-UpgradeAction-RECOVERY = 'recovery'-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

