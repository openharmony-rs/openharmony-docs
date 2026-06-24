# AnimationStartHandler

```TypeScript
declare type AnimationStartHandler = (index: number, targetIndex: number, event: SwiperAnimationEvent) => void
```

�л�������ʼʱ�Ļص���

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | ��ǰ��ʾԪ�ص�������������ʼǰ��indexֵ���������ս���������indexֵ���� |
| targetIndex | number | 是 | �л�����Ŀ��Ԫ�ص������� |
| event | SwiperAnimationEvent | 是 | ���������Ϣ���������᷽���ϵ�ǰ��ʾԪ�غ�Ŀ��Ԫ�����ArcSwiper��ʼλ�õ�λ�ƣ��Լ������ٶȡ� |

