# @ohos.screen (屏幕)(系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

本模块提供管理屏幕的一些基础能力，包括获取屏幕对象，监听屏幕变化，创建和销毁虚拟屏幕等。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> - 本模块接口为系统接口。
> 
> - 针对系统能力SystemCapability.Window.SessionManager，请先使用[canUse()](../common/js-apis-syscap.md#caniuse)接口判断当前设备是否支持此syscap及对应接口。

## 导入模块

```ts
import { screen } from '@kit.ArkUI';
```

## screen.getAllScreens

getAllScreens(callback: AsyncCallback&lt;Array&lt;Screen&gt;&gt;): void

获取所有的屏幕，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                   |
| -------- | --------------------------------------------------- | ---- | -------------------------------------- |
| callback | AsyncCallback&lt;Array&lt;[Screen](#screen)&gt;&gt; | 是   | 回调函数。返回当前获取的屏幕对象集合。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 1400001 | Invalid display or screen. |

示例：

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | null = null;
screen.getAllScreens((err: BusinessError, data: Array<screen.Screen>) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to get all screens. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting all screens. Data: ${JSON.stringify(data)}`);
  if (data.length > 0) {
    screenClass = data[0];
  }
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | undefined = undefined;
screen.getAllScreens((err: BusinessError | null, data: Array<screen.Screen> | undefined) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to get all screens. Code:${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info(`Succeeded in getting all screens. Data: ${JSON.stringify(data)}`);
  let length: int = data?.length ?? 0;
  if (length > 0) {
    screenClass = data![0];
  }
});
```

## screen.getAllScreens

getAllScreens(): Promise&lt;Array&lt;Screen&gt;&gt;

获取所有的屏幕，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**返回值：** 

| 类型                                          | 说明                                      |
| --------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Screen](#screen)&gt;&gt; | Promise对象。返回当前获取的屏幕对象集合。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | null = null;
let promise: Promise<Array<screen.Screen>> = screen.getAllScreens();
promise.then((data: Array<screen.Screen>) => {
  if(data.length > 0){
  	screenClass = data[0];
  }
  console.info(`Succeeded in getting all screens. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get all screens. Code: ${err.code}, message : ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | null = null;
let promise: Promise<Array<screen.Screen>> = screen.getAllScreens();
promise.then((data: Array<screen.Screen>) => {
  if(data.length > 0){
  	screenClass = data[0];
  }
  console.info(`Succeeded in getting all screens. Data: ${JSON.stringify(data)}`);
}).catch((err: Error) => {
  console.error(`Failed to get all screens. Code: ${err?.code}, message : ${err?.message}`);
});
```

## screen.on('connect' | 'disconnect' | 'change')

on(eventType: 'connect' | 'disconnect' | 'change', callback: Callback&lt;number&gt;): void

开启屏幕状态变化的监听。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[screen.onConnect](#screenonconnect22)，[screen.onDisconnect](#screenondisconnect22)，[screen.onChange](#screenonchange22)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                                        |
| --------- | ---------------------- | ---- | ----------------------------------------------------------- |
| eventType | string                 | 是   | 监听事件。<br/>-eventType为"connect"表示屏幕连接事件。<br/>-eventType为"disconnect"表示断开屏幕连接事件。<br/>-eventType为"change"表示屏幕状态改变事件。 |
| callback  | Callback&lt;number&gt; | 是   | 回调函数。返回屏幕的id，该参数为整数。                                    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|

**示例：**

```ts
let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in registering the callback for screen changes. Data: ${data}`)
};
screen.on('connect', callback);
```

## screen.onConnect<sup>22+</sup>

onConnect(callback: Callback&lt;long&gt;): void

开启屏幕连接事件的监听。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[screen.on('connect' | 'disconnect' | 'change')](#screenonconnect-disconnect-change)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                                        |
| --------- | ---------------------- | ---- | ----------------------------------------------------------- |
| callback  | Callback&lt;long&gt; | 是   | 回调函数。返回屏幕的id，该参数为整数。                                    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|

**示例：**

```ts
let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in registering the callback for screen connect. Data: ${data}`)
};
screen.onConnect(callback);
```

## screen.onDisconnect<sup>22+</sup>

onDisconnect(callback: Callback&lt;long&gt;): void

开启屏幕断连事件的监听。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[screen.on('connect' | 'disconnect' | 'change')](#screenonconnect-disconnect-change)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                                        |
| --------- | ---------------------- | ---- | ----------------------------------------------------------- |
| callback  | Callback&lt;long&gt; | 是   | 回调函数。返回屏幕的id，该参数为整数。                                    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|

**示例：**

```ts
let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in registering the callback for screen disconnect. Data: ${data}`)
};
screen.onDisconnect(callback);
```

## screen.onChange<sup>22+</sup>

onChange(callback: Callback&lt;long&gt;): void

开启屏幕状态改变事件的监听。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[screen.on('connect' | 'disconnect' | 'change')](#screenonconnect-disconnect-change)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                                        |
| --------- | ---------------------- | ---- | ----------------------------------------------------------- |
| callback  | Callback&lt;long&gt; | 是   | 回调函数。返回屏幕的id，该参数为整数。                                    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|

**示例：**

```ts
let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in registering the callback for screen disconnect. Data: ${data}`)
};
screen.onChange(callback);
```

## screen.off('connect' | 'disconnect' | 'change')

off(eventType: 'connect' | 'disconnect' | 'change', callback?: Callback&lt;number&gt;): void

关闭屏幕状态变化的监听。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[screen.offConnect](#screenoffconnect22)，[screen.offDisconnect](#screenoffdisconnect22)，[screen.offChange](#screenoffchange22)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                                         |
| --------- | ---------------------- | ---- | ------------------------------------------------------------ |
| eventType | string                 | 是   | 监听事件。<br/>-eventType为"connect"表示屏幕连接事件。<br/>-eventType为"disconnect"表示断开屏幕连接事件。<br/>-eventType为"change"表示屏幕状态改变事件。 |
| callback  | Callback&lt;number&gt; | 否   | 回调函数。返回屏幕的id，该参数为整数。                                     |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|

**示例：**

```ts
let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in unregistering the callback for screen changes. Data: ${data}`)
};
screen.off('connect', callback);
screen.off('connect');
```

## screen.offConnect<sup>22+</sup>

offConnect(callback?: Callback&lt;long&gt;): void

关闭屏幕连接变化的监听。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[screen.off('connect' | 'disconnect' | 'change')](#screenoffconnect-disconnect-change)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                                         |
| --------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback  | Callback&lt;long&gt; | 否   | 回调函数。返回屏幕的id，该参数为整数。若无此参数，则取消注册屏幕连接变化监听的所有回调函数。       |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|

**示例：**

```ts
let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in unregistering the callback for screen changes. Data: ${data}`)
};
screen.offConnect(callback);
screen.offConnect();
```

## screen.offDisconnect<sup>22+</sup>

offDisconnect(callback?: Callback&lt;long&gt;): void

关闭屏幕断连变化的监听。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[screen.off('connect' | 'disconnect' | 'change')](#screenoffconnect-disconnect-change)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                                         |
| --------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback  | Callback&lt;long&gt; | 否   | 回调函数。返回屏幕的id，该参数为整数。若无此参数，则取消注册屏幕断连变化监听的所有回调函数。              |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|

**示例：**

```ts
let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in unregistering the callback for screen changes. Data: ${data}`)
};
screen.offDisconnect(callback);
screen.offDisconnect();
```

## screen.offChange<sup>22+</sup>

offChange(callback?: Callback&lt;long&gt;): void

关闭屏幕状态改变事件的监听。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[screen.off('connect' | 'disconnect' | 'change')](#screenoffconnect-disconnect-change)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                                         |
| --------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback  | Callback&lt;long&gt; | 否   | 回调函数。返回屏幕的id，该参数为整数。若无此参数，则取消注册屏幕状态改变事件监听的所有回调函数。             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|

**示例：**

```ts
let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in unregistering the callback for screen changes. Data: ${data}`)
};
screen.offChange(callback);
screen.offChange();
```

## screen.makeMirror

ArkTS-Dyn: makeMirror(mainScreen:number, mirrorScreen:Array&lt;number&gt;, callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: makeMirror(mainScreen:long, mirrorScreen:Array&lt;long&gt;, callback: AsyncCallback&lt;long&gt;): void

将屏幕设置为镜像模式，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名       | 类型                        | 必填 | 说明                 |
| ------------ | --------------------------- | ---- |--------------------|
| mainScreen   | ArkTs-Dyn: number <br> ArkTs-Sta: long                      | 是   | 主屏幕ID，该参数仅支持整数输入。  |
| mirrorScreen | ArkTs-Dyn: Array&lt;number&gt; <br> ArkTs-Sta: Array&lt;long&gt;         | 是   | 镜像屏幕ID集合，其中ID应为整数。 |
| callback     | ArkTs-Dyn: AsyncCallback&lt;number&gt; <br> ArkTs-Sta: AsyncCallback&lt;long&gt; | 是   | 回调函数。返回镜像屏幕的群组id，其中id为整数。  |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: number = 0;
let mirrorScreenIds: Array<number> = [1, 2, 3];
screen.makeMirror(mainScreenId, mirrorScreenIds, (err: BusinessError, data: number) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set screen mirroring. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: long = 0;
let mirrorScreenIds: Array<long> = [1, 2, 3];
screen.makeMirror(mainScreenId, mirrorScreenIds, (err: BusinessError | null, data: long | undefined) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to set screen mirroring. Code:${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
});
```

## screen.makeMirror

ArkTS-Dyn: makeMirror(mainScreen:number, mirrorScreen:Array&lt;number&gt;): Promise&lt;number&gt;

ArkTS-Sta: makeMirror(mainScreen:long, mirrorScreen:Array&lt;long&gt;): Promise&lt;long&gt;

将屏幕设置为镜像模式，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名       | 类型                | 必填 | 说明                 |
| ------------ | ------------------- | ---- |--------------------|
| mainScreen   | ArkTs-Dyn: number <br> ArkTs-Sta: long              | 是   | 主屏幕ID，该参数仅支持整数输入。  |
| mirrorScreen | ArkTs-Dyn: Array&lt;number&gt; <br> ArkTs-Sta: Array&lt;long&gt; | 是   | 镜像屏幕ID集合。其中ID应为整数。 |

**返回值：**

| 类型                  | 说明                              |
| --------------------- |---------------------------------|
| ArkTs-Dyn: Promise&lt;number&gt; <br> ArkTs-Sta: Promise&lt;long&gt; | Promise对象。返回镜像屏幕的群组id，其中id为整数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: number = 0;
let mirrorScreenIds: Array<number> = [1, 2, 3];
screen.makeMirror(mainScreenId, mirrorScreenIds).then((data: number) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen mirroring. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: long = 0;
let mirrorScreenIds: Array<long> = [1, 2, 3];
screen.makeMirror(mainScreenId, mirrorScreenIds).then((data: long) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: Error) => {
  console.error(`Failed to set screen mirroring. Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.stopMirror<sup>10+</sup>

ArkTS-Dyn: stopMirror(mirrorScreen:Array&lt;number&gt;, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: stopMirror(mirrorScreen:Array&lt;long&gt;, callback: AsyncCallback&lt;void&gt;): void

停止屏幕的镜像模式，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型 | 必填 | 说明                                      |
| ------------ | --------------------------- | --- |-----------------------------------------|
| mirrorScreen | ArkTs-Dyn: Array&lt;number&gt; <br> ArkTs-Sta: Array&lt;long&gt; | 是   | 镜像屏幕ID集合，其中ID应为整数。 mirrorScreen数组大小不应超过1000。 |
| callback     | AsyncCallback&lt;void&gt; | 是   | 回调函数。当停止屏幕镜像模式成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mirrorScreenIds: Array<number> = [1, 2, 3];
screen.stopMirror(mirrorScreenIds, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to stop mirror screens. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in stopping mirror screens.');
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mirrorScreenIds: Array<long> = [1, 2, 3];
screen.stopMirror(mirrorScreenIds, (err: BusinessError | null) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to stop mirror screens. Code:${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info('Succeeded in stopping mirror screens.');
});
```

## screen.stopMirror<sup>10+</sup>

ArkTS-Dyn: stopMirror(mirrorScreen:Array&lt;number&gt;): Promise&lt;void&gt;

ArkTS-Sta: stopMirror(mirrorScreen:Array&lt;long&gt;): Promise&lt;void&gt;

停止屏幕的镜像模式，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------------ | ------------------- | --- |--------------------|
| mirrorScreen | ArkTs-Dyn: Array&lt;number&gt; <br> ArkTs-Sta: Array&lt;long&gt; | 是   | 镜像屏幕ID集合，其中ID应为整数。mirrorScreen数组大小不应超过1000。 |

**返回值：**

| 类型 | 说明 |
| --------------------- | ----------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mirrorScreenIds: Array<number> = [1, 2, 3];
screen.stopMirror(mirrorScreenIds).then(() => {
  console.info('Succeeded in stopping mirror screens.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop mirror screens.Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
let mirrorScreenIds: Array<long> = [1, 2, 3];
screen.stopMirror(mirrorScreenIds).then(() => {
  console.info('Succeeded in stopping mirror screens.');
}).catch((err: Error) => {
  console.error(`Failed to stop mirror screens.Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.makeUnique<sup>18+</sup>

ArkTS-Dyn: makeUnique(uniqueScreen: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

ArkTS-Sta: makeUnique(uniqueScreen: Array&lt;long&gt;): Promise&lt;Array&lt;long&gt;&gt;

将屏幕设置为异源模式，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Window.SessionManager

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 22

**设备行为差异：** 该接口在Phone设备、PC/2in1设备、Tablet设备中可正常调用，在其他设备中不生效不报错。

**参数：**

| 参数名    | 类型   | 必填 | 说明          |
| --------- | ------ | ---- | ------------- |
| uniqueScreen  | ArkTs-Dyn: Array&lt;number&gt; <br> ArkTs-Sta: Array&lt;long&gt; | 是   | 异源屏幕ID集合。其中ID应为大于0的整数，否则返回401错误码。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| ArkTs-Dyn: Promise&lt;Array&lt;number&gt;&gt; <br> ArkTs-Sta: Promise&lt;Array&lt;long&gt;&gt; | Promise对象。返回异源屏幕的displayId集合，其中id为大于0的整数。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed, non-system application uses system API. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1400001 | Invalid display or screen. |
| 1400003 | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let uniqueScreenIds: Array<number> = [1001, 1002, 1003];
screen.makeUnique(uniqueScreenIds).then((data: Array<number>) => {
  console.info('Succeeded in making unique screens.');
}).catch((err: BusinessError) => {
  console.error(`Failed to make unique screens. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let uniqueScreenIds: Array<long> = [1001, 1002, 1003];
screen.makeUnique(uniqueScreenIds).then((data: Array<long>) => {
  console.info('Succeeded in making unique screens.');
}).catch((err: BusinessError) => {
  let error = exception as BusinessError;
  console.error(`Failed to make unique screens. Code:${error.code}, message is ${error.message}`);
});
```


## screen.createVirtualScreen

createVirtualScreen(options:VirtualScreenOption, callback: AsyncCallback&lt;Screen&gt;): void

创建虚拟屏幕，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**需要权限**：ohos.permission.CAPTURE_SCREEN

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                               |
| -------- | ------------------------------------------- | ---- | ---------------------------------- |
| options  | [VirtualScreenOption](#virtualscreenoption) | 是   | 用于创建虚拟屏幕的参数。           |
| callback | AsyncCallback&lt;[Screen](#screen)&gt;      | 是   | 回调函数，返回创建的虚拟屏幕对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | null = null;
class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
}

let option : VirtualScreenOption = { 
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};
screen.createVirtualScreen(option, (err: BusinessError, data: screen.Screen) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
    return;
  }
  screenClass = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
});
```

ArkTS-Sta示例：

```ts
let option : screen.VirtualScreenOption = { 
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};
screen.createVirtualScreen(option, (err: BusinessError | null, data) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to create the virtual screen. Code:${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
});
```

## screen.createVirtualScreen

createVirtualScreen(options:VirtualScreenOption): Promise&lt;Screen&gt;

创建虚拟屏幕，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**需要权限**：ohos.permission.CAPTURE_SCREEN

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名  | 类型                                        | 必填 | 说明                     |
| ------- | ------------------------------------------- | ---- | ------------------------ |
| options | [VirtualScreenOption](#virtualscreenoption) | 是   | 用于创建虚拟屏幕的参数。 |

**返回值：**

| 类型                             | 说明                                  |
| -------------------------------- | ------------------------------------- |
| Promise&lt;[Screen](#screen)&gt; | Promise对象。返回创建的虚拟屏幕对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | null = null;
class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
}

let option : VirtualScreenOption = { 
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  screenClass = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
}).catch((err: Error) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
let screenClass: screen.Screen | null = null;

let option : screen.VirtualScreenOption = { 
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};
screen.createVirtualScreen(option).then((data: screen.Screen) => {
  screenClass = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
}).catch((err: Error) => {
  console.error(`Failed to create the virtual screen. Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.destroyVirtualScreen

ArkTS-Dyn: destroyVirtualScreen(screenId:number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: destroyVirtualScreen(screenId:long, callback: AsyncCallback&lt;void&gt;): void

销毁虚拟屏幕，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                                         |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| screenId | ArkTs-Dyn: number <br> ArkTs-Sta: long             | 是   | 屏幕的id，该参数仅支持整数输入。                                                   |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。当销毁虚拟屏幕成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400002 | Unauthorized operation. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: number = 1;
screen.destroyVirtualScreen(screenId, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to destroy the virtual screen. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in destroying the virtual screen.');
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: long = 1;
screen.destroyVirtualScreen(screenId, (err: BusinessError | null) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to destroy the virtual screen. Code:${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info('Succeeded in destroying the virtual screen.');
});
```

## screen.destroyVirtualScreen

ArkTS-Dyn: destroyVirtualScreen(screenId:number): Promise&lt;void&gt;

ArkTS-Sta: destroyVirtualScreen(screenId:long): Promise&lt;void&gt;

销毁虚拟屏幕，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型   | 必填 | 说明       |
| -------- | ------ | ---- | ---------- |
| screenId | ArkTs-Dyn: number <br> ArkTs-Sta: long | 是   | 屏幕的id，该参数仅支持整数输入。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400002 | Unauthorized operation. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: number = 1;
screen.destroyVirtualScreen(screenId).then(() => {
  console.info('Succeeded in destroying the virtual screen.');
}).catch((err: BusinessError) => {
  console.error(`Failed to destroy the virtual screen.Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: long = 1;
screen.destroyVirtualScreen(screenId).then(() => {
  console.info('Succeeded in destroying the virtual screen.');
}).catch((err: Error) => {
  console.error(`Failed to destroy the virtual screen. Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.setVirtualScreenSurface

ArkTS-Dyn: setVirtualScreenSurface(screenId:number, surfaceId: string, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setVirtualScreenSurface(screenId:long, surfaceId: string, callback: AsyncCallback&lt;void&gt;): void

设置虚拟屏幕的surface，表示当前虚拟屏用于显示对应surface中的内容，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**需要权限**：ohos.permission.CAPTURE_SCREEN，仅系统应用可用。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                      | 必填 | 说明                                                         |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| screenId  | ArkTs-Dyn: number <br> ArkTs-Sta: long | 是   | 屏幕的id，该参数仅支持整数输入。                                                   |
| surfaceId | string                    | 是   | 代表虚拟屏幕的surface标识符，surfaceId值可自行定义，由用户指定某一实际存在的surface。 |
| callback  | AsyncCallback&lt;void&gt; | 是   | 回调函数。当设置虚拟屏幕surface成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  xComponentController: XComponentController = new XComponentController();

  setVirtualScreenSurface = () => {
    let screenId: number = 1;
    let surfaceId = this.xComponentController.getXComponentSurfaceId();
    screen.setVirtualScreenSurface(screenId, surfaceId, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the surface for the virtual screen. Code:${err.code}, message is ${err.message}`);
      return;
    }
      console.info('Succeeded in setting the surface for the virtual screen.');
    });
  }
  build() {
    RelativeContainer() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
      Button('setSurface')
        .onClick((event: ClickEvent) => {
          this.setVirtualScreenSurface();
      }).width('100%')
      .height(20)
    }
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: long = 1;
let surfaceId: string = '2048';
screen.setVirtualScreenSurface(screenId, surfaceId, (err: BusinessError | null) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to set the surface for the virtual screen. Code:${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info('Succeeded in setting the surface for the virtual screen.');
});
```

## screen.setVirtualScreenSurface

ArkTS-Dyn: setVirtualScreenSurface(screenId:number, surfaceId: string): Promise&lt;void&gt;

ArkTS-Sta: setVirtualScreenSurface(screenId:long, surfaceId: string): Promise&lt;void&gt;

设置虚拟屏幕的surface，表示当前虚拟屏用于显示对应surface中的内容，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**需要权限**：ohos.permission.CAPTURE_SCREEN，仅系统应用可用。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型   | 必填 | 说明          |
| --------- | ------ | ---- | ------------- |
| screenId  | ArkTs-Dyn: number <br> ArkTs-Sta: long | 是   | 屏幕的id，该参数仅支持整数输入。    |
| surfaceId | string | 是   | 代表虚拟屏幕的surface标识符，surfaceId值可自行定义，由用户指定某一实际存在的surface。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  xComponentController: XComponentController = new XComponentController();

  setVirtualScreenSurface = () => {
    let screenId: number = 1;
    let surfaceId = this.xComponentController.getXComponentSurfaceId();
    screen.setVirtualScreenSurface(screenId, surfaceId).then(() => {
      console.info('Succeeded in setting the surface for the virtual screen.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set the surface for the virtual screen. Code:${err.code}, message is ${err.message}`);
    });
  }
  build() {
    RelativeContainer() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
      Button('setSurface')
        .onClick((event: ClickEvent) => {
          this.setVirtualScreenSurface();
      }).width('100%')
      .height(20)
    }
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: long = 1;
let surfaceId: string = '2048';
screen.setVirtualScreenSurface(screenId, surfaceId).then(() => {
  console.info('Succeeded in setting the surface for the virtual screen.');
}).catch((err: Error) => {
  console.error(`Failed to set the surface for the virtual screen. Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.setScreenPrivacyMaskImage<sup>19+</sup>

ArkTS-Dyn: setScreenPrivacyMaskImage(screenId:number, image?: image.PixelMap): Promise&lt;void&gt;

ArkTS-Sta: setScreenPrivacyMaskImage(screenId:long, image?: image.PixelMap): Promise&lt;void&gt;

设置屏幕的隐私蒙版图片，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Window.SessionManager

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型   | 必填 | 说明          |
| --------- | ------ | ---- | ------------- |
| screenId  | ArkTs-Dyn: number <br> ArkTs-Sta: long | 是   | 屏幕的id，该参数仅支持正整数输入。    |
| image | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 否   | 屏幕的隐私蒙版图片，不传入则使用默认隐私蒙版图片。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1400001 | Invalid display or screen. |
| 1400003 | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素buffer大小，取值为：height * width *4
let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
image.createPixelMap(color, opts).then((pixelMap: image.PixelMap) => {
  console.info('Succeeded in creating pixelmap.');
  let screenId: number = 1;
  screen.setScreenPrivacyMaskImage(screenId, pixelMap).then(() => {
    console.info('Succeeded in setting the privacy mask image for the screen.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the privacy mask image for the screen. Code:${err.code}, message is ${err.message}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
})
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素buffer大小，取值为：height * width *4
let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
image.createPixelMap(color, opts).then((pixelMap: image.PixelMap) => {
  console.info('Succeeded in creating pixelmap.');
  let screenId: long = 1;
  screen.setScreenPrivacyMaskImage(screenId, pixelMap).then(() => {
    console.info('Succeeded in setting the privacy mask image for the screen.');
  }).catch((err: Error) => {
    console.error(`Failed to set the privacy mask image for the screen. Code:${err?.code}, message is ${err?.message}`);
  });
}).catch((error: Error) => {
  console.error(`Failed to create pixelmap. code is ${error?.code}, message is ${error?.message}`);
})
```

## screen.isScreenRotationLocked

isScreenRotationLocked(): Promise&lt;boolean&gt;

查询当前自动转屏是否锁定，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型                   | 说明                                  |
| ---------------------- | ------------------------------------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前自动转屏处于锁定状态；返回false表示当前自动转屏不处于锁定状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

screen.isScreenRotationLocked().then((isLocked: boolean) => {
  console.info(`Succeeded in getting the screen rotation lock status. isLocked: ${isLocked}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get the screen rotation lock status. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

screen.isScreenRotationLocked().then((isLocked: boolean) => {
  console.info(`Succeeded in getting the screen rotation lock status. isLocked: ${isLocked}`);
}).catch((err: Error) => {
  console.error(`Failed to get the screen rotation lock status. Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.isScreenRotationLocked

isScreenRotationLocked(callback: AsyncCallback&lt;boolean&gt;): void

查询当前自动转屏是否锁定，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                          | 必填 | 说明                                                         |
| --------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| callback  | AsyncCallback&lt;boolean&gt; | 是   | 回调函数。返回true表示当前自动转屏处于锁定状态；返回false表示当前自动转屏不处于锁定状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

screen.isScreenRotationLocked((err: BusinessError, isLocked: boolean) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to get the screen rotation lock status. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting the screen rotation lock status. isLocked: ${isLocked}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

screen.isScreenRotationLocked((err: BusinessError | null, isLocked: boolean | undefined) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to get the screen rotation lock status. Code:${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info(`Succeeded in getting the screen rotation lock status. isLocked: ${isLocked}`);
});
```

## screen.setScreenRotationLocked

setScreenRotationLocked(isLocked: boolean): Promise&lt;void&gt;

设置自动转屏开关是否锁定，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**设备行为差异：** 仅在支持跟随sensor旋转的设备中生效，其他设备调用不生效不报错。

**参数：**

| 参数名    | 类型   | 必填 | 说明          |
| --------- | ------ | ---- | ------------- |
| isLocked  | boolean | 是   | 自动转屏开关是否锁定。true为锁定，false为未锁定。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let isLocked: boolean = false;
screen.setScreenRotationLocked(isLocked).then(() => {
  console.info('Succeeded in unlocking auto rotate');
}).catch((err: BusinessError) => {
  console.error(`Failed to unlock auto rotate. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let isLocked: boolean = false;
screen.setScreenRotationLocked(isLocked).then(() => {
  console.info('Succeeded in unlocking auto rotate');
}).catch((err: Error) => {
  console.error(`Failed to unlock auto rotate. Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.setScreenRotationLocked

setScreenRotationLocked(isLocked: boolean, callback: AsyncCallback&lt;void&gt;): void

设置自动转屏开关是否锁定，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**设备行为差异：** 仅在支持跟随sensor旋转的设备中生效，其他设备调用不生效不报错。

**参数：**

| 参数名    | 类型                      | 必填 | 说明                                                         |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| isLocked  | boolean                   | 是   | 自动转屏开关是否锁定。true为锁定，false为未锁定。                 |
| callback  | AsyncCallback&lt;void&gt; | 是   | 回调函数。当设置自动转屏是否锁定成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let isLocked: boolean = false;
screen.setScreenRotationLocked(isLocked, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to unlock auto rotate. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in unlocking auto rotate.');
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let isLocked: boolean = false;
screen.setScreenRotationLocked(isLocked, (err: BusinessError) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to unlock auto rotate. Code:${err?.code}, message is ${err?.message}`);
    return;
  }
  console.info('Succeeded in unlocking auto rotate.');
});
```

## screen.setMultiScreenMode<sup>13+</sup>

ArkTS-Dyn: setMultiScreenMode(primaryScreenId: number, secondaryScreenId: number, secondaryScreenMode: MultiScreenMode): Promise&lt;void&gt;

ArkTS-Sta: setMultiScreenMode(primaryScreenId: long, secondaryScreenId: long, secondaryScreenMode: MultiScreenMode): Promise&lt;void&gt;

设置扩展屏幕的显示模式（镜像/扩展），使用Promise异步回调。primaryScreenId和secondaryScreenId均为0时，仅在扩展屏显示。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名       | 类型                 | 必填 | 说明                |
| ------------ | ------------------- | ---- |--------------------|
| primaryScreenId   | ArkTs-Dyn: number <br> ArkTs-Sta: long           | 是  | 主屏的id，该参数应为非负整数。如果输入的数字包含小数部分，向下取整。|
| secondaryScreenId | ArkTs-Dyn: number <br> ArkTs-Sta: long           | 是  | 扩展屏幕的id，该参数应为非负整数。如果输入的数字包含小数部分，向下取整。|
| secondaryScreenMode | [MultiScreenMode](#multiscreenmode13)  | 是  | 扩展屏幕的显示模式。|

**返回值：**

| 类型               | 说明                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 202     | Permission verification failed, non-system application uses system API. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 1400003 | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let primaryScreenId: number = 0;
let secondaryScreenId: number = 12;
let screenMode: screen.MultiScreenMode = screen.MultiScreenMode.SCREEN_MIRROR;
screen.setMultiScreenMode(primaryScreenId, secondaryScreenId, screenMode).then(() => {
  console.info('Succeeded in setting multi screen mode. Data: ');
}).catch((err: BusinessError) => {
  console.error(`Failed to set multi screen mode. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let primaryScreenId: long = 0;
let secondaryScreenId: long = 12;
let screenMode: screen.MultiScreenMode = screen.MultiScreenMode.SCREEN_MIRROR;
screen.setMultiScreenMode(primaryScreenId, secondaryScreenId, screenMode).then(() => {
  console.info('Succeeded in setting multi screen mode. Data: ');
}).catch((err: Error) => {
  console.error(`Failed to set multi screen mode. Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.setMultiScreenRelativePosition<sup>13+</sup>

setMultiScreenRelativePosition(mainScreenOptions: MultiScreenPositionOptions, secondaryScreenOptions: MultiScreenPositionOptions): Promise&lt;void&gt;

仅在扩展模式下，设置主屏和扩展屏幕的位置信息，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名       | 类型                 | 必填 | 说明               |
| ------------ | ------------------- | ---- |--------------------|
| mainScreenOptions      | [MultiScreenPositionOptions](#multiscreenpositionoptions13)  | 是  | 主屏的位置信息。|
| secondaryScreenOptions | [MultiScreenPositionOptions](#multiscreenpositionoptions13)  | 是  | 扩展屏幕的位置信息。|

**返回值：**

| 类型                | 说明                       |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 202     | Permission verification failed, non-system application uses system API. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 1400003 | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenOptions: screen.MultiScreenPositionOptions = {
  id : 0,
  startX : 0,
  startY : 0
};

let secondaryScreenOptions: screen.MultiScreenPositionOptions = {
  id : 12,
  startX : 1000,
  startY : 1000
};

screen.setMultiScreenRelativePosition(mainScreenOptions, secondaryScreenOptions).then(() => {
  console.info('Succeeded in setting multi screen relative position.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set multi screen relative position. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
let mainScreenOptions: screen.MultiScreenPositionOptions = {
  id : 0,
  startX : 0,
  startY : 0
};

let secondaryScreenOptions: screen.MultiScreenPositionOptions = {
  id : 12,
  startX : 1000,
  startY : 1000
};

screen.setMultiScreenRelativePosition(mainScreenOptions, secondaryScreenOptions).then(() => {
  console.info('Succeeded in setting multi screen relative position.');
}).catch((err: Error) => {
  console.error(`Failed to set multi screen relative position. Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.makeMirrorWithRegion<sup>19+</sup>

ArkTS-Dyn: makeMirrorWithRegion(mainScreen:number, mirrorScreen:Array&lt;number&gt;, mainScreenRegion:Rect): Promise&lt;number&gt;

ArkTS-Sta: makeMirrorWithRegion(mainScreen:long, mirrorScreen:Array&lt;long&gt;, mainScreenRegion:Rect): Promise&lt;long&gt;

将屏幕的某一矩形区域设置为镜像模式，使用Promise异步回调。调用该接口后，不建议再进行屏幕的旋转/折叠，否则可能导致镜像内容异常。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名       | 类型                | 必填 | 说明                 |
| ------------ | ------------------- | ---- |--------------------|
| mainScreen   | ArkTs-Dyn: number <br> ArkTs-Sta: long              | 是   | 主屏幕ID，该参数仅支持正整数输入。  |
| mirrorScreen | ArkTs-Dyn: Array&lt;number&gt; <br> ArkTs-Sta: Array&lt;long&gt; | 是   | 镜像屏幕ID集合。其中ID应为正整数。  |
| mainScreenRegion | [Rect](#rect19) | 是   | 主屏创建镜像的矩形区域。         |

**返回值：**

| 类型                  | 说明                              |
| --------------------- |---------------------------------|
| Promise&lt;number&gt; | Promise对象。返回镜像屏幕的群组id，其中id为正整数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 1400001 | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: number = 0;
let mirrorScreenIds: Array<number> = [1, 2, 3];
let mainScreenRegion: screen.Rect = {
  left : 0,
  top : 0,
  width : 1920,
  height : 1080
};
screen.makeMirrorWithRegion(mainScreenId, mirrorScreenIds, mainScreenRegion).then((data: number) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen area mirroring. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: long = 0;
let mirrorScreenIds: Array<long> = [1, 2, 3];
let mainScreenRegion: screen.Rect = {
  left : 0,
  top : 0,
  width : 1920,
  height : 1080
};
screen.makeMirrorWithRegion(mainScreenId, mirrorScreenIds, mainScreenRegion).then((data: long) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: Error) => {
  console.error(`Failed to set screen area mirroring. Code:${err?.code}, message is ${err?.message}`);
});
```

## screen.makeExpand<sup>(deprecated)</sup>

makeExpand(options:Array&lt;ExpandOption&gt;, callback: AsyncCallback&lt;number&gt;): void

将屏幕设置为扩展模式，使用callback异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型                                       | 必填 | 说明                         |
| -------- | ------------------------------------------ | ---- |----------------------------|
| options  | Array&lt;[ExpandOption](#expandoption)&gt; | 是   | 设置扩展屏幕的参数集合。               |
| callback | AsyncCallback&lt;number&gt;                     | 是   | 回调函数。返回扩展屏幕的群组id，其中id为整数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400001 | Invalid display or screen. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let groupId: number | null = null;
class ExpandOption {
  screenId: number = 0;
  startX: number = 0;
  startY: number = 0;
}
let mainScreenOption: ExpandOption = { screenId: 0, startX: 0, startY: 0 };
let otherScreenOption: ExpandOption = { screenId: 1, startX: 1080, startY: 0 };
let expandOptionArray : ExpandOption[] = [ mainScreenOption, otherScreenOption ];
screen.makeExpand(expandOptionArray, (err: BusinessError, data: number) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to expand the screen. Code:${err.code}, message is ${err.message}`);
    return;
  }
  groupId = data;
  console.info(`Succeeded in expanding the screen. Data: ${data}`);
});
```

## screen.makeExpand<sup>(deprecated)</sup>

makeExpand(options:Array&lt;ExpandOption&gt;): Promise&lt;number&gt;

将屏幕设置为扩展模式，使用Promise异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名  | 类型                                       | 必填 | 说明                     |
| ------- | ------------------------------------------ | ---- | ------------------------ |
| options | Array&lt;[ExpandOption](#expandoption)&gt; | 是   | 设置扩展屏幕的参数集合。 |

**返回值：**

| 类型                  | 说明                              |
| --------------------- |---------------------------------|
| Promise&lt;number&gt; | Promise对象。返回扩展屏幕的群组id，其中id为整数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400001 | Invalid display or screen. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class ExpandOption {
  screenId: number = 0;
  startX: number = 0;
  startY: number = 0;
}
let mainScreenOption: ExpandOption = { screenId: 0, startX: 0, startY: 0 };
let otherScreenOption: ExpandOption = { screenId: 1, startX: 1080, startY: 0 };
let expandOptionArray : ExpandOption[] = [ mainScreenOption, otherScreenOption ];
screen.makeExpand(expandOptionArray).then((
  data: number) => {
  console.info(`Succeeded in expanding the screen. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to expand the screen. Code:${err.code}, message is ${err.message}`);
});
```

## screen.stopExpand<sup>(deprecated)</sup>

stopExpand(expandScreen:Array&lt;number&gt;, callback: AsyncCallback&lt;void&gt;): void

停止屏幕的扩展模式，使用callback异步回调。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 10

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明                                      |
| ------------ | --------------------------- | --- |-----------------------------------------|
| expandScreen | Array&lt;number&gt;         | 是   | 扩展屏幕ID集合，其中ID为整数。 expandScreen数组大小不应超过1000。  |
| callback     | AsyncCallback&lt;void&gt; | 是   | 回调函数。当停止屏幕扩展模式成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 1400001 | Invalid display or screen. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let expandScreenIds: Array<number> = [1, 2, 3];
screen.stopExpand(expandScreenIds, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to stop expand screens. Code:${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in stopping expand screens.');
});
```

## screen.stopExpand<sup>(deprecated)</sup>

stopExpand(expandScreen:Array&lt;number&gt;): Promise&lt;void&gt;

停止屏幕的扩展模式，使用Promise异步回调。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 10

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------------ | ------------------- | --- |--------------------|
| expandScreen | Array&lt;number&gt; | 是   | 扩展屏幕ID集合，其中ID为整数。expandScreen数组大小不应超过1000。 |

**返回值：**

| 类型 | 说明 |
| --------------------- | ----------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 1400001 | Invalid display or screen. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let expandScreenIds: Array<number> = [1, 2, 3];
screen.stopExpand(expandScreenIds).then(() => {
  console.info('Succeeded in stopping expand screens.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop expand screens. Code:${err.code}, message is ${err.message}`);
});
```

## ExpandOption

扩展屏幕的参数。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称     | 类型 | 只读 | 可选 | 说明                |
| -------- | -------- | ---- | ---- | ------------------- |
| screenId | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 屏幕的id，该参数应为整数。          |
| startX   | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 屏幕的起始X轴坐标，该参数应为整数。 |
| startY   | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 屏幕的起始Y轴坐标，该参数应为整数。 |

## MultiScreenMode<sup>13+</sup>

屏幕模式枚举。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 22

| 名称              | 值  | 说明                            |
| ------------------ | ---- | -------------------------------- |
| SCREEN_MIRROR      | 0    | 表示屏幕为镜像模式。 |
| SCREEN_EXTEND      | 1    | 表示屏幕为扩展模式。 |

## MultiScreenPositionOptions<sup>13+</sup>

屏幕位置信息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 22

| 名称    | 类型     | 只读 | 可选  | 说明                |
| -------- | -------- | ---- | ---- | ------------------- |
| id       | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 屏幕的ID，该参数应为正整数，非正整数会作为非法参数报错。|
| startX   | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 屏幕的起始X轴坐标。以两块屏幕外接矩形的左上顶点为原点，向右为正方向。该参数应为正整数，非正整数会作为非法参数报错。 |
| startY   | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 屏幕的起始Y轴坐标。以两块屏幕外接矩形的左上顶点为原点，向下为正方向。该参数应为正整数，非正整数会作为非法参数报错。 |

## VirtualScreenOption

创建虚拟屏幕的参数。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称      | 类型 | 只读 | 可选 | 说明                       |
| --------- | -------- | ---- | ---- |--------------------------|
| name      | string   | 否   | 否   | 指定虚拟屏幕的名称。               |
| width     | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 指定虚拟屏幕的宽度，单位为px，该参数应为整数。 |
| height    | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 指定虚拟屏幕的高度，单位为px，该参数应为整数。 |
| density   | ArkTs-Dyn: number <br> ArkTs-Sta: double   | 否   | 否   | 指定虚拟屏幕的密度，单位为px，该参数为浮点数。 |
| surfaceId | string   | 否   | 否   | 指定虚拟屏幕的surfaceId。        |

## Screen

屏幕实例。

下列API示例中都需先使用[getAllScreens()](#screengetallscreens)、[createVirtualScreen()](#screencreatevirtualscreen)中的任一方法获取到Screen实例，再通过此实例调用对应方法。

### 属性

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

| 名称              | 类型                                       | 只读 | 可选 | 说明                                                          |
| ----------------- | ---------------------------------------------- | ---- | ---- |-------------------------------------------------------------|
| id                | ArkTs-Dyn: number <br> ArkTs-Sta: long                                         | 是   | 否   | 屏幕的ID，该参数为整数。<br/> **ArkTS-Dyn起始版本：** 9   <br/>  **ArkTS-Sta起始版本：** 22      |
| rsId<sup>21+</sup> |ArkTs-Dyn: number <br> ArkTs-Sta: long | 是 | 否 | 屏幕端口的id，该参数为整数。<br/> **ArkTS-Dyn起始版本：** 21   <br/>  **ArkTS-Sta起始版本：** 22|
| parent            | ArkTs-Dyn: number <br> ArkTs-Sta: long                                         | 是   | 否   | 屏幕所属群组的id，该参数为整数。 <br/> **ArkTS-Dyn起始版本：** 9   <br/>  **ArkTS-Sta起始版本：** 22     |
| supportedModeInfo | Array&lt;[ScreenModeInfo](#screenmodeinfo)&gt; | 是   | 否   | 屏幕支持的模式集合。<br/> **ArkTS-Dyn起始版本：** 9   <br/>  **ArkTS-Sta起始版本：** 22 |
| activeModeIndex   | ArkTs-Dyn: number <br> ArkTs-Sta: long                                         | 是   | 否   | 当前屏幕所处模式索引。模式索引的当前值和值的范围，会根据屏幕当前分辨率、刷新率和设备硬件差异产生变化。该参数为整数。<br/> **ArkTS-Dyn起始版本：** 9   <br/>  **ArkTS-Sta起始版本：** 22 |
| orientation       | [Orientation](#orientation)                     | 是   | 否   | 屏幕方向。<br/> **ArkTS-Dyn起始版本：** 9   <br/>  **ArkTS-Sta起始版本：** 22 |
| sourceMode<sup>10+</sup> | [ScreenSourceMode](#screensourcemode10)            | 是   | 否   | 屏幕来源模式。<br/> **ArkTS-Dyn起始版本：** 10   <br/>  **ArkTS-Sta起始版本：** 22     |
| serialNumber<sup>15+</sup> | string        | 是   | 是   | 扩展屏幕的序列号，默认返回为空字符串。**ArkTS-Dyn起始版本：** 15   <br/>  **ArkTS-Sta起始版本：** 22 |       

### setOrientation

setOrientation(orientation: Orientation, callback: AsyncCallback&lt;void&gt;): void

设置屏幕方向，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名      | 类型                        | 必填 | 说明                                                         |
| ----------- | --------------------------- | ---- | ------------------------------------------------------------ |
| orientation | [Orientation](#orientation) | 是   | 屏幕方向。orientation值必须来自Orientation枚举方向。                |
| callback    | AsyncCallback&lt;void&gt;   | 是   | 回调函数。当设置屏幕方向成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 1400003 | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  screenClass.setOrientation(screen.Orientation.VERTICAL, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the vertical orientation. Code:${err.code}, message is ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the vertical orientation.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let option : screen.VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  screenClass.setOrientation(screen.Orientation.VERTICAL, (err: BusinessError | null) => {
    const errCode = err?.code;
    if (errCode) {
      console.error(`Failed to set the vertical orientation. Code:${err?.code}, message is ${err?.message}`);
      return;
    }
    console.info('Succeeded in setting the vertical orientation.');
  });
}).catch((err: Error) => {
  console.error(`Failed to create the virtual screen. Code:${err?.code}, message is ${err?.message}`);
});
```

### setOrientation

setOrientation(orientation: Orientation): Promise&lt;void&gt;

设置屏幕方向，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名      | 类型                        | 必填 | 说明       |
| ----------- | --------------------------- | ---- | ---------- |
| orientation | [Orientation](#orientation) | 是   | 屏幕方向。orientation值必须来自Orientation枚举方向。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 1400003 | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let promise: Promise<void> = screenClass.setOrientation(screen.Orientation.VERTICAL);
  promise.then(() => {
    console.info('Succeeded in setting the vertical orientation.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the vertical orientation. Code:${err.code}, message is ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let option : screen.VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let promise: Promise<void> = screenClass.setOrientation(screen.Orientation.VERTICAL);
  promise.then(() => {
    console.info('Succeeded in setting the vertical orientation.');
  }).catch((err: Error) => {
    console.error(`Failed to set the vertical orientation. Code:${err?.code}, message is ${err?.message}`);
  });
}).catch((err: Error) => {
  console.error(`Failed to create the virtual screen. Code:${err?.code}, message is ${err?.message}`);
});
```

### setScreenActiveMode

ArkTS-Dyn: setScreenActiveMode(modeIndex: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setScreenActiveMode(modeIndex: long, callback: AsyncCallback&lt;void&gt;): void

设置屏幕当前显示模式，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型                      | 必填 | 说明                                                         |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| modeIndex | ArkTs-Dyn: number <br> ArkTs-Sta: long      | 是   | 模式索引。模式索引的当前值和值的范围，会根据屏幕当前分辨率、刷新率和设备硬件差异产生变化，该参数仅支持整数输入。索引为screen中[ScreenModeInfo](#screenmodeinfo)属性的模式id。 |
| callback  | AsyncCallback&lt;void&gt; | 是   | 回调函数。当设置屏幕当前显示模式成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400003 | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let modeIndex: number = 0;
  screenClass.setScreenActiveMode(modeIndex, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set screen active mode 0. Code:${err.code}, message is ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the screen active mode 0.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let option : screen.VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let modeIndex: long = 0;
  screenClass.setScreenActiveMode(modeIndex, (err: BusinessError | null) => {
    const errCode = err?.code;
    if (errCode) {
      console.error(`Failed to set screen active mode 0. Code:${err?.code}, message is ${err?.message}`);
      return;
    }
    console.info('Succeeded in setting the screen active mode 0.');
  });
}).catch((err: Error) => {
  console.error(`Failed to create the virtual screen. Code:${err?.code}, message is ${err?.message}`);
});
```

### setScreenActiveMode

ArkTS-Dyn: setScreenActiveMode(modeIndex: number): Promise&lt;void&gt;

ArkTS-Sta: setScreenActiveMode(modeIndex: long): Promise&lt;void&gt;


设置屏幕当前显示模式，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名    | 类型   | 必填 | 说明       |
| --------- | ------ | ---- | ---------- |
| modeIndex | ArkTs-Dyn: number <br> ArkTs-Sta: long | 是   | 模式索引。模式索引的当前值和值的范围，会根据屏幕当前分辨率、刷新率和设备硬件差异产生变化，该参数仅支持整数输入。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400003 | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let modeIndex: number = 0;
  let promise: Promise<void> = screenClass.setScreenActiveMode(modeIndex);
  promise.then(() => {
    console.info('Succeeded in setting screen active mode 0.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set screen active mode 0.Code:${err.code}, message is ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let option : screen.VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let modeIndex: number = 0;
  let promise: Promise<void> = screenClass.setScreenActiveMode(modeIndex);
  promise.then(() => {
    console.info('Succeeded in setting screen active mode 0.');
  }).catch((err: Error) => {
    console.error(`Failed to set screen active mode 0.Code:${err?.code}, message is ${err?.message}`);
  });
}).catch((err: Error) => {
  console.error(`Failed to create the virtual screen. Code:${err?.code}, message is ${err?.message}`);
});
```

### setDensityDpi

ArkTS-Dyn: setDensityDpi(densityDpi: number, callback: AsyncCallback&lt;void&gt;): void;

ArkTS-Sta: setDensityDpi(densityDpi: double, callback: AsyncCallback&lt;void&gt;): void;

设置屏幕的像素密度，使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名     | 类型                      | 必填 | 说明                                       |
| ---------- | ------------------------- | ---- |------------------------------------------|
| densityDpi | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 像素密度。支持的输入范围为[80, 640]，该参数仅支持整数输入。       |
| callback   | AsyncCallback&lt;void&gt; | 是   | 回调函数。当设置屏幕的像素密度成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400003 | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let densityDpi: number = 320;
class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  screenClass.setDensityDpi(densityDpi, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the pixel density of the screen to 320. Code:${err.code}, message is ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the density dpi.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let densityDpi: double = 320;

let option : screen.VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  screenClass.setDensityDpi(densityDpi, (err: BusinessError | null) => {
    const errCode = err?.code;
    if (errCode) {
      console.error(`Failed to set the pixel density of the screen to 320. Code:${err?.code}, message is ${err?.message}`);
      return;
    }
    console.info('Succeeded in setting the density dpi.');
  });
}).catch((err: Error) => {
  console.error(`Failed to create the virtual screen. Code:${err?.code}, message is ${err?.message}`);
});
```

### setDensityDpi

ArkTS-Dyn: setDensityDpi(densityDpi: number): Promise&lt;void&gt;

ArkTS-Sta: setDensityDpi(densityDpi: double): Promise&lt;void&gt;

设置屏幕的像素密度，使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名     | 类型   | 必填 | 说明                                 |
| ---------- | ------ | ---- |------------------------------------|
| densityDpi | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 像素密度。支持的输入范围为[80, 640]，该参数仅支持整数输入。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[屏幕错误码](errorcode-display.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 202     | Permission verification failed. A non-system application calls a system API.|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.|
| 1400003 | This display manager service works abnormally. |

**ArkTS-Dyn: 示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let densityDpi: number = 320;
class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  let promise: Promise<void> = screenClass.setDensityDpi(densityDpi);
  promise.then(() => {
    console.info('Succeeded in setting the pixel density of the screen to 320.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the pixel density of the screen to 320. Code:${err.code}, message is ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});
```

**ArkTS-Sta: 示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let densityDpi: double = 320;

let option : screen.VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: ''
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  let promise: Promise<void> = screenClass.setDensityDpi(densityDpi);
  promise.then(() => {
    console.info('Succeeded in setting the pixel density of the screen to 320.');
  }).catch((err: Error) => {
    console.error(`Failed to set the pixel density of the screen to 320. Code:${err?.code}, message is ${err?.message}`);
  });
}).catch((err: Error) => {
  console.error(`Failed to create the virtual screen. Code:${err?.code}, message is ${err?.message}`);
});
```

## Orientation

屏幕方向枚举。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称               | 值   | 说明                             |
| ------------------ | ---- | -------------------------------- |
| UNSPECIFIED        | 0    | 表示未指定屏幕方向，由系统指定。 |
| VERTICAL           | 1    | 表示指定屏幕为垂直方向。         |
| HORIZONTAL         | 2    | 表示指定屏幕为水平方向。         |
| REVERSE_VERTICAL   | 3    | 表示指定屏幕为反向垂直方向。     |
| REVERSE_HORIZONTAL | 4    | 表示指定屏幕为反向水平方向。     |

## ScreenSourceMode<sup>10+</sup>

屏幕显示内容来源模式枚举。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

| 名称               | 值   | 说明                             |
| ------------------ | ---- | -------------------------------- |
| SCREEN_MAIN         | 0    | 表示屏幕为默认主屏。 |
| SCREEN_MIRROR       | 1    | 表示屏幕内容来自镜像。         |
| SCREEN_EXTEND       | 2    | 表示屏幕内容来自扩展。         |
| SCREEN_ALONE        | 3    | 表示屏幕为未指定来源。     |

## ScreenModeInfo

屏幕显示模式信息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称        | 类型 | 只读 | 可选 | 说明                                               |
| ----------- | -------- | ---- | ---- | -------------------------------------------------- |
| id          | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 模式ID，所支持的模式由具体设备分辨率和刷新率决定，该参数为整数。 | 
| width       | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 屏幕的宽度，单位为px，该参数为整数。                                |
| height      | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 屏幕的高度，单位为px，该参数为整数。                                |
| refreshRate | ArkTs-Dyn: number <br> ArkTs-Sta: int   | 否   | 否   | 屏幕的刷新率，单位为hz，该参数为整数。                                     |

## Rect<sup>19+</sup>

矩形信息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 22

| 名称        | 类型 | 只读 | 可选 | 说明                                               |
| ----------- | -------- | ---- | ---- | -------------------------------------------------- |
| left    | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 矩形左上角顶点的X轴坐标，单位为px，该参数应为整数。 |
| top     | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 矩形左上角顶点的Y轴坐标，单位为px，该参数应为整数。 |
| width   | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 矩形的宽度，单位为px，该参数应为整数。             |
| height  | ArkTs-Dyn: number <br> ArkTs-Sta: long   | 否   | 否   | 矩形的高度，单位为px，该参数应为整数。             |