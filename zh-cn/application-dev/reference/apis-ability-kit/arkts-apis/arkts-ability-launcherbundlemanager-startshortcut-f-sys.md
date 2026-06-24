# startShortcut（系统接口）

## startShortcut

```TypeScript
function startShortcut(shortcutInfo: ShortcutInfo, options?: StartOptions): Promise<void>
```

����ָ��[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)�е�ability��ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.START_SHORTCUT

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutInfo | ShortcutInfo | 是 | Ӧ�õĿ�ݷ�ʽ��Ϣ�� |
| options | StartOptions | 否 | ��������ѡ�����ָ�������е�ǰ̨ʱ�Ĵ���ģʽ���豸ID�ȡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Verify) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not support. |
| [17700065](../../errorcode-universal.md#17700065-The) | The specified shortcut want in shortcut info is not supported to be started. |

**示例：**

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data: Array<launcherBundleManager.ShortcutInfo> = launcherBundleManager.getShortcutInfoSync("com.example.demo");
  console.info('data is ' + JSON.stringify(data));
  if (data) {
    try {
      launcherBundleManager.startShortcut(data[0])
        .then(() => {
          console.info('startShortcut success');
        }).catch((err: BusinessError) => {
        console.error(`errData is errCode:${err.code}  message:${err.message}`);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`error is errCode:${code}  message:${message}`);
    }
  }
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}

```

