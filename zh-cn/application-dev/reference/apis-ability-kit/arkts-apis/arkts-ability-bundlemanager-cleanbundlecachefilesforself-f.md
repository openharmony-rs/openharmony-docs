# cleanBundleCacheFilesForSelf

## cleanBundleCacheFilesForSelf

```TypeScript
function cleanBundleCacheFilesForSelf(): Promise<void>
```

����Ӧ�������Ļ��档ʹ��Promise�첽�ص���

**起始版本：** 21

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

bundleManager.cleanBundleCacheFilesForSelf().then(() => {
  hilog.info(0x0000, 'testTag', 'cleanBundleCacheFilesForSelf complete.');
});

```

