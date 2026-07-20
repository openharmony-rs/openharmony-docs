# setPolicies（系统接口）

## 导入模块

```TypeScript
import { browser } from '@kit.MDMKit';
```

<a id="setpolicies"></a>
## setPolicies

```TypeScript
function setPolicies(admin: Want, appId: string, policies: string, callback: AsyncCallback<void>): void
```

为指定的浏览器设置浏览策略，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [setPolicySync](arkts-mdm-browser-setpolicysync-f.md#setpolicysync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BROWSER_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-browser-function setPolicies(admin: Want, appId: string, policies: string, callback: AsyncCallback<void>): void--><!--Device-browser-function setPolicies(admin: Want, appId: string, policies: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appId | string | 是 | 应用ID，用于指定浏览器。 |
| policies | string | 是 | 浏览器策略，当参数policies为空字符串时，表示取消指定浏览器的策略。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当接口调用成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
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
let policies: string = '{"InsecurePrivateNetworkRequestsAllowed":{"level":"mandatory","scope":"machine","source":"platform","value":true},"LegacySameSiteCookieBehaviorEnabledForDomainList":{"level":"mandatory","scope":"machine","source":"platform","value":["[*.]"]}}';
browser.setPolicies(wantTemp, appId, policies, (err) => {
  if (err) {
    console.error(`Failed to set browser policies. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in setting browser policies.');
});

```


<a id="setpolicies-1"></a>
## setPolicies

```TypeScript
function setPolicies(admin: Want, appId: string, policies: string): Promise<void>
```

为指定的浏览器设置浏览策略，使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [setPolicySync](arkts-mdm-browser-setpolicysync-f.md#setpolicysync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BROWSER_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-browser-function setPolicies(admin: Want, appId: string, policies: string): Promise<void>--><!--Device-browser-function setPolicies(admin: Want, appId: string, policies: string): Promise<void>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appId | string | 是 | 应用ID，用于指定浏览器。 |
| policies | string | 是 | 浏览器策略，当参数policies为空字符串时，表示取消指定浏览器的策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。当设置浏览器策略失败时，会抛出错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
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
let policies: string = '{"InsecurePrivateNetworkRequestsAllowed":{"level":"mandatory","scope":"machine","source":"platform","value":true},"LegacySameSiteCookieBehaviorEnabledForDomainList":{"level":"mandatory","scope":"machine","source":"platform","value":["[*.]"]}}';
browser.setPolicies(wantTemp, appId, policies).then(() => {
  console.info('Succeeded in setting browser policies.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set browser policies. Code is ${err.code}, message is ${err.message}`);
});

```

