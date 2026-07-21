# off（系统接口）

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

<a id="off"></a>
## off('uninstallDLPSandbox')

```TypeScript
function off(type: 'uninstallDLPSandbox', listener?: Callback<DLPSandboxState>): void
```

取消监听DLP沙箱卸载事件。调用成功后，应用不再接收DLP沙箱卸载事件的回调通知。

必须在调用[on](dlpPermission.on(type: 'uninstallDLPSandbox', listener: Callback<DLPSandboxState>))注册监听后才能调用此方法取消监听。

DLP管理应用退出或不再需要追踪沙箱状态变化时，取消事件订阅以释放监听资源。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-dlpPermission-function off(type: 'uninstallDLPSandbox', listener?: Callback<DLPSandboxState>): void--><!--Device-dlpPermission-function off(type: 'uninstallDLPSandbox', listener?: Callback<DLPSandboxState>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'uninstallDLPSandbox' | 是 | 监听事件类型。固定值为'uninstallDLPSandbox'：DLP沙箱卸载事件。 |
| listener | Callback&lt;DLPSandboxState&gt; | 否 | 沙箱应用卸载事件的回调。默认为空，表示取消该类型事件的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.off('uninstallDLPSandbox', (info: dlpPermission.DLPSandboxState) => {
  console.info('uninstallDLPSandbox event', info.appIndex, info.bundleName)
}); // 取消订阅。

```

