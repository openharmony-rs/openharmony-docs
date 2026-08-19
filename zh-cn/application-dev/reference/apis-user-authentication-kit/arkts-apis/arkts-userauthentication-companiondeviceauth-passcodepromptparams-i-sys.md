# PasscodePromptParams（系统接口）

提示输入辅助设备密码时框架携带的选项。

**起始版本：** 26.1.0

<!--Device-companionDeviceAuth-interface PasscodePromptParams--><!--Device-companionDeviceAuth-interface PasscodePromptParams-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## challenge

```TypeScript
challenge: Uint8Array
```

当提示输入辅助设备密码时，框架携带的挑战。

**类型：** Uint8Array

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PasscodePromptParams-challenge: Uint8Array--><!--Device-PasscodePromptParams-challenge: Uint8Array-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

