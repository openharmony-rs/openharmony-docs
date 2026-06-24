# deleteDynamicShortcutInfos（系统接口）

## deleteDynamicShortcutInfos

```TypeScript
function deleteDynamicShortcutInfos(bundleName: string, appIndex: number, userId: number, ids?: Array<string>): Promise<void>
```

ɾ��ָ���Ķ�̬��ݷ�ʽ��

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_SHORTCUTS or (ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫɾ���Ķ�̬��ݷ�ʽ�����İ����� |
| appIndex | number | 是 | Ҫɾ���Ķ�̬��ݷ�ʽ�����ķ���������֧��ȡֵΪ��1��2��3��4��5�� |
| userId | number | 是 | Ҫɾ���Ķ�̬��ݷ�ʽ�������û�id������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |
| ids | Array&lt;string&gt; | 否 | Ҫɾ���Ķ�̬��ݷ�ʽid�б���ȱʡ�����б�Ϊ��ʱ����ʾɾ�����з��������Ķ�̬��ݷ�ʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user id is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700061](../../errorcode-universal.md#17700061-The) | The specified app index is invalid. |
| [17700070](../../errorcode-universal.md#17700070-The) | The specified shortcut id is illegal. |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际的快捷方式id、bundleName、userId。
const bundleName = "com.example.dynamic";

try {
  shortcutManager.deleteDynamicShortcutInfos(bundleName, 0, 100, ["1", "2"])
    .then(() => {
      console.info('deleteDynamicShortcutInfos success');
    }).catch((err: Error) => {
    console.error(`deleteDynamicShortcutInfos errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
  });
} catch (err) {
  console.error(`deleteDynamicShortcutInfos errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
}

```

