# getApplicationWindowStates

## getApplicationWindowStates

```TypeScript
function getApplicationWindowStates(admin: Want, bundleName: string, appIndex: number): Array<WindowStateInfo>
```

��ѯӦ�ô���״̬

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ��� |
| bundleName | string | 是 | Ӧ�ð��� |
| appIndex | number | 是 | Ӧ�÷�������<br/><br/>ȡֵӦΪ��0�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;WindowStateInfo&gt; | ����Ӧ�ô���״̬��Ϣ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 被查询的应用包名，需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
// 被查询应用的分身索引，需根据实际情况进行替换
let appIndex: number = 0;
try {
  let result: Array<applicationManager.WindowStateInfo> = applicationManager.getApplicationWindowStates(wantTemp, bundleName, appIndex);
  console.info(`Succeeded in getting application window states, result: ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get application window states. Code: ${err.code}, message: ${err.message}`);
}

```

