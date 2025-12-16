# @ohos.bundle.shortcutManager (shortcutManager) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

The module allows system applications to add, delete, and query shortcuts, including [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { shortcutManager } from '@kit.AbilityKit';
```


## shortcutManager.addDesktopShortcutInfo<sup>12+</sup>

addDesktopShortcutInfo(shortcutInfo: [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md), userId: number) : Promise\<void>

Adds a shortcut for the given user. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_SHORTCUTS

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

**Parameters**

| Name    | Type  | Mandatory| Description        |
| ---------- | ------ | ---- | -------------- |
| shortcutInfo | [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md) | Yes  | Shortcut information.|
| userId     | number | Yes  | User ID, which can be obtained by calling [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9).|

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                                |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700001 | The specified bundle name is not found.  |
| 17700004 | The specified user ID is not found.      |
| 17700026 | The specified bundle is disabled. |
| 17700061 | The specified app index is invalid. |
| 17700070 | The specified shortcut id is illegal. |

**Example**

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

Deletes a shortcut for the given user. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_SHORTCUTS

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

**Parameters**

| Name    | Type  | Mandatory| Description        |
| ---------- | ------ | ---- | -------------- |
| shortcutInfo | [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md) | Yes  | Shortcut information.|
| userId     | number | Yes  | User ID, which can be obtained by calling [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9).|

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                                |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700004 | The specified user ID is not found.       |

**Example**

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

Obtains the information about all shortcuts of the given user.

**Required permissions**: ohos.permission.MANAGE_SHORTCUTS

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

**Parameters**

| Name    | Type  | Mandatory| Description        |
| ---------- | ------ | ---- | -------------- |
| userId     | number | Yes  | User ID, which can be obtained by calling [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9).|

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise<Array\<[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md)>> | Promise that returns the shortcut information defined in the application configuration file.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                                |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700004 | The specified user ID is not found.       |

**Example**

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

Adds dynamic shortcuts for the given user.

**Required permissions**: ohos.permission.MANAGE_SHORTCUTS or a combination of ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

 - To add dynamic shortcuts for the user associated with the application, the ohos.permission.MANAGE_SHORTCUTS permission is required.

 - To add dynamic shortcuts for other users, the ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permissions are required.

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

**Parameters**

| Name    | Type  | Mandatory| Description        |
| ---------- | ------ | ---- | -------------- |
|  shortcutInfo   |   Array\<[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md#shortcutinfo-1)>    |   Yes |  Information about the dynamic shortcuts. When the shortcut information is submitted through this API, the following validations are performed:<br> 1. The **sourceType** field in **ShortcutInfo** is set to **2**.<br> 2. If the **moduleName** field in **ShortcutInfo** does not exist in the corresponding application, error code 17700002 is thrown.<br> 3. If the **hostAbility** field in **ShortcutInfo** is set to a non-empty string, the system checks whether the corresponding ability exists. If it does not exist, error code 17700003 is thrown. |
| userId     | number | Yes  | ID of the user to which the dynamic shortcuts belong. The user ID can be obtained by calling [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). The default value is the user ID of the caller. The value must be greater than or equal to 0.|

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                                |
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

**Example**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use the actual shortcut ID, bundle name, module name, and user ID.
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

Deletes dynamic shortcuts.

**Required permissions**: ohos.permission.MANAGE_SHORTCUTS or a combination of ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

 - To delete dynamic shortcuts for the user associated with the application, the ohos.permission.MANAGE_SHORTCUTS permission is required.

 - To delete dynamic shortcuts for other users, the ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permissions are required.

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

**Parameters**

| Name    | Type  | Mandatory| Description        |
| ---------- | ------ | ---- | -------------- |
| bundleName   |   string    |   Yes |   Bundle name of the application to which the dynamic shortcuts belong.   |
| appIndex     | number | Yes  | Clone index of the application to which the dynamic shortcuts belong. The value can be 1, 2, 3, 4, or 5.|
| userId     | number | Yes  | ID of the user to which the dynamic shortcuts belong. The user ID can be obtained by calling [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). The default value is the user ID of the caller. The value must be greater than or equal to 0.|
| ids     |  Array\<string> | No  | Array of IDs of the dynamic shortcuts to be deleted. If the default value is used or an empty array is passed, all dynamic shortcuts that meet the conditions are deleted.|

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                                |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 801 | Capability not support. |
| 17700001 | The specified bundle name is not found.|
| 17700004 | The specified user ID is not found.|
| 17700026 | The specified bundle is disabled.|
| 17700061 | The specified app index is invalid.|
| 17700070 | The specified shortcut id is illegal.|

**Example**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use the actual shortcut ID, bundle name, and user ID.
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

Enables or disables the specified static shortcuts. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_SHORTCUTS

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

**Parameters**

| Name    | Type  | Mandatory| Description        |
| ---------- | ------ | ---- | -------------- |
|  shortcutsInfo   |   Array\<[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md#shortcutinfo-1)>    |   Yes |  Array of static shortcuts. |
| isEnabled    | boolean| Yes  | Whether to enable the static shortcuts. **true** to enable, **false** otherwise.|

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                                |
| -------- | ---------------------------------------- |
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 801 | Capability not support. |
| 17700001 | The specified bundle name is not found.|
| 17700070 | The specified shortcut id is illegal.|

**Example**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use the actual shortcut ID and bundle name.
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
