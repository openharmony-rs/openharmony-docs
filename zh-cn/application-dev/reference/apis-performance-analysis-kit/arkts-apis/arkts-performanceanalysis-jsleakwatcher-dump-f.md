# dump

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## dump

```TypeScript
function dump(filePath: string): Array<string>
```

����й©�б���������ڴ���ա�

**起始版本：** 12

<!--Device-jsLeakWatcher-function dump(filePath: string): Array<string>--><!--Device-jsLeakWatcher-function dump(filePath: string): Array<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | ������Ϣ���ɵ��ļ���ŵ�·����<br>**˵��**����API version 24��ʼ���������������ڣ����������µ�һ�ݿ�����Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | ����������ֱ�Ϊ�ļ�����׺Ϊ.jsleaklist��й©�б����ļ�����׺Ϊ.heapsnapshot������ڴ�����ļ���<br>**˵��**��dump�ɹ�������й©�б��ļ�·����������ڴ����·����dumpʧ�ܣ����ؿ����顣 |

**示例：**

```TypeScript
let context = this.getUIContext().getHostContext();
let files: Array<string> = jsLeakWatcher.dump(context?.filesDir);

```

