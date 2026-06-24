# getPolicies（系统接口）

## getPolicies

```TypeScript
function getPolicies(admin: Want, appId: string, callback: AsyncCallback<string>): void
```

��ȡָ��������Ĳ��ԣ�ʹ��callback�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** getPolicySync

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appId | string | 是 | Ӧ��ID������ָ��������� |
| callback | AsyncCallback&lt;string&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { browser } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 此处参数appId的赋值应替换为开发者自己指定的浏览器的应用ID
let appId: string = 'com.example.******_******/******5t5CoBM=';
browser.getPolicies(wantTemp, appId, (err, result) => {
  if (err) {
    console.error(`Failed to get browser policies. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting  browser policies, result : ${JSON.stringify(result)}`);
});

```


## getPolicies

```TypeScript
function getPolicies(admin: Want, appId: string): Promise<string>
```

��ȡָ��������Ĳ��ԣ�ʹ��Promise�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** getPolicySync

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appId | string | 是 | Ӧ��ID������ָ��������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise���󣬷�����������ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { browser } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 此处参数appId的赋值应替换为开发者自己指定的浏览器的应用ID
let appId: string = 'com.example.******_******/******5t5CoBM=';
browser.getPolicies(wantTemp, appId).then((result) => {
  console.info(`Succeeded in getting browser policies, result : ${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get browser policies. Code is ${err.code}, message is ${err.message}`);
});

```

