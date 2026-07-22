# abort

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## abort

```TypeScript
function abort(): void
```

中止进程并生成核心文件。该方法会导致进程立即退出，请谨慎使用。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-process-function abort(): void--><!--Device-process-function abort(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
process.abort();

```

