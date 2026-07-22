# off

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## off('openDLPFile')

```TypeScript
function off(type: 'openDLPFile', listener?: Callback<AccessedDLPFileInfo>): void
```

取消监听打开DLP文件。仅支持在非DLP沙箱应用中调用。调用成功后，将不再接收DLP文件打开事件的通知。

该接口通常在页面销毁或不再需要监听时调用以释放资源。

**起始版本：** 10

<!--Device-dlpPermission-function off(type: 'openDLPFile', listener?: Callback<AccessedDLPFileInfo>): void--><!--Device-dlpPermission-function off(type: 'openDLPFile', listener?: Callback<AccessedDLPFileInfo>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'openDLPFile' | 是 | 监听事件类型。固定值为'openDLPFile'：打开DLP文件事件。 |
| listener | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AccessedDLPFileInfo&gt; | 否 | DLP文件被打开的事件的回调。当需要取消特定回调时传入此参数（传入之前注册的回调函数），当需要取消所有回调时可不传此参数。不传入时默认为空，取消该类型事件的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100007](../errorcode-dlp.md#19100007-dlp沙箱应用不允许调用此接口) | No permission to call this API,which is available only for non-DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.off('openDLPFile', (info: dlpPermission.AccessedDLPFileInfo) => {
  console.info('openDlpFile event', info.uri, info.lastOpenTime);
}); // 取消订阅。

```

