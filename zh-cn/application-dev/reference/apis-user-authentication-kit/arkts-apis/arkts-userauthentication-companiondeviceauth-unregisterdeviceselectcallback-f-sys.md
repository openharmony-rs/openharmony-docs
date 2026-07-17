# unregisterDeviceSelectCallback（系统接口）

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## unregisterDeviceSelectCallback

```TypeScript
function unregisterDeviceSelectCallback(): void
```

取消注册伴随设备选择回调。取消后，系统将不再调用应用注册的设备选择回调，设备选择将回退到系统默认行为。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-companionDeviceAuth-function unregisterDeviceSelectCallback(): void--><!--Device-companionDeviceAuth-function unregisterDeviceSelectCallback(): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  companionDeviceAuth.unregisterDeviceSelectCallback();
} catch (error) {
  const err = error as BusinessError;
  console.error(`error has been captured: ${err.code} ${err.message}`);
}

```

