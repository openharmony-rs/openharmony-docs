# enableAdmin（系统接口）

## enableAdmin

```TypeScript
function enableAdmin(admin: Want, enterpriseInfo: EnterpriseInfo, type: AdminType, callback: AsyncCallback<void>): void
```

����ָ�����豸����Ӧ�á������豸����Ӧ�ý������û���u100���¿ɼ�������Ӧ�ò���ж�أ���[��ҵ�豸������չ����](../../../../mdm/mdm-kit-term.md#��ҵ�豸������չ����)������������������û��л�
��������ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| enterpriseInfo | EnterpriseInfo | 是 | �豸����Ӧ�õ���ҵ��Ϣ�� |
| type | AdminType | 是 | ������豸����Ӧ�����͡� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200003](../../errorcode-universal.md#9200003-The) | The administrator ability component is invalid. |
| [9200004](../../errorcode-universal.md#9200004-Failed) | Failed to activate the administrator application of the device. |
| [9200007](../../errorcode-universal.md#9200007-The) | The system ability works abnormally. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let enterpriseInfo: adminManager.EnterpriseInfo = {
  // 需根据实际情况进行替换
  name: 'enterprise name',
  description: 'enterprise description'
};

adminManager.enableAdmin(wantTemp, enterpriseInfo, adminManager.AdminType.ADMIN_TYPE_SUPER, (err) => {
  if (err) {
    console.error(`Failed to enable admin. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in enabling admin');
});

```


## enableAdmin

```TypeScript
function enableAdmin(admin: Want, enterpriseInfo: EnterpriseInfo, type: AdminType, userId: number, callback: AsyncCallback<void>): void
```

����ָ���û���ͨ��userIdָ������ָ�����豸����Ӧ�ã����г�������Ӧ�ý��������û���u100���±����ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| enterpriseInfo | EnterpriseInfo | 是 | �豸����Ӧ�õ���ҵ��Ϣ�� |
| type | AdminType | 是 | ������豸����Ӧ�����͡� |
| userId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0��<br/>Ĭ��ֵ�����÷������û��� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200003](../../errorcode-universal.md#9200003-The) | The administrator ability component is invalid. |
| [9200004](../../errorcode-universal.md#9200004-Failed) | Failed to activate the administrator application of the device. |
| [9200007](../../errorcode-universal.md#9200007-The) | The system ability works abnormally. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let enterpriseInfo: adminManager.EnterpriseInfo = {
  // 需根据实际情况进行替换
  name: 'enterprise name',
  description: 'enterprise description'
};

adminManager.enableAdmin(wantTemp, enterpriseInfo, adminManager.AdminType.ADMIN_TYPE_NORMAL, 100, (err) => {
  if (err) {
    console.error(`Failed to enable admin. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in enabling admin');
});

```


## enableAdmin

```TypeScript
function enableAdmin(admin: Want, enterpriseInfo: EnterpriseInfo, type: AdminType, userId?: number): Promise<void>
```

���ǰ/ָ���û���ָ�����豸����Ӧ�ã����г�������Ӧ�ý��������û���u100���±����ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| enterpriseInfo | EnterpriseInfo | 是 | �豸����Ӧ�õ���ҵ��Ϣ�� |
| type | AdminType | 是 | ������豸����Ӧ�����͡� |
| userId | number | 否 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>- ���ýӿ�ʱ��������userId����ʾָ���û���<br/>- ���ýӿ�ʱ����δ����userId����ʾ��ǰ�û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵������豸����Ӧ��ʧ��ʱ�����׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200003](../../errorcode-universal.md#9200003-The) | The administrator ability component is invalid. |
| [9200004](../../errorcode-universal.md#9200004-Failed) | Failed to activate the administrator application of the device. |
| [9200007](../../errorcode-universal.md#9200007-The) | The system ability works abnormally. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

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
let enterpriseInfo: adminManager.EnterpriseInfo = {
  // 需根据实际情况进行替换
  name: 'enterprise name',
  description: 'enterprise description'
};

adminManager.enableAdmin(wantTemp, enterpriseInfo, adminManager.AdminType.ADMIN_TYPE_NORMAL, 100).catch(
  (err: BusinessError) => {
    console.error(`Failed to enable admin. Code: ${err.code}, message: ${err.message}`);
  });

```

