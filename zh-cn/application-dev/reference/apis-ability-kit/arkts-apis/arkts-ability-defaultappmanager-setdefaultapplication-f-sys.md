# setDefaultApplication（系统接口）

## setDefaultApplication

```TypeScript
function setDefaultApplication(type: string, elementName: ElementName, userId: number, callback: AsyncCallback<void>) : void
```

����ϵͳ�Ѷ����Ӧ�����ͻ��߷���ý�����͸�ʽ��type/subtype�����ļ����ͻ���
[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)��������Ĭ��Ӧ�á�ʹ��callback��
���ص���

**起始版本：** 9

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Ҫ���õ�Ӧ�����ͣ�ȡ<br/>[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)�е�ֵ�����߷���ý�����͸�ʽ���ļ����ͣ�����<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)���͡� |
| elementName | ElementName | 是 | Ҫ����ΪĬ��Ӧ�õ������Ϣ�� |
| userId | number | 是 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)��������Ĭ��Ӧ�óɹ�ʱ��err����undefined������ص���������<br/>���������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700025](../../errorcode-universal.md#17700025-The) | The specified type is invalid. |
| [17700028](../../errorcode-universal.md#17700028-The) | The specified ability does not match the type. |

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

����ϵͳ�Ѷ����Ӧ�����ͻ��߷���ý�����͸�ʽ��type/subtype�����ļ����ͻ���
[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)��������Ĭ��Ӧ�á�ʹ��callback��
���ص���

**起始版本：** 9

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Ҫ���õ�Ӧ�����ͣ�ȡ<br/>[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)�е�ֵ�����߷���ý�����͸�ʽ���ļ����ͣ�����<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)���͡� |
| elementName | ElementName | 是 | Ҫ����ΪĬ��Ӧ�õ������Ϣ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)��������Ĭ��Ӧ�óɹ�ʱ��err����undefined������ص���������<br/>���������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700025](../../errorcode-universal.md#17700025-The) | The specified type is invalid. |
| [17700028](../../errorcode-universal.md#17700028-The) | The specified ability does not match the type. |

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

����ϵͳ�Ѷ����Ӧ�����ͻ��߷���ý�����͸�ʽ��type/subtype�����ļ����ͻ���
[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)��������Ĭ��Ӧ�á�ʹ��Promise�첽
�ص���

**起始版本：** 9

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Ҫ���õ�Ӧ�����ͣ�ȡ<br/>[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)�е�ֵ�����߷���ý�����͸�ʽ���ļ����ͣ�����<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)���͡� |
| elementName | ElementName | 是 | Ҫ����ΪĬ��Ӧ�õ������Ϣ�� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700025](../../errorcode-universal.md#17700025-The) | The specified type is invalid. |
| [17700028](../../errorcode-universal.md#17700028-The) | The specified ability does not match the type. |

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

