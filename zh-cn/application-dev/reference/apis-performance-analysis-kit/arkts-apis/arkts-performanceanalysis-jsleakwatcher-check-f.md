# check

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## check

```TypeScript
function check(): string
```

��ȡ��ͨ��jsLeakWatcher.watchע�ᷢ��й©�Ķ����б�������GC��δ�����յĶ���ᱻ���Ϊй©��

**起始版本：** 12

<!--Device-jsLeakWatcher-function check(): string--><!--Device-jsLeakWatcher-function check(): string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ����GC��δ�����յ�й©�����б���<br>**˵��**��check�ɹ�������JSON��ʽ��й©�����б���checkʧ�ܣ����ؿ��ַ����� |

**示例：**

```TypeScript
let leakObjlist:string = jsLeakWatcher.check();

```

