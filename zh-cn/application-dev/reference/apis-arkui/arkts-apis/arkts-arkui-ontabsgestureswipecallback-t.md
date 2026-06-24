# OnTabsGestureSwipeCallback

```TypeScript
declare type OnTabsGestureSwipeCallback = (index: number, extraInfo: TabsAnimationEvent) => void
```

��ҳ����ֻ��������У���֡�����Ļص���

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | ��ǰ��ʾԪ�ص�������������0��ʼ��<br/>ȡֵ��Χ��[0, ����ֵ-1] |
| extraInfo | TabsAnimationEvent | 是 | ���������Ϣ��ֻ�������᷽���ϵ�ǰ��ʾԪ�������Tabs��ʼλ�õ�λ�ơ� |

