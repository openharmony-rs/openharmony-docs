# UserRecognitionMgr

提供用户识别结果查询和订阅接口，使用[getUserRecognitionMgr](arkts-userauthentication-userauth-getuserrecognitionmgr-f.md)获取**UserRecognitionMgr**实例。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getUserRecognitionResult

```TypeScript
getUserRecognitionResult(): Promise<UserRecognitionResult>
```

获取最新的用户识别结果。该接口使用promise返回结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[UserRecognitionResult](arkts-userauthentication-userauth-userrecognitionresult-i.md)&gt; | Promise用于返回识别结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

## offUserRecognitionChange

```TypeScript
offUserRecognitionChange(callback?: UserRecognitionResultCallback): void
```

取消订阅用户识别变更事件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UserRecognitionResultCallback](arkts-userauthentication-userauth-userrecognitionresultcallback-t.md) | 否 | 取消注册的回调。如果未指定该参数，则取消订阅所有已注册的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

## onUserRecognitionChange

```TypeScript
onUserRecognitionChange(callback: UserRecognitionResultCallback): void
```

订阅用户识别变更事件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UserRecognitionResultCallback](arkts-userauthentication-userauth-userrecognitionresultcallback-t.md) | 是 | 接收识别结果的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
