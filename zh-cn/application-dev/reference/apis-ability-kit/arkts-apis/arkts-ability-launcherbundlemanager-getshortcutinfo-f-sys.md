# getShortcutInfo（系统接口）

## getShortcutInfo

```TypeScript
function getShortcutInfo(bundleName :string, callback: AsyncCallback<Array<ShortcutInfo>>) : void
```

查询当前用户下指定应用的快捷方式信息[ShortcutInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，只支持查询主应用的ShortcutInfo，查询分身应用请使用 [getShortcutInfoByAppIndex]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。使用callback异步回调。 获取调用方自身的信息时不需要权限。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-launcherBundleManager-function getShortcutInfo(bundleName :string, callback: AsyncCallback<Array<ShortcutInfo>>) : void--><!--Device-launcherBundleManager-function getShortcutInfo(bundleName :string, callback: AsyncCallback<Array<ShortcutInfo>>) : void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;ShortcutInfo&gt;&gt; | 是 | [回调函数]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。当函数调用成功，err为undefined，data为当前用户下指定应用的[ShortcutInfo]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_信息。否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |

**示例：**

ArkTS-Dyn示例:

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

ArkTS-Sta示例:

```TypeScript
'use static'

// 开发者需传入实际工程的bundleName。
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  launcherBundleManager.getShortcutInfo("com.example.demo",
    (errData: BusinessError | null, data: launcherBundleManager.ShortcutInfo[] | undefined) => {
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

查询当前用户下指定应用的快捷方式信息[ShortcutInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，只支持查询主应用的ShortcutInfo，查询分身应用请使用 [getShortcutInfoByAppIndex]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。使用Promise异步回调。 获取调用方自身的信息时不需要权限。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-launcherBundleManager-function getShortcutInfo(bundleName : string) : Promise<Array<ShortcutInfo>>--><!--Device-launcherBundleManager-function getShortcutInfo(bundleName : string) : Promise<Array<ShortcutInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ShortcutInfo&gt;&gt; | Promise对象。返回当前用户下指定应用的[ShortcutInfo]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |

**示例：**

ArkTS-Dyn示例:

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

ArkTS-Sta示例:

```TypeScript
'use static'

// 开发者需传入实际工程的bundleName。
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  launcherBundleManager.getShortcutInfo("com.example.demo")
    .then((data: launcherBundleManager.ShortcutInfo[]) => {
      console.info('data is ' + JSON.stringify(data));
    }).catch ((errData: Error) => {
      console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
    });
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

