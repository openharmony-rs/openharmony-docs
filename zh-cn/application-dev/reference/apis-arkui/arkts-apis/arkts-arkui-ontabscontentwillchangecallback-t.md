# OnTabsContentWillChangeCallback

```TypeScript
declare type OnTabsContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean
```

�Զ���Tabsҳ���л������¼���������ҳ�漴����ʾʱ�����Ļص���

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentIndex | number | 是 | ��ǰ��ʾҳ���index������������0��ʼ���㡣 |
| comingIndex | number | 是 | ��Ҫ��ʾ����ҳ���index������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ���ص�����handler�ķ���ֵΪtrueʱ��Tabs�����л�����ҳ�档<br/>���ص�����handler�ķ���ֵΪfalseʱ��Tabs�޷��л�����ҳ�棬��Ȼ��ʾԭ��ҳ�����ݡ� |

