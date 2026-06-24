# isByodAdmin

## isByodAdmin

```TypeScript
function isByodAdmin(admin: Want): boolean
```

������ҵ�豸������չ�����ѯ��ǰӦ���Ƿ񱻼���ΪBYOD�豸����Ӧ�á�

**起始版本：** 20

**需要权限：** ohos.permission.START_PROVISIONING_MESSAGE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName����֧�ִ��뵱ǰӦ�õ���ҵ�豸������չ����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ����true��ʾ������ΪBYOD�豸����Ӧ�ã�����false��ʾû�б�����ΪBYOD�豸����Ӧ�á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200012](../../errorcode-universal.md#9200012-The) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { adminManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 请根据实际情况替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: boolean = adminManager.isByodAdmin(wantTemp);
  console.info(`Succeeded in querying admin is byod admin or not : ${result}`);
} catch (error) {
  console.error(`Failed to query admin is byod admin or not. Code is ${error.code}, message is ${error.message}`);
}

```

