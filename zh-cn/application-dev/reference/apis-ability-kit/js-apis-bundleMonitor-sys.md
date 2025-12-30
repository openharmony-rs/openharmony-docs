# @ohos.bundle.bundleMonitor (bundleMonitor模块)(系统接口)

本模块提供监听应用安装，卸载，更新的能力。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块为系统接口。

## 导入模块

```ts
import { bundleMonitor } from '@kit.AbilityKit';
```

## BundleChangedInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：**  此接口为系统接口。

| 名称       | 类型   | 只读 | 可选 | 说明                       |
| ---------- | ------ | ---- | ---- | -------------------------- |
| bundleName | string | 是   | 否   | 应用状态发生变化的应用Bundle名称。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| userId     | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 否   | 应用状态发生变化的用户ID，可以通过[getOsAccountLocalId接口](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)获取。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| appIndex<sup>12+</sup>     | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 否   |  应用状态发生变化的应用分身索引。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |

## BundleChangedEvent

监听的事件类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Dyn起始版本：** 9

**系统接口：**  此接口为系统接口。

| 名称       | 说明             |
| ---------- | --------------- |
| add        | 监听应用事件。   |
| update     | 监听更新事件。   |
| remove     | 监听删除事件。   |

## bundleMonitor.on

on(type: BundleChangedEvent, callback: Callback\<BundleChangedInfo>): void

