# exit

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

<a id="exit"></a>
## exit

```TypeScript
function exit(code: number): void
```

终止程序。

请谨慎使用此接口。调用此接口后应用将退出。如果输入参数非 0，可能会导致数据丢失或出现异常。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [exit](arkts-arkts-process-processmanager-c.md#exit-1)

<!--Device-process-function exit(code: number): void--><!--Device-process-function exit(code: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 进程的退出码。 |

**示例：**

```TypeScript
process.exit(0);

```

