# OnTabsAnimationStartCallback

```TypeScript
declare type OnTabsAnimationStartCallback = (index: number, targetIndex: number, extraInfo: TabsAnimationEvent) => void
```

�л�������ʼʱ�����Ļص���

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | ��ǰ��ʾԪ�ص�������������0��ʼ�� |
| targetIndex | number | 是 | ��ǰ��ʾԪ�ص�������������0��ʼ�� |
| extraInfo | TabsAnimationEvent | 是 | ���������Ϣ���������᷽���ϵ�ǰ��ʾԪ�غ�Ŀ��Ԫ�����Tabs��ʼλ�õ�λ�ƣ��Լ������ٶȡ� |

