# disableGwpAsanGrayscale

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

<a id="disablegwpasangrayscale"></a>
## disableGwpAsanGrayscale

```TypeScript
function disableGwpAsanGrayscale(): void
```

ֹͣʹ��GWP-ASan�����øýӿڽ�ȡ���Զ������ã��ָ�Ĭ�ϲ���GwpAsanOptions��

**起始版本：** 20

<!--Device-hidebug-function disableGwpAsanGrayscale(): void--><!--Device-hidebug-function disableGwpAsanGrayscale(): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { taskpool } from '@kit.ArkTS';

@Concurrent
function disableGwpAsanTask(): void {
  hidebug.disableGwpAsanGrayscale();
}
taskpool.execute(disableGwpAsanTask).then(() => {
  console.info(`Disable GWP-ASan succeeded.`);
})

```

