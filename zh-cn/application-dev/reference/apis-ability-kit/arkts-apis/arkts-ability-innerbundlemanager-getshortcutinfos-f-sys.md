# getShortcutInfos（系统接口）

## 导入模块

```TypeScript
import { BundleStatusCallback } from '@kit.AbilityKit';
```

## getShortcutInfos

```TypeScript
function getShortcutInfos(bundleName: string, callback: AsyncCallback<Array<ShortcutInfo>>): void
```

根据给定的Bundle名称获取快捷方式信息，使用callback异步回调。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md#getshortcutinfo-1)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getShortcutInfo(bundleName

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-innerBundleManager-function getShortcutInfos(bundleName: string, callback: AsyncCallback<Array<ShortcutInfo>>): void--><!--Device-innerBundleManager-function getShortcutInfos(bundleName: string, callback: AsyncCallback<Array<ShortcutInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<ShortcutInfo>> | 是 | 程序启动作为入参的回调函数，返回快捷方式信息。 |


## getShortcutInfos

```TypeScript
function getShortcutInfos(bundleName: string): Promise<Array<ShortcutInfo>>
```

根据给定的Bundle名称获取快捷方式信息，使用Promise异步回调。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md#getshortcutinfo-1)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getShortcutInfo(bundleName

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-innerBundleManager-function getShortcutInfos(bundleName: string): Promise<Array<ShortcutInfo>>--><!--Device-innerBundleManager-function getShortcutInfos(bundleName: string): Promise<Array<ShortcutInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<ShortcutInfo>> | Promise形式返回快捷方式信息。 |

