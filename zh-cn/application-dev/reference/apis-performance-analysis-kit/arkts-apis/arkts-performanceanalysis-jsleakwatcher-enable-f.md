# enable

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## enable

```TypeScript
function enable(isEnable: boolean): void
```

ʹ��ArkTS����й©��⣬Ĭ�Ϲرա���������ռ�й©��Ϣ�������������ܿ�����

**起始版本：** 12

<!--Device-jsLeakWatcher-function enable(isEnable: boolean): void--><!--Device-jsLeakWatcher-function enable(isEnable: boolean): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnable | boolean | 是 | �Ƿ�ʹ��jsLeakWatcher��true��ʹ��jsLeakWatcher��false����ʹ��jsLeakWatcher�� |

**示例：**

```TypeScript
jsLeakWatcher.enable(true);

```

