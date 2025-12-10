# @ohos.bundle.shortcutManager (shortcutManager模块)(系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

本模块提供系统应用对于快捷方式的增加、删除，以及查询能力，包括[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md)信息的增加、删除以及查询等。

> **说明：**
>
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块为系统接口。

## 导入模块

```ts
import { shortcutManager } from '@kit.AbilityKit';
```


## shortcutManager.addDesktopShortcutInfo<sup>12+</sup>

addDesktopShortcutInfo(shortcutInfo: [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md), userId: number) : Promise\<void>

增加指定用户的快捷方式信息。使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_SHORTCUTS

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名     | 类型   | 必填 | 说明         |
| ---------- | ------ | ---- | -------------- |
| shortcutInfo | [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md) | 是   | 快捷方式信息。 |
| userId     | number | 是   | 用户id。可以通过[getOsAccountLocalId接口](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)获取。|

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.bundle错误码](errorcode-bundle.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700001 | The specified bundle name is not found.  |
| 17700004 | The specified user ID is not found.      |
| 17700026 | The specified bundle is disabled. |
| 17700061 | The specified app index is invalid. |
| 17700070 | The specified shortcut id is illegal. |

**示例：**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ShortcutExample {
  build() {
    Column({ space: 20 }) {
      Row({ space: 20 }) {
        Button('add').onClick(() => {
          let data: shortcutManager.ShortcutInfo = {
            id: "test1",
            bundleName: "com.example.myapplication",
            moduleName: "hello",
            hostAbility: "hello",
            icon: "hello",
            iconId: 1,
            label: "hello",
            labelId: 1,
            wants: [],
            appIndex: 0,
            sourceType: 0,
          }
          try {
            shortcutManager.addDesktopShortcutInfo(data, 100)
              .then(() => {
                console.info("addDesktopShortcutInfo success");
              }).catch((err: BusinessError) => {
              console.error(`addDesktopShortcutInfo errData is errCode:${err.code}  message:${err.message}`);
            });
          } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`addDesktopShortcutInfo error is errCode:${code}  message:${message}`);
          }
        })
      }
    }
  }
}
```

## shortcutManager.deleteDesktopShortcutInfo<sup>12+</sup>

deleteDesktopShortcutInfo(shortcutInfo: [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md), userId: number) : Promise\<void>

删除指定用户的快捷方式信息。使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_SHORTCUTS

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名     | 类型   | 必填 | 说明         |
| ---------- | ------ | ---- | -------------- |
| shortcutInfo | [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md) | 是   | 快捷方式信息。 |
| userId     | number | 是   | 用户id。可以通过[getOsAccountLocalId接口](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)获取。|

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.bundle错误码](errorcode-bundle.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700004 | The specified user ID is not found.       |

**示例：**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ShortcutExample {
  build() {
    Column({ space: 20 }) {
      Row({ space: 20 }) {
        Button('delete').onClick(() => {
          let data: shortcutManager.ShortcutInfo = {
            id: "test1",
            bundleName: "com.example.myapplication",
            moduleName: "",
            hostAbility: "",
            icon: "",
            iconId: 1,
            label: "hello",
            labelId: 1,
            wants: [],
            appIndex: 0,
            sourceType: 0,
          }
          try {
            shortcutManager.deleteDesktopShortcutInfo(data, 100)
              .then(() => {
                console.info("deleteDesktopShortcutInfo success");
              }).catch((err: BusinessError) => {
              console.error(`deleteDesktopShortcutInfo errData is errCode:${err.code}  message:${err.message}`);
            });
          } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`deleteDesktopShortcutInfo error is errCode:${code}  message:${message}`);
          }
        })
      }
    }
  }
}
```

## shortcutManager.getAllDesktopShortcutInfo<sup>12+</sup>

getAllDesktopShortcutInfo(userId: number) : Promise<Array\<[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md)>>

查询指定用户的所有快捷方式信息。

**需要权限：** ohos.permission.MANAGE_SHORTCUTS

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名     | 类型   | 必填 | 说明         |
| ---------- | ------ | ---- | -------------- |
| userId     | number | 是   | 被查询的用户id。可以通过[getOsAccountLocalId接口](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)获取。|

