# GraphicsMemorySummary

����Ӧ���Դ����ݣ�����gl��graph���֡�

**起始版本：** 21

<!--Device-hidebug-interface GraphicsMemorySummary--><!--Device-hidebug-interface GraphicsMemorySummary-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## gl

```TypeScript
gl: number
```

gl�Դ��С��RenderService��Ⱦ���̼���������Դռ�õ��ڴ棬����ͼƬ�������ȣ���KBΪ��λ��

**类型：** number

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-GraphicsMemorySummary-gl: int--><!--Device-GraphicsMemorySummary-gl: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## graph

```TypeScript
graph: number
```

graph�Դ��С������ͳ�Ƶ�DMA�ڴ�ռ�ã�����ֱ��ͨ���ӿ������DMA buffer��ͨ��allocator_host�����DMA buffer����KBΪ��λ��

**类型：** number

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-GraphicsMemorySummary-graph: int--><!--Device-GraphicsMemorySummary-graph: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

