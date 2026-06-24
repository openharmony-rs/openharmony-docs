# ApplicationInstance

Ӧ�õ�ʵ�����ݡ�

�ýӿ�Ŀǰ��[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addUserNonStopApps-1)��
[removeUserNonStopApps](arkts-mdm-applicationmanager-removeusernonstopapps-f.md#removeUserNonStopApps-1)��
[addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addFreezeExemptedApps-1)��
[removeFreezeExemptedApps](arkts-mdm-applicationmanager-removefreezeexemptedapps-f.md#removeFreezeExemptedApps-1)�ӿ�
����Ϊ���ʹ�á�

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## accountId

```TypeScript
accountId: number
```

�û�ID��ȡֵ��Χ�����ڵ���0��������
accountId����ͨ��[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)��
�ڻ�ȡ��
ȡֵӦΪ��0��������

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIdentifier

```TypeScript
appIdentifier: string
```

Ӧ��[Ψһ��ʶ��](../../apis-ability-kit/arkts-apis/arkts-ability-signatureinfo-i.md#SignatureInfo)������ͨ���ӿ�
[bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-3)
��ȡbundleInfo.signatureInfo.appIdentifier��

**类型：** string

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

Ӧ�÷���������ȡֵ��Χ�����ڵ���0��������
appIndex����ͨ��[getAppCloneIdentity](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getappcloneidentity-f.md#getAppCloneIdentity-1)�ӿڻ�ȡ��
ȡֵ��ΧΪȫ��������

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

