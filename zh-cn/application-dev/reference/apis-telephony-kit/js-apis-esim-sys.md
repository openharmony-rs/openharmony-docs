# @ohos.telephony.esim (eSIM卡管理) (系统接口)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @yangyannanyangyannan-->
<!--Designer: @ghxbob-->
<!--Tester: @weitiantian-->
<!--Adviser: @zhang_yixin13-->

穿戴设备支持eSIM，电话服务提供API给eSIM卡管理和eSIM卡服务使用。

> **说明：**
>
> 本模块首批接口从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.telephony.esim (eSIM卡管理)](js-apis-esim.md)。

## 导入模块

```ts
import { eSIM } from '@kit.TelephonyKit';
```

## eSIM.getEid

getEid\(slotId: number\): Promise\<string\>

获取指定卡槽标识eUICC硬件的EID。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.GET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型   | 必填 | 说明                                     |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。   |

**返回值：**

| 类型                  | 说明                                |
| --------------------- | ---------------------------------- |
| Promise\<string\> | 返回指定卡槽标识eUICC硬件的EID。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                         |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { eSIM } from '@kit.TelephonyKit';

eSIM.getEid(1).then((eid) => {
    console.info(`the EID is:` + eid);
}).catch((err:BusinessError<void>) => {
    console.error(`getEid, promise: err->${JSON.stringify(err)}`)
});
```

## eSIM.getOsuStatus

getOsuStatus\(slotId: number\): Promise\<OsuStatus\>

获取指定卡槽操作系统升级的状态。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.GET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[OsuStatus](#osustatus)\> |  Promise对象，返回操作系统升级的状态。<br/> 1. 正在升级。 <br/>   2. 升级失败。<br/>  3. 升级成功。<br/>  4. 当前版本是最新版本。<br/> 5. 升级服务不可用。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getOsuStatus(1).then(() => {
    console.info(`getOsuStatus invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`getOsuStatus, promise: err->${JSON.stringify(err)}`);
});
```

## eSIM.startOsu

startOsu\(slotId: number\): Promise\<OsuStatus\>

如果指定卡槽的操作系统不是最新的，则执行操作系统升级。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[OsuStatus](#osustatus)\> |  Promise对象，返回操作系统升级的状态。<br/> 1. 正在升级。 <br/>   2. 升级失败。<br/>  3. 升级成功。<br/>  4. 当前版本是最新版本。<br/> 5. 升级服务不可用。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.startOsu(1).then(() => {
    console.info(`startOsu invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`startOsu, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.getDownloadableProfileMetadata

getDownloadableProfileMetadata\(slotId: number, portIndex: number, profile: DownloadableProfile, forceDisableProfile: boolean\): Promise\<GetDownloadableProfileMetadataResult\>

填充可下载配置文件的元数据。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明                                                                                                   |
| ------ | ------ | ----- |------------------------------------------------------------------------------------------------------|
| slotId              | number                                        | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。                                                                      |
| portIndex           | number                                        | 是 | 插槽的端口索引。                                                                                             |
| profile             | [DownloadableProfile](./js-apis-esim.md#downloadableprofile) | 是 | 可下载的配置文件信息。                                                                                          |
| forceDisableProfile | boolean | 是 | 是否可直接去激活配置文件。true表示切换配置文件时，如果需要去激活当前的配置文件，则可以直接操作。false表示如果需要去激活当前的配置文件，则会返回错误，并得到用户授权后再继续调用该接口，执行切换配置文件操作。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[GetDownloadableProfileMetadataResult](#getdownloadableprofilemetadataresult)\> | Promise对象，返回填充可下载配置文件的元数据。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

let profile: eSIM.DownloadableProfile = {
  activationCode:'1',
  confirmationCode:'1',
  carrierName:'test',
  accessRules:[{
    certificateHashHexStr:'test',
    packageName:'com.example.testcoreservice',
    accessType:0
  }]
};

eSIM.getDownloadableProfileMetadata(1, 0, profile, true).then((data: eSIM.GetDownloadableProfileMetadataResult) => {
    console.info(`getDownloadableProfileMetadata, GetDownloadableProfileMetadataResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getDownloadableProfileMetadata, GetDownloadableProfileMetadataResult: err->${JSON.stringify(err)}`);
});
```

