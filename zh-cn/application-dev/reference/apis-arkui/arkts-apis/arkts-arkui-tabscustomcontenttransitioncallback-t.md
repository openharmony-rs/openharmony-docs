# TabsCustomContentTransitionCallback

```TypeScript
declare type TabsCustomContentTransitionCallback = (from: number, to: number) => TabContentAnimatedTransition | undefined
```

�Զ���Tabsҳ���л�������ʼʱ�����Ļص���

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | number | 是 | ������ʼʱ����ǰҳ���indexֵ��������0��ʼ��<br/>ȡֵ��Χ��[0, ����ֵ-1]�������õ�ֵ��������ֵ��С��0ʱ��ת�������� |
| to | number | 是 | ������ʼʱ��Ŀ��ҳ���indexֵ��������0��ʼ��<br/>ȡֵ��Χ��[0, ����ֵ-1]�������õ�ֵ��������ֵ��С��0ʱ��ת�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TabContentAnimatedTransition \| undefined | Information about the custom tab switching animation. |

