# getInstalledBundleList

## getInstalledBundleList

```TypeScript
function getInstalledBundleList(admin: Want, accountId: number): Promise<Array<BundleInfo>>
```

��ȡ�豸ָ���û����Ѱ�װӦ���б���ʹ��Promise�첽�ص���

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| accountId | number | 是 | �û�ID��ȡֵΪ��������ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleInfo&gt;&gt; | Promise���󣬷����Ѱ�װӦ�ð���Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
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
let accountId: number = 100;
bundleManager.getInstalledBundleList(wantTemp, accountId).then((result) => {
  console.info('Succeeded in getting installed bundle list.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get installed bundle list. Code is ${err.code}, message is ${err.message}`);
});

```


## getInstalledBundleList

```TypeScript
function getInstalledBundleList(admin: Want, accountId: number, bundleInfoGetFlag: number): Promise<Array<BundleInfo>>
```

���ݸ�����bundleInfoGetFlag��ȡ�豸ָ���û����Ѱ�װӦ���б���ʹ��Promise�첽�ص���

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| accountId | number | 是 | �˺�ID<br/><br/>ȡֵӦΪ��0��������<br/>- �û�ID��ȡֵΪ��������ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |
| bundleInfoGetFlag | number | 是 | ָ�����ص�BundleInfo����������Ϣ��<br/><br/>ȡֵ��ΧΪȫ�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleInfo&gt;&gt; | Promise���󣬷����Ѱ�װӦ�ð���Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
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
let accountId: number = 100;
let bundleInfoGetFlag: number = bundleManager.BundleInfoGetFlag.WITH_APPLICATION_INFO
  | bundleManager.BundleInfoGetFlag.WITH_SIGNATURE_INFO;
bundleManager.getInstalledBundleList(wantTemp, accountId, bundleInfoGetFlag).then((result) => {
  console.info('Succeeded in getting installed bundle list.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get installed bundle list. Code is ${err.code}, message is ${err.message}`);
});

```