## eSIM.getDownloadableProfiles

getDownloadableProfiles\(slotId: number, portIndex: number,
forceDisableProfile: boolean\): Promise\<GetDownloadableProfilesResult\>

获取可用的可下载配置文件列表。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.GET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId              | number  | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| portIndex           | number  | 是 | 插槽的端口索引。 |
| forceDisableProfile | boolean | 是 | 是否可直接去激活配置文件。true表示切换配置文件时，如果需要去激活当前的配置文件，则可以直接操作。false表示如果需要去激活当前的配置文件，则会返回错误，并得到用户授权后再继续调用该接口，执行切换配置文件操作。|

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[GetDownloadableProfilesResult](#getdownloadableprofilesresult)\> | Promise对象，返回可下载配置文件列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getDownloadableProfiles(1, 0, true).then((data: eSIM.GetDownloadableProfilesResult) => {
    console.info(`getDownloadableProfiles, GetDownloadableProfilesResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getDownloadableProfiles, GetDownloadableProfilesResult: err->${JSON.stringify(err)}`);
});
```

## eSIM.downloadProfile

downloadProfile\(slotId: number, portIndex: number, profile: DownloadableProfile,
configuration: DownloadConfiguration\): Promise\<DownloadProfileResult\>

下载配置文件。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId        | number                                            | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| portIndex     | number                                            | 是 | 插槽的端口索引。 |
| profile       | [DownloadableProfile](./js-apis-esim.md#downloadableprofile)     | 是 | 可下载的配置文件信息。 |
| configuration | [DownloadConfiguration](#downloadconfiguration) | 是 | 下载的配置信息。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[DownloadProfileResult](#downloadprofileresult)\> | Promise对象，返回下载配置文件的结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

let profile: eSIM.DownloadableProfile = {
  activationCode:'1',
  confirmationCode:'1',
  carrierName:'test',
  accessRules:[{
    certificateHashHexStr:'test',
    packageName:'com.example.testcoreservice',
    accessType:0
  }]
};

let configuration: eSIM.DownloadConfiguration = {
  switchAfterDownload: true,
  forceDisableProfile: true,
  isPprAllowed: true,
};

eSIM.downloadProfile(1, 0, profile, configuration).then((data: eSIM.DownloadProfileResult) => {
    console.info(`downloadProfile, DownloadProfileResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`downloadProfile, DownloadProfileResult: err->${JSON.stringify(err)}`);
});
```

## eSIM.getEuiccProfileInfoList

getEuiccProfileInfoList\(slotId: number\): Promise\<GetEuiccProfileInfoListResult\>

获取配置文件信息列表。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.GET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId | number | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[GetEuiccProfileInfoListResult](#geteuiccprofileinfolistresult)\> | Promise对象，返回配置文件信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getEuiccProfileInfoList(1).then((data: eSIM.GetEuiccProfileInfoListResult) => {
    console.info(`getEuiccProfileInfoList, GetEuiccProfileInfoListResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getEuiccProfileInfoList, GetEuiccProfileInfoListResult: err->${JSON.stringify(err)}`);
});
```

## eSIM.getEuiccInfo

getEuiccInfo\(slotId: number\): Promise\<EuiccInfo\>

