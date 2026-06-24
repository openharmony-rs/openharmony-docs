# BundleInfo

Ӧ�ð���Ϣ��

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

## appInfo

```TypeScript
readonly appInfo: ApplicationInfo
```

Ӧ�ó����������Ϣ��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_APPLICATION��ȡ��

**类型：** ApplicationInfo

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## buildVersion

```TypeScript
readonly buildVersion?: string
```

Ӧ�ð��Ĺ����汾�ţ����ڱ�ʶ��ͬ�����汾�µĲ�ͬ�����汾������Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�buildVersion�ֶΡ�
**ģ��Լ����** �˽ӿڽ�����Stageģ����ʹ�á�

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## firstInstallTime

```TypeScript
readonly firstInstallTime?: number
```

Ӧ���ڵ�ǰ�豸���״ΰ�װʱ�������ʾ��1970-01-01 08:00:00 UTC+8��ȥ�ĺ���������λ���룬Ԥ��Ӧ�õ��״ΰ�װʱ���Ϊ1533657660000��

**类型：** number

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## hapModulesInfo

```TypeScript
readonly hapModulesInfo: Array<HapModuleInfo>
```

ģ���������Ϣ��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_HAP_MODULE��ȡ��

**类型：** Array<HapModuleInfo>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## installTime

```TypeScript
readonly installTime: number
```

Ӧ�ð���װʱ�������ʾ��1970-01-01 08:00:00 UTC+8��ȥ�ĺ���������λ���롣

**˵����**

�豸�����״ο���ʱ�����δ��ȡ����ǰʱ�䣬����Unixʱ�����׼��1970-01-01 08:00:00 UTC+8����Ϊ��ǰϵͳ����ʼʱ�䡣���磬������δ��ȡ��ʱ�䣬�ȴ�32s֮��װ�ɹ�����Ӧ�ð���װʱ���Ϊ32000��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## minCompatibleVersionCode

```TypeScript
readonly minCompatibleVersionCode: number
```

�ֲ�ʽ�����µ�Ӧ�ð����ݵ���Ͱ汾����Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�minCompatibleVersionCode�ֶΡ�

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Ӧ�ð������ƣ���Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�bundleName�ֶΡ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## permissionGrantStates

```TypeScript
readonly permissionGrantStates: Array<bundleManager.PermissionGrantState>
```

����Ȩ�޵�����״̬��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION��ȡ��reqPermissionDetails�����permissionGrantStates���������˳��һһ��
Ӧ����reqPermissionDetails[2]����Ȩ״̬ΪpermissionGrantStates[2]��

**类型：** Array<bundleManager.PermissionGrantState>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## reqPermissionDetails

```TypeScript
readonly reqPermissionDetails: Array<ReqPermissionDetail>
```

Ӧ������ʱ����ϵͳ�����Ȩ�޼��ϵ���ϸ��Ϣ��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION��ȡ��reqPermissionDetails�����permissionGrantStates���������˳��һһ��
Ӧ����reqPermissionDetails[2]����Ȩ״̬ΪpermissionGrantStates[2]��

**类型：** Array<ReqPermissionDetail>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## routerMap

```TypeScript
readonly routerMap: Array<RouterItem>
```

Ӧ�õ�·�ɱ����ã���hapModulesInfo�µ�routerMap��Ϣ������RouterItem�е�name�ֶν���ȥ�غ�ϲ��õ���ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_HAP_MODULE��GET_BUNDLE_INFO_WITH_ROUTER_MAP��ȡ��

**类型：** Array<RouterItem>

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## signatureInfo

```TypeScript
readonly signatureInfo: SignatureInfo
```

Ӧ�ð���ǩ����Ϣ��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_SIGNATURE_INFO��ȡ��

**类型：** SignatureInfo

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## targetVersion

```TypeScript
readonly targetVersion: number
```

Ӧ������Ŀ��汾����Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�targetAPIVersion�ֶΡ�

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## updateTime

```TypeScript
readonly updateTime: number
```

Ӧ�ð�����ʱ�������ʾ��1970-01-01 08:00:00 UTC+8��ȥ�ĺ���������λ���롣

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## vendor

```TypeScript
readonly vendor: string
```

Ӧ�ð��Ĺ�Ӧ�̣���Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�vendor�ֶΡ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## versionCode

```TypeScript
readonly versionCode: number
```

Ӧ�ð��İ汾�ţ���Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�versionCode�ֶΡ�

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## versionName

```TypeScript
readonly versionName: string
```

Ӧ�ð��İ汾�ı�������Ϣ����Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�versionName�ֶΡ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