注册监听应用的安装、卸载、更新。
>**说明：**
>
>该方法需要与[bundleMonitor.off](#bundlemonitoroff)配合使用，在组件、页面、应用的生命周期结束时，使用[bundleMonitor.off](#bundlemonitoroff)注销对应用的安装、卸载、更新等事件的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名                       | 类型     | 必填 | 说明               |
| ---------------------------- | -------- | ---- | ------------------ |
| type| [BundleChangedEvent](js-apis-bundleMonitor-sys.md#bundlechangedevent)| 是   | 注册监听的事件类型。 |
| callback | callback\<BundleChangedInfo>| 是   | 注册监听的[回调函数](../apis-basic-services-kit/js-apis-base.md#asynccallback)。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | --------------------------------------|
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

```ts
import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    bundleMonitor.on('add', (bundleChangeInfo) => {
        console.info(`bundleName : ${bundleChangeInfo.bundleName} userId : ${bundleChangeInfo.userId}`);
	})
} catch (errData) {
    let message = (errData as BusinessError).message;
    let errCode = (errData as BusinessError).code;
    console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

## bundleMonitor.onAdd<sup>22+</sup>

onAdd(callback: Callback\<BundleChangedInfo>): void

注册监听应用的安装。
>**说明：**
>
>该方法需要与[bundleMonitor.offAdd](#bundlemonitoroffadd)配合使用，在组件、页面、应用的生命周期结束时，使用[bundleMonitor.offAdd](#bundlemonitoroffadd)注销对应用的安装事件的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on](#bundlemonitoron)。

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                       | 类型     | 必填 | 说明               |
| ---------------------------- | -------- | ---- | ------------------ |
| callback | callback\<BundleChangedInfo>| 是   | 注册监听的[回调函数](../apis-basic-services-kit/js-apis-base.md#asynccallback)。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | --------------------------------------|
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

```ts
'use static'

import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    bundleMonitor.onAdd((bundleChangeInfo) => {
        console.info(`bundleName : ${bundleChangeInfo.bundleName} userId : ${bundleChangeInfo.userId}`);
	})
} catch (errData) {
    let message = (errData as BusinessError).message;
    let errCode = (errData as BusinessError).code;
    console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

## bundleMonitor.onUpdate<sup>22+</sup>

onUpdate(callback: Callback\<BundleChangedInfo>): void

注册监听应用的更新。
>**说明：**
>
>该方法需要与[bundleMonitor.offupdate](#bundlemonitoroffupdate)配合使用，在组件、页面、应用的生命周期结束时，使用[bundleMonitor.offupdate](#bundlemonitoroffupdate)注销对应用的更新事件的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on](#bundlemonitoron)。

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                       | 类型     | 必填 | 说明               |
| ---------------------------- | -------- | ---- | ------------------ |
| callback | callback\<BundleChangedInfo>| 是   | 注册监听的[回调函数](../apis-basic-services-kit/js-apis-base.md#asynccallback)。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | --------------------------------------|
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

```ts
'use static'

import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    bundleMonitor.onUpdate((bundleChangeInfo) => {
        console.info(`bundleName : ${bundleChangeInfo.bundleName} userId : ${bundleChangeInfo.userId}`);
	})
} catch (errData) {
    let message = (errData as BusinessError).message;
    let errCode = (errData as BusinessError).code;
    console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

## bundleMonitor.onRemove<sup>22+</sup>

onRemove(callback: Callback\<BundleChangedInfo>): void

注册监听应用的卸载。
>**说明：**
>
>该方法需要与[bundleMonitor.offRemove](#bundlemonitoroffremove)配合使用，在组件、页面、应用的生命周期结束时，使用[bundleMonitor.offRemove](#bundlemonitoroffremove)注销对应用的卸载事件的监听。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on](#bundlemonitoron)。

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                       | 类型     | 必填 | 说明               |
| ---------------------------- | -------- | ---- | ------------------ |
| callback | callback\<BundleChangedInfo>| 是   | 注册监听的[回调函数](../apis-basic-services-kit/js-apis-base.md#asynccallback)。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | --------------------------------------|
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

```ts
'use static'

import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    bundleMonitor.onRemove((bundleChangeInfo) => {
        console.info(`bundleName : ${bundleChangeInfo.bundleName} userId : ${bundleChangeInfo.userId}`);
	})
} catch (errData) {
    let message = (errData as BusinessError).message;
    let errCode = (errData as BusinessError).code;
    console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

## bundleMonitor.off

off(type: BundleChangedEvent, callback?: Callback\<BundleChangedInfo>): void

注销监听应用的安装，卸载，更新。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名                       | 类型     | 必填 | 说明                                                       |
| ---------------------------- | -------- | ---- | ---------------------------------------------------------- |
| type| [BundleChangedEvent](js-apis-bundleMonitor-sys.md#bundlechangedevent)| 是   | 注销监听的事件类型。                                         |
| callback | callback\<BundleChangedInfo>| 否   | 注销监听的[回调函数](../apis-basic-services-kit/js-apis-base.md#asynccallback)，默认值：注销当前事件的所有callback。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | --------------------------------------|
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

```ts
import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    bundleMonitor.off('add');
} catch (errData) {
    let message = (errData as BusinessError).message;
    let errCode = (errData as BusinessError).code;
    console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

## bundleMonitor.offAdd<sup>22+</sup>

offAdd(callback?: Callback\<BundleChangedInfo>): void

注销监听应用的安装。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off](#bundlemonitoroff)。

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                       | 类型     | 必填 | 说明                                                       |
| ---------------------------- | -------- | ---- | ---------------------------------------------------------- |
| callback | callback\<BundleChangedInfo>| 否   | 注销监听的[回调函数](../apis-basic-services-kit/js-apis-base.md#asynccallback)，默认值：注销当前事件的所有callback。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | --------------------------------------|
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

```ts
'use static'

import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    bundleMonitor.offAdd();
} catch (errData) {
    let message = (errData as BusinessError).message;
    let errCode = (errData as BusinessError).code;
    console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

## bundleMonitor.offUpdate<sup>22+</sup>

offUpdate(callback?: Callback\<BundleChangedInfo>): void

注销监听应用的更新。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off](#bundlemonitoroff)。

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                       | 类型     | 必填 | 说明                                                       |
| ---------------------------- | -------- | ---- | ---------------------------------------------------------- |
| callback | callback\<BundleChangedInfo>| 否   | 注销监听的[回调函数](../apis-basic-services-kit/js-apis-base.md#asynccallback)，默认值：注销当前事件的所有callback。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | --------------------------------------|
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

```ts
'use static'

import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    bundleMonitor.offUpdate();
} catch (errData) {
    let message = (errData as BusinessError).message;
    let errCode = (errData as BusinessError).code;
    console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

## bundleMonitor.offRemove<sup>22+</sup>

offRemove(callback?: Callback\<BundleChangedInfo>): void

注销监听应用的卸载。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off](#bundlemonitoroff)。

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                       | 类型     | 必填 | 说明                                                       |
| ---------------------------- | -------- | ---- | ---------------------------------------------------------- |
| callback | callback\<BundleChangedInfo>| 否   | 注销监听的[回调函数](../apis-basic-services-kit/js-apis-base.md#asynccallback)，默认值：注销当前事件的所有callback。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | --------------------------------------|
| 201 | Verify permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**示例：**

```ts
'use static'

import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    bundleMonitor.offRemove();
} catch (errData) {
    let message = (errData as BusinessError).message;
    let errCode = (errData as BusinessError).code;
    console.error(`errData is errCode:${errCode}  message:${message}`);
}
```