# clearBackgroundApps（系统接口）

## 导入模块

```TypeScript
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

## clearBackgroundApps

```TypeScript
function clearBackgroundApps(clearType: ClearType): Promise<void>
```

主动清理后台资源。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.CLEAR_BACKGROUND_APPS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearType | [ClearType](arkts-backgroundtasks-backgroundprocessmanager-cleartype-e-sys.md) | 是 | 资源清理类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [31800002](../errorcode-backgroundProcessManager.md#31800002-参数错误) | Parameter error. |
