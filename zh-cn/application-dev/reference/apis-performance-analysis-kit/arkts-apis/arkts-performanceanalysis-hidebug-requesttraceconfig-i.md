# RequestTraceConfig

�ṩtrace�ɼ��Ĳ���ѡ�

**起始版本：** 24

<!--Device-hidebug-interface RequestTraceConfig--><!--Device-hidebug-interface RequestTraceConfig-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## bufferSizeKb

```TypeScript
bufferSizeKb: number
```

trace�ļ��Ļ����С����KBΪ��λ����ֵΪ32λ�޷����������֣�������Ч��Χ��������ֵ�����ȡֵ��ΧΪ[1024, 15360]�������������ȡֵ��Χ��������������Ϊ����ı߽�ֵ��

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RequestTraceConfig-bufferSizeKb: int--><!--Device-RequestTraceConfig-bufferSizeKb: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## durationMs

```TypeScript
durationMs: number
```

trace�ɼ�ʱ������msΪ��λ����ֵΪ32λ�޷����������֣�������Ч��Χ��������ֵ�����ȡֵ��ΧΪ[1000, 15000]�������������ȡֵ��Χ��������������Ϊ����ı߽�ֵ��

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RequestTraceConfig-durationMs: int--><!--Device-RequestTraceConfig-durationMs: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## identifier

```TypeScript
identifier: string
```

�ɼ�trace������ļ���ǰ׺���ļ���ǰ׺ֻȡ�ַ���ǰ20���ַ����������ֽ�������ǰ20���ַ�ֻ������Сд��ĸ���»��ߣ�����������Ĭ��Ϊ���ַ�����

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RequestTraceConfig-identifier: string--><!--Device-RequestTraceConfig-identifier: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## reserved

```TypeScript
reserved: number
```

Ԥ���ֶΣ���������Ϊ0��

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RequestTraceConfig-reserved: int--><!--Device-RequestTraceConfig-reserved: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

