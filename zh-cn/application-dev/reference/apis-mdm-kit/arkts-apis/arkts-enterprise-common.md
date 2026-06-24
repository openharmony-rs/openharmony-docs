# @ohos.enterprise.common

��ģ���ṩMDM Kit�г��ù��������Ĵ����Ͷ��壬����ö�����ͺ����ݽṹ����ģ���������������������������ʵ���߼����ִ�д��롣

> **˵����**
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ApplicationInstance](arkts-mdm-common-applicationinstance-i.md) | Ӧ�õ�ʵ�����ݡ�<br/><br/>�ýӿ�Ŀǰ��[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addUserNonStopApps-1)��<br/>[removeUserNonStopApps](arkts-mdm-applicationmanager-removeusernonstopapps-f.md#removeUserNonStopApps-1)��<br/>[addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addFreezeExemptedApps-1)��<br/>[removeFreezeExemptedApps](arkts-mdm-applicationmanager-removefreezeexemptedapps-f.md#removeFreezeExemptedApps-1)�ӿ�<br/>����Ϊ���ʹ�á�<br/> |
| [InstallationResult](arkts-mdm-common-installationresult-i.md) | Ӧ�ð�װ�����<br/><br/>�ö���Ŀǰ��<br/>[EnterpriseAdminExtensionAbility.onMarketAppInstallResult](arkts-mdm-enterpriseadminextensionability-c.md#onMarketAppInstallResult-1)<br/>��Ϊ�ص����ʹ�á�<br/> |
| [PolicyChangedEvent](arkts-mdm-common-policychangedevent-i.md) | ���Ա���¼�<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ManagedPolicy](arkts-mdm-common-managedpolicy-e.md) | ��ҵ�豸�ܿز��ԡ�<br/> |
| [Result](arkts-mdm-common-result-e.md) | Ӧ�ð�װ����롣<br/> |
| [StartupScene](arkts-mdm-common-startupscene-e.md) | ��������ɳ������˲�ϵͳ���״��л����û���ɣ�����PC����OTA������ɡ��״ο�����ɿ�����ʱ��ͨ��<br/>[onStartupGuideCompleted](arkts-mdm-enterpriseadminextensionability-c.md#onStartupGuideCompleted-1)<br/>�ص��ӿ�֪ͨ�豸����Ӧ�á�<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [EnterpriseAdminExtensionContext](arkts-mdm-common-enterpriseadminextensioncontext-t.md) | EnterpriseAdminExtensionContext��<br/>[EnterpriseAdminExtensionAbility](arkts-mdm-enterpriseadminextensionability-c.md#EnterpriseAdminExtensionAbility)<br/>�������Ļ������̳���[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext)��<br/> |

