# PasscodePromptParams（系统接口）

```TypeScript
interface PasscodePromptParams
```

通行码输入请求的参数，用于传递挑战值等上下文信息。

**起始版本：** 26.0.1

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

请求通行码时由系统下发的挑战值。

**类型：** Uint8Array

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PasscodePromptParams-challenge: Uint8Array--><!--Device-PasscodePromptParams-challenge: Uint8Array-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。
