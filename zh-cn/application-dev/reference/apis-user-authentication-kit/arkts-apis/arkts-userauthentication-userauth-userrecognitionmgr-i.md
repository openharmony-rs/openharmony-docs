# UserRecognitionMgr

```TypeScript
interface UserRecognitionMgr
```

提供查询和订阅用户识别结果的接口。通过[getUserRecognitionMgr](arkts-userauthentication-userauth-getuserrecognitionmgr-f.md)获取实例。

> **说明：** 
> 
> 每次调用getUserRecognitionMgr返回新的UserRecognitionMgr实例。on和off需使用同一实例。

**起始版本：** 26.0.1

<!--Device-userAuth-interface UserRecognitionMgr--><!--Device-userAuth-interface UserRecognitionMgr-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getUserRecognitionResult

```TypeScript
getUserRecognitionResult(): Promise<UserRecognitionResult>
```

获取最新的用户识别结果。使用Promise异步回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionMgr-getUserRecognitionResult(): Promise<UserRecognitionResult>--><!--Device-UserRecognitionMgr-getUserRecognitionResult(): Promise<UserRecognitionResult>-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[UserRecognitionResult](arkts-userauthentication-userauth-userrecognitionresult-i.md)&gt; | Promise对象，返回用户识别结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let mgr = userAuth.getUserRecognitionMgr();
if (mgr == null) {
  console.error('device does not support user recognition');
} else {
  mgr.getUserRecognitionResult()
    .then((result: userAuth.UserRecognitionResult) => {
      console.info(`status: ${result.status}, userId: ${result.userId}`);
    })
    .catch((err: BusinessError) => {
      console.error(`getUserRecognitionResult failed, Code: ${err?.code}, message: ${err?.message}`);
    });
}
```

## offUserRecognitionChange

```TypeScript
offUserRecognitionChange(callback?: UserRecognitionResultCallback): void
```

取消订阅用户识别结果变化事件。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionMgr-offUserRecognitionChange(callback?: UserRecognitionResultCallback): void--><!--Device-UserRecognitionMgr-offUserRecognitionChange(callback?: UserRecognitionResultCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UserRecognitionResultCallback](arkts-userauthentication-userauth-userrecognitionresultcallback-t.md) | 否 | 要取消的回调。仅可取消通过本实例onUserRecognitionChange订阅的回调；不指定则取消本实例下所有已注册的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let mgr = userAuth.getUserRecognitionMgr();
if (mgr == null) {
  console.error('device does not support user recognition');
} else {
  let callback: userAuth.UserRecognitionResultCallback = (result: userAuth.UserRecognitionResult) => {
    console.info(`status: ${result.status}, userId: ${result.userId}`);
  };
  mgr.onUserRecognitionChange(callback);
  // 取消指定回调
  mgr.offUserRecognitionChange(callback);
  // 取消所有回调
  mgr.offUserRecognitionChange();
}
```

## onUserRecognitionChange

```TypeScript
onUserRecognitionChange(callback: UserRecognitionResultCallback): void
```

订阅用户识别结果变化事件。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionMgr-onUserRecognitionChange(callback: UserRecognitionResultCallback): void--><!--Device-UserRecognitionMgr-onUserRecognitionChange(callback: UserRecognitionResultCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UserRecognitionResultCallback](arkts-userauthentication-userauth-userrecognitionresultcallback-t.md) | 是 | 用户识别结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let mgr = userAuth.getUserRecognitionMgr();
if (mgr == null) {
  console.error('device does not support user recognition');
} else {
  let callback: userAuth.UserRecognitionResultCallback = (result: userAuth.UserRecognitionResult) => {
    console.info(`status: ${result.status}, userId: ${result.userId}`);
  };
  mgr.onUserRecognitionChange(callback);
}
```