**返回值：**

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise<Array\<[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md)>> | Promise对象，返回应用配置文件中定义的快捷方式信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.bundle错误码](errorcode-bundle.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700004 | The specified user ID is not found.       |

**示例：**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ShortcutExample {
  build() {
    Column({ space: 20 }) {
      Row({ space: 20 }) {
        Button('getall').onClick(() => {
          try {
            shortcutManager.getAllDesktopShortcutInfo(100)
              .then((data: shortcutManager.ShortcutInfo[]) => {
                console.info("Shortcut data is " + JSON.stringify(data));
              }).catch((err: BusinessError) => {
              console.error(`getAllDesktopShortcutInfo errData is errCode:${err.code}  message:${err.message}`);
            });
          } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getAllDesktopShortcutInfo error is errCode:${code}  message:${message}`);
          }
        })
      }
    }
  }
}
```

## shortcutManager.addDynamicShortcutInfos<sup>23+</sup>

addDynamicShortcutInfos(shortcutInfo: Array\<ShortcutInfo>, userId: number): Promise\<void>

添加指定用户的动态快捷方式。

**需要权限：** ohos.permission.MANAGE_SHORTCUTS 或 (ohos.permission.MANAGE_SHORTCUTS 和 ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

 - 添加应用程序所属用户下的动态快捷方式时，需要申请ohos.permission.MANAGE_SHORTCUTS。

 - 添加其他用户下的动态快捷方式时，需要申请ohos.permission.MANAGE_SHORTCUTS和ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名     | 类型   | 必填 | 说明         |
| ---------- | ------ | ---- | -------------- |
|  shortcutInfo   |   Array\<[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md#shortcutinfo-1)>    |   是  |  待添加的动态快捷方式信息。通过本接口提交时，会做如下校验：</br> 1.ShortcutInfo中的sourceType字段会被设置为2。</br> 2.ShortcutInfo中的moduleName字段在对应的应用中不存在时，会抛出17700002错误码。</br> 3.ShortcutInfo中的hostAbility字段被设置为非空的字符串时，会校验对应的ability是否存在，不存在时，会抛出17700003错误码。  |
| userId     | number | 是   | 动态快捷方式所属的用户id。可以通过[getOsAccountLocalId接口](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)获取。默认值：调用方所在用户，取值范围：大于等于0。|

**返回值：**

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[包管理子系统通用错误码](errorcode-bundle.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 801 | Capability not support. |
| 17700001 | The specified bundle name is not found.|
| 17700002 | The specified module name is not found.|
| 17700003 | The specified ability is not found.|
| 17700004 | The specified user ID is not found.|
| 17700026 | The specified bundle is disabled.|
| 17700061 | The specified app index is invalid.|
| 17700070 | The specified shortcut id is illegal.|
| 18100001 | A combination of bundleName and appIndex in the shutcutInfo list is different from the others.|

**示例：**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际的快捷方式id、bundleName、moduleName、userId。
const bundleName = "com.example.dynamic";
let moduleName = 'entry';
const arrShortcutInfo: Array<shortcutManager.ShortcutInfo> = [
  { id: "1", bundleName: bundleName, moduleName: moduleName, appIndex: 0, sourceType: 2 },
  { id: "2", bundleName: bundleName, moduleName: moduleName, appIndex: 0, sourceType: 2 }
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

## shortcutManager.deleteDynamicShortcutInfos<sup>23+</sup>

deleteDynamicShortcutInfos(bundleName: string, appIndex: number, userId: number, ids?: Array\<string>): Promise\<void>

删除指定的动态快捷方式。

**需要权限：** ohos.permission.MANAGE_SHORTCUTS 或 (ohos.permission.MANAGE_SHORTCUTS 和 ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

 - 删除应用程序所属用户下的动态快捷方式，需要ohos.permission.MANAGE_SHORTCUTS权限。

 - 删除其他用户下的动态快捷方式时，需要ohos.permission.MANAGE_SHORTCUTS和ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名     | 类型   | 必填 | 说明         |
| ---------- | ------ | ---- | -------------- |
| bundleName   |   string    |   是  |   要删除的动态快捷方式所属的包名。    |
| appIndex     | number | 是   | 要删除的动态快捷方式所属的分身索引。支持取值为：1、2、3、4、5。 |
| userId     | number | 是   | 要删除的动态快捷方式所属的用户id。可以通过[getOsAccountLocalId接口](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)获取。默认值：调用方所在用户，取值范围：大于等于0。|
| ids     |  Array\<string> | 否   | 要删除的动态快捷方式id列表。缺省或传入列表为空时，表示删除所有符合条件的动态快捷方式。|

**返回值：**

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[包管理子系统通用错误码](errorcode-bundle.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 801 | Capability not support. |
| 17700001 | The specified bundle name is not found.|
| 17700004 | The specified user ID is not found.|
| 17700026 | The specified bundle is disabled.|
| 17700061 | The specified app index is invalid.|
| 17700070 | The specified shortcut id is illegal.|

**示例：**

```ts
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

## shortcutManager.setShortcutsEnabled<sup>23+</sup>

setShortcutsEnabled(shortcutsInfo: Array\<ShortcutInfo>, isEnabled: boolean): Promise\<void>

设置启用或禁用传入的静态快捷方式。使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_SHORTCUTS

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名     | 类型   | 必填 | 说明         |
| ---------- | ------ | ---- | -------------- |
|  shortcutsInfo   |   Array\<[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md#shortcutinfo-1)>    |   是  |  待启用或禁用的静态快捷方式。  |
| isEnabled    | boolean| 是   | 快捷方式是否启用。true：快捷方式启用；false：快捷方式禁用。 |

**返回值：**

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[包管理子系统通用错误码](errorcode-bundle.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 801 | Capability not support. |
| 17700001 | The specified bundle name is not found.|
| 17700070 | The specified shortcut id is illegal.|

**示例：**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际的快捷方式id、bundleName。
const bundleName = "com.example.myapplication";
const arrShortcutInfo: Array<shortcutManager.ShortcutInfo> = [
  { id: "1", bundleName: bundleName, appIndex: 0, sourceType: 1 },
  { id: "2", bundleName: bundleName, appIndex: 0, sourceType: 1 }
]

try {
  shortcutManager.setShortcutsEnabled(arrShortcutInfo, false)
    .then(() => {
      console.info('setShortcutsEnabled success');
    }).catch((err: Error) => {
      console.error(`setShortcutsEnabled errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
    });
} catch (err) {
  console.error(`setShortcutsEnabled errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
}
```