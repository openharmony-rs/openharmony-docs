# isHyperSnapInitializing

## 导入模块

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## isHyperSnapInitializing

```TypeScript
function isHyperSnapInitializing(): Promise<boolean>
```

检查当前进程是否正在进行Hyper Snap初始化。

在Hyper Snap模板进程初始化阶段（包括预加载阶段和创建镜像阶段），此方法返回**true**。一旦快照完成、失败或流程不是模板过程，此方法返回**false**。

> **说明：** 
> 这对于应用程序区分正常冷启动和Hyper Snap模板非常有用
> 进程初始化，允许他们相应地调整初始化逻辑。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-hyperSnapManager-function isHyperSnapInitializing(): Promise<boolean>--><!--Device-hyperSnapManager-function isHyperSnapInitializing(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise用于返回结果。**true**表示当前进程正在进行Hyper Snap初始化。**false**表示当前进程未进行Hyper Snap初始化（快照已完成、失败或进程不是模板进程）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system service failed. |
