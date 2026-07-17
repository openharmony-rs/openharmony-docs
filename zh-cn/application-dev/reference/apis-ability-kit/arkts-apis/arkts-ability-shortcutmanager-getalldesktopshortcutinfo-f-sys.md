# getAllDesktopShortcutInfo（系统接口）

## 导入模块

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

## getAllDesktopShortcutInfo

```TypeScript
function getAllDesktopShortcutInfo(userId: number): Promise<Array<ShortcutInfo>>
```

查询指定用户的所有快捷方式信息。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_SHORTCUTS

<!--Device-shortcutManager-function getAllDesktopShortcutInfo(userId: int): Promise<Array<ShortcutInfo>>--><!--Device-shortcutManager-function getAllDesktopShortcutInfo(userId: int): Promise<Array<ShortcutInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 被查询的用户id。可以通过[getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<ShortcutInfo>> | Promise对象，返回应用配置文件中定义的快捷方式信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

