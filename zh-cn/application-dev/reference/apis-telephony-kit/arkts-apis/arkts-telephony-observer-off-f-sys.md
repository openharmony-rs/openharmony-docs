# off（系统接口）

## 导入模块

```TypeScript
```

## off('cellInfoChange')

```TypeScript
function off(type: 'cellInfoChange', callback?: Callback<Array<CellInformation>>): void
```

取消订阅小区信息变化事件，使用callback方式作为异步方法。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.StateRegistry

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cellInfoChange' | 是 | 小区信息变化事件，固定为'cellInfoChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;CellInformation&gt;&gt; | 否 | 以callback形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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
