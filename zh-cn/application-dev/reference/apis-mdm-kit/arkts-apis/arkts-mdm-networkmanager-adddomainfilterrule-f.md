# addDomainFilterRule

## addDomainFilterRule

```TypeScript
function addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void
```

Ϊ�豸�����������˹���

API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��

��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��

������[Action](arkts-mdm-networkmanager-action-e.md#Action)ΪALLOW����󣬽���Ĭ������DENY���򣬲���ALLOW����֮�ڵ������������ݰ����ᱻ���������ء�

�豸��������������������˹���

> **˵����**
>
> Ϊ����DNS���浼�����ع���ʧЧ������ϵͳ���������������������˹���������DNS���浼������ʧЧ������ϵͳ��������棬�ָ����ع��ܡ�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| domainFilterRule | DomainFilterRule | 是 | �����������˹��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let domainFilterRule: networkManager.DomainFilterRule = {
  // 需根据实际情况进行替换
  "domainName": "www.example.com",
  "appUid": "9696",
  "action": networkManager.Action.DENY,
  "family": 1,
  "logType": networkManager.LogType.NFLOG
};

try {
  networkManager.addDomainFilterRule(wantTemp, domainFilterRule);
  console.info('Succeeded in adding domain filter rules');
} catch (err) {
  console.error(`Failed to add domain filter rules. Code: ${err.code}, message: ${err.message}`);
}

```

