# Flags

[Want.flags](arkts-ability-app-ability-want-want-c.md#flags)字段常用的系统预置关键字。开发者可以通过这些预置关键字设置或获取应用跳转等场景中额外携带的标志位信息。

**起始版本：** 9

<!--Device-wantConstant-export enum Flags--><!--Device-wantConstant-export enum Flags-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_READ_URI_PERMISSION

```TypeScript
FLAG_AUTH_READ_URI_PERMISSION = 0x00000001
```

表示临时授予接收方读取该URI指向的数据的权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Flags-FLAG_AUTH_READ_URI_PERMISSION = 0x00000001--><!--Device-Flags-FLAG_AUTH_READ_URI_PERMISSION = 0x00000001-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_WRITE_URI_PERMISSION

```TypeScript
FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002
```

表示临时授予接收方写入该URI指向的数据的权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Flags-FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002--><!--Device-Flags-FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_PERSISTABLE_URI_PERMISSION

```TypeScript
FLAG_AUTH_PERSISTABLE_URI_PERMISSION = 0x00000040
```

表示该URI可被接收方持久化。目标应用可以通过[fileShare.persistPermission](./@ohos.fileshare:fileShare.persistPermission)接口进行权限持久化。

**起始版本：** 12

<!--Device-Flags-FLAG_AUTH_PERSISTABLE_URI_PERMISSION = 0x00000040--><!--Device-Flags-FLAG_AUTH_PERSISTABLE_URI_PERMISSION = 0x00000040-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_INSTALL_ON_DEMAND

```TypeScript
FLAG_INSTALL_ON_DEMAND = 0x00000800
```

表示拉起原子化服务时开启免安装功能。

- 如果开启了免安装功能，当系统检测到被拉起的原子化服务未安装时，会自动安装原子化服务，再进行拉起。  
- 如果未开启免安装功能，当原子化服务未安装时，将拉起失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Flags-FLAG_INSTALL_ON_DEMAND = 0x00000800--><!--Device-Flags-FLAG_INSTALL_ON_DEMAND = 0x00000800-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_ON_COLLABORATE

```TypeScript
FLAG_ABILITY_ON_COLLABORATE = 0x00002000
```

在多设备协同场景下，调用方应用通过DMS系统发起请求并且通过Flags字段携带此标志，协同方应用才会触发生命周期回调方法[onCollaborate()](arkts-ability-app-ability-uiability-uiability-c.md#oncollaborate)。

**起始版本：** 18

<!--Device-Flags-FLAG_ABILITY_ON_COLLABORATE = 0x00002000--><!--Device-Flags-FLAG_ABILITY_ON_COLLABORATE = 0x00002000-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_START_WITHOUT_TIPS

```TypeScript
FLAG_START_WITHOUT_TIPS = 0x40000000
```

表示是否关闭匹配失败弹窗功能。

通过[隐式方式拉起应用](../../../application-models/app-startup-overview.md)时，如果没有能够匹配的应用，默认会弹出提示弹窗“暂无可用打开方式”。开发者可以通过该字段屏蔽该弹窗。

**起始版本：** 11

<!--Device-Flags-FLAG_START_WITHOUT_TIPS = 0x40000000--><!--Device-Flags-FLAG_START_WITHOUT_TIPS = 0x40000000-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

