# processPluginCommand

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## processPluginCommand

```TypeScript
function processPluginCommand(code: PluginCmd, message: string): Promise<string>
```

处理透明加解密场景下的插件相关命令。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.DLP_POLICY_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | [PluginCmd](arkts-dataprotection-dlppermission-plugincmd-e.md) | 是 | 表示要进行处理的插件命令。 |
| message | string | 是 | 要进行处理的信息。长度不超过4096字节，超出此范围抛出错误码19100001。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回当前命令执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |
| [19100025](../errorcode-dlp.md#19100025-文件无效) | The file is invalid. |

**示例**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

const cmd: dlpPermission.PluginCmd = dlpPermission.PluginCmd.CMD_BASE_INSTALL_PLUGIN;
const message: string = "testPath";
dlpPermission.processPluginCommand(cmd, message).then((res) => {
  console.info('res', JSON.stringify(res));
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
}).finally(() => {
  console.info("Completed processPluginCommand operation.");
})
```
