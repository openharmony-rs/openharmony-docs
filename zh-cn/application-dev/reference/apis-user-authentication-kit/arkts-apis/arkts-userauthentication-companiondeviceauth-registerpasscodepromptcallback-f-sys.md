# registerPasscodePromptCallback（系统接口）

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## registerPasscodePromptCallback

```TypeScript
function registerPasscodePromptCallback(callback: PasscodePromptCallback): void
```

注册当框架需要辅助设备密码时调用的回调。 如果回调已经被注册，则新的回调将替换它。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-companionDeviceAuth-function registerPasscodePromptCallback(callback: PasscodePromptCallback): void--><!--Device-companionDeviceAuth-function registerPasscodePromptCallback(callback: PasscodePromptCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PasscodePromptCallback](arkts-userauthentication-companiondeviceauth-passcodepromptcallback-t-sys.md) | 是 | 框架调用的回调 密码为必填项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

