# @ohos.telephony.sim (SIM卡管理)

SIM卡管理模块提供了SIM卡管理的基础能力，包括获取指定卡槽SIM卡的ISO国家码、归属PLMN号、服务提供商名称、SIM卡状态、卡类型、是否插卡、是否激活等。

> **说明：** 
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>

## 导入模块

```ts
import { sim } from '@kit.TelephonyKit';
```

## sim.isSimActive<sup>7+</sup>

ArkTS-Dyn: isSimActive\(slotId: number, callback: AsyncCallback\<boolean\>\): void

ArkTS-Sta: isSimActive\(slotId: int, callback: AsyncCallback\<boolean\>\): void

获取指定卡槽SIM卡是否激活。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                   |
| -------- | --------------------------- | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback&lt;boolean&gt; | 是   | 回调函数。返回指定卡槽是否激活。<br/>- true:激活。<br/>- false：未激活。                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.isSimActive(0, (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.isSimActive(0, (err: BusinessError | null, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## sim.isSimActive<sup>7+</sup>

ArkTS-Dyn: isSimActive\(slotId: number\): Promise\<boolean\>

ArkTS-Sta: isSimActive\(slotId: int\): Promise\<boolean\>

获取指定卡槽SIM卡是否激活。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise&lt;boolean&gt; | 以Promise形式返回指定卡槽是否激活。<br/>- true:激活。<br/>- false：未激活。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.isSimActive(0).then((data: boolean) => {
    console.info(`isSimActive success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isSimActive failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.isSimActiveSync<sup>10+</sup>

ArkTS-Dyn: isSimActiveSync\(slotId: number\): boolean

ArkTS-Sta: isSimActiveSync\(slotId: int\): boolean

获取指定卡槽SIM卡是否激活。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| boolean | 返回指定卡槽是否激活。<br/>- true:激活。<br/>- false：未激活。 |

**示例：**

```ts
import { sim } from '@kit.TelephonyKit';

let isSimActive: boolean = sim.isSimActiveSync(0);
console.info(`the sim is active: isSimActive->${JSON.stringify(isSimActive)}`);
```


## sim.getDefaultVoiceSlotId<sup>7+</sup>

getDefaultVoiceSlotId\(callback: AsyncCallback\<number\>\): void

获取默认语音业务的卡槽ID。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名   | 类型                        | 必填 | 说明       |
| -------- | --------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;number&gt; | 是   | 回调函数。<br />- 0：卡槽1。<br />- 1：卡槽2。<br />- -1：未设置或服务不可用。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getDefaultVoiceSlotId((err: BusinessError, data: number) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## sim.getDefaultVoiceSlotId<sup>7+</sup>

getDefaultVoiceSlotId\(\): Promise\<number\>

获取默认语音业务的卡槽ID。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型              | 说明                                    |
| ----------------- | --------------------------------------- |
| Promise\<number\> | 以Promise形式返回默认语音业务的卡槽ID。<br />- 0：卡槽1。<br />- 1：卡槽2。<br />- -1：未设置或服务不可用。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getDefaultVoiceSlotId().then((data: number) => {
    console.info(`getDefaultVoiceSlotId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultVoiceSlotId failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.hasOperatorPrivileges<sup>7+</sup>

ArkTS-Dyn: hasOperatorPrivileges\(slotId: number, callback: AsyncCallback\<boolean\>\): void

ArkTS-Sta: hasOperatorPrivileges\(slotId: int, callback: AsyncCallback\<boolean\>\): void

检查应用(调用者)是否已被授予运营商权限。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                     |
| -------- | ------------------------ | ---- | ---------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                   | 是   | 卡槽ID。<br />- 0：卡槽1。<br />- 1：卡槽2。 |
| callback | AsyncCallback\<boolean\> | 是   | 回调函数。 返回检查应用(调用者)是否已被授予运营商权限。<br/>- true:授权。<br/>- false：未授权。                              |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.hasOperatorPrivileges(0, (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.hasOperatorPrivileges(0, (error: BusinessError | null, data: boolean | undefined) => {
    if (error?.code === 0) {
        console.info(`hasOperatorPrivileges success, callback: data->${JSON.stringify(data)}`);
    } else {
        console.error(`hasOperatorPrivileges failed, callback: err->${JSON.stringify(error)}`);
    }
});
```

## sim.hasOperatorPrivileges<sup>7+</sup>

ArkTS-Dyn: hasOperatorPrivileges\(slotId: number\): Promise\<boolean\>

ArkTS-Sta: hasOperatorPrivileges\(slotId: int\): Promise\<boolean\>

检查应用(调用者)是否已被授予运营商权限。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                     |
| ------ | ------ | ---- | ---------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br />- 0：卡槽1。<br />- 1：卡槽2。 |

**返回值：**

| 类型               | 说明                                                        |
| :----------------- | :---------------------------------------------------------- |
| Promise\<boolean\> | 以Promise形式返回检查应用(调用者)是否已被授予运营商权限。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.hasOperatorPrivileges(0).then((data: boolean) => {
    console.info(`hasOperatorPrivileges success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`hasOperatorPrivileges failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.hasOperatorPrivileges(0).then((data: boolean) => {
    console.info(`hasOperatorPrivileges success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`hasOperatorPrivileges failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.getISOCountryCodeForSim

ArkTS-Dyn: getISOCountryCodeForSim\(slotId: number, callback: AsyncCallback\<string\>\): void

ArkTS-Sta: getISOCountryCodeForSim\(slotId: int, callback: AsyncCallback\<string\>\): void

获取指定卡槽SIM卡的ISO国家码。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                     |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| slotId   | rkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。   |
| callback | AsyncCallback\<string\> | 是   | 回调函数。返回国家码，例如：CN(中国)。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getISOCountryCodeForSim(0, (err: BusinessError, data: string) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getISOCountryCodeForSim(0, (err: BusinessError | null, data: string) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## sim.getISOCountryCodeForSim

ArkTS-Dyn: getISOCountryCodeForSim\(slotId: number\): Promise\<string\>

ArkTS-Sta: getISOCountryCodeForSim\(slotId: int\): Promise\<string\>

获取指定卡槽SIM卡的ISO国家码。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**rkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| Promise\<string\> | 以Promise形式返回获取指定卡槽SIM卡的ISO国家码。例如：CN(中国)。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getISOCountryCodeForSim(0).then((data: string) => {
    console.info(`getISOCountryCodeForSim success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getISOCountryCodeForSim failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.getISOCountryCodeForSimSync<sup>10+</sup>

ArkTS-Dyn: getISOCountryCodeForSimSync\(slotId: number\): string

ArkTS-Sta: getISOCountryCodeForSimSync\(slotId: int\): string

获取指定卡槽SIM卡的ISO国家码。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| string | 返回获取指定卡槽SIM卡的ISO国家码。例如：CN(中国)。 |


**示例：**

ArkTS-Dyn示例：

```ts
import { sim } from '@kit.TelephonyKit';

let countryCode: string = sim.getISOCountryCodeForSimSync(0);
console.info(`the country ISO is: ${JSON.stringify(countryCode)}`);
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';

let countryCode: string = sim.getISOCountryCodeForSimSync(0);
console.info(`the country ISO is: ${JSON.stringify(countryCode)}`);
```


## sim.getSimOperatorNumeric

ArkTS-Dyn: getSimOperatorNumeric\(slotId: number, callback: AsyncCallback\<string\>\): void

ArkTS-Sta: getSimOperatorNumeric\(slotId: int, callback: AsyncCallback\<string\>\): void

获取指定卡槽SIM卡的归属PLMN(Public Land Mobile Network)号。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                   |
| -------- | ----------------------- | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                  | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback\<string\> | 是   | 回调函数。返回指定卡槽SIM卡的归属PLMN号。                          |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimOperatorNumeric(0, (err: BusinessError, data: string) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getSimOperatorNumeric(0, (error: BusinessError | null, data: string | undefined) => {
    if (error?.code === 0) {
        console.info(`getSimOperatorNumeric success, callback: data->${JSON.stringify(data)}`);
    } else {
        console.error(`getSimOperatorNumeric failed, promise: err->${JSON.stringify(err)}`);
    }
});
```


## sim.getSimOperatorNumeric

ArkTS-Dyn: getSimOperatorNumeric\(slotId: number\): Promise\<string\>

ArkTS-Sta: getSimOperatorNumeric\(slotId: int\): Promise\<string\>

获取指定卡槽SIM卡的归属PLMN(Public Land Mobile Network)号。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型              | 说明                                             |
| ----------------- | ------------------------------------------------ |
| Promise\<string\> | 以Promise形式返回获取指定卡槽SIM卡的归属PLMN号。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimOperatorNumeric(0).then((data: string) => {
    console.info(`getSimOperatorNumeric success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSimOperatorNumeric failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getSimOperatorNumeric(0).then((data: string) => {
    console.info(`getSimOperatorNumeric success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getSimOperatorNumeric failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.getSimOperatorNumericSync<sup>10+</sup>

ArkTS-Dyn: getSimOperatorNumericSync\(slotId: number\): string

ArkTS-Sta: getSimOperatorNumericSync\(slotId: int\): string

获取指定卡槽SIM卡的归属PLMN(Public Land Mobile Network)号。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型              | 说明                                             |
| ----------------- | ------------------------------------------------ |
| string | 返回获取指定卡槽SIM卡的归属PLMN号。 |


**示例：**

ArkTS-Dyn示例：

```ts
import { sim } from '@kit.TelephonyKit';

let numeric: string = sim.getSimOperatorNumericSync(0);
console.info(`the sim operator numeric is: ${JSON.stringify(numeric)}`);
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';

let numeric: string = sim.getSimOperatorNumericSync(0);
console.info(`the sim operator numeric is: ${JSON.stringify(numeric)}`);
```


## sim.getSimSpn

ArkTS-Dyn: getSimSpn\(slotId: number, callback: AsyncCallback\<string\>\): void

ArkTS-Sta: getSimSpn\(slotId: int, callback: AsyncCallback\<string\>\): void

获取指定卡槽SIM卡的服务提供商名称(Service Provider Name，SPN)。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                   |
| -------- | ----------------------- | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                  | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback\<string\> | 是   | 回调函数。返回指定卡槽SIM卡的SPN。                             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimSpn(0, (err: BusinessError, data: string) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getSimSpn(0, (error: BusinessError | null, data: string | undefined) => {
    if (error?.code === 0) {
        console.info(`getSimSpn success, callback: data->${JSON.stringify(data)}`);
    } else {
        console.error(`getSimSpn failed, callback: err->${JSON.stringify(error)}`);
    }
});
```


## sim.getSimSpn

ArkTS-Dyn: getSimSpn\(slotId: number\): Promise\<string\>

ArkTS-Sta: getSimSpn\(slotId: int\): Promise\<string\>

获取指定卡槽SIM卡的服务提供商名称(Service Provider Name，SPN)。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型              | 说明                                      |
| ----------------- | ----------------------------------------- |
| Promise\<string\> | 以Promise形式返回获取指定卡槽SIM卡的SPN。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimSpn(0).then((data: string) => {
    console.info(`getSimSpn success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSimSpn failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getSimSpn(0).then((data: string) => {
    console.info(`getSimSpn success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = err as BusinessError;
    console.error(`getSimSpn failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.getSimSpnSync<sup>10+</sup>

ArkTS-Dyn: getSimSpnSync\(slotId: number\): string

ArkTS-Sta: getSimSpnSync\(slotId: int\): string

获取指定卡槽SIM卡的服务提供商名称(Service Provider Name，SPN)。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型              | 说明                                      |
| ----------------- | ----------------------------------------- |
| string | 返回获取指定卡槽SIM卡的SPN。 |


**示例：**

ArkTS-Dyn示例：

```ts
import { sim } from '@kit.TelephonyKit';

let spn: string = sim.getSimSpnSync(0);
console.info(`the sim card spn is: ${JSON.stringify(spn)}`);
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';

let spn: string = sim.getSimSpnSync(0);
console.info(`the sim card spn is: ${JSON.stringify(spn)}`);
```


## sim.getSimState

ArkTS-Dyn: getSimState\(slotId: number, callback: AsyncCallback\<SimState\>\): void

ArkTS-Sta: getSimState\(slotId: int, callback: AsyncCallback\<SimState\>\): void

获取指定卡槽的SIM卡状态。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                   | 必填 | 说明                                   |
| -------- | -------------------------------------- | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback\<[SimState](#simstate)\> | 是   | 回调函数。参考[SimState](#simstate)。  |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimState(0, (err: BusinessError, data: sim.SimState) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimState(0, (err: BusinessError | null, data: sim.SimState) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## sim.getSimState

ArkTS-Dyn: getSimState\(slotId: number\): Promise\<SimState\>

ArkTS-Sta: getSimState\(slotId: int\): Promise\<SimState\>

获取指定卡槽的SIM卡状态。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                             | 说明                                       |
| -------------------------------- | ------------------------------------------ |
| Promise\<[SimState](#simstate)\> | 以Promise形式返回获取指定卡槽的SIM卡状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimState(0).then((data: sim.SimState) => {
    console.info(`getSimState success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSimState failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.getSimStateSync<sup>10+</sup>

ArkTS-Dyn: getSimStateSync\(slotId: number\): SimState

ArkTS-Sta: getSimStateSync\(slotId: int\): SimState

获取指定卡槽的SIM卡状态。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                         | 说明                                       |
| ---------------------------- | ------------------------------------------ |
| [SimState](#simstate) | 返回获取指定卡槽的SIM卡状态。 |


**示例：**

```ts
import { sim } from '@kit.TelephonyKit';

let simState: sim.SimState = sim.getSimStateSync(0);
console.info(`The sim state is: ${JSON.stringify(simState)}`);
```

## sim.getCardType<sup>7+</sup>

ArkTS-Dyn: getCardType\(slotId: number, callback: AsyncCallback\<CardType\>\): void

ArkTS-Sta: getCardType\(slotId: int, callback: AsyncCallback\<CardType\>\): void

获取指定卡槽SIM卡的卡类型。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                   |
| -------- | ----------------------- | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                  | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback\<[CardType](#cardtype7)\> | 是   | 回调函数。                             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getCardType(0, (err: BusinessError, data: sim.CardType) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getCardType(0, (error: BusinessError | null, data: sim.CardType | undefined) => {
    if (error?.code === 0) {
        console.info(`getCardType success, callback: data->${JSON.stringify(data)}`);
    } else {
        console.error(`getCardType failed, callback: err->${JSON.stringify(error)}`);
    }
});
```


## sim.getCardType<sup>7+</sup>

ArkTS-Dyn: getCardType\(slotId: number\): Promise\<CardType\>

ArkTS-Sta: getCardType\(slotId: int\): Promise\<CardType\>

获取指定卡槽SIM卡的卡类型。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| Promise\<[CardType](#cardtype7)\> | 以Promise形式返回指定卡槽SIM卡的卡类型。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getCardType(0).then((data: sim.CardType) => {
    console.info(`getCardType success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getCardType failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getCardType(0).then((data: sim.CardType) => {
    console.info(`getCardType success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getCardType failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.getCardTypeSync<sup>10+</sup>

ArkTS-Dyn: getCardTypeSync\(slotId: number\): CardType

ArkTS-Sta: getCardTypeSync\(slotId: int\): CardType

获取指定卡槽SIM卡的卡类型。

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| [CardType](#cardtype7) | 返回指定卡槽SIM卡的卡类型。 |


**示例：**

ArkTS-Dyn示例：

```ts
import { sim } from '@kit.TelephonyKit';

let cardType: sim.CardType = sim.getCardTypeSync(0);
console.info(`the card type is: ${JSON.stringify(cardType)}`);
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';

let cardType: sim.CardType = sim.getCardTypeSync(0);
console.info(`the card type is: ${JSON.stringify(cardType)}`);
```


## sim.hasSimCard<sup>7+</sup>

ArkTS-Dyn: hasSimCard\(slotId: number, callback: AsyncCallback\<boolean\>\): void

ArkTS-Sta: hasSimCard\(slotId: int, callback: AsyncCallback\<boolean\>\): void

获取指定卡槽SIM卡是否插卡。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                   |
| -------- | --------------------------- | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback&lt;boolean&gt; | 是  | 回调返回指定卡槽是否插卡。<br/>- true:插卡。<br/>- false：未插卡。                           |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.hasSimCard(0, (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.hasSimCard(0, (err: BusinessError | null, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## sim.hasSimCard<sup>7+</sup>

ArkTS-Dyn: hasSimCard\(slotId: number\): Promise\<boolean\>

ArkTS-Sta: hasSimCard\(slotId: int\): Promise\<boolean\>

获取指定卡槽SIM卡是否插卡。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| Promise&lt;boolean&gt; | 以Promise形式返回指定卡槽是否插卡。<br/>- true:插卡。<br/>- false：未插卡。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.hasSimCard(0).then((data: boolean) => {
    console.info(`hasSimCard success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`hasSimCard failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.hasSimCardSync<sup>10+</sup>

ArkTS-Dyn: hasSimCardSync\(slotId: number\): boolean

ArkTS-Sta: hasSimCardSync\(slotId: int\): boolean

获取指定卡槽SIM卡是否插卡。

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                  | 说明                               |
| --------------------- | ---------------------------------- |
| boolean | 返回指定卡槽是否插卡。<br/>- true:插卡。<br/>- false：未插卡。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { sim } from '@kit.TelephonyKit';

let hasSimCard: boolean = sim.hasSimCardSync(0);
console.info(`has sim card: ${JSON.stringify(hasSimCard)}`);
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';

let hasSimCard: boolean = sim.hasSimCardSync(0);
console.info(`has sim card: ${JSON.stringify(hasSimCard)}`);
```

## sim.getSimAccountInfo<sup>10+</sup>

ArkTS-Dyn: getSimAccountInfo\(slotId: number, callback: AsyncCallback\<IccAccountInfo\>\): void

ArkTS-Sta: getSimAccountInfo\(slotId: int, callback: AsyncCallback\<IccAccountInfo\>\): void

获取SIM卡帐户信息。使用callback异步回调。

**需要权限**：ohos.permission.GET_TELEPHONY_STATE

> **说明：**
>
> 获取ICCID和号码信息时需要GET_TELEPHONY_STATE权限，ICCID和号码信息为敏感数据，不向三方应用开放。调用接口时，获取到的ICCID和号码信息为空。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                   |
| -------- | --------------------------------------------------- | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number<br/>ArkTS-Sta: int          | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback&lt;[IccAccountInfo](#iccaccountinfo10)&gt; | 是   | 回调函数。返回指定卡槽SIM卡的帐户信息。                             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |
| 8301002  | The SIM card failed to read or update data.  |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimAccountInfo(0, (err:BusinessError , data: sim.IccAccountInfo) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimAccountInfo(0, (err:BusinessError | null , data: sim.IccAccountInfo) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## sim.getSimAccountInfo<sup>10+</sup>

ArkTS-Dyn: getSimAccountInfo\(slotId: number\): Promise\<IccAccountInfo\>

ArkTS-Sta: getSimAccountInfo\(slotId: int\): Promise\<IccAccountInfo\>

获取SIM卡帐户信息。使用Promise异步回调。

**需要权限**：ohos.permission.GET_TELEPHONY_STATE

> **说明：**
>
> 获取ICCID和号码信息时需要GET_TELEPHONY_STATE权限，ICCID和号码信息为敏感数据，不向三方应用开放。调用接口时，获取到的ICCID和号码信息为空。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                                         | 说明                                       |
| -------------------------------------------- | ------------------------------------------ |
| Promise&lt;[IccAccountInfo](#iccaccountinfo10)&gt; | 以Promise形式返回指定卡槽SIM卡的帐户信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |
| 8301002  | The SIM card failed to read or update data.  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimAccountInfo(0).then((data: sim.IccAccountInfo) => {
    console.info(`getSimAccountInfo success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSimAccountInfo failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.getActiveSimAccountInfoList<sup>10+</sup>

getActiveSimAccountInfoList\(callback: AsyncCallback\<Array\<IccAccountInfo\>\>\): void

获取激活SIM卡帐户信息列表。使用callback异步回调。

**需要权限**：ohos.permission.GET_TELEPHONY_STATE

> **说明：**
>
> 获取ICCID和号码信息时需要GET_TELEPHONY_STATE权限，ICCID和号码信息为敏感数据，不向三方应用开放。调用接口时，获取到的ICCID和号码信息为空。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                                        | 必填 | 说明       |
| -------- | ----------------------------------------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;Array&lt;[IccAccountInfo](#iccaccountinfo10)&gt;&gt; | 是   | 回调函数。返回激活SIM卡帐户信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getActiveSimAccountInfoList((err: BusinessError, data: Array<sim.IccAccountInfo>) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getActiveSimAccountInfoList((err: BusinessError | null, data: Array<sim.IccAccountInfo>) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## sim.getMaxSimCount<sup>7+</sup>

ArkTS-Dyn: getMaxSimCount\(\): number

ArkTS-Sta: getMaxSimCount\(\): int

获取卡槽数量。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| ArkTS-Dyn: number<br/>ArkTS-Sta: int | 卡槽数量。 |

**示例：**

```ts
import { sim } from '@kit.TelephonyKit';

console.info(`Result: ${JSON.stringify(sim.getMaxSimCount())}`);
```


## sim.getActiveSimAccountInfoList<sup>10+</sup>

getActiveSimAccountInfoList\(\): Promise\<Array\<IccAccountInfo\>\>

获取激活SIM卡帐户信息列表。使用Promise异步回调。

**需要权限**：ohos.permission.GET_TELEPHONY_STATE

> **说明：**
>
> 获取ICCID和号码信息时需要GET_TELEPHONY_STATE权限，ICCID和号码信息为敏感数据，不向三方应用开放。调用接口时，获取到的ICCID和号码信息为空。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型                                                 | 说明                                           |
| ---------------------------------------------------- | ---------------------------------------------- |
| Promise&lt;Array&lt;[IccAccountInfo](#iccaccountinfo10)&gt;&gt; | 以Promise形式返回激活卡槽SIM卡的帐户信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getActiveSimAccountInfoList().then((data: Array<sim.IccAccountInfo>) => {
    console.info(`getActiveSimAccountInfoList success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getActiveSimAccountInfoList failed, promise: err->${JSON.stringify(err)}`);
});
```


## sim.getOpKey<sup>9+</sup>

ArkTS-Dyn: getOpKey\(slotId: number, callback: AsyncCallback\<string\>): void

ArkTS-Sta: getOpKey\(slotId: int, callback: AsyncCallback\<string\>): void

获取指定卡槽中SIM卡的opkey。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                   |
| -------- | ---------------------- | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                 | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback<string\> | 是   | 回调函数。                             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 801      | Capability not supported.                    |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

try {
    sim.getOpKey(0, (err: BusinessError, data: string) => {
    if (err) {
      console.error(`getOpKey failed, err: ${JSON.stringify(err)}`);
    } else {
      console.info(`getOpKey successfully, data: ${JSON.stringify(data)}`);
    }
  });
} catch (err) {
  console.error(`getOpKey err: ${JSON.stringify(err)}`);
}
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getOpKey(0, (error: BusinessError | null, data: string | undefined) => {
    if (error?.code === 0) {
        console.info(`getOpKey success, callback: data->${JSON.stringify(data)}`); 
    } else {
        console.error(`getOpKey failed, callback: err->${JSON.stringify(error)}`);
    }
});
```


## sim.getOpKey<sup>9+</sup>

ArkTS-Dyn: getOpKey\(slotId: number\): Promise\<string\>

ArkTS-Sta: getOpKey\(slotId: int\): Promise\<string\>

获取指定卡槽中SIM卡的opkey。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型             | 说明                                      |
| ---------------- | ----------------------------------------- |
| Promise<string\> | 以Promise形式返回指定卡槽中SIM卡的opkey。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 801      | Capability not supported.                    |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getOpKey(0).then((data: string) => {
    console.info(`getOpKey success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getOpKey failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getOpKey(0).then((data: string) => {
    console.info(`getOpKey success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getOpKey failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.getOpKeySync<sup>10+</sup>

ArkTS-Dyn: getOpKeySync\(slotId: number\): string

ArkTS-Sta: getOpKeySync\(slotId: int\): string

获取指定卡槽中SIM卡的opkey。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型             | 说明                                      |
| ---------------- | ----------------------------------------- |
| string | 返回指定卡槽中SIM卡的opkey。 |


**示例：**

ArkTS-Dyn示例：

```ts
import { sim } from '@kit.TelephonyKit';

let data: string = sim.getOpKeySync(0);
console.info(`getOpKey success, promise: data->${JSON.stringify(data)}`);
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';

let data: string = sim.getOpKeySync(0);
console.info(`getOpKey success, promise: data->${JSON.stringify(data)}`);
```

## sim.getOpName<sup>9+</sup>

ArkTS-Dyn: getOpName\(slotId: number, callback: AsyncCallback\<string\>\): void

ArkTS-Sta: getOpName\(slotId: int, callback: AsyncCallback\<string\>\): void

获取指定卡槽中SIM卡的OpName。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                   |
| -------- | ---------------------- | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                 | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback<string\> | 是   | 回调函数。                               |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 801      | Capability not supported.                    |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

try {
    sim.getOpName(0, (err: BusinessError, data: string) => {
    if (err) {
      console.error(`getOpName failed, err: ${JSON.stringify(err)}`);
    } else {
      console.info(`getOpName successfully, data: ${JSON.stringify(data)}`);
    }
  });
} catch (err) {
  console.error(`getOpName err: ${JSON.stringify(err)}`);
}
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getOpName(0, (error: BusinessError | null, data: string | undefined) => {
    if (error?.code === 0) {
        console.info(`getOpName success, callback: data->${JSON.stringify(data)}`);
    } else {
        console.error(`getOpName failed, callback: err->${JSON.stringify(error)}`);
    }
});
```


## sim.getOpName<sup>9+</sup>

ArkTS-Dyn: getOpName\(slotId: number\): Promise\<string\>

ArkTS-Sta: getOpName\(slotId: int\): Promise\<string\>

获取指定卡槽中SIM卡的OpName。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型             | 说明                                       |
| ---------------- | ------------------------------------------ |
| Promise<string\> | 以Promise形式返回指定卡槽中SIM卡的OpName。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 801      | Capability not supported.                    |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getOpName(0).then((data: string) => {
    console.info(`getOpName success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getOpName failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getOpName(0).then((data: string) => {
    console.info(`getOpName success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getOpName failed, promise: err->${JSON.stringify(err)}`);
});
```

## sim.getOpNameSync<sup>10+</sup>

ArkTS-Dyn: getOpNameSync\(slotId: number\): string

ArkTS-Sta: getOpNameSync\(slotId: int\): string

获取指定卡槽中SIM卡的OpName。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型             | 说明                                       |
| ---------------- | ------------------------------------------ |
| string | 返回指定卡槽中SIM卡的OpName。 |


**示例：**

ArkTS-Dyn示例：

```ts
import { sim } from '@kit.TelephonyKit';

let data: string = sim.getOpNameSync(0);
console.info(`getOpName success, promise: data->${JSON.stringify(data)}`);
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';

let data: string = sim.getOpNameSync(0);
console.info(`getOpName success, promise: data->${JSON.stringify(data)}`);
```

## sim.getDefaultVoiceSimId<sup>10+</sup>

ArkTS-Dyn: getDefaultVoiceSimId\(callback: AsyncCallback\<number\>\): void

ArkTS-Sta: getDefaultVoiceSimId\(callback: AsyncCallback\<int\>\): void

获取默认语音业务的SIM卡ID。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                        | 必填 | 说明       |
| -------- | --------------------------- | ---- | ---------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br/>ArkTS-Sta: AsyncCallback&lt;int&gt; | 是   | 回调函数。<br/>与SIM卡绑定，从1开始递增。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |
| 8301001  | SIM card is not activated.                   |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getDefaultVoiceSimId((err: BusinessError, data: number) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

sim.getDefaultVoiceSimId((error: BusinessError | null, data: int | undefined) => {
    if (error?.code === 0) {
        console.info(`getDefaultVoiceSimId success, callback: data->${JSON.stringify(data)}`);
    } else {
        console.error(`getDefaultVoiceSimId failed, callback: err->${JSON.stringify(error)}`);
    }
});
```

## sim.getDefaultVoiceSimId<sup>10+</sup>

ArkTS-Dyn: getDefaultVoiceSimId\(\): Promise\<number\>

ArkTS-Sta: getDefaultVoiceSimId\(\): Promise\<int\>

获取默认语音业务的SIM卡ID。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型              | 说明                                    |
| ----------------- | --------------------------------------- |
| ArkTS-Dyn: Promise\<number\><br/>ArkTS-Sta: Promise\<int\> | 以Promise形式返回默认语音业务的SIM卡ID。<br/>与SIM卡绑定，从1开始递增。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300004  | No SIM card found.                           |
| 8300999  | Unknown error.                               |
| 8301001  | SIM card is not activated.                   |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let promise = sim.getDefaultVoiceSimId();
promise.then((data: number) => {
    console.info(`getDefaultVoiceSimId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultVoiceSimId failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import sim from '@ohos.telephony.sim';
import { BusinessError } from '@ohos.base';

let promise = sim.getDefaultVoiceSimId();
promise.then((data: int) => {
    console.info(`getDefaultVoiceSimId success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getDefaultVoiceSimId failed, promise: err->${JSON.stringify(err)}`);
});
```

## SimState

SIM卡状态。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

| 名称                  | 值   | 说明                                                       |
| --------------------- | ---- | ---------------------------------------------------------- |
| SIM_STATE_UNKNOWN     | 0    | SIM卡状态未知，即无法获取准确的状态。                      |
| SIM_STATE_NOT_PRESENT | 1    | 表示SIM卡处于not present状态，即卡槽中没有插入SIM卡。      |
| SIM_STATE_LOCKED      | 2    | 表示SIM卡处于locked状态，即SIM卡被PIN、PUK或网络锁锁定。   |
| SIM_STATE_NOT_READY   | 3    | 表示SIM卡处于not ready状态，即SIM卡在位但无法正常工作。    |
| SIM_STATE_READY       | 4    | 表示SIM卡处于ready状态，即SIM卡在位且工作正常。            |
| SIM_STATE_LOADED      | 5    | 表示SIM卡处于loaded状态，即SIM卡在位且所有卡文件加载完毕。 |

## CardType<sup>7+</sup>

卡类型。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

| 名称 | 值 | 说明 |
| ----- | ----- | ----- |
|UNKNOWN_CARD | -1 | 未知类型。 |
|SINGLE_MODE_SIM_CARD | 10 | 单SIM卡。 |
|SINGLE_MODE_USIM_CARD | 20 | 单USIM卡。 |
|SINGLE_MODE_RUIM_CARD | 30 | 单RUIM卡。 |
|DUAL_MODE_CG_CARD | 40 | 双卡模式C+G。 |
|CT_NATIONAL_ROAMING_CARD | 41 | 中国电信内部漫游卡。 |
|CU_DUAL_MODE_CARD | 42 | 中国联通双模卡。 |
|DUAL_MODE_TELECOM_LTE_CARD | 43 | 双模式电信LTE卡。 |
|DUAL_MODE_UG_CARD | 50 | 双模式UG卡。 |
|SINGLE_MODE_ISIM_CARD<sup>8+</sup> | 60 | 单一ISIM卡类型。 |

## IccAccountInfo<sup>10+</sup>

Icc帐户信息。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

| 名称       | 类型    | 只读| 可选 | 说明             |
| ---------- | ------- | ---- |--- |---------------- |
| simId      | ArkTS-Dyn: number <br/>ArkTS-Sta: int  |  否 |否 | SIM卡ID。          |
| slotIndex  | ArkTS-Dyn: number <br/>ArkTS-Sta: int  |  否  |否 | 卡槽ID。           |
| isEsim     | boolean |  否 | 否| 标记卡是否是eSim。<br/>- true:是eSim。<br/>- false：不是eSim。 |
| isActive   | boolean |  否 | 否| 卡是否被激活。   <br/>- true:激活。<br/>- false：未激活。  |
| iccId      | string  |  否 | 否| ICCID号码。        |
| showName   | string  |  否 | 否| SIM卡显示名称。    |
| showNumber | string  |  否 | 否| SIM卡显示号码。    |