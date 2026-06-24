# queryApn

## queryApn

```TypeScript
function queryApn(admin: Want, apnInfo: Record<string, string>): Array<string>
```

��ѯ�����ض�APN��Ϣ��APN ID��

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| apnInfo | Record&lt;string, string&gt; | 是 | APN�Ĳ�ѯ������<br/>- apnName��APN���õ����Ʊ�ʶ������ѡ��<br/>- mcc��3λ���ֵ��ƶ����Ҵ��룬��ѡ��<br/>-<br/>mnc��2-3λ���ֵ��ƶ�������룬��ѡ��<br/>- apn����������ƣ���ѡ��<br/>- type��APN�ķ������ͣ���ѡ��<br/>- user��APN������֤���û�������ѡ��<br/>- proxy����ͨ��������<br/>�Ĵ�����������ַ����ѡ��<br/>- mmsproxy�����ŷ����ר�ô�����ַ����ѡ��<br/>- authType��APN����֤Э�����ͣ���ѡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | ����Ҫ���APN ID�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnInfo: Record<string, string> = {
  // 需根据实际情况进行替换
  "apnName": "CTNET",
  "apn": "CTNET",
  "mnc": "11",
  "mcc": "460",
};
try {
  let queryResult: Array<string> = networkManager.queryApn(wantTemp, apnInfo);
  console.info(`Succeeded in querying apn, result : ${JSON.stringify(queryResult)}`);
} catch (err) {
  console.error(`Failed to query apn. Code: ${err.code}, message: ${err.message}`);
}

```


## queryApn

```TypeScript
function queryApn(admin: Want, apnId: string): Record<string, string>
```

��ѯ�ض�APN��APN������Ϣ��

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| apnId | string | 是 | ָ����APN ID������ͨ��<br/>[networkManager.queryApn](arkts-mdm-networkmanager-queryapn-f.md#queryApn-1)��ȡ�豸��Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Record&lt;string, string&gt; | APN parameter information of the specified APN ID.<br/><br/>- **apnName**: APN identifier.<br/><br/>- **mcc**: 3-digit mobile country code (MCC).<br/><br/>- **mnc**: 2-digit or 3-digit mobile network code (MNC).<br/><br/>- **apn**: access point name.<br/><br/>- **type**: APN service type.<br/><br/>- **user**: user name for APN authentication.<br/><br/>- **proxy**: address of the proxy server for a common data connection.<br/><br/>- **mmsproxy**: dedicated proxy address of the MMS service.<br/><br/>- **authType**: authentication protocol type of the APN. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnId: string = "1"; // 需根据实际情况进行替换
try {
  let queryResult: Record<string, string> = networkManager.queryApn(wantTemp, apnId);
  console.info(`Succeeded in querying apn, result : ${JSON.stringify(queryResult)}`);
} catch (err) {
  console.error(`Failed to query apn. Code: ${err.code}, message: ${err.message}`);
}

```

