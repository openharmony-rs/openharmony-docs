# setScreenLockDisabledForAccount

## setScreenLockDisabledForAccount

```TypeScript
function setScreenLockDisabledForAccount(admin: Want, disable: boolean): void
```

����/���õ�ǰ�û��Ļ�����������������ʱ���豸���������������û���Ҫ����Ļ�ϻ�������ܽ������档����ʱ���豸��������������ֱ�ӽ������档

> **˵����**
>
> 1.�ýӿ����������豸����������ʱ��Ч��
>
> 2.�豸Ĭ���������û���������״̬��
>
> 3.�豸�ϴ�������ʱ�����ý��û���������ʧ�ܣ��׳�9201021�����롣
>
> 4.�·����û��������Ĳ��Ժ��û��������豸���룬��ʱ�������Ч���豸��Ҫ��֤�������ܽ������棬֮ǰ�·��Ĳ���ʧЧ��

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| disable | boolean | 是 | �Ƿ���õ�ǰ�û��Ļ�������������true��ʾ���ã�false��ʾ�����á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9201021](../../errorcode-universal.md#9201021-A) | A lock screen password has been set for the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  securityManager.setScreenLockDisabledForAccount(wantTemp, true);
  console.info(`Succeeded in setting screen lock disabled for account.`);
} catch(err) {
  console.error(`Failed to set screen lock disabled for account. Code: ${err.code}, message: ${err.message}`);
}

```