获取eUICC信息。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.GET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId | number | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[EuiccInfo](#euiccinfo)\> | Promise对象，返回eUicc信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getEuiccInfo(1).then((data: eSIM.EuiccInfo) => {
    console.info(`getEuiccInfo, EuiccInfo: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getEuiccInfo, EuiccInfo: err->${JSON.stringify(err)}`);
});
```

## eSIM.deleteProfile

deleteProfile\(slotId: number, iccid: string\): Promise\<ResultCode\>

删除配置文件。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId | number | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| iccid  | string | 是 | 配置文件的ID。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode)\> | Promise对象，返回删除配置文件的结果码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.deleteProfile(1, 'testId').then(() => {
    console.info(`deleteProfile invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`deleteProfile, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.switchToProfile

switchToProfile\(slotId: number, portIndex: number, iccid: string,
forceDisableProfile: boolean\): Promise\<ResultCode\>

切换到(启用)给定的配置文件。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId              | number  | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| portIndex           | number  | 是 | 插槽的端口索引。 |
| iccid               | string  | 是 | 配置文件的ID。   |
| forceDisableProfile | boolean | 是 | 是否可直接去激活配置文件。true表示切换配置文件时，如果需要去激活当前的配置文件，则可以直接操作。false表示如果需要去激活当前的配置文件，则会返回错误，并得到用户授权后再继续调用该接口，执行切换配置文件操作。|

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode)\> | Promise对象，返回切换配置文件的结果码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.switchToProfile(1, 0, 'testId', true).then(() => {
    console.info(`switchToProfile invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`switchToProfile, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.setProfileNickname

setProfileNickname\(slotId: number, iccid: string, nickname: string\): Promise\<ResultCode\>

设置给定配置文件的昵称。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId   | number | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| iccid    | string | 是 | 配置文件的ID。 |
| nickname | string | 是 | 昵称。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode)\> | Promise对象，返回设置昵称的结果码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.setProfileNickname(1, 'testId', 'testName').then(() => {
    console.info(`setProfileNickname invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`setProfileNickname, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.resetMemory

resetMemory\(slotId: number, options?: ResetOption\): Promise\<ResultCode\>

清除所有特定配置文件并重置eUICC。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId  | number                        | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| options | [ResetOption](#resetoption) | 否 | 重置状态。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode)\> | Promise对象，返回重置的结果码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.resetMemory(1).then(() => {
    console.info(`resetMemory invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`resetMemory, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.reserveProfilesForFactoryRestore

reserveProfilesForFactoryRestore\(slotId: number\): Promise\<ResultCode\>

恢复出厂设置，并保留profiles。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId | number | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode)\> | Promise对象，返回恢复出厂设置的结果码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.reserveProfilesForFactoryRestore(1).then(() => {
    console.info(`reserveProfilesForFactoryRestore invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`reserveProfilesForFactoryRestore, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.setDefaultSmdpAddress

setDefaultSmdpAddress\(slotId: number, address: string\): Promise\<ResultCode\>

设置或更新eUICC中存储的默认SM-DP+地址。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId  | number | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| address | string | 是 | 要设置的默认SM-DP+地址。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode)\> | Promise对象，返回设置默认SM-DP+地址的结果码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.setDefaultSmdpAddress(1, 'testAddress').then(() => {
    console.info(`setDefaultSmdpAddress invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`setDefaultSmdpAddress, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.getDefaultSmdpAddress

getDefaultSmdpAddress\(slotId: number\): Promise\<string\>

获取存储在eUICC中的默认SM-DP+地址。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.GET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId | number | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<string\> | Promise对象，返回SM-DP+地址。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getDefaultSmdpAddress(1).then((data: string) => {
    console.info(`getDefaultSmdpAddress, result: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getDefaultSmdpAddress, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.cancelSession

cancelSession\(slotId: number, transactionId: string, cancelReason: CancelReason\): Promise\<ResultCode\>

取消会话。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限**： ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ----- | ----- |
| slotId        | number                          | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| transactionId | string                          | 是 | 业务ID。|
| cancelReason  | [CancelReason](#cancelreason) | 是 | 取消会话的原因。|

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode)\> | Promise对象，返回取消会话的结果码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID                 | 错误信息                               |
| --------------------- | ---------------------------------- |
| 201   | Permission denied. |
| 202   | Non-system applications use system APIs. |
| 401   | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801   | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

let transactionId = '';
eSIM.cancelSession(1, transactionId, eSIM.CancelReason.CANCEL_REASON_END_USER_REJECTION)
  .then((data: eSIM.ResultCode) => {
    console.info(`cancelSession, result: data->${JSON.stringify(data)}`);
  })
  .catch((err: BusinessError<void>) => {
    console.error(`cancelSession execution failed: err->${JSON.stringify(err)}`);
  });
