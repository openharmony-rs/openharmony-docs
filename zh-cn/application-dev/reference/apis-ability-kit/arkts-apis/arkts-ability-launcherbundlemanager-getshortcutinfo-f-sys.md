# getShortcutInfo（系统接口）

## 导入模块

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
```

## getShortcutInfo

```TypeScript
function getShortcutInfo(bundleName :string, callback: AsyncCallback<Array<ShortcutInfo>>) : void
```

查询当前用户下指定应用的快捷方式信息[ShortcutInfo](arkts-ability-shortcutinfo-i.md)，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。使用callback异步回调。

获取调用方自身的信息时不需要权限。

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ShortcutInfo](arkts-ability-launcherbundlemanager-shortcutinfo-t.md)&gt;&gt; | 是 | [回调函数](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)。当函数调用成功，err为undefined，data为当前用户下指定应用的[ShortcutInfo](arkts-ability-shortcutinfo-i.md)信息。否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not support. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |

**示例**

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


<a id="getshortcutinfo-1"></a>

## getShortcutInfo

```TypeScript
function getShortcutInfo(bundleName : string) : Promise<Array<ShortcutInfo>>
```

查询当前用户下指定应用的快捷方式信息[ShortcutInfo](arkts-ability-shortcutinfo-i.md)，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。使用Promise异步回调。

获取调用方自身的信息时不需要权限。

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ShortcutInfo](arkts-ability-launcherbundlemanager-shortcutinfo-t.md)&gt;&gt; | Promise对象。返回当前用户下指定应用的[ShortcutInfo](arkts-ability-shortcutinfo-i.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not support. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |

**示例**

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
