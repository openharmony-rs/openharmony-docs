# isDefaultApplicationSync

## isDefaultApplicationSync

```TypeScript
function isDefaultApplicationSync(type: string): boolean
```

��ͬ����������ϵͳ�Ѷ����Ӧ�����ͻ���[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor)�����жϵ�ǰӦ���Ƿ��Ǹ����͵�Ĭ��
Ӧ�ã�ʹ��boolean��ʽ���ؽ����

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Ҫ��ѯ��Ӧ�����ͣ�ȡ[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)����<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor)�����е�ֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ���ص�ǰӦ���Ƿ���Ĭ��Ӧ�ã�true��ʾ��Ĭ��Ӧ�ã�false��ʾ����Ĭ��Ӧ�á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';

try {
  let data = defaultAppManager.isDefaultApplicationSync(defaultAppManager.ApplicationType.BROWSER)
  console.info('Operation successful. IsDefaultApplicationSync ? ' + JSON.stringify(data));
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
}

```

