# markLifecycleEnded

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## markLifecycleEnded

```TypeScript
function markLifecycleEnded(obj: object): void
```

将对象标记为生命周期已结束的对象。如果开发者确定某个对象不再需要使用或引用，开发者在释放该对象之前使用此接口进行标记。当OOM故障发生时，如果导出的堆快照文件中某个对象的属性包含__ohosDfxJsLeakMarker属性，则说明该对象未被如期释放。

> **注意**
> 由于单次标记操作会产生少量内存开销，建议仅标记疑似泄漏的对象或仅在灰度场景下进行标记，避免在正常场景下大规模标记。

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-jsLeakWatcher-function markLifecycleEnded(obj: object): void--><!--Device-jsLeakWatcher-function markLifecycleEnded(obj: object): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | object | 是 | 需要标记为生命周期已结束的对象。<br>值约束：1: 非null值2: 非undefined值3: 非原始类型值。 |
