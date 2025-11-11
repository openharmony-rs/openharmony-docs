# @ohos.telephony.sms (短信服务)（系统接口）

短信服务提供了管理短信的一些基础能力，包括发送、下载彩信，设置发送短信的默认SIM卡槽ID，获取、设置短信服务中心（SMSC）地址等。

>**说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.telephony.sms (短信服务)](js-apis-sms.md)


## 导入模块

```ts
import { sms } from '@kit.TelephonyKit';
```


## sms.sendMms<sup>11+</sup>

sendMms\(context: Context, mmsParams: MmsParams, callback: AsyncCallback&lt;void&gt;\): void

发送彩信。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                     |
| -------- | --------------------------- | ---- | ---------------------------------------- |
| context | Context          | 是   | 应用上下文。<br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。<br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md)。 |
| mmsParams | [MmsParams](#mmsparams11) | 是   | 发送彩信的参数和回调，参考[MmsParams](#mmsparams11)。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 发送彩信的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

FA模型示例：
<!--code_no_check_fa-->
```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common, featureAbility } from '@kit.AbilityKit';

// 获取context
let context: common.BaseContext = featureAbility.getContext();

// 彩信pdu存储路径，pdu来源于编码接口
const sandBoxPath: string = '/data/storage/el2/base/files/';
let filePath: string  = sandBoxPath + 'SendReq.mms';

// 发送彩信参数(mmsc以联通卡为例)
let mmsPars: sms.MmsParams = {
  slotId : 0,
  mmsc: 'http://mmsc.myuni.com.cn',
  data: filePath,
  mmsConfig: {
   userAgent:'ua',
   userAgentProfile: 'uaprof'
  }
};

// 调用发送接口
sms.sendMms(context, mmsPars, async(err: BusinessError) =>{
  if (err) {
      console.error(`sendMms fail, err : ${JSON.stringify(err)}`);
      return;
  }
  console.info(`sendMms Success`);
})
```

Stage模型示例：

```ts
import { UIAbility } from '@kit.AbilityKit';
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

// 彩信pdu存储路径，pdu来源于编码接口
const sandBoxPath = '/data/storage/el2/base/files/';
let filePath  = sandBoxPath + 'SendReq.mms';

// 彩信用户代理、用户代理描述配置。根据运营商要求配置，默认ua，uaprof
let mmsConf: sms.MmsConfig = {
  userAgent:'ua',
  userAgentProfile: 'uaprof'
};

// 发送彩信参数(mmsc以联通卡为例)
let mmsPars: sms.MmsParams = {
  slotId : 0,
  mmsc: 'http://mmsc.myuni.com.cn',
  data: filePath,
  mmsConfig: mmsConf
};

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
    sms.sendMms(this.context, mmsPars, async(err: BusinessError) =>{
        if (err) {
            console.error(`sendMms fail, err : ${JSON.stringify(err)}`);
            return;
        }
        console.info(`sendMms Success`);
        })
    }
}
```

ArkTS-Sta示例：

Stage模型示例：

```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';
import window from '@ohos.window';

// 彩信pdu存储路径，pdu来源于编码接口
const sandBoxPath = '/data/storage/el2/base/files/';
let filePath  = sandBoxPath + 'SendReq.mms';

// 彩信用户代理、用户代理描述配置。根据运营商要求配置，默认ua，uaprof
let mmsConf: sms.MmsConfig = {
  userAgent:'ua',
  userAgentProfile: 'uaprof'
};

// 发送彩信参数(mmsc以联通卡为例)
let mmsPars: sms.MmsParams = {
  slotId : 0,
  mmsc: 'http://mmsc.myuni.com.cn',
  data: filePath,
  mmsConfig: mmsConf
};

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        sms.sendMms(this.context, mmsPars, async(err: BusinessError | null, data:undefined) =>{
            if (err?.code) {
                console.error(`sendMms fail, err : ${JSON.stringify(err)}`);
            } else {
                console.info(`sendMms Success`);
            }
        })
    }
}
```

## sms.sendMms<sup>11+</sup>

sendMms\(context: Context, mmsParams: MmsParams\): Promise&lt;void&gt;

发送彩信。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                     |
| -------- | --------------------------- | ---- | ---------------------------------------- |
| context | Context          | 是   | 应用上下文。<br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。<br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md)。 |
| mmsParams | [MmsParams](#mmsparams11) | 是   | 发送彩信的参数和回调，参考[MmsParams](#mmsparams11)。 |

**返回值：**

| 类型            | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | 以Promise形式返回发送彩信的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

FA模型示例：
<!--code_no_check_fa-->
```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common, featureAbility } from '@kit.AbilityKit';

// 获取context
let context: common.BaseContext = featureAbility.getContext();

// 彩信pdu存储路径，pdu来源于编码接口
const sandBoxPath: string = '/data/storage/el2/base/files/';
let filePath: string = sandBoxPath + 'SendReq.mms';

// 发送彩信参数(mmsc以联通卡为例)
let mmsPars: sms.MmsParams = {
  slotId: 0,
  mmsc: 'http://mmsc.myuni.com.cn',
  data: filePath,
  mmsConfig: {
   userAgent:'ua',
   userAgentProfile: 'uaprof'
  }
};

// 调用发送接口
let promise = sms.sendMms(context, mmsPars);
promise.then(() => {
    console.info(`sendMms success`);
}).catch((err: BusinessError) => {
    console.error(`sendMms failed, promise: err->${JSON.stringify(err)}`);
});
```

Stage模型示例：

```ts
import { UIAbility } from '@kit.AbilityKit';
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

// 彩信pdu存储路径，pdu来源于编码接口
const sandBoxPath = '/data/storage/el2/base/files/';
let filePath  = sandBoxPath + 'SendReq.mms';

// 彩信用户代理、用户代理描述配置。根据运营商要求配置，默认ua，uaprof
let mmsConf: sms.MmsConfig = {
  userAgent:'ua',
  userAgentProfile: 'uaprof'
};

// 发送彩信参数(mmsc以联通卡为例)
let mmsPars: sms.MmsParams = {
  slotId : 0,
  mmsc: 'http://mmsc.myuni.com.cn',
  data: filePath,
  mmsConfig: mmsConf
};

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
    let promise = sms.sendMms(this.context, mmsPars);
    promise.then(() => {
        console.info(`sendMms success`);
    }).catch((err: BusinessError) => {
        console.error(`sendMms failed, promise: err->${JSON.stringify(err)}`);
    });
    }
}
```

ArkTS-Sta示例：

Stage模型示例：

```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';
import window from '@ohos.window';

// 彩信pdu存储路径，pdu来源于编码接口
const sandBoxPath = '/data/storage/el2/base/files/';
let filePath  = sandBoxPath + 'SendReq.mms';

// 彩信用户代理、用户代理描述配置。根据运营商要求配置，默认ua，uaprof
let mmsConf: sms.MmsConfig = {
  userAgent:'ua',
  userAgentProfile: 'uaprof'
};

// 发送彩信参数(mmsc以联通卡为例)
let mmsPars: sms.MmsParams = {
  slotId : 0,
  mmsc: 'http://mmsc.myuni.com.cn',
  data: filePath,
  mmsConfig: mmsConf
};

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
    let promise = sms.sendMms(this.context, mmsPars);
    promise.then(() => {
        console.info(`sendMms success`);
    }).catch((error: Error) => {
        let err = error as BusinessError;
        console.error(`sendMms failed, promise: err->${JSON.stringify(err)}`);
    });
    }
}
```

## sms.downloadMms<sup>11+</sup>

downloadMms\(context: Context, mmsParams: MmsParams, callback: AsyncCallback&lt;void&gt;\): void

下载彩信。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_MMS

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                     |
| -------- | --------------------------- | ---- | ---------------------------------------- |
| context | Context          | 是   | 应用上下文。<br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。<br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md)。 |
| mmsParams | [MmsParams](#mmsparams11) | 是   | 下载彩信的参数和回调，参考[MmsParams](#mmsparams11)。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 下载彩信的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

FA模型示例：
<!--code_no_check_fa-->
```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common, featureAbility } from '@kit.AbilityKit';

// 获取context
let context: common.BaseContext = featureAbility.getContext();

// 彩信pdu存储路径
const sandBoxPath: string = '/data/storage/el2/base/files/';
let filePath: string = sandBoxPath + 'RetrieveConf.mms';

// 从WapPush中解析出彩信URL
let wapPushUrl: string = 'URL';

// 下载彩信参数
let mmsPars: sms.MmsParams = {
  slotId: 0,
  mmsc: wapPushUrl,
  data: filePath,
  mmsConfig: {
   userAgent:'ua',
   userAgentProfile: 'uaprof'
  }
};

// 调用下载接口
sms.downloadMms(context, mmsPars, async(err: BusinessError) =>{
  if (err) {
      console.error(`downloadMms fail, err : ${JSON.stringify(err)}`);
      return;
  }
  console.info(`downloadMms Success`);
})
```

Stage模型示例：

```ts
import { UIAbility } from '@kit.AbilityKit';
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

// 彩信pdu存储路径
const sandBoxPath = '/data/storage/el2/base/files/';
let filePath  = sandBoxPath + 'RetrieveConf.mms';

// 从WapPush中解析出彩信URL
let wapPushUrl  = 'URL';

// 彩信用户代理、用户代理描述配置。根据运营商要求配置，默认ua，uaprof
let mmsConf: sms.MmsConfig = {
  userAgent:'ua',
  userAgentProfile: 'uaprof'
};

// 下载彩信参数
let mmsPars: sms.MmsParams = {
  slotId : 0,
  mmsc: wapPushUrl,
  data: filePath,
  mmsConfig: mmsConf
};

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
    sms.downloadMms(this.context, mmsPars, async(err: BusinessError) =>{
        if (err) {
            console.error(`downloadMms fail, err : ${JSON.stringify(err)}`);
            return;
        }
        console.info(`downloadMms Success`);
        });
    }
}
```

ArkTS-Sta示例：

Stage模型示例：

```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';
import window from '@ohos.window';

// 彩信pdu存储路径
const sandBoxPath = '/data/storage/el2/base/files/';
let filePath  = sandBoxPath + 'RetrieveConf.mms';

// 从WapPush中解析出彩信URL
let wapPushUrl  = 'URL';

// 彩信用户代理、用户代理描述配置。根据运营商要求配置，默认ua，uaprof
let mmsConf: sms.MmsConfig = {
  userAgent:'ua',
  userAgentProfile: 'uaprof'
};

// 下载彩信参数
let mmsPars: sms.MmsParams = {
  slotId : 0,
  mmsc: wapPushUrl,
  data: filePath,
  mmsConfig: mmsConf
};

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        sms.downloadMms(this.context, mmsPars, async(err: BusinessError | null, data: undefined) =>{
            if (err?.code) {
                console.error(`downloadMms fail, err : ${JSON.stringify(err)}`);
            } else {
                console.info(`downloadMms Success`);
            }
        });
    }
}
```

## sms.downloadMms<sup>11+</sup>

downloadMms\(context: Context, mmsParams: MmsParams\): Promise&lt;void&gt;

发送彩信。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_MMS

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                     |
| -------- | --------------------------- | ---- | ---------------------------------------- |
| context | Context          | 是   | 应用上下文。<br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。<br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md)。 |
| mmsParams | [MmsParams](#mmsparams11) | 是   | 发送彩信的参数和回调，参考[MmsParams](#mmsparams11)。 |

**返回值：**

| 类型            | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | 以Promise形式返回发送彩信的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

FA模型示例：
<!--code_no_check_fa-->
```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common, featureAbility } from '@kit.AbilityKit';

// 获取context
let context: common.BaseContext = featureAbility.getContext();

// 彩信pdu存储路径
const sandBoxPath: string = '/data/storage/el2/base/files/';
let filePath: string = sandBoxPath + 'RetrieveConf.mms';

// 从WapPush中解析出彩信URL
let wapPushUrl: string = 'URL';

// 下载彩信参数
let mmsPars: sms.MmsParams = {
  slotId: 0,
  mmsc: wapPushUrl,
  data: filePath,
  mmsConfig: {
   userAgent:'ua',
   userAgentProfile: 'uaprof'
  }
};

// 调用发送接口
let promise = sms.downloadMms(context, mmsPars);
promise.then(() => {
    console.info(`downloadMms success`);
}).catch((err: BusinessError) => {
    console.error(`downloadMms failed, promise: err->${JSON.stringify(err)}`);
});
```

Stage模型示例：

```ts
import { UIAbility } from '@kit.AbilityKit';
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

// 彩信pdu存储路径
const sandBoxPath = '/data/storage/el2/base/files/';
let filePath  = sandBoxPath + 'RetrieveConf.mms';

// 从WapPush中解析出彩信URL
let wapPushUrl  = 'URL';

// 彩信用户代理、用户代理描述配置。根据运营商要求配置，默认ua，uaprof
let mmsConf: sms.MmsConfig = {
  userAgent:'ua',
  userAgentProfile: 'uaprof'
};

// 下载彩信参数
let mmsPars: sms.MmsParams = {
  slotId : 0,
  mmsc: wapPushUrl,
  data: filePath,
  mmsConfig: mmsConf
};

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
    let promise = sms.downloadMms(this.context, mmsPars);
    promise.then(() => {
        console.info(`downloadMms success`);
    }).catch((err: BusinessError) => {
        console.error(`downloadMms failed, promise: err->${JSON.stringify(err)}`);
    });
    }
}
```

ArkTS-Sta示例：

Stage模型示例：

```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';
import window from '@ohos.window';

// 彩信pdu存储路径
const sandBoxPath = '/data/storage/el2/base/files/';
let filePath  = sandBoxPath + 'RetrieveConf.mms';

// 从WapPush中解析出彩信URL
let wapPushUrl  = 'URL';

// 彩信用户代理、用户代理描述配置。根据运营商要求配置，默认ua，uaprof
let mmsConf: sms.MmsConfig = {
  userAgent:'ua',
  userAgentProfile: 'uaprof'
};

// 下载彩信参数
let mmsPars: sms.MmsParams = {
  slotId : 0,
  mmsc: wapPushUrl,
  data: filePath,
  mmsConfig: mmsConf
};

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let promise = sms.downloadMms(this.context, mmsPars);
        promise.then(() => {
            console.info(`downloadMms success`);
    }).catch((error: Error) => {
            let err = error as BusinessError;
            console.error(`downloadMms failed, promise: err->${JSON.stringify(err)}`);
        });
    }
}
```


## sms.setDefaultSmsSlotId<sup>7+</sup>

ArkTS-Dyn: setDefaultSmsSlotId\(slotId: number, callback: AsyncCallback&lt;void&gt;\): void

ArkTS-Sta: setDefaultSmsSlotId\(slotId: int, callback: AsyncCallback&lt;void&gt;\): void

设置发送短信的默认SIM卡槽ID。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                                         |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                    | 是   | SIM卡槽ID。<br/>- 0：卡槽1<br/>- 1：卡槽2<br/>- -1：清除默认配置 |
| callback | AsyncCallback&lt;void&gt; | 是   | 设置发送短信的默认SIM卡槽ID的回调函数。                                                   |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300004  | Do not have sim card.                        |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.setDefaultSmsSlotId(0, (err: BusinessError) => {
    console.info(`callback: err->${JSON.stringify(err)}.`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

sms.setDefaultSmsSlotId(0, (err: BusinessError| null, data: undefined) => {
    if (err?.code) {
        console.error(`sms.setDefaultSmsSlotId callback test failed, err->${JSON.stringify(err)}.`);
    } else {
        console.info(`sms.setDefaultSmsSlotId callback test success`);
    }
});
```


## sms.setDefaultSmsSlotId<sup>7+</sup>

ArkTS-Dyn: setDefaultSmsSlotId\(slotId: number\): Promise&lt;void&gt;

ArkTS-Sta: setDefaultSmsSlotId\(slotId: int\): Promise&lt;void&gt;

设置发送短信的默认SIM卡槽ID。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | SIM卡槽ID。<br/>- 0：卡槽1<br/>- 1：卡槽2<br/>- -1：清除默认配置 |

**返回值：**

| 类型            | 说明                            |
| --------------- | ------------------------------- |
| Promise\<void\> | 以Promise形式异步返回设置结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300004  | Do not have sim card.                        |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.setDefaultSmsSlotId(0).then(() => {
    console.info(`setDefaultSmsSlotId success.`);
}).catch((err: BusinessError) => {
    console.error(`setDefaultSmsSlotId failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

sms.setDefaultSmsSlotId(0).then(() => {
    console.info(`setDefaultSmsSlotId success.`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`setDefaultSmsSlotId failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.setSmscAddr<sup>7+</sup>

ArkTS-Dyn: setSmscAddr\(slotId: number, smscAddr: string, callback: AsyncCallback&lt;void&gt;\): void

ArkTS-Sta: setSmscAddr\(slotId: int, smscAddr: string, callback: AsyncCallback\<void\>\): void

设置短信服务中心（SMSC）地址。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.SET_TELEPHONY_STATE，该权限为系统权限

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                      |
| -------- | ------------------------- | ---- | ----------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                       | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| smscAddr | string                    | 是   | 短信服务中心地址。                        |
| callback | AsyncCallback&lt;void&gt; | 是   | 设置短信服务中心（SMSC）地址的回调函数。                                |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let smscAddr: string = '+861xxxxxxxxxx';
sms.setSmscAddr(slotId, smscAddr, (err: BusinessError) => {
      console.info(`callback: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
let smscAddr: string = '+861xxxxxxxxxx';
sms.setSmscAddr(slotId, smscAddr, (err: BusinessError | null, data: undefined) => {
    if (err?.code) {
        console.error(`sms.setSmscAddr callback test failed, err->${JSON.stringify(err)}`);
    } else {
        console.info(`sms.setSmscAddr callback test success`);
    }
});
```


## sms.setSmscAddr<sup>7+</sup>

ArkTS-Dyn: setSmscAddr\(slotId: int, smscAddr: string\): Promise&lt;void&gt;

ArkTS-Sta: setSmscAddr\(slotId: int, smscAddr: string\): Promise\<void\>

设置短信服务中心（SMSC）地址。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.SET_TELEPHONY_STATE，该权限为系统权限

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型   | 必填 | 说明                                      |
| -------- | ------ | ---- | ----------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| smscAddr | string | 是   | 短信服务中心地址。                        |

**返回值：**

| 类型                | 说明                            |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | 以Promise形式异步返回设置结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let smscAddr: string = '+861xxxxxxxxxx';
sms.setSmscAddr(slotId, smscAddr).then(() => {
    console.info(`setSmscAddr success.`);
}).catch((err: BusinessError) => {
    console.error(`setSmscAddr failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
let smscAddr: string = '+861xxxxxxxxxx';
sms.setSmscAddr(slotId, smscAddr).then(() => {
    console.info(`setSmscAddr success.`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`setSmscAddr failed, promise: err->${JSON.stringify(err)}`);
});
```


## sms.getSmscAddr<sup>7+</sup>

ArkTS-Dyn: getSmscAddr\(slotId: number, callback: AsyncCallback&lt;string&gt;\): void

ArkTS-Sta: getSmscAddr\(slotId: int, callback: AsyncCallback\<string\>\): void

获取短信服务中心（SMSC）地址。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.GET_TELEPHONY_STATE，该权限为系统权限

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                      |
| -------- | --------------------------- | ---- | ----------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                      | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| callback | AsyncCallback&lt;string&gt; | 是   | 指示用于获取SMSC地址的回调函数。                                |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
sms.getSmscAddr(slotId, (err: BusinessError, data: string) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
sms.getSmscAddr(slotId, (err: BusinessError | null, data: string | undefined) => {
    if (err?.code) {
        console.error(`sms.getSmscAddr callback test failed， err->${JSON.stringify(err)}`);
    } else {
        console.info(`sms.getSmscAddr callback test success, data->${JSON.stringify(data)}`);
    }
});
```


## sms.getSmscAddr<sup>7+</sup>

ArkTS-Dyn: getSmscAddr\(slotId: number\): Promise&lt;string&gt;

ArkTS-Sta: getSmscAddr\(slotId: int\): Promise\<string\>

获取短信服务中心（SMSC）地址。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.GET_TELEPHONY_STATE，该权限为系统权限

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                      |
| ------ | ------ | ---- | ----------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int    | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |

**返回值：**

| 类型                  | 说明                                          |
| --------------------- | --------------------------------------------- |
| Promise&lt;string&gt; | 以Promise形式返回获取短信服务中心地址的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
sms.getSmscAddr(slotId).then((data: string) => {
    console.info(`getSmscAddr success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSmscAddr failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
sms.getSmscAddr(slotId).then((data: string) => {
    console.info(`getSmscAddr success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getSmscAddr failed, promise: err->${JSON.stringify(err)}`);
});
```


## sms.splitMessage<sup>8+</sup>

splitMessage\(content: string, callback: AsyncCallback\<Array\<string\>\>\): void

将长短信拆分为多个片段。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                          | 必填 | 说明                          |
| -------- | ----------------------------- | ---- | ----------------------------- |
| content  | string                        | 是   | 指示短消息内容，不能为null。 |
| callback | AsyncCallback<Array<string\>> | 是   | 返回可合并为完整SMS的拆分段列表的回调函数。|

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let content: string = "long message";
sms.splitMessage(content, (err: BusinessError, data: string[]) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let content: string = "long message";
sms.splitMessage(content, (err: BusinessError, data: Array<string>) => {
    if (err?.code) {
        console.error(`sms.splitMessage callback test failed, err->${JSON.stringify(err)}`);
    } else {
        console.info(`sms.splitMessage callback test success, data is: data->${JSON.stringify(data)}`);
    }
});
```


## sms.splitMessage<sup>8+</sup>

splitMessage\(content: string\): Promise\<Array\<string\>\>

将长短信拆分为多个片段。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名  | 类型   | 必填 | 说明                         |
| ------- | ------ | ---- | ---------------------------- |
| content | string | 是   | 指示短消息内容，不能为null。 |

**返回值：**

| 类型                    | 说明                                |
| ----------------------- | ----------------------------------- |
| Promise<Array<string\>> | 以Promise形式返回多个片段的的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let content: string = "long message";
let promise = sms.splitMessage(content);
promise.then((data: string[]) => {
    console.info(`splitMessage success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`splitMessage failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let content: string = "long message";
let promise = sms.splitMessage(content);
promise.then((data: Array<string>) => {
    console.info(`splitMessage success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`splitMessage failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.addSimMessage<sup>7+</sup>

addSimMessage\(options: SimMessageOptions, callback: AsyncCallback\<void\>\): void

添加SIM卡消息，sim卡消息满，添加报错。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS,ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                     | 必填 | 说明            |
| -------- | ---------------------------------------- | ---- | --------------- |
| options  | [SimMessageOptions](#simmessageoptions7) | 是   | SIM卡消息选项。 |
| callback | AsyncCallback&lt;void&gt;                | 是   | 添加SIM卡消息的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                           |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let simMessageOptions: sms.SimMessageOptions = {
    slotId: 0,
    smsc: "test",
    pdu: "xxxxxx",
    status: sms.SimMessageStatus.SIM_MESSAGE_STATUS_READ
};
sms.addSimMessage(simMessageOptions, (err: BusinessError) => {
      console.info(`callback: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let simMessageOptions: sms.SimMessageOptions = {
    slotId: 0,
    smsc: "test",
    pdu: "xxxxxx",
    status: sms.SimMessageStatus.SIM_MESSAGE_STATUS_READ
};
sms.addSimMessage(simMessageOptions, (err: BusinessError| null, data: undefined) => {
    if (err?.code) {
        console.error(`addSimMessage callback test failed, err->${JSON.stringify(err)}`);
    } else {
        console.info("addSimMessage callback test success");
    }
});
```


## sms.addSimMessage<sup>7+</sup>

addSimMessage\(options: SimMessageOptions\): Promise\<void\>

添加SIM卡消息，sim卡消息满，添加报错。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS,ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名  | 类型                                     | 必填 | 说明            |
| ------- | ---------------------------------------- | ---- | --------------- |
| options | [SimMessageOptions](#simmessageoptions7) | 是   | SIM卡消息选项。 |

**返回值：**

| 类型                | 说明                          |
| ------------------- | ----------------------------- |
| Promise&lt;void&gt; | 以Promise形式返回添加的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let simMessageOptions: sms.SimMessageOptions = {
    slotId: 0,
    smsc: "test",
    pdu: "xxxxxx",
    status: sms.SimMessageStatus.SIM_MESSAGE_STATUS_READ
};
sms.addSimMessage(simMessageOptions).then(() => {
    console.info(`addSimMessage success.`);
}).catch((err: BusinessError) => {
    console.error(`addSimMessage failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let simMessageOptions: sms.SimMessageOptions = {
    slotId: 0,
    smsc: "test",
    pdu: "xxxxxx",
    status: sms.SimMessageStatus.SIM_MESSAGE_STATUS_READ
};
sms.addSimMessage(simMessageOptions).then(() => {
    console.info(`addSimMessage success.`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`addSimMessage failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.delSimMessage<sup>7+</sup>

ArkTS-Dyn: delSimMessage\(slotId: number, msgIndex: number, callback: AsyncCallback\<void\>\): void

ArkTS-Sta: delSimMessage\(slotId: int, msgIndex: int, callback: AsyncCallback\<void\>\): void

删除SIM卡消息，msgIndex无效时，删除报错。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS,ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                      |
| -------- | ------------------------- | ---- | ----------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                    | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| msgIndex | ArkTS-Dyn: number <br/>ArkTS-Sta: int                    | 是   | 消息索引。                                  |
| callback | AsyncCallback&lt;void&gt; | 是   | 删除SIM卡消息的回调函数。  |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let msgIndex: number = 1;
sms.delSimMessage(slotId, msgIndex, (err: BusinessError) => {
      console.info(`callback: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
let msgIndex: int = 1;
sms.delSimMessage(slotId, msgIndex, (err: BusinessError| null, data: undefined) => {
    if (err?.code) {
        console.error(`delSimMessage callback test failed, err->${JSON.stringify(err)}`);
    } else {
        console.info(`delSimMessage callback test success`);
    }
});
```


## sms.delSimMessage<sup>7+</sup>

ArkTS-Dyn: delSimMessage\(slotId: number, msgIndex: number\): Promise\<void\>

ArkTS-Sta: delSimMessage\(slotId: int, msgIndex: int\): Promise\<void\>

删除SIM卡消息，msgIndex无效时，删除报错。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS,ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型   | 必填 | 说明                                      |
| -------- | ------ | ---- | ----------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| msgIndex | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 消息索引。                                  |

**返回值：**

| 类型                | 说明                          |
| ------------------- | ----------------------------- |
| Promise&lt;void&gt; | 以Promise形式返回删除的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let msgIndex: number = 1;
let promise = sms.delSimMessage(slotId, msgIndex);
promise.then(() => {
    console.info(`delSimMessage success.`);
}).catch((err: BusinessError) => {
    console.error(`delSimMessage failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
let msgIndex: int = 1;
let promise = sms.delSimMessage(slotId, msgIndex);
promise.then(() => {
    console.info(`delSimMessage success.`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`delSimMessage failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.updateSimMessage<sup>7+</sup>

updateSimMessage\(options: UpdateSimMessageOptions, callback: AsyncCallback\<void\>\): void

更新SIM卡消息。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS,ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                |
| -------- | ---------------------------------------------------- | ---- | ------------------- |
| options  | [UpdateSimMessageOptions](#updatesimmessageoptions7) | 是   | 更新SIM卡消息选项。 |
| callback | AsyncCallback&lt;void&gt;                            | 是   | 更新SIM卡消息的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let updateSimMessageOptions: sms.UpdateSimMessageOptions = {
    slotId: 0,
    msgIndex: 1,
    newStatus: sms.SimMessageStatus.SIM_MESSAGE_STATUS_FREE,
    pdu: "xxxxxxx",
    smsc: "test"
};
sms.updateSimMessage(updateSimMessageOptions, (err: BusinessError) => {
      console.info(`callback: err->${JSON.stringify(err)}`);
});
```


## sms.updateSimMessage<sup>7+</sup>

updateSimMessage\(options: UpdateSimMessageOptions\): Promise\<void\>

更新SIM卡消息。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS,ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                |
| ------- | ---------------------------------------------------- | ---- | ------------------- |
| options | [UpdateSimMessageOptions](#updatesimmessageoptions7) | 是   | 更新SIM卡消息选项。 |

**返回值：**

| 类型                | 说明                          |
| ------------------- | ----------------------------- |
| Promise&lt;void&gt; | 以Promise形式返回更新的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let updateSimMessageOptions: sms.UpdateSimMessageOptions = {
    slotId: 0,
    msgIndex: 1,
    newStatus: sms.SimMessageStatus.SIM_MESSAGE_STATUS_FREE,
    pdu: "xxxxxxx",
    smsc: "test"
};
let promise = sms.updateSimMessage(updateSimMessageOptions);
promise.then(() => {
    console.info(`updateSimMessage success.`);
}).catch((err: BusinessError) => {
    console.error(`updateSimMessage failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.getAllSimMessages<sup>7+</sup>

ArkTS-Dyn: getAllSimMessages\(slotId: number, callback: AsyncCallback\<Array\<SimShortMessage\>\>\): void

ArkTS-Sta: getAllSimMessages\(slotId: int, callback: AsyncCallback\<Array\<SimShortMessage\>\>\): void

获取所有SIM卡消息。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                                        | 必填 | 说明                                      |
| -------- | ----------------------------------------------------------- | ---- | ----------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                                                      | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| callback | AsyncCallback<Array<[SimShortMessage](#simshortmessage7)\>> | 是   | 获取所有SIM卡消息的回调函数。  |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                         |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
sms.getAllSimMessages(slotId, (err: BusinessError, data: sms.SimShortMessage[]) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
sms.getAllSimMessages(slotId, (err: BusinessError | null, data: Array<sms.SimShortMessage> | undefined) => {
    if(err?.code){
        console.error(`getAllSimMessages failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`getAllSimMessages success, callback: data->${JSON.stringify(data)}`);
    }
});
```


## sms.getAllSimMessages<sup>7+</sup>

ArkTS-Dyn: getAllSimMessages\(slotId: number\): Promise\<Array\<SimShortMessage\>\>

ArkTS-Sta: getAllSimMessages\(slotId: int\): Promise\<Array\<SimShortMessage\>\>

获取所有SIM卡消息。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                      |
| ------ | ------ | ---- | ----------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |

**返回值：**

| 类型                                                    | 说明                               |
| ------------------------------------------------------- | ---------------------------------- |
| Promise<Array<[SimShortMessage](#simshortmessage7)\>&gt; | 以Promise形式返回获取的SIM短消息。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                           |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let promise = sms.getAllSimMessages(slotId);
promise.then((data: sms.SimShortMessage[]) => {
    console.info(`getAllSimMessages success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getAllSimMessages failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
let promise = sms.getAllSimMessages(slotId);
promise.then((data: Array<sms.SimShortMessage>) => {
    console.info(`getAllSimMessages success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getAllSimMessages failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.setCBConfig<sup>7+</sup>

setCBConfig\(options: CBConfigOptions, callback: AsyncCallback\<void\>\): void

设置小区广播配置。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                 | 必填 | 说明         |
| -------- | ------------------------------------ | ---- | ------------ |
| options  | [CBConfigOptions](#cbconfigoptions7) | 是   | 小区广播配置选项。 |
| callback | AsyncCallback&lt;void&gt;            | 是   | 设置小区广播配置的回调函数。  |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                         |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let cbConfigOptions: sms.CBConfigOptions = {
    slotId: 0,
    enable: true,
    startMessageId: 100,
    endMessageId: 200,
    ranType: sms.RanType.TYPE_GSM
};
sms.setCBConfig(cbConfigOptions, (err: BusinessError) => {
      console.info(`callback: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let cbConfigOptions: sms.CBConfigOptions = {
    slotId: 0,
    enable: true,
    startMessageId: 100,
    endMessageId: 200,
    ranType: sms.RanType.TYPE_GSM
};
sms.setCBConfig(cbConfigOptions, (err: BusinessError | null, data: undefined) => {
    if(err?.code){
        console.error(`setCBConfig failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`setCBConfig success`);
    }
});
```


## sms.setCBConfig<sup>7+</sup>

setCBConfig\(options: CBConfigOptions\): Promise\<void\>

设置小区广播配置。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.RECEIVE_SMS

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名  | 类型                                 | 必填 | 说明         |
| ------- | ------------------------------------ | ---- | ------------ |
| options | [CBConfigOptions](#cbconfigoptions7) | 是   | 小区广播配置选项。 |

**返回值：**

| 类型                | 说明                          |
| ------------------- | ----------------------------- |
| Promise&lt;void&gt; | 以Promise形式返回设置的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                         |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let cbConfigOptions: sms.CBConfigOptions = {
    slotId: 0,
    enable: true,
    startMessageId: 100,
    endMessageId: 200,
    ranType: sms.RanType.TYPE_GSM
};
let promise = sms.setCBConfig(cbConfigOptions);
promise.then(() => {
    console.info(`setCBConfig success.`);
}).catch((err: BusinessError) => {
    console.error(`setCBConfig failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let cbConfigOptions: sms.CBConfigOptions = {
    slotId: 0,
    enable: true,
    startMessageId: 100,
    endMessageId: 200,
    ranType: sms.RanType.TYPE_GSM
};
let promise = sms.setCBConfig(cbConfigOptions);
promise.then(() => {
    console.info(`setCBConfig success.`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`setCBConfig failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.getSmsSegmentsInfo<sup>8+</sup>

ArkTS-Dyn: getSmsSegmentsInfo\(slotId: number, message: string, force7bit: boolean, callback: AsyncCallback\<SmsSegmentsInfo\>\): void

ArkTS-Sta: getSmsSegmentsInfo\(slotId: int, message: string, force7bit: boolean, callback: AsyncCallback\<SmsSegmentsInfo\>\): void

获取短信段信息。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                                                         | 必填 | 说明                                      |
| --------- | ------------------------------------------------------------ | ---- | ----------------------------------------- |
| slotId    | ArkTS-Dyn: number <br/>ArkTS-Sta: int                          | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| message   | string                                                       | 是   | 消息。                                      |
| force7bit | boolean                                                      | 是   | 是否使用7 bit编码，默认false。<br/>-true：是<br/>-false：否                          |
| callback  | AsyncCallback&lt;[SmsSegmentsInfo](#smssegmentsinfo8)&gt; | 是   | 指示用于获取短信短信息的回调函数。  |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
sms.getSmsSegmentsInfo(slotId, "message", false, (err: BusinessError, data: sms.SmsSegmentsInfo) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
sms.getSmsSegmentsInfo(slotId, "message", false, (err: BusinessError | null, data: sms.SmsSegmentsInfo | undefined) => {
    if(err?.code){
        console.error(`getSmsSegmentsInfo failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`getSmsSegmentsInfo success, callback: data->${JSON.stringify(data)}`);
    }
});
```


## sms.getSmsSegmentsInfo<sup>8+</sup>

ArkTS-Dyn: getSmsSegmentsInfo\(slotId: number, message: string, force7bit: boolean\): \Promise<SmsSegmentsInfo\>

ArkTS-Sta: getSmsSegmentsInfo\(slotId: int, message: string, force7bit: boolean\): Promise\<SmsSegmentsInfo\>

获取短信段信息。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型    | 必填 | 说明                                      |
| --------- | ------- | ---- | ----------------------------------------- |
| slotId    | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| message   | string  | 是   | 消息。                                      |
| force7bit | boolean | 是   | 是否使用7 bit编码，默认false。<br/>-true：是<br/>-false：否                          |

**返回值：**

| 类型                                                    | 说明                          |
| ------------------------------------------------------- | ----------------------------- |
| Promise&lt;[SmsSegmentsInfo](#smssegmentsinfo8)&gt; | 以Promise形式返回短信段信息。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let promise = sms.getSmsSegmentsInfo(slotId, "message", false);
promise.then((data: sms.SmsSegmentsInfo) => {
    console.info(`getSmsSegmentsInfo success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSmsSegmentsInfo failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
let promise = sms.getSmsSegmentsInfo(slotId, "message", false);
promise.then((data: sms.SmsSegmentsInfo) => {
    console.info(`getSmsSegmentsInfo success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getSmsSegmentsInfo failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.isImsSmsSupported<sup>8+</sup>

ArkTS-Dyn: isImsSmsSupported\(slotId: number, callback: AsyncCallback\<boolean\>\): void

ArkTS-Sta: isImsSmsSupported\(slotId: int, callback: AsyncCallback\<boolean\>\): void

如果IMS已注册并且在IMS上支持SMS，则支持通过IMS发送SMS。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                         | 必填 | 说明       |
| -------- | ---------------------------- | ---- | ---------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                       | 是   | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| callback | AsyncCallback&lt;boolean&gt; | 是   | 指示是否支持IMS发送SMS的回调函数，默认false。<br/>-true：是<br/>-false：否 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                          |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
sms.isImsSmsSupported(slotId, (err: BusinessError, data: boolean) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
sms.isImsSmsSupported(slotId, (err: BusinessError | null, data: boolean | undefined) => {
    if(err?.code){
        console.error(`isImsSmsSupported failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`isImsSmsSupported success, callback: data->${JSON.stringify(data)}`);
    }
});
```


## sms.isImsSmsSupported<sup>8+</sup>

ArkTS-Dyn: isImsSmsSupported\(slotId: number\): Promise\<boolean\>

ArkTS-Sta: isImsSmsSupported\(slotId: int\): Promise\<boolean\>

如果IMS已注册并且在IMS上支持SMS，则支持通过IMS发送SMS。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填  | 说明                                  |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1<br/>- 1：卡槽2 |

**返回值：**

| 类型                   | 说明                    |
| ---------------------- | ----------------------- |
| Promise&lt;boolean&gt; | 以Promise形式返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                         |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let promise = sms.isImsSmsSupported(slotId);
promise.then((data: boolean) => {
    console.info(`isImsSmsSupported success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isImsSmsSupported failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
let promise = sms.isImsSmsSupported(slotId);
promise.then((data: boolean) => {
    console.info(`isImsSmsSupported success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`isImsSmsSupported failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.getImsShortMessageFormat<sup>8+</sup>

getImsShortMessageFormat\(callback: AsyncCallback\<string\>\): void

获取IMS上支持的SMS格式。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                        | 必填 | 说明       |
| -------- | --------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;string&gt; | 是   | 指示用于获取格式、3gpp、3gpp2或未知的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                           |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getImsShortMessageFormat((err: BusinessError, data: string) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

sms.getImsShortMessageFormat((err: BusinessError | null, data: string | undefined) => {
    if(err?.code){
        console.error(`getImsShortMessageFormat failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`getImsShortMessageFormat success, callback: data->${JSON.stringify(data)}`);
    }
});
```


## sms.getImsShortMessageFormat<sup>8+</sup>

getImsShortMessageFormat\(\): Promise\<string\>

获取IMS上支持的SMS格式。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型                  | 说明                       |
| --------------------- | -------------------------- |
| Promise&lt;string&gt; | 以Promise形式返回SMS格式。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getImsShortMessageFormat().then((data: string) => {
    console.info(`getImsShortMessageFormat success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getImsShortMessageFormat failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

sms.getImsShortMessageFormat().then((data: string) => {
    console.info(`getImsShortMessageFormat success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getImsShortMessageFormat failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.decodeMms<sup>8+</sup>

ArkTS-Dyn: decodeMms\(mmsFilePathName: string | Array\<number\>, callback: AsyncCallback\<MmsInformation\>\): void

ArkTS-Sta: decodeMms\(mmsFilePathName: string | Array\<int\>, callback: AsyncCallback\<MmsInformation\>\): void

彩信解码。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名          | 类型                                                    | 必填 | 说明           |
| --------------- | ------------------------------------------------------- | ---- | -------------- |
| mmsFilePathName | ArkTS-Dyn: string \| Array<number\> <br/>ArkTS-Sta: string \| Array<int\>                                 | 是   | 彩信文件路径。 |
| callback        | AsyncCallback&lt;[MmsInformation](#mmsinformation8)&gt; | 是   | 获取｛@code MmsInformation｝的回调函数。     |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let mmsFilePathName: string = "filename";
sms.decodeMms(mmsFilePathName, (err: BusinessError, data: sms.MmsInformation) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});

const mmsPdu: Array<number> = [0x8c, 0x80, 0x98, 0x31, 0x00, 0x8d, 0x92, 0x89, 0x09, 0x80, 0x07, 0xea, 0x31, 0x30, 0x30, 0x38, 0x36, 0x00, 0x97, 0x07, 0xea, 0x31, 0x30, 0x30,0x31, 0x30, 0x00, 0x84, 0x74, 0x79, 0x70, 0x65, 0x00, 0x00];
sms.decodeMms(mmsPdu, (err: BusinessError, data: sms.MmsInformation) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let mmsFilePathName: string = "filename";
sms.decodeMms(mmsFilePathName, (err: BusinessError | null, data: sms.MmsInformation | undefined) => {
    if(err?.code){
        console.error(`decodeMms failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`decodeMms success, callback: data->${JSON.stringify(data)}`);
    }
});

const mmsPdu: Array<int> = [0x8c, 0x80, 0x98, 0x31, 0x00, 0x8d, 0x92, 0x89, 0x09, 0x80, 0x07, 0xea, 0x31, 0x30, 0x30, 0x38, 0x36, 0x00, 0x97, 0x07, 0xea, 0x31, 0x30, 0x30,0x31, 0x30, 0x00, 0x84, 0x74, 0x79, 0x70, 0x65, 0x00, 0x00];
sms.decodeMms(mmsPdu, (err: BusinessError | null, data: sms.MmsInformation | undefined) => {
    if(err?.code){
        console.error(`decodeMms failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`decodeMms success, callback: data->${JSON.stringify(data)}`);
    }
});
```


## sms.decodeMms<sup>8+</sup>

ArkTS-Dyn: decodeMms\(mmsFilePathName: string | Array\<number\>): Promise\<MmsInformation\>

ArkTS-Sta: decodeMms\(mmsFilePathName: string | Array\<number\>\): Promise\<MmsInformation\>

彩信解码。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名          | 类型                    | 必填 | 说明           |
| --------------- | ----------------------- | ---- | -------------- |
| mmsFilePathName | ArkTS-Dyn: string \| Array<number\> <br/>ArkTS-Sta: string \| Array<int\> | 是   | 彩信文件路径。 |

**返回值：**

| 类型                                                      | 说明                        |
| --------------------------------------------------------- | --------------------------- |
| Promise&lt;&lt;[MmsInformation](#mmsinformation8)&gt;&gt; | 以Promise形式返回彩信信息。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let mmsFilePathName: string = "filename";
let promise = sms.decodeMms(mmsFilePathName);
promise.then((data: sms.MmsInformation) => {
    console.info(`decodeMms success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`decodeMms failed, promise: err->${JSON.stringify(err)}`);
});

const mmsPdu: Array<number> = [0x8c, 0x80, 0x98, 0x31, 0x00, 0x8d, 0x92, 0x89, 0x09, 0x80, 0x07, 0xea, 0x31, 0x30, 0x30, 0x38, 0x36, 0x00, 0x97, 0x07, 0xea, 0x31, 0x30, 0x30,0x31, 0x30, 0x00, 0x84, 0x74, 0x79, 0x70, 0x65, 0x00, 0x00];
let promiseArr = sms.decodeMms(mmsPdu);
promiseArr.then((data: sms.MmsInformation) => {
    console.info(`decodeMms success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`decodeMms failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let mmsFilePathName: string = "filename";
let promise = sms.decodeMms(mmsFilePathName);
promise.then((data: sms.MmsInformation) => {
    console.info(`decodeMms success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`decodeMms failed, promise: err->${JSON.stringify(err)}`);
});

const mmsPdu: Array<int> = [0x8c, 0x80, 0x98, 0x31, 0x00, 0x8d, 0x92, 0x89, 0x09, 0x80, 0x07, 0xea, 0x31, 0x30, 0x30, 0x38, 0x36, 0x00, 0x97, 0x07, 0xea, 0x31, 0x30, 0x30,0x31, 0x30, 0x00, 0x84, 0x74, 0x79, 0x70, 0x65, 0x00, 0x00];
let promiseArr = sms.decodeMms(mmsPdu);
promiseArr.then((data: sms.MmsInformation) => {
    console.info(`decodeMms success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`decodeMms failed, promise: err->${JSON.stringify(err)}`);
});
```

## sms.encodeMms<sup>8+</sup>

ArkTS-Dyn: encodeMms\(mms: MmsInformation, callback: AsyncCallback\<Array\<number\>\>\): void

ArkTS-Sta: encodeMms\(mms: MmsInformation, callback: AsyncCallback\<Array\<int\>\>\): void

彩信编码。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                | 必填 | 说明       |
| -------- | ----------------------------------- | ---- | ---------- |
| mms      | [MmsInformation](#mmsinformation8)  | 是   | 彩信信息。 |
| callback | ArkTS-Dyn: AsyncCallback&lt;Array<number\>&gt;<br/>ArkTS-Sta: AsyncCallback&lt;Array<int\>&gt; | 是   | 指示用于获取MMS编码结果的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let mmsAcknowledgeInd: sms.MmsAcknowledgeInd = {
    transactionId: "100",
    version: sms.MmsVersionType.MMS_VERSION_1_0,
    reportAllowed: sms.ReportType.MMS_YES
};
let mmsInformation: sms.MmsInformation = {
    messageType: sms.MessageType.TYPE_MMS_ACKNOWLEDGE_IND,
    mmsType: mmsAcknowledgeInd
};
sms.encodeMms(mmsInformation, (err: BusinessError, data: number[]) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let mmsAcknowledgeInd: sms.MmsAcknowledgeInd = {
    transactionId: "100",
    version: sms.MmsVersionType.MMS_VERSION_1_0,
    reportAllowed: sms.ReportType.MMS_YES
};
let mmsInformation: sms.MmsInformation = {
    messageType: sms.MessageType.TYPE_MMS_ACKNOWLEDGE_IND,
    mmsType: mmsAcknowledgeInd
};
sms.encodeMms(mmsInformation, (err: BusinessError | null, data: Array<int> | undefined) => {
    if(err?.code) {
        console.error(`encodeMms failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`encodeMms success, callback: data->${JSON.stringify(data)}`);
    }
});
```


## sms.encodeMms<sup>8+</sup>

ArkTS-Dyn: encodeMms\(mms: MmsInformation\): Promise\<Array\<number\>\>

ArkTS-Sta: encodeMms\(mms: MmsInformation\): Promise\<Array\<int\>\>

彩信编码。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型                               | 必填 | 说明       |
| ------ | ---------------------------------- | ---- | ---------- |
| mms    | [MmsInformation](#mmsinformation8) | 是   | 彩信信息。 |

**返回值：**

| 类型                          | 说明                                |
| ----------------------------- | ----------------------------------- |
| ArkTS-Dyn: Promise&lt;Array<int\>&gt;<br/>ArkTS-Sta: Promise&lt;Array<int\>&gt; | 以Promise形式返回彩信编码后的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**示例：**

ArkTS-Dyn示例：

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let mmsAcknowledgeInd: sms.MmsAcknowledgeInd = {
    transactionId: "100",
    version: sms.MmsVersionType.MMS_VERSION_1_0,
    reportAllowed: sms.ReportType.MMS_YES
};
let mmsInformation: sms.MmsInformation = {
    messageType: sms.MessageType.TYPE_MMS_ACKNOWLEDGE_IND,
    mmsType: mmsAcknowledgeInd
};
sms.encodeMms(mmsInformation).then((data: number[]) => {
    console.info(`encodeMms success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`encodeMms failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sms from '@ohos.telephony.sms';
import { BusinessError } from '@ohos.base';

let mmsAcknowledgeInd: sms.MmsAcknowledgeInd = {
    transactionId: "100",
    version: sms.MmsVersionType.MMS_VERSION_1_0,
    reportAllowed: sms.ReportType.MMS_YES
};
let mmsInformation: sms.MmsInformation = {
    messageType: sms.MessageType.TYPE_MMS_ACKNOWLEDGE_IND,
    mmsType: mmsAcknowledgeInd
};
sms.encodeMms(mmsInformation).then((data: Array<int>) => {
    console.info(`encodeMms success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`encodeMms failed, promise: err->${JSON.stringify(err)}`);
});
```


## MmsParams<sup>11+</sup>

发送彩信的参数。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

|       名称       | 类型                                                         | 只读 |  可选 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ----- |------------------------------------------------------------ |
| slotId<sup>11+</sup>           | ArkTS-Dyn: number <br/>ArkTS-Sta: int            | 否   |   否  | 用于发送短信的SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2      |
| mmsc<sup>11+</sup>  | string                                                    | 否   |   否  |彩信中心地址。                                             |
| data<sup>11+</sup>          | string                                            | 否   |   否  |彩信PDU地址。 |
| mmsConfig<sup>11+</sup>    | MmsConfig                                          | 否   |   是  |彩信配置文件，参考[MmsConfig](#mmsconfig11)。                |

## MmsConfig<sup>11+</sup>

彩信配置文件。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

|       名称       | 类型                                                         | 只读 |  可选 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ----- |------------------------------------------------------------ |
| userAgent<sup>11+</sup>  | string                                               | 否   |   否  | 用户代理。                                             |
| userAgentProfile<sup>11+</sup>    | string                                      | 否   |   否  | 用户代理配置。                |



## MmsInformation<sup>8+</sup>

彩信信息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|     名称    | 类型                                                         | 只读 |  可选 |    说明    |
| ----------- | ------------------------------------------------------------ | ---- | ----- | ---------- |
| messageType | [MessageType](#messagetype8)                                 | 否   |   否  | 指示MMS消息的消息类型。。 |
| mmsType     | [MmsSendReq](#mmssendreq8) \|[MmsSendConf](#mmssendconf8) \|[MmsNotificationInd](#mmsnotificationind8) \|[MmsRespInd](#mmsrespind8) \|[MmsRetrieveConf](#mmsretrieveconf8)\|[MmsAcknowledgeInd](#mmsacknowledgeind8)\|[MmsDeliveryInd](#mmsdeliveryind8)\|[MmsReadOrigInd](#mmsreadorigind8)\|[MmsReadRecInd](#mmsreadrecind8) | 否   |   否  | 指示MMS消息的PDU头类型。 |
| attachment  | Array<[MmsAttachment](#mmsattachment8)\>                     | 否   |   是  | 指示该MMS消息的附件。     |

## MmsSendReq<sup>8+</sup>

彩信发送请求。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|       名称       | 类型                                 | 只读 |  可选 | 说明         |
| ---------------- | ------------------------------------ | ---- | ----- | ------------ |
| from             | [MmsAddress](#mmsaddress8)           | 否   |   否  |  指示MMS消息发送请求的源地址。     |
| transactionId    | string                               | 否   |   否  |  指示MMS消息发送请求的事务ID。       |
| contentType      | string                               | 否   |   否  |  指示MMS消息发送请求的内容类型。     |
| version          | [MmsVersionType](#mmsversiontype8)   | 否   |   否  |  指示MMS消息发送请求的版本。        |
| to               | Array<[MmsAddress](#mmsaddress8)\>   | 否   |   是  |  指示MMS消息发送请求的目的地址。       |
| date             | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   是  |  指示MMS消息发送请求的日期。        |
| cc               | Array<[MmsAddress](#mmsaddress8)\>   | 否   |   是  |  指示MMS消息发送请求的抄送地址。        |
| bcc              | Array<[MmsAddress](#mmsaddress8)\>   | 否   |   是  |  指示MMS消息发送请求的暗抄送地址。       |
| subject          | string                               | 否   |   是  |  指示MMS消息发送请求的主题。         |
| messageClass     | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   是  |  指示MMS消息发送请求的消息类。       |
| expiry           | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   是  |  指示MMS消息发送请求的到期时间。         |
| priority         | [MmsPriorityType](#mmsprioritytype8) | 否   |   是  |  指示MMS消息发送请求的优先级。         |
| senderVisibility | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   是  |  指示MMS消息发送请求的发件人可见性。 |
| deliveryReport   | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   是  |  指示MMS消息发送请求的发件人可见性的交付报告。     |
| readReport       | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   是  |  指示MMS消息发送请求的发件人可见性的阅读报告。     |

## MmsSendConf<sup>8+</sup>

彩信发送配置。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|     名称      | 类型                               | 只读 |  可选 | 说明     |
| ------------- | ---------------------------------- | ---- | ----- |-------- |
| responseState | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   否  | 指示MMS消息发送配置的响应状态。 |
| transactionId | string                             | 否   |   否  | 指示MMS消息发送配置的事务ID。   |
| version       | [MmsVersionType](#mmsversiontype8) | 否   |   否  | 指示MMS消息发送配置的版本。     |
| messageId     | string                             | 否   |   是  | 指示MMS消息发送配置的消息ID。   |

## MmsNotificationInd<sup>8+</sup>

彩信通知索引。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|      名称       | 类型                               | 只读 |  可选 | 说明     |
| --------------- | ---------------------------------- | ---- | ----- | -------- |
| transactionId   | string                             | 否   |   否  | 指示MMS通知的事务ID。   |
| messageClass    | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   否  | 指示MMS通知的消息类。  |
| messageSize     | ArkTS-Dyn: number <br/>ArkTS-Sta: long| 否   |   否  | 指示MMS通知的消息大小。 |
| expiry          | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   否  | 指示MMS通知的过期时间。     |
| contentLocation | string                             | 否   |   否  | 指示MMS通知的内容位置。 |
| version         | [MmsVersionType](#mmsversiontype8) | 否   |   否  | 指示MMS通知的版本。     |
| from            | [MmsAddress](#mmsaddress8)         | 否   |   是  | 指示MMS通知的来源。     |
| subject         | string                             | 否   |   是  | 指示MMS通知的主题。     |
| deliveryReport  | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   是  | 指示MMS通知的状态报告。 |
| contentClass    | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   是  | 指示MMS通知的内容类。   |

## MmsAcknowledgeInd<sup>8+</sup>

彩信确认索引。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|      名称     | 类型                               | 只读 |  可选 | 说明     |
| ------------- | ---------------------------------- | ---- | ----- | -------- |
| transactionId | string                             | 否   |   否  | 指示MMS确认指示的事务ID。   |
| version       | [MmsVersionType](#mmsversiontype8) | 否   |   否  | 指示MMS确认指示的版本。     |
| reportAllowed | [ReportType](#reporttype8)         | 否   |   是  | 指示MMS确认指示的允许报告。 |

## MmsRetrieveConf<sup>8+</sup>

彩信检索配置。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|      名称      | 类型                                 | 只读 |  可选 | 说明     |
| -------------- | ------------------------------------ | ---- | ----- | -------- |
| transactionId  | string                               | 否   |   否  | 指示MMS消息检索配置的事务ID。   |
| messageId      | string                               | 否   |   否  | 指示MMS消息检索配置的消息ID。   |
| date           | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   否  | 指示MMS消息检索配置的日期。     |
| contentType    | string                               | 否   |   否  | 指示MMS消息检索配置的内容类型。 |
| to             | Array<[MmsAddress](#mmsaddress8)\>   | 否   |   否  | 指示MMS消息检索配置的目的地地址。   |
| version        | [MmsVersionType](#mmsversiontype8)   | 否   |   否  | 指示MMS消息检索配置的版本。     |
| from           | [MmsAddress](#mmsaddress8)           | 否   |   是  | 指示MMS消息检索配置的来源。     |
| cc             | Array<[MmsAddress](#mmsaddress8)\>   | 否   |   是  | 指示MMS消息检索配置的抄送地址。     |
| subject        | string                               | 否   |   是  | 指示MMS消息检索配置的主题。     |
| priority       | [MmsPriorityType](#mmsprioritytype8) | 否   |   是  | 指示MMS消息检索配置的优先级。   |
| deliveryReport | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   是  | 指示MMS消息检索配置的状态报告。 |
| readReport     | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   是  | 指示MMS消息检索配置的阅读报告。 |
| retrieveStatus | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 否   |   是  | 指示MMS消息检索配置的检索状态。 |
| retrieveText   | string                               | 否   |   是  | 指示MMS消息检索配置的检索文本。 |

## MmsReadOrigInd<sup>8+</sup>

彩信读取原始索引。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|    名称    | 类型                               | 只读 |  可选 | 说明     |
| ---------- | ---------------------------------- | ---- | ----- | -------- |
| version    | [MmsVersionType](#mmsversiontype8) | 否   |   否  | 指示原始MMS消息的阅读指示版本。     |
| messageId  | string                             | 否   |   否  | 指示原始MMS消息读取状态的消息ID。   |
| to         | Array<[MmsAddress](#mmsaddress8)\> | 否   |   否  | 指示原始MMS消息读取状态的目的地地址。   |
| from       | [MmsAddress](#mmsaddress8)         | 否   |   否  | 指示原始MMS消息读取状态的来源。     |
| date       | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   否  | 指示原始MMS消息读取状态的日期。     |
| readStatus | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   否  | 指示原始MMS消息读取状态的阅读状态。 |

## MmsReadRecInd<sup>8+</sup>

彩信读取记录索引。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|    名称    | 类型                               | 只读 |  可选 | 说明     |
| ---------- | ---------------------------------- | ---- | ----- | -------- |
| version    | [MmsVersionType](#mmsversiontype8) | 否   |   否  | 指示MMS消息阅读状态的版本。     |
| messageId  | string                             | 否   |   否  | 指示MMS消息阅读状态的消息ID。   |
| to         | Array<[MmsAddress](#mmsaddress8)\> | 否   |   否  | 指示MMS消息阅读状态的目的地地址。   |
| from       | [MmsAddress](#mmsaddress8)         | 否   |   否  | 指示MMS消息阅读状态的来源。     |
| readStatus | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   否  | 指示MMS消息阅读状态的阅读状态。 |
| date       | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   是  | 指示MMS消息阅读状态的日期。     |

## MmsAttachment<sup>8+</sup>

彩信附件。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|          名称           | 类型                                 | 只读 |  可选 | 说明               |
| ----------------------- | ------------------------------------ | ---- | ----- | ------------------ |
| contentId               | string                               | 否   |   否  | 指示附件的内容ID。            |
| contentLocation         | string                               | 否   |   否  | 指示附件的内容位置。           |
| contentDisposition      | [DispositionType](#dispositiontype8) | 否   |   否  | 指示附件的内容处理。           |
| contentTransferEncoding | string                               | 否   |   否  | 指示附件的内容传输编码。       |
| contentType             | string                               | 否   |   否  | 指示附件的内容类型。           |
| isSmil                  | boolean                              | 否   |   否  | 指示附件的同步多媒体集成语言。 |
| path                    | string                               | 否   |   是  | 指示附件的路径。               |
| inBuff                  | Array<number\>                       | 否   |   是  | 指示附件的缓冲区中           |
| fileName                | string                               | 否   |   是  | 指示附件的文件名。             |
| charset                 | [MmsCharSets](#mmscharsets8)         | 否   |   是  | 指示附件的字符集。             |

## MmsAddress<sup>8+</sup>

彩信地址。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|   名称  | 类型                         | 只读 |  可选 | 说明   |
| ------- | ---------------------------- | ---- | ----- | ------ |
| address | string                       | 否   |   否  | 指示MMSC地址的网络地址。   |
| charset | [MmsCharSets](#mmscharsets8) | 否   |   否  | 指示MMSC地址的字符集。 |

## MessageType<sup>8+</sup>

消息类型。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|          名称             | 值   | 说明                 |
| ------------------------- | ---- | -------------------- |
| TYPE_MMS_SEND_REQ         | 128  | 彩信发送请求类型。     |
| TYPE_MMS_SEND_CONF        | 129  | 彩信发送配置类型。     |
| TYPE_MMS_NOTIFICATION_IND | 130  | 彩信通知索引类型。     |
| TYPE_MMS_RESP_IND         | 131  | 彩信回复索引类型。     |
| TYPE_MMS_RETRIEVE_CONF    | 132  | 彩信检索配置类型。     |
| TYPE_MMS_ACKNOWLEDGE_IND  | 133  | 彩信确认索引类型。     |
| TYPE_MMS_DELIVERY_IND     | 134  | 彩信传送索引类型。     |
| TYPE_MMS_READ_REC_IND     | 135  | 彩信读取接收索引类型。 |
| TYPE_MMS_READ_ORIG_IND    | 136  | 彩信读取原始索引类型。 |

## MmsPriorityType<sup>8+</sup>

彩信优先级类型。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|    名称    | 值   | 说明           |
| ---------- | ---- | -------------- |
| MMS_LOW    | 128  | 彩信优先级低。   |
| MMS_NORMAL | 129  | 彩信优先级正常。 |
| MMS_HIGH   | 130  | 彩信优先级高。   |

## MmsVersionType<sup>8+</sup>

彩信版本类型。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|      名称       | 值   | 说明        |
| --------------- | ---- | ----------- |
| MMS_VERSION_1_0 | 0x10 | 彩信版本1_0。 |
| MMS_VERSION_1_1 | 0x11 | 彩信版本1_1。 |
| MMS_VERSION_1_2 | 0x12 | 彩信版本1_2。 |
| MMS_VERSION_1_3 | 0x13 | 彩信版本1_3。 |

## MmsCharSets<sup>8+</sup>

彩信字符集。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|      名称       | 值     | 说明                |
| --------------- | ------ | ------------------- |
| BIG5            | 0X07EA | BIG5格式。            |
| ISO_10646_UCS_2 | 0X03E8 | ISO_10646_UCS_2格式。 |
| ISO_8859_1      | 0X04   | ISO_8859_1格式。      |
| ISO_8859_2      | 0X05   | ISO_8859_2格式。      |
| ISO_8859_3      | 0X06   | ISO_8859_3格式。      |
| ISO_8859_4      | 0X07   | ISO_8859_4格式。      |
| ISO_8859_5      | 0X08   | ISO_8859_5格式。      |
| ISO_8859_6      | 0X09   | ISO_8859_6格式。      |
| ISO_8859_7      | 0X0A   | ISO_8859_7格式。      |
| ISO_8859_8      | 0X0B   | ISO_8859_8格式。      |
| ISO_8859_9      | 0X0C   | ISO_8859_9格式。      |
| SHIFT_JIS       | 0X11   | SHIFT_JIS格式。       |
| US_ASCII        | 0X03   | US_ASCII格式。        |
| UTF_8           | 0X6A   | UTF_8格式。           |

## DispositionType<sup>8+</sup>

处理类型。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|    名称    | 值   | 说明     |
| ---------- | ---- | -------- |
| FROM_DATA  | 0    | 数据来源类型。 |
| ATTACHMENT | 1    | 附件类型。     |
| INLINE     | 2    | 内联类型。     |

## ReportType<sup>8+</sup>

报告类型。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|  名称   | 值   | 说明 |
| ------- | ---- | ---- |
| MMS_YES | 128  | YES  |
| MMS_NO  | 129  | NO   |

## CBConfigOptions<sup>7+</sup>

小区广播配置选项。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|      名称      | 类型                 | 只读 |  可选 | 说明         |
| -------------- | -------------------- | ---- | ----- | ------------ |
| slotId         | ArkTS-Dyn: number <br/>ArkTS-Sta: int               | 否   |   否  | 指示单元广播配置选项的卡槽ID       |
| enable         | boolean              | 否   |   否  | 指示是否启用小区广播         |
| startMessageId | ArkTS-Dyn: number <br/>ArkTS-Sta: int               | 否   |   否  | 指示单元广播配置选项的消息起始ID。   |
| endMessageId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int               | 否   |   否  | 指示单元广播配置选项的消息结束ID。   |
| ranType        | [RanType](#rantype7) | 否   |   否  | 指示单元广播配置选项的设备网络制式。 |

## SimMessageStatus<sup>7+</sup>

SIM卡消息状态。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

|           名称            | 值   | 说明                        |
| ------------------------- | ---- | --------------------------- |
| SIM_MESSAGE_STATUS_FREE   | 0    | SIM卡上的可用空间状态。       |
| SIM_MESSAGE_STATUS_READ   | 1    | 消息已读状态。                |
| SIM_MESSAGE_STATUS_UNREAD | 3    | 消息未读状态。                |
| SIM_MESSAGE_STATUS_SENT   | 5    | 存储发送消息（仅适用于SMS。 |
| SIM_MESSAGE_STATUS_UNSENT | 7    | 存储未发送消息（仅适用于SMS）。 |

## RanType<sup>7+</sup>

设备网络制式。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

|   名称    | 值   | 说明 |
| --------- | ---- | ---- |
| TYPE_GSM  | 1    | GSM  |
| TYPE_CDMA | 2    | CMDA |

## SmsEncodingScheme<sup>8+</sup>

短信编码方案。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|         名称         | 值   | 说明         |
| -------------------- | ---- | ------------ |
| SMS_ENCODING_UNKNOWN | 0    | 未知短信编码。 |
| SMS_ENCODING_7BIT    | 1    | 7位短信编码。  |
| SMS_ENCODING_8BIT    | 2    | 8位短信编码。  |
| SMS_ENCODING_16BIT   | 3    | 16位短信编码。 |

## SimMessageOptions<sup>7+</sup>

SIM卡消息选项。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

|  名称  | 类型                                   | 只读 |  可选 | 说明           |
| ------ | -------------------------------------- | ---- | ----- | -------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int    | 否   |   否  | 指示SIM消息选项的卡槽ID。         |
| smsc   | string                                 | 否   |   否  | 指示SIM消息选项的短消息业务中心。 |
| pdu    | string                                 | 否   |   否  | 指示SIM消息选项的协议数据单元。   |
| status | [SimMessageStatus](#simmessagestatus7) | 否   |   否  | 指示SIM消息选项的状态。           |

## UpdateSimMessageOptions<sup>7+</sup>

更新SIM卡消息选项。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

|   名称    | 类型                                   | 只读 |  可选 | 说明           |
| --------- | -------------------------------------- | ---- | ----- | -------------- |
| slotId    | ArkTS-Dyn: number <br/>ArkTS-Sta: int    | 否   |   否  | 指示用于更新SIM消息选项的卡槽ID。         |
| msgIndex  | ArkTS-Dyn: number <br/>ArkTS-Sta: int    | 否   |   否  | 指示用于更新SIM消息选项的消息索引 。      |
| newStatus | [SimMessageStatus](#simmessagestatus7) | 否   |   否  | 指示用于更新SIM消息选项的新状态。         |
| pdu       | string                                 | 否   |   否  | 指示用于更新SIM消息选项的协议数据单元。   |
| smsc      | string                                 | 否   |   否  | 指示用于更新SIM消息选项的短消息业务中心。 |

## SimShortMessage<sup>7+</sup>

SIM卡短消息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

|       名称       | 类型                                   | 只读 |  可选 | 说明          |
| ---------------- | -------------------------------------- | ---- | ----- | ------------- |
| shortMessage     | [ShortMessage](js-apis-sms.md#shortmessage)          | 否   |   否  | 指示SIM卡中的短信消息。        |
| simMessageStatus | [SimMessageStatus](#simmessagestatus7) | 否   |   否  | 指示SIM卡中的SIM卡消息状态。 |
| indexOnSim       | ArkTS-Dyn: number <br/>ArkTS-Sta: int    | 否   |   否  | 指示SIM卡中的SIM卡索引。     |

## MmsDeliveryInd<sup>8+</sup>

彩信发送标识。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|    名称   | 类型                               | 只读 |  可选 | 说明   |
| --------- | ---------------------------------- | ---- | ----- | ------ |
| messageId | string                             | 否   |   否  | 指示MMS消息传送指示的消息ID。 |
| date      | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   否  | 指示MMS消息传送指示的日期。   |
| to        | Array<[MmsAddress](#mmsaddress8)\> | 否   |   否  | 指示MMS消息传送指示的目的地地址。 |
| status    | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   否  | 指示MMS消息传送指示的状态。   |
| version   | [MmsVersionType](#mmsversiontype8) | 否   |   否  | 指示MMS消息传送指示的版本。   |

## MmsRespInd<sup>8+</sup>

彩信回复标志。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|     名称      | 类型                               | 只读 |  可选 | 说明     |
| ------------- | ---------------------------------- | ---- | ----- | -------- |
| transactionId | string                             | 否   |   否  | 指示MMS响应指示的事件ID。   |
| status        | ArkTS-Dyn: number <br/>ArkTS-Sta: int| 否   |   否  | 指示MMS响应指示的状态。     |
| version       | [MmsVersionType](#mmsversiontype8) | 否   |   否  | 指示MMS响应指示的版本。     |
| reportAllowed | [ReportType](#reporttype8)         | 否   |   是  | 指示MMS响应指示的允许报告。 |

## SmsSegmentsInfo<sup>8+</sup>

短信段信息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Telephony.SmsMms

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

|        名称          | 类型                                     | 只读 |  可选 | 说明         |
| -------------------- | ---------------------------------------- | ---- | ----- | ------------ |
| splitCount           | ArkTS-Dyn: number <br/>ArkTS-Sta: int      | 否   |   否  | 拆分计数。     |
| encodeCount          | ArkTS-Dyn: number <br/>ArkTS-Sta: int      | 否   |   否  | 编码计数。     |
| encodeCountRemaining | ArkTS-Dyn: number <br/>ArkTS-Sta: int      | 否   |   否  | 剩余编码计数。 |
| scheme               | [SmsEncodingScheme](#smsencodingscheme8) | 否   |   否  | 短信编码方案。 |
