# controlCamera（系统接口）

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## controlCamera

```TypeScript
function controlCamera(callId: int, cameraId: string): Promise<void>
```

设置使用指定的相机进行视频通话，cameraId为空表示关闭相机。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-call-function controlCamera(callId: int, cameraId: string): Promise<void>--><!--Device-call-function controlCamera(callId: int, cameraId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | int | 是 | 呼叫Id。可以通过订阅callDetailsChange事件获得。 |
| cameraId | string | 是 | 相机ID。cameraId获取方式可参考相机管理 [getSupportedCameras](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#getsupportedcameras)接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式异步返回设置开启，关闭，切换相机结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.controlCamera(1, "1").then(() => {
    console.info(`controlCamera success.`);
}).catch((err: BusinessError) => {
    console.error(`controlCamera fail, promise: err->${JSON.stringify(err)}`);
});
```

