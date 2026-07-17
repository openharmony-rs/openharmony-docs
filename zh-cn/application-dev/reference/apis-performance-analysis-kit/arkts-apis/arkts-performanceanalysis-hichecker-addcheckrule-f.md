# addCheckRule

## 导入模块

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## addCheckRule

```TypeScript
function addCheckRule(rule: bigint) : void
```

����һ�����������ϵͳ��ϵͳ�������ӵĹ�����м�������������Ӧ���򴥷�ʱ����hilog��grep HiChecker�鿴������Ϣ��

**起始版本：** 9

<!--Device-hichecker-function addCheckRule(rule: bigint) : void--><!--Device-hichecker-function addCheckRule(rule: bigint) : void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | ��Ҫ���ӵĹ��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | the parameter check failed, only one bigint type parameter is needed |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // 添加一条规则
    hichecker.addCheckRule(hichecker.RULE_CAUTION_PRINT_LOG);
    // 添加多条规则
    // hichecker.addCheckRule(
    //     hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
} catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}

```

