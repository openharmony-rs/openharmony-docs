# getFreezeExemptedApps

## getFreezeExemptedApps

```TypeScript
function getFreezeExemptedApps(admin: Want): Array<common.ApplicationInstance>
```

��ȡ��ǰ�豸�������û���̨������Ӧ��������

**起始版本：** 22

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common.ApplicationInstance&gt; | Array of the background freeze-exempt application list. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<common.ApplicationInstance> = applicationManager.getFreezeExemptedApps(wantTemp);
  console.info(`Succeeded in getting FreezeExempted applications, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get FreezeExempted applications. Code: ${err.code}, message: ${err.message}`);
}

```

