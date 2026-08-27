# on（系统接口）

## 导入模块

```TypeScript
```

## on('cellInfoChange')

```TypeScript
function on(type: 'cellInfoChange', callback: Callback<Array<CellInformation>>): void
```

订阅小区信息变化事件，使用callback方式作为异步方法。

**起始版本：** 8

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Telephony.StateRegistry

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cellInfoChange' | 是 | 小区信息变化事件，固定为'cellInfoChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;CellInformation&gt;&gt; | 是 | 以callback形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
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


## on('cellInfoChange')

```TypeScript
function on(type: 'cellInfoChange', options: ObserverOptions, callback: Callback<Array<CellInformation>>): void
```

订阅指定卡槽位的小区信息变化事件，使用callback方式作为异步方法。

**起始版本：** 8

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Telephony.StateRegistry

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cellInfoChange' | 是 | 小区信息变化事件，固定为'cellInfoChange'。 |
| options | ObserverOptions | 是 | 电话相关事件订阅参数可选项。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;CellInformation&gt;&gt; | 是 | 以callback形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
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
