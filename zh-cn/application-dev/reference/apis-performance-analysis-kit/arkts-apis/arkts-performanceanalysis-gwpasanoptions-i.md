# GwpAsanOptions

GWP-ASan����������������Ƿ�ʹ�ܡ�����Ƶ�ʣ��Լ�������Ĳ������

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## alwaysEnabled

```TypeScript
alwaysEnabled?: boolean
```

�����Ƿ�ÿ��������ʹ��GWP-ASan��true��100%ʹ��GWP-ASan��false��1/128����ʹ��GWP-ASan��Ĭ��ֵ��false��

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## isRecover

```TypeScript
isRecover?: boolean
```

���ڿ���Ӧ����100%���ʿ���GWP-ASanʱ���Ƿ��Կɻָ�ģʽ���С�true����GWP-ASan��100%���ʿ���ʱ��Ӧ���Կɻָ�ģʽ���С�false����GWP-ASan��100%���ʿ���ʱ��Ӧ���Բ��ɻָ�ģʽ���С�Ĭ��ֵ��false��ע�⣺�ò���ֻ��"��100%���ʿ���GWP-ASan"��������Ч��1/128���ʿ���������Ĭ��Ϊ�ɻָ�������isRecover���ơ�

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxSimutaneousAllocations

```TypeScript
maxSimutaneousAllocations?: number
```

������Ĳ������Ĭ��ֵΪ1000����Ҫ�������0����������������С��������ȡ����������þ�ʱ���·�����ڴ潫�����ܼ�ء��ͷ���ʹ�õ��ڴ����ռ�õĲ�۽��Զ����á�����ֵ��<=20000���������ܵ���VMA���ޱ�����

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sampleRate

```TypeScript
sampleRate?: number
```

GWP-ASan����Ƶ�ʣ�Ĭ��ֵΪ2500����Ҫ�������0����������������С��������ȡ����1/sampleRate�ĸ��ʶԷ�����ڴ���в���������ֵ��>=1000����С������Ӱ�����ܡ�

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

