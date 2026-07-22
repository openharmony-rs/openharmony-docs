# @ohos.hichecker

HiChecker������ΪӦ�ÿ����׶�ʹ�õļ�⹤�ߣ����ڼ��������й����в����׺��Ե����⣬��Ӧ���̳߳��ֺ�ʱ���á�Ӧ�ý�����Ability��Դй¶�����⡣�����߿���ͨ����־��¼�����crash����ʽ�鿴�������Ⲣ�����޸ģ�����Ӧ����ʹ�����顣

**起始版本：** 8

<!--Device-unnamed-declare namespace hichecker--><!--Device-unnamed-declare namespace hichecker-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## 导入模块

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md#addcheckrule) | ����һ�����������ϵͳ��ϵͳ�������ӵĹ�����м�������������Ӧ���򴥷�ʱ����hilog��grep HiChecker�鿴������Ϣ�� |
| [addRule](arkts-performanceanalysis-hichecker-addrule-f.md#addrule) | > **˵����**  >  > ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��[hichecker.addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md#addcheckrule)�����  ����һ�����������ϵͳ��ϵͳ�������ӵĹ�����м������� |
| [contains](arkts-performanceanalysis-hichecker-contains-f.md#contains) | > **˵����**  >  > ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��[hichecker.containsCheckRule](arkts-performanceanalysis-hichecker-containscheckrule-f.md#containscheckrule)�����  ��ǰ�����ӵĹ������Ƿ������ĳһ���ض��Ĺ����������Ĺ��򼶱�Ϊ�̼߳�������ڵ�ǰ�߳��н��в�ѯ�� |
| [containsCheckRule](arkts-performanceanalysis-hichecker-containscheckrule-f.md#containscheckrule) | ��ǰ�����ӵĹ������Ƿ������ĳһ���ض��Ĺ����������Ĺ��򼶱�Ϊ�̼߳�������ڵ�ǰ�߳��н��в�ѯ�� |
| [getRule](arkts-performanceanalysis-hichecker-getrule-f.md#getrule) | ��ȡ��ǰ�̹߳��򡢽��̹��򡢸澯����ĺϼ��� |
| [removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md#removecheckrule) | ɾ��һ�����������ɾ���Ĺ��������������Ч�� |
| [removeRule](arkts-performanceanalysis-hichecker-removerule-f.md#removerule) | > **˵����**  >  > ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��[hichecker.removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md#removecheckrule)�����  ɾ��һ�����������ɾ���Ĺ��������������Ч�� |

### 常量

| 名称 | 说明 |
| --- | --- |
| [RULE_CAUTION_PRINT_LOG](arkts-performanceanalysis-hichecker-con.md#rule_caution_print_log) | �澯���򣬵��и澯ʱ��¼��־�� |
| [RULE_CAUTION_TRIGGER_CRASH](arkts-performanceanalysis-hichecker-con.md#rule_caution_trigger_crash) | �澯���򣬵��и澯ʱ��Ӧ���˳��� |
| [RULE_CHECK_ABILITY_CONNECTION_LEAK](arkts-performanceanalysis-hichecker-con.md#rule_check_ability_connection_leak) | �����򣬼���Ƿ���abilityй¶�� |
| [RULE_CHECK_ARKUI_PERFORMANCE](arkts-performanceanalysis-hichecker-con.md#rule_check_arkui_performance) | �����򣬼��arkui���ܡ� |
| [RULE_THREAD_CHECK_NETWORK_USAGE](arkts-performanceanalysis-hichecker-con.md#rule_thread_check_network_usage) | �����򣬼���߳��Ƿ���������ʱ�ӿڡ� |
| [RULE_THREAD_CHECK_SLOW_PROCESS](arkts-performanceanalysis-hichecker-con.md#rule_thread_check_slow_process) | �����򣬼���Ƿ��к�ʱ���������á� |

