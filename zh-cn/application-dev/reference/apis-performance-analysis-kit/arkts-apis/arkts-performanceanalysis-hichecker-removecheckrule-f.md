# removeCheckRule

## 导入模块

```TypeScript
```

## removeCheckRule

```TypeScript
function removeCheckRule(rule: bigint) : void
```

删除一条或多条规则，删除的规则后续将不再生效。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | 需要删除的规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | the parameter check failed, only one bigint type parameter is needed |

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
