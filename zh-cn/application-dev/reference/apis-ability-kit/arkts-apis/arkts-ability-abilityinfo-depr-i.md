# AbilityInfo

Ability��Ϣ��δ������˵�������ԣ���ͨ��
[bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getAbilityInfo-2)��ȡ��

> **˵����**
>
> ��API version 9��ʼ����ģ�鲻��ά��������ʹ��[bundleManager-AbilityInfo](arkts-ability-abilityinfo-depr-i.md#AbilityInfo)�����

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [abilityInfo:AbilityInfo](arkts-ability-abilityinfo-depr-i.md#AbilityInfo)

**系统能力：** SystemCapability.BundleManager.BundleFramework

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

Ӧ�ó����������Ϣ��

ͨ������[bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getAbilityInfo-2)
�ӿ�ʱ������GET_ABILITY_INFO_WITH_APPLICATION��ȡ��

**类型：** ApplicationInfo

**默认值：** Obtains configuration information about an application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** applicationInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework

## backgroundModes

```TypeScript
readonly backgroundModes: number
```

��ʾ��̨��������͡�

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** number

**默认值：** Indicates the background service addressing a specific usage scenario

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework

## bundleName

```TypeScript
readonly bundleName: string
```

Ӧ��Bundle���ơ�

**类型：** string

**默认值：** Indicates the name of the bundle containing the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** bundleName

**系统能力：** SystemCapability.BundleManager.BundleFramework

## description

```TypeScript
readonly description: string
```

Ability��������

**类型：** string

**默认值：** Describes the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** description

**系统能力：** SystemCapability.BundleManager.BundleFramework

## descriptionId

```TypeScript
readonly descriptionId: number
```

Ability����������Դidֵ��

**类型：** number

**默认值：** Indicates the description id of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** descriptionId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## deviceCapabilities

```TypeScript
readonly deviceCapabilities: Array<string>
```

Ability��Ҫ���豸������

**类型：** Array<string>

**默认值：** The device capability that this ability needs

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Ability֧�ֵ��豸���͡�

**类型：** Array<string>

**默认值：** The device types that this ability can run on

**起始版本：** 7

**废弃版本：** 9

**替代接口：** deviceTypes

**系统能力：** SystemCapability.BundleManager.BundleFramework

## enabled

```TypeScript
readonly enabled: boolean
```

Ability�Ƿ���ã�ȡֵΪtrue��ʾAbility���ã�ȡֵΪfalse��ʾAbility�����á�

**类型：** boolean

**默认值：** Indicates whether the ability is enabled

**起始版本：** 8

**废弃版本：** 9

**替代接口：** enabled

**系统能力：** SystemCapability.BundleManager.BundleFramework

## formEnabled

```TypeScript
readonly formEnabled: boolean
```

�ж�Ability�Ƿ��ṩ��Ƭ������ȡֵΪtrue��ʾAbility�ṩ��Ƭ������ȡֵΪfalse��ʾAbility���ṩ��Ƭ������

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** boolean

**默认值：** Indicates whether the ability provides the embedded card capability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

Ability��ͼ����Դ�ļ�������

**类型：** string

**默认值：** Indicates the icon of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** icon

**系统能力：** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: number
```

Ability��ͼ�����Դidֵ��

**类型：** number

**默认值：** Indicates the icon id of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** iconId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## isVisible

```TypeScript
readonly isVisible: boolean
```

�ж�Ability�Ƿ���Ա�����Ӧ�õ��ã�ȡֵΪtrue��ʾAbility���Ա�����Ӧ�õ��ã�ȡֵΪfalse��ʾAbility�����Ա�����Ӧ�õ��á�

**类型：** boolean

**默认值：** Indicates whether an ability can be called by other abilities

**起始版本：** 7

**废弃版本：** 9

**替代接口：** exported

**系统能力：** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

Ability���û���ʾ�����ơ�

**类型：** string

**默认值：** Indicates the label of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** label

**系统能力：** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: number
```

Ability�ı�ǩ����Դidֵ��

**类型：** number

**默认值：** Indicates the label id of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** labelId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## launchMode

```TypeScript
readonly launchMode: bundle.LaunchMode
```

Ability������ģʽ��

**类型：** bundle.LaunchMode

**默认值：** Enumerates ability launch modes

**起始版本：** 7

**废弃版本：** 9

**替代接口：** launchType

**系统能力：** SystemCapability.BundleManager.BundleFramework

## metaData

```TypeScript
readonly metaData: Array<CustomizeData>
```

Ability��Ԫ��Ϣ��

ͨ������[bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getAbilityInfo-2)
�ӿ�ʱ������GET_ABILITY_INFO_WITH_METADATA��ȡ��

**类型：** Array<CustomizeData>

**默认值：** Indicates the metadata of ability

**起始版本：** 8

**废弃版本：** 9

**替代接口：** metadata

**系统能力：** SystemCapability.BundleManager.BundleFramework

## moduleName

```TypeScript
readonly moduleName: string
```

Ability������HAP�����ơ�

**类型：** string

**默认值：** Indicates the name of the .hap package to which the capability belongs

**起始版本：** 7

**废弃版本：** 9

**替代接口：** moduleName

**系统能力：** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

Ability���ơ�

**类型：** string

**默认值：** Ability simplified class name

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

**系统能力：** SystemCapability.BundleManager.BundleFramework

## orientation

```TypeScript
readonly orientation: bundle.DisplayOrientation
```

Ability����ʾģʽ��

**类型：** bundle.DisplayOrientation

**默认值：** Enumerates ability display orientations

**起始版本：** 7

**废弃版本：** 9

**替代接口：** orientation

**系统能力：** SystemCapability.BundleManager.BundleFramework

## permissions

```TypeScript
readonly permissions: Array<string>
```

������Ӧ��Ability����ʱ��Ҫ�����Ȩ�޼��ϡ�

ͨ������[bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getAbilityInfo-2)
�ӿ�ʱ������GET_ABILITY_INFO_WITH_PERMISSION��ȡ��

**类型：** Array<string>

**默认值：** The permissions that others need to launch this ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** permissions

**系统能力：** SystemCapability.BundleManager.BundleFramework

## process

```TypeScript
readonly process: string
```

Ability�Ľ������ơ�

**类型：** string

**默认值：** Process of ability, if user do not set it ,the value equal application process

**起始版本：** 7

**废弃版本：** 9

**替代接口：** process

**系统能力：** SystemCapability.BundleManager.BundleFramework

## readPermission

```TypeScript
readonly readPermission: string
```

��ȡAbility���������Ȩ�ޡ�

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** string

**默认值：** Indicates the permission required for reading ability data

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework

## subType

```TypeScript
readonly subType: bundle.AbilitySubType
```

Ability��ö��ʹ�õ�ģ��������͡�

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** bundle.AbilitySubType

**默认值：** Enumerates the subType of templates used by an ability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework

## targetAbility

```TypeScript
readonly targetAbility: string
```

��ǰAbility���õ�Ŀ��Ability��

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** string

**默认值：** Info about which ability is this nick point to

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework

## type

```TypeScript
readonly type: bundle.AbilityType
```

Ability���͡�

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** bundle.AbilityType

**默认值：** Enumerates types of templates that can be used by an ability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework

## uri

```TypeScript
readonly uri: string
```

��ȡAbility��ͳһ��Դ��ʶ����URI����

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** string

**默认值：** Uri of ability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework

## writePermission

```TypeScript
readonly writePermission: string
```

��Abilityд���������Ȩ�ޡ�

**ģ��Լ����** �˽ӿڽ�����FAģ����ʹ�á�

**类型：** string

**默认值：** Indicates the permission required for writing data to the ability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework

