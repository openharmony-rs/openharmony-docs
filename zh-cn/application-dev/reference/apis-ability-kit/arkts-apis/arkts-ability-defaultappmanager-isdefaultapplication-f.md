# isDefaultApplication

## isDefaultApplication

```TypeScript
function isDefaultApplication(type: string, callback: AsyncCallback<boolean>) : void
```

����ϵͳ�Ѷ����Ӧ�����ͻ���[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor)�����жϵ�ǰӦ���Ƿ��Ǹ����͵�Ĭ��Ӧ�á�ʹ��
callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Ҫ��ѯ��Ӧ�����ͣ�ȡ[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)����<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor)�����е�ֵ�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪundefined��dataΪboolֵ<br/>��true��ʾ��Ĭ��Ӧ�ã�false��ʾ����Ĭ��Ӧ�ã�����Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
});

```


## isDefaultApplication

```TypeScript
function isDefaultApplication(type: string) : Promise<boolean>
```

����ϵͳ�Ѷ����Ӧ�����ͻ���[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)�����жϵ�ǰ
Ӧ���Ƿ��Ǹ����͵�Ĭ��Ӧ�á�ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Ҫ��ѯ��Ӧ�����ͣ�ȡ[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)����<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor)�����е�ֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󣬷��ص�ǰӦ���Ƿ���Ĭ��Ӧ�ã�true��ʾ��Ĭ��Ӧ�ã�false��ʾ����Ĭ��Ӧ�á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER)
  .then((data) => {
    console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
});

```

