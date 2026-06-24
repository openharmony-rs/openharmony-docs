# AbilityFlag（系统接口）

```TypeScript
enum AbilityFlag
```

Ability�����Ϣ��־��ָʾ��Ҫ��ȡ��Ability�����Ϣ�����ݡ�

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_DEFAULT

```TypeScript
GET_ABILITY_INFO_DEFAULT = 0x00000000
```

��ȡĬ��[AbilityInfo](bundleManager/AbilityInfo)����ȡ��AbilityInfo������permissions��metadata��������Ability��Ӧ��
AbilityInfo��<!--Del-->ͨ��
[setAbilityEnabled�ӿ�](arkts-ability-bundlemanager-setabilityenabled-f-sys.md#setAbilityEnabled-2)
������Ability����״̬��ͨ��
[isAbilityEnabled�ӿ�](arkts-ability-bundlemanager-isabilityenabled-f-sys.md#isAbilityEnabled-3)�ɻ�ȡ
Ability����״̬��<!--DelEnd-->

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_PERMISSION

```TypeScript
GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001
```

��ȡ����permissions��AbilityInfo��

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_APPLICATION

```TypeScript
GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002
```

��ȡ����applicationInfo��AbilityInfo��

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_METADATA

```TypeScript
GET_ABILITY_INFO_WITH_METADATA = 0x00000004
```

��ȡ����metadata��AbilityInfo��

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_DISABLE

```TypeScript
GET_ABILITY_INFO_WITH_DISABLE = 0x00000008
```

��ȡ������Ability��Ӧ��AbilityInfo��

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_ONLY_SYSTEM_APP

```TypeScript
GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010
```

��ȡϵͳӦ�ö�Ӧ��AbilityInfo��

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_APP_LINKING

```TypeScript
GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040
```

��ȡͨ��<!--RP3-->[����У��](../../../../application-models/app-linking-startup.md#ʵ��ԭ��)<!--RP3End-->ɸѡ��AbilityInfo��

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_SKILL

```TypeScript
GET_ABILITY_INFO_WITH_SKILL = 0x00000080
```

��ȡ����skills��AbilityInfo��

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

