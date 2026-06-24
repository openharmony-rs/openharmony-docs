# startShortcutWithReason（系统接口）

## startShortcutWithReason

```TypeScript
function startShortcutWithReason(shortcutInfo: ShortcutInfo, startReason: string, options?: StartOptions): Promise<void>
```

����ָ���Ŀ�ݷ�ʽ��Ϣ�������Ӧ��Ability����Я����ݷ�ʽ������ԭ��ʹ��Promise�첽�ص���

�����𷽿���ͨ��[LaunchParam](arkts-ability-abilityconstant-launchparam-i.md#LaunchParam)��launchReasonMessage�ֶλ�ȡ��
����ԭ�򣬲���������ԭ�����ҵ���߼�������

**起始版本：** 20

**需要权限：** ohos.permission.START_SHORTCUT and ohos.permission.SET_LAUNCH_REASON_MESSAGE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutInfo | ShortcutInfo | 是 | Ӧ�õĿ�ݷ�ʽ��Ϣ�� |
| startReason | string | 是 | ��ݷ�ʽ������ԭ��ȡֵ������<br/>[AbilityConstant.REASON_MESSAGE_DESKTOP_SHORTCUT](../../../../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#����)<br/>����ʾ�����ݷ�ʽ������ |
| options | StartOptions | 否 | ����Ability��Я���Ĳ���������ָ��Ŀ��Ability�Ĵ���ģʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Verify) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not support. |
| [17700065](../../errorcode-universal.md#17700065-The) | The specified shortcut want in shortcut info is not supported to be started. |

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

