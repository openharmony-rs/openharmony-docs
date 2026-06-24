# BundleFlag

```TypeScript
enum BundleFlag
```

����Ϣ��־��ָʾ��Ҫ��ȡ�İ���Ϣ�����ݡ�

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_DEFAULT

```TypeScript
GET_BUNDLE_INFO_DEFAULT = 0x00000000
```

��ȡĬ�ϰ���Ϣ��������signatureInfo��applicationInfo��hapModuleInfo��ability��extensionAbility��permission����Ϣ��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_APPLICATION

```TypeScript
GET_BUNDLE_INFO_WITH_APPLICATION = 0x00000001
```

���ڻ�ȡ����applicationInfo��bundleInfo����ȡ��bundleInfo������signatureInfo��hapModuleInfo��ability��extensionAbility��permission��
��Ϣ��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_HAP_MODULE

```TypeScript
GET_BUNDLE_INFO_WITH_HAP_MODULE = 0x00000002
```

���ڻ�ȡ����hapModuleInfo��bundleInfo����ȡ��bundleInfo������signatureInfo��applicationInfo��ability��extensionAbility��permission��
��Ϣ��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_ABILITY

```TypeScript
GET_BUNDLE_INFO_WITH_ABILITY = 0x00000004
```

���ڻ�ȡ����ability��bundleInfo����ȡ��bundleInfo������signatureInfo��applicationInfo��extensionAbility��permission����Ϣ������ʹ�ò���Ч����Ҫ��
GET_BUNDLE_INFO_WITH_HAP_MODULEһ��ʹ�á�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY

```TypeScript
GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY = 0x00000008
```

���ڻ�ȡ����extensionAbility��bundleInfo����ȡ��bundleInfo������signatureInfo��applicationInfo��ability ��permission����Ϣ������ʹ�ò���Ч����Ҫ
��GET_BUNDLE_INFO_WITH_HAP_MODULEһ��ʹ�á�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION

```TypeScript
GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION = 0x00000010
```

���ڻ�ȡ����permission��bundleInfo����ȡ��bundleInfo������signatureInfo��applicationInfo��hapModuleInfo��extensionAbility��ability��
��Ϣ��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_METADATA

```TypeScript
GET_BUNDLE_INFO_WITH_METADATA = 0x00000020
```

���ڻ�ȡapplicationInfo��moduleInfo��abilityInfo��extensionAbilityInfo�а�����metadata������ʹ�ò���Ч������Ҫ��
GET_BUNDLE_INFO_WITH_APPLICATION��GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_ABILITY��
GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY���ʹ�ã����У�

-?��ȡapplicationInfo�а�����metadata����Ҫ��GET_BUNDLE_INFO_WITH_APPLICATIONһ��ʹ�á�

-?��ȡmoduleInfo�а�����metadata����Ҫ��GET_BUNDLE_INFO_WITH_HAP_MODULEһ��ʹ�á�

-?��ȡabilityInfo�а�����metadata����Ҫ��GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_ABILITYһ��ʹ�á�

-?��ȡextensionAbilityInfo�а�����metadata����Ҫ��GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_EXTENSION_ABILITYһ��ʹ
�á�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_DISABLE

```TypeScript
GET_BUNDLE_INFO_WITH_DISABLE = 0x00000040
```

���ڻ�ȡapplication�����õ�BundleInfo�ͱ����õ�Ability��Ϣ����ȡ��bundleInfo������signatureInfo��applicationInfo��hapModuleInfo��ability��
extensionAbility��permission����Ϣ��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_SIGNATURE_INFO

```TypeScript
GET_BUNDLE_INFO_WITH_SIGNATURE_INFO = 0x00000080
```

���ڻ�ȡ����signatureInfo��bundleInfo����ȡ��bundleInfo������applicationInfo��hapModuleInfo��extensionAbility��ability��permission��
��Ϣ��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_MENU

```TypeScript
GET_BUNDLE_INFO_WITH_MENU = 0x00000100
```

���ڻ�ȡ����fileContextMenuConfig��bundleInfo������ʹ�ò���Ч����Ҫ��GET_BUNDLE_INFO_WITH_HAP_MODULEһ��ʹ�á�

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_ROUTER_MAP

```TypeScript
GET_BUNDLE_INFO_WITH_ROUTER_MAP = 0x00000200
```

���ڻ�ȡ����routerMap��bundleInfo������ʹ�ò���Ч����Ҫ��GET_BUNDLE_INFO_WITH_HAP_MODULEһ��ʹ�á�

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_SKILL

```TypeScript
GET_BUNDLE_INFO_WITH_SKILL = 0x00000800
```

���ڻ�ȡ����skills��bundleInfo������ʹ�ò���Ч����Ҫ��GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_ABILITY��
GET_BUNDLE_INFO_WITH_EXTENSION_ABILITYһ��ʹ�á�

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_ENTRY_MODULE

```TypeScript
GET_BUNDLE_INFO_WITH_ENTRY_MODULE = 0x00010000
```

���ڻ�ȡ����hapModuleInfo��bundleInfo����֧��entryģ���Ӧ��bundleInfo.hapModulesInfo�����entryģ�鲻���ڣ�bundleInfo.hapModulesInfo�б�Ϊ�ա�
��ȡ��bundleInfo������signatureInfo��applicationInfo��ability��extensionAbility��permission����Ϣ��

**起始版本：** 23

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

