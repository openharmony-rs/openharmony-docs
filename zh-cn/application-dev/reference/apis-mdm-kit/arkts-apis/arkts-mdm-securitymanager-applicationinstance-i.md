# ApplicationInstance

Ӧ��ʵ����

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## accountId

```TypeScript
accountId: number
```

Account ID, which must be greater than or equal to 0. You can call
[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2) of
**@ohos.account.osAccount** to obtain the account ID.

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIdentifier

```TypeScript
appIdentifier: string
```

Ӧ��[Ψһ��ʶ��](../../apis-ability-kit/arkts-apis/arkts-ability-signatureinfo-i.md#SignatureInfo)�����Ӧ��û��appIdentifier��ʹ��appId���棬����ͨ���ӿ�
[bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-3)
��ȡbundleInfo.signatureInfo.appIdentifier��bundleInfo.signatureInfo.appId��

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

��ʾ����Ӧ�õ�������Ĭ��ֵΪ0��

appIndexΪ0ʱ����ʾ��Ӧ�á�appIndex����0ʱ����ʾָ���ķ���Ӧ�á�

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

