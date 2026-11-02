# setPinDeletionDisabledState（系统接口）

## 导入模块

```TypeScript
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## setPinDeletionDisabledState

```TypeScript
function setPinDeletionDisabledState(userId: number, isDisabled: boolean): void
```

设置PIN删除功能的禁用状态。策略设置完成后，用户功能禁用时，无法删除PIN。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.USE_USER_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pinAuth-function setPinDeletionDisabledState(userId: int, isDisabled: boolean): void--><!--Device-pinAuth-function setPinDeletionDisabledState(userId: int, isDisabled: boolean): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。如果取值为0，则对所有用户生效，否则对指定用户生效。<br>取值限定为整数。 |
| isDisabled | boolean | 是 | 是否禁用PIN删除功能。True表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500008](../errorcode-useriam.md#12500008-参数校验失败) | The parameter is out of range. |
