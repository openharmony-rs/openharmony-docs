# @ohos.systemDateTime (系统时间、时区)(系统接口)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Time-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @murphy1984-->
<!--Adviser: @fang-jinxu-->

本模块主要由系统时间和系统时区功能组成。开发者可以设置、获取系统时间及系统时区。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { systemDateTime } from '@kit.BasicServicesKit';
```

## TimeType<sup>10+</sup>

定义获取时间的枚举类型。

**系统能力**: SystemCapability.MiscServices.Time

**ArkTS-Dyn起始版本:** 10

**ArkTS-Sta起始版本:** 23

| 名称    | 值   | 说明                                             |
| ------- | ---- | ------------------------------------------------ |
| STARTUP | 0    | 自系统启动以来经过的毫秒数，包括深度睡眠时间。   |
| ACTIVE  | 1    | 自系统启动以来经过的毫秒数，不包括深度睡眠时间。 |

## systemDateTime.setTime

ArkTS-Dyn: setTime(time : number, callback : AsyncCallback&lt;void&gt;) : void

ArkTS-Sta: setTime(time : long, callback : AsyncCallback&lt;void&gt;) : void

设置系统时间，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MiscServices.Time

**ArkTS-Dyn起始版本:** 9

**ArkTS-Sta起始版本:** 23

**需要权限：** ohos.permission.SET_TIME

**参数：**

| 参数名   | 类型            | 必填 | 说明                                       |
| -------- | ----------- | ---- | ---------------- |
| time     | ArkTS-Dyn: number<br>ArkTS-Sta: long                    | 是   | 目标时间戳(ms)。                         |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                        |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy.                                                            |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// time对应的时间为2021-01-20 02:36:25。
let time: number = 1611081385000;
try {
  systemDateTime.setTime(time, (error: BusinessError) => {
    if (error) {
      console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in setting time`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
}
```
ArkTS-Sta示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// time对应的时间为2021-01-20 02:36:25。
let time = 1611081385000;
try {
  systemDateTime.setTime(time, (error: BusinessError<void> | null) => {
    if (error) {
      console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in setting time`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
}
```

## systemDateTime.setTime

ArkTS-Dyn: setTime(time : number) : Promise&lt;void&gt;

ArkTS-Sta: setTime(time : long) : Promise&lt;void&gt;

设置系统时间，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MiscServices.Time

**ArkTS-Dyn起始版本:** 9

**ArkTS-Sta起始版本:** 23

**需要权限：** ohos.permission.SET_TIME

**参数：**

| 参数名 | 类型   | 必填 | 说明               |
| ------ | ------ | ---- | ------------------ |
| time   | ArkTS-Dyn: AsyncCallback&lt;number><br>ArkTS-Sta: AsyncCallback&lt;long>   | 是   | 目标时间戳(ms)。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                        |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy.                                                            |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// time对应的时间为2021-01-20 02:36:25。
let time: number = 1611081385000;
try {
  systemDateTime.setTime(time).then(() => {
    console.info(`Succeeded in setting time.`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
}
```

