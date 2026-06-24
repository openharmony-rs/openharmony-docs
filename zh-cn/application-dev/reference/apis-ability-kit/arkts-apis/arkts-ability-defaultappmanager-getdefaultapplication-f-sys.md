# getDefaultApplication（系统接口）

## getDefaultApplication

```TypeScript
function getDefaultApplication(type: string, userId: number, callback: AsyncCallback<BundleInfo>) : void
```

����ϵͳ�Ѷ����Ӧ�����ͻ��߷���ý�����͸�ʽ��type/subtype�����ļ����ͻ���
[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)���ͻ�ȡĬ��Ӧ����Ϣ��ʹ��
callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_DEFAULT_APPLICATION

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Ҫ��ѯ��Ӧ�����ͣ�ȡ<br/>[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)�е�ֵ�����߷���ý�����͸�ʽ���ļ����ͣ�����<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)���͡� |
| userId | number | 是 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ�� |
| callback | AsyncCallback&lt;BundleInfo&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪundefined��dataΪ��ȡ<br/>����Ӧ����Ϣ������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700023](../../errorcode-universal.md#17700023-The) | The specified default app does not exist. |
| [17700025](../../errorcode-universal.md#17700025-The) | The specified type is invalid. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

let userId = 100;
defaultAppManager.getDefaultApplication(defaultAppManager.ApplicationType.BROWSER, userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

defaultAppManager.getDefaultApplication("image/png", userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

defaultAppManager.getDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

```


## getDefaultApplication

```TypeScript
function getDefaultApplication(type: string, callback: AsyncCallback<BundleInfo>) : void
```

����ϵͳ�Ѷ����Ӧ�����ͻ��߷���ý�����͸�ʽ��type/subtype�����ļ����ͻ���
[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)���ͻ�ȡĬ��Ӧ����Ϣ��ʹ��
callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_DEFAULT_APPLICATION

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Ҫ��ѯ��Ӧ�����ͣ�ȡ<br/>[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)�е�ֵ�����߷���ý�����͸�ʽ���ļ����ͣ�����<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)���͡� |
| callback | AsyncCallback&lt;BundleInfo&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪundefined��dataΪ��ȡ<br/>����Ӧ����Ϣ������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700023](../../errorcode-universal.md#17700023-The) | The specified default app does not exist. |
| [17700025](../../errorcode-universal.md#17700025-The) | The specified type is invalid. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

defaultAppManager.getDefaultApplication(defaultAppManager.ApplicationType.BROWSER, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

defaultAppManager.getDefaultApplication("image/png", (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

defaultAppManager.getDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. bundleInfo:' + JSON.stringify(data));
});

```


## getDefaultApplication

```TypeScript
function getDefaultApplication(type: string, userId?: number) : Promise<BundleInfo>
```

����ϵͳ�Ѷ����Ӧ�����ͻ��߷���ý�����͸�ʽ��type/subtype�����ļ����ͻ���
[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)���ͻ�ȡĬ��Ӧ����Ϣ��ʹ��Promise
�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_DEFAULT_APPLICATION

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Ҫ��ѯ��Ӧ�����ͣ�ȡ<br/>[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)�е�ֵ�����߷���ý�����͸�ʽ���ļ����ͣ�����<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)���͡� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInfo&gt; | Promise���󣬷���Ĭ��Ӧ�ð���Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700023](../../errorcode-universal.md#17700023-The) | The specified default app does not exist. |
| [17700025](../../errorcode-universal.md#17700025-The) | The specified type is invalid. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

defaultAppManager.getDefaultApplication(defaultAppManager.ApplicationType.BROWSER)
  .then((data) => {
    console.info('Operation successful. bundleInfo: ' + JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });

defaultAppManager.getDefaultApplication("image/png")
  .then((data) => {
    console.info('Operation successful. bundleInfo: ' + JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });

defaultAppManager.getDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI)
  .then((data) => {
    console.info('Operation successful. bundleInfo: ' + JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });

```

