# @ohos.telephony.observer (电话服务状态监听)(系统接口)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @shao-yikai-->
<!--Designer: @wnazgul-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->

本模块提供订阅管理功能，可以订阅/取消订阅的事件包括：小区信息变化事件、指定卡槽位的小区信息变化事件。

> **说明：**
>
> 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口请参见[@ohos.telephony.observer (电话服务状态监听)](js-apis-observer.md)。

## 导入模块

```ts
import { observer } from '@kit.TelephonyKit';
```


## observer.on('cellInfoChange')<sup>8+</sup>

on\(type: \'cellInfoChange\', callback: Callback\<Array\<CellInformation\>\>\): void

订阅小区信息变化事件，使用callback方式作为异步方法。适用于需要获取基站小区信息变化的应用场景，如位置服务辅助定位、网络信号质量监测、基站切换跟踪等。

**系统接口：** 此接口为系统接口。

**需要权限**：ohos.permission.LOCATION 和 ohos.permission.APPROXIMATELY_LOCATION

**系统能力**：SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名   | 类型                                                      | 必填 | 说明                                      |
| -------- | --------------------------------------------------------- | ---- |------------------------------------------|
| type     | string                                                    | 是   | 小区信息变化事件，固定为'cellInfoChange'。 |
| callback | Callback\<Array\<[CellInformation](js-apis-radio.md#cellinformation8)\>\> | 是   | 以callback形式异步返回结果。                |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[电话子系统错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { observer, radio } from '@kit.TelephonyKit';
import { radio } from '@kit.TelephonyKit';

// 订阅小区信息变化事件
try {
  observer.on('cellInfoChange', (data: Array<radio.CellInformation>) => {
      console.info("on cellInfoChange, data:" + JSON.stringify(data));
  });
} catch (err) {
  console.error(`observer.on failed, err: ${JSON.stringify(err)}`);
}
```


## observer.on('cellInfoChange')<sup>8+</sup>（指定卡槽位）

on\(type: \'cellInfoChange\', options: ObserverOptions, callback: Callback\<Array\<CellInformation\>\>\): void

订阅指定卡槽位的小区信息变化事件，使用callback方式作为异步方法。适用于多卡场景下需要监听指定卡槽小区信息变化的应用，如双卡设备分别监测不同运营商的基站信号质量、位置服务等。

**系统接口：** 此接口为系统接口。

**需要权限**：ohos.permission.LOCATION 和 ohos.permission.APPROXIMATELY_LOCATION

**系统能力**：SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型                                               | 必填 | 说明                                      |
| ------ |--------------------------------------------------| ---- |--------------------------------------------|
| type     | string                                           | 是   | 小区信息变化事件，固定为'cellInfoChange'。 |
| options  | [ObserverOptions](js-apis-observer.md#observeroptions11)            | 是   | 事件订阅参数选项，可指定需要订阅的卡槽位（slotId）等信息。                |
| callback | Callback\<Array\<[CellInformation](js-apis-radio.md#cellinformation8)\>\> | 是   | 以callback形式异步返回结果。       |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[电话子系统错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { observer, radio } from '@kit.TelephonyKit';
import { radio } from '@kit.TelephonyKit';

// 设置订阅参数，指定卡槽位
let options: observer.ObserverOptions = {
    slotId: 0
}
// 订阅指定卡槽位的小区信息变化事件
try {
  observer.on('cellInfoChange', options, (data: Array<radio.CellInformation>) => {
      console.info("on cellInfoChange, data:" + JSON.stringify(data));
  });
} catch (err) {
  console.error(`observer.on failed, err: ${JSON.stringify(err)}`);
}
```


## observer.off('cellInfoChange')<sup>8+</sup>

off\(type: \'cellInfoChange\', callback?: Callback\<Array\<CellInformation\>\>\): void

取消订阅小区信息变化事件。

> **说明：**
>
>可以指定传入`on`中的`callback`取消一个订阅。也可以不指定`callback`清空所有订阅。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名   | 类型                                                      | 必填 | 说明                                                         |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                    | 是   | 小区信息变化事件，固定为'cellInfoChange'。                                            |
| callback | Callback\<Array\<[CellInformation](js-apis-radio.md#cellinformation8)\>\> | 否   | 取消指定回调的订阅。指定传入on中的callback可取消对应的一个订阅；不填写该参数时，将清空所有订阅。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[电话子系统错误码](errorcode-telephony.md)。

| 错误码ID |                  错误信息                    |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**示例：**

```ts
import { observer, radio } from '@kit.TelephonyKit';
import { radio } from '@kit.TelephonyKit';

let callback: (data: Array<radio.CellInformation>) => void = (data: Array<radio.CellInformation>) => {
    console.info("on cellInfoChange, data:" + JSON.stringify(data));
}
try {
  observer.on('cellInfoChange', callback);
  // 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
  observer.off('cellInfoChange', callback);
  observer.off('cellInfoChange');
} catch (err) {
  console.error(`observer on/off failed, err: ${JSON.stringify(err)}`);
}

```

