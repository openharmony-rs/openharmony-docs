# BundleInfo

> **˵����**
>
> ��API version 7��ʼ֧�֣���API version 9��ʼ����������ʹ��[bundleManager-BundleInfo](arkts-ability-bundleinfo-depr-i.md#BundleInfo)�����

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [bundleInfo:BundleInfo](arkts-ability-bundleinfo-depr-i.md#BundleInfo)

**系统能力：** SystemCapability.BundleManager.BundleFramework

## abilityInfos

```TypeScript
readonly abilityInfos: Array<AbilityInfo>
```

Ability��������Ϣ

ͨ������
[bundle.getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getBundleInfo-3)
�ӿ�ʱ������GET_BUNDLE_WITH_ABILITIES��ȡ��

**类型：** Array<AbilityInfo>

**默认值：** Obtains configuration information about an ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** abilitiesInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework

## appId

```TypeScript
readonly appId: string
```

Ӧ�ð���Ӧ�ó����id��

**类型：** string

**默认值：** Indicates the ID of the application to which this bundle belongs
The application ID uniquely identifies an application. It is determined by the bundle name and signature

**起始版本：** 7

**废弃版本：** 9

**替代接口：** appId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## appInfo

```TypeScript
readonly appInfo: ApplicationInfo
```

Ӧ�ó����������Ϣ��

**类型：** ApplicationInfo

**默认值：** Obtains configuration information about an application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** appInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework

## compatibleVersion

```TypeScript
readonly compatibleVersion: number
```

����Ӧ�ð�����Ҫ��͵�SDK�汾�š�

**类型：** number

**默认值：** Indicates the compatible version number of the bundle

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## cpuAbi

```TypeScript
readonly cpuAbi: string
```

Ӧ�ð���cpuAbi��Ϣ��

**类型：** string

**默认值：** Indicates the cpuAbi information of this bundle.

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## entryInstallationFree

```TypeScript
readonly entryInstallationFree: boolean
```

Entry�Ƿ�֧���ⰲװ��ȡֵΪtrue��ʾ֧���ⰲװ��ȡֵΪfalse��ʾ��֧���ⰲװ��

**类型：** boolean

**默认值：** Indicates whether free installation of the entry is supported

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## entryModuleName

```TypeScript
readonly entryModuleName: string
```

Entry��ģ�����ơ�

**类型：** string

**默认值：** Indicates entry module name

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## hapModuleInfos

```TypeScript
readonly hapModuleInfos: Array<HapModuleInfo>
```

ģ���������Ϣ��

**类型：** Array<HapModuleInfo>

**默认值：** Obtains configuration information about a module

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hapModulesInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework

## installTime

```TypeScript
readonly installTime: number
```

HAP��װʱ�䣬��λ�����롣

**类型：** number

**默认值：** Indicates the hap install time

**起始版本：** 7

**废弃版本：** 9

**替代接口：** installTime

**系统能力：** SystemCapability.BundleManager.BundleFramework

## isCompressNativeLibs

```TypeScript
readonly isCompressNativeLibs: boolean
```

�Ƿ�ѹ��Ӧ�ð��ı��ؿ⣬ȡֵΪtrue��ʾѹ��Ӧ�ð��ı��ؿ⣬ȡֵΪfalse��ʾ��ѹ��Ӧ�ð��ı��ؿ⡣

**类型：** boolean

**默认值：** Indicates is compress native libs

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## isSilentInstallation

```TypeScript
readonly isSilentInstallation: string
```

�Ƿ�ͨ����Ĭ��װ��

**类型：** string

**默认值：** Indicates is silent installation

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## minCompatibleVersionCode

```TypeScript
readonly minCompatibleVersionCode: number
```

�ֲ�ʽ�����µ�Ӧ�ð����ݵ���Ͱ汾��

**类型：** number

**默认值：** Indicates the earliest historical version compatible with the bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** minCompatibleVersionCode

**系统能力：** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

Ӧ�ð������ơ�

**类型：** string

**默认值：** Indicates the name of this bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

**系统能力：** SystemCapability.BundleManager.BundleFramework

## reqPermissionDetails

```TypeScript
readonly reqPermissionDetails: Array<ReqPermissionDetail>
```

Ӧ������ʱ����ϵͳ�����Ȩ�޼��ϵ���ϸ��Ϣ

ͨ������
[bundle.getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getBundleInfo-3)
�ӿ�ʱ������GET_BUNDLE_WITH_REQUESTED_PERMISSION��ȡ��

**类型：** Array<ReqPermissionDetail>

**默认值：** Indicates the required permissions details defined in file config.json

**起始版本：** 7

**废弃版本：** 9

**替代接口：** reqPermissionDetails

**系统能力：** SystemCapability.BundleManager.BundleFramework

## reqPermissionStates

```TypeScript
readonly reqPermissionStates: Array<number>
```

����Ȩ�޵�����״̬��0��ʾ����ɹ���-1��ʾ����ʧ�ܡ�

**类型：** Array<number>

**默认值：** Indicates the grant status of required permissions

**起始版本：** 8

**废弃版本：** 9

**替代接口：** permissionGrantStates

**系统能力：** SystemCapability.BundleManager.BundleFramework

## reqPermissions

```TypeScript
readonly reqPermissions: Array<string>
```

Ӧ������ʱ����ϵͳ�����Ȩ�޼���

ͨ������
[bundle.getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getBundleInfo-3)
�ӿ�ʱ������GET_BUNDLE_WITH_REQUESTED_PERMISSION��ȡ��

**类型：** Array<string>

**默认值：** Indicates the required permissions name defined in file config.json

**起始版本：** 7

**废弃版本：** 9

**替代接口：** permissions

**系统能力：** SystemCapability.BundleManager.BundleFramework

## targetVersion

```TypeScript
readonly targetVersion: number
```

����Ӧ�ð�����Ҫ���SDK�汾�š�

**类型：** number

**默认值：** Indicates the target version number of the bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** targetVersion

**系统能力：** SystemCapability.BundleManager.BundleFramework

## type

```TypeScript
readonly type: string
```

Ӧ�ð����͡�

**类型：** string

**默认值：** Indicates the name of this original bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** bundleType

**系统能力：** SystemCapability.BundleManager.BundleFramework

## uid

```TypeScript
readonly uid: number
```

Ӧ�ð���Ӧ�ó����uid��

**类型：** number

**默认值：** Indicates the UID of the application to which this bundle belongs
The UID uniquely identifies an application. It is determined by the process and user IDs of the application
After an application is installed, its UID remains unchanged unless it is uninstalled and then reinstalled

**起始版本：** 7

**废弃版本：** 9

**替代接口：** uid

**系统能力：** SystemCapability.BundleManager.BundleFramework

## updateTime

```TypeScript
readonly updateTime: number
```

HAP����ʱ�䣬��λ�����롣

**类型：** number

**默认值：** Indicates the hap update time

**起始版本：** 7

**废弃版本：** 9

**替代接口：** updateTime

**系统能力：** SystemCapability.BundleManager.BundleFramework

## vendor

```TypeScript
readonly vendor: string
```

Ӧ�ð��Ĺ�Ӧ�̡�

**类型：** string

**默认值：** Describes the bundle vendor

**起始版本：** 7

**废弃版本：** 9

**替代接口：** vendor

**系统能力：** SystemCapability.BundleManager.BundleFramework

## versionCode

```TypeScript
readonly versionCode: number
```

Ӧ�ð��İ汾�š�

**类型：** number

**默认值：** Indicates the version number of the bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** versionCode

**系统能力：** SystemCapability.BundleManager.BundleFramework

## versionName

```TypeScript
readonly versionName: string
```

Ӧ�ð��İ汾�ı�������Ϣ��

**类型：** string

**默认值：** Indicates the text description of the bundle version

**起始版本：** 7

**废弃版本：** 9

**替代接口：** versionName

**系统能力：** SystemCapability.BundleManager.BundleFramework

