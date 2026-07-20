# startShortcut（系统接口）

## 导入模块

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
```

<a id="startshortcut"></a>
## startShortcut

```TypeScript
function startShortcut(shortcutInfo: ShortcutInfo, options?: StartOptions): Promise<void>
```

拉起指定[ShortcutInfo](arkts-ability-shortcutinfo-i-sys.md)中的ability。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.START_SHORTCUT

<!--Device-launcherBundleManager-function startShortcut(shortcutInfo: ShortcutInfo, options?: StartOptions): Promise<void>--><!--Device-launcherBundleManager-function startShortcut(shortcutInfo: ShortcutInfo, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutInfo | [ShortcutInfo](arkts-ability-shortcutinfo-i-sys.md) | 是 | 应用的快捷方式信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 否 | 启动参数选项，用于指定任务切到前台时的窗口模式，设备ID等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [17700065](../errorcode-bundle.md#17700065-shortcutinfo结构体中指定的want不支持被拉起) | The specified shortcut want in shortcut info is not supported to be started. |

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

