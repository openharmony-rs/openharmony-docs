# createGroup

## createGroup

```TypeScript
function createGroup(config: GroupConfig): Promise<string>
```

根据[GroupConfig](arkts-basicservices-agent-groupconfig-i.md#GroupConfig)分组条件创建分组 ，并返回分组id。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-agent-function createGroup(config: GroupConfig): Promise<string>--><!--Device-agent-function createGroup(config: GroupConfig): Promise<string>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [GroupConfig](arkts-basicservices-agent-groupconfig-i.md) | 是 | 下载任务分组选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回创建完成的分组id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

## 示例

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 准备分组配置选项 GroupConfig 对象。
let config: request.agent.GroupConfig = {
    notification: {},
};
// 调用 createGroup 接口创建分组。
request.agent.createGroup(config).then((gid: string) => {
  console.info(`Succeeded in creating a download task group. `);
}).catch((err: Error) => {
  console.error(`Failed to create a download group, Code: ${err.code}, message: ${err.message}`);
});
```

