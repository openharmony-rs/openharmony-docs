# InstallParam（系统接口）

Ӧ�ó���װ��ж�ػ�ָ���ָ���Ĳ�����Ϣ��

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## additionalInfo

```TypeScript
additionalInfo?: string
```

Ӧ�ð�װʱ�Ķ�����Ϣ��Ĭ��ֵΪ�գ���󳤶�Ϊ3000�ֽڡ����ֶ�ͨ���ɲ���ϵͳ��Ӫ����Ӧ���г��ڰ�װ��ҵӦ��ʱָ�������ڱ���Ӧ�õĶ�����Ϣ��

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## crowdtestDeadline

```TypeScript
crowdtestDeadline?: number
```

�ڲ��Ľ�ֹ���ڣ�Ĭ��ֵΪ-1����ʾ�޽�ֹ����Լ������λ���롣

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## hashParams

```TypeScript
hashParams?: Array<HashParam>
```

��ϣֵ������Ĭ��ֵΪ�ա�

**类型：** Array<HashParam>

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## installFlag

```TypeScript
installFlag?: number
```

ָʾ��װ��־��ö��ֵ��0x00��Ӧ�ó��ΰ�װ��0x01��Ӧ�ø��ǰ�װ��0x10��Ӧ���ⰲװ��Ĭ��ֵΪӦ�ó��ΰ�װ��

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## isKeepData

```TypeScript
isKeepData?: boolean
```

ж��ʱ�Ƿ�������Ŀ¼��Ĭ��ֵΪfalse��true��ʾж��ʱ��������Ŀ¼��false��ʾж��ʱ����������Ŀ¼��

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
parameters?: Array<Parameters>
```

��չ������Parameters���͵����飬Ĭ��ֵΪ�ա�Parameters.keyȡֵ֧�֣�</br> - "ohos.bms.param.renameInstall"������ӦvalueֵΪ��true������ʾ��װʱʹ�ù���Ŀ¼
����װ����Ӧ��ɳ���ƶ�����װĿ¼������ʹ�ó���Ŀ¼����װ����Ӧ��ɳ�俽������װĿ¼��</br> - "ohos.bms.param.enterpriseForAllUser"������ӦvalueֵΪ��true������ʾ�ڰ�װ��ҵӦ
��ʱΪ�����û���װ���ò���ֻ��[ǩ��֤��ķַ�����](arkts-ability-applicationinfo-i.md#ApplicationInfo)Ϊenterprise_mdm��
enterprise_normal��Ӧ����Ч��</br> - "ohos.bms.param.verifyUninstallRule"������ӦvalueֵΪ��true������ʾ����ж�ش��ù�����������Ӧ��ж�ء�</br> -
"ohos.bms.param.enterpriseManifest"��valueֵΪjson�ļ���ɳ��·����json�ļ����ڴ洢Ӧ�õ������ļ�������Ӧ�ð����ȣ����ֶ�������ҵӦ�ÿ�¡��������¡ʱ������json�ļ����ڣ��򽫾�
����Ӧ�ð�װ���������»����а�װ��</br> - "ohos.bms.param.installBundleName"��valueֵΪӦ�õİ��������ֶ�����Ӧ�ð�װ��������API version 23��ʼ֧�֣��������װʱ����
�˸��ֶΣ�����Ӧ�ð�װ�����е��ýӿ�[getBundleInstallStatus](arkts-ability-bundlemanager-getbundleinstallstatus-f-sys.md#getBundleInstallStatus-1)
�ܹ���ѯ��Ӧ�����ڰ�װ��״̬��</br> - "ohos.bms.param.installAllowDowngrade"������ӦvalueֵΪ��true�������ֶα�ʾ֧��Ӧ�ý�����װ����API version 23��ʼ֧�֣�
�����豸�Ѱ�װ�ϸ߰汾��Ӧ�ã�Ҳ���Ը��ǰ�װ�ϵͰ汾��Ӧ�á���֧��ǩ��֤��ַ�����Ϊapp_gallery����ǩ��֤������Ϊdebug������Ӧ�ý�����װ��ʹ�ý�����װ������Ҫͬʱ����
ohos.permission.INSTALL_BUNDLE��ohos.permission.INSTALL_ALLOW_DOWNGRADEȨ�ޡ�</br> - "
ohos.bms.param.originalInstallSource"������ָ������װӦ�õ�ԭʼ��װ��Դ����Ӧvalueȡֵ��ΧΪ
[ApplicationInfo](arkts-ability-applicationinfo-i.md#ApplicationInfo)�е�installSource�ֶ�ȡֵ��ʹ�øò�����װ��Ӧ�ã��䰲װ��Դ
installSource�ᱻ����Ϊָ����valueֵ��������Ч����������װӦ�ñ���δ���豸�ϰ�װ����valueָ��ΪӦ�ð���ʱ��Ҫ��ָ����Ӧ�ñ����Ѱ�װ��ΪϵͳӦ�á���API version 23��ʼ֧�֡�

**类型：** Array<Parameters>

**起始版本：** 15

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## pgoParams

```TypeScript
pgoParams?: Array<PGOParam>
```

PGO�����ļ�������Ĭ��ֵΪ�ա�

**类型：** Array<PGOParam>

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## sharedBundleDirPaths

```TypeScript
sharedBundleDirPaths?: Array<string>
```

�������ļ�����·����Ĭ��ֵΪ�ա���API version 24��ʼ����ָ��Ŀ¼ʱ��·��Ŀ¼�¿��Դ��ڶ��ͬ��������ͬģ������HSP��API version 23��֮ǰ�汾��·��Ŀ¼��ֻ�ܴ���һ��HSP��

**类型：** Array<string>

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## specifiedDistributionType

```TypeScript
specifiedDistributionType?: string
```

Ӧ�ð�װʱָ����[�ַ�����](../../../../security/app-provision-structure.md)��Ĭ��ֵΪ�գ���󳤶�Ϊ128�ֽڡ����ֶ�ͨ���ɲ���ϵͳ��Ӫ����Ӧ���г�ָ����

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

ָʾ�û�id��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0����ʹ��
[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)
��ȡ��ǰ���������û�������װ��ж�ػ�ָ�һ������Ӧ��ʱ���ò����ᱻ���ԣ����������û���ִ�С�

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## verifyCodeParams

```TypeScript
verifyCodeParams?: Array<VerifyCodeParam>
```

����ǩ���ļ�������Ĭ��ֵΪ�ա�

**˵����**

��API version 10��ʼ֧�֣���API version 11��ʼ����ά����Ӧ�õĴ���ǩ���ļ������ɵ���װ���У�������Ҫͨ�����ӿ�ָ����װ���Ĵ���ǩ���ļ���

**类型：** Array<VerifyCodeParam>

**起始版本：** 10

**废弃版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

