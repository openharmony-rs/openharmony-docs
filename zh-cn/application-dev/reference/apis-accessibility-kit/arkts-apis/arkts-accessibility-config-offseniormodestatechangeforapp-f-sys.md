# offSeniorModeStateChangeForApp（系统接口）

## offSeniorModeStateChangeForApp

```TypeScript
function offSeniorModeStateChangeForApp(callback?: Callback<AppSeniorModeInfo>): void
```

Unregister the observer for application's senior mode state changes.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.READ_ACCESSIBILITY_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-config-function offSeniorModeStateChangeForApp(callback?: Callback<AppSeniorModeInfo>): void--><!--Device-config-function offSeniorModeStateChangeForApp(callback?: Callback<AppSeniorModeInfo>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AppSeniorModeInfo&gt; | 否 | Asynchronous callback interface. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A non-system application calls a system API. |

**示例：**

```TypeScript
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback = (data: config.AppSeniorModeInfo) => {
    console.info(`callback data, name: ${data.bundleName}, appIndex: ${data.appIndex}, seniorModeState: ${data.seniorModeState}`);
  }

  aboutToAppear(): void {
    config.onSeniorModeStateChangeForApp(this.callback);
  }

  aboutToDisappear(): void {
    config.offSeniorModeStateChangeForApp(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

