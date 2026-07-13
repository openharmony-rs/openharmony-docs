# containsCheckRule

## containsCheckRule

```TypeScript
function containsCheckRule(rule: bigint) : boolean
```

��ǰ�����ӵĹ������Ƿ������ĳһ���ض��Ĺ����������Ĺ��򼶱�Ϊ�̼߳�������ڵ�ǰ�߳��н��в�ѯ��

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | ��Ҫ��ѯ�Ĺ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ��ѯ�����true ��ʾ���������ӣ�false ��ʾ����δ���ӡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | the parameter check failed, only one bigint type parameter is needed |

**示例：**

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

