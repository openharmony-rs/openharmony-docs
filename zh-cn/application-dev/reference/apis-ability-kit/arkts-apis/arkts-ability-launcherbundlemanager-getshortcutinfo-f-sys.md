# getShortcutInfo（系统接口）

## getShortcutInfo

```TypeScript
function getShortcutInfo(bundleName :string, callback: AsyncCallback<Array<ShortcutInfo>>) : void
```

��ѯ��ǰ�û���ָ��Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��ֻ֧�ֲ�ѯ��Ӧ�õ�ShortcutInfo����ѯ����Ӧ����ʹ��
[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex-1)��ʹ��callback�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| callback | AsyncCallback&lt;Array&lt;ShortcutInfo&gt;&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)�����������óɹ���errΪ<br/>undefined��dataΪ��ǰ�û���ָ��Ӧ�õ�[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��Ϣ������Ϊ������� |

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
  launcherBundleManager.getShortcutInfo("com.example.demo",
    (errData: BusinessError, data: launcherBundleManager.ShortcutInfo[]) => {
      if (errData !== null) {
        console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
      } else {
        console.info('data is ' + JSON.stringify(data));
      }
    });
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}

```


## getShortcutInfo

```TypeScript
function getShortcutInfo(bundleName : string) : Promise<Array<ShortcutInfo>>
```

��ѯ��ǰ�û���ָ��Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��ֻ֧�ֲ�ѯ��Ӧ�õ�ShortcutInfo����ѯ����Ӧ����ʹ��
[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex-1)��ʹ��Promise�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

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
| Promise&lt;Array&lt;ShortcutInfo&gt;&gt; | Promise���󡣷��ص�ǰ�û���ָ��Ӧ�õ�[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)�� |

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
  launcherBundleManager.getShortcutInfo("com.example.demo")
    .then((data: launcherBundleManager.ShortcutInfo[]) => {
      console.info('data is ' + JSON.stringify(data));
    }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  });
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}

```