ArkTS-Sta示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// time对应的时间为2021-01-20 02:36:25。
let time = 1611081385000;
try {
  systemDateTime.setTime(time).then(() => {
    console.info(`Succeeded in setting time.`);
  }).catch((error: Error) => {
    console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
}
```

## systemDateTime.setDate<sup>(deprecated)</sup>

setDate(date: Date, callback: AsyncCallback&lt;void&gt;): void

设置系统日期，使用callback异步回调。

> **说明：**
>
> 从API version 9开始支持，从API 10开始废弃，建议使用[systemDateTime.setTime](#systemdatetimesettime)替代。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MiscServices.Time

**需要权限：** ohos.permission.SET_TIME

**参数：**

| 参数名   | 类型                      | 必填 | 说明          |
| -------- | ------------- | ---- |-------------|
| date     | Date                      | 是   | 目标日期，且必须>0。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。       |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                                                         |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                                                           |
| 202       | Permission verification failed. A non-system application calls a system API.                                                                 |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date();
try {
  systemDateTime.setDate(date, (error: BusinessError) => {
    if (error) {
      console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in setting date.`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
}
```

## systemDateTime.setDate<sup>(deprecated)</sup>

setDate(date: Date): Promise&lt;void&gt;

设置系统日期，使用Promise异步回调。

> **说明：**
>
> 从API version 9开始支持，从API 10开始废弃，建议使用[systemDateTime.setTime](#systemdatetimesettime)替代。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MiscServices.Time

**需要权限：** ohos.permission.SET_TIME

**参数：**

| 参数名 | 类型 | 必填 | 说明       |
| ------ | ---- | ---- | ---------- |
| date   | Date | 是   | 目标日期，且必须>0。 |

**返回值：**

| 类型                | 说明                 |
| ------------------- | -------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                                                         |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                                                           |
| 202       | Permission verification failed. A non-system application calls a system API.                                                                 |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date(); 
try {
  systemDateTime.setDate(date).then(() => {
    console.info(`Succeeded in setting date.`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
}
```

## systemDateTime.setTimezone

ArkTS-Dyn: setTimezone(timezone: string, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setTimezone(timezone: string, callback: AsyncCallback&lt;void&gt;): void

设置系统时区，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MiscServices.Time

**需要权限：** ohos.permission.SET_TIME_ZONE

**ArkTS-Dyn起始版本:** 9

**ArkTS-Sta起始版本:** 23

**参数：**

| 参数名   | 类型              | 必填 | 说明                  |
| -------- | ------------- | ---- | -------------------------- |
| timezone | string                    | 是   | 系统时区。 具体可见[支持的系统时区](#支持的系统时区) 。        |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                        |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy.                                                            |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setTimezone('Asia/Shanghai', (error: BusinessError) => {
    if (error) {
      console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in setting timezone.`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
}
```
ArkTS-Sta示例:
```ts
impoer { BusinessError } from '@ohos.base';

try {
  systemDateTime.setTimezone('Asia/Jakarta', (error: BusinessError | null) => {
    if (error) {
      console.error(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.error(`Succeeded in setting timezone.`);
  });
} catch(error: BusinessError) {
  console.error(`setTimezone error: ${error.message}, code: ${error.code}`);
}
```

## systemDateTime.setTimezone

ArkTS-Dyn: setTimezone(timezone: string): Promise&lt;void&gt;

ArkTS-Sta: setTimezone(timezone: string): Promise&lt;void&gt;

设置系统时区，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MiscServices.Time

**需要权限：** ohos.permission.SET_TIME_ZONE

**ArkTS-Dyn起始版本:** 9

**ArkTS-Sta起始版本:** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明       |
| -------- | ------ | ---- | ---------- |
| timezone | string | 是   | 系统时区。具体可见[支持的系统时区](#支持的系统时区) 。 |

**返回值：**

| 类型                | 说明                 |
| ------------------- | -------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                        |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy.                                                            |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setTimezone('Asia/Shanghai').then(() => {
    console.info(`Succeeded in setting timezone.`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
}
```

ArkTS-Sta示例：
```ts
impoer { BusinessError } from '@ohos.base';

try {
  await systemDateTime.setTimezone('Europe/Moscow');
  systemDateTime.getTimezone((error: BusinessError | null, data: String | undefined) => {
    if (error) {
      console.error(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
      reutrn;
    }
    console.error(`Succeeded in getting timezone : ${data}`);
  });
} catch(error: BusinessError) {
  console.error(`setTimezone error: ${error.message}, code: ${error.code}`);
}
```

## systemDateTime.updateNtpTime<sup>14+</sup>

ArkTS-Dyn: updateNtpTime(): Promise&lt;void&gt;

ArkTS-Sta: updateNtpTime(): Promise&lt;void&gt;

使用异步方式从NTP服务器更新NTP时间。该方法一小时内只会从NTP服务器更新一次NTP时间。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MiscServices.Time

**ArkTS-Dyn起始版本:** 14

**ArkTS-Sta起始版本:** 23

**返回值：**

| 类型                | 说明                 |
| ------------------- | -------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[时间时区错误码](./errorcode-time.md)和[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                    |
|-------|-------------------------------------------------------------------------------------------------------------|
| 13000001    | Network connection error or OS error.                                                                 |
| 202   | Permission verification failed. A non-system application calls a system API.                                |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.updateNtpTime().then(() => {
    console.info(`Succeeded in update ntp time.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to update ntp time. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to update ntp time. message: ${error.message}, code: ${error.code}`);
}
```
ArkTS-Sta示例:
```ts
import { BusinessError } from '@ohos.base';

try {
  systemDateTime.updateNtpTime().then(() => {
    console.info(`Succeeded in update ntp time.`);
  }).catch((error) => {
    console.error(`Failed to update ntp time. message: ${error.message}, code: ${error.code}`);
  });
} catch(error: BusinessError) {
  console.error(`Failed to update ntp time. message: ${error.message}, code: ${error.code}`);
}
```

## systemDateTime.getNtpTime<sup>14+</sup>

ArkTS-Dyn: getNtpTime(): number

ArkTS-Sta: getNtpTime(): long

使用同步方式获取基于上次更新的NTP时间所计算出的真实时间。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MiscServices.Time

**ArkTS-Dyn起始版本:** 14

**ArkTS-Sta起始版本:** 23

**返回值**：

| 类型   | 说明                             |
| ------ |--------------------------------|
| ArkTS-Dyn: number<br>ArkTS-Sta: long | 基于上次更新的NTP时间所计算出的Unix纪元时间(ms)。 |

**错误码：**

以下错误码的详细介绍请参见[时间时区错误码](./errorcode-time.md)和[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                    |
|-------|-------------------------------------------------------------------------------------------------------------|
| 13000002    | Location NTP time of the system is invalid.                                                           |
| 202   | Permission verification failed. A non-system application calls a system API.                                |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time = systemDateTime.getNtpTime();
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get ntp time. message: ${error.message}, code: ${error.code}`);
}
```
ArkTS-Sta示例:
```ts
import { BusinessError } from '@ohos.base';

try {
  let time: long = systemDateTime.getNtpTime();
} catch(error: BusinessError) {
  console.error(`Failed to get ntp time. message: ${error.message}, code: ${error.code}`);
}
```

## 支持的系统时区

支持的系统时区参考接口[I18n.SystemLocaleManager.getTimeZoneCityItemArray()](../apis-localization-kit/js-apis-i18n-sys.md#gettimezonecityitemarray10)。


## systemDateTime.setAutoTimeStatus<sup>21+</sup>

setAutoTimeStatus(status: boolean): Promise&lt;void&gt;

设置自动设置时间开关状态，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MiscServices.Time

**ArkTS-Dyn起始版本:** 21

**ArkTS-Sta起始版本:** 23

**需要权限：** ohos.permission.SET_TIME

**参数：**

| 参数名   | 类型   | 必填 | 说明       |
| -------- | ------ | ---- | ---------- |
| status | boolean | 是   | 设置自动设置时间开关状态。<br/>- true：表示打开自动设置时间开关。 <br/>- false：表示关闭自动设置时间开关。 |

**返回值：**

| 类型                | 说明                 |
| ------------------- | -------------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[时间时区错误码](./errorcode-time.md)和[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                        |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy.                                                            |
| 13000001  | Network connection error or OS error. Possible causes: System memory is insufficient or Calls the underlying system interface failed|


**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setAutoTimeStatus(true).then(() => {
    console.info(`Succeeded in setting autotime.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set autotime. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to set autotime. message: ${error.message}, code: ${error.code}`);
}
```

ArkTS-Sta示例:

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setAutoTimeStatus(true).then(() => {
    console.info(`Succeeded in setting autotime.`);
  }).catch((error: Error) => {
    console.error(`Failed to set autotime. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to set autotime. message: ${error.message}, code: ${error.code}`);
}
```