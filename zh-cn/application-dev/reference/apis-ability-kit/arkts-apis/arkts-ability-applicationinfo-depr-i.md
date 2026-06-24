# ApplicationInfo

Ӧ�ó�����Ϣ��δ������˵�������ԣ���ͨ��
[bundle.getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getApplicationInfo-3)
��ȡ��

> **˵����**
>
> ��API version 9��ʼ����ģ�鲻��ά��������ʹ��[bundleManager-ApplicationInfo](arkts-ability-applicationinfo-depr-i.md#ApplicationInfo)�����

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [applicationInfo:ApplicationInfo](arkts-ability-applicationinfo-depr-i.md#ApplicationInfo)

**系统能力：** SystemCapability.BundleManager.BundleFramework

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

Ӧ�ó����accessTokenId��

**类型：** number

**默认值：** Indicates the access token of the application

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessTokenId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## codePath

```TypeScript
readonly codePath: string
```

Ӧ�ó���İ�װĿ¼������ƴ��·��������Դ�ļ�����ʹ��[��Դ�����ӿ�](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#resourceManager)������Դ��

**类型：** string

**默认值：** Indicates the application source code path

**起始版本：** 8

**废弃版本：** 9

**替代接口：** codePath

**系统能力：** SystemCapability.BundleManager.BundleFramework

## description

```TypeScript
readonly description: string
```

Ӧ�ó����������Ϣ��

**类型：** string

**默认值：** Description of application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** description

**系统能力：** SystemCapability.BundleManager.BundleFramework

## descriptionId

```TypeScript
readonly descriptionId: number
```

Ӧ�ó����������Ϣ����ԴID��

**类型：** number

**默认值：** Indicates the description id of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** descriptionId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## enabled

```TypeScript
readonly enabled: boolean
```

�ж�Ӧ�ó����Ƿ����ʹ�ã�ȡֵΪtrue��ʾ����ʹ�ã�ȡֵΪfalse��ʾ����ʹ�á�

**类型：** boolean

**默认值：** Indicates whether or not this application may be instantiated

**起始版本：** 7

**废弃版本：** 9

**替代接口：** enabled

**系统能力：** SystemCapability.BundleManager.BundleFramework

## entityType

```TypeScript
readonly entityType: string
```

Ӧ�ó�������������Ϸ���罻��Ӱ�ӡ����š�

**类型：** string

**默认值：** Indicates entity type of the application

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## entryDir

```TypeScript
readonly entryDir: string
```

Ӧ�ó�����ļ�����·��������ƴ��·��������Դ�ļ�����ʹ��[��Դ�����ӿ�](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#resourceManager)������Դ��

**类型：** string

**默认值：** Indicates the path where the {@code Entry.hap} file of the application is saved

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

Ӧ�ó����ͼ�ꡣ

**类型：** string

**默认值：** Indicates the icon of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** icon

**系统能力：** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: string
```

Ӧ�ó���ͼ�����ԴIDֵ��

**类型：** string

**默认值：** Indicates the icon id of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** iconId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

Ӧ�ó�����ʾ�ı�ǩ��

**类型：** string

**默认值：** Indicates the label of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** label

**系统能力：** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: string
```

Ӧ�ó���ı�ǩ����ԴIDֵ��

**类型：** string

**默认值：** Indicates the label id of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** labelId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## metaData

```TypeScript
readonly metaData: Map<string, Array<CustomizeData>>
```

Ӧ�ó�����Զ���Ԫ��Ϣ��

ͨ������
[bundle.getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getApplicationInfo-3)
�ӿ�ʱ������GET_APPLICATION_INFO_WITH_METADATA��ȡ��

**类型：** Map<string, Array<CustomizeData>>

**默认值：** Indicates the metadata of module

**起始版本：** 8

**废弃版本：** 9

**替代接口：** metadataArray

**系统能力：** SystemCapability.BundleManager.BundleFramework

## moduleInfos

```TypeScript
readonly moduleInfos: Array<ModuleInfo>
```

Ӧ�ó����ģ����Ϣ��

**类型：** Array<ModuleInfo>

**默认值：** Indicates module information about an application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hapModulesInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework

## moduleSourceDirs

```TypeScript
readonly moduleSourceDirs: Array<string>
```

Ӧ�ó������Դ��ŵ����·��������ƴ��·��������Դ�ļ�����ʹ��[��Դ�����ӿ�](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#resourceManager)������Դ��

**类型：** Array<string>

**默认值：** Indicates the path storing the module resources of the application

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

Ӧ�ó�������ơ�

**类型：** string

**默认值：** Indicates the application name, which is the same as {@code bundleName}

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

**系统能力：** SystemCapability.BundleManager.BundleFramework

## permissions

```TypeScript
readonly permissions: Array<string>
```

����Ӧ�ó��������Ȩ�ޡ�

ͨ������
[bundle.getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getApplicationInfo-3)
�ӿ�ʱ������GET_APPLICATION_INFO_WITH_PERMISSION��ȡ��

**类型：** Array<string>

**默认值：** Indicates the permissions required for accessing the application.

**起始版本：** 7

**废弃版本：** 9

**替代接口：** permissions

**系统能力：** SystemCapability.BundleManager.BundleFramework

## process

```TypeScript
readonly process: string
```

Ӧ�ó���Ľ������ơ�

**类型：** string

**默认值：** Process of application, if user do not set it ,the value equal bundleName

**起始版本：** 7

**废弃版本：** 9

**替代接口：** process

**系统能力：** SystemCapability.BundleManager.BundleFramework

## removable

```TypeScript
readonly removable: boolean
```

Ӧ�ó����Ƿ���Ա��Ƴ���ȡֵΪtrue��ʾ���Ա��Ƴ���ȡֵΪfalse��ʾ�����Ա��Ƴ���

**类型：** boolean

**默认值：** Indicates whether or not this application may be removable

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removable

**系统能力：** SystemCapability.BundleManager.BundleFramework

## supportedModes

```TypeScript
readonly supportedModes: number
```

��ʶӦ��֧�ֵ�����ģʽ����ǰֻ�����˼�ʻģʽ��drive�����ñ�ǩֻ�����ڳ�����

**类型：** number

**默认值：** Indicates the running mode supported by the application

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## systemApp

```TypeScript
readonly systemApp: boolean
```

�ж��Ƿ�ΪϵͳӦ�ó���ȡֵΪtrue��ʾϵͳӦ�ã�ȡֵΪfalse��ʾ��ϵͳӦ�á�

**类型：** boolean

**默认值：** Indicates whether the application is a system application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** systemApp

**系统能力：** SystemCapability.BundleManager.BundleFramework

## uid

```TypeScript
readonly uid: number
```

Ӧ�ó����uid��

**类型：** number

**默认值：** Indicates the uid of the application

**起始版本：** 8

**废弃版本：** 9

**替代接口：** uid

**系统能力：** SystemCapability.BundleManager.BundleFramework

