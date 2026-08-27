# getEnvironmentVar

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## getEnvironmentVar

```TypeScript
function getEnvironmentVar(name: string): string
```

获取环境变量名对应的值。如果环境变量不存在，返回undefined。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getEnvironmentVar](arkts-arkts-process-processmanager-c.md#getenvironmentvar)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 环境变量名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回环境变量名对应的值。 |

**示例**

```TypeScript
let pres = process.getEnvironmentVar("PATH");
```

```TypeScript
// 创建ProcessManager实例
let processManager = new process.ProcessManager();
// 获取PATH环境变量的值
let pres = processManager.getEnvironmentVar("PATH");
```
