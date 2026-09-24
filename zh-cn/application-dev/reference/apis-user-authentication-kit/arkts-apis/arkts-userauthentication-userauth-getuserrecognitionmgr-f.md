# getUserRecognitionMgr

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getUserRecognitionMgr

```TypeScript
function getUserRecognitionMgr(): UserRecognitionMgr | null
```

获取一个[UserRecognitionMgr](arkts-userauthentication-userauth-userrecognitionmgr-i.md)实例，用于查询和订阅用户识别结果。

> **说明：** 
> 每次调用都会返回一个新的**UserRecognitionMgr**实例。需使用同一实例进行订阅和取消订阅。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ACCESS_USER_PASSIVE_RECOGNITION

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UserRecognitionMgr](arkts-userauthentication-userauth-userrecognitionmgr-i.md) &#124; null | 用户识别管理器实例。如果设备不支持此能力则返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
