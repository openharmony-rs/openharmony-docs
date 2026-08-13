# containsCheckRule

## containsCheckRule

```TypeScript
function containsCheckRule(rule: bigint) : boolean
```

当前已添加的规则集中是否包含了某一个特定的规则。如果传入的规则级别为线程级别，则仅在当前线程中进行查询。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hichecker-function containsCheckRule(rule: bigint) : boolean--><!--Device-hichecker-function containsCheckRule(rule: bigint) : boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | 需要查询的规则。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询结果。true 表示规则已添加；false 表示规则未添加。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | the parameter check failed, only one bigint type parameter is needed |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // 添加一条规则
    hichecker.addCheckRule(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS);

    // 查询是否包含
    hichecker.containsCheckRule(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS); // return true;
    hichecker.containsCheckRule(hichecker.RULE_CAUTION_PRINT_LOG); // return false;
} catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}
```

