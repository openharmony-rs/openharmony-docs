# getShortcutInfoByAppIndex（系统接口）

## 导入模块

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
```

<a id="getshortcutinfobyappindex"></a>
## getShortcutInfoByAppIndex

```TypeScript
function getShortcutInfoByAppIndex(bundleName: string, appIndex: number): Array<ShortcutInfo>
```

查询当前用户下指定分身应用的快捷方式信息[ShortcutInfo](arkts-ability-shortcutinfo-i-sys.md)。

调用方获取自己的信息时不需要权限。

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-launcherBundleManager-function getShortcutInfoByAppIndex(bundleName: string, appIndex: int): Array<ShortcutInfo>--><!--Device-launcherBundleManager-function getShortcutInfoByAppIndex(bundleName: string, appIndex: int): Array<ShortcutInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| appIndex | number | 是 | 分身应用的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ShortcutInfo&gt; | Array形式返回当前用户下指定分身应用的[ShortcutInfo](arkts-ability-shortcutinfo-i-sys.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |

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

