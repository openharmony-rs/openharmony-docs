# @ohos.telephony.esim (eSIM卡管理)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @yangyannanyangyannan-->
<!--Designer: @ghxbob-->
<!--Tester: @weitiantian-->
<!--Adviser: @zhang_yixin13-->

eSIM卡管理模块提供了eSIM卡管理的基础能力，包括获取指定卡槽是否支持eSIM功能，如果支持则允许用户添加单个配置文件。

> **说明：**
>
> 本模块首批接口从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>

## 导入模块

```ts
import { eSIM } from '@kit.TelephonyKit';
```

## eSIM.isSupported<sup>18+</sup>

isSupported\(slotId: number\): boolean

获取指定卡槽是否支持eSIM功能。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| boolean | 返回指定卡槽是否支持eSIM功能，如果支持返回true。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID              | 错误信息                           |
| --------------------- | ---------------------------------- |
| 401 | Invalid parameter value.     |
|3120001| Service connection failed. |
|3120002| System internal error.     |

**示例：**

```ts
import { eSIM } from '@kit.TelephonyKit';

let isSupported: boolean = eSIM.isSupported(0);
console.log(`the esim is Supported:` + isSupported);
```

## eSIM.addProfile<sup>18+</sup>

addProfile\(profile: DownloadableProfile\): Promise\<boolean\>

通过该接口拉起下载界面，允许用户添加单个配置文件。使用Promise异步回调。

**需要权限**：ohos.permission.SET_TELEPHONY_ESIM_STATE_OPEN

**系统能力**：SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型                                            | 必填 | 说明                                   |
| ------ |-----------------------------------------------| ---- | -------------------------------------- |
| profile | [DownloadableProfile](#downloadableprofile18) | 是   | 可下载的配置文件信息。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise\<boolean\> | 以Promise形式返回最终用户添加单个配置文件的结果。返回true为成功，false为失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID              | 错误信息                           |
| --------------------- | ---------------------------------- |
| 201 | Permission denied.           |
| 401 | Invalid parameter value.     |
| 801 | Capability not supported.    |
|3120001| Service connection failed. |
|3120002| System internal error.     |

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

eSIM.addProfile(profile).then(() => {
    console.log(`addProfile invoking succeeded.`);
}).catch((err: BusinessError) => {
    console.error(`addProfile, promise: err->${JSON.stringify(err)}`);
});
```

## DownloadableProfile<sup>18+</sup>

可下载的配置文件。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型                                   | 必填 | 说明 |
| ----- |--------------------------------------| ----- | -----|
| activationCode   | string                               |  是  | 激活码。对于不基于激活码的配置文件，可能为空。 |
| confirmationCode | string                               |  否  | 确认码。      |
| carrierName      | string                               |  否  | 订阅名称。    |
| accessRules      | Array\<[AccessRule](#accessrule18)\> |  否  | 访问规则数组。 |

## AccessRule<sup>18+</sup>

访问规则。

**系统能力**：SystemCapability.Telephony.CoreService.Esim

| 名称 | 类型 | 必填 | 说明 |
| ----- | ----- | ----- | -----|
| certificateHashHexStr | string  |  是  | 证书哈希的十六进制字符串。 |
| packageName           | string  |  是  | 规则适用的程序包名称。 |
| accessType            | number  |  是  | 规则的类型。 |
