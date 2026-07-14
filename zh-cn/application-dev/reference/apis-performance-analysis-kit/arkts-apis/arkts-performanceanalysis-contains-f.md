# contains

## contains

```TypeScript
function contains(rule: bigint): boolean
```

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��[hichecker.containsCheckRule](arkts-performanceanalysis-containscheckrule-f.md#containscheckrule-1)�����

��ǰ�����ӵĹ������Ƿ������ĳһ���ض��Ĺ����������Ĺ��򼶱�Ϊ�̼߳�������ڵ�ǰ�߳��н��в�ѯ��

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [containsCheckRule](arkts-performanceanalysis-containscheckrule-f.md#containscheckrule-1)

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | ��Ҫ��ѯ�Ĺ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ��ѯ�����true ��ʾ���������ӣ�false ��ʾ����δ���ӡ� |

**示例：**

```TypeScript
// 添加一条规则
hichecker.addRule(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS);

// 查询是否包含
hichecker.contains(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS); // return true;
hichecker.contains(hichecker.RULE_CAUTION_PRINT_LOG); // return false;

```

