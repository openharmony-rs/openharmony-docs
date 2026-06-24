# AbilityInfo

Ability��Ϣ��

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

Ӧ�ð��ķ���������ʶ������[����Ӧ��](../../../../quick-start/app-clone.md)����Ч��

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

Ӧ�ó����������Ϣ<!--Del-->������ͨ������
[queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryAbilityInfo-2)
�ӿڣ�abilityFlags��������GET_ABILITY_INFO_WITH_APPLICATION��ȡ<!--DelEnd-->��

[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
��
[getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-2)
�ӿڻ�ȡAbilityInfo��Ϣʱ���᷵�ظ��ֶ����ݣ�����ͨ����ȡ[bundleInfo](arkts-ability-bundleinfo-i.md#BundleInfo).appInfo��������ȡ�����Ϣ��

**类型：** ApplicationInfo

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

Ӧ��Bundle���ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

Ability����������Ӧ[module.json5](../../../../quick-start/module-configuration-file.md)��abilities�����õ�description�ֶΣ�����������ǰ
ability�ṩ��ҳ�����ݺ͹������á�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

Ability��������Դid���Ǳ��빹��ʱ����Ӧ������abilities�µ�description�Զ����ɵ���Դid��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Ability֧�ֵ��豸���ͣ���Դ��module.json5���õ�[deviceTypes](../../../../quick-start/module-configuration-file.md#devicetypes��ǩ)��

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

Ability�Ƿ���ã����ñ�ʾ����������߲�ѯ��������ʱ����[getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md#getAbilityInfo-1)
��ѯability��ҪЯ��GET_ABILITY_INFO_WITH_DISABLE��AbilityFlag��ȡֵΪtrue��ʾAbility���ã�ȡֵΪfalse��ʾAbility�����á�

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## excludeFromDock

```TypeScript
readonly excludeFromDock: boolean
```

�ж�Ability�Ƿ������dock��������ͼ�꣬ȡֵΪtrue��ʾ�������أ�ȡֵΪfalse���������ء�

**˵����** ���ֶβ���Ч��

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## exported

```TypeScript
readonly exported: boolean
```

�ж�Ability�Ƿ���Ա�����Ӧ������ȡֵΪtrue��ʾAbility���Ա�����Ӧ������ȡֵΪfalse��ʾAbility�����Ա�����Ӧ������

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

Ability��ͼ����Դ����������Ӧ[module.json5](../../../../quick-start/module-configuration-file.md)��abilities�����õ�icon�ֶΡ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

Ability��ͼ����Դid���Ǳ��빹��ʱ����Ӧ������abilities�µ�icon�Զ����ɵ���Դid��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

Ability���û���ʾ�����Ƶ���Դ����������Ӧ[module.json5](../../../../quick-start/module-configuration-file.md)��abilities�����õ�label�ֶΡ�

**˵����** ��API version 20��ʼ�������ͨ��
[bundleManager.getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md#getAbilityInfo-1)��ȡAbility��Ϣ�����ֶ�Ϊ
Ability���û���ʾ�����ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

Ability�ı�ǩ��Դid���Ǳ��빹��ʱ����Ӧ������abilities�µ�label�Զ����ɵ���Դid��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## launchType

```TypeScript
readonly launchType: bundleManager.LaunchType
```

Ability������ģʽ����������ʱ���Ƿ��Զ�ʵ������������ο�[����ģʽö��](arkts-ability-bundlemanager-launchtype-e.md#LaunchType) ��

**类型：** bundleManager.LaunchType

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

Ability��Ԫ��Ϣ���������ó�ϵͳ����Ĳ�����ʹ��ϵͳ�ṩ������������[��ݷ�ʽ](../../../../quick-start/module-configuration-file.md#shortcuts��ǩ)��
[����Ԫ��������](../../../../windowmanager/window-config-m.md)�ȡ�Ҳ�����Զ������ò�����ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_ABILITY��GET_BUNDLE_INFO_WITH_METADATA��ȡ��

**类型：** Array<Metadata>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

Ability������ģ�����ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Ability���ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## orientation

```TypeScript
readonly orientation: bundleManager.DisplayOrientation
```

Ability����ʾģʽ����Դ��[module.json5](../../../../quick-start/module-configuration-file.md)��abilities��ǩ�����õ�orientation�ֶΣ����
module.json5�����ļ���orientation����ö�٣�orientation������ֵ�ҷ�0��ȡֵ����ο�
[��ʾģʽö��](arkts-ability-bundlemanager-displayorientation-e.md#DisplayOrientation)����������ļ������õ�����Դ������orientation����ֵΪ0��

**类型：** bundleManager.DisplayOrientation

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## orientationId

```TypeScript
readonly orientationId: number
```

Ability����ʾģʽ��Դid����Դ��[module.json5](../../../../quick-start/module-configuration-file.md)��abilities��ǩ�µ�orientation�ֶΣ���
��module.json5�����ļ���orientation����ö�٣�orientationId����ֵΪ0����������ļ������õ�����Դ������orientationId����ֵΪ��0��Ϊ���빹��ʱ���ɵ���Դid��������
orientationId��Ϊ0ʱ��ʾ��ǰ��ʾģʽΪ�Զ������ã���Ҫʹ��orientationIdȥ��Դ������ȡ��Ӧ����Դ����orientationIdΪ0ʱ��ʾδ������Դ��

**类型：** number

**起始版本：** 14

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

������Ӧ������/����ʱ������Ӧ����Ҫ�����Ȩ�޼��ϣ�ֻ�е�ǰAbilityInfo��exportedΪtrue������ǰAbility���Ա�����Ӧ������ʱ���Ż�鿴����Ӧ���Ƿ��������/���ʵ�Ȩ�ޡ�

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## process

```TypeScript
readonly process: string
```

Ability�Ľ������ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## readPermission

```TypeScript
readonly readPermission: string
```

��ȡAbility���������Ȩ�ޡ�

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## skills

```TypeScript
readonly skills: Array<Skill>
```

Ability��Skills��Ϣ����ʶUIAbility�������ExtensionAbility����ܹ����յ�[Want](../../../../application-models/want-overview.md)��������

**类型：** Array<Skill>

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## supportWindowModes

```TypeScript
readonly supportWindowModes: Array<bundleManager.SupportWindowMode>
```

Ability֧�ֵĴ���ģʽ��

**类型：** Array<bundleManager.SupportWindowMode>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: bundleManager.AbilityType
```

Ability���͡�

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** bundleManager.AbilityType

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## uri

```TypeScript
readonly uri: string
```

��ȡAbility��ͳһ��Դ��ʶ����URI����

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## windowSize

```TypeScript
readonly windowSize: WindowSize
```

Ability���ڳߴ硣

**类型：** WindowSize

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## writePermission

```TypeScript
readonly writePermission: string
```

��Abilityд���������Ȩ�ޡ�

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

