# isAdminEnabled（系统接口）

## isAdminEnabled

```TypeScript
function isAdminEnabled(admin: Want, callback: AsyncCallback<boolean>): void
```

��ѯ��ǰ�û���ָ�����豸����Ӧ���Ƿ񱻼��ʹ��callback�첽�ص���

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull��dataΪbooleanֵ��true��ʾ��ǰ�û���ָ�����豸����Ӧ�ñ����false��ʾ��ǰ��<br/>����ָ�����豸����Ӧ��δ�������errΪ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

adminManager.isAdminEnabled(wantTemp, (err, result) => {
  if (err) {
    console.error(`Failed to query admin is enabled or not. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying admin is enabled or not, result : ${result}`);
});

```


## isAdminEnabled

```TypeScript
function isAdminEnabled(admin: Want, userId: number, callback: AsyncCallback<boolean>): void
```

��ѯָ���û���ͨ��userIdָ������ָ�����豸����Ӧ���Ƿ񱻼��ʹ��callback�첽�ص���

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| userId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0��<br/>Ĭ��ֵ����ǰ�û��� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull��dataΪbooleanֵ��true��ʾ��ǰ�û���ָ�����豸����Ӧ�ñ����false��ʾ��ǰ��<br/>����ָ�����豸����Ӧ��δ�������errΪ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 参数需根据实际情况进行替换
adminManager.isAdminEnabled(wantTemp, 100, (err, result) => {
  if (err) {
    console.error(`Failed to query admin is enabled. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying admin is enabled or not, result : ${result}`);
});

```


## isAdminEnabled

```TypeScript
function isAdminEnabled(admin: Want, userId?: number): Promise<boolean>
```

��ѯ��ǰ/ָ���û���ָ�����豸����Ӧ���Ƿ񱻼��ʹ��Promise�첽�ص���

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| userId | number | 否 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>- ���ýӿ�ʱ��������userId����ʾָ���û���<br/>- ���ýӿ�ʱ����δ����userId����ʾ��ǰ�û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise����, ����true��ʾָ�����豸����Ӧ�ñ��������false��ʾָ�����豸����Ӧ��δ��� |

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

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 参数需根据实际情况进行替换
adminManager.isAdminEnabled(wantTemp, 100).then((result) => {
  console.info(`Succeeded in querying admin is enabled or not, result : ${result}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to query admin is enabled or not. Code: ${err.code}, message: ${err.message}`);
});

```

