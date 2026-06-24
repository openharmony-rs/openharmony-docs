# getAutoStartApps

## getAutoStartApps

```TypeScript
function getAutoStartApps(admin: Want): Array<Want>
```

��ѯ��ǰ�û�����������Ӧ��������

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Want&gt; | Ӧ���������������顣��API version 24��ʼ��֧�ַ����Ƿ�����UI�����á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let res: Array<Want> = applicationManager.getAutoStartApps(wantTemp);
  console.info(`Succeeded in adding auto start apps: ${JSON.stringify(res)}`);
} catch(err) {
  console.error(`Failed to auto start apps. Code: ${err.code}, message: ${err.message}`);
}

```

```TypeScript
// 返回示例
[
  {
    "bundleName": "com.example.edmtest",
    "abilityName": "EntryAbility",
    // 从API version 24支持
    "parameters": {
      "isHiddenStart": false
    }
  },
  // ...
]

```


## getAutoStartApps

```TypeScript
function getAutoStartApps(admin: Want, accountId: number): Array<Want>
```

��ѯָ���û��µĿ���������Ӧ��������

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Want&gt; | Ӧ���������������顣��API version 24��ʼ��֧�ַ����Ƿ�����UI�����á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let res: Array<Want> = applicationManager.getAutoStartApps(wantTemp, 100);
  console.info(`Succeeded in getting auto start apps: ${JSON.stringify(res)}`);
} catch(err) {
  console.error(`Failed to get auto start apps. Code: ${err.code}, message: ${err.message}`);
}

```

```TypeScript
// 返回示例
[
  {
    "bundleName": "com.example.edmtest",
    "abilityName": "EntryAbility",
    // 从API version 24支持
    "parameters": {
      "isHiddenStart": false
    }
  },
  // ...
]

```

