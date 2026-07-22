# watch

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## watch

```TypeScript
function watch(obj: object, msg: string): void
```

ע������й©�Ķ���

**起始版本：** 12

<!--Device-jsLeakWatcher-function watch(obj: object, msg: string): void--><!--Device-jsLeakWatcher-function watch(obj: object, msg: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | object | 是 | ��Ҫ���Ķ���<br>**˵��**���ɴ����κη�null��ArkTS���󣬲�֧��undefined�ͻ������͡� |
| msg | string | 是 | �Զ��������Ϣ�� |

**示例：**

```TypeScript
let obj:Object = new Object();
jsLeakWatcher.watch(obj, "Trace Object");

```

