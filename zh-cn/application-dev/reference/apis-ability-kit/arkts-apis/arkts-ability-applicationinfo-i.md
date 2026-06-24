# ApplicationInfo

Ӧ�ó�����Ϣ��

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

Ӧ�ó����accessTokenId��Ӧ�õ����ݱ�ʶ����
[������ʿ���У��ӿ�](../../../../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#checkaccesstoken9)��ʹ�á�

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

Ӧ�ó���ǩ��֤��ķַ����ͣ���Ϊ�� <li>app_gallery��Ӧ���г���װ��Ӧ�á�<!--RP1--><!--RP1End--> <li> enterprise����ҵ�ڲ�Ӧ�ã���ҵ���п�����������ҵ�ڲ�Ա��ʹ�õ�Ӧ�ã���ͨ��
Ӧ���г��ȹ�����������������ͨ����ҵ�Լ������������ڲ��ַ���<!--RP2--><!--RP2End--><li> enterprise_mdm����ҵ
[MDMӦ��](../../../../mdm/mdm-kit-term.md#mdmӦ���豸����Ӧ��)��<!--Del-->��Ҫ������
[����Ա��Ȩ](../../apis-mdm-kit/arkts-apis/arkts-mdm-adminmanager-enableadmin-f-sys.md#enableAdmin-1)
�󣬲��ܰ�װ��ͨ��ҵӦ�á�<!--DelEnd--><!--RP3--><!--RP3End--> <li>enterprise_normal����ͨ��ҵӦ�ã������ϼܻ�ΪӦ���г�����ͨ����ҵ
[MDMӦ��](../../../../mdm/mdm-kit-term.md#mdmӦ���豸����Ӧ��)�Լ����߰�װ���ַ���װ��<!--RP4--><!--RP4End--><li>os_integration��Ԥ��Ӧ�ã�����Ӧ���޷�
�������á�<li>crowdtesting���ڰ�����Ӧ�ã�����Ӧ���г��ַ��������û�����һ������Ч�ڵ��ض�Ӧ�ã�ϵͳ��⵽Ӧ�õ���Ч�ڵ��ں󣬻�֪ͨ�û���Ӧ���г�����release�汾��Ӧ�á���API version 11��ʼ����
����<li>internaltesting��Ӧ���г��ڲ��Ӧ�á�<!--RP5--><!--RP5End--><li>none��������

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

Ӧ�ð��ķ���������ʶ�����ڷ���Ӧ������Ч��

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appProvisionType

```TypeScript
readonly appProvisionType: string
```

Ӧ�ó���ǩ��֤���ļ������ͣ���Ϊdebug��release�������͡�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## bundleType

```TypeScript
readonly bundleType: bundleManager.BundleType
```

��ʶ�������ͣ�ȡֵΪAPP��Ӧ�ã�����ATOMIC_SERVICE��ԭ�ӻ����񣩡�

**类型：** bundleManager.BundleType

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## cloudFileSyncEnabled

```TypeScript
readonly cloudFileSyncEnabled: boolean
```

��ʶ��ǰӦ���Ƿ����ö����ļ�ͬ��������true��ʾ��ǰӦ�����ö����ļ�ͬ��������false��ʾ��ǰӦ�ò����ö����ļ�ͬ��������

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## cloudStructuredDataSyncEnabled

```TypeScript
readonly cloudStructuredDataSyncEnabled?: boolean
```

��ʶ��ǰӦ���Ƿ����ö��ƽṹ������ͬ��������true��ʾ��ǰӦ�����ö��ƽṹ������ͬ��������false��ʾ��ǰӦ�ò����ö��ƽṹ������ͬ��������

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## codePath

```TypeScript
readonly codePath: string
```

Ӧ�ó���İ�װĿ¼��

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## dataUnclearable

```TypeScript
readonly dataUnclearable: boolean
```

��ʶӦ�������Ƿ�ɱ�ɾ����true��ʾ����ɾ����false��ʾ����ɾ����

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## debug

```TypeScript
readonly debug: boolean
```

��ʶӦ���Ƿ��ڵ���ģʽ��ȡֵΪtrue��ʾӦ�ô��ڵ���ģʽ��ȡֵΪfalse��ʾӦ�ô��ڷǵ���ģʽ��

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

��ʶӦ�õ�������Ϣ����Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�description�ֶΡ�����description����ϸ��Ϣ��������е�
descriptionResource�ֶ�˵����

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

��ʶӦ�õ�������Ϣ����Դid���Ǳ��빹��ʱ����Ӧ�����õ�description�Զ����ɵ���Դid��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionResource

```TypeScript
readonly descriptionResource: Resource
```

Ӧ�ó����������Դ��Ϣ�������˸���Դ��Ϣ��bundleName��moduleName �� id�����Ե���ȫ�򻯵Ľӿ�
[getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getMediaContent-5)
����ȡ��ϸ����Դ������Ϣ��

**类型：** Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

�ж�Ӧ�ó����Ƿ����ʹ�ã�ȡֵΪtrue��ʾ����ʹ�ã�ȡֵΪfalse��ʾ����ʹ�á�

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

Ӧ�ó����ͼ�꣬��Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�icon�ֶΡ�����icon����ϸ��Ϣ��������е�iconResource�ֶ�˵����

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

Ӧ�ó���ͼ�����Դid���Ǳ��빹��ʱ����Ӧ�����õ�icon�Զ����ɵ���Դid��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconResource

```TypeScript
readonly iconResource: Resource
```

Ӧ�ó����ͼ����Դ��Ϣ�������˸���Դ��Ϣ��bundleName��moduleName �� id�����Ե���ȫ�򻯵Ľӿ�
[getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getMediaContent-5)
����ȡ��ϸ����Դ������Ϣ��

**类型：** Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## installSource

```TypeScript
readonly installSource: string
```

��ʶӦ�ó���İ�װ��Դ��֧�ֵ�ȡֵ���£�

- pre-installed����ʾ�״ο���ʱ�Ѱ�װ��Ԥ��Ӧ�á�
- ota����ʾϵͳ����ʱ������Ԥ��Ӧ�á�
- recovery����ʾ�û�ж�غ����ֶ��ָ���Ԥ��Ӧ�á�
- bundleName����ʾ�ɴ˰�����Ӧ��Ӧ�ð�װ����bundleName������������ʵ��ֵΪ׼��
- unknown����ʾӦ�ð�װ��Դδ֪��

**类型：** string

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

��ʶӦ�õ����ƣ���Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�label�ֶΡ�����label����ϸ��Ϣ��������е�labelResource�ֶ�
˵������API version 20��ʼ�������ͨ��
[bundleManager.getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md#getAbilityInfo-1)��ȡApplicationInfo
��Ϣ�����ֶ�ΪӦ�ö��û���ʾ�����ƣ���������Դ��������

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

��ʶӦ�����Ƶ���Դid���Ǳ��빹��ʱ����Ӧ�����õ�label�Զ����ɵ���Դid��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelResource

```TypeScript
readonly labelResource: Resource
```

Ӧ�ó����������Դ��Ϣ�������˸���Դ��Ϣ��bundleName��moduleName �� id�����Ե���ȫ�򻯵Ľӿ�
[getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getMediaContent-5)
����ȡ��ϸ����Դ������Ϣ��

**类型：** Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Map<string, Array<Metadata>>
```

Ӧ�ó����Ԫ��Ϣ��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_APPLICATION��GET_BUNDLE_INFO_WITH_METADATA��ȡ��

**˵����** ��API version 9��ʼ֧�֣���API version 10��ʼ����ά��������ʹ��metadataArray�����

**类型：** Map<string, Array<Metadata>>

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [metadataArray](arkts-ability-applicationinfo-i.md#metadataArray)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadataArray

```TypeScript
readonly metadataArray: Array<ModuleMetadata>
```

Ӧ�ó����Ԫ��Ϣ��ͨ������
[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
�ڣ�bundleFlags��������GET_BUNDLE_INFO_WITH_APPLICATION��GET_BUNDLE_INFO_WITH_METADATA��ȡ��

**类型：** Array<ModuleMetadata>

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## multiAppMode

```TypeScript
readonly multiAppMode: MultiAppMode
```

Ӧ�ö࿪ģʽ��

**类型：** MultiAppMode

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Ӧ�ð���bundle���ƣ���Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����bundleName��

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

Ӧ�ó���ı��ؿ��ļ�·����

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

����Ӧ�ó��������Ȩ���б�<!--Del-->������ͨ������
[getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md#getApplicationInfo-2)
�ӿڣ�appFlags��������GET_APPLICATION_INFO_WITH_PERMISSION��ȡ<!--DelEnd-->��

[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)��
��
[getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-2)
�ӿڻ�ȡApplicationInfo��Ϣʱ���᷵�ظ��ֶ����ݣ�����ͨ����ȡ[bundleInfo](arkts-ability-bundleinfo-i.md#BundleInfo).reqPermissionDetails��Ϣ��ȡȨ���б���

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## process

```TypeScript
readonly process: string
```

Ӧ�ó���Ľ������ơ�

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## releaseType

```TypeScript
readonly releaseType: string
```

��ʶӦ�ô��ʱʹ�õ�SDK�ķ������͡���ǰSDK�ķ�������ΪCanary��Beta��Release������Canary��Betaͨ����Ž�һ��ϸ�֣�����Canary1��Canary2��Beta1��Beta2�ȡ������߿�ͨ���Ա�Ӧ�ô�
��������SDK�������ͺ�OS�ķ������ͣ�[deviceInfo.distributionOSReleaseType](../../apis-basic-service-kit/arkts-apis/arkts-deviceinfo.md#deviceInfo)�����жϼ����ԡ�

**类型：** string

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## removable

```TypeScript
readonly removable: boolean
```

Ӧ�ó����Ƿ���Ա��Ƴ���ȡֵΪtrue��ʾ���Ա��Ƴ���ȡֵΪfalse��ʾ�����Ա��Ƴ���

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## systemApp

```TypeScript
readonly systemApp: boolean
```

��ʶӦ���Ƿ�ΪϵͳӦ�ã�ȡֵΪtrue��ʾϵͳӦ�ã�ȡֵΪfalse��ʾ��ϵͳӦ�á�

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## uid

```TypeScript
readonly uid: number
```

Ӧ�ó����UID��

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

