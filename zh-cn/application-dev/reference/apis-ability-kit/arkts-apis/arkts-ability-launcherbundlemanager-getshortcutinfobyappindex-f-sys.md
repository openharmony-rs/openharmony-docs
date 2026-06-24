# getShortcutInfoByAppIndex（系统接口）

## getShortcutInfoByAppIndex

```TypeScript
function getShortcutInfoByAppIndex(bundleName: string, appIndex: number): Array<ShortcutInfo>
```

��ѯ��ǰ�û���ָ������Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��

���÷���ȡ�Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| appIndex | number | 是 | ����Ӧ�õ������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ShortcutInfo&gt; | Array��ʽ���ص�ǰ�û���ָ������Ӧ�õ�[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Verify) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not support. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700061](../../errorcode-universal.md#17700061-The) | The specified app index is invalid. |

**示例：**

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = launcherBundleManager.getShortcutInfoByAppIndex("com.example.demo", 1);
  console.info('getShortcutInfoByAppIndex successfully, data is ' + JSON.stringify(data));
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`Failed to getShortcutInfoByAppIndex. Code: ${code}, message: ${message}`);
}

```

