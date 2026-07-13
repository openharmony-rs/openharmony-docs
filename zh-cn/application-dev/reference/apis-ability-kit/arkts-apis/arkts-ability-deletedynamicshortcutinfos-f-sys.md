# deleteDynamicShortcutInfos（系统接口）

## deleteDynamicShortcutInfos

```TypeScript
function deleteDynamicShortcutInfos(bundleName: string, appIndex: number, userId: number, ids?: Array<string>): Promise<void>
```

删除指定的动态快捷方式。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_SHORTCUTS or (ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要删除的动态快捷方式所属的包名。 |
| appIndex | number | 是 | 要删除的动态快捷方式所属的分身索引。支持取值为：1、2、3、4、5。 |
| userId | number | 是 | 要删除的动态快捷方式所属的用户id。可以通过[getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-accountmanager-i.md#getosaccountlocalid-1)获取。默认值：调用方所在用户，取值范围：大于等于0。 |
| ids | Array&lt;string&gt; | 否 | 要删除的动态快捷方式id列表。缺省或传入列表为空时，表示删除所有符合条件的动态快捷方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user id is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |
| [17700070](../errorcode-bundle.md#17700070-指定的快捷方式id不合法) | The specified shortcut id is illegal. |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际的快捷方式id、bundleName、userId。
const bundleName = "com.example.dynamic";

try {
  shortcutManager.deleteDynamicShortcutInfos(bundleName, 0, 100, ["1", "2"])
    .then(() => {
      console.info('deleteDynamicShortcutInfos success');
    }).catch((err: Error) => {
    console.error(`deleteDynamicShortcutInfos errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
  });
} catch (err) {
  console.error(`deleteDynamicShortcutInfos errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
}

```

