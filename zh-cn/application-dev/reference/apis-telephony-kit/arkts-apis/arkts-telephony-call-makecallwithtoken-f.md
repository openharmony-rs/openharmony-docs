# makeCallWithToken

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## makeCallWithToken

```TypeScript
function makeCallWithToken(phoneNumber: string, options?: MakeCallOptions): Promise<string>
```

跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。 > **说明：**: > > 该接口返回校验token，应用可以利用phoneNumber和token实现特定能力，比如蜂窝下行流的录制。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-call-function makeCallWithToken(phoneNumber: string, options?: MakeCallOptions): Promise<string>--><!--Device-call-function makeCallWithToken(phoneNumber: string, options?: MakeCallOptions): Promise<string>-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [MakeCallOptions](arkts-telephony-call-makecalloptions-i.md) | 否 | 通话参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回鉴权校验token。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

**示例**

```TypeScript
import { call } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 设置是否隐藏拨号界面与应用是否开启自定义无障碍功能
let makeOptions: call.MakeCallOptions = {
  isHideDialScreen: true,
  isCustomAccessibility: true
};

call.makeCallWithToken("138xxxxxxxx", makeOptions).then(() => {
  console.info(`makeCallWithToken success`);
}).catch((err: BusinessError) => {
  console.error(`makeCallWithToken fail, promise: 本次操作异常，err->Code${err.code}, message:${err.message}请稍后重试。`);
});
```

