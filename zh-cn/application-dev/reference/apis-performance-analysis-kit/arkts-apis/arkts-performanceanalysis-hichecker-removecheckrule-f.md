# removeCheckRule

## 导入模块

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## removeCheckRule

```TypeScript
function removeCheckRule(rule: bigint) : void
```

删除一条或多条规则，删除的规则后续将不再生效。

如果传入的规则级别为线程级别，则仅从当前线程中删除。

**起始版本：** 9

<!--Device-hichecker-function removeCheckRule(rule: bigint) : void--><!--Device-hichecker-function removeCheckRule(rule: bigint) : void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | 需要删除的规则。支持使用或运算组合多个规则。可选值包括：<br>RULE_CAUTION_PRINT_LOG（记录日志）、RULE_CAUTION_TRIGGER_CRASH（应用退出）、RULE_THREAD_CHECK_SLOW_PROCESS（检测耗时函数调用）等，详见常量定义。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Sync] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // 删除一条规则
    hichecker.removeCheckRule(hichecker.RULE_CAUTION_PRINT_LOG);
    // 删除多条规则
    // hichecker.removeCheckRule(
    //     hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
} catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}
```
