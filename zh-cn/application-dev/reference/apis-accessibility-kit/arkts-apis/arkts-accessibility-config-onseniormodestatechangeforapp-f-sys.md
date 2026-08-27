# onSeniorModeStateChangeForApp（系统接口）

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## onSeniorModeStateChangeForApp

```TypeScript
function onSeniorModeStateChangeForApp(callback: Callback<AppSeniorModeInfo>): void
```

监听所有应用“长辈模式”的状态变化事件。使用callback异步回调。

> **说明：**
> 
> - 注册监听的callback参数应使用具名函数而非匿名函数，否则每次调用时会创建一个新的底层对象，引起内存泄漏问题。
> 
> - 调用此方法后，务必在组件实例销毁前（如aboutToDisappear生命周期中）使用
> [config.offSeniorModeStateChangeForApp](arkts-accessibility-config-offseniormodestatechangeforapp-f-sys.md)
> 取消监听，否则可能会导致崩溃。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_ACCESSIBILITY_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AppSeniorModeInfo](arkts-accessibility-config-appseniormodeinfo-i-sys.md)&gt; | 是 | 回调函数。返回被修改的应用“长辈模式”信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

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
