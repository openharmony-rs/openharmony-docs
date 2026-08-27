# unregisterPasscodePromptCallback（系统接口）

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## unregisterPasscodePromptCallback

```TypeScript
function unregisterPasscodePromptCallback(): void
```

取消注册用于提示输入辅助设备密码的回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |
