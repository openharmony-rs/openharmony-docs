# isSuperAdmin（系统接口）

## isSuperAdmin

```TypeScript
function isSuperAdmin(bundleName: String, callback: AsyncCallback<boolean>): void
```

����bundleName��ѯ���û���u100���µĳ����豸����Ӧ���Ƿ񱻼��ʹ��callback�첽�ص���

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | String | 是 | �����豸����Ӧ�á� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull��dataΪboolean����ֵ��true��ʾ��ǰ�û���ָ�����豸����Ӧ�ñ����false��ʾ��<br/>ǰ�û���ָ�����豸����Ӧ��δ�������errΪ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';

adminManager.isSuperAdmin(bundleName, (err, result) => {
  if (err) {
    console.error(`Failed to query admin is super admin or not. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying admin is super admin or not, result : ${result}`);
});

```


## isSuperAdmin

```TypeScript
function isSuperAdmin(bundleName: String): Promise<boolean>
```

����bundleName��ѯ���û���u100���µĳ����豸����Ӧ���Ƿ񱻼��ʹ��Promise�첽�ص���

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | String | 是 | �����豸����Ӧ�á� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise����, ����true��ʾָ���ĳ����豸����Ӧ�ñ��������false��ʾָ���ĳ����豸����Ӧ��δ��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';

adminManager.isSuperAdmin(bundleName).then((result) => {
  console.info(`Succeeded in querying admin is super admin or not, result : ${result}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to query admin is super admin or not. Code: ${err.code}, message: ${err.message}`);
});

```

