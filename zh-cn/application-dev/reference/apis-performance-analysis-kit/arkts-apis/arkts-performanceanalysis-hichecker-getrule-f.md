# getRule

## 导入模块

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

<a id="getrule"></a>
## getRule

```TypeScript
function getRule() : bigint
```

��ȡ��ǰ�̹߳��򡢽��̹��򡢸澯����ĺϼ���

**起始版本：** 8

<!--Device-hichecker-function getRule() : bigint--><!--Device-hichecker-function getRule() : bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | ��ǰϵͳ�����ӵĹ��� |

**示例：**

```TypeScript
// 添加一条规则
hichecker.addCheckRule(hichecker.RULE_CAUTION_PRINT_LOG);

// 获取已添加的规则
hichecker.getRule();

```

