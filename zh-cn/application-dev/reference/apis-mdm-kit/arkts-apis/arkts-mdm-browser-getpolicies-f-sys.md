# getPolicies（系统接口）

## 导入模块

```TypeScript
import { browser } from '@kit.MDMKit';
```

<a id="getpolicies"></a>
## getPolicies

```TypeScript
function getPolicies(admin: Want, appId: string, callback: AsyncCallback<string>): void
```

获取指定浏览器的策略，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** getPolicySync

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-browser-function getPolicies(admin: Want, appId: string, callback: AsyncCallback<string>): void--><!--Device-browser-function getPolicies(admin: Want, appId: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appId | string | 是 | 应用ID，用于指定浏览器。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，当接口调用成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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


<a id="getpolicies-1"></a>
## getPolicies

```TypeScript
function getPolicies(admin: Want, appId: string): Promise<string>
```

获取指定浏览器的策略，使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** getPolicySync

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-browser-function getPolicies(admin: Want, appId: string): Promise<string>--><!--Device-browser-function getPolicies(admin: Want, appId: string): Promise<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appId | string | 是 | 应用ID，用于指定浏览器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回浏览器策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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

