# getSystemConfig

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## getSystemConfig

```TypeScript
function getSystemConfig(name: number): number
```

获取系统配置信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getSystemConfig](arkts-arkts-process-processmanager-c.md#getsystemconfig)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | number | 是 | 指定系统配置参数名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回系统配置信息。 |

**示例**

```TypeScript
let _SC_ARG_MAX = 0;
let pres = process.getSystemConfig(_SC_ARG_MAX);
```

```TypeScript
// 创建ProcessManager实例
let processManager = new process.ProcessManager();
// 定义系统配置参数
let _SC_ARG_MAX = 0;
// 获取系统配置信息
let pres = processManager.getSystemConfig(_SC_ARG_MAX);
```
