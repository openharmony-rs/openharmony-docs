# getShortcutInfoSync（系统接口）

## getShortcutInfoSync

```TypeScript
function getShortcutInfoSync(bundleName: string): Array<ShortcutInfo>
```

��ѯ��ǰ�û���ָ��Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��ֻ֧�ֲ�ѯ��Ӧ�õ�ShortcutInfo����ѯ����Ӧ����ʹ��
[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex-1)��

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ShortcutInfo&gt; | Array��ʽ���ص�ǰ�û���ָ��Ӧ�õ�[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Verify) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not support. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = launcherBundleManager.getShortcutInfoSync("com.example.demo");
  console.info('data is ' + JSON.stringify(data));
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}

```


## getShortcutInfoSync

```TypeScript
function getShortcutInfoSync(bundleName: string, userId: number): Array<ShortcutInfo>
```

��ѯָ���û���ָ��Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��ֻ֧�ֲ�ѯ��Ӧ�õ�ShortcutInfo����ѯ����Ӧ����ʹ��
[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex-1)��

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 13

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| userId | number | 是 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ShortcutInfo&gt; | Array��ʽ����ָ���û���ָ��Ӧ�õ�[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Verify) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not support. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = launcherBundleManager.getShortcutInfoSync("com.example.demo", 100);
  console.info('data is ' + JSON.stringify(data));
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}

```

