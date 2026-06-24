# getInstalledBundleStorageStats

## getInstalledBundleStorageStats

```TypeScript
function getInstalledBundleStorageStats(admin: Want, bundleNames: Array<string>, accountId: number): Promise<Array<BundleStorageStats>>
```

��ȡ�豸ָ���û����Ѱ�װӦ�õĴ洢ռ����Ϣ��ʹ��Promise�첽�ص���

> **˵����**
>
> 1.���ܻ�ȡ�Ѱ�װӦ�õĴ洢ռ����Ϣ��
>
> 2.bundleNames����Ϊempty��ȫ������δ��װ��Ӧ�ð��������׳�9200012�����롣
>
> 3.bundleNames�������ݵİ�������Ӧ���Ѱ�װ������Ӧ��δ��װʱ���ӿڷ����������Ѱ�װ��Ӧ�÷���ʵ�ʵĴ洢ռ����Ϣ��δ��װ��Ӧ�ô洢ռ����ϢΪ0��
>
> 4.�ýӿ�֧�ֿ��û���ѯ�����������100�û��£���ѯ101�û��µ�ĳЩӦ�õĴ洢ռ����Ϣ��

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleNames | Array&lt;string&gt; | 是 | Ӧ�ð����б���ȡֵ��Χ��С�ڵ���200��Ӧ�ð����� |
| accountId | number | 是 | �˺�ID<br/><br/>ȡֵӦΪ��0��������<br/>- �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleStorageStats&gt;&gt; | Promise���󣬷����Ѱ�װӦ�õĴ洢ռ����Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleNames: Array<string> = ['com.example.app1', 'com.example.app2'];
let accountId: number = 100;
bundleManager.getInstalledBundleStorageStats(wantTemp, bundleNames, accountId).then((result) => {
  console.info('Succeeded in getting installed bundle storage stats.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get installed bundle storage stats. Code is ${err.code}, message is ${err.message}`);
});

```

```TypeScript
// 返回示例
[
  {
    "bundleName": "com.example.edmtest",
    "appSize": 38185408,
    "dataSize": 1216566
  },
  // ...
]

```