```

## GetDownloadableProfileMetadataResult

获取可下载配置文件的元数据。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型                                        | 只读 | 可选 | 说明 |
| ----- |-------------------------------------------|---| ---- | -----|
| downloadableProfile | [DownloadableProfile](./js-apis-esim.md#downloadableprofile) | 否 | 否 | 可下载的配置文件信息。   |
| pprType             | number                     | 否 | 否 | 配置文件策略规则类型。 |
| pprFlag             | boolean                    | 否 | 否 | 配置文件是否有策略规则。true表示有策略规则，false表示无策略规则。|
| iccid               | string                     | 否 | 否 | 配置文件的iccId。    |
| serviceProviderName | string                     | 否 | 否 | 配置文件的服务提供商名称。 |
| profileName         | string                     | 否 | 否 | 配置文件名称。 |
| profileClass        | [ProfileClass](#profileclass)        | 否 | 否 | 配置文件类。  |
| solvableErrors      | [SolvableErrors](#solvableerrors)      | 否 | 否 | 可解决的错误。 |
| responseResult      | [ResultCode](#resultcode)         | 否 | 否 | 操作结果码。  |

## GetDownloadableProfilesResult

获取默认可下载配置文件的列表。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型                                                | 只读 | 可选 | 说明 |
| ----- |---------------------------------------------------|---| ----- | -----|
| responseResult       | [ResultCode](#resultcode)                   | 否 | 否 | 返回操作结果码。     |
| downloadableProfiles | Array\<[DownloadableProfile](./js-apis-esim.md#downloadableprofile)\> | 否 | 否 | 可下载配置文件数组。 |

## DownloadProfileResult

下载配置文件的结果。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型                                  | 只读 | 可选 | 说明 |
| ----- |-------------------------------------|----|---| -----|
| responseResult | [ResultCode](#resultcode)         | 否  | 否 | 操作结果码。 |
| solvableErrors | [SolvableErrors](#solvableerrors) | 否  | 否 | 可解决错误。 |
| cardId         | number                | 否  | 否 | 获取卡ID。 |

## GetEuiccProfileInfoListResult

获取配置文件信息列表。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型                                     | 只读 | 可选 | 说明   |
| ----- |----------------------------------------|---| ---- |------|
| responseResult  | [ResultCode](#resultcode)            | 否 | 否 | 返回操作结果码。    |
| profiles        | Array\<[EuiccProfile](#euiccprofile)\> | 否 | 否 | 配置文件数组。     |
| isRemovable     | boolean                      | 否 | 否 | eUICC是否可移除。true表示可移除，false表示不可移除。|

## OperatorId

获取eUICC芯片/设备的相关信息。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ----- | ----- |---| ----- | -----|
| mcc  | string | 否 | 否 | 移动国家代码。 |
| mnc  | string | 否 | 否 | 网络代码。    |
| gid1 | string | 否 | 否 | 组ID级别1。  |
| gid2 | string | 否 | 否 | 组ID级别2。  |

## EuiccProfile

配置文件信息。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型                                                    | 只读 | 可选 | 说明 |
| ----- |-------------------------------------------------------|---|---- |  -----|
| iccid               | string                                                | 否 | 否 | 配置文件的iccId。 |
| nickName            | string                                                | 否 | 否 | 昵称。 |
| serviceProviderName | string                                                | 否 | 否 | 配置文件的服务提供商名称。 |
| profileName         | string                                                | 否 | 否 | 配置文件名称。   |
| state               | [ProfileState](#profilestate)                       | 否 | 否 | 配置文件的状态。 |
| profileClass        | [ProfileClass](#profileclass)                       | 否 | 否 | 配置文件类。     |
| operatorId          | [OperatorId](#operatorid)                           | 否 | 否 | 配置文件的操作ID。|
| policyRules         | [PolicyRules](#policyrules)                         | 否 | 否 | 配置文件策略。   |
| accessRules         | Array\<[AccessRule](./js-apis-esim.md#accessrule20)\> | 否 | 否 | 配置文件规则。   |

## EuiccInfo

euicc信息。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ----- | ----- |----|----| -----|
| osVersion | string | 否  | 否  | 系统版本。 |

## ResetOption

重置状态。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 值 | 说明 |
| ----- | ----- | ----- |
|DELETE_OPERATIONAL_PROFILES       | 1      | 删除所有操作配置文件。 |
|DELETE_FIELD_LOADED_TEST_PROFILES | 1 << 1 | 删除所有字段加载的测试配置文件。 |
|RESET_DEFAULT_SMDP_ADDRESS        | 1 << 2 | 重置默认SM-DP+地址。 |

## OsuStatus

操作系统升级状态。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 值 | 说明 |
| ----- | ----- | ----- |
|EUICC_UPGRADE_IN_PROGRESS         | 1 | 升级中。 |
|EUICC_UPGRADE_FAILED              | 2 | 升级失败。 |
|EUICC_UPGRADE_SUCCESSFUL          | 3 | 升级成功。 |
|EUICC_UPGRADE_ALREADY_LATEST      | 4 | 当前为最新版本，无需升级 。|
|EUICC_UPGRADE_SERVICE_UNAVAILABLE | 5 | 升级服务不可用。 |

## ResultCode

结果码。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 值 | 说明 |
| ----- | ----- | ----- |
| RESULT_SOLVABLE_ERRORS                                   | -2  | 用户必须解决可解决的错误。        |
| RESULT_MUST_DISABLE_PROFILE                              | -1  | 必须禁用活动配置文件才能执行操作。 |
| RESULT_OK                                                | 0   | 成功。 |
| RESULT_GET_EID_FAILED                                    | 201 | 获取EID失败。 |
| RESULT_ACTIVATION_CODE_CHANGED                           | 203 | 最终用户确认后，激活码将被更改。   |
| RESULT_ACTIVATION_CODE_INVALID                           | 204 | 激活码无效。  |
| RESULT_SMDP_ADDRESS_INVALID                              | 205 | SM-DP+服务器地址非法。 |
| RESULT_EUICC_INFO_INVALID                                | 206 | 无效的eUICC信息。      |
| RESULT_TLS_HANDSHAKE_FAILED                              | 207 | TLS握手失败。          |
| RESULT_CERTIFICATE_IO_ERROR                              | 208 | 证书网络连接错误。      |
| RESULT_CERTIFICATE_RESPONSE_TIMEOUT                      | 209 | 证书地址无效或响应超时。 |
| RESULT_AUTHENTICATION_FAILED                             | 210 | 鉴权失败。     |
| RESULT_RESPONSE_HTTP_FAILED                              | 211 | HTTP响应失败。 |
| RESULT_CONFIRMATION_CODE_INCORRECT                       | 212 | 确认码不正确。 |
| RESULT_EXCEEDED_CONFIRMATION_CODE_TRY_LIMIT              | 213 | 已达到最大确认码尝试次数。      |
| RESULT_NO_PROFILE_ON_SERVER                              | 214 | 服务器上没有可供下载的配置文件。 |
| RESULT_TRANSACTION_ID_INVALID                            | 215 | 事务ID无效。    |
| RESULT_SERVER_ADDRESS_INVALID                            | 216 | 服务器地址无效。 |
| RESULT_GET_BOUND_PROFILE_PACKAGE_FAILED                  | 217 | 获取BPP失败。    |
| RESULT_USER_CANCEL_DOWNLOAD                              | 218 | 最终用户取消下载。   |
| RESULT_SERVER_UNAVAILABLE                                | 220 | 运营商服务器不可用。 |
| RESULT_PROFILE_NON_DELETE                                | 223 | PPR禁止删除文件。    |
| RESULT_SMDP_ADDRESS_INCORRECT                            | 226 | 认证响应服务器地址不匹配。   |
| RESULT_ANALYZE_AUTHENTICATION_SERVER_RESPONSE_FAILED     | 228 | 解析服务器身份验证响应错误。 |
| RESULT_ANALYZE_AUTHENTICATION_CLIENT_RESPONSE_FAILED     | 229 | 解析客户端身份验证响应错误。 |
| RESULT_ANALYZE_AUTHENTICATION_CLIENT_MATCHING_ID_REFUSED | 231 | 由于匹配ID被拒绝，解析客户端身份验证响应错误。 |
| RESULT_PROFILE_TYPE_ERROR_AUTHENTICATION_STOPPED         | 233 | 由于配置文件类型中的错误，身份验证已停止。     |
| RESULT_CARRIER_SERVER_REFUSED_ERRORS                     | 249 | 运营商服务器拒绝原因码为3.8的错误。 |
| RESULT_CERTIFICATE_INVALID                               | 251 | 证书无效。 |
| RESULT_OUT_OF_MEMORY                                     | 263 | 由于内存不足，配置文件安装失败。 |
| RESULT_PPR_FORBIDDEN                                     | 268 | PPR规则禁止此操作。 |
| RESULT_NOTHING_TO_DELETE                                 | 270 | 没有可删除的配置文件。 |
| RESULT_PPR_NOT_MATCH                                     | 276 | 与PPR约束不匹配。   |
| RESULT_CAT_BUSY                                          | 283 | 会话正在进行。   |
| RESULT_PROFILE_EID_INVALID                               | 284 | 此eSIM配置文件已被使用或无效。 |
| RESULT_DOWNLOAD_TIMEOUT                                  | 287 | 下载超时。                   |
| RESULT_SGP_22_OTHER                                      | 400 | SGP.22中定义的其他错误。      |

## CancelReason

取消会话的原因。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 值 | 说明 |
| ----- | ----- | ----- |
|CANCEL_REASON_END_USER_REJECTION | 0 | 最终用户已拒绝下载。          |
|CANCEL_REASON_POSTPONED          | 1 | 下载已推迟，稍后可以重新启动。 |
|CANCEL_REASON_TIMEOUT            | 2 | 下载已超时，稍后可以重新启动。 |
|CANCEL_REASON_PPR_NOT_ALLOWED    | 3 | 由于eUICC上的授权表或其他已安装的配置文件不允许其策略规则，因此无法安装。 |

## ProfileState

配置文件状态。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 值 | 说明 |
| ----- | ----- | ----- |
|PROFILE_STATE_UNSPECIFIED | -1 | 未设置配置文件状态。 |
|PROFILE_STATE_DISABLED    | 0  | 禁用配置文件。   |
|PROFILE_STATE_ENABLED     | 1  | 已启用配置文件。 |

## ProfileClass

配置文件类。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 值 | 说明 |
| ----- | ----- | ----- |
|PROFILE_CLASS_UNSPECIFIED  | -1 | 未设置配置文件类。           |
|PROFILE_CLASS_TEST         | 0  | 测试配置文件。               |
|PROFILE_CLASS_PROVISIONING | 1  | 预加载在eUICC上的配置文件。   |
|PROFILE_CLASS_OPERATIONAL  | 2  | 可预加载或下载的操作配置文件。 |

## PolicyRules

配置文件的策略规则。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 值 | 说明 |
| ----- | ----- | ----- |
|POLICY_RULE_DISABLE_NOT_ALLOWED | 1      | 启用此配置文件后，将无法禁用。 |
|POLICY_RULE_DELETE_NOT_ALLOWED  | 1 << 1 | 无法删除此配置文件。          |
|POLICY_RULE_DISABLE_AND_DELETE  | 1 << 2 | 禁用后应删除此配置文件。      |

## SolvableErrors

可解决错误码。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 值 | 说明 |
| ----- | ----- | ----- |
|SOLVABLE_ERROR_NEED_CONFIRMATION_CODE | 1 << 0 | 下载过程需要用户输入确认码。                |
|SOLVABLE_ERROR_NEED_POLICY_RULE       | 1 << 1 | 下载过程需要用户同意才能允许配置文件策略规则。|

## DownloadConfiguration

下载过程中的属性配置。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ----- | ----- |----| ----- | -----|
|switchAfterDownload | boolean | 否  | 否 | 下载成功后是否启用配置文件。true表示启用，false表示不启用。|
|forceDisableProfile | boolean | 否  | 否 | 是否可直接去激活配置文件。true表示切换配置文件时，如果需要去激活当前的配置文件，则可以直接操作。false表示如果需要去激活当前的配置文件，则会返回错误，并得到用户授权后再继续调用该接口，执行切换配置文件操作。|
|isPprAllowed        | boolean | 否  | 否 | 是否得到用户授权。true表示得到用户授权，服务提供商可实施配置文件策略规则；false表示未得到用户授权，不允许实施配置文件策略规则。|

