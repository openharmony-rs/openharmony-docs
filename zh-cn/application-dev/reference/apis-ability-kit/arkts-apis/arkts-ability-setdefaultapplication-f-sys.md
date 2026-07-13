# setDefaultApplication（系统接口）

## setDefaultApplication

```TypeScript
function setDefaultApplication(type: string, elementName: ElementName, userId: number, callback: AsyncCallback<void>) : void
```

根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者
[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型设置默认应用。使用callback异
步回调。

**起始版本：** 9

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要设置的应用类型，取[ApplicationType](arkts-ability-applicationtype-e.md)中的值，或者符合媒体类型格式的文件类型，或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型。 |
| elementName | ElementName | 是 | 要设置为默认应用的组件信息。 |
| userId | number | 是 | 表示用户ID，可以通过[getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-accountmanager-i.md#getosaccountlocalid-1)获取。 |
| callback | AsyncCallback&lt;void&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md)，当设置默认应用成功时，err返回undefined。否则回调函数返回具体错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |
| [17700028](../errorcode-bundle.md#17700028-输入的ability与type不匹配) | The specified ability does not match the type. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

let userId = 100;
defaultAppManager.setDefaultApplication(defaultAppManager.ApplicationType.BROWSER, {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}, userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

defaultAppManager.setDefaultApplication("image/png", {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}, userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

defaultAppManager.setDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}, userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

```


## setDefaultApplication

```TypeScript
function setDefaultApplication(type: string, elementName: ElementName, callback: AsyncCallback<void>) : void
```

根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者
[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型设置默认应用。使用callback异
步回调。

**起始版本：** 9

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要设置的应用类型，取[ApplicationType](arkts-ability-applicationtype-e.md)中的值，或者符合媒体类型格式的文件类型，或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型。 |
| elementName | ElementName | 是 | 要设置为默认应用的组件信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md)，当设置默认应用成功时，err返回undefined。否则回调函数返回具体错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |
| [17700028](../errorcode-bundle.md#17700028-输入的ability与type不匹配) | The specified ability does not match the type. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

defaultAppManager.setDefaultApplication(defaultAppManager.ApplicationType.BROWSER, {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

defaultAppManager.setDefaultApplication("image/png", {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

defaultAppManager.setDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

```


## setDefaultApplication

```TypeScript
function setDefaultApplication(type: string, elementName: ElementName, userId?: number) : Promise<void>
```

根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者
[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型设置默认应用。使用Promise异步
回调。

**起始版本：** 9

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要设置的应用类型，取[ApplicationType](arkts-ability-applicationtype-e.md)中的值，或者符合媒体类型格式的文件类型，或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型。 |
| elementName | ElementName | 是 | 要设置为默认应用的组件信息。 |
| userId | number | 否 | 表示用户ID，可以通过[getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-accountmanager-i.md#getosaccountlocalid-1)获取。默认值：调用方所在用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |
| [17700028](../errorcode-bundle.md#17700028-输入的ability与type不匹配) | The specified ability does not match the type. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

defaultAppManager.setDefaultApplication(defaultAppManager.ApplicationType.BROWSER, {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}).then((data) => {
  console.info('Operation successful.');
}).catch((error: BusinessError) => {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
});

let userId = 100;
defaultAppManager.setDefaultApplication(defaultAppManager.ApplicationType.BROWSER, {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}, userId).then((data) => {
  console.info('Operation successful.');
}).catch((error: BusinessError) => {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
});

defaultAppManager.setDefaultApplication("image/png", {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}, userId).then((data) => {
  console.info('Operation successful.');
}).catch((error: BusinessError) => {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
});

defaultAppManager.setDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, {
  bundleName: "com.example.myapplication",
  moduleName: "module01",
  abilityName: "EntryAbility"
}, userId).then((data) => {
  console.info('Operation successful.');
}).catch((error: BusinessError) => {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
});

```

