# addDynamicShortcutInfos（系统接口）

## addDynamicShortcutInfos

```TypeScript
function addDynamicShortcutInfos(shortcutInfo: Array<ShortcutInfo>, userId: number): Promise<void>
```

����ָ���û��Ķ�̬��ݷ�ʽ��

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_SHORTCUTS or (ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutInfo | Array&lt;ShortcutInfo&gt; | 是 | �����ӵĶ�̬��ݷ�ʽ��Ϣ��ͨ�����ӿ��ύʱ����������У�飺 1.ShortcutInfo�е�sourceType�ֶλᱻ����Ϊ2<br/>�� 2.ShortcutInfo�е�moduleName�ֶ��ڶ�Ӧ��Ӧ���в�����ʱ�����׳�17700002�����롣 3.ShortcutInfo�е�hostAbility�ֶα�����Ϊ�ǿյ��ַ���ʱ����У<br/>���Ӧ��ability�Ƿ���ڣ�������ʱ�����׳�17700003�����롣 |
| userId | number | 是 | ��̬��ݷ�ʽ�������û�id������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

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
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user id is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700061](../../errorcode-universal.md#17700061-The) | The specified app index is invalid. |
| [17700070](../../errorcode-universal.md#17700070-The) | The specified shortcut id is illegal. |
| [18100001](../../errorcode-universal.md#18100001-A) | A combination of bundleName and appIndex in the shutcutInfo list is<br/>different from the others. |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际的快捷方式id、bundleName、moduleName、userId。
const bundleName = "com.example.dynamic";
let moduleName = 'entry';
const arrShortcutInfo: Array<shortcutManager.ShortcutInfo> = [
  {
    id: "1",
    bundleName: bundleName,
    moduleName: moduleName,
    appIndex: 0,
    sourceType: 2
  },
  {
    id: "2",
    bundleName: bundleName,
    moduleName: moduleName,
    appIndex: 0,
    sourceType: 2
  }
]

try {
  shortcutManager.addDynamicShortcutInfos(arrShortcutInfo, 100)
    .then(() => {
      console.info('addDynamicShortcutInfos success');
    }).catch((err: Error) => {
    console.error(`addDynamicShortcutInfos errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
  });
} catch (err) {
  console.error(`addDynamicShortcutInfos errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
}

```

