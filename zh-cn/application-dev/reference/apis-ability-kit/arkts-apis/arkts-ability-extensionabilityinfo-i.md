# ExtensionAbilityInfo

ExtensionAbility��Ϣ������ͨ��
[bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)
��ȡ������ExtensionAbility��Ϣ�����в���[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md#BundleFlag)���ٰ���
GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY��

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

Ӧ�ð��ķ���������ʶ�����ڷ���Ӧ������Ч��

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

Ӧ�ó����������Ϣ<!--Del-->������ͨ������
[queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md#queryExtensionAbilityInfo-2)
�ӿڣ�extensionAbilityFlags��������GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION��ȡ<!--DelEnd-->��

[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
��
[getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-2)
�ӿڻ�ȡExtensionAbilityInfo��Ϣʱ���᷵�ظ��ֶ����ݣ�����ͨ����ȡ[bundleInfo](arkts-ability-bundleinfo-i.md#BundleInfo).appInfo��������ȡ�����Ϣ��

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

## descriptionId

```TypeScript
readonly descriptionId: number
```

ExtensionAbility��������ԴID��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

ExtensionAbility�Ƿ���ã�ȡֵΪtrue��ʾExtensionAbility���ã�ȡֵΪfalse��ʾExtensionAbility�����á�

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## exported

```TypeScript
readonly exported: boolean
```

�ж�ExtensionAbility�Ƿ���Ա�����Ӧ�õ��ã�ȡֵΪtrue��ʾExtensionAbility���Ա�����Ӧ�õ��ã�ȡֵΪfalse��ʾExtensionAbility�����Ա�����Ӧ�õ��á�

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilityType

```TypeScript
readonly extensionAbilityType: bundleManager.ExtensionAbilityType
```

ExtensionAbility���͡�

**类型：** bundleManager.ExtensionAbilityType

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilityTypeName

```TypeScript
readonly extensionAbilityTypeName: string
```

ExtensionAbility���������ƣ�ȡֵ��ο�
[extensionabilities��ǩ�µ�type�ֶ�](../../../../quick-start/module-configuration-file.md#extensionabilities��ǩ)��

**类型：** string

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

ExtensionAbility��ͼ����ԴID��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

ExtensionAbility�ı�ǩ��ԴID��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

ExtensionAbility��Ԫ��Ϣ��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY��
GET_BUNDLE_INFO_WITH_METADATA��ȡ��

**类型：** Array<Metadata>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

ExtensionAbility������HAP�����ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

ExtensionAbility���ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

������Ӧ��ExtensionAbility����ʱ��Ҫ�����Ȩ�޼��ϡ�

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## readPermission

```TypeScript
readonly readPermission: string
```

��ȡExtensionAbility���������Ȩ�ޡ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## skills

```TypeScript
readonly skills: Array<Skill>
```

ExtensionAbility��Skills��Ϣ��

**类型：** Array<Skill>

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## writePermission

```TypeScript
readonly writePermission: string
```

��ExtensionAbilityд���������Ȩ�ޡ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

