# addDynamicShortcutInfos（系统接口）

## 导入模块

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

## addDynamicShortcutInfos

```TypeScript
function addDynamicShortcutInfos(shortcutInfo: Array<ShortcutInfo>, userId: number): Promise<void>
```

添加指定用户的动态快捷方式。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_SHORTCUTS or (ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

<!--Device-shortcutManager-function addDynamicShortcutInfos(shortcutInfo: Array<ShortcutInfo>, userId: int): Promise<void>--><!--Device-shortcutManager-function addDynamicShortcutInfos(shortcutInfo: Array<ShortcutInfo>, userId: int): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutInfo | Array&lt;ShortcutInfo&gt; | 是 | 待添加的动态快捷方式信息。通过本接口提交时，会做如下校验：</br> 1.ShortcutInfo中的sourceType字段会被设置为2。</br> 2.ShortcutInfo中的moduleName字段在对应的应用中不存在时，会抛出17700002错误码。</br> 3.ShortcutInfo中的hostAbility字段被设置为非空的字符串时，会校验对应的ability是否存在，不存在时，会抛出17700003错误码。 |
| userId | number | 是 | 动态快捷方式所属的用户id。可以通过[getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)获取。默认值：调用方所在用户，取值范围：大于等于0。 |

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
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user id is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |
| [17700070](../errorcode-bundle.md#17700070-指定的快捷方式id不合法) | The specified shortcut id is illegal. |
| [18100001](../errorcode-bundle.md#18100001-shortcutinfo列表中bundlename和appindex不一一对应) | A combination of bundleName and appIndex in the shutcutInfo list is different from the others. |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际的快捷方式id、bundleName、moduleName、userId。
const bundleName = "com.example.dynamic";
let moduleName = 'entry';
const arrShortcutInfo: Array<shortcutManager.ShortcutInfo> = [
  {
    id: "1",
    bundleName: bundleName,
    moduleName: moduleName,
    appIndex: 0,
    sourceType: 2
  },
  {
    id: "2",
    bundleName: bundleName,
    moduleName: moduleName,
    appIndex: 0,
    sourceType: 2
  }
]

try {
  shortcutManager.addDynamicShortcutInfos(arrShortcutInfo, 100)
    .then(() => {
      console.info('addDynamicShortcutInfos success');
    }).catch((err: Error) => {
    console.error(`addDynamicShortcutInfos errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
  });
} catch (err) {
  console.error(`addDynamicShortcutInfos errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
}

```

