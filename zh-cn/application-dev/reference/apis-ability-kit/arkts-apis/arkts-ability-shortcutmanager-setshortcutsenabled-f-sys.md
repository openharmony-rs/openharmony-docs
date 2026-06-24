# setShortcutsEnabled（系统接口）

## setShortcutsEnabled

```TypeScript
function setShortcutsEnabled(shortcutsInfo: Array<ShortcutInfo>, isEnabled: boolean): Promise<void>
```

�������û���ô���ľ�̬��ݷ�ʽ��ʹ��Promise�첽�ص���

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_SHORTCUTS

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutsInfo | Array&lt;ShortcutInfo&gt; | 是 | �����û���õľ�̬��ݷ�ʽ��<br/>**˵����**<br/>���ӿڲ�������Ӧ�úͷ���Ӧ�ã��ҽ��Ծ�̬��ݷ�ʽ��Ч������<br/>ShortcutInfo�е�appIndex��sourceType���ò���Ч�� |
| isEnabled | boolean | 是 | ��ݷ�ʽ�Ƿ����á�true����ݷ�ʽ���ã�false����ݷ�ʽ���á� |

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
| [17700070](../../errorcode-universal.md#17700070-The) | The specified shortcut id is illegal. |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际的快捷方式id、bundleName。
const bundleName = "com.example.myapplication";
const arrShortcutInfo: Array<shortcutManager.ShortcutInfo> = [
  {
    id: "1",
    bundleName: bundleName,
    appIndex: 0,
    sourceType: 1
  },
  {
    id: "2",
    bundleName: bundleName,
    appIndex: 0,
    sourceType: 1
  }
]

try {
  shortcutManager.setShortcutsEnabled(arrShortcutInfo, false)
    .then(() => {
      console.info('setShortcutsEnabled success');
    }).catch((err: Error) => {
    console.error(`setShortcutsEnabled errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
  });
} catch (err) {
  console.error(`setShortcutsEnabled errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
}

```

