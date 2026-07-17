# startShortcutWithReason（系统接口）

## 导入模块

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
```

## startShortcutWithReason

```TypeScript
function startShortcutWithReason(shortcutInfo: ShortcutInfo, startReason: string, options?: StartOptions): Promise<void>
```

根据指定的快捷方式信息，拉起对应的Ability，并携带快捷方式的启动原因。使用Promise异步回调。

被拉起方可以通过[LaunchParam](arkts-ability-abilityconstant-launchparam-i.md)的launchReasonMessage字段获取到启动原因，并根据启动原因进行业务逻辑处理。

**起始版本：** 20

**需要权限：** ohos.permission.START_SHORTCUT and ohos.permission.SET_LAUNCH_REASON_MESSAGE

<!--Device-launcherBundleManager-function startShortcutWithReason(shortcutInfo: ShortcutInfo, startReason: string, options?: StartOptions): Promise<void>--><!--Device-launcherBundleManager-function startShortcutWithReason(shortcutInfo: ShortcutInfo, startReason: string, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutInfo | [ShortcutInfo](arkts-ability-shortcutinfo-i-sys.md) | 是 | 应用的快捷方式信息。 |
| startReason | string | 是 | 快捷方式的启动原因，取值包括：[AbilityConstant.REASON_MESSAGE_DESKTOP_SHORTCUT](../../../../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#常量)，表示桌面快捷方式启动。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 否 | 启动Ability所携带的参数，用于指定目标Ability的窗口模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [17700065](../errorcode-bundle.md#17700065-shortcutinfo结构体中指定的want不支持被拉起) | The specified shortcut want in shortcut info is not supported to be started. |

**示例：**

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant } from '@kit.AbilityKit';

try {
  let data: Array<launcherBundleManager.ShortcutInfo> =
    launcherBundleManager.getShortcutInfoSync("com.example.myapplication");
  console.info('startShortcutWithReason data is ' + JSON.stringify(data));
  let startReason = AbilityConstant.REASON_MESSAGE_DESKTOP_SHORTCUT;
  if (data) {
    try {
      launcherBundleManager.startShortcutWithReason(data[0], startReason)
        .then(() => {
          console.info('startShortcutWithReason success');
        }).catch((err: BusinessError) => {
        console.error(`startShortcutWithReason errData is errCode:${err.code}  message:${err.message}`);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`startShortcutWithReason error is errCode:${code}  message:${message}`);
    }
  }
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`startShortcutWithReason errData is errCode:${code}  message:${message}`);
}

```

