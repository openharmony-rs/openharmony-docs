# DestroyAppCloneParam（系统接口）

ɾ������Ӧ�ÿ�ָ���Ĳ�����Ϣ��

**起始版本：** 15

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

## userId

```TypeScript
userId?: number
```

ָ��ɾ������Ӧ�����ڵ��û�ID������ͨ��
[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)
��ȡ��Ĭ��ֵ�����÷������û���

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

