# @ohos.telephony.radio (网络搜索)

网络搜索模块提供管理网络搜索的一些基础功能，包括获取当前接入的CS域和PS域无线接入技术、获取网络状态、获取当前选网模式、获取注册网络所在国家的ISO国家码、获取主卡所在卡槽的索引号、获取指定SIM卡槽对应的注册网络信号强度信息列表、获取运营商名称，判断当前设备是否支持NR(New Radio)、判断主卡的Radio是否打开等。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```ts
import { radio } from '@kit.TelephonyKit';
```

## radio.getRadioTech

ArkTS-Dyn: getRadioTech\(slotId: number, callback: AsyncCallback<[NetworkRadioTech](#networkradiotech11)\>\): void

ArkTS-Sta: getRadioTech\(slotId: int, callback: AsyncCallback<[NetworkRadioTech](#networkradiotech11)\>\): void

获取当前接入的CS域和PS域无线接入技术。使用callback异步回调。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                   |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                                                       | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback\<[NetworkRadioTech](#networkradiotech11)\> | 是   | 回调函数。返回当前接入的CS域和PS域无线接入技术。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getRadioTech(slotId, (err: BusinessError, data: radio.NetworkRadioTech) => {
    if (err) {
        console.error(`getRadioTech failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getRadioTech success, callback: data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.getRadioTech(slotId, (err: BusinessError | null, data: radio.NetworkRadioTech | undefined) => {
    if (err?.code) {
        console.error(`getRadioTech failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`getRadioTech success, callback: data->${JSON.stringify(data)}`);
    }
    
});
```


## radio.getRadioTech

ArkTS-Dyn: getRadioTech\(slotId: number\): Promise\<[NetworkRadioTech](#networkradiotech11)\>

ArkTS-Sta: getRadioTech\(slotId: int\): Promise\<[NetworkRadioTech](#networkradiotech11)\>

获取当前接入的CS域和PS域无线接入技术。使用Promise异步回调。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                                                         | 说明                                            |
| ------------------------------------------------------------ | ----------------------------------------------- |
| Promise\<[NetworkRadioTech](#networkradiotech11)\> | 以Promise形式返回当前接入的CS域和PS域技术。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getRadioTech(slotId).then((data: radio.NetworkRadioTech) => {
    console.info(`getRadioTech success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getRadioTech failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.getRadioTech(slotId).then((data: radio.NetworkRadioTech) => {
    console.info(`getRadioTech success, promise: data->${JSON.stringify(data)}`);
    done();
}).catch((error: Error) => {
    let err: BusinessError = error;
    console.error(`getRadioTech failed, promise: err->${JSON.stringify(err)}`);
    done();
});
```


## radio.getRadioTechSync<sup>18+</sup>

ArkTS-Dyn: getRadioTechSync\(slotId: number\): [NetworkRadioTech](#networkradiotech11)

ArkTS-Sta: getRadioTechSync\(slotId: int\): [NetworkRadioTech](#networkradiotech11)

获取当前接入的CS域和PS域无线接入技术。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                                                         | 说明                                            |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [NetworkRadioTech](#networkradiotech11) | 返回当前接入的CS域和PS域技术。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { radio } from '@kit.TelephonyKit';

let slotId: number = 0;
let networkRadioTech: radio.NetworkRadioTech = radio.getRadioTechSync(slotId);
console.info(`getRadioTechSync success, NetworkRadioTech->${JSON.stringify(networkRadioTech)}`);
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';

let slotId: int = 0;
let networkRadioTech: radio.NetworkRadioTech = radio.getRadioTechSync(slotId);
console.info(`getRadioTechSync success, NetworkRadioTech->${JSON.stringify(networkRadioTech)}`);
```


## radio.getNetworkState

getNetworkState\(callback: AsyncCallback\<NetworkState\>\): void

获取网络状态。使用callback异步回调。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名   | 类型                                           | 必填 | 说明       |
| -------- | ---------------------------------------------- | ---- | ---------- |
| callback | AsyncCallback\<[NetworkState](#networkstate)\> | 是   | 回调函数。返回当前网络状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

radio.getNetworkState((err: BusinessError, data: radio.NetworkState) => {
    if (err) {
        console.error(`getNetworkState failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getNetworkState success, callback: data->${JSON.stringify(data)}`);
});
```


## radio.getNetworkState

getNetworkState\(slotId: number, callback: AsyncCallback\<NetworkState\>\): void

获取网络状态。使用callback异步回调。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名   | 类型                                           | 必填 | 说明                                   |
| -------- | ---------------------------------------------- | ---- | -------------------------------------- |
| slotId   | number                                         | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback\<[NetworkState](#networkstate)\> | 是   | 回调函数。返回当前网络状态。                             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getNetworkState(slotId, (err: BusinessError, data: radio.NetworkState) => {
    if (err) {
        console.error(`getNetworkState failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getNetworkState success, callback: data->${JSON.stringify(data)}`);
});
```


## radio.getNetworkState

getNetworkState\(slotId?: number\): Promise\<NetworkState\>

获取网络状态。使用Promise异步回调。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | 否   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。<br/> 未指定卡槽时，默认为卡槽1。 |

**返回值：**

| 类型                                     | 说明                        |
| ---------------------------------------- | --------------------------- |
| Promise\<[NetworkState](#networkstate)\> | 以Promise形式返回网络状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getNetworkState(slotId).then((data: radio.NetworkState) => {
    console.info(`getNetworkState success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getNetworkState failed, promise: err->${JSON.stringify(err)}`);
});
```


## radio.getNetworkSelectionMode

ArkTS-Dyn: getNetworkSelectionMode\(slotId: number, callback: AsyncCallback\<NetworkSelectionMode\>\): void

ArkTS-Sta: getNetworkSelectionMode\(slotId: int, callback: AsyncCallback\<NetworkSelectionMode\>\): void

获取当前选网模式。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                   |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                                                       | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |
| callback | AsyncCallback\<[NetworkSelectionMode](#networkselectionmode)\> | 是   | 回调函数。返回当前选网模式。                             |

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
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getNetworkSelectionMode(slotId, (err: BusinessError, data: radio.NetworkSelectionMode) => {
    if (err) {
        console.error(`getNetworkSelectionMode failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getNetworkSelectionMode success, callback: data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.getNetworkSelectionMode(slotId, (err: BusinessError | null, data: radio.NetworkSelectionMode | undefined) => {
    if (err?.code) {
        console.error(`getNetworkSelectionMode failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`getNetworkSelectionMode success, callback: data->${data}`);
    }
});
```


## radio.getNetworkSelectionMode

ArkTS-Dyn: getNetworkSelectionMode\(slotId?: number\): Promise\<NetworkSelectionMode\>

ArkTS-Sta: getNetworkSelectionMode\(slotId: int\): Promise\<NetworkSelectionMode\>

获取当前选网模式。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                                                     | 说明                            |
| -------------------------------------------------------- | ------------------------------- |
| Promise\<[NetworkSelectionMode](#networkselectionmode)\> | 以Promise形式返回当前选网模式。 |

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
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getNetworkSelectionMode(slotId).then((data: radio.NetworkSelectionMode) => {
    console.info(`getNetworkSelectionMode success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getNetworkSelectionMode failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.getNetworkSelectionMode(slotId).then((data: radio.NetworkSelectionMode) => {
    console.info(`getNetworkSelectionMode success, promise: data->${data}`);
    done();
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getNetworkSelectionMode failed, promise: err->${JSON.stringify(err)}`);
    done();
});
```


## radio.getISOCountryCodeForNetwork<sup>7+</sup>

ArkTS-Dyn: getISOCountryCodeForNetwork\(slotId?: number, callback?: AsyncCallback\<string\>\): void

ArkTS-Sta: getISOCountryCodeForNetwork\(slotId: int, callback: AsyncCallback\<string\>\): void

获取注册网络所在国家的ISO国家码。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                     |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                  | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。   |
| callback | AsyncCallback\<string\> | 是   | 回调函数。返回国家码，例如：CN(中国)。如果设备没有注册任何网络，接口返回空字符串。|

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
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getISOCountryCodeForNetwork(slotId, (err: BusinessError, data: string) => {
    if (err) {
        console.error(`getISOCountryCodeForNetwork failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getISOCountryCodeForNetwork success, callback: data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.getISOCountryCodeForNetwork(slotId, (err: BusinessError | null, data: string | undefined)) => {
    if (err?.code) {
        console.error(`getISOCountryCodeForNetwork failed, callback: err->${JSON.stringify(err)}`);
        done();
    } else {
        console.info(`getISOCountryCodeForNetwork success, callback: data->${JSON.stringify(data)}`);
        done();
    }
});
```


## radio.getISOCountryCodeForNetwork<sup>7+</sup>

ArkTS-Dyn: getISOCountryCodeForNetwork\(slotId?: number\): Promise\<string\>

ArkTS-Sta: getISOCountryCodeForNetwork\(slotId: int\): Promise\<string\>

获取注册网络所在国家的ISO国家码。使用Promise异步回调。

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
| Promise\<string\> | 以Promise形式返回注册网络所在国家的ISO国家码，例如CN(中国)。如果设备没有注册任何网络，接口返回空字符串。|

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
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getISOCountryCodeForNetwork(slotId).then((data: string) => {
    console.info(`getISOCountryCodeForNetwork success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getISOCountryCodeForNetwork failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.getISOCountryCodeForNetwork(slotId).then((data: string) => {
    console.info(`getISOCountryCodeForNetwork success, promise: data->${JSON.stringify(data)}`);
    done();
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getISOCountryCodeForNetwork failed, promise: err->${JSON.stringify(err)}`);
    done();
});
```

## radio.getISOCountryCodeForNetworkSync<sup>10+</sup>

ArkTS-Dyn: getISOCountryCodeForNetworkSync\(slotId?: number\): string

ArkTS-Sta: getISOCountryCodeForNetworkSync\(slotId: int\): string

获取注册网络所在国家的ISO国家码。

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
| string | 返回注册网络所在国家的ISO国家码，例如CN(中国)。如果设备没有注册任何网络，接口返回空字符串。|

**示例：**

ArkTS-Dyn示例：

```ts
import { radio } from '@kit.TelephonyKit';

let slotId: number = 0;
let countryISO: string = radio.getISOCountryCodeForNetworkSync(slotId);
console.info(`the country ISO is ${JSON.stringify(countryISO)}`);
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';

let slotId: int = 0;
let countryISO: string = radio.getISOCountryCodeForNetworkSync(slotId);
console.info(`the country ISO is ${JSON.stringify(countryISO)}`);
```



## radio.getPrimarySlotId<sup>7+</sup>

getPrimarySlotId\(callback: AsyncCallback\<number\>\): void

获取主卡所在卡槽的索引号。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<number\> | 是   | 回调函数。返回主卡所在卡槽的索引号。 |

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

radio.getPrimarySlotId((err: BusinessError, data: number) => {
    if (err) {
        console.error(`getPrimarySlotId failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getPrimarySlotId success, callback: data->${JSON.stringify(data)}`);
});
```


## radio.getPrimarySlotId<sup>7+</sup>

getPrimarySlotId\(\): Promise\<number\>

获取主卡所在卡槽的索引号。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型                                                        | 说明                                                         |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| Promise\<number\> | 以Promise形式返回获取设备主卡所在卡槽的索引号的结果。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                 错误信息                     |
| -------- | -------------------------------------------- |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

radio.getPrimarySlotId().then((data: number) => {
    console.info(`getPrimarySlotId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getPrimarySlotId failed, promise: err->${JSON.stringify(err)}`);
});
```


## radio.getSignalInformation<sup>7+</sup>

getSignalInformation\(slotId: number, callback: AsyncCallback\<Array\<SignalInformation\>\>\): void

获取指定SIM卡槽对应的注册网络信号强度信息列表。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| slotId   | number                                                       | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。                       |
| callback | AsyncCallback\<Array\<[SignalInformation](#signalinformation)\>\> | 是   | 回调函数，返回从[SignalInformation](#signalinformation)中派生出的子类对象的数组。|

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

let slotId: number = 0;
radio.getSignalInformation(slotId, (err: BusinessError, data: Array<radio.SignalInformation>) => {
    if (err) {
        console.error(`getSignalInformation failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getSignalInformation success, callback: data->${JSON.stringify(data)}`);
});
```


## radio.getSignalInformation<sup>7+</sup>

getSignalInformation\(slotId: number\): Promise\<Array\<SignalInformation\>\>

获取指定SIM卡槽对应的注册网络信号强度信息列表。使用Promise异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                                                        | 说明                                                         |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| Promise\<Array\<[SignalInformation](#signalinformation)\>\> | 以Promise形式返回网络信号强度[SignalInformation](#signalinformation)子类对象的数组。|

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

let slotId: number = 0;
radio.getSignalInformation(slotId).then((data: Array<radio.SignalInformation>) => {
    console.info(`getSignalInformation success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSignalInformation failed, promise: err->${JSON.stringify(err)}`);
});
```

## radio.getSignalInformationSync<sup>10+</sup>

ArkTS-Dyn: getSignalInformationSync\(slotId: number\): Array\<SignalInformation\>

ArkTS-Sta: getSignalInformationSync\(slotId: int\): Array\<SignalInformation\>

获取指定SIM卡槽对应的注册网络信号强度信息列表。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型                                                        | 说明                                                         |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| Array\<[SignalInformation](#signalinformation)\>| 返回网络信号强度[SignalInformation](#signalinformation)子类对象的数组。|


**示例：**

ArkTS-Dyn示例：

```ts
import { radio } from '@kit.TelephonyKit';

let slotId: number = 0;
let signalInfo: Array<radio.SignalInformation> = radio.getSignalInformationSync(slotId);
console.info(`signal information size is ${signalInfo.length}`);
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';

let slotId: int = 0;
let signalInfo: Array<radio.SignalInformation> = radio.getSignalInformationSync(slotId);
console.info(`signal information size is ${signalInfo.length}`);
```

## radio.isNrSupported<sup>8+(deprecated)</sup>

isNrSupported\(\): boolean

判断当前设备是否支持NR(New Radio)。

> **说明：**
>
> 从 API version 7开始支持，从API version 9开始废弃。建议使用[isNRSupported](#radioisnrsupported9)替代。

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型    | 说明                             |
| ------- | -------------------------------- |
| boolean | - true：支持。<br/>- false：不支持。 |

**示例：**

```ts
let result: boolean = radio.isNrSupported();
console.info("Result: "+ result);
```

## radio.isNrSupported<sup>(deprecated)</sup>

isNrSupported\(slotId: number\): boolean

判断当前设备是否支持NR(New Radio)。

> **说明：**
>
> 从 API version 8开始支持，从API version 9开始废弃。建议使用[isNRSupported](#radioisnrsupported9-1)替代。

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| boolean | - true：支持。<br/>- false：不支持。 |

**示例：**

```ts
let slotId: number = 0;
let result: boolean = radio.isNrSupported(slotId);
console.info("Result: "+ result);
```


## radio.isNRSupported<sup>9+</sup>

isNRSupported\(\): boolean

判断当前设备是否支持NR(New Radio)。

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型    | 说明                             |
| ------- | -------------------------------- |
| boolean | - true：支持。<br/>- false：不支持。 |

**示例：**

```ts
let result: boolean = radio.isNRSupported();
console.info("Result: "+ result);
```


## radio.isNRSupported<sup>9+</sup>

isNRSupported\(slotId: number\): boolean

判断当前设备是否支持NR(New Radio)。

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| boolean | - true：支持。<br/>- false：不支持。 |

**示例：**

```ts
let slotId: number = 0;
let result: boolean = radio.isNRSupported(slotId);
console.info("Result: "+ result);
```


## radio.isRadioOn<sup>7+</sup>

isRadioOn\(callback: AsyncCallback\<boolean\>\): void

判断主卡的Radio是否打开。使用callback异步回调。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                    |
| -------- | ------------------------ | ---- | ------------------------------------------------------- |
| callback | AsyncCallback\<boolean\> | 是   | 回调函数。返回主卡的Radio状态。<br/>- true：Radio打开。<br/>- false：Radio关闭。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

radio.isRadioOn((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`isRadioOn failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`isRadioOn success, callback: data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

radio.isRadioOn((err: BusinessError | null, data: boolean | undefined) => {
    if (err?.code) {
        console.error(`isRadioOn failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`isRadioOn success, callback: data->${JSON.stringify(data)}`);
    }
});
```

## radio.isRadioOn<sup>7+</sup>

ArkTS-Dyn: isRadioOn\(slotId: number, callback: AsyncCallback\<boolean\>\): void

ArkTS-Sta: isRadioOn\(slotId: int, callback: AsyncCallback\<boolean\>\): void

判断指定卡槽位的Radio是否打开。使用callback异步回调。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                    |
| -------- | ------------------------ | ---- | ------------------------------------------------------- |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                   | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。                  |
| callback | AsyncCallback\<boolean\> | 是   | 回调函数。返回指定卡槽的Radio状态。<br/>- true：Radio打开。<br/>- false：Radio关闭。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.isRadioOn(slotId, (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`isRadioOn failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`isRadioOn success, callback: data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.isRadioOn(slotId, (err: BusinessError | null, data: boolean | undefined) => {
    if (err?.code) {
        console.error(`isRadioOn failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`isRadioOn success, callback: data->${JSON.stringify(data)}`);
    }
});
```


## radio.isRadioOn<sup>7+</sup>

ArkTS-Dyn: isRadioOn\(slotId?: number\): Promise\<boolean\>

ArkTS-Sta: isRadioOn\(slotId?: int\): Promise\<boolean\>

判断Radio是否打开。使用Promise异步回调。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 否   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。<br/>如果不指定slotId，默认判断主卡Radio是否打开 |

**返回值：**

| 类型               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| Promise\<boolean\> | 以Promise形式返回判断Radio是否打开的结果。<br/>- true：Radio打开。<br/>- false：Radio关闭。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[ohos.telephony(电话子系统)错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.isRadioOn(slotId).then((data: boolean) => {
    console.info(`isRadioOn success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isRadioOn failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.isRadioOn(slotId).then((data: boolean) => {
    console.info(`isRadioOn success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`isRadioOn failed, promise: err->${JSON.stringify(err)}`);
});
```


## radio.getOperatorName<sup>7+</sup>

ArkTS-Dyn: getOperatorName\(slotId: number, callback: AsyncCallback\<string\>\): void

ArkTS-Sta: getOperatorName\(slotId: int, callback: AsyncCallback\<string\>\): void

获取运营商名称。使用callback异步回调。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                       |
| -------- | ----------------------- | ---- | ------------------------------------------ |
| slotId   | ArkTS-Dyn: number <br/>ArkTS-Sta: int                  | 是   | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。     |
| callback | AsyncCallback\<string\> | 是   | 回调函数，返回运营商名称。例如：中国移动。 |

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
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getOperatorName(slotId, (err: BusinessError, data: string) => {
    if (err) {
        console.error(`getOperatorName failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getOperatorName success, callback: data->${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.getOperatorName(slotId, (err: BusinessError | null, data: string | undefined) => {
    if (err?.code) {
        console.error(`getOperatorName failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`getOperatorName success, callback: data->${JSON.stringify(data)}`);
    }
});
```


## radio.getOperatorName<sup>7+</sup>

ArkTS-Dyn: getOperatorName\(slotId?: number\): Promise\<string\>

ArkTS-Sta: getOperatorName\(slotId: int\): Promise\<string\>

获取运营商名称。使用Promise异步回调。

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
| Promise\<string\> | 以Promise形式返回运营商名称。例如：中国移动。                |

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
import { radio } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getOperatorName(slotId).then((data: string) => {
    console.info(`getOperatorName success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getOperatorName failed, promise: err->${JSON.stringify(err)}`);
});
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';
import { BusinessError } from '@ohos.base';

let slotId: int = 0;
radio.getOperatorName(slotId).then((data: string) => {
    console.info(`getOperatorName success, promise: data->${JSON.stringify(data)}`);
}).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getOperatorName failed, promise: err->${JSON.stringify(err)}`);
});
```

## radio.getOperatorNameSync<sup>10+</sup>

ArkTS-Dyn: getOperatorNameSync\(slotId?: number\): string

ArkTS-Sta: getOperatorNameSync\(slotId: int\): string

获取运营商名称。

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
| string | 返回运营商名称。例如：中国移动。                |


**示例：**

ArkTS-Dyn示例：

```ts
import { radio } from '@kit.TelephonyKit';

let slotId: number = 0;
let operatorName: string = radio.getOperatorNameSync(slotId);
console.info(`operator name is ${JSON.stringify(operatorName)}`);
```

ArkTS-Sta示例：

```ts
import radio from '@ohos.telephony.radio';

let slotId: int = 0;
let operatorName: string = radio.getOperatorNameSync(slotId);
console.info(`operator name is ${JSON.stringify(operatorName)}`);
```

## NetworkRadioTech<sup>11+</sup>

网络中packet service (PS) 和 circuit service (CS) 无线接入技术。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

|      名称       |           类型              | 只读 | 可选 |      说明          |
| --------------- | --------------------------- | ---- | ---- | ------------------ |
| psRadioTech     | [RadioTechnology](#radiotechnology) | 否   | 否   | PS无线接入技术。 |
| csRadioTech     | [RadioTechnology](#radiotechnology) | 否   | 否   | CS无线接入技术。 |

## RadioTechnology

无线接入技术。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

| 名称                      | 值   | 说明                                                         |
| ------------------------- | ---- | ------------------------------------------------------------ |
| RADIO_TECHNOLOGY_UNKNOWN  | 0    | 未知无线接入技术(RAT)。                                    |
| RADIO_TECHNOLOGY_GSM      | 1    | 无线接入技术GSM(Global System For Mobile Communication)。  |
| RADIO_TECHNOLOGY_1XRTT    | 2    | 无线接入技术1XRTT(Single-Carrier Radio Transmission Technology)。 |
| RADIO_TECHNOLOGY_WCDMA    | 3    | 无线接入技术WCDMA(Wideband Code Division Multiple Access)。 |
| RADIO_TECHNOLOGY_HSPA     | 4    | 无线接入技术HSPA(High Speed Packet Access)。               |
| RADIO_TECHNOLOGY_HSPAP    | 5    | 无线接入技术HSPAP(High Speed packet access (HSPA+) )。     |
| RADIO_TECHNOLOGY_TD_SCDMA | 6    | 无线接入技术TD_SCDMA(TimeDivision-Synchronous Code Division Multiple Access)。 |
| RADIO_TECHNOLOGY_EVDO     | 7    | 无线接入技术EVDO(Evolution Data Only)。                   |
| RADIO_TECHNOLOGY_EHRPD    | 8    | 无线接入技术EHRPD(Evolved High Rate Package Data)。        |
| RADIO_TECHNOLOGY_LTE      | 9    | 无线接入技术LTE(Long Term Evolution)。                     |
| RADIO_TECHNOLOGY_LTE_CA   | 10   | 无线接入技术LTE_CA(Long Term Evolution_Carrier Aggregation)。 |
| RADIO_TECHNOLOGY_IWLAN    | 11   | 无线接入技术IWLAN(Industrial Wireless LAN)。               |
| RADIO_TECHNOLOGY_NR       | 12   | 无线接入技术NR(New Radio)。                                |


## SignalInformation

网络信号强度信息对象。

**系统能力：** SystemCapability.Telephony.CoreService

|      名称       |           类型              | 只读 | 可选 |      说明          |
| --------------- | --------------------------- | ---- | ---- | ------------------ |
| signalType      | [NetworkType](#networktype) | 否   | 否   | 网络信号强度类型。<br> **ArkTS-Dyn起始版本：** 6 <br>**ArkTS-Sta起始版本：** 22|
| signalLevel     | ArkTS-Dyn: number <br/>ArkTS-Sta: int                      | 否   | 否   | 网络信号强度等级。<br> **ArkTS-Dyn起始版本：** 6 <br>**ArkTS-Sta起始版本：** 22 |
| dBm<sup>9+</sup>| ArkTS-Dyn: number <br/>ArkTS-Sta: int                      | 否   | 否   | 网络信号强度。<br> **ArkTS-Dyn起始版本：** 9 <br>**ArkTS-Sta起始版本：** 22     |

## NetworkType

网络类型。

**系统能力：** SystemCapability.Telephony.CoreService

| 名称                 | 值   | 说明                                                         |
| -------------------- | ---- | ------------------------------------------------------------ |
| NETWORK_TYPE_UNKNOWN | 0    | 未知网络类型。                                               |
| NETWORK_TYPE_GSM     | 1    | 网络类型为GSM(Global System For Mobile Communication)。    |
| NETWORK_TYPE_CDMA    | 2    | 网络类型为CDMA(Code Division Multiple Access)。            |
| NETWORK_TYPE_WCDMA   | 3    | 网络类型为WCDMA(Wideband Code Division Multiple Access)。  |
| NETWORK_TYPE_TDSCDMA | 4    | 网络类型为TDSCDMA(TimeDivision-Synchronous Code Division Multiple Access)。 |
| NETWORK_TYPE_LTE     | 5    | 网络类型为LTE(Long Term Evolution)。                       |
| NETWORK_TYPE_NR      | 6    | 网络类型为NR(New Radio)。                               |

## NetworkState

网络注册状态。

**系统能力：** SystemCapability.Telephony.CoreService

|       名称           |                 类型                | 只读 | 可选 |                          说明                                |
| -------------------- | ----------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| longOperatorName     | string                              |  否  |  否  | 注册网络的长运营商名称。                                     |
| shortOperatorName    | string                              |  否  |  否  | 注册网络的短运营商名称。                                     |
| plmnNumeric          | string                              |  否  |  否  | 注册网络的PLMN码。                                           |
| isRoaming            | boolean                             |  否  |  否  | 是否处于漫游状态。                                           |
| regState             | [RegState](#regstate)               |  否  |  否  | 设备的网络注册状态。                                         |
| cfgTech<sup>8+</sup> | [RadioTechnology](#radiotechnology) |  否  |  否  | 设备的无线接入技术。                                         |
| nsaState             | [NsaState](#nsastate)               |  否  |  否  | 设备的NSA网络注册状态。                                      |
| isCaActive           | boolean                             |  否  |  否  | CA的状态。                                                   |
| isEmergency          | boolean                             |  否  |  否  | 此设备是否只允许拨打紧急呼叫。                               |


## RegState

网络注册状态。

**系统能力：** SystemCapability.Telephony.CoreService

| 名称                          | 值   | 说明                       |
| ----------------------------- | ---- | -------------------------- |
| REG_STATE_NO_SERVICE          | 0    | 设备不能使用任何服务，包括数据业务、短信、通话等。     |
| REG_STATE_IN_SERVICE          | 1    | 设备可以正常使用服务，包括数据业务、短信、通话等。     |
| REG_STATE_EMERGENCY_CALL_ONLY | 2    | 设备只能使用紧急呼叫业务。 |
| REG_STATE_POWER_OFF           | 3    | 蜂窝无线电已关闭，modem下电，无法和网侧进行通信。      |


## NsaState

非独立组网状态。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

| 名称                       | 值   | 说明                                                       |
| -------------------------- | ---- | ---------------------------------------------------------- |
| NSA_STATE_NOT_SUPPORT      | 1    | 设备在不支持NSA的LTE小区下处于空闲状态或连接状态。         |
| NSA_STATE_NO_DETECT        | 2    | 在支持NSA但不支持NR覆盖检测的LTE小区下，设备处于空闲状态。 |
| NSA_STATE_CONNECTED_DETECT | 3    | 设备在LTE小区下连接到LTE网络支持NSA和NR覆盖检测。          |
| NSA_STATE_IDLE_DETECT      | 4    | 支持NSA和NR覆盖检测的LTE小区下设备处于空闲状态。           |
| NSA_STATE_DUAL_CONNECTED   | 5    | 设备在支持NSA的LTE小区下连接到LTE + NR网络。               |
| NSA_STATE_SA_ATTACHED      | 6    | 设备在5GC附着时在NG-RAN小区下空闲或连接到NG-RAN小区。      |


## NetworkSelectionMode

选网模式。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 22

| 名称                        | 值   | 说明           |
| --------------------------- | ---- | -------------- |
| NETWORK_SELECTION_UNKNOWN   | 0    | 未知选网模式。 |
| NETWORK_SELECTION_AUTOMATIC | 1    | 自动选网模式。 |
| NETWORK_SELECTION_MANUAL    | 2    | 手动选网模式。 |


## CellInformation<sup>8+</sup>

小区信息。

**系统能力：** SystemCapability.Telephony.CoreService

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

| 名称              |                  类型                   | 只读 | 可选 |                           说明                               |
| ----------------- | --------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| networkType       | [NetworkType](#networktype)             |  否  |  否  | 获取服务单元的网络类型。                                     |
| signalInformation | [SignalInformation](#signalinformation) |  否  |  否  | 信号信息。                                                   |

