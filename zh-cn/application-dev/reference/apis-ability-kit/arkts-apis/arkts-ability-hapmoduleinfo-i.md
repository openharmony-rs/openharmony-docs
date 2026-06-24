# HapModuleInfo

HAP��Ϣ��

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## abilitiesInfo

```TypeScript
readonly abilitiesInfo: Array<AbilityInfo>
```

��ǰģ������Ability����Ϣ��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_ABILITY��ȡ��

**类型：** Array<AbilityInfo>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## codePath

```TypeScript
readonly codePath: string
```

ģ��İ�װ·����

**类型：** string

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## dependencies

```TypeScript
readonly dependencies: Array<Dependency>
```

ģ�����������Ķ�̬�������б���

**类型：** Array<Dependency>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

ģ��������Ϣ��

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

������Ϣ����ԴIDֵ��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

ģ��֧�ְ�װ���е�[�豸����](../../../../quick-start/module-configuration-file.md#devicetypes��ǩ)�ļ��ϡ�

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilitiesInfo

```TypeScript
readonly extensionAbilitiesInfo: Array<ExtensionAbilityInfo>
```

��ǰģ������ExtensionAbility����Ϣ��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY��ȡ��

**类型：** Array<ExtensionAbilityInfo>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## fileContextMenuConfig

```TypeScript
readonly fileContextMenuConfig: string
```

ģ����ļ��˵����á�ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_MENU��ȡ��

**类型：** string

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## hashValue

```TypeScript
readonly hashValue: string
```

ģ���Hashֵ��

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

��ǰģ�����Ability��[ͼ��](../../../../quick-start/layered-image.md)��ȡֵΪͼ����Դ�ļ�����������ģ�������ļ���
[abilities��ǩ](../../../../quick-start/module-configuration-file.md#abilities��ǩ)��
[extensionAbilities��ǩ](../../../../quick-start/module-configuration-file.md#extensionabilities��ǩ)��icon�ֶ�ֵһ�¡���δ�������
Ability����Ϊ�ա�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

��ǰģ�����Ability��ͼ��[��ԴID](../../../../quick-start/resource-categories-and-access.md#��ԴĿ¼)ֵ����δ�������Ability����Ϊ0��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## installationFree

```TypeScript
readonly installationFree: boolean
```

ģ���Ƿ�֧���ⰲװ�������û�ͨ��Ӧ���г���ʽ��װ����ȡֵΪtrue��ʾ֧���ⰲװ��ȡֵΪfalse��ʾ��֧���ⰲװ��

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

��ǰģ�����Ability�����ƣ�ȡֵΪ�ַ�����Դ����������ģ�������ļ���[abilities��ǩ](../../../../quick-start/module-configuration-file.md#abilities��ǩ)��
[extensionAbilities��ǩ](../../../../quick-start/module-configuration-file.md#extensionabilities��ǩ)��label�ֶ�ֵһ�¡���δ�������
Ability����Ϊ�ա�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

��ǰģ�����Ability���Ƶ�[��ԴID](../../../../quick-start/resource-categories-and-access.md#��ԴĿ¼)ֵ����δ�������Ability����Ϊ0��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## mainElementName

```TypeScript
readonly mainElementName: string
```

��ǰģ������UIAbility���ƻ���ExtensionAbility���ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

��ǰģ���Ԫ���ݡ�ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_METADATA��ȡ��

**类型：** Array<Metadata>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

ģ�����ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

Ӧ�ó�����ģ�鱾�ؿ��ļ�·����

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## preloads

```TypeScript
readonly preloads: Array<PreloadItem>
```

ԭ�ӻ�������ģ���Ԥ�����б���

**类型：** Array<PreloadItem>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## routerMap

```TypeScript
readonly routerMap: Array<RouterItem>
```

[ģ���·�ɱ�����](../../../../quick-start/module-configuration-file.md#routermap��ǩ)��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_ROUTER_MAP��ȡ��

**类型：** Array<RouterItem>

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: bundleManager.ModuleType
```

��ʶ��ǰģ������͡�

**类型：** bundleManager.ModuleType

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

