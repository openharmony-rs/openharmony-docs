# enableAbility（系统接口）

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## enableAbility

```TypeScript
function enableAbility(name: string, capability: Array<accessibility.Capability>): Promise<void>
```

启用辅助扩展。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

<!--Device-config-function enableAbility(name: string, capability: Array<accessibility.Capability>): Promise<void>--><!--Device-config-function enableAbility(name: string, capability: Array<accessibility.Capability>): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 辅助应用的名称，格式为：'bundleName/abilityName'。 |
| capability | Array&lt;accessibility.Capability&gt; | 是 | 辅助应用的能力属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [9300001](../errorcode-accessibility.md#9300001-输入无效的包名称或者ability名称) | Invalid bundle name or ability name. |
| [9300002](../errorcode-accessibility.md#9300002-目标ability已启用) | Target ability already enabled. |

**示例：**

```TypeScript
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];

config.enableAbility(name, capability).then(() => {
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`);
}).catch((err: BusinessError) => {
  console.error(`failed to enable ability, Code is ${err.code}, message is ${err.message}`);
});

```


## enableAbility

```TypeScript
function enableAbility(
    name: string,
    capability: Array<accessibility.Capability>,
    callback: AsyncCallback<void>
  ): void
```

启用辅助扩展，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

<!--Device-config-function enableAbility(    name: string,    capability: Array<accessibility.Capability>,    callback: AsyncCallback<void>  ): void--><!--Device-config-function enableAbility(    name: string,    capability: Array<accessibility.Capability>,    callback: AsyncCallback<void>  ): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 辅助应用的名称，格式为：'bundleName/abilityName'。 |
| capability | Array&lt;accessibility.Capability&gt; | 是 | 辅助应用的能力属性。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [9300001](../errorcode-accessibility.md#9300001-输入无效的包名称或者ability名称) | Invalid bundle name or ability name. |
| [9300002](../errorcode-accessibility.md#9300002-目标ability已启用) | Target ability already enabled. |

**示例：**

```TypeScript
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];

config.enableAbility(name, capability, (err: BusinessError) => {
  if (err) {
    console.error(`failed to enable ability, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`); 
});

```

